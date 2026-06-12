---
title: "Problems with MPICH"
date: 2011-07-28
forum: Server Platforms
---

### Post by yerttle on 2011-07-28
Hello,
I am a Linux noob but I like to jump in at the deep end. I am trying to use Ubuntu Server 10.4 and MPICH to make a "super computer" of sorts out of three old Dell P4 machines. I have followed a couple of guides online and have done these basic steps.

I have installed nfs-kernel-server and build-essential via apt-get. Then I used wget to download mpich2, libmpich2-1.2, libmpich2-dev and mpich2-doc from [http://packages.ubuntu.com/natty](http://packages.ubuntu.com/natty) and installed them with dpkg.

The problem is the guide that I am following is asking me to run "mpd &" but it says the application is not installed. I did run "apt-get install mpd" but got a Music Player Daemon, which didn't seem right?

Any help would be much appreciated.

Yerttle

---

### Post by cannona on 2011-07-28
Hi.

From [http://wiki.freepascal.org/MPICH:](http://wiki.freepascal.org/MPICH:)

"Under ubuntu/debian you can install the following packages: libmpich-mpd1.0-dev mpich-mpd-bin 

There's a how-to for installing Mpich2 in Ubuntu/Debian in Ubuntu Wiki : 
[https://wiki.ubuntu.com/MpichCluster](https://wiki.ubuntu.com/MpichCluster)
"

Not sure if either of those packages is what you are looking for, as I've not done this myself, but thought it might be possible.

Good luck.

Aaron

---

