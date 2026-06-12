---
title: "what CPU to use for my server"
date: 2014-09-28
forum: Server Platforms
---

### Post by CaseyRedDragon on 2014-09-28
I have a web server I made out of a old computer and I'm wanting to upgrade the CPU in it. I have several computers that I can get a cpu from. I would like to know what you guys think would be the better one to use. It currently has a Pentium 3 550 MHz SL3FJ
Here is the cpus i got
AMD Athlon XP 1700+ 1467 MHz FSB 266 MHz
AMD Athlon 1200 1200 MHz FSB 200 MHz
Pentium 3 800EB 800 MHz FSB 133 MHz
Pentium 3 750 MHz FSB 100 MHz SL3XP
I also have some more Pentium 3s
Which of these should i use or should I buy a better Pentium 3 CPU?

---

### Post by QIII on 2014-09-28
Hello!

It depends on you motherboard -- you can't mix and match Intel and AMD.  The socket layouts are completely different physically and the chipsets on the mobos don't work interchangably.

Personally, I'd not bother buying a new dinosaur if one of them is currently working.

---

### Post by CaseyRedDragon on 2014-09-28
I know these are from different computers including the motherboard for it. They are from some computers that I have setting around.

---

### Post by tgalati4 on 2014-09-28
The 800 MHz P3 would be your best bet--if it is compatible.  You would have to research it.  It might be plug-and-play, it might not work at all.  You won't notice a large increase in performance because the bus, RAM, harddisk are all part of the performance equation.  I would look for a Core2Duo or similar and max out the RAM.  P3's are long in the tooth don't have enough power to run modern services.

---

### Post by CaseyRedDragon on 2014-09-28
I know that the cpu has to be compatible with the motherboard I was going to see which would be best to use and then switch out the motherboard for the one with that cpu.

---

### Post by nerdtron on 2014-09-28
Hhhhmmm...Does any of those processor support 64bit?

---

### Post by CaseyRedDragon on 2014-09-28
no all 32 bit. I'm going to be putting Lubuntu on it

---

### Post by nerdtron on 2014-09-28
If you are all out on pure cpu performance you can compare which one of those is the most powerful, try [http://cpuboss.com/](http://cpuboss.com/)

---

### Post by mastablasta on 2014-09-29
you could get more power and less power consuption by getting a small Celeron (e.g. on ITX motherbaord) or Pentium G (which is basically celeron). 

the old ones kind of make sense only if you get them for free and if you run some simple web services.

don't install lubuntu install ubutnu server or better yet minimal and then only add what you need. some light webserver (lightpd maybe?!) and you should do just fine.

I mean raspbery pi can run webserver, and it's power is arround those P3. so it's slowish but it can work ok. for anything more modern you need about 100 USD or 100 EUR

---

### Post by Michael_McKenney on 2014-09-29
I would say the fastest and newest one.  You might want to see if you can get a newer motherboard, CPU, RAM deal.  Microcenter usually has combo deals once a month.   I did a Intel board, 775 based dual core CPU, and 2 GB RAM for $149.

---

### Post by mörgæs on 2014-09-30
Arer you sure that CPU performance is the bottleneck? What does **top** show when the server is in use?

---

### Post by CaseyRedDragon on 2014-09-30
I'm probably not going to be changing out just the CPU but the motherboard and memory too. I was looking to know which CPU would be best and then I was going to change out the motherboard with the one that came with that CPU or would work with it.

---

### Post by Michael_McKenney on 2014-09-30
The problem you might have is getting a motherboard to match your old CPU and RAM.  Some times it is less expensive to get a combo kit.  Micro Center has monthly specials that are 40-50% off buying separate.  You also have to make sure your power supply connections match up to the new board.

---

### Post by CaseyRedDragon on 2014-09-30
The CPU's are in some computers that I have, they're not by themselves so I have the motherboard for each CPU and I'm more looking to not spend too much on it but I will checkout  Micro Center.

---

### Post by Michael_McKenney on 2014-09-30
AMD Athlon XP 1700+ 1467 MHz FSB 266 MHz seems to be your best board.  Do you have 2 GB of RAM for it?  I have seen RAM for these older rigs go $60-$80 a GB.   That is why I recommended looking for a combo kit.  Might be a less expensive option.  I guess it comes down to how much RAM do you have on each setup?  With Ubuntu, 2 GB seems a good sweet spot.

---

### Post by mörgæs on 2014-10-01
No, a server needs very little RAM. It's one of the few examples where CPU speed is more important than RAM.

---

### Post by mastablasta on 2014-10-01
unless it's using ZFS or has virtual machines...

---

### Post by volkswagner on 2014-10-01
For a web server, you may consider getting a cheap VPS. Unless you have specific needs for housing the server at home, get a cheap VPS for $5/month
at Digital Ocean or similar provider. That $5/mo will get you 512MB of RAM and a solid state disk (20GB), in a real data center with serious uptime. You won't have to pay
for electric on your server and you'll get a real static, public ip address.

---

### Post by Vegan on 2014-10-01
> **CaseyRedDragon said:**
> I have a web server I made out of a old computer and I'm wanting to upgrade the CPU in it. I have several computers that I can get a cpu from. I would like to know what you guys think would be the better one to use. It currently has a Pentium 3 550 MHz SL3FJ
Here is the cpus i got
AMD Athlon XP 1700+ 1467 MHz FSB 266 MHz
AMD Athlon 1200 1200 MHz FSB 200 MHz
Pentium 3 800EB 800 MHz FSB 133 MHz
Pentium 3 750 MHz FSB 100 MHz SL3XP
I also have some more Pentium 3s
Which of these should i use or should I buy a better Pentium 3 CPU?

You may find Linux today to run very poorly in those older processors. You might want to consider a more modern 64-bit processor with at least 2GB of RAM or more.

I installed Linux on a machine I refurbished recently and it was slow with a 2.4 GHz processor

I suspect a dual core may be a better option in addition to the 64-bit capability

---

### Post by mörgæs on 2014-10-01
Once more: A server install (real install, not virtual) is thrifty and runs on very modest hardware. You certainly don't need 64 bit nor 2 GB of memory.

---

### Post by Vegan on 2014-10-01
64-bit will be an advantage with modern 4k format hard disks as the continue to rise in capacity
this is due to the LBA48 and LBA64 which need 64-bit registers

for a fresh install, unless the CPU is older, the 64-bit version is the way of the future

---

### Post by mörgæs on 2014-10-02
> **Vegan said:**
> ... unless the CPU is older...

Please see original post.

---

