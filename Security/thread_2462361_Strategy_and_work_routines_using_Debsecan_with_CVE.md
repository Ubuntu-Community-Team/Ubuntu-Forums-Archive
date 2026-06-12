---
title: "Strategy and work routines using Debsecan with CVE's"
date: 2021-05-19
forum: Security
---

### Post by af-crm on 2021-05-19
```
https://manpages.debian.org/testing/debsecan/debsecan.1.en.html
```

Every week I log on to one of out servers and run this script:

```
$ debsecan --suite $(lsb_release --codename --short) --source https://raw.githubusercontent.com/BBVA/ust2dsa/data/ --whitelist fossa_whitelist.txt |grep -v fixed|grep -v "low urgency" |sort -n | uniq -u >> 2021-03-23.txt
```

To save a file with the accurate date.

I add CVE's to the whitelist if I find them irrelevant for our infrastructure:

```
$ debsecan --whitelist fossa_whitelist.txt --add-whitelist CVE-2020-28463
```

These things are working... but it's a fairly slow way of working! I'm thinking of improving the procedure, I have some ideas... Do you have any ideas? What shall I do to optimize the process?

---

### Post by TheFu on 2021-05-21
Try 
```
DATE=$(date "+%F")
echo $DATE
```

I'd definitely use parameters to make the script easier to read and modify too.  Anything that is hardcoded is to be replaced by a parameter.

---

