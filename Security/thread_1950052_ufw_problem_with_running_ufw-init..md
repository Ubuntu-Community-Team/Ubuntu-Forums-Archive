---
title: "ufw problem with running ufw-init."
date: 2012-03-31
forum: Security
---

### Post by kleenex on 2012-03-31
Hello, I have a problem with setting default ufw firewall policy on Xubuntu-desktop 12.04 LTS beta2. When I tries to execute the **ufw default deny** command, I get the error

```
ERROR: problem running ufw-init
``` I have no **ufw-init** file in my system. One more thing, can I block/drop **tcp-flags** with ufw firewall? I mean for example 

```
ALL NONE
SYN,FIN SYN,FIN
SYN,RST SYN,RST
FIN,RST FIN,RST
etc...
```

---

### Post by 2F4U on 2012-03-31
Just tried in on my machine

```
sudo ufw default deny incoming
sudo ufw default allow outgoing

```

without problems. Can you give the exact commands you used and the output?

---

### Post by kleenex on 2012-03-31
Hello 2F4U, I solved my ufw problem using iptables. Anyway, thanks for suggestions. Just curiosity - what about tcp flags? How can I block these flags with ufw firewall? It is possible?

---

### Post by haqking on 2012-03-31
> **kleenex said:**
> Hello 2F4U, I solved my ufw problem using iptables. Anyway, thanks for suggestions. Just curiosity - what about tcp flags? How can I block these flags with ufw firewall? It is possible?

the U in UFW stands for uncomplicated, it is intended for simple rules.

As far as i know TCP flags can only be done with IPTbles and UFW does not support it, but i dont use UFW extensively so i may be wrong but dont think so

it may take the 
```

--tcp-flags
``` option but i dont think so.

There is nothing in the man page

---

### Post by Dangertux on 2012-03-31
This is kind of a gotcha question.. Is there a command line parameter for --tcp-flags for ufw? No...

However if you edit the /etc/ufw/before.rules and /etc/ufw/after.rules you will notice that the rules encompassed in those files are iptables syntaxed rules, they will be added to the chain with the rest of the UFW rules when it is started. They take regular iptables rules and all of the flags , targets and chains associated with that.

Hope this helps.

---

### Post by kleenex on 2012-04-01
**Dangertux** Yes, it helped, but for now I will stick with iptables. Thanks for suggestions and answers. Best regards!

---

### Post by haqking on 2012-04-01
> **Dangertux said:**
> This is kind of a gotcha question.. Is there a command line parameter for --tcp-flags for ufw? No...

However if you edit the /etc/ufw/before.rules and /etc/ufw/after.rules you will notice that the rules encompassed in those files are iptables syntaxed rules, they will be added to the chain with the rest of the UFW rules when it is started. They take regular iptables rules and all of the flags , targets and chains associated with that.

Hope this helps.


ahh gotcha, yeah makes sense you can put it in the config files, never done that much with UFW.

Cheers

---

