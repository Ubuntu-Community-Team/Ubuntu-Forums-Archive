---
title: "Update Manager - Restart"
date: 2013-10-08
forum: Ubuntu Development Version
---

### Post by Elfy on 2013-10-08
Is anyone seeing Restart button being ineffective of late. 

In Xubuntu - restart button does nothing, seems to work ok in Ubuntu. 

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1232363](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1232363)

---

### Post by ventrical on 2013-10-09
Works fine here on one of my Sandybridge Desktops. Not as fast as a startup as I thought it would (fully updated beta daily) and it still has that little delay in the opening screen with the circular counterclockwise avatar spinning , then stops and gives the appearance of a hang, which it is not .. but the devs should make this transition a little smoother. I have tried to help some of my clients with low end machines with Xubuntu and (12.04) and the DE gets so borked that I end up having to install the Unity DE. 

  Saucy Xubuntu beta has a real nice motif and artwork. Seems smoother . etc.. but is still chunky , even on higher end machines.

 Also ..  could you perhaps put in the version type (amd64bit - i386) etc... I know you put it in your bug report but I don't always have time to check those bug reports. Sorry . I can't "me too" your bug report because restart is working OK here.

Regards..

```
ventrical@ventrical-MS-7798:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation B75 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by OrangeCrate on 2013-10-09
> **Elfy said:**
> Is anyone seeing Restart button being ineffective of late. 

In Xubuntu - restart button does nothing, seems to work ok in Ubuntu. 

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1232363](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1232363)

Doesn't work here either, and hasn't for as long as I can remember during this development cycle. I just use the "Action Buttons" option to restart, as an alternative.

Edit:

I added a comment to the bug report.

---

### Post by Elfy on 2013-10-09
seems to be consolekit causing the issue

@orangecrate/ventrical - thanks for looking

---

### Post by slickymaster on 2013-10-09
> **Elfy said:**
> Is anyone seeing Restart button being ineffective of late. 

In Xubuntu - restart button does nothing, seems to work ok in Ubuntu. 

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1232363](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1232363)

+1.

```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
3.11.0-031100rc6-generic

```

```
~$ apt-cache policy update-manager
update-manager:
  Installed: 1:0.194
  Candidate: 1:0.194
  Version table:
 *** 1:0.194 0
        500 http://pt.archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
```

```
~$ apt-cache policy consolekit
consolekit:
  Installed: 0.4.5-3.1ubuntu2
  Candidate: 0.4.5-3.1ubuntu2
  Version table:
 *** 0.4.5-3.1ubuntu2 0
        500 http://pt.archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
```

---

