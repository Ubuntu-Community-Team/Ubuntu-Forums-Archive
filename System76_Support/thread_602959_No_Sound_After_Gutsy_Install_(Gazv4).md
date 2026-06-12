---
title: "No Sound After Gutsy Install (Gazv4)"
date: 2007-11-04
forum: System76 Support
---

### Post by IgnacioMiller on 2007-11-04
Hi all,

I wiped my hard drive on my Gazelle Value (gazv4) and installed Gutsy off of the Alternate Install CD. I followed the instructions on te System76 knowledge base while doing this. However, when the system76 driver had completed the restoring task, and I restarted, I found that I had no sound. In fact, the sound preferences application does not even show any sound devices in the drop down menu.

I tried running the system76 driver again, with no change. Then I tried restoring again, with no change, and running the system76 driver, again with no change.

When I try to double click on the volume applet I get these errors:

> No volume control GStreamer plugins and/or devices found.

AND

> The volume control did not find any elements and/or devices to control. This means that either you don't have the right GStreamer plugins installed, or that you don't have your sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

I also installed all Gstreamer plugins in the Ubuntu repositories, to no effect.

Any ideas?

Thanks in advance!
Dan

---

### Post by thomasaaron on 2007-11-05
Yeah, somehow update manager hoses some gstreamer plugins. The only solution I've been able to find thus far is re-installing via these directions. If you take any shortcuts in it, you'll probably end up with no sound, so follow them exactly.

1. Back up important files. I do not recommend backing up any config files other than .mozilla and .gaim.

2. You must re-install Ubuntu. Any install CD is fine, but I have had the best results with the alternate CD.

3. REFORMAT your partitions when you get to that step of the install, and I do not recommend keeping your current home directory. Re-create it from scratch. Failure to REFORMAT ALL PARTITIONS has been linked to retained Feisty configurations, which can break sound, cd-drives and printing (i.e. I am recommending a 100% clean install). (See cwej's post on this thread for motivation to not try to shortcut a clean install ;)  
[http://ubuntuforums.org/showthread.php?t=584100&page=5](http://ubuntuforums.org/showthread.php?t=584100&page=5)

4. Once you have re-installed, remove the install cd listing from your sources file. To do this, go to a terminal and enter this command:
sudo gedit /etc/apt/sources.list
In the resulting file, comment out (#) the cdrom reference at the top of the page.
Click the SAVE button.

5. Update your install FROM THE COMMAND LINE. Updating with Update Manager has been linked in our shop tests to a failure to load the proper gstreamer packages. Here are the commands:
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade
sudo reboot

6. Download and install the system 76 driver with these commands:
wget [http://planet76.com/repositories/system76-driver-2.1.1.deb](http://planet76.com/repositories/system76-driver-2.1.1.deb)
sudo dpkg -i system76-driver-2.1.1.deb

7. Go to System > Administration > System 76 Driver
Run the Restore function of the driver

8. Reboot the computer

Now you should have a perfect install of Gutsy.

---

### Post by IgnacioMiller on 2007-11-05
Thanks for the detailed instructions Tom, I'll try them tonight after orchestra.

Dan

---

### Post by IgnacioMiller on 2007-11-06
All worked, thanks Tom!

Dan

---

### Post by mblemieux on 2007-11-07
Not sure if this will work for others, but I simply reconfigured my boot menu to boot into the generic kernel and the sound worked great after that.

---

### Post by palintheus on 2007-11-07
> **mblemieux said:**
> Not sure if this will work for others, but I simply reconfigured my boot menu to boot into the generic kernel and the sound worked great after that.

It was probably the older kernel that was used with Feisty. Until I reinstalled I used the older kernel as well.

---

### Post by Chelidon on 2007-11-07
I don't know if this has anything to do with Feisty because I have the same problem and Gutsy is my first (ever) Linux system. I need to reinstall it anyway because I made a bit of a mess of things (dual boot issues and all that) so I will definitely try the clean install.

---

### Post by rvdavid on 2007-11-10
Before reinstalling, try checking that your account is listed as part of the audio group. 

```

$ sudo vim /etc/group

```

Check the line that starts with "audio" and ensure that your username is registered. 

for example, say that my username for my machine is "rvdavid" 

This is what line 22 on my /etc/group file would look like: 

```

audio:x:29:rvdavid

```

I don't know exactly if this will solve your problems, but it did solve mine - and I didn't have to reinstall!

HTH - and if it doesn't, there's a couple of other fixes out there that I came accross, but after spending 5 mins trying to find it without avail, i can't give  specific instructions or even a link on where you can read about it. 

Here's very vague description of what it said to do  - the other solution I saw was to check to see if you have a specific rc file that has been created by alsaconfig and if you do have it either rename it to something else - don't know the full details of this fix as I didn't do that to fix my sound issues.

If this, that and the other fails and you still have no sound, have fun reinstalling :P

regards,

---

### Post by thomasaaron on 2007-11-12
ATTENTION: We now have a clean fix for the "no sound after upgrade" problem. It is a .deb package, so email me for it. 

Also, a new fix will be coming down via the System 76 driver that will fix this problem and prevent future sound problems caused by kernel updates.

---

### Post by rvdavid on 2007-11-19
Hi there,

Just out of curiosity, what was the problem?  How did updating the kernel affect sound? 

regards,

---

### Post by thomasaaron on 2007-11-19
We're not entirely sure.

It somehow screws up gstreamer plugins/configurations pretty badly. It's definitely a bug in the update manager.

---

### Post by rvdavid on 2007-11-25
> **thomasaaron said:**
> We're not entirely sure.

It somehow screws up gstreamer plugins/configurations pretty badly. It's definitely a bug in the update manager.

Right, I'll keep this one in mind. 
Thank you for getting back to us :) 

regards,

---

### Post by StJack on 2007-11-26
Alright, I followed the instructions, though I omitted the step re taking the reference to the cd listing out.  Still having the same problem with the fresh install.

When trying to run the System76 function, I was greeted with: Unsupported: This driver is designed for System76 machines running Ubuntu version 6.06, 6.10, 7.04, or 7.10.  If you have a System76 machine running one of the above Ubuntu versions please file a bug report at [https://launchpad.net/system76](https://launchpad.net/system76)

Perhaps I should educate myself regarding System76, and I will reinstall without skipping that step, then retry.  Will post results.

---

### Post by palintheus on 2007-11-26
> **StJack said:**
> Alright, I followed the instructions, though I omitted the step re taking the reference to the cd listing out.  Still having the same problem with the fresh install.

When trying to run the System76 function, I was greeted with: Unsupported: This driver is designed for System76 machines running Ubuntu version 6.06, 6.10, 7.04, or 7.10.  If you have a System76 machine running one of the above Ubuntu versions please file a bug report at [https://launchpad.net/system76](https://launchpad.net/system76)

Perhaps I should educate myself regarding System76, and I will reinstall without skipping that step, then retry.  Will post results.

What System76 model do you own? Are you running Ubuntu, Kubuntu, Xubuntu? 32bit or 64bit?

---

### Post by StJack on 2007-11-27
I actually don't own a system76 system.  my bad.  i have on previous occasions been given drivers from linux developers with wink assurances that it would work with a frankenstein system.  

long story short, i'm running a 32-bit Ubuntu installation (with desktop, 'cause command lines make me nervous) with an old athlon 950 MHz processor, a chaintech (i think) mobo), and an old western digital hard drive.  everything works fine except the sound.

I've tried reinstalling, without skipping the step i skipped before, to no avail.

when trying to play an .mp3 file (in this case: /Main USB Volume/Music Files/Asheru/Unknown Album/The Boondocks Theme Song.mp3) I get a message that it has to download the gstreamer codecs, which is eerily familiar, 'cause that's the last thing I remember seeing before realizing that I had a major sound problem on the first Ubuntu install some five days ago.  I am now on my fourth (i think) re-install, and am having the same problem.

Is there any more information that I could retrieve that might help find a solution?  Do I have to have specific software to run the System76 drivers?  And why is it that nobody says they're going on a coffee break anymore?

---

### Post by palintheus on 2007-11-27
I thought that may be the case, the system76 driver is made for system76 machines I don't think you would want it to run on a non system76 machine because it modifies config files to make those machines work.

I would ask in a general sub-forum because this sub-forum focuses on System76 support and it may not get read by enough people that can help you.

---

