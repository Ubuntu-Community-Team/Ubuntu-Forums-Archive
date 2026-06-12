---
title: "Blocked all external connections - but doesn't seem to be UFW or Iptables"
date: 2020-10-22
forum: Security
---

### Post by tuxman_ottawa on 2020-10-22
Hi all,

I have an issue that's got me puzzled, and somewhat worried that I may have been partly hacked.

One of my ubuntu 18.04.4 LTS boxes stopped responding to external requests.  I can ping it but that's all.   If I console into it everything seems fine.  If I nmap itself from itself it shows all the expected listening ports (SSH, apache etc), but from another box on my LAN it will only ping, port scans show all filtered.

repeated reboots, no change
UFW says disabled.
iptables -L -n -v shows all ACCEPT by default and no other rules.

Anyone have any suggestions ? 

Tks!

---

### Post by scorp123 on 2020-10-23
> **tuxman_ottawa said:**
>  If I console into it everything seems fine.  If I nmap itself from itself it shows all the expected listening ports (SSH, apache etc), but from another box on my LAN it will only ping, port scans show all filtered.

Are you sure the required services are still running? What does e.g. this command say:
```
sudo lsof -n -i -P
```

---

### Post by tuxman_ottawa on 2020-10-23
!I found it.  And it's mostly my fault. 

I had changed the ip on the server a while ago, I can't explain why it continued to work then, but the issue was due to the PBR configuration.. Couple of things, 1) the ip wasn't updated in the PBR config, and 2) the entries I had in the netplan file for the PBR were causing issues.  Removed all the PBR and LAN traffic is working again as expected.  

Have to troubleshoot the PBR but all good for now

---

### Post by TheFu on 2020-10-23
> **tuxman_ottawa said:**
>  Have to troubleshoot the PBR but all good for now

OT: Uh .... PBR ... means something different, I suppose, there?  Here it is a nice way to say, "I've had too much cheap beer."  ;)

---

### Post by tuxman_ottawa on 2020-10-23
ROFL.. Policy Based Routing :)

---

### Post by TheFu on 2020-10-23
> **tuxman_ottawa said:**
> ROFL.. Policy Based Routing :)

So ... pretty much the same meaning. ;)

If this is solved, please use the "Thread Tools" button near the top of the page and mark it "SOLVED" so others can easily see that in their searches. It really helps out the community here.

---

