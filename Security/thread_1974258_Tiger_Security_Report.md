---
title: "Tiger Security Report"
date: 2012-05-05
forum: Security
---

### Post by OtagoHarbour on 2012-05-05
I am using Ubuntu 11.10.  I installed Tiger 3.2.3 on my system using the Ubuntu Software Center.  When I ran tiger, I got a long security report with a lot of warnings like these.

```

--WARN-- [pass013w] Username `root' is not using an acceptable password hash 
         (x). 
--WARN-- [pass013w] Username `daemon' is not using an acceptable password hash 
         (x). 
--WARN-- [pass013w] Username `bin' is not using an acceptable password hash 
         (x). 
--WARN-- [pass013w] Username `sys' is not using an acceptable password hash 
         (x). 
--WARN-- [pass013w] Username `sync' is not using an acceptable password hash 
         (x). 
--WARN-- [pass015w] Login ID sync does not have a valid shell (/bin/sync). 
--WARN-- [pass013w] Username `games' is not using an acceptable password hash 
         (x). 
--WARN-- [pass013w] Username `man' is not using an acceptable password hash 
         (x). 
--WARN-- [pass013w] Username `lp' is not using an acceptable password hash 
         (x). 
--WARN-- [pass013w] Username `mail' is not using an acceptable password hash 


```Are these false alarms or real issues?

Thanks very much in advance for any help,
Peter.

---

### Post by unspawn on 2012-05-05
> **OtagoHarbour said:**
> ```
[pass013w] Username X is not using an acceptable password hash (x).
```
See [http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;bug=432918](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;bug=432918) (2007 ;-p) and a proposed fix at [http://savannah.nongnu.org/patch/?7675](http://savannah.nongnu.org/patch/?7675) (2011).


> **OtagoHarbour said:**
> ```
[pass015w] Login ID sync does not have a valid shell (/bin/sync).
```
'sync' isn't a human user account. Setting an inert shell is good. This warning occurs if /bin/sync isn't in /etc/shells.

* Next time use the "-e" (or was it "-E"?) switch (it adds explanations to warnings) or look up the codes in the explanation file.

---

### Post by OtagoHarbour on 2012-05-06
> **unspawn said:**
> See [http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;bug=432918](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;bug=432918) (2007 ;-p) and a proposed fix at [http://savannah.nongnu.org/patch/?7675](http://savannah.nongnu.org/patch/?7675) (2011).
.

Thank you for your reply.  I downloaded the patches, zappasswd.patch and zappasswd-3.2.3.patch but did not see any info. on how to use them.  Am I supposed to modify the code.

Thanks,
Peter.

---

### Post by unspawn on 2012-05-06
Usually you download the source and patches, unpack it and run 'patch' before installing it. See 'man patch' for more.

---

