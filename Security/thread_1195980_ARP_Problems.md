---
title: "ARP Problems"
date: 2009-06-24
forum: Security
---

### Post by joec369 on 2009-06-24
Hello I am a Networking student.  I am working in a lab environment.  I am trying to CAM Flood/ARP Flood a Switch to put it into 'hub' mode.  I'm going to watch it all happen with WireShark and take a look at pcap file after it's all done.  (hopefully learn some stuff)

The Problem:  I can't seem to find a program that will ARP flood my switch.  I looked into _HPing2_ and it seems like it doesn't have that function.  I have also looked into _Ettercap_.  And reading stuff on the internet, people are claiming it does.  They say you have to have a plug in.  My version of Ettercap has 28 plug ins, but nothing to to with ARP flood or even MiTM attack.  I was wondering if I go the wrong version.  

If anyone knows of a good tutorial on how to use plugins in Ettercap, or know of another program I can use I would be greatly appreciated.

---

### Post by Poincare101 on 2009-07-14
I'm having the same problem as you. The ubuntu forums are not a place to post these types of questions in my opinion. But, have you tried out bit twist? If not: [http://bittwist.sourceforge.net/](http://bittwist.sourceforge.net/)

It can do loads of stuff but don't just use like a script kiddie, understand how to works. If you know a bit of C(not exactly a bit), then you can go with send_arp.c and modify to fit your needs. 

Hope this still helps.

---

### Post by bodhi.zazen on 2009-07-14
> **Poincare101 said:**
> The ubuntu forums are not a place to post these types of questions in my opinion.

+1 to that, there are better sources of information then the UF.

Now if you have a support question, how do I install or configure ... that is different.

---

### Post by joec369 on 2009-07-14
Nobody cares about you opinions, I asked questions about Networking Tools in Ubuntu.

---

