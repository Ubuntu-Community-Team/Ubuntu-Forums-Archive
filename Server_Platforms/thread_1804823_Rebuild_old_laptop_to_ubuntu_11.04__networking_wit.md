---
title: "Rebuild old laptop to ubuntu 11.04 / networking with windows 7"
date: 2011-07-15
forum: Server Platforms
---

### Post by koshiuk on 2011-07-15
Ive got an old laptop which had windows 7 on it, and a ntfs data partition full of movies/photos..   i'm planning on moving the windows 7 to another pc and re building my old win7 laptop with ubuntu 11.04 as a sort of file server, and maybe a webserver in the future.

Would it be good practice to format and partition the drive to ext4 instead of a ext4 / ntfs combo?  and move the data back onto ext4? or leave NTFS on the data partition?  i need to access the data from a seperate windows 7 pc.  which i've read that samba is good for?  or maybe use freenas?

many thanks! :popcorn:

---

### Post by koshiuk on 2011-07-21
I've moved all the NTFS data to a USB HDD.... so now using ubuntu on a clean HDD, advisable to run SAMBA, LAMP on ubuntu desktop, or should i be using server ed?

---

### Post by 2F4U on 2011-07-21
If you intend to use it as a server, I would take Ubuntu server edition. Much longer support and stability. Go for the 10.04 edition if stability and long-term support is important to you.

---

