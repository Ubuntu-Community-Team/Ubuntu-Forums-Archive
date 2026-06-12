---
title: "Linux Firewall"
date: 2006-09-04
forum: Server Platforms
---

### Post by notoriouslou1022 on 2006-09-04
Can some link me to a guide on how to setup up a linux firewall box? Thanks

---

### Post by breuerp on 2006-09-04
The easiest way to to this in Ubuntu is to use firestarter, a graphical frontend for the included firewall.  To install firestarter:  sudo apt-get install firestarter

It's *VERY* straightforward.  Ask again if you have any questions.

---

### Post by skymt on 2006-09-04
Firestarter is for running a firewall on a desktop. The OP seems to want a dedicated firewall box for a network.

The easiest way to set up a firewall box is to use a specialized distro. I've heard good things about [SmoothWall](http://www.smoothwall.org/) or [Astaro](http://astaro.com/) (free for home use).

---

### Post by notoriouslou1022 on 2006-09-04
Yeah skymt, thats exacly what I want. Thank you both for your help! ;)

---

### Post by wiseguy on 2006-09-05
You may want to consider ClarkConnect as an option. :) 

[http://distrowatch.com/table.php?distribution=clarkconnect](http://distrowatch.com/table.php?distribution=clarkconnect)

Here's a review.

[http://linux-blog.org/index.php?/archives/127-ClarkConnect-Enterprise-Linux-for-Your-Home.html](http://linux-blog.org/index.php?/archives/127-ClarkConnect-Enterprise-Linux-for-Your-Home.html)

---

### Post by seekyrr on 2006-09-12
[http://ipcop.org/](http://ipcop.org/)

Small fast easy to use stand alone.

Seek

---

### Post by Flashstar on 2006-09-12
You can use Firestarter to protect your network easily...I did it.
 
[http://www.linuxquestions.org/questions/showthread.php?t=477941](http://www.linuxquestions.org/questions/showthread.php?t=477941)

---

### Post by 454redhawk on 2006-09-12
> **Flashstar said:**
> You can use Firestarter to protect your network easily...I did it.
 
[http://www.linuxquestions.org/questions/showthread.php?t=477941](http://www.linuxquestions.org/questions/showthread.php?t=477941)

Simply running Firestarter to protect your network is not even close to using IPCOP, Smoothwall or Clarkconnect as a dedicated firewall.

---

### Post by Flashstar on 2006-09-13
"IPCop Firewall basically sits "in between" your Internet connection (dial-up modem, cable-modem, DSL, etc) and works directs traffic using a set of rules for the TCP/IP traffic that underlies all Internet activities. The default rules, ideal for most users, are essentially simple in nature. They allow you to "surf" to the outside world and visit web-sites, FTP, email and so forth. And as you go about your tasks on the Internet, IPCop allows return traffic from those tasks, that you requested, to pass through. If, however, some random TCP/IP traffic comes in, requesting information from your computer, and that traffic is not in response to your requests, IPCop Firewall refuses to respond, and logs that attempt. Thus, you are allowed to go about your normal business, but when the bad guys try to come after you, they are stopped cold, because they are not responding to your requests. Think of IPCop Firewall as your friendly traffic cop down on the corner, making sure that things travel smoothly, and enforcing good rules on your Internet traffic."

This is essentially the same a Firestarter (which is a gui for IPtables) because both the firewall distros and Firestarter use Iptables which allows LAN user requested data to go out, but not non-requested data to come in. I've tested my network which is protected by Firestarter/Iptables with NMAP, Nessus, and Shields Up from the outside and not only is my network virtually impenibtrable by outside hackers, it is impossible to even see it because Firestarter lets you easily turn of replies to pings, etc. 

Just talk to Win32sux, he helped me get a basic Iptables script set up and it's working great! :cool:

EDIT: You will still have a dedicated firewall, it's just that your dedicated firewall will have more possibilities like a proxy server or game server.

---

### Post by sktx on 2006-09-15
> **Flashstar said:**
> You will still have a dedicated firewall, it's just that your dedicated firewall will have more possibilities like a proxy server or game server.

Hmmm.. But, if you're running a proxy/game server on your firewall box, wouldn't that mean it's *not* a dedicated firewall?  

And, correct me if I'm wrong (which I often am), but wouldn't it be bad practice to install listening services on a firewall? One would think that you'd want as little exploitable software on that box as possible, considering that it's sole job is to be the first line of defence for the rest of the boxen in your network.  Anyone have any thoughts on this?

The way my current understanding goes, if I were wanting to set up a dedicated firewall, I'd probably go with one of the distro walls like smoothwall or ipcop, though i'll admit my understanding of them is pretty slack as I've never run one or tinkered with one.  

As it is, I'd probably have the best luck (and the most fun) putting together an old machine from the pile o' parts in my garage, sticking freeBSD on it, and dropping it between my connection and my router.  Anyone done this, or have any ideas?

 -ck-

---

### Post by Flashstar on 2006-09-16
> 
The way my current understanding goes, if I were wanting to set up a dedicated firewall, I'd probably go with one of the distro walls like smoothwall or ipcop, though i'll admit my understanding of them is pretty slack as I've never run one or tinkered with one.

It's true that it wouldn't be just a dedicated firewall, but you would be amazed by the possibilities of Firestarter and iptables. There is no doubt that I would prefer to use an old computer just for a firewall, but often one cannot dedicate one computer just to be a firewall. Although running some listening services seems like a very bad thing to do on a firewall computer, you can specify who will have access to those services. For example, in 5 seconds you can allow the internal network access to port 8080, but not the WAN, or you can allow just a single ip address access to a port. I admit that it isn't ideal, but running a multi-purpose computer/firewall is both more economical through electrical savings as well as component costs, and is very safe and easy to set up to top it off.

---

### Post by sktx on 2006-09-16
> **Flashstar said:**
> It's true that it wouldn't be just a dedicated firewall, but you would be amazed by the possibilities of Firestarter and iptables.
I'm not amazed.  I run firestarter.  Desktop firewalls are nice, and do their job alright, but the fact of the matter is that they're not effective.  Getting through a desktop firewall on a machine full of buggy software and exploitable services is not a difficult endeavour for someone who knows what they are doing. 

> **Flashstar said:**
> There is no doubt that I would prefer to use an old computer just for a firewall, but often one cannot dedicate one computer just to be a firewall.
Ingredients for One(1) Dedicated Firewall:
1 old computer case
1 old mobo with a Pentium or P2 cpu on it
128-256Mb RAM (if you're feeling generous)
1 10Gb Hard drive (you can actually get away with less)
NICs and cables
1 CD-ROM drive (for installation)
Mix ingredients together in bowl, follow instructions on screen, preheat oven to 350 and bake. Further instructions available in various places all over the internet. Refer to ipcop, m0n0wall, smoothwall, etc etc etc. Cost: about 37 cents and some pocket lint, a blank CD and a bit of your time. 

> **Flashstar said:**
> Although running some listening services seems like a very bad thing to do on a firewall computer, you can specify who will have access to those services.
It doesn't matter, as long as someone has access.  The basic fact of the matter is that you want as little code to be running on that machine as possible... The more code, the more chance there is that someone knowledgeable can exploit it. 

> **Flashstar said:**
> For example, in 5 seconds you can allow the internal network access to port 8080, but not the WAN, or you can allow just a single ip address access to a port.
Running firestarter.  On your desktop box.  With a machine full of possibly buggy code and possibly exploitable services.  It's true that it's a decent first-line-of-defence, and if you shut off ICMPs and drop packets to all incoming ports, you'll keep those brute-force SSH worms away, possibly, if they don't recieve a response to ping or a refused packet, they might think that there's no machine at that IP.  But for someone who knows what they're doing, and who wants to spend a couple minutes so they can play with your toys, this solution isn't going to stop anything.

> **Flashstar said:**
> I admit that it isn't ideal, but running a multi-purpose computer/firewall is both more economical through electrical savings as well as component costs, and is very safe and easy to set up to top it off.
Component costs aren't really an issue with a dedicated linux firewall machine, considering the fact that you can run ipcop off of a 386 with 64Mb ram. You can go to a thrift store and buy an old P2 for ~$20, if you can't piece one together from old parts, and that would be more than enough for a decent firewall box.  If you join a local user group mailing list, you get emails every couple weeks about how someone is throwing away a bunch of obsolete machines and wants to donate them to some good cause.  And as far as the cost of electricity goes, it doesn't cost a whole lot to run a single machine with one hard drive and a few NICs, with no monitor, mouse, or keyboard. You don't even need to keep the graphics card in the box past installation.

---

