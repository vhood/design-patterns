# Design Patterns

## Navigation

- **Creational**  
  Provide client isolation from object creation
  - [Factory Method](#factory-method)
  - [Abstract Factory](#abstract-factory)
  - [Builder](#builder)
  - [Singleton](#singleton)

- **Structural**  
  Extend system capabilities without affecting class structures
  - [Decorator](#decorator)
  - [Facade](#facade)
  - [Adapter](#adapter)
  - [Composite](#composite)

- **Behavioral**  
  Regulate responsibilities and relationships between objects
  - [Strategy](#strategy)
  - [State](#state)
  - [Iterator](#iterator)
  - [Observer](#observer)
  - [Chain Of Responsibilities](#chain-of-responsibilities)
  - [Template Method](#template-method)
  - [Command](#command)
  - [Proxy](#proxy)
  - [Mediator](#mediator)
  - [Null Object](#null-object)

## How to read UML

Entity                                          | Description
:---------------------------------------------: | :------------------------------------------------------------------------
![class](/docs/img/class.png)                   | a class (top down: name, data, methods)
\-                                              | private
\+                                              | public
\#                                              | protected
![interface](/docs/img/interface.png)           | an interface or an abstract Class
![context](/docs/img/context.png)               | an example of interacting with a pattern
![context-arrow](/docs/img/context-arrow.png)   | how the interaction with the pattern goes
![pattern](/docs/img/pattern.png)               | a pattern or his conceptual part
![implementation](/docs/img/implementation.png) | interface implementation or inheritance
![aggregation](/docs/img/aggregation.png)       | the object on the right contains the object on the left through aggregation or composition
![composition](/docs/img/composition.png)       | The object on the right contains the object on the left through composition

## Creational

### Factory Method

![Factory-Method](/docs/img/patterns/Factory%20Method.png)

**Purpose**  
Provides the interface for creating objects without binding to the class of the object being created

| examples
| -
| TODO

**Note**:

- Factory function must return an object
- The responsibility for creating an object lies entirely with the object that implements the interface with the factory method
- The pattern provides the ability to perform operations before returning an object
- You can use the [Strategy](#strategy) pattern, where changing the strategy is changing the factory

**[Navigation ↑](#navigation)**

### Abstract Factory

![Abstract-Factory](/docs/img/patterns/Abstract%20Factory.png)

**Purpose**  
Provides the interface for creating a family of objects without specifying the specific classes of those families

| examples
| -
| TODO

**Note**:

- Abstract factory includes [factory methods](#factory-method)
- To comply with design principles, objects created by a factory must have strong cohesion (**not coupling**)
- You can create [Strategy](#strategy) changes to the family of objects

**[Navigation ↑](#navigation)**

### Builder

![Builder](/docs/img/patterns/Builder.png)

**Purpose**  
Divides the design of objects into stages and provides the interface for managing these stages

| examples
| -
| TODO

**Note**:

- The client doesn't interact with the stages directly
- The stages are not required to return an object
- The director must provide a function that manages the stages and returns an object
- The director can have several methods that control the stages
- You can use the [Strategy](#strategy) pattern, where a change in strategy will be a change in the strategy for building an object

**[Navigation ↑](#navigation)**

### Singleton

![Singleton](/docs/img/patterns/Singleton.png)

**Purpose**  
Ensures that the object being created is the only one in its class

| examples
| -
| TODO

**Note**:

- The pattern implies a static method that returns an object, instead of initializing the object. I don't find it anti-pattern.
- To comply with design principles, don't load the object with additional logic, the object should only provide itself with its state
- The pattern doesn't cope with simultaneous asynchronous access, it is recommended to create Singleton objects at the stage of project initialization

**[Navigation ↑](#navigation)**

## Structural

### Decorator

![Decorator](/docs/img/patterns/Decorator.png)

**Purpose**  
Provides the object interface with new functionality without changing it

| examples
| -
| TODO

**Note**:

- The client interacts with the target object and the decorator object using the same method of their interface
- The decorator object contains the target object and implements its interface based on its properties.
- The initialization of one object when initializing another object is not a Decorator, but a Dependency Injection.
- If you need to use an independent object of one interface under another interface, use the [Adapter](#adapter)

**[Navigation ↑](#navigation)**

### Facade

![Facade](/docs/img/patterns/Facade.png)

**Purpose**  
Provides a simplified interface for a complex system

| examples
| -
| TODO

**Note**:

- Facade can contain multiple methods with the same objects
- Objects on the properties of which the facade object relies on must have logical coherence and belong to the same system
- The names of the Facade methods should not coincide with the names of the methods of the objects used, hiding the connectivity with other objects

**[Navigation ↑](#navigation)**

### Adapter

![Adapter](/docs/img/patterns/Adapter.png)

**Purpose**  
Provides the ability for objects with different interfaces to work under the same interface

| examples
| -
| TODO

**Note**:

- The adapter object must implement the interface of the object to which you want to adapt
- The client interacts with the target object and the adapter object using the same method of their interface
- The adapter object is an independent object and can be used in the system under its own interface
- If you need to change a behavior of a method of the target object,
use the [Decorator](#decorator) pattern

**[Navigation ↑](#navigation)**

### Composite

![Composite](/docs/img/patterns/Composite.png)

**Purpose**  
Allows you to work with a tree of objects of one interface as with one object

| examples
| -
| TODO

**Note**:

- Composite is similar to the [Facade](#facade) pattern in that its method encapsulates the work of methods of linked objects
- A Composite object can contain components and other Composite objects as long as they implement the component interface, forming an object tree
- The method that processes the object tree is implemented using the [Iterator](#iterator) pattern

**[Navigation ↑](#navigation)**

## Behavioral

### Strategy

![Strategy](/docs/img/patterns/Strategy.png)

**Purpose**  
Encapsulates changing the behavior of the same object methods depending on the chosen strategy

| examples
| -
| TODO

**Note**:

- The strategy provides one of the options for implementing subtype polymorphism
- According to object-oriented thinking, the object must make decisions on its own, therefore, a change in strategy should be a request, not an order
- If you need to store strategies, use the [State](#state) pattern

**[Navigation ↑](#navigation)**

### State

![State](/docs/img/patterns/State.png)

**Purpose**  
Encapsulates changing the behavior of the same methods of an object depending on its state

| examples
| -
| TODO

**Note**:

- When creating an object with states, it is necessary to initialize the initial state
- The states are objects of the same interface
- Using composition, you can initialize all states of an object when it is created, but you can transfer them later using aggregation
- The pattern contains [Strategy](#strategy) for setting the state

**[Navigation ↑](#navigation)**

### Iterator

![Iterator](/docs/img/patterns/Iterator.png)

**Purpose**  
Provides an interface to iterate over data of various types

| examples
| -
| TODO

**Note**:

- An object with a collection to be iterated must implement the interface for creating an iterator object
- The pattern contains [Factory Method](#factory-method) for creating an iterator object
- The client doesn't interact with iterator objects

**[Navigation ↑](#navigation)**

### Observer

![Observer](/docs/img/patterns/Observer.png)

**Purpose**  
Provides a mechanism for tracking the state of objects

| examples
| -
| TODO

**Note**:

- Subscriber objects must be ready to receive information from the object to which they are subscribed without knowing it
- The object that stores subscribers decides when to notify them
- Subscriber objects can receive information from different objects of the same interface in the same way, implementing parametric polymorphism

**[Navigation ↑](#navigation)**

### Chain Of Responsibilities

![Chain Of Responsibilities](/docs/img/patterns/Chain%20Of%20Responsibilities.png)

**Purpose**  
Encapsulates the operation of a system based on sequential invocations of objects of the same interface into a invocation of a single object

| examples
| -
| TODO

**Note**:

- The "Chain Of Responsibilities" pattern is similar to the [Facade](#facade) pattern in that its method encapsulates the work of methods of connected objects
- Unlike the [Facade](#facade) pattern, the object accessed by the client implements a single interface with all participants
- Unlike the [Facade](#facade) pattern, the object to which the client is referring is
doesn't interact with all participants, but transfers control
- The pattern provides the ability to choose the beginning of the chain, but if the chain is a complex structure, implement it through the [Mediator](#mediator)

**[Navigation ↑](#navigation)**

### Template Method

![Template Method](/docs/img/patterns/Template%20Method.png)

**Purpose**  
Provides the interface for using an algorithm with the possibility of different implementation of steps

| examples
| -
| TODO

**Note**:

- The pattern implements the principle of encapsulating changes, separating them from permanent
- The template method is similar to the [Facade](#facade) pattern in that its method encapsulates the work of methods of connected objects
- The template method differs from the [Facade](#facade) pattern in that it can replace the behavior of objects with the standard behavior

**[Navigation ↑](#navigation)**

### Command

![Command](/docs/img/patterns/Command.png)

**Purpose**  
Provides the interface for executing commands with the ability to perform additional operations on them

| examples
| -
| TODO

**Note**:

- The commands are objects of the same interface
- You can use the [Strategy](#strategy) pattern to change a command
- The client works with the object in which the command is initialized and controlled

**[Navigation ↑](#navigation)**

### Proxy

![Proxy](/docs/img/patterns/Proxy.png)

**Purpose**  
Controls access to an object through a proxy object

| examples
| -
| TODO

**Note**:

- The Proxy pattern is very similar to the [Decorator](#decorator) pattern
- Unlike the [Decorator](#decorator) pattern, a proxy object can exist without a target object, replacing it in its absence
- Unlike the [Decorator](#decorator) pattern, a proxy object is not required to extend the functionality of a target object and can transfer control to it

**[Navigation ↑](#navigation)**

### Mediator

![Mediator](/docs/img/patterns/Mediator.png)

**Purpose**  
Takes responsibility for communication between components

| examples
| -
| TODO

**Note**:

- The client doesn't interact with mediator objects
- Components don't interact with each other
- The pattern provides the ability for components to change the mediator object
- The Mediator pattern is similar to the ["Chain Of Responsibilities"](#chain-of-responsibilities) in that after the client has accessed a series of events in which several objects can participate

**[Navigation ↑](#navigation)**

### Null Object

![Null Object](/docs/img/patterns/Null%20Object.png)

**Purpose**  
Provides an object with neutral behavior of interface methods

| examples
| -
| TODO

**Note**:

- An object with neutral state provides one of the exception handling options
- "Null Object" is obliged to implement the interface of the system, which needs neutral states

**[Navigation ↑](#navigation)**
