---
title: "The UseDNS option in ssh"
date: 2008-07-05
forum: Security
---

### Post by szim90 on 2008-07-05
Hello.

Recently I began having problems logging in to my ssh server. While on my LAN, I could log in if I used the dns name of the server (which pointed to my router which forwarded port 22 to my ssh server), but I couldn't if I used the 192.168.x.x IP address. 

When it would not work, it would hang at:
debug1: SSH2_MSG_SERVICE_ACCEPT received

I found that if I turned off the UseDNS option in the sshd_config file, the problem went away. Is there any security risk in turning this option off?

Thank you for any help,
Sean

---

### Post by HalPomeranz on 2008-07-06
There's some marginal security benefit to "UseDNS" (it does a simple sort of anti-spoofing check using DNS), but it's not the worst thing in the world to turn it off.

A "better" solution would be to create entries in your local DNS server for the machine(s) on your 192.168.x.x LAN.  That way the SSH server could actually perform its DNS checks without hanging.

---

