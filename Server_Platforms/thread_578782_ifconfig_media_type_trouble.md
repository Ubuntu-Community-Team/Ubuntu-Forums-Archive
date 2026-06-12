---
title: "ifconfig media type trouble"
date: 2007-10-17
forum: Server Platforms
---

### Post by XeroxGUI on 2007-10-17
Hello, I am using Dapper Drake with no updates (no internet connection as of yet, new network). I was excited to get this Net Admin job for a popular local business, and I put Dapper on the server using samba for a windows domain. BUT-heres where it gets sticky-being paranoid over security, I DELETED sudo, using $su root for root permissions(I put the desktop distro on the server since I thought the internet would be up quicker, and for a failsafe GUI). But now, with no extra software installed or ability, I have to use ifconfig. See, the switch uses 100baseT ports, and my NIC is going at 1000BaseT, but when I use $ifconfig eth0 media 100baseT, it throws the "This Operation Not Supported" message, which google tells me Others have seen as well. Is there any way around this? I REALLY need this server up, since the intranet comes before the internet in this scenario!:(

---

### Post by MJN on 2007-10-18
Post the output of **ethtool eth0 **and we can see what media types are supported. The card ought to negotiate with the switch port and find the lowest-common-denominator configuration so the fact that it isn't may suggest you won't be able to get it to be compatible (let's not jump too far ahead of ourselves just yet though!).

What's all this about deleting sudo?! Does your new employer know what you're upto? ;)

Mathew

---

### Post by XeroxGUI on 2007-10-20
Weekend off- I will post output on Monday after work(which is play 4 me!)

Speaking of which, my employer is the "just make it work for them" type and understands that once all is set up, remote admin means he'll never see my fat a** again unless something major goes wrong! Nobody over there is gonna touch the server, and it is on battery backup, surge, in a three-key only tech closet, AND the front power button has been taken off(only availibly via key!). Sorry, just love to brag on a good network!:guitar:

---

