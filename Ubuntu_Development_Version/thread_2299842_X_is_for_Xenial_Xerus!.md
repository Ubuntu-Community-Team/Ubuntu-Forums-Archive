---
title: "X is for Xenial Xerus!"
date: 2015-10-21
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2015-10-21
So now we know!

[http://markshuttleworth.com/archives/1479](http://markshuttleworth.com/archives/1479)

An African ground squirrel apparently - [https://en.wikipedia.org/wiki/African_ground_squirrel](https://en.wikipedia.org/wiki/African_ground_squirrel)  ;)

---

### Post by ronacc on 2015-10-21
darn I was hoping for xenophobic  Xenurine .

---

### Post by v3.xx on 2015-10-21
So when can we change our sources list over to xenial?

---

### Post by PaulW2U on 2015-10-21
> **v3.xx said:**
> So when can we change our sources list over to xenial?
I'm betting on Friday.

---

### Post by sammiev on 2015-10-21
> **PaulW2U said:**
> I'm betting on Friday.

I can't wait... ;)

---

### Post by ventrical on 2015-10-21
Changed over already here.

Nuts!  I was hoping for the humming bird.

---

### Post by grahammechanical on 2015-10-21
And he did say "Ubuntu personal will be the all snappy phone/tablet/PC." Two parallel development branches this cycle. One traditional deb based Ubuntu leading to 16.04 and the snap based personal which does not need a release date.

---

### Post by v3.xx on 2015-10-21
> **ventrical said:**
> Changed over already here.

I'm on the main server and all I get is 404s.

---

### Post by ventrical on 2015-10-21
> **v3.xx said:**
> I'm on the main server and all I get is 404s.

I mean to say I have changed over my sources.list to xenial

---

### Post by bcschmerker on 2015-10-22
**Thanks for the confirmation** - I had a feeling that an animal name that oozes *ubuntu* would be most appropriate.  Any estimate of when nightlies will commence for 15.12a1 through 16.04rc?

---

### Post by grahammechanical on 2015-10-22
I takes a week or two for QA to get setup for building and testing ISO images. Right now the Xenial code base is no different to the Wily code base. I will also be changing the sources list URLs to point to xenial repositories even if at present they do not exist. I just need to get the command exactly right and it has been six months since I last used this command.

ventrical is keeping up to date

[https://wiki.ubuntu.com/U+1/tester-wiki](https://wiki.ubuntu.com/U+1/tester-wiki)

But he does need to change this

> sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list

to this

```
sudo sed -i 's/wily/xenial/g' /etc/apt/sources.list
```

He does have a nice photograph of a Xerus. As noted, the xenial repositories do not yet exist. Lots of 404 not found. Here is another piece of useless information. For the last 26 weeks I have been running a second wily install off of the devel repositories. That install got kernel 4.0 but never got kernel 4.1 and still does not have kernel 4.2. It is a messed up install. Excessive experimentation. I will do a fresh install.

Regards.

---

### Post by Cavsfan on 2015-10-22
So, I was right in my guess. :p That's a first. 

[http://ubuntuforums.org/showthread.php?t=2299161&p=13375116#post13375116](http://ubuntuforums.org/showthread.php?t=2299161&p=13375116#post13375116)

Kool! :popcorn::lolflag:

---

### Post by cariboo on 2015-10-22
> **grahammechanical said:**
> I takes a week or two for QA to get setup for building and testing ISO images. Right now the Xenial code base is no different to the Wily code base. I will also be changing the sources list URLs to point to xenial repositories even if at present they do not exist. I just need to get the command exactly right and it has been six months since I last used this command.

ventrical is keeping up to date

[https://wiki.ubuntu.com/U+1/tester-wiki](https://wiki.ubuntu.com/U+1/tester-wiki)

But he does need to change this



to this

```
sudo sed -i 's/wily/xenial/g' /etc/apt/sources.list
```

He does have a nice photograph of a Xerus. As noted, the xenial repositories do not yet exist. Lots of 404 not found. Here is another piece of useless information. For the last 26 weeks I have been running a second wily install off of the devel repositories. That install got kernel 4.0 but never got kernel 4.1 and still does not have kernel 4.2. It is a messed up install. Excessive experimentation. I will do a fresh install.

Regards.

I will be updating the Common questions thread, I may be a little bit late, as we are extremely busy at work, with our yearly inventory coming up next Wednesday. I've been working 6 days a week, so my time is very limited. I should be able to get to it on the weekend.

---

### Post by harry332 on 2015-10-22
Well now the Xenial repos are there. Actually they are the same as wily.
It is now possible to change "wily" to "xenial" in the /etc/apt/sources.list file and all is fine.

---

### Post by harry332 on 2015-10-22
The release schedule of Xenial is also in place:
[https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule)

---

### Post by PaulW2U on 2015-10-22
> **PaulW2U said:**
> I'm betting on Friday.
So I was wrong... :(
> **harry332 said:**
> Well now the Xenial repos are there. Actually they are the same as wily.
It is now possible to change "wily" to "xenial" in the /etc/apt/sources.list file and all is fine.
Eavesdropping on various IRC channels shortly after the release of Wily I got the impression that it could be today...

---

### Post by v3.xx on 2015-10-22
I just did a successful xenial update, no 404s.

But the upgrade still fails.  I guess there is nothing there yet.

---

### Post by ventrical on 2015-10-22
> **grahammechanical said:**
> I takes a week or two for QA to get setup for building and testing ISO images. Right now the Xenial code base is no different to the Wily code base. I will also be changing the sources list URLs to point to xenial repositories even if at present they do not exist. I just need to get the command exactly right and it has been six months since I last used this command.

ventrical is keeping up to date

[https://wiki.ubuntu.com/U+1/tester-wiki](https://wiki.ubuntu.com/U+1/tester-wiki)

But he does need to change this



to this

```
sudo sed -i 's/wily/xenial/g' /etc/apt/sources.list
```

He does have a nice photograph of a Xerus. As noted, the xenial repositories do not yet exist. Lots of 404 not found. Here is another piece of useless information. For the last 26 weeks I have been running a second wily install off of the devel repositories. That install got kernel 4.0 but never got kernel 4.1 and still does not have kernel 4.2. It is a messed up install. Excessive experimentation. I will do a fresh install.

Regards.

@graham
@cariboo
@harry
@all..

Thanks you guys. I have some extra time now to get some work done about  here and there with the wikis and such. 

Regards..

---

### Post by ventrical on 2015-10-22
> **v3.xx said:**
> I just did a successful xenial update, no 404s.

But the upgrade still fails.  I guess there is nothing there yet.

So far .. yes .. but keep trying . You may be surprised :)

---

### Post by ventrical on 2015-10-22
> **Cavsfan said:**
> So, I was right in my guess. :p That's a first. 

[http://ubuntuforums.org/showthread.php?t=2299161&p=13375116#post13375116](http://ubuntuforums.org/showthread.php?t=2299161&p=13375116#post13375116)

Kool! :popcorn::lolflag:

Bravo Cavsfan. You are now 'ubuntu-guru' :)

---

### Post by anca-emanuel on 2015-10-22
> **ventrical said:**
> So far .. yes .. but keep trying . You may be surprised :)

> [COLOR=#000000][16:51] <barry> doko: what's the eta for xenial opening?
[/COLOR][COLOR=#000000][16:52] <doko> should be ready tonight for toolchain uploads[/COLOR]
(from [http://irclogs.ubuntu.com/2015/10/22/%23ubuntu-devel.txt](http://irclogs.ubuntu.com/2015/10/22/%23ubuntu-devel.txt))


Xenial-changes Archives: [https://lists.ubuntu.com/archives/xenial-changes/](https://lists.ubuntu.com/archives/xenial-changes/)

---

### Post by harry332 on 2015-10-22
Hey,

base-files (9.4-0ubuntu1) upgraded.
This is in xenial-proposed, not in wily.

[https://launchpad.net/ubuntu/+source/base-files/9.4ubuntu1/+build/8171154](https://launchpad.net/ubuntu/+source/base-files/9.4ubuntu1/+build/8171154)

---

### Post by ventrical on 2015-10-22
Careful about enabling proposed.
..soon..
regards..

---

### Post by tista on 2015-10-22
Greetings,

Now I'm moving all packages to xenial...
[https://launchpad.net/~tista/+archive/ubuntu/wayland]("https://launchpad.net/~tista/+archive/ubuntu/wayland")

Thanks for head up.:p

Best Regards.

---

### Post by grahammechanical on 2015-10-22
I got an update! Oh, it was to the Chrome Browser. False alarm. :)  I have noticed that there is never much activity in the way of updates over the weekend. I am not expecting much until the weekend has ended.

Regards.

---

### Post by ventrical on 2015-10-22
> **grahammechanical said:**
> I got an update! Oh, it was to the Chrome Browser. False alarm. :)  I have noticed that there is never much activity in the way of updates over the weekend. I am not expecting much until the weekend has ended.

Regards.

+1 .. but I am going to keep trying here and there when I get the chance.

:)

---

### Post by bcschmerker on 2015-10-22
> **harry332 said:**
> The release schedule of Xenial is also in place:
[https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule)
Thanks for the update.  Looks as though the Xenial nightlies will be available while I purchase and install my new HDD's.  15.12a1, 16.01a2, 16.02b1, and 16.03b2 available at the ends of their respective months?  I can dig it.

---

### Post by harry332 on 2015-10-23
Ventrical,

I am careful, as always, but I also know how to use terminal in order to sudo apt-get install x.deb=version and I also know how to chroot.
I haven't reinstalled the distro for many many years.

---

### Post by ventrical on 2015-10-23
> **harry332 said:**
> Ventrical,

I am careful, as always, but I also know how to use terminal in order to sudo apt-get install x.deb=version and I also know how to chroot.
I haven't reinstalled the distro for many many years.

Not a problem .. My message was meant for newer users. I am , in fact, in the process of laying open a  system to proposed.

regards..

---

### Post by zika on 2015-10-23
```
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
```(this time from the very start, like in old times... ;))

---

### Post by slickymaster on 2015-10-23
And we're starting to roll```
~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  hplip printer-driver-postscript-hp python3-uno
The following NEW packages will be installed:
  libpython3.5-minimal libpython3.5-stdlib python3.5 python3.5-minimal
The following packages have been kept back:
  aptdaemon python-aptdaemon.gtk3widgets python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat
The following packages will be upgraded:
  base-files binutils cpp-5 debhelper g++-5 gcc-5 gcc-5-base indicator-sound libasan2 libatomic1 libcc1-0 libcilkrts5 libgcc-5-dev libgcc1 libgfortran3
  libgomp1 libitm1 libmpx0 libpython3-stdlib libquadmath0 libstdc++-5-dev libstdc++6 libubsan0 python3 python3-minimal
25 upgraded, 4 newly installed, 3 to remove and 4 not upgraded.
Need to get 98,9 MB of archives.
After this operation, 275 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main base-files i386 9.4ubuntu1 [62,4 kB]
Get:2 http://pt.archive.ubuntu.com/ubuntu/ xenial/main libpython3.5-minimal i386 3.5.0-3 [519 kB]
Get:3 http://pt.archive.ubuntu.com/ubuntu/ xenial/main python3.5-minimal i386 3.5.0-3 [1327 kB]
Get:4 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main python3-minimal i386 3.5.0-2 [23,7 kB]                                                      
Get:5 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main python3 i386 3.5.0-2 [8648 B]                                                               
Get:6 http://pt.archive.ubuntu.com/ubuntu/ xenial/main libpython3.5-stdlib i386 3.5.0-3 [2081 kB]                                                           
Get:7 http://pt.archive.ubuntu.com/ubuntu/ xenial/main python3.5 i386 3.5.0-3 [150 kB]                                                                      
Get:8 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libpython3-stdlib i386 3.5.0-2 [7080 B]                                                     
Get:9 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libubsan0 i386 5.2.1-22ubuntu4 [111 kB]                                                     
Get:10 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main gcc-5-base i386 5.2.1-22ubuntu4 [16,5 kB]                                                  
Get:11 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libstdc++6 i386 5.2.1-22ubuntu4 [418 kB]                                                   
Get:12 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libgomp1 i386 5.2.1-22ubuntu4 [58,6 kB]                                                    
Get:13 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libitm1 i386 5.2.1-22ubuntu4 [30,7 kB]                                                     
Get:14 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libatomic1 i386 5.2.1-22ubuntu4 [9676 B]                                                   
Get:15 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libasan2 i386 5.2.1-22ubuntu4 [271 kB]                                                     
Get:16 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libcilkrts5 i386 5.2.1-22ubuntu4 [44,8 kB]                                                 
Get:17 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libmpx0 i386 5.2.1-22ubuntu4 [11,2 kB]                                                     
Get:18 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libquadmath0 i386 5.2.1-22ubuntu4 [203 kB]                                                 
Get:19 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main cpp-5 i386 5.2.1-22ubuntu4 [25,2 MB]                                                       
Get:20 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libcc1-0 i386 5.2.1-22ubuntu4 [32,4 kB]                                                    
Get:21 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main binutils i386 2.25.51.20151022-0ubuntu1 [2478 kB]                                          
Get:22 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main g++-5 i386 5.2.1-22ubuntu4 [35,6 MB]                                                       
Get:23 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main gcc-5 i386 5.2.1-22ubuntu4 [25,5 MB]                                                       
Get:24 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libgcc-5-dev i386 5.2.1-22ubuntu4 [2245 kB]                                                
Get:25 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libstdc++-5-dev i386 5.2.1-22ubuntu4 [1452 kB]                                             
Get:26 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libgfortran3 i386 5.2.1-22ubuntu4 [250 kB]                                                 
Get:27 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libgcc1 i386 1:5.2.1-22ubuntu4 [46,5 kB]                                                   
Get:28 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main debhelper all 9.20151005ubuntu1 [729 kB]                                                   
Get:29 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main indicator-sound i386 12.10.2+15.10.20151019-0ubuntu1 [86,3 kB]                             
Fetched 98,9 MB in 9min 1s (183 kB/s)                                                                                                                       
(Reading database ... 169752 files and directories currently installed.)
Preparing to unpack .../base-files_9.4ubuntu1_i386.deb ...
Unpacking base-files (9.4ubuntu1) over (7.2ubuntu11) ...
Processing triggers for install-info (6.0.0.dfsg.1-3) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.0-0ubuntu9) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-16-generic
Setting up base-files (9.4ubuntu1) ...
Installing new version of config file /etc/debian_version ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Updating /etc/profile to current default.
Updating /root/.profile to current default.
Processing triggers for plymouth-theme-ubuntu-text (0.9.0-0ubuntu9) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-16-generic
(Reading database ... 169753 files and directories currently installed.)
Removing printer-driver-postscript-hp (3.15.7-0ubuntu4) ...
Removing hplip (3.15.7-0ubuntu4) ...
Removing python3-uno (1:5.0.2-0ubuntu1) ...
Processing triggers for cups (2.1.0-4ubuntu3) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for dbus (1.10.0-1ubuntu1) ...
Selecting previously unselected package libpython3.5-minimal:i386.
(Reading database ... 169646 files and directories currently installed.)
Preparing to unpack .../libpython3.5-minimal_3.5.0-3_i386.deb ...
Unpacking libpython3.5-minimal:i386 (3.5.0-3) ...
Selecting previously unselected package python3.5-minimal.
Preparing to unpack .../python3.5-minimal_3.5.0-3_i386.deb ...
Unpacking python3.5-minimal (3.5.0-3) ...
Preparing to unpack .../python3-minimal_3.5.0-2_i386.deb ...
Unpacking python3-minimal (3.5.0-2) over (3.4.3-4ubuntu1) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up libpython3.5-minimal:i386 (3.5.0-3) ...
Setting up python3.5-minimal (3.5.0-3) ...
Setting up python3-minimal (3.5.0-2) ...
(Reading database ... 169882 files and directories currently installed.)
Preparing to unpack .../python3_3.5.0-2_i386.deb ...
running python pre-rtupdate hooks for python3.5...
Unpacking python3 (3.5.0-2) over (3.4.3-4ubuntu1) ...
Selecting previously unselected package libpython3.5-stdlib:i386.
Preparing to unpack .../libpython3.5-stdlib_3.5.0-3_i386.deb ...
Unpacking libpython3.5-stdlib:i386 (3.5.0-3) ...
Selecting previously unselected package python3.5.
Preparing to unpack .../python3.5_3.5.0-3_i386.deb ...
Unpacking python3.5 (3.5.0-3) ...
Preparing to unpack .../libpython3-stdlib_3.5.0-2_i386.deb ...
Unpacking libpython3-stdlib:i386 (3.5.0-2) over (3.4.3-4ubuntu1) ...
Preparing to unpack .../libubsan0_5.2.1-22ubuntu4_i386.deb ...
Unpacking libubsan0:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../gcc-5-base_5.2.1-22ubuntu4_i386.deb ...
Unpacking gcc-5-base:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Setting up gcc-5-base:i386 (5.2.1-22ubuntu4) ...
(Reading database ... 170479 files and directories currently installed.)
Preparing to unpack .../libstdc++6_5.2.1-22ubuntu4_i386.deb ...
Unpacking libstdc++6:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Setting up libstdc++6:i386 (5.2.1-22ubuntu4) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
(Reading database ... 170479 files and directories currently installed.)
Preparing to unpack .../libgomp1_5.2.1-22ubuntu4_i386.deb ...
Unpacking libgomp1:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libitm1_5.2.1-22ubuntu4_i386.deb ...
Unpacking libitm1:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libatomic1_5.2.1-22ubuntu4_i386.deb ...
Unpacking libatomic1:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libasan2_5.2.1-22ubuntu4_i386.deb ...
Unpacking libasan2:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libcilkrts5_5.2.1-22ubuntu4_i386.deb ...
Unpacking libcilkrts5:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libmpx0_5.2.1-22ubuntu4_i386.deb ...
Unpacking libmpx0:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libquadmath0_5.2.1-22ubuntu4_i386.deb ...
Unpacking libquadmath0:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../cpp-5_5.2.1-22ubuntu4_i386.deb ...
Unpacking cpp-5 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libcc1-0_5.2.1-22ubuntu4_i386.deb ...
Unpacking libcc1-0:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../binutils_2.25.51.20151022-0ubuntu1_i386.deb ...
Unpacking binutils (2.25.51.20151022-0ubuntu1) over (2.25.1-6ubuntu1) ...
Preparing to unpack .../g++-5_5.2.1-22ubuntu4_i386.deb ...
Unpacking g++-5 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../gcc-5_5.2.1-22ubuntu4_i386.deb ...
Unpacking gcc-5 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libgcc-5-dev_5.2.1-22ubuntu4_i386.deb ...
Unpacking libgcc-5-dev:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libstdc++-5-dev_5.2.1-22ubuntu4_i386.deb ...
Unpacking libstdc++-5-dev:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libgfortran3_5.2.1-22ubuntu4_i386.deb ...
Unpacking libgfortran3:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libgcc1_1%3a5.2.1-22ubuntu4_i386.deb ...
Unpacking libgcc1:i386 (1:5.2.1-22ubuntu4) over (1:5.2.1-22ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up libgcc1:i386 (1:5.2.1-22ubuntu4) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
(Reading database ... 170499 files and directories currently installed.)
Preparing to unpack .../debhelper_9.20151005ubuntu1_all.deb ...
Unpacking debhelper (9.20151005ubuntu1) over (9.20150811ubuntu2) ...
Preparing to unpack .../indicator-sound_12.10.2+15.10.20151019-0ubuntu1_i386.deb ...
Unpacking indicator-sound (12.10.2+15.10.20151019-0ubuntu1) over (12.10.2+15.10.20150915-0ubuntu1) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for libglib2.0-0:i386 (2.46.1-1) ...
Setting up libpython3.5-stdlib:i386 (3.5.0-3) ...
Setting up python3.5 (3.5.0-3) ...
Setting up libpython3-stdlib:i386 (3.5.0-2) ...
Setting up python3 (3.5.0-2) ...
running python rtupdate hooks for python3.5...
running python post-rtupdate hooks for python3.5...
Setting up libubsan0:i386 (5.2.1-22ubuntu4) ...
Setting up libgomp1:i386 (5.2.1-22ubuntu4) ...
Setting up libitm1:i386 (5.2.1-22ubuntu4) ...
Setting up libatomic1:i386 (5.2.1-22ubuntu4) ...
Setting up libasan2:i386 (5.2.1-22ubuntu4) ...
Setting up libcilkrts5:i386 (5.2.1-22ubuntu4) ...
Setting up libmpx0:i386 (5.2.1-22ubuntu4) ...
Setting up libquadmath0:i386 (5.2.1-22ubuntu4) ...
Setting up cpp-5 (5.2.1-22ubuntu4) ...
Setting up libcc1-0:i386 (5.2.1-22ubuntu4) ...
Setting up binutils (2.25.51.20151022-0ubuntu1) ...
Setting up libgcc-5-dev:i386 (5.2.1-22ubuntu4) ...
Setting up gcc-5 (5.2.1-22ubuntu4) ...
Setting up libstdc++-5-dev:i386 (5.2.1-22ubuntu4) ...
Setting up g++-5 (5.2.1-22ubuntu4) ...
Setting up libgfortran3:i386 (5.2.1-22ubuntu4) ...
Setting up debhelper (9.20151005ubuntu1) ...
Setting up indicator-sound (12.10.2+15.10.20151019-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
```

---

### Post by zika on 2015-10-23
> **slickymaster said:**
> And we're starting to roll```
The following packages will be REMOVED:hplip printer-driver-postscript-hp **python3-uno**
```Was it not python3-uno needed for LO?

---

### Post by ventrical on 2015-10-23
> **slickymaster said:**
> And we're starting to roll```
~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  hplip printer-driver-postscript-hp python3-uno
The following NEW packages will be installed:
  libpython3.5-minimal libpython3.5-stdlib python3.5 python3.5-minimal
The following packages have been kept back:
  aptdaemon python-aptdaemon.gtk3widgets python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat
The following packages will be upgraded:
  base-files binutils cpp-5 debhelper g++-5 gcc-5 gcc-5-base indicator-sound libasan2 libatomic1 libcc1-0 libcilkrts5 libgcc-5-dev libgcc1 libgfortran3
  libgomp1 libitm1 libmpx0 libpython3-stdlib libquadmath0 libstdc++-5-dev libstdc++6 libubsan0 python3 python3-minimal
25 upgraded, 4 newly installed, 3 to remove and 4 not upgraded.
Need to get 98,9 MB of archives.
After this operation, 275 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main base-files i386 9.4ubuntu1 [62,4 kB]
Get:2 http://pt.archive.ubuntu.com/ubuntu/ xenial/main libpython3.5-minimal i386 3.5.0-3 [519 kB]
Get:3 http://pt.archive.ubuntu.com/ubuntu/ xenial/main python3.5-minimal i386 3.5.0-3 [1327 kB]
Get:4 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main python3-minimal i386 3.5.0-2 [23,7 kB]                                                      
Get:5 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main python3 i386 3.5.0-2 [8648 B]                                                               
Get:6 http://pt.archive.ubuntu.com/ubuntu/ xenial/main libpython3.5-stdlib i386 3.5.0-3 [2081 kB]                                                           
Get:7 http://pt.archive.ubuntu.com/ubuntu/ xenial/main python3.5 i386 3.5.0-3 [150 kB]                                                                      
Get:8 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libpython3-stdlib i386 3.5.0-2 [7080 B]                                                     
Get:9 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libubsan0 i386 5.2.1-22ubuntu4 [111 kB]                                                     
Get:10 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main gcc-5-base i386 5.2.1-22ubuntu4 [16,5 kB]                                                  
Get:11 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libstdc++6 i386 5.2.1-22ubuntu4 [418 kB]                                                   
Get:12 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libgomp1 i386 5.2.1-22ubuntu4 [58,6 kB]                                                    
Get:13 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libitm1 i386 5.2.1-22ubuntu4 [30,7 kB]                                                     
Get:14 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libatomic1 i386 5.2.1-22ubuntu4 [9676 B]                                                   
Get:15 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libasan2 i386 5.2.1-22ubuntu4 [271 kB]                                                     
Get:16 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libcilkrts5 i386 5.2.1-22ubuntu4 [44,8 kB]                                                 
Get:17 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libmpx0 i386 5.2.1-22ubuntu4 [11,2 kB]                                                     
Get:18 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libquadmath0 i386 5.2.1-22ubuntu4 [203 kB]                                                 
Get:19 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main cpp-5 i386 5.2.1-22ubuntu4 [25,2 MB]                                                       
Get:20 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libcc1-0 i386 5.2.1-22ubuntu4 [32,4 kB]                                                    
Get:21 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main binutils i386 2.25.51.20151022-0ubuntu1 [2478 kB]                                          
Get:22 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main g++-5 i386 5.2.1-22ubuntu4 [35,6 MB]                                                       
Get:23 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main gcc-5 i386 5.2.1-22ubuntu4 [25,5 MB]                                                       
Get:24 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libgcc-5-dev i386 5.2.1-22ubuntu4 [2245 kB]                                                
Get:25 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libstdc++-5-dev i386 5.2.1-22ubuntu4 [1452 kB]                                             
Get:26 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libgfortran3 i386 5.2.1-22ubuntu4 [250 kB]                                                 
Get:27 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main libgcc1 i386 1:5.2.1-22ubuntu4 [46,5 kB]                                                   
Get:28 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main debhelper all 9.20151005ubuntu1 [729 kB]                                                   
Get:29 http://pt.archive.ubuntu.com/ubuntu/ xenial-proposed/main indicator-sound i386 12.10.2+15.10.20151019-0ubuntu1 [86,3 kB]                             
Fetched 98,9 MB in 9min 1s (183 kB/s)                                                                                                                       
(Reading database ... 169752 files and directories currently installed.)
Preparing to unpack .../base-files_9.4ubuntu1_i386.deb ...
Unpacking base-files (9.4ubuntu1) over (7.2ubuntu11) ...
Processing triggers for install-info (6.0.0.dfsg.1-3) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.0-0ubuntu9) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-16-generic
Setting up base-files (9.4ubuntu1) ...
Installing new version of config file /etc/debian_version ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Updating /etc/profile to current default.
Updating /root/.profile to current default.
Processing triggers for plymouth-theme-ubuntu-text (0.9.0-0ubuntu9) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-16-generic
(Reading database ... 169753 files and directories currently installed.)
Removing printer-driver-postscript-hp (3.15.7-0ubuntu4) ...
Removing hplip (3.15.7-0ubuntu4) ...
Removing python3-uno (1:5.0.2-0ubuntu1) ...
Processing triggers for cups (2.1.0-4ubuntu3) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for dbus (1.10.0-1ubuntu1) ...
Selecting previously unselected package libpython3.5-minimal:i386.
(Reading database ... 169646 files and directories currently installed.)
Preparing to unpack .../libpython3.5-minimal_3.5.0-3_i386.deb ...
Unpacking libpython3.5-minimal:i386 (3.5.0-3) ...
Selecting previously unselected package python3.5-minimal.
Preparing to unpack .../python3.5-minimal_3.5.0-3_i386.deb ...
Unpacking python3.5-minimal (3.5.0-3) ...
Preparing to unpack .../python3-minimal_3.5.0-2_i386.deb ...
Unpacking python3-minimal (3.5.0-2) over (3.4.3-4ubuntu1) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up libpython3.5-minimal:i386 (3.5.0-3) ...
Setting up python3.5-minimal (3.5.0-3) ...
Setting up python3-minimal (3.5.0-2) ...
(Reading database ... 169882 files and directories currently installed.)
Preparing to unpack .../python3_3.5.0-2_i386.deb ...
running python pre-rtupdate hooks for python3.5...
Unpacking python3 (3.5.0-2) over (3.4.3-4ubuntu1) ...
Selecting previously unselected package libpython3.5-stdlib:i386.
Preparing to unpack .../libpython3.5-stdlib_3.5.0-3_i386.deb ...
Unpacking libpython3.5-stdlib:i386 (3.5.0-3) ...
Selecting previously unselected package python3.5.
Preparing to unpack .../python3.5_3.5.0-3_i386.deb ...
Unpacking python3.5 (3.5.0-3) ...
Preparing to unpack .../libpython3-stdlib_3.5.0-2_i386.deb ...
Unpacking libpython3-stdlib:i386 (3.5.0-2) over (3.4.3-4ubuntu1) ...
Preparing to unpack .../libubsan0_5.2.1-22ubuntu4_i386.deb ...
Unpacking libubsan0:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../gcc-5-base_5.2.1-22ubuntu4_i386.deb ...
Unpacking gcc-5-base:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Setting up gcc-5-base:i386 (5.2.1-22ubuntu4) ...
(Reading database ... 170479 files and directories currently installed.)
Preparing to unpack .../libstdc++6_5.2.1-22ubuntu4_i386.deb ...
Unpacking libstdc++6:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Setting up libstdc++6:i386 (5.2.1-22ubuntu4) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
(Reading database ... 170479 files and directories currently installed.)
Preparing to unpack .../libgomp1_5.2.1-22ubuntu4_i386.deb ...
Unpacking libgomp1:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libitm1_5.2.1-22ubuntu4_i386.deb ...
Unpacking libitm1:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libatomic1_5.2.1-22ubuntu4_i386.deb ...
Unpacking libatomic1:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libasan2_5.2.1-22ubuntu4_i386.deb ...
Unpacking libasan2:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libcilkrts5_5.2.1-22ubuntu4_i386.deb ...
Unpacking libcilkrts5:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libmpx0_5.2.1-22ubuntu4_i386.deb ...
Unpacking libmpx0:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libquadmath0_5.2.1-22ubuntu4_i386.deb ...
Unpacking libquadmath0:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../cpp-5_5.2.1-22ubuntu4_i386.deb ...
Unpacking cpp-5 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libcc1-0_5.2.1-22ubuntu4_i386.deb ...
Unpacking libcc1-0:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../binutils_2.25.51.20151022-0ubuntu1_i386.deb ...
Unpacking binutils (2.25.51.20151022-0ubuntu1) over (2.25.1-6ubuntu1) ...
Preparing to unpack .../g++-5_5.2.1-22ubuntu4_i386.deb ...
Unpacking g++-5 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../gcc-5_5.2.1-22ubuntu4_i386.deb ...
Unpacking gcc-5 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libgcc-5-dev_5.2.1-22ubuntu4_i386.deb ...
Unpacking libgcc-5-dev:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libstdc++-5-dev_5.2.1-22ubuntu4_i386.deb ...
Unpacking libstdc++-5-dev:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libgfortran3_5.2.1-22ubuntu4_i386.deb ...
Unpacking libgfortran3:i386 (5.2.1-22ubuntu4) over (5.2.1-22ubuntu2) ...
Preparing to unpack .../libgcc1_1%3a5.2.1-22ubuntu4_i386.deb ...
Unpacking libgcc1:i386 (1:5.2.1-22ubuntu4) over (1:5.2.1-22ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up libgcc1:i386 (1:5.2.1-22ubuntu4) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
(Reading database ... 170499 files and directories currently installed.)
Preparing to unpack .../debhelper_9.20151005ubuntu1_all.deb ...
Unpacking debhelper (9.20151005ubuntu1) over (9.20150811ubuntu2) ...
Preparing to unpack .../indicator-sound_12.10.2+15.10.20151019-0ubuntu1_i386.deb ...
Unpacking indicator-sound (12.10.2+15.10.20151019-0ubuntu1) over (12.10.2+15.10.20150915-0ubuntu1) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for libglib2.0-0:i386 (2.46.1-1) ...
Setting up libpython3.5-stdlib:i386 (3.5.0-3) ...
Setting up python3.5 (3.5.0-3) ...
Setting up libpython3-stdlib:i386 (3.5.0-2) ...
Setting up python3 (3.5.0-2) ...
running python rtupdate hooks for python3.5...
running python post-rtupdate hooks for python3.5...
Setting up libubsan0:i386 (5.2.1-22ubuntu4) ...
Setting up libgomp1:i386 (5.2.1-22ubuntu4) ...
Setting up libitm1:i386 (5.2.1-22ubuntu4) ...
Setting up libatomic1:i386 (5.2.1-22ubuntu4) ...
Setting up libasan2:i386 (5.2.1-22ubuntu4) ...
Setting up libcilkrts5:i386 (5.2.1-22ubuntu4) ...
Setting up libmpx0:i386 (5.2.1-22ubuntu4) ...
Setting up libquadmath0:i386 (5.2.1-22ubuntu4) ...
Setting up cpp-5 (5.2.1-22ubuntu4) ...
Setting up libcc1-0:i386 (5.2.1-22ubuntu4) ...
Setting up binutils (2.25.51.20151022-0ubuntu1) ...
Setting up libgcc-5-dev:i386 (5.2.1-22ubuntu4) ...
Setting up gcc-5 (5.2.1-22ubuntu4) ...
Setting up libstdc++-5-dev:i386 (5.2.1-22ubuntu4) ...
Setting up g++-5 (5.2.1-22ubuntu4) ...
Setting up libgfortran3:i386 (5.2.1-22ubuntu4) ...
Setting up debhelper (9.20151005ubuntu1) ...
Setting up indicator-sound (12.10.2+15.10.20151019-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
```


+1

```

ventrical@ventrical-OptiPlex-755:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
ventrical@ventrical-OptiPlex-755:~$ 

```

---

### Post by slickymaster on 2015-10-23
> **zika said:**
> Was it not python3-uno needed for LO?
Was, and still is, as far as I'm aware```
~$ apt-cache rdepends libreoffice
libreoffice
Reverse Depends:
 |ooohg
  openclipart2-libreoffice
  openclipart-libreoffice
  myspell-hu
 |loook
  libreoffice-zemberek
 |libreoffice-zemberek
  libreoffice-subsequentcheckbase
  libreoffice-kde
  libreoffice-gtk3
  libjodconverter-java
  grcompiler
  python3-uno
  myspell-uk
  myspell-pl
  libreoffice-voikko
 |libreoffice-voikko
  libreoffice-gtk
  libreoffice-gnome
  hunspell-ru
  hunspell-br
  hunspell-be
```I also saw that when I was upgrading this box, but nonetheless I let it went through (it's a testing box anyway). Anyway, long story short, after upgrading everything **python3-uno** is still present in the system```
~$ apt-cache policy python3-uno
python3-uno:
  Installed: 1:5.0.2-0ubuntu1
  Candidate: 1:5.0.2-0ubuntu1
  Version table:
 *** 1:5.0.2-0ubuntu1 0
        500 http://pt.archive.ubuntu.com/ubuntu/ wily/main i386 Packages
        100 /var/lib/dpkg/status
```I'll have to do a throughout analysis of what, and why, happened.

---

### Post by v3.xx on 2015-10-23
> **slickymaster said:**
> And we're starting to roll

I'm not getting much.  I'm going to guess this is because I run Mate.

```
The following packages will be upgraded:
  base-files libminiupnpc10 oxideqt-codecs-extra python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
  xserver-xorg-video-vmware
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,162 kB of archives.
After this operation, 17.4 kB disk space will be freed.

```

---

### Post by ventrical on 2015-10-23
> **v3.xx said:**
> I'm not getting much.  I'm going to guess this is because I run Mate.

```
The following packages will be upgraded:
  base-files libminiupnpc10 oxideqt-codecs-extra python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
  xserver-xorg-video-vmware
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,162 kB of archives.
After this operation, 17.4 kB disk space will be freed.

```

Thats about it for now.

---

### Post by v3.xx on 2015-10-23
> **ventrical said:**
> Thats about it for now.

Guess I will try again Monday.  Have a good weekend people :)

---

### Post by MikeMecanic on 2015-10-23
I'm not getting anything.  Is there something I do wrong?  I enable proposed a second time a hour ago and Wily's cache is empty.  The Ubuntu server in my hometown returns no result. One of these 2 terminal commands in post 11 erase settings in Software updater (software update).


```
wily@hp:~$ sudo apt-get dist-upgrade 
[sudo] password for wily: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following package was automatically installed and is no longer required:
  libmirprotobuf2
Use 'apt-get autoremove' to remove it.
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wily@hp:~$
```

---

### Post by ventrical on 2015-10-23
> **MikeMecanic said:**
> I'm not getting anything.  Is there something I do wrong?  I enable proposed a second time a hour ago and Wily's cache is empty.  The Ubuntu server in my hometown returns no result. One of these 2 terminal commands in post 11 erase settings in Software updater (software update).


```
wily@hp:~$ sudo apt-get dist-upgrade 
[sudo] password for wily: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following package was automatically installed and is no longer required:
  libmirprotobuf2
Use 'apt-get autoremove' to remove it.
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wily@hp:~$
```

There is a major problem with a new sources.list format. I do not know what it is but I posted it in new thread here.  I am waiting to see if mac4man or zika are going to chime in on this.

Regards..

---

### Post by rrnbtter on 2015-10-23
Greetings,
OS = Xenial, Kernel = 4.3RC6, Proposed Enabled. I will let you know should I have to reinstall.  


```
Distributor ID:	Ubuntu
Description:	Ubuntu Xenial Xerus (development branch)
```

```
Calculating upgrade... Done
The following packages will be REMOVED:
  hplip printer-driver-postscript-hp python3-uno rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins
The following NEW packages will be installed:
  libgif7 libpython3.5
The following packages will be upgraded:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  base-files binutils cpp-5 debhelper dpkg dpkg-dev g++-5 gcc-5 gcc-5-base gcr
  gdb gdbserver gir1.2-totem-1.0 gnome-calculator indicator-datetime
  indicator-sound kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools
  libaccount-plugin-generic-oauth libaccount-plugin-google libasan2 libatomic1
  libbabeltrace-ctf1 libbabeltrace1 libcap-ng0 libcc1-0 libcilkrts5
  libcolumbus1-common libcolumbus1v5 libdpkg-perl libgcc-5-dev libgcc1
  libgck-1-0 libgcr-3-common libgcr-base-3-1 libgcr-ui-3-1 libgeis1 libgomp1
  libitm1 libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdesu5
  libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 libmpx0 libmtp-common libmtp-runtime libmtp9 libplasma3
  libpython3-stdlib libqt5multimedia5 libquadmath0 libsolid4 libstdc++-5-dev
  libstdc++6 libthreadweaver4 libtotem0 libtracker-sparql-1.0-0 libubsan0
  libwebp5 libwebpmux1 mplayer2 python3 python3-minimal
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-ubuntu-web-plugin
  totem totem-common totem-plugins ubuntu-ui-toolkit-theme unzip
  webapp-container webbrowser-app zenity zenity-common
98 upgraded, 2 newly installed, 8 to remove and 0 not upgraded.
Need to get 121 MB of archives.
After this operation, 254 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```
```
Release:	16.04
Codename:	xenial
rrnbtter@rrnbtter-Satellite-L305:~$
```

Linux rrnbtter-Satellite-L305 4.3.0-040300rc6-generic #201510182030 SMP Mon Oct 19 00:45:51 UTC 2015 i686 i686 i686 GNU/Linux

---

### Post by ronacc on 2015-10-23
I just used sudo gedit to search and replace wily with xenial in etc/apt/source.list    etc/apt/source.list.save   and   /usr/share/python-apt/templates/Ubuntu.info  . I didn't enable proposed so only ubuntu base and 3 other files updated so far .

---

### Post by ventrical on 2015-10-23
I got proposed enabled and just got some more-

```

Done
The following packages will be upgraded:
  dpkg dpkg-dev libdpkg-perl libexiv2-14 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 policykit-1 zenity zenity-common

```

so the joints a jumpin' :)

---

### Post by ventrical on 2015-10-23
> **ronacc said:**
> I just used sudo gedit to search and replace wily with xenial in etc/apt/source.list    etc/apt/source.list.save   and   /usr/share/python-apt/templates/Ubuntu.info  . I didn't enable proposed so only ubuntu base and 3 other files updated so far .

That's good to see those files are out of proposed repos .

Regards..

---

### Post by syntaxerror74 on 2015-10-23
> **ronacc said:**
> darn I was hoping for xenophobic  Xenurine .

gawd no! This name change would have literally p!$$ed me off (due to too much urine in the name :lol: )

---

### Post by MikeMecanic on 2015-10-23
Switch to the Ubuntu Main Server and all I got is a new Kernel patch.  The USA server returns no result, just like the Ubuntu mirror in my hometown.
At this time of the year, Xenial prepares hibernation. So, maybe he's to busy...;)
```
wily@hp:~$ uname -r
4.2.0-17-generic
wily@hp:~$ 

```

**Please don't try that because video streaming is affected by this new Kernel release.  Will go backward using Synaptic.**
Take care,
Edit:  When backward to 4.2.0.16 but the problem appears to be the web site.  False alarm there ain't no bug with the 4..2.0.17 version.   I guess we all have to wait.

---

### Post by rrnbtter on 2015-10-24
Greetings,
I got another 306MB of updates last night, mostly from proposed. Then another 26MB this morning, proposed also. Still no crash and reinstall. FYI.
There is a python update in proposed that is being held back as of this morning.

---

### Post by grahammechanical on 2015-10-24
Yes, I am getting more code than I expected for a weekend, even without proposed enabled.

---

### Post by anca-emanuel on 2015-10-27
First ISO: [http://cdimage.ubuntu.com/daily-live/pending/](http://cdimage.ubuntu.com/daily-live/pending/)

---

### Post by sgage on 2015-10-27
> **anca-emanuel said:**
> First ISO: [http://cdimage.ubuntu.com/daily-live/pending/](http://cdimage.ubuntu.com/daily-live/pending/)

Seems like the 'flavors' all have their daily builds up today as well...

---

### Post by Cavsfan on 2015-11-03
I was just noticing how cool this is: **Xenial Xerus Xubuntu 16.04**. :p

---

### Post by v3.xx on 2015-11-03
I find myself off to a bumpy start.  Two crashes and one freeze.  Some apps are glitching and virtualbox is behaving oddly.  But still running it full time :)

---

### Post by sammiev on 2015-11-03
So far so good with Xenial.

No errors to report.

---

### Post by jerrylamos on 2015-11-03
Text and jpg's smeared and garbled unreadable.

Fix was in
bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255

Cory Davis (corzneffect) is correct;
Downgrading the video acceleration from "sna" to "uxa" works as a temporary fix:

I've been battling this since December on 15.04 now 15.10.  14.10 and previous no problem at all.

Not sure how "temporary" this fix is going to be for me.

---

### Post by Cavsfan on 2015-11-05
Noticed this today:

[Ubuntu 16.04 LTS to Drop Ubuntu Software Center for GNOME Software.]("http://news.softpedia.com/news/ubuntu-16-04-lts-to-drop-ubuntu-software-center-for-gnome-software-495760.shtml")

---

### Post by rrnbtter on 2015-11-05
Greetings,
This may be creditable also.

> [http://news.softpedia.com/news/no-canonical-is-not-killing-the-ubuntu-software-center-489990.shtml](http://news.softpedia.com/news/no-canonical-is-not-killing-the-ubuntu-software-center-489990.shtml)

---

### Post by grahammechanical on 2015-11-05
I watched the UOS session. Did you notice the motivation for this change? It is the intention to have a software centre that can install snap packages on 16.04 unity 7. And these snap apps are meant to be the standard desktop type apps and not just the phone apps.

 It seems that it will be easier to modify Gnome software centre than Ubuntu software centre. So, Gnome software centre will become the default for 16.04.

But keep in mind that for Ubuntu Personal the intention is for the phone app store to be the default and for all apps to the snap packaged. We need tp tie all this in with the intention to run X apps like Libreoffice in a Linux container (LXC) in xmir and live in hope that they will at some point become native Mir apps or at least snaps.

Regards.

---

### Post by v3.xx on 2015-11-05
Has anyone tried virtualbox?  I loaded it from the xenial repositories and it installed without issue, but..

I remove the toolbar and statusbar by unchecking them.  If I then recheck the display option, it will not display.  Seem to be gone forever.

I can also reboot the guest without issue, but if I shutdown or power down I lose my  guest screen resolution.

---

### Post by fjgaude on 2015-11-05
> **v3.xx said:**
> Has anyone tried virtualbox?  I loaded it from the xenial repositories and it installed without issue, but..

I remove the toolbar and statusbar by unchecking them.  If I then recheck the display option, it will not display.  Seem to be gone forever.

I can also reboot the guest without issue, but if I shutdown or power down I lose my  guest screen resolution.

I had to install libvpx1 before VBox would load but after that all seems correct. Of course I'm running the Intel video code. 16.04 is starting out just like 15.10, very easy to work with but who knows when the bugs, breakages starts? <smile>

---

### Post by fjgaude on 2015-11-05
> **grahammechanical said:**
> I watched the UOS session. Did you notice the motivation for this change? It is the intention to have a software centre that can install snap packages on 16.04 unity 7. And these snap apps are meant to be the standard desktop type apps and not just the phone apps.

 It seems that it will be easier to modify Gnome software centre than Ubuntu software centre. So, Gnome software centre will become the default for 16.04.

But keep in mind that for Ubuntu Personal the intention is for the phone app store to be the default and for all apps to the snap packaged. We need tp tie all this in with the intention to run X apps like Libreoffice in a Linux container (LXC) in xmir and live in hope that they will at some point become native Mir apps or at least snaps.

Regards.

This all sounds good to me. We desktop folks will be happy campers as all these changes come about.

---

### Post by QDR06VV9 on 2015-11-05
> **grahammechanical said:**
> I watched the UOS session. Did you notice the motivation for this change? It is the intention to have a software centre that can install snap packages on 16.04 unity 7. And these snap apps are meant to be the standard desktop type apps and not just the phone apps.

 It seems that it will be easier to modify Gnome software centre than Ubuntu software centre. So, Gnome software centre will become the default for 16.04.

But keep in mind that for Ubuntu Personal the intention is for the phone app store to be the default and for all apps to the snap packaged. We need tp tie all this in with the intention to run X apps like Libreoffice in a Linux container (LXC) in xmir and live in hope that they will at some point become native Mir apps or at least snaps.

Regards.
Thank You Sir for the clear explanations. I have honestly tried to keep up with UOS Sessions but I'll be Darned if I don't forget or something will come up that prevents me from
Watching or Reading. Very kind of you to take the time to post them.
Kind Regards

---

### Post by launchpad-washuu on 2015-11-05
> **Cavsfan said:**
> Noticed this today:

[Ubuntu 16.04 LTS to Drop Ubuntu Software Center for GNOME Software.]("http://news.softpedia.com/news/ubuntu-16-04-lts-to-drop-ubuntu-software-center-for-gnome-software-495760.shtml")

This may be due to the intent to finally [retire Python 2.x from Ubuntu]("http://summit.ubuntu.com/uos-1511/meeting/22568/python3-only-on-the-images/") with the Xenial release.

---

### Post by rcjones1369 on 2016-01-12
I like this distro. It worked with my UEFI mainboard and also with my PNY GT240 video card.

---

