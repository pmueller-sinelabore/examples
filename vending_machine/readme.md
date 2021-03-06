# Vending Machine
## Overview

This example realizes a simple vending machine. The envisioned machine looks like this ![image in the doc folder](doc/vending.png).

To compile the example just call make. It is assumed that the code generator from sinelabore is installed (location see [Makefile](Makefile)).

After startup you can select a product "A", "B" or "C" by pressing one of theses buttons on your keyboard.

Then you have to insert the coins to pay for the product. Only 10Ct, 20Ct and 50Ct coins are supported. To "insert" them click "1","2" or "5" on your keyboard.

After you paid the product will be released and you receive back you change.

## Implementation

Most of the code is automatically generated from this UML file. ![classmodel.png in doc folder](doc/classmodel.png) 

It contains two state machines and an activity diagram. The state machines receive events from a message queue (see lib folder) and can also send messages to other state machines. This is a well known design pattern to decouple objects. A timer service (see lib folder) provides basic timer services that can be used from the state machines to realize delays or repetitive activities.


### Product Store State Machine

The "product_store_sm" implements a simple product store containing the goods. It is responsible to release the products by turning on the motor etc.

![sm.png in doc folder](doc/sm.png)

### Vending Machine
This is the controller machine keeping things together.

![ui.png in doc folder](doc/ui.png)

### Change Algorithm

This is a simple algorithm modeled with the help of an activity diagram to release the right amount of money if the user overpaid. It takes care if one coin type is empty.

![change_algorithm.png in doc folder](doc/change_algorithm.png)
