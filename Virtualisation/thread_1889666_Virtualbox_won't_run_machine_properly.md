---
title: "Virtualbox won't run machine properly"
date: 2011-12-01
forum: Virtualisation
---

### Post by zach.1 on 2011-12-01
Hello, I'm a new Linux user using Kubuntu through Virtualbox with MacOSx as my host. I have no idea what's happened, but when I boot up the VM I get the initial Kubuntu loading page, but instead of running the OS it just goes to a black terminal type screen that says, ```

Ubuntu 11.10 name-Virtualbox tty1
name-Virtualbox login: 
```If I type in my username and password that I've set up with Kubuntu it looks as if it does some checks and then just gives me another command line, this time,

```
name@name-Virtualbox:~$
```
Any thoughts on what happened and how I can fix it? Thanks.

---

### Post by chrisinspace on 2011-12-01
It sounds like X isn't loading correctly.  Did you recently upgrade VirtualBox?  If so, you'll need to load the new Guest Additions so your Kubuntu guest has the proper video drivers.

---

### Post by zach.1 on 2011-12-02
I have the same version of VB as I initially installed and the guest additions I have mounted is the one that came in the tin.

---

### Post by CharlesA on 2011-12-02
Hit Alt + F7

---

### Post by snowpine on 2011-12-02
Or type 'startx' and tell us the errors.

---

### Post by zach.1 on 2011-12-02
Okay, after startx I get the following message:

```
Error: Cannot close "/tmp/fileJtAKQZ" properly (not enough space?)
       Output file "/tmp/filejtAKQZ" removed
Errors from xkbcomp are not fatal to the X server
(EE) Error compiling keymap (-)
(EE) XKB: Couldn't compile keymap
(EE) XKB: Failed to load keymap. Loading default keymap instead.
The XKEYBOARD keymap compiler (xkbcomp) reports:
Error:                  Cannot close "/tmp/fileHun08W" properly (not enough space?)
                        Output file "/tmp/fileHun08W" removed
Errors from xkbcomp are not fatal to the X server
(EE) Error compiling keymap (-)
(EE) XKB: Couldn't compile keymap
XKB: Failed to compile keymap
Keyboard initialization failed. This could be a missing or incorrext setup of xk
eyboard-config.

Fatal server error:
Failed to activate core devices.
```

I'm not exactly sure what is important out of all that, so I posted the entire message I get.

Hitting Alt+F7 gave me a screen with a bunch of starting and stopping processes and everything says [ OK ] at the end, but it doesn't do anything...

---

### Post by snowpine on 2011-12-02
Let's start from the beginning--Line 1 suggests maybe not enough space? You can check with:

```
df -h
```

---

### Post by CharlesA on 2011-12-02
Try a reinstall. It looks like it's failing to start X due to lack of space (?)

---

### Post by zach.1 on 2011-12-02
According to that I have 0 space, which is my fault as I made a mistake in copying some files (a lot of files) instead of moving them. Come to think of it, that's the last thing I did before I shut the machine down the last time it still booted. This is actually what I'm worried about with a reinstall, i.e. I'll end up losing files that I unfortunately only have in this machine. Which, I'm well aware, is unbelievably moronic, believe me, it's not something I plan to make a habit of, just an oversight.

Idiocy aside, will making space on the virtual disk allow me to boot (and how would I do so)? Alternatively, is there a way to create and mount a shared folder and move files straight from the terminal screen I'm getting? In my mind I think I know how that would work, but I don't exactly trust myself to just do it at this point. I don't mind losing this system, but I really don't want to lose the files on it.

---

### Post by CharlesA on 2011-12-02
Yeah, if you make space, it'll boot.

---

### Post by zach.1 on 2011-12-02
Thank you so much for your help, I can't believe the problem was so simple.

---

### Post by CharlesA on 2011-12-02
Glad you were able to get it working. :)

---

