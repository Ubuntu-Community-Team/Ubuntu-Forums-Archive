---
title: "Issues in AMD Phenom X3/X4 Platform"
date: 2008-09-25
forum: Server Platforms
---

### Post by benoybose on 2008-09-25
I am thinking to host a dedicated web server with Ubuntu Server 8.0 LTS 64 Bit.

The hardware specification I chosen is

AMD Phenom X3 8450 64 Bit
ASUS M3A Mother Board
4 GB Transcend 600 Mhz RAM
250 GB SATA HDD Segate
Compex 10/100 Gigabit LAN Card

Applications I am planning to install are

Apache2.0 / MySQL 5.0 / PHP 5.2.6 / Exim4 / VSFTPD / Mono 

Any one knowns whether any issues are reported towards any component in this specification

---

### Post by fjgaude on 2008-09-25
My only concern would be the Compex LAN card... what model and does the maker indicate Linux is okay?

---

### Post by windependence on 2008-09-25
I know you're trying to keep costs down, but if it's gonna be serious production stuff, I would use an Opteron and something like a Tyan or Supermicro board.

The Phenom should work but if you want to avoid any issues, use server class hardware.

-Tim

---

### Post by NullHead on 2008-09-25
> **benoybose said:**
> I am thinking to host a dedicated web server with Ubuntu Server 8.0 LTS 64 Bit.

The hardware specification I chosen is

AMD Phenom X3 8450 64 Bit
ASUS M3A Mother Board
4 GB Transcend 600 Mhz RAM
250 GB SATA HDD Segate
Compex 10/100 Gigabit LAN Card

Applications I am planning to install are

Apache2.0 / MySQL 5.0 / PHP 5.2.6 / Exim4 / VSFTPD / Mono 

Any one knowns whether any issues are reported towards any component in this specification
My machine is very very similar to what you're saying. Mine works just fine. I haven't tested the LAN though, but I'm sure it'll work fine.

My system is in my signature. Take a look.

---

### Post by benoybose on 2008-09-25
> **fjgaude said:**
> My only concern would be the Compex LAN card... what model and does the maker indicate Linux is okay?

Thanks a lot for your reply


The system is yet to be deliverd. The model is not decided yet, it will be as per availability. Do you think will it be better avoiding complex lan card?

---

### Post by benoybose on 2008-09-25
Thanks!

Its looks cool!

---

### Post by fjgaude on 2008-09-25
> **benoybose said:**
> Thanks a lot for your reply

The system is yet to be deliverd. The model is not decided yet, it will be as per availability. Do you think will it be better avoiding complex lan card?

To be on the safe side, make sure the card you order is okay for Linux. In the manufacters literature it should say.

I guess your intended motherboard doesn't have direct 10/100 LAN support? Most boards these days have 10/100/1000 Mb/sec features.

---

### Post by NullHead on 2008-09-25
My motherboard has 10/100/1000mb support. It's the Asus M3A78.

---

