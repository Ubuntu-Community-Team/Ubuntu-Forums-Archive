---
title: "0 snort rules read"
date: 2008-05-01
forum: Security
---

### Post by mrtrick on 2008-05-01
No matter what I do with the snort.conf in 2.8.1 I can't get it to read my rule chians. I always get the following when running snort. 

```
+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
0 Snort rules read
    0 detection rules
    0 decoder rules
    0 preprocessor rules
0 Option Chains linked into 0 Chain Headers
0 Dynamic rules
+++++++++++++++++++++++++++++++++++++++++++++++++++

```

I have the rule path defined in the snort.conf file to /etc/snort/rules (which is the path that contains the extracted rule set from snortrules-snapshot-2.8.tar.gz which was downloaded right from the snort.org rules page. 

I've verified permissions on the directory and even launched it using the flag to specify the rule path

```
./snort -c /etc/snort/rules -i eth1
```

I've verified that the port is running correctly in promisc mode. 

I'm stumped. :confused:

---

### Post by mrtrick on 2008-05-01
Nevermind... I'm an idiot

Witht he -c flag the path was supposed to be to the snort.conf not the rules dir. 

:lolflag:

---

