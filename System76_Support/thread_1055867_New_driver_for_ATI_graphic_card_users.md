---
title: "New driver for ATI graphic card users"
date: 2009-01-31
forum: System76 Support
---

### Post by Lee_Machine on 2009-01-31
On the 28th of January AMD release the new drivers for the ATI Radeon cards. Big thing here is full openGL 3.0 support. 

[HERE]("http://ati.amd.com/support/driver.html") is the new driver.

---

### Post by thomasaaron on 2009-02-02
Thanks. I'll send that over to R&D so that they can have a look.

---

### Post by fohat on 2009-02-27
Any word on if this new driver is stable?  Would love to try it to see if there is any improovement with some various issues I'm running into (flickering video playback while using compiz for starters)

Thanks

---

### Post by thomasaaron on 2009-02-27
No. We're probably going to keep recommending what's in the repos for now. It becomes a support disaster when people start installing drivers from elsewhere.

To fix the flickering, go to a terminal and enter this command...

gstreamer-properties

Under the "Video" tab, on the very first drop-down selector, select "X Window System (N XV)."

You may need to reboot.

---

### Post by cat1minder on 2009-02-27
Newbie - first time post

As I am having trouble with dual monitor setups, visited the ATI Board. There is a new management program (ATI Catalyst) version 9.2. On my system the version is 2.1 (?) Have downloaded the 64 bit x86 Linux version. Version is 9.2. Have not installed - yet. Advice please - :confused:

Machine wilp6, ATI 4800 series.

---

### Post by thomasaaron on 2009-02-27
Hi, Cat1minder.

**Welcome to the forums! **

It's always a good idea to create a new thread for dealing with new issues, or to add your post to a thread that more closely matches your problem. Otherwise, it is "considered" hijacking the thread. 

Hijacking basically causes the initial problem to be ignored and changes the subject, which, of course, ticks off the original poster, confuses communication, and makes it more difficult for others to search out the answers to their own problems.

Your question is actually a very good one, though. And I've not seen it addressed on our forums yet. You use ATI Catalyst to obtain dual-head displays. If you have a System76 computer, it is at Accessories > ATI Catalyst.

---

### Post by swajime on 2009-09-13
> **fohat said:**
> Any word on if this new driver is stable?  Would love to try it to see if there is any improovement with some various issues I'm running into (flickering video playback while using compiz for starters)

Thanks

I just went through a mess of flickering madness (especially with google earth!).  
I seem to have corrected the "flickering" problem on my system. (Hopefully)

I followed Lee_Machine's link [http://ubuntuforums.org/showpost.php?p=6650348&postcount=1](http://ubuntuforums.org/showpost.php?p=6650348&postcount=1) to [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

I downloaded the file there [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-9-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-9-x86.x86_64.run)
and followed the instructions [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf) 

Starting with the last paragraph of page 3, which says: 
[INDENT]"If the initial installation of the driver was done via the Operating Systems package
        management software (RPM, APT, etc.) then please use that package management
        software to remove the ATI Proprietary Linux Driver."[/INDENT]
Accordingly: Gnome Menu | System | Administration | Hardware Drivers | "ATI/AMD proprietary FGLRX graphics driver" | Deactivate

Then I skipped to the procedure "Generate Distribution Specific Driver Package Option" on page 10.
At step 4 I chose "other" and was given new instructions, which pretty much amounted to the following:
```
$ su
# mkdir /root/ati
# cd /root/ati
# mv ~john/Desktop/ati-driver-installer-9-9-x86.x86_64.run .
# sh ./ati-driver-installer-9-9-x86.x86_64.run --listpkg
# sh ./ati-driver-installer-9-9-x86.x86_64.run --buildpkg Ubuntu/9.04
# less fglrx-installer_8.650-0ubuntu1_amd64.changes
# aptitude install libstdc++5            # prerequisite was missing
# dpkg -i *.deb
# /usr/bin/aticonfig --initial
# reboot
```

I'm very grateful to the originator of this thread, as I was about to go bald.

I have seen some very minor artifacts, nothing like what I was fighting with that flickering though!
-- 
John

---

### Post by swajime on 2009-09-13
> **swajime said:**
> ... I have seen some very minor artifacts, nothing like what I was fighting with that flickering though!

Very bad flickering when running wine, even with the updated driver.
I also have noticed some flicker when scrolling in firefox.
-- 
John :(

---

### Post by swajime on 2009-09-15
I'm finding as I do various tasks that portions of the screen become blacked out.  Very annoying.  I have yet to determine if I have a bad video card or if it's a problem with the video drivers.
Also I get the "flicker" when I launch the "ATI Catalyst Control Center", or gnome-display-properties.
-- 
John

---

### Post by pyroclastic on 2009-09-16
Just visit the Ati site, and u will find the latest driver

---

### Post by Lee_Machine on 2009-09-19
The only exp I have with ATI cards with Linux is limited, but I have been told that some things transfer over from NVIDIA. Such as if you install/compile the latest driver, and have one already installed it may and usually wont work as it should.

Meaning the only way to make sure it will work correctly is: 1) use the driver packaged for Ubuntu. 2) Install the newest ATI/NVIDIA driver on a fresh install.

The later is what I do if the new driver fixes bugs that affect me, or adds a feature I want. 

I know the one available by Team Ubuntu tends to be older, but it will (should) be stable.

If you are looking for a Distro that updates things like that more often I would recommend Fedora 11. :lolflag:

I have been using Fedora on my Pangolin for a while now, and in their repos they have the newest ATI, and NVIDIA driver. 

Just a warning though things in Fedora are done differently than Ubuntu. Sometimes very different.

---

