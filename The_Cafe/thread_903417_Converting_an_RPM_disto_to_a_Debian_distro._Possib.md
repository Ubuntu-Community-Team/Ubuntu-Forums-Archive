---
title: "Converting an RPM disto to a Debian distro. Possible?"
date: 2008-08-28
forum: The Cafe
---

### Post by icett on 2008-08-28
Do you think it is possible to convert an RPM based distro like Fedora or openSUSE to a Debian one? And if it is not too tough would you care to give me some hints? Best regards:KS

---

### Post by Dremora on 2008-08-28
You can install dpkg into an RPM distro, and you can use RPM in a debian based distro.

It's not really a good idea though, everything in the system is still tracked by apt or yum using their respective backend, anything installed with the foreign package manager will have to be tracked by their database, potential for clobbering system files and creating dependency hell is almost guaranteed.

---

### Post by Hire on 2008-08-28
You can use a native distro based on rpm like Fedora, or you can - if you have a rpm and use a distro deb-based - use alien :)

Why doing another time the wheel when it just exist?

---

### Post by az on 2008-08-28
While you can install some binary packages from one distro into another, it's not recommended.  GNU/Linux is source-compatible, not binary-compatible.

The binary package is just the end-product of the development chain.  The reason why the software is so good is because that chain works with the source code and one developers' idea can be used and reused without much limitation.

Focusing on the binary packages is a really bad idea.  You lose out on innovation, flexibility, convenience and security.

A distro is not a bunch of software on CDs you download from the internet;  a distro is a community of developers who put the software together.  When you pick a distro, you don't want the advantages of whatever software packages they offer, but rather the advantages the group has to offer in *maintaining* that software.

In that context, swapping package managers for the sake of changing package managers doesn't really make sense.

---

### Post by Slug71 on 2008-08-28
I dont know as im still a newbie myself but maybe if you built a distro from scratch starting with the kernel you could use two seperate Package Managers each using APT and apt-rpm as front-ends so that you have some sort of simularity there. You'd have to have dependencies for both formats in your distro and the distro would probably be bigger than any or most other distros because of this but i think that might work. The only thing is youd have to have two Package Managers installed and use them approprietly.

---

### Post by KiwiNZ on 2008-08-28
+1

I agree 100% 


> **az said:**
> While you can install some binary packages from one distro into another, it's not recommended.  GNU/Linux is source-compatible, not binary-compatible.

The binary package is just the end-product of the development chain.  The reason why the software is so good is because that chain works with the source code and one developers' idea can be used and reused without much limitation.

Focusing on the binary packages is a really bad idea.  You lose out on innovation, flexibility, convenience and security.

A distro is not a bunch of software on CDs you download from the internet;  a distro is a community of developers who put the software together.  When you pick a distro, you don't want the advantages of whatever software packages they offer, but rather the advantages the group has to offer in *maintaining* that software.

In that context, swapping package managers for the sake of changing package managers doesn't really make sense.

---

### Post by SunnyRabbiera on 2008-08-28
Its usually better to just install apt for RPM in a rpm based distro then to do this.

---

### Post by RiceMonster on 2008-08-28
PCLinuxOS uses apt for rpm. You could try that.

---

### Post by LaRoza on 2008-08-28
If you go by the way they look and default software, it would be very easy. Just recreate or find the theme and install the software (see sticky in Other OS Talk). The package manager (the biggest different between distros) wouldn't be so easy. You would, in a Debian enviroment, use Debian package managers.

---

### Post by insane_alien on 2008-08-28
you can, i changed linux from scratch into ubuntu but it took 8 months most of it fixing stuff that went wrong. but it eventually turned into ubuntu.

---

### Post by swoll1980 on 2008-08-28
> **hire said:**
> 

why doing another time the wheel when it just exist?

+1

---

