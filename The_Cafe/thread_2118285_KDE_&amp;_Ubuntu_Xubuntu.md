---
title: "KDE &amp; Ubuntu Xubuntu"
date: 2013-02-20
forum: The Cafe
---

### Post by aspergerian on 2013-02-20
I'm not asking a HowTo question. Apparently, digiKam is a KDE program that can be run on computers whose OS is Ubuntu or Xubuntu. An explanation of how a KDE program like [digiKam]("http://www.digikam.org/") runs in Ubuntu or in Xubuntu would be appreciated. I wouldn't try to run Fedora within Ubuntu, yet a KDE program like digiKam can run in Ubuntu. I would like to understand more about this.

---

### Post by snowpine on 2013-02-20
First, it is necessary to distinguish between "distributions" and "desktop environments." A "distribution" such as Ubuntu or Fedora is a separate operating system, and you are correct that you can't easily run Fedora software in Ubuntu (or vice versa). A "desktop environment" (such as Unity, KDE, Xfce, etc.) is simply a "skin" on top of the distribution. Whether you are running Ubuntu, Lubuntu, Kubuntu, or Xubuntu, you are running Ubuntu at the core.

Second, Ubuntu uses a system called "dependency resolution" to ensure that the software you install has everything you need to run. [Take a look at this page]("http://packages.ubuntu.com/quantal/digikam"), which lists the dependencies for digikam. As you can see, when you install digikam, you are also installing things like kde-runtime (runtime components from the official KDE release), libkdecore5 (KDE Platform Core Library), and so forth. In essence, you are converting your Ubuntu system into a hybrid Ubuntu/Kubuntu system by installing the libraries necessary to run KDE apps.

Hope that was helpful, post back if you have any questions. :)

---

### Post by mick222 on 2013-02-20
kde is a desktop enviroment Ubuntu uses the same linux kernal if you want you can install the whole kubuntu desktop in ubuntu but it pulls in lots of kde programs which means lots of duplication. 
I think you could run digicam onfedora as long as the dependancies were satisfied.

---

### Post by mips on 2013-02-20
When people develop applications they use [toolkits]("http://en.wikipedia.org/wiki/List_of_toolkits"), Ubuntu apps are mostly based on GTK. Now KDE and it's associated apps are mostly based on Qt. Thing is you can use GTK in KDE or Qt in Gnome/Unity as all they do is essentially pull in the required software libraries allowing them to function.

So use what you want, it's not a deal breaker.

---

### Post by MadmanRB on 2013-02-20
This is actually normal, as KDE apps can be used in GTK and vice versa.
Its the toolkit and interface that truly makes the two different.
They are aspects of the same OS

---

### Post by mastablasta on 2013-02-21
digikam can also run on windows. but the first time you install any KDE app there oyu will need to download a lot of KDE libraries with it. for exampel i installed skrooge which is about 10-12 MB big but since windows doesn't have KDE libraries it needed to pull those off the net.  they were about 350 MB big. any frther KDE apps took much less downloading since i had the libraries already installed.

---

### Post by aspergerian on 2013-02-21
Thank you, all who have replied.

> **snowpine said:**
> ...A "desktop environment" (such as Unity, KDE, Xfce, etc.) is simply a "skin" on top of the distribution. Whether you are running Ubuntu, Lubuntu, Kubuntu, or Xubuntu, you are running Ubuntu at the core.... Second, Ubuntu uses a system called "dependency resolution" to ensure that the software you install has everything you need to run. [Take a look at this page]("http://packages.ubuntu.com/quantal/digikam"), which lists the dependencies for digikam...

So (almost apparently), I can be working in Xubuntu-desktop -- using Thunderbird, LibeOffice Writer, and Zotero -- and, if need arises, I would be able to run digiKam w/o exiting my Xubuntu-desktop session. Is that supposition correct?

---

### Post by lento_ on 2013-02-21
Yes - you can run programmes from one desktop environment within another. It'll just mean that a few extra bits and bobs get installed to allow the programme to work.

I'm running Ubuntu with Gnome, but typed this text in the KDE text editor Kate, which runs happily inside it.

---

### Post by snowpine on 2013-02-21
> **aspergerian said:**
> Thank you, all who have replied.



So (almost apparently), I can be working in Xubuntu-desktop -- using Thunderbird, LibeOffice Writer, and Zotero -- and, if need arises, I would be able to run digiKam w/o exiting my Xubuntu-desktop session. Is that supposition correct?

Exactly, you've got it!
But why take my word for it---give it a try and see for yourself. ;)

---

### Post by MadmanRB on 2013-02-21
Indeed.
In fact using kde apps in XFCE is not much different then say using iTunes in windows.
or Gimp in windows
or audacity in windows
or clementine in windows
or VLC in windows
etc, etc...

---

