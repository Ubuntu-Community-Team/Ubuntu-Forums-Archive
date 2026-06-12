---
title: "Wanting to set up a small home network server..."
date: 2007-03-05
forum: Server Platforms
---

### Post by s1mple_M4N on 2007-03-05
Hi all,

I'm looking into setting up Ubuntu Server 6.06 for my home network to centralise music/movies/documents. We will have 3 PCs plus server.

I have a spare PC (Celeron 600/128mb RAM on a Gigabyte 6V-EML mobo) and was wondering if it would be enough to run Server on my network.

I also have a 1-year-old PCI SATA/PATA(IDE) controller card with VIA chipset purchased from Dick Smith (NZ) with a 160G Seagate SATA drive (NTFS with data already on it). Will this be compatible with the old Gigabyte motherboard?

I'm also wondering about Server setup - will it recognise the SATA card during installation or added at a later date? I don't want to risk the data already on it and can't store it anywhere else.

Lastly, 2 PCs will be running XP and 1 XP/Ubuntu Dapper. I have networked these already, will connecting to Ubuntu Server be different?

Thanks in advance,

RoyJ

---

### Post by va1ha11a on 2007-03-06
You should have no problem with the hardware if you stick to the server versions (read no gui) However more RAM would be good.

As for NTFS disk, not so easy. Linux is not that great with NTFS. What you might be able to do is use a partition magic type program to resize the NTFS partition to as small as will fit the data. Use the free space to install your linux partition. If possible move the data to the linux partition. I hear it may be better now but NTFS writes were flaky last time I checked

---

### Post by s1mple_M4N on 2007-03-06
Thanks va1ha11a - I forgot to mention in my first post I will be installing Ubuntu Server onto a small (4G) disc by itself and adding the SATA drive later. Only the networked machines will be writing to the shared folders on the SATA.
I might try an install with just the controller card installed and see how that goes...

---

### Post by ianare on 2007-03-07
You should be alright then. Once you have the system up and running install ntfs-3g to enable write support on the ntfs drive.

Backup all your important data before doing anything.

---

