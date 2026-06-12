---
title: "software to document download speed?"
date: 2013-04-09
forum: The Cafe
---

### Post by goodbye-windows(tm) on 2013-04-09
My ISP is giving me a bunch of crap about the performance of their network and it's ability to deliver promised download speeds. Obviously, they can't be at my computer 24/7, so they don't see malfunctions, drop outs and file transfers that just stop without warning.

Is there any software that can monitor the network throughput and issue a report that can be sent to the ISP's tech department??? Ideally this would generate a text file, so it's easily transferred (small file as opposed to a video) and give the approximate same information as the Network History trace in the System Monitor application. 

Must be open source.

Appreciate any nudge in the right direction.......

TIA

Art

---

### Post by mike acker on 2013-04-10
[http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by goodbye-windows(tm) on 2013-04-10
> **mike acker said:**
> [http://www.speedtest.net/](http://www.speedtest.net/)

Thanks Mike, but speedtest.net does me no good. It's sends 6 to 10 seconds worth of data and my failure more does not show up in such a small sample period.

I need something that runs in my computer and can monitor incoming data rates over periods of an hour or more. 

Speedtest.net gives me a download rate of .74 Mps, **my ISP promises .768 Mps**, but the actual download speed is typically .37 to .5 Mps when taken over a 1/2 hour period. When the System monitor is running, it shows long periods of zero throughput, which is the problem. 

Any other ideas???

Art

PS: the ISP in question is Fairpoint.net (Fairpoint Communications), nuff said.

---

### Post by ibjsb4 on 2013-04-10
What about this ..

[http://ubuntuforums.org/showthread.php?t=2003017](http://ubuntuforums.org/showthread.php?t=2003017)

---

### Post by goodbye-windows(tm) on 2013-04-12
> **ibjsb4 said:**
> What about this ..

[http://ubuntuforums.org/showthread.php?t=2003017](http://ubuntuforums.org/showthread.php?t=2003017)

Yes, that worked great. Has light processor usage too!!! Many thanks.

Art

---

### Post by CharlesA on 2013-04-13
Just giving a +1 to vnstat. I run it on my servers and it's quite handy. :)

---

### Post by Jonny87 on 2013-04-13
> **goodbye-windows(tm) said:**
> ...so they don't see malfunctions, drop outs and file transfers that just stop without warning..

It may pay to look into your router that you're using, especially if it's one that you were given by your ISP with your internet plan. There are some out there that will restart themselves every so often. I had one that did this and it frustrated me to no end.

Also if you are getting regular drop outs/poor speeds, keep fighting your ISP to investigate it. I was having some trouble with my connection awhile ago and my ISP tried telling me that it was a fault on my end, that my ethernet cable or router wasn't plugged in correctly. Despite me trying to tell them that I know a thing or two about computers/IT, they insisted that the fault was at my end. To be 100% sure I rechecked over every aspect of my set up and sure enough everything was fine. I told them, I can ping my router I can ping other devices but I can't ping their web server, so the issue is on the other side of the router. They didn't listen. Eventually they said they would send out a technician to investigate. He later rang me from the local exchange telling me that he had found the fault. It was faulty port at the exchange.

My point is that it can be a fight with the ISP, but if you're sure that it's their fault then keep pressing on.

---

### Post by ibjsb4 on 2013-04-13
Welcome, don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by goodbye-windows(tm) on 2013-04-13
> **Jonny87 said:**
> It may pay to look into your router that you're using, especially if it's one that you were given by your ISP with your internet plan. 
There are some out there that will restart themselves every so often. I had one that did this and it frustrated me to no end.

Also if you are getting regular drop outs/poor speeds, keep fighting your ISP to investigate it. 

Eventually they said they would send out a technician to investigate. He later rang me from the local exchange telling me that he had found the fault. It was faulty port at the exchange.

My point is that it can be a fight with the ISP, but if you're sure that it's their fault then keep pressing on.

WOW, your description of the issue I'm having is exactly as you described. ISP says nothing is wrong and the network traffic flow is up and down. I posted a few screen captures showing my network traffic in a new post on this forum last night.

[B]Have a look at the attachment here:

[http://ubuntuforums.org/showthread.php?t=2135029](http://ubuntuforums.org/showthread.php?t=2135029)[/B]

The information in the thread states that my wife's Win 7 computer downloads properly, but that 2 Linux machines don't. But, before they did some very recent changes in the network, my wife's computer and my Linux computers both had the same failure modes (as shown in the pdf attachment to the thread above). They did something (very very recently) to the network to make the Win 7 machine download properly, but the Linux machines are still failing to download properly.

Appreciate any comments.

Art

---

### Post by gordintoronto on 2013-04-13
It never hurts to describe your computer: CPU, RAM, hard drive, video card. Also mention what programs you typically have running. Do you use a CPU and memory monitor such as conky?

Your computer shares the pipe with your wife's computer, can you confirm that the problem appears when her computer is idle?

Finally, your concern is download speeds. In my experience, when a download doesn't run at full speed, it's because the system I'm downloading from is underpowered. Or my wife is watching Chinese TV....

---

### Post by Jonny87 on 2013-04-14
> **goodbye-windows(tm) said:**
> The information in the thread states that my wife's Win 7 computer downloads properly, but that 2 Linux machines don't. But, before they did some very recent changes in the network, my wife's computer and my Linux computers both had the same failure modes (as shown in the pdf attachment to the thread above). They did something (very very recently) to the network to make the Win 7 machine download properly, but the Linux machines are still failing to download properly.

Appreciate any comments.

Art
 
As [COLOR=#000000]gordintoronto stated, it would pay to make sure that your wife's Win 7 machine isn't using the internet when you experience the issues, even if shes not on it, if it's running it may be checking for updates or email or doing other things depending on it's software.
As far as the whole Windows / Linux thing goes, theres no reason that Windows should have a better internet connection than Linux. After all Linux was created with networking in mind. I'm not saying that it's not possible, but I do doubt that your ISP has put something in place to favor Windows comps.

[/COLOR][COLOR=#000000]gordintoronto also made the very good point that changes in performance could be caused from the source that you downloading from, regardless of what speed you're meant to have. For example, (I don't know if you do or not, but..) if you had fiber to the door and you downloaded something from me, and you have great upload and download speed, that download is always going to be bottle necked at my upload speed.[/COLOR]

[COLOR=#000000]And like I said if you're still 100% sure that issue is with your ISP then keep on them. In my experience I've found that if you can push past that Level 1 tech support (the first person that deals with you when you ring) and sometimes even past Level 2 then you will often get someone that is in fact helpful. The person at Level 1 usually doesn't have very much understanding past the basic trouble shooting question that they have in front of them. Often the key to get past them and on to Level 2 is to start giving them technical info and sound like you know more than them. Mention things like pinging this and that server, you're vnstat results etc, they will start to get the idea that it's beyond them and pass you on. Don't mention that you're running Linux unless they ask what OS you're running because they'll most likely say "We don't support that Operating system sorry. We only support Windows and Mac.", not that it should matter what OS you're using. If all else fails on Level 1 try threatening that if you don't get some help that you'll change to a provider that will help. That will **Sometimes** get them going. And remember to stay calm, at the end of the day the person on the other end is only doing what they have been trained to do, it's not their fault, getting angry at them won't make them want to help you any more.
[/COLOR][I]
** Just want to add a quick note to say that I mean no offense to any phone tech support people reading this in any way. I realise that you don't all fit the description above. However this is My experience with multiple ISP support lines. **[/I]

---

