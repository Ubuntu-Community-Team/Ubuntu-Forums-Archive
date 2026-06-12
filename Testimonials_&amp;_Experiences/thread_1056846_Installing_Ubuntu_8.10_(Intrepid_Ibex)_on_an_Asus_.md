---
title: "Installing Ubuntu 8.10 (Intrepid Ibex) on an Asus EEE 900"
date: 2009-02-01
forum: Testimonials &amp; Experiences
---

### Post by bbabu84 on 2009-02-01
Feb 1, 2009:
I have been running the Xandros system that came with my Asus EEE 900 for some time.  There are hardly any upgrades available and installing new software was a problem due to compatibility issues (libraries).  I tried out eeebuntu, which was ok, but not the latest version of Ubuntu.  Easy Peasy just didn't install and I got tired of installing "doctored" versions and decided to install a generic version of Ubuntu and here is how it went.  If you have been using Ubuntu for some time, you should be able to follow theses steps for a successful installation.

The Asus EEE 900 has two SSD: /dev/sda is 4GB, and has most of the Xandros stuff in it.  /dev/sdb is 16GB and has the user files.  I decided to leave /dev/sda alone so that I can use Xandros also.

1. Connected an external CD/DVD, and booted with Ubuntu.  Mounted /dev/hdb1 and saved the files in a USB flash drive.  I had only less than a gig of files and this was faster than trying to use gparted to shrink the partition.

2. Ran fdisk on /dev/sdb and deleted the existing partition and created two partitions: 4G for Xandros and 16G for Ubuntu.  EEE 900 has 1G memory and runs fine without swap.  So I didn't create a swap partition.  Created an ext2 file system on /dev/sdb1 and replaced the files from backup.

3. Started an installation of Ubuntu 8.10, and when it came to partition management, chose the last option which allows the user to make his own choices.  I chose /dev/sdb2 as /, clicked on the Advanced tab in the next screen to skip boot loader installation (because it is already there in sda).  I chose ext2 instead of ext3 for /dev/sdb2 to reduce the extra writing (to protect the SSD) by ext3.  Maybe this is not needed.

4. Ubuntu installed fine, though it seems to try to read nonexistent blocks from the CD (may have been an error on my CD).  When it rebooted, I booted again into the live CD, edited the grub.conf (may be menu.lst in some installations) file in /dev/sda1 to add the new Ubuntu configuration in the boot menu, and increased timeout to 5.  Otherwise the Xandros system boots without any time for making a choice.  I could have let Ubuntu make this entry by itself, but I was afraid that something will go wrong.

5. Rebooted again, without the CD, chose Ubuntu 8.10 from the boot menu.  Boot time is slow compared to Xandros, of course.  When the system came up, it had most things right, including sound, battery monitor, and ethernet.  The wireless, of course, was messed up, since the Atheors driver that gets loaded seems to be the wrong one for EEE.  I decided to fix the problem by using the windows driver (provided by ASUS) with ndiswrapper, rather than a customized kernel, say from array.org.

6. To fix the wireless, in  /etc/modprobe.d, added to blacklist-local file, the lines "blacklist ath_pci" and "blacklist ath_hal".  Connected the computer to the LAN through ethernet, and updated the system.  Doing this update is crucial in getting even basic things like network manager.  Also added ndiswrapper and a gtk tool for a UI to it using synaptic package manager.

7. Rebooted the system so that it doesn't load the Atheros drivers.  Selected the ndiswrapper management tool (under syetm->administration), and pointed it to the net5211.inf file (windows driver for the wireless).  It loaded the driver and a scan found my wireless network with WPA authentication.  I entered the key and it connected.

8. I have been using the system for a couple of days and the wireless is very stable.  I can use Fn-F3 and Fn-F4 for changing the brightness of the screen.  I have not tried to suspend wireless or any of the other Fn keys.  One of these days I will check out the webcam.

9. The system takes a couple of minutes to boot, compared to 20 sec for Xandros.  Once it starts, the speeds seem similar.  Some parts of Xandros are bound to be faster since it seems to load some partitions in ram.  But I don't think I will go back to Xandros again.  I also replaced the relatime option with noatime in /etc/fstab for /dev/sdb2 to reduce writing to the disk (SSD).

10. Thanks to the open source movement, and the Ubuntu community for all the work, and information in the forums.

BB

---

### Post by Crafty Kisses on 2009-02-01
Glad you got it up and running, I'm surprised Easy Peasy didn't work.

---

### Post by wolfen69 on 2009-02-02
you could have saved yourself the trouble of configuring things by installing Eeebuntu. it's regular ubuntu with all the tweaks already done for you. but then again you may enjoy tinkering.

---

### Post by Crafty Kisses on 2009-02-02
> **wolfen69 said:**
> you could have saved yourself the trouble of configuring things by installing Eeebuntu. it's regular ubuntu with all the tweaks already done for you. but then again you may enjoy tinkering.

Does Eeebuntu come with a graphical installer?

---

### Post by bbabu84 on 2009-02-02
> **wolfen69 said:**
> you could have saved yourself the trouble of configuring things by installing Eeebuntu. it's regular ubuntu with all the tweaks already done for you. but then again you may enjoy tinkering.

Excellent point.  I do enjoy tinkering and this was a good learning opportunity.  Also, there were other distributions I looked at like Pupeee, Breezy, etc.  I thought it is better to learn to do it on my own, because when Ubuntu 9.04 is released, I will be eager to try it out, but most of the derivatives will still be stuck in the past.  eeebuntu is the only one that is close to recent.

---

### Post by wolfen69 on 2009-02-02
> **Codename said:**
> Does Eeebuntu come with a graphical installer?

yes.

---

### Post by Crafty Kisses on 2009-02-02
Oh thanks for the info, I'm getting an EEEPC soon, I just wanted to know because I really don't want to use Xandros if you know what I mean. I was thinking about Easy Peasy as well, what do you think would be better personally? I was thinking Easy Peasy.

---

### Post by bbabu84 on 2009-02-03
> **Codename said:**
> Oh thanks for the info, I'm getting an EEEPC soon, I just wanted to know because I really don't want to use Xandros if you know what I mean. I was thinking about Easy Peasy as well, what do you think would be better personally? I was thinking Easy Peasy.

Once you have them running, they are all the same (ubuntu).  In my case, I don't really care about the webcam, since the processor just lacks the power to do video.  So, once I get Ubuntu going with working wireless, I am in business.  If you want to stay with the latest updates, go for a generic install.  The custom distributions (EasyPeasy, EEEbuntu) use modified kernels, and the kernel is pinned (and so may not allow some updates).  On the flip side, the custom dists use direct drivers for the wireless, whereas you may have to settle for the windows driver with ndiswrapper when using a generic distribution.

---

### Post by Drew Corser on 2009-02-06
This is a fascinating discussion for me: we have just bought 20 eee pc's with Linux installed for our small primary school in Cornwall, and I have been advised to replace eee Xandros with Ubuntu (partly to make it easier to get iTALC - a teaching programme which seems to me to be quite important to the classroom management of 20 laptops on pupils' desks - and partly because Ubuntu appears to be much better supported and have more available than eee Xandros) - I am a newbie in Linux, although I have been having a look at Ubuntu for the past few weeks.

To me it is quite important to have all the things that are on the eee pc working - we have bought 18 1000's with 40 Gb SSD (the other two are smaller machines to try out, in case we can afford to buy them for the other half of the school - yes we only have 40 kids!) - so I obviously want the wireless to work (which it is not yet doing on the one Intrepid install I have done) but I would also like the webcam to work.  However, I don't want to get left out of the apparent advantages of normal Ubuntu.  And I want to get this right before I go through the installation on the other 19 machines!!

So what is the advice on Eeebuntu vs Ubuntu 8.10?  What are the plusses and minusses?

Many thanks

Drew Corser
Headteacher
Boskenwyn School
Cornwall

---

### Post by snowpine on 2009-02-06
Hi Drew, I think Eeebuntu will save you a lot of time setting up the 20 eee's. There is nothing wrong with "regular" Ubuntu on the eee, but it does take a few extra steps to get it set up. Eeebuntu is close enough to Ubuntu that I think it will be a comparable educational experience for your students. 

Best advice I can give you however is to try both and decide for yourself. :)

ps You might look into an application called Remastersys. It would allow you to get everything set up on one machine, then make your own custom CD/USB installer for the other 19.

---

### Post by Drew Corser on 2009-02-06
Thanks for your advice, Snowpine, I will try Eeebuntu on another machine to compare.  

What would you say is the easiest way (for a Linux newbie) to get the wireless and webcam working on a 1000 40 Gb SSD Eee PC with straight Ubuntu 8.10?  (I followed something in the first post in this thread about getting the wireless working, got as far as modprobe.d, but there wasn't a blacklist-local file...)

Many thanks.

Drew C
BCP

---

### Post by snowpine on 2009-02-06
Hi Drew, bbabu84's tutorial looks pretty good, but I haven't tried it.

This is the method I used to "tweak" Ubuntu Intrepid for my eee 900ha: [http://array.org/ubuntu/setup-intrepid.html](http://array.org/ubuntu/setup-intrepid.html)

---

### Post by bbabu84 on 2009-02-06
> **Drew Corser said:**
> Thanks for your advice, Snowpine, I will try Eeebuntu on another machine to compare.  

What would you say is the easiest way (for a Linux newbie) to get the wireless and webcam working on a 1000 40 Gb SSD Eee PC with straight Ubuntu 8.10?  (I followed something in the first post in this thread about getting the wireless working, got as far as modprobe.d, but there wasn't a blacklist-local file...)

Many thanks.

Drew C
BCP

I think you first have to run an update by connecting it through the wired (ethernet) network.  The live CD just installs the bare minimum.  Also, you can add the two lines to the end of the file named "blacklist" in /etc/modprobe.d directory (if blacklist-local file is missing).

If you are responsible to maintain 40 systems for "production" use, go with a standard platform like eeebuntu.  With eeebuntu, you should have all the hardware working upon installation.

BB

---

### Post by stalkingwolf on 2009-02-07
when I first got my EEEPC I installed 8.04.1 0n it.  Worked fine, wireless
and all.  Then I downloaded and installed  the EEE version. the biggest difference I saw was drive space.  The normal version took a bit more.
This was a consideration with only a 4gb drive.  The only issue i had was
more of an irritant than an issue.  I would not always completely shut down.
It was like the old systems where you shut down then had to hit the power
button to turn it off.

Other than that I loved it. never a problem. I just sold it to my landlord.
I think when I replace it I will probably get one of the HP mini's. The keyboard is a bit larger for my fat fingers.

---

