---
title: "Ubuntu 10.04 desktop bootkit"
date: 2010-12-09
forum: Security
---

### Post by flame retardant on 2010-12-09
Recently I played a movie on Ubuntu 10.04 x64.  The movie played fine, no jumps as in some previous ones.  I had 10.04 installed alongside vista.  It used the grub boot menu.  the next morning Ubuntu lost contact with the network, further investigation showed that eth0 had disappeared from the /etc/interfaces configuration.  I used mc to put it back, no good.  I then used the ubuntu network tool to try and replace it, got the mac id from windows ipconfig, tried but with no luck.  Refused to create a new interface.

I then tried to reinstall the OS from a disk, the disk would not boot. I then tried another version of ubuntu still would not install.  I installed debian 5 from the disk, it found my windows installation, and installed fine.  I then re-tried to install ubuntu, which crashed at the grub install portion. again no version of ubuntu would install.

I then re-installed windows from the rescue partition on the drive. (Vista et-al). Once again tried to install ubuntu any version from the disk, both attempts failed, disk tried to install, but crashed before the first window on version 9.04, and refused to boot on 10.04.

then used windows7 install disk to overwrite boot sector several times, used bcdedit, and fixboot etc.

I am now using the ubuntu 10.04 distro again, it finally worked.

to recap:

virus was from ubuntu movie player, Xvid file I believe.
had ugly  plugins in place.
the virus/bootkit disabled the internet connection in Ubuntu 10.04
It would not let me install ANY version of ubuntu
Debian 5 installed fine, grub worked.
replacing the Vista install from the rescue partition did not change the situation
overwriting the boot sector from an install disk using the command prompt (several times) did resolve the problem.



I have several questions;
1. why are my vista drives automounted, and why can't I configure them using fstab?
2. how can I remove the drives (at least the C: drive) so that a virus can't reconfigure the boot file?
3. What's up with the movie player that apparmor didn't deal with?
4. how was a virus able to disable my internet connections in Ubuntu?


hope you can find the answers.  If you're having a problem, this may be the cause.

Yes, Virginia, there is a virus for Ubuntu.


hoping you don't have the same thing
FR

---

### Post by cariboo on 2010-12-09
Moved to a thread of it's own, as it had nothing to do with the thread it was attached to.

---

### Post by flame retardant on 2010-12-09
I have/had an ubuntu 10.04 x64 installation.  I recently played a movie on the Ubuntu 10.04 movie player. I was in the Xvid format.  I had the Ugly plugins in place.  The next morning my 10.04 installation could not find my network connections, namely the eth0 connection. I went to the /etc/interfaces file and added it, but it still did not work.  I then tried to use the network connections dialog to try to reinstall, to no avil ( used the mac address of the interface ).
I then tried to reinstall the os, which crashed at the grub install, and left things completely broken.  I used a Debian 5 cd, and installed it, grub, etc.  Things worked fine.  I tried a windows cd, would not boot.  I then tried to re-install 10.04, and it crashed again.  I installed Debian, and used grub to access the rescue partition on my drive, and re-installed Vista. 

I tried again to install Ubuntu, any version, and would not get to the first window with 9.04, or find the boot sector with 10.04.  I used a windows 7 install disk, and the command prompt to use the boot repair tools (3 times) with Bootrec.exe /bcdedit, and the fixmbr switches.  I was finally able to install Ubuntu once again.

I have several questions;
1. why does Ubuntu 10.04 automatically mount my windows drives? it leaves a way for something to reconfigure my boot files.
2. how can I disable the mounting of the C: drive.  it is not listed in fstab, and I do not want to mount it AT ALL.
3. how can I make the other ntfs partition mount only with a prompt?
4. what's up with the movie player and apparmor?
5. how can a virus etc. disable my interfaces even through the apparmor?


Ubuntu has been very very good to me. It's a great system, but it seems as though you've gotten ahead of yourselves.

Your version of grub has a problem, or there's a targeted attack going on against Ubuntu.


Yes Virginia, there is a virus/bootkit for Ubuntu.
I guess you made the big time.

---

### Post by cariboo on 2010-12-09
Please don't create multiple threads on the same subject, I have merged your two threads

---

### Post by flame retardant on 2010-12-09
sorry was new to the forum, didn't see original post and reposted.

just wanted to give a heads up, maybe help to someone with a broken system.

not a fun adventure by any means.

just so you know, movie was a tv show Xvid format

---

### Post by cariboo on 2010-12-09
> 1. why does Ubuntu 10.04 automatically mount my windows drives? it leaves a way for something to reconfigure my boot files.

Yoyr NTFS partions will only mount automatically if you set the system up that way. The partitions do show up in the file manager, but you have to click on them to mount them.

> 2. how can I disable the mounting of the C: drive. it is not listed in fstab, and I do not want to mount it AT ALL.

The partition doesn't mount automatically, unless you set it to, see first answer

> 4. what's up with the movie player and apparmor?

Show us your totem apparmor script, as there isn't a pre-made profile for it. You may get an idea of what is happening by checking the logs in  /var/log. You can also view the logs by going to System->Administration->Log File Viewer

> 5. how can a virus etc. disable my interfaces even through the apparmor?

There aren't any Linux viruses in the wild. If you were hit by one, I hope you kept a copy of it. There are many reasons why a device will seem to stop working, it could be anything from an unfinished update to network-manager crashing to something the user did by mistake. Apparmor doesn't protect interfaces, only programs that need to connect to the internet

It seems you are expecting apparmor to do more than it was designed to, are you maybe confusing apparmor with ufw/gufw?

---

### Post by flame retardant on 2010-12-09
Just to verify, yes it was an avi movie file.  

AND I DID NOT click on the import settings etc. during the install !!!!

I do not run as root, although I do run as administrator, and was not running as a sub user etc.  It is probably a VERY good idea NOT to run ubuntu as the configured user
and to create another lesser profile, although that makes installing programs a pain in the *** since you don't have sudo privileges.  As is, my boot file is exposed on the windows
partition/drive, and I could have gotten a windows Virus since it's mounted.  I have no idea how the eth0 connection disappeared, or why I could not reconfigure it.

I have posted here for EXPERTS to assess the problem, and offer suggestions so as not to have the problem again. (or anyone else for that matter).


hoping yours is a better day

---

### Post by flame retardant on 2010-12-10
to anyone who may have been insulted by my replies to this forum, sorry.

If you want to have a conversation about the problem, I am more than happy to help however I can with the matter.  One of my posts has been flagged, and I did not directly insult anyone.  I have the right to question someone's knowledge of the subject matter, and for that matter call them on it.

for whoever's edification, the windows partitions on ubuntu 10.04 are automatically mounted on bootup not by fstab (that little list) but by some script, that I don't know how to disable.

good luck

---

### Post by tgm4883 on 2010-12-10
You want to question peoples expertise that are trying to help you... ok.

> **flame retardant said:**
> Just to verify, yes it was an avi movie file.  

AND I DID NOT click on the import settings etc. during the install !!!!


Hmm, ok. Maybe it had some malicious header information or something.


> **flame retardant said:**
> 
**I do not run as root, although I do run as administrator**, and was not running as a sub user etc.  It is probably a VERY good idea NOT to run ubuntu as the configured user
and to create another lesser profile, although that makes installing programs a pain in the *** since you don't have sudo privileges.  


There is a difference between root and administrator on Linux? That is news to me.

> **flame retardant said:**
> 
As is, my boot file is exposed on the windows
partition/drive, and I could have gotten a windows Virus since it's mounted.  I have no idea how the eth0 connection disappeared, or why I could not reconfigure it.


No no no. Lets assume that Ubuntu did automatically mount your C drive. That means that your Windows drive is exposed to Linux. (and for these purposes, vice versa). You couldn't get a Windows virus from mounting the drive. Heres why

[LIST=1]
[*]Windows software doesn't run in Ubuntu. Sure you could load wine, but then you also need to mark the threat executable (in 10.04 at least)
[*]Just mounting a drive with a threat on it doesn't infect the system. Not even in Windows, you would have to run the threat.
[*]Since #2 is true, you would then need to find the threat on your Windows partition and run it. In order to run it, you would need #1 to be true
[*]And finally, the threat would need to have been written to take advantage of a Linux system. Running a Windows threat in Wine isn't going to remove your network connections in Linux
[/LIST]


> **flame retardant said:**
> 
I have posted here for EXPERTS to assess the problem, and offer suggestions so as not to have the problem again. (or anyone else for that matter).


hoping yours is a better day

Define expert?

---

