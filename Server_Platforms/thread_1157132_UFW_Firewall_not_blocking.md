---
title: "UFW Firewall not blocking?"
date: 2009-05-12
forum: Server Platforms
---

### Post by bcdudley on 2009-05-12
I have the following rules setup in UFW


To                                 Action      From
--                                  ------       ----
22/tcp                       ALLOW       10.1.1.89
21                                ALLOW       Anywhere
25                                 DENY         Anywhere
110                              DENY         Anywhere

When I run a port scan, I am showing 25 and 110 are open ports even after adding them as deny rules. I do not have any type of mail program installed such as postfix. The install was done with no options at all and only proftpd has been installed since then.

One other question about the rules, what syntax would I use to remove the first rule? I followed a guide to add it, however it did not show how to remove it.

Thank you,

---

### Post by cdenley on 2009-05-12
If you scan your own computer, then nothing will be filtered. You need to scan your computer from another computer in order to test your firewall rules.

---

### Post by bcdudley on 2009-05-12
I am scanning it from a windows computer using Angry IP scanner. 

I also just went through and completely removed all the rules and set the following.

sudo ufw default deny
sudo ufw allow ftp

I get the same results. All other 65000 ports are blocked.

Thank you,

---

### Post by cdenley on 2009-05-12
> **bcdudley said:**
> I am scanning it from a windows computer using Angry IP scanner. 

I also just went through and completely removed all the rules and set the following.

sudo ufw default deny
sudo ufw allow ftp

I get the same results. All other 65000 ports are blocked.

Thank you,

Are you scanning from a windows computer on the same LAN, or are you scanning a router? Even if you didn't filter it with a firewall, it wouldn't be open unless you were running a process which was listening on that port.
```

sudo netstat -tlnp

```

---

### Post by bcdudley on 2009-05-12
I am scanning it from a computer on the same lan. This is kind of wierd. The Windows computer with Angry IP Scanner shows 21, 25 and 110 open. I ran zenmap from my Ubuntu workstation and it only shows 21. 

Is this perhaps a bug within Angry IP scanner or windows?

Edit: I just confirmed this. I scanned 25 computers on my network and all of them show up as having 25 and 110 open. There must be something wrong with my Angry IP scanner.

---

