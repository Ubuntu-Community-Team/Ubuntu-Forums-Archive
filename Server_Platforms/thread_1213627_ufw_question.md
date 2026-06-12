---
title: "ufw question"
date: 2009-07-15
forum: Server Platforms
---

### Post by dragos2 on 2009-07-15
I have the following situation:

I have on a external interface an open port, I can't move it to another interface
because the application that uses it won't function otherwise, but the application is
on the server itself, this means that the port is exposed to the outside but it is
being used only by the application running on server.

Now using ufw how can I allow access to that port only of the request comes
from the localhost or from the ip of the external interface ?

This is fow Ubuntu Server 8.04 that ships with ufw 0.16.2, can my version
of ufw achieve what I said earlier (blocking port from outside the server but
allowing only request made from the server itself).

---

### Post by windependence on 2009-07-15
I'd love to be able to help you on this but I've never used it. 

I can give you a good suggestion though. You should probably not rely on a firewall on your server because it can easily be DDOS attacked and bring the server down. Set up and old PC with pfsense on it and use that as your firewall box. You can do what you want to do with pfsense and it has a nice GUI or use the command line, your choice. Let me know if you need help.

-Tim

---

### Post by wojox on 2009-07-15
```
sudo ufw allow proto tcp from 192.168.0.2 to any port 80
```

Substitue 192.168.0.2 with whatever external address.
What app are you running? php

---

### Post by giggins on 2009-07-16
@windependence: I don't think the intention of this forum is to encourage people to use something else when they're trying to use the tools provided with Ubuntu to accomplish a pretty standard goal. Although pfSense is a fine product, it doesn't really answer the question...

@dragos2: I know wojox's response can look a little intimidating, so I'll try and explain. Its pretty easy to use ufw to solve simple problems like this. The hardest part is finding out what ports your application utilizes. The example wojox provided is for a webserver listening on TCP port 80. To provide a complete answer, we really need to know what application you're using (or more importantly, what ports it listens on). Here's a good place to learn more about ufw: [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

Along with that, I think there are some confusing parts about your description of the problem. Is your issue that you have two applications on the same server that aren't working, or do you have two (or more) devices trying to connect to each other?

---

### Post by windependence on 2009-07-16
> **giggins said:**
> @windependence: I don't think the intention of this forum is to encourage people to use something else when they're trying to use the tools provided with Ubuntu to accomplish a pretty standard goal. Although pfSense is a fine product, it doesn't really answer the question...



Until the mods tell me not to provide the best solution to the problem I will continue to give the PROPER advice on running servers. I am a professional at this, and I know what I'm doing. Not only that, but I consider dragos to be my friend. I have helped him on problems before, and both of us have helped other posters together. This is why I posted and told him I could not help him, but gave him a sound, solid suggestion. Would you have been as blunt had I told him to use a hardware firewall such as Cisco, Linsys, or Netgear? this kind of attitude is why Windoze has the market. Let's work together.

-Tim

---

### Post by giggins on 2009-07-16
> **windependence said:**
> Would you have been as blunt had I told him to use a hardware firewall such as Cisco, Linsys, or Netgear?

Absolutely.

Both suggestions would be just as out of place. You're suggesting dragos2 install another machine (or appliance of some kind) in order to secure his server... and as great of a suggestion as that is, its still not answering his question. He asked how to achieve his goal using ufw, right? Ubuntu includes ufw, so asking how to work with a tool that's included is a great request. Telling somebody to use something else (when there may not be any real need) is in conflict with your "work together" philosophy, since it may just encourage him to use something else (like FreeBSD, since that's what pfSense is based on).

Just as a helpful hint, its a pretty poor practice to not use software firewalls on servers, since other external firewalls are not infallible, and other machines on his internal network might get compromised. I'm not suggesting that you ONLY use software firewalls on servers, but that you use BOTH external network firewalls AND software firewalls on servers for maximum protection. That said, I think we should work together to help dragos2 reach his goal. :)

As far as pfSense goes, I think it works well. They did a great job improving on m0n0wall, and they added some great features and better hardware support. I would definitely suggest it, or some other form of firewall device to protect your servers from the internet. Ubuntu also makes a pretty great firewall device, since ufw and dnsmasq are pretty easy to get up and running on Ubuntu server.

---

### Post by dragos2 on 2009-07-17
> **windependence said:**
> Until the mods tell me not to provide the best solution to the problem I will continue to give the PROPER advice on running servers. I am a professional at this, and I know what I'm doing. Not only that, but I consider dragos to be my friend. I have helped him on problems before, and both of us have helped other posters together. This is why I posted and told him I could not help him, but gave him a sound, solid suggestion. Would you have been as blunt had I told him to use a hardware firewall such as Cisco, Linsys, or Netgear? this kind of attitude is why Windoze has the market. Let's work together.

-Tim

Thanks, I consider you to be my friend too :)

As fot the firewall part I am not a complete beginner, I have configured iptables before
but I think I achieved my goal using ufw like this:

```

ufw delete allow 1521
ufw allow from 193.19.176.102 to any port 1521 # no proto since it may use both TCP and UDP
ufw allow from 127.0.0.1 to any port 1521

```On port 1521 was Oracle tnslistener because it needs to bind to external interfaces
(don't ask me why) so with the rules above I allowed him to connect only from
the host itself.

I would like to have the ufw limit 22 in 8.04 too but I will do it by hand from
configuratio scripts

pfSense sounds quite good, but I am still struggling to make jails work in freebsd :D

And nmap, the ssh still betrades the OS(there is a ssh patch that write whatever you want instead
of OpenSSH 4.7p1..)

```

PORT   STATE SERVICE VERSION

22/tcp open  ssh     OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)

|  ssh-hostkey: 1024 20:ef:d2:a1:7f:bf:9e:d6:90:f7:b2:5a:17:99:3f:17 (DSA)

|_ 2048 ff:17:d6:b1:7b:0b:3d:2a:8c:17:4f:93:a3:9c:f1:fb (RSA)

80/tcp open  http    Apache Tomcat/Coyote JSP engine 1.1

Aggressive OS guesses: D-Link DSL-G624T wireless ADSL router (MontaVista embedded Linux 2.4.17), or Netgear DG834Bv3 ADSL router or DG834G WAP (93%), Linux 2.6.20 (Ubuntu 7.04 server, x86) (92%), Linux 2.6.18 (89%), Linux 2.6.18-8.el5 (Red Hat Enterprise Linux 5) (89%), Linux 2.6.21 (89%), Linux 2.6.15 - 2.6.26 (87%), Linux 2.6.16 - 2.6.20 (87%), Linux 2.6.18 - 2.6.27 (87%), Linux 2.6.21 (Arch Linux 0.8, x86) (87%), Linux 2.6.27 (Ubuntu 8.10) (87%)

No exact OS matches for host (test conditions non-ideal).

```

---

### Post by cariboo on 2009-07-17
I'll just stick in my 2 cents worth here. Tim has helped a lot of people over the years, and we don't want him to leave any time soon. 

Sometimes you have to use the best tool for the job. Other than using a prebuilt firwall appliance, Learning how to setup iptables rules will serve the op a lot better than relying on a frontend to do the work for you.

Edit: I forgot to provide a link to the [Official iptables howto]("https://help.ubuntu.com/community/IptablesHowTo")

---

### Post by windependence on 2009-07-17
> **giggins said:**
> Absolutely.

Telling somebody to use something else (when there may not be any real need) is in conflict with your "work together" philosophy, since it may just encourage him to use something else (like FreeBSD, since that's what pfSense is based on).


Would this be a terrible thing to learn another tool? It seems he's used *BSD anyway. I really just thought your comment was uncalled for flame bait. I have a real problem with Linux "purists" who won't use anything else. There are all kinds of Unix like OSs out there and some are even more stable and have been around long before Linus mucked with Minix. 

I happen to run all my Zimbra installs on Ubuntu server because I really have no other choice. It doesn't run on Unix or BSD. I like Ubuntu's server version a lot, because i can install ONLY what I need instead of having to deal with all the bloat in the desktop distros. I also run OpenSuSE, CentOS, and Red Hat. Sometimes, I suggest those as well. Why would that be wrong?

Because I get help from the community, I like to give back to the community also, and I do it in an area where I have expertise - the server forum. I do this every day in enterprise environments. I know how it's supposed to be done, so if I don't make a suggestion, Ubuntu or not, it isn't doing anyone any favors. If dragos would have complained, I would have apologized. If you hadn't made your comment, I wouldn't have to post this either.

-Tim

---

### Post by windependence on 2009-07-17
> **cariboo907 said:**
> I'll just stick in my 2 cents worth here. Tim has helped a lot of people over the years, and we don't want him to leave any time soon. 

Sometimes you have to use the best tool for the job. Other than using a prebuilt firwall appliance, Learning how to setup iptables rules will serve the op a lot better than relying on a frontend to do the work for you.

Edit: I forgot to provide a link to the [Official iptables howto]("https://help.ubuntu.com/community/IptablesHowTo")

Thanks Jim, he should note that I never said DON'T use Ubuntu. As you already know, I'm a big advocate of learning as many tools as you can. ....And no, I'm not going anywhere unless they throw me out. ;-)

-Tim

---

### Post by windependence on 2009-07-17
> **dragos2 said:**
> Thanks, I consider you to be my friend too :)



pfSense sounds quite good, but I am still struggling to make jails work in freebsd :D



OFF-TOPIC: We'd love to have you over on daemonforums.org also if you have the time. It's just all the BSDs.

-Tim

---

### Post by dragos2 on 2009-07-17
> **windependence said:**
> OFF-TOPIC: We'd love to have you over on daemonforums.org also if you have the time. It's just all the BSDs.

-Tim

I will, thanks ;)

---

### Post by Kolipoki on 2009-07-17
> **giggins said:**
> @windependence: I don't think the intention of this forum is to encourage people to use something else when they're trying to use the tools provided with Ubuntu to accomplish a pretty standard goal. Although pfSense is a fine product, it doesn't really answer the question...
Well I don't think the intention of this forum is to limit people to use the tools provided with Ubuntu, neither. 

Gotta say, the statement quoted sounds like a fundamentalist, absolute controlling, gang-pack ideology. Sounds totally contrary to what I have learned from the open source community's perspectives over the years. 

"Open source" seems to hold hands much better with "open mind". I didn't take Tim's suggestion as a sole promotion of any product. I will actually thank anyone who suggests any good and legal solution, in or out the box.

---

### Post by giggins on 2009-07-17
Wow, I gotta say that the commentary on this thread is pretty ridiculous... I'm a huge fan of open source and having an open mind. I use both in my personal and professional life continuously. I think the sad part is that few people bothered to look back at dragos2's problem along with the people who've actually helped him answer his question. I think out of 13 (now 14) posts in this thread, only a few (like one or two tops) actually helped him. Seems like wojox did the most, and wojox did it in a simple and appropriate manner by ANSWERING THE QUESTION. You don't see how telling dragos2 to use pfSense (or anything else external) didn't really help him? That was all I was trying to point out, that using an external firewall, be it pfSense or anything, is a great idea, but its not answering his question.

I think a good comparison for what happened here, is if I went to a FreeBSD forum and posted a request for "How to install a web server using ports" and someone answered by saying "Setup a Linux box and run the web server on there". Truely, this is not a bad idea, but it also has nothing to do with what I ask, right? Geez, people, don't take everything so personally. 

I was just trying to help keep the thread on topic by focusing obviously experienced and knowledgable people on the question at hand.

---

