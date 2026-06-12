---
title: "what it is the mean of (threshold:type threshold,track by_src)in this snort rule"
date: 2009-10-10
forum: Security
---

### Post by TUDORS on 2009-10-10
Alert tcp any any -> any any (msg”SYN flooding attack”;flags:s,12;flow:to_server;  [COLOR="Red"][SIZE="6"]threshold:type threshold,track by_src[/SIZE][/COLOR],count 20,seconds 1

dear all above snort rule to detect TCP-SYN flood attack 
what the mean of threshold:type threshold,track by_src

thanks in advance

---

### Post by unspawn on 2009-10-11
> **TUDORS said:**
> what the mean of threshold:type threshold,track by_src
Did you check your documentation? ([http://cvs.snort.org/viewcvs.cgi/*checkout*/snort/doc/README.thresholding](http://cvs.snort.org/viewcvs.cgi/*checkout*/snort/doc/README.thresholding))

---

### Post by TUDORS on 2009-10-11
thank you very much

---

