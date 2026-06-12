---
title: "TorrentFlux is using a lot of RAM"
date: 2008-06-09
forum: Server Platforms
---

### Post by Jordanwb on 2008-06-09
I have 512 MB of RAM in my replacement server, the old one has 256 MB. And on each when I have TorrentFlux running (no torrents) it would leave all but 3 megs of RAM free. Does this happen for anyone else?

---

### Post by quelx on 2008-06-09
Is it really **torrentflux** or all the support services it requires, **apache2** and the **mysql** database?

```
ps -e -orss=,args= | sort -b -k1,1n | pr -TW$COLUMNS
```

Also Linux will cache information in memory (the system isn't using it) and if needed move it to swap if another process requires it.

---

### Post by cracka50 on 2008-06-09
> **Jordanwb said:**
> I have 512 MB of RAM in my replacement server, the old one has 256 MB. And on each when I have TorrentFlux running (no torrents) it would leave all but 3 megs of RAM free. Does this happen for anyone else?

Typically python eats up all my resources while running TFlux, No idea why it would do that when there are no torrents, but if your system is under full load while barely running it I can see it easily crashing once you start throwing any files on there.. check your configuration, make sure there are no LAMP errors..

---

### Post by Jordanwb on 2008-06-09
> **quelx said:**
> Is it really **torrentflux** or all the support services it requires, **apache2** and the **mysql** database?

Well If I never went to the TFlux WebUI, my server only uses about 128 MB (+/- 30MB), As soon as I type 192.168.1.131/torrentflux, bam it's down to 3 megs free with no swap used.

> **cracka50 said:**
> Typically python eats up all my resources while running TFlux, No idea why it would do that when there are no torrents, but if your system is under full load while barely running it I can see it easily crashing once you start throwing any files on there.. check your configuration, make sure there are no LAMP errors..

What files would I check for errors?

---

### Post by cracka50 on 2008-06-09
> **Jordanwb said:**
> Well If I never went to the TFlux WebUI, my server only uses about 128 MB (+/- 30MB), As soon as I type 192.168.1.131/torrentflux, bam it's down to 3 megs free with no swap used.



What files would I check for errors?

Check whatever logs you can find for apache, check torrentflux's logs if it has any, I don't know exactly where these are, because I've only been working with ubuntu for web servers for a short time...

---

### Post by hyper_ch on 2008-06-10
how about rtorrent?

---

### Post by gtdaqua on 2008-06-10
Jordanwb, when torrentflux is running, are you experiencing any kind of performance issue? Linux takes most of the memory all the time even when the system is idle and releases to resources whenever it is requested. That's the design. 

So anytime, your linux box will have only a small amount of RAM in free space. If you are not seeing performance issues, then it is normal. Post your "free -m" output. Also, see what "top" says.

---

### Post by Jordanwb on 2008-06-10
Right ater I start up my server, I type saidar to get system info. It says 512 MB Total, 100 MB (+/- 30MB), 412 MB Free (+/- 30MB).

I'll go to the tf site now. Hmm that's weird, with no torrents running the memory doesn't drop to 3MB free. Why does this always happen to me? I found a torrent, started it, but now I have 380 MB free. It seems to be working properly now. Maybe it has to do with the size of the files in the torrent?

---

### Post by gtdaqua on 2008-06-10
can you post your "free -m" output? would like to see ur swap settings.

---

### Post by Jordanwb on 2008-06-10
Oh ok:

```
jordanwb@SERVER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        162        340          0         36         58
-/+ buffers/cache:         67        435
Swap:         1507          0       1507
```

---

