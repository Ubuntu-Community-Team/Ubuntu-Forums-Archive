---
title: "New (unity) Ubuntu &quot;Software&quot; Center"
date: 2016-02-26
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-02-26
It has not come up with my updated/upgraded installs but it came in with  (ubuntu-unity/beta1) image.

---

### Post by ELD on 2016-02-26
Mine doesn't even list the categories.

The window also has black corners making the window square, which doesn't look right with Unity's rounded window corners.

---

### Post by grahammechanical on 2016-02-26
Is Ubuntu Software Centre still installed? Like you it has not yet been installed in my daily updated Xenial install. I do have Gnome Software (what confusion that name is going to cause) installed on another Xenial install but I got it through a PPA.

I will see if it is improved since I last tried that install of Xenial.

Regards.

---

### Post by mc4man on 2016-02-26
It (Software) remains pretty useless atm, it now shows *some* updates & can actually install those updates though it doesn't recognize that it did install them. (see screen, both updates were installed.
Maybe it thinks it's on Windows & you need to "Restart & Install"

---

### Post by grahammechanical on 2016-02-26
I used dist-upgrade to bring in Gnome Software. I also noticed that peculiarity with the Updates tab. A second click on the install button will produce another refresh of the window and this time the Install button is no longer present.

Click on an installed package and we get more information about the package & if it is an application there is a Launch button which at present is not working. The Dash does a similar trick. Give information and offer to launch the application and it works. Still it is early days. These things will come. We get to see the vision.

Regards.

---

### Post by MikeMecanic on 2016-02-26
> **grahammechanical said:**
> Is Ubuntu Software Centre still installed?.

No its not since more then a week now.

---

### Post by ventrical on 2016-02-26
> **mc4man said:**
> It (Software) remains pretty useless atm, it now shows *some* updates & can actually install those updates though it doesn't recognize that it did install them. (see screen, both updates were installed.
Maybe it thinks it's on Windows & you need to "Restart & Install"

It is actually very useless atm. Agreed. I wonder if  synaptic would fare any better.

I am using a system with intel xeon graphics and I notice as I am browsing arounf that I can see quick flashes of container type widgets that have content in them but it flicks so fast I cannot see what they are. maybe some GUI problems also.

---

### Post by ventrical on 2016-02-26
> **grahammechanical said:**
> I Still it is early days. These things will come. We get to see the vision.

Regards.

You have a knack with reassuring bromides. :)

regards..

---

### Post by sammiev on 2016-03-02
I updated tonight and Ubuntu-Gnome has a very nice populated "Software Center" now.

Hope it filter down to the other flavors.

---

### Post by mc4man on 2016-03-02
It's also filled in here on an ubuntu session

---

### Post by Frogs Hair on 2016-03-02
I have Gnome software and thought it was part of my Gnome Shell installation. ??

---

### Post by grahammechanical on 2016-03-02
USC has not been removed but its icon in the Launcher has been replaced by the GS icon. And yes, the catalogue was updated. It now has "books" on the shelves.

It handles updates in an unusual way. It will identify applications that can be updated but not (yet?) system packages. Each application has to be updated individually. It offers a restart & install option that does indeed restart but does not seem to do any installing. It will trigger the loading of Software Updater which will show in its list the packages that should have just been updated.

When 16.04 is released and the complaints start coming in, remember that this a Gnome utility and not a Ubuntu utility.

Regards.

---

### Post by Frogs Hair on 2016-03-02
I have USC also, Gnome software showed up with the shell.

---

### Post by mc4man on 2016-03-02
As far as I see Usc is gone from the images so it will only be Software (gnome). 
As far as updating thru it I just did for the one package update I had, Software did update it though still doesn't indicate that it did so even after closing & reopening.
As far as the Restart & Install button - it makes no sense, at best should only be available if updates require a restart. The wording will never make any sense in any use case, at least in 16.04, or ever.

[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1552508](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1552508)

---

### Post by MikeMecanic on 2016-03-03
Software: Third crash on startup back to back in less then an hour.

Made a bug report this morning: 
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1552787](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1552787)

---

### Post by ventrical on 2016-03-04
> **grahammechanical said:**
> USC has not been removed but its icon in the Launcher has been replaced by the GS icon. And yes, the catalogue was updated. It now has "books" on the shelves.

It handles updates in an unusual way. It will identify applications that can be updated but not (yet?) system packages. Each application has to be updated individually. It offers a restart & install option that does indeed restart but does not seem to do any installing. It will trigger the loading of Software Updater which will show in its list the packages that should have just been updated.

When 16.04 is released and the complaints start coming in, remember that this a Gnome utility and not a Ubuntu utility.

Regards.

It's working now to some dgree. The staus bar indicator does not work but it indexes/downloads and installs all programs (and newer ones) as USC used to do. Had to get some helpers and xorg update. Apport flagged out and would not report . Said I had ot update .. so I updated again and got these and now it works.

```

ventrical@ventrical-MS-7850:~$ sudo apt-get update
[sudo] password for ventrical: 
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                
Hit:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease              
Hit:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease               
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease         
Reading package lists... Done           
ventrical@ventrical-MS-7850:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  init init-system-helpers libbabeltrace-ctf1 libbabeltrace1 x11-common xorg
  xserver-xorg xserver-xorg-input-all xserver-xorg-video-all
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 251 kB of archives.
After this operation, 5,120 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 init-system-helpers all 1.29ubuntu1 [32.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 init amd64 1.29ubuntu1 [4,546 B]
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 x11-common all 1:7.7+13ubuntu3 [22.4 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial/main amd64 xserver-xorg-input-all amd64 1:7.7+13ubuntu3 [4,398 B]
Get:5 http://archive.ubuntu.com/ubuntu xenial/main amd64 xserver-xorg amd64 1:7.7+13ubuntu3 [57.2 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial/main amd64 xorg amd64 1:7.7+13ubuntu3 [2,988 B]
Get:7 http://archive.ubuntu.com/ubuntu xenial/main amd64 xserver-xorg-video-all amd64 1:7.7+13ubuntu3 [4,440 B]
Get:8 http://archive.ubuntu.com/ubuntu xenial/main amd64 libbabeltrace1 amd64 1.3.2-1 [34.7 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial/main amd64 libbabeltrace-ctf1 amd64 1.3.2-1 [88.3 kB]
Fetched 251 kB in 1s (210 kB/s)              
(Reading database ... 197638 files and directories currently installed.)
Preparing to unpack .../init-system-helpers_1.29ubuntu1_all.deb ...
Unpacking init-system-helpers (1.29ubuntu1) over (1.28ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up init-system-helpers (1.29ubuntu1) ...
(Reading database ... 197638 files and directories currently installed.)
Preparing to unpack .../init_1.29ubuntu1_amd64.deb ...
Unpacking init (1.29ubuntu1) over (1.28ubuntu2) ...
Setting up init (1.29ubuntu1) ...
(Reading database ... 197638 files and directories currently installed.)
Preparing to unpack .../x11-common_1%3a7.7+13ubuntu3_all.deb ...
Unpacking x11-common (1:7.7+13ubuntu3) over (1:7.7+13ubuntu1) ...
Preparing to unpack .../xserver-xorg-input-all_1%3a7.7+13ubuntu3_amd64.deb ...
Unpacking xserver-xorg-input-all (1:7.7+13ubuntu3) over (1:7.7+13ubuntu1) ...
Preparing to unpack .../xserver-xorg_1%3a7.7+13ubuntu3_amd64.deb ...
Unpacking xserver-xorg (1:7.7+13ubuntu3) over (1:7.7+13ubuntu1) ...
Preparing to unpack .../xorg_1%3a7.7+13ubuntu3_amd64.deb ...
Unpacking xorg (1:7.7+13ubuntu3) over (1:7.7+13ubuntu1) ...
Preparing to unpack .../xserver-xorg-video-all_1%3a7.7+13ubuntu3_amd64.deb ...
Unpacking xserver-xorg-video-all (1:7.7+13ubuntu3) over (1:7.7+13ubuntu1) ...
Preparing to unpack .../libbabeltrace1_1.3.2-1_amd64.deb ...
Unpacking libbabeltrace1:amd64 (1.3.2-1) over (1.3.1-1build1) ...
Preparing to unpack .../libbabeltrace-ctf1_1.3.2-1_amd64.deb ...
Unpacking libbabeltrace-ctf1:amd64 (1.3.2-1) over (1.3.1-1build1) ...
Processing triggers for systemd (229-2ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.21-0ubuntu6) ...
Setting up x11-common (1:7.7+13ubuntu3) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up xserver-xorg-input-all (1:7.7+13ubuntu3) ...
Setting up xserver-xorg (1:7.7+13ubuntu3) ...
Setting up xorg (1:7.7+13ubuntu3) ...
Setting up xserver-xorg-video-all (1:7.7+13ubuntu3) ...
Setting up libbabeltrace1:amd64 (1.3.2-1) ...
Setting up libbabeltrace-ctf1:amd64 (1.3.2-1) ...
Processing triggers for libc-bin (2.21-0ubuntu6) ...
ventrical@ventrical-MS-7850:~$ 

```

regards..

---

