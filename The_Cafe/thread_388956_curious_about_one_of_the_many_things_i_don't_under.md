---
title: "curious about one of the many things i don't understand"
date: 2007-03-20
forum: The Cafe
---

### Post by matthekc on 2007-03-20
When you take ubuntu and say throw a new kernel or xorg into it how does it effect package managment? when is it no longer edgy or fiesty?

---

### Post by igknighted on 2007-03-20
Linux is sort of a "rolling release" type of OS.  With some distro's (Gentoo for example) there is no real versions.  Just an updated installer gets released every now and then.  Debian is similar.  As programs get more stable and better tested they move from unstable to testing to stable (I think... im not an expert with how Debian works though) and then a new installer is released when enough has changed.  Ubuntu, I guess you could say, changes versions based on what repo's you are using.  If you use Edgy updates you are using edgy, and if you use feisty updates you are using feisty.  If you are using both, well, you are probably going to mess up your system soon so I don't think it matters what you call it in the meantime ;-).

---

### Post by matthekc on 2007-03-20
thanks and that last part was pretty funny

---

### Post by matthekc on 2007-03-20
so when people throw in a new kernel or xorg they can mess stuff up but what are the chances good fair poor of messing something up

---

### Post by igknighted on 2007-03-20
> **matthekc said:**
> so when people throw in a new kernel or xorg they can mess stuff up but what are the chances good fair poor of messing something up

A new kernel is almost completely harmless.  Worst thing that happens is you boot the old one instead (unless you deleted the old one... never do that until you know the new one works).  As for Xorg... this could be iffy.  I wouldn't attempt it unless I had a repo I trusted to install it from.  I know for people wanting to use AIGLX on dapper there is a repo that install "xorg-server-air" or something like that.  I think if you mess that up you can save your system by reverting to the normal Xorg.  However to do a straight up upgrade of Xorg would be risky.  That said, if you were using Gentoo it would be fairly easy.  You would run "emerge -u xserver-xorg" (or whatver the ebuild [source code + instructions to portage to compile & install it for you] is called) and it would get the newest version and install it, updating any dependencies needed as well.  But with Ubuntu I wouldn't try it.  That is the type of surgery that would make me just upgrade to the newer version if I really want it.

If you want to stay more up to date, and don't mind a little more work you might try Fedora.  Also a great choice would be Sidux (comes with KDE desktop as default, tho Xfce, fluxbox, fvwm and a few others are options at install as well).  Sidux uses Debian Sid, so it always has the latest versions of programs.

---

### Post by 23meg on 2007-03-20
Depends on the care you apply when doing it, on how much you know what you're doing. 

If you'd like to upgrade to Xorg 7.2 on Edgy, you can use Treviño's repository; it's easy to upgrade and will most likely be safe. Do a search, there's a thread in the Tutorials and Tips section that explains how.

---

### Post by matthekc on 2007-03-20
not plannig it just been reading the tips and tutorials section and became curious

---

### Post by matthekc on 2007-03-20
my browser did something weird got a double post

---

