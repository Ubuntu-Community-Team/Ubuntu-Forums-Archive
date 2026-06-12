---
title: "Is my machine being used for spam?"
date: 2010-12-26
forum: Security
---

### Post by Zyprexa on 2010-12-26
Hi.

when i run
```
netstat -a
```i sometimes see
```
tcp6       0      1 10.0.0.10%1382977:34240 ew-in-f27.1e100.ne:smtp SYN_SENT
```So i'm wondering if this means my ubuntu server box is being used for spam or something? There are no other (human) users on the computer and i don't use it to send mails. 

i've run
```
sudo apt-get autoremove sendmail
```in paranoia, but still when i run
```
sudo lsof -w -n -i tcp:25
```i get
```
sendmail- 1643 root    3u  IPv4   6920      0t0  TCP 127.0.0.1:smtp (LISTEN)
```and sometimes```
sendmail- 1643 root    3u  IPv4   6920      0t0  TCP 127.0.0.1:smtp (LISTEN)
sendmail- 2629 root    8u  IPv6  54150      0t0  TCP 10.0.0.10:34121->74.125.91.27:smtp (SYN_SENT)

```Just thought i should ask before starting the tedious process of reinstalling and restoring the system.

---

### Post by CharlesA on 2010-12-26
Judging from the lsof and netstat, it looks like you've got a mail server listening on the lo interface - meaning it has no access from the local network.

Is that there all the time?

---

### Post by HermanAB on 2010-12-26
You can easily look at port 25 traffic with tcpdump or wireshark.

---

