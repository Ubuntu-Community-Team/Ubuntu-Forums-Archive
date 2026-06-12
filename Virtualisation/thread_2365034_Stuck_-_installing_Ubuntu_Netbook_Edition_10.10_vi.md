---
title: "Stuck - installing Ubuntu Netbook Edition 10.10 via Virtual Box on Windows 10"
date: 2017-07-01
forum: Virtualisation
---

### Post by procession on 2017-07-01
Hi all,

I am trying to install *Ubuntu Netbook Edition 10.10* via *Virtual Box* on Windows 10.

I have 2 questions:

**_Question 1_** 

: The install seems to get stuck and the 'forward' buttom won't light up (see below) 

Can anyone offer some pointers on this?

[IMG][[IMG]http://img.photobucket.com/albums/v154/Procession/linux%20photo.jpg[/IMG]]("http://smg.photobucket.com/user/Procession/media/linux%20photo.jpg.html")[/IMG]

[B][U]
Question 2[/U][/B]

I have posted my system specs below and what I need to know is:

- how much ram and virtual hard drive space should I allocate during Virtual Box installation?

- is this (Ubuntu Netbook Edition 10.10) the best version of Ubuntu I can run, given the limited specs that are currently supporting Windows 10 as the host?

  ( I tried installing Zorin 32-bit [which I would prefer] but it didn't like it). 

                      _**SPECS**_

OS Name    Microsoft Windows 10 Home
Version    10.0.14393 Build 14393

Installed Physical Memory (RAM)    4.00 GB
Total Physical Memory    3.90 GB
Available Physical Memory    2.08 GB
Total Virtual Memory    4.59 GB
Available Virtual Memory    2.11 GB
Page File Space    704 MB

Processor    Intel(R) Atom(TM) x5-Z8350  CPU @ 1.44GHz, 1441 Mhz, 4 Core(s), 4 Logical Processor(s)

System Name    DESKTOP-G2SBGTR
System Manufacturer    HP
System Model    HP x2 Detachable 10-p0XX
System Type    x64-based PC
System SKU    Z1E03PA#ABG

BIOS Version/Date    American Megatrends Inc. F.11, 30/09/2016
SMBIOS Version    3.0
Embedded Controller Version    93.22
BIOS Mode    UEFI
BaseBoard Manufacturer    HP
BaseBoard Model    Not Available
BaseBoard Name    Base Board
Platform Role    Mobile
Secure Boot State    On
PCR7 Configuration    Elevation Required to View
Windows Directory    C:\windows
System Directory    C:\windows\system32
Boot Device    \Device\HarddiskVolume1
Locale    Australia
Hardware Abstraction Layer    Version = "10.0.14393.206"
Time Zone    AUS Eastern Standard Time

Page File    C:\pagefile.sys
Hyper-V - VM Monitor Mode Extensions    Yes
Hyper-V - Second Level Address Translation Extensions    Yes
Hyper-V - Virtualization Enabled in Firmware    No
Hyper-V - Data Execution Protection    Yes


Thank-you all in advance :)

---

### Post by howefield on 2017-07-01
If you click on the "arrow" button to the left of the getting the time ect.. message you may get more of a clue as to where the install is stuck. Even so, 10.10 is hopelessly outdated and no longer supported, probably a poor choice even for a virtual machine.

I'd suggesting trying something like Lubuntu and give it one meg of ram but it could weel be that the machine is just too weak to run VMs decently.

---

### Post by lammert-nijhof on 2017-07-01
I run the netbook version 10.04 (32 bits) in a virtual machine since many many years and I don't remember any problems with the installation. 10.04 is a LTS (Long Term Support) release which has been updated for many years, so that version should be more reliable then 10.10. I run that version with 448 MB of memory and in the past (2012?) even In a Virtual Machine on a Pentium 4 (3.0MHz) and on a dual core AMD 64 (1.8MHz) both with a whopping total of 2GB of memory. So don't worry, you can run a Virtual Machine on your PC, I did it on an old Pentium and AMD and both machines did NOT support virtualization in hardware/firmware. The limitation is that you can only use 32 bits Operating Systems in the VM.

I see the next output in your post: "Hyper-V - Virtualization Enabled in Firmware    No". It looks like you did not enable virtualization in the Bios of your PC, I would go into the Bios and enable virtualization support. It will probably not solve you problem with Ubuntu Netbook 10.10, but it will improve the performance of any VM you create.

If you want to try a more modern version of Linux in Virtualbox, I would suggest Peppermint 8 (the sexy sister of Lubuntu), which would run easily in e.g 784MB or Ubuntu Mate or Linux Mint Cinnamon, which I run in 1GB.

So to conclude:
1. Enable virtualization in your Bios/Firmware
2. Try the Ubuntu Netbook 10.04, since it is more reliable or another Linux distro.

---

### Post by oldfred on 2017-07-01
Please use a current release.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Old releases are not supported, and often newer ones do work better.
I had a 2006 laptop with 1.5GB of RAM and 12.04. It could not run Unity (way slow), so I installed fallback/flashback. But I recently tested an install of 16.04 and even Unity ran ok, not speedy, but usable. 

Also suggest installing Lubuntu.
[https://wiki.ubuntu.com/Lubuntuhttps://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Lubuntu")

Other flavors:
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
       Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie

---

### Post by gordintoronto on 2017-07-02
Agreed, stay away from 10.04.

I am running Ubuntu Mate 16.04 on a real old netbook with 1 GB of RAM, and it's OK. I use the computer as a file server, and have also used it as a remote camera. These machines go for $25 on eBay, and a "Wi-Fi camera" costs significantly more.

---

### Post by uRock on 2017-07-02
> **gordintoronto said:**
> Agreed, stay away from 10.04.

I am running Ubuntu Mate 16.04 on a real old netbook with 1 GB of RAM, and it's OK. I use the computer as a file server, and have also used it as a remote camera. These machines go for $25 on eBay, and a "Wi-Fi camera" costs significantly more.
My Netbook is being used as a Motion camera server. It has the built in cam and a USB. The USB is in the window so we can see out front. 
Everyone in the house has the feed as their home page so we can see who's knocking at the door.
I plan to set up Apache on it and create a home page to which we can log in from the Internet.

As for the OP. Install a VM with Xubuntu. I have installed it with only 512k RAM and it ran fine. The drive space only needs to be 8GB, but 12GB is better if you plan to install a lot of software.

---

