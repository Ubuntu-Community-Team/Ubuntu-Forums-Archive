---
title: "suspicious network traffic..."
date: 2011-01-01
forum: Security
---

### Post by daniel_w93 on 2011-01-01
Hi everyone,
I am a little troubled...because for quite some time now, every time I start up my computer the outgoing internet traffic soars up to a steady 70KiB/s... I've had it running for about 2 1/2 hours now and the total sent traffic is 347MB even though I haven't been uploading anything.
I can't imagine that this kind of high traffic is normal and would like to ask you if you have any suggestions for me.
Thanks in advance

---

### Post by nerdy_kid on 2011-01-01
have you ever downloaded any .debs from the web?
You could install wireshark (sudo apt-get install wireshark) and get a nice packet dump to see where it is all going.

---

### Post by uRock on 2011-01-01
If an application is uploading, then you should be able to catch the traffic with Wireshark. It is in the repositories, so it is easy to install, and will show everything in the packet's headers. This will tell the destination and the protocol being used, which may help with finding what is running. The biggest downfall is that you will be allowing the malware application do its thing while you are monitoring it.

---

### Post by daniel_w93 on 2011-01-02
mhhh it seems to just have been Ubuntu One....cause after I disabled it in Startup Applications I haven't had the problem.

Also I ran this command to double check 
```
sudo tcpdump -i eth0 -w /tmp/test -c 500 tcp or udp
```
and didn't find anything suspicious there.
So I guess this thread is solved :)

---

### Post by The Cog on 2011-01-02
Another application that I like to use occasionally to see what's going on is etherape. It's very much simpler than wireshark if you just want to see who's talking to who.

---

### Post by The Cog on 2011-01-02
Another application that I like to use occasionally to see what's going on is etherape. It's very much simpler than wireshark if you just want to see who's talking to who.

---

### Post by uRock on 2011-01-02
> **The Cog said:**
> Another application that I like to use occasionally to see what's going on is etherape. It's very much simpler than wireshark if you just want to see who's talking to who.
I haven't seen that one yet. Will install and check it out.

Edit: I like that one a lot.:p

---

### Post by inobe on 2011-01-02
> **The Cog said:**
> Another application that I like to use occasionally to see what's going on is etherape. It's very much simpler than wireshark if you just want to see who's talking to who.

oh my, that thing is slick :-)

---

### Post by nerdy_kid on 2011-01-02
> **The Cog said:**
> Another application that I like to use occasionally to see what's going on is etherape. It's very much simpler than wireshark if you just want to see who's talking to who.

oo I like that :D

---

### Post by daniel_w93 on 2011-01-03
oh that really is great! 
I like it :)

---

