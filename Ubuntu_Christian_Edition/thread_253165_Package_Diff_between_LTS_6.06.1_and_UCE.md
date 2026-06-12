---
title: "Package Diff between LTS 6.06.1 and UCE"
date: 2006-09-07
forum: Ubuntu Christian Edition
---

### Post by jfryman on 2006-09-07
Hello,

I have a younger brother who is interested in installing UCE not for the fact that it is Linux, but because of the Dansguardian software.

The entire family on that side has been using Ubuntu now since 5.04, and have enjoyed it immensely. However, I was recently asked about the difference in UCE and Stock Ubuntu for Dansguardian.

My question is this: are the packages that are used in UCE stock, or are they custom modified? What would be needed to include these packages in an already installed 6.06.1 system?

I would also be interested in any other packages that deviate from UCE and LTS, to find out if that family is interested in any other package providings.

Thoughts would be greatly appreciated. Thanks.

---

### Post by mhancoc7 on 2006-09-08
> **jfryman said:**
> Hello,

I have a younger brother who is interested in installing UCE not for the fact that it is Linux, but because of the Dansguardian software.

The entire family on that side has been using Ubuntu now since 5.04, and have enjoyed it immensely. However, I was recently asked about the difference in UCE and Stock Ubuntu for Dansguardian.

My question is this: are the packages that are used in UCE stock, or are they custom modified? What would be needed to include these packages in an already installed 6.06.1 system?

I would also be interested in any other packages that deviate from UCE and LTS, to find out if that family is interested in any other package providings.

Thoughts would be greatly appreciated. Thanks.

Thanks for your interest in Ubuntu CE. Ubuntu CE is built directly from Ubuntu 6.06.1 "Dapper Drake". The additions to the default are GnomeSword Bible Software, Dansguardian, Daily Bible Verse, GnuCash, and Automatix. These are all in the standard Ubuntu repos with the exception of Automatix which is a tool to tweak Ubuntu. 

I have also added a GUI for the Dansguardian filter as well as the Ubuntu CE Installer. These are not in the repos and are basically frontends to make things a bit easier for new users. They were both built with Gambas which is in the repos.

There are also a few minor graphical changes.

There are also a few things removed from the standard Ubuntu. They are Gnome Games, Ekiga, GIMP, and the Example Content. These, however, can all be reinstalled with the Ubuntu CE Installer or through Synaptic or Apt-Get of course.

The easiest way to include everything from Ubuntu CE into a Ubuntu 6.06.1 install is to use the [Convert_Me]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/convert-to-latest-version-of-ubuntu.html") script. Please read the directions fully of course. :)


I hope that helps.

God Bless, Jereme

---

