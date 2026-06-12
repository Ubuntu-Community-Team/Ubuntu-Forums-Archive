---
title: "[SOLVED] Weird server disconnect issue"
date: 2008-06-19
forum: Server Platforms
---

### Post by magicplayr2000 on 2008-06-19
Hi, I just set up my server today.  I'm running samba to share files with Windows machines.  For some reason, after I finish sending files to my server over samba or looking at files over samba, I get disconnected from the internet.  I cannot visit any websites from any computers.  I can't even ping google from my server.  I'm not sure what could be causing this, and I'm pretty new at dealing with servers, so if anyone could at least point me in the right direction I would greatly appreciate it.  Thanks

EDIT: Also, when I ran nmap, it seemed to reconnect.  I'm not sure if this is unrelated, I just thought I'd add it.

---

### Post by magicplayr2000 on 2008-06-20
Bump

---

### Post by gtdaqua on 2008-06-20
Can you ping your default gateway??
Type 'arp' in terminal and see if your default gateway's MAC address is correctly reflecting there.

See these:

[Frequent Internet Timeout]("http://ubuntuforums.org/showthread.php?t=530074")

[Dupplicate ARP!]("http://ubuntuforums.org/showthread.php?t=531954")

---

### Post by magicplayr2000 on 2008-06-20
Thanks, I will try that when I get back home.

---

### Post by magicplayr2000 on 2008-06-20
So far so good...

---

### Post by magicplayr2000 on 2008-06-20
Spoke too soon I guess.  I added my router to the arp table (192.168.0.1) since that wasn't showing up in there.  After I finished moving some files over samba, my internet died on me again.  I can't ping my router when it goes down, from either my desktop or server.

---

### Post by magicplayr2000 on 2008-06-21
bump again

---

### Post by gtdaqua on 2008-06-21
Run a continuous ping to your router when working on samba. Disconnect Samba and see if the ping drops.

---

### Post by magicplayr2000 on 2008-06-21
Stupid moment caused all this I think.  When I set up my network interface, I didn't set it to static.  I think for whatever reason it was trying to get a new address.  No clue if that actually makes the slightest bit of senst, but I've been going for about an hour with no disconnects.  I've used samba, ssh, torrentflux, and ebox through all of it.

Thanks gtdaqua for all your help!  I don't think I would have realized that I missed the dhcp thing if it weren't for looking around about arp.

---

### Post by gtdaqua on 2008-06-21
> **magicplayr2000 said:**
> Stupid moment caused all this I think.  When I set up my network interface, I didn't set it to static.  I think for whatever reason it was trying to get a new address.  No clue if that actually makes the slightest bit of senst, but I've been going for about an hour with no disconnects.  I've used samba, ssh, torrentflux, and ebox through all of it.

Thanks gtdaqua for all your help!  I don't think I would have realized that I missed the dhcp thing if it weren't for looking around about arp.

I wanted to ask the basic question of DHCP or static IP , but because you seemed to be well versed with Samba and all, I was suggesting other alternatives!!!

Cheers :)

---

