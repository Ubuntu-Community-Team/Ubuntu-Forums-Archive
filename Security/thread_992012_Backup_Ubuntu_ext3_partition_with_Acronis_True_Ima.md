---
title: "Backup Ubuntu ext3 partition with Acronis True Image"
date: 2008-11-24
forum: Security
---

### Post by lorenzippo on 2008-11-24
I am fairly new to Ubuntu. I'm running Hardy Heron and dual booting with Vista Home Premium. Vista was installed first. I have installed a program on Vista that allows me to access my Ext3 partition. I also have Acronis True Image 11 and have created a secure zone and have been using it to backup my Vista Partition. My question is "can I use it to also backup the Ubuntu ext3 partition. It is recognized by True Image.
Thank you
Larry

---

### Post by scribbles on 2008-11-24
Why use Acronis when there's [Clonezilla]("http://www.clonezilla.org/")? Has many more features and is open source. Also, from my own personal experience, Acronis images are prone to becoming corrupt. Do a quick google search for "acronis corrupt" and you'll see what I mean... :)

Oh, and to answer your question. Yes, Acronis supports ext3 and will back it up.

---

### Post by gpsmikey on 2008-11-24
Be aware there have been some reports of issues with the latest Ubuntu ( 8.10 ) and Acronis due to 256 bytes/inode instead of the usual 128 bytes/inode in previous versions.  I don't know if it has been solved yet so if you are thinking of upgrading to 8.10 you might want to check the other threads here on that issue.

mikey

---

### Post by bodhi.zazen on 2008-11-24
I would use a Linux native application. clonezilla, partimage, etc, etc.

---

### Post by apaty on 2008-11-24
> **lorenzippo said:**
> I am fairly new to Ubuntu. I'm running Hardy Heron and dual booting with Vista Home Premium. Vista was installed first. I have installed a program on Vista that allows me to access my Ext3 partition. I also have Acronis True Image 11 and have created a secure zone and have been using it to backup my Vista Partition. My question is "can I use it to also backup the Ubuntu ext3 partition. It is recognized by True Image.
Thank you
Larry

Hello!
from my experience it should work well.

---

