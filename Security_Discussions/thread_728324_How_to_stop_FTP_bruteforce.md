---
title: "How to stop FTP bruteforce?"
date: 2008-03-18
forum: Security Discussions
---

### Post by Dr Small on 2008-03-18
I got this joker bruteforcing FTP right now on my server (watching everything in Wireshark) and he's simply doing a dictionary attack on Administrator right now.

I added:
```
ALL: **IP**
```

To /etc/hosts.deny, but it hasn't stopped him yet. What other method (besides closing the port) can I use to block him?

Dr Small

---

### Post by HermanAB on 2008-03-18
Google for "iptables rate limit" and set the filter for 10 times per minute.

Cheers,

Herman

---

### Post by FakeOutdoorsman on 2008-03-19
I've used something similar to these iptables rules to block an ip for 60 seconds if there are more than 3 connections within 60 seconds to throttle-down attacks like yours.  You can change the port from 22 in the example to 21 or whatever you are using for your FTP port.

```
iptables -N SSH_CHECK
iptables -A INPUT -p tcp --dport 22 -m state NEW -j SSH_CHECK
iptables -A SSH_CHECK -m recent --set --name SSH
iptables -A SSH_CHECK -m recent --update --seconds 60 --hitcount 4 --name SSH -j DROP
```

Before you start editing iptables make sure to make an iptables backup as described [here]("http://ubuntuforums.org/showpost.php?p=4518723&postcount=2").

Here's a good iptables tutorial.  Make sure to have physical access to your machine if you are about to edit iptables as you can accidentally lock yourself out:
[IPTables HOWTO CentOS Wiki]("http://wiki.centos.org/HowTos/Network/IPTables")

You could also change your FTP port to a non-standard number.  It would greatly reduce the number of brute force/dictionary attacks, but not eliminate them.  Is there a reason your using FTP instead of SSH (aka SFTP)?

---

### Post by Dr Small on 2008-03-19
Thanks for the information, both of you. I have yet to try any of it out yet, but I plan to after I do some reading up on it.

Yes, I do have physical access to my server. It's setting right beside my desk, and if I have to hook the monitor up to it, it wouldn't be the first time :p

There is no pratical reason why I am using FTP. Maybe because I wasn't sure if FireFTP could connect via SFTP (?) but the box is mainly for tesing and backups anyhow. Changing ports is practical, and essential, but since it's a testing box I guess I am sort of lazy at changing ports :p

Dr Small

---

### Post by p_quarles on 2008-03-19
FireFTP doesn't support sftp, but many clients do, including Filezilla. In any case, changing ports is easy, and if that's a practical solution as you say, go for it. Using a non-standard port is one of the most foolproof ways of getting rid of brute force attempts altogether.

---

### Post by hyper_ch on 2008-03-20
if you're the only one on the system and you just want to have remote access to your files, remove ftp and install openssh-server... use then winscp on windows and konqueror or some other program on linux for sftp/scp access.

Then also install fail2ban or hostsdeny and set the limit of lets say 3 unsuccessful login tries within 10 min in order to get that ip blacklisted.

---

