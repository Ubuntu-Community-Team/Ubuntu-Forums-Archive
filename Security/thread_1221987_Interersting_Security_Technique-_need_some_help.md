---
title: "Interersting Security Technique- need some help"
date: 2009-07-24
forum: Security
---

### Post by e30drift on 2009-07-24
I was discussing scheduling SSH access from outside the network with a colleague of mine and I came up with this interesting concept that should be relatively easy to setup.

We dubbed it "PINg Code"
Basically we ping 3 or more unopen ports on the Linux based firewall and based on the order of the ping and the time to ping those ports would open up port 22.  

Obviously there would be a script running in the background monitoring what ports are being pinged.  

Once the right ports are pinged, the script opens port 22 for SSH access.  Other than that, it is closed.

Just to make it more interesting, we have key fobs that display generated PIN codes for accessing client sites, using that concept, we figured another script could be made to email us a newly generated set of ports to ping to get in and set a time limit on how long those would be available and have those emailed to us.

I'm sure something like this has been done before, but seeings how this is an interesting concept, I was wondering if you guys might help make some bash scripts to get this working.  

Any other constructive criticism would be appreciated :D

---

### Post by Kinstonian on 2009-07-24
Good idea, but you're right, its already been done. :)  It's called "Port Knocking."

Check out: [http://www.cipherdyne.org/fwknop/](http://www.cipherdyne.org/fwknop/)

---

### Post by e30drift on 2009-07-24
> **Kinstonian said:**
> Good idea, but you're right, its already been done. :)  It's called "Port Knocking."

Check out: [http://www.cipherdyne.org/fwknop/](http://www.cipherdyne.org/fwknop/)

Lolz!  I knew it wasn't a new thing, but I thought it would be a fun mini project.

Looking at fwknop, it has way more than I wanted, but nonetheless very cool!

Found the tutorial:
[http://ubuntuforums.org/showthread.php?t=812573]("http://ubuntuforums.org/showthread.php?t=812573")

---

### Post by e30drift on 2009-07-24
The one feature I would want is for a bash script to email me a generated knock code and add that to the master bash script.  I think that would add to the coolness factor ;-)

---

### Post by bodhi.zazen on 2009-07-24
It is a nice idea, but really if you configure iptables "properly" or use HIDS (OSSEC, denyhosts, fail2ban) you will be just fine. 

* Yea, I know HIDS is used loosely in this post.

---

### Post by dragos2 on 2009-07-24
> **e30drift said:**
> Lolz!  I knew it wasn't a new thing, but I thought it would be a fun mini project.

Looking at fwknop, it has way more than I wanted, but nonetheless very cool!

Found the tutorial:
[http://ubuntuforums.org/showthread.php?t=812573](http://ubuntuforums.org/showthread.php?t=812573)

Port knocking was first but it had some problems like time and the fact that
the knocks could be sniffed. fwknop appeared as a SPA resolving both
the time factor and the sniff one.

---

### Post by The Tronyx on 2009-07-24
Edit:

Misread.

---

### Post by kevdog on 2009-07-26
I really only find fwknop useful (personal opinion), in cases of an openssh exploit.  This assumes you are using a properly configured firewall.  There have been at least two cases of openssh exploit within the last several years, so although it is rare, it does happen.  In the first case, it took a long time to discover the error.  If you need top-notch security, or are extremely paranoid, running a port knocker may not be a bad idea.  In most cases however its probably overkill.  In all cases its probably a good idea to keep an eye on the your system logs to see where the attacks are coming from.  fwsnort (another utility) has the ability to turn certain log findings into iptable rules, in a way of automating the steps. The only other inconvenience of running a port knocker, is the need for a client program to allow access.  In some cases this makes portability somewhat of a pain.

---

