---
title: "Headless server, running/displaying a program with UI on a remote computer..."
date: 2009-08-21
forum: Server Platforms
---

### Post by kripz on 2009-08-21
Are there any guides? I would google but i dont even know what this concept is called...

---

### Post by hessiess on 2009-08-21
> **kripz said:**
> Are there any guides? I would google but i dont even know what this concept is called...

VNC, though you rilly don't want to be using remote desktop protocols as they are extremely inefficient (use a hell of a lot of network bandwidth), learn to use the command line, and use ssh. or use webmin.

---

### Post by fishy6969 on 2009-08-21
The simplest way is to SSH into the box using the '-X' option ie
ssh -X someone@someserver. '-X' forwards the X11 display. One connected launch the application you want to use from the commandline and voila, it should appear on your local screen. There are other options, but this is probably the simplest. 

If connecting from windows, xming and putty will do the same.

Regards

---

### Post by DaithiF on 2009-08-21
Hi,
there are a number of possibilities.  One of the simplest is X forwarding over ssh.

so to run someguiprogam on the server but with display on your local client then:
```
ssh -X you@yourserver someguiprogram

```

This requires you to be running X on your client which is fine for Linux but not from a Windows machine (though can do it using cygwin on windows).

Performance with X forwarding may not be fantastic either, so if for either of these reasons this approach doesn't work out, there are some other solutions you could look into:
vnc-server
NX
Xpra
are some of the ones I have heard of, though I'm sure there are more.
good luck

---

### Post by kripz on 2009-08-21
OK ive got xming on my windows PC and xorg on my server. x11 forwarding is working. Im running my program in a screen session and im seeing the UI on my PC.

Can i somehow close the SSH session but keep the program running on the server and then check back on it later on?

---

### Post by DaithiF on 2009-08-21
No, i don't think so.

XPRA apparently does this: [http://partiwm.org/wiki/xpra](http://partiwm.org/wiki/xpra)
I haven't tried it, but it was mentioned on a recent Ubuntu Uk podcast.

---

### Post by fishy6969 on 2009-08-21
AFAIK screen only supports console-mode apps. xpra would be an equivalent for graphical apps. 

Personally I tend to use freenx instead. It supports suspend/resume of sessions etc. Not difficult to set up - 
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by kripz on 2009-08-21
Just had a quick google, freenx seems like vnc. xpra seems buggy and the project looks dead.

:(

---

### Post by fishy6969 on 2009-08-21
FreeNX is much better IMHO than VNC, mainly for the following two reasons - 

1) Speed (I'm writing this now over my work's crappy internet connection via my machine at home and the response is near local)
2) Rootless mode ie you can run just an app and not a whole desktop (though VNC may be able to do this as well)

Google are also looking at the 'NX' method of remote desktops with neatx - [http://code.google.com/p/neatx/](http://code.google.com/p/neatx/)

---

