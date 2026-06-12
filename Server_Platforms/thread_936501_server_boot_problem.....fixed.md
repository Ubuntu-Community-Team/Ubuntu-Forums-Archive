---
title: "server boot problem.....fixed"
date: 2008-10-02
forum: Server Platforms
---

### Post by porphiron on 2008-10-02
Lo folks,

well, I have now been messing around for the past couple of weeks with ubuntu server, as I wanted a realy stripped down install for my fileserver, unfortunatly I have had some mega problems getting the bugger to boot, with numerous grub 15 or 17 errors, or no error messages at all, just a blank screen.

The server was made up of not only ide but sata drives, and afaik this is somthing that can be problematic, but i finally found the answer that worked for me, so thought I would share it.

The following may seem obvious, but I tried many other things, including different bootloaders, until finally biting the bullet and talking the side of my case.

right, simply detach the molex cables from all but the drive you need to boot from and install which ever flavour of ubuntu server you need, i'm using 8.04.1.

Once it gets the the part where you need to partiton your drive, create a boot partiton and make sure its a primary, then either create further partitons as you need or just one big one for /.

Once done create a final primary partiton for swap, leaving everyhing else to an extended partiton(S).

once this has installed and updated, you are now ready to bring the other drives online.

This may seem pointless to you, but this was the only way I could get a working system.

Plug in the next drive you need to setup (after shutting the machine down first )

once rebooted enter its details into you fstab (i tried UUIDgen but it didnt seem to work for me, so just the usual mount point settings worked fine for me)

once you are happy that the drive has/is mounted ok, reboot your machine and repeat the process of manually installing each drive......lo behold you now have all your drives working and the begger now boots

hope this helps

Porph.

---

