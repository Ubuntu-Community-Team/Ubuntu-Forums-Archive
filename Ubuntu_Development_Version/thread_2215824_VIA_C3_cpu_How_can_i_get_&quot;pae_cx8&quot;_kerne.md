---
title: "VIA C3 cpu: How can i get &quot;pae cx8&quot; kernel support on lubuntu"
date: 2014-04-08
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2014-04-08
I am doing some volunteer work and we need to get XP off some old systems
these things have 512MB ram i tried to boot a lubuntu live disk, but the kernel does not support it
is there a version i can install on these things
speccy output
```
Summary
        Operating System
            MS Windows XP Professional 32-bit SP3
        CPU
            VIA C3
            Nehemiah 0.13um Technology
        RAM
            Unknown system error: 0x8004100c
        Motherboard
        Graphics
            Generic Television @ 1024x768
            S3 Graphics Twister
        Hard Drives
            29.3GB FUJITSU MHT2030AT (PATA)    148 &#7710;C
        Optical Drives
            No optical disk drives detected
        Audio
            VIA AC'97 Audio Controller (WDM)
Operating System
    MS Windows XP Professional 32-bit SP3
    Installation Date: 01 January 2003, 11:51
    Serial Number: <snip>
CPU
        VIA C3
            Cores    1
            Threads    1
            Name    VIA C3
            Code Name    Nehemiah
            Package    Socket 370 CPGA
            Technology    0.13um
            Specification    VIA Nehemiah
            Family    6
            Extended Family    0
            Model    9
            Extended Model    0
            Stepping    8
            Revision    C5P
            Instructions    MMX, SSE
            Bus Speed    133.0 MHz
            Stock Core Speed    666 MHz
            Stock Bus Speed    133 MHz
                Caches
                    L1 Data Cache Size    64 KBytes
                    L1 Instructions Cache Size    64 KBytes
                    L2 Unified Cache Size    64 KBytes
                Core 0
                    Core Speed    665.0 MHz
                    Multiplier    x 5.0
                    Bus Speed    133.0 MHz
                        Thread 1
                            APIC ID    0
RAM
    Unknown system error: 0x8004100c
Motherboard
    Chipset Vendor    VIA
    Chipset Model    Apollo Pro133Z/PM133
    Chipset Revision    00
    Southbridge Vendor    VIA
    Southbridge Model    VT82C686
    Southbridge Revision    40
        BIOS
Graphics
        Monitor
            Name    Generic Television on S3 Graphics Twister
            Current Resolution    1024x768 pixels
            Work Resolution    1024x768 pixels
            State    enabled, primary, output devices support
            Monitor Width    1024
            Monitor Height    768
            Monitor BPP    32 bits per pixel
            Monitor Frequency    60 Hz
            Device    \\.\DISPLAY1\Monitor0
        S3 Graphics Twister
            Memory    16 MB
            Memory type    2
            Driver version    6.14.10.0012-13.94.12
Hard Drives
        FUJITSU MHT2030AT
            Manufacturer    Unknown manufacturer
            Serial Number    NN0DT531JASS
            Interface    PATA
            Capacity    29.3GB
            Real size    30,005,821,440 bytes
                S.M.A.R.T
                    01 Read Error Rate    100 (100 worst) Data 000002D414
                    02 Throughput Performance    100 (100) Data 0000CA0000
                    03 Spin-Up Time    100 (100) Data 0000000000
                    04 Start/Stop Count    099 (099) Data 00000003C5
                    05 Reallocated Sectors Count    100 (100) Data 0000030004
                    07 Seek Error Rate    100 (100) Data 0000000741
                    08 Seek Time Performance    100 (100) Data 0000000000
                    09 Power-On Hours (POH)    050 (050) Data 0005745130
                    0A Spin Retry Count    100 (040) Data 0000000000
                    0C Device Power Cycle Count    100 (100) Data 00000003BB
                    C0 Power-off Retract Count    100 (100) Data 0000000070
                    C1 Load/Unload Cycle Count    080 (080) Data 0000031658
                    C2 Temperature    001 (001) Data 00000E3694
                    C3 Hardware ECC Recovered    100 (100) Data 00000003F1
                    C4 Reallocation Event Count    100 (100) Data 0010A20002
                    C5 Current Pending Sector Count    100 (100) Data 0000000000
                    C6 Uncorrectable Sector Count    100 (100) Data 0000000000
                    C7 UltraDMA CRC Error Count    200 (200) Data 0000000000
                    C8 Write Error Rate / Multi-Zone Error Rate    100 (100) Data 0000000127
                    Temperature    148 &#7710;C
                    Temperature Range    bad (greater than 55 &#7710;C)
                    Status    Good
                Partition 0
                    Partition ID    Disk #0, Partition #0
                    Disk Letter    C:
                    File System    NTFS
                    Volume Serial Number    405B3EE1
                    Size    27.9GB
                    Used Space    4.06GB (15%)
                    Free Space    23.9GB (85%)
Optical Drives
    No optical disk drives detected
Audio
        Sound Card
            VIA AC'97 Audio Controller (WDM)
        Playback Device
            VIA Audio (WAVE)
        Recording Device
            VIA Audio (WAVE)
Peripherals
        HID Keyboard Device
            Device Kind    Keyboard
            Device Name    HID Keyboard Device
            Vendor    Logitech
            Location    Location 0
                Driver
                    Date    7-1-2001
                    Version    5.1.2600.5512
                    File    C:\WINDOWS\system32\DRIVERS\kbdhid.sys
                    File    C:\WINDOWS\system32\DRIVERS\kbdclass.sys
        HID-compliant mouse
            Device Kind    Mouse
            Device Name    HID-compliant mouse
            Vendor    Logitech
            Location    Location 0
                Driver
                    Date    7-1-2001
                    Version    5.1.2600.0
                    File    C:\WINDOWS\system32\DRIVERS\mouclass.sys
                    File    C:\WINDOWS\system32\DRIVERS\mouhid.sys
        HID-compliant mouse
            Device Kind    Mouse
            Device Name    HID-compliant mouse
            Vendor    Unknown
            Location    Location 0
                Driver
                    Date    7-1-2001
                    Version    5.1.2600.0
                    File    C:\WINDOWS\system32\DRIVERS\mouclass.sys
                    File    C:\WINDOWS\system32\DRIVERS\mouhid.sys
        DYMO LabelWriter 450 Turbo
            Device Kind    Printer
            Device Name    DYMO LabelWriter 450 Turbo
            Location    USB Printing Support
                Driver
                    Date    6-6-2010
                    Version    8.3.0.443
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\UNIDRV.DLL
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\UNIRES.DLL
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\UNIDRVUI.DLL
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\STDNAMES.GPD
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\UNIDRV.HLP
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\lw450t.GPD
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\LW400.DLL
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\LW400_UI.DLL
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\LW450C.GPD
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\LW400.INI
                    File    C:\WINDOWS\System32\spool\DRIVERS\W32X86\dymolabelwriter_450_aa08\LW400MON.DLL
                    File    C:\WINDOWS\system32\LW400MON.DLL
        Disk drive
            Device Kind    USB storage
            Device Name    Disk drive
            Vendor    TOSHIBA
            Comment    TOSHIBA TransMemory USB Device
            Location    Location 0
                Driver
                    Date    7-1-2001
                    Version    5.1.2535.0
                    File    C:\WINDOWS\system32\DRIVERS\disk.sys
Network
    You are connected to the internet
    Connected through    Realtek RTL8139/810x Family Fast Ethernet NIC - Packet Scheduler Miniport
    IP Address    192.168.1.156
    Subnet mask    255.255.255.0
    Gateway server    192.168.1.1
    Preferred DNS server    192.168.1.2
    Alternate DNS server    192.168.1.3
    DHCP    Enabled
    DHCP server    192.168.1.2
    External IP Address    <snip>
    Adapter Type    Ethernet
    NetBIOS over TCP/IP    Enabled via DHCP
        WinInet Info
            LAN Connection
            Local system uses a local area network to connect to the Internet
            Local system has RAS to connect to the Internet
        Wi-Fi Info
            Wi-Fi not enabled
        WinHTTPInfo
            WinHTTPSessionProxyType    No proxy
            Session Proxy
            Session Proxy Bypass
            Connect Retries    5
            Connect Timeout    60000
            HTTP Version    HTTP 1.1
            Max Connects Per 1.0 Servers    INFINITE
            Max Connects Per Servers    INFINITE
            Max HTTP automatic redirects    10
            Max HTTP status continue    10
            Send Timeout    30000
            IEProxy Auto Detect    No
            IEProxy Auto Config
            IEProxy
            IEProxy Bypass
            Default Proxy Config Access Type    No proxy
            Default Config Proxy
            Default Config Proxy Bypass
```
```
~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : CentaurHauls
cpu family    : 6
model        : 9
model name    : VIA Nehemiah
stepping    : 8
cpu MHz        : 665.000
cache size    : 64 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr cx8 mtrr pge cmov pat mmx fxsr sse up rng rng_en ace ace_en
bogomips    : 1329.85
clflush size    : 32
cache_alignment    : 32
address sizes    : 32 bits physical, 32 bits virtual
power management:
~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : CentaurHauls
cpu family    : 6
model        : 9
model name    : VIA Nehemiah
stepping    : 8
cpu MHz        : 665.000
cache size    : 64 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr cx8 mtrr pge cmov pat mmx fxsr sse up rng rng_en ace ace_en
bogomips    : 1329.85
clflush size    : 32
cache_alignment    : 32
address sizes    : 32 bits physical, 32 bits virtual
power management:

it@chpt4:~$ cat /proc/meminfo 
MemTotal:         491652 kB
MemFree:           43928 kB
Buffers:           20060 kB
Cached:           303144 kB
SwapCached:         6092 kB
Active:           192736 kB
Inactive:         220388 kB
Active(anon):      42932 kB
Inactive(anon):    48468 kB
Active(file):     149804 kB
Inactive(file):   171920 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:             0 kB
HighFree:              0 kB
LowTotal:         491652 kB
LowFree:           43928 kB
SwapTotal:        505852 kB
SwapFree:         490364 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:         85572 kB
Mapped:            27132 kB
Shmem:              1480 kB
Slab:              21004 kB
SReclaimable:      12816 kB
SUnreclaim:         8188 kB
KernelStack:        1768 kB
PageTables:         3528 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:      751676 kB
Committed_AS:     547284 kB
VmallocTotal:     524344 kB
VmallocUsed:        4336 kB
VmallocChunk:     517680 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       53184 kB
DirectMap4M:      454656 kB
~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8605 [PM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
01:00.0 VGA compatible controller: S3 Graphics Ltd. 86C380 [ProSavageDDR K4M266] (rev 02)
```

---

### Post by ventrical on 2014-04-08
Lubuntu Precise should work just swell on those old machines.
Do you have some additonal hardware specs??

[URL="http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/"]http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/


[/URL]

---

### Post by pqwoerituytrueiwoq on 2014-04-08
thanks I wil try to boot that, if it boots i assume i cant upgrade the kernel unless i compile my own right?

---

### Post by ventrical on 2014-04-08
> **pqwoerituytrueiwoq said:**
> thanks I wil try to boot that, if it boots i assume i cant upgrade the kernel unless i compile my own right?


 Actually I had some older machines where I had installed Lucid or Precise (with Unity 2D) and I was able to install the Saucy kernel series with no problems, but there are certain points when the newer kernels will fail on the older distros ...  I did some early work with trusty kernel series and Mate and xmonad desktop (especially fvwm-crystal desktop)  and they worked ok with the trusty kernels. Only problem is that once you get it stable you have to lock it down because then when you try to update openly it will break your system. At least it did for me. If you have a lot of patience then it's a real adventure ! :) lol

and btw .. no .. i did not have to compile the kernel. Just straight install from RC.

sudo dpkg  -i //kernelxxx.deb

---

### Post by ventrical on 2014-04-08
Here is 3.14.n-n kernel running Lucid.

```

ventrical@ventrical-desktop:~$ uname -a
Linux ventrical-desktop 3.14.0-031400-generic #201403310035 SMP Mon Mar 31 04:55:40 UTC 2014 i686 GNU/Linux
ventrical@ventrical-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid
ventrical@ventrical-desktop:~$ 

```

You can get it here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/)

but it is highly experimental. It just proves that you can use an earlier release cycle and install a development release kernel on that older cycle.

 Of course it went into low graphics recovery (because of nVidia) but I'll work with it for a bit and see what happens. I can always roll to the Lucid kernel or an earlier kernel of trusty.

See here also:
[http://ubuntuforums.org/showthread.php?t=2214217](http://ubuntuforums.org/showthread.php?t=2214217)

---

### Post by pqwoerituytrueiwoq on 2014-04-08
i managed to install 12.04 on it took all evening, i left it installing updates, maybe it will be done tomorrow
i think i will leave 12.04 on it just cause i am tired of messing with that snail and i have 2 more to get done tomorrow
i know i cam install the kernel like that but it needs to have "pae cx8" support in the kernel to boot, without that it is like trying to boot the amd64 version on a Pentium 4
those thing allow you to boot usb-hdd usb-cdrom usb-zip usb-floppy but not a usb flash drive and i only had 1 usb optical drive, bringing my own with me this time
usb 1.0 ports to top off the slowness

---

### Post by ventrical on 2014-04-09
A lot of the older VIA and SiS chipsets respond very slow and equal to  lot of downtime. Most PCs lower than a 2.4GHzP4 are going to be a more 'standard' experience.

---

### Post by sudodus on 2014-04-09
I don't want to make you sad, but if you intend to use the Lubuntu desktop, neither of 10.04 nor 12.04 have LTS and they have passed end of life. So you are replacing one distro (XP) with another one that lacks [complete] security updates.

I would suggest that you try the experimental installer ***9w*** which can install Trusty with a non-pae kernel on these computers with VIA processors. (*Ventrical* tried it on an extremely old computer some weeks ago - that computer was too old for it, but I think you'll have better luck with these VIA systems).

See this link (posts #88 and #89 and the following describe it)

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

Once installed, you can use the normal methods to update/upgrade and install programs. Trusty will soon become 14.04 LTS. I suggest that you try the [Lubuntu Core iso file]("http://phillw.net/isos/linux-tools/9w/TrustyB1npae-LubuCore.iso") from

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

---

### Post by pqwoerituytrueiwoq on 2014-04-09
thanks sudoers, i will give that a try

i had to use the alternate installer cause the thing locked up with the gui install of 12.04

i would like to get them on 14.04 if i can
can that 12.04 install be upgraded to 14.04 and still work? (tell it to do a automated upgrade and come back in 2 days when it is done)

all these things are used for is getting/printing some labels, i doubt anyone has the patience to try anything on them that would put them at high risk

---

### Post by sudodus on 2014-04-09
It should be possible, at least some weeks after the release of 14.04 LTS, to upgrade directly from 12.04 LTS.

The good thing with ***Lubuntu Core Trusty*** of ***9w*** is that it has a non-pae kernel and should work directly without any slow upgrading precedure, 'only' update/upgrade from the beta version to the current date.

-o-

On the other hand, if these computers will only print labels, and not connect to the internet, you can use 'any' system that has passed end of life, as long as they can print those labels. Or does getting the labels imply connecting to the internet?

---

### Post by pqwoerituytrueiwoq on 2014-04-09
labels are generated at a external ip via OnDemand web ui or xp client software

i will burn that iso and let you know how it goes
 will also get /proc/cpuinfo in the 1st post

---

### Post by sudodus on 2014-04-09
Good luck :-)

---

### Post by pqwoerituytrueiwoq on 2014-04-09
that ISO booted and seemed responsive (more so that 12.04)
it booted 
ran startx
it will not open a terminal window
when i click the install icon i get a I/O error
installing 12.04 now on  the last 2

added cpuinfo, meminfo, and lspci info to the 1st post

---

### Post by sudodus on 2014-04-09
> **pqwoerituytrueiwoq said:**
> that ISO booted and seemed responsive (more so that 12.04)
it booted 
ran startx
it will not open a terminal window
when i click the install icon i get a I/O error
installing 12.04 now on  the last 2

added cpuinfo, meminfo, and lspci info to the 1st post

So if I understand correctly, the installer itself did not work in graphics mode.  That is too bad, but an important piece of knowledge about the limits of the 9w installer.

There is still a possibility, that it could install in text mode

running the suggested (red) command line

```
mkusb TrustyB1npae-LubuCore.iso
```

Try it if you wish, but if you are happy with what you have already installed, that's fine.

---

### Post by pqwoerituytrueiwoq on 2014-04-09
i would not call it so much as happy but i don't want to spend another full day messing this that hardware

---

### Post by sudodus on 2014-04-10
I see.

---

### Post by sudodus on 2014-04-11
Hi again pqwoerituytrueiwoq,

*[phillw]("http://ubuntuforums.org/member.php?u=824544")* has compiled a new version of his non-pae kernel, and has built an iso file with an alternate installer around it. He is asking for help now, help to test it in a computer with a real non-pae kernel, and I think that these VIA CPUs are non-pae. It would be very valuable for the Lubuntu project, if you can spend some time testing it. The iso file can be downloaded from this link (at Phill's own server)

[http://phillw.net/isos/non-pae/](http://phillw.net/isos/non-pae/)
 [URL="http://ubuntuforums.org/member.php?u=824544"]
[/URL]The system 9w, that I suggested earlier, contains an earlier version of Phill's non-pae kernel.

---

### Post by pqwoerituytrueiwoq on 2014-04-11
thanks will try it next Tuesday
i will try the kernel debs and upgrade to trusty on another

---

### Post by sudodus on 2014-04-11
Thanks, I'm looking forward to your result :-)

---

### Post by phillw on 2014-04-11
As do I !! Thanks for being prepared to test. It has been quite a journey to get the point of a fully made ISO with a tweaked kernel. My brain is still hurting and I still do not fully understand all the steps - I'm told that once you learn it, it is dead easy :D

Regards,

Phill.

---

### Post by phillw on 2014-04-11
subscribed

---

### Post by ventrical on 2014-04-11
Gotta love that vintage VIA processor  :) lol

---

### Post by sudodus on 2014-04-12
Hi *pqwoerituytrueiwoq*,

Let us hope you have better luck than *jerrylamos* and I in the following thread
[URL="http://ubuntuforums.org/showthread.php?t=2216356"]
Please help us test Lubuntu with Phill's non-pae kernel[/URL] 

But be prepared, that your installation attempt might also fail to mount the CDROM. (And in that case, you will know soon after booting.)

---

### Post by pqwoerituytrueiwoq on 2014-04-12
it has to boot via usb cdrom
on that not i did a install on a 08ish dell (1.8Ghz core 2 duo) and i could not boot my flash drive i had to burn a dvd

---

### Post by sudodus on 2014-04-12
You must convert the iso file to a hybrid iso file. Then it will be possible to boot from USB (even after flashing).

1. Check the downloaded file with md5sum

2. Convert it with this command

```
isohybrid  lubuntu-14.04-non-pae.iso
```

But the current version seems buggy, and after booting it get stuck trying to mount the CD 'again'. 

Right now we are waiting for Phill to make a new version of the iso file. We'll check if the next version will work as USB boot drive after conversion to hybrid iso file.

---

### Post by pqwoerituytrueiwoq on 2014-04-14
so currently it will not work with a usb cdrom? aside from usb floppy, usb zip, and usb hdd that is the only option for these things

---

### Post by sudodus on 2014-04-14
We have to wait for Phill to debug the current version (2) and upload a new version to his web-site (3).

I have also processed the iso files with isohybrid, and I think it makes them work in USB, at least as well as in a CD disk. But that was a previous version, the current one has the same issue as the first one (and only the current version is available at Phill's server).

version 0: 'cannot mount CD-ROM'
version 1: needed the forcepae boot option, but I could install a working system with it
version 2: 'cannot mount CD-ROM' again

See this link

[http://ubuntuforums.org/showthread.php?t=2216356&p=12986457#post12986457](http://ubuntuforums.org/showthread.php?t=2216356&p=12986457#post12986457)

If you want to try version (1) I can upload it for you. Just let me know! (You can send an Ubuntu Forums Message to me.)

Otherwise we'll wait for Phill's next version.

---

