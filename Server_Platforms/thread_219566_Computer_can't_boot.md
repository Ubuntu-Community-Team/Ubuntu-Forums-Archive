---
title: "Computer can't boot"
date: 2006-07-20
forum: Server Platforms
---

### Post by SuperMightyMo on 2006-07-20
Hey

Oke maybe it's a hardware problem, but i am trying to run Ubuntu Dapper Draker server. So i thought maybe i got to post it here. If i am wrong please say so i will move it..

When i installed ( installation go's ok) and a reboot i just go normally and than it says Grub Loading 2 sec 1 sec 0sec boot and than it just restarts.

does anyone have an idea??? 

Hardware:

It's an old Packerd Bell computer that's runnig it. 

- 500mhz
- 256mb ram
- 20 gig IDE harddisk ( used to had a fat 32 partition on it)
- no stats on the motherboard i am afraid.
- a cd-rom player 24x

Thanx SuperMightyMo

---

### Post by swamytk on 2006-07-20
if u don't mind, pl. check your default runlevel in /etc/inittab. Hope it should not be in 6 (reboot)!

---

### Post by SuperMightyMo on 2006-07-20
Hey

Thanx for your fast reply!

Do i have to do this with the Live cd or in recovery mode??

Can i change it wenn it's nog working??

tnx

SuperMightyMo

---

### Post by swamytk on 2006-07-20
Recovery mode is enough. First check whethere really runlevel is the problem? if it is so, change it even while on network. any way you have to reboot.

---

### Post by SuperMightyMo on 2006-07-21
Ok, 

I will try, 

thanx, SuperMightyMO

---

### Post by SuperMightyMo on 2006-07-25
I can't open /etc/inittab -bash: premmision dennied

even wenn i run as root.

Do you have any suggestions??

tnx, SuperMightyMo

---

### Post by SuperMightyMo on 2006-07-28
Oke, sorry i did it wrong

I had to do:

> 
vim /etc/inittab


Now i got it to open but do i have to run the default runlevel???

Tnx

SuperMightyMo

---

