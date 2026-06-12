---
title: "Why are repos for different versions of Ubuntu organized like this?"
date: 2011-04-13
forum: The Cafe
---

### Post by TheHimself on 2011-04-13
Some of the new software that are included in newer versions of Ubuntu are not included in older repositories for no obvious reason. Some software need substantial new libraries (like newer versions of libgtk) to be installed but I don't think that's always the case. 

I have Jaunty on an old computer which runs pretty well. However I'm not able to install  Empathy, Shotwell, Emacs23 and the newest version of Java, among other things. Can somebody tell me why?  

Of course one can download individual debs (which are not always available) but that's not always convenient and installing the dependencies can become very tedious.

---

### Post by doorknob60 on 2011-04-13
Because they're older, Canonical can't continue to provide updates (and fix the inevitable bugs that come with them) forever. If you want new stuff, upgrade to the latest Ubuntu or use a rolling release like Debian Testing or Arch.

---

### Post by Enigmapond on 2011-04-13
There is no more support for Jaunty. You need to do a fresh install of at least 10.04 at this point.

---

### Post by Paqman on 2011-04-13
> **Enigmapond said:**
> There is no more support for Jaunty. You need to do a fresh install of at least 10.04 at this point.

This.

Besides not being able to install recent software, your Jaunty machine is no longer receiving security updates. If it's connected to the internet, you should upgrade immediately.

Longer term, if you want up-to-date packages then your should consider getting on the six-monthly update cycle. Other than that your option is to use an LTS release and enable backports. You can use PPAs to get updated versions of any critical packages that aren't updated in either the normal or backports repos.

Wikipedia has a nice [list of Ubuntu releases]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions") showing what's still supported, and till when.

---

### Post by Aquix on 2011-04-13
But you do get security updates for Lucid 10.04? I already have backports enabled. This made me unsure.

---

### Post by Enigmapond on 2011-04-13
> **Aquix said:**
> But you do get security updates for Lucid 10.04? I already have backports enabled. This made me unsure.

Yes...for quite some time yet...no worries.. :)

---

### Post by 3rdalbum on 2011-04-13
> **TheHimself said:**
> Some of the new software that are included in newer versions of Ubuntu are not included in older repositories for no obvious reason.

Ubuntu is a **stable release** distribution. That means, no new major versions of software get put into existing distributions. Only bugfixes and security fixes.

If you're the CTO of a company using Ubuntu desktops, you don't want to run updates and then find that the new software has bugs in it that you didn't expect. Or, even worse, you run updates and then get a dozen calls from workers complaining that the feature they want has been moved and they can't find it anymore. Or worse yet, the new version of the software has a new feature that causes it to probe for other services running on the network, which (multiplied by a dozen desktops) causes the network to grind to a halt.

New software does sometimes get packaged in PPAs for older distributions, but Jaunty is too old for anyone to still do this. Update to 10.04 at least; and if you really want/need the latest software, you should keep on the latest version of Ubuntu.

---

### Post by TheHimself on 2011-04-14
OK, so maybe I should ask: should I upgrade to newer versions? My computer has a 1.7 MHz Pentium M and 2 GB of RAM and under XUbuntu 9.04 it runs fast. I've been afraid it may be too old for the newer releases.

---

### Post by plucky on 2011-04-14
> **TheHimself said:**
> OK, so maybe I should ask: should I upgrade to newer versions? My computer has a 1.7 MHz Pentium M and 2 GB of RAM and under XUbuntu 9.04 it runs fast. I've been afraid it may be too old for the newer releases.

Yes,I have Xubuntu 10.04.2 running on a PIII 600Mhz,384Mb so you should be Ok.

Maybe you should stick with the LTS versions,the latest of which is  Xubuntu Lucid 10.04.02.

See [Here](http://cdimage.ubuntu.com/xubuntu/releases/10.04.2/release/)

Good Luck

---

### Post by CraigPaleo on 2011-04-14
The devs have been trimming the fat of Xubuntu lately. 11.04 is lighter than previous versions, which is good for having the latest software on older hardware.

---

### Post by TheHimself on 2011-04-16
I think I've not got the answer to my original question. I understand the idea of stable releases but I think (in the name of free software!) one should have the option of upgrading to or not upgrading to any version one wants. In other words there should be a repository with different stable versions of all packages available and which doesn't make you install the latest version. One would simply choose the version which has the best ratio of functionality over dependencies for them.

---

### Post by Paqman on 2011-04-16
> **TheHimself said:**
> In other words there should be a repository with different stable versions of all packages available and which doesn't make you install the latest version.

That would be a bit of a nightmare for devs. Most projects have _one_ stable version of their software that they support, and a development branch/version that's under active development. You won't get projects to start supporting multiple stable versions. The first thing you always get told if you try and file a bug against an old version is to install the new one.

---

### Post by CraigPaleo on 2011-04-16
I've seen it done with some applications. When I used PCLOS, there were two versions of FF in the repo. 

You'll get into trouble having more than one version of libraries though. So those should be kept to one.

---

