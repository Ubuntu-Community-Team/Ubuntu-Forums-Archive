---
title: "Learning materials for Ubuntu?"
date: 2012-11-19
forum: The Cafe
---

### Post by Ragi1992 on 2012-11-19
I am interested in getting books or maybe an educational application that can teach me all about Ubuntu and the Command Prompt, as well as general tips and tricks.

Any references on books or other educational material on these subjects?

---

### Post by mag1strate on 2012-11-19
Pretty much most handbooks on linux can be used for nearly any distro. 

Specialized ubuntu books to me seem sort of useless because most of the information you can find about ubuntu you can find through  the internet.

---

### Post by mastablasta on 2012-11-20
Ubuntu manual (see my signature)
 
ubuntu help pages: [https://help.ubuntu.com/](https://help.ubuntu.com/)
 
linuxcommand.org - a free e-book

---

### Post by Erik1984 on 2012-11-20
Just my opinion: Most paper books on IT subject seem like a waste of money and trees, unless they teach some skill that can be widely applied. Application specific information (especially related to the GUI) rapidly becomes outdated. More useful (and especially more up to date) information can be found online.

---

### Post by Takanakathehacker on 2012-11-20
You can learn a lot just from looking at the manual pages of each application. 

For instance....

> Yo@hoho:~$ man ping

PING(8)                System Manager's Manual: iputils                PING(8)

NAME
       ping, ping6 - send ICMP ECHO_REQUEST to network hosts

SYNOPSIS
       ping  [-LRUbdfnqrvVaAB]  [-c count] [-i interval] [-l preload] [-p pat&#8208;
       tern] [-s packetsize] [-t ttl] [-w deadline] [-F flowlabel] [-I  inter&#8208;
       face] [-M hint] [-Q tos] [-S sndbuf] [-T timestamp option] [-W timeout]
       [hop ...] destination

DESCRIPTION
       ping uses the ICMP protocol's mandatory ECHO_REQUEST datagram to elicit
       an  ICMP  ECHO_RESPONSE from a host or gateway.  ECHO_REQUEST datagrams
       (``pings'') have an IP and ICMP header, followed by  a  struct  timeval
       and  then  an  arbitrary  number  of ``pad'' bytes used to fill out the
       packet.

OPTIONS
       -a     Audible ping.

       -A     Adaptive ping. Interpacket interval adapts to  round-trip  time,
              so  that  effectively  not more than one (or more, if preload is
 Manual page ping(8) line 1Not all programs have a man page though in which case, you can usually still acquire a small list of editable switches/parameters by using the switch.

> ping --help

You can also learn a fair amount in a more advanced way, by studying the source code of programs/modules. The degree of difficulty to start, varies from program/script to program/script, as the best source for learning is usually the programmers notes/references. 

You do get some instances where there are no notes, or overly obfuscated code, but this is usually few and far between, and usually happens when someone with an overly big head says look at me aren't i clever? *Short Answer = no. ;)

---

### Post by BlinkinCat on 2012-11-20
Hi, 

The guide by aysiu (link in my signature) may prove useful.

Cheers - :)

---

### Post by syerges on 2012-11-20
You will learn the most by searching in the forums for what it is you are more interested in and following those. If you really want to learn, do what the person who had a problem did and follow the group's debugging. You will learn more that way and possibly come across a mistake they made to help them.
:popcorn:

---

### Post by mamamia88 on 2012-11-20
Only half kidding [https://wiki.archlinux.org/](https://wiki.archlinux.org/)

---

