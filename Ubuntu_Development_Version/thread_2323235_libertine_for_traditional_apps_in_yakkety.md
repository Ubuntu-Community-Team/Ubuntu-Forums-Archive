---
title: "libertine for traditional apps in yakkety"
date: 2016-05-03
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-05-03
I took the plunge and;

```

sudo apt-get install libertine

```

and got this

```

The following additional packages will be installed:
  bridge-utils cloud-image-utils debootstrap distro-info gir1.2-libertine
  libaio1 libboost-random1.60.0 libboost-thread1.60.0 libertine-tools
  libiscsi2 liblibertine1 liblxc1 libpam-cgfs librados2 librbd1 lxc-common
  lxc-templates lxc1 lxcfs python3-distro-info python3-libertine
  python3-libertine-lxc python3-lxc python3-psutil qemu-block-extra qemu-utils
  sharutils uidmap
Suggested packages:
  cloud-utils-euca shunit2 btrfs-tools lvm2 lxctl python3-libertine-chroot
  python-psutil-doc bsd-mailx | mailx
The following NEW packages will be installed:
  bridge-utils cloud-image-utils debootstrap distro-info gir1.2-libertine
  libaio1 libboost-random1.60.0 libboost-thread1.60.0 libertine
  libertine-tools libiscsi2 liblibertine1 liblxc1 libpam-cgfs librados2
  librbd1 lxc-common lxc-templates lxc1 lxcfs python3-distro-info
  python3-libertine python3-libertine-lxc python3-lxc python3-psutil
  qemu-block-extra qemu-utils sharutils uidmap
0 upgraded, 29 newly installed, 0 to remove and 34 not upgraded.
Need to get 5,915 kB of archives.
After this operation, 22.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y

```

and

```

Unpacking debootstrap (1.0.78+nmu1ubuntu2) ...
Selecting previously unselected package liblibertine1:amd64.
Preparing to unpack .../liblibertine1_1.0.0+16.04.20160411-0ubuntu1_amd64.deb ...
Unpacking liblibertine1:amd64 (1.0.0+16.04.20160411-0ubuntu1) ...
Selecting previously unselected package gir1.2-libertine:amd64.
Preparing to unpack .../gir1.2-libertine_1.0.0+16.04.20160411-0ubuntu1_amd64.deb ...
Unpacking gir1.2-libertine:amd64 (1.0.0+16.04.20160411-0ubuntu1) ...
Selecting previously unselected package python3-libertine.
Preparing to unpack .../python3-libertine_1.0.0+16.04.20160411-0ubuntu1_amd64.deb ...
Unpacking python3-libertine (1.0.0+16.04.20160411-0ubuntu1) ...
Selecting previously unselected package libertine-tools.
Preparing to unpack .../libertine-tools_1.0.0+16.04.20160411-0ubuntu1_amd64.deb ...
Unpacking libertine-tools (1.0.0+16.04.20160411-0ubuntu1) ...
Selecting previously unselected package python3-libertine-lxc.
Preparing to unpack .../python3-libertine-lxc_1.0.0+16.04.20160411-0ubuntu1_amd64.deb ...
Unpacking python3-libertine-lxc (1.0.0+16.04.20160411-0ubuntu1) ...
Selecting previously unselected package libertine.
Preparing to unpack .../libertine_1.0.0+16.04.20160411-0ubuntu1_amd64.deb ...
Unpacking libertine (1.0.0+16.04.20160411-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (229-5ubuntu1) ...
Processing triggers for install-info (6.1.0.dfsg.1-6) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up libiscsi2:amd64 (1.12.0-2) ...
Setting up bridge-utils (1.5-9ubuntu1) ...
Setting up distro-info (0.14build1) ...
Setting up libaio1:amd64 (0.3.110-2) ...
Setting up libboost-random1.60.0:amd64 (1.60.0+dfsg-4ubuntu1) ...
Setting up libboost-thread1.60.0:amd64 (1.60.0+dfsg-4ubuntu1) ...
Setting up libpam-cgfs (2.0.0-3) ...
Setting up librados2 (10.2.0-0ubuntu1) ...
Setting up librbd1 (10.2.0-0ubuntu1) ...
Setting up lxcfs (2.0.0-3) ...
Created symlink from /etc/systemd/system/multi-user.target.wants/lxcfs.service to /lib/systemd/system/lxcfs.service.
Setting up python3-distro-info (0.14build1) ...
Setting up python3-psutil (4.1.0-1) ...
Setting up qemu-block-extra:amd64 (1:2.5+dfsg-5ubuntu11) ...
Setting up qemu-utils (1:2.5+dfsg-5ubuntu11) ...
Setting up sharutils (1:4.15.2-1) ...
Setting up uidmap (1:4.2-3.1ubuntu5) ...
Setting up cloud-image-utils (0.27-0ubuntu24) ...
Setting up debootstrap (1.0.78+nmu1ubuntu2) ...
Setting up liblibertine1:amd64 (1.0.0+16.04.20160411-0ubuntu1) ...
Setting up gir1.2-libertine:amd64 (1.0.0+16.04.20160411-0ubuntu1) ...
Setting up python3-libertine (1.0.0+16.04.20160411-0ubuntu1) ...
Setting up libertine-tools (1.0.0+16.04.20160411-0ubuntu1) ...
Setting up liblxc1 (2.0.0-0ubuntu2) ...
Setting up python3-lxc (2.0.0-0ubuntu2) ...
Setting up lxc1 (2.0.0-0ubuntu2) ...
Created symlink from /etc/systemd/system/multi-user.target.wants/lxc-net.service to /lib/systemd/system/lxc-net.service.
Created symlink from /etc/systemd/system/multi-user.target.wants/lxc.service to /lib/systemd/system/lxc.service.
Setting up lxc dnsmasq configuration.
Setting up lxc-templates (2.0.0-0ubuntu2) ...
Setting up python3-libertine-lxc (1.0.0+16.04.20160411-0ubuntu1) ...
Setting up libertine (1.0.0+16.04.20160411-0ubuntu1) ...
Setting up lxc-common (2.0.0-0ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for systemd (229-5ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ventrical@ventrical-System-Product-Name:~$ 

```

regards..

---

### Post by ventrical on 2016-05-03
It provides a container for Snappy Personal.. hmmm .. interesting.

---

### Post by ventrical on 2016-05-04
libertine for unit8 and desktop.

[https://wiki.ubuntu.com/Touch/Libertine](https://wiki.ubuntu.com/Touch/Libertine)

---

### Post by ventrical on 2016-05-04
libertine, unity8 links

[https://wiki.ubuntu.com/Touch/Libertine#nextSteps](https://wiki.ubuntu.com/Touch/Libertine#nextSteps)

[https://wiki.ubuntu.com/Unity8Desktop](https://wiki.ubuntu.com/Unity8Desktop)

---

### Post by ventrical on 2016-05-04
libertine is working in unity8 with the exception that you have to enter the exact link to install the debian package.

Can anyone give me some examples .. ie; such as firefox or mkusb?

---

### Post by ventrical on 2016-05-04
To install a ppa, libertine asks for :  ppa:user/ppa-name   ...hrrrmmn

---

### Post by zika on 2016-05-05
> **ventrical said:**
> To install a ppa, libertine asks for :  ppa:user/ppa-name   ...hrrrmmn**ppa:mkusb/ppa** 
  [https://launchpad.net/~mkusb/+archive/ubuntu/ppa](https://launchpad.net/~mkusb/+archive/ubuntu/ppa) 
  [http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

---

### Post by ventrical on 2016-05-05
> **zika said:**
> **ppa:mkusb/ppa** 
  [https://launchpad.net/~mkusb/+archive/ubuntu/ppa](https://launchpad.net/~mkusb/+archive/ubuntu/ppa) 
  [http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

Libertine keeps dismissing it no matter which way I put it in, full link or just ppa. I think there may be a network problem.

---

### Post by ventrical on 2016-05-05
This program seems only to work on specialty hardware at the moment. I can create containers, download classic apps and the scopes/icons install in unity8 but they will not run.

---

### Post by grahammechanical on 2016-05-05
The future of Ubuntu depends on this working. So, it is not like it is important. :) It does explain why there is no date set for Unity 8 to become default.

---

### Post by ventrical on 2016-05-05
> **grahammechanical said:**
> The future of Ubuntu depends on this working. So, it is not like it is important. :) It does explain why there is no date set for Unity 8 to become default.

The bottom line is that  the unity8 desktop team has "80 people" working on just unity8 desktop. Mark wants it out by 16.10.. but then he went on to say that *they* would use it first, ya know , test this, play with that .. etc..  and then it would be released to the general masses.. etc... This sort of leads me to believe that we (the testers) may be left out on this one. However, we know how dynamic ubuntu development is and so I do not plan to turn off my proposed repo any time soon. I also understand that it may be a very long summer. ehehe..

  uhhhm... yeah .. it is sort of like an empty canvas right now.

  In the meantime I am going to keep looking for tools and try to  compile my own container system to run classic apps.  I can sense it that it is right there.. it's just hanging on the edge waiting to fall into the matrix.

 regards..

---

### Post by ventrical on 2016-05-25
Good things come to those who wait :)

Already posted this in another forum . Got firefox running on Unity8 but that is the only legacy app working atm. Lots of libertine updates .. etc..

---

### Post by radarmy on 2016-06-01
I like it very much It's a good advantage

---

### Post by ventrical on 2016-06-01
It will take some time for it to all come together. A working firefox this early in the cycle is a real bonus.

regards..

---

### Post by ventrical on 2016-06-11
I was able to install leafpad and gedit into unity8 using libertine containers. Why? because we are suppossed to be testing that. I can also use xterm but it will not give me root permissions. I was able to create texts files with leafpad and gedit and save them and reload them.

There is one problem. If I boot clean into unity8 from a hard boot these apps (with the exception of firefox browser) will freeze up. But when I log off from unity7 an then log on to unity8 through the greeter that the apps work fine. So far at least anyways. I cannto get a good screenshot program to work so I can't send screenshots just yet. I can also use nautilus to check files.

Keep in mind that I am using the app x11-apps which I installed using:
```

sudo snap install x11-apps

```

I installed that app in a normal yakkety install of ubuntu (unity7). Now it shows up in unity8 'apps' and Legacy Apps icon is gone. I can still use libertine to install apps and experiment and create limitless containers. Libertine will not work on several installs . It is very touchy. The current install of which I am sending this message is using the ppa.

I can also tell developers are really working hard with it. One day firefox is working smooth and then the next you have to tap on the arrow keys to get the cursor to move left and right. Thats all a good sign :)

edit:

I have come to see that there seems to be some sort of collision with the x11-apps from snapd and libertine. Firefox will not run on libertine alone (in some instances and installs) but will work with x11-apps but then libertine will not function in unity8 at all (probably what it is designed to do) :)
 

Regards..

---

### Post by ventrical on 2016-06-15
This problem seems to be now fixed. I can run gedit and firefox at the same time in unity8 from hardboot.

There is a problem with cursor as it will not auto-slide when the arrow keys are held down. You have to tap, tap them  to get into desired position.

regards..

---

