---
title: "Console access: VMware Server 1.0.6 build-91891 on Ubuntu Server"
date: 2008-07-17
forum: Virtualisation
---

### Post by Urbanmoth on 2008-07-17
Hi All,

I have been trying to fix this for some time but have had no luck.

I have VMware server 1.0.6 installed on my Ubuntu Server (8.04) and I am attempting to access it from my Desktop machine (8.04) via the VMware Server console. This does not work - I cannot login, when I enter my details the console just hangs and I have to 'force quit' to exit.

I know the default port is listening on the server:
```
james@ubuntu:~$ netstat -an | grep 902
tcp        0      0 0.0.0.0:902             0.0.0.0:*
```
and I know VMware is running since I can connect to the web interface (from my desktop) and start a VM machine (although the 'Options' tab is not accessible but this is a problem for another day).

I have confirmed that iptables on the server is allowing all traffic:
```

james@ubuntu:~$ sudo iptables -L
[sudo] password for james: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```

Also, when I attempt to telnet to the port I get:

```

james@james-desktop:~$ telnet 192.168.1.3 902
Trying 192.168.1.3...
Connected to 192.168.1.3.
Escape character is '^]'.
Connection closed by foreign host.
james@james-desktop:~$ 

```
when I believe I should get a response from the VMware httpd service. Any help would be much appreciated.

J.

---

### Post by Urbanmoth on 2008-07-19
Does anyone have any ideas on this? Please?

I cannot connect to the VMWare server from any console on any platform - XP, Vista or Ubuntu, all just hang.

The clue, I feel, is the telnet response from 902

The actual server is working - I can run existing VM's via the web management process but I cannot create new VM's and I cannot access the running VM's since I can't get into a console.

Please, someone must have a clue - I have searched long and hard but have found nothing - I have reinstalled so many times it hurts :(

---

