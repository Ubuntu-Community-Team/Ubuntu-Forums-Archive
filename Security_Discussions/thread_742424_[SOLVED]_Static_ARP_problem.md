---
title: "[SOLVED] Static ARP problem?"
date: 2008-04-01
forum: Security Discussions
---

### Post by jingo811 on 2008-04-01
I'm trying to secure my machine by doing a "Static ARPing by manually configure IP to MAC mappings".  Not sure what that sentence mean exactly but I followed instructions and got these errors.  Do you know what could be wrong?

```
lunis@linux:~$ **arp -s 192.168.0.7 33:89:MD:05:27:08**
SIOCSARP: Operation not permitted
lunis@linux:~$ **sudo -s**
root@linux:~# **arp -s 192.168.0.7 33:89:MD:05:27:08**
[COLOR="Red"]SIOCSARP: Invalid argument[/COLOR]

```

---

### Post by jingo811 on 2008-04-01
Using the flag -i with my working interface seemed to solve my problems.  According to the guide [COLOR="Red"]CM[/COLOR] is a good sign not sure what it stands for though.

```
lunis@linux:~$ **sudo arp -i eth0 -s 192.168.0.7 33:89:MD:05:27:08**
lunis@linux:~$ **arp -a**
? (192.168.0.7) at 33:89:MD:05:27:08 [ether] PERM on eth0
? (192.168.0.1) at GG:AA:TT:EE:WW:YY [ether] on eth0
lunis@linux:~$ **arp**
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.7              ether   33:89:MD:05:27:08   [COLOR="Red"]CM[/COLOR]                    eth0
192.168.0.1              ether   GG:AA:TT:EE:WW:YY   C     
```

---

