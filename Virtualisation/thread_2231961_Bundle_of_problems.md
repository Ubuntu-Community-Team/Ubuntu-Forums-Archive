---
title: "Bundle of problems"
date: 2014-06-29
forum: Virtualisation
---

### Post by henrixd on 2014-06-29
Hello

I have many problems and few solution, so if I may ask for some recommendations.

I have ATI mobility HD2400, which ties me to fglrx-legacy and therefor to old kernel (so 12.04 precise Xubuntu).
I have tried to survive with open source drivers, but my system resources are just too low to get by.
I would be happy with 12.04 precise Xubuntu, but there is this annoying USB bug which slows my external USB-drive to crawl (under 1Mbps speeds). My primary SSD is just 8Gb. My plan was to keep OS on fast disk and everything else on slower external USB-disk, obviously the bug ruined this plan. This would be fixed in newer kernel (I did try all possible magic tricks). So my problem is that I simultaneously need older and newer kernels.

I would like to stick with Xubuntu as my desktop, so I came up with this plan. I install some other Linux distribution or FreeBSD and run Xubuntu on virtual machine, this would allow me to experiment with other OS's as well. Other solution could be, just change to some other distribution.

So the questions..

Is there anything better that comes to mind?
Does someone know if this USB bug is existing in other Linux distributions as well?
I think that qemu-kvm would be best for virtualization, but please correct me if you think there is something better.

I'm not exaggerating or lying..
# sudo hdparm -tT /dev/sdb1
/dev/sdb1:
 Timing cached reads:     2 MB in  2.05 seconds = 999.94 kB/sec
 Timing buffered disk reads:   4 MB in  4.05 seconds = 1010.80 kB/sec

---

### Post by coldraven on 2014-06-29
This laptop has the fairly useless ATI X1250 card and worked great with old versions of Ubuntu. But now I'm running 14.04 and my solution is to go to 2D mode. I don't get to have funky effects but other than that it works ok. IIRC you select 2D mode from the login screen.

```
*-display
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:43 memory:c0000000-c7ffffff memory:d0400000-d040ffff ioport:4000(size=256) memory:d0500000-d05fffff
```

---

### Post by gordintoronto on 2014-06-29
What is the brand and model of your laptop? Is it actually a netbook? A VM will almost certainly run slower than a native install.

What are the specs for the computer? What speeds did you expect to get over USB?

---

### Post by henrixd on 2014-06-30
Laptop is Amilo PI 2540

hardrive is external USB 2.0 connected SATA 2.0 2.5" disk.

Today tested with new USB 2.0 pen-drive:
/dev/sdb1:
 Timing cached reads:   2914 MB in  2.00 seconds = 1456.91 MB/sec
 Timing buffered disk reads:  52 MB in  3.07 seconds =  16.93 MB/sec

I made an mistake, when I read from this phantom usb bug that has been on and off in Ubuntu. I jumped to conclusions too quickly. I should know better.
My new suspect is hardware problem with Initio Corporation INIC-1618L SATA chip. It's connected as USB 2.0, without any errors.. but still so slow..
Drive it self works well when connected directly to sata2 port.

What comes to the virtualization, I don't think one Linux kernel without xorg as dom0 eats much system resources. Sure it is fair to say it is little slower, but not significantly.

---

