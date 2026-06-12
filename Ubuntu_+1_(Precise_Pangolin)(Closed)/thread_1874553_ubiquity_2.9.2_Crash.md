---
title: "ubiquity 2.9.2 Crash"
date: 2011-11-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sparker256 on 2011-11-03
I was using a Startup USB to try to reinstall my 12.04 64bit install. After I had selected something else I selected the partition where I wanted the root. I next selected change and a dialog box appeared and when I tried to select the type ubiquity crashed. I have filed a bug report and its number is [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654)

Bill

---

### Post by jerrylamos on 2011-11-04
> **sparker256 said:**
> I was using a Startup USB to try to reinstall my 12.04 64bit install. After I had selected something else I selected the partition where I wanted the root. I next selected change and a dialog box appeared and when I tried to select the type ubiquity crashed. I have filed a bug report and its number is [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654)

Bill

Ubiquity crashes and failures occur all the way through development on ubuntu releases, on oneiric ocelot I even got a ubiquity crash on Beta 2 - configuring "apt".  That botched Grub2 so oneiric ocelot wouldn't boot nor even the other multiboot partitions. Grub2 rescue> mode wouldn't work. Some scurrying around and I was able to restore Grub2 with a rescue CD (Lucid Lynx LTS).

"Ubiquity" bugs do not seem to be of interest to ubuntu development.

Jerry

---

### Post by sparker256 on 2011-11-04
> **jerrylamos said:**
> Ubiquity crashes and failures occur all the way through development on ubuntu releases, on oneiric ocelot I even got a ubiquity crash on Beta 2 - configuring "apt".  That botched Grub2 so oneiric ocelot wouldn't boot nor even the other multiboot partitions. Grub2 rescue> mode wouldn't work. Some scurrying around and I was able to restore Grub2 with a rescue CD (Lucid Lynx LTS).

"Ubiquity" bugs do not seem to be of interest to ubuntu development.

Jerry
Since I do multi boot I have to be able to pick which partition to install Precise on. Since I want to reinstall I am stuck until this can get resolved. My only other option is to install 11.10 and upgrade but misses the point of testing of daily live iso's.

This is the full error.

ubiquity crashed with KeyError in partman_edit_dialog(): 'method_choices'

Bill

---

### Post by jerrylamos on 2011-11-04
> **sparker256 said:**
> Since I do multi boot I have to be able to pick which partition to install Precise on. Since I want to reinstall I am stuck until this can get resolved. My only other option is to install 11.10 and upgrade but misses the point of testing of daily live iso's.

Bill

I'm with you, one of the things I test is install after I've recovered from the last mess.

Now I keep the last precise pangolin that would work and test in another partition.  If the new is dead in the water, I may be able to use the last .iso for a while, unless what is garbaged is the partition table.  grub2 garbage might be recoverable with CD live. 

For my testing 6 GB partitions work O.K. so far.

I have tried upgrade - reading the forums more people have trouble with upgrade!  Also, upgrade tends to use more disk space than fresh install.

For limited testing I'll boot the .iso from a USB stick or from a .iso file on another partition.  That can be used to test install as well so long as the install target is a different hard drive.  'way back when, install would work to the same hard drive as the live image was booted from, but somebody put a check and install won't do that any more.

Jerry

---

### Post by Quackers on 2011-11-04
> **jerrylamos said:**
> 
"Ubiquity" bugs do not seem to be of interest to ubuntu development.

Jerry

It would seem so. The bug below is completely unacknowledged nearly 3 weeks after reporting.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/876499](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/876499)

---

### Post by bedbug on 2011-11-06
Temporary workaround
change  #! /bin/sh to #! /bin/bash in /lib/partman/choose_partition/60partition_tree/do_option

Ignore Crashes... It's Worked for me !!!

---

### Post by cbowman57 on 2011-11-06
Not directly related but I am so glad I found this thread.

I've been trying to test the latest Remastersys and it keeps bombing out on my 12.04 installation, this would explain it.

---

### Post by sparker256 on 2011-11-07
> **bedbug said:**
> Temporary workaround
change  #! /bin/sh to #! /bin/bash in /lib/partman/choose_partition/60partition_tree/do_option

Ignore Crashes... It's Worked for me !!!
It worked for me also. :D It is going to be fixed by alpha1 but I did not want to wait that long if there was a work around. The amount of knowledge on this forum is amazing at times. 

Thankyou Thankyou Thankyou Bill

---

### Post by kansasnoob on 2011-11-07
Haven't tried the work-around yet but I was the one who just posted to your bug report (Erick) :D

For now I'm just upgrading from Oneiric, which works well for what I'm doing anyway :guitar:

---

### Post by kansasnoob on 2011-11-07
I ran through this again and it looks to me like ubiquity tries to mount all existing partitions before beginning the partitioning. Anyone else see that?

---

### Post by cbowman57 on 2011-11-07
I tried the workaround with my 12.04 setup, it now works correctly.

Yeah, that automount autorun behavior that is the Gnome default it appears.

---

### Post by cbowman57 on 2011-11-15
> **kansasnoob said:**
> I ran through this again and it looks to me like ubiquity tries to mount all existing partitions before beginning the partitioning. Anyone else see that?

Yes, it's real obvious when trying to install from gnome shell.

---

### Post by floydsp on 2011-11-15
can someone point me where and how to change this

thanks in advance....I have booted into ubuntu 12.04 but can't find
where to make changes

floydsp

---

### Post by beew on 2011-11-15
This seems to be a show stopping bug that has been around for a long time (with minor variations) that never really got fixed. I started using Ubuntu since 10.04 and installation has always been hit and miss  because the installer often creashes, regardless of hardware (tried on many machines) Eventually I always succeeded somehow but often took several trials, or wait for a long time for them to release an iso that doesn't crash.

 How do you persuade people to use Ubuntu when the very first step of installing flops like this. Fedora may be buggy in other ways, but the installer never quits on me like that, even for the betas.

Just reinstalled 11.10 yesterday with a live usb made from a freshly downloaded iso, guess what, the installer crashed, again. Finally managed to install by checking off the boxes "installing updates" and "installing third party software" (this appears to be a known bug, so there is a known work around, but why don't they just fix it?)

P.S. Whenever the installer crashes a pop up appears asking you to file bug report. Why bother?? What is the point? It is not that they don't know about it

---

### Post by cbowman57 on 2011-11-15
Temporary workaround
change  #! /bin/sh to #! /bin/bash in /lib/partman/choose_partition/60partition_tree/do_option

---

### Post by sgage on 2011-11-15
> **cbowman57 said:**
> Temporary workaround
change  #! /bin/sh to #! /bin/bash in /lib/partman/choose_partition/60partition_tree/do_option

This worked for me, too. Boot into "Try Ubuntu", make the edit, run the install, and all good! :KS

---

### Post by floydsp on 2011-11-15
Also worked fine for me..Thanks everyone

floydsp

---

### Post by kansasnoob on 2011-11-15
Just tried the 2011/11/15 i386 image and while the work-around sort of works I still just get "blank" selection "windows" for New partition size, Use as, Format the partition, and Mount point.

So I can still only reliably install to a blank drive. Anyone else seeing that?

---

### Post by mc4man on 2011-11-26
> **sparker256 said:**
> I was using a Startup USB to try to reinstall my 12.04 64bit install. After I had selected something else I selected the partition where I wanted the root. I next selected change and a dialog box appeared and when I tried to select the type ubiquity crashed. I have filed a bug report and its number is [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654)

Bill

This is fix released now & the current image no longer needs any editing for manual partitioning

---

### Post by cbowman57 on 2011-11-26
> **mc4man said:**
> This is fix released now & the current image no longer needs any editing for manual partitioning

Great news, thanks for passing that on.

---

### Post by cariboo on 2011-11-26
> **beew said:**
> 
P.S. Whenever the installer crashes a pop up appears asking you to file bug report. Why bother?? What is the point? It is not that they don't know about it

Martin Pitt suggested that the more people that click the affects me button, increase the hotness of the bug, making it stick out more, ensuring that it will get some attention.

Now that apport is supposed to root out duplicate bugs, things may get better, as there are so many duplicate bugs, it's hard for the triagers to know which one to give attention to, causing a lot of wasted effort.

---

