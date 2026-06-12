---
title: "New Drive Issues"
date: 2012-11-29
forum: Server Platforms
---

### Post by Jacobm001 on 2012-11-29
I'm running the latest ubuntu server on a x32 tower.  Recently I just purchased a 2tb drive (Segate ATA ST2000DM001-1CH1) for it, but I'm having trouble making it work.

Webmin recognizes the fact that the drive exists, but does not recognize the total size.  It says there are 0 partitions on it, and when I try to add one it gives me an error of:

Failed to save partition : parted -s /dev/sdb unit cyl mkpart primary 0 243201 failed : Error: /dev/sdb: unrecognised disk label

Any ideas as to what would cause this?  Googling it wasn't very helpful.

---

### Post by darkod on 2012-11-30
I'm not sure if webmin can handle a new drive without any partition table existing. And I would suggest to forget webmin about partitioning, just do it in terminal (or over ssh if that's how you are accessing the server).

Try this:
Log into the server and in terminal create new partition table with parted. The choice is yours whether you will create msdos or gpt table.
```
sudo parted /dev/sdb
mklabel msdos (or mklabel gpt)
quit
```

That will create new blank table. After that, you can create partitions using parted, or webmin if you insist on using it.

PS. Note that if you create a gpt table and you plan this disk to have the grub bootloader installed now or later, you will need to create a small bios_grub partition so that grub2 has enough space to install.

---

