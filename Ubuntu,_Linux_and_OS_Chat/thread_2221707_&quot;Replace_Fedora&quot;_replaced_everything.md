---
title: "&quot;Replace Fedora&quot; replaced everything"
date: 2014-05-03
forum: Ubuntu, Linux and OS Chat
---

### Post by vaccix on 2014-05-03
I attempted to install 14.04 alongside my Windows partition and selected the "replace fedora" option, but it ended up wiping my entire hard drive and installing Ubuntu. I don't have a Windows disk to reinstall, so I am losing access to some software that I have paid for and also will have to tinker around to hopefully get all my hardware working.. I do know how to survive in Linux, but this is irritating.

---

### Post by SurfaceUnits on 2014-05-03
Did it overwrite your Windows parttion or just blank it out.

---

### Post by RichardET on 2014-05-03
just do a virtual windows;  its better than a dual boot.

---

### Post by monkeybrain20122 on 2014-05-03
If it said "replace fedora" that means it only saw fedora then of course it would wipe everything. When you have complex configurations always choose manual install ('something else')

---

### Post by monkeybrain20122 on 2014-05-03
> **RichardET said:**
> just do a virtual windows;  its better than a dual boot.

+1.  I would much prefer dual booting with Fedora then Windows, much simpler to set up and maintain.

---

### Post by LastDino on 2014-05-03
Oh, looks like you experience something similar. Never pick replace option even if there is just single Linux on HD. I did that last time and I was expecting my partition scheme to be intact and just simple format and install of the drives used by previous version. But it took entire HD and only made 2 partitions (swap & root, and in that I think swap was taken from last scheme). 

Lesson to be learned: Always go with ''something else'' in gpart or whichever tool you've been provided in installation process.

---

### Post by oldfred on 2014-05-03
there is a bug report and lots of complaints.
But may be a Windows is hibernated or fast boot issue so that Linux cannot 'see' the Windows install to even know to keep it.
 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by RichardET on 2014-05-03
> **monkeybrain20122 said:**
> +1.  I would much prefer dual booting with Fedora then Windows, much simpler to set up and maintain.

I never dual boot - too much wasted HD space, plus installation headaches as one can see from this thread.

---

### Post by monkeybrain20122 on 2014-05-03
> **RichardET said:**
> I never dual boot - too much wasted HD space, plus installation headaches as one can see from this thread.

The headaches mainly come from trying to dual boot with Windows, especially Win8. I triple, multiple boot with other Linux distros and it is easy as a piece of cake (except for OpenSuse)  MicroSoft doesn't like dualboot and tries to do everything to discourage it, so I comply and just remove Windows. :)

---

### Post by JayKay3OOO on 2014-05-03
I always make system restore disks / images of my Windows installations. 

Not only does it allow you to restore Windows without a disk, but if you make the image with all your system setup it saves so much time.

Don't worry. I accidentally wiped my backup drive a few months ago. Luckily I had an emergency backup in a draw in another room.

---

### Post by SurfaceUnits on 2014-05-03
One last thing to try is testdisk to see if any partition is recoverable

---

### Post by Eggnog on 2014-05-03
I've never run Win 8, and don't intend to.  I do, however, have one of my machines in a dual boot with Win 7 simply so I can game with games I have that don't run on Linux and I won't be bothered to use Wine.  That's all it's for.  I don't boot into the Win 7 portion for anything else.

As pointed out above, running Win in a virtual machine is awesome, at least Win 7.  While it's not good enough for gaming, it's more than good enough for the standard apps most people tend to run in Windows, like Quicken, MS Office, etc.  And the bonus is that Windows isn't running your PC.  It's a win-win situation.

---

### Post by vaccix on 2014-05-05
> **monkeybrain20122 said:**
> If it said "replace fedora" that means it only saw fedora then of course it would wipe everything. When you have complex configurations always choose manual install ('something else')

I guess Ubuntu and I had a miscommunication.
It was just a headache, but I've been able to get most of my hardware working so far.

---

### Post by vaccix on 2014-05-05
I tried testdisk and it confirmed that everything had been wiped.

---

