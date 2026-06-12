---
title: "DIfferent advice from Update-Manager and apt-get update/upgrade"
date: 2011-10-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-23
Weird thing going on today:

Update-Manager pops telling me it has 30 updates. Pressing check (to refresh) gives me the same 30. sudo apt-get update && sudo apt-get upgrade tells me I'm up to date: no updates, no held back packages.

Can anyone confirm this difference between Update-Manager and apt-get?

Thanks,
Effenberg

---

### Post by ronacc on 2011-10-23
I updated earlier today using synaptic , before your post ,now update-manager (which I NEVER USE ) shows no updates .

---

### Post by effenberg0x0 on 2011-10-23
There's something very wrong here.

$ sudo apt-get update && sudo apt-get upgrade

```
Fetched 1.581 B in 10s (144 B/s)                                                                                                   
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.**

```[ATTACH]205254[/ATTACH]

---

### Post by lucazade on 2011-10-23
I have seen the same in Oneiric on a friend's pc.. sincerly no idea why this is happening

---

### Post by coffeecat on 2011-10-23
The two are in agreement for me.

```
coffeecat@amd4-testing:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ia32-libs-multiarch:i386
The following packages will be upgraded:
  binutils firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  initramfs-tools initramfs-tools-bin libaa1 libatasmart4 libcddb2 libcroco3
  libmpg123-0:i386 liboil0.3 libsmbclient libtheora0 libvpx0 libwbclient0
  libwbclient0:i386 libxp6:i386 libxpm4 polkit-kde-1 python-gobject
  python-gobject-cairo python-pkg-resources samba samba-common
  samba-common-bin smbclient thunderbird thunderbird-globalmenu
  thunderbird-gnome-support wamerican wbritish
33 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 74.7 MB of archives.
After this operation, 361 kB disk space will be freed.
Do you want to continue [Y/n]? 
```

I did an "apt-get update" less than a minute before and Update Manager is in screenshot.

---

### Post by philinux on 2011-10-23
I'm not at home now but I would be interested to see what aptitude safe-upgrade shows.

---

### Post by effenberg0x0 on 2011-10-23
Using aptitude safe-upgrade:

```
[03:45 ][al:AL-DESK:~]
$ sudo aptitude safe-upgrade
The following packages will be upgraded: 
  libpam-smbpass libwbclient0 samba samba-common smbclient winbind 
The following packages are RECOMMENDED but will NOT be installed:
  libpam-winbind 
6 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 28,8 MB of archives. After unpacking 3.475 kB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
```[ATTACH]205267[/ATTACH]

I'll try to debug it further. It makes no sense to post a bug report when other users can't confirm any unusual behavior here.

---

### Post by ronacc on 2011-10-23
I often see synaptic or apt-get showing MORE updates than update-manager but I have never seen LESS .

---

### Post by effenberg0x0 on 2011-10-23
> **ronacc said:**
> I often see synaptic or apt-get showing MORE updates than update-manager but I have never seen LESS .

That does worry me. I thought any update tool would report the same. Either there are n updates or there are 0 updates. There can't be a different number of updates suggestions depending on the tool used, right?

---

### Post by CaptainMark on 2011-10-23
that is a weird one, just out of curiosity, what does synaptic report, synaptic is only an apt-get front so should be the same but ive come to expect anything from pre-release now

---

### Post by effenberg0x0 on 2011-10-23
> **CaptainMark said:**
> that is a weird one, just out of curiosity, what does synaptic report, synaptic is only an apt-get front so should be the same but ive come to expect anything from pre-release now

It's a mess. 3 tools, 3 different results. But in my opinion, unless someone else sees it here, I have to assume it's specific to my system and debug it before considering to file a bug report.

**sudo apt-get update && sudo apt-get upgrade** **(6 packages held back)**
```

The following packages have been kept back:
  libpam-smbpass libwbclient0 samba samba-common smbclient winbind
**0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.**

```**Synaptic (0 Broken, 0 to Install/Upgrade, 0 to Remove)**
[ATTACH]205291[/ATTACH]

**Update-Manager** **(10 packages to download)**
[ATTACH]205292[/ATTACH]

---

### Post by ronacc on 2011-10-23
I just updated my repos and checked again , update manager and synaptic agree 5 avail one of which is held .

---

### Post by ranch hand on 2011-10-24
This is very strange.  These things all use dpkg.  I would have thought that the results, at least of "apt-get dist-upgrade", "aptitude full-upgrade", UM and synaptic would be identical.  I say that because with any other commands you are not going to get the added packages to be installed with the upgrades.  In UM they are there (if I remember right).  In synaptic you need to hit "apply" to get them all together.

If they are not listing the same numbers that way I would be trying to "dpkg-reconfigure <package> <package>   " and if that didin't do it I would use apt-get or aptitude to reinstall them.

If that leaves the buggers out of sync I would file a bug on dpkg if they were all out of agreement.

---

### Post by stoneguy on 2011-10-24
After about 36 hours of

[INDENT]0 upgraded, 0 newly installed, 0 to remove[/INDENT]

and me thinking

[INDENT]Wow! They got all Oneiric's bugs resolved _already_?[/INDENT]

I finally got a request to upgrade some libpam components.

Perhaps Precise will get upgrades sorted out as well.

---

### Post by gsmanners on 2011-10-24
Does Update Manager actively update itself while it's open or do you need to close it and restart it for that?

---

### Post by ventrical on 2011-10-24
I think I got the black screenshot of death here. I was trying to capture Update manager and Synaptic and I got the BLSOD on 2 screens.

 But I got this from terminal:
dale@ubuntu:~$ sudo apt-get upgrade
[sudo] password for dale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dale@ubuntu:~$ 

but the other 2 screenshots reported upgrades available from SPM and  UM.

---

### Post by effenberg0x0 on 2011-10-24
I purged update-manager, update-notifier and synaptic. Never used these tools and trust apt-get is more reliable (has always been for me, at least). Once the real resting for PP starts, we'll have the opportunity to see if more users see difference between what these tools report. Right now I can't really say whether I might have somehow messed up here and created this situation.

---

### Post by ventrical on 2011-10-24
> **effenberg0x0 said:**
> I purged update-manager, update-notifier and synaptic. Never used these tools and trust apt-get is more reliable (has always been for me, at least). Once the real resting for PP starts, we'll have the opportunity to see if more users see difference between what these tools report. Right now I can't really say whether I might have somehow messed up here and created this situation.


I ran Update Manager (don't use it) . I had a major crash. cant take screen shots, CPUs both running at 100%. I am typing this from an Ocelot Install.

My CPU was 65C! too warm for me. and memory jumped right up there.

  I'll try and get back in ince my cpu cools off.

---

