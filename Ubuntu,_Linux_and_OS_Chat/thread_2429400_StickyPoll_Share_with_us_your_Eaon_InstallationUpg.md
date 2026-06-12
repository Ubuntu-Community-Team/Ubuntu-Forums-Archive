---
title: "Sticky:Poll: Share with us your Eaon Installation/Upgrade experience:"
date: 2019-10-17
forum: Ubuntu, Linux and OS Chat
---

### Post by cariboo on 2019-10-17
Eaon Ermine was released October 17 2019, so it's time for a new poll. Please tell us about your experience upgrading, or doing a fresh install of Eaon.

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

The previous poll can be found here:

[https://ubuntuforums.org/showthread.php?t=2417102](https://ubuntuforums.org/showthread.php?t=2417102)

---

### Post by uRock on 2019-10-17
In before, well, before anyone else.

I upgraded one Xubuntu machine from 19.04 to 19.10 and it went well.
```
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 19.10
Release:	19.10
Codename:	eoan

```
```
:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation HM55 Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [GeForce 310M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev ff)
03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)

```

---

### Post by deadflowr on 2019-10-22
Did the upgrade from 19.04 today.
Mostly good, no serious issues.
But have a few broken extensions to deal with.
Nothing major that inhibits the experience.

---

### Post by Frogs Hair on 2019-10-22
Been using/updating the same Budgie daily build since July and have had no reason to perform a clean installation of the final release.

---

### Post by cellsite60 on 2019-10-22
Made a clean install just a few moments ago, worked pretty much the way i expected it to work, very well!

---

### Post by wildmanne39 on 2019-10-22
The installer did not recognize my hard drive, I disabled the optane memory then I was able to install Ubuntu Mate 19.10, it is running very smooth.

---

### Post by Irihapeti on 2019-10-22
I did multiple installs (of Ubuntu plus various flavours) during final testing. The majority installed without issue. I think I had one or maybe two show-stopper bugs, but these were sorted before release.

---

### Post by C.S.Cameron on 2019-10-22
Had some problems with screenshots, (prt sc). on HP EliteBook 8560W.

Anybody else have problem with screenshots?

Edit:
Seems to be sorted out now.

---

### Post by zimbuf on 2019-10-22
Install went flawlessly, only impediment was the 32 bit removal which - apparently isn't configured correctly? dpkg has multiarch-support enabled, but will not report it to .deb files no matter what you do. Crossover Linux is one example. Had to install wine-staging instead and install dxvk via apt... which is also broken and does nothing because the script is symlinked to /usr/bin, but the script runs expecting the dxvk binaries to be in the current working directory.

I had to grab the dxvk script and binaries from the releases on github and install them manually as well. The power button on the login screen is also broken, and doesn't restart nor power off.

But aside from that, no other issues from fresh install.

---

### Post by uRock on 2019-10-23
Just did a fresh install on the laptop I had previously upgraded on. I need Advil to recover. The installer installed nvidia-340 which doesn't work. I tried nomodeset, then rebooted and was no longer able to get to Ctrl+Alt+F1, so I had to reinstall, again. This time I installed openssh-server and remotely removed the nvidia-340 package, then rebooted and have a desktop again. Everything else with Xubuntu is rocking.

@C.S.Cameron I am able to do screenshots using the print screen key.

---

### Post by deadflowr on 2019-10-23
In Ubuntu with unity screenshots work and give the save dialog option.
In Ubuntu with gnome-shell screenshots work, but no save dialog option. It just saves them straight into Pictures.
But all keybindings work for both (alt+prtscn, shift + prtscn work as expected for window and area selection)

---

### Post by Dennis N on 2019-11-08
I upgraded my Ubuntu 19.04 virtual machine to 19.10 by cloning it first (thus keeping the original 19.04 vm in case something failed), then upgrading the clone with Software Updater. One precaution: I disabled all extensions before upgrading to avoid possible problems, since they don't automatically upgrade. From what I see so far, the upgrade was entirely successful. The only change I had to make post install was to install and use a different gnome-shell theme.

Current:

```
dmn@Sydney-vm:~$ neofetch
            .-/+oossssoo+/-.               dmn@Sydney-vm 
        `:+ssssssssssssssssss+:`           ------------- 
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 19.10 x86_64 
    .ossssssssssssssssssdMMMNysssso.       Host: KVM/QEMU (Standard PC (Q35 + ICH9, 2009) pc-q35-3.1) 
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Kernel: 5.3.0-26-generic 
  +ssssssssshmydMMMMMMMNddddyssssssss+     Uptime: 24 mins 
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Packages: 1795 (dpkg), 8 (flatpak), 12 (snap) 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Shell: bash 5.0.3 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Resolution: 1920x1080 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   DE: GNOME 3.34.1 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM: GNOME Shell 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   WM Theme: Adwaita 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Theme: Zukitwo [GTK2/3] 
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/    Icons: Qogir-ubuntu [GTK2/3] 
  +sssssssssdmydMMMMMMMMddddyssssssss+     Terminal: gnome-terminal 
   /ssssssssssshdmNNNNmyNMMMMhssssss/      CPU: Intel (Haswell, no TSX, IBRS) (2) @ 3.491GHz 
    .ossssssssssssssssssdMMMNysssso.       GPU: Red Hat, Inc. Virtio GPU 
      -+sssssssssssssssssyyyssss+-         Memory: 1327MiB / 3936MiB 
        `:+ssssssssssssssssss+:`
            .-/+oossssoo+/-.
```

---

### Post by bernard010 on 2019-11-27
New install of Eoan 19.10 Ubuntu Gnome 64bit. . Went OK on install except the Plymouth animated Bootloader. . Messed with it for a while, uninstalled the bootloader. I Boot with a blank screen. . Works fabulous other than that.

---

### Post by The Cog on 2019-11-28
Clean OS install of Xubuntu 19.10, then edited fstab to mount my proper home partition which has lasted many new OS versions.
Perfect except for Chromium which lost its stored passwords and couldn't save new ones. But I had been thinking of switching to Firefox anyway so not a biggie.

---

