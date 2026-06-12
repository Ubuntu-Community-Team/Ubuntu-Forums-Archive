---
title: "I need to clone an XP hard drive (installing new hard drive; want it to be primary)"
date: 2008-10-29
forum: Windows
---

### Post by diablo75 on 2008-10-29
I am going to pick up a new hard drive for a computer that is running Windows XP.  The hard drive that is in the machine right now isn't very large and has very little free space left on it.  Rather than shift use habits around and have the new hard drive be a secondary drive, I'd like it to be the primary.  I've heard of clonezilla before, but don't know how to use it at all.  Are there any tutorials out there that show how to clone a drive with an NTFS partition on it to a new drive so I can replace the old one?

Thanks in advanced.

---

### Post by fiddledd on 2008-10-29
[http://www.scribd.com/doc/2067480/How-to-copyclone-hard-drive](http://www.scribd.com/doc/2067480/How-to-copyclone-hard-drive)

---

### Post by smoker on 2008-10-29
i've never used clonzilla to date, so can't comment on that, but most hard drive manufacturers offer an easy to use, and freely downloadable application for moving data from an old to a new drive, one of the drives usually has to belong to the maker of the application though. instructions are simple to follow, so have a look at the 'readme' or the web guide beforehand. for eg:

DiscWizard from Seagate - If you are upgrading and want to migrate your data from the old drive to the new drive we provide DiscWizard as an option.
[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=DiscWizard&vgnextoid=d9fd4a3cdde5c010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=DiscWizard&vgnextoid=d9fd4a3cdde5c010VgnVCM100000dd04090aRCRD)

Data Lifeguard Tools from Western Digital
[http://support.wdc.com/product/download.asp?groupid=502&lang=en](http://support.wdc.com/product/download.asp?groupid=502&lang=en)

check the support pages for the manufacturer of your hard drives if different from above.

these downloads usually need a floppy drive (check for iso downloads if you have no floppy)

a windows application i've used several times before is driveimagexml, which is free and downloadable from here: [http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
instructions are fairly straightforward. this you can install and run in windows.

whatever option you chose, defrag your drive first if required, and clean up any junk.

the main thing to remember is changing jumper settings when required, eg, if using existing windows drive, which will be 'master' to migrate data to new drive which will be 'slave', when operation is complete, jumper settings will have to be changed on each drive to suit, eg, existing windows drive would have to made 'slave', and new drive 'master' so it will boot. also, if sharing the same ide cable, then connectors may have to be changed to reflect this, eg, new master drive at the end of cable connection, and new slave to middle cable connection. this obviously applies only to ide drives. if sata drives, check your motherboard manual for positioning drives.

as always with moving data, always make a backup of essential stuff beforehand. it also may take longer, having to reinstall drivers, and applications, but a fresh install on a new drive is, imo, the best way to go. once you have everything setup again, you can make a backup image of the fresh install, so this should only have to be done once. that way you have a new install on a new drive, and the efficiency and speed benefits that go with it.

best of luck

---

