---
title: "Blocked IP in SSH"
date: 2012-01-17
forum: Server Platforms
---

### Post by Intu on 2012-01-17
Just wondering if anyone knows how I can see what IP's are blocked in SSH and how I can unblock them using Ubuntu server edition. 


I normally work on red hat and centos servers and ive noticed ubuntu server is a bit different then what im used to. 


Any suggestions welcome.

---

### Post by jonobr on 2012-01-17
Hi There


Not sure if I understand the question, but for example, if you use something like fail2ban which is the most popular.
(do command which fail2ban to see if its on there)
this will go through the auth.log and see what IP addresses are trying to get access.
It will add to iptables to stop this,

fail2ban could also use hosts.deny , so again, depends what you have

---

### Post by SeijiSensei on 2012-01-17
By default no IP addresses are blocked.  What specific problem are you having?

---

### Post by hackertarget on 2012-01-17
Nothing is blocked by default however, if you are looking at a server you did not build look at:

```
iptables -L

/etc/hosts.deny
```

See if OSSEC is running, as this may have active response enabled. There are also other tools / scripts that could be implementing blocking, however you will find that most will likely be adding IP tables DROP rules or modify hosts.deny.

---

