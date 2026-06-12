---
title: "UDP Failure, only first packet comes through"
date: 2010-11-23
forum: Server Platforms
---

### Post by xantios on 2010-11-23
Hi all!

I have a bit of a problem with my server at the moment,
First of all its running Ubuntu 8.04 (Server edition) and it works perfect just like you would expect. 

Only when i want to toss UDP to it its a total pain in the {BEEP},
I was trying to set up a CS 1.6 Server but that was failing big time, so i've went through some testing:

I test using 2 ubuntu boxes.

on the first server (the one with the problem) i run:
```
nc -lup 2000 
```
then on the second server:
```
 nc -u hostname.server.com 
```

i can send exactly ONE package from my Second server to the other one, also i cant send anypackets the other-way arround (from the problem-server to the other one)

Also there is no firewall, the 'problem-server' is directly connected to the internet, so i guess i cant be a LAN Problem ?

Also when i switch roles (Second server listening,problem-server connecting to it it all works like a charm).

Long-post-short:

- My server cant receive UDP Packets
- My server cant send UDP Packets in some case's
- I dont know what the &#)( is going on.

Any suggestions ?
I can really use some help on this one!

---

### Post by xantios on 2010-11-24
I've been testing arround with other ports and also TCP-Dump (Name doesnt imply but it seems to be able to dump UDP to)

There is just one packet incoming, even when i toss a whole bunch of them to the server.

Still dont have a clue what could be causing this,
and i'm kind of getting crazy over this.

Anyone has any clue how this could happen?

---

### Post by xantios on 2010-11-25
Anyone ? C'mon... there bust me somebody who knows this ?

---

### Post by xantios on 2010-11-26
Nevermind already fixed it, Thanks for all the great support!!

---

