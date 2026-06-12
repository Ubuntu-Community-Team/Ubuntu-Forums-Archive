---
title: "transmission - raper of bandwidth"
date: 2008-01-15
forum: The Cafe
---

### Post by koshatnik on 2008-01-15
Whats the deal with Transmission? I'm downloading a torrent at some stupidly slow speed, like 8kb/s and uploading at say 12kb/s and my entire bandwidth is royally stuffed - browsing the internet slows right down to a crawl... anyone else get this? 

As soon as I shut down Transmission PING browsing is back to super fast. Im on a decent cable line too.. 8meg.

Why?

---

### Post by koleoptero on 2008-01-15
I had absolutely no probs with transmission, it worked like a charm. If it had all the options I needed I would use it still. Perhaps you haven't configured everything as you should...

---

### Post by LookTJ on 2008-01-15
If you are in the USA, I assume most cable companies(like Comcast) restricts p2p?

---

### Post by koshatnik on 2008-01-15
No, Im in the UK. I dont have this problem with other bit torrent clients, just transmission. I know the obvious answer is, "well use another one" but I like transmission and I still want to know why its doing it :)

---

### Post by LookTJ on 2008-01-15
> **koshatnik said:**
> No, Im in the UK. I dont have this problem with other bit torrent clients, just transmission. I know the obvious answer is, "well use another one" but I like transmission and I still want to know why its doing it :)Did you configure it? If so, how is it configured?

---

### Post by rikdeek on 2008-10-26
Hello,
I have this problem too.
Even if the upload and download speeds are WELL within the limits of my connection (even if I throttle them down in the options), Transmission seems to hog all of the bandwidth of my connection. When using it I cannot browse the net, nor can anyone else on my network.

I did not configure Transmission, it is set at the installed defaults. Am I meant to set something somewhere? (Surely it should be set to sensible settings by default?)

Any help at all with this would be great, as I also like the simple interface of Transmission, but I'll have to change if I can't sort this problem out.

Thanks very much in advance,
 - Rik

---

### Post by noremac on 2008-10-26
I have had this problem, but on Deluge. And it seems to only do this on certain torrents, not all the time. Kind of odd.

-C

---

### Post by mentallaxative on 2008-10-26
I haven't had any major slowdown with Transmission. Have you tried other bittorrent clients to see if you get the same effect?

---

### Post by I-75 on 2008-10-26
I have the opposite problem.

I think with Vuze/Azureus on Windows, my internet slows down. I have noticed no problems with Transmission on Ubuntu.

---

### Post by sn0m on 2008-10-26
I had the same problem,changed to deluge and found peace. Maybe Deluge should be by default in Ubuntu rather then Transmission.

---

### Post by mips on 2008-10-26
Ktorrent is still my favourite.

---

### Post by billgoldberg on 2008-10-26
> **koshatnik said:**
> Whats the deal with Transmission? I'm downloading a torrent at some stupidly slow speed, like 8kb/s and uploading at say 12kb/s and my entire bandwidth is royally stuffed - browsing the internet slows right down to a crawl... anyone else get this? 

As soon as I shut down Transmission PING browsing is back to super fast. Im on a decent cable line too.. 8meg.

Why?

You have too much peers.

Limit the number of peers to something around 50 and you won't have that problem.

My connection gets shaky (the upload and download speeds don't matter) when I get more than 50 seeds.

Most likely because my router sucks, although I'm not sure.

Also, I'm on ADSL. That means the the less I upload, the faster I download. Most people will says that the more you upload the faster you download, this isn't true for adsl.

---

### Post by Polygon on 2008-10-26
ive heard its because your session table in your router gets filled up if you allow too many peers so then your internet literally slows to a crawl or stops.

---

### Post by rikdeek on 2008-10-27
> **sn0m said:**
> I had the same problem,changed to deluge and found peace. Maybe Deluge should be by default in Ubuntu rather then Transmission.

I did the same, no problems, nice client. I'll keep my eye on the number of connections.

Thanks guys!

I also think that Deluge should be default in Ubuntu, but I would guess that Transmission is the lightest on rescources, so that's a good reason to keep it as the default.

---

### Post by perfectska04@hotmail.com on 2008-10-27
> **sn0m said:**
> I had the same problem,changed to deluge and found peace. Maybe Deluge should be by default in Ubuntu rather then Transmission.

Weird, the opposite happened to me. I used to swear by deluge ever since it came out, but after their buggy release of version 1.0, I tried transmission and all of my speed/bandwidth/port forwarding issues were fixed by it.

---

### Post by BGFG on 2008-10-27
> **billgoldberg said:**
> You have too much peers.

Limit the number of peers to something around 50 and you won't have that problem.

My connection gets shaky (the upload and download speeds don't matter) when I get more than 50 seeds.

Most likely because my router sucks, although I'm not sure.

Also, I'm on ADSL. That means the the less I upload, the faster I download. Most people will says that the more you upload the faster you download, this isn't true for adsl.

Hi,
I don't think peers is the problem. My max peer# is 200. As i type i have a torrent coming down and my bandwith is only 512kbps.

You could try limiting your upload speed(but please remember to seed once your torrent is finished:) )
and lowering your number of upload slots.
If these settings are not familiar i use deluge. Faster and more configurable.

---

### Post by BGFG on 2008-10-27
> **perfectska04@hotmail.com said:**
> Weird, the opposite happened to me. I used to swear by deluge ever since it came out, but after their buggy release of version 1.0, I tried transmission and all of my speed/bandwidth/port forwarding issues were fixed by it.

1.0.3 is pretty stable and fast, you might consider checking it out again :)

---

### Post by Lord DarkPat on 2008-10-27
This happens to me in KTorrent.
Wait... if the torrent is at 40 kbps, then WHY ARE MY INTERNETS SLOW?
:|

---

### Post by handy on 2008-10-27
I have been using Transmission for over a year on Mac & various distro's without there ever being a bandwidth problem.  Transmission just works for me.

---

### Post by wolfen69 on 2008-10-27
> **koleoptero said:**
> I had absolutely no probs with transmission, it worked like a charm. If it had all the options I needed I would use it still. Perhaps you haven't configured everything as you should...

you will probably like transmission that comes with ibex. more options. that said, i've never had a problem with it. btw koleoptero, what options do you *need*?

---

### Post by chyess on 2009-10-18
I have the same problem, using Fedora 11. Did an strace on the process and it looks like it's polling a ton.

```
[chyess@kush ssh]$ strace -p 32205
Process 32205 attached - interrupt to quit
restart_syscall(<... resuming interrupted call ...>) = 1
ioctl(25, FIONREAD, [64])               = 0
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 9) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 650) = 1 ([{fd=25, revents=POLLIN}])
ioctl(25, FIONREAD, [64])               = 0
read(25, "\2\0\0\0\2\0\0\0\0\0\0\0000\0\0\0The Tournament 20"..., 1024) = 64
read(25, 0x16f2450, 1024)               = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 649) = 1 ([{fd=25, revents=POLLIN}])
ioctl(25, FIONREAD, [64])               = 0
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 9) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 152) = 1 ([{fd=25, revents=POLLIN}])
ioctl(25, FIONREAD, [64])               = 0
read(25, "\2\0\0\0\2\0\0\0\0\0\0\0000\0\0\0The Tournament 20"..., 1024) = 64
read(25, 0x16f2450, 1024)               = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 152) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 308) = 1 ([{fd=25, revents=POLLIN}])
ioctl(25, FIONREAD, [64])               = 0
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 9) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 191) = 1 ([{fd=25, revents=POLLIN}])
ioctl(25, FIONREAD, [64])               = 0
read(25, "\2\0\0\0\2\0\0\0\0\0\0\0000\0\0\0Kung Fu Flid 2009"..., 1024) = 64
read(25, 0x16f2450, 1024)               = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 191) = 1 ([{fd=25, revents=POLLIN}])
ioctl(25, FIONREAD, [64])               = 0
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 2) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\22\0\30\0 \0\340\2(\0\0\0)\0\0\0 \1\0\0\22\0\0\0\20\2\0\0\0\0\0\0\0"..., 156}, {NULL, 0}, {""..., 0}], 3) = 156
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\322\7` \0\340\2(\0\0\0\327\233\363\2\0\204Z\2\0\0\0\0\220\232\0\3\0\0\0\0\26"..., 4096) = 112
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\16\0\2\0 \0\340\2"..., 8}, {NULL, 0}, {""..., 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\30\v`\0\0\0\0<\1\0\0\375\6D\0\300\2\247\1\0\0\0\0\200\33\234\3\0\0\0\0"..., 4096) = 32
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"(\0\4\0 \0\340\2<\1\0\0\0\0\0\0"..., 16}, {NULL, 0}, {""..., 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\f`\0\0\0\0 \0\340\2\375\6D\0`\354|\0\0\0\0\0(\0\0\0\0\0\0\0"..., 4096) = 32
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"5\30\4\0 \271\340\2 \0\340\2d\2\37\0\227\4\5\0!\271\340\2 \271\340\2\7\1\0\0\0"..., 15724}, {"\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096}, {""..., 0}], 3) = 19820
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\227\4\6\0I\271\340\2H\271\340\2\5\1\0\0\0\1\0\0\1\0\0\0\227\5\4\0-\271\340\2@"..., 10220}, {NULL, 0}, {""..., 0}], 3) = 10220
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 0) = 1 ([{fd=25, revents=POLLIN}])
ioctl(25, FIONREAD, [64])               = 0
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(25, "\2\0\0\0\2\0\0\0\0\0\0\0000\0\0\0Kung Fu Flid 2009"..., 1024) = 64
read(25, 0x16f2450, 1024)               = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"$\4\1\0&\271\2\0<\1\0\0"..., 12}, {NULL, 0}, {""..., 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1/a\0\0\0\0<\1\0\0\5\0\240\5\267\0072\3\267\0072\3\20\0\0\0\0\0\0\0"..., 4096) = 32
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"&\4\2\0\5\0\240\5"..., 8}, {NULL, 0}, {""..., 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0010a\0\0\0\0<\1\0\0003\0\240\5\267\0072\3k\2;\2\20\0\0\0\1\0\0\0"..., 4096) = 32
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"&\4\2\0003\0\240\5"..., 8}, {NULL, 0}, {""..., 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0011a\0\0\0\0<\1\0\0\0\0\0\0\267\0072\3k\2\"\2\20\0\0\0\1\0\0\0"..., 4096) = 32
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"%\4\1\0"..., 4}, {NULL, 0}, {""..., 0}], 3) = 4
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 126) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 354) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 315) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 801) = 1 ([{fd=25, revents=POLLIN}])
ioctl(25, FIONREAD, [64])               = 0
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 9) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 257) = 1 ([{fd=25, revents=POLLIN}])
ioctl(25, FIONREAD, [64])               = 0
read(25, "\2\0\0\0\2\0\0\0\0\0\0\0000\0\0\0The Tournament 20"..., 1024) = 64
read(25, 0x16f2450, 1024)               = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 256) = 1 ([{fd=3, revents=POLLIN}])
read(3, "\241 2a \0\340\2\371\0\0\0\6\1\0\0\244\37\0\0 \0\340\2\0\0\0\0\0\0\0\0"..., 4096) = 32
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\31\0\v\0<\1\0\0\0\0\30\0! \0\0<\1\0\0\371\0\0\0\6\1\0\0\244\37\0\0 "..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 227) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x127e914, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=26, events=POLLIN}, {fd=17, events=POLLIN}, {fd=6, events=POLLIN}, {fd=25, events=POLLIN}], 6, 81^C <unfinished ...>
Process 32205 detached
```

---

### Post by chyess on 2009-10-18
Well, nevermind all that... I can run transmission just fine in Ubuntu as a virtualbox guest, and I get basically the same results from strace there.

---

### Post by cariboo on 2009-10-18
@chyess

I can see you are a new member, It would be much better if you asked your questions in the support forums, instead of digging up old threads and appending comments that really have nothing to do with the question.

This thread is closed.

---

