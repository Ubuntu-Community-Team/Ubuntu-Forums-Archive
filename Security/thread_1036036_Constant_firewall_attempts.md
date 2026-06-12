---
title: "Constant firewall attempts"
date: 2009-01-10
forum: Security
---

### Post by toasty_ghosty on 2009-01-10
I have Firestarter working as my firewall GUI. Normally I might get one or two blocked attempts a day. Within 30 minutes of being on my machine today there has been nearly 100 attempts to port 6349. What is this port responsible for? It may be a system service as well. Does anyone know what may be causing this?

Thanks.

---

### Post by 2hot6ft2 on 2009-01-10
6349 is used by kazza and limewire. So if you're running any p2p file sharing check to see which ports it's using.

It appears to be unassigned which would explain why it's used by p2p apps. I used to have the entire list of ports but no telling where it is now. All I seem to find for that other than kazza and limewire is this.
6348-6354  Unassigned

---

### Post by toasty_ghosty on 2009-01-10
The only time I use any sort of p2p software is to download a new distro via bit torrent. But that uses port 6881-6889...

---

### Post by 2hot6ft2 on 2009-01-10
> **toasty_ghosty said:**
> The only time I use any sort of p2p software is to download a new distro via bit torrent. But that uses port 6881-6889...
LOL, deluge.

---

### Post by toasty_ghosty on 2009-01-10
> **2hot6ft2 said:**
> LOL, deluge.

I'm sorry but what.

---

### Post by 2hot6ft2 on 2009-01-10
That's the range deluge uses, but others may use it as well. Just so you know I have seen my firewall get hit repeatedly at that same 6349 port so I suspect someone is trying to exploit a security flaw in most likely kazza and is just sending out random hits looking for someone running it.

As long as your firewall is dropping the hits I wouldn't worry too much about it. It doesn't appear to be a service port used by the OS.

---

### Post by toasty_ghosty on 2009-01-10
Thanks.

Now it appears port 51413 seems to be getting hit. About 50 times since the last post! I've never seen this happen before...

---

### Post by 2hot6ft2 on 2009-01-10
If you really want to beef up your security there's a great thread on it here. [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

Mines getting hit on 61488 right now. Ubuntu is pretty secure so unless there's some special reason for concern I don't sit and watch what gets rejected by the firewall that's it doing its job.

A decent router and a firewall do the trick.

---

### Post by keith.newell on 2009-01-10
Port 51413 is the default port in Transmission. I would have to agree with 2hot6ft2, that someone is randomly looking for an unsecured port.

---

### Post by HermanAB on 2009-01-10
Your firewall is working.  Relax and enjoy it.

Actually, the best way to relax is to quit the 'interactive' feature of the firewall.  You only need to run Firestarter once to set up iptables.  Thereafter you don't need to run it anymore.

Cheers,

Herman

---

### Post by bodhi.zazen on 2009-01-11
If I find an IP address that is scanning my box I black list it.

---

### Post by toasty_ghosty on 2009-01-11
Thanks for all the replies...and bodhi.zazen, what do you use to blacklist the ip? Is something like IPList sufficient to use? I made a custom blocklist and it has seemed to help.

---

### Post by bodhi.zazen on 2009-01-11
> **toasty_ghosty said:**
> Thanks for all the replies...and bodhi.zazen, what do you use to blacklist the ip? Is something like IPList sufficient to use? I made a custom blocklist and it has seemed to help.

Well the firewall on Linux is iptables.

iptables is a little difficult to learn, and most people use some kind of front end.

The default in ubuntu is now UFW

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

If you want a gui (graphical tool) try gufw

---

### Post by brandon88tube on 2009-01-12
Is there a need to deny IP's in UFW if you have it set to deny all?

---

### Post by Nepherte on 2009-01-12
No.

---

### Post by HunterThomson on 2009-01-12
I like to use denyhosts it auto blacklists hosts that have repeated failed login's to ssh

---

### Post by nubdora on 2009-01-14
Probably a bored kid playing with netstat. I do it from time to time.

---

