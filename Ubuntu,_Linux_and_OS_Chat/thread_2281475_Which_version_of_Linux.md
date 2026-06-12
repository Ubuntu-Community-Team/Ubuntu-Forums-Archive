---
title: "Which version of Linux?"
date: 2015-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by mlvmhn on 2015-06-07
I am going to buy a HP 550 laptop, and wonder which version of Linux i shall install?

Now i run Ubuntu 15.04 on my stationary station w/ 4 GB Ram, and i think this runs fine. 

From what i can see, this laptop has only 2 GB of Ram installed? And a Core 2 Duo processor?

Since i already runs Ubuntu, it feels like a good idea to also run it on this laptop. 

is this a good idea?

The main usage area for this computer is to run qBittorrent and watch movies from it usin VLC. 

Will this work fine with this laptop?

---

### Post by sudodus on 2015-06-07
Search the internet for ***HP 550 laptop*** and you will find good information. For example this link

[http://www.linlap.com/hp_550](http://www.linlap.com/hp_550)

which indicates that most things work, but you may have some problems with the wifi. If there is Broadcom wifi, you need proprietary drivers.

With 2 GB RAM, standard Ubuntu works, but I would prefer a flavour with a light desktop environment, for example Xubuntu or Ubuntu Mate, or an ultra-light desktop environment, Lubuntu.

Watching movies in HD, for example 1280x720 or 1920x1080 will work better with a lighter desktop environment.

I would recommend that you start with the version 14.04.1 LTS and update/dist-upgrade it (only normal updates keeping the 3.13 series of linux kernels). Try other versions only if there are problems with this version.

---

### Post by mlvmhn on 2015-06-07
Ok, since it is Windows in it now; can i totally format the disk when installing Ubuntu? 

Where do i find and download the installation ISO?

Does VLC and qBittorrent work in both Lubuntu and Ubuntu?

Is Linux Mint an option for this machine?

---

### Post by sudodus on 2015-06-07
> **mikael.hansson.967 said:**
> Ok, since it is Windows in it now; can i totally format the disk when installing Ubuntu? 

Are you sure that you do not want Windows? You might want to create a Windows recovery disk before it is too late.

Yes, you can format it - wipe the file system and create new file system(s). On the other hand, the standard installation will do it automatically for you, if you let it use the whole drive.
> 
Where do i find and download the installation ISO?
 
I suggest that you [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

You get the iso files at the home pages of standard Ubuntu and each of the flavours (there are links in the previous link).
> 
Does VLC and qBittorrent work in both Lubuntu and Ubuntu?
 
VLC works for me in both Lubuntu and Ubuntu. I have not used  qBittorrent, but I guess it works well in both Lubuntu and Ubuntu. I use  Transmission. qBittorrent uses qt4, which I think is associated with  KDE and Kubuntu, so it will bring some extra packages into Lubuntu and  Ubuntu. I use digikam, which also brings KDE stuff, and it is no real  problem, only that it occupies disk space.
> 
Is Linux Mint an option for this machine?

Yes, I think so. Try several linux distros live and install the distro that works best for you in that particular computer.

---

### Post by v3.xx on 2015-06-07
IMO, you have a good candidate for Mate (again, 14.04.1), its fast on my dual core.

Both Lu and Xubuntu will also run fast, done those too.  But I prefer to run a gnome flavor.

I do not know how Unity will fare, but I think 4G ram is a good idea.

Lots of positive post out there about Mint.  Not and ubuntu flavor though.  Makes it a little tough getting support here.  I ran it for a while and liked it, but Mate won out.

Edit
Should also mention that Mint can have Mate.

---

### Post by mlvmhn on 2015-06-07
K, i will try Ubuntu first on this machine, since i know it and how it works. 

Mint was to similar to Windows which i hate above all. 

But the main purpose is to run qBittorrent and watch Bluray rips on my bigger lcd. 

Which distro is best for this?

---

### Post by mlvmhn on 2015-06-07
> **v3.xx said:**
> IMO, you have a good candidate for Mate (again, 14.04.1), its fast on my dual core.

Both Lu and Xubuntu will also run fast, done those too.  But I prefer to run a gnome flavor.

I do not know how Unity will fare, but I think 4G ram is a good idea.

Lots of positive post out there about Mint.  Not and ubuntu flavor though.  Makes it a little tough getting support here.  I ran it for a while and liked it, but Mate won out.

Edit
Should also mention that Mint can have Mate.

K, looks like i am gonna install Ubuntu after all. I know this system pretty well and this feels safe. 

How do i install Ubuntu from a USB?

---

### Post by v3.xx on 2015-06-07
I don't do blueray, can't help you there.  But since your going the Ubuntu (Unity) route, thought you should know it is easy to install a lighter desktop to it.  This would give you something to compare with.  Its called 'Flashback'.
```
sudo apt-get install gnome-panel
```
and choose your desktop at login

---

### Post by sudodus on 2015-06-07
> **mikael.hansson.967 said:**
> K, looks like i am gonna install Ubuntu after all. I know this system pretty well and this feels safe. 

How do i install Ubuntu from a USB?

This link and links from it will give you a lot of tips

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by mlvmhn on 2015-06-07
K, i am about to download Ubuntu, but which shall i download; the 32 or 64-bit version?

My computer is a HP 550 laptop.

---

### Post by sudodus on 2015-06-08
A computer with core2duo can run both 64-bit and 32-bit Ubuntu. If you have 4 GB RAM or more I would recommend the 64-bit version. But you have ***2 GB RAM***, and the 64-bit version needs more RAM for the same task compared to the 32-bit version. ***I would recommend the 32-bit version***, but other people would recommend the 64-bit version.

So I suggest that you download and try both of them, at least if you have a good internet connection. I also suggest that you download and try Xubuntu, Ubuntu Mate and/or Lubuntu and compare (live) with standard Ubuntu.

---

### Post by mastablasta on 2015-06-08
64 bit since you are using the 64 bit CPU.

---

### Post by v3.xx on 2015-06-08
> **sudodus said:**
> but other people would recommend the 64-bit version.
Yep, different opinions on this.  I do 32bit with 2G of ram.

---

### Post by mlvmhn on 2015-06-08
K, i was not sure if i had the 32 or the 64-bit processor. 

so i downloaded the 32-bit version of Ubuntu. 

How long will the installation process take?

Will the wireless function work from start after installing Ubuntu?

---

### Post by Bucky Ball on 2015-06-08
*Thread moved to **Ubuntu, Linux and OS Chat**.*

How long the installation takes depends on the capabilities of your hardware. No one can give you a precise answer to that question.

Ditto for wireless. Boot from the install media> Try Ubuntu> does wireless work? Look for the wireless icon and click it to see if there are wireless access points available. If so, it will more than likely work on a full hard drive install. If not, then it might work on a full install and we can dig then and help you work it out.

If you have specific questions regarding installing Ubuntu or anything else, best to ask in the appropriate sub-forums. It appears the thread is now heading off-topic to your original question (which is asked often) and you'd be better served if you ask specific questions in support areas when they arise. Without more information the answers to what you are asking here would be guessing.

My two cents? Get to installing Ubuntu and post a new thread if you have a specific problem and need support with it. Good luck. :)

---

### Post by mlvmhn on 2015-06-08
Ok, i will do that. 

Thank you for now, over and out :popcorn:

---

### Post by LastDino on 2015-06-08
In my experience even Unity works okay on that processor, so there is no real problem. But I would indeed start with the suggestions given by others.

---

