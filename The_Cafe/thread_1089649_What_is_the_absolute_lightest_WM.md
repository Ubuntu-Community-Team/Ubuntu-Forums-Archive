---
title: "What is the absolute lightest WM?"
date: 2009-03-07
forum: The Cafe
---

### Post by NintendoTogepi on 2009-03-07
Obviously this knocks out GNOME, KDE, XFCE, even some of the lighter ones like LXDE and ICEWM...so which is the absolute lightest WM?

---

### Post by izizzle on 2009-03-07
Try evilwm. [http://www.6809.org.uk/evilwm/](http://www.6809.org.uk/evilwm/)

---

### Post by kk0sse54 on 2009-03-07
DWM, Ratpoison, antiWM, evilwm, probably something along those lines

---

### Post by Rokurosv on 2009-03-07
I think that in terms of funtionality and simplicity JWM is pretty good and lightweight. 
I personally like StumpWM.

---

### Post by Naiki Muliaina on 2009-03-07
Ratpoisons good ^^

---

### Post by jomiolto on 2009-03-07
[TinyWM]("http://incise.org/tinywm.html").

---

### Post by gnomeuser on 2009-03-07
[50kb - I win](http://home.comcast.net/~fbui/)

[no I beat myself 27kb](http://home.comcast.net/~fbui/fwe.html)

I dare you to find anything less bloated

---

### Post by jomiolto on 2009-03-07
> **gnomeuser said:**
> [50kb - I win](http://home.comcast.net/~fbui/)

[no I beat myself 27kb](http://home.comcast.net/~fbui/fwe.html)

I dare you to find anything less bloated

I think that 27kB is about the same as [dwm]("http://www.suckless.org/dwm/").

But TinyWM is only about 8.5kB, so it easily beats both FWE and dwm.

---

### Post by NintendoTogepi on 2009-03-07
Okay what is the lightest one that is still pretty usable? (as in JWM/Fluxbox/Openbox etc.)

---

### Post by InfinityCircuit on 2009-03-07
Do you want a tiling window manager? "Usable" is pretty vague.

---

### Post by kavon89 on 2009-03-07
> What is the absolute lightest WM?

[Screen]("http://en.wikipedia.org/wiki/GNU_Screen") without a doubt.

---

### Post by sertse on 2009-03-07
dvtm, a tiling console WM is lighter than screen... 

dwm I think, is the lightest usable graphical wm, usable in the sense people *do* use it, (Cardinals'? Chucky? one of them iirc) rather than just a novelty...

They are both tiling, it's usually lighter. Tiling is also very usable, I don't accept excuse that it's hard very convincing... (though I rather use xmonad and awesome rather than dwm heh)

---

### Post by namegame on 2009-03-07
> **sertse said:**
> 
dwm I think, is the lightest usable graphical wm, usable in the sense people *do* use it..


I do like the suckless.org WMs, I forget which one, either dwm or wmii, is extremely "small." The source code is only 250 lines long.

---

### Post by gnomeuser on 2009-03-07
> **jomiolto said:**
> I think that 27kB is about the same as [dwm]("http://www.suckless.org/dwm/").

But TinyWM is only about 8.5kB, so it easily beats both FWE and dwm.

ah but dwm pulls in X, FWE is X free. Massive saving right there.'

That being said, I am a GNOME user for a reason, I like functionality in my desktop.

---

### Post by Lux Perpetua on 2009-03-07
> **NintendoTogepi said:**
> Obviously this knocks out GNOME, KDE, XFCE, even some of the lighter ones like LXDE and ICEWM...so which is the absolute lightest WM?Your question has a clear right answer:
> **jomiolto said:**
> [TinyWM]("http://incise.org/tinywm.html").Thank you. :-)

To everyone still arguing, I give you the complete source of tinywm: 

**tinywm.c**```
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
**Makefile**```
PREFIX?=/usr/X11R6
CFLAGS?=-Os -pedantic -Wall

all:
        $(CC) $(CFLAGS) -I$(PREFIX)/include -L$(PREFIX)/lib -lX11 -o tinywm tinywm.c

clean:
        rm -f tinywm


```

---

### Post by wolfen69 on 2009-03-07
openbox gets my vote.

---

