---
title: "ufw and Thunderbird"
date: 2011-08-13
forum: Security
---

### Post by cscj01 on 2011-08-13
I have been having severe performance issues with Thunderbird 3.1.11 under Natty x64, particularly when sending messages with attachments.  I have had ufw enabled with rules for CUPS printing (port 631 allowed in for tcp and udp) and tcp (allowed in and out for my home LAN).  Incoming is denied and Outgoing is allowed.

Today, I disabled ufw and sent an email with an attachment.  It went very fast.

Is there some rule I need in ufw for TB?

---

### Post by bodhi.zazen on 2011-08-13
Post your ufw rules.

---

### Post by cscj01 on 2011-08-31
Sorry, I have been away.  Here are the rules:```
Status: active

To                         Action      From
--                         ------      ----
192.168.1.0/24/tcp         ALLOW       192.168.1.0/24/tcp
631/tcp                    ALLOW       192.168.1.101
631/udp                    ALLOW       192.168.1.101

192.168.1.0/24/tcp         ALLOW OUT   192.168.1.0/24/tcp

```

---

### Post by bodhi.zazen on 2011-08-31
Those rules appear very restrictive, allowing traffic only to your lan.

You will need to be more permissive then that.

---

### Post by cscj01 on 2011-09-01
So what other rules would you suggest?

---

