---
title: "Experiment - Minimum Ubuntu System + Fluxbox = True"
date: 2015-12-30
forum: Ubuntu, Linux and OS Chat
---

### Post by patrikmellq on 2015-12-30
I will try to build a working minimum Ubuntu system with Fluxbox.
 I have a old laptop eeePC that i will experiment with.

 First i do is to download ubuntu-14.04.3-server-i386.iso
 I try to download ubuntu LTS alternate and run the installation from command line, but got errors when i was going to install xorg among other to get system up running, so i use server edition as i had succes with that before installing minimum ubuntu system from scratch.

 Will continue this topic with step by step instruction howto install and configurate the minimum ubuntu system with fluxbox.
 Reason i do this is because i like to experiement and try to solve issues along the way, also pretty cool having a laptop with fluxbox.

 Cheers

---

### Post by patrikmellq on 2015-12-30
Is working :-)

1) install server edition of Ubuntu - follow step by step and when you get alternative to pick server alternative to install you just ignore them and let the boxex be empty and click on Enter to continue the installation - then you install minimum ubuntu system from scratch.

2) installation of the basics to get grhapics running with fluxbox:

To get your ghrapic up running:
```

sudo apt-get install xorg

```

Getting the Fluxbox GUI window-manager:
```

sudo apt-get install fluxbox

```

To get your login window when staring system
```

sudo apt-get install xdm

```

Udate and upgrade system:
```

sudo apt-get update

```

```

sudo apt-get upgrade

```

Now you can reboot system and get minimum Ubuntu system running with Fluxbox:
```

reboot

```

---

### Post by etescartz on 2015-12-30
Hi!
I have an eeePC 1000H Ubuntu server , but I used the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") 32bit ( 32 MB in size) instead. If you go through the expert install , you'll be prompted with an option to detect what hardware you are installing it on and only install the kernel modules that will be needed to make that run. This has a dramatic impact on resources.

Unless you decide to install more packages right from the start, you could just install OpenSSH server packages (from a menu during the installation steps), and you can continue adding on services after first boot.

Screenshot of my server's htop
[https://www.dropbox.com/s/gfie5fcqaspccko/Capture.JPG?dl=0](https://www.dropbox.com/s/gfie5fcqaspccko/Capture.JPG?dl=0)

---

### Post by v3.xx on 2015-12-30
Subscribe :)

---

### Post by howefield on 2015-12-30
Thread moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by patrikmellq on 2015-12-31
> **etescartz said:**
> Hi!
I have an eeePC 1000H Ubuntu server , but I used the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") 32bit ( 32 MB in size) instead. If you go through the expert install , you'll be prompted with an option to detect what hardware you are installing it on and only install the kernel modules that will be needed to make that run. This has a dramatic impact on resources.

Unless you decide to install more packages right from the start, you could just install OpenSSH server packages (from a menu during the installation steps), and you can continue adding on services after first boot.

Screenshot of my server's htop
[https://www.dropbox.com/s/gfie5fcqaspccko/Capture.JPG?dl=0](https://www.dropbox.com/s/gfie5fcqaspccko/Capture.JPG?dl=0)

Hello why would i install OpenSSH server - i ask as i don't understand - i pick no server alternetive because i wanted a clean basic Ubuntu system from scratch - did i do something wrong?

Well now i have install network-manager-gnome and openvpn - this is because i could not find any light network-manager that support openvpn settings.
If some one know light version feel free to tell about it :-)

```

sudo apt-get install network-manager-gnome

```

```

sudo apt-get install network-manager-openvpn

```

Now i start the network-manager from terminal writing ```
 nm-connection-editor 
``` and i need to get a system tray with Fluxbox, will search and learn and get back how to do that, i read that i should add ```
 nm-applet & 
``` in the Fluxbox startup file, but i don't know how you do this, but i will learn and write about it later.

Cheers

---

### Post by sudodus on 2015-12-31
Have a look at this link

[Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

and particularly the chapter [Unmanaged Wired Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

-o-

My experience is that you can get almost the same system when you start from the Ubuntu Server iso file and from the Ubuntu mini.iso.

- An obvious advantage of mini.iso is the size.

Two advantages of the server iso are

- You need not download [many] packages during the installation, so if you intend to use the iso file many times, you download the packages only once.
- You can install in UEFI mode (with the amd64 iso file)

---

