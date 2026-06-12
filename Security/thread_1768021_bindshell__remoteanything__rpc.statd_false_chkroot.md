---
title: "bindshell / remoteanything / rpc.statd false chkrootkit positive?"
date: 2011-05-26
forum: Security
---

### Post by aarongc on 2011-05-26
Hi. I administer server A on a network (running ubuntu server 10.04) where server B was recently  compromised by an intrusion that escalated to root access. I'm checking  the server for signs of intrustion. chkrootkit detects a "bindshell"  infection on port 4000. Nmap shows a service called "remoteanything"  running on 4000, which worries me. However, ps aux shows rpc.statd  listening on 4000 and I have seen things about a false positive in  chkrootkit for rpc.statd.

Questions:
- What the hell is "remoteanything"? I have seen several a few other threads where people report it and then generally decide to ignore it. Something named that provocatively needs a better explanation.
- Why don't the nmap service names match the ps service names that are supposedly on the same port?

---

### Post by aarongc on 2011-05-27
So, the answer to this was obvious: nmap reports the service's "well-known" name, i.e. the process that commonly uses that port. I mistook this for identification of an actual service. Still don't know what "remoteanything" is, but now I don't care since port 4000 on my machine was being used by a legitimate NFS process.

---

