---
title: "WICD problem - Connection Failed: Unable to Get IP Address"
date: 2009-11-11
forum: Testimonials &amp; Experiences
---

### Post by realn on 2009-11-11
Hello all,

 I had the problem from the title - when trying to connect to a WEP wireless network, I kept on having this message.
 The log seemed to indicate that I had a dhcp problem, but still didn't work, when I was setting a fixed IP address.

 I saw various reports of this SYMPTOM, some of them apparently coming from different reasons (bugs in wifi cards drivers, etc.) and I encountered many reports of the problem, of which none of them helped me.

 SOLUTION: the WEP key was a HEX one (and not a passphrase or a shared/restricted one - these are the other two options in wicd).

 I have been trying with the other two, even now not knowing exactly what the difference among the three of them is.
 
 I would like to express an opinion, though: in Linux, after sound management (which I suppose is a more complex problem) I find networking support of the poorest quality ( I gave up network manager a long time ago, when it was frustrating me SOOO MUCH, by freezing the whole computer, by mixing default way of handling network connection with its own - the result - a total crap. I said I would never touch that piece pf c..p even if I had to type 100 commands in CLI).
 Wicd is nice, but it's far from being what I would call a serious piece of software. That's too bad, because it seems all the bits are there, it just needs some re-thinking and polishing. Why can't it show me only the type of encryption used by each network, it beats me. Why is it so slow, sometimes, and refuses to reconnect, it beats me. Anyway, it's better than CLI and WAAY better than NM (which I understand now it "improved a lot". Well, from my point of view it might as well have leaped 100 years forward, it's still behind.

 It's a pity that on the latest KK, with evolving Desktop environments and Plasmoids and stuff, we still lack basic tools.
 I hope it helps at least someone.

 please see also:

[http://ubuntuforums.org/showthread.php?t=948390](http://ubuntuforums.org/showthread.php?t=948390)
[http://ubuntuforums.org/showthread.php?t=1310913](http://ubuntuforums.org/showthread.php?t=1310913)

---

### Post by solwic on 2009-11-11
> **realn said:**
> Hello all,

 I had the problem from the title - when trying to connect to a WEP wireless network, I kept on having this message.
 The log seemed to indicate that I had a dhcp problem, but still didn't work, when I was setting a fixed IP address.

 I saw various reports of this SYMPTOM, some of them apparently coming from different reasons (bugs in wifi cards drivers, etc.) and I encountered many reports of the problem, of which none of them helped me.

 SOLUTION: the WEP key was a HEX one (and not a passphrase or a shared/restricted one - these are the other two options in wicd).

 I have been trying with the other two, even now not knowing exactly what the difference among the three of them is.
 
 I would like to express an opinion, though: in Linux, after sound management (which I suppose is a more complex problem) I find networking support of the poorest quality ( I gave up network manager a long time ago, when it was frustrating me SOOO MUCH, by freezing the whole computer, by mixing default way of handling network connection with its own - the result - a total crap. I said I would never touch that piece pf c..p even if I had to type 100 commands in CLI).
 Wicd is nice, but it's far from being what I would call a serious piece of software. That's too bad, because it seems all the bits are there, it just needs some re-thinking and polishing. Why can't it show me only the type of encryption used by each network, it beats me. Why is it so slow, sometimes, and refuses to reconnect, it beats me. Anyway, it's better than CLI and WAAY better than NM (which I understand now it "improved a lot". Well, from my point of view it might as well have leaped 100 years forward, it's still behind.

 It's a pity that on the latest KK, with evolving Desktop environments and Plasmoids and stuff, we still lack basic tools.
 I hope it helps at least someone.

 please see also:

[http://ubuntuforums.org/showthread.php?t=948390](http://ubuntuforums.org/showthread.php?t=948390)
[http://ubuntuforums.org/showthread.php?t=1310913](http://ubuntuforums.org/showthread.php?t=1310913)

My experience with wicd wasn't very positive, either.  Stick with NM - it has improved...a lot.

---

### Post by Newmanbroken on 2010-10-04
Thank you realn,
Your solution solved my connection problem instantly.

---

### Post by SquaredRoot on 2011-05-31
i know this post is really old. but dude, i've been scouring the internet looking for a fix to this same exact problem and after 2 months you gave me the exact answer. thank you so much ! im finally online in ubuntu !!! wicked ! love yah bro


> **realn said:**
> Hello all,

 I had the problem from the title - when trying to connect to a WEP wireless network, I kept on having this message.
 The log seemed to indicate that I had a dhcp problem, but still didn't work, when I was setting a fixed IP address.

 I saw various reports of this SYMPTOM, some of them apparently coming from different reasons (bugs in wifi cards drivers, etc.) and I encountered many reports of the problem, of which none of them helped me.

 SOLUTION: the WEP key was a HEX one (and not a passphrase or a shared/restricted one - these are the other two options in wicd).

 I have been trying with the other two, even now not knowing exactly what the difference among the three of them is.
 
 I would like to express an opinion, though: in Linux, after sound management (which I suppose is a more complex problem) I find networking support of the poorest quality ( I gave up network manager a long time ago, when it was frustrating me SOOO MUCH, by freezing the whole computer, by mixing default way of handling network connection with its own - the result - a total crap. I said I would never touch that piece pf c..p even if I had to type 100 commands in CLI).
 Wicd is nice, but it's far from being what I would call a serious piece of software. That's too bad, because it seems all the bits are there, it just needs some re-thinking and polishing. Why can't it show me only the type of encryption used by each network, it beats me. Why is it so slow, sometimes, and refuses to reconnect, it beats me. Anyway, it's better than CLI and WAAY better than NM (which I understand now it "improved a lot". Well, from my point of view it might as well have leaped 100 years forward, it's still behind.

 It's a pity that on the latest KK, with evolving Desktop environments and Plasmoids and stuff, we still lack basic tools.
 I hope it helps at least someone.

 please see also:

[http://ubuntuforums.org/showthread.php?t=948390](http://ubuntuforums.org/showthread.php?t=948390)
[http://ubuntuforums.org/showthread.php?t=1310913](http://ubuntuforums.org/showthread.php?t=1310913)

---

