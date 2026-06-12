---
title: "so what exactly does it mean when you say DirectX and/or OpenGL are API's?"
date: 2007-03-05
forum: The Cafe
---

### Post by billdotson on 2007-03-05
API's are application programming interfaces but what exactly does an API do?

From my interpretation of what I have read an API such as DirectX is simply something that consists of libraries and such and when a game or another program written to use DirectX calls on the API the API gives the program what it wants.  So if a game is written in C++ the developers call for the DirectX API to complete certain processes for the application like rendering a 3D figure or something similar.

Am I correct in saying that an API is just a program/library/something else that simply communicates with the source code or something of that nature.  I do not completely understand how the whole API thing works.  I was just using DirectX and OpenGL because those are commonly referred to.. like for ex:  "Microsoft has included the DirectX10 API for use only with Windows Vista"

---

### Post by Mathiasdm on 2007-03-05
The API is what's used to communicate between programmer and program.

DirectX and OpenGL do a lot of things, but the programmer needs to be able to tell them: "I want you to do this."

An API is basically a list with commands you can put in your program to tell those programs what to do.

For example: a programmer wants to create a blue square on the screen.

In the API, there's information that says:

```

printShape(Color COLOR, Shape SHAPE);

COLOR: {black, white, blue, green, yellow, red}
SHAPE: {square, circle, triangle, icosahedron}

```

That way, the program can include the following text in his program:
```
printShape(blue, square);
```
Of course, it's a lot more complicated, but that's the basic idea.

---

### Post by billdotson on 2007-03-05
so to use DOS terminology the API is a bunch of external programs that can be used to add more functionality to a program or make the program usable at all?

So for instance in a programming language there is no module/library to render a 3D image.. a dev would simply call on OpenGL or DirectX (actually Direct3D) to render that image for them?  

That kindof makes sense.  So the API in a way is some sort of run-time environment for that program (game specifically)?

---

### Post by Tomosaur on 2007-03-05
OpenGL and Direct3D talk to the hardware which handles video and images - ie - the graphics card. Hardware programming is complex - and if OpenGL or Direct3d didn't exist - then games would take a LOT longer to come out, and the quality would vary much more than it currently does. APIs like OpenGL and D3d take the strain off the programmer, and free him/her up to program the rest of the game.

As someone already said - the API is just a 'wrapper' around other code. This code will do lots of work to draw something on the screen. The name of this block of code can be used by the programmer, rather than him/her having to write out all of the necessary code his/herself. So, let's say the code inside the actual OpenGL API looks like this:
```

int draw_square(int x, int y, int with,int height){
  //100 lines of code talking directly to the video hardware
}

```

Then the programmer only has to put a call to the above code inside his program:
```

//Include openGL libraries in the program
#include <ogl.h>

int main(){
  draw_square(5,20,20,20);
  return 0
}

```.

As you can see, this drastically cuts down on the amount of code the programmer has to write.

It also means that everyone can take advantage of great new techniques. If the people who maintain the OpenGL libraries discover how to say - make in-game water look very realistic without taking a massive hit on game performance, then they can include it in the OpenGL API and then every games programmer can have awesome looking water. This is much better than each programmer having to figure out how to do it on their own - thus meaning that graphics capabilities of games improve in a more uniform manner.

---

