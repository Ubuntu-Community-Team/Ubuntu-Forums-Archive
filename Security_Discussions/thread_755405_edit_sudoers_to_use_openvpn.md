---
title: "edit sudoers to use openvpn"
date: 2008-04-14
forum: Security Discussions
---

### Post by Biochem on 2008-04-14
Hi,

I want to be able to login an openvpn server without having to enter a password. I haded the following line in /etc/sudoers

```
user ALL=(ALL) NOPASSWD: /usr/sbin/openvpn
```

Then when I start openvpn I'm not ask for a password but the connection drop with this message

```
Mon Apr 14 19:30:14 2008 OPTIONS IMPORT: timers and/or timeouts modified
Mon Apr 14 19:30:14 2008 OPTIONS IMPORT: --ifconfig/up options modified
Mon Apr 14 19:30:14 2008 OPTIONS IMPORT: route options modified
Mon Apr 14 19:30:14 2008 OPTIONS IMPORT: route-related options modified
Mon Apr 14 19:30:14 2008 Note: Cannot open TUN/TAP dev /dev/net/tun:
Permission denied (errno=13)
Mon Apr 14 19:30:14 2008 Note: Attempting fallback to kernel 2.2 TUN/TAP
interface
Mon Apr 14 19:30:14 2008 Cannot open TUN/TAP dev /dev/tap2: No such file
or directory (errno=2)
Mon Apr 14 19:30:14 2008 Exiting

```

Anyone got an idea on how to work it out?

Thanks for your help

---

### Post by cornelinux on 2008-04-20
Hi Biochem,

what is the mode of /dev/net/tun ?

I could imagine that some sub process drops the root previliges although it would need them. 

Kind regards
Cornelius

---

### Post by Biochem on 2008-04-21
Thanks for replying to my message cornelinux,

I'm not sure what you mean by "the mode of /dev/net/tun"

the file itself has a 770 permission and the cat command returns
cat: /dev/net/tun: File descriptor in bad state

Biochem

---

### Post by Biochem on 2008-05-03
bump

---

### Post by bloodchilde on 2008-05-19
I believe the correct syntax is:

```
user ALL=NOPASSWD: /usr/sbin/openvpn
```

of course, replace "user" with your username.

---

