---
title: "Howto VirtualBox 2.1 in Ubuntu 8.10"
date: 2008-12-18
forum: Virtualisation
---

### Post by nhasian on 2008-12-18
Sun just released a major update to Virtualbox with version 2.1.  New features include:

[LIST]
[*]Support for 64-bit guests on 32-bit host operating systems. (experimental)
[*]3D acceleration via OpenGL (experimental)
[*]New Host Interface Networking implementations for Windows and Linux hosts. (replaces TUN/TAP on Linux and manual bridging on Windows)
[*]New NAT engine with signi&#64257;cantly better performance, reliability and ICMP echo (ping) support
[*]Full VMDK/VHD support including snapshots
[/LIST]

Even if you previously added virtualbox's software repository it will not upgrade you to 2.1 as it is a different package altogether.  If you havent done so yet, add the Virtualbox Repo to your */etc/apt/sources.list*

```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```

remove your old installation of virtualbox 2.0 (depending on which version you installed) with:

```
sudo apt-get remove virtualbox-ose
```

or 

```
sudo apt-get remove virtualbox-2.0
```

update your package index files from their sources:

```
sudo apt-get update
```

then finally install the new virtualbox-2.1 package:

```
sudo apt-get install virtualbox-2.1
```

---

### Post by HotShotDJ on 2008-12-18
Just some additions to this HowTo:

Replace "remove" with "autoremove"  (otherwise some cruft will be left behind -- not much, but some)

I also added --purge to the autoremove lines.  Probably not necessary, but worked for me.

When you first start up your shiny new VirtualBox 2.1, it will ask you if you want it to back up your original configuration.  Answer YES!  If you don't, you will NOT be able to easily return to an earlier version.

Better yet, back up your ~/.VirtualBox folder(s) to another location for additional insurance.

In the end, I didn't need the backed up configuration or the backed up folders.  But it is always good to have "Just In Case"

---

### Post by binbash on 2008-12-18
if you are using virtualbox-2.0 you can remove it (not purge), and install the deb manually.

---

### Post by chris.pappas on 2008-12-22
Installation instructions for VirtualBox 2.1 can be also found at:
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

In a nutshell:
Add this line (choosing your Ubuntu variant appropriately) to your /etc/apt/sources.list:
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free (if you're using a different Ubuntu release, replace intrepid with its name (eg. hardy, gutsy)

Add the Sun public key to sign the repository:
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

Update your repositories:
sudo apt-get update

Install dkms (to make sure the kernel modules are kept up-to-date) and VirtualBox:
sudo apt-get install dkms virtualbox-2.1

Make sure you compile the kernel module when it prompts you, and enjoy a great virtualization product.

---

### Post by eshant_engineer on 2009-01-01
is it free or not?

---

### Post by HotShotDJ on 2009-01-01
> **eshant_engineer said:**
> is it free or not?That depends on what you mean by "free."   The PUEL version is "gratis" (free of charge -- for personal use) but it is not "libre" (free of restrictions).  See the PUEL License for more detail -- [http://www.virtualbox.org/wiki/VirtualBox_PUEL](http://www.virtualbox.org/wiki/VirtualBox_PUEL)

---

### Post by 67GTA on 2009-01-02
I recently upgraded from 2.0.6 to 2.1.0. For some reason CD/DVD's won't load in Virtualbox now. When I set up a new VM and start it, it always says Fatal, No medium found. All the settings are correct. Anyone else having trouble?

---

### Post by MystaMax on 2009-01-03
> **67GTA said:**
> I recently upgraded from 2.0.6 to 2.1.0. For some reason CD/DVD's won't load in Virtualbox now. When I set up a new VM and start it, it always says Fatal, No medium found. All the settings are correct. Anyone else having trouble?

I think your issues maybe similar to mine and others over @ [virtualbox.org forums]("http://forums.virtualbox.org/viewtopic.php?p=51273"). After upgrading to 2.1, the cd/dvd passthrough option no longer works. If enabled, the drive never shows up in my XP VM. If disabled, it shows up, but only as a cd-rom drive. In 2.0, I was using the passthrough feature to rip certain DVDs.

There is also a [ticket]("http://www.virtualbox.org/ticket/2795") open w/ Virtualbox regarding this issue.

---

