---
title: "GTKwifi is good...very good"
date: 2006-01-24
forum: The Cafe
---

### Post by Sparkalo on 2006-01-24
Let me start off by saying that I've used various distributions of linux for the last couple of years or so, and I find ubuntu to be my personal favorite for a multitude of reasons (detects everything nicely, fairly stable, good update manager, great compatibility, WONDERFUL community).  

This is my first attempt to use a laptop solely with a linux distro and let me say that for the most part, it's worked WONDERFULLY : P.  The only issue was (not surprisingly) with the PCMCIA wifi card.  I have quite a strange card in the regard that it has absolutely NO brandname on it...at all.  Fortunately, through the FCCID number, I was able to find out that it's a DrayTek Vigor 520 using the TI ACX100 chipset.  The card was detected nicely and the appropriate drivers were assigned during installation, but to my dismay, it wouldn't connect to my (WEP encrypted) wireless network.

So, I skipped that part of the installation and upon booting, I messed around with iwconfig and my /etc/network/interfaces file and had it working just fine...manually : P.  I am on the move a lot and use this laptop from home, school, cafes, and a variety of other locations and having to manually configure my card was a pain in the ass.  It was even more of a pain in the ass because iwlist scan only works 10% of the time from the terminal :p .  

So, I quested for a network manager and after trying four or five, I found GTKwifi.

This literally INSTANTLY solved all of my problems ^_^.  It installed smoothly, added to the panel nicely, and works like a charm (even with WEP encryptions!)!  I must say that this is a fine piece of software, and provided that the security concerns regarding the sudouser file are cleared up, it should definetly be implimented in Dapper : P.  

I do suffer from incredibly long Network Configuration Syndrom (ILNCS for short), but I remedy this with ctrl+c.

So, what I'm wondering is what network managers all of you are using for your various wireless cards.  I would have made this a poll, but unfortunately, the add poll buttons seems to have ran away :P

---

