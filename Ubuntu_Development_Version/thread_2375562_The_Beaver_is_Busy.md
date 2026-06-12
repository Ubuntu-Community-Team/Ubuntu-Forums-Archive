---
title: "The Beaver is Busy"
date: 2017-10-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-10-25
I'm in:

```

ventrical@ventrical-MS-7850:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Bionic Beaver (development branch)
Release:    18.04
Codename:    bionic
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by ventrical on 2017-10-25
software-properties-gtk will still fail software&updates app after editing ubuntu.info file.

---

### Post by Chanath on 2017-10-25
> **ventrical said:**
> software-properties-gtk will still fail software&updates app after editing ubuntu.info file.

While you were at python-apt, did you notice the Blankon.info, Tanglu.info etc? I wonder why they keep these around still?

---

### Post by flocculant on 2017-10-25
> **Chanath said:**
> While you were at python-apt, did you notice the Blankon.info, Tanglu.info etc? I wonder why they keep these around still?

The best way to report this - is ubuntu-bug <package>

---

### Post by rrnbtter on 2017-10-25
Greetings,
No 'software and updates" app but proposed working just fine.


The following packages will be upgraded:
  binutils binutils-common binutils-x86-64-linux-gnu libbinutils
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,520 kB of archives.
After this operation, 1,024 B disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 binutils-x86-64-linux-gnu amd64 2.29.1-6ubuntu1 [1,825 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 libbinutils amd64 2.29.1-6ubuntu1 [502 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 binutils amd64 2.29.1-6ubuntu1 [3,344 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 binutils-common amd64 2.29.1-6ubuntu1 [190 kB]
Fetched 2,520 kB in 8s (307 kB/s)

---

### Post by Chanath on 2017-10-25
> **flocculant said:**
> The best way to report this - is ubuntu-bug <package>

Those unnecessary folders in that place don't do anything to the installed/live distro. They are just there, and were there I think in 12.04 or even earlier. I wonder why Blankon and Tanglu are there. What did these distros gave Ubuntu? 

They are not bugs, just useless stuff hanging on.

---

### Post by ventrical on 2017-10-25
> **Chanath said:**
> Those unnecessary folders in that place don't do anything to the installed/live distro. They are just there, and were there I think in 12.04 or even earlier. I wonder why Blankon and Tanglu are there. What did these distros gave Ubuntu? 

They are not bugs, just useless stuff hanging on.

Old Debain "wheezy", "lenny"  sources list files. They will get cleaned up in time.

Did you get your base files in?

Regards.

---

### Post by linuxyogi on 2017-10-25
From where did you download the 18.04 iso ? Cant find it.

---

### Post by ventrical on 2017-10-25
> **linuxyogi said:**
> From where did you download the 18.04 iso ? Cant find it.

There is none. We update the sources.list on 17.10

```

[B]sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list

[/B] [B]sudo apt-get update && sudo apt-get dist-upgrade

 [B]sudo apt-get update

[/B] [B]sudo apt-get dist-upgrade


```

or read this link : [/B][https://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](https://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)
[/B]

---

### Post by ventrical on 2017-10-25
> **rrnbtter said:**
> Greetings,
No 'software and updates" app but proposed working just fine.


I have software&updates working fine on unity-session install.

---

### Post by Chanath on 2017-10-25
Actually, you don't need to dist-upgrade, if you were in the development branch. All you have to do is change repo name and do a 'sudo apt upgrade.' The Suite: devel in the Ubuntu.info would take care of the rest. 
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu Bionic Beaver (development branch)"
```

---

### Post by ventrical on 2017-10-25
> **Chanath said:**
> Actually, you don't need to dist-upgrade, if you were in the development branch. All you have to do is change repo name and do a 'sudo apt upgrade.' The Suite: devel in the Ubuntu.info would take care of the rest. 
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu Bionic Beaver (development branch)"
```

We chose that method because there were problems in previous cycles. So it is more streamlined. You have to change the Ubuntu.info file as *early adopter* because /dev will give software-propeties-gtk error eventually.

Regards..

---

### Post by Chanath on 2017-10-25
> **ventrical said:**
> We chose that method because there were problems in previous cycles. So it is more streamlined. You have to change the Ubuntu.info file as *early adopter* because /dev will give software-propeties-gtk error eventually.

Regards..

Why should it? It is always the "development series."
  
Once you change the name of the repos, the sudo apt upgrade would take care of the matter, *if you were in the development branch all the time*. The idea is to wait few days without upgrading, once a development series become stable. The last apt upgrade should be done the day before the final release, and then wait a while, then change the repo name, do update and upgrade. You are moved to next development cycle.  

If you want to keep on moving in the development cycles, you just don't upgrade on the final release day or in the days, before the announcement of next development cycle. You do that a day or two after the announcement day. I did that today and the distros moved nicely to the bionic development cycle.

Wait > change the name of the repo > sudo apt update && sudo apt upgrade > Done!

On the question of "software-propeties-gtk error," just change the name artful to bionic, below the last "Suite: devel", that is, if you want to use the GUI application to do the upgrades. I use the terminal.

---

### Post by ventrical on 2017-10-25
> **Chanath said:**
> Why should it? It is always the "development series."
  
Once you change the name of the repos, the sudo apt upgrade would take care of the matter, *if you were in the development branch all the time*. The idea is to wait few days without upgrading, once a development series become stable. The last apt upgrade should be done the day before the final release, and then wait a while, then change the repo name, do update and upgrade. You are moved to next development cycle.  

If you want to keep on moving in the development cycles, you just don't upgrade on the final release day or in the days, before the announcement of next development cycle. You do that a day or two after the announcement day. I did that today and the distros moved nicely to the bionic development cycle.

Wait > change the name of the repo > sudo apt update && sudo apt upgrade > Done!

On the question of "software-propeties-gtk error," just change the name artful to bionic, below the last "Suite: devel", that is, if you want to use the GUI application to do the upgrades. I use the terminal.

 I personally  do an early adopters method. I don't wait "a few days"


> 
On the question of "software-propeties-gtk error," just change the name  artful to bionic, below the last "Suite: devel", that is, if you want to  use the GUI application to do the upgrades. I use the terminal.



But that's what we all do and I have already addressed this and the Ubuntu.info file is already edited: [https://ubuntuforums.org/showthread.php?t=2359108&p=13636680#post13636680](https://ubuntuforums.org/showthread.php?t=2359108&p=13636680#post13636680) for  new and current testers to use.

You should also read here: [https://ubuntuforums.org/showthread.php?t=1970289](https://ubuntuforums.org/showthread.php?t=1970289)

and here: [https://wiki.ubuntu.com/U%2B1/tester-wiki#preview](https://wiki.ubuntu.com/U%2B1/tester-wiki#preview)

but the latter is still being worked on:)

If you put up the code on your method   I can post it in  the sticky and perhaps users may prefer your way better. But you have to put up code and reasonable discussion of how to.

Regards..

---

### Post by Chanath on 2017-10-25
@ventrical

I've been moving from one development cycle to the other for quite a while. The devs know about the "software-propeties-gtk error." 
The Software upgrader works quite well. Upgrading through terminal works well too. Only the Software & Updates can't see the 'bionic' template, if the there is no line with bionic in the Ubuntu.info. That's the problem of that application, and the maintainer's. To get rid of that, you change artful to bionic, *not* devel to bionic.  Early adopting is a good thing, but one has to do it carefully. Mark mentioned the name on 24th, I moved to new development branch today. 2 days didn't make that much of a difference. 

The last upgrade few minutes ago ```
binutils binutils-common binutils-x86-64-linux-gnu gir1.2-gtk-3.0
  gnome-control-center-data gnome-control-center-faces gnome-shell-common
  gtk-update-icon-cache libbinutils libgail-3-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libnautilus-extension1a libsane-common libsane1
  mutter-common nautilus nautilus-data python3-distupgrade python3-six
  sane-utils ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
  xdg-utils 
```

As you see above, ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk are upgraded few minutes ago. It goes the same with KDE too.

---

### Post by ventrical on 2017-10-25
> **Chanath said:**
> @ventrical

I've been moving from one development cycle to the other for quite a while. The devs know about the "software-propeties-gtk error." 
The Software upgrader works quite well. Upgrading through terminal works well too. Only the Software & Updates can't see the 'bionic' template, if the there is no line with bionic in the Ubuntu.info. That's the problem of that application, and the maintainer's. To get rid of that, you change artful to bionic, *not* devel to bionic.  Early adopting is a good thing, but one has to do it carefully. Mark mentioned the name on 24th, I moved to new development branch today. 2 days didn't make that much of a difference. 

The last upgrade few minutes ago ```
binutils binutils-common binutils-x86-64-linux-gnu gir1.2-gtk-3.0
  gnome-control-center-data gnome-control-center-faces gnome-shell-common
  gtk-update-icon-cache libbinutils libgail-3-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libnautilus-extension1a libsane-common libsane1
  mutter-common nautilus nautilus-data python3-distupgrade python3-six
  sane-utils ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
  xdg-utils 
```

As you see above, ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk are upgraded few minutes ago. It goes the same with KDE too.

Chanath..

I don't want to argue preference here.  I asked specifically for  you to please post your method in [code] and I will put it on the sticky.

@ all,

Perhaps methods have changed a bit from what we posted at the recovery wiki quite some time ago. If anyone knows what Chanath is saying could you please  post it in the terminal  code that  we use of "how to" so I can paste it in the  sticky?

Thanks , Regards..

---

### Post by Frogs Hair on 2017-10-25
I opened software & updates and Apport opened to a submitted bug report/s. This happened to me with 17.10 and was resolved with an update. 

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1312673](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1312673)

---

### Post by ventrical on 2017-10-25
> **Frogs Hair said:**
> I opened software & updates and Apport opened to a submitted bug report/s. This happened to me with 17.10 and was resolved with an update. 

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1312673](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1312673)

Seems this cycle is resolving this matter a little earlier than usual. It has just been standard practicefor early adopters to paste in the Ubuntu.info file as a workaround.

Regards..

---

### Post by rrnbtter on 2017-10-25
Greetings,
Another download from "proposed" updates. 

The following NEW packages will be installed:
  libicu59 libicu59:i386
The following packages will be upgraded:
  brltty cpp-7 dpkg dpkg-dev evolution-data-server
  evolution-data-server-common g++-7 gcc-7 gcc-7-base gcc-7-base:i386
  gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 libasan4 libatomic1
  libboost-date-time1.62.0 libboost-filesystem1.62.0
  libboost-filesystem1.62.0:i386 libboost-iostreams1.62.0
  libboost-system1.62.0 libboost-system1.62.0:i386 libboost-thread1.62.0
  libbrlapi0.6 libcamel-1.2-60 libcc1-0 libcdr-0.1-1 libcilkrts5 libdpkg-perl
  libe-book-0.1-1 libebackend-1.2-10 libebook-1.2-19 libebook-contacts-1.2-2
  libecal-1.2-19 libedata-book-1.2-25 libedata-cal-1.2-28
  libedataserver-1.2-22 libedataserverui-1.2-1 libgcc-7-dev libgcc1
  libgcc1:i386 libgomp1 libharfbuzz-icu0 libharfbuzz0b libharfbuzz0b:i386
  libhfstospell9 libical2 libitm1 libjavascriptcoregtk-4.0-18 liblsan0 libmpx2
  libmspub-0.1-1 libphonenumber7 libqt5core5a libqt5dbus5 libqt5gui5
  libqt5network5 libqt5opengl5 libqt5printsupport5 libqt5sql5
  libqt5sql5-sqlite libqt5widgets5 libqt5xml5 libquadmath0 libstdc++-7-dev
  libstdc++6 libstdc++6:i386 libtag1v5 libtag1v5-vanilla libtsan0 libubsan0
  libvisio-0.1-1 libwebkit2gtk-4.0-37 libxml2 libxml2:i386 python-apt-common
  python3-apt python3-brlapi qt5-gtk-platformtheme xbrlapi
78 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 76.1 MB of archives.

---

### Post by jbicha on 2017-10-26
> **ventrical said:**
> But that's what we all do and I have already addressed this and the Ubuntu.info file is already edited: [https://ubuntuforums.org/showthread.php?t=2359108&p=13636680#post13636680](https://ubuntuforums.org/showthread.php?t=2359108&p=13636680#post13636680) for  new and current testers to use.


Instead of doing that, you could ask in #ubuntu-devel for someone to update python-apt (that's what I did). It's on the [to-do list]("https://wiki.ubuntu.com/NewReleaseCycleProcess") for opening a new Ubuntu series, but it's a very long list.

> **rrnbtter said:**
> Greetings,
Another download from "proposed" updates.


That's *really* bleeding edge. I don't know any Ubuntu developers who routinely run with -proposed enabled during the development cycle.

---

### Post by ventrical on 2017-10-26
> **jbicha said:**
> Instead of doing that, you could ask in #ubuntu-devel .

#ubuntu-devel on irc??

---

### Post by Chanath on 2017-10-26
When the development series ends, you don't know the next name, the name of the next repo, until Mark announces it. So, you don't do anything to the "Suite: devel" section in the Ubuntu.info and once you know the name, you change Suite: old-name to the new name, so the GUI app Software & Updates can see it. There is a problem with this app in "seeing," whereas the terminal, and the  Software Updater always sees the "devel" repo. 

As we are going to be in the Development Branch continuously, the devel suite should be kept as it is. There are no named repos there. Its like Debian Testing or Debian Sid; you don't change, just move on.  

Also, you change the old-name to the new-name in the sources.list and do an update and upgrade. You'd be asked to restart for the upgrade to take effect and once you restart, you are in the new development cycle.

---

### Post by Chanath on 2017-10-26
> **jbicha said:**
> 
That's *really* bleeding edge. I don't know any Ubuntu developers who routinely run with -proposed enabled during the development cycle.

I too have enabled -proposed. We can have bleeding edge in Ubuntu and Ubuntu appears to be moving forward quite fast.:)

---

### Post by cariboo on 2017-10-26
This thread is straying from it's original intent, please stay on topic, or it will be closed.

---

### Post by zika on 2017-10-26
> **jbicha said:**
> That's *really* bleeding edge. I don't know any Ubuntu developers who routinely run with -proposed enabled during the development cycle.You've made me try to remember the time I was not on proposed... Can not... ;)

---

### Post by zika on 2017-10-26
> **cariboo said:**
> This thread is straying from it's original intent, please stay on topic, or it will be closed.What is the intent/topic of this thread, anyway?

---

### Post by P-I H on 2017-10-26
I did the upgrade this way on a newly installed 17.10. It's only a little different compared to the proposed methods and I didn't get the software-properties-gtk crash.
```
sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list
sudo sed -i 's/artful/bionic/g' /usr/share/python-apt/templates/Ubuntu.info
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

---

### Post by zika on 2017-10-26
> **P-I H said:**
> I did the upgrade this way on a newly installed 17.10. It's only a little different compared to the proposed methods and I didn't get the software-properties-gtk crash.
```
sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list
sudo sed -i 's/artful/bionic/g' /usr/share/python-apt/templates/Ubuntu.info
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```I wish to stand corrected in opinion that file mentioned should have (for proper usage) at least pointers to previous version if not to all previous... As always I do have all of those pointers, as it is/was a custom/syntax... Not to mention that above all I do have devel... ;)

---

### Post by Frogs Hair on 2017-10-26
> **P-I H said:**
> I did the upgrade this way on a newly installed 17.10. It's only a little different compared to the proposed methods and I didn't get the software-properties-gtk crash.
```
sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list
sudo sed -i 's/artful/bionic/g' /usr/share/python-apt/templates/Ubuntu.info
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

Worked well , software & updates launching now.

---

### Post by Chanath on 2017-10-26
> **Frogs Hair said:**
> Worked well , software & updates launching now.

This way, the "devel" stays unmoved, only "artful" becomes "bionic." 
It would nice, if the repos are actually "devel" all the time, but freezes just about a week before the final release and then unfreezes, when the new name is announced. That way, we'd have a continuous development cycle, like "Testing" in Debian.

You can also change the repo name to devel, instead of bionic in sources.list, but it'd complain when you try to update, but still would upgrade.

```
W: Conflicting distribution: http://archive.ubuntu.com/ubuntu devel InRelease (expected devel but got bionic)W: Conflicting distribution: http://archive.ubuntu.com/ubuntu devel-updates InRelease (expected devel-updates but got bionic)
W: Conflicting distribution: http://security.ubuntu.com/ubuntu devel-security InRelease (expected devel-security but got bionic)
W: Conflicting distribution: http://archive.ubuntu.com/ubuntu devel-backports InRelease (expected devel-backports but got bionic)

```

The Software & Updates app won't work, but the Software Updater app would work.

---

### Post by ventrical on 2017-10-26
> **P-I H said:**
> I did the upgrade this way on a newly installed 17.10. It's only a little different compared to the proposed methods and I didn't get the software-properties-gtk crash.
```
sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list
sudo sed -i 's/artful/bionic/g' /usr/share/python-apt/templates/Ubuntu.info
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

I will post this in the sticky as an alternative method to upgrade to a new development cycle as an early adopter.

Regards..

---

### Post by rrnbtter on 2017-10-26
Greetings,
Post #27 works for me. Software & Updates app fixed. 
Thanks

---

### Post by jbicha on 2017-10-26
> **ventrical said:**
> #ubuntu-devel on irc??

Yes

---

### Post by ventrical on 2017-10-26
> **jbicha said:**
> Yes

Thanks.

This fixed it.  I don't mind proposed either.;)

[https://ubuntuforums.org/showthread.php?t=2359108&p=13703481#post13703481](https://ubuntuforums.org/showthread.php?t=2359108&p=13703481#post13703481)

---

### Post by ventrical on 2017-10-26
> **rrnbtter said:**
> Greetings,
Another download from "proposed" updates. 


That makes two of us ;)

---

### Post by ventrical on 2017-10-27
> **P-I H said:**
> I did the upgrade this way on a newly installed 17.10. It's only a little different compared to the proposed methods and I didn't get the software-properties-gtk crash.
```
sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list
sudo sed -i 's/artful/bionic/g' /usr/share/python-apt/templates/Ubuntu.info
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

This worked excellently on my xubuntu box upgrade.

```

ventrical@ventrical-asusbox:~$ inxi -Fxz
System:    Host: ventrical-asusbox Kernel: 4.13.0-16-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Xfce 4.12.3 (Gtk 2.24.31)
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: ASUSTeK model: P5B-E v: Rev 1.xx serial: N/A
           BIOS: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) 
           arch: Penryn rev.6 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.5 )
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1440x900@59.89hz
           OpenGL: renderer: NVD9 version: 4.3 Mesa 17.2.2 Direct Render: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 80.0GB (10.5% used)
           ID-1: /dev/sda model: ST380819AS size: 80.0GB
Partition: ID-1: / size: 73G used: 7.8G (12%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 34.0C mobo: 37.0C gpu: 40.0
           Fan Speeds (in rpm): cpu: 4218 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 179 Uptime: 3 min Memory: 458.4/3004.4MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.37 
ventrical@ventrical-asusbox:~$ 

```

---

### Post by rrnbtter on 2017-10-27
Greetings,
Bionic Proposed enabled.  115Meg updates so far today.
Artful Proposed disabled 460Kb updates today.

---

### Post by Chanath on 2017-10-28
Also do,

```
sudo sed -i 's/17.10 Artful Aardvark/18.04 Bionic Beaver/g' /usr/share/python-apt/templates/Ubuntu.info
```

---

### Post by jbicha on 2017-10-28
@Chanath, that's not needed since the python-apt update is in bionic now.

---

### Post by NikTh on 2017-10-29
> **jbicha said:**
> That's *really* bleeding edge. I don't know any Ubuntu developers who routinely run with -proposed enabled during the development cycle.
That's correct. Some developers told me (IRC) the proposed repos should remain disabled during the development cycle.

---

### Post by Chanath on 2017-10-29
> **NikTh said:**
> That's correct. Some developers told me (IRC) the proposed repos should remain disabled during the development cycle.

Any (real) reason why they should be disabled?

---

### Post by Smask on 2017-10-30
> **Chanath said:**
> Any (real) reason why they should be disabled?

Proposed packages can cause dependency problems and those may uninstall important packages or add wrong/incorrect configuration settings.


/I have proposed repo enabled
//Loves computing on the bleeding edge

---

### Post by zika on 2017-10-30
> **Smask said:**
> Proposed packages can cause dependency problems and those may uninstall important packages or add wrong/incorrect configuration settings.{Cars,guns} do not kill people, people kill people... If used with reasonable understanding aforementioned is extremely rare and even then could not be attributed to &#8222;proposed packages&#8220; alone... ;)
When in doubt just use N... ;)
Let alone I do not recommend using proposed if You're not either sure in what You're doing or ... like some of us... ;)

---

### Post by Chanath on 2017-10-30
> **zika said:**
> {Cars,guns} do not kill people, people kill people... If used with reasonable understanding aforementioned is extremely rare and even then could not be attributed to „proposed packages“ alone... ;)
When in doubt just use N... ;)
Let alone I do not recommend using proposed if You're not either sure in what You're doing or ... like some of us... ;)

Ubuntu is based on Debian Buster and Sid, so we are *always* on Testing and Unstable, so on the bleeding edge, even when we use the "stable" distro. And, here at the "development branch," we are *always* *over the bleeding edge*, so anything goes. No one knows what the next update/upgrade would bring. Adding a bit more of that instability with "proposed" enabled might only make things keel over the edge. 

For example, after few upgrades earlier there is no more Ubuntu on Wayland atm in Ubuntu 18.04. Click on Ubuntu (Default) at login get pushed to Ubuntu on Xorg (Default); echo $XDG_SESSION_TYPE gives X11. This happens, even if you don't enable "proposed."

---

### Post by zika on 2017-10-30
> **Chanath said:**
> Ubuntu is based on Debian Buster and Sid, so we are *always* on Testing and Unstable, so on the bleeding edge, even when we use the "stable" distro. And, here at the "development branch," we are *always* *over the bleeding edge*, so anything goes. No one knows what the next update/upgrade would bring. Adding a bit more of that instability with "proposed" enabled might only make things keel over the edge. 

For example, after few upgrades earlier there is no more Ubuntu on Wayland atm in Ubuntu 18.04. Click on Ubuntu (Default) at login get pushed to Ubuntu on Xorg (Default); echo $XDG_SESSION_TYPE gives X11. This happens, even if you don't enable "proposed."Not here since I'm on GnomeUnstablePPA... ;) It is even a bit worse... ;P

---

### Post by Chanath on 2017-10-30
> **zika said:**
> Not here since I'm on GnomeUnstablePPA... ;) It is even a bit worse... ;P

Using this ppa could break your system or make it unstable!;)
Just same, of course, as using the development 18.04. We are keeling over the edge.

---

### Post by zika on 2017-10-30
> **Chanath said:**
> [COLOR=#333333][FONT=monospace]Using this ppa could break your system or make it unstable![/FONT][/COLOR][FONT=arial];)
Just same, of course, as using the development 18.04. We are keeling over the edge.[/FONT]System is at most stable as much as user is and in my case it is infinitesimal if even that much... ;)
I should stop joking before I get a slap on my fingers from moderators... ;)

---

### Post by ventrical on 2017-10-30
> **Smask said:**
> Proposed packages can cause dependency problems and those may uninstall important packages or add wrong/incorrect configuration settings.


/I have proposed repo enabled
//Loves computing on the bleeding edge

I use proposed on some installs and not others. Although I have had some installs break in proposed I have also had installs break without proposed .It is more generally accepted that proposed be not checked on. It depends on preference , of how each person wants to do their testing.

Regards..

---

### Post by Chanath on 2017-10-30
> **ventrical said:**
> I use proposed on some installs and not others. Although I have had some installs break in proposed I have also had installs break without proposed .It is more generally accepted that proposed be not checked on. It depends on preference , of how each person wants to do their testing.

Regards..

We are anyway using the Testing and Unstable Debian packages (repackaged, of course), whether we use Ubuntu "stable" or "Development Branch," not guaranteed from the original source.

---

### Post by ventrical on 2017-10-30
But general study  is that proposed will break a system more readily. More advanced testers like proposed on. They are testing development. You need extra hardware and hdds. Having on partitions could be readily more difficult to recover.

So it is the conventional wisdom to keep proposed off.

---

### Post by zika on 2017-10-30
I must admit that, after I've just loked, I was well surprised that this install goes to 2013. and earlier... No major reinstall but just a good housekeeping on the other side of edge... ;)
One partition and good cloud backup of scarse stuff that is unreplaceable in event of major crash...
Update&#8321;: No, by no means, I'm not encouraging anyone to use proposed or such, I'm just pointing that proposed is not to blame... ;) Ubuntu and Linux generally is guilty of being to easy to reinstall so... Do not see much of use to have more than one install because only that way I can keep journal of what I've done on that install and get some other (let me say seriuos) job done which is the main purpose for me to even have PC or... I do not like to do l'art pour l'art install(s) just to check if I could brake it/them... I know I can but what is the fun in that... ;) Over and out... ;)

---

### Post by Chanath on 2017-10-30
> **ventrical said:**
> But general study  is that proposed will break a system more readily. More advanced testers like proposed on. They are testing development. You need extra hardware and hdds. Having on partitions could be readily more difficult to recover.

So it is the conventional wisdom to keep proposed off.

When one uses Ubuntu, whether it is the "stable" or the "development branch," one is always testing, as the packages come from Debian Testing and Unstable. So, a little bit of more instability doesn't matter much, does it?

---

### Post by ventrical on 2017-10-30
The general idea for some testers is to break ubuntu during dev cycle.  A more careful conservative tester would test pre-set corner cases where as a more liberal and daring tester would want to see breakage because it is good to examine breakage at core points. U+1 is not always smooth sailing eh.

---

### Post by jbicha on 2017-10-30
Chanath, see [this bug]("https://launchpad.net/bugs/1728616") for your issues using the 'devel' symlink.

---

### Post by Chanath on 2017-10-31
> **jbicha said:**
> Chanath, see [this bug]("https://launchpad.net/bugs/1728616") for your issues using the 'devel' symlink.

For few days, I had only devel repo enabled ([ubuntuforums.org/showthread.php?t=2375562&page=3/#30]("http://ubuntuforums.org/showthread.php?t=2375562&page=3/#30")). Later I replaced the repos with Bionic. Ubuntu.info has devel on top and bionic next. I don't use apt-get update, just apt update. Usually, when I move my systems to the new development branch, I wait until the new name is announced, then change the old name to the new name in in sources.list and in Ubuntu.info and update and upgrade. 

Apt takes care of everything and my systems are moved to the new repos. The name change in lsb-release, os-release also happened ([ubuntuforums.org/showthread.php?t=2375562&page=2/#11]("http://ubuntuforums.org/showthread.php?t=2375562&page=3/#30") and later posts).

Updates in Kubuntu, Uubuntu and in Xubuntu are getting on without any trouble to the installations, but the only problem had been with the default Ubuntu -- the Wayland doesn't boot, the default boots to Ubuntu on Xorg (Default).

---

### Post by cecilpierce on 2017-10-31
Any one know when the daily ISO might be out ?

---

