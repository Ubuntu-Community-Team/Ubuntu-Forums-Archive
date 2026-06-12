---
title: "Dapper/Hardy Dual Boot?"
date: 2008-07-06
forum: Server Platforms
---

### Post by spike_strip on 2008-07-06
I have an Intel based system SCSI U320 with Hot Swap drives. I have been running ```
lsb_release -a 
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper

```

on /sda and have been using /sdb as a secondary drive. I cleaned /sdb and installed Hardy 8.04 on it; and now have two drives, one with Dapper and the other with Hardy.

However, if I want to use the new Hardy install, I must first eject /sda [Dapper], otherwise my server just boots directly into /sda Dapper. 

I would like to not have to eject a drive and simply chose the version I want to boot too. If I was given this choice during boot, that would be great. 

Q: Can this be done?

Q: And how to do it?

Thanks in Advance!

---

### Post by red_team316 on 2008-07-06
Try looking at this. [Boot 145 OSes]("http://www.justlinux.com/forum/showthread.php?threadid=147959") Keeps grub on a separate partition. Just make sure that the drive that you have this grub installed to is set 1st in the boot order in the BIOS.

You could also edit the grub menu.lst in your sda drive to add an entry for hardy.

Side note, if you installed hardy on sdb with the sda drive installed, the installer may have sneakily installed grub to the MBR of sda, not sdb. This is something that confused me when I started multibooting SATA drives with more than 1 OS on each drive. Read about chainloading in the link above and how to install grub to each partition.

---

### Post by spike_strip on 2008-07-06
I think this is the problem I am going to run into is—each /sda & /sdb have there own boot loader installed.

---

### Post by red_team316 on 2008-07-06
Here's the quick answer to what I posted above.
Remove sdb and install dapper on sda.
Then remove sda and install hardy on sdb(the install will look like sda though)
Then hook up both drives in the machine, and edit the menu.lst of the sda by adding:

```

title        Hardy on 2nd drive
root         (hd1,0)
chainloader  +1

```

There will be grub installed on each drive but it wont matter. The first grub that the machine finds will allow you to chainload the 2nd bootloader.

---

### Post by spike_strip on 2008-07-06
> **red_team316 said:**
> 
Side note, if you installed hardy on sdb with the sda drive installed, the installer may have sneakily installed grub to the MBR of sda, not sdb. This is something that confused me when I started multibooting SATA drives with more than 1 OS on each drive. Read about chainloading in the link above and how to install grub to each partition.

No; I ejected /sda prior to installing Hardy on /sdb. I have been down that road before! 

I guess I will need to edit /grub/menu.lst[?]

Do not know how to and will need to do research prior to this!

---

### Post by spike_strip on 2008-07-06
> **red_team316 said:**
> Here's the quick answer to what I posted above.
Remove sdb and install dapper on sda.
Then remove sda and install hardy on sdb(the install will look like sda though)
Then hook up both drives in the machine, and edit the menu.lst of the sda by adding:

```

title        Hardy on 2nd drive
root         (hd1,0)
chainloader  +1

```

There will be grub installed on each drive but it wont matter. The first grub that the machine finds will allow you to chainload the 2nd bootloader.

Thank; I will try this. Sounds like what I need.

---

