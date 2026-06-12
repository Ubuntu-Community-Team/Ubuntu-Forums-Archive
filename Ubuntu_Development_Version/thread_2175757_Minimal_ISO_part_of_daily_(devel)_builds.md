---
title: "Minimal ISO part of daily (devel) builds?"
date: 2013-09-20
forum: Ubuntu Development Version
---

### Post by grindstone2 on 2013-09-20
Can't find one.  If there isn't one, can this count as a request for one?  Thanks.

---

### Post by VMC on 2013-09-20
How about [Ubuntu Core]("http://cdimage.ubuntu.com/ubuntu-core/daily/current/"). From [wiki]("https://wiki.ubuntu.com/Core").

---

### Post by cariboo on 2013-09-20
> **grindstone2 said:**
> Can't find one.  If there isn't one, can this count as a request for one?  Thanks.

Making a request here won't do any good, as we here on the forums have nothing to do with development. I'd suggest you make a request on the [ubuntu-qa]("ubuntu-quality@lists.ubuntu.com") mailing list. Nick should be able to get the iso created.

> **VMC said:**
> How about [Ubuntu Core]("http://cdimage.ubuntu.com/ubuntu-core/daily/current/"). From [wiki]("https://wiki.ubuntu.com/Core").

The image you linked to, is for ARM processors.

---

### Post by cpatrick08 on 2013-09-21
If you go to [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and find iso for previous release you want,  you can copy link into Web browser, and change raring to saucy and get saucy mini iso, will work for  releases past saucy.

---

### Post by grindstone2 on 2013-09-21
Thank you all for the replies -- much appreciated!

---

### Post by VMC on 2013-09-21
> **cariboo907 said:**
> ...
The image you linked to, is for ARM processors.
From the wiki: > [COLOR=#333333][FONT=Ubuntu Beta] It is available for the **i386, amd64**, and arm architectures.[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]

[/FONT][/COLOR]From Core: [saucy-core-amd64.tar.gz]("http://cdimage.ubuntu.com/ubuntu-core/daily/current/saucy-core-amd64.tar.gz") ,isn't ARM.

---

### Post by wojox on 2013-09-21
They hide them these days. :)

[i386]("http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-i386/current/images/netboot/")
[amd64]("http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/")

---

### Post by cariboo on 2013-09-21
@wojox, the links you provided are for the netboot iso, the wiki page with links to the images are available [here]("https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet"). As the title of the wiki page says, you need an working internet connection in order to use these images.

I haven't tried the netboot images this cycle, but during the raring cycle there wasn't any support for my netbook wireless device which uses the bmcwl driver, so others that need proprietary drivers may have problems using this image.

---

### Post by kansasnoob on 2013-09-22
I think you're looking for the netboot images :confused:

If so I prefer using the QA Tracker:

[http://iso.qa.ubuntu.com/qatracker/milestones/270/builds](http://iso.qa.ubuntu.com/qatracker/milestones/270/builds)

[ATTACH=CONFIG]246426[/ATTACH]

You should be aware though that it sometimes takes kernel updates a few days to hit the mini-isos during development ;)

---

### Post by wojox on 2013-09-22
> **cariboo907 said:**
> but during the raring cycle there wasn't any support for my netbook wireless device which uses the bmcwl driver

lol, I've never tried a wireless install of it.

---

### Post by forcecore on 2013-09-22
> **wojox said:**
> They hide them these days. :)

[i386]("http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-i386/current/images/netboot/")
[amd64]("http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/")

Thanks i searched everywhere 13.10 mini.iso, i use netboot for building my custom Ubuntu 13.10 with System Imaging(formerly Remastersys)

---

