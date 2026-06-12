---
title: "LSI MegaRAID SAS 8208ELP/8208ELP (rev 08)"
date: 2010-06-28
forum: Server Platforms
---

### Post by akanux on 2010-06-28
Hello,

I have a raid intel card based on 
LSI Logic / Symbios Logic MegaRAID SAS 8208ELP/8208ELP (rev 08)

There is drivers on LSI website for SLES end RHEL but no ubuntu 10.04  LTS 64bit (or any  other ubuntu).

I would like to boot ubuntu from one of the raid managed by this card.

My idea (I may be naive) is to boot from live system, install the driver  (I need help to find the driver and the howto install it), then install  the system. I hope it will install something with the same drivers than  the ones used for the live system... If not I will need some tips on  how to make it...

I have already some threads about other model of LSI but  nothing relevant for me.

So thank you for any help you can give me.

akanux.

---

### Post by windependence on 2010-06-28
You don't normally need a driver for this kind of thing. You need to press the appropriate keys during bootup and set up your RAID the way you want and then reboot and install your OS. The OS sees your RAID volume as just one disk (or more if you set it up that way). You should not need to load any drivers in Linux for this to work. 

-Tim

---

### Post by petehinds on 2010-06-28
Hi,

I've also seen this problem but haven't been able to find a solution. It seems the LSI MegaRAID SAS 8208ELP is only supported on RHEL. 

I removed the jumper from the RAID card which allowed it to act in a pass through mode. IE. I could see 6 disks in the installer. I set up software RAID and the installer finished successfully but upon a reboot the drives were not seen by the server so GRUB  nor LILO didn't even load.

---

### Post by windependence on 2010-06-28
Then the card must be a software RAID (fake RAID) card. You should be able to set up the card before the OS even starts booting. If not, you have a software card and in that case you might as well use mdadmin and set up software RAID in Ubuntu. You need a hardware card to do what you want to do.

-Tim

---

### Post by petehinds on 2010-06-28
Hi again,

Yes it's not a great card at all. I've the card set up by entering the raid card manager but during the OS install Ubuntu fails to pick up any disks. 

As the card is 'fake' RAID that's why I removed the jumper so that I could use software RAID within the OS but that's when the second issue crops up. The install completed successfully and if I enter a shell (Alt + F2) I can do a df -h and see the partitions but soon as I reboot the server doesn't detect the disks and tries to PXE boot. 

Admittedly it's more of a limitation of the card rather than a flaw in Ubuntu but that said, it does work with RHEL. I've ordered an Adaptec RAID 3805 as a replacement which offers proper RAID. 

Thanks,

---

### Post by windependence on 2010-06-28
I have had good luck with the Adaptec cards but even with those you gotta be careful what model you get or you will have the same problem. This is why I was kinda surprised when you said you had the problem you did as most of the LSI cards I have used work great with Linux. The companies are getting cheaper and cheaper with their hardware lately. I suppose Linux will eventually support these cards even though I'm not sure that is a good thing. :-)

-Tim

---

### Post by cainwong on 2010-08-07
Just managed to make it work on the **LSI MegaRAID SAS 8208ELP/8204ELP ( rev 08 )** with the followings:

**_ MegaRAID BIOS Configuration Utility_:**
- [Intel Embedded MegaRAID Software]("http://download.intel.com/support/motherboards/server/s5500hv/sb/embedded_mr_sw_ug_v01.pdf")

**_Debian megasr Resources_:**
- [http://csa.pp.ru/megasr/](http://csa.pp.ru/megasr/) [COLOR=Blue](seems newer)[/COLOR]
- [http://mentors.debian.net/debian/pool/non-free/m/megasr/](http://mentors.debian.net/debian/pool/non-free/m/megasr/) [COLOR=Red](seems older)[/COLOR]

**_Tool Resources_:**
- [http://hwraid.le-vert.net/wiki/DebianPackages](http://hwraid.le-vert.net/wiki/DebianPackages)

**_Driver & Tool Guides_:**
- [http://sa-chernomor.livejournal.com/6255.html](http://sa-chernomor.livejournal.com/6255.html)
- [http://nyalb.wordpress.com/2008/07/27/lsi-1608-in-debian-etch-megasrko-2/](http://nyalb.wordpress.com/2008/07/27/lsi-1608-in-debian-etch-megasrko-2/)
- [http://hwraid.le-vert.net/wiki](http://hwraid.le-vert.net/wiki)

**_[COLOR=Red]*** Important ***[/COLOR] last steps after the above guides_:**
** (1)** Add '**megasr**' (without quote) line to */etc/initramfs-tools/modules* if this SAS drive is boot drive (Working on **Ubuntu Jaunty**, shall work on later)
** (2)** If the SAS drive is not boot drive, add '**megasr**' (without quote) line to */etc/modules* and add '*GRUB_CMDLINE_LINUX="**[COLOR=SeaGreen]rootdelay=<sec>[/COLOR]**"*' (without quote) to */etc/default/grub* (Working on **Ubuntu Jaunty**, shall work on later)
[COLOR=DarkOrchid]**(3)** *update-initramfs -k all -u*[/COLOR]
[COLOR=DarkOrchid]** (4)** *update-grub*[/COLOR]

**_Important Notes_:**
- Working on **2.6.28-15** and **2.6.28-19** (both **generic** and **server**), future upgrading seems possible...
- You may use the following cmds to build the upgraded kernels on above guides:
```
*m-a -t -k /usr/src/linux-headers-<new kernel version>/ -l linux-headers-<new kernel version> build megasr*
*m-a -t -k /usr/src/linux-headers-<new kernel version>/ -l linux-headers-<new kernel version> install megasr*

```- If get the **initramfs** console on bootup (cannot mount the root due to timeout), pls repeat using the '*cat /proc/modules*' (without quote) to  check whether the **megasr** is loaded. It seems always needs few mins to be loaded (Guess this is what happens to FAKE RAID card :)). As  my trials told me, **2.6.28-15-generic** took 3mins+ to load whereas  **2.6.28-19-server** took 6mins+ to load the **megasr**. The results show that **megasr** boot-time is depending on the kernel version.
- If happen that you can't add **megasr** to */etc/initramfs-tools/modules*, you may try manually add the "[COLOR=SeaGreen]**rootdelay=<sec>**[/COLOR]" to kernel line in the */boot/grub/grub.cfg* (GRUB 2) or */boot/grub/menu.lst* (Legacy GRUB), eg:
```
menuentry "Ubuntu, linux 2.6.28-19-server" {
        linux   /vmlinuz-2.6.28-19-server root=UUID=aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeeee ro [COLOR=DarkOrange]doscsi[/COLOR] quiet splash **[COLOR=SeaGreen]rootdelay=360[/COLOR]**
        initrd  /initrd.img-2.6.28-19-server
}
```- If you think you need [COLOR=DarkOrange]doscsi[/COLOR], added it as well. Not sure it work on the kernel or not. I just added it to prevent some issues.
- Having GPG signature issue for [2nd guide link]("http://nyalb.wordpress.com/2008/07/27/lsi-1608-in-debian-etch-megasrko-2/") on [COLOR=Blue]Icabrera[/COLOR] hints), replace "*debuild -sa*" with "*dch -i ; dpkg-buildpackage*" (without double quotes) to resolve it.
- Remember to run the [COLOR=DarkOrchid]**last steps (3 & 4)**[/COLOR] to apply the changes to the kernel(s).

Benchmark results seems fine with the compiled **megasr** module:
> *hdparm -Tt /dev/sd*1*

/dev/sda1:
 Timing cached reads:   8086 MB in  2.00 seconds = 4051.86 MB/sec
 Timing buffered disk reads:  466 MB in  3.00 seconds = 155.08 MB/sec

/dev/sdb1:
 Timing cached reads:   7988 MB in  2.00 seconds = 4002.37 MB/sec
 Timing buffered disk reads:  466 MB in  3.00 seconds = 155.30 MB/sec

......
[COLOR=Red]**Remark:**[/COLOR] You may try the [**HWRAID's MegaRAID SAS** tools]("http://hwraid.le-vert.net/wiki/DebianPackages") to benchmark, manage or monitor the hard discs. If happens that you can do all 3 activities with the tools, you are a lucky guy :) It seems that i can only use:
> *megaclisas-status*
-- Controller informations --
-- ID | Model
c0 | LSI MegaRAID SAS 8208ELP and 8204ELP

-- Arrays informations --
-- ID | Type | Size | Status | InProgress
c0u0 | RAID1 | 1G | Optimal | None
c0u1 | RAID1 | 15G | Optimal | None
c0u2 | RAID1 | 29G | Optimal | None
c0u3 | RAID1 | 29G | Optimal | None
c0u4 | RAID1 | 49G | Optimal | None
c0u5 | RAID1 | 12G | Optimal | None

......
And most of the *megacli* cmd parameters :) Refers [here]("http://hwraid.le-vert.net/wiki/LSIMegaRAIDSAS") for more details.

Sorry for the unorganized info, i'm still busy with real-life stuffs. Hope these info will help, [COLOR=Red]try it at your own risk[/COLOR]... Will return when my stuffs are settled.

---

### Post by ShouriChatterjee on 2013-01-15
> **petehinds said:**
> 

Yes it's not a great card at all. I've the card set up by entering the raid card manager but during the OS install Ubuntu fails to pick up any disks. 

As the card is 'fake' RAID that's why I removed the jumper so that I could use software RAID within the OS but that's when the second issue crops up. The install completed successfully and if I enter a shell (Alt + F2) I can do a df -h and see the partitions but soon as I reboot the server doesn't detect the disks and tries to PXE boot. 



Did the jumper-removal finally work out? I am inclined to do the same.
I ordered a server with 4 sas disks - it came with this raid card which I do not want. I just can't install anything onto it (other than rhel, which I don't want).

---

