---
title: "lxc Xserver fails  /dev/dri/card0: failed to set DRM"
date: 2015-05-19
forum: Virtualisation
---

### Post by odror on 2015-05-19
I am trying to have a container (lxc) with its own desktop on vt8 (v.s. vt7 default ubuntu desktop)

Host: ubuntu 15.04
guest: arch

My ultimate goal is to have gnome 3.16 running in a container (vt8) side by side with ubuntu (vt7).

As I start X on vt2 
> /usr/bin/X vt8

I get a blank screen. (I cannot go back to the host at vt7 or any of the terminal vt1-6). At the bottom of /var/log/Xorg.0.log

I get the following error message.
```
[ 65103.291] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 65103.291] (II) xfree86: Adding drm device (/dev/dri/card0)
[ 65103.291] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
[ 65103.294] (EE) FBDEV(0): FBIOBLANK: Invalid argument

```

I would appreciate any idea how to fix this.

---

### Post by TheFu on 2015-05-21
**Update:**

So, I've displayed my ignorance for the world 1 more time when I thought I understood a technology and before doing any directly relevant research. ;)  Found lots of people attempting this - many seem to be on a beta Ubuntu. There's an Ubuntu.com how-to guide  specific to running Unity-8 inside LXC.  [https://wiki.ubuntu.com/Unity8inLXC](https://wiki.ubuntu.com/Unity8inLXC)

I stand behind my options below, but clearly there are many others, if you DEMAND the performance of a direct-hardware mode and security is NOT of any concern. Allowing a container OS to direct memory access of the host sorts removes all security. [https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop) has simple instructions - basically, the tool automates passthru of all direct HW access from the host to the container.

If you just want to run a browser inside a container and access it over remote X11 on the same LAN, I think "B" is what you want still.

[https://unix.stackexchange.com/questions/18003/linux-lxc-deploying-images-with-tiniest-possible-x11/21607#21607](https://unix.stackexchange.com/questions/18003/linux-lxc-deploying-images-with-tiniest-possible-x11/21607#21607) 

**Original Post follows:**

I don't believe you can run an X/Server inside a container like that without providing virtual GPU hardware or hardware passthru of dedicated GPU hardware (which I've never heard of anyone doing for containers).

Option A: Use a remote desktop into the container (like VNC or x2go) or 
Option B: Use proper X-Server to X-Client communications.  The X-Client is inside the container. The X-server is your desktop.

Both of these options would work like any other local-to-remote GUI connection with C/S tools. Forget about the "container" and treat the systems as local and remote X-Windows systems.

---

### Post by odror on 2015-05-21
My understanding is that I can do it. My approach was wrong. Apparently I need to use the nvidia cuda driver. 

[http://tleyden.github.io/blog/2014/10/25/docker-on-aws-gpu-ubuntu-14-dot-04-slash-cuda-6-dot-5/](http://tleyden.github.io/blog/2014/10/25/docker-on-aws-gpu-ubuntu-14-dot-04-slash-cuda-6-dot-5/)

Since I posted the issue initially I tried installing the cuda driver. I had issues with getting the cuda driver working. primarily because I have nvidia driver 352.09 and kernel 3.19.8.

I was able to get it to work with the nvidia nouveau driver.

---

### Post by odror on 2015-05-21
I managed to get X11/nvidia under arch lxc working under ubuntu 15.04

I am still getting this error in my Xorg.0.log

```
[ 12143.553] (II) xfree86: Adding drm device (/dev/dri/card0)
[ 12143.553] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied

```

What does that mean. Is it important. My ultimate goal is to install gnome 3.16

---

