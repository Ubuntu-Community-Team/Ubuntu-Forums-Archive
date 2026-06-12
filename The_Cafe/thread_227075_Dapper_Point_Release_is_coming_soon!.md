---
title: "Dapper Point Release is coming soon!"
date: 2006-08-01
forum: The Cafe
---

### Post by ubuntu_demon on 2006-08-01
From [http://permalink.gmane.org/gmane.linux.ubuntu.devel.announce/158](http://permalink.gmane.org/gmane.linux.ubuntu.devel.announce/158) :

[quote=Colin Watson]
As discussed in [http://wiki.ubuntu.com/DapperPointReleaseProcess](http://wiki.ubuntu.com/DapperPointReleaseProcess),, we’ll be producing the first point release of Dapper (to be called Ubuntu 6.06.1 LTS) very soon, probably this week; this will be built from dapper, dapper-security, and dapper-updates, and will consist of updated desktop, alternate, and server CD images.

On the development release front, we expect to start preparing the next milestone release of Edgy (Knot 2) late this week.
[/quote]

I blogged this here :
[http://ubuntudemon.wordpress.com/2006/08/01/dapper-point-release-is-coming-soon/](http://ubuntudemon.wordpress.com/2006/08/01/dapper-point-release-is-coming-soon/)

---

### Post by Kernel Sanders on 2006-08-01
What is it? Is it an official Ubuntu update to Dapper? Kinda like Windows XP + a service pack? Or is it Dapper, plus some third party addons?

---

### Post by christhemonkey on 2006-08-01
From the site he linked to:
> Point release:
Methods and processes for releasing updated Ubuntu 6.06 CD images to correct (at least) installer bugs.


---

### Post by frenkel on 2006-08-01
Like Windows XP + a service pack.

---

### Post by Kernel Sanders on 2006-08-01
Apologies for my noobness :(

---

### Post by bb002 on 2006-08-01
I think it leans towards a service pack.  instead of downloading the original dapper cd then doing "sudo apt-get update && sudo apt-get upgrade" to get the most up-to-date packages and having a huge download size. You will be downloading a already updated dapper iso and have a much smaller update size in the future compared to the original dapper iso.

---

### Post by Brunellus on 2006-08-01
I welcome the point release.  I'm having headaches installing plain vanilla dapper on my old thinkpad...the plain breezy kernel works, but the plain dapper one freaks out when it meets my PCMCIA hardware. Updated dapper kernels work fine.

Effectively, I have to do a minimal install of breezy, then dist-upgrade to dapper to get a usable system.  Not ideal!  The point release would have solved this.

---

### Post by G Morgan on 2006-08-01
So the live disc installer may actually work this time then ;). TBH I'm more than happy with the alternate installer, far better in my estimation.

---

### Post by John.Michael.Kane on 2006-08-01
Will this point release include a kernel upgrade? Or is that for edgy only.

---

### Post by ubuntu_demon on 2006-08-01
The fix for "the worst bug in Dapper" :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367)
won't make this Point Release. I hope it makes a future Point Release. At least its fixed for Edgy AFAIK.

---

### Post by ubuntu_demon on 2006-08-01
> **SD-Plissken said:**
> Will this point release include a kernel upgrade? Or is that for edgy only.
This release will probably contain the current Dapper kernel (unless there's a kernel update this week). 

The current Dapper kernel is a different one from the one on the original Dapper (6.06) cd image.

---

### Post by MetalMusicAddict on 2006-08-01
Will this also go for X/Kubuntu?

---

### Post by ubuntu_demon on 2006-08-01
> **MetalMusicAddict said:**
> Will this also go for X/Kubuntu?
I have no idea.

---

### Post by ember on 2006-08-01
Sounds promising - I hope that will fix my USB boot crash problem. I guess, I'll give it a try.

---

### Post by 3rdalbum on 2006-08-02
They should have called it Ubuntu 6.06.07 LTS!

---

### Post by AlphaMack on 2006-08-02
Let's hope it will boot on my old clamshell iBook.

---

### Post by ubuntu_demon on 2006-08-02
> **3rdalbum said:**
> They should have called it Ubuntu 6.06.07 LTS!
6.06 means that Dapper released in June 2006
6.06.1 means that this is an update to the release in June 2006

Since Dapper is a Long Time Support release there will probably be another Point Release in the future. The naming scheme still needs to work in the future (for example in 2007).

---

### Post by ubuntu_demon on 2006-08-02
> **3rdalbum said:**
> They should have called it Ubuntu 6.06.07 LTS!
6.06 means that Dapper released in June 2006
6.06.1 means that this is an update to the release in June 2006

Since Dapper is a Long Time Support release there will probably be another Point Release in the future. The naming scheme still needs to work in the future (for example in 2007).

---

### Post by MetalMusicAddict on 2006-08-03
I wonder if the ship-it cds will be repressed?

---

### Post by ubuntu_demon on 2006-08-04
> **MetalMusicAddict said:**
> I wonder if the ship-it cds will be repressed?
AFAIK the next batch of shipit cd's will be 6.06.1. I don't know when they start shipping or arrive.

---

### Post by Brunellus on 2006-08-04
> **MetalMusicAddict said:**
> I wonder if the ship-it cds will be repressed?
oh.  re-PRESSED.  when you said "repressed" I had this image of goons with Ubuntu armbands hunting down dapper shipit cds and smashing them.

---

