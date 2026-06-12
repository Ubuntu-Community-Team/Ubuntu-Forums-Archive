---
title: "Problems with PC Deepfreeze on Dual Boot Setup?"
date: 2009-01-27
forum: Security
---

### Post by anthonious on 2009-01-27
Hi,

Our group was looking to test Ubuntu on dual boot XP machines.  I originally installed 8.04 to setup a test environment and didn't have any problems on two machines.

I then installed 8.10 onto machines with the same setup.  My PC colleague informed me today that 2/3 of the machines seem to have a problem with Deep Freeze not working on the PC side.  

Has anybody seen this before from installing Ubuntu?  I configured the /boot/grub/menu.lst file to automatically default to our XP partition.  I did this with 8.04 and we didn't notice any problems and I don't think it is related to the Ubuntu install.  If it was, all the machines would have the same problem!

I installed Ubuntu off CDs I burned from the Ubuntu sight.  I don't think it is related to Ubuntu, but need to have some other opinions if I hope to keep this project rolling in the future.

Thanks,
Anthony :D

---

### Post by coolczone on 2009-09-23
Hi, I have the same prbl, .Ubuntu and vista business installed with vista loading first and configured this way with grub. I am thinking that reconfiguring grub will solve the prbl. Did not tryied yet this is just something I am planning to.

---

### Post by coolczone on 2009-09-24
Ok, funny thing, I tried to reconfigure Grub, but strange my Grub file is empty.Trying to restore orginal vista loader with EasyBCD  won''t help either. So I decided to :
 1) reinstall Vista
2) repartition C with vista Disk management.
3)install Deepfreeze on C
4)instal Ubuntu side by side 

Here comes the big problem: my PC won't boot in any OS and I get an error 21. Triyed to repair with Vista DVD- Startup repair fails. Recovery partition fails to fix MBR but -strange, **reinstalls Vista to factory conditions**(No MBR). I hade a MBR bac-kup made with Acronis so I reinstalled MBR from backup. Vista loads now, but Ubuntu is just another regular partition.
 I am not a tech guy but what I think is that Deepfreeze is protecting the boot.ini file in Windows. Grub is messing with vista loader and all it can do is changing the partition letter for Vista since boot.ini is protected. The rezult is a valid boot.ini file with a strange  true path to C that doesent seems to act like that. I verified in CMD  (with vista DVD) the   .ini file and all was ok in my opinion.
  What could be next: Install Ubuntu first and Vista 2nd. Install Deepfreeze and see if it works. I have no hart to mess again with my PC. Probably latter.

---

