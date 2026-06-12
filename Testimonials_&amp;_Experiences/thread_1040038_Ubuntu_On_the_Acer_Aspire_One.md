---
title: "Ubuntu On the Acer Aspire One"
date: 2009-01-15
forum: Testimonials &amp; Experiences
---

### Post by Vince4Amy on 2009-01-15
So after playing with loads of different distros on the Aspire One and settling with Fedora for a while I've concluded that after tweaking Ubuntu is actually running the best on this. I don't use Ubuntu usually as I've never had it run to good on my systems, but on the Aspire one it's quite impressive.

When I decided to try Ubuntu I downloaded 8.04 as I don't want to be upgrading every 6 months, and I like the mix of stability and sometimes feature updates that will happen throughout the course of the release. 

I'm happy with the way this is running though it did require quite a few tweaks to get it just right, I assume it's because it's obviously an older version with an older kernel so hardware support is not as strong. 

Here are some of the things I did to get this running smoothly:

Remove a lot of packages included with the base install, most of them are completely useless to me, but this is because I normally use distros which allow you to choose packages on install time. No big deal.

Install madwifi to get the wireless working.

Tweak xorg.conf

Profile the boot sequence, remove some startup services

Change the hard drive load cycle because it was parking way too often, I think this is something that needs to be addressed if it's not already in newer releases. 

Used a fix pulseaudio guide I found on this forum

Here are the resources I used:

[Pulse Audio Tweaks](http://ubuntuforums.org/showthread.php?t=789578)

[Ubuntu Aspire One Gudei](https://help.ubuntu.com/community/AspireOne)

I also upgraded Openoffice using the deb version on the official Openoffice website.

Everything is working awesome now and I'm pleased with the way that Ubuntu is performing on here. This is of course after tweaking but 177MB RAM usage when idle is not bad at all considering it's quite a feature rich distro.

There is one thing I'd like to know though and that is how to disable some excess ttys. It appears that Ubuntu doesn't use init so I'm not quite sure on how to change these settings.

Anyway I now have a use for Ubuntu again and a lot has changed since I last used it full time on 6.06.

---

### Post by halovivek on 2009-01-15
Acer does not support linux. But with this forum i got helped and done more things.

---

### Post by flaggh on 2009-01-15
> **Vince4Amy said:**
> 
There is one thing I'd like to know though and that is how to disable some excess ttys. It appears that Ubuntu doesn't use init so I'm not quite sure on how to change these settings.


This post may be helpful
[http://ubuntuforums.org/showpost.php?p=4637895&postcount=350]("http://ubuntuforums.org/showpost.php?p=4637895&postcount=350")

---

### Post by waspbr on 2009-01-15
a few weeks ago I've bumped into this ubuntu variation that is supposed to be tweaked for the acer aspire, it may be worth checking out: [http://www.raneri.it/blog/eng/index.php/2008/12/26/linux4one-ubuntu-for-the-acer-aspire-one/]("http://www.raneri.it/blog/eng/index.php/2008/12/26/linux4one-ubuntu-for-the-acer-aspire-one/")

---

### Post by stchman on 2009-01-15
I have Intrepid installed on my Aspire One and it runs very well.  I only needed to do a few tweaks to get the wireless and SD card readers working perfectly.  The video with Compiz effects worked OOB.  I eventually disabled desktop effects as they are too resource hungry and netbook remix needs them disabled.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

---

### Post by Vince4Amy on 2009-01-15
> **stchman said:**
> I have Intrepid installed on my Aspire One and it runs very well.  I only needed to do a few tweaks to get the wireless and SD card readers working perfectly.  The video with Compiz effects worked OOB.  I eventually disabled desktop effects as they are too resource hungry and netbook remix needs them disabled.

Yes same sort of tweaks that were done on 8.04. I also had to disable compiz and I don't think that Netbook Remix is necessary the Gnome desktop is good enough. 

Also I locked the Kernel version because of the wireless drivers.

---

### Post by stchman on 2009-01-15
> **Vince4Amy said:**
> Yes same sort of tweaks that were done on 8.04. I also had to disable compiz and I don't think that Netbook Remix is necessary the Gnome desktop is good enough. 

Also I locked the Kernel version because of the wireless drivers.

I like netbook remix.  I think it is made for the smaller screen.

---

### Post by 3rdalbum on 2009-01-16
> **halovivek said:**
> Acer does not support linux.

Acer supports Linux on certain hardware. They ship a modified Linpus Lite on their Aspire One machines, and in some regions they have Linux-preinstalled notebooks too.

---

### Post by Vince4Amy on 2009-01-16
Linpus Lite that it came with was quite fast, but it was also quite useless. When I enabled the XFCE menu on right click and went into the package manager I found out that it was indeed based on a very old version of Fedora (7 or 8 I'd say) and the software was mostly very outdated and not practical for what I wanted to use it for.

---

