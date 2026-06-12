---
title: "Impish UP"
date: 2021-04-28
forum: Ubuntu Development Version
---

### Post by zebra2 on 2021-04-28
```

zebra1@zebra1-Lenovo-320-15IAP:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Impish Indri (development branch)
Release:	21.10
Codename:	impish
zebra1@zebra1-Lenovo-320-15IAP:~$ 


No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Impish Indri (development branch)
Release:	21.10
Codename:	impish
inxi -Sxx
System:
  Host: zebra1-Lenovo-320-15IAP Kernel: 5.11.0-16-generic x86_64 bits: 64 
  compiler: gcc v: 10.2.1 Desktop: GNOME 3.38.4 tk: GTK 3.24.25 
  wm: gnome-shell dm: GDM3 Distro: Ubuntu 21.10 21.04 (Impish Indri) 
$DESKTOP_SESSION
ubuntu
$XDG_SESSION_TYPE
wayland
GNOME Shell 3.38.4
Version: 3.38.4-1ubuntu2
loginctl type
Type=wayland

```

---

### Post by grahammechanical on 2021-04-28
I have taken the plunge
```
 :~$ cat /etc/os-release 
PRETTY_NAME="Ubuntu Impish Indri (development branch)" 
NAME="Ubuntu" 
VERSION_ID="21.10" 
VERSION="21.04 (Impish Indri)" 
VERSION_CODENAME=impish 
ID=ubuntu 
ID_LIKE=debian 
HOME_URL="https://www.ubuntu.com/" 
SUPPORT_URL="https://help.ubuntu.com/" 
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" 
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" 
UBUNTU_CODENAME=impish
```

Regards

---

### Post by ajgreeny on 2021-04-28
Yesterday I manually updated a VM I was running of Xubuntu Hirsute to Xubuntu Impish by editing the /etc/apt/sources.list file, changing all instances of the word **hirsute** to **impish**.

No updates came immediately after that edit but today there were several, though I have no idea if those same updates came to hirsute as I no longer have that version.

It is currently running very well in a wayland session; it'll be interesting to see when the first problem occurs after an update.

---

### Post by grahammechanical on 2021-04-28
Before changing the sources.list file on my Ubuntu Hirsute I checked and there were no updates available. But after changing the sources.list file to Impish and then updating there were several updates in the pipeline.

Regards

---

### Post by ajgreeny on 2021-04-28
Not yesterday!
I updated before the sources.list edit as well and none appeared immediately afterwards.

---

### Post by guiverc on 2021-04-28
I made my review of old sources (commenting out anything I'd added for testing purposes, looking for clues on stuff I could remove (installed for test only) etc.) and added `impish` about ~30 hours after the release was done or as soon as I detected impish was usable without errors on `sudo apt update`.

It took longer this time for `base-files` to be amended so my system stopping saying it was 21.04 than I believe is normal; *stable* isn't what I expect to see on this box.. but  yesterday that appeared, and this morning I had packages to upgrade...

---

### Post by zika on 2021-04-29
„Devel“ works:
```
W: Conflicting distribution: http://archive.ubuntu.com/ubuntu devel-proposed InRelease (expected devel-proposed but got impish)
W: Conflicting distribution: http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu devel InRelease (expected devel but got groovy)
W: Conflicting distribution: http://ppa.launchpad.net/canonical-kernel-team/proposed/ubuntu devel InRelease (expected devel but got hirsute)
W: Conflicting distribution: http://archive.ubuntu.com/ubuntu devel InRelease (expected devel but got impish)
W: Conflicting distribution: http://archive.canonical.com/ubuntu devel InRelease (expected devel but got groovy)
W: Conflicting distribution: http://archive.ubuntu.com/ubuntu devel-updates InRelease (expected devel-updates but got impish)
W: Conflicting distribution: http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu devel InRelease (expected devel but got hirsute)
W: Conflicting distribution: http://archive.ubuntu.com/ubuntu devel-backports InRelease (expected devel-backports but got impish)
W: Conflicting distribution: http://ppa.launchpad.net/cappelikan/ppa/ubuntu devel InRelease (expected devel but got hirsute)
W: Conflicting distribution: http://ppa.launchpad.net/damentz/liquorix/ubuntu devel InRelease (expected devel but got hirsute)
W: Conflicting distribution: http://security.ubuntu.com/ubuntu devel-security InRelease (expected devel-security but got impish)
W: Conflicting distribution: http://ppa.launchpad.net/deity/sid/ubuntu devel InRelease (expected devel but got hirsute)
W: Conflicting distribution: http://ppa.launchpad.net/libreoffice/libreoffice-7-0/ubuntu devel InRelease (expected devel but got focal)
W: Conflicting distribution: http://security.ubuntu.com/ubuntu devel InRelease (expected devel but got impish)
W: Conflicting distribution: http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu devel InRelease (expected devel but got impish)
W: Conflicting distribution: http://ppa.launchpad.net/mkusb/ppa/ubuntu devel InRelease (expected devel but got hirsute)
W: Conflicting distribution: http://ppa.launchpad.net/regolith-linux/unstable/ubuntu devel InRelease (expected devel but got hirsute)
W: Conflicting distribution: http://ppa.launchpad.net/shemgp/gnome-40/ubuntu devel InRelease (expected devel but got hirsute)
```

---

### Post by guiverc on 2021-04-30
I noted @[[COLOR=#000000]grahammechanical[/COLOR]]("https://ubuntuforums.org/member.php?u=1087323")[COLOR=#000000] had (comment #2)
[/COLOR][SIZE=2]
> [SIZE=3]Version=Ubuntu 21.04 (Impish Indri)[/SIZE][/SIZE]

as I did... so [https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/1926544](https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/1926544)

now Fix Committed.. so the *"**stray" *21.04 should disappear soon.

> base-files (11.1ubuntu2) impish; urgency=medium
  * Fix remaining stray reference to 21.04.  LP: [#1926544]("https://bugs.launchpad.net/bugs/1926544").
 -- Steve Langasek <email address hidden>  Wed, 28 Apr 2021 23:47:16 -0700

---

### Post by corradoventu on 2021-05-01
1st ISO available: [https://cdimage.ubuntu.com/daily-live/pending/](https://cdimage.ubuntu.com/daily-live/pending/)
but inxi seems confused between 21.10 and 21.04```
corrado@corrado-x6-ii-0501:~$ inxi -Fx
System:
  Host: corrado-x6-ii-0501 Kernel: 5.11.0-16-generic x86_64 bits: 64 
  compiler: gcc v: 10.2.1 Desktop: GNOME 3.38.4 
  Distro: Ubuntu 21.10 21.04 (Impish Indri) 
```

---

### Post by oldfred on 2021-05-01
Copied 21.04 ISO to new impish name. Bit more than usual for first ISO change.

[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cd ISO [/COLOR]
[COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/ISO**[/COLOR][COLOR=#000000]$ zsync [http://cdimage.ubuntu.com/kubuntu/daily-live/pending/impish-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/kubuntu/daily-live/pending/impish-desktop-amd64.iso.zsync) [/COLOR]
#################### 100.0% 156.3 kBps DONE     

```
reading seed file impish-desktop-amd64.iso: ******************************************************************************************

*************************************************************************************************************************************
Read impish-desktop-amd64.iso. Target 74.3% complete.       
downloading from [http://cdimage.ubuntu.com/kubuntu/daily-live/pending/impish-desktop-amd64.iso:](http://cdimage.ubuntu.com/kubuntu/daily-live/pending/impish-desktop-amd64.iso:) 
##############------ 74.3% 5.8 kBps          
#################### 100.0% 10473.0 kBps DONE      

verifying download...checksum matches OK 
used 2187321344 local, fetched 755315670

```

[/FONT]

---

### Post by VMC on 2021-05-02
Yes, I noticed that on all of them (U,K,L,M,X). Everyone is quite large.

---

### Post by lammert-nijhof on 2021-05-10
I installed 4 Ubuntu versions in a Virtualbox VM:
 1. Ubuntu 21.10 with QEMU/KVM to keep an eye of developments in QEMU/KVM and the use of Gnome 40 for full screen VMs. So I'm running 
     ---- Ubuntu 14.04 or Windows Vista on top of 
     ---- Ubuntu 21.10 using ext4 and QEMU/KVM on top of 
     ---- Ubuntu 21.04 using OpenZFS 2.0 and Virtualbox.
 2. Xubuntu 21.10 using OpenZFS, to keep an eye on OpenZFS 2.1
 3. Ubuntu Budgie 21.10
 4. Ubuntu Mate 21.10

Note that Ubuntu 14.04 has even access to the lowest level shared folders of OpenZFS on the Host OS Ubuntu 21.04. The hardware is a very modest Ryzen 3 2200G with 16GB DDR4 (3000MHz).
I dislike the default Gnome design, running a Fedora 34 VM I have every time to push the "windows" key and that really start to annoy me. I hope Ubuntu improves on that experience with its dock.

---

