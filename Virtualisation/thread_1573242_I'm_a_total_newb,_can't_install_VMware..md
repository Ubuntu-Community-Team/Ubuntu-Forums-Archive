---
title: "I'm a total newb, can't install VMware."
date: 2010-09-12
forum: Virtualisation
---

### Post by Tian102983 on 2010-09-12
My very first post. I'm trying to install VMware.
I'm using Ubuntu 10.04 LTS
I downloaded VMware-Player-3.1.1-282343.x86_64.bundle
I looked online for some solutions on how to install a bundle, I have been unsuccessful in my attempts perhaps someone can help me out.
This is what I have tried so far:
The file was in my Downloads folder.

I opened Terminal
cd Downloads
chmod +x VMware-Player-3.1.1-282343.x86_64.bundle
sudo ./VMware-Player-3.1.1-282343.x86_64.bundle

Then I got a message
./VMware-Player-3.1.1-282343.x86_64.bundle: 110: Syntax error:newline unexpected

and that's where I stand.
I'm trying to install windows 7 onto my Ubuntu.
Did I do something wrong? Am I missing something? Did I download the wrong bundle?

---

### Post by JustinR on 2010-09-12
If you want to save some trouble, [VirtualBox]("http://www.virtualbox.org/") has a simpler installation (it does everything VMWare can do), [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

Here is the link, just open it up and press 'Install'.
[http://download.virtualbox.org/virtualbox/3.2.8/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_i386.deb](http://download.virtualbox.org/virtualbox/3.2.8/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_i386.deb)

---

### Post by TJet1.8 on 2010-09-12
Before installing VMware Player, you must ensure your "build" environment is already setup on your computer.

When installing VMware Player/Workstation, it will compile the modules required to run based on the kernel version installed.
If your build environment doesn't exist...it can't build the modules.

So...install the build environment first:

sudo apt-get install gcc build-essential linux-headers-$(uname -r) dkms

Once the build environment is installed, then install VMware Player.

As for the bundle, which version of Ubuntu did you install?...i386 (32-bit) version or the x86_64 (64-bit) version?

If you installed the i386 version...then you need to install the i386 VMware Player bundle. x86_64 version will require the bundle you already have.

Good luck :)

---

### Post by Tian102983 on 2010-09-12
JustinR: Thanks I'd tried that on your suggestion, and I'll use it for now, but I've heard some reviews that VMware works better. And I'm having aspect ratio issues with Virtualbox, I'm only getting 4:3 instead of 16:9. And there doesn't seem to be any sound. Is this normal? Checked virutalbox settings, and doesn't to be anything that I can do to change the aspect ratio or get sound, or it's out of my outstanding of how to fix the issues.

TJet: I installed 64bit Ubuntu. I'll try what you said right now, and give an update.

---

### Post by Tian102983 on 2010-09-12
Okay this is what I did and what happened:

allen@Gwen:~$ sudo apt-get install gcc build-essential linux-headers-$(uname -r) dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
linux-headers-2.6.32-24-generic is already the newest version.
linux-headers-2.6.32-24-generic set to manually installed.
The following extra packages will be installed:
  dpkg-dev fakeroot patch xz-utils
Suggested packages:
  debian-keyring debian-maintainers diffutils-doc
The following NEW packages will be installed:
  build-essential dkms dpkg-dev fakeroot patch xz-utils
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,185kB of archives.
After this operation, 3,756kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main xz-utils 4.999.9beta+20091116-1 [233kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main patch 2.6-2ubuntu1 [121kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main dpkg-dev 1.15.5.6ubuntu4.1 [653kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main build-essential 11.4build1 [7,278B]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main dkms 2.1.1.2-2fakesync1 [70.1kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main fakeroot 1.14.4-1ubuntu1 [101kB]
Fetched 1,185kB in 4s (242kB/s)
Selecting previously deselected package xz-utils.
(Reading database ... 168961 files and directories currently installed.)
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20091116-1_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.5.6ubuntu4.1_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4build1_amd64.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up xz-utils (4.999.9beta+20091116-1) ...
Setting up patch (2.6-2ubuntu1) ...
Setting up dpkg-dev (1.15.5.6ubuntu4.1) ...
Setting up build-essential (11.4build1) ...
Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

allen@Gwen:~$ cd Downloads
allen@Gwen:~/Downloads$ chmod +x VMware-Player-3.1.1-282343.x86_64.bundle
allen@Gwen:~/Downloads$ sudo ./VMware-Player-3.1.1-282343.x86_64.bundle
./VMware-Player-3.1.1-282343.x86_64.bundle: 110: Syntax error: newline unexpected

---

### Post by JustinR on 2010-09-12
Not trying to be a VirtualBox fanboy here but, as your first post said - your a Newb - and VirtualBox is way easier to install for a newbie. So unless you require VMware I would suggest VirtualBox.

---

### Post by Tian102983 on 2010-09-12
I understand that, but if the performance is better under VMware, I'd still like to figure it out. Beside like I said the aspect ratio is 4:3 and I don't get any sound in Virtualbox, I appreciate the advice and I'm going to use virtualbox, but if it's possible I'd want to try VMware also.

---

### Post by JustinR on 2010-09-12
> **Tian102983 said:**
> I understand that, but if the performance is better under VMware, I'd still like to figure it out. Beside like I said the aspect ratio is 4:3 and I don't get any sound in Virtualbox, I appreciate the advice and I'm going to use virtualbox, but if it's possible I'd want to try VMware also.

In your VM, try installing VirtualBox Guest Additions - this should fix display issues/sound issues/network issues, etc.

When your VM is at it's desktop, on the VirtualBox VM Menu, go to Devices > Install VirtualBox Guest Additions. (Works for Windows/Linux and some other OS')

---

### Post by cwwilson721 on 2010-09-13
DUH!!!

Everyone is missing the point.

OPs issue would be solved by typing ```
 [COLOR=Red]sudo sh[/COLOR] VM*.bundle
```NOT ```
[COLOR=Red]sudo ./[/COLOR]VMware-Player-3.1.1-282343.x86_64.bundle
```right off the bat. 
I still do the same thing myself, coming from a distro with a REAL root and no GUI to start with (SW3, back in the day)

I'm surprised you didn't tell the OP to reformat their sda drive, then re-invent the wheel. Well, you DID with the other stuff you told them to install. 
Here's some news: THOSE OTHER PROGS ARE NOT REQUIRED TO INSTALL VMWARE PLAYER!

While you can FanBoy about VB, the OP wants VMWare. Now the OP can get on with using VMWare Player.

Take it to the playground, children.

---

### Post by Tian102983 on 2010-09-14
Thanks cwwilson721, that worked. I suspected that I did something wrong and that it was my lack of understanding of directions that I googled. Marking thread as solved now. 

Also thank Justin, your advice on how to fix the aspect ratio on virtualbox worked also. The sound still wasn't working though, but I found out I had to install realtek '97 audio driver, and that worked.

---

