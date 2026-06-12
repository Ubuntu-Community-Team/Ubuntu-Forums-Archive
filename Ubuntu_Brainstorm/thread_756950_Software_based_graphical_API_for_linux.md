---
title: "Software based graphical API for linux"
date: 2008-04-16
forum: Ubuntu Brainstorm
---

### Post by theubersmurf on 2008-04-16
So, I've thought about this a bit. If gamers, who in many cases build their own computers could get a free OS on which there were a lot of game development, such that they didn't have to fiddle around with WINE, would they migrate to linux? I'm not much of a linux user, I've installed it a good handful of times, but invariably I'm unwilling to devote to it the time it requires to master it, much less troubleshoot WINE for an installation of a windows game. That is problem number 1.

2. As I understand it, writing for Direct3D is much easier than writing for OpenGL, and also adds a good amount of functionality. So that if developers wanted to write a game for linux, it would be a much more significant effort than writing for Direct3D.

So I'm curious if anyone has given this any thought, the idea of creating a software based graphical API for Linux. I think it would give Linux a lot of traction if you could get a majority of gamers to dual boot...:KS...people who commonly use it to troubleshoot, give it a broader appeal to other developers outside of game developers as well.

---

### Post by smartboyathome on 2008-04-16
Direct3D is proprietary, only the owner can port it. Also, the only project working on something similar for problem 1 is ReactOS, and it is still alpha.

---

### Post by xelapond on 2008-04-16
Direct3D may be easier to code for, but it is no where near as capable as OpenGL.

---

### Post by theubersmurf on 2008-04-16
> **xelapond said:**
> Direct3D may be easier to code for, but it is no where near as capable as OpenGL.That may be, but it inhibits development because game developers don't want to deal with it.

---

### Post by theubersmurf on 2008-04-16
> **smartboyathome said:**
> Direct3D is proprietary, only the owner can port it. Also, the only project working on something similar for problem 1 is ReactOS, and it is still alpha.I realize that Direct3D is proprietary, but linux should have a graphical software based API to allow for ease of development and the expansion of games and multimedia. Not use direct3d, have it's own software graphical api, I think, if it got good, it would attract a lot of users.

---

### Post by smartboyathome on 2008-04-16
> **theubersmurf said:**
> I realize that Direct3D is proprietary, but linux should have a graphical software based API to allow for ease of development and the expansion of games and multimedia. Not use direct3d, have it's own software graphical api, I think, if it got good, it would attract a lot of users.

It does, and it is called OpenGL. I don't think it will be switching anytime soon. ;)

---

### Post by Feelout on 2008-04-16
Well, we have SDL + OpenGL for low-level graphics and many free libraries and engines like Allegro and Ogre. So, what`s the problem? Game development is possible on Linux and it`s not harder than on Windows - the only problem is lack of motivation.

By the way, OpenGL is not so complex. Things like ISOMEVERYLONGINTERFACE frighten me more :)

---

### Post by Steveway on 2008-04-16
It's a myth that OpenGL is harder than Direct3d. It's just different and it does things different so it seems harder for people switching from Direct3d.
The actual version of OpenGL 2.1 is at least as cappable as DirectX 10, and version 3 is allready not to far from beeing finshed. (Due to be released at the beginning of 2008.)

---

### Post by qamelian on 2008-04-16
> **Steveway said:**
> It's a myth that OpenGL is harder than Direct3d. It's just different and it does things different so it seems harder for people switching from Direct3d.
The actual version of OpenGL 2.1 is at least as cappable as DirectX 10, and version 3 is allready not to far from beeing finshed. (Due to be released at the beginning of 2008.)
Add to that the fact that OpenGL is usable on pretty much every OS platform that a user might have on a PC and you have a good argument why it should be the graphical standard to which games are written. Games using Direct3D might be Window-only, but OpenGL means that a portion of the development for other platforms such as Linux or Mac OS would not require "re-inventing the wheel" on each platform.

---

### Post by theubersmurf on 2008-04-16
> **Steveway said:**
> It's a myth that OpenGL is harder than Direct3d. It's just different and it does things different so it seems harder for people switching from Direct3d.
The actual version of OpenGL 2.1 is at least as cappable as DirectX 10, and version 3 is allready not to far from beeing finshed. (Due to be released at the beginning of 2008.)Perhaps I am misled then. 

Probably best to disregard this based on what has been said then.

---

### Post by theubersmurf on 2008-04-16
> **smartboyathome said:**
> It does, and it is called OpenGL. I don't think it will be switching anytime soon. ;)I thought OpenGL was hardware based.

---

### Post by CarpKing on 2008-04-16
> **theubersmurf said:**
> I thought OpenGL was hardware based.

I think it's up to the drivers whether it uses hardware or software.  I could be wrong, though.  But in any case, it's the same deal with Direct3D as far as I know.

---

### Post by bruce89 on 2008-04-16
OpenGL seems fine to me:

[PHP]
#include <GL/gl.h>
#include <GL/glu.h>
#include <GL/glut.h>

GLfloat xrot;
GLfloat yrot;

void
setup (void)
{
	glClearColor (1.0, 1.0, 1.0, 0.0);
	glEnable (GL_DEPTH_TEST);
}

/* Might be nice to use vertex arrays */
void
draw_cube (void)
{
	glBegin (GL_QUADS);
		/* Front */
		glColor3f (1.0, 0.0, 0.0);	/* Red */
		glVertex3f (-0.5, -0.5, -0.5);
		glVertex3f ( 0.5, -0.5, -0.5);
		glVertex3f ( 0.5,  0.5, -0.5);
		glVertex3f (-0.5,  0.5, -0.5);
		/* Back */
		glColor3f (0.0, 1.0, 0.0);	/* Green */
		glVertex3f ( 0.5, -0.5,  0.5);
		glVertex3f (-0.5, -0.5,  0.5);
		glVertex3f (-0.5,  0.5,  0.5);
		glVertex3f ( 0.5,  0.5,  0.5);
		/* Left */
		glColor3f (0.0, 0.0, 1.0);	/* Blue */
		glVertex3f (-0.5, -0.5,  0.5);
		glVertex3f (-0.5, -0.5, -0.5);
		glVertex3f (-0.5,  0.5, -0.5);
		glVertex3f (-0.5,  0.5,  0.5);
		/* Right */
		glColor3f (1.0, 1.0, 0.0);	/* Yellow */
		glVertex3f ( 0.5, -0.5, -0.5);
		glVertex3f ( 0.5, -0.5,  0.5);
		glVertex3f ( 0.5,  0.5,  0.5);
		glVertex3f ( 0.5,  0.5, -0.5);
		/* Top */
		glColor3f (1.0, 0.0, 1.1);	/* Magenta */
		glVertex3f (-0.5,  0.5, -0.5);
		glVertex3f ( 0.5,  0.5, -0.5);
		glVertex3f ( 0.5,  0.5,  0.5);
		glVertex3f (-0.5,  0.5,  0.5);
		/* Bottom */
		glColor3f (0.0, 1.0, 1.0);	/* Cyan */
		glVertex3f (-0.5, -0.5, -0.5);
		glVertex3f (-0.5, -0.5,  0.5);
		glVertex3f ( 0.5, -0.5,  0.5);
		glVertex3f ( 0.5, -0.5, -0.5);
	glEnd ();
}

void
display (void)
{
	glClear (GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
	glLoadIdentity ();

	glRotatef (xrot, 1.0, 0.0, 0.0);
	glRotatef (yrot, 0.0, 1.0, 0.0);

	draw_cube ();

	glutSwapBuffers ();
}

void
spin_cube (void)
{
	xrot += 0.2;
	yrot += 0.4;

	glutPostRedisplay ();
}

void
mouse (int button, int state, int x, int y)
{
	switch (button)
	{
		case GLUT_LEFT_BUTTON:
			if (state == GLUT_DOWN)
				glutIdleFunc (spin_cube);
			break;
		case GLUT_RIGHT_BUTTON:
			if (state == GLUT_DOWN)
				glutIdleFunc (NULL);
			break;
		default:
			break;
	}
}

int
main (int argc, char **argv)
{
	glutInit (&argc, argv);

	glutInitDisplayMode (GLUT_RGB | GLUT_DEPTH | GLUT_DOUBLE);
	glutInitWindowSize (600, 600);
	glutCreateWindow ("Cube");

	setup();

	glutDisplayFunc (display);
	glutMouseFunc (mouse);

	glutMainLoop ();

	return 0;
}
[/PHP]

---

