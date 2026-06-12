---
title: "Should I be concerned about this chkrootkit warning?"
date: 2015-07-26
forum: Security
---

### Post by Rytron on 2015-07-26
Hi.
I ran ```
sudo chkrootkit
```

# Excerpt of output:
```
Searching for Suckit rootkit... Warning: /sbin/init INFECTED
```

Should I be concerned? Do I need to remedy this?

Thanks.

---

### Post by obake2 on 2015-07-26
I am not security expert, so I will merely convey what I have learned by looking around the web. 

First thing first, what version of chkrootkit is it installed? type 
```
sudo chkrootkit - V
```

If the version is less than chkrootkit-**0.50**, then it is more likely to be false positive.

Sources:

[https://bugzilla.redhat.com/show_bug.cgi?id=636231](https://bugzilla.redhat.com/show_bug.cgi?id=636231)

[http://www.chkrootkit.org/README](http://www.chkrootkit.org/README)

[http://www.chkrootkit.org/](http://www.chkrootkit.org/)

---------------

If you want you can try to scan with other rootkit scanners such as: 
rkhunter, rootcheck, unhide

----------------

By the way, just in case, check to see if you are infected with Operation Windigo by typing:

```
ssh -G 2>&1 | grep -e illegal -e unknown > /dev/null && echo "System clean" || echo "System infected"
```

If it returns "System Infected", then reinstal your operating system from a clean media, then CHANGE YOUR PASSWORDS And credentials.

Sources: 
[http://www.welivesecurity.com/2014/03/18/operation-windigo-the-vivisection-of-a-large-linux-server-side-credential-stealing-malware-campaign/](http://www.welivesecurity.com/2014/03/18/operation-windigo-the-vivisection-of-a-large-linux-server-side-credential-stealing-malware-campaign/)

[http://www.eset.com/int/about/press/articles/article/operation-windigo-largest-server-botnet-uncovered/](http://www.eset.com/int/about/press/articles/article/operation-windigo-largest-server-botnet-uncovered/)

[http://www.webopedia.com/TERM/O/operation-windigo.html](http://www.webopedia.com/TERM/O/operation-windigo.html)

[http://thehackernews.com/2014/03/operation-windigo-linux-malware.html](http://thehackernews.com/2014/03/operation-windigo-linux-malware.html)

---

### Post by Rytron on 2015-07-26
> **obake2 said:**
> 

...

First thing first, what version of chkrootkit is it installed? type 
```
sudo chkrootkit - V
```

If the version is less than chkrootkit-**0.50**, then it is more likely to be false positive.

...



Hi obake2.

```
chkrootkit -V
```
```
chkrootkit version 0.49
```

---

### Post by Rytron on 2015-07-26
> **obake2 said:**
> 

...

By the way, just in case, check to see if you are infected with Operation Windigo by typing:

```
ssh -G 2>&1 | grep -e illegal -e unknown > /dev/null && echo "System clean" || echo "System infected"
```

If it returns "System Infected", then reinstal your operating system from a clean media, then CHANGE YOUR PASSWORDS And credentials.


```
ssh -G 2>&1 | grep -e illegal -e unknown > /dev/null && echo "System clean" || echo "System infected"
```
```
System clean
```

---

