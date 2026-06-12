---
title: "Why is MS trying to access my Port 1863?"
date: 2007-06-21
forum: The Cafe
---

### Post by coolclassic on 2007-06-21
Nothing better to do but read the stats in my rooter. One of these firewall stats show that 207.46.108.62 (which is MSN) had attempted to access that port (packets in 52, packets out 48 ). As I am 100% kubuntu and have nothing to do with MS, why is this connection being attempted?

---

### Post by PartisanEntity on 2007-06-21
Do you have/use an MSN messenger account?

---

### Post by coolclassic on 2007-06-21
No account of any kind with MS

---

### Post by prizrak on 2007-06-21
Some malware can use that port as well perhaps someone got one and it's random scanning machines?

---

### Post by coolclassic on 2007-06-21
But the Ip is identified as microsoft so unlikely to be malware.

---

### Post by some_random_noob on 2007-06-21
Surely it must be your IM client? Is it a hotmail account?

---

### Post by Ultra Magnus on 2007-06-21
It seems to me that this is probably part of a wider conspiracy - Microsoft is systematically scanning everyones ports so that it can identify all those people who don't use vista to run some kind of auto-assimilation program to force everyone to upgrade to vista!

---

### Post by cunawarit on 2007-06-21
> **Ultra Magnus said:**
> It seems to me that this is probably part of a wider conspiracy - Microsoft is systematically scanning everyones ports so that it can identify all those people who don't use vista to run some kind of auto-assimilation program to force everyone to upgrade to vista!

It is the AYLABTU program, Microsoft has set us up the bomb! All You Linux Are Belong to Us In Progress!!!

Seriously, loose the paranoia, someone may be up to something odd, but it is very unlikely to be Microsoft. Even if they wer up to something dodgey, they have much bigger targets than some random guy's little PC.

---

### Post by bchaffin72 on 2007-06-21
From what  I found, port 1863 is used by MS Messenger Service. Perhaps the site is trying to determine if you have it installed/running, despite the fact that you are not using Windows.

---

### Post by blah blah blah on 2007-06-21
> **Ultra Magnus said:**
> It seems to me that this is probably part of a wider conspiracy - Microsoft is systematically scanning everyones ports so that it can identify all those people who don't use vista to run some kind of auto-assimilation program to force everyone to upgrade to vista!

So much for running a business to make money.

---

### Post by smoker on 2007-06-21
> **coolclassic said:**
> But the Ip is identified as microsoft so unlikely to be malware.

it's maybe ms wga authenicating your kubuntu install:popcorn:

---

### Post by stmiller on 2007-06-21
Windows XP constantly sends packets from your computer to Microsoft. These come from different 'MS services' running in the background. Who knows...

One of the many reasons to stay away from MS.

---

### Post by jfinkels on 2007-06-21
> **smoker said:**
> it's maybe ms wga authenicating your kubuntu install:popcorn:

[http://www.linuxgenuineadvantage.org/](http://www.linuxgenuineadvantage.org/)

---

### Post by FuturePilot on 2007-06-21
They're trying to figure out who to sue when, I mean *if* they file their so called 200 some patent infringements law suite against Linux.:lolflag:

---

### Post by purdy hate machine on 2007-06-22
> **coolclassic said:**
> Nothing better to do but read the stats in my rooter. 

It’s a special service provided by MS, the purpose of which is to subtly inform you that you have far too much free time on your hands.

---

### Post by steven8 on 2007-06-22
If your not careful. . .Microsoft will try to enter any unguarded ports. . .

---

### Post by coolclassic on 2007-06-22
The assumption here is that I am using homail or instant messaging. I am not using either. As the ip has been confirmed as MS in source then MS must be trawling the internet looking for info. Paranoia now, is MS trawling for illegal copies?

---

### Post by PartisanEntity on 2007-06-22
> **coolclassic said:**
> The assumption here is that I am using homail or instant messaging. I am not using either. As the ip has been confirmed as MS in source then MS must be trawling the internet looking for info. Paranoia now, is MS trawling for illegal copies?

Do you share your PC or IP-range? Perhaps someone else used the same network or IP to access MS services earlier.

---

### Post by brim4brim on 2007-06-22
You don't have anything running in WINE do you?

I don't know why Ms would want to access your computer.  You could always ask them.

---

### Post by samjh on 2007-06-22
> **coolclassic said:**
> Nothing better to do but read the stats in my rooter. One of these firewall stats show that 207.46.108.62 (which is MSN) had attempted to access that port (packets in 52, packets out 48 ). As I am 100% kubuntu and have nothing to do with MS, why is this connection being attempted?If your ISP assigns dynamic IP addresses, your IP at the time could have matched the IP of another user who accessed MSN services earlier.  (As others have said, port 1863 is used by MSN Messenger services.  GAIM uses that port to access MSN services too.)

PartisanEntity's theory is also a possibility.

I doubt MSN is trawling IP addresses, as that makes no business or operational sense whatsoever.

---

### Post by Enverex on 2007-06-22
> **PartisanEntity said:**
> Do you share your PC or IP-range? Perhaps someone else used the same network or IP to access MS services earlier.

Can you paste the output of "netstat" so we can see exactly what's going on? (hard to work out with bits and pieces of info).

---

