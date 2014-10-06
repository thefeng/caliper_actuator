
# Digital Caliper Linear Actuator

## Building a Linear Actuator From a Set of Digital Calipers

<img src=images/caliperBanner.png>

### Introduction
This is a tutorial for construction of a linear actuator with encoder feedback capable of linear positioning to a precision of 0.01mm. The system is based on a set of standard digital calipers and requires only 3D printed components and basic hardware. 

### Hardware requirements

<img src=images/hardwareRequirements.png width=600>

* **1x Standard Digital Caliper**
    * These can be found on eBay, amazon or your local hardware shop for ~£15.
* **1x 12V Hobby DC Gearmotor**
    * Preferably high torque. The motor used here was 120rpm.
    * Look for a metric shaft diameter. The motor used here had a 3mm shaft.
    * These types of hobby motors can be found on eBay or at your local hobby store. [This](http://www.ebay.co.uk/itm/120RPM-12V-0-5A-High-Torque-Mini-Electric-DC-Geared-Motor/290912754915?_trksid=p2047675.c100011.m1850&_trkparms=aid%3D222007%26algo%3DSIC.MBE%26ao%3D1%26asc%3D25292%26meid%3D3328ae8d418844cdbd0718bd1c078b82%26pid%3D100011%26prg%3D10621%26rk%3D4%26rkt%3D10%26sd%3D271576830585) is the motor used here.
* **1x 5x3mm Motor Coupling**
    * This is to couple your DC Gearmotor to your M5 Threaded Rod. If you have a different shaft diameter, you will need a 5x_mm Motor Coupling.
    * This is probably the most difficult component to source, but eBay generally has a good selection. It is also possible to machine or 3D print a coupling yourself, but it will not have the same robustness as a flexible jaw coupling.
* **1x 200mm M5 Threaded Rod**
    * Look for high quality A2 or A4 stainless steel. Stiffness and precision machining are desirable. 
* **8x M3x8mm Hex Bolts**
* **2x M5 Nylon Hex Nuts**
    * Nylon hex nuts are preferable because of their low friction, but if you struggle to find them, then normal stainless steel ones will suffice
* **4x M5 Stainless Hex Nuts**
    * These can also be nylon. 
* **Araldite**
    * Or equivalent epoxy resin. We will need to glue plastic and stainless steel.
* **Electrical Wire**
    * The wire should be rated to over 1A. The wire used here was 7/0.2 (24AWG) 1.4A rated. 
    * It helps to have a few different colours!
* **Arduino + Motor Shield OR 12V Power Supply**
    * This system is designed to operate as a servomotor - ie. a linear actuator with feedback control. The output of the digital caliper can be fed into an Arduino (or similar microprocessor) which can then control the power of a motor shield driving the DC motor (potentially using a PID loop) to achieve desired positioning.
    * However, a simple benchtop power supply will be able to test the mechanical linear positioning system.
* **Cable Crimps and Connector Housings** (Optional)
    * Depending on how you want to connect the output from the digital caliper to your microprocessor, you may want some crimps and housings to make a simple connector. 
* **Heatshrink and Cable Braid** (Optional)
    * Useful for keeping wires looking neat and tidy, but not essential

### Other Requirements
* **3D Printer**
    * You will need a 3D printer to print crucial components required for the linear actuator. 
    * The printer used to print the components here was a MakerBot Replicator 2 printing PLA. 
    * The size of the printing platform needs to be at least 100x60mm to print the required components (this is allowing for space to print a support raft)

<img src=images/3dPrinter.png width=600>

* **Soldering Iron**
    * At least 25W
    * Ideally temperature adjustable, 370 degrees is around the temperature you want
* **M3 Tap**
* **Screwdrivers, Allen Keys etc**
* **Glue Gun** (Optional)
    * Useful for securing delicate solder connections, but not essential
* **Table/G Clamps** (Optional)
    * Useful for securing the work pieces when gluing

### Step 1 - Soldering the Motor Electrical Connections
Cut and strip two lengths wire of ~200mm each. These will connect the motor to the motor shield or power supply. A standard colour convention of Brown for +ve and Blue for -ve should be used. 

<img src=images/motorWires.png width=600>

Solder the brown and blue wires to the +ve and -ve terminals of the motor respectively. A ceramic capacitor can also be soldered between the terminals to reduce motor noise. 

<img src=images/motorSolder.png width=600>

It is nice to tidy up the cabling using heatshrink and cable braid. Here red and black Hellerman Sleeves have been used on the motor side. The wire ends have also been crimped using bootlace crimps for a more reliable connection when used with screw terminals. 

<img src=images/motorCable.png width=600>

### Step 2 - Disassembling the Digital Caliper
Remove any stickers on the digital caliper and remove any glue residue, workshop oil and grime from the calipers using a suitable solvent. Unscrew the four screws on the rear of the caliper retaining the screen assembly. 

<img src=images/caliperRear.png width=600>

Remove the screen carefully from the sliding carriage. Also unscrew the retaining piece on the far end of the calipers. This should allow the carriage to come off the end of the slide. There should be a brass strip which falls out when you take the carriage off *do not lose this*. Snap off the rod which may be attached to the carriage - this, the thumb wheel and the retaining piece are no longer required. 

<img src=images/caliperDisassembled.png width=600>

There are two pieces which need to be forcibly removed from the carriage and the screen outer casing. The section which protrudes from the right of the carriage on the image below should be removed. The carriage is made from hardened stainless steel, so this may require some elbow grease - try using a hacksaw first, but if this is difficult, then try a dremel or a guillotine. The thumb wheel retainer should be removed from the plastic casing - a Stanley knife should suffice. 

<img src=images/caliperMod.png width=600>

Here is what the two components should look like afterwards. 

<img src=images/caliperModComplete.png width=600>

Now, reassemble the digital caliper by sliding the carriage back onto the slide. There should be some slop, and a gap between the slide and the carriage, through which the brass strip should be reinserted as shown in the image below. You may have to loosen the small screws on the side of the carriage. Now tighten the screws again once the strip is fully inserted - this is a fine operation - too tight and the slider will stick, too loose and the brass strip will pop out. Be prepared for some trial and error and frustration! 

<img src=images/caliperReassemble.png width=600>

### Step 3 - Soldering the Digital Caliper Connections
Inspect the rear of the screen which you have disassembled from the carriage. There should be four more screws holding a small PCB in place. Remove these screws and carefully remove the PCB. 

<img src=images/caliperElectronics.png width=600>

Different caliper designs will very slightly in how the screen is connected to the PCB and the excact configuration of the buttons, but it should look something like this. Note, the white that you see on the plastic section is not the backgroud below, but the rear or the screen. The black square is foam padding which separates the screen and the PCB. 

<img src=images/caliperElectronicsDisassembled.png width=600>

Importantly, note the four solder connections on the left of the PCB. These are the digital outputs of the caliper. From left to right, they are +1.5V (Green), Clock (Purple), Data (White) and Ground (Black). Cut and strip ~200mm wire of each respective colour to solder onto the connections. 

<img src=images/caliperElectronicsSolder.png width=600>

Carefully solder each wire to its respective connection. This is a very delicate operation because the wires are so close togeter. A clamp, good lamp and an extra pair of hands will make your life much easier. Make sure that you have a solid connection for each wire - tug on it gently to check. Make sure that your blobs of solder do not accidentally connect neighbouring connections together. Also, be careful not to heat the wires for too long and melt the insulation - this could lead to wires shorting when you move the carriage.

<img src=images/caliperElectronicsSoldered.png width=600>

To protect the delicate connection and make sure it doesn't move during operation, use a glue gun to encase the solder connections in glue. You may have to trim the glue so that the PCB will fit back into the casing.

<img src=images/caliperElectronicsGlued.png width=600>

Carefully reassemble the PCB, screen and plastic casing. The plastic casing should have a removable cover where the solder connections are so that the wires can pass through. If there isn't a removable cover, then you will have to drill holes for the wires to pass through. 

<img src=images/caliperElectronicsComplete.png width=600>

You can choose to crimp the other end of the cables for an easy connection to the microprocessor. 

<img src=images/caliperCrimp.png width=600>

Finally, here's the completed screen assembly, cable braided and heatshrinked. 

<img src=images/caliperCable.png width=600>

### Step 4 - Printing the 3D Printed Components 

<img src=images/3dPrint.png width=600>

There are three components to print:
* A carriage which houses the hex nuts and is glued onto the reverse of the sliding screen on the digital caliper. The lead screw (threaded rod) drives this carriage.
* A motor mount which glues onto one end of the stationary slider of the digital caliper. This holds the motor fixed so that rotation of the lead screw will drive the carriage.
* A support bracket which glues onto the other end of the stationary slider. This holds the other end of the lead screw in place to reduce slop in the system. This also provides vertical support for the lead screw. 

Download the 3D printed Components from [here](dummy link).

<img src=images/3dPrintNozzle.png width=600>

The components have been provided in .stl format, and these files as printed on a MakerBot Replicator 2 using PLA were compatible with the particular components which we sourced. However, to accommodate different availability of components, it may be necessary for you to alter the dimensions of the 3D printed components, especially the motor mount, the exact sizing of which will depend on the particular gearmotor used. With different printers and different plastics, the tolerances will also change, and the exact sizing of the holes for the threaded rod and nylon nuts may need to be changed in order to ensure a snug fit. Be prepared to go through a few iterations of trial and error!

The components were originally designed using SolidWorks, and the source files have been provided. There is ongoing work to convert these files into the open source OpenSCAD format, and we apologise for using a format which is less than open-source friendly.

### Step 5 - Finishing and Gluing the 3D Printed Components

<img src=images/3dPrintComponents.png width=600>

Before gluing the 3D printed components, they need to be tapped. There are four holes on the carriage and four holes on the motor mount which should be tapped with an M3 tap. Make sure the thread is straight - a straight hole does necessarily mean a straight thread. 

Insert the M5 nylon nuts into the slots on the 3D printed carriage. They should go in with some resistance, and fit snugly. However, if you have to distort the screws to get them in, then it is too tight. Adjust the design of the 3D printed piece until you have a good fit.

Now is also a good time to check the clearances of the 5mm holes and make sure that the threaded rod will slide through with no resistance. If it is too tight, then clear out the hole by hand with a 5mm drill bit. 

Glue the carriage on first - there are cutouts for the screws, so aligh the holes on the rear of the carriage to the cutouts on the 3D printed piece. Apply a thin layer of epoxy on both pieces to be glued, press together firmly, and clamp securely. Check the alignment of the holes and edges before and after clamping. 

<img src=images/glueCarriage.png width=600>

In the image above, you can also see the end support glued on - it is advisable to glue the carriage first, so that it is less likely to glue the end support on the wrong side of the slider. The end support is symmetrical so there is no need to worry about orientation. The far edge should be aligned with the end of the slide. 

Here is the completed carriage. One side should be flush.

<img src=images/glueCarriageComplete.png width=600>

And the other should overhang slightly.

<img src=images/glueCarriageComplete2.png width=600>

Finally, glue on the motor mount. This should sit snugly on the end of the caliper, and the side should be flush with the side of the caliper. The exact positioning of this may need to be adjusted depending on the particular design of caliper and any modifications made to the mount. 

<img src=images/glueMotor.png width=600>

### Step 6 - Assembling the System

Attach the motor coupling to the motor shaft and screw the motor onto the motor mount using the M3 bolts. 

<img src=images/assembleMotor.png width=600>

Insert the M5 threaded rod through the end support at the end of the slide. The hole should correspond to where the nylon nuts are on the carriage. Put two M5 nuts onto the threaded rod and then screw it into the carriage until it comes out of the other side. You can also optionally insert a 5mm rod (or a M5 threaded rod) through the other hole in the support and insert it into the hole in the carriage. This can act as an optional external actuating rod. This should be retained by inserting two M3 bolts into the tapped holes. 

<img src=images/assembleEnd.png width=600>

Screw the threaded rod until a sufficiently long section protrudes from the other end of the carriage that it can be coupled to the motor. The coupling is shown here.

<img src=images/assembleCoupling.png width=600>

Screw the screen back onto the carriage. This should go on the opposite side to the 3D printed component. 

<img src=images/assembleScreen.png width=600>

Finally, screw two more nuts onto the threaded rod on the other side of the end support. Then the screws on each side of the end support against each other such that they retain the threaded rod and prevent any lateral movement. Make sure they are not so tight that they restrict the rotation though. 

<img src=images/assembleEndNuts.png width=600>

And voila! We have assembled a complete linear actuator. 

<img src=images/assembleComplete.png width=600>

Turn the motor by hand to check that it is rotating smoothly - if there is a lot of resistance, make sure the nuts are not overtightened, and that everything is aligned properly. Then connect the motor to a power supply or a motor shield and power on. The motor should have plenty of torque to turn the lead screw at even <5V. 

### Controlling the System and Potential Applicaitons

This system is designed to operate as a servomotor - ie. a linear actuator with feedback control. The output of the digital caliper can be fed into an Arduino (or similar microprocessor) which can then control the power of a motor shield driving the DC motor (potentially using a PID loop) to achieve desired positioning. 

The end user is free to determine how they wish to control the system. Included in this github is an arduino library which is able to read the input from the digital caliper and output it as a floating point number in mm. 

There is also a project also developed under the OpenLabTools initiative of an open source linear actuator controller, which is compatible with this system and can control up to four of such axes. The system has an in-built GUI and offers functions to home, jog and move a linear axis to absolute or relative positions. 

This low cost open source linear actuator can be used in a wide range of applications where 0.01mm precision is sufficient. These can include low cost microscopes and optical systems, precision machining and other automation applications. This project has merely been a proof of concept and further research is required to improve the mechanical performance of the system and to quantitatively determine its performance. 


*This project is part of the OpenLabTools initiative and was developed in the Cambridge University Engineering Department. For more information, please visit [www.openlabtools.org](www.openlabtools.org).*
