---
title: "Rocketraid 3520 Install"
date: 2012-06-12
forum: Server Platforms
---

### Post by dice81 on 2012-06-12
Hey All,

Hope you all can help me with this,  I am running zentyal on a HP workstation which is ubuntu 12.04.  I have a RocketRaid 3520 8 port sata running raid 10 with 4 drives.  For the life of me I can not get it to install the drivers. I have used google for the longest time on trying to find a solution.  

When I do a ./install.sh I get "KERNEL_VER is not set", which seems like I have to set Kernel version but dont know how.  I have read where someone else posted about this error but could not get the steps to work on this model of card.

Is there an quick tutorial that come one could give me on how to install this, or compile or whatever it is I need to do to get this raid controller installed?

[http://www.highpoint-tech.com/USA_new/rr3500_download.htm](http://www.highpoint-tech.com/USA_new/rr3500_download.htm) is the download link for drivers
[http://www.highpoint-tech.com/BIOS_Driver/RR3xxx_4xxx/Linux/1.6/rr3xxx_4xxx-linux-src-v1.6-072009-1131.tar.gz](http://www.highpoint-tech.com/BIOS_Driver/RR3xxx_4xxx/Linux/1.6/rr3xxx_4xxx-linux-src-v1.6-072009-1131.tar.gz)
That is the link I was using to install drivers.

is it as simple as [This link](https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver)

or what?  I am so confused about installing drivers in ubuntu / any version of linux.

Edit1: [I]Tried -
sudo make install
gcc -DMODVERSIONS -DMODULE -DLINUX -D_LINUX_ -D__KERNEL__=1 -DCONFIG_PCI  -O2 -pipe -Wparentheses -Wuninitialized -Wchar-subscripts -Wtrigraphs -Wswitch -Wreturn-type -Wimplicit -Wstrict-prototypes -fomit-frame-pointer -I. -I/lib/modules/3.2.0-18-generic/build/include -I/lib/modules/3.2.0-18-generic/build/drivers/scsi -mcmodel=kernel -mno-red-zone -c -o hptiop.o hptiop.c
hptiop.c:20:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
make: *** [hptiop.o] Error 1
[/I]
Please help!

Thanks,
Dice

---

