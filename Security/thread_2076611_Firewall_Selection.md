---
title: "Firewall Selection"
date: 2012-10-26
forum: Security
---

### Post by mike acker on 2012-10-26
in my FireWall I would like to be able to restrict certain applications to no internet access.*

which firewall?  or do I use AppArmor for this ?

* fundamentally allow net access to only programs that are supposed to use the net: Firefox, Thunderbird

---

### Post by JKyleOKC on 2012-10-26
That's a task for AppArmor, not for any firewall front-end. The firewall capability of Linux is all achieved via the netfilter portion of the kernel, and netfilter deals specifically with individual packets that are going to or from the network interfaces. These packets carry ID for addresses, but nothing at all to directly associate them with the applications involved. Thus the firewalls cannot include application data itself in the rules that they generate; the closest they can come is to identify specific ports -- but an application can attempt to use any port, so there's no one-to-one correspondence between port number and the app.

AppArmor works at a different level, and can control an application's access to specific resources -- including network interfaces. However I don't use it and cannot give you any more detail than this, about it. Others here, though, can, and there's an excellent sticky about it that can get you started...

---

### Post by mike acker on 2012-10-26
> **JKyleOKC said:**
> That's a task for AppArmor, not for any firewall front-end. The firewall capability of Linux is all achieved via the netfilter portion of the kernel, and netfilter deals specifically with individual packets that are going to or from the network interfaces. These packets carry ID for addresses, but nothing at all to directly associate them with the applications involved. Thus the firewalls cannot include application data itself in the rules that they generate; the closest they can come is to identify specific ports -- but an application can attempt to use any port, so there's no one-to-one correspondence between port number and the app.

AppArmor works at a different level, and can control an application's access to specific resources -- including network interfaces. However I don't use it and cannot give you any more detail than this, about it. Others here, though, can, and there's an excellent sticky about it that can get you started...

thanks; this makes good sense. everything i found in the firewalls matches your description.

i read the sticky on AppArmor; it doesn't look too bad, particularly if i can find a starter profile

---

### Post by JKyleOKC on 2012-10-26
As one old mainframer to another, it's still good to know what the machine is doing beneath all those frills of the high-level languages and simplified interfaces. If you want a quick and quite good introduction to what's involved in the packets that handle the networking, install "wireshark" from the repositories, modify it to be setuid and owned by root, and capture your traffic for a couple of megabytes while browsing the internet. That will give you a great assortment of packets to look through, and the program will sort out their contents and show you each part quite clearly. This is what finally let me grok the packet-switching paradigm, after many years of simply taking it for granted.

And to top it off, wireshark is a primary troubleshooting tool when things go sour!

I learned programming in the first place by doing machine-language programming on an Olivetti, around 1966 or so, then moved on to writing assembly language for a G-E machine where I learned the rudiments of system design and maintenance. Didn't get into micros for years after they first showed up, but for the past 15 years or so haven't dealt with anything else...

---

### Post by brinks99 on 2012-10-27
I am trying to set up a website for a university project and wanted to rent a server from [www.digitalocean.com](www.digitalocean.com) to host the site while im doing development so I could work on it and access it from anywhere.

My question is can I configure my firewall to only allow traffic from specific devices(using the device MAC address) of my choice and block all port of any device MAC address I haven't selected.

My understanding of networking protocol is very limited and I wasn't sure if even the origins MAC address was sent in the packets.

---

### Post by Linuxisfast on 2012-10-27
[http://tomoyo.sourceforge.jp/2.2/index.html.en](http://tomoyo.sourceforge.jp/2.2/index.html.en)

TOMOYO is a security module which focuses on behavior of a system. A process is created to achieve something. TOMOYO lets each process declare behaviors and resources needed to achieve its purpose (like an immigration officer) and permits only declared behaviors and resources (like an operation watchdog). This approach made it possible for users to understand how a Linux system works. You can use TOMOYO as a system analysis tool as well as an access restriction tool.

---

### Post by mike acker on 2012-10-27
> **brinks99 said:**
> I am trying to set up a website for a university project and wanted to rent a server from [www.digitalocean.com]("http://www.digitalocean.com") to host the site while im doing development so I could work on it and access it from anywhere.

My question is can I configure my firewall to only allow traffic from specific devices(using the device MAC address) of my choice and block all port of any device MAC address I haven't selected.

My understanding of networking protocol is very limited and I wasn't sure if even the origins MAC address was sent in the packets.

please allow me to recommend [ CoreComm Services]("http://home.core.com/home/")  . I have used them for years for my personal website

---

### Post by mike acker on 2012-10-27
> **JKyleOKC said:**
> As one old mainframer to another{snip}

I learned programming in the first place by doing machine-language programming on an Olivetti, around 1966 or so, then moved on to writing assembly language for a G-E machine where I learned the rudiments of system design and maintenance. Didn't get into micros for years after they first showed up, but for the past 15 years or so haven't dealt with anything else...

thanks, pard!!

I learned programming on an IBM 1620 at K- College and from there moved into the IBM/360 . we did a lot of assembly programming in those days, mainly because the programs required roughly 8:1 less memory and executed correspondingly quicker than e.g. COBOL

we converted a lot of programs for folks from 1401 to System/360.   We could not teach 360/asm to an autocoder programmer generally -- they could not understand privileged instructions and storage protection and most of them took up RPG

after my stint as an MFT/MVT systems programmer I ended up as a RACF administrator for the local hospital 370MVS . 

c.1990   as folks started hooking up PCs the virus problem started.  there were a lot of pranks in those days -- Falling Letters, Stoned, etc but that business quickly morphed into what we have today: espionage and fraud

any app that you run can potentially be exfiltrating information about you, and once that happens your information can end up anywhere...

our Linux systems appear to be better protected against un-authorized programming than some other systems but it is easy to see that there are other concerns as well.  particularly scamming ( aka "Spear Phishing" ) -- but also espionage -- carried out by what we might think are legitimate applications.

I think Canonical missed a good chance in implementing their "work spaces". If these could have been made into concurrently operating separate log-ons they could be used to provide application isolation by just using a separate log-on rather than fussing with AppArmor.  Particularly if the internet access could be configured as an on|off option at log-on affecting only the one "work space" .

---

### Post by JKyleOKC on 2012-10-27
The workspaces were a part of the X Windows System long before Canonical came on the scene. I think they were around even before Linux! Since Linux is a multi-user multi-processing system, you actually could use different log-ins at the same time to provide process isolation. I do something of the sort with my multiple VMs, in fact, although I don't make any attempt to isolate them from each other. I've actually gone the other way to simplify communication between them so that I can easily pass data between them.

I forgot to mention one part of my past: programming a database lookup and editing system for a PDP-11 system where the entire o/s was in DEC Basic. That was a true exercise in frustration although I finally got it working well enough to get paid for it. Also taught a class in system design on the 1440 for a year at a local tech school, volunteered by my employer (G-E). Really disliked the IBM variable-length opcodes; G-E's fixed word length made much more sense to me...

---

### Post by JKyleOKC on 2012-10-27
> **brinks99 said:**
> My question is can I configure my firewall to only allow traffic from specific devices(using the device MAC address) of my choice and block all port of any device MAC address I haven't selected.I don't think it's a part of the standard packets and thus isn't a filter candidate. However you can set the filters up to allow traffic only from specific IP addresses, so if you can have static IP addresses for your desired devices that could serve the same purpose.

I highly recommend using "wireshark" to view all the packets; it's easy, with it, to see what values are in every packet, and to determine exactly what is going over the wire in both directions. You'll see exactly how IP addresses get translated into MAC addresses with a multi-packet exchange, in which the MAC address never gets into the packet headers...

---

