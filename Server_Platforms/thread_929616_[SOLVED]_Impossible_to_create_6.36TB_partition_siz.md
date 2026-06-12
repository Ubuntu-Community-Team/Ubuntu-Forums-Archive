---
title: "[SOLVED] Impossible to create 6.36TB partition size"
date: 2008-09-25
forum: Server Platforms
---

### Post by MatPoweR on 2008-09-25
Hello,

I have an ubuntu server 8.04.1 installed.
I try to create a 6.36 TB partition create with an adaptec RAID card
The RAID seems to be Ok
but i can't create a 6.36TB partition, with gparted give me a 373GB maximum size and fdisk a 2TB.

if i try to specify fdisk the size i want, it says me "Valeur hors limites." (which means "outrange value.")

is someone can help me ?

thanks.

---

### Post by DarkPhoenixTSi on 2008-09-25
> **MatPoweR said:**
> Hello,

I have an ubuntu server 8.04.1 installed.
I try to create a 6.36 TB partition create with an adaptec RAID card
The RAID seems to be Ok
but i can't create a 6.36TB partition, with gparted give me a 373GB maximum size and fdisk a 2TB.

if i try to specify fdisk the size i want, it says me "Valeur hors limites." (which means "outrange value.")

is someone can help me ?

thanks.

I had the same issue with two 4.5TB drives I was trying to partition and format. I tried gParted, and that was unhappy, so I used parted and it worked great. 

#sudo parted /dev/sba#

At the parted prompt:

#mklabel gpt#

#mkpart primary 0 -0#

That will make use of the entire "drive"

From there, if you have gParted installed, you should be able to format it.

Hope that helps.

---

### Post by fjgaude on 2008-09-25
Thanks for the heads up... I trust that now big drives are here **GParted** soon will handle all the commands of **parted**.

---

### Post by MatPoweR on 2008-09-26
thanks a lot
it works very well.

---

### Post by pdub on 2009-03-12
Thanks. This post was helpful.

---

