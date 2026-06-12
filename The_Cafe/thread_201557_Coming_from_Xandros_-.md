---
title: "Coming from Xandros -"
date: 2006-06-22
forum: The Cafe
---

### Post by cprise on 2006-06-22
Hi. I'm trying out Kubuntu Dapper after having used Corel->Xandros since early 2000. I've also gotten accustomed to Mac OS after about 1.5 years now.  Xandros just released version 4, and before I upgrade I want to see if Kubuntu can meet my needs instead.

I did try a prior version of Kubuntu, but it was unable even to set a static IP address from the GUI plus several other *basic faults* that I encountered all within a few hours, so I couldn't carry on in confidence with it. (Yes, I filed the bugs.)

Some questions are surfacing with Dapper however:

* I expected a firewall as basic equipment. Where is it?

* Does Dapper have a VPN client?

* Is there an easy way to enable home-folder encryption?

* Are there easy ways to setup an Adhoc wifi connection (between two computers) and share a cablemodem Internet connection to it?


These are all things I've gotten easily from the GUI in Xandros. The first three items are security-conscious features that seem conspicuously absent in Kubuntu Dapper.

So far I see lots of recommendations and howtos that amount to CLI-jockeying: Even though I'm comfortable using the shell, Dapper is confronting me with quite a lot of that after using it for just 7 hours so I cannot help but wonder what else it has in store for me in terms of manual labor and micromanagement if I commit to using it for the long term.

Your thoughts and suggestions would be appreciated. :KS

---

### Post by nalmeth on 2006-06-22
Your firewall is built-in, it is called iptables.
To configure it, install a firewall GUI, either Firestarter or Guarddog. 
Use synaptic to install it, you'll find likely find points 2 and 3 in there, make sure you enable the universe/multiverse repositories, you may want to enable restricted aswell. Yes, you can do this in synaptic.

I don't know about 4, don't use wireless at all.

Your thread may be better suited in other areas of the forums, as people come here just to take about (well usually :) ) anything but their specific technical issues.

Enjoy Ubuntu, I think when you figure out where you're at, it will easily replace your Xandros. 

Good luck

---

### Post by Christmas on 2006-06-22
The new Kubuntu 6.06 is more stable and less bug free than the 5.10 version. I agree with you about the 5.10, it was buggy and failed to open programs very often.
[quote=cprise]I did try a prior version of Kubuntu, but it was unable even to set a static IP address from the GUI plus several other basic faults that I encountered all within a few hours, so I couldn't carry on in confidence with it. (Yes, I filed the bugs.)[/quote]
Yes, I encountered this problems to. Actually the problem (which persists in Dapper) is that it won't let me configure a secondary DNS, which is 194.150.255.248, given by my ISP, so it should be valid, but Kubuntu says it's not. Anybody knows what is wrong with this IP? Anyway, it's not much of a problem as I noticed that my primary DNS is enough for internet to work OK.

Leaving this small problem, I would say Kubuntu is a great OS, in my opinion it's the best OS I dealed with. Ubuntu seems more stable, programs don't fail to start, but I feel like chained in Ubuntu, no configuration tool works, you have to stay with some stupid conceptions the GNOME developers put in it. I mean I can't stand this very popular problem, the lines that you have when minimizing windows, they are so ugly and unaesthetic.

Of course, even in Dapper Kubuntu needs some work, but you can give it a try and see if you like it.

---

