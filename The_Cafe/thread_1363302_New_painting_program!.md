---
title: "New painting program!"
date: 2009-12-24
forum: The Cafe
---

### Post by Zeemvel on 2009-12-24
Hi, I'm making a painting program, called "LodePaint". Its features are currently somewhere in between KolourPaint and Gimp. It's not finished yet, but could you give some feedback about it so I know if it works well and what the most missed features are? Thanks!

Manual is included.

It can be downloaded at the link below, and to install it, unzip it, make sure the file "LodePaint" is executable, and run it from a terminal. It should work in Ubuntu, but if it doesn't, try to install SDL and check if it works then. Also make sure to run it from a terminal so that the working directory is the one in which the files "buttons16.png" and "buttons32.png" are, otherwise it can't start up. And you need a hardware accelerated 3D video card with good drivers (MESA turns out to be too slow).

[http://members.gamedev.net/lode/projects/LodePaint/LodePaint_Linux.zip](http://members.gamedev.net/lode/projects/LodePaint/LodePaint_Linux.zip)

---

### Post by Psumi on 2009-12-24
Screenshots? Because I can't run the program: No 3D Drivers, since I really don't like using 3D anymore.

---

### Post by Zeemvel on 2009-12-24
Attached are some screenshots. Enjoy!

---

### Post by Psumi on 2009-12-24
> **Zeemvel said:**
> Attached is a screenshot.

THAT requires 3D Drivers?

LMAO, LOL, ROFLCOPTER!

---

### Post by Zeemvel on 2009-12-24
> **Psumi said:**
> THAT requires 3D Drivers?

LMAO, LOL, ROFLCOPTER!

Yep. I use OpenGL instead of GTK/Qt/... for the complete GUI, sorry this isn't a GUI app but a painting program running in a game engine so you need 3D drivers :).

---

### Post by RiceMonster on 2009-12-24
> **Zeemvel said:**
> Yep. I use OpenGL instead of GTK/Qt/... for the complete GUI, sorry this isn't a GUI app but a painting program running in a game engine so you need 3D drivers :).

Could you explain why you chose to do this?

---

### Post by Zeemvel on 2009-12-24
> **RiceMonster said:**
> Could you explain why you chose to do this?

I've got much more experience with OpenGL than with GTK or Qt. And GTK, as well as wxWidgets that uses GTK and thus is limited by GTK, frustrated me with some limitations on floating windows inside other windows. So I was just like, what the heck, let's use this GUI meant for computer games, for a painting program.

Advantages:

-more control over everything, any type of GUI element one can dream of can be made (including floating windows inside other windows, something that'd look like a Ribbon if I'd feel like it, etc...) without limitations
-alpha channel transparency is easy with OpenGL
-A texture representing a painting is also easy with OpenGL
-zooming in and out the painting goes quite smooth

Disadvantages:

-everything, even a file dialog, has to be designed from scratch so that is a lot of work

---

### Post by Psumi on 2009-12-24
> **Zeemvel said:**
> Disadvantages:

-everything, even a file dialog, has to be designed from scratch so that is a lot of work

Add two more:

- Can't use it on IBM T4# Laptops (3D is toooooooooo slow.)
- Can't use it without some propietary video drivers on some cards.

---

### Post by Zeemvel on 2009-12-24
Is there anyone with 3D drivers who'd like to test it?

This program works for me on a 7 year old Athlon PC with 256MB RAM and a Geforce3 card with only 64MB RAM in that card so it's not so that this program requires the *newest* 3D card or anything, it's just that with software emulated OpenGL it's too slow.

If you can play Nexuiz in your Linux, then you can run this too :)

---

### Post by YeOK on 2009-12-24
> **Zeemvel said:**
> Is there anyone with 3D drivers who'd like to test it?

This program works for me on a 7 year old Athlon PC with 256MB RAM and a Geforce3 card with only 64MB RAM in that card so it's not so that this program requires the *newest* 3D card or anything, it's just that with software emulated OpenGL it's too slow.

If you can play Nexuiz in your Linux, then you can run this too :)

I'll test it for you.

Edit:

Works well, it managed to crash Emerald theme manager, but thats not uncommon. Runs well and seems stable. It will need more features before I'd think of using it, but for a pre alpha its looking like a promising project. Do you have a site or url to bookmark for future updates ?

---

### Post by Zeemvel on 2009-12-24
There's no website or anything yet, but *if* this project turns out to be successful then you'll hear from it again :)

Since you mentioned that you'd like to see more features, what kind of features would you like to see?

---

### Post by YeOK on 2009-12-24
> **Zeemvel said:**
> There's no website or anything yet, but *if* this project turns out to be successful then you'll hear from it again :)

Since you mentioned that you'd like to see more features, what kind of features would you like to see?

The most obvious missing feature was the ability to open more than one image at once.

---

### Post by Psumi on 2009-12-24
> **YeOK said:**
> The most obvious missing feature was the ability to open more than one image at once.

Why? MSPaint doesn't open more than one file.

---

### Post by YeOK on 2009-12-24
> **Psumi said:**
> Why? MSPaint doesn't open more than one file.

I don't use MSPaint. Also, he asked me what I think is missing. In my opinion, its missing the ability to open more than one image at a time.

---

### Post by RiceMonster on 2009-12-24
> **Psumi said:**
> Why? MSPaint doesn't open more than one file.

...and that's a reason not to have that ability because?

---

### Post by Psumi on 2009-12-24
> **RiceMonster said:**
> ...and that's a reason not to have that ability because?

I still have yet to see a basic of basic functionality image editing program for linux.

---

### Post by RiceMonster on 2009-12-24
> **Psumi said:**
> I still have yet to see a basic of basic functionality image editing program for linux.

I don't think this is meant to be a basic image editing program.

Also, try KolourPaint.

---

### Post by Psumi on 2009-12-24
> **RiceMonster said:**
> I don't think this is meant to be a basic image editing program.

Also, try KolourPaint.

OP said **painting** program.

MSPaint is both a painting program and image editor of sorts.

---

### Post by RiceMonster on 2009-12-24
> **Psumi said:**
> OP said **painting** program.

MSPaint is both a painting program and image editor of sorts.

And you said **image editing** program. See blow.

> **Psumi said:**
> I still have yet to see a basic of basic functionality **image editing** program for linux.

---

### Post by Psumi on 2009-12-24
> **RiceMonster said:**
> And you said **image editing** program. See blow.

MSPaint is both though, and I said "basic of basic."

Meaning one that can only handle one image at a time.

---

### Post by Zeemvel on 2009-12-24
> **RiceMonster said:**
> I don't think this is meant to be a basic image editing program.

Also, try KolourPaint.

Actually, it's meant to be a painting program that is more like KolourPaint than like Gimp, but actually what I'm aiming for is to have something like the early versions of Paint Shop Pro (certainly not like the latest versions of it, which are meant for editing vacation photos). But having the ability to open multiple images, and to do operations like blending two images together, are planned for later.

Also, this painting program is aimed to drawing icons, textures for 2D games, pixel art, and such, and doing basic image operations like "emboss" and such. But it's NOT meant at all for professional graphics and printing (like Gimp and Photoshop are).

Since pixel art is so important in this program, it has such design choices like, the arrow keys move the mouse cursor one pixel, a separate color for left and right mouse button, snapping to pixels instead of allowing points in between, and (apart from a wide brush) a pen tool that is always exactly one pixel in size independent of brush size and softness sliders.

And I also hate how most painting program treat the alpha channel (they allow making the background transparent and drawing tools make it more opaque), so this program here allows drawing shapes, doing flood fill, etc... with an alpha channel that actually gives the pixels that alpha channel instead of only doing "opacity". Which is handy for RGBA textures in games.

And I like programming image filters and fractals so whenever I feel like adding one, it gets an extra one. Programs like KolourPaint and MS Paint never seem to get any extra filters...

EDIT: painting program or image editing program??? I didn't really make the distinction.

---

### Post by Zeemvel on 2009-12-24
> **cheapkites said:**
> Thanks all for contributing to this thread. Lots to read in this forum but I like it.

Very friendly of you to reply this in my thread, but did you make an account just for that? :)

---

### Post by Warpnow on 2009-12-24
```

chase@chase-desktop:~/Desktop/LodePaint_Linux$ ./LodePaint
PaintDebug Info: Starting LodePaint
PaintDebug Info: Loading persistent data
PaintDebug Info: Persistent data loaded
PaintDebug Info: Creating screen width: 1024 height: 700 fullscreen: 0 resizable: 1
info: initing SDL
info: SDL inited
info: initing screen
Error: Unable to set video: Could not create GL context
chase@chase-desktop:~/Desktop/LodePaint_Linux$ gdb LodePaint
GNU gdb (GDB) 7.0-ubuntu
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/chase/Desktop/LodePaint_Linux/LodePaint...(no debugging symbols found)...done.
(gdb) run
Starting program: /home/chase/Desktop/LodePaint_Linux/LodePaint 
[Thread debugging using libthread_db enabled]
PaintDebug Info: Starting LodePaint
PaintDebug Info: Loading persistent data
PaintDebug Info: Persistent data loaded
PaintDebug Info: Creating screen width: 1024 height: 700 fullscreen: 0 resizable: 1
info: initing SDL
info: SDL inited
info: initing screen
Error: Unable to set video: Could not create GL context

Program exited with code 01.
(gdb) 

```

---

### Post by hessiess on 2009-12-24
A resolution dependent painting program, great idea;) not everyone has a 1024*768 monitor you know, or even 4:3. wide-screen monitors are also becoming increasingly common.

About using OpenGL for the GUI, Blender also does this, though for good reason because it integrates extremely well with the rest of the application, and is also completely resolution independent. In the case of this painting program, as it is currently, there is no advantage over using one of the traditional GUI tool kits.

Also needs more features, i.e. tablet support.

---

### Post by Zeemvel on 2009-12-24
Tablet support, while very cool, is out of the question for this program I'm afraid. Unless something like SDL would support it.

But about the resolution dependence, are you sure it is resolution dependent? It was in the first stages of development, but shouldn't be now, it should be a resizable window. (it uses the "SDL_RESIZABLE" flag when creating the screen with SDL).

It remembers the window size of the previous time the program was quit, and the very first time it tries "1024*700", but I think even if that is too big the window should be resizable by the desktop manager.

---

### Post by aspiredfang on 2009-12-24
I'd like to say a good start for a brand new project, would be really nice to have a paint like program within *nix.

That you've chosen to use OpenGL is not really a criticism, this program embraces what OSS is all about. Someone who has an idea with a skill set and makes that idea to share with others, keep it up and kudos!

When/if this project matures, I could perhaps see it replacing GIMP for me as I don't need so much in an editor :)

---

### Post by hessiess on 2009-12-24
> **Zeemvel said:**
> Tablet support, while very cool, is out of the question for this program I'm afraid. Unless something like SDL would support it.

But about the resolution dependence, are you sure it is resolution dependent? It was in the first stages of development, but shouldn't be now, it should be a resizable window. (it uses the "SDL_RESIZABLE" flag)

Xmonad won't tile it and it does not open full screen by default. Though yes it is resizeable,sorry about that;)

Instead of assuming 1024*768, get the screen res and set the programs window size to whatever that is.

---

### Post by Zeemvel on 2009-12-24
> **hessiess said:**
> Xmonad won't tile it.

Well that sucks. I hope SDL 1.3's better resizable window support will fix that.

EDIT:

> **hessiess said:**
> Xmonad won't tile it and it does not open full screen by default. Though yes it is resizeable,sorry about that;)

Instead of assuming 1024*768, get the screen res and set the programs window size to whatever that is.

By default, the program does 1024*700, windowed. The 700 was chosen as first-time resolution (instead of 768!) specifically for laptops! Widescreen laptops often have 768 as height, and 68 is subtracted from that to allow some window decorations and desktop manager bars below/above it.

Now about getting the current desktop screen size: there's AFAIK, no multiplatform way to do that. But this is only about the resolution when starting the program the FIRST time! Once you've resized the window to something else, the program remembers that resolution and uses that resolution the next time you start it up. I don't see much difference between this behaviour, and for example a text editor, which, when you start it up, has the whatever screen resolution it feels like at that time and I often use "maximize" or resize the window anyway.

According to the w3schools statistics ([http://www.w3schools.com/browsers/browsers_display.asp](http://www.w3schools.com/browsers/browsers_display.asp)), 4% of the users has a resolution smaller than 1024*768. So 4% of users might get a window that is larger than his screen only the first time they start the program up, if their window manager doesn't already automatically decrease the size of the window...

Of course if it can create a crash or problem starting the program up, then it's a problem that must be fixed. I might add something where if creating the screen fails, it'll retry with 640*480 or so.

Once the program has ran successfully, it creates a text file in ~/.config/LodePaint. In there you can change the resolution too if needed, disable the "resizable" window option, and, try the "fullscreen" mode. Fullscreen mode only works for resolutions that work in games, like 1024*768 and such, but gives a bit the feeling of those old MS DOS painting programs :)

---

### Post by hessiess on 2009-12-24
> **Zeemvel said:**
> Well that sucks. I hope SDL 1.3's better resizable window support will fix that.

It may actually be a configuration in Xmonad, Ive bean having problems with it floating resizeable Quad-ren windows also. This is why I have bean intending to dump SDL and write a new minimal cross platform OpenGL layer using GLX/Win32 etc directly. Another reason is to enable multi-window support. 

You can find the screen resolution using the folwing code, though I haven't found any way of automatically adjusting for window bars etc yet. Would have thought that SDL would have had a way of doing that and GTK/QT manage some how.

```

const SDL_VideoInfo *screen_info = SDL_GetVideoInfo();

int screen_size_x = screen_info->current_w;
int screen_size_y = screen_info->current_h;

```

---

### Post by Zeemvel on 2009-12-24
Thanks, didn't know that, that's useful :)

---

### Post by phrostbyte on 2009-12-24
Did you make your own widget toolkit ontop of OpenGL?

---

### Post by Zeemvel on 2009-12-24
> **phrostbyte said:**
> Did you make your own widget toolkit ontop of OpenGL?

Yep. It was meant for buttons and menu's in games at first, but can also be used for other things.

---

### Post by RiceMonster on 2009-12-24
So I finally got a chance to test it. Everything seems to work, but one thing is there is A LOT of flickering during a window resize. I don't know if this is due to my graphics driver or not.

Interesting concept overall. I'll try it again in the future as well to see where you've gone with it.

---

### Post by johannes123 on 2010-02-23
I think people who compare this to Gimp (or MS Paint) are not really understanding the philosophy of the program. I think I like where this is going! The FFT filters are really cool btw.

---

### Post by DeadSuperHero on 2010-02-23
It looks oddly Amiga-like.

Me likey. :D

---

