---
title: "Content filtering using a filtered DNS"
date: 2010-03-11
forum: Ubuntu Christian Edition
---

### Post by mavrick13927 on 2010-03-11
I am attempting to filter internet content for all my computers on my network.  The simplest way to do this seemed to be to have a filtered DNS.  I have signed up for an account at openDNS.  There is another filtered DNS server from [http://scrubit.com/index.cfm](http://scrubit.com/index.cfm), but they appear to still be in beta testing.   The only problem is I have a dynamic IP.  I found the following two programs for solving this problem:
	inadyn
	ddclient
I know openDNS has a config file for ddclient, so it would be more convenient.  Are there any other pros/cons to using one over the other?

Also,. my computers are behind both a modem and a router, will these programs correctly send openDNS the IP of my modem?

Thank you.

---

### Post by david_kt on 2010-03-12
> **mavrick13927 said:**
> I am attempting to filter internet content for all my computers on my network.  The simplest way to do this seemed to be to have a filtered DNS.  I have signed up for an account at openDNS.  There is another filtered DNS server from [http://scrubit.com/index.cfm](http://scrubit.com/index.cfm), but they appear to still be in beta testing.   The only problem is I have a dynamic IP.  I found the following two programs for solving this problem:
	inadyn
	ddclient
I know openDNS has a config file for ddclient, so it would be more convenient.  Are there any other pros/cons to using one over the other?

Also,. my computers are behind both a modem and a router, will these programs correctly send openDNS the IP of my modem?

Thank you.

Why don't you use dansguardian that is pre-installed in ubuntu ce? You could add it to normal ubuntu as well.

DK

---

### Post by mavrick13927 on 2010-03-13
> Why don't you use dansguardian that is pre-installed in ubuntu ce? You could add it to normal ubuntu as well.

DK 

I have looked at DG and think it would be a great tool to use for me personally.  However, I need something that would work on Windows and be easy to set up as I want something I can suggest and set up for friends and family who are almost exclusively Windows users, and are mostly computer illiterate.  So I'm setting up OpenDNS on my computer not only to help me personally, but to also explore options for others as well.  From what I have read of DG, it seems rather difficult to setup.  I have Ubuntu Christian Ed on my laptop and will experiment with DG on that.  My desktop is running Kubuntu, so I think will take even more finesse to get DG running properly on there.

---

### Post by david_kt on 2010-03-13
> **mavrick13927 said:**
>  I have Ubuntu Christian Ed on my laptop and will experiment with DG on that.

Please use dansguardian gui (system > Administration > Dansguardian gui) to configure and control dansguardian. It should be very easy for you.

DK

---

### Post by peterroots on 2010-04-18
I know I am a bit late with this but if you have an old computer laying around you could use it to run IPcop - if you use the proxy in transparent mode and add the url filter addon you will be able to filter the browsing of all the computers on your network. An easy solution if you have the spare hardware (quite a low spec, otherwise useless piece of junk that does not even need a screen and keyboard, once the first part of the install is done).
I have used openDNS and it is rather nice but I have only ever tried it on systems with fixed ip so have no experience of it on a dynamic set up.

---

### Post by mavrick13927 on 2010-04-23
david_kt
I did find and play with the DG GUI.  I only have it on the one computer currently as I am running Kubuntu on the other computer.  I am considering going to Ubuntu Christian Ed on both computers on the next release Lucid.

peterroots
OpenDNS has already addressed the dynamic IP address issue you mentioned.  The solution involves setting up and using ddclient.  The configuration can be found here:
[http://www.opendns.com/support/article/192](http://www.opendns.com/support/article/192)

---

