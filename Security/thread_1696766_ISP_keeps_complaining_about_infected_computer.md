---
title: "ISP keeps complaining about infected computer"
date: 2011-02-27
forum: Security
---

### Post by iverasp on 2011-02-27
For a while my ISP has been sending me emails regarding an infected computer or computers on my local network. There are 4 computers running linux and 3 running windows on said network (3x ubuntu, gentoo, 2x windows server 2003 and windows 7).

The emails from my ISP says they have been contacted by a third part client regarding an infected machine and contains repeated instances of the following:
```
xxx.xx.xxx.xx , 2011-02-21 13:43:09 , sinkholed , downadup: GET /search?q=0 HTTP/1.0
```

From /var/log/messages on my router it shows a lot of attempts of brute forcing the SSH service. This has never been a problem as root login is disabled through SSH and the usernames and passwords are strong enough. A quick search with google regarding "sinkholed" points in the direction of DoS attacks. From the same log on my router it also repeatedly reads
```
Feb 27 17:13:58 router sshd[24854]: reverse mapping checking getaddrinfo for cncln.online.ln.cn [218.60.53.109] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb 27 17:13:58 router sshd[24854]: User root from 218.60.53.109 not allowed because not listed in AllowUsers
```

Now, I haven't used Windows in oh so many years and am not responsible for those computers on this network. Does it seem like this is a virus on a Windows host or should I research and adjust my iptables settings on the router? The applied anti-virus software (I don't know which one) apparently does not find any infections. On my workstation I'm using spotify and win32 office through wine, both obtained from legal and trusted sources, and would thus not consider my wine environment a threat.

---

### Post by rookcifer on 2011-02-27
I would eliminate Windows as being the culprit before I blamed your Linux boxes.

---

### Post by Kinstonian on 2011-02-27
Downadup is another name for Conficker so going by that one log record, it looks like a Windows problem.

---

### Post by iverasp on 2011-03-01
Thank you very much! Conficker was present at one of the servers (win 2003) and is now removed.

---

### Post by Diametric on 2011-03-01
Damn...didn't know that.  Cool info.

---

