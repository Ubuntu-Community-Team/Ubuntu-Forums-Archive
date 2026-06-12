---
title: "How do I find the network card model?"
date: 2006-06-30
forum: The Cafe
---

### Post by Kimm on 2006-06-30
I just installed Dapper on an old laptop that one of my fathers clients (a blind guy) gave me a few days ago (he was buying new). And I have got everything running properly (has an ATI card that gave me some trubble, but changing the driver to 'vesa' sorted that out), besides networking.

My local network uses Static IP-addresses, so Ubuntu couldnt configure networking during the install (I did that manualy in Administration though), but I have never got internet working in a LiveCD session anyway.

Anyway.. internet still doesnt work, even after the install, so I'm woundering if there is any way of telling what brand the network card is... so that I can try to find a driver for it.

If anyone has any experiance with these computers, this is the
brand: NatureTech
model: 900X

its a fairly old laptop, with an 850 MHz CPU and 256 Mb RAM.

---

### Post by John.Michael.Kane on 2006-06-30
This will list devices ```
lspci -tv
```

---

### Post by Kimm on 2006-06-30
Thanks, it seems to be a:

Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatable 10/100 Ethernet

Strange... I had a look in the Device manager, it is listed there, and there was an entry in Avanced:

info.linux.driver          tulip

I think that looks like the networkcard was detected... but is not working.
Perhaps its broken :(

Just found a link though:
[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

But it still doesnt work... looking some more...

---

### Post by mips on 2006-06-30
There are know issues with Tulip chipsets. Do a search in these forums for "tulip' and you will find some solutions. Someone even wrote a HOWTO in the howto section on the Davicom Semiconductor Tulip issue.

---

### Post by Kimm on 2006-06-30
Yes mips, I found that tutorial and followed it (theres a link to it in my previous post :-P ) But it didnt work.

As it apears it was not only a driver error... but also a user error. I forgor to configure my DNS server :oops: 

Just for fun... I'm writing this message from the lappy ^^

---

### Post by John.Michael.Kane on 2006-06-30
Kimm i'm glad you was able to get it going..

---

### Post by Kimm on 2006-06-30
Are you having trubble with it SD-Plissken?

---

### Post by John.Michael.Kane on 2006-06-30
Kimm no sofar i have not had a machine with that networking card in it.

---

### Post by mips on 2006-07-01
[QUOTE=Kimm]
As it apears it was not only a driver error... but also a user error. I forgor to configure my DNS server :oops: 
[/QUOTE]

Yes, that would also explain it ;)

---

