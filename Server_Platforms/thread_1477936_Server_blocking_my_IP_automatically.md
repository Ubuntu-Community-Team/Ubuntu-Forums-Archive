---
title: "Server blocking my IP automatically?"
date: 2010-05-09
forum: Server Platforms
---

### Post by Dirtycash on 2010-05-09
Hello all,

Recently I got bored and decided to setup a home server using 10.04. So far everything is working good (Samba, rtorrent, ftp, apache, etc...).  My reason for starting this thread is as of two days ago I am noticing some strange behavior.

I have reproduced this twice.  I ssh into my server from my local network and use screen to startup rtorrent.  Throughout the day I will add/delete torrents to a folder in my samba share and access files generally without error.  The problem happens when I logout of the server leaving rtorrent running for a long period of time (first time I went shopping, second time I went to sleep), **when I try to log back in to the server I get a connection timed out**. I can't ssh or ping the server.  Its almost like some security setting that I know nothing about is running and blocking my IP because I logged out and didn't log back in for a while.  To test this I changed my static (local network) IP and EVERYTHING WORKED!  

So after reading this short novel of mine(I have more info if you want :P).  I have looked for a day or so for what could be blocking my local IP and have come up with nothing.  I'm fairly literate with Linux so feel free to throw advanced mind-boggling solutions my way (if you must).  Thanks in advance for all help and insight.  

FYI, my temp workaround is changing my laptop's IP everytime this happens, the problem is I will eventually run out of IPs.  Then i guess I could change to the 10.x.x.x network setup :P

---

### Post by Ryan Dwyer on 2010-05-09
I don't know much about the specifics of how Linux does its networking, but I'm guessing it's reaching the max allowed limit of TCP connections. Changing the IP restarts the networking service and clears the queue.

Maybe you could decrease or set a limit on the max allowed connections in rtorrent.

---

