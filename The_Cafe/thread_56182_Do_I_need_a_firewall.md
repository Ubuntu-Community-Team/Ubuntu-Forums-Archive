---
title: "Do I need a firewall?"
date: 2005-08-11
forum: The Cafe
---

### Post by krusbjorn on 2005-08-11
In [this](http://www.ubuntuforums.org/showthread.php?t=55754) thread, Dave919 stated the following:

[QUOTE=dave9191]Are you running any services like a web server or a mail server on your computer or any other services? Is your compuer being used as a gateway for a network? If the answer is no to both of the questions you dont need a firewall. This is linux, not windows. 

But if you are still determined, then at [www.ubuntuguide.org](www.ubuntuguide.org) you can find instructions on installing firestarter :)

Dave[/QUOTE]

Here's my question:

I know nothing about networking. Nothing. Until now, I've been behind a dlink router at home, just having the factory setting firewall on by default. However, this monday, I'm moving to a new apartment, and I'm going to plug my computer right into a low budget dsl-modem. No firewall in that one.

I have been speaking to a few people, asking how secure Linux is (switched to Ubuntu from WinXP 5 months ago). Most people don't know, a few say "Give it a week and you'll have people sneaking around on your hard drive". I've been googling, getting everything from "Linux is completely safe" to "Always use a firewall, or you'll regret it sooner than you think".

I'm not using my computer for anything but desktop use. No web- or mail server, no gateway. Just plain desktop use.

So basically, all i wonder is, how dangerous is it to hook up my computer, completely unprotected, to the web?

Cheers.

---

### Post by Stormy Eyes on 2005-08-11
You probably don't need one, but if you feel more comfortable with a firewall between your PC and the net, then by all means set one up. It's better to be a little paranoid than it is to be trusting and naive.

---

### Post by az on 2005-08-11
The default ubuntu setup is completely safe.  If you install software from universe or other non-standard repositories, you will have to know what they do to get a sense of whether you need additional protection or not.   

Even if you install tons of packages from Universe, though, I hardly think anyone will be able to poke around your hard drive.  That only can happen in windows where you do not know about the security policies in place, nor can you control them.  In windows, by natureof their market, there are security vulnerabilities built-in.  This is not the case in Ubuntu.

For what it is worth, you can still use your dlink router to connect to the net.  You plug in your modem to the line, the router to the modem and your computer to the router.  You will get the benefit of the router's firewall for no effort.

---

### Post by krusbjorn on 2005-08-11
[QUOTE=azz]For what it is worth, you can still use your dlink router to connect to the net.  You plug in your modem to the line, the router to the modem and your computer to the router.  You will get the benefit of the router's firewall for no effort.[/QUOTE]

yeah, but i think my mom and sister still want to be able to use the internet where i'm moving out from ;)

Thanks for the answers guys. Very much appreciated!

---

### Post by sapo on 2005-08-11
I use Firestarter here.. but the log just says "Microsoft DCOM Attack"

I never used firewall in a linux desktop, i use in my pc cause i run apache, mysql, ssh and ftp here.. so its unsafe to leave it all without a firewall.. but just to connect and browse the internet you dont need one :p

---

### Post by nonutopia on 2005-08-12
Chances are pretty big that your low budget modem has a NAT. a NAT is a routing table its not a firewall but it pretty similair in its use. Normally it would be confgured  in a way that allows all traffic from the local net to the internet but from the internet to the local net it will block anything wich isnt allowed trough the rules of the routing table or NAT. You might want to do some research on your new modem. 

You can use an online port scan or ask a friend to scan you with nmap orso to test your setup and find out wich ports are open from the net. 

I myself use a iptables based firewall wich is configured trough a kind of script called shorewall on a very old but kicking pentium pro 200 mhz box. An other option is to install a distro like smoothwall or clarkconnect on a box with 2 NIC's (network card interface) because it has a lot more options then a NAT. But if you dont have to do compilcated routing or forwarding stuff the NAT will probably work just fine for you.

Edit: and the NAT will probably be perfectly able to keep you and your network safe unless weird things happend :)

---

