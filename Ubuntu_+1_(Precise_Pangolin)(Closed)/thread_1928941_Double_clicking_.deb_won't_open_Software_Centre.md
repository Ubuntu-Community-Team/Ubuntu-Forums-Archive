---
title: "Double clicking .deb won't open Software Centre"
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-21
If I double-click on any .deb file, the Software Centre window only flashes on the screen for a single moment and disappears without any error message.

If I run Software Centre from Launcher/Dash/Terminal, it opens normally.

---

### Post by mc4man on 2012-02-21
It's possibly this bug - 
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/827615](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/827615)

Take a look in /var/crash for a software-center .crash

If desired open a terminal & go, obviously replace 'whatever'

software-center /path/to/whatever.deb

Install gdebi & use that instead (gdebi will also produce a crash atm but still works

---

### Post by VMC on 2012-02-21
> **mc4man said:**
> It's possibly this bug - 
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/827615](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/827615)

Take a look in /var/crash for a software-center .crash

If desired open a terminal & go, obviously replace 'whatever'

software-center /path/to/whatever.deb

Install gdebi & use that instead (gdebi will also produce a crash atm but still works

I had the same problem for several current iso's. thanks for the bug link. I will 'it affects me too' on that report.

I never thought of using gdebi. I always log onto the dir that has my debs and issue 'dpkg -i *'

---

### Post by mc4man on 2012-02-21
> **VMC said:**
> I had the same problem for several current iso's. thanks for the bug link. I will 'it affects me too' on that report.

I never thought of using gdebi. I always log onto the dir that has my debs and issue 'dpkg -i *'
Gdebi is great when you have a .deb where possibly some dependencies aren't installed but available in your enabled sources. It will download & install them

dpkg can't do that but it will do anything you tell it do which is also quite useful

---

### Post by VMC on 2012-02-21
> **mc4man said:**
> Gdebi is great when you have a .deb where possibly some dependencies aren't installed but available in your enabled sources. It will download & install them

dpkg can't do that but it will do anything you tell it do which is also quite useful

Yes, here's the scenario that happens to me. I execute 'dpkg -i *' then it installs the program, but says there were errors (if there are any). 

Then it suggests running 'apt-get -f install' to fix the problems.

---

### Post by shuttleworthwannabe on 2012-02-22
> sudo dpkg -i <packagename>
is what I use until the bug is fixed.

---

### Post by prusswan on 2012-02-22
> **mc4man said:**
> Gdebi is great when you have a .deb where possibly some dependencies aren't installed but available in your enabled sources. It will download & install them

dpkg can't do that but it will do anything you tell it do which is also quite useful

Gdebi doesn't seem to be aware of virtual packages, I had to use dpkg in cases where Gdebi refused to install.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-04
This was fixed with one of the recent updates, so I marked it as [SOLVED]

---

