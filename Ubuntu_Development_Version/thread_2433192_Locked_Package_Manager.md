---
title: "Locked Package Manager"
date: 2019-12-15
forum: Ubuntu Development Version
---

### Post by arkeo on 2019-12-15
Hello everyone, please forgive me if this has been answered elsewhere but I couldn't find anything.
Less than a a week ago I updated the distro from 19.10 to 20.04 (on a spare laptop) and I check daily for updates, so I basically keep a "rolling development version" of vanilla Ubuntu.
BUT.
When I run "apt update" I always get this error message: "E: Could not get lock /var/lib/apt/lists/lock. It is held by process 51149 (packagekitd) - open (11: Resource temporarily unavailable)E: Could not get lock /var/lib/apt/lists/lock. It is held by process 51149 (packagekitd) - open (11: Resource temporarily unavailable)".

The PID is always different, I just type "kill xxxx" and apt starts working again perfectly. My guess is that it is Ubuntu Software trying to automate something which I'd like to do manually. Am I correct in this assumption? Is there a way to keep Ubuntu Software from respawning itself, forcing me every time to kill its PID? Or is it something different altogether?

Thanks in advance to you all,

Arkeo

---

### Post by Frogs Hair on 2019-12-15
That message is most often associated with having two package management tools open at the same time. An example would be updating via the terminal while the software updater is starting up or running.

---

### Post by oldfred on 2019-12-15
I have had same issue.
As soon as you boot, it checks for updates.

But in some of the slow boot threads, they change daily timer.
       [https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297](https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297)
This is Debian bug #844453. apt-daily.service shouldn't be run during boot
in /etc/systemd/system/apt-daily.timer.d/override.conf
/etc/systemd/system 

      
 [https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)
sudo systemctl edit apt-daily.timer
q
# apt-daily timer configuration override
[Timer]
OnBootSec=15min
OnUnitActiveSec=1d
AccuracySec=1h
RandomizedDelaySec=30min

---

### Post by arkeo on 2019-12-17
I tried opening Ubuntu Software just to check the settings. Same Error msg.

How many package managers are running at the same time???

Synaptic is NOT running.
Ubuntu Software is NOT running.
APT is NOT running.

Very Win10-like...

---

### Post by ajgreeny on 2019-12-17
But "unattended-upgrades" might be; if you really want to upgrade everything manually yourself you can remove that with ```
sudo apt remove unattended-upgrades
``` which I always do, preferring to know exactly what is happening, and when.

Please note I have edited your post removing language which is not "family friendly"; please keep your posts free from this in future.

---

### Post by arkeo on 2019-12-17
Thanks ajgreeny! I'll try that!
My apologies for my language not being family friendly--it was just frustration... Cheers!

---

### Post by arkeo on 2019-12-25
The problem seems to be gone with the latest updates (since a week or so): I don't have to kill any process keeping the whatever/it/is locked. apt update and apt upgrade always work now, which I much prefer to Ubuntu Software and its related Updater. BTW, the packages installed by UbSoft and those installed by APT are different, right? For example, VLC from UbSoft should be a snap/flat or one of those newfangled packages, while if I install it via APT it should be the same old thing I learnt in college oh-so-many years ago, correct?

---

### Post by oldfred on 2019-12-25
Yes

But I turn snaps off totally.
And then when I installed Chromium, it installed a snap. They say it will only be available as a snap.
But there still are ppa where you can still get a .deb version.

---

### Post by deadflowr on 2019-12-25
> BTW, the packages installed by UbSoft and those installed by APT are different, right? 

Ubsoft, which I guess means Ubuntu Software, installs all, apt, flatpak and snap.
By default it always installs apt packages , but can install snaps and flatpaks if the additional plugins for those are also installed first.
(Ubuntu ships with the snap plugin, but not the flatpak plugin.)

The devil is in the Details, literally, as to which package type is being installed in Ubuntu Software.
Packages tell where they come from in the source entry in the Package's Software Details listing.
(typically you have to scroll down to see the Details section of the package on the package's Ubuntu Software Homepage)

(All snaps come from the Snap Store. Flatpak's come from places typically like flathub, but aren't restricted to just that, there are other flatpak repos,
and apt depends on various apt repositories but typically show as from the current in-use release and the archive, so it'd show up as something like focal-universe)

---

### Post by arkeo on 2019-12-26
> **oldfred said:**
> But I turn snaps off totally.

Very interesting! How do you do that?

I admit SW packages is a very interesting concept in the fragmented Linux world (but of course, it has been already fragmented as well... :roll: ) but not mature yet to my tastes. I'd much rather stick to apt-get (well, just apt now)... Just my 2 ¢...

---

### Post by oldfred on 2019-12-26
I should have said I totally remove snaps. It does not prevent a new install as I found when it installed Chromium. 

       sudo apt autoremove --purge snapd

---

### Post by arkeo on 2019-12-27
Does this mean that when I daily run apt update/upgrade snap packages such as VLC (I installed it via Ubuntu Software and checked the details, and *it is* a snap package) and basically all of the other snaps *do not* get in fact upgraded?
Meaning, I should remove the snap package in question, VLC to remain in the example, and then reinstall it again via apt/synaptic in order for it to update daily ?

Thanks, and I'm sorry but I find all of this a bit confusing: I do not believe it was a very wise decision to mix the 2 approaches. By the way, are snap or flat mature enough to be able to support an entire distro by themselves, meaning without a parallel update line like apt or yum? I suppose not: low level stuff like the kernel for example I don't think can be packaged. Or can it?

---

### Post by Frogs Hair on 2019-12-27
The snap and flathub repositories  are fairly limited right now and are maintained by those creating and developing the packages. There is no need to remove any snaps unless you truly don't want them. One Linux distribution, Deepin is using flatpack for their native applications, but that is work in progress and a mixed bag. Remember that you are using a development release and unlike a standard release updates maybe available more than once a day and there can be package manager and other types of problems, that's just part of testing.

   There are also snaps that are added directly to the release repositories by Ubuntu developers and can include themes,calculator,and other applications.These applications will have Canonical listed as the publisher.  
    
```
snap list
Name                   Version                  Rev   Tracking  Publisher     Notes
core                   16-2.42.5                8268  stable    canonical&#10003;    core
core18                 20191212                 1288  stable    canonical&#10003;    base
gtk-common-themes      0.1-25-gcc83164          1353  stable    canonical&#10003; 
```   



[https://flathub.org/home](https://flathub.org/home)

[https://snapcraft.io/store](https://snapcraft.io/store)

---

### Post by Dennis N on 2019-12-27
> Does this mean that when I daily run apt update/upgrade snap packages such as VLC (I installed it via Ubuntu Software and checked the details, and *it is* a snap package) and basically all of the other snaps *do not* get in fact upgraded?
Meaning, I should remove the snap package in question, VLC to remain in the example, and then reinstall it again via apt/synaptic in order for it to update daily ?
Snaps update automatically, and by default, the snapd daemon checks for updates 4 times a day. Each update check is called a refresh. **apt** does not handle snap package updating.

---

### Post by arkeo on 2019-12-27
> **Dennis N said:**
> **apt** does not handle snap package updating.

Thanks for clarifying that, I just wasn't sure if and when snap updates would occur.

---

### Post by arkeo on 2019-12-27
> **Frogs Hair said:**
> Remember that you are using a development release and unlike a standard release updates maybe available more than once a day and there can be package manager and other types of problems, that's just part of testing.

Oh I'm not complaining about that :D
I just wanted to understand better how the update process works in this "mixed" snap/apt environment *exactly* because I knew that in a development version updates would be more frequent and wanted to make sure I was getting them all...
In a regular release I would just let Ubuntu notify me when updates were available, wouldn't really care about where they came from (snap repo or apt).

---

### Post by arkeo on 2020-01-05
> **arkeo said:**
> The problem seems to be gone with the latest updates

Aaaand now it's back. :roll:

What *is* going on?

---

### Post by Frogs Hair on 2020-01-05
You might want to back up and try a clean installation of the latest daily build. I upgraded during the last testing cycle and had the same problem until a clean installation was used. If i tried any form of manual updating the package system would often lock . The following command was a work-around though the clean installation saved more time in the long run. 

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a 
```
 
[http://cdimage.ubuntu.com/ubuntu/daily-live/pending/](http://cdimage.ubuntu.com/ubuntu/daily-live/pending/)

---

### Post by arkeo on 2020-01-06
I've been out the Linux world for a while and it just now occurred to me to actually identify the process *before* killing it... :lolflag:

It turns out it's **packagekitd** that keeps respawning, and it's keeping /var/lib/apt/lists/lock locked. I removed unattended-upgrades as well but it doesn't change anything that I can see... :confused:

---

### Post by logix2 on 2020-01-15
I have some virtual machines for testing where this kept happening. It was a combination due to Unattended Upgrades and me shutting down the VM without allowing it to install all the updates. I would get those pesky "Could not get lock /var/lib/dpkg/lock" errors all the time. 

Until I found out it was due to Unattended Upgrades, I would normally fix it by using ([source]("https://www.linuxuprising.com/2018/07/how-to-fix-could-not-get-lock.html")):

```
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
sudo apt install -f
```

I know that's not exactly nice, but it works. But after disabling Unattended Upgrades, this stopped happening (maybe it happened two or three times since then, but very rarely anyway).

---

