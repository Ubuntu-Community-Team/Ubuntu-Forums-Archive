---
title: "firewall"
date: 2005-06-15
forum: The Cafe
---

### Post by vega44 on 2005-06-15
are there better firewalls out there for linux? then the one that comes with it? what are some ways to improve the linux firewall? are there ways to set up a alert that pops up in a window telling you are under atteck? i will be intalling ununtu on a laptop ....... when i find one on ebay.

i hang out in black hat hacker rooms and noobs try to hack me all the time. and im using windows. with sygate pro, im going to find an old computer and put smoothwall on it..... but i don't think any time soon.):

---

### Post by sonny on 2005-06-15
have you tried firestarter??? I used it for a couple of months and tough it was a good firewall; you have to do a lot of configuring if you want it to suit your need, though.

---

### Post by Optimal Aurora on 2005-06-15
I like the one on fedora although you have to go about configuring it in a different way which I still have trouble doing... But right out of the box, the fedora firewall works good to stealth and hide almost all the ports... (almost they may be some that are open or closed)... But using ubuntu I like firestarter but it isn't to me all that powerful... 

Hay isn't this like a support question...

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=lowlux]when i find one on ebay.
:[/QUOTE]

I reccomend Toshibas for Linux compatibility.

---

### Post by desdinova on 2005-06-15
There's absolutely nothing wrong with ipchains and it walks all over any Windows equivalent btw. If you want pop up text boxes there's addons to it, but I prefer a console open.

PS install portsentry and hostsentry..... Now thats cool cover.

---

### Post by vega44 on 2005-06-15
[QUOTE=Optimal Aurora]I like the one on fedora although you have to go about configuring it in a different way which I still have trouble doing... But right out of the box, the fedora firewall works good to stealth and hide almost all the ports... (almost they may be some that are open or closed)... But using ubuntu I like firestarter but it isn't to me all that powerful... 

Hay isn't this like a support question...[/QUOTE]
is there anything like firestarter for windows? (:

---

### Post by student on 2005-06-15
Firestarter seems to be the most recommended.

<offtopic wining>
I've always hated firewall's with their allert's, they break my concentration more than it's already interrupted.
</offtopic>

---

### Post by desdinova on 2005-06-15
I prefer shorewall as its unobtrusive and starts as a service right after my network is up

---

### Post by jdong on 2005-06-15
Firestarter, shorewall, iptables, whatever. They are all the same firewall. Just different graphical methods of configuring it.

---

### Post by desdinova on 2005-06-15
Oh I know ;-)  I just like shorewall as its unobtrusive and "Just works" ;-)

---

### Post by Brunellus on 2005-06-15
[QUOTE=lowlux]are there better firewalls out there for linux? then the one that comes with it? what are some ways to improve the linux firewall? are there ways to set up a alert that pops up in a window telling you are under atteck? i will be intalling ununtu on a laptop ....... when i find one on ebay.

i hang out in black hat hacker rooms and noobs try to hack me all the time. and im using windows. with sygate pro, im going to find an old computer and put smoothwall on it..... but i don't think any time soon.):[/QUOTE]
 gee.  if you were as 1337 as you were trying to sound, I figure you might have already known the answer to your question, I mean, since all the people trying to h4x0r your computer are noobs, anyway.

Why not install & run ubuntu on the computer you're actually using?  Why wait for the laptop off ebay?

---

### Post by jdong on 2005-06-15
[QUOTE=lowlux]are there better firewalls out there for linux? then the one that comes with it? what are some ways to improve the linux firewall? are there ways to set up a alert that pops up in a window telling you are under atteck? i will be intalling ununtu on a laptop ....... when i find one on ebay.

i hang out in black hat hacker rooms and noobs try to hack me all the time. and im using windows. with sygate pro, im going to find an old computer and put smoothwall on it..... but i don't think any time soon.):[/QUOTE]
Umm. Firestarter has an alert icon in tray whenever a packet was dropped by the firewall. As far as alert windows go, that just drives me nuts. If an attacker made it through your computer, the firewall wouldn't know. If an attacker failed miserably, the firewall would pop up an alert. Doesn't make much sense, does it?

---

### Post by vega44 on 2005-06-15
[QUOTE=Brunellus]gee.  if you were as 1337 as you were trying to sound, I figure you might have already known the answer to your question, I mean, since all the people trying to h4x0r your computer are noobs, anyway.

Why not install & run ubuntu on the computer you're actually using?  Why wait for the laptop off ebay?[/QUOTE]
if it deletes this OS im fooked, i can't risk it.

suse pro 9.1 already deleted one of my main computers. and kicking me offline for 2 mouths

---

### Post by jdong on 2005-06-15
> gee.  if you were as 1337 as you were trying to sound, I figure you might have already known the answer to your question, I mean, since all the people trying to h4x0r your computer are noobs, anyway.


I don't like where this thread is heading now... Please, let's behave maturely. :)

P.S. I included this quote just to reference an example of where tensions in this thread may be escalating. Not a direct attack or put-back to anyone in particular.

---

### Post by Takis on 2005-06-15
[QUOTE=lowlux] im going to find an old computer and put smoothwall on it..... but i don't think any time soon.):[/QUOTE]
Smoothwall rocks and I heartily recommend it to everybody. It's a very quick and easy install, all you need is an old Pentium computer that's pretty much a dime a dozen these days.
You should seriously look into installing this goldmine.

---

### Post by vega44 on 2005-06-15
[QUOTE=jdong]I don't like where this thread is heading now... Please, let's behave maturely. :)

P.S. I included this quote just to reference an example of where tensions in this thread may be escalating. Not a direct attack or put-back to anyone in particular.[/QUOTE]
hackers don't use elite nor l33t, noobs or script kiddies use the word l33t. and a hacker would never say he/she is a hacker or a cracker.

---

### Post by vega44 on 2005-06-15
[QUOTE=Takis]Smoothwall rocks and I heartily recommend it to everybody. It's a very quick and easy install, all you need is an old Pentium computer that's pretty much a dime a dozen these days.
You should seriously look into installing this goldmine.[/QUOTE]
will it slow my internet?

---

### Post by Takis on 2005-06-15
Not at all. Your Internet would need to be *extremely* fast for any sort of slow down to occur.

Edit: By extremely, I mean ridiculously, ludicrously fast (> LAN speed).

---

### Post by Brunellus on 2005-06-15
[QUOTE=lowlux]if it deletes this OS im fooked, i can't risk it.

suse pro 9.1 already deleted one of my main computers. and kicking me offline for 2 mouths[/QUOTE]
 explain again how Suse 9.1 pro deleted one of your computers?

Generally speaking, if you pay attention at the install, this sort of thing can be avoided.  The key things to do are 

1) Partition your hard drive, and find a suitable empty partition (partitions) you want Ubuntu (or your distribution of choice) to use.  A swap partition is useful as well.

2) Install ubuntu (or the distribution of your choice) onto the partition you want it installed.  The installer will pretty much leave any partitions you don't tell it to use alone.

It goes without saying that you should back up any critical data that you have on that hard drive before you begin.  

If that's too much of a commitment for you, I recommend using the livecd--Hoary Live x86 is good.  But if you don't want to do that, well, there are always other choices: Knoppix, or Phlack, or my all-time personal favorite livecd distro, Damnsmall Linux.  For a good time, boot Damnsmall with the "dsl -toram" option, if your box has >96 MB RAM--the whole distribution loads itself into RAM, and the machine will run quickly and silently.

---

### Post by vega44 on 2005-06-15
[QUOTE=Brunellus]explain again how Suse 9.1 pro deleted one of your computers?

Generally speaking, if you pay attention at the install, this sort of thing can be avoided.  The key things to do are 

1) Partition your hard drive, and find a suitable empty partition (partitions) you want Ubuntu (or your distribution of choice) to use.  A swap partition is useful as well.

2) Install ubuntu (or the distribution of your choice) onto the partition you want it installed.  The installer will pretty much leave any partitions you don't tell it to use alone.

It goes without saying that you should back up any critical data that you have on that hard drive before you begin.  

If that's too much of a commitment for you, I recommend using the livecd--Hoary Live x86 is good.  But if you don't want to do that, well, there are always other choices: Knoppix, or Phlack, or my all-time personal favorite livecd distro, Damnsmall Linux.  For a good time, boot Damnsmall with the "dsl -toram" option, if your box has >96 MB RAM--the whole distribution loads itself into RAM, and the machine will run quickly and silently.[/QUOTE]


i used knoppix befor. some stupid fool tald me i had to do t this and it deleted my hard drive. ):

---

### Post by WildTangent on 2005-06-16
buy a Dlink, Linksys or Netgear router...you now have a hardware firewall, thats highly configurable, and ALWAYS working. no annoying popups either.

-Wild

---

### Post by Optimal Aurora on 2005-06-16
[QUOTE=lowlux]is there anything like firestarter for windows? (:[/QUOTE]
When it comes to windows I use an external firewall/router and the XP SP2 built-in firewall...

---

