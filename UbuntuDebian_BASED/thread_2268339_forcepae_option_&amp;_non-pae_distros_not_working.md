---
title: "forcepae option &amp; non-pae distros not working"
date: 2015-03-08
forum: Ubuntu/Debian BASED
---

### Post by andfree on 2015-03-08
I have a Toshiba Satellite L10-194 with &#65279;Intel Pentium M 1.7 Ghz processor.

I boot from cd or usb (by using plop-boot-manager) trying to install various distros with no success.

1)
When I try to install 14.10 distros, I get the message:

“&#65279;Missing parameter in configuration file. Keyword: path gfxboot.c32: not a COM32R image boot:”

Then I print “help” and press “enter” twice and I get the message:

“&#65279;Unable to boot - please use a kernel appropriate for your CPU”.

2)
When I try to install 14.04 distros and, before get the message 

&#65279;“WARNING: PAE disabled. Use parameter ‘forcepae’ to enable at your own risk! (...) This kernel requires the following features not present on the CPU: pae.”,

I press “tab”, then I am at &#65279;the boot menu screen. &#65279;I add 'forcepae' to the string before and after the two dashes ("forcepae -- forcepae"), press “enter” and then I am at the trial Desktop with the “Install ubuntu” icon on it. I double-click on it, the cursor spins for a while, but nothing happens.

3)
When I try to install LXLE 32-bit Revisited alias 12.04.5 I get the message:

&#65279;"The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again."

4)
When I try to install Bodhi Linux, boot menu page gets stuck and some black dots appear at the top of it.

5)
I installed nOS, but menu bars and icons are missing.

6)
I installed toriOS, but login (root, 123456) fails.

Any ideas what to do after all?

---

### Post by grahammechanical on 2015-03-08
1) 
> [COLOR=#000000]&#8220;&#65279;Unable to boot - please use a kernel appropriate for your CPU&#8221;.[/COLOR]

That could  indicate that you are running a 64 Bit operating system on a 32 bit CPU and that is not going to work.

2)

> [COLOR=#000000]I press &#8220;tab&#8221;, then I am at &#65279;the boot menu screen. &#65279;I add 'forcepae' to the string before and after the two dashes ("forcepae -- forcepae"), press &#8220;enter&#8221; and then I am at the trial Desktop[/COLOR]

So, using that 2 x forcepae gets you to a working live session. That is progress. And it shows that you need that double forcepae boot parameter. Your other attempts show that Linux has other issues with that hardware. The question is, which one of those Linux distributions do you want help with?

Decide which distribution you want to go with and work through the problems that come up. As general advice I offer this. Do not install a proprietary video driver during installation. In Ubuntu live sessions run with an open source video driver. So, if the live session works fine but the installed session does not load to a desktop or loads to a desktop without menu bars and icons it could indicate a problem with the proprietary video driver no longer supporting that video card.

Regards.

---

### Post by andfree on 2015-03-08
Grahammechanical, thank you very much for your help.

1)

> **grahammechanical said:**
> 
That could  indicate that you are running a 64 Bit operating system on a 32 bit CPU and that is not going to work.

I tried ubuntu / lubuntu / xubuntu-14.10-desktop-i386.iso & lubuntu-14.10-alternate-i386.iso, all supposed to be appropriate for 32 bit CPU.


2)

> **grahammechanical said:**
> 
So, using that 2 x forcepae gets you to a working live session. That is progress. And it shows that you need that double forcepae boot parameter. Your other attempts show that Linux has other issues with that hardware. The question is, which one of those Linux distributions do you want help with?

Decide which distribution you want to go with and work through the problems that come up. As general advice I offer this. Do not install a proprietary video driver during installation. In Ubuntu live sessions run with an open source video driver. So, if the live session works fine but the installed session does not load to a desktop or loads to a desktop without menu bars and icons it could indicate a problem with the proprietary video driver no longer supporting that video card.

Regards.

Live session seems to work fine for 14.04.2 distros, but the installation doesn’t start at all. The cursor spins for a while, then stops, nothing.

nOS is installed, but menu bars and icons are missing in both live and installed session.

I’m afraid I have not the chance for a choice. I look for something working, whatever it is. Any help with any distro is welcome.

Thanks very much again.

---

### Post by andfree on 2015-03-09
Some corrections:

ToriOS installed and logged-in, but then there is no internet connection (no ethernet connection, "no wireless network found").

NOS live session doesn't work at all (black screen with a movable curson doing nothing).

I tried also ubuntu 15.04. Same result as 14.10 distros.

Do you think I should start a new thread for every distro? I preferred a thread for all, because it's about the same laptop (and the same CPU).

---

### Post by sudodus on 2015-03-09
Welcome to the Ubuntu Forums :-)

> **andfree said:**
> I have a Toshiba Satellite L10-194 with &#65279;Intel Pentium M 1.7 Ghz processor.

I boot from cd or usb (by using plop-boot-manager) trying to install various distros with no success.

1)
When I try to install 14.10 distros, I get the message:

&#8220;&#65279;Missing parameter in configuration file. Keyword: path gfxboot.c32: not a COM32R image boot:&#8221;

Then I print &#8220;help&#8221; and press &#8220;enter&#8221; twice and I get the message:

&#8220;&#65279;Unable to boot - please use a kernel appropriate for your CPU&#8221;.

This is a known bug affecting some tools to flash the iso file to a pendrive. Use [mkusb]("https://help.ubuntu.com/community/mkusb") in linux and [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows.
> 
2)
When I try to install 14.04 distros and, before get the message 

&#65279;&#8220;WARNING: PAE disabled. Use parameter &#8216;forcepae&#8217; to enable at your own risk! (...) This kernel requires the following features not present on the CPU: pae.&#8221;,

I press &#8220;tab&#8221;, then I am at &#65279;the boot menu screen. &#65279;I add 'forcepae' to the string before and after the two dashes ("forcepae -- forcepae"), press &#8220;enter&#8221; and then I am at the trial Desktop with the &#8220;Install ubuntu&#8221; icon on it. I double-click on it, the cursor spins for a while, but nothing happens.

When the live session works, there is hope :-)

***Maybe you have too little RAM***. ***Lubuntu*** needs at least 512 MB RAM for the desktop installer to work well. The Lubuntu alternate installer can do with less RAM. But the installed system will not work really well with less than 1 GB RAM, for example modern web-sites need more RAM, than was delivered in old computers. Other Ubuntu flavours, for example Xubuntu, need at least 1 GB RAM.

See this link for more details [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)
> 
3)
When I try to install LXLE 32-bit Revisited alias 12.04.5 I get the message:

&#65279;"The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again."

It might be problems with low RAM also in this case.
> 
4)
When I try to install Bodhi Linux, boot menu page gets stuck and some black dots appear at the top of it.

Bodhi is often a good alternative. Maybe you have problems with a driver for the graphics or wifi.
> 

5)
I installed nOS, but menu bars and icons are missing.
I don't know nOS> 
6)
I installed toriOS, but login (root, 123456) fails.

It is a bad idea to create a user with the name root, because it is reserved for administrative tasks. In the installed system you should use sudo to elevate permissions for system tasks (and gksudo for GUI application programs).

If you use network-manager, you should be able to connect with ToriOS. Try first via wired internet. Maybe you need a proprietary driver for wifi.
> 
Any ideas what to do after all?

> **andfree said:**
> Grahammechanical, thank you very much for your help.

1)

I tried ubuntu / lubuntu / xubuntu-14.10-desktop-i386.iso & lubuntu-14.10-alternate-i386.iso, all supposed to be appropriate for 32 bit CPU.

This is correct :-)
> 

2)

Live session seems to work fine for 14.04.2 distros, but the installation doesn&#8217;t start at all. The cursor spins for a while, then stops, nothing.

nOS is installed, but menu bars and icons are missing in both live and installed session.

I&#8217;m afraid I have not the chance for a choice. I look for something working, whatever it is. Any help with any distro is welcome.


You might need a lighter distro. ***ToriOS*** is a good alternative, or should i say, will be, because it is still in development. The beta version will be released soon, so you must have patience with some things, that don't work yet. I think it will work well, when the official version is released.

There are other ultra-light linux distros, that might work well for you: ***Wary Puppy***, ***TahrPup*** and ***Tiny Core***.
> 

Thanks very much again.

> **andfree said:**
> Some corrections:

ToriOS installed and logged-in, but then there is no internet connection (no ethernet connection, "no wireless network found").

NOS live session doesn't work at all (black screen with a movable curson doing nothing).

I tried also ubuntu 15.04. Same result as 14.10 distros.

Do you think I should start a new thread for every distro? I preferred a thread for all, because it's about the same laptop (and the same CPU).

I think we can discuss your problems, suggest and test various solutions in this thread :-)

Finally, please read the following threads

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

                          [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
[/URL]

*Edit*: Maybe you can find (used alias second-hand) RAM from another old computer or buy it via the internet, to increase the RAM in your computer to at least 1 GB.

---

### Post by andfree on 2015-03-09
Thank you very very much, sudodus.

I' ll try all of your advice, but some comments for the while:

> **sudodus said:**
> ***Maybe you have too little RAM***. ***Lubuntu*** needs at least 512 MB RAM for the desktop installer to work well. The Lubuntu alternate installer can do with less RAM. But the installed system will not work really well with less than 1 GB RAM, for example modern web-sites need more RAM, than was delivered in old computers. Other Ubuntu flavours, for example Xubuntu, need at least 1 GB RAM.

> **sudodus said:**
> It might be problems with low RAM also in this case.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
[/URL]> **sudodus said:**
> Maybe you can find (used alias second-hand) RAM from another old computer or buy it via the internet, to increase the RAM in your computer to at least 1 GB.

I have already increased the RAM to 1 GB.

> **sudodus said:**
> If you use network-manager, you should be able to connect with ToriOS.  Try first via wired internet. Maybe you need a proprietary driver for  wifi.

I open Wicd Network Manager, choose "Create an ad-hoc network", click a tick at "Activate Internet Connection Sharing" and click "OK". Nothing happens, get same messages after & before: "Not connected" & "No wireless networks found".

Thanks again.

---

### Post by sudodus on 2015-03-09
1 GB RAM is plenty for Lubuntu and Xubuntu. There is some other problem. Did you check with ***md5sum*** that the download was good?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Have you got a wired connection to the internet? Wicd is very light-weight, so it is selected for ToriOS, and it gives me wired connection most of the time. It works but it is hard to use. I prefer to install the package ***network-manager***

```
sudo apt-get install network-manager
```

which installs the program ***NetworkManager*** (/usr/sbin/NetworkManager). I find it easier to use. With 1 GB RAM it should be no problem.

Maybe you should uninstall wicd to make it work properly (without the two programs competing with each other), I'm not sure but think it might be a good idea.

```
sudo apt-get remove wicd
```

You might have problems with the wifi driver too. What wifi chip/card is it?

If necessary, you can tweak it according to the following link

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)[URL="https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network"]
[/URL]
*Edit*: network-manager seems to be installed already in the current version of ToriOS.

---

### Post by sudodus on 2015-03-09
Which version of ToriOS are you trying? The current version has the following md5sum

```
md5sum ToriOS-beta.iso
90762dc126d59da37ce9155577d56d70  ToriOS-beta.iso
```

---

### Post by andfree on 2015-03-09
> **sudodus said:**
> This is a known bug affecting some tools to flash the iso file to a pendrive. Use [mkusb]("https://help.ubuntu.com/community/mkusb") in linux and [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows.

Thank you very much for this. Lubuntu 14.10 is now installed. But after updating, doesn’t reboot, doesn’t shutdown, see all time the Lubuntu logo. I open tty1 terminal and asks for login, but I can write nothing. There are a lot of references about problems like this, but still haven’t find solution.

---

### Post by andfree on 2015-03-09
> **sudodus said:**
> 1 GB RAM is plenty for Lubuntu and Xubuntu. There is some other problem. Did you check with ***md5sum*** that the download was good?

I checked the hashes for:

lubuntu-14.04.2-desktop-i386.iso
xubuntu-14.04.2-desktop-i386.iso
xubuntu-14.10-desktop-i386.iso
ubuntu-14.04.2-desktop-i386.iso
ubuntu-14.10-desktop-i386.iso

All hashes seem to be OK, but I have the same problem with all of them: live session works fine but they don't be installed.

> **sudodus said:**
> Which version of ToriOS are you trying? The current version has the following md5sum

     ```
md5sum ToriOS-beta.iso 90762dc126d59da37ce9155577d56d70  ToriOS-beta.iso
```



I was trying ToriOS-alpha-rc2.iso. Now I downloaded ToriOS-beta.iso. But there's something I don't understand. Hashes seem to change. First I got d41d8cd98f00b204e9800998ecf8427e for ToriOS-alpha-rc2.iso & ToriOS-beta.iso too. Then I renamed ToriOS-beta.iso to ToriOS-beta2.iso and got 90762dc126d59da37ce9155577d56d70. I renamed it again to ToriOS-beta.iso but hash remained the same. Finally ToriOS-alpha-rc2.iso got 6775c77be242e6145552eeed9b6e85a7.


 ```
~/Downloads$ md5sum lubuntu-14.04.2-desktop-i386.iso
aab1b7817c7994e2f9a6fc5f90c609bd  lubuntu-14.04.2-desktop-i386.iso
~/Downloads$ md5sum xubuntu-14.04.2-desktop-i386.iso
b840066af2797fa8c973d99110c64c91  xubuntu-14.04.2-desktop-i386.iso
~/Downloads$ md5sum xubuntu-14.10-desktop-i386.iso
f30586a06391d0fb69482eada40614af  xubuntu-14.10-desktop-i386.iso
~/Downloads$ md5sum ubuntu-14.04.2-desktop-i386.iso
a8a14f1f92c1ef35dae4966a2ae1a264  ubuntu-14.04.2-desktop-i386.iso
~/Downloads$ md5sum ubuntu-14.10-desktop-i386.iso
4a3c4b8421af51c29c84fb6f4b3fe109  ubuntu-14.10-desktop-i386.iso
~/Downloads$ md5sum wary-5.5.iso
3763175a51a6428aaf2bb28de868b00b  wary-5.5.iso
~/Downloads$ md5sum ToriOS-alpha-rc2.iso
d41d8cd98f00b204e9800998ecf8427e  ToriOS-alpha-rc2.iso
~/Downloads$ md5sum ToriOS-beta.iso
d41d8cd98f00b204e9800998ecf8427e  ToriOS-beta.iso
~/Downloads$ ToriOS-beta2.iso
ToriOS-beta2.iso: command not found
~/Downloads$ md5sum ToriOS-beta2.iso
90762dc126d59da37ce9155577d56d70  ToriOS-beta2.iso
~/Downloads$ md5sum ToriOS-beta.iso
90762dc126d59da37ce9155577d56d70  ToriOS-beta.iso
~/Downloads$ md5sum ToriOS-alpha-rc2.iso
6775c77be242e6145552eeed9b6e85a7  ToriOS-alpha-rc2.iso
~/Downloads$ md5sum ToriOS-alpha-rc2.iso
6775c77be242e6145552eeed9b6e85a7  ToriOS-alpha-rc2.iso

```

---

### Post by sudodus on 2015-03-09
> **andfree said:**
> I checked the hashes for:

lubuntu-14.04.2-desktop-i386.iso
xubuntu-14.04.2-desktop-i386.iso
xubuntu-14.10-desktop-i386.iso
ubuntu-14.04.2-desktop-i386.iso
ubuntu-14.10-desktop-i386.iso

All hashes seem to be OK, but I have the same problem with all of them: live session works fine but they don't be installed.

I was trying ToriOS-alpha-rc2.iso. Now I downloaded ToriOS-beta.iso. But there's something I don't understand. Hashes seem to change. First I got d41d8cd98f00b204e9800998ecf8427e for ToriOS-alpha-rc2.iso & ToriOS-beta.iso too. Then I renamed ToriOS-beta.iso to ToriOS-beta2.iso and got 90762dc126d59da37ce9155577d56d70. I renamed it again to ToriOS-beta.iso but hash remained the same. Finally ToriOS-alpha-rc2.iso got 6775c77be242e6145552eeed9b6e85a7.

 ```
~/Downloads$ ...
...
~/Downloads$ md5sum ToriOS-beta2.iso
90762dc126d59da37ce9155577d56d70  ToriOS-beta2.iso
~/Downloads$ md5sum ToriOS-beta.iso
[COLOR=#ff0000]90762dc126d59da37ce9155577d56d70  ToriOS-beta.iso[/COLOR]
~/Downloads$ md5sum ToriOS-alpha-rc2.iso
6775c77be242e6145552eeed9b6e85a7  ToriOS-alpha-rc2.iso
~/Downloads$ md5sum ToriOS-alpha-rc2.iso
6775c77be242e6145552eeed9b6e85a7  ToriOS-alpha-rc2.iso

```

This is the current ToriOS file, that you should try.

```
90762dc126d59da37ce9155577d56d70  ToriOS-beta.iso
```

When the live session works but not the installed one, I'm rather sure that it is a problem with a driver. You might have problems with the driver for the graphics or wifi.

Please specify at least your

- graphics chip/card
- wifi chip/card

You can use the command line tool ***lshw*** like this:

```
sudo -s
lshw -sanitize > lshw.txt
exit   # exit from the superuser environment
```

and post the content of the file lshw.txt within code tags in a reply.

---

### Post by andfree on 2015-03-09
> **sudodus said:**
> When the live session works but not the installed one, I'm rather sure that it is a problem with a driver. You might have problems with the driver for the graphics or wifi.

Please specify at least your

- graphics chip/card
- wifi chip/card

You can use the command line tool ***lshw*** like this:

```
sudo -s
lshw -sanitize > lshw.txt
exit   # exit from the superuser environment
```

and post the content of the file lshw.txt within code tags in a reply.

```
computer
    description: Notebook
    product: Satellite L10
    vendor: TOSHIBA
    version: PSL10E-021011GE
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Satellite L10
       vendor: TOSHIBA
       physical id: 0
       version: Rev 1.0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V2.40
          date: 06/22/2005
          size: 107KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: uFCPGA2
          size: 1700MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM 0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:6 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:6 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:6 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:10 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e04fffff memory:40000000-43ffffff
           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:10 memory:e0400000-e0400fff ioport:3000(size=256) ioport:3400(size=256) memory:40000000-43ffffff memory:e4000000-e7ffffff
           *-network:0
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:6 ioport:3800(size=256) memory:e0402000-e04020ff
           *-network:1 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:11 memory:e0401000-e0401fff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:6 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:44000000-440003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1860(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:11 ioport:1c00(size=256) ioport:1880(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK6025GA
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0U
             serial: [REMOVED]
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=44d92a24
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 54GiB
                capacity: 54GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-03-09 14:20:20 filesystem=ext4 lastmountpoint=/ modified=2015-03-09 23:24:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-03-09 23:24:50 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1005MiB
                capacity: 1005MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1005MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ-831S
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /media/popi/Plop Boot Manager 5.0.14
             version: 1.90
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/popi/Plop Boot Manager 5.0.14
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
     *-scsi:2
          physical id: 3
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 3695MiB (3874MB)
             configuration: sectorsize=512 signature=8852edcf
  *-battery
       description: Lithium Ion Battery
       product: Sanyo
       vendor: Sanyo
       physical id: 1
       slot: Right Side
       capacity: 4400mWh
       configuration: voltage=14.8V
```

---

### Post by andfree on 2015-03-09
> **sudodus said:**
> This is the current ToriOS file, that you should try.

```
90762dc126d59da37ce9155577d56d70  ToriOS-beta.iso
```



Ok, the wired internet works, but doesn't look very handy to me. I also can't find some functions. I can't copy-paste text from webpages. Right-click on marked text does nothing, "Ctrl + C" closes the browser.

---

### Post by sudodus on 2015-03-10
```
        *-display:0
             description: VGA compatible controller
             [COLOR=#ff0000]product: 82852/855GM Integrated Graphics Device[/COLOR]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:6 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             [COLOR=#ff0000]product: 82852/855GM Integrated Graphics Device[/COLOR]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff


```
```

*-network:0
                description: Ethernet interface
                [COLOR=#ff0000]product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter[/COLOR]
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:6 ioport:3800(size=256) memory:e0402000-e04020ff
           *-network:1 DISABLED
                description: Wireless interface
                [COLOR=#ff0000]product: PRO/Wireless 2200BG [Calexico2] Network Connection[/COLOR]
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:11 memory:e0401000-e0401fff

```
***Lubuntu 14.04 LTS*** and other 14.04 based distros and re-spins, you might also try Xubuntu with 1 GB RAM:

You have Intel graphics, ethernet and wifi, which usually works with linux. Sometimes old intel graphics will benefit from ***UXA acceleration*** according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

(to be used in for example Lubuntu 14.04 LTS. It should not be necessary in distros and re-spins based on 12.04 LTS).

-0-

***ToriOS:***

Select from the pull-down menu at the top left corner:

Apps -- Network -- Web Browser

And select ***SeaMonkey*** as the default browser (instead of the extremely light-weight Links 2). Then you will have a rather 'normal' behaviour.

---

### Post by andfree on 2015-03-10
> **sudodus said:**
> ***ToriOS:***

Select from the pull-down menu at the top left corner:

Apps -- Network -- Web Browser

And select ***SeaMonkey*** as the default browser (instead of the extremely light-weight Links 2). Then you will have a rather 'normal' behaviour.

At the "Apps -- Network" menu there's not a "Web Browser" choice. Only the choices "Links 2" & "wpa_gui". And I don't find "Web Browser" or "SeaMonkey" anywhere at the menus.

I'm in the live session.

---

### Post by sudodus on 2015-03-10
Well, I'm talking about the ***installed*** system. The live system is very minimalistic to be light-weight enough for very old computers. Use the live system to install ToriOS and continue testing in the installed system.

---

### Post by Elfy on 2015-03-10
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by andfree on 2015-03-11
> **sudodus said:**
> Well, I'm talking about the ***installed*** system. The live system is very minimalistic to be light-weight enough for very old computers. Use the live system to install ToriOS and continue testing in the installed system.

Ok, browsing seems to work fine in the installed system. But there are other problems. It asks me for every simple file (doc, xls) which application to use to open. And in the "Choose an application" window that opens there's not a choice like "Document Viewer" or something.

And doesn't shutdown nor reboot. Instead of Lubuntu 14.10 that begins to shutdown but never pass the screen with Lubuntu logo, Torios "Shutdown menu" seems total inactive. I press "Shutdown" or "Restart" and happens nothing at all.

---

### Post by sudodus on 2015-03-11
If you want to help the developer, please report these problems (and refer to the computer data in post #12). See this link

[http://torios.net/get-involved/testing/](http://torios.net/get-involved/testing/)

-o-

It might still be interesting to continue along the Lubuntu track (to get Lubuntu 14.04 LTS working) with ***UXA acceleration***. This is a released version (not suffering from typical problems of a not yet released distro). See this link

[https://wiki.ubuntu.com/Lubuntu/Adva...Intel_graphics]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics")

---

### Post by andfree on 2015-03-11
> **sudodus said:**
> It might still be interesting to continue along the Lubuntu track (to get Lubuntu 14.04 LTS working) with ***UXA acceleration***. This is a released version (not suffering from typical problems of a not yet released distro). See this link

[https://wiki.ubuntu.com/Lubuntu/Adva...Intel_graphics]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics")

Ok, I' ve done it dual-boot. Torios & Lubuntu 14.04 [lubuntu-14.04-alternate-i386.iso] with ***UXA acceleration***. But it doesn't solve me the shutdown/reboot problem. Here's the xorg.conf that I' ve created & edited:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card0"
    Driver      "modesetting"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card1"
    Driver      "modesetting"
    BusID       "PCI:0:2:1"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

---

### Post by sudodus on 2015-03-11
1. Does the UXA acceleration solve the problem with Lubuntu 14.04 LTS, that you get into the log in screen and can log in now?

2. Do not expect UXA it to solve problems with shutdown/reboot (I guess that is with ToriOS). Will it reboot and shutdown with the following commands from a terminal window?

```
sudo reboot
sudo poweroff
```

---

### Post by andfree on 2015-03-11
> **sudodus said:**
> 1. Does the UXA acceleration solve the problem with Lubuntu 14.04 LTS, that you get into the log in screen and can log in now?

2. Do not expect UXA it to solve problems with shutdown/reboot (I guess that is with ToriOS). Will it reboot and shutdown with the following commands from a terminal window?

```
sudo reboot
sudo poweroff
```

The problem with login (for which I wrote in post #1) was about toriOS, not Lubuntu, and it was my fault because I typed wrong password.

The problem with Lubuntu (as I wrote in posts #9 & #18) is that it doesn't reboot/shutdown.  I have exactly the same result if i press shutdown/reboot or with the commands```
sudo reboot
sudo poweroff
``` The screen shows constantly the Lubuntu logo and nothing after that happens. 

It is at this point, if I open tty1, that it asks me for login and I can type nothing. The problem with THIS login still remains (if it really is a problem).

The problem with Torios (one of many) is that the shutdown/reboot menu does nothing at all.

---

### Post by sudodus on 2015-03-12
The shutdown/reboot problem might be a problem with your particular hardware, that might be worked around with a boot option. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

There are many to try, you can start with

acpi=off
noapic
nolapic

---

### Post by andfree on 2015-03-12
Maybe I must try explain a little more my Lubuntu shutdown problem. I haven't any login problem when start lubuntu. Lubuntu starts, loads and logs-in fine. I have problem when shutdown lubuntu: It begins to shutdown, until the point with Lubuntu logo in the black screen. It never passes this point to complete the shutdown. At this point, in an attempt to complete the shutdown, I open the tty1 thing but I can type nothing. (If I open the tty1 other time, before the shutdown attempt, I can type and login with no problem.)

Commands like "sudo reboot" & "sudo poweroff" seem to not do any difference at all: get me to the never shutdown black screen with Lubuntu logo, as I had chosen to shutdown/restart from the shutdown menu.

Finally, I shutdown by keeping pressed the power button or I restart by the Alt+SysRq+type "reisub" combination.

Edit: When I posted it, I hadn't seen yet your last post

---

### Post by sudodus on 2015-03-12
> **andfree said:**
> Maybe I must try explain a little more my Lubuntu shutdown problem. I haven't any login problem when start lubuntu. Lubuntu starts, loads and logs-in fine. I have problem when shutdown lubuntu: It begins to shutdown, until the point with Lubuntu logo in the black screen. It never passes this point to complete the shutdown. At this point, in an attempt to complete the shutdown, I open the tty1 thing but I can type nothing. (If I open the tty1 other time, before the shutdown attempt, I can type and login with no problem.)

Commands like "sudo reboot" & "sudo poweroff" seem to not do any difference at all: get me to the never shutdown black screen with Lubuntu logo, as I had chosen to shutdown/restart from the shutdown menu.

Finally, I shutdown by keeping pressed the power button or I restart by the Alt+SysRq+type "reisub" combination.

Edit: When I posted it, I hadn't seen yet your last post

***Alt+SysRq+type "reisub"*** combination is ***much*** better :-)

But let us hope that you make reboot and shutdown work with some boot option.

---

### Post by andfree on 2015-03-12
> **sudodus said:**
> There are many to try, you can start with

acpi=off
noapic
nolapic

All these three have this result:

1. Reboot from the menu seems to work (I say "seems" because there's a feeling that it shuts down a little quickly and noisily, but maybe it's just my idea. Anyway, the system reboots when I click to do so from the menu).

2. Shutdown from the menu (or "sudo poweroff") stops again at the black screen with lubuntu logo. But, before boot-repairing, the five dots under the logo went on changing colour from white to blue vice versa indefinitely and I could reboot with "reisub" combination. After boot-repairing, the five dots stop to change colours (2 froze in blue & 3 in white, I think) and the "reisub" doesn't work at this point, so I shutdown only by the button.

---

### Post by sudodus on 2015-03-12
Try with the boot options one at a time to find what might work the best (not all three of them at the same time).

---

### Post by andfree on 2015-03-12
One at a time I' ve tried them, but all of them had the same results and for this reason I summed them up in this way at my previous post.

---

### Post by sudodus on 2015-03-12
At this stage I suggest that you try something different, that might work better in your computer:

- ***Knoppix*** (rather powerful debian based distro, known to be good at recognizing hardware)

- ***Puppy Linux*** (the versions ***Wary Puppy*** and ***TahrPup***

---

### Post by andfree on 2015-03-12
I can't boot Knoppix (ADRIANE-KNOPPIX_V7.2.0bootonly-2013-07-28-EN.iso) & Wary Puppy (wary-5.5.iso) from usb. After three continuous times I choose "usb" from the plop boot manager menu, it gets me in a black screen with an under dash in the upper left side and then I can do nothing but shutdown by pressing power button. Hashes for isos checked.

TahrPup 6.0.2 has been installed. Shuts down and reboots perfectly. But I'm afraid it' ll take a long for me to learn it. It took time for me to find the browser. Now I'm looking for the Update Manager.

---

### Post by sudodus on 2015-03-12
Congratulations, I'm glad you found something that works :KS

There are people at the Ubuntu Forums who like and use ***TahrPup***, and with some luck they will see this thread and can help you. (I only like it, I don't use it). If you wish, I can change the title of the thread to attract TahrPup users (it can be changed again if you with). Another alternative, maybe better, is that you start a new thread with TahrPup in the title.

You can also visit the Puppy Forums and get help there.

---

### Post by andfree on 2015-03-12
Thank you very much for your help. I agree that it's probably better for me to start a new thread about TahrPup, here or at Puppy Forums. I think this thread can be supposed as "solved". You can do with it whatever you think more useful for the forum. Thanks very very much again.

---

### Post by sudodus on 2015-03-12
You are welcome :-)

I can mark it SOLVED, but it is better that you do it yourself: Click on **Thread Tools** at the top of the page and select 'Mark this page as SOLVED'.

And good luck with the new thread about TahrPup!

---

