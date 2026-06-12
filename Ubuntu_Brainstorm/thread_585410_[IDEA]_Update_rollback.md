---
title: "[IDEA] Update rollback"
date: 2007-10-21
forum: Ubuntu Brainstorm
---

### Post by QwUo173Hy on 2007-10-21
The only major I've ever had with Ubuntu is when an update leaves your machine unbootable or with Xorg unable to run.

These were usually caused by kernel and nvidia updates respectively. I think the user should be able to undo an update. This could be achieved by keeping the previous update packages on the system as well as a log of the currently updated packages. When a rollback is requested, just remove the packages from the list and install the previous ones again from a cache.

Obviously in the case of an unbootable system, this feature won't be any help so I think this should in fact be a feature of the live CD. The installed system keeps the packages as described above and the CD can access them.

Jarlath

---

### Post by Choad on 2007-10-21
a very good idea.

---

### Post by Lozz on 2007-10-21
I agree completely. I very much hope this gets included.

---

### Post by smartboyathome on 2007-10-21
There was a project started on the gutsy forum called time machine which saved a backup and allowed you to restore. I think it was called time machine.

---

### Post by Lozz on 2007-10-21
> **smartboyathome said:**
> There was a project started on the gutsy forum called time machine which saved a backup and allowed you to restore. I think it was called time machine.

That sounds interesting. Any idea how far it got?

---

### Post by smartboyathome on 2007-10-21
> **Lozz said:**
> That sounds interesting. Any idea how far it got?

I think it got released last I checked, but I don't know the state of it now.

---

### Post by glotz on 2007-10-22
With bullet proof X  you should be able to forget those problems.

---

### Post by QwUo173Hy on 2007-10-22
That may apply to part of the problem. We still need a Bullet Proof kernel / boot loader though. The idea applies to every package that is upgradable, not just X.

---

### Post by ltk5 on 2007-11-07
> **smartboyathome said:**
> I think it got released last I checked, but I don't know the state of it now.

As I was checking Slashdot I saw the story about [time machine for linux]("http://hardware.slashdot.org/hardware/07/11/07/1451235.shtml")
The proects name is [Flyback]("http://code.google.com/p/flyback/")

---

### Post by bruce89 on 2007-11-07
X isn't everything, you could just use aptitude to roll back.

---

### Post by coolen on 2007-11-07
Perhaps some more work into the upgrade process is required. I think it'd be better to ensure a clean upgrade than to allow users to undo the damage once they mess up their machine.

---

### Post by mellowd on 2007-12-15
This really should be implemented. When upgrading the Red Hat Enterprise servers at work using up2date there is an option to enable rollback. There should be an option for this on aptitude or apt-get.

That being said, the rollback doesn't work perfectly and this is the enterprise version.

---

### Post by QwUo173Hy on 2007-12-15
> **ltk5 said:**
> As I was checking Slashdot I saw the story about [time machine for linux]("http://hardware.slashdot.org/hardware/07/11/07/1451235.shtml")
The proects name is [Flyback]("http://code.google.com/p/flyback/")

That looks interesting. As it stands, it wouldn't be any use in the scenarios I'm describing because you need a bootable system to run the application. But if something like this was intergrated with the liveCD I think it would be excellent.

---

### Post by smartboyathome on 2007-12-15
There IS still timevault (I think that Timevault and Flyback are doing the same thing).

---

### Post by gnomeuser on 2007-12-16
To make this work, really we have to realise that the Debian Packaging System needs to go away, it does not have the functionality we require to do this right. You can do snapshot at a file system level but the packages themselves might alter settings and configuration files which you need to cleanly rollback.

The nicest solution to this problem is to work on replacing dpkg with Conary, this might sound impossible but with tools like PackageKit it becomes remarkably more possible to rewrite tools like installers and GUIs to be abstracted from the package manager specifics underneath. This way you can batch convert your existing packages, clean up specs, write documentation and retrain developers with much less effort, but it is still going to take a considerable amount of time.

All this takes is the determination to set a goal to get all the type of functionality Conary buys us (not that Conary is required to be the goal but it happens to be a well tested solution that gives us all we require to fulfill this goal and many others plus we can help drive the development of Conary to do what it might lack while we work on converting to PackageKit everywhere).

---

### Post by QwUo173Hy on 2007-12-16
> **gnomeuser said:**
> ... the Debian Packaging System ... does not have the functionality we require to do this right. You can do snapshot at a file system level but the packages themselves might alter settings and configuration files which you need to cleanly rollback.

If you look at a .deb file, you can find where all these configuration files are. So we could also simply choose to back these up as well.

---

### Post by 23meg on 2007-12-16
[QUOTE=jarlath]If you look at a .deb file, you can find where all these configuration files are.[/QUOTE]

No, not all. The packaging system doesn't know anything about configuration files created after installation.

---

### Post by QwUo173Hy on 2007-12-16
I forgot to consider post install. Good point.

---

### Post by plun on 2007-12-16
> **smartboyathome said:**
> There IS still timevault (I think that Timevault and Flyback are doing the same thing).

Yup... inventing the wheel over and over again...:)

Ubuntus wiki
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

Launchpad, info and Beta code
[https://launchpad.net/timevault](https://launchpad.net/timevault)

---

### Post by MayorBobster on 2009-01-29
I could have used this today!   I have updates disabled till the next release  (jackelope?) because the current set of updates kills both X windows and networking.

---

### Post by clcoyle on 2009-02-04
> **MayorBobster said:**
> I could have used this today!   I have updates disabled till the next release  (jackelope?) because the current set of updates kills both X windows and networking.


I could have used it today too, which is why I did a search on 'update rollback' and found this thread!  

The apt-get update broke my internet - not the eth0, as it will ping the DNS (ISP), the gateway (router), and this xp laptop on the network, but it won't go to the web.   

What is it that allows it to ping the ISP, but not something on the web??  What am I missing here??

---

### Post by smartboyathome on 2009-02-04
> **clcoyle said:**
> What is it that allows it to ping the ISP, but not something on the web??  What am I missing here??

For some reason it isn't getting an IP address from your gateway. Are you on wireless or wired, btw?

---

### Post by imag1narynumber on 2009-02-04
This is a great idea.  And it's so not new.  I'm curious why Ubuntu doesn't have it yet.  I believe Sourcemage offers it.

---

