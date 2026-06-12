---
title: "OpenGl and SDL problem"
date: 2009-11-06
forum: Ubuntu Dev Link Forum
---

### Post by Saxcore on 2009-11-06
Hi. I've had a look around, and can't seem to find this problem; although it's a very straight forward one. Also I hope this is the right forum!

I'm currently trying out SDL and OpenGL, and have written a simple C++ program to test them out. It compiles fine, and even runs fine when I replace [COLOR="Red"]SDL_OPENGL[/COLOR] in the [COLOR="Red"]SDL_SetVideoMode(..[/COLOR] line with [COLOR="Red"]0[/COLOR].

With the line in, however, it's failing. Would anyone know of any reasons why this might happen?


```
// Let's see if we can get OpenGL working!
// Compile with:
	// g++ test01.cpp `sdl-config --cflags --libs` -lGL -Wall -o TEST01

#include "SDL.h"
#include "SDL_opengl.h"
#include <iostream>

int main()
{
	// Set window size
	int WIDTH = 1024;
	int HEIGHT = 768;

	// Set up SDL / Window
	SDL_Init(SDL_INIT_EVERYTHING);
	SDL_Surface *base = NULL;
	if(	(base = SDL_SetVideoMode(WIDTH, HEIGHT, 32, SDL_OPENGL)) == NULL)
	{
		std::cout << "Error loading base window!\n";
		return 0;
	}

	// Set up OpenGL
	glClearColor(0,0,0,0);
	// ...projection
	glMatrixMode( GL_PROJECTION );
	glLoadIdentity();
	glOrtho( 0, WIDTH, HEIGHT, 0, -1, 1 );

	glMatrixMode( GL_MODELVIEW );
	glLoadIdentity(); 

	// Draw a square
	glBegin(GL_QUADS);
		//set colour
		glColor4f(1,1,1,1);
		//draw sqaure
		glVertex3f(25,25,0);
		glVertex3f(75,25,0);
		glVertex3f(75,75,0);
		glVertex3f(25,75,0);
	glEnd();

	SDL_Delay(2000);

	// Clean up SDL
	SDL_Quit();
	
	return EXIT_SUCCESS;
}
```

Cheers, Sam.

---

### Post by Saxcore on 2009-11-07
Ah. After a bit of research, I wasn't aware that certain OpenGL variables needed to be set with the SDL_GL_SetAttribute() function.

..while I still haven't got it working, I think all I'll need to do now is find out *which* variables I have to set. I'll report back once I've got it going!

---

