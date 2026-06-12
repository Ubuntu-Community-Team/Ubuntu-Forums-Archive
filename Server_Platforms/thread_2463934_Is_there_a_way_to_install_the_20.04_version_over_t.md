---
title: "Is there a way to install the 20.04 version over the Internet or network?"
date: 2021-06-21
forum: Server Platforms
---

### Post by irv on 2021-06-21
This thread is related to this thread: [https://ubuntuforums.org/showthread.php?t=2463761]("https://ubuntuforums.org/showthread.php?t=2463761")
If you look at this link you need to go to the end of the thread post 19.
Okay, now on with this thread. I have an old PC running Ubuntu server 16.04 that is messed up. It will boot and I can do a remote into it okay, I just get a lot of errors when trying to do updates. (see other thread link.)
Because of this I what to install a newer server, (20.04). The problem is the BIOS will not see USB's and it only has a CD drive in it, not a DVD. The iso will not fit on a CD so here comes my question.
Is there a way to install the 20.04 version over the Internet or network? I prefer the Internet if I can do it remotely. I am on my desktop with a terminal open and logged on to my server.
```
irv@irv-OptiPlex-9010:~$ ssh [email]irv@wabasha-server.net[/email]
[email]irv@wabasha-server.net[/email]'s password: 
Welcome to Ubuntu 16.04.7 LTS (GNU/Linux 4.4.0-38-generic i686)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

  System information as of Mon Jun 21 10:58:16 CDT 2021

  System load:  0.06                Swap usage:          0%
  Usage of /:   83.0% of 227.14GB   Processes:           177
  Memory usage: 24%                 IP address for p3p1: 192.168.1.105

  Graph this data and manage this system at:
    [https://landscape.canonical.com/](https://landscape.canonical.com/)

203 updates can be applied immediately.
185 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

New release '18.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


Last login: Mon Jun 21 10:19:40 2021 from 192.168.1.1
irv@wabasha-server:~$ 


```
There must be a way to do this, but I have never done this before.
Any suggestions would be appreciated.

EDIT: Maybe I should have mentioned that I have download the ubuntu-20.04.2-live-server-amd64 and have it on my server. I have mounted it in "/media/iso" here is a list of the files in the iso file.
```
irv@wabasha-server:/media/iso$ ls
boot  casper  dists  EFI  install  isolinux  md5sum.txt  pool  preseed  ubuntu
```
Is there a way to run the install or boot it from there? Maybe I am thinking wrong on this.

---

### Post by tommyfun on 2021-06-21
I use these files to pxe boot off the my network and install 20.04

[http://mirrors.mit.edu/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/](http://mirrors.mit.edu/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/)

Specifically, I have the files in this directory on my tftp server: [http://mirrors.mit.edu/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/ubuntu-installer/amd64/](http://mirrors.mit.edu/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/ubuntu-installer/amd64/) 

If your computer doesn't support booting from a usb flash drive it probably doesn't support pxe booting, but you might be able to put these files on a cdrom.

I'm not sure how to put these files on a cdrom and make it bootable though, I'm just throwing it out there, maybe someone else can chime in.

good luck,
-tom

---

### Post by MAFoElffen on 2021-06-21
First, I should probably point out that the target is an old ***32bit server.***, that has been online for years and years... I know the last fresh install was 14.04, and release upgraded to it's present 16.04. And I know where it is and that you are the sole support.

*** Ubuntu dropped support for Ubuntu Server 32bit with the version he is on, at least with the install media. 32bit installers for any Ubuntu flavor, dead-ended at  Lubuntu 18.04. No other flavor of Ubuntu 18.04 had a 32bit installer..

The way to get to Ubuntu Server 18.04 32bit through a fresh install was to use the Lubuntu 18.04 Alternate Install ISO, and using Tasksel to install the Server Services, then either not installing or uninstalling the lubuntu-desktop. (Okay, it's been a few years since I did that.) There is no upgrade path to 32bit Ubuntu of any flavors, from 18.04 to 20.04. The 32bit library path ends at 19.10. The Lubuntu 18.04 Alternate Install image for 32bit is also the only image that will fit on a CD... (That machine will not boot from a USB)

Off the top of my head, 4 options...

Option 1: 


[LIST=1]
[*]Run debootstrap on the existing Ubuntu server
[*]Transfer the files to the swap partition of the server
[*]Boot into the swap partition (the debootstrap system)
[*]Transfer the files to the original root partition
[*]Boot into the new Lubuntu system and finish up the installation with tasksel, apt-get, etc
[/LIST]

  Re: [HOWTO - Install Debian Onto a Remote Linux System]("http://www.underhanded.org/papers/debian-conversion/remotedeb.html")

Option 2:
   
  
[LIST=1]
[*]Do a Lubuntu !8.04 Alternate install, from what I told you yesterday on what I do for my own servers...
[*]Create a small partition to copy ISO images to.
[*]Create a seed file for an automated install, that also (importantly) sets it's static address.
[*]Change the Grub Menu to switch over it's default to the alternate install image
[*]Before that Install reboots, interrupt it, to edit the Grub menu default back to the Live system
[/LIST]

(The first two options, I would practice on VM's, before you do it live)

Option 3:


[LIST=1]
[*]Go down to the location, where it's been running for years and do the physical maintenance on the server (blowing it out and such...)
[*]Do the initial part of the install there, with either a CD that your burned the image onto... or a hybrid of Option 3, after adding the iso image to the grub menu, and switching to it manually (while there) off the Grub menu. You don't know the physical condition of the existing CD drive... so)
[*]Do the rest of the configuration and migration from home.
[/LIST]


*** *But the first 3 options do not fix your long-term problem. It gets you to a supported system, only to 30 April, 2023. (less than two years)* ***

Option 4

[LIST]
[*]This is a non-profit Org.
[*]Get a casted off 64bit system as a "donation".
[*]I volunteered for a computer recycler. If you approached one of them, they would most likely be happy to donate a suitable 64bit system to that non-profit. Or donated by the community there.
[*]Then you can go beyond the limits and dead-end you face now.
[*]The current server could just run as is, as you set the new one up from home. The old is beyond it's EOS, so it isn't going to get updates. And besides, Apt is broken so it couldn't anyways.
[*]You have it's data backed to do the migration at your own leisure.
[*]Then just go down and unplug the old, and plug in the new metal to replace it.
[/LIST]

---

### Post by rsteinmetz70112 on 2021-06-21
For 18.04 you can do a release upgrade of 32 bit that could buy you some time I've done it on one machine. 
You can also use the 18.04 net install which uses  a minimal iso that will fit on a CD and downloads everything over the Internet, the trick there is to get access remotely or get local help. 
Once you get to 18.04  64 bit you can do a release upgrade to 20.04. 
Finally there is a network install option for 20.04 I've never used that one.

---

### Post by MAFoElffen on 2021-06-21
Please refer to the thread he linked to, And my last post. (LOL) 
> **rsteinmetz70112 said:**
> For 18.04 you can do a release upgrade of 32 bit that could buy you some time I've done it on one machine.
He cannot do a do-release-upgrade from his 16.04 to 18.04 because his apt system is fragged on an unsupported version. I mean "bad."
> **rsteinmetz70112 said:**
> You can also use the 18.04 net install which uses  a minimal iso that will fit on a CD and downloads everything over the Internet, the trick there is to get access remotely or get local help.
Okay, add one more ISO image to install fresh on 18.04, via pieces to get there. Still the same options as above, but slower, because that completely uses the official repos, instead of local repos on that image. 
> **rsteinmetz70112 said:**
> Once you get to 18.04  64 bit you can do a release upgrade to 20.04.
Once he acquires a "64bit system", he has no need to do additional work or effort to get to 20.04, than just install fresh on 20.04.
> **rsteinmetz70112 said:**
> Finally there is a network install option for 20.04 I've never used that one.
But again, 20.04 is 64bit and he would need a 64bit system to do that...

If there are other ideas, or recommendations... He would probably be open to them. It's something that has to make common sense, right?

For instance, it's been awhile, and there has been cobwebs in my head since then. When was the last Ubuntu Server Install disk that had "Repair System" on the initial Ubiquity Grub Menu as an option? I know it's been a long time, but I remember it was there at some point in time. At that point, it had the in-image logic to possibly repair what he has going on, back in his previous thread. Not a good option to where he needs to get, and still only buys him so much time, but... 


**Edit:** I just remembered another, very dangerous way to resurrect what he has and get him to a point where he can a do-release-upgrade. Again, it is dangerous. It is not recommended by anyone. I have done it a few times as a last resort. It has to be done in-person, on-site. Because this Forum is open to the world and you never know who is reading these posts, I will not post that here. And... it is still dead-ended to 18.04.

---

### Post by irv on 2021-06-21
I am going to try something tomorrow and will let you know if it works.
[https://www.plop.at/en/bootmanager/download.html]("https://www.plop.at/en/bootmanager/download.html")
I burned a CD and will see if I can use it to book from a USB in the old server hardware.

---

### Post by irv on 2021-06-22
Okay, I'm back. I tried what I said I would do in post #6, but that didn't work. So I installed 15.10.
> Welcome to Ubuntu 15.04 (GNU/Linux 3.19.0-15-generic i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue Jun 22 09:26:32 CDT 2021

  System load:  0.1                Processes:           105
  Usage of /:   0.5% of 227.14GB   Users logged in:     1
  Memory usage: 10%                IP address for p3p1: 192.168.1.105
  Swap usage:   0%

  Graph this data and manage this system at:
    [https://landscape.canonical.com/](https://landscape.canonical.com/)

0 packages can be updated.
0 updates are security updates.

Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)

New release '15.10' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Tue Jun 22 09:06:50 2021 from devicedhcp.home
irv@wabasha-server:~$ 


This worked and fixed all the errors. Before I restore all the backup files, I wanted to do a release-upgrade, but all I get is errors. It is like the next release is no longer out there.
So it is down to this, I run with this old version or get up-to-date hardware. That could be done for a couple hundred bucks, US.
Here is the ending error that I received while trying the release-upgrade.
> [http://us.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-i386/Packages) 
404 Not Found [IP: 91.189.91.38 80] 
, W:Failed to fetch 
[http://us.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-i386/Packages) 
404 Not Found [IP: 91.189.91.38 80] 
, W:Failed to fetch 
[http://us.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-i386/Packages) 
404 Not Found [IP: 91.189.91.38 80] 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
=== Command detached from window (Tue Jun 22 09:40:05 2021) ===
=== Command terminated with exit status 1 (Tue Jun 22 09:40:15 2021) ===


---

### Post by MAFoElffen on 2021-06-22
> **irv said:**
> Okay, I'm back. I tried what I said I would do in post #6, but that didn't work. [SIZE=3][COLOR=#ff0000]So I installed 15.10[/COLOR][/SIZE].


This worked and fixed all the errors. Before I restore all the backup files, I wanted to do a release-upgrade, but all I get is errors. It is like the next release is no longer out there.
So it is down to this, I run with this old version or get up-to-date hardware. That could be done for a couple hundred bucks, US.
Here is the ending error that I received while trying the release-upgrade.
Your Plop CD would not allow you to boot your USB install image?

If Plop had worked from CD, and allowed you to boot your USB (because the install image for 16.04 will not fit on CD)... then installed 16.04 LTS for repair, or as fresh, then you would have had a path from 16.04 to 18.04...

With the version you installed, the current problem is.. Interim vs LTS End of Life. 15.10 was released on October 22, 2015 and it's End of Life was July 28, 2016. The Interim Releases are only supported for one year. That is why it couldn't find the release repo. It went away years ago.

I can still talk you through making a small recovery partition for the Image and using that to install from.. Or install fresh from the Lubuntu 18.04 Alternates Installation ISO on CD... Those are options if it is staying 32bit hardware.

Or there are a few commands that I can share with you that will allow you to update 15.10 from the Ubuntu archived "Old Release" repo's, do a release upgrade to 16.04, then change it back to the Ubuntu main Repo's to do a release upgrade to 18.04. All that can be done remotely. You at least have a working system that you can do that from now.

EDIT: The Ubuntu "Old Release" repo's are still up. Artful, Breezy, Cosmic... LOL

---

### Post by irv on 2021-06-22
Plop didn't work, and the only release I could find that would fit on a CD was 15.04.
I checked the size of 16.04 and it was too big, but I must have looked at something wrong, but cause I see it will fit on a CD.
I am burning a CD as I write this and will install it and then upgrade to 18.04. The only thing I had to do after installing was to set up my static IP so I could get it on the Internet. so I could remote into it.
Will do this the first chance I get.

---

### Post by MAFoElffen on 2021-06-22
Through ssh, on the remote host, this will point your sources list to the old release archives and update the current system.
```

sudo sed -i 's/us\.archive/old\-releases/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

```

Through ssh, this will point your sources list back to the main repos, and allow it to upgrade the release to 16.04
```

sudo sed -i 's/old\-releases/us\.archive/g' /etc/apt/sources.list
sudo sed -i 's/wiley/xenial/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

```
Then you will  be able to transfer your data, do a normal update, and do a normal release upgrade to 18.04...

EDIT: Since you now installed fresh from an interim release, when you get back to 16.04 LTS, please edit /etc/update-manager/release-upgrades and set Prompt=lts, so it locks back into the LTS Release schedule, which you have kept to in the past so far.

---

### Post by irv on 2021-06-22
I got 16.04 installed and up and running.
I did a
```
sudo apt-get update
```
and then a
```
sudo apt-get upgrade
```
this took a while.
It will not do a 
```
do-release-upgrade
```
to 18.04 because it will not upgrade because the following files were kept back:
> The following packages have been kept back:
  apt apt-utils base-files dpkg libapt-pkg5.0 linux-generic
  linux-headers-generic linux-image-generic open-vm-tools python3-apt
  ubuntu-minimal ubuntu-server update-notifier-common
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

I am in the process of installing them one at a time and it seems to be working.
Got them all install and had to reboot the server to do the 
```
do-release-upgrade
```
After reboot, tried the release upgrade but here is what it tells me.
> Welcome to Ubuntu 16.04.7 LTS (GNU/Linux 4.4.0-210-generic i686)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

0 updates can be applied immediately.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

New release '18.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


Last login: Tue Jun 22 13:54:02 2021 from 140.190.55.196
irv@wabasha-server:~$ do-release-upgrade
Checking for a new Ubuntu release
No new release found.


I am ready to pull my hair out. (what I have left).
It looks like I have Ubuntu 16.04.7 LTS (GNU/Linux 4.4.0-210-generic i686) installed. Not sure why it is telling me "No new release found?"

---

### Post by MAFoElffen on 2021-06-22
Look at the "EDIT" that was in the bottom of my last post...

> EDIT: Since you now installed fresh from an interim release, when you get back to 16.04 LTS, please edit /etc/update-manager/release-upgrades and set Prompt=lts, so it locks back into the LTS Release schedule, which you have kept to in the past so far.

If you do not do that... It would still be on the interim release schedule, which would think that 16.10 was the next release, which the End of Life for 16.10 was July 20, 2017... 4 years ago. Getting it back into the LTS schedule, it will see 18.04LTS as the next release.

Either that, or:
```

sudo apt-get install update-manager-core
sudo sed -i 's/Prompt=normal/Prompt=lts/g' /etc/update-manager/release-upgrades
sudo do-release-upgrade

```
If that still doesn't work then the fallback Debian branch release upgrade method of:
```

sudo sed -i 's/xenial/bionic/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by irv on 2021-06-22
It looks like it is already set to this.
> # Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=lts
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~  

---

### Post by MAFoElffen on 2021-06-22
And the error of the do-release-upgrade script is???

Did you see what I added (later) on the last post of mine?

---

### Post by MAFoElffen on 2021-06-22
Your last posted ssh login banner did say that "18.04 LTS is available" and to do a do-release-upgrade to get it...

---

### Post by irv on 2021-06-22
I ran everything in your post 12 and it is still returning the same, "no new release found." and I am still at 16.04.7 LTS

---

### Post by irv on 2021-06-22
Now I am getting 
> irv@wabasha-server:~$ sudo apt-get update
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:5 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) xenial-infra-security InRelease
  Could not resolve host: esm.ubuntu.com
Err:6 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) xenial-infra-updates InRelease
  Could not resolve host: esm.ubuntu.com
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [https://esm.ubuntu.com/infra/ubuntu/dists/xenial-infra-security/InRelease](https://esm.ubuntu.com/infra/ubuntu/dists/xenial-infra-security/InRelease)  Could not resolve host: esm.ubuntu.com
W: Failed to fetch [https://esm.ubuntu.com/infra/ubuntu/dists/xenial-infra-updates/InRelease](https://esm.ubuntu.com/infra/ubuntu/dists/xenial-infra-updates/InRelease)  Could not resolve host: esm.ubuntu.com
W: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by irv on 2021-06-22
The file /etc/update-manager/release-upgrades is empty

---

### Post by MAFoElffen on 2021-06-22
PM me a Zoom meeting info...

---

### Post by irv on 2021-06-22
I PM you the link to zoom.

---

### Post by MAFoElffen on 2021-06-22
This is here for your reference:

This is the original 16.04 Sources List...
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

Here is a Sources list for 18.04:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner


deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```

---

### Post by irv on 2021-06-22
Well, I mark this one solved. Mike (MAFoElffen) and I spent the evening together on Zoom and got it up and running to 18.04. here it is:
> Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-147-generic i686)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

  System information as of Tue Jun 22 19:31:03 CDT 2021

  System load:  0.07               Processes:             114
  Usage of /:   1.2% of 226.87GB   Users logged in:       0
  Memory usage: 14%                IP address for enp4s0: 192.168.1.105
  Swap usage:   0%

0 updates can be applied immediately.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.


Last login: Tue Jun 22 18:39:28 2021 from 140.190.55.196


---

### Post by irv on 2021-06-23
I thought I would add one more post to this thread to tell you how we fixed the problem of all the errors I got in trying to do the upgrade to 18.04. It was s DNS error. I had to enter the command
```
sudo nano /etc/network/interfaces
```
and fix the DNS setting in this file.
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp4s0
iface enp4s0 inet static
        address 192.168.1.105
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameserver 8.8.8.8 8.8.4.4

I had to change the last line I had some mistakes in the formatting. Once this was done the upgrade worked.
Sometimes the obvious is overlooked.

EDIT: we found this out by doing a:
```
ping www.google.com
```
It did not connect with told us it as a DNS error.

---

### Post by MAFoElffen on 2021-06-23
Yes. Pinging named addresses did not work, but pinging the same's IP addresses did. Those little things matter. 

I'm glad we found the problem and everything is working and supported for him now.

---

### Post by irv on 2021-06-24
> **MAFoElffen said:**
> Yes. Pinging named addresses did not work, but pinging the same's IP addresses did. Those little things matter. 

I'm glad we found the problem and everything is working and supported for him now.

Yes, thanks for all the help Mike, it was enjoyable working with you on this problem. And my wife still can believe we had so much to talk about while we did this.
Well, I should be good until 2023 now. I have all the files back on the server and everything is running great. The only thing I had to do was clean out the .ssh folder in my home directory on my local machine so I didn't have to keep answering "yes" to the question about the key.

---

