---
title: "[HELP] Connecting ubuntu host to XP guest using VBox"
date: 2009-11-26
forum: Virtualisation
---

### Post by alfonzjanfrithz on 2009-11-26
I have ubuntu 9.10 installed on my computer, and windows XP service pack3 on my vbox. I also have debian etch guest installed on my vbox.

When i configure my etch's ip, and connect it to ubuntu, it works fine. But still, i have to plug some RJ45 to my laptop to make it has connection (Without plug some cable, I cannot have any connection on my network manager). Yeah but at least it works. :)

Thing that makes me frustated is in win xp. When i connect the cable to my laptop, I can choose what network i want to use from my ubuntu network manager. But it doesnt appear in my xp, so i cannot set my xp's ip address.

So my question is,,

1. How to connect my ubuntu host to xp guest?
2. is it possible to connect it without plugging some cable to my laptop?


Your help is really useful for me...   Thanks..:P

Linux Newbie, Alfonz

---

### Post by tacantara on 2009-11-26
You have to configure the virtual machine to recognize and use the host internet connection (ethernet or wi-fi).  You can only do that when the virtual machine is not running.  Open VB, select (but don't start) the Win XP machine, and scroll through the settings for the various hardware options until you find the networking section.  Make sure you have a connection set up.

---

### Post by alfonzjanfrithz on 2009-11-27
I did, I tried to using several network settings such NAT and Bridge. Using NAT, I can even connect the xp to host internet.

I also tried to use bridge networking as on my etch. But its not working on my xp.

---

