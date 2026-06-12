---
title: "How to close a listening port?"
date: 2010-07-07
forum: Security
---

### Post by Jart44 on 2010-07-07
Greetings,
I have removed a program and it's dependencies that were listening on port 5500. I used nmap to scan my system and found port 5500 is still open and listening. After research, including iptables I cannot seem  to find a definitive answer. How do I close this port permanently?
Thanks

---

### Post by bodhi.zazen on 2010-07-07
Did you stop the service ?

---

### Post by cariboo on 2010-07-07
IF the program was still running when you tried to remove it, it more than likely wasn't removed. Use ps ax to find the program and it's pid:

```
ps ax | grep <program_name>
```

Once you find it's pid, kill it:

```
sudo kill <pid>
```

Then use the pruge option to remove it:

```
sudo apt-get purge <program_name>
```

---

### Post by Jart44 on 2010-07-07
Thanks for the fast replies,
I was certain I stopped all related services but after a check of Synaptic Package Manager and doing a

Code: 
ps ax | grep <program_name>
check I found the offending Server.
A quick nmap search,

Code:
-sV -O -v -T4 -PN 
showed all ports closed.
Cheers

---

