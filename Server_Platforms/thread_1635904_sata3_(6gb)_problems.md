---
title: "sata3 (6gb) problems"
date: 2010-12-02
forum: Server Platforms
---

### Post by draven on 2010-12-02
OS: Ubuntu 10.4 LTS (64-bit)
Motherboard: GIGABYTE GA-P55A-UD3 LGA 1156 Intel P55 SATA 6Gb/s USB 3.0 ATX Intel Motherboard
Sata3 Chipset: Marvell 9128
Hard Drives: (2x) Western Digital Caviar Black WD1002FAEX 1TB 7200 RPM SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive

Drives are not raided in the BIOS, instead I setup linux software raid (md0). This entire system is brand new so while something could be DOA, none of it is old and worn out. Drives are setup in the BIOS as AHCI (not IDE).

> 
[  520.971576] ata10.00: status: { DRDY }
[  520.973759] ata10.00: failed command: WRITE FPDMA QUEUED
[  520.975994] ata10.00: cmd 61/80:f0:bf:19:05/00:00:00:00:00/40 tag 30 ncq 65536 out
[  520.975996]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  520.980411] ata10.00: status: { DRDY }
[  520.982633] ata10: hard resetting link
[  526.371666] ata10: link is slow to respond, please be patient (ready=0)
[  530.979262] ata10: COMRESET failed (errno=-16)
[  530.979611] ata10: hard resetting link
[  536.374737] ata10: link is slow to respond, please be patient (ready=0)
[  540.982327] ata10: COMRESET failed (errno=-16)
[  540.982670] ata10: hard resetting link
[  541.351344] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 320)
[  546.337911] ata10.00: qc timeout (cmd 0xec)
[  546.357857] ata10.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  546.357862] ata10.00: revalidation failed (errno=-5)
[  546.357869] ata10: hard resetting link
[  551.763301] ata10: link is slow to respond, please be patient (ready=0)
[  556.370896] ata10: COMRESET failed (errno=-16)
[  556.371247] ata10: hard resetting link
[  561.287677] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 320)
[  571.260811] ata10.00: qc timeout (cmd 0xec)
[  571.280756] ata10.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  571.280760] ata10.00: revalidation failed (errno=-5)
[  571.281082] ata10: limiting SATA link speed to 1.5 Gbps
[  571.281088] ata10: hard resetting link
[  576.018012] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 310)
[  582.189041] ata10.00: configured for UDMA/133
[  582.189050] ata10.00: device reported invalid CHS sector 0
[  582.189055] ata10.00: device reported invalid CHS sector 0
[  582.189058] ata10.00: device reported invalid CHS sector 0
[  582.189062] ata10.00: device reported invalid CHS sector 0
[  582.189066] ata10.00: device reported invalid CHS sector 0
[  582.189070] ata10.00: device reported invalid CHS sector 0
[  582.189074] ata10.00: device reported invalid CHS sector 0
[  582.189077] ata10.00: device reported invalid CHS sector 0
[  582.189081] ata10.00: device reported invalid CHS sector 0
[  582.189084] ata10.00: device reported invalid CHS sector 0
[  582.189088] ata10.00: device reported invalid CHS sector 0
[  582.189092] ata10.00: device reported invalid CHS sector 0
[  582.189096] ata10.00: device reported invalid CHS sector 0
[  582.189099] ata10.00: device reported invalid CHS sector 0
[  582.189103] ata10.00: device reported invalid CHS sector 0
[  582.189106] ata10.00: device reported invalid CHS sector 0
[  582.189110] ata10.00: device reported invalid CHS sector 0
[  582.189114] ata10.00: device reported invalid CHS sector 0
[  582.189118] ata10.00: device reported invalid CHS sector 0
[  582.189122] ata10.00: device reported invalid CHS sector 0
[  582.189126] ata10.00: device reported invalid CHS sector 0
[  582.189129] ata10.00: device reported invalid CHS sector 0
[  582.189133] ata10.00: device reported invalid CHS sector 0
[  582.189137] ata10.00: device reported invalid CHS sector 0
[  582.189141] ata10.00: device reported invalid CHS sector 0
[  582.189145] ata10.00: device reported invalid CHS sector 0
[  582.189148] ata10.00: device reported invalid CHS sector 0
[  582.189152] ata10.00: device reported invalid CHS sector 0
[  582.189156] ata10.00: device reported invalid CHS sector 0
[  582.189159] ata10.00: device reported invalid CHS sector 0
[  582.189195] ata10: EH complete
[  599.275414] [drm] nouveau 0000:07:04.0: Setting dpms mode 1 on vga encoder (output 0)
[  607.022169] [drm] nouveau 0000:07:04.0: Setting dpms mode 0 on vga encoder (output 0)
[  627.429635] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  627.429970] ata10.00: failed command: WRITE DMA EXT
[  627.431206] ata10.00: cmd 35/00:00:3f:d1:06/00:04:00:00:00/e0 tag 0 dma 524288 out
[  627.431208]          res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  627.435299] ata10.00: status: { DRDY }
[  627.437434] ata10: hard resetting link
[  632.825064] ata10: link is slow to respond, please be patient (ready=0)
[  637.432661] ata10: COMRESET failed (errno=-16)
[  637.433003] ata10: hard resetting link
[  642.828138] ata10: link is slow to respond, please be patient (ready=0)
[  647.435745] ata10: COMRESET failed (errno=-16)
[  647.436085] ata10: hard resetting link
[  647.804745] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 310)
[  652.791319] ata10.00: qc timeout (cmd 0xec)
[  652.811261] ata10.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  652.811265] ata10.00: revalidation failed (errno=-5)
[  652.811581] ata10: hard resetting link
[  658.206736] ata10: link is slow to respond, please be patient (ready=0)
[  662.814331] ata10: COMRESET failed (errno=-16)
[  662.814669] ata10: hard resetting link
[  667.790937] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 310)
[  677.764081] ata10.00: qc timeout (cmd 0xec)
[  677.784026] ata10.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  677.784030] ata10.00: revalidation failed (errno=-5)
[  677.784308] ata10: hard resetting link
[  682.461438] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 310)
[  688.575727] ata10.00: configured for UDMA/133
[  688.575743] ata10: EH complete
[  736.136945] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  736.137229] ata10.00: failed command: WRITE DMA EXT
[  736.137518] ata10.00: cmd 35/00:00:3f:af:08/00:03:00:00:00/e0 tag 0 dma 393216 out
[  736.137520]          res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  736.140612] ata10.00: status: { DRDY }
[  736.142231] ata10: hard resetting link
[  741.532399] ata10: link is slow to respond, please be patient (ready=0)
[  746.140003] ata10: COMRESET failed (errno=-16)
[  746.140307] ata10: hard resetting link
[  751.535472] ata10: link is slow to respond, please be patient (ready=0)
[  756.143107] ata10: COMRESET failed (errno=-16)
[  756.143410] ata10: hard resetting link
[  756.512080] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 310)
[  761.498650] ata10.00: qc timeout (cmd 0xec)
[  761.518595] ata10.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  761.518599] ata10.00: revalidation failed (errno=-5)
[  761.518878] ata10: hard resetting link
[  766.914070] ata10: link is slow to respond, please be patient (ready=0)
[  771.521665] ata10: COMRESET failed (errno=-16)
[  771.521967] ata10: hard resetting link
[  776.498276] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 310)
[  786.471429] ata10.00: qc timeout (cmd 0xec)
[  786.492608] ata10.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  786.492613] ata10.00: revalidation failed (errno=-5)
[  786.492894] ata10: hard resetting link
[  791.168775] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 310)
[  797.339322] ata10.00: configured for UDMA/133
[  797.339337] ata10: EH complete


---

### Post by ian dobson on 2010-12-02
Hi,

Check your SATA cables, I've seen such errors with some cables. On my backend I was having problems with 3 wd 2Tb EARS drives and after replacing all the SATA cables everything was sweet.

Regards
Ian Dobson

---

### Post by draven on 2010-12-02
So I thought I narrowed it down to a single drive. Soon as that drive was added to the raid array, dmesg would flood with errors. But after I removed that drive from the system and started copying data from a USB drive to the other good drive, I got the exact same error.

Do I have two bad drives? Bad on board controller? This whole sata3 experience seems to be nothing but a disaster.

---

### Post by jkgoya on 2011-05-21
Have you made any progress on this? I'm having basically the same problem on the same Marvel controller, and I just switched to the Intel SATA 3.0Gb/s controller and everything is working fine now. It'd be great to get SATA 3 working though...

---

### Post by R.Bucky on 2011-05-21
I have never had any luck with 6G motherboard (mb) connections. Last week, I tried again on a Sabertooth X58 mb. The WD 1.5TB Caviar Black drives were not recognized. I have also tried on the DP55KG without success. 

As a sidenote, and perhaps another thread, can you use the 6G connectors for your two drives and then connect a hot spare? I tried this on the X58 and the BIOS only recognized the hot spare on the 3G. Just talking out loud here...

---

### Post by us11csalyer on 2011-05-21
I'm a noob to linux but I installed four sata2 hdd in raid 0 and ubuntu 11.4 had no problem with it. Of course I set the raid before installing ubuntu and my mobo had raid support in the bios.

---

### Post by satworld on 2011-06-04
i had exactly the same problem with one of my server with ubunto 10.04 lts server
**sata3 (6gb) problems** 
OS: Ubuntu 10.4 LTS (64-bit)
Motherboard: GIGABYTE GA-P55A-UD3 LGA 1155 Intel P55 **[COLOR=#ff0000]SATA[/COLOR]** 6Gb/s USB 3.0 ATX Intel Motherboard
Sata3 Chipset: Marvell 9128
Hard Drives: seagate 2tb  **[COLOR=#ff0000]SATA[/COLOR]** 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive
memory :4gb kingston

everything is brand new .
i try them all  ide hdd- raid-hdci
i changed the sata cable 
changed the hsard drive to western digitial 1tb green edition but nothing
i formated the seagate drive changed to 
then it loaded once when i reboot it the ubuntu wont detect the hdd again
grub does not detect the sata hdd no mater what you do
This seems to be a rather big bug in an Ubuntu Server release, and certainly not the kind of thing I have come to expect from the folks at Ubuntu HQ
 
[http://scottiestech.info/2011/05/04/grub-problem-in-ubuntu-server-11-04-natty-narwhal/](http://scottiestech.info/2011/05/04/grub-problem-in-ubuntu-server-11-04-natty-narwhal/)
 
i hope it will be fixed soon !
how ubuntu does not support sata in 2011.?
i was thinking i was alone with this problem but then i saw on the net a lot of users with the same problem but no solution arround
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/745960](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/745960)

---

### Post by ian dobson on 2011-06-04
Hi,

I'm running 7 sata drives on my server (2 on sata6 ports) and I'm not seeing any problems. Check your sata cables. I've seen really cheap cables that cause problems. Under windows the cables work/you don't see any errors just transfers are really slow.

Regards
Ian Dobson

---

