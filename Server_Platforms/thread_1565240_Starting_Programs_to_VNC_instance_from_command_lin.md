---
title: "Starting Programs to VNC instance from command line"
date: 2010-08-31
forum: Server Platforms
---

### Post by Jamina1 on 2010-08-31
I have a headless virtual machine that I intend to use as a browsershots screenshot factory. I'd like to install as many browsers as possible, but I've come across some weird errors that prevent me from using some of the more popular ones.

**I know that to launch a program in a VNC instance, you use the --display=:# format. Some programs do not abide by that. How do I launch them?**

The biggest example of this is arora, which continues to state "Cannot connect to X server" regardless of what parameters I put in the command line.

The other large issue I am coming across with Chrome and Opera is the error **Xlib: extension "RANDR" missing on display** how do I fix this error?

---

### Post by endotherm on 2010-08-31
are you using desktop sharing (remote desktop/vino) or did you install a full vnc instance for multiple sessions?

you may want to try running this first to check your current display:
```
echo $DISPLAY
```

this page may give you some better examples and options for specifying your display parameter. [http://www.notesbit.com/index.php/scripts-unix/how-do-i-set-the-display-variable-on-linux/](http://www.notesbit.com/index.php/scripts-unix/how-do-i-set-the-display-variable-on-linux/)

---

### Post by Jamina1 on 2010-08-31
To clarify, I'm accessing this machine completely remotely. It does not have a desktop environment installed and all my interactions with it are through SSH. That being said, I have tightvncserver installed so that I can run certain programs through a virtual display.

The problem is that the syntax I have been using (I.E):

$firefox --display=:1 

Which would put firefox up on VNC display 1, does not work for some programs, such as arora.

---

