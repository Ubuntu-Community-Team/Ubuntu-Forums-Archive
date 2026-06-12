---
title: "RAID1 issue"
date: 2007-06-02
forum: Server Platforms
---

### Post by jose3 on 2007-06-02
Hi guys,
I have installed my Ubuntu server in RAID1 following this great tutorial
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

My spare disk failed and I did *cat */proc/mdstat * * in order to check the state of the other disks and found this:

root@MICRON:~# cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 sdb2[0] sda2[1]
136448 blocks [2/2] [UU]

md0 : active raid1 sdb1[0]
4104512 blocks [2/1] [U_] 

I have contacted the person who wrote the tutorial and he kindly told me that 
**"the RAID device is in degraded mode, i.e. sda1 has failed (or you have manually marked it as failed). "**

I don't see sdb1[1] in md0 active and it is that what he is talking about but I really don't know what to do. 

How can I activate it or mark it as not-failed?

Any help will be appreciated.
Thanks for reading this!!!

Jose

-----------------------------------------------------


***System information:***

/etc/lsb-release file information
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"


cat /proc/version
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006



fdisk -l
Disco /dev/sda: 4350 MB, 4350443520 bytes
255 cabezas, 63 sectores/pista, 528 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1         511     4104576   fd  Linux raid autodetect
/dev/sda2             512         528      136552+  fd  Linux raid autodetect

Disco /dev/sdb: 9132 MB, 9132374016 bytes
255 cabezas, 63 sectores/pista, 1110 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1         511     4104576   fd  Linux raid autodetect
/dev/sdb2             512         528      136552+  fd  Linux raid autodetect

Disco /dev/sdc: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1       29126   233954563+  83  Linux
/dev/sdc2           29127       30401    10241437+  83  Linux

Disco /dev/sdd: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdd1               1       14593   117218241   83  Linux

Disco /dev/md0: 4203 MB, 4203020288 bytes
2 cabezas, 4 sectores/pista, 1026128 cilindros
Unidades = cilindros de 8 * 512 = 4096 bytes

El disco /dev/md0 no contiene una tabla de particiones vÃ¡lida

Disco /dev/md1: 139 MB, 139722752 bytes
2 cabezas, 4 sectores/pista, 34112 cilindros
Unidades = cilindros de 8 * 512 = 4096 bytes

El disco /dev/md1 no contiene una tabla de particiones vÃ¡lida

---

### Post by jose3 on 2007-06-03
Any idea how can I do to fix this? sdb1[0] is missing.

md0 : active raid1 sdb1[0]
4104512 blocks [2/1] [U_] 

Thanks.

---

### Post by keithweddell on 2007-06-03
I haven't done it myself but [this]("http://users.piuha.net/martti/comp/ubuntu/raid.html") Howto has a section on Rebuild after Disk Failure.  And googling "rebuild mdadm" brings up some useful looking pages including the mdadm man page.

Keith

---

### Post by jose3 on 2007-06-03
Thanks for the answer keithweddell but that is exaclty the tutorial I am talking above. I have even communicater with the author adn he identified my problem.

Remember I have this problem I cannot see sdb2 as active into md0?

md0 : active raid1 sdb1[0]
4104512 blocks [2/1] [U_] 

Well I have been doing some search in order to activate that sdb2 and tryed the following.

mdadm /dev/md0 -a /dev/sdb2

The result is I cannot open it because it is busy.

**mdadm: Cannot open /dev/sdb2: Device or resource busy**

 Now if it is busy. Does that mean that exists but is hidden or something?

I even tryed this: 
swapoff -a
mdadm --manage /dev/md0 --add /dev/sdb2
swapon -a

And I get the same error.

Any ideas?

---

### Post by keithweddell on 2007-06-04
As I said, I've not had to do this.  But have you tried mdadm -remove and -re-add?
Maybe you need to do fsck or something to see if there's a fault. 

Keith

---

### Post by jose3 on 2007-06-05
Thanks for the advice keithweddell.
I finally booted with a recovery cd and added the failing partition but failed to load with a sector error. I am going to buy a ne disk very soon. It was good to know it was broken indeed.
Thanks.

---

