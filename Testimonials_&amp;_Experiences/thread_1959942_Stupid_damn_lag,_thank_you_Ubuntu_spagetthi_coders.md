---
title: "Stupid damn lag, thank you Ubuntu spagetthi coders"
date: 2012-04-16
forum: Testimonials &amp; Experiences
---

### Post by Mikler on 2012-04-16
Hello all..
I'm new here and I have no idea if I'm posting in the right forum.
Well the story goes like this : before I had an online game which was  based on TCP/IP (not udp). It was a real time game that I developed myself in Java. It worked fine for several years until I decided to upgrade to Ubuntu.
After this, everything started to lag heavily. After much investigation I found out that Ubuntu had raised the TCP DELAYED  ACK from 40 MS to 200 MS..hmm who cares you would prop say.
But this means that every single online realtime app  previously running smoothly and fast, would now run with the speed of a snail.
Well you would probably tell me that : "TCP IP is NOT designed to real time games, you should use UDP.".
Well if TCP by default had a 200 MS lag between each packet your right. But that should be something that you should be able to customize. Before TCP/IP was fast enough. Why slow it down to a crawl ?
As it is now Ubunto TCP/IP is customized to movie Streaming..(porn).YOU CANT JUST RANDOMLY CHANGE BEHAVIOR OF A PROTOCOL.
DId you never think about what this change would mean to other people ?
I've always heard that Linux is much more customizable than windows. BULL. THis one you cant even change in linux (but you can in windows).

---

### Post by NadirPoint on 2012-04-16
Sorry, but I can't seem to imagine how to quantify the relative value of porn vs. games.

Maybe you could try tuning your IP stack to behave as desired?

---

### Post by haqking on 2012-04-16
```
tcp_nodelay
```

---

### Post by jwbrase on 2012-04-16
> **Mikler said:**
> YOU CANT JUST RANDOMLY CHANGE BEHAVIOR OF A PROTOCOL.

They didn't. The TCP protocol allows for a delayed ACK to be up to 0.5 seconds (500 ms), as long as an ACK is sent for every second packet received. As Haqking said, TCP_NODELAY may help you.

---

### Post by lovinglinux on 2012-04-16
Moved to testimonials, because it didn't sound like you was asking for help.

---

### Post by haqking on 2012-04-16
> **jwbrase said:**
> They didn't. The TCP protocol allows for a delayed ACK to be up to 0.5 seconds (500 ms), as long as an ACK is sent for every second packet received. As Haqking said, TCP_NODELAY may help you.

for some reason i cant capitalise it...LOL

I can capitalise but when i try to capitalise TCP_NODELAY it goes back to lower case...LOL

Edit ha it worked in this post,. i cant go back and edit original,. it wont have it...LOL

oh well

---

### Post by jadtech on 2012-04-16
porn ??? 

ok who was in charge of sending that invitation .

---

### Post by overdrank on 2012-04-16
On that note, thread closed. :)

---

