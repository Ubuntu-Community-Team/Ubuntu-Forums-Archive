---
title: "Allowing Access on Port 3306"
date: 2007-08-22
forum: Server Platforms
---

### Post by igb on 2007-08-22
I have just set up a Feisty server and want to allow external access to MySQL. I have commented out the bind-address line in my.cnf. When I try to telnet to myhost 3306, I get access denied.

A workstation with a similar setup allows remote access with no problems. hence I assume that the server is specifically blocking access to port 3306. How do I go about telling the server to open up port 3306.

I have already tried adding mysqld: All to hosts.allow. I have no specific firewall rules, other than whatever Feisty server provides by default.

Ian.

---

### Post by Hugolp on 2007-08-22
As I have been told Ubuntu ports are open by default, but if you want to control it you can install firestarter for ease of use (through its been quite buggy in feisty) or shorewall or winadmin if you want more control.

Hugo

---

### Post by kosmic on 2007-08-22
in a terminal just type :

sudo iptables -L to see if you have any rule blocking that port

---

### Post by igb on 2007-08-23
I am not a firewall expert, but it doesn't look as though it's a firewall problem:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh,sftp

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     0    --  anywhere             anywhere

```

That looks to me as if it allows everything in and out. I don't think fail2ban is to blame, as I have another server which doesn't have it installed and it has exactly the same problem.

The error I am getting is:

```
ian@scamper:/var/home/ian$ mysql -h 192.168.0.30 -u root -pxxxxx
ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.0.30' (111)
```

Interestingly if I ssh into the firewall and try:

```
mysql -h localhost -uroot -pxxxx
```

that works, but the following doesn't:

```
mysql -h firewall.banter.local -uroot -pxxxxx
```

Ian.

---

### Post by igb on 2007-08-23
Finally fixed it. I must have restarted MySQL about half a dozen times, with no effect. Finally I rebooted and it now all works as expected. Don't know why that should work though.

Ian.

---

