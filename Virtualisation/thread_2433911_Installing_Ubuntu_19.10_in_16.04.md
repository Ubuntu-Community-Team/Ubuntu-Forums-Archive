---
title: "Installing Ubuntu 19.10 in 16.04"
date: 2019-12-27
forum: Virtualisation
---

### Post by daniell59 on 2019-12-27
I am trying to install Ubuntu 19.04 in 16.04. It wont install past the keyboard layout. You may wonder why I would want to do it. Here is why. I can't install drivers in my Epson scanner on Ubuntu past 16.04. I wanted to see if I could do so in Ubuntu 19.10 64. I think that my resources may be too low.

Thanks for listening.

---

### Post by ajgreeny on 2019-12-27
I am completely baffled by your description of what you're trying to do; you do not and can not install ubuntu 19.10 in Ubuntu 16.04 (nor in any other version), nor is there any sense in trying to upgrade from 16.04 to 19.10 as you can upgrade only from one version to the next, eg, from 19.04 to 19.10, or from one LTS version to the next LTS version, eg, from 16.04 to 18.04.

Rather than upgrading the OS version from 16.04 I recommend that you backup all your personal files and folders (in your home) and then install the version of Ubuntu that you want.  In theory you could upgrade from 16.04 to 18.04 but many users had problems with that, possibly a result of the change from unity to gnome 3 as the DE.

---

### Post by daniell59 on 2019-12-27
[I am completely baffled by your description of what you're trying to do; you do not and can not install ubuntu 19.10 in Ubuntu 16.04 (nor in any other version), nor is there any sense in trying to upgrade from 16.04 to 19.10 as you can upgrade only from one version to the next, eg, from 19.04 to 19.10, or from one LTS version to the next LTS version, eg, from 16.04 to 18.04.



I am new to Virtual box. I was under the impression that another OS could be installed in the host. Please elaborate.

---

### Post by CelticWarrior on 2019-12-27
A virtual machine is not "installing an OS in another".

If you're using Virtualbox then you can create VMs with it and it's very similar to installing in bare metal but there are subtle differences and many considerations, namely whether or not the host machine (not the OS) supports virtualization (BIOS or UEFI settings). 

So, you needd to give details about what you're trying to do. From the firt post we can infer you have a Ubuntu 16.04 host and you want to install a Ubuntu 19.04 guest (VM) which in itself is a bad idea already because the support for 19.04 ends in a few days. 19.10 would be a better idea. Then you need to post your hardware specs and verify whether or not virtualization is enabled. Then please describe the Virtualbox settings you0're trying to use and how are you trying to install.

---

### Post by daniell59 on 2019-12-27
> **CelticWarrior said:**
> A virtual machine is not "installing an OS in another".

If you're using Virtualbox then you can create VMs with it and it's very similar to installing in bare metal but there are subtle differences and many considerations, namely whether or not the host machine (not the OS) supports virtualization (BIOS or UEFI settings). 

So, you needd to give details about what you're trying to do. From the firt post we can infer you have a Ubuntu 16.04 host and you want to install a Ubuntu 19.04 guest (VM) which in itself is a bad idea already because the support for 19.04 ends in a few days. 19.10 would be a better idea. Then you need to post your hardware specs and verify whether or not virtualization is enabled. Then please describe the Virtualbox settings you0're trying to use and how are you trying to install.

I should have said 19.10. I only want it in long enough to determine whether I can get my Epson perfection scanner to be recognized. I have a really old system. ( I am in the process of building a new one)
AMD Athlon 64 X 2 1000MHz
Radeon HD3450 graphics card
4 GIG memory

---

### Post by CelticWarrior on 2019-12-27
CPU supports virtualization -> GOOD
Motherboard may or may not support it though.
**4GB is barely enough for the host system let alone to run a VM (the VM will necessarily use less than half of the RAM)**

Installing a VM to test for old hardware support is a total absurd!!!

OK, first of all, if your old scanner wasn't supported in the version/release you already have then you shouldn't expect it to be supported in a newer release. This makes sense only for hardware that's newer that the release we're running.

And in any case, a VM for that sole purpose is overkiller. You can try a live session instead without making any changes to the installed system.

---

### Post by ajgreeny on 2019-12-27
I did not notice your thread was placed in the Virtualisation forum, so apologies for my misunderstanding.

Tell us what hardware you are using as that may mean we can give you better information about the likelihood of success with Virtualbox, and allow us to give you better advice.
The terminal command ***inxi -Fxz*** will give us a lot of detail about your hardware if you are not totally sure what you are using at present.
You may also find that one of the other less resource-hungry *buntu versions is easier to use and more successful in VBox than Ubuntu itself, eg Xubuntu, Lubuntu, Ubuntu-Mate.

---

### Post by daniell59 on 2019-12-27
Resolution: 1680x1050@59.88hz
           GLX Renderer: AMD RV620 (DRM 2.50.0 / 4.15.0-72-generic, LLVM 6.0.0)
           GLX Version: 3.0 Mesa 18.0.5 Direct Rendering: Yes
Audio:     Card-1 NVIDIA MCP61 High Definition Audio
           driver: snd_hda_intel bus-ID: 00:05.0
           Card-2 Advanced Micro Devices [AMD/ATI] RV620 HDMI Audio [Radeon HD 3450/3470/3550/3570]
           driver: snd_hda_intel bus-ID: 02:00.1
           Sound: Advanced Linux Sound Architecture v: k4.15.0-72-generic
Network:   Card: NVIDIA MCP61 Ethernet
           driver: forcedeth port: ec00 bus-ID: 00:07.0
           IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 410.1GB (10.8% used)
           ID-1: /dev/sda model: WDC_WD1600AAJS size: 160.0GB temp: 30C
           ID-2: /dev/sdb model: ST3250410AS size: 250.1GB temp: 32C
Partition: ID-1: / size: 226G used: 38G (18%) fs: ext4 dev: /dev/sdb1
           ID-2: swap-1 size: 4.29GB used: 0.15GB (4%) fs: swap dev: /dev/sdb5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A gpu: 60.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 196 Uptime: 10:27 Memory: 2482.1/3944.4MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

---

### Post by crip720 on 2019-12-27
First thing to do, is a google search of your scanner make and model plus linux or ubuntu drivers.  Might as well see if drivers are made for it.  Best bet for trying a new ubuntu version is booting from a "live USB" or you have space where you can do a dual boot and install on one of your HDs if you are careful with installing.

---

### Post by daniell59 on 2019-12-28
I should have been clearer. My scanner is detected in Ubuntu 16.04. This is not the case in 18.04. As I previously mentioned, I am building a new system. It will be dual booted with Windows. I want to determine in advance whether the bug in 18.04 had been corrected enabling me to avoid using windows to use my scanner. Epson Perfection V30. I hope that this makes it clearer.

---

### Post by daniell59 on 2019-12-29
I just learned something. I carefully checked the BIOS. There is no mention of virtualization. Does that mean that the motherboard wont support it? In any event, I will soon be building my new system. Thanks to all for your informative assistance.

---

