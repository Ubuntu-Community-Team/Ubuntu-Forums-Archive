---
title: "HOWTO:Add WebP (weppy) support to GIMP."
date: 2014-05-25
forum: Tutorials
---

### Post by ron998 on 2014-05-25
Hi
There's an old locked thread about adding WebP support to GIMP.
Here ---> [http://ubuntuforums.org/showthread.php?t=1809284&highlight=webp](http://ubuntuforums.org/showthread.php?t=1809284&highlight=webp)

That PPA hasn't been updated for ages, but the 12.04 Precise version seems to work OK with 14.04 Trusty. ;)

I've created a deb file from the old PPA.
It's in the attachment below.
Download and untar it first.

Install libwebp
```
sudo apt-get update; sudo apt-get -y install libwebp-dev
```
Install the deb
```
sudo dpkg -i gimp-webp_0.2-1.deb
```

Then with GIMP it will be possible to import and export webp files.
:cool:

This works OK for me with 32 bit system.
I don't have access to a 64 bit system, but maybe somebody else can test it and leave feedback.

---

### Post by Mark de J on 2014-05-28
For me it isn't working on a 64 bit system.

---

### Post by ron998 on 2014-05-28
> **Mark de J said:**
> For me it isn't working on a 64 bit system.
Hi
I've attached the original 64-bit deb from the launchpad page.

---

### Post by Trevor_Grant on 2015-01-22
Sorry to raise the dead on this post, but the 64 bit package worked for me in 14.10

Thanks!

---

### Post by jacek-filipek on 2015-02-23
> **ron998 said:**
> Hi
I've attached the original 64-bit deb from the launchpad page.

Thank You! With Ubuntu 14.10 it's works.

---

### Post by George Edison on 2015-06-07
Hey everyone. Sorry for the long delay in getting up-to-date packages into the PPA. I uploaded builds for Trusty, Utopic, Vivid, and Wily, which you can add to your system with:

```
sudo add-apt-repository ppa:george-edison55/webp
```

Once added, simply install the "gimp-webp" package and you will be able to use the plugin. I've also switched to CMake and moved the plug-in over to GitHub with the intention of adding some new features in the future and maybe adjusting the interface a bit.

---

### Post by hotel_Peru_hostal on 2015-07-06
i working in 15.04   64 bits  but don´t work

---

### Post by nataly2 on 2015-07-30
> **George Edison said:**
> Hey everyone. Sorry for the long delay in getting up-to-date packages into the PPA. I uploaded builds for Trusty, Utopic, Vivid, and Wily, which you can add to your system with:

```
sudo add-apt-repository ppa:george-edison55/webp
```

Once added, simply install the "gimp-webp" package and you will be able to use the plugin. I've also switched to CMake and moved the plug-in over to GitHub with the intention of adding some new features in the future and maybe adjusting the interface a bit.

I've imported your PPA. Trying to execute
```
$ sudo apt-get install gimp-webp
```
and got message:
```
gimp-webp package not found
```

---

