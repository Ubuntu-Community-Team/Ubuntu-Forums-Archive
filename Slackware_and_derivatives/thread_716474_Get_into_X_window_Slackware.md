---
title: "Get into X window Slackware"
date: 2008-03-05
forum: Slackware and derivatives
---

### Post by NautTboy on 2008-03-05
Xbuntu freez/hold up on my old 300mhz so I tried Slackware for the 2nd times.  I consider it successful. 

After reboot it comes up asking:

name login: root
password: password

than it came up with you got mail " message bla bla bla..."

root@name:`#

Where do i go from here?
How to get into X Windows?

---

### Post by Whiffle on 2008-03-05
I don't remember if it will run as root,  but the first thing you'll want to do is make another user, I think thats the adduser command.  Once you've logged in as that user, try "startx"

---

### Post by NautTboy on 2008-03-06
Coooooooooooool!!! it works for root. 
But...........

I'm in X windows already but it's greyed. with a little panel at the bottom with clock on the right and some left and right arrows.

Look as if it's running on monochrome with 640X480 or smaller.

If i right click on the desk top it will show fluxbox 0.1.14.

How do I make it boot up(startx) automatically?

---

### Post by croto on 2008-03-06
Hey, I hope you're happy with your new slackware.

I *strongly* recommend... well let me put it this way: if you run your system as root, you're asking for trouble, and you'll have it. Seriously. So go ahead and create a user:
```

yourhost# adduser

```
It'll ask you a few questions, and you'll be ready to go.

Now you can set the system to go to X on boot. Linux has different "runlevels". Slackware is configured by default to not run X after boot, that is runlevel 3. You want to set de default runlevel to 4. So edit the file /etc/inittab (you can use the editor nano, for instance):
```

yourhost# nano /etc/inittab

```
You'll see two lines like
```

# Default runlevel. (Do not set to 0 or 6)
id:3:initdefault:

```

you just want to change them so it looks like:
```

# Default runlevel. (Do not set to 0 or 6)
id:4:initdefault:

```
don't forget to save the file (in nano I think it's CTRL-O, don't remember, but it should be written on the screen)

Now reboot, and it should go directly to X. I have no idea why it loaded fluxbox when you started X as root. If you installed KDE, you can set it as your default desktop manager at the login screen.

---

### Post by PmDematagoda on 2008-03-06
This thread has been moved to the Slackware section as it concerns Slackware.

---

### Post by NautTboy on 2008-03-06
Thanks croto.
I will try that once i get home.  Since that flux is so small i can barely see it.  There is not even a display panel option to set resolution for me to use like the ubuntu does.  It has all other stuff like gimps, gaims and games.

Any idea how i can change theme maybe? 

No, I didnt install KDE.  I just install step by step, answer what was ask from what i call the DOS installation.

---

### Post by Whiffle on 2008-03-06
You can change the resolution by editing /etc/X11/xorg.conf.  I'd give more detail but I'm not on a linux box at the moment.  It wouldn't hurt to install your video card drivers if you have them, its probably just using vesa at the moment.

---

