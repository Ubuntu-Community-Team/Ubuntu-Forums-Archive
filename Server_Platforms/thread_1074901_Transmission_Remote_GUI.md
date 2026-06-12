---
title: "Transmission Remote GUI"
date: 2009-02-19
forum: Server Platforms
---

### Post by Master One on 2009-02-19
I am running the 64bit version of Ubuntu Intrepid on my workstation, and I just downloaded the [transmission-remote-gui](http://code.google.com/p/transmisson-remote-gui/) 0.95 i386 binary, to connect to my headless FreeNAS server running transmission-headless 1.42.

It works, but I am now wondering, if/how it is possible to compile that application from source, to get a native 64bit binary, since it is developed using Lazarus RAD and Free Pascal compiler.

Anybody already tried that? Or can anybody with the proper knowledge please create Ubuntu packages?

---

### Post by cariboo on 2009-02-19
Why not create a bug on [Launchpad]("https://bugs.launchpad.net/") asking for some one to package the program.

If the devs don't know there is a need for something, they can't do anything about it.

Jim

---

### Post by HermanAB on 2009-02-19
Simpler method:
Install ssh-server then connect with:
$ ssh user@server gnome-panel

and go click happy.

Cheers,

Herman

---

### Post by Master One on 2009-02-20
> **cariboo907 said:**
> Why not create a bug on [Launchpad]("https://bugs.launchpad.net/") asking for some one to package the program. If the devs don't know there is a need for something, they can't do anything about it.
Good idea, nevertheless I was hopeing for some advice to be able to compile that app myself.

---

### Post by songshu on 2009-02-20
the souce code should be available, if you have that then just untar it and there is usually a readme file that will show you the steps to take, like configure make and make install

---

### Post by Master One on 2009-02-20
And that's the problem, there is no info in the [archive](http://transmisson-remote-gui.googlecode.com/files/transgui-0.95-src.zip) on how to compile that app, there is no makefile since it's "developed using Lazarus RAD and Free Pascal compiler", and I have no clue on how to deal with the available files in the source archive.

---

