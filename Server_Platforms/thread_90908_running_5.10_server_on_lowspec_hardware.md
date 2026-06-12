---
title: "running 5.10 server on lowspec hardware?"
date: 2005-11-16
forum: Server Platforms
---

### Post by wijnands on 2005-11-16
Hi, 

I'm seriously considering ubuntu to replace my clarkconnect 2.1 system. I like clarkconnect, it does it's job nicely but I think I'm ready now for a slightly less "next, next, finish" enviroment.

I'm planning to run a basic server with:
- apache
- mysql
- postfix
- samba
- webmail
The server will not be very busy, mail for 4 people, a small website with a few dozen hits a day.

I;m now running my server on a p2-350 with 128mb ram. It's sufficient but php performance could be better. I've recently obtained another desktop with a celeron 400something and 256mb ram. Would this be sufficient for a server install?

---

### Post by hostile on 2005-11-16
[QUOTE=wijnands]I;m now running my server on a p2-350 with 128mb ram. It's sufficient but php performance could be better. I've recently obtained another desktop with a celeron 400something and 256mb ram. Would this be sufficient for a server install?[/QUOTE]


If ClarkConnect is doing everything for you now, why change? I have never used it, but I've heard nothing but good things about it.

As for your hardware, the Celeron/P-II is pretty much a wash. I'd take the RAM from the 350 and dump it into the Celery system, and use the Celery. Why? Most likely the RAM won't work from the Celery in the P-II system (PC66 vs PC100).

---

### Post by wijnands on 2005-11-16
[QUOTE=hostile]If ClarkConnect is doing everything for you now, why change? I have never used it, but I've heard nothing but good things about it.
[/quote]

Well, couple of things really. 
- changing from postfix 1.x to 2.x on this box is a bit taxing on my linux skills
- I'm sort of hoping that another distro will give me better php performance
- I'm in the mood for a fresh challenge and something new.

In addition to that the box I'm running it on now is showing the first signs of old age. Clarkconnect is very good when you're looking for a soho server with minimal install hassle

[QUOTE=hostile]
As for your hardware, the Celeron/P-II is pretty much a wash. I'd take the RAM from the 350 and dump it into the Celery system, and use the Celery. Why? Most likely the RAM won't work from the Celery in the P-II system (PC66 vs PC100).[/QUOTE]
The P-II is running on pc100 (getting enough of that was a BIG challenge for my scrounging abilities :-) ). The cellery seems to like either pc100 or pc133. In addition to that, the power supply is somewhat better and I got a bigger disk for it.

---

### Post by hostile on 2005-11-16
[QUOTE=wijnands]The cellery seems to like either pc100 or pc133. In addition to that, the power supply is somewhat better and I got a bigger disk for it.[/QUOTE]

That Celeron is 66MHz fsb, so it should be PC66 RAM.

The speed difference b/t the P-II and Celery will be pretty much a wash.

Aaah... this makes me want to go and dig out my venerable 300A from the depths of my parts bin...  :D

---

### Post by squirrelyosis on 2005-11-16
That is a pretty beastly PC.  I have Ubuntu running on a P3 500 with 256 MB as my "server" bind9, proftpd, apache, etc...  I just hit Ctrl+Alt+F1 when the login screen comes up and run it in text mode.  I was in a similar situation as you.  I had MS Server installed on it and I was getting bored with it.  I wanted so start something new and different to do the same things.  My advise, go with a new setup you will learn so much more and be better off in the end.

---

### Post by majikstreet on 2005-11-16
my server stats:
```

SYSTEM i686 Ubuntu (Debian) GNU/Linux, Kernel 2.6.12-9-386, LIBC 2.3.5, GNU Bash Shell | CPU Pentium III (Katmai), 451Mhz, 512KB Cache, 893 BMIPs | MEM 93/123MB RAM Used, 104/203MB Swap Used | STORAGE 2x1.5GB Ext2, 3.8GB Ext3, 2x62MB TmpFS | STATS Uptime 27.14d, Users 1(1), Procs 78(82025), Load 0.00 | X11 Unknown | http://auk.ca/v

```

can't get postfix to work though... can't figure out why..

---

### Post by spade_shark on 2005-11-19
How about taking the PII 350 out and putting it and the RAM ( 128 ) in the celerys place (slot 1)?  Giving you a PII 350 with 384 MB and a nicer case / power supply.  You may need the extra L2 cache on the 350.  I agree, CC is a nice build for the SOHO, tons of plugins in just one click!  Better solution yet?  If your celeron mobo supports PIII chips, do it!  Go to a computer swap and spend the $5.00 and dig up a PIII 500 (your mobo may even support higher if it is socket 370).  Double the performance for pennies!  Remeber KISS for a SOHO box.  Keep it Super Simple. ;)

---

