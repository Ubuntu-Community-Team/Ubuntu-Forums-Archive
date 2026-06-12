---
title: "load average: 13.29, 13.67, 13.77"
date: 2010-07-11
forum: Server Platforms
---

### Post by ryry46d9 on 2010-07-11
Just as the topic says > load average: 13.29, 13.67, 13.77
little history:

I used to run multiple instances of a python program called B3, off a dual P3 1.0Ghz box. This got upgraded to a single 1.7Ghz celly.

Both boxes are runing a flavor of 10.04.
 
The 1Ghz box had been a 8.04 sever, 9.10 & 10.04 desktop & curently mythbuntu 10.04 

All with out going over 0.10 most of the time. except for the first couple of days building all the programs etc. , but even then it never got much over 1.2 if I recall right. This box lives at my house.

The 1.7 was 8.04-4 server updated to 10.04 server. It lives in a data center rented out as a dedicated, not shared. If I kill all the python scripts it settles back down.

The weird thing is the box is still responsive as if it only had a load of 0.50, but I do receive far to many "SQL has gone away" errors from a add on program for B3 called Echelon 

So my question today is: where do I go from here 

could it be that dual 1Ghz out preforms a 1.7Ghz celly

---

### Post by doogy2004 on 2010-07-11
Load average tells you the average number of processes that are running - [http://immike.net/blog/2007/07/27/what-exactly-is-a-load-average/](http://immike.net/blog/2007/07/27/what-exactly-is-a-load-average/)

---

### Post by ryry46d9 on 2010-07-12
little quote from that page > you shouldn’t be worried about your system’s load unless it is consistently higher than the number of processors (or cores) in your machine.

LOL since it is a single core and the load =13 , I think its safe to be worried :)

---

### Post by cracker on 2010-07-14
If a single python script is causing a load of 13, there is definitely something wrong with it. Get some more info with top, and make sure the code is compatible with the current python version.

---

### Post by ryry46d9 on 2010-07-14
> **cracker said:**
> If a single python script is causing a load of 13, there is definitely something wrong with it. Get some more info with top, and make sure the code is compatible with the current python version.

Top is where I got the load average from
and its around 13 python prepossess but like I stated a few posts back I never had a problem with my **dual 1Ghz** box most of the time when I would peek in on it it was 0.00 

but I think this might be a SQL not possessing fast enough, causing the python to wait in line, hence the higher load.

CPU pull on SQL is never over 5% and for the python never over 4% they all come and go as the should when I press "i" just like they did on the other box 

or just maybe dual 1Ghz P3 coppermines, out crunch a single 1.7Ghz P4 socket 478 celly ](*,)

---

