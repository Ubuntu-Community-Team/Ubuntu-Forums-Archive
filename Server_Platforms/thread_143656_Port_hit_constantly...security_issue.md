---
title: "Port hit constantly...security issue?"
date: 2006-03-12
forum: Server Platforms
---

### Post by Griff on 2006-03-12
Starting yesterday firestarter has been recording hits on one specific port.  This port (1027) is hit constantly by similar IP addresses.  Hits occur between 2 and 20 minutes apart...neverending.  Is this something I need to be concerned about or is there something I need to do?

edit: A different port (32809) was just hit by Sun-RPC portmap.  What is this?

---

### Post by Zelut on 2006-03-12
Well if you have firestarter running and dont have those ports open you're fine.  My guess is its some stupid script-kiddie &/or virus-bot trying to spread itself.

I wouldn't be worried as long as firestarter is going..

---

### Post by Griff on 2006-03-13
That makes me feel a little better.  However, a roomate uses windows exclusively.  Should they be worried?  I believe they only have the windows firewall and norton antivirus installed.

---

### Post by Zelut on 2006-03-13
I can't as certain for your windows roommate.  For me, anything labeled Microsoft is 'use at your own risk' anymore.

I would, however, suggest your roommate switch to [FreeAVG]("http://free.grisoft.com/doc/1") or [Avast!]("http://avast.com").  Both free anti-virus, malware/firewall applications that dont absolutely control your machine the way Norton products do.  I switched my office machine to Avast recently and have stayed problem free with a noticeable boost in performance.

---

### Post by codejunkie on 2006-03-13
agreed tell them to drop Norton's, you can do a clean install of windows and just install Norton's AV and it seems like the PC takes a 20% drop in performance. if there are any Norton fans around, I'm not talking actual benchmarks I'm just describing how it seems to feel.

---

### Post by Griff on 2006-03-13
Alright.  I'll do that.  Thanks guys. :)

---

### Post by r4ik on 2006-03-13
Personaly this combination worked for me on a Windows box.
Viruscanner,

[http://free.grisoft.com/doc/2/lng/us/tpl/v5](http://free.grisoft.com/doc/2/lng/us/tpl/v5)

Firewall,

[http://www.zonelabs.com/store/content/catalog/products/sku_list_za.jsp?lid=nav_za](http://www.zonelabs.com/store/content/catalog/products/sku_list_za.jsp?lid=nav_za)

But as stated that worked for me.

---

### Post by beast2k on 2006-03-16
I also get hit on those same ports are you guys sure it is not a program or application ?

---

### Post by beast2k on 2006-03-16
Hello?

Anyone?

---

### Post by Griff on 2006-03-16
I did a 'whois (IP address)' and i got everything from a user in europe to a small company in Arkansas.  I would also like to note that I am no longer being hit on any port.  It's been 2 days hit free now.  :-D

---

### Post by MJN on 2006-03-17
Would these 'hits' be over UDP by any chance?
 
If so, they're likely spoofed source addresses and indicitive of so-called 'Messenger Spam' attempts (usually on ports 1026-1029). Google for info but it's as harmless as they come, unless you run MS Messenger with the ports open then you'll get the popups.
 
Tracing, and harrassing, the owner of the apparent address is futile... and particularly annoying for managers (like me!) of large netblocks whose addresses keep getting spoofed. ;)
 
Mathew

---

### Post by Griff on 2006-03-17
Hmmm.  I don't *think* they were, but I'm not being hit anymore so I can't really check.  I sort of figured that the users of those IPs weren't the guilty parties though.  Don't worry.  I won't be calling you.  :-D

---

### Post by beast2k on 2006-03-18
I'm hit free now as well, I guess it had to be an attempted attack but I wonder why he used those ports?

---

### Post by MJN on 2006-03-18
Well, were they over UDP? If so, see above!

Mathew

---

### Post by h3llfyr3 on 2006-03-19
Please give port / protocol combination, it would also be beneficial if you could get packdumps using ethereal.

Prob worm traffic / scanning from hacked hosts, looks like an MS related exploit.

You should be more worried if your firewall is'nt reporting stuff.

---

