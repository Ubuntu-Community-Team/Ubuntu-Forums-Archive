---
title: "Streaming MP3 server"
date: 2006-01-06
forum: Server Platforms
---

### Post by Grey on 2006-01-06
Hi all.  I'm trying to find an internet radio server software with a few very specific requirements.

- UDP based, not TCP
- Streams MP3s (possibly with some preprocessing... it would be nice, but not required)
- Open protocol (I am going to be writing a client from scratch... so this is pretty much required)

So... does anyone have any suggestions?  Thanks in advance.  :)

---

### Post by benthai98 on 2006-01-07
I have been playing with a little html based proggy called mp3act. Requires PHP and a MySQL database but seems to do the trick. Not exactly what you are after but may give you some nice ideas...  [www.mp3act.net](www.mp3act.net)

---

### Post by Grey on 2006-01-07
Thanks for the suggestion.  If I wasn't coding a client from scratch, I might actually be very interested in that.

But here's the deal.  I am coding an Internet Radio client for my Nintendo DS.  I lack the low level networking knowledge to write a TCP/IP stack, and I would prefer to use the UDP/IP library that's looking quite promising.  I AM capable of writing software at that level.

So I'm shopping for a server that simply keeps chugging out MP3s through UDP, without much other overhead.  Web browser based streaming is actually a detriment in this particular project.

---

### Post by grendelkhan on 2006-01-08
Have you looked at icecast?  It's in the repos and does what I think you're looking for.

---

### Post by TheJoker on 2006-01-09
Have you had a look at [http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html) the SlimServer?

:)

---

### Post by Grey on 2006-01-10
Thanks for the suggestions guys.  I will definitely check those out, next time I have a chance.  :)

---

### Post by shadowman on 2006-01-11
You might look here as well:  [http://www.pancake.org/zina/](http://www.pancake.org/zina/)

---

### Post by jackdaw on 2006-02-03
you may want to look at gnump3d...works very well, easy to set up...and it's only an apt-get away...

---

