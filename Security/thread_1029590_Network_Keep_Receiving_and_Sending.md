---
title: "Network Keep Receiving and Sending"
date: 2009-01-03
forum: Security
---

### Post by Ioky on 2009-01-03
I am pretty New on Networking stuff. The other days, I realize from my system monitor/Network monitor that, the network is always receiving something, as well as sending something. I have never see that before, or as less not as much as I realize. 

So I just wondering, what is actually being receiving and sending. I mean Ideally, if I am not browsing the web or downloading something, it shouldn't receive anything as well as Sending. Maybe except the system is looking for update or something, but that to my knowledge should only happen once a day and it shouldn't take that long. 

Is there anyway, that I can see all the Network event/log? So I can stop this from happening? 

Thanks

---

### Post by Kinstonian on 2009-01-03
Try using *netstat -anp* to find the program(s) that is using the network.  You could also use Wireshark to see the traffic as it is on the wire, but understanding the data could be a problem if it's the first time dealing with network traffic.

---

### Post by Ioky on 2009-01-03
What are some possible problems those traffic might cause? 

Also I have few question about those "Stuff" I am receiving:

Are they like date file that save somewhere in your system?

How those people located you and send you those "Stuff" at the first please?

Any good way to avoid receiving stuff that you don't want? 

Haha, as I said, I am very new coming to dealing with Networking stuff. All I know is how to get my computer on-line, but nothing else. I try to google it, but doesn't really know where to start. 

Thank you so much for the help.

---

### Post by Rob_H on 2009-01-03
There are lots of possibilities depending on what kind of network you are on (e.g. home or office). You might be seeing broadcast/multicast traffic that others are sending out, for example. Or, if you're connected directly to the Internet without a firewall (hope not!), you could be seeing lots of random stuff. :-)

I would suggest as others have that you run Wireshark to gather a few seconds worth of traffic. Install it, run it as root from the menu, then go to Capture > Interfaces and click the Start button next to the correct network interface. (It will be the one whose packet counter is going up the fastest.) After a few seconds or so, go to Capture > Stop to stop it. Then look at the data in the window. In particular, the protocol column will give you an idea of what kind of traffic it is. If you don't know how to interpret the protocol names, post some of the ones you see to this thread and maybe we can help. (Don't post the traffic itself. It might contain sensitive data.)

---

### Post by Ioky on 2009-01-03
> **Rob_H said:**
> There are lots of possibilities depending on what kind of network you are on (e.g. home or office). You might be seeing broadcast/multicast traffic that others are sending out, for example. Or, if you're connected directly to the Internet without a firewall (hope not!), you could be seeing lots of random stuff. :-)

I would suggest as others have that you run Wireshark to gather a few seconds worth of traffic. Install it, run it as root from the menu, then go to Capture > Interfaces and click the Start button next to the correct network interface. (It will be the one whose packet counter is going up the fastest.) After a few seconds or so, go to Capture > Stop to stop it. Then look at the data in the window. In particular, the protocol column will give you an idea of what kind of traffic it is. If you don't know how to interpret the protocol names, post some of the ones you see to this thread and maybe we can help. (Don't post the traffic itself. It might contain sensitive data.)

It seem like there is a lot UDP going on, and I have no idea, what they are, I am using a wired network. Those UDP is what seem doing all those "unknown sending/receiving". And they seem are Samba Service event. I don't know what is going on. any idea?

I will looking into firewall config stuff. Thanks for the help

---

### Post by Rob_H on 2009-01-04
> **Ioky said:**
> It seem like there is a lot UDP going on, and I have no idea, what they are, I am using a wired network. Those UDP is what seem doing all those "unknown sending/receiving". And they seem are Samba Service event. I don't know what is going on. any idea?

UDP covers a broad range of applications, so no help there. Samba is used for file and printer sharing. If you're sharing files or using a file server, that might explain it. Ad even if you're not actively moving files around, computers acting as file/print servers periodically "announce themselves" on the network, so you could be seeing that. Good luck.

---

### Post by Vantrax on 2009-01-04
UDP is a file transfer protocol, such as TCP. 

Its probably not a major problem, I typically have at least a dozen connections at any given time. If you see one there consistantly that is also using significant ram or CPU then I would be doing a quick google check to be safe. Largely I would not worry about it.

If you are worried about it and want to find out whats really going on I would recommend bohdi's thread [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

---

### Post by BGFG on 2009-01-04
I'm no professional either, but certain programs have settings that would cause network activity when the system is seemingly inactive. Examples:

*Deluge Torrent - Settings: Be alerted about new updates
                            Send anonymous usage statistics
                            Daemon-periodically check for new releases

*Update Manager may be connecting to the servers

*Firefox may be downloading updates

*Administration Software Sources - Submit Statistical information

---

### Post by Ioky on 2009-01-05
Thanks for all of your help. I will look into it. I guess sometime just monitor the system itself is not enough, have some knowledge to monitor "who" the system is "talking" to seem like a good idea.

---

