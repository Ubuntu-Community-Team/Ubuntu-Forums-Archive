---
title: "What is the tiniest Window Manager in existence for Linux?"
date: 2009-11-19
forum: The Cafe
---

### Post by hoppipolla on 2009-11-19
I was wondering about this because I wanted one that I could play games on under Cedega, and my first thoughts were awesome, Fluxbox, TWM etc etc, just to give my pc the easiest time possible and offset the (possibly small) performance hit of playing games emulated.

But that got me thinking. What is the smallest window manager out there? Is there ANYTHING smaller than TWM? o.O

Hoppi :)

---

### Post by SunnyRabbiera on 2009-11-19
CLI?

:D

Maybe ratpoison

---

### Post by RiceMonster on 2009-11-19
TinyWM. It's only 50 lines of code or something like that.

Edit: Here's the code:

```

/* TinyWM is written by Nick Welch <mack@incise.org>, 2005.
 *
 * This software is in the public domain
 * and is provided AS IS, with NO WARRANTY. */

#include <X11/Xlib.h>

#define MAX(a, b) ((a) > (b) ? (a) : (b))

int main()
{
    Display * dpy;
    Window root;
    XWindowAttributes attr;
    XButtonEvent start;
    XEvent ev;

    if(!(dpy = XOpenDisplay(0x0))) return 1;

    root = DefaultRootWindow(dpy);

    XGrabKey(dpy, XKeysymToKeycode(dpy, XStringToKeysym("F1")), Mod1Mask, root,
            True, GrabModeAsync, GrabModeAsync);
    XGrabButton(dpy, 1, Mod1Mask, root, True, ButtonPressMask, GrabModeAsync,
            GrabModeAsync, None, None);
    XGrabButton(dpy, 3, Mod1Mask, root, True, ButtonPressMask, GrabModeAsync,
            GrabModeAsync, None, None);

    for(;;)
    {
        XNextEvent(dpy, &ev);
        if(ev.type == KeyPress && ev.xkey.subwindow != None)
            XRaiseWindow(dpy, ev.xkey.subwindow);
        else if(ev.type == ButtonPress && ev.xbutton.subwindow != None)
        {
            XGrabPointer(dpy, ev.xbutton.subwindow, True,
                    PointerMotionMask|ButtonReleaseMask, GrabModeAsync,
                    GrabModeAsync, None, None, CurrentTime);
            XGetWindowAttributes(dpy, ev.xbutton.subwindow, &attr);
            start = ev.xbutton;
        }
        else if(ev.type == MotionNotify)
        {
            int xdiff, ydiff;
            while(XCheckTypedEvent(dpy, MotionNotify, &ev));
            xdiff = ev.xbutton.x_root - start.x_root;
            ydiff = ev.xbutton.y_root - start.y_root;
            XMoveResizeWindow(dpy, ev.xmotion.window,
                attr.x + (start.button==1 ? xdiff : 0),
                attr.y + (start.button==1 ? ydiff : 0),
                MAX(1, attr.width + (start.button==3 ? xdiff : 0)),
                MAX(1, attr.height + (start.button==3 ? ydiff : 0)));
        }
        else if(ev.type == ButtonRelease)
            XUngrabPointer(dpy, CurrentTime);
    }
}
```

---

### Post by hoppipolla on 2009-11-19
Wow, that really is tiny!

Im not sure if its possible to beat 50 lines of code! lol

---

### Post by sertse on 2009-11-19
tinywm wins, but I think dwm takes it for one that is actively maintained and has a decent user base.

---

### Post by falconindy on 2009-11-19
The smallest is none at all. Run your app on a separate X server. I've got a script called newX that looks like this:
```
#!/bin/bash
DISPLAY=:1
X :1 -ac -terminate &
sleep 2
$*
```
so running `newX <application>` would launch a new X server with only your application running on it. It'll use the next available virtual console, so if you use ctrl-alt-f7 to get back to your desktop from a TTY, the new X server will be ctrl-alt-f8.

---

### Post by Exodist on 2009-11-19
TinyWM = Winner.

Other light WMs I like are.. [Windowmaker]("http://www.windowmaker.info/")  and [Afterstep]("http://www.afterstep.org/index.php")

---

### Post by Mike'sHardLinux on 2009-11-19
I usually don't bother with trying to use the most efficient window manager since modern PCs usually have plenty of horsepower, but AfterStep sure does look interesting. The screen shots have quite a bit more eye candy than I am used to seeing on that type of system. 

[http://www.afterstep.org/screenshots/screenshot.glass.jpg](http://www.afterstep.org/screenshots/screenshot.glass.jpg)

---

### Post by phrostbyte on 2009-11-20
> **falconindy said:**
> The smallest is none at all. Run your app on a separate X server. I've got a script called newX that looks like this:
```
#!/bin/bash
DISPLAY=:1
X :1 -ac -terminate &
sleep 2
$*
```
so running `newX <application>` would launch a new X server with only your application running on it. It'll use the next available virtual console, so if you use ctrl-alt-f7 to get back to your desktop from a TTY, the new X server will be ctrl-alt-f8.

++ 

Most people don't realize that X will happily run without a WM. I do this to make VM sessions, a session which "boots" into an OS, by writing a session which calls VBoxSDL.

---

### Post by K.Mandla on 2009-11-20
Musca might be interesting to you. Not the smallest, but very small all the same.  

[http://aerosuidae.net/musca](http://aerosuidae.net/musca)

---

### Post by Irihapeti on 2009-11-20
> **K.Mandla said:**
> Musca might be interesting to you. Not the smallest, but very small all the same.  

[http://aerosuidae.net/musca](http://aerosuidae.net/musca)

Umm... Link gives 400 Bad Request.

---

### Post by m.rankovic on 2009-11-20
[http://aerosuidae.net/musca/](http://aerosuidae.net/musca/)

---

### Post by cdwillis on 2009-11-20
My first thought was twm ([http://en.wikipedia.org/wiki/Twm](http://en.wikipedia.org/wiki/Twm)), but TinyWM sounds like it has twm beat. :p

---

### Post by 3rdalbum on 2009-11-20
I had this idea a while ago. Give Wine more resources by running Openbox instead of Gnome.

Result: I discovered that, for some reason, some Wine programs don't work properly outside Gnome. This interested me but I never got a chance to play around and work it out.

---

### Post by RabbitWho on 2009-11-20
> **RiceMonster said:**
> TinyWM. It's only 50 lines of code or something like that.

Edit: Here's the code:

```

/* TinyWM is written by Nick Welch <mack@incise.org>, 2005.
 *
 * This software is in the public domain
 * and is provided AS IS, with NO WARRANTY. */

#include <X11/Xlib.h>

#define MAX(a, b) ((a) > (b) ? (a) : (b))

int main()
{
    Display * dpy;
    Window root;
    XWindowAttributes attr;
    XButtonEvent start;
    XEvent ev;

    if(!(dpy = XOpenDisplay(0x0))) return 1;

    root = DefaultRootWindow(dpy);

    XGrabKey(dpy, XKeysymToKeycode(dpy, XStringToKeysym("F1")), Mod1Mask, root,
            True, GrabModeAsync, GrabModeAsync);
    XGrabButton(dpy, 1, Mod1Mask, root, True, ButtonPressMask, GrabModeAsync,
            GrabModeAsync, None, None);
    XGrabButton(dpy, 3, Mod1Mask, root, True, ButtonPressMask, GrabModeAsync,
            GrabModeAsync, None, None);

    for(;;)
    {
        XNextEvent(dpy, &ev);
        if(ev.type == KeyPress && ev.xkey.subwindow != None)
            XRaiseWindow(dpy, ev.xkey.subwindow);
        else if(ev.type == ButtonPress && ev.xbutton.subwindow != None)
        {
            XGrabPointer(dpy, ev.xbutton.subwindow, True,
                    PointerMotionMask|ButtonReleaseMask, GrabModeAsync,
                    GrabModeAsync, None, None, CurrentTime);
            XGetWindowAttributes(dpy, ev.xbutton.subwindow, &attr);
            start = ev.xbutton;
        }
        else if(ev.type == MotionNotify)
        {
            int xdiff, ydiff;
            while(XCheckTypedEvent(dpy, MotionNotify, &ev));
            xdiff = ev.xbutton.x_root - start.x_root;
            ydiff = ev.xbutton.y_root - start.y_root;
            XMoveResizeWindow(dpy, ev.xmotion.window,
                attr.x + (start.button==1 ? xdiff : 0),
                attr.y + (start.button==1 ? ydiff : 0),
                MAX(1, attr.width + (start.button==3 ? xdiff : 0)),
                MAX(1, attr.height + (start.button==3 ? ydiff : 0)));
        }
        else if(ev.type == ButtonRelease)
            XUngrabPointer(dpy, CurrentTime);
    }
}
```



That's so adorable! Awwwwwwwwwwwwwwwwwwwwww

---

### Post by Tibuda on 2009-11-20
open a xterm session from GDM/KDM and start your apps from there without WM.

you need to run a network daemon (wicd-client or nm-applet) before launching an app that uses the internet.

---

### Post by hoppipolla on 2009-11-20
> **RabbitWho said:**
> That's so adorable! Awwwwwwwwwwwwwwwwwwwwww

hahaha :)

> **danielrmt said:**
> open a xterm session from GDM/KDM and start your apps from there without WM.

you need to run a network daemon (wicd-client or nm-applet) before launching an app that uses the internet.

oo that's VERY smart I never thought of this kinda because I didn't know it was possible! Nice one I'll try this too :)

---

### Post by RiceMonster on 2009-11-20
The thing about running with no WM though, is that you can't move or resize windows. Still fun to try, none the less.

---

### Post by Tibuda on 2009-11-20
> **RiceMonster said:**
> The thing about running with no WM though, is that you can't move or resize windows. Still fun to try, none the less.

True, but this don't matter when you are playing a full-screen game, which is why hoppipolla wants a light WM.

---

### Post by darkksyde on 2009-11-20
TinyWM i believe

---

### Post by Psumi on 2009-11-20
TinyWM does not even run in Ubuntu 9.10:

```
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  10
  Current serial number in output stream:  12
```

---

### Post by hoppipolla on 2009-11-20
> **danielrmt said:**
> True, but this don't matter when you are playing a full-screen game, which is why hoppipolla wants a light WM.

yeah, that's why I was considering it :)

As long as it plays FEAR, I'm happy ^_^

---

### Post by mmix on 2009-11-20
try to build one with this library, if size does matter.
[http://sourceforge.net/projects/asmlibx/](http://sourceforge.net/projects/asmlibx/)

sawman does not use Xorg, but directfb.
[http://www.directfb.org/index.php?path=Platform%2FSaWMan](http://www.directfb.org/index.php?path=Platform%2FSaWMan)

---

### Post by Naiki Muliaina on 2009-11-20
> **Psumi said:**
> TinyWM does not even run in Ubuntu 9.10:


Ahh poops :(

---

### Post by chris200x9 on 2009-11-20
> **mmix said:**
> 
sawman does not use Xorg, but directfb.
[http://www.directfb.org/index.php?path=Platform%2FSaWMan](http://www.directfb.org/index.php?path=Platform%2FSaWMan)

on a similar not got it beat [http://brain-dump.org/projects/dvtm/](http://brain-dump.org/projects/dvtm/) :p

---

### Post by mmix on 2009-11-20
FBUI is kernel built-in graphic system

[http://home.comcast.net/~fbui/](http://home.comcast.net/~fbui/)

> 

FBUI, or FrameBufferUI, is a small, in-kernel graphical user interface for Linux. It works only with kernel 2.6.9, although I've gotten it partially working with 2.6.31.

A summary of its key features:

    * It is very small, about 50kB.
    * It lives inside the Linux kernel, which places a natural limit on GUI bloat.
    * It permits multiple programs to share the framebuffer by letting each have graphical windows.
    * Each program may have multiple windows.
    * Windows may overlap, and be moved, resized, raised, lowered etc.
    * There can be windows on each virtual console.
    * Program interaction with FBUI is via a small set of system calls (ioctls).
    * Drawing primitives now support transparency.
    * It includes a small library libfbui to make using FBUI easier, and it includes an image-manipulation library and a font library. 


Item  	 FBUI 0.11.0(in kB) 	X-Windows / XFree86 (in kB)
Core software 	~50 	1710
Library software 	~30 	1370 (just Xlib; required)
Panel-style window manager program 	46½ (fbpm / static link) 	not available
Conventional window manager 	41 (fbwm* / static link) 	145 (twm / dynamic link)
Terminal emulator program 	73 (fbterm / static link) 	247 (xterm / dynamic link)
Analog clock program size 	43½ (fbclock / static link) 	29 (xclock / dynamic link)
Simple calculator program size 	43½ (fbcalc / static link) 	? (xcalc / dynamic link)
JPEG/TIFF viewer 	60 (fbview / static link) 	962 (xv / dynamic link) 

---

### Post by ajy0852 on 2009-11-20
> **Psumi said:**
> TinyWM does not even run in Ubuntu 9.10:

```
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  10
  Current serial number in output stream:  12
```

I really can't help with this, but I can say that I just installed it from the repos and it seems to work fine.

---

### Post by hoppipolla on 2009-11-20
> **ajy0852 said:**
> I really can't help with this, but I can say that I just installed it from the repos and it seems to work fine.

It fails to run on mine too (Ubuntu Karmic using KDM :( )

---

### Post by RiceMonster on 2009-11-20
I compiled and ran it on Arch. It basically just lets you move and resize windows, that's it. There's no window borders or anything. It's fun to try, though.

---

### Post by MisfitI38 on 2009-11-20
Tiniest while still being usable is dwm.

---

### Post by BuffaloX on 2009-11-20
> **hoppipolla said:**
> I was wondering about this because I wanted one that I could play games on under Cedega, and my first thoughts were awesome, Fluxbox, TWM etc etc, just to give my pc the easiest time possible and offset the (possibly small) performance hit of playing games emulated.


Cedega isn't an emulator, problem solved.

---

### Post by hoppipolla on 2009-11-20
> **BuffaloX said:**
> Cedega isn't an emulator, problem solved.

well, you know what I mean. Usually you do get a slight performance hit don't you?

---

### Post by BuffaloX on 2009-11-21
Sometimes you do, but sometimes it's actually slightly faster.

---

### Post by Rodney9 on 2009-11-21
How 'bout [Blackbox]("http://blackboxwm.sourceforge.net/AboutBlackbox")

---

### Post by frenchn00b on 2009-11-21
> **RiceMonster said:**
> TinyWM. It's only 50 lines of code or something like that.

Edit: Here's the code:

```

/* TinyWM is written by Nick Welch <mack@incise.org>, 2005.
 *
 * This software is in the public domain
 * and is provided AS IS, with NO WARRANTY. */

#include <X11/Xlib.h>

#define MAX(a, b) ((a) > (b) ? (a) : (b))

int main()
{
    Display * dpy;
    Window root;
    XWindowAttributes attr;
    XButtonEvent start;
    XEvent ev;

    if(!(dpy = XOpenDisplay(0x0))) return 1;

    root = DefaultRootWindow(dpy);

    XGrabKey(dpy, XKeysymToKeycode(dpy, XStringToKeysym("F1")), Mod1Mask, root,
            True, GrabModeAsync, GrabModeAsync);
    XGrabButton(dpy, 1, Mod1Mask, root, True, ButtonPressMask, GrabModeAsync,
            GrabModeAsync, None, None);
    XGrabButton(dpy, 3, Mod1Mask, root, True, ButtonPressMask, GrabModeAsync,
            GrabModeAsync, None, None);

    for(;;)
    {
        XNextEvent(dpy, &ev);
        if(ev.type == KeyPress && ev.xkey.subwindow != None)
            XRaiseWindow(dpy, ev.xkey.subwindow);
        else if(ev.type == ButtonPress && ev.xbutton.subwindow != None)
        {
            XGrabPointer(dpy, ev.xbutton.subwindow, True,
                    PointerMotionMask|ButtonReleaseMask, GrabModeAsync,
                    GrabModeAsync, None, None, CurrentTime);
            XGetWindowAttributes(dpy, ev.xbutton.subwindow, &attr);
            start = ev.xbutton;
        }
        else if(ev.type == MotionNotify)
        {
            int xdiff, ydiff;
            while(XCheckTypedEvent(dpy, MotionNotify, &ev));
            xdiff = ev.xbutton.x_root - start.x_root;
            ydiff = ev.xbutton.y_root - start.y_root;
            XMoveResizeWindow(dpy, ev.xmotion.window,
                attr.x + (start.button==1 ? xdiff : 0),
                attr.y + (start.button==1 ? ydiff : 0),
                MAX(1, attr.width + (start.button==3 ? xdiff : 0)),
                MAX(1, attr.height + (start.button==3 ? ydiff : 0)));
        }
        else if(ev.type == ButtonRelease)
            XUngrabPointer(dpy, CurrentTime);
    }
}
```


you shall use fbdev instead of xorg

and use JWM
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8287684](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8287684)

---

### Post by frenchn00b on 2009-11-21
> **Rodney9 said:**
> How 'bout [Blackbox]("http://blackboxwm.sourceforge.net/AboutBlackbox")

nope 


vtwm , twm , and jwm are faster and lighter than blackbox, by far.

---

### Post by frenchn00b on 2009-11-21
> **hoppipolla said:**
> I was wondering about this because I wanted one that I could play games on under Cedega, and my first thoughts were awesome, Fluxbox, TWM etc etc, just to give my pc the easiest time possible and offset the (possibly small) performance hit of playing games emulated.

But that got me thinking. What is the smallest window manager out there? Is there ANYTHING smaller than TWM? o.O

Hoppi :)

KDE  (joke) and [TWIN ]("http://yellowprotoss.ye.funpic.org/website/twin/")

---

### Post by Magnesium on 2009-11-21
Might I suggest Openbox? That's what I use on my 8-year-old laptop (see my sig) and it flies. Perhaps there are even smaller ones out there, but I've found that Openbox is remarkably fast, and still has enough features to be usable.

Mg

---

### Post by &#32 Greg on 2009-11-21
Evilwm is another one to add on to the list of very tiny ones.

---

### Post by RiceMonster on 2009-11-21
> **Greg said:**
> Evilwm is another one to add on to the list of very tiny ones.

Yes, that may be even smaller than dwm.

---

### Post by Naiki Muliaina on 2009-11-23
From the TinyWM website, some unscientific study into Window Manager sizes. Interesting lil table  ^^

[U][B][URL="http://incise.org/not-so-tiny-window-managers.html"]
Link to an un-scientific comparison[/URL][/B][/U]

---

### Post by Exodist on 2009-11-23
> **Rodney9 said:**
> How 'bout [Blackbox]("http://blackboxwm.sourceforge.net/AboutBlackbox")
That was another one I was trying to remember in the lines of AStep, WMaker and Fluxbox.

---

