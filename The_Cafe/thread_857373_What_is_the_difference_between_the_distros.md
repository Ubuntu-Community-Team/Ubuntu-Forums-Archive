---
title: "What is the difference between the distros"
date: 2008-07-12
forum: The Cafe
---

### Post by clanky on 2008-07-12
I have been using Ubuntu for a few months now and have been given a fedora CD, when I eventually installed and booted from my portable HD I was quite shocked to find that in terms of looks it was exactly the same.

I have both the Gnome and KDE versions installed and there is very little difference in looks between either of these, so what is the difference in terms of functionality?  Is software compatible with various distros or is it specific to one?

---

### Post by Lostincyberspace on 2008-07-12
It depends from distro to distro and even version to version.

Different distro will have impliment something before the other ones normaly only have that exsclusive for up to 1 release maybe even less.

An example
Fedora includes a combined library for fire fox, openoffice, and gnome tools, while none other have it. This is planed for the other major competitors in their next releases though.

---

### Post by Canis familiaris on 2008-07-12
Fedora uses RPM i.e. Read Hat Package Management
Ubuntu uses DEB i.e. The Debian Package Management

---

### Post by clanky on 2008-07-12
> **Anurag_panda said:**
> Fedora uses RPM i.e. Read Hat Package Management
Ubuntu uses DEB i.e. The Debian Package Management

What is the difference?  Does this mean that software for ubuntu will not run in fedora or are there versions of most software for both distros.  Is there a different process for installing new software?

---

### Post by ryaxnb on 2008-07-12
> **clanky said:**
> I have been using Ubuntu for a few months now and have been given a fedora CD, when I eventually installed and booted from my portable HD I was quite shocked to find that in terms of looks it was exactly the same.

I have both the Gnome and KDE versions installed and there is very little difference in looks between either of these, so what is the difference in terms of functionality?  Is software compatible with various distros or is it specific to one?

Distros look superficially similar, but the software is quite different. Try using KWord, Konqueror or Amarok after being used to Rhythymbox, AbiWord, or Epiphany, or try GNOME/KDE-uncentric software like Songbird, Firefox, and OpenOffice.org Writer, and you'll see a dramatic difference. Fedora is quite similar on first glance to Ubuntu, but the software management is very different, and configuration, settings and available software are different too. Not to mention the internals are set up differently. And the exact same software package is not usually compatible, but software can be converted to work on both fairly easily using tools such as "alien".
Also note that Fedora is very similar to Ubuntu in some ways. A more dramatically different distro would be, say, Sabayon linux, PCLinux OS MiniMe, or Puppy Linux. Also, other very dissimilar distros are CentOS, designed for servers, Slackware, designed for experts and advanced users, and Arch, also designed for experts.

---

### Post by Canis familiaris on 2008-07-12
> **clanky said:**
> What is the difference?  Does this mean that software for ubuntu will not run in fedora or are there versions of most software for both distros.  Is there a different process for installing new software?

Basically both use different packaging tools for installing, updating, removal and maintaining of software in the Linux distribution.
Both RPM and APT(The Debian Package Manager) do the same thing in different ways and are not compatible with each other. i.e. you cannot install an RPM in your Ubuntu system, well at least not before converting th RPM into Debian/Ubuntu package and vice-versa.
To make things worse even Debian and Ubuntu package management are not completely compatible.
The creators of Ubuntu for example pre package most software in their package format of as much software possible in the repos to ease software installation. So do the creators of Fedora.
So you get your software albeit in different method of distribution.

Since I'm not very good in explaining things, I hope these links may help:

[http://en.wikipedia.org/wiki/Package_manager](http://en.wikipedia.org/wiki/Package_manager)
[http://en.wikipedia.org/wiki/RPM_Package_Manager](http://en.wikipedia.org/wiki/RPM_Package_Manager)
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

---

