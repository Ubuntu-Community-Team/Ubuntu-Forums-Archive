---
title: "Virtualbox won't forward port 8000"
date: 2015-01-09
forum: Virtualisation
---

### Post by UCanCallMeRay on 2015-01-09
My host OS is Windows 7. I am running Ubuntu 14.04 on Virtualbox 4.3. The VM has a NAT network adapter. The NAT network adapter has 2 port forwarding rules. Firstly, it forwards host 3023 to guest 22 for SSH. This works, I can SSH from the host to the guest.

Secondly, the network adapter should forward host port 8000 to guest port 8000. I have a Django webserver running on guest port 8000 that I'd like to view from the host's web browser. I can access this webserver from the guest. I cannot access it from the host.

I have checked Windows' firewall settings. I am not a firewall expert, but I see exceptions made for Virtualbox. I am unfamiliar with Ubuntu firewall software, but I know that ufw is disabled.

How can I get host port 8000 forwarded to guest port 8000? Any help is greatly appreciated.

---

### Post by Doug S on 2015-01-09
First, I would try to determine where the problem is. I would run tcpdump on the quest Ubuntu 14.04 VM (or wireshark, if you prefer) to determine if the packets are showing up at your guest and if it is answering. You could do that via your working SSH session. I don't know your network interface name, so I'll use eth1 in my example:```
sudo tcpdump -n -tttt -i eth1 port 8000
```

---

### Post by UCanCallMeRay on 2015-01-09
Thanks for the quick response. That tcpdump definitely reveals some activity once I try localhost:8000 from the host. Here's the output.

```
$ sudo tcpdump -n -tttt -i eth0 port 8000[sudo] password for andrew:
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
2015-01-09 21:59:31.716537 IP 10.0.2.2.51464 > 10.0.2.15.8000: Flags [S], seq 523968001, win 65535, options [mss 1460], length 0
2015-01-09 21:59:31.716586 IP 10.0.2.15.8000 > 10.0.2.2.51464: Flags [R.], seq 0, ack 523968002, win 0, length 0
2015-01-09 21:59:31.716641 IP 10.0.2.2.51465 > 10.0.2.15.8000: Flags [S], seq 524032001, win 65535, options [mss 1460], length 0
2015-01-09 21:59:31.716650 IP 10.0.2.15.8000 > 10.0.2.2.51465: Flags [R.], seq 0, ack 524032002, win 0, length 0
2015-01-09 21:59:32.031207 IP 10.0.2.2.51468 > 10.0.2.15.8000: Flags [S], seq 524160001, win 65535, options [mss 1460], length 0
2015-01-09 21:59:32.031256 IP 10.0.2.15.8000 > 10.0.2.2.51468: Flags [R.], seq 0, ack 524160002, win 0, length 0
2015-01-09 21:59:32.282950 IP 10.0.2.2.51470 > 10.0.2.15.8000: Flags [S], seq 524224001, win 65535, options [mss 1460], length 0
2015-01-09 21:59:32.283007 IP 10.0.2.15.8000 > 10.0.2.2.51470: Flags [R.], seq 0, ack 524224002, win 0, length 0
2015-01-09 21:59:32.450429 IP 10.0.2.2.51471 > 10.0.2.15.8000: Flags [S], seq 524288001, win 65535, options [mss 1460], length 0
2015-01-09 21:59:32.450468 IP 10.0.2.15.8000 > 10.0.2.2.51471: Flags [R.], seq 0, ack 524288002, win 0, length 0
2015-01-09 21:59:37.589588 IP 10.0.2.2.51474 > 10.0.2.15.8000: Flags [S], seq 524928001, win 65535, options [mss 1460], length 0
2015-01-09 21:59:37.589641 IP 10.0.2.15.8000 > 10.0.2.2.51474: Flags [R.], seq 0, ack 524928002, win 0, length 0
2015-01-09 21:59:37.840949 IP 10.0.2.2.51475 > 10.0.2.15.8000: Flags [S], seq 525056001, win 65535, options [mss 1460], length 0
2015-01-09 21:59:37.840988 IP 10.0.2.15.8000 > 10.0.2.2.51475: Flags [R.], seq 0, ack 525056002, win 0, length 0



```

---

### Post by Doug S on 2015-01-09
So, the host is getting a reset packet for every attempt to open a tcp connection. So your guest is actively refusing the connection.
(I am assuming your host is 10.2.2.2 and your guest is 10.2.2.15)

Now, I wonder if your django thing is actually allowing or listening to traffic from eth0 sub-net on port 8000.

(I'll edit this post in a minute with a command to try).

Edit: Post the output from this command:```
sudo netstat -ltnp
```

---

### Post by UCanCallMeRay on 2015-01-09
This is while the webserver is running.

```
$ sudo netstat -ltnpActive Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:6011          0.0.0.0:*               LISTEN      2126/2
tcp        0      0 127.0.0.1:8000          0.0.0.0:*               LISTEN      2675/python
tcp        0      0 127.0.0.1:41004         0.0.0.0:*               LISTEN      2276/python2
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      911/dnsmasq
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      351/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      414/cupsd
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN      1497/0
tcp6       0      0 ::1:6011                :::*                    LISTEN      2126/2
tcp6       0      0 :::22                   :::*                    LISTEN      351/sshd
tcp6       0      0 ::1:6010                :::*                    LISTEN      1497/0
```

---

### Post by Doug S on 2015-01-09
Ray,

Your port 22 stuff is working because sshd is listening to any IP address.
Your port 8000 stuff is not working because it is only listening to the localhost.
You need to examine your configuration stuff for django.

---

### Post by UCanCallMeRay on 2015-01-10
Thanks Doug. I will seek help from the Django community. If I find a solution, I'll post it here.

---

### Post by UCanCallMeRay on 2015-01-10
Indeed, by default the Django webserver only listens on 127.0.0.1. You can configure it to listen on all IP addresses by specifying the IP address 0.0.0.0. That is, you should launch the webserver with this command

```
python manage.py runserver 0.0.0.0:8000
```

To be clear, this is the solution to my problem.

---

