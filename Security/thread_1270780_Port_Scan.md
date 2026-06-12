---
title: "Port Scan"
date: 2009-09-20
forum: Security
---

### Post by sopadeajo on 2009-09-20
On a port scan done on my computer from a web page scanning ports 20,21,22,23,25,53,79,80,110,119,135,
139,143,389,443,445,631,1433,3306,5000 which tells me all ports are closed; firestarter does not show me hits on ports 20,79,119,135,139,445,631,5000.
Why can this be?

---

### Post by movieman on 2009-09-20
If you're using a router rather than a direct connection from the Internet into your PC, that router probably has its own firewall that blocks all incoming connections unless you explicitly allow them.

---

### Post by TuckLive on 2009-09-20
> **movieman said:**
> If you're using a router rather than a direct connection from the Internet into your PC, that router probably has its own firewall that blocks all incoming connections unless you explicitly allow them.

+1

Your router also has a port-forward option.  In order to see those hits in Firestarter you would have to forward those ports, which isn't a good idea unless you need remote access.  Your router is acting as another layer of security.

---

### Post by The Cog on 2009-09-20
> **movieman said:**
> If you're using a router rather than a direct connection from the Internet into your PC, that router probably has its own firewall that blocks all incoming connections unless you explicitly allow them.

That doesn't sound right to me. It it were the case, then I would not expect to see any hits in the log. Unless the Original Poster has already configured port forwarding for those protocols, in which case I doubt he would be asking the question.

I wonder if firestarted has a rate limit on its logging - only logging X hits/sec. Notice that it's the first few ports where the hits are logged.

It might be interesting to run a tcpdump or wireshark capture while this test is going on.

---

### Post by lovinglinux on 2009-09-20
Also keep in mind that if you are not running any applications that listen to ports (server), like ssh, samba or even Bittorrent, then your port scan result will give you all ports closed, even if you don't use a firewall and don't have a router. This means all ports are virtually closed and all connection attempts on any port will be refused. A port will be opened only if you have an application listen to it. So, a firewall is usually not necessary if you don't install server applications, since Ubuntu doesn't have any server running by default. All ports closed when you first install Ubuntu.

---

### Post by sopadeajo on 2009-09-20
> **lovinglinux said:**
> Also keep in mind that if you are not running any applications that listen to ports (server), like ssh, samba or even Bittorrent, then your port scan result will give you all ports closed, even if you don't use a firewall and don't have a router. This means all ports are virtually closed and all connection attempts on any port will be refused. A port will be opened only if you have an application listen to it. So, a firewall is usually not necessary if you don't install server applications, since Ubuntu doesn't have any server running by default. All ports closed when you first install Ubuntu.

Yes. i am well aware that Firestarter did nothing in the process. He just logged the scanning being done. But that's why i wonder why he did not log 8 out of 20 hits.
And well, i have a lot of logs (hits) on port 135, but this time Firestarter logged no hit on port 135...

---

### Post by sopadeajo on 2009-09-20
> I wonder if firestarted has a rate limit on its logging - only logging X hits/sec. (The Cog)

I have repeated the operation and exactly the same 8 ports have been excluded from log.If there was a rate limit the ports excluded from log would be random and so different each time (unless a determined interval of time (always the same) is choosen not to log hits on ports while.. This could be also the web-page port scan that is not working properly because when you're behind a proxy this web site tells you all the 20 ports are closed while in fact it should have been unable to scan any of them (not completely sure of that, though). I'll redo the test in a different site to see what happens.

---

### Post by sopadeajo on 2009-09-20
Any of you may try and tell us which logs Firestarter does:
[http://www.internautas.org/w-scanonline.php](http://www.internautas.org/w-scanonline.php)

You must click on the button: "Escanea los puertos más habituales"

I have done a port scan on the five ports 20,79,119,135,139 only, and though i am told they are closed, Firestarter does not show any log at all,while i am having lots of hits and logs on port 135 from 40  (or more) different IP"s

---

### Post by sopadeajo on 2009-09-20
Redone a port scan with:
_[http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)_
on common ports and i only get logged hits on: 5000 (two times),1720,1030,1029,1028 ant tht's all.
It seems that there is no way (at leat for me) to explain .
Note that port 5000 was not logged in the precedent scan, but is logged in this one.

---

### Post by __p1n__ on 2009-09-21
> **sopadeajo said:**
> Redone a port scan with:
_[http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)_
on common ports and i only get logged hits on: 5000 (two times),1720,1030,1029,1028 ant tht's all.
It seems that there is no way (at leat for me) to explain .
Note that port 5000 was not logged in the precedent scan, but is logged in this one.

GRC is more of a fud/marketing site than a decent security resource.  The test that you cite was created back when gibson was cross-promoting a rubbish firewall called zonealarm*.  The ne.dll referenced in the uri is interesting too.

Your firewall might only be logging connection attempts as opposed to random out-of-sequence TCP packets so you can easily check this by running an nmap -sT scan (TCP connect) against your firewall.  Follow it up by running an nmap -sF scan (FIN packet) and contrast the difference in logged results at the firewall.

* see [http://www.radsoft.net/software/reviews/za/](http://www.radsoft.net/software/reviews/za/)

---

