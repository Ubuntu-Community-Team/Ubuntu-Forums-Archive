---
title: "http &amp; ssh externally accessible only after network restart"
date: 2013-10-05
forum: Server Platforms
---

### Post by bild85 on 2013-10-05
The symptom: http & ssh work fine from an internal IP address. External visits show the ports are not visible. 

The odd fact: If I reset the networking config using **service networking stop; sleep 5; service networking start**, everything comes up and I can access the services from both internal and external IPs. A reboot reverts the ports to invisible again.

The setup: My ISP is Mediacom, who've been extremely helpful in pointing me in the right direction. While it's a residential connection, they say that port-forwarding should work and they've gone out of their way to help me get it configured.

The router is a WRT54G running DD-WRT (it wasn't before, but I flashed it while trying to get this problem sorted.)

The server is running 12.04.3 LTS and has a static IP configured for eth0:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp

```
It is running iptables, but flushing the rules doesn't change the above symptoms. Only a network services restart will allow it to talk to outsiders.

History: This was working just fine with our previous cable modem. A newer modem was required to handle future upgrades, and the next time I checked, port-forwarding wasn't working. It's entirely possible that an update came through during this time. I do not check in on this server daily and it is configured to apply updates without human intervention.

The question: what is changing within the network to allow traffic? How can I get these two ports to remain open during a reboot?

---

### Post by CharlesA on 2013-10-05
Reboot and run this:

```
sudo netstat -nlp
```

And post the output.

---

### Post by bild85 on 2013-10-07
Well, apparently my *untested* **@reboot sleep 20; network services restart** cronjob didn't work :-/ LOL! Here's what I grabbed prior to the reboot:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1531/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1199/sshd       
...     
tcp6       0      0 :::22                   :::*                    LISTEN      1199/sshd
...
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
...
unix  2      [ ACC ]     STREAM     LISTENING     10396    1534/apache2        /var/run/apache2/cgisock.1531

```
I'm off-site so will have to wait to see what's listening when I get back to the internal network tomorrow evening.

---

### Post by bild85 on 2013-10-13
And after a reboot (during this time the server is inaccessible from the Internet):
```
$ sudo netstat -nlp | grep -e ssh -e apache
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1617/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1319/sshd       
tcp6       0      0 :::22                   :::*                    LISTEN      1319/sshd       
unix  2      [ ACC ]     STREAM     LISTENING     11458    1620/apache2        /var/run/apache2/cgisock.1617
```
And for easier visual comparison, after [FONT=courier new]/etc/init.d/networking restart[/FONT] when everything works splendidly:

```
$ sudo netstat -nlp | grep -e ssh -e apache
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1617/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      25557/sshd      
tcp6       0      0 :::22                   :::*                    LISTEN      25557/sshd      
unix  2      [ ACC ]     STREAM     LISTENING     2316244  13237/apache2       /var/run/apache2/cgisock.1617
```

It doesn't look like the difference is visible above. Did I grep out relevant data?

---

### Post by CharlesA on 2013-10-13
That doesn't make any sense. Do you have any firewalls in place?

---

### Post by sandyd on 2013-10-13
> **bild85 said:**
> And after a reboot (during this time the server is inaccessible from the Internet):
```
$ sudo netstat -nlp | grep -e ssh -e apache
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1617/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1319/sshd       
tcp6       0      0 :::22                   :::*                    LISTEN      1319/sshd       
unix  2      [ ACC ]     STREAM     LISTENING     11458    1620/apache2        /var/run/apache2/cgisock.1617
```
And for easier visual comparison, after [FONT=courier new]/etc/init.d/networking restart[/FONT] when everything works splendidly:

```
$ sudo netstat -nlp | grep -e ssh -e apache
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1617/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      25557/sshd      
tcp6       0      0 :::22                   :::*                    LISTEN      25557/sshd      
unix  2      [ ACC ]     STREAM     LISTENING     2316244  13237/apache2       /var/run/apache2/cgisock.1617
```

It doesn't look like the difference is visible above. Did I grep out relevant data?
Can you ping the server from DD-wrt before restarting?
If you can't, is the IP of the server in the ARP tables?

---

### Post by bild85 on 2013-10-14
> **CharlesA said:**
> That doesn't make any sense. Do you have any firewalls in place?
Agreed. Yes, iptables plus fail2ban. The config is:
```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere

```

> **sandyd said:**
> Can you ping the server from DD-wrt before restarting?
If you can't, is the IP of the server in the ARP tables?
The local server has a static IP. I can get to it just fine through the local network, which is managed by the DD-WRT router. How does one examine ARP tables?

---

### Post by bild85 on 2013-10-14
the working crontab entry is:
```

@reboot sleep 60; /etc/init.d/networking restart

```This basically solves the problem described in this thread, but it is still a mystery to me as to why this is necessary and what exactly it accomplishes...

---

### Post by CharlesA on 2013-10-14
> **bild85 said:**
> the working crontab entry is:
```

@reboot sleep 60; /etc/init.d/networking restart

```This basically solves the problem described in this thread, but it is still a mystery to me as to why this is necessary and what exactly it accomplishes...

Yeah... that makes no sense at all. It's like the interface is coming up, but not entirely.

Can you run an ifconfig -a after rebooting and before restarting network and see if it's any different?

---

### Post by bild85 on 2013-10-14
Sure! I added a pre-and post dump to local files:
```

@reboot sleep 30; ifconfig -a > ifconfig-a_afterReboot.txt
@reboot sleep 60; /etc/init.d/networking restart
@reboot sleep 120; ifconfig -a > ifconfig-a_afterNetworkRestart.txt

```

The only difference seems to be the bytecount:

```
# diff ifconfig-a_after*
5,6c5,6
<           RX packets:391 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:189 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:107 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
8c8
<           RX bytes:90313 (90.3 KB)  TX bytes:40119 (40.1 KB)
---
>           RX bytes:28336 (28.3 KB)  TX bytes:20012 (20.0 KB)
15,16c15,16
<           RX packets:163 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:85 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
18c18
<           RX bytes:40361 (40.3 KB)  TX bytes:21476 (21.4 KB)
---
>           RX bytes:16469 (16.4 KB)  TX bytes:24015 (24.0 KB)
25,26c25,26
<           RX packets:56 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
28c28
<           RX bytes:4256 (4.2 KB)  TX bytes:4256 (4.2 KB)
---
>           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

---

### Post by CharlesA on 2013-10-14
Strange indeed. Well, if the networking restart is a workaround, I guess it'll do for now. I still wonder what the root cause is.

---

### Post by bild85 on 2013-10-14
Thanks for the ideas. I appreciate your time, good sir!

---

