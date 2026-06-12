---
title: "Build a deb?"
date: 2005-04-26
forum: The Cafe
---

### Post by somuchfortheafter on 2005-04-26
Well it seems suse has a new toy
[http://www.novell.com/coolsolutions/feature/11793.html](http://www.novell.com/coolsolutions/feature/11793.html)
this allows users to build rpms rather easily and well it seemed like a good idea if we had an ubuntu version for debs that would allow apps that many people dont hear about to have deb packages, and then through a submission service they could be included into the ubunty repository tree

---

### Post by DJ_Max on 2005-04-26
From that that article is showing, it's just building an RPM binary from an RPM source. Thats nothing new, you can do the same with .deb's/

Building a RPM source from a tar.gz source is the hard part.

---

### Post by poofyhairguy on 2005-04-26
Building a deb is VERY hard. I tried, and its quite a process (well...not for a truw blue unix admin). If debs were a little easier to build, I would make a lot (wifiradar anyone?)

---

### Post by az on 2005-04-26
"RPM is now considered the 'standard' for application and system packaging by most Linux distributions. Novell SUSE LINUX is one of those distributions that has standardized on RPM."

Which is why time after time, big migrations to linux are done using debian because the package management is so much better.


"Novell SUSE LINUX provides a utility called build that streamlines the RPM creation"

Whatever.

apt-cache show debhelper.

---

### Post by TravisNewman on 2005-04-26
azz-- right on! I THINK (don't hold me to this) that there are more Debian based distros than there are RPM based distros. Is this correct? I know there are literally hundreds of debian based distros. If so, RPM is NOT the standard for most distributions.

Great that Novell provides that utility, but debian has had a similar utility for a while now.

---

### Post by az on 2005-04-26
[QUOTE=poofyhairguy]Building a deb is VERY hard. I tried, and its quite a process (well...not for a truw blue unix admin). If debs were a little easier to build, I would make a lot (wifiradar anyone?)[/QUOTE]

If I had more than a minute just now, I would
1. Check than wifiradar is GPL.
2.  Scan the debian-mentors mailling list to see if someone intends on packageing it.

Then you can give take a crack at it.  Debian-mentors should be able to give you a hand.

GO FOR IT!

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=azz]If I had more than a minute just now, I would
1. Check than wifiradar is GPL.[/QUOTE]

Its GPL.

[QUOTE=azz]
2.  Scan the debian-mentors mailling list to see if someone intends on packageing it.

Then you can give take a crack at it.  Debian-mentors should be able to give you a hand.

GO FOR IT![/QUOTE]

[http://lists.debian.org/debian-mentors/](http://lists.debian.org/debian-mentors/)

Is this what you are talking about?

I think I will try to package it. It sounds like a good challenge.

---

### Post by TravisNewman on 2005-04-26
Rock on dude, tell us how it goes!

---

### Post by az on 2005-04-27
[QUOTE=poofyhairguy]Its GPL.



[http://lists.debian.org/debian-mentors/](http://lists.debian.org/debian-mentors/)

Is this what you are talking about?

I think I will try to package it. It sounds like a good challenge.[/QUOTE]


You rock!

I have more than just a minute, right now.  If wifiradar is just a binary, it should be straightforward to package.


Debian developers maintain packages and decide debian issues.  There are certain criteria to becoming a DD.  The first step is to read the debian maintainers guide.  The second is to package an application and ask a DD to sponsor it's upload to the archive.

You can quit there and never apply to becoming a DD.  Many official debian packages are maintained by non-debian developer people who just have their packages sponsored by debian mentors.

They have an irc channel too.  _Very_ helpful.  Much less busy (rude) than the debian-devel irc (or mailing list, for that matter)

Check to see the debian developers' corner page where they list packages that have been requested.  Maybe someone is already working on wifiradar.  You can also check to see if there are some packages that have been abandoned that you want to adopt (if you have the free time to keep tabs on the upstream and tweak the package every now and then.  (answer bug reports)

If you package wifiradar, you can then ask to be the Ubuntu developer.  Go to the wiki and take a look at the process of getting on board the ubuntu developper team.

I am enthusiastic.

EDIT:
[http://www.tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/](http://www.tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/)
[http://www.sdn.or.id/share/Debian-Doc/manuals/maint-guide/index.en.html#contents](http://www.sdn.or.id/share/Debian-Doc/manuals/maint-guide/index.en.html#contents)
[http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper](http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper)

---

### Post by fng on 2005-04-27
[QUOTE=poofyhairguy]Building a deb is VERY hard. I tried, and its quite a process (well...not for a truw blue unix admin). If debs were a little easier to build, I would make a lot (wifiradar anyone?)[/QUOTE]

Like most people :)
openttd, xcom ufo, ... (there must be a gazzilion games out there not in the universe/multiverse  repo)

---

### Post by oddabe19 on 2005-04-27
[QUOTE=poofyhairguy]Building a deb is VERY hard. I tried, and its quite a process (well...not for a truw blue unix admin). If debs were a little easier to build, I would make a lot (wifiradar anyone?)[/QUOTE]
 *Cough* use checkinstall.... sudo apt-get install checkinstall
./configure
make
sudo checkinstall
*end cough*

---

### Post by sas on 2005-04-27
[QUOTE=oddabe19]*Cough* use checkinstall.... sudo apt-get install checkinstall
./configure
make
sudo checkinstall
*end cough*[/QUOTE]
 check installs aren't really redistributable by someone like ubuntu though are they? They require specific things be there that checkinstalls don't do iirc.

---

### Post by az on 2005-04-27
Would you like a *cough* Autopackage *cough* lozenge?

We *may* see autopackage integration with Ubuntu in the future.

---

### Post by az on 2005-04-28
_This_ is great:

[http://liw.iki.fi/liw/talks/debian-packaging-tutorial.pdf](http://liw.iki.fi/liw/talks/debian-packaging-tutorial.pdf)

[http://liw.iki.fi/liw/log/2005-04.html#20050427b](http://liw.iki.fi/liw/log/2005-04.html#20050427b)

---

### Post by jdong on 2005-04-28
[QUOTE=poofyhairguy]Building a deb is VERY hard. I tried, and its quite a process (well...not for a truw blue unix admin). If debs were a little easier to build, I would make a lot (wifiradar anyone?)[/QUOTE]

Building debs is as easy as figuring out induced current in an oddly shaped non-uniformly charged object after applying Ampere's Law... ;)


Anyway, checkinstall does make that side of life very easy.

Autopackage won't help...

---

