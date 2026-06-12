---
title: "I love the repair-ability of linux"
date: 2010-03-21
forum: The Cafe
---

### Post by sandyd on 2010-03-21
I just love it.
One of my coworkers just did "sudo rm /usr/lib/x*" (dont do it).
and the only thing that was needed to fix that was to boot up using a livecd, plop /usr/lib/x* onto the ubuntu drive. and the computer was back online.

But then, it takes the joys out of reinstalling :D

---

### Post by RabbitWho on 2010-03-21
How come he did it?

---

### Post by FuturePilot on 2010-03-21
The problem is, now you're probably using old versions of whatever those libraries are.

---

### Post by Shpongle on 2010-03-21
> **FuturePilot said:**
> The problem is, now you're probably using old versions of whatever those libraries are.

would that not get fixed with an update ?

---

### Post by sandyd on 2010-03-21
> **FuturePilot said:**
> The problem is, now you're probably using old versions of whatever those libraries are.
I later marked them all for complete removal, then after that reinstallation.
But then again, I did that remotely from my office while she was still working...

I could have just toyed with the update servers (we have local repos here), but I was too lazy to :|

---

### Post by RiceMonster on 2010-03-21
> **DillByrne said:**
> would that not get fixed with an update ?

They won't automatically update because the package manager doesn't know it's an older version if you just manually copy the files over.

---

### Post by Shpongle on 2010-03-21
> **RiceMonster said:**
> They won't automatically update because the package manager doesn't know it's an older version if you just manually copy the files over.

oh i see , thanks for pointing that out

---

### Post by sandyd on 2010-03-21
> **RabbitWho said:**
> How come he did it?
she was preparing to vaporize the libx264 libraries. because she compiled them manually.

and she aparently did a few typos along the way...

---

### Post by madjr on 2010-03-21
hm, ubuntu should focus on the next versions with some kind of **backup/image/self-repair** thingy

the number of if images/backups would just depend on the space you assign to it

that would b wonderful if well integrated and give it an edge over other distros :D

---

### Post by fatality_uk on 2010-03-21
doh!

---

### Post by Post Monkeh on 2010-03-21
> **madjr said:**
> hm, ubuntu should focus on the next versions with some kind of **backup/image/self-repair** thingy

the number of if images/backups would just depend on the space you assign to it

that would b wonderful if well integrated and give it an edge over other distros :D

sounds very like windows system restore.

---

### Post by madjr on 2010-03-21
> **Post Monkeh said:**
> sounds very like windows system restore.

um kinda
we dont have nothing similar built in

would avoid lots of headaches

---

### Post by Seano911 on 2010-03-21
Try Back In Time. [http://backintime.le-web.org/](http://backintime.le-web.org/) for back ups.

---

### Post by falconindy on 2010-03-21
> **madjr said:**
> hm, ubuntu should focus on the next versions with some kind of **backup/image/self-repair** thingy

the number of if images/backups would just depend on the space you assign to it

that would b wonderful if well integrated and give it an edge over other distros :D
Windows needs such a crutch because the registry is essentially a black box. The filesystem itself is moving in this direction, as well, with Windows 7. Mangling either one of these can lead to a completely unresponsive system that might not even be recoverable with System Restore. SR is a flawed system which backs up to the same drive the data is on. What happens if this drive becomes corrupt during defrag, chkdsk, or otherwise? Mirroring software capable of performing the same task but in a consistent manner costs money.

In Linux, everything is transparent. If you make regular backups of the proper directories (using any one of number of free and readily available methods), you will always be able to restore to your exact previous state. If you don't make backups, you get what you deserve. This is the user's responsibility, not the OS's.

To that extent, there **is** backup software in the Ubuntu repos. There's even entire filesystems (e.g. btrfs or nilfs) and partition overlays (LVM) that give you the ability to make snapshots and roll back at will.

In short: **The tools are already available**.

---

### Post by madjr on 2010-03-21
> **Seano911 said:**
> Try Back In Time. [http://backintime.le-web.org/](http://backintime.le-web.org/) for back ups.

interesting, would u recommend this as default for next ubuntu releases?

---

### Post by sq7bti on 2010-03-21
I'd recommend [debsums]("http://vmlinux.org/cgi-bin/dwww?type=runman&location=DEBSUMS/1") on such system with inconsistency between deb package database vs actual filesystem. Just to make sure what version dpkg "thinks" it had installed and what is actually there, apparently copied from LiveCD. It will tell you what files needs a re-installation.

---

