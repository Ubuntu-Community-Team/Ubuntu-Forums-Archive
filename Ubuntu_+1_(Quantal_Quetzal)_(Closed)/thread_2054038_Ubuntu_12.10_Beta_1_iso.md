---
title: "Ubuntu 12.10 Beta 1 iso"
date: 2012-09-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by craig10x on 2012-09-06
Hi: I would like to check out the beta 1 iso of Ubuntu 12.10...i believe it is supposed to be released today?   Does anyone have a link to where i would go to get the download for it?
     Thanks ;)

---

### Post by vasilbelarus on 2012-09-06
[http://cdimage.ubuntu.com/releases/12.10/](http://cdimage.ubuntu.com/releases/12.10/) - here the link!

---

### Post by craig10x on 2012-09-06
Thank you so much....wanted to take a sneak peak at what is coming ;)
I'll watch for it on that link..

---

### Post by cariboo on 2012-09-06
Beta 1 hasn't been released yet, but watch this sub-forum, for official notice.

---

### Post by jerrylamos on 2012-09-06
No new daily build for today.  In past, either yesterday's daily build is the Beta, or else it might be out later today or tomorrow.  Anyway I'll do a zsync to have the latest posted .iso ready.

If you're keeping up with daily updates don't expect much difference.

On the other hand, new installs can show up some bugs for us to report, starting with the Ubiquity installer of course.

Just installed kernel 3.6.0-rc4 to give it a whirl.  I suspect it is later than the kernel in the Beta?

---

### Post by craig10x on 2012-09-06
I'm seeing a 64 bit iso for beta1 on that link now..is that one only for the mac or any 64 bit system?
(I have a windows laptop)...

---

### Post by PaulW2U on 2012-09-06
> **craig10x said:**
> I'm seeing a 64 bit iso for beta1 on that link now..is that one only for the mac or any 64 bit system?
(I have a windows laptop)...

Beta 1 hasn't been released yet so there may be more images still to be uploaded.

---

### Post by craig10x on 2012-09-06
Thank you Paul...i will keep a "look out" for the proper iso..

---

### Post by sammiev on 2012-09-06
On the above addie, Beta 1 is now there.

---

### Post by craig10x on 2012-09-06
I had to follow through a couple of links, but found it here:
[http://releases.ubuntu.com/12.10/](http://releases.ubuntu.com/12.10/)

---

### Post by jerrylamos on 2012-09-06
Installed, up and running on Acer Aspire 1 netbook with 1366x768 VGA TV.

Ubiuity did connect to wireless WPA security, very very slow (!) response to drop down menu selections but did succeed.

Booted O.K. connect to wireless WPA very slow but did succeed.

149 updates being installed already.

Systems settings turn off laptop 1024x600 display, set "unknown" to 1024x768, then do: 
xrandr --addmode VGA1 "1366x768_60.00"
xrandr --output VGA1 --mode "1366x768_60.00"
have a matching xorg.conf to copy into /etc/X11

I'll look at a couple bugs to see how they're doing on Beta 1.

---

### Post by vasilbelarus on 2012-09-07
beta 1 is avaliable. I have already tryed it.

---

### Post by fjgaude on 2012-09-07
Installed fresh on my Intel HD3000 main box and after 220 updates all went well, no issues. Rebooted, still no issues.

Tested the video quickness with gtkperm and got 2.99. On this same box on another partition and drive, 4.36. Now this is a huge speed improvement, all caused by the Intel drivers, open source, in the kernel. Wow!

Beta1 of 12.10 is impressive, hopefully not too much to fix before release time.

---

### Post by stoneguy on 2012-09-07
Got beta-1 installed. See [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1047498]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1047498") for speedbump and workaround.

---

### Post by tienvx on 2012-09-07
I checked [http://releases.ubuntu.com/12.10/](http://releases.ubuntu.com/12.10/) and [http://cdimage.ubuntu.com/releases/12.10/beta-1/](http://cdimage.ubuntu.com/releases/12.10/beta-1/).
Are there any differences between [http://releases.ubuntu.com/12.10/ubuntu-12.10-beta1-desktop-amd64.iso](http://releases.ubuntu.com/12.10/ubuntu-12.10-beta1-desktop-amd64.iso) and [http://cdimage.ubuntu.com/releases/12.10/beta-1/ubuntu-12.10-beta1-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.10/beta-1/ubuntu-12.10-beta1-desktop-amd64+mac.iso)? They are the same size.

Sorry for my English! Please correct it for me.

---

### Post by sammiev on 2012-09-07
Finish doing a install of QQ Beta 1 tonight. Used a USB to install and all was very good. No bugs to report. :popcorn: Will do another 2 more installs over the next day or two. Still have one computer on the 1st release of QQ when it hit Alpha 1 and really do not see much difference between Alpha and Beta to date, even with boot times and shut downs.

---

### Post by cariboo on 2012-09-07
I did a fresh clean Beta 1 install today, on first boot of the Live USB, I had corrupted graphics, using nomodeset allowed me to boot to a desktop, and complete the installation.

---

### Post by craig10x on 2012-09-08
> **tienvx said:**
> I checked [http://releases.ubuntu.com/12.10/](http://releases.ubuntu.com/12.10/) and [http://cdimage.ubuntu.com/releases/12.10/beta-1/](http://cdimage.ubuntu.com/releases/12.10/beta-1/).
Are there any differences between [http://releases.ubuntu.com/12.10/ubuntu-12.10-beta1-desktop-amd64.iso](http://releases.ubuntu.com/12.10/ubuntu-12.10-beta1-desktop-amd64.iso) and [http://cdimage.ubuntu.com/releases/12.10/beta-1/ubuntu-12.10-beta1-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.10/beta-1/ubuntu-12.10-beta1-desktop-amd64+mac.iso)? They are the same size.
 
Sorry for my English! Please correct it for me.
 
I think that the 2nd one is the mac enhanced version to be used on mac computers, i downloaded the first one, since i have a windows laptop...

---

