---
title: "Broken Packages in Dapper unable to install G++ and dependencies"
date: 2007-02-12
forum: Repositories &amp; Backports
---

### Post by 1917oct on 2007-02-12
I'm really new to Ubuntu, and to linux.  I've run across a situation that is not a problem yet, but will shortly become one (i think.) In installing one of many things that I have installed in the last week to try and get everything I need up and running on Ubuntu (Dapper) I have at some point broken some packages.  G++ (all versiond through G++4) will not install in synaptic.  They should already be on the system, however, at some point, while trying to get transcode/ dvd::rip to work properly, they were removed. One of the dependencies is libc6-dev (if I remeber correctly.)  The G++ packages will be important for all sorts of thing I'm assuming...

I tried fixing my broken packages, and it fixed 2 of them.  However still cant re-install G++ 

Also, I was wandering if this could have to do with a libc6 backport problem? 

I think my problem may be related to dvd decription codecs, because my mencoder is no longer functioning properly.

I'll try to post more technical information tonight from home where I have my terminal infront of me.

Sorry for rambling on, I'm really new at this.

---

### Post by 1917oct on 2007-02-12
ok.  

So, I removed a couple of repositories, and rolled back my libc6 to an earlier version, and aptitude kicked in from there.  Then I went over to synaptic, and installed G++ and now it's all cool. 

I guess sometimes you just have to solve your own problems.

---

