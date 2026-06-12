---
title: "Linux graphics and XGL , and the future"
date: 2006-01-04
forum: The Cafe
---

### Post by NoTiG on 2006-01-04
Its odd that nobody is talking about this, since it's such an important issue for the desktop. Not only does hardware acceleration add eye candy to users (which is oh so wanted) ... but it should make the desktop actually faster and relieve the cpu of the burden of drawing the desktop. 

recently there have been some changes in the XGL development, namely that Novell has released the source now making it more open. Read:

[http://linux.slashdot.org/linux/06/01/03/0416248.shtml?tid=104&tid=106](http://linux.slashdot.org/linux/06/01/03/0416248.shtml?tid=104&tid=106)

and

[http://www.osnews.com/comment.php?news_id=13154](http://www.osnews.com/comment.php?news_id=13154)

And here is an informative post i saw on slashdot:


> Two things:

1. XGL wasn't developed in-house for Novell.

XGL was started by independent free software programmers. Novell highered some of them and then took the developement 'in-house'.

It started off open, Novell paid some of them to concentrate on it on the 'inside', now they are openning it up again.

2. You don't understand the relationship between Xegl and XGL.

XGL is a _toy_, it's a pre-view. It's a beginning. It's forming the basis for future X servers, but it is not actually usefull itself.

XGL requires another X server to run on. Similar to Xnest.

Xegl is based on XGL (again started and worked on originally without any Novell involvement), it is a standalone X server that will actually be used.

You see one is useless without the other. XGL is worthless outside of developement. Xegl is worthless without the basis.

Xegl is called Xegl because it takes OpenGL and add the EGL extensions to it. These extensions were originally designed for embedded work, but can be used with a full-fledged OpenGL system like Linux has. What it does is allow OpenGL programs to send signals to change screen resolution and things like that. These extensions will 'fill out' the OpenGL API so that you can use it effectively for a basis of a standalone system.

Originally Linux's OpenGL stuff was like this. With original Mesa solo you didn't use X to run 3d accelerated applications. With things like GLX (open sourced from SGI) to 'mix' or manage OpenGL applications on a X server.

There still are some gaps though.. Indirect rendering isn't very hot, for instance. That is when you run a application remotely (X Windows is a networking protocol after all, like HTTP or whatnot) you can't get OpenGL acceleration working on it.

This, combined with other advances such as 'Modular X', 'X Damage', 'X composite', and 'XGL'/'xegl', is helping to move the X system from the 1980's era technology (were it is now) to the 2010's technology (where it will be in a couple more years).

Hopefully it will allow you to do things like display your desktop applications on your laptop or handheld (which it can do now) but also allow you to easily transfer applications between devices while they are running, and to display to display. All with nice acceleration with complex window managers. Oh and don't forget Vector-based graphics (which we will have with next releases of Gnome and KDE), which will be OpenGL themselves accelerated in a year or two.

EXA will help this a bit.

As X server switch over to EXA for the time being and applications utilize it's acceleration more and more.. this EXA stuff translates suprisingly well to OpenGL.

Also it will have the added benifit of moving X off of the hardware.

Right now with X.org's X server you have all this extra crap it has to do with hardware drivers and such. By moving to pure OpenGL then each OS can handle the protocol stack on themselves. You can have Linux framebuffer with Mesa-based DRI drivers, propriatory drivers or have software Mesa on Netbsd, some sort of weird embedded stuff, or have Window's OpenGL stuff.. It doesn't matter. Let the OS manage the hardware itself and run X windows on OpenGL, just like any other OpenGL application.

Right now we have Framebuffer, DRI, VGAcon, EXA and such that all have to fight over the hardware at the same time.

That's 4 independant drivers from multiple independant vendors.. some from DRI, some from Linux kernel, some from X.org, that all have to use the _same_peice_of_fucking_hardware.

Think about this:
1 peice of hardware, 4 drivers.

How many devices do you expect to function properly like that?

With OpenGL-based X server, then you have only one driver that can do everything. It can even do console if you want.. (although I don't expect Linux to drop vgacon as long as video cards support legacy vga mode)

Also if your a disapointed programmer wanting to work on X then I suggest you look strongly at XCB.
[http://xcb.freedesktop.org/wiki/](http://xcb.freedesktop.org/wiki/) [freedesktop.org]

This is a Xlib _replacement_.

You know how people bitch and moan about how Xlib sucks and how it's bloated and how it is full of legacy crap and so on and so forth?

Well this is the solution: XCB

It's new C bindings for the X protocol.

Xlib will hang around in very gutted form, rebuilt to run on top of XCB for backward binary compatability. Called Xlib/XCB

So don't worry about that

---

### Post by poofyhairguy on 2006-01-04
I promise its being discussed:

[http://doc.gwos.org/index.php/Poofyhairguy%27s_Eye_Candy_Report](http://doc.gwos.org/index.php/Poofyhairguy%27s_Eye_Candy_Report)

[http://ubuntuforums.org/showthread.php?t=111941](http://ubuntuforums.org/showthread.php?t=111941)

---

