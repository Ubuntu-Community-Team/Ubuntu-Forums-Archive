---
title: "Windows 7, services stop running"
date: 2012-10-02
forum: System76 Support
---

### Post by matase on 2012-10-02
I have system76 gezelle professional laptop.  It's the older model with the gtx560.  I am trying to use vpn cisco client to connect to a vpn and logmein hamachi to set up a private virtual lan so I can play lan games with my friend.  These two programs were working fine initially, until it started having intermittent problems with launching their services. I sometimes still decides to work, but I feel like it's  a problem with drivers conflicting or something like that.  When I try to launch either service the error says "windows could not start ... service on local computer. Error 1053: the service did not respond to the start or control request in a timely fashion.".  Some help?

---

### Post by Ubun2to on 2012-10-02
Do you have to use Hamachi for networked gaming?
Some games have multiplayer features built in and the ability to connect to them and play on them without using something like Hamachi (Minecraft is my favorite example of this).
But, I suspect that it is the developers that are at fault here.
Windows 7 does a much better job than Vista and XP at getting drivers, so I doubt that is an issue.
I would try contacting the developers first.

---

### Post by matase on 2012-10-03
Actually I think I am experiencing a bigger problem, and the above mentioned are just the symptoms.  I think that NET framework or something related to that is broken.  I started my laptop this morning and I was not able to open any programs, control panel, internet, or task manager.  I restarted the pc a couple of times and the problem was gone. This has happened before, where none of the programs load up at start up and nothing opens.  I did get some net framework error.  I restored windows 7 to some earlier point and re installed framework, but this problem reoccurred this morning.

---

### Post by Ubun2to on 2012-10-03
> **matase said:**
> Actually I think I am experiencing a bigger problem, and the above mentioned are just the symptoms.  I think that NET framework or something related to that is broken.  I started my laptop this morning and I was not able to open any programs, control panel, internet, or task manager.  I restarted the pc a couple of times and the problem was gone. This has happened before, where none of the programs load up at start up and nothing opens.  I did get some net framework error.  I restored windows 7 to some earlier point and re installed framework, but this problem reoccurred this morning.

System Restore doesn't work? Crap just got real. When is the last time you did a virus scan?

---

### Post by matase on 2012-10-03
It only does this sometimes.I have to restart a couple of times to get it going, which is a totally unhealthy method. I am doing a virus scan as I am writing this, but it's almost done and no viruses found. What could be another cause of this problem?

---

### Post by Ubun2to on 2012-10-05
> **matase said:**
> It only does this sometimes.I have to restart a couple of times to get it going, which is a totally unhealthy method. I am doing a virus scan as I am writing this, but it's almost done and no viruses found. What could be another cause of this problem?

What are you using to scan? I use Malware Bytes, Spybot S&D, and MSE.
Also, I take it you kept Windows 7 on auto-defrag? If not, you might be experiencing file fragmentation.

---

