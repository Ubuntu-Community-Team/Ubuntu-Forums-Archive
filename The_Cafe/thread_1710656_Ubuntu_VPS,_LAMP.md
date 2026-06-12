---
title: "Ubuntu VPS, LAMP"
date: 2011-03-20
forum: The Cafe
---

### Post by GreenDance on 2011-03-20
Hi, I've found a provider to rent an Ubuntu VPS from, the VPS only has 256mb ram, is that suitable for Apache PHP and MySQL?

Thank You.

---

### Post by SeijiSensei on 2011-03-20
It'll be tight, but it should work.  If that's the largest machine available from that provider, I'd look around, though.  In the longer run, you'll be better served by a machine with 512 MB that can be increased if your needs expand.

---

### Post by GreenDance on 2011-03-20
I've notice some VPS sellers offer 128mb ram for a VPS, surely with 128mb ram you couldn't run much else? maybe lighttpd and php?

Thank You. :KS

---

### Post by CharlesA on 2011-03-20
Which provider were you looking at?

I've heard [Linode]("http://www.linode.com/index.cfm") is pretty nice.

---

### Post by BkkBonanza on 2011-03-20
It will run ok. But if you get too busy you will be swamped by Apache's threads gobbling up RAM. If there isn't some feature that you must have Apache for then you will find yourself much better off in that size VPS running Nginx instead. Only uses about 2MB independent of how busy it gets. For PHP/MySql alone there isn't any reason not to use Nginx - I've done exactly that for years.

---

### Post by kevin11951 on 2011-03-20
You guys may be over estimating what servers need.  For example, I an the admin for a shared hosting server with a good number of websites on it, many written in PHP, and this is the output of free -m:

```
# free -m
             total       used       free     shared    buffers     cached
Mem:          3996       1883       2112          0        202       1208
-/+ buffers/cache:        **472**       3523
Swap:         4016          1       4014

```

I also ran a support ticket system server for a very large high school here, and it only had 256mb of ram, and it was faster then that shared hosting server above...

I also happen to know that a Debian 6 CLI install with A lamp stack only runs at about 128mb, and thats a lot even...

In short, yes, your 256mb VPS will do fine for a very large array of projects...

---

### Post by kevin11951 on 2011-03-20
> **GreenDance said:**
> Hi, I've found a provider to rent an Ubuntu VPS from, the VPS only has 256mb ram, is that suitable for Apache PHP and MySQL?

Thank You.

If your computer can handle it, setup a virtualbox virtual machine with 256mb of ram, running Ubuntu 10.04.2 server edition, and setup the lamp stack, with whatever PHP stuff you want, and then measure the ram usage, this will be the most accurate way to know how it will do in production...

---

### Post by CharlesA on 2011-03-20
> **kevin11951 said:**
> If your computer can handle it, setup a virtualbox virtual machine with 256mb of ram, running Ubuntu 10.04.2 server edition, and setup the lamp stack, with whatever PHP stuff you want, and then measure the ram usage, this will be the most accurate way to know how it will do in production...

+1 to that.

---

### Post by stmiller on 2011-03-20
I guess it depends more or less on the price. For $20 a month you can get 512MB from linode.com, quad xeon.

---

### Post by themarker0 on 2011-03-20
jckd.co.uk

I use them, they resell outa someone, but i don't care, its just so good of a deal.

50 for the year, i have a burst of a gig and 256 i think.

---

