---
title: "Unattended-upgrades can break persistent live media"
date: 2016-08-31
forum: Ubuntu Development Version
---

### Post by sudodus on 2016-08-31
Looking at the persistent live Ubuntu 16.04 LTS system - the Software & Updates screen / Update - I notice, that ***Automatic updates is set to 'Download and install automatically'***. This is bad in a persistent live system.
	
After leaving the persistent live Ubuntu 16.04 LTS system running overnight, I found that it had performed an automatic upgrade:   	 
	
***df*** revealed that the content in **casper-rw** had increased to 1.6 GiB.

This is risky: If not enough space (and inodes) in the casper-rw partition or file, the upgrade operation will be incomplete and fail. There might be big problems even if there is space left in casper-rw, and finally, this is wasting the available space, unless you have a huge casper-rw partition.

I am surprised that the persistent live system started an automatic upgrade. I don't think it is caused by the installer (mkusb), because the files controlling those actions are not touched. I can test what happens in an Ubuntu 16.04.1 LTS system, that I leave by itself for a long time.

Until this is resolved, it is a good idea to disable unattended-upgrades, but above all, to take regular backups, when you use a persistent live system.

***Is this a bug?***

Should I write a bug report about it? In that case against which package?

[hr][/hr]
See the following links for more details,

[Unattended-upgrades broke persistent live media](https://askubuntu.com/questions/817750/unattended-upgrades-broke-persistent-live-media/817820#)

[reply with output from df](https://ubuntuforums.org/showthread.php?t=1958073&page=20&p=13538379#post13538379)

---

### Post by jbicha on 2016-08-31
> **sudodus said:**
> 

***Is this a bug?***

Should I write a bug report about it? In that case against which package?



Yes, I think it would be useful for you to file a bug against casper. There are various scripts in that package that change things to be more appropriate for the live environment.

---

### Post by sudodus on 2016-08-31
Thanks, jbicha :-)

---

### Post by sudodus on 2016-09-01
***Survey to find affected flavours and versions***

[table="width: 720, class: grid, align: left"]
[tr]
	[td] Flavour & version [/td]
	[td] Security update setting [/td]
	[td] Comment [/td]
[/tr][tr]
	[td] Lubuntu 14.04.1 LTS [/td]
	[td] Display immediately [/td]
	[td][/td]
[/tr]
[tr]
	[td] Ubuntu 14.04.1 LTS [/td]
	[td] Display immediately [/td]
	[td][/td]
[/tr]
[tr]
	[td] Xubuntu 14.04.5 LTS [/td]
	[td] Display immediately [/td]
	[td][/td]
[/tr]
[tr]
	[td] [color="#cc0000"]Ubuntu 16.04 LTS[/color] [/td]
	[td] Download and install automatically [/td]
	[td]  Reported update & dist-upgrade  [/td]
[/tr]
[tr]
	[td] [color="#cc0000"]Mythbuntu 16.04 LTS[/color] [/td]
	[td]Download and install automatically[/td]
	[td] Reported update & dist-upgrade [/td]
[/tr]
[tr]
	[td] [color="#cc0000"]Kubuntu 16.04.1 LTS[/color] [/td]
	[td] Install security updates without confirmation [/td]
	[td] alias 'Download and install automatically' [/td]
[/tr]
[tr]
	[td] Lubuntu 16.04.1 LTS [/td]
	[td] Display immediately [/td]
	[td][/td]
[/tr]
[tr]
	[td] [color="#cc0000"]Ubuntu 16.04.1 LTS[/color] [/td]
	[td] Download and install automatically [/td]
	[td] Reported update & dist-upgrade [/td]
[/tr]
[tr]
	[td] [color="#cc0000"]Xubuntu 16.04.1 LTS daily 2016-08-31[/color] [/td]
	[td] Download and install automatically [/td]
	[td][/td]
[/tr]
[tr]
	[td] Lubuntu Yakkety beta [/td]
	[td] Display immediately [/td]
	[td][/td]
[/tr]
[tr]
	[td] [color="#cc0000"]Ubuntu Yakkety daily 2016-08-31[/color] [/td]
	[td] Download and install automatically [/td]
	[td][/td]
[/tr]

[/table]

If you are running a persistent live system, I suggest that you select 'Display immediately', if your flavour and version is affected. See the attached screenshots.

---

### Post by sudodus on 2016-09-01
I created this Launchpad bug report: [Bug #1619188: Unattended upgrades can break persistent live media](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1619188)

Please mark 'Affects me too' to confirm the bug at Launchpad.

---

### Post by sudodus on 2016-09-01
Would these changes be enough to change the setting from 'Download and install automatically' to 'Display immediately' in Ubuntu 16.04.1 LTS? I mean during live and persistent live sessions.

```
ubuntu@ubuntu:/etc/apt/apt.conf.d$ [COLOR="#0000FF"]for i in *;do diff $i orig || echo "^^^ diff in $i";done[/COLOR]
4d3
< APT::Periodic::Unattended-Upgrade "0";
^^^ diff in 10periodic
2,4c2
< APT::Periodic::Download-Upgradeable-Packages "0";
< APT::Periodic::AutocleanInterval "0";
< APT::Periodic::Unattended-Upgrade "0";
---
> APT::Periodic::Unattended-Upgrade "1";
^^^ diff in 20auto-upgrades
ubuntu@ubuntu:/etc/apt/apt.conf.d$
```

See also the attached screenshot.

Are these updating settings saved somewhere else in other versions?

Are there other files that would need modifications too?

---

### Post by sudodus on 2016-09-01
I understand that the following format is better for patching: **diff -u old-file newfile**

```

[COLOR="#0000FF"]ubuntu@ubuntu:/etc/apt/apt.conf.d$ **for i in *;do diff -u orig/$i .;done**[/COLOR]
--- orig/10periodic	2016-05-24 16:48:53.000000000 +0000
+++ ./10periodic	2016-09-01 16:56:26.303618989 +0000
@@ -1,3 +1,4 @@
 APT::Periodic::Update-Package-Lists "1";
 APT::Periodic::Download-Upgradeable-Packages "0";
 APT::Periodic::AutocleanInterval "0";
+APT::Periodic::Unattended-Upgrade "0";
--- orig/20auto-upgrades	2016-02-18 22:19:18.000000000 +0000
+++ ./20auto-upgrades	2016-09-01 16:56:26.303618989 +0000
@@ -1,2 +1,4 @@
 APT::Periodic::Update-Package-Lists "1";
-APT::Periodic::Unattended-Upgrade "1";
+APT::Periodic::Download-Upgradeable-Packages "0";
+APT::Periodic::AutocleanInterval "0";
+APT::Periodic::Unattended-Upgrade "0";
[COLOR="#696969"]diff: orig/orig: No such file or directory[/COLOR]
[COLOR="#0000FF"]ubuntu@ubuntu:/etc/apt/apt.conf.d$ [/COLOR]
```

---

### Post by jis on 2016-09-02
> **sudodus said:**
> Would these changes be enough to change the setting from 'Download and install automatically' to 'Display immediately' in Ubuntu 16.04.1 LTS? I mean during live and persistent live sessions.
...
Are these updating settings saved somewhere else in other versions?

Are there other files that would need modifications too?

I think so yes.

Not that I know.

I don't think so, respectively.

But does this change the default setting of the system installed by the persistent live system later, as well?

---

### Post by sudodus on 2016-09-02
Thanks for replying and confirming the bug :-)

> **jis said:**
> But does this change the default setting of the system installed by the persistent live system later, as well?

I don't think so. At least it *should* be considered and avoided by the developer when squashing the bug, and tested by us before releasing the bug-fix.

***Edit:*** I tested with Ubuntu 16.04.1 LTS, and changing this setting in the persistent live system (to Display immediately') did *not* change the setting in the installed system.

---

### Post by sudodus on 2016-09-03
***mkusb version 11.0.2*** is uploaded to [ppa:mkusb/unstable](https://help.ubuntu.com/community/mkusb/gui#from_the_unstable_PPA) for testing. I hope it will provide a better solution than the advice to use the graphical user interface. (I think many people who need that kind of advice will not find it before it is too late.)

But the best long term solution is to modify Ubuntu with different default settings for live and persistent live systems. Installed systems can keep the current default (in 16.04.1 LTS).

See this link: [Solutions in the pipeline](https://help.ubuntu.com/community/mkusb/persistent#Solutions_in_the_pipeline)

---

### Post by sudodus on 2016-09-04
I tested a live only session with Ubuntu 16.04.1 LTS amd64 last night and it did an unattended upgrade, and after that it used 726 MiB of the allocated space for the root file system:

```
ubuntu@ubuntu:~$ df -h .
Filesystem Size Used Avail Use% Mounted on
/cow 1.9G 21M 1.9G 2% /
ubuntu@ubuntu:~$ df -h .
Filesystem Size Used Avail Use% Mounted on
/cow 1.9G 726M 1.2G 38% /
ubuntu@ubuntu:~$ df -hi .
Filesystem Inodes IUsed IFree IUse% Mounted on
/cow 480K 37K 443K 8% /
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 16.04.1 LTS
Release: 16.04
Codename: xenial
ubuntu@ubuntu:~$
```

This system has 4 GB RAM, half of it was made available for this ramdrive automatically. No swap partition was available. The system could handle it, but this is really eating capacity from the live session.

---

### Post by sudodus on 2016-09-11
I made a long time test with a persistent live Ubuntu 16.04.1 LTS amd64 (made with mkusb) during several days and nights and it did ***no*** unattended upgrade. So the tweak in mkusb version 11.0.2 works for me :-)

You find it at the unstable PPA. See this link: [[mkusb] from the unstable PPA](https://help.ubuntu.com/community/mkusb/gui#from_the_unstable_PPA)

---

### Post by sudodus on 2016-10-06
There is a fix in Yakkety, and it is prepared for Xenial :-)

Please test that it works for you according to this link:

[Comment 32 for bug 1619188: 'Please test proposed package'](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1619188/comments/32)

---

### Post by ventrical on 2016-10-07
I am getting 'apache forbids' etc.. so I did this on yakkety release candidate.

[https://www.youtube.com/watch?v=B4ARAtpImVo](https://www.youtube.com/watch?v=B4ARAtpImVo)  

```

ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
aufs            1.5G  373M  1.2G  25% /
ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
aufs            1.5G  373M  1.2G  25% /
ubuntu@ubuntu:~$ df -hi .
Filesystem     Inodes IUsed IFree IUse% Mounted on
aufs             376K  4.0K  372K    2% /
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 4.8.0-19-generic #21-Ubuntu SMP Thu Sep 29 19:39:23 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Yakkety Yak (development branch)
Release:    16.10
Codename:    yakkety
ubuntu@ubuntu:~$ 



```

---

### Post by sudodus on 2016-10-07
Nice video clip :-)

It works like the following description for me (tested so far only in Yakkety)

- There are no unattended upgrades in a líve session.
- But the information at the Software & Updates screen / Update tab in Automatic updates is still set to 'Download and install automatically'.

Is this also the case for you? (Did you test overnight to check if there will be significantly more used space in the root partition. See the comments in the bug report, where I am discussing it with Brian Murray).

In other words - is the hard bug fixed (upgrades are no longer filling the drive space), but a soft bug remains (it is still announcing that it will fill the drive space, when there are security upgrades to fetch)? :-P

---

### Post by ventrical on 2016-10-07
At this stage I think the bug is not fixed with proposed method, however using mkusb/unstable presented the option to fix the status to "display immediately" . Otherwise. with proposed enabled it did not change any status.. but I did not leave usb  on all night. I could do that but your test is proof enough. Uhh.. I have other machines I can let sit for 24 hours.

[https://www.youtube.com/watch?v=ayWxYNzr5CQ&feature=youtu.be](https://www.youtube.com/watch?v=ayWxYNzr5CQ&feature=youtu.be)

regards..

---

### Post by ventrical on 2016-10-07
> **sudodus said:**
> Nice video clip :-)

It works like the following description for me (tested so far only in Yakkety)

- There are no unattended upgrades in a líve session.
- But the information at the Software & Updates screen / Update tab in Automatic updates is still set to 'Download and install automatically'.

Is this also the case for you? (Did you test overnight to check if there will be significantly more used space in the root partition. See the comments in the bug report, where I am discussing it with Brian Murray).

In other words - is the hard bug fixed (upgrades are no longer filling the drive space), but a soft bug remains (it is still announcing that it will fill the drive space, when there are security upgrades to fetch)? :-P

Ok.. yakkety has casper 1.379
Yes.. it is still 'download and install automatically'

I will let this DT run throughout the night.

---

### Post by ventrical on 2016-10-08
No real change with yakkety stack.

```

ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
aufs           1000M  260M  740M  27% /
ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
aufs           1000M  260M  740M  27% /
ubuntu@ubuntu:~$ df -hi .
Filesystem     Inodes IUsed IFree IUse% Mounted on
aufs             250K  4.3K  246K    2% /
ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
aufs           1000M  270M  730M  28% /
ubuntu@ubuntu:~$ df -hi .
Filesystem     Inodes IUsed IFree IUse% Mounted on
aufs             250K  4.5K  246K    2% /
ubuntu@ubuntu:~$ 

```

now xenial release stack test.

---

### Post by sudodus on 2016-10-08
Your result is matching mine :-)

I'm looking forward to your test in Xenial :-P

---

### Post by ventrical on 2016-10-08
Just loaded now .. without fix. I am going to let it run  for the day.

Here is current:

```

ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
/cow           1000M   71M  930M   8% /
ubuntu@ubuntu:~$ df -hi .
Filesystem     Inodes IUsed IFree IUse% Mounted on
/cow             250K   896  250K    1% /
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
ubuntu@ubuntu:~$ 


```

---

### Post by ventrical on 2016-10-09
Overnight changes.

```

Linux ubuntu 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
/cow           1000M   74M  927M   8% /
ubuntu@ubuntu:~$ df -hi .
Filesystem     Inodes IUsed IFree IUse% Mounted on
/cow             250K  1.2K  249K    1% /
ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
/cow           1000M   77M  924M   8% /
ubuntu@ubuntu:~$ df -hi .
Filesystem     Inodes IUsed IFree IUse% Mounted on
/cow             250K  1.2K  249K    1% /
ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
/cow           1000M   78M  923M   8% /
ubuntu@ubuntu:~$ df -hi .
Filesystem     Inodes IUsed IFree IUse% Mounted on
/cow             250K  1.2K  249K    1% /
ubuntu@ubuntu:~$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
/cow           1000M  942M   59M  95% /
ubuntu@ubuntu:~$ df -hi .
Filesystem     Inodes IUsed IFree IUse% Mounted on
/cow             250K  9.1K  241K    4% /
ubuntu@ubuntu:~$ 

```


looks like it did an upgrade overnight..

8GB verbatim store n go

---

### Post by sudodus on 2016-10-09
Could it be an update according to this link?

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1619188/comments/29](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1619188/comments/29)

> You can look for file dates in **/var/lib/apt/lists/**

I think an upgrade would increase the used space more, because the downloaded and installed files would reside in the overlay system.

---

### Post by ventrical on 2016-10-09
Well here is what the unattended-ugrades&dpkg logs say

```

Log started: 2016-10-09  03:41:26
 Extracting templates from packages: 16% Extracting templates from packages: 33% Extracting templates from packages: 49% Extracting templates from packages: 66% Extracting templates from packages: 82% Extracting templates from packages: 99% Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191101 files and directories currently installed.) 
Preparing to unpack .../libsystemd0_229-4ubuntu10_amd64.deb ... 
Unpacking libsystemd0:amd64 (229-4ubuntu10) over (229-4ubuntu4) ... 
Processing triggers for libc-bin (2.23-0ubuntu3) ... 
Setting up libsystemd0:amd64 (229-4ubuntu10) ... 
Processing triggers for libc-bin (2.23-0ubuntu3) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191101 files and directories currently installed.) 
Preparing to unpack .../libpam-systemd_229-4ubuntu10_amd64.deb ... 
Unpacking libpam-systemd:amd64 (229-4ubuntu10) over (229-4ubuntu4) ... 
Preparing to unpack .../systemd_229-4ubuntu10_amd64.deb ... 
Unpacking systemd (229-4ubuntu10) over (229-4ubuntu4) ... 
Processing triggers for man-db (2.7.5-1) ... 
Processing triggers for ureadahead (0.100.0-19) ... 
Processing triggers for dbus (1.10.6-1ubuntu3) ... 
Setting up systemd (229-4ubuntu10) ... 
Installing new version of config file /etc/systemd/system.conf ... 
addgroup: The group `systemd-journal' already exists as a system group. Exiting. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191102 files and directories currently installed.) 
Preparing to unpack .../udev_229-4ubuntu10_amd64.deb ... 
Unpacking udev (229-4ubuntu10) over (229-4ubuntu4) ... 
Preparing to unpack .../libudev1_229-4ubuntu10_amd64.deb ... 
Unpacking libudev1:amd64 (229-4ubuntu10) over (229-4ubuntu4) ... 
Processing triggers for systemd (229-4ubuntu10) ... 
Processing triggers for ureadahead (0.100.0-19) ... 
Processing triggers for man-db (2.7.5-1) ... 
Processing triggers for libc-bin (2.23-0ubuntu3) ... 
Setting up libudev1:amd64 (229-4ubuntu10) ... 
Processing triggers for libc-bin (2.23-0ubuntu3) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191103 files and directories currently installed.) 
Preparing to unpack .../systemd-sysv_229-4ubuntu10_amd64.deb ... 
Unpacking systemd-sysv (229-4ubuntu10) over (229-4ubuntu4) ... 
Processing triggers for man-db (2.7.5-1) ... 
Setting up systemd-sysv (229-4ubuntu10) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191103 files and directories currently installed.) 
Preparing to unpack .../libfontconfig1_2.11.94-0ubuntu1.1_amd64.deb ... 
Unpacking libfontconfig1:amd64 (2.11.94-0ubuntu1.1) over (2.11.94-0ubuntu1) ... 
Preparing to unpack .../fontconfig-config_2.11.94-0ubuntu1.1_all.deb ... 
Unpacking fontconfig-config (2.11.94-0ubuntu1.1) over (2.11.94-0ubuntu1) ... 
Preparing to unpack .../libexpat1_2.1.0-7ubuntu0.16.04.2_amd64.deb ... 
Unpacking libexpat1:amd64 (2.1.0-7ubuntu0.16.04.2) over (2.1.0-7) ... 
Preparing to unpack .../fontconfig_2.11.94-0ubuntu1.1_amd64.deb ... 
Unpacking fontconfig (2.11.94-0ubuntu1.1) over (2.11.94-0ubuntu1) ... 
Preparing to unpack .../libubsan0_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libubsan0:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libtsan0_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libtsan0:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libgomp1_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libgomp1:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libitm1_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libitm1:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libatomic1_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libatomic1:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libasan2_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libasan2:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../liblsan0_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking liblsan0:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libcilkrts5_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libcilkrts5:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libmpx0_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libmpx0:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libquadmath0_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libquadmath0:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../cpp-5_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking cpp-5 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libcc1-0_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libcc1-0:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../binutils_2.26.1-1ubuntu1~16.04.3_amd64.deb ... 
Unpacking binutils (2.26.1-1ubuntu1~16.04.3) over (2.26-8ubuntu2) ... 
Preparing to unpack .../g++-5_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking g++-5 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../gcc-5_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking gcc-5 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libgcc-5-dev_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libgcc-5-dev:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../libstdc++-5-dev_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libstdc++-5-dev:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Preparing to unpack .../gcc-5-base_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking gcc-5-base:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Processing triggers for libc-bin (2.23-0ubuntu3) ... 
Processing triggers for man-db (2.7.5-1) ... 
Processing triggers for doc-base (0.10.7) ... 
Processing 33 changed doc-base files... 
Setting up gcc-5-base:amd64 (5.4.0-6ubuntu1~16.04.2) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191106 files and directories currently installed.) 
Preparing to unpack .../libstdc++6_5.4.0-6ubuntu1~16.04.2_amd64.deb ... 
Unpacking libstdc++6:amd64 (5.4.0-6ubuntu1~16.04.2) over (5.3.1-14ubuntu2) ... 
Processing triggers for libc-bin (2.23-0ubuntu3) ... 
Setting up libstdc++6:amd64 (5.4.0-6ubuntu1~16.04.2) ... 
Processing triggers for libc-bin (2.23-0ubuntu3) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191106 files and directories currently installed.) 
Preparing to unpack .../libxml2_2.9.3+dfsg1-1ubuntu0.1_amd64.deb ... 
Unpacking libxml2:amd64 (2.9.3+dfsg1-1ubuntu0.1) over (2.9.3+dfsg1-1) ... 
Preparing to unpack .../libmagickwand-6.q16-2_8%3a6.8.9.9-7ubuntu5.1_amd64.deb ... 
Unpacking libmagickwand-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.1) over (8:6.8.9.9-7ubuntu5) ... 
Preparing to unpack .../libmagickcore-6.q16-2_8%3a6.8.9.9-7ubuntu5.1_amd64.deb ... 
Unpacking libmagickcore-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.1) over (8:6.8.9.9-7ubuntu5) ... 
Preparing to unpack .../imagemagick-common_8%3a6.8.9.9-7ubuntu5.1_all.deb ... 
Unpacking imagemagick-common (8:6.8.9.9-7ubuntu5.1) over (8:6.8.9.9-7ubuntu5) ... 
Preparing to unpack .../libreoffice-ogltrans_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-ogltrans (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../ure_5.1.4-0ubuntu1_amd64.deb ... 
Unpacking ure (5.1.4-0ubuntu1) over (5.1.2-0ubuntu1) ... 
Preparing to unpack .../uno-libs3_5.1.4-0ubuntu1_amd64.deb ... 
Unpacking uno-libs3 (5.1.4-0ubuntu1) over (5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-calc_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-calc (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-impress_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-impress (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-draw_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-draw (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-gnome_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-gnome (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-gtk_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-gtk (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../python3-uno_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking python3-uno (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-style-galaxy_1%3a5.1.4-0ubuntu1_all.deb ... 
Unpacking libreoffice-style-galaxy (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-style-breeze_1%3a5.1.4-0ubuntu1_all.deb ... 
Unpacking libreoffice-style-breeze (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-common_1%3a5.1.4-0ubuntu1_all.deb ... 
Unpacking libreoffice-common (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-pdfimport_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-pdfimport (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-math_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-math (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-base-core_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-base-core (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-avmedia-backend-gstreamer_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-avmedia-backend-gstreamer (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-writer_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-writer (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
Preparing to unpack .../libreoffice-core_1%3a5.1.4-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-core (1:5.1.4-0ubuntu1) over (1:5.1.2-0ubuntu1) ... 
dpkg: error processing archive /var/cache/apt/archives/libreoffice-core_1%3a5.1.4-0ubuntu1_amd64.deb (--unpack): 
 unable to make backup link of './usr/lib/libreoffice/program/libooxlo.so' before installing new version: No space left on device 
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Preparing to unpack .../libgdk-pixbuf2.0-0_2.32.2-1ubuntu1.2_amd64.deb ... 
Unpacking libgdk-pixbuf2.0-0:amd64 (2.32.2-1ubuntu1.2) over (2.32.2-1ubuntu1) ... 
Preparing to unpack .../libgdk-pixbuf2.0-common_2.32.2-1ubuntu1.2_all.deb ... 
Unpacking libgdk-pixbuf2.0-common (2.32.2-1ubuntu1.2) over (2.32.2-1ubuntu1) ... 
Preparing to unpack .../fonts-opensymbol_2%3a102.7+LibO5.1.4-0ubuntu1_all.deb ... 
Unpacking fonts-opensymbol (2:102.7+LibO5.1.4-0ubuntu1) over (2:102.7+LibO5.1.2-0ubuntu1) ... 
Preparing to unpack .../curl_7.47.0-1ubuntu2.1_amd64.deb ... 
Unpacking curl (7.47.0-1ubuntu2.1) over (7.47.0-1ubuntu2) ... 
Preparing to unpack .../libidn11_1.32-3ubuntu1.1_amd64.deb ... 
Unpacking libidn11:amd64 (1.32-3ubuntu1.1) over (1.32-3ubuntu1) ... 
Preparing to unpack .../libcurl3-gnutls_7.47.0-1ubuntu2.1_amd64.deb ... 
Unpacking libcurl3-gnutls:amd64 (7.47.0-1ubuntu2.1) over (7.47.0-1ubuntu2) ... 
Preparing to unpack .../libharfbuzz0b_1.0.1-1ubuntu0.1_amd64.deb ... 
Unpacking libharfbuzz0b:amd64 (1.0.1-1ubuntu0.1) over (1.0.1-1build2) ... 
Preparing to unpack .../libharfbuzz-icu0_1.0.1-1ubuntu0.1_amd64.deb ... 
Unpacking libharfbuzz-icu0:amd64 (1.0.1-1ubuntu0.1) over (1.0.1-1build2) ... 
Preparing to unpack .../libnspr4_2%3a4.12-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking libnspr4:amd64 (2:4.12-0ubuntu0.16.04.1) over (2:4.11-1ubuntu1) ... 
Preparing to unpack .../libnss3-1d_2%3a3.23-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking libnss3-1d:amd64 (2:3.23-0ubuntu0.16.04.1) over (2:3.21-1ubuntu4) ... 
Preparing to unpack .../libnss3-nssdb_2%3a3.23-0ubuntu0.16.04.1_all.deb ... 
Unpacking libnss3-nssdb (2:3.23-0ubuntu0.16.04.1) over (2:3.21-1ubuntu4) ... 
Preparing to unpack .../libnss3_2%3a3.23-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking libnss3:amd64 (2:3.23-0ubuntu0.16.04.1) over (2:3.21-1ubuntu4) ... 
Preparing to unpack .../libtevent0_0.9.28-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking libtevent0:amd64 (0.9.28-0ubuntu0.16.04.1) over (0.9.26-3) ... 
Preparing to unpack .../python-samba_2%3a4.3.11+dfsg-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking python-samba (2:4.3.11+dfsg-0ubuntu0.16.04.1) over (2:4.3.8+dfsg-0ubuntu1) ... 
Preparing to unpack .../samba-common-bin_2%3a4.3.11+dfsg-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking samba-common-bin (2:4.3.11+dfsg-0ubuntu0.16.04.1) over (2:4.3.8+dfsg-0ubuntu1) ... 
Preparing to unpack .../libsmbclient_2%3a4.3.11+dfsg-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking libsmbclient:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1) over (2:4.3.8+dfsg-0ubuntu1) ... 
Preparing to unpack .../samba-libs_2%3a4.3.11+dfsg-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking samba-libs:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1) over (2:4.3.8+dfsg-0ubuntu1) ... 
Preparing to unpack .../libwbclient0_2%3a4.3.11+dfsg-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking libwbclient0:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1) over (2:4.3.8+dfsg-0ubuntu1) ... 
Preparing to unpack .../samba-common_2%3a4.3.11+dfsg-0ubuntu0.16.04.1_all.deb ... 
Unpacking samba-common (2:4.3.11+dfsg-0ubuntu0.16.04.1) over (2:4.3.8+dfsg-0ubuntu1) ... 
Preparing to unpack .../libgcrypt20_1.6.5-2ubuntu0.2_amd64.deb ... 
Unpacking libgcrypt20:amd64 (1.6.5-2ubuntu0.2) over (1.6.5-2) ... 
Processing triggers for libc-bin (2.23-0ubuntu3) ... 
Processing triggers for mime-support (3.59ubuntu1) ... 
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ... 
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ... 
Processing triggers for man-db (2.7.5-1) ... 
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libreoffice-core_1%3a5.1.4-0ubuntu1_amd64.deb 
Log ended: 2016-10-09  03:42:11

```


```

2016-10-09 03:24:20,800 INFO Initial blacklisted packages: 
2016-10-09 03:24:20,801 INFO Initial whitelisted packages: 
2016-10-09 03:24:20,801 INFO Starting unattended upgrades script
2016-10-09 03:24:20,801 INFO Allowed origins are: ['o=Ubuntu,a=xenial-security']
2016-10-09 03:41:26,268 INFO Packages that will be upgraded: bind9-host binutils cpp-5 curl distro-info-data dnsmasq-base dnsutils dosfstools ecryptfs-utils eog file-roller firefox firefox-locale-de firefox-locale-en firefox-locale-es firefox-locale-fr firefox-locale-it firefox-locale-pt firefox-locale-ru firefox-locale-zh-hans fontconfig fontconfig-config fonts-opensymbol g++-5 gcc-5 gcc-5-base gir1.2-gdkpixbuf-2.0 gir1.2-javascriptcoregtk-4.0 gir1.2-soup-2.4 gir1.2-webkit2-4.0 gnupg gpgv imagemagick imagemagick-6.q16 imagemagick-common libarchive13 libasan2 libatomic1 libbind9-140 libcc1-0 libcilkrts5 libcurl3 libcurl3-gnutls libdns-export162 libdns162 libecryptfs1 libexpat1 libfontconfig1 libgcc-5-dev libgcrypt20 libgd3 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgomp1 libharfbuzz-icu0 libharfbuzz0b libidn11 libimobiledevice6 libisc-export160 libisc160 libisccc140 libisccfg140 libitm1 libjavascriptcoregtk-4.0-18 libksba8 liblsan0 liblwres141 libmagickcore-6.q16-2 libmagickcore-6.q16-2-extra libmagickwand-6.q16-2 libmpx0 libndp0 libnspr4 libnss3 libnss3-1d libnss3-nssdb liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0 libpam-systemd libquadmath0 libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-de libreoffice-help-en-gb libreoffice-help-en-us libreoffice-help-es libreoffice-help-fr libreoffice-help-it libreoffice-help-pt libreoffice-help-pt-br libreoffice-help-ru libreoffice-help-zh-cn libreoffice-help-zh-tw libreoffice-impress libreoffice-l10n-de libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-l10n-es libreoffice-l10n-fr libreoffice-l10n-it libreoffice-l10n-pt libreoffice-l10n-pt-br libreoffice-l10n-ru libreoffice-l10n-zh-cn libreoffice-l10n-zh-tw libreoffice-math libreoffice-ogltrans libreoffice-pdfimport libreoffice-style-breeze libreoffice-style-galaxy libreoffice-writer libsmbclient libsoup-gnome2.4-1 libsoup2.4-1 libssl1.0.0 libstdc++-5-dev libstdc++6 libsystemd0 libtasn1-6 libtevent0 libtsan0 libubsan0 libudev1 libusbmuxd4 libwbclient0 libwebkit2gtk-4.0-37 libwebkit2gtk-4.0-37-gtk2 libxml2 linux-generic linux-headers-generic linux-image-generic linux-libc-dev linux-signed-generic linux-signed-image-generic openssh-client openssl oxideqt-codecs python-samba python3-uno samba-common samba-common-bin samba-libs systemd systemd-sysv thunderbird thunderbird-gnome-support thunderbird-locale-de thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-es thunderbird-locale-es-ar thunderbird-locale-es-es thunderbird-locale-fr thunderbird-locale-it thunderbird-locale-pt thunderbird-locale-pt-br thunderbird-locale-pt-pt thunderbird-locale-ru thunderbird-locale-zh-cn thunderbird-locale-zh-hans thunderbird-locale-zh-hant thunderbird-locale-zh-tw tzdata ubuntu-core-launcher udev uno-libs3 ure wget
2016-10-09 03:41:26,269 INFO Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log'
2016-10-09 03:42:11,052 ERROR Installing the upgrades failed!
2016-10-09 03:42:11,062 ERROR error message: 'installArchives() failed'
2016-10-09 03:42:11,065 ERROR dpkg returned a error! See '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log' for details
2016-10-09 03:42:11,901 ERROR Cache has broken packages, exiting

```


so looks like overnight upgrade to me.. or am I missing something again :)

---

### Post by sudodus on 2016-10-09
Yes, indeed!

So maybe the difference is that in this live system the package is replaced with the new package, and the size did not change much. In persistent live systems, all changes must be written to the casper-rw file or partition, so it will increase in size rapidly.

Were you running this test with the upgraded casper package? In that case, I suggest that you add a comment to the bug report with your result,

[Bug #1619188: Unattended upgrades can break persistent live media](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1619188)

---

### Post by ventrical on 2016-10-09
> **sudodus said:**
> Yes, indeed!

So maybe the difference is that in this live system the package is replaced with the new package, and the size did not change much. In persistent live systems, all changes must be written to the casper-rw file or partition, so it will increase in size rapidly.

Were you running this test with the upgraded casper package? In that case, I suggest that you add a comment to the bug report with your result,

[Bug #1619188: Unattended upgrades can break persistent live media]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1619188")

No .. I was not running with casper upgrade. I was running "live" only , not persistent.

---

### Post by ventrical on 2016-10-09
I left a message and asked the question if the new casper fix will be upgraded in the daily/current  xenial amd64.iso image.

Regards..

---

### Post by sudodus on 2016-10-10
The answer is yes :-)

It is there in the current daily iso files (dated 20161009 in the iso qa tracker)

---

### Post by sudodus on 2016-10-10
Alongside your test, *ventrical*, I started a test using the Ubuntu amd64 current daily iso file (dated 20161009). I created a ***persistent live*** drive with mkusb (and selected not to use the mkusb tweak to stop unattended upgrades). I'm looking forward to the result tomorrow, if there are any unattended upgrades.

---

### Post by sudodus on 2016-10-11
You are right, *ventrical*, this fix in xenial does not work. This morning the used space in casper-rw had increased from 66 MiB to 449 MiB (unattended upgrade). See the attached files.

---

### Post by ventrical on 2016-10-11
Downloading xenial daily -Oct 11.  Will test it from there.

---

### Post by ventrical on 2016-10-11
casper 1.376.1 is in the daily/current xenial iso.

The notification says the same though. Ill let it run  and see  what happens..

---

### Post by sudodus on 2016-10-12
My repeated tests of Yakkety indicate that the bug is squashed. So it seems the bug fix works for Yakkety but not for Xenial.

See posts #47-48 in the bug report [https://bugs.launchpad.net/ubuntu/+bug/1619188](https://bugs.launchpad.net/ubuntu/+bug/1619188)

---

### Post by ventrical on 2016-10-12
ahhh but check unattended-upgrades.log and see fix...

```

2016-10-12 03:31:14,661 INFO Initial blacklisted packages: 
2016-10-12 03:31:14,661 INFO Initial whitelisted packages: 
2016-10-12 03:31:14,661 INFO Starting unattended upgrades script
2016-10-12 03:31:14,662 INFO Allowed origins are: ['o=Ubuntu,a=xenial-security']
2016-10-12 03:31:18,460 INFO No packages found that can be upgraded unattended and no pending auto-removals

```

this is what happened on the live daily/current xenial amd64.ubuntu-desktop iso. So there is a big diff.

---

### Post by sudodus on 2016-10-12
So maybe I created a 'false negative'. I think I have to learn how to read the linux logfiles :-/

How do you interpret this file (created last night in my test with the Yakkety release candidate (the iso available yesterday, not the current one of course)?

/media/sudodus/casper-rw/upper/var/log/unattended-upgrades/unattended-upgrades.log:

```
2016-10-11 21:07:30,193 INFO Initial blacklisted packages: 
2016-10-11 21:07:30,194 INFO Initial whitelisted packages: 
2016-10-11 21:07:30,195 INFO Starting unattended upgrades script
2016-10-11 21:07:30,196 INFO Allowed origins are: []
2016-10-11 21:07:31,236 INFO No packages found that can be upgraded unattended and no pending auto-removals
```

And this one from the test using the iso file dated 20161003,

/media/sudodus/casper-rw1/upper/var/log/unattended-upgradesunattended-upgrades.log:

```
2016-10-12 01:39:27,410 INFO Initial blacklisted packages: 
2016-10-12 01:39:27,410 INFO Initial whitelisted packages: 
2016-10-12 01:39:27,411 INFO Starting unattended upgrades script
2016-10-12 01:39:27,411 INFO Allowed origins are: []
2016-10-12 01:39:27,979 INFO No packages found that can be upgraded unattended and no pending auto-removals
```

There is a difference in 'allowed origins' compared to your result from Xenial. Does it mean that Yakkety live should be safe from unattended upgrades, while Xenial live is still affected?

---

### Post by ventrical on 2016-10-12
brain-murray says  basically no to that question .. so another fix is in.

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1619188/comments/55](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1619188/comments/55)

---

### Post by ventrical on 2016-10-12
> **sudodus said:**
> So maybe I created a 'false negative'. I think I have to learn how to read the linux logfiles :-/

How do you interpret this file (created last night in my test with the Yakkety release candidate (the iso available yesterday, not the current one of course)?

/media/sudodus/casper-rw/upper/var/log/unattended-upgrades/unattended-upgrades.log:

```
2016-10-11 21:07:30,193 INFO Initial blacklisted packages: 
2016-10-11 21:07:30,194 INFO Initial whitelisted packages: 
2016-10-11 21:07:30,195 INFO Starting unattended upgrades script
2016-10-11 21:07:30,196 INFO Allowed origins are: []
2016-10-11 21:07:31,236 INFO No packages found that can be upgraded unattended and no pending auto-removals
```

And this one from the test using the iso file dated 20161003,

/media/sudodus/casper-rw1/upper/var/log/unattended-upgradesunattended-upgrades.log:

```
2016-10-12 01:39:27,410 INFO Initial blacklisted packages: 
2016-10-12 01:39:27,410 INFO Initial whitelisted packages: 
2016-10-12 01:39:27,411 INFO Starting unattended upgrades script
2016-10-12 01:39:27,411 INFO Allowed origins are: []
2016-10-12 01:39:27,979 INFO No packages found that can be upgraded unattended and no pending auto-removals
```

There is a difference in 'allowed origins' compared to your result from Xenial. Does it mean that Yakkety live should be safe from unattended upgrades, while Xenial live is still affected?

Good question. ;)

I think I am going to just monitor the situation atm.

regards..

---

### Post by sudodus on 2016-10-18
The test system (persistent live Ubuntu 16.04.1 LTS) has been running for 3 days and nights now, and there has been no unattended upgrade. So either no security upgrade has been uploaded, or the bug-fix works, even with the current settings of the file

**/etc/apt/apt.conf.d/50unattended-upgrades**

```
Unattended-Upgrade::Allowed-Origins {
 "${distro_id}:${distro_codename}-security";
};
```

-o-

How can we find out, when the latest security upgrade was uploaded for Ubuntu 16.04.1 LTS?

---

### Post by ventrical on 2016-10-18
It has been my experience  that there have always been security updates after a nn.nn.1 hard install so I think your diligence at testing is paying off. I would assume then that the 16.04.1 "live" session will not auto-upgrade security updates but that does not mean to say that the same applies for live-persistent but then, of course, the instruction are clear in that one would have to turn off that option in software and updates.

Regards..

---

### Post by sudodus on 2016-11-26
I am running a long time test now (since approximately 24 hours) with a live-only system. There are fresh security updates (for example of python), that appeared after October 26 when the daily iso file was saved. It is promising; I think the bug-fix works, but I will let it run for a second night before I finish the test.

See this link, [Bug #1619188: Unattended upgrades can break persistent live media](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1619188)

***Edit:*** I am finishing the long time test now after the second night. There were no unattended upgrades in this Ubuntu live system. I can confirm that the bug-fix works in a live-only system :-)

---

### Post by sudodus on 2016-11-28
I started a new test, this time with a persistent live system made with mkusb. We will see what happens ...

***Edit:*** After the first night and a good part of the next day (today), there is still no unattended upgrade, but I will let it run for a second night before I finish the test.

---

### Post by sudodus on 2016-11-30
I am finishing the test with a persistent live system made with mkusb after two nights.

I did not let mkusb change 'what to do, when security updates are detected', so the corresponding system from the 16.04.1 LTS iso file would perform unattended upgrades. The used drive space increased from 66 MiB to 88 MiB. I did not check which files were written, but I assume some log files. This is far from the big increase of used space, when the system performs unattended upgrades.

So I can confirm that the bugfix in casper works also in a persistent live system. We can look forward to the next point release, Ubuntu 16.04.2 LTS, where it will be implemented. Today it is possible to grab the Ubuntu Xenial daily iso file and make a live drive without unattended upgrades.

***Edit:*** The file **unattended-upgrades.log** looks like it should: 'No upgrades, no removals'.

---

