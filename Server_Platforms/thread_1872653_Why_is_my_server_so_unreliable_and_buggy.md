---
title: "Why is my server so unreliable and buggy?"
date: 2011-10-31
forum: Server Platforms
---

### Post by dylan_m on 2011-10-31
I've been running Lubuntu 11.10 as an SSH server on an old Celeron machine. It does work to some extent, but it takes multiple attempts to connect, and once connected, it constantly disconnects/freezes. A session never lasts more than about a minute. The reason I'm using Lubuntu is because I couldn't get wireless networking to work on Ubuntu Server for the life of me, and Lubuntu seems like the next best thing.. (Please don't try and convince me to try again with Ubuntu Server, I've already wasted enough time on that). If I can't get this to work, I may have to use an ethernet connection, forcing me to put the PC in a really unsuitable spot. 

So anyway, what's the issue here, why isn't it running smoothly..?

Thanks

---

### Post by vasile002 on 2011-10-31
can you try pinging it for a while? are there any lost packets? the wifi connection might be bad

---

### Post by knight187 on 2011-10-31
you could just install the Ubuntu desktop and configure the wireless with the gui then have the system auto login so the wireless is activated.

Its a really lazy option... but its getting late.

Cheers All.

---

### Post by HermanAB on 2011-10-31
Sounds like you should try a different WiFi adaptor.

---

### Post by dylan_m on 2011-10-31
I'm only realising this now, but maybe it's because it's running inside a cupboard with mirrors on the outside of the doors.. Could that be interfering with the signal?

But I have tried it outside the cupboard for a while and it was better, but still not 100% reliable..

---

### Post by HermanAB on 2011-10-31
A mirror is a layer of aluminium and a cupboard will quickly become hot and steamy, so you have two reasons not to do that.

---

### Post by Jonathan L on 2011-10-31
> **dylan_m said:**
> ... it was better, but still not 100% reliable..

Hi Dylan

I'd suggest you separate out your ssh server from the networking, and see if your basic networking is reliable.  Is it reliably pingable from other machines?

Could you post the output of ifconfig and nm-tool?  That will give a clear idea of what's up.

Kind regards
Jonathan.

---

### Post by Vegan on 2011-10-31
I use a wired connection for my servers, makes a universe of difference

---

### Post by haqking on 2011-10-31
You have an old celeron machine running latest 11.10 and it is in a cupboard and wifi doesnt work, or remote connections are unreliable ?

and server is unreliable and buggy ?


mmmm i cant think of any reason at all....;-)


Basic troubleshooting, go to ethernet see if it works more reliably, remove it from its dungeon see if it works better etc.

Process of eliminiation

---

