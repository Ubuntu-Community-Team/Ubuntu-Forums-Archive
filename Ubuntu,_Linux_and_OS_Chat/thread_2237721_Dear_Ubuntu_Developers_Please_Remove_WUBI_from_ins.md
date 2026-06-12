---
title: "Dear Ubuntu Developers: Please Remove WUBI from installation files."
date: 2014-08-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Doxie on 2014-08-03
Greetings all,

As a newcomer to Ubuntu from Windows I've had most difficult time attempting to run and install this operating system. I have used 3 different ISO's to do this:

1. From CD
2. From latest Desktop Download
3. From an image-burned ISO

Mounting UBUNTU on a USB enabled driver like LiLi does not work. Using Daemon tools does not work. Attempting to boot from CD using Reboot-Later or Manual Reboot and Restart Boot does not work, considering those that may also be CD-Driveless machines as well too. 

From what I found out Wubi is no longer supported, so why is this .exe still included in the latest downloads available for Ubuntu. Not only does it make installation confusing when a user sees an installation progress going fine then stops 1/3 towards the end, but we are unable to use Ubuntu at all due to persistent errors such as this:

[http://askubuntu.com/questions/317480/wubi-install-fails-could-not-retrieve-the-required-installation-files](http://askubuntu.com/questions/317480/wubi-install-fails-could-not-retrieve-the-required-installation-files)

If an installation file is no longer compatible or supported, why is it still included in the latest download builds for Ubuntu? We can't use Ubuntu OS at all with Wubi, and there is no clarity on the issue of installing Ubuntu without Wubi through spreaded information on forums through multiple threads that can be condensing and time-consuming. 

A guide to installing Ubuntu, without Wubi, would be great. The default ISO comes pre-installed with Wubi.exe so I'm not seeing a work around to installing this OS that would provide a much more stable and smoother installation process for those seeking to switch between Windows and Linux. 

As of right now, both the ISO desktop download and CD are broken. Broken, because the installations will not work. If anyone has a workable solution for this problem, feel free to post.

---

### Post by yancek on 2014-08-03
I've never used wubin and have no idea why it is still available.  There are several tutorials on the Ubuntu site, two links below.  The problem is they are either Erase and use Entire Disk or install Alongside and the problems with both is you don't see much of what is going on so if something does go wrong, you won't have any idea.  The manual option "Something Else" is better particularly, if you have another operating system.  You will need to have a basic understanding before installing and the best tutorial I have seen for this is the second link below.  There is a lot detailed information on using Linux as well as the installation process specific to Ubuntu 14.04 and there are also a number of other links to useful information.  

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)  

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Bucky Ball on 2014-08-03
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome. Not much point posting directly to the devs here. Best to either approach Canonical directly or hunt down the dev team that is involved with this. They won't see it here. 

Wubi is no longer supported by Canonical or by these forums, even though you can still find it. Please read this:

Wubi recommendations:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

PS: There are guides to numerous to mention regarding a regular install of Ubuntu.

Good luck. ;)

---

### Post by sudodus on 2014-08-03
Please [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by ian-weisser on 2014-08-03
It may be broken for you...but it certainly was not broken for me when I recently removed Windows 8.1 and installed a fresh copy of Ubuntu 14.04 on a laptop. No problems at all.

Of course, I used the safest install, and did not attempt to install WUBI.
If I recall correctly, WUBI is incompatible with Windows 8...but is fully compatible with previous versions of Windows, myriads of which are out in the wild.

---

### Post by kansasnoob on 2014-08-03
If you're trying to dual-boot with Windows just be glad it didn't eat Windows:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

The installer (ubiquity) is an absolute bloody mess :mad:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity](https://bugs.launchpad.net/ubuntu/+source/ubiquity)

---

### Post by mastablasta on 2014-08-05
> **Doxie said:**
> 

A guide to installing Ubuntu, without Wubi, would be great. The default ISO comes pre-installed with Wubi.exe so I'm not seeing a work around to installing this OS that would provide a much more stable and smoother installation process for those seeking to switch between Windows and Linux. 



yeah it would be better if they put portable virtualbox on there (like Lili does it with "Virtualize this key" option)

I think wubi still works with windows XP and possibly 7, however it should be separate download since it is not supported. These kind of things should be reported on Launchpad, developers don't visit the forums often it seems.

---

### Post by Warren Hill on 2014-08-05
> **Doxie said:**
> Greetings all,

A guide to installing Ubuntu, without Wubi, would be great. The default ISO comes pre-installed with Wubi.exe so I'm not seeing a work around to installing this OS that would provide a much more stable and smoother installation process for those seeking to switch between Windows and Linux. 



Take a look at this question on AskUbuntu [How do I Install Ubuntu]("http://askubuntu.com/q/6328/107450")

---

### Post by grahammechanical on 2014-08-06
Wubi.exe is not compatible with Windows 8 but that does not mean that it incompatible with Windows 7. And there are still some Windows 7 users out there. As for instructions.

[http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/)

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

All links are accessible from Ubuntu.com. Who told you about Wubi? It is not mentioned the official Ubuntu installation instructions for Ubuntu 14.04.1. 

Regards.

---

