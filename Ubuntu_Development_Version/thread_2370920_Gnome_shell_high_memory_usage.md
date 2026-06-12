---
title: "Gnome shell high memory usage"
date: 2017-09-08
forum: Ubuntu Development Version
---

### Post by godofking222 on 2017-09-08
Hey guys :) 

I've installed the daily build to see what's new in there and i'm pretty surpise ( good and bad ).

One thing rly concern me is the gnome shell memory usage, it's high, rly rly high. 

When i used ubuntu with gnome shell ( in old versions ) it's started at 80Mio and the pike was 170/180  Mio. Now it's 200Mio after a boot and at least 350Mio after 1hour. 

Someone has any clue about what could affect so bad gnome shell ? ( sry for my english btw ^^)

thanks guys :)

---

### Post by amano on 2017-09-09
There might still be some memory leaks in GNOME-Shell or Mutter yet, hopefully to be fixed by 3.26 or 3.26.1. On my nettop (very limited ram, just about 1,5 GB available) I can see the system using the swap partition earlier when opening a few apps. Thus I can somewhat confirm.

---

### Post by amano on 2017-09-09
There was a gtk+ leak discovered recently: [https://github.com/GNOME/gtk/commit/09d1d5a0d6dd9a4c5e0a137a92e9fa38b7ad36dd](https://github.com/GNOME/gtk/commit/09d1d5a0d6dd9a4c5e0a137a92e9fa38b7ad36dd)

It is fixed upstream,  but not yet in Ubuntu. That might be the culprit.

---

### Post by rrnbtter on 2017-09-09
Greetings,
@OP it may help if you run "free" at a prompt and post the results.

like this.
rrnbtter@rrnbtter-110-15ISK:~$ free
              total        used        free      shared  buff/cache   available
Mem:        3914536     1125308      134008      300144     2655220     2196980
Swap:       5119996           0     5119996

Available RAM is wasted ram.  If there is free ram and unused swap then I would say "forget it".

---

### Post by amano on 2017-09-09
Edit: nevermind

---

### Post by godofking222 on 2017-09-09
Ok here some screenshot from htop.

You'll see that gnome software may have a leak too.

---

### Post by rrnbtter on 2017-09-09
Greetings,
@OP I my opinion you don't have enough ram to run 17.10 without using the swap file. It will run but not as smooth as a 4Gig system. Someone in this section said a few years back that anything over 4Gig was just bragging rights, but those days are passing quickly with a full featured OS and modern software. I bought my wife a new laptop because her 2Gig 10" Toshiba was dragging from Xenial onward. It really didn't do well with Trusty.

---

### Post by mc4man on 2017-09-09
> **godofking222 said:**
> Ok here some screenshot from htop.

You'll see that gnome software may have a leak too.
Your gnome-shell usage seems ok, I'd expect here between 200 - 400 MB, you're at 180.
However the gnome-software usage is absurd (close to 3 GiB res), you should kill it . It may be useful to open Software & Updates, under the Updates tab set it to never check & never auto install..

---

### Post by godofking222 on 2017-09-09
@rrnbtter: Not so sure, 4Gb/ram is enough for what ubuntu do or what i do (ide/gaming).

@mc4man: i have to kill it like 4/5 time during my all sessions or it's just freezing as hell. for gnome-sofftware, i checked a lot and it auto restart even if i stop the update or kill it. So i just purge it and everything is fine now (i checked my self for update almost everyday), here is another screenshot without killing gnome-shell ( 2 instances for 500Mb together).

---

