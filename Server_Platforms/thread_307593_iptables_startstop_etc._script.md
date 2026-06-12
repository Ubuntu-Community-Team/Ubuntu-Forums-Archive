---
title: "iptables start/stop etc. script"
date: 2006-11-26
forum: Server Platforms
---

### Post by satimis on 2006-11-26
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64

$ ls /etc/init.d | grep iptables
Nothing printed out

$ sudo iptables -L```

Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1400:1536 TCPMSS clamp to PMTU

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


Where can I get iptables' start/stop/restart/status scripts?

Or they run on another file/path?

TIA


B.R.
satimis

---

### Post by fatbastard spice on 2006-11-27
What sort of things are you after apart from just setting some default policies? I just googled for the various points i was after and wrote my own. I can post up most of that if it's of some use.

---

### Post by satimis on 2006-11-27
> **fatbastard spice said:**
> What sort of things are you after apart from just setting some default policies? I just googled for the various points i was after and wrote my own. I can post up most of that if it's of some use.
Hi fatbastard spice,

Tks for your response.

I found the script, named firewall script not iptables.

Tks.

B.R.
satimis

---

