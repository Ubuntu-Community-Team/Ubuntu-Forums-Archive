---
title: "/boot redundancy--question about grub and hardware"
date: 2009-01-14
forum: Server Platforms
---

### Post by pi3832 on 2009-01-14
I'm in the planning stages of building a small server, to host an rsync server, and an internal-use Moinmoin wiki.  I'm not an IT-pro, so I'm a big, **big** believer in redundancy.  I'll be using LVM on a couple of RAID1 sets.

However, from what I've been reading, the [FONT="Fixedsys"]/boot[/FONT] partition cannot be on a RAID drive.  Chicken'n'egg kind of fing.

Apparently, you can, however, get [FONT="Fixedsys"]grub[/FONT] to install a [FONT="Fixedsys"]/boot[/FONT] partition on multiple drives, so even if the drive from which your booting dies suddenly, you can just swap the drives and still boot.

Well, that got me to thinking--could I get [FONT="Fixedsys"]grub[/FONT] to create a [FONT="Fixedsys"]/boot[/FONT] partition on a CD-R?  Then I could set the mobo BIOS to boot from CD if the HD fails.  Would this work?

And, since I haven't ordered the parts for building the 'puter yet, I was wondering if there is any device that is known to be more reliable than your basic 7200 rpm hard drive?  Compact flash?  SDD?  (Just for [FONT="Fixedsys"]/boot[/FONT].)

TIA.

---

### Post by caljohnsmith on 2009-01-14
You might want to check out the instructions on this page for how to make a boot CD for your Ubuntu install:

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Let me know if that helps.

---

### Post by pi3832 on 2009-01-14
> **caljohnsmith said:**
> You might want to check out the instructions on this page for how to make a boot CD for your Ubuntu install:

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)


Thank you very much for your reply, but I think I may have found a simpler solution, finally, (*after* I posted here, of course!): [[FONT="System"][COLOR="Blue"]GrubWiki: Setting up GRUB to boot from both disks of mirrored RAID[/COLOR][/FONT]]("http://grub.enbug.org/MirroringRAID").

Presuming I can get that to work under Ubuntu (I don't see any reason to expect that it won't), that answers my questions and fills my burning desire for automagical redundancy.

Thanks again.

---

