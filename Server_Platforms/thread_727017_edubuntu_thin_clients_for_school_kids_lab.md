---
title: "edubuntu thin clients for school kids lab"
date: 2008-03-17
forum: Server Platforms
---

### Post by fourthofjuly on 2008-03-17
setting up a new computer lab with 35 systems for kids - nursery to Grade V

have about 65 old systems running Win 98 / XP - a mix of Intel P3 & Celeron systems mostly with 128 MB RAM.

consultant has recommended a thin client setup (Windows server based) which will cost 35% less than buying new Intel Dual Core machines.

since kids will mostly be learning typing, paint & typical games... edubuntu seems to be the best bet here... brings down cost to almost 50%.

we would like all 35 machines to run with no compromise on speed.

following setup has been recommended:

One new IBM x3400 Intel Xeon Quad core server 1.6 GHz , 1 GB RAM, 250 GB 7200 RPM SATA HDD

35 new thin client ethernet cards

35 new lcd monitors

35 of our old systems

we have the following queries...

1) all our existing systems are networked & have lan cards - can they be re-used as thin client cards or should we buy new cards?

2) should we choose gigabit lan? - more clients shall be added in the future

3) since we will have a hybrid client environment of P3s and Celerons with different RAM sizes, how do we configure them separately on the Edubuntu server?

4) are we missing / overlooking something?

please help...

thanks in advance & regards,

devang.

---

### Post by fourthofjuly on 2008-03-17
anyone, please?

---

### Post by Tomatz on 2008-03-17
This might help :)

[https://wiki.ubuntu.com/ThinClientHowto](https://wiki.ubuntu.com/ThinClientHowto)


[http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted) (more relevant)

---

### Post by fourthofjuly on 2008-03-18
thanks a lot, but can we have specific details related to my questions please?

regards,

devang.

---

### Post by Tomatz on 2008-03-18
Sorry should have elaborated.  All the info you asked for is in those links.

Just have a read :)

---

### Post by neerajga on 2008-03-19
Hi Devang:

Where are you located? Please call me on Mumbai 98201 46118 or give your contact number, we can help you on this. Thin Client cards is our primary business.

Regards,
Neeraj Saraf

---

### Post by maybeway36 on 2008-03-23
1) The exsisting cards should work
2) A gigabit connection from server to switch would be a good idea; the clinets should not need more than 100MBit
3) You don't need to; they will work out of the box.

---

### Post by fourthofjuly on 2008-03-24
> **neerajga said:**
> Hi Devang:

Where are you located? Please call me on Mumbai 98201 46118 or give your contact number, we can help you on this. Thin Client cards is our primary business.

Regards,
Neeraj Saraf
thanks Mr. Saraf, we are located at Vapi in South Gujarat.

we have our consultant working on this, but we need support on the OS side specifically for Edubuntu including installation of the server and thin clients...

if you provide support for Edubuntu, do let us know and we will get in touch with you...

thanks & regards,

devang.

---

### Post by rickyjones on 2008-03-24
I would install more memory in that terminal server. Maybe up it to 4GB to be on the safe side. Especially if your thin clients will be running the programs on the server. If all programs are running on the clients then this might not be necessary, but I thought that I'd mention it to you.

-Richard

---

### Post by fourthofjuly on 2008-03-24
> **rickyjones said:**
> I would install more memory in that terminal server. Maybe up it to 4GB to be on the safe side. Especially if your thin clients will be running the programs on the server. If all programs are running on the clients then this might not be necessary, but I thought that I'd mention it to you.

-Richard
can programs stored on the server be run on client machines? 

and i thought, all processing is done only on the server?

please clarify...

thanks & regards,

devang.

---

### Post by rickyjones on 2008-03-24
I could be wrong here so please take my information lightly.

If I recall correctly thin clients can have two different operations. One one hand they can connect to a terminal server. The terminal server would be configured in such a way that all programs are running on the server, in its memory. All processing is done on the server. Another way is to serve applications to the thin client, so processing/memory is done/used on the client. 

I can't remember how to configure each.

If I am right then the Linux LTSP (Linux Terminal Server Project) is supposed to be the first one, where all processing/memory is done on the server. Think of it as VNCing into the server and running a program.

I could be wrong. If so I look for other experts to correct me. This is just based on what I've read a few years ago.

-Richard

---

### Post by SmarterThanMyPhone on 2008-03-26
from my experience with thin clients, its best practice to run everything server side. We use pretty high end thin clients at work, but they still wont hold a candle to a good beefy server.

---

