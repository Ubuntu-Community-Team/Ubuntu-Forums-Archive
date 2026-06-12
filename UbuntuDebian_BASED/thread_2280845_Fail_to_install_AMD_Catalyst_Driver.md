---
title: "Fail to install AMD Catalyst Driver"
date: 2015-06-02
forum: Ubuntu/Debian BASED
---

### Post by nicolas40 on 2015-06-02
So, I am having a lot of video tearing in my computer, even when I just drag a window around.
So I thought I would install a AMD graphics card driver so it would stop, but after uninstalling previous drivers and running the installer I got a message saying that it had a problem while installing and generated the following log:

```

Supported adapter detected.
Check if system has the tools required for installation.
Uninstalling any previously installed drivers.


Creating symlink /var/lib/dkms/fglrx/14.20/source ->
                 /usr/src/fglrx-14.20


DKMS: add completed.


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/14.20/build; sh make.sh --nohints --uname_r=3.16.0-38-generic --norootcheck......(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-14.20 with DKMS
[Error] Kernel Module : Removing fglrx-14.20 from DKMS


------------------------------
Deleting module version: 14.20
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs
```



I'm running on a notebook with ElementaryOS(based on Ubuntu)
Processor: Quad-Core AMD A8-3520M APU with Radeon(tm) HD Graphics
Graphics Card: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6620G]                         Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M] (rev ff)

I have just started using Linux, and this constant video tearing is very annoying. If someone could help me, it'd be awesome.

---

### Post by QIII on 2015-06-02
What was the "previous driver"?

How did you install fglrx?

---

### Post by nicolas40 on 2015-06-03
I had installed other AMD Driver but it didnt solve anything, so I uninstalled it with these commands:
sudo apt-get purge "fglrx.*"
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
sudo dpkg-reconfigure xserver-xorg
sudo rebootAnd then I followed this video to install the new driver (which I downloaded from the AMD site):
[https://www.youtube.com/watch?v=evqpassbyqA](https://www.youtube.com/watch?v=evqpassbyqA)

And during the installation it gave me that problem.

---

### Post by QIII on 2015-06-03
I would recommend that you attempt to uninstall that partially installed driver if you can.

Then, if you can, reinstall from your repo.  I don't know how that is done in Elementary.

I suspect your issue had more to do with your settings in Catalyst Control Center than the driver itself.

---

### Post by kryten35 on 2015-06-03
To install driver i would
1-  [http://support.amd.com](http://support.amd.com)  enter card details and download recommended driver. Unzip to a   .run script  but dont try to install.

2-download dependencies
```
sudo apt-get install dh-make dh-modaliases execstack libc6-i386 lib32gccl
```

3-run the driver installer
```
sudo sh ./put full name of .run script here from step 1.
```
the .run script will look something like   amd-driver-installer-12.23.1002-x86_64.run.

Just in case you didnt use exactly the same method.Cant watch Youtube at moment.Browser problem with video playback.
I think theres a tearing option in the catalyst control centre.

---

