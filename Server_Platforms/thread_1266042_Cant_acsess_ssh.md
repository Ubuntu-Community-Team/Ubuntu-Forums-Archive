---
title: "Cant acsess ssh"
date: 2009-09-14
forum: Server Platforms
---

### Post by 5millp0x on 2009-09-14
Hi, i have port 80, 21 and 22 in my firewall, but i can only assess 21 and 80, cant seam to assess 22

svn works grate form within network but not outside :/  and if i do a port scan 22 dose not respond.

netstat -an | grep "LISTEN "  gives me

```

tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:631                 :::*                    LISTEN

```and iptables -L   gives me                                                           

 ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp-data
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:svn

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```this tells my absolutely nothing :D Can some one help me?

---

### Post by volkswagner on 2009-09-14
Long shot, but possibly it is blocked by your ISP.  Check port 22 via canyouseeme.org

---

### Post by 5millp0x on 2009-09-14
> **volkswagner said:**
> Long shot, but possibly it is blocked by your ISP.  Check port 22 via canyouseeme.org

No itis not blocked by ISP :/

I dont need to block annu thing by software, can i unistall or  open all ports in iptables?

---

### Post by windependence on 2009-09-14
Try:

```
sudo /usr/sbin/sshd

```
-Tim

---

### Post by 5millp0x on 2009-09-14
It gave no output, and port 22 is still not responding, do i need to restart?

---

### Post by 5millp0x on 2009-09-14
Nothing happens, still not responding :/

---

### Post by jondkent on 2009-09-14
try:

ssh localhost

If that doesn't work (though this seems dumb), check sshd runing (ps -ef |grep sshd)

If that does work check the version of ssh sshd is supporting (look at the sshd_config file in /etc/ssh at the section Protocol, should say 2).

Have you got a adsl modem in front of you btw?  If so it could be being blocked there.

---

### Post by 5millp0x on 2009-09-14
thanks for all the help, i did a reinstall av openssh and now it workes!

---

### Post by 5millp0x on 2009-09-24
problem, again!! :( I did something, don't know what, but now cant i login using pyttu using the server ip even from within the network! :confused: It only allows local ip or the host name.
What can i have done to cause this?!

netstat -an | grep "LISTEN " and iptables -L looks still the same, am thinking i need to reinstall the whole server :(

on the server it dose nor even respond to "ssh serveIp" it only gives a blank row, and i need to cancel the proses to continue -

please help!

ps, the port is open, and the server is a DMZ

---

### Post by ChumleyEX on 2009-09-24
Could it be that in one of your config files you have misspelled something?

---

### Post by 5millp0x on 2009-09-24
This is a STRONG possibility, but the files dose not seam to be replaced after reinstall, what can i do besides reinstalling Ubuntu, to reset all my settings?

---

### Post by ChumleyEX on 2009-09-25
Maybe post your config file.

---

