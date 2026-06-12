---
title: "iptables-restore failing"
date: 2010-05-04
forum: Security
---

### Post by Blue_Jay on 2010-05-04
Hi,

I'm setting up a server with Jaunty Jackalope version. I'm trying to test setting up a basic iptables rules... No matter which command I put in, it is failing on the first command when I run iptables-restore < file location (the first rule always fails). I'm doing this on the root user and first typing in the iptables rules in a test file. I've tried the first command starting with % sudo, iptables and -A. All have the same result. I've also tried letting the HTTP rule be first with the same result.

Sample:
#All connections already established
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

#Allow HTTP and HTTPS
#$ sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

I know there must be something obvious that I'm missing but can't figure it out... Any suggestions?

---

### Post by cdenley on 2010-05-05
The iptables-restore command does not accept commands as output, only rules as output by iptables-save.
```

sudo iptables-save

```

---

### Post by bodhi.zazen on 2010-05-05
Not sure what or where your problem is, are you trying to write a file ?

Basically what I advise is you first set up your rules with iptables

```
sudo -i
iptables -A INPUT rule_1
iptables -A INPUT rule_2

...

iptables -A INPUT rule_the_last
```You then save with 

```
iptables-save > iptables.save
```The syntax of the saved file is

```
-A INPUT rule_1
-A INPUT rule_2

...

-A INPUT rule_the_last
```With some additional information mixed into the file.

To restore the rules, use
Command line:
```
sudo iptables-apply iptables.save
```Or in scripts use iptables-restore

You can add it to your network scripts (post-up) or /etc/rc.local

---

