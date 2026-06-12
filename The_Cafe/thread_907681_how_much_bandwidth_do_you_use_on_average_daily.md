---
title: "how much bandwidth do you use on average daily?"
date: 2008-09-01
forum: The Cafe
---

### Post by ice60 on 2008-09-01
i've been monitoring my bandwidth for a long time and on a normal day i use about 1.5GiB, i don't ever use torrents for anything because i prefer to make one direct connection for my downloads, i watch a lot of movies and download pictures too sometimes lol.

this is what i use, in conky, to measure what i use -
```
${color #909090}Down:$color ${totaldown eth0} ${alignr}${color #909090}Up:$color ${totalup eth0}
```

i'm just starting to get a bit worried my ISP will start capping my bandwidth and want to know if i'm a bandwidth hog or not!

---

### Post by Bachstelze on 2008-09-01
This is not bandwitdh, this is traffic. Bandwith is amount of data transferred per unit of time, so 1.5 GiB a day is an average 145 kb/s, which is not that bad. I never measured it precisely, but I definitely use more.

---

### Post by ice60 on 2008-09-01
> **HymnToLife said:**
> This is not bandwitdh, this is traffic. Bandwith is amount of data transferred per unit of time, so 1.5 GiB a day is an average 145 KiB/s, which is not that bad. I never measured it precisely, but I definitely use more.
do you always notice when people call it bandwidth instead of traffic? i've never noticed before, traffic does sound right now you've mentioned it!

is there anyway to tell how much i've used in the last 30 days by running something in the terminal?

---

### Post by happysmileman on 2008-09-01
> **HymnToLife said:**
> This is not bandwitdh, this is traffic. Bandwith is amount of data transferred per unit of time, so 1.5 GiB a day is an average 145 KiB/s, which is not that bad. I never measured it precisely, but I definitely use more.

Well 145kbps I assume you meant, since KiB/s is 8 times as much (AFAIK), and I'm not sure how much I use, but probably nowhere near that much, since my download speed is capped at 512kbps and I have school + sleep (I torrent stuff pretty much constantly but usually don't get great speed)

---

### Post by Bachstelze on 2008-09-01
> **happysmileman said:**
> Well 145kbps I assume you meant, since KiB/s is 8 times as much (AFAIK)

Yes, it was 145 kilobits per second (kbps) indeed.

---

### Post by ice60 on 2008-09-01
i hadn't really thought about it before, but i haven't done anything linux related for about 2 years i just watch movies when i'm on the computer sometimes 2 in a row lol

---

### Post by Mazza558 on 2008-09-01
Is there a command to use in the terminal which will show bandwidth?

---

### Post by ice60 on 2008-09-01
> **Mazza558 said:**
> Is there a command to use in the terminal which will show bandwidth?

you can run this i think, it works on my suse
```
/sbin/ifconfig eth0 | grep "RX bytes"
```
edit
actually just running /sbin/ifconfig might make more sense.

---

### Post by swoll1980 on 2008-09-01
> **Mazza558 said:**
> Is there a command to use in the terminal which will show bandwidth?

install iftop then use command sudo iftop this is what it looks like

---

### Post by doorknob60 on 2008-09-02
My ISP shows me that :D They started monitoring traffic in June, and this is the billing cycle that's had the most traffic so far:
[img]http://img114.imageshack.us/img114/6437/mydesktop1xc8.png[/img]

---

### Post by billgoldberg on 2008-09-02
> **ice60 said:**
> i've been monitoring my bandwidth for a long time and on a normal day i use about 1.5GiB, i don't ever use torrents for anything because i prefer to make one direct connection for my downloads, i watch a lot of movies and download pictures too sometimes lol.

this is what i use, in conky, to measure what i use -
```
${color #909090}Down:$color ${totaldown eth0} ${alignr}${color #909090}Up:$color ${totalup eth0}
```

i'm just starting to get a bit worried my ISP will start capping my bandwidth and want to know if i'm a bandwidth hog or not!

Around 2-3 gigs a day. 

But I have to calculate every download I do because of my 60 gig download and upload combined caps. Needless to say I go over them and pay extra (&#8364;1/1gb, which is stupidly expensive).

Should I don't have caps or better ones, I would consume around 10 gigs a day, maybe more.

---

### Post by ice60 on 2008-09-03
> **doorknob60 said:**
> My ISP shows me that :D They started monitoring traffic in June, and this is the billing cycle that's had the most traffic so far:
[img]http://img114.imageshack.us/img114/6437/mydesktop1xc8.png[/img]

you don't use tiscali in the uk do you? i wonder if they have that graph thing too?

---

### Post by ice60 on 2008-09-03
> **billgoldberg said:**
> Around 2-3 gigs a day. 

But I have to calculate every download I do because of my 60 gig download and upload combined caps. Needless to say I go over them and pay extra (€1/1gb, which is stupidly expensive).

Should I don't have caps or better ones, I would consume around 10 gigs a day, maybe more.

that makes me feel a bit better about my usage :D

things really should be getting better for us, i keep hearing how bandwidth is getting cheaper all the time and that's why places like justin.tv and stickam etc can give away so much bandwidth for free!

---

### Post by jomiolto on 2008-09-04
I've always liked vnstat (available in the Ubuntu repos). It's a very simple console application that monitors web usage and displays statistics.

My daily Internet usage varies quite a lot, depending on what I do. Most of the time I'm seeding a lot of torrents, so even with my slow connection (1Mbit/512kbit), my daily traffic often reaches few gigabytes (current average 3.7GB/day). Occasionally I also watch a lot of flash videos or download some Linux/*BSD/something ISOs and I can reach 12GB in a single day (not very far from the theoretical maximum with this connection :) ).

---

### Post by etnlIcarus on 2008-09-04
My ISP is telling me:

[img]http://img211.imageshack.us/img211/5625/trafficdr0.png[/img]

Granted, I'm only on 10gb/month

---

### Post by Vishal Agarwal on 2008-09-04
I had a connection with fix payment for unlimited downloads. But still I want to measure that how much bandwidth I am using. What should I do ?

---

### Post by kostkon on 2008-09-04
Not much: ~1-2GBs/day.

---

