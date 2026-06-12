---
title: "Ubuntu on a netbook. Wait for 12.10?"
date: 2012-10-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by penubag on 2012-10-08
My friend has a really slow 2 yr old Toshiba netbook with 1GB of RAM.  She is annoyed how slow Windows Starter runs on it so I suggested  switching to Ubuntu. Since 12.10 is due in a few days, I'm not sure if  we should wait before installing Ubuntu or if we should install it now  in order to use Unity 2D. For a low-end device, should we use Unity 2D  or use Unity 3D on 12.10 since Unity 2D is no longer present in 12.10? I  understand Unity 3D has been greatly improved but is it faster than  Unity 2D in the LTS version for a low-spec'd device?

---

### Post by cariboo on 2012-10-09
> **penubag said:**
> My friend has a really slow 2 yr old Toshiba netbook with 1GB of RAM.  She is annoyed how slow Windows Starter runs on it so I suggested  switching to Ubuntu. Since 12.10 is due in a few days, I'm not sure if  we should wait before installing Ubuntu or if we should install it now  in order to use Unity 2D. For a low-end device, should we use Unity 2D  or use Unity 3D on 12.10 since Unity 2D is no longer present in 12.10? I  understand Unity 3D has been greatly improved but is it faster than  Unity 2D in the LTS version for a low-spec'd device?

I'd rather you installed 12.04 on that netbook, as Quantal has problems that may not be fixed by the release date. One other thing I'd like to suggest, is that if you do install Ubuntu on your friends netbook, be prepared to support it personally for at least a couple of years. installing it for someone, then telling them to use the forum for support is almost guaranteed to have them asking you to reinstall windows, in a very short time.

---

### Post by penubag on 2012-10-09
Thank you for your suggestion. I will install 12.04

---

### Post by emk2203 on 2012-10-09
> **penubag said:**
> My friend has a really slow 2 yr old Toshiba netbook with 1GB of RAM.  She is annoyed how slow Windows Starter runs on it so I suggested  switching to Ubuntu. Since 12.10 is due in a few days, I'm not sure if  we should wait before installing Ubuntu or if we should install it now  in order to use Unity 2D. For a low-end device, should we use Unity 2D  or use Unity 3D on 12.10 since Unity 2D is no longer present in 12.10? I  understand Unity 3D has been greatly improved but is it faster than  Unity 2D in the LTS version for a low-spec'd device?
I am running Quantal (12.10) on several computers, some of them fairly old, and performance is a mixed bag.

On two laptops (Dell C840 from 2002 with a Nvidia Geforce4 440 Go, DirectX 7), standard 12.10 is unusable because the graphics performance is so bad that menus literally take a minute to appear, CPU maxes out, in short: not recommended.

On another machine from 2002, but a desktop with a Nvidia Geforce 6600 GT added (also from 2004, so 8 years old graphics, but DirectX 9), 12.10 runs well and better than the XP boot option.

I am currently answering from this machine.

---

### Post by sonnet on 2012-10-09
> **cariboo907 said:**
> I'd rather you installed 12.04 on that netbook, **_as Quantal has problems that may not be fixed by the release date._** One other thing I'd like to suggest, is that if you do install Ubuntu on your friends netbook, be prepared to support it personally for at least a couple of years. installing it for someone, then telling them to use the forum for support is almost guaranteed to have them asking you to reinstall windows, in a very short time.

Are you talking about unity-related issues, or other kind of issues which affect all the releases?

---

### Post by penubag on 2012-10-09
> **emk2203 said:**
> On two laptops (Dell C840 from 2002 with a Nvidia Geforce4 440 Go, DirectX 7), standard 12.10 is unusable because the graphics performance is so bad that menus literally take a minute to appear, CPU maxes out, in short: not recommended.

How does unity 2d fair on that machine?

---

### Post by Seb71 on 2012-10-09
For netbooks, a better choice might be Xubuntu 12.04.

---

### Post by VinDSL on 2012-10-09
> **penubag said:**
> My friend has a really slow 2 yr old Toshiba netbook with 1GB of RAM.[...]

I'm not sure if  we should wait before installing Ubuntu or if we should install it now[...]

I  understand Unity 3D has been greatly improved but is it faster than  Unity 2D in the LTS version for a low-spec'd device?
You NEED to go the 2D route, which would necessitate 12.04 LTS.  However, may I strongly suggest...

Peppermint OS (a Lubuntu fork) would be a much better way go!

LINKAGE:  [http://peppermintos.com/](http://peppermintos.com/)

That's what I run on my netbook, and USB-stick installs. You can't beat it!

You'll still be running Ubuntu, but it's a very special implementation, specifically designed for speed, efficiency, and beauty on hardware with limited resources. ;)

---

### Post by penubag on 2012-10-09
Wow so many options, that's what's great about Linux. Peppermint looks pretty nice and so does Lubuntu. I'll see how Ubuntu 2D fairs since we already downloaded the iso and if we want to try something else, we'll look into Peppermint.

---

### Post by pqwoerituytrueiwoq on 2012-10-09
i have been running xubuntu 12.10 for a couple weeks now only had 2 apps crash on me
file-roller (extract here/extract to from the right click menu in the file browser)
i have has thunar crash 2 or 3 times (one was related to a file-roller crash i think) the other happened when displaying pictures on my sd card as thunmbnails (255 of them)

---

### Post by KBD47 on 2012-10-10
If it must be Ubuntu, and you want no headaches, and don't want to become their personal technician:
Ubuntu 12.04, run all the updates, then set it only to check for security updates--less chance of borkage for the user, less calls to you. Use either Unity 2D or Gnome Classic/Fallback, these run much lighter and cooler and faster on a netbook than Unity 3D.
  If you want to try something else, Debian runs very light on a netbook. There are few Debian forks that are easier to install than vanilla Debian and have codecs, etc., like SalineOS, SimplyMepis, Linux Mint Debian, and SolusOS. Mint Maya Xfce is impressive as an Ubuntu spin. Fuduntu is a Redhat fork but made for netbooks and is nice.

---

### Post by jerrylamos on 2012-10-10
1 GB is running fine on this Acer Aspire 1 netbook.  

Currently running "Unity" for testing purposes.  I prefer to install Ubuntu then do 

sudo apt-get install lxde

then log out, log back in choosing lxde.  I get applications I use such as Libre Office, Firefox, gedit, files (Nautilus), etc. without the candy store Unity/compiz.  If I should want to check some of these features out I just log in Ubuntu (unity/compiz).

Now this is 1.666 gHz dual processors which is likely the major difference to the configuration you're looking at.  $250 from Walmart.

I could install Lubuntu, but then I'd install Libre, Firefox, gedit, ... so it's just easier to install Ubuntu.  Disk space no problem here.  Impression I get is Lubuntu isn't LTS and could get dropped?

---

