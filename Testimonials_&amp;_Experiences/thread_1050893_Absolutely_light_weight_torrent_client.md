---
title: "Absolutely light weight torrent client"
date: 2009-01-26
forum: Testimonials &amp; Experiences
---

### Post by cannon_dt on 2009-01-26
Heres me just sharing a wonderful experience

I was a user of Bit Tornado while I was in windows. So I hunted these forums and got it running. However, some of the torrent sits that I use have the regular ratio restrictions. What this means is that we would have to seed the torrents once we fully get them down. Now BitTornado on an average uses at least 3-4 % of processor times. Now if I seed 10 torrents and leech another 5, my processor is totally being burnt. Now my machine configuration is inferior - intel M processor with 512 MB RAM only. And that is when I stumbled upon an extremely low-processor-intensive torrent client - rTorrent. 

This runs via command line but believe me it is a breeze to operate. At this moment I am seeding 20 torrents and downloading five and this is what I get when I grep rTorrent with top
	PID   PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
	21458 20  0 59452  49m 6532  S 0.3  10.5   2:39.74 rtorrent 

If you see it is just taking .3%, now thats awesome. So all you folks who are torrent users and are in need of a great client, look no further.

A beautiful guide for setting this up (which is a breeze in itself) is at
[http://polishlinux.org/apps/p2p/rtorrent-console-p2p/](http://polishlinux.org/apps/p2p/rtorrent-console-p2p/)

And the official guides/wiki etc is at [http://libtorrent.rakshasa.no](http://libtorrent.rakshasa.no)

Have fun and hope some one finds this useful

BTW, this is was better than delugedll too, that was bulky too. This one 
is great


Thanks,
Cannon

PS: MODS, I posted the same thread under Multimedia & Video by mistake (I was posting my PS3 streaming experience and I did this one too), request you to please delete that (I was not able to delete the post)

---

### Post by Sin@Sin-Sacrifice on 2009-01-26
Sweet... thanks man. I have a 2.6 ghz dualcore but that dfoesnt mean I don't need the extra cpu time for other things. Great tip.

---

### Post by halovivek on 2009-01-26
Try using utorrent using wine. It will be more speed.

---

### Post by cb951303 on 2009-01-26
> **halovivek said:**
> Try using utorrent using wine. It will be more speed.

no need! there are tons of torrent clients for linux. sure utorrent is a good piece of software but it's also completely replaceable.

---

### Post by Joeb454 on 2009-01-26
Moved to Testimonials & Experiences :) I'll delete your other thread now too :)

And rtorrent is brilliant. It'll be getting a heavy workout from me in April when I seed 9.04 from my server ;)

---

### Post by overlord.gaurav on 2009-01-26
>  It'll be getting a heavy workout from me in April when I seed 9.04 from my server  
UPDATES ! I so love them !

---

### Post by solwic on 2009-01-26
> **cb951303 said:**
> no need! there are tons of torrent clients for linux. sure utorrent is a good piece of software but it's also completely replaceable.

+1.  uTorrent is OK, but I've found KTorrent to be far superior.  KTorrent runs faster than any other client on my system.  I'm getting 500-700kbps downloads.  That's triple what uTorrent gave me.  :)

---

### Post by stchman on 2009-01-26
> **jrock612 said:**
> +1.  uTorrent is OK, but I've found KTorrent to be far superior.  KTorrent runs faster than any other client on my system.  I'm getting 500-700kbps downloads.  That's triple what uTorrent gave me.  :)

I think regular old Transmission works just fine for me.  I am not a huge torrent downloader though.

---

### Post by solwic on 2009-01-26
> **stchman said:**
> I think regular old Transmission works just fine for me.  I am not a huge torrent downloader though.

Yeah I don't do the torrent thing very much either, but when I have to, it's KTorrent.  

Of course, it's all preference.  I've seen people swear by K3b for burning CDs, but I tried it yesterday and find Brasero to be much more intuitive and easy to use.  

All preference.  :)

---

### Post by cb951303 on 2009-01-26
> **stchman said:**
> I think regular old Transmission works just fine for me.  I am not a huge torrent downloader though.

I love the simplicity of transmission but it doesn't support DHT. From my personal experiences, speed wise it sets you back big time. The sad part is, developers doesn't care about it, the bug report is 3 years old.

---

### Post by solwic on 2009-01-26
> **cb951303 said:**
> I love the simplicity of transmission but it doesn't support DHT. From my personal experiences, speed wise it sets you back big time. The sad part is, developers doesn't care about it, the bug report is 3 years old.

This is the biggest flaw in Linux's nature.  I read once that Linux program developers didn't owe the users anything, because in the end they were writing programs for themselves, and were doing everyone a favor by sharing.

Not only was that one of the most arrogant things I've ever read (not to mention the stupidest and - sadly - the truest), but it underlines the exact reason why Linux is still #3 in the desktop world.  There exists no responsibility on the developers to create a sound, superior, stable product.  They just do it for themselves, which is why Linux will never be more than what it is.

Now, the developers reject that idea, and that's only natural.  Hitler thought he was right, too.  But expect 3 year old bug reports like this because if the developers of Transmission don't see DHT as a good, necessary, or helpful thing - no matter whether it is or not - then they won't add it.  It's *their* program, after all, and who cares about the users who want at least the option to use it?  If they want something better, they can use something else.  Or write their own version.  All they need is a few years programming experience.  

Of course, if the system were to shift and programs for Linux were sold rather than given away, then you're going to start seeing things like [this]("http://www.macworld.com/article/138380/iworktrojan.html") in a supposedly secure OS.  Which means that the system sucks, but if it changes, it's going to suck more.  

It's a choice between bad and evil, I suppose.  Pick your poison.  :)

---

### Post by wolfen69 on 2009-01-26
> **cb951303 said:**
> I love the simplicity of transmission but it doesn't support DHT. From my personal experiences, speed wise it sets you back big time.

i have not experienced this slow down you speak of. i have to set download speed limits because it goes *too* fast and uses up too much bandwidth. perhaps it is just your connection at fault.

---

### Post by cb951303 on 2009-01-26
> **wolfen69 said:**
> i have not experienced this slow down you speak of. i have to set download speed limits because it goes *too* fast and uses up too much bandwidth. perhaps it is just your connection at fault.

no it's not. I know exactly how to configure torrent and router. I tested it with ktorrent, deluge and bit tornado. All are at least %20 faster sometimes even %50. Also I'm not the only one complaining about transmission's slowness. Do a forum search.

EDIT: Also keep in mind that DHT is not always useful. If there are enough seeds DHT doesn't do anything extra.

---

### Post by karlmp on 2009-03-12
love rtorrent thanks :D

---

### Post by Thanh-BKK on 2009-03-15
Hi :)

I stuck with uTorrent - the only Windows-app that is still active on my computer. It always maxes out my ADSL connection and i run it pretty much all the time my computer is on. Currently, 5 active downloads and 7 active seeds plus this Firefox window i get a 3% CPU load. I love it's speed graph :)

And that's a single-core Sempron 2800+!

Beste regards.....

Thanh

---

### Post by hyper_ch on 2009-03-15
I hope your run rtorrent within screen :)

---

### Post by linuxyogi on 2011-02-17
I run a slow pc & I am presently using ktorrent. But it is quite cpu demanding for my specs. I use  ktorrent because it can be configured to stop after a download is finished 
**i.e. not start seeding aumatically after a download is finished.**
I know Transmission has no such option.
**Is is possible to configure rtorrent to act in the above mentioned manner ?**
I tried to read the man page but couldn't find anything.

Thanks in advance.

---

### Post by johntaylor1887 on 2011-02-17
> **linuxyogi said:**
> 
**i.e. not start seeding aumatically after a download is finished.**
I know Transmission has no such option.


Yes it does. Just right click the torrent in transmission>options>"seed torrent until its ratio reaches">then set it to .01 which will effectively shut it down immediately. But not sharing torrents is morally wrong. If no one shared, torrents would not work.

---

