---
title: "DNS issues with static ip."
date: 2006-07-23
forum: Server Platforms
---

### Post by capi on 2006-07-23
I have a Linksys BEFSR41 router and I'm trying to set a static internal ip to a machine. The problem is that the machine doesn't seem to be able to reach out to the internet. Other computers can ping the machine and access it. The machine itself can also ping the gateway and other computers on the network, it's just when I try to ping google or aptitude update that it fails. :\ I'm not sure whats wrong. 

/etc/network/interfaces and /etc/resolv.conf are set up, and I've toyed with them. I'm not really sure where else to play around.

Any ideas?

---

### Post by MonkeyNet on 2006-07-23
Can you post a copy of your interfaces file?

```
cat /etc/network/interfaces > int.txt
```

This will dump the output to a file int.txt which you can then post. This will help out to find out where the problem might be.

Cheers,

Andrew

---

### Post by capi on 2006-07-23
eh, actually I figured it out when I was retyping the file to post it. Aparently I used 225 instead of 255. For some reason I've been doing that a lot recently. :\

thanks.

---

