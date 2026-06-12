---
title: "zenmap found 5 open ports?"
date: 2013-10-14
forum: Security
---

### Post by Kojak Peg on 2013-10-14
Hi everyone 
New-ish to linux. I've just performed a scan with zenmap and it found 5 open ports. Is that something to worry about and if so what do I need to do

Update
I've just done 
> sudo fuser -v ##/tcp

to find out what is running the open ports and it's plex, but why is it keeping ports open when I'm not using it

Update
I had firestarter installed so I thought I'd try installing firewall configeration instead. I even made rules for the 5 ports but still zenmap says the ports are open. So I did deny in and deny out (the deny in rules where in gray and the deny out were in green?) What am I doing wrong? why are the ports still open

---

### Post by TheFu on 2013-10-14
Ports being open is how a computer provides other computing devices with services. Services, or daemons as we call them in UNIX, are usually started automatically at boot and left running in the background. I don't use plex, but isn't it a media server?  Those daemons must be running AND "listenting" on those ports so when external devices contact, then the request can be handled. As long as your system isn't directly on the internet, it is unlikely for anything to access those daemons getting through your router - your router DOES block everything inbound, correct?

If you don't want those services to run, then disable them or unplug the network cable.  

A 100% firewalled PC isn't much use on a network.

Being paranoid is good and so is doing the research that you've already done. Knowing what it running on your systems is a good thing.

BTW, there are external port scanning services that you can use to see how your IP appears to the outside world.  grc.com has one.

---

### Post by trundlenut on 2013-10-14
I assume you ran zenmap on the actual machine and not on a different machine on the same network.  It may be that the ports which are open are internal facing and so not a problem.

---

### Post by Kojak Peg on 2013-10-15
Thanks for the replies

TheFu
Yes plex is a media server, I just didn't know if it was normal or secure to have open ports, even when the program wasn't being use, but if it is normal then I won't worry about it. 

As for my system not being directly on the internet, I'm not sure. In fact, that was one of the things I was trying to determine when I used the Zenmap. When I first installed plex I was using zorin, and for some reason plex couldn't connect to it. So as a temporary solution I used port forwarding, which of course I wasn't happy with. Thankfully now, I'm using ubuntu everything is working, as it should. However, I've never set up my own network, and to be honest it's stretching my computer knowledge to the limit. If it hadn't been for the trouble at the beginning, none of this would have even crossed my mind, but like you say I am security conscious and wanted to make sure I wasn't leaving holes in my system. Unfortunately my security consciousness out strips my computing abilities, which since switching to linux seems to happen on a daily basic, lol  

As for the router it has a firewall from my ISP, so I suppose it does block everything, but again I come up against the same problem. Namely my lack of computing knowledge. When I was a windows user I would have described my abilities as fair to good, but now I'm using linux I know I'm a novice for sure

As for the 100% firewalled PC, I take your point

As for the grc.com website, that's the kind of thing I was looking for and is very useful, but please tell me it's easy and secure to use, lol

trundlenut
I've got a smart tv (wired) and a desktop (wireless) and assuming for a moment I have a LAN and am not connecting over the internet (which at this stage I'm not sure about), I ran zenmap on my desktop. As I mentioned to TheFu above this is stretching my computing knowledge. So please don't assume I know anything and do forgive me if I can't answers. Equally if I'm not asking the right questions please feel free to give any guidance you want no matter how obvious it seems to you, because it probably won't be obvious to my, lol.

Update
So my computer and tv are both connected and my computer is not connected to the plex server. So I'm pretty sure the connection is over a LAN connection. However I have to turn my firewall off for the connection to work, and I'm not 100% sure how to make a rule about it in the uncomplicated firewall. So I tried firestarter instead, but it said "failed to start: the device eth0 is not ready", the only problem is I haven't got a clue how to make it ready

---

### Post by TheFu on 2013-10-15
We were all new to computing and networking at some point.  Not knowing what you don't know is a strange place to be. Almost everybody thinks they know more than the actually do. I did.  Networking is **much** much, much, much larger than most people understand. I'm extremely comfortable around small home and business networks, but think I only know about 10%.

Any way, check my signature for links to learn more about security. Start with "basic" and read more as you learn more.

---

### Post by Kojak Peg on 2013-10-15
Thanks TheFu
I went to grc.com and my computer passed all the test. So I can rest a little easier 

I've got firestarter running and have create an inbound rule to allow connection from my tv and it all seems to be working fine, but I'm definitely going to have to do a lot more research into it    

out of interest which firewall would you recommend ufw or firestarter or is there a better one.

---

### Post by TheFu on 2013-10-15
> **Kojak Peg said:**
> Thanks TheFu
I went to grc.com and my computer passed all the test. So I can rest a little easier 

I've got firestarter running and have create an inbound rule to allow connection from my tv and it all seems to be working fine, but I'm definitely going to have to do a lot more research into it    

out of interest which firewall would you recommend ufw or firestarter or is there a better one.

On Linux, all firewalls use iptables. Anything else is just a GUI over that. It doesn't matter what you use, since in the end, it is iptables, so pick whichever works for your needs.

---

### Post by cariboo on 2013-10-15
As trundlenut said you get different results from nmao (zenmap is the gui interface) depending on where it's run from. If you run it on the local system the results will be different, than when you run it from a remote system. I'll use my own home server as an example.

This the result if I run nmap on the server itself:

```
 nmap localhost

Starting Nmap 5.21 ( http://nmap.org ) at 2013-10-15 15:26 PDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00024s latency).
Not shown: 991 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs
3306/tcp open  mysql
8200/tcp open  unknown
```

This is the result if I run it from the system I'm using at the moment:

```
nmap willy

Starting Nmap 6.40 ( http://nmap.org ) at 2013-10-15 15:27 PDT
Nmap scan report for willy (192.168.0.205)
Host is up (0.00030s latency).
Not shown: 993 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs
8200/tcp open  trivnet1
```

On your system, plex is run as a service (server) so unless you specifically stop it, it will always be running, so will always show up in a port scan, which shouldn't be a problem, if you don't have the port forwarded to the router, for the rest of the world to access.

---

### Post by Kojak Peg on 2013-10-16
THanks for clearing that up for me

As for port forwarding, no I not using it any more. I'd tried it out as a temporary fix, I wasn't happy with having to use it and now I've made a fresh install from zorin to ubuntu I don't need it. However I'm having a new problem, trying to set up rules to allow plex through my firewall, so my tv and plex can access my computer without having to switching off the firewall. I added a rule that allowed my tv to access my computer and it worked fine, but today it doesn't work. And when I try to create the rules to allow the plex server to connect with my computer it won't work either, even though I've set up the ports they mentioned on there website. It's very frustrating and I don't know if it's a fault at there end or with me

Plex tries to connect using UPnP and with the firewall of it can do it now without any problems, however I don't want to keep switching it on and off all the time so I looked at their help website and found the ports they need to use to gain access, namely 
TPC 32400
DUP 1900
  "    32469
  "    5353

however even with the rules in place plex still tried to access random ports using UPnP. I even tried opening those ports, but of course the next time I tried connecting plex would try different ports. So my next option is to go down the listing report in ufw and open each port listed in turn, but I'd really appreciate some guidance because I've only got a little bit of knowledge when it come to firewalls and you know what they say about a little bit of knowledge. I don't want to end up compromising the firewall and not even know it 

Thanks

---

