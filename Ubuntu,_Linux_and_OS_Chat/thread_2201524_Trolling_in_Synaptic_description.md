---
title: "Trolling in Synaptic description?"
date: 2014-01-24
forum: Ubuntu, Linux and OS Chat
---

### Post by bob43 on 2014-01-24
I installed Ubuntu 13.10 , then added the repositories for the MATE desktop environment. I looked in Synaptic package manager. I see that the:-

**mate-desktop-environment-extra**

file, has the following description against it ( I quote):-

The MATE Desktop Environment, a[B] non-intuitive and unattractive desktop
[/B]for users, using traditional computing desktop metaphor.
This package depends on the extra set of applications that are
part of the official MATE release.

-------------------
Whatever you think of MATE this is pretty rude isn't it? Has something been hacked? Has anyone else noticed this?

Regards

---

### Post by papibe on 2014-01-24
Hi bob43.

That looks awful. I'd like to know the source of this so I can report it.

Could you open a terminal run this command and post back its results?
```
apt-cache policy mate-desktop-environment-extra
```
Regards.

BTW: there's no such package on the Ubuntu repositories, so my guess is that it came from a ppa, or from another manually added repository.

---

### Post by QIII on 2014-01-24
Still, just ... wrong!

---

### Post by coffeecat on 2014-01-24
The deb package mate-desktop-environment-extra_1.6.0.2+raring_all.deb from the mate-desktop.org site itself contains this in the DEBIAN/control file:

> Package: mate-desktop-environment-extra
Source: mate-desktop-environment
Version: 1.6.0.2+raring
Architecture: all
Maintainer: Stefano Karapetsas <stefano@karapetsas.com>
Installed-Size: 26
Depends: mate-core (= 1.6.0.2+raring), mate-desktop-environment (= 1.6.0.2+raring), mate-bluetooth (>= 1.6.0), mate-netspeed (>= 1.6.0), mate-sensors-applet (>= 1.6.0), mate-system-tools (>= 1.6.0), mozo (>= 1.6.0), dconf-tools
Section: mate
Priority: optional
Homepage: [http://www.mate-desktop.org/](http://www.mate-desktop.org/)
Description: MATE Desktop Environment
 The MATE Desktop Environment, a non-intuitive and unattractive desktop
 for users, using traditional computing desktop metaphor.
 .
 This package depends on the extra set of applications that are
 part of the official MATE release.

The package mate-desktop-environment_1.6.0.2+raring_all.deb contains the same sentence in the control file.

If you google "The MATE Desktop Environment, a non-intuitive and unattractive desktop" there are dozens of hits. The sentence seems to be everywhere, including here:

[http://sourceforge.net/projects/matede/](http://sourceforge.net/projects/matede/)

It looks to be a joke from the maintainer himself.

**EDIT**: And from two years ago:

[http://www.dedoimedo.com/computers/linux-mint-mate.html](http://www.dedoimedo.com/computers/linux-mint-mate.html)

> MATE is designed to be, and let me quote the author, a non-intuitive and unattractive desktop for users, using traditional computing desktop metaphor.

And from the Linux Mint forums just over two years ago:

[http://forums.linuxmint.com/viewtopic.php?t=86481](http://forums.linuxmint.com/viewtopic.php?t=86481)

---

### Post by buzzingrobot on 2014-01-24
Yes, it's a "joke". Or, intended as such.  

Mate was launched on Arch after the debut of Gnome 3 amid much hostility to that new approach, some reasonable, some not. The remark was apparently an in-joke.

For the sake of prfoessionalism, it should have been removed long ago.

---

### Post by vasa1 on 2014-01-25
Good that someone mocks "intuitive".

---

### Post by buzzingrobot on 2014-01-25
> **vasa1 said:**
> Good that someone mocks "intuitive".

We seem to have redefined "intuitive" to mean "I already learned how to do that".

---

### Post by dadoublem on 2014-01-26
I remember seeing that phrase when MATE first came out. It made me do a double take!

---

### Post by ssam on 2014-01-27
Its a joke from the original announcement.
[https://bbs.archlinux.org/viewtopic.php?id=121162](https://bbs.archlinux.org/viewtopic.php?id=121162)
and it is at
[https://github.com/Perberos/Mate-Desktop-Environment](https://github.com/Perberos/Mate-Desktop-Environment)

---

### Post by lykwydchykyn on 2014-01-28
Self-deprecating hacker humour flops once again with wider audiences...

---

### Post by buzzingrobot on 2014-01-28
> **lykwydchykyn said:**
> Self-deprecating hacker humour flops once again with wider audiences...

You had to be there, I guess.

---

### Post by sffvba[e0rt on 2014-01-29
> **lykwydchykyn said:**
> Self-deprecating hacker humour flops once again with wider audiences...

Imagine that :p

---

### Post by coffeecat on 2014-01-30
> Self-deprecating humour flops with some audiences...

Fixed for that for you!

---

