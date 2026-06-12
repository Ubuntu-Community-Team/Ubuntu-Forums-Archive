---
title: "SSH from outside the lan"
date: 2006-11-15
forum: Server Platforms
---

### Post by DeepThoughts on 2006-11-15
Hi, I'm using a slimmed down install of Ubuntu (Dapper) on my little server at home. I had it set up so that I can use ssh as a SFTP-server (my friends can log in to a nice chrooted environment). Unfortunately it doesn't work since a while back.

I am able to ssh in and administer the server if I'm on my main computer that's on the same lan using it's local ip (ie 192.168.1.3). If I however try to use my external ip or domain name it times out. On my router I have forwarded port 22 to the local ip of the server (and it's set up so the computers always revices the same ip) so there shouldn't be any problem there, should it?

Does anyone know what might be wrong? Something that changed during an update? Is my semi-crappy router to blame (if so, how)? The idiot behind the wheels (a.k.a. me)?

---

### Post by earobinson on 2006-11-15
what you need to do is to ssh to your routers ip and then set up port forwarding in your router to forward port 22 to the ip of the server you wish to ssh into.

then from out side ssh to your routers ip and log in.

---

### Post by Wicca on 2006-11-15
Your ISP might block traffic for port 22, a lot of them do so. To find out use a port higher then 1024 instead.

---

### Post by DeepThoughts on 2006-11-15
> **earobinson said:**
> what you need to do is to ssh to your routers ip and then set up port forwarding in your router to forward port 22 to the ip of the server you wish to ssh into.

then from out side ssh to your routers ip and log in.

Well that's what I've done, sorry if I wasn't clear.

I have a static ip from my isp (my university) and a domain name from them too (ie http://{user}.campus.ltu.se ). So that's the ip and domain name my router has and the router is forwarding port 22 to my server's internal ip.

Every other port forward from the router works, except this one which has made me believe that ssh is refusing connections from outside the lan but I might be wrong about that, which is why I've posted these questions.

And to be clear, if I wasn't earlier:
**I've had this working but since a while back it ain't.**

---

### Post by earobinson on 2006-11-15
try a different port like Wicca said, maybe your ISP started blocking port 22

---

### Post by Nano on 2006-11-15
I have gone through this by using the 443 port, usually dedicated to https and most of the times unlocked

---

### Post by dweez on 2006-11-15
Are you attempting to ssh using the domain name or have you tried using the IP?

---

### Post by DeepThoughts on 2006-11-15
> **dweez said:**
> Are you attempting to ssh using the domain name or have you tried using the IP?

I've tried both with no success.




[SIZE="4"]**NEWS?**[/SIZE]
Upon further investigation it seems that Apache i also unaccessible from outside the lan. Both are accessible internally.

I'm running an Apache-server on my main computer also (just for developing) and if I try to make it the default server it also fails. This has gotten me thinking.

Could it be so that I've misconfigured something so they won't resolve my outside ip/domain name?

---

### Post by DeepThoughts on 2006-11-15
> **earobinson said:**
> try a different port like Wicca said, maybe your ISP started blocking port 22

According to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) my isp isn't blocking any of the ports in question. As far as I know they don't block any ports actually.

---

### Post by tturrisi on 2006-11-15
Well, for one thing, you don't have a domain or a domain name, you have a sub-domain of the college public domain.  The sub-domain configs on the college server may not allow users to host sites or use ssh.  Check w/ the domain admins.

Is the college issuing you a public ip address or a private ip address.  You are assigned a static address by the college server, but THAT address may be a private address.

What's YOUR real url here?
http://{user}.campus.ltu.se
That url should be routed /home/user on the college's server, not your server.  To access web content on your server from the wan you will need to put an index.xxx file on your college /home/user/www dir with a redirect to your server, either using a meta refresh or a php header redirect.

Chances are you are assigned a private ip address by the college.  I doubt they are handing out public ip addresses to students, in which case you ar sol getting access from the wan.

---

### Post by dannyboy79 on 2006-11-15
> **tturrisi said:**
> Well, for one thing, you don't have a domain or a domain name, you have a sub-domain of the college public domain.  The sub-domain configs on the college server may not allow users to host sites or use ssh.  Check w/ the domain admins.

Is the college issuing you a public ip address or a private ip address.  You are assigned a static address by the college server, but THAT address may be a private address.

What's YOUR real url here?
http://{user}.campus.ltu.se
That url should be routed /home/user on the college's server, not your server.  To access web content on your server from the wan you will need to put an index.xxx file on your college /home/user/www dir with a redirect to your server, either using a meta refresh or a php header redirect.

Chances are you are assigned a private ip address by the college.  I doubt they are handing out public ip addresses to students, in which case you ar sol getting access from the wan.

yes, what he says. this has already been posted once in the forums, I remember trying to help the guy out but I can't remember what the solution was besides what tturrisi is saying. good luck

---

### Post by DeepThoughts on 2006-11-15
> **tturrisi said:**
> Well, for one thing, you don't have a domain or a domain name, you have a sub-domain of the college public domain.  The sub-domain configs on the college server may not allow users to host sites or use ssh.  Check w/ the domain admins.
Let's get this straight, once and for all. Sub-domain or domain is just semantics in this case, **because I've had these things up and running**. The configs doesn't block those things.

> **tturrisi said:**
> Is the college issuing you a public ip address or a private ip address.  You are assigned a static address by the college server, but THAT address may be a private address.
Public.

> **tturrisi said:**
> What's YOUR real url here?
http://{user}.campus.ltu.se
That url should be routed /home/user on the college's server, not your server.  To access web content on your server from the wan you will need to put an index.xxx file on your college /home/user/www dir with a redirect to your server, either using a meta refresh or a php header redirect.
[http://deepthoughts.campus.ltu.se](http://deepthoughts.campus.ltu.se) and it points to my public ip 130.240.218.80

Whether it should be routed to the university's server or not I don't care BUT it is routed to my computer which has the public ip 130.240.218.80

> **tturrisi said:**
> Chances are you are assigned a private ip address by the college.  I doubt they are handing out public ip addresses to students, in which case you ar sol getting access from the wan.
You may doubt as much as you want. Fact is that it is a public ip address. A friend of mine is running an ftp-server on his campus-address and the server is on his computer.

---

### Post by tturrisi on 2006-11-15
I don't disagree w/ you, you DO have a public ip.  (I AM jealous, I wish my isp gave me a static ip!) I was just stating some obvious common causes of such problems.  Things to check:
- permissions on directories & files
- any firewall (iptables) configs
- needed services starting at boot?

I'll do a quick nmap run to check the ports, so if you see a port scan from US w/ ip of 68.100.xx.xx, that's me.

I mentioned permissions because some dirs on your server can be accessed and some just time out when trying to access them from yoiur default apache index list of files in /var/www.

---

### Post by tturrisi on 2006-11-15
Starting Nmap 4.11 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-11-15 14:39 EST
DNS resolution of 1 IPs took 0.01s.
Initiating SYN Stealth Scan against deepthoughts.campus.luth.se (130.240.218.80) [1680 ports] at 14:39
Discovered open port 22/tcp on 130.240.218.80
Discovered open port 80/tcp on 130.240.218.80
SYN Stealth Scan Timing: About 6.49% done; ETC: 14:47 (0:07:15 remaining)
Increasing send delay for 130.240.218.80 from 0 to 5 due to 11 out of 18 dropped probes since last increase.
Increasing send delay for 130.240.218.80 from 5 to 10 due to 11 out of 16 dropped probes since last increase.
Increasing send delay for 130.240.218.80 from 10 to 20 due to 11 out of 16 dropped probes since last increase.
Increasing send delay for 130.240.218.80 from 20 to 40 due to 11 out of 15 dropped probes since last increase.
Increasing send delay for 130.240.218.80 from 40 to 80 due to 11 out of 13 dropped probes since last increase.
Increasing send delay for 130.240.218.80 from 80 to 160 due to 11 out of 14 dropped probes since last increase.
SYN Stealth Scan Timing: About 93.36% done; ETC: 14:47 (0:00:33 remaining)
The SYN Stealth Scan took 511.35s to scan 1680 total ports.
Initiating service scan against 2 services on deepthoughts.campus.luth.se (130.240.218.80) at 14:48
Warning: Servicescan failed to fill info_template (subjectlen: 1440). Too long? Match string was line 2683: v/Apache httpd/$1/$2
The service scan took 6.45s to scan 2 services on 1 host.
For OSScan assuming port 22 is open, 5010 is closed, and neither are firewalled
For OSScan assuming port 22 is open, 5010 is closed, and neither are firewalled
For OSScan assuming port 22 is open, 5010 is closed, and neither are firewalled
Host deepthoughts.campus.luth.se (130.240.218.80) appears to be up ... good.
Interesting ports on deepthoughts.campus.luth.se (130.240.218.80):
Not shown: 1675 filtered ports
PORT     STATE  SERVICE         VERSION
22/tcp   open   ssh             OpenSSH 4.2p1 Debian 7ubuntu3.1 (protocol 2.0)
80/tcp   open   http            Apache httpd 2.0.55
5010/tcp closed telelpathstart
5060/tcp closed sip
8082/tcp closed blackice-alerts
No exact OS matches for host (If you know what OS is running on it, see [http://www.insecure.org/cgi-bin/nmap-submit.cgi)](http://www.insecure.org/cgi-bin/nmap-submit.cgi)).
TCP/IP fingerprint:
SInfo(V=4.11%P=i686-pc-linux-gnu%D=11/15%Tm=455B6F0C%O=22%C=5010)
TSeq(Class=RI%gcd=1%SI=2523CC%IPID=Z)
TSeq(Class=RI%gcd=1%SI=25259E%IPID=Z)
TSeq(Class=RI%gcd=1%SI=24FC66%IPID=Z)
T1(Resp=Y%DF=Y%W=16A0%ACK=S++%Flags=AS%Ops=MNNTNW)
T2(Resp=Y%DF=N%W=0%ACK=S%Flags=AR%Ops=)
T3(Resp=N)
T4(Resp=Y%DF=N%W=0%ACK=O%Flags=R%Ops=)
T5(Resp=Y%DF=Y%W=0%ACK=S++%Flags=AR%Ops=)
T6(Resp=Y%DF=N%W=0%ACK=O%Flags=R%Ops=)
T7(Resp=N)
PU(Resp=N)

TCP Sequence Prediction: Class=random positive increments
                         Difficulty=2423910 (Good luck!)
IPID Sequence Generation: All zeros
Service Info: OS: Linux

Nmap finished: 1 IP address (1 host up) scanned in 533.465 seconds
               Raw packets sent: 3504 (156.580KB) | Rcvd: 63 (3192B)

---

### Post by tturrisi on 2006-11-15
Your router IS port forwarding 22 & 80, but no others.

---

### Post by NorthCoast on 2006-11-15
In fact:
```
Remote protocol version 2.0, remote software version OpenSSH_4.2p1 Debian-7ubuntu3.1
```

When in doubt, go verbose.

---

### Post by DeepThoughts on 2006-11-15
> **tturrisi said:**
> Your router IS port forwarding 22 & 80, but no others.

This mess is getting stranger and stranger it seems.

#1. If it's forwarding 80 & 22 how come I can neither SSH or get the apache-server to show when using my external IP?

#2. I am forwarding more ports than 80 and 22. Some for BitTorrent, one for DC++ and some others. Although these aren't forwarded to my server so that might be it?

---

### Post by NorthCoast on 2006-11-15
I don't understand, I see your SSH and web server.  It works for me.
Be prepared for trouble, you'll get thousands of brute force attacks on SSH and a million other things with forwards like that....

---

### Post by tturrisi on 2006-11-15
> #2. I am forwarding more ports than 80 and 22. Some for BitTorrent, one for DC++ and some others. Although these aren't forwarded to my server so that might be it?
No, because your router has the static public ip and your server has a static private ip assigned by the router, at least that's how is should be setup.  The nmap scan shows all open ports on the router IF your setup is as I just decribed.

fyi, I can access all dirs now on your server via the apache index, but some are very slow to load, like the system is hanging somewhere, or there is latency on the network.

---

### Post by dannyboy79 on 2006-11-15
> **NorthCoast said:**
> I don't understand, I see your SSH and web server.  It works for me.
Be prepared for trouble, you'll get thousands of brute force attacks on SSH and a million other things with forwards like that....

what else is he suppose to do to run a web server and be able to ssh into his box??? should he have firewall rules in place? if he should, he would have to know every ip that he is going to want to connect from so that he could ALLOW that ip in, that would be impossible to know. i am asking because I to am going to be doing the same thing he is soon!

---

### Post by MJN on 2006-11-15
Deepthoughts, are you still having problems? I can SSH to 130.240.218.80 from here okay...

Mathew

---

### Post by DeepThoughts on 2006-11-15
> **MJN said:**
> Deepthoughts, are you still having problems? I can SSH to 130.240.218.80 from here okay...

Mathew
Depends on how you see it. I can't view the webserver nor ssh in if i use the external ip. I have to use the internal ip to get somewhere but as it seems everyone else can use the external ip to view the webserver or connect through ssh.

Are there any reasonable explanation to this? (Because it hasn't been like this before)

---

### Post by MJN on 2006-11-15
Are you using your external IP from within your LAN? If so, are you sure your router can support such 'loopback' connections? Many don't...

You mentioned it used to work so if you haven't changed your router, its config or a local mapping of your domain to a local IP then I can't think what it is...

Mathew

---

### Post by DeepThoughts on 2006-11-15
> **MJN said:**
> Are you using your external IP from within your LAN? If so, are you sure your router can support such 'loopback' connections? Many don't...

You mentioned it used to work so if you haven't changed your router, its config or a local mapping of your domain to a local IP then I can't think what it is...

Mathew
I think you might have given me the explanation. Yes I'm trying to do a 'loopback' connection because I've done that before with no problems. But... I'v recently upgraded the router firmware and might have caused a regression on that point. Since it's my first router and it was possible from the beginning I assumed it was standard to support that "loopbacking".

---

### Post by MJN on 2006-11-15
You'd think so wouldn't you... (unfortunately not though)

Given your firmware was 'upgraded' it's likely it still does... but perhaps there's now an option whereby you need to activate it (perhaps there was before and it was already set).

I'd be very surprised if a new(er) firmware no longer supported loopback connections as, as you say, this would be a real regression of functionality.

If you can't sort the router out a workaround would be to configure your local hosts file with a mapping between your hostname/domainname to the internal IP of your server.

Mathew

---

### Post by PilotJLR on 2006-11-15
> **DeepThoughts said:**
> I think you might have given me the explanation. Yes I'm trying to do a 'loopback' connection because I've done that before with no problems. But... I'v recently upgraded the router firmware and might have caused a regression on that point. Since it's my first router and it was possible from the beginning I assumed it was standard to support that "loopbacking".

I know most version of the WRT54G support loopback... unless you want to revert firmware.

Another solution is to add an entry for your private IP in /etc/hosts, so that you can use the domain name and skip the wan ip / loopback requirement.

---

### Post by tturrisi on 2006-11-16
> **dannyboy79 said:**
> what else is he suppose to do to run a web server and be able to ssh into his box??? should he have firewall rules in place? if he should, he would have to know every ip that he is going to want to connect from so that he could ALLOW that ip in, that would be impossible to know. i am asking because I to am going to be doing the same thing he is soon!

Config sshd to use a different port.  
/etc/ssh/sshd_config
# What ports, IPs and protocols we listen for
Port 3022

I use 3022 instead of 22 and router port forward 3022.  Script Kiddies usually do port scans of common ports.  Port 22 is a common port.  Port 3022 is uncommon so won't get looked for the majority of theb time.

---

### Post by tturrisi on 2006-11-16
To determine if loopback is the issue, try to ssh using the lan ip address (not //localhost)

---

### Post by dataw0lf on 2006-11-16
Are the packets getting to the router?  Or are they not even reaching that?

---

### Post by dannyboy79 on 2006-11-16
the problem with that is you have to hope that the place you're sshing from doesn't block outgoing traffic on that port. like my work only allows outgoing traffic on the common ports so i didn't have an option there.

---

