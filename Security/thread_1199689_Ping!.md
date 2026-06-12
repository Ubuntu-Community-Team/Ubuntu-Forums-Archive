---
title: "Ping!"
date: 2009-06-29
forum: Security
---

### Post by jwkungfu on 2009-06-29
This might be opening up a can of worms? But here goes...

I was "shown the light" by a friend who converted me from the "dark side" of operating systems to the only sensible choice, which is of course Linux/Ubuntu about 18 months ago after 'contracting' a virus...

I am particularly security conscious and now that I am finally getting down to really learn about computers/security/linux/ubuntu (etc), I have downloaded the Ubuntu Pocketbook (Keir) and I have just finished the chapter on security...

I opened up 'Firestarter' and turned off ICMP filtering. I was under the impression that one of the reasons MS computers are vulnerable is because they alway respond to 'pings'...?
If I'm right, wouldn't it be better if all computers were set to 'not' to respond to pings? And then only turn the function back on when there was a fault that needed to be tested with a ping... (and then turned back off when fixed)...

Have I put myself at some sort of disadvantage by having my ping response turned off? I seem to be able to function perfectly normaly without it so far...?  

Thanks in advance for responses!

---

### Post by decoherence on 2009-06-29
The only real disadvantage is that you won't be able to ping your machine to see if it's alive.

The main advantage is that nobody else will be able to ping your machine to see if it's alive.

Ping is useful mostly to network administrators and hackers to see whether or not a particular IP address is being used. If you've never had to use ping then you probably don't need to allow it.

---

### Post by sasho_zl on 2009-06-29
In these days the ICPM filtering wont fool anyone who is interested in your machine. Most of the port scanning software out there has the option to check if you are a "live" host even if your computer is not responding to ping requests.

---

### Post by koenn on 2009-06-29
what decoherence said, but nothing more than that.

i.e. when a PC connects to an internet server, that server will be aware of your PC no matter whether ping is disabled or not. 
If you run a server, it will have at least 1 listening port wich makes it visible on the internet, ping or not. 

besides that, most security issues with MS for every-day users come from websites or through mail, and those already know how to get to your PC without having to ping it.

---

### Post by bodhi.zazen on 2009-06-29
> **sasho_zl said:**
> In these days the ICPM filtering wont fool anyone who is interested in your machine. Most of the port scanning software out there has the option to check if you are a "live" host even if your computer is not responding to ping requests.

> **koenn said:**
> what decoherence said, but nothing more than that.

i.e. when a PC connects to an internet server, that server will be aware of your PC no matter whether ping is disabled or not. 
If you run a server, it will have at least 1 listening port wich makes it visible on the internet, ping or not. 

besides that, most security issues with MS for every-day users come from websites or through mail, and those already know how to get to your PC without having to ping it.

Although opinions will vary, responding to a ping is not IMO a security hole.

Security holes come from listening services or servers. In Ubuntu the culprits are VNC , VNC, and VNC (desktop sharing).

Windows is vulnerable due to a number of issues including the fact that a default installation has a number of documented and undocumented services.

There was a time when responding to ping was perhaps a vulnerability, but with modern cracking techniques not so.

If you wish to read about such things, take a look at say nmap :

[http://nmap.org/book/man.html](http://nmap.org/book/man.html)

For Ubuntu security see :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

In terms of Firstarter, the advice to install firestarter is IMO very much out dated. Ubuntu now uses ufw, and if you want a gui interface, gufw.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

Firestarter and ufw are not firewalls, but rather front end configuration tools to iptables.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

The configuratin tools often conflict so you should not use more then one at a time. So either remove firestarter or ufw.

```
sudo apt-get remove --purge firestarter && sudo apt-get install gufw
```
  
Or, if you prefer, remove ufw.

---

### Post by brian_p on 2009-06-29
> **jwkungfu said:**
> 

I was under the impression that one of the reasons MS computers are vulnerable is because they alway respond to 'pings'...?

Millions of other Windows and Linux users think the same. How wrong they are!

> If I'm right, wouldn't it be better if all computers were set to 'not' to respond to pings? And then only turn the function back on when there was a fault that needed to be tested with a ping... (and then turned back off when fixed)...

You are misguided. Being invisible is the stuff of science fiction.

> I seem to be able to function perfectly normaly without it so far...?  

You can function pretty normally in every day life if you go about clothed in a black plastic bag from top to toe.

---

### Post by bodhi.zazen on 2009-06-29
OMG :shock:

You forgot your [AFDB]("http://zapatopi.net/afdb/")

---

### Post by brian_p on 2009-06-29
> **bodhi.zazen said:**
> OMG :shock:

You forgot your [AFDB]("http://zapatopi.net/afdb/")

I had complete confidence in black plastic bags until:

[http://coolcosmos.ipac.caltech.edu/image_galleries/handinbag.html](http://coolcosmos.ipac.caltech.edu/image_galleries/handinbag.html)

---

### Post by bodhi.zazen on 2009-06-29
:lolflag:

---

### Post by scorp123 on 2009-06-29
> **jwkungfu said:**
> I was under the impression that one of the reasons MS computers are vulnerable is because they alway respond to 'pings'...? Responding to a "ping" isn't a problem. Running truckloads of broken and badly secured protocols in the background is the real problem. Just go to any Windows system and take a look at the "Services" control applet (you should find it somewhere in the "Administrative Tools" section). There are tons and tons and tons of processes running in the background, accepting connections from anywhere, and even better: most of those processes run with full administrator priviledges. _THIS_ is what makes Windows security so horribly bad: a hacker or his viruses are always guaranteed to find a handful of stupid services that are willingly accepting incoming connections .... Instead of shutting down those (mostly obsolete) background services Microsoft though that giving users a (a really bad) firewall or this new "User Access Control" big-brother thing would be enough. But the many Windows viruses still out there prove: It isn't.

Ping isn't the real problem ... It's all the smelly old truckload of junk protocols in the rest of Windows networking that really causes the troubles.

---

### Post by Dr Small on 2009-06-29
I use ping to determine if hosts are online or not. It's pretty convenient for that. But it isn't a security vulnerability for a machine to respond to a ping request.

---

### Post by rookcifer on 2009-06-29
Most of this "Stealth" firewall hoopla was started by one man -- Steve Gibson.  This is the same guy who said raw sockets would bring the Internet to a halt.

Bottom line: a closed port is just as good as a "stealthed" one.  If an attacker is after your machine, it isn't going to matter whether you stealth the ports or not -- he already knows your machine exists.  You should only be concerned about making sure there are no unsecured services running.

And ICMP is not really a security hole in itself but I prefer to drop all incoming packets to that port since there is no reason anyone "out there" needs to ping me.  Moreover, if you leave ICMP open, your machine could possibly be used for SMURF attacks (in other words your box *could* be used for a DDOS.  However, SMURF attacks do not require your box to be compromised, only that your machine respond to pings as it normally would).  It should be said that SMURF attacks are more of a thing of the 90's.  They are rare now.

---

### Post by jwkungfu on 2009-06-30
Many many thanks for all your help!
I have run that script in a terminal as well.

One thing I liked about Firestarter was that it actually showed connections... doesn't seem that ufw does that? Does it?

I will check out the other links too!

Namaste.

john

---

### Post by bodhi.zazen on 2009-06-30
> **jwkungfu said:**
> Many many thanks for all your help!
I have run that script in a terminal as well.

One thing I liked about Firestarter was that it actually showed connections... doesn't seem that ufw does that? Does it?

I will check out the other links too!

Namaste.

john

Linux is "modular". By that I mean in Windows you tend to have one single monolithic application that does everything.

In Linux you tend to have many smaller applications performing specific tasks.

So take firewalls. You have iptables, then you can configure iptables with UFW, gufw, firestarter, shorewall, guarddog, etc, etc ...

To monitor your traffic you have snort, wireshark, watch your logs, etc, etc, etc.

---

### Post by koenn on 2009-06-30
> **rookcifer said:**
> Most of this "Stealth" firewall hoopla was started by one man -- Steve Gibson.  This is the same guy who said raw sockets would bring the Internet to a halt.

Bottom line: a closed port is just as good as a "stealthed" one.  If an attacker is after your machine, it isn't going to matter whether you stealth the ports or not -- he already knows your machine exists.  You should only be concerned about making sure there are no unsecured services running.

And ICMP is not really a security hole in itself but I prefer to drop all incoming packets to that port since there is no reason anyone "out there" needs to ping me.  Moreover, if you leave ICMP open, your machine could possibly be used for SMURF attacks (in other words your box *could* be used for a DDOS.  However, SMURF attacks do not require your box to be compromised, only that your machine respond to pings as it normally would).  It should be said that SMURF attacks are more of a thing of the 90's.  They are rare now.

A SMURF attack is based on pinging the broadcast address of a network - causing all hosts on that network to start sending replies - it's this amplifier effect that made smurf effective as a DOS. But replying to ping broadcasts is now disabled by deafault on most networked hosts. 

raw sockets can be used for creating ip packets with spoofed addresses, and anything else that requires doctored IP packets. That's why you usually need root/admin privs to use them. That's the reason that e.g. nmap requires sudo for some scan modes. Given that Windows users tend to run as admin by deafult (especially in the days you're referring to) and in general have no idea what their computers are doing, it's conceivable that heaps of them would be running malware which could eg soof a sender address to make that address a target of a DOS attack. 
Gibson likes to make noise and promote his products, but sometimes he has a point.

---

### Post by Polaris96 on 2009-06-30
One of the first things to consider is:  Who's trying to breach your system?  Hardening past a certain point becomes more of a hobby than a necessity. 

ping is a super useful tool.  I doubt it's ever worth worth the headaches you get from ignoring pings - at least if you do any networking.  With ping, traceroute, and netstat, you can do almost all of your net admin from kernel utilities.

Have a look at bastille, btw.  It's slightly older technology but they do a pretty good job of tightening up the system and explain a lot of security basics in the process.  

Now, it's MY turn to open a can of worms :)  ... Anybody running SELINUX out there?

---

### Post by bodhi.zazen on 2009-06-30
> **Polaris96 said:**
> Anybody running SELINUX out there?

Yes, although not on Ubuntu. If you want to try selinux , try Fedora 11 / Centos  or similar.

---

### Post by rookcifer on 2009-06-30
> **Polaris96 said:**
> One of the first things to consider is:  Who's trying to breach your system?  Hardening past a certain point becomes more of a hobby than a necessity. 

I agree.  Linux is secure enough by default that the chances of being compromised are slim, especially if one follows basic precautions.

> ping is a super useful tool.  I doubt it's ever worth worth the headaches you get from ignoring pings - at least if you do any networking.  With ping, traceroute, and netstat, you can do almost all of your net admin from kernel utilities.

You can disable pings to the Internet at large yet still have them enabled locally.

> Have a look at bastille, btw.  It's slightly older technology but they do a pretty good job of tightening up the system and explain a lot of security basics in the process.  

The last time I checked, Bastille had not been updated for the latest Ubuntu.

> Now, it's MY turn to open a can of worms :)  ... Anybody running SELINUX out there?

Not here, although I do when I run Fedora.  I actually prefer AppArmor.  It's much easier to configure and I can easily create a profile for all my unprivileged network facing apps.  Try writing a policy for Firefox in SELinux and see how much hair you have left when done. :p  The default Fedora SELinux policy is targeted and usually only covers root privileged network facing daemons.  The targeted profile does nothing to protect user-level stuff.

Now, I will agree that SELinux is probably more "failsafe" but that's another subject..

---

### Post by Polaris96 on 2009-06-30
One of my clients is the US Gov.  They require SELinux.  It's becoming problematic because I don't have any Red Hat based flavours, right now.

I didn't know bastille isn't updated anymore, I still think the interactive tutorial would be worthwhile for a novice to page through.  It does a nice job of nailing down any obvious holes.  ...I mean it's bastille, not Guatanamo, after all.

Oh, cifer, one last thing about ping.  My network is WAN because I convinced my friends to all go on the bird by offering free remote admin via ssh.  it works great but I need ping to be netwide (freakin' ISP provided routers...).  I definitely should've mentioned Ping can operate LAN only if you want.  Thanx for the catch.

---

### Post by jwkungfu on 2009-07-02
Have a look at bastille, btw.  It's slightly older technology but they do a pretty good job of tightening up the system and explain a lot of security basics in the process.  

...............................................................

Can you recommend a website & / address for this Bastille please?

Many thanks for the reply!

Cheers!

---

### Post by bodhi.zazen on 2009-07-02
Here are some nice slide sets on SELinux :

[SELinux for Everyday Users]("http://www.slideshare.net/PaulWay/selinux-for-everyday-users") 

[Slug 2009 06 SELinux For Sysadmins]("http://www.slideshare.net/PaulWay/slug-2009-06-selinux-for-sysadmins")

---

