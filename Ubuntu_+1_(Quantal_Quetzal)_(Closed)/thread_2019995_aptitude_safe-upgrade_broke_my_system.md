---
title: "aptitude safe-upgrade broke my system"
date: 2012-07-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by JRV on 2012-07-07
My hardware is an Intel D945CGLF2 motherboard with 2 gig ram.

I installed the 64 bit Alpha2 and everything seemed to be working properly.

Next I did a:
```

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude safe-upgrade

```

Now it defaults to Unity2d and my wired LAN is offline.

I zsync(ed) my disk image to get the latest updates and the disk now just gives me a black screen.

---

### Post by VinDSL on 2012-07-07
Gotta say it...

Look, I'm NOT trying to thread crap, make anybody *feel* bad, or whatever, but...

I just wanna say, I used Aptitude for about a year (a Debian IT know-it-all fanboi talked me into it) and I had nothing but problems with it.

After giving Aptitude a fair trial, I finally purged it from my system(s) and have been happy ever since.

Speaking strictly for myself (this is NOT a recommendation) I would format my HDD and do a fresh install -- that's how much I grew to h-a-t-e Aptitude.

Okay, I'm done ranting!

Hopefully, somebody more reasonable will pop in here.  LoL!  :D

Good luck, man...

---

### Post by scradock on 2012-07-07
You pretty well said it all, Vin!

Good luck - or better yet, follow the advice in the first reply.

---

### Post by jerrylamos on 2012-07-07
I've been having good luck with Quantal Alpha lately with:
sudo aptitude update && sudo aptitude -y full-upgrade

For some reason "safe" doesn't bring in all the changes, and have not gotten burned with "full-upgrade".

I have had many installations destroyed by sudo apt-get dist-upgrade so I only do that when absolutely necessary, have backups on hand, duplicate installs, etc.

Jerry

---

### Post by JRV on 2012-07-08
Thankyou for the friendly advice.
I had always thought safe-upgrade was 100% safe.  I was wrong.

I reverted to the 3.5.0-2 kernel and then I was able to use the network.
"sudo aptitude update && sudo aptitude -y full-upgrade" solved the problem.

Now everything works with either the 3.5.0-2, or 3.5.0-3 kernels.

---

### Post by philinux on 2012-07-09
[http://ubuntuforums.org/showpost.php?p=11464224&postcount=22](http://ubuntuforums.org/showpost.php?p=11464224&postcount=22)

---

### Post by effenberg0x0 on 2012-07-10
IMHO, apt and aptitude do not work 100% reliably for DR. Not to mention the GUI interfaces, as synaptic and update-manager. Any of them can cost you a setup during development. They are good tools and reliable enough for SR though. During development, all update tools have given me headaches once in a while, and it's not unusual to see one of them happily updating while another chooses to hold packages. 

The development phase is just too messy and complex for these tools and we have to pay attention to the options presented in screen by any of them. Actually, this is the game: We can't trust a single binary during DR testing, that's just normal.

Now, The thing I praise about aptitude is that it usually offers a set of viable solutions to fix a broken setup and allows you to choose which option to apply (and that has saved me a number of times). It has also been useful when apt's cache is corrupt (no idea why but it works).

(just my 0.02)

Regards,
Effenberg

---

