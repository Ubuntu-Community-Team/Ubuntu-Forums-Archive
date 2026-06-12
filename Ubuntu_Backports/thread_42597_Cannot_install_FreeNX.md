---
title: "Cannot install FreeNX"
date: 2005-06-18
forum: Ubuntu Backports
---

### Post by mglukhovsky on 2005-06-18
FreeNX is listed in Synaptic, but there is no installable version for it! When I try to install FreeNX, this is what I get:
```
michael@ubuntu64-server:~$ sudo apt-get install freenx nxssh
Reading package lists... Done
Building dependency tree... Done
Package freenx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package freenx has no installation candidate

```

Supposedly many people have managed to install FreeNX from the Backports repositories- has FreeNX been removed since then?

---

### Post by jdong on 2005-06-18
What architecture?

---

### Post by mglukhovsky on 2005-06-18
Good call, that may be why. I'm running AMD64- has FreeNX not been released for that architecture yet?

---

### Post by jdong on 2005-06-18
I don't package AMD64 backports yet, though I'm working on that issue right now.

As far as whether or not FreeNX compiles for AMD64, IIRC from Gentoo, the answer is **no**. sorry :(

---

### Post by mglukhovsky on 2005-06-18
Well thanks for letting me know... anything I can do to help move the Backports project forward for AMD64?

One other thing- did you hear of problems with FreeNX on Gentoo from the Gentoo forums? The speed of FreeNX vs. VNC is remarkable, so I'll do some research and look into it.

---

### Post by mglukhovsky on 2005-06-18
Apparently one guy on the Gentoo Forums has gotten FreeNX working under AMD64 by compiling with a 32-bit chroot environment. The links to the files he used and the changes he's made are posted there.
Link: [http://forums.gentoo.org/viewtopic-t-309474-highlight-freenx+amd64.html](http://forums.gentoo.org/viewtopic-t-309474-highlight-freenx+amd64.html)

On the FreeNX-kNX mailing list (for the project of that name, for a KDE implementation) mentions that it should compile on AMD64, but I'm not sure if the project encompasses a server or just a KDE NX client. Here's the link: [http://mail.kde.org/pipermail/freenx-knx/](http://mail.kde.org/pipermail/freenx-knx/)
 
Cheers!

---

### Post by jdong on 2005-06-19
Well, we can't do that. FreeNX exports many libraries, and the dpkg package manager doesn't support multiple architectures on one system. If I introduce 32-bit binaries blatantly packaged inside 64-bit packages, that's a great way to get all of the Ubuntu devs pissed at Backports again!

---

### Post by mglukhovsky on 2005-06-19
A good point indeed.  :)  I suppose it's pointless to try further, so I'll just give up for now. Although I will try emailiing the devs at NoMachine to see if they have any plans on making readily available for AMD64. 

Thanks for all your help, and let me know if there's anything I can do to help out with the AMD64 backports.

---

