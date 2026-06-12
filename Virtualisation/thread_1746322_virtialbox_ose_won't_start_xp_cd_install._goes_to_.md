---
title: "virtialbox ose won't start xp cd install. goes to CLI"
date: 2011-05-01
forum: Virtualisation
---

### Post by Newuser901 on 2011-05-01
I'm new to this so I'm not sure where to start or what this is. I'm hoping it's simple. I've looked all over can't find anything on it specifically or close.

I have it setup start it has 512mb ram 128 vram 10gb of expandable hdd space etc etc. both cds are selected and listed and I think the boot priority sets them before the default hdd if I am reading it correctly. (not sure how else to read it)

It starts up like it were the sytem gives the box graphic for their logo. then gives some weird messages and then eventually a command line prompt. It will not beging the xp 32 bit cd instalation. Some of the messages mention the cd/dvd drives but i don't know what they mean. 

(This is all in different colors but..)

EFI Shell version 2.10 [1.1]
Current running mode 1.1.2
Device mapping table
   fs0 :BlockDevice - Alias f21b blk0
        Pci Root (0x0) /Pci(0x1f,0x1)/Ata(Primary,Slave,0x0)
   blk0 :BlockDevice - Alias f21b fs0
        Pci Root (0x0) /Pci(0x1f,0x1)/Ata(Primary,Slave,0x0)
   blk1 :CDRom - Alias (null)
        Pci Root (0x0) /Pci(0x1f,0x1)/Ata(Primary,Slave,0x0)/CDROM(0x0,0x141,0x4)
   blk2 :BlockDevice - Alias (null)
        Pci Root (0x0) /Pci(0x1f,0x1)/Ata(Primary,Slave,0x0)
   blk3 :BlockDevice - Alias (null)
        Pci Root (0x0) /Pci(0x1f,0x1)/Ata(Primary,Slave,0x0)

Press ESC in x seconds to skip startup.nsh, any other key to continue.
Shell> _


Any idea what this is and what it is doing? All tutorials and videos show it starting automatically in a windows install? What could it be hung up on. and what other info would I need to show to figure it out also. I'm not sure what else is needed.

not that it matters but I"m setting it up as a locked up version of windows to watch netflix on.

And the windows cd was in the cd rom when I started the vrm up.

I'm on a fresh install of ubuntu 11.04 also. I seperately need to whipe my old one and take the other 500gb(currently on 250gb hdd) and incorporate them into this or get a disk setup for backups. But that is another story. 8)

---

### Post by Newuser901 on 2011-05-05
I figured it out. I had something checked in the setting or something. I unchecked some stuff I checked that wasn't there by default and it started using the cd. Had a problem during install where it had to restart. Luckily it restarted from where it left off since it was just the part that was determining settings. And it does that when I would isntall on an hdd when it was primary. Either way solved.

---

