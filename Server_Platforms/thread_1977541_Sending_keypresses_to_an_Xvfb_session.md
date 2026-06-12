---
title: "Sending keypresses to an Xvfb session"
date: 2012-05-10
forum: Server Platforms
---

### Post by Cadmus on 2012-05-10
Hello. Having [gotten my headless server to serve sound]("http://ubuntuforums.org/showthread.php?t=1956577") I can now make videos on my headless server with Xvfb.

There's just one thing that would make it perfect, and that would be if I could send some keypresses to it to get past the applications start prompt.

Assuming I need to press 'X' to get past the prompt and if I'm running my X server at display :1 I have tried the following tools
```
export DISPLAY=:1
xte -x :1 'key X'
xdotool key 'X'
```

To no avail. Can anyone point me in the right direction?

---

### Post by Jonathan L on 2012-05-10
Hi Cadmus

> I need to press 'X'Have you tried moving the mouse to the right spot:
```
xdotool mousemove 100 200
xdotool key X

```Any use?

Otherwise I think you have to send an X11 event, which is considerably trickier.  I've only seen C programs for it, but there must be other ways.  [http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html](http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html)

Kind regards,
Jonathan.

PS.  Also found [http://www.shallowsky.com/software/crikey/](http://www.shallowsky.com/software/crikey/) which might be helpful.  And [http://code.google.com/p/autokey/](http://code.google.com/p/autokey/)

---

### Post by Cadmus on 2012-05-11
I tried using xvkbd, and I thought I had it working with something like:

```
xvkbd -display :1 -window x2000d -text "X"
```

But I tried it a second time and it wasn't playing. As this is infrequent I may just set up a VNC into it and skip the prompt by hand.

---

### Post by Jonathan L on 2012-05-11
Hi again

> **Cadmus said:**
> I tried using xvkbd, and I thought I had it working with something like:

```
xvkbd -display :1 -window x2000d -text "X"
```But I tried it a second time and it wasn't playing. As this is infrequent I may just set up a VNC into it and skip the prompt by hand.

Window IDs, names, and titles are apt to change.  I'd start the application with a geometry string so it's in exactly the same place each time, move the cursor there, select window (if necessary), and then the text.  What program is it you're running?

Kind regards,
Jonathan.

---

### Post by Cadmus on 2012-05-11
It's MAME and by default that opens full screen

```
cadmus@headless:~$ xwininfo -display :1 -root -tree

xwininfo: Window id: 0xde (the root window) (has no name)

  Root window id: 0xde (the root window) (has no name)
  Parent window id: 0x0 (none)
     2 children:
     0x20000d (has no name): ()  800x600+0+0  +0+0
        1 child:
        0x20000f (has no name): ()  800x600+0+0  +0+0
     0x20000e "MAME: Alien vs. Predator (Euro 940520) [avsp]": ("mame" "mame")  800x600+0+0  +0+0
```

If you're not familiar with MAME you have to press 'OK' (literally type O then K) if you haven't run a game before, however for recording you are advised to delete all your configs to ensure a clean slate. Therefore you always have to press 'OK'. I've tried sending to e f and d when it's been at the prompt but it doesn't seem to be working. I will take a look over the weekend as I'm actually recording right now.

---

