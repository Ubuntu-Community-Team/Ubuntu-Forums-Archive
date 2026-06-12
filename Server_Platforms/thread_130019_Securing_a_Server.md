---
title: "Securing a Server"
date: 2006-02-15
forum: Server Platforms
---

### Post by Rollo Tamasi on 2006-02-15
hi guys, i'm running the Brezzy Badger Release of Ubuntu as a server for a project i'm working on. I would like to know the best ways to make this server 100% secure. The server is live on the net at the moment.

On the server i am using php5, MYSQL and Apache with tools such as ftp programs and ISPconfig. What would i need to consider in order to make all thoe programs secure. The biggest threat/concern i have at the moment is of a network intrusion.  Any advise or any programs that someone could recommend would be greatly appricated. Thanks

I'm already running Smoothwall as a NAT.

I have a fixed IP. A Netgear Router.

---

### Post by nagilum on 2006-02-15
Two things first: the only way to make a server 100% secure is to turn it off and lock it away. Secondly you better secure the server **before** you put it online, not afterwards.

As for your question, a good starting point for general security is the ["Securing Debian Manual"](http://www.debian.org/doc/manuals/securing-debian-howto). Most of it also applies to Ubuntu since it's based on Debian, and it contains many hints to further documentation. Additionally the manuals of the software packages you want to use often include a section regarding security.

---

### Post by Rollo Tamasi on 2006-02-19
thanks. can anyone recommend me some applications that can prevent network intrusion. I have heard of smurf and snort but i know there must be loads out there.

---

### Post by kmi on 2006-02-21
One option to consider, especially if you have or can find a spare (even obsolete) computer is to set up a hardware firewall : [IPCop]("http://www.ipcop.org") does the trick pretty well (after a 10 minutes setup) and allows you to have a DMZ and all sorts of modules, to monitor (SNORT) and even "reply" to intrusions (Guardian, LaBrea)...
But I'm not sure that is the answer you were looking fo... :-k

---

