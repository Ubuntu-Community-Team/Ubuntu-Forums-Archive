---
title: "Home server"
date: 2016-01-09
forum: Server Platforms
---

### Post by jakr2 on 2016-01-09
I have a spare PC and I installed ubuntu and im using at as file system/hosting stupid websites, so I can access it from anywhere in the world but I cant assess it via SSH or FTP or view the sites. Any idea what to do?

---

### Post by lisati on 2016-01-09
*Thread moved to **Server Platforms**.*

There's a little bit more to setting up a server that you can access from the outside world than installing server software on one of the machines on your home network. For example:
[LIST]
[*]Do you have a domain name that points at your home network or are you just using your public IP address?
[*]Do you have the relevant port forwarding enabled on your router that redirects incoming requests to the correct machine?
[/LIST]

---

### Post by jakr2 on 2016-01-09
I have a domain yes and I portforwarded 22 80 25

---

### Post by Doug S on 2016-01-09
> **jakr2 said:**
> I have a domain yes and I portforwarded 22 80 25Perhaps some monitoring at the packet level using tcpdump, or wireshark if you prefer, will help to gain some insight. For example for SSH try (assuming your NIC name is eth0, change to whatever yours is):```
sudo tcpdump -tttt -n -i eth0 port 22
```Then try to access it from somewhere else in internet and see if the packets get there and if it responds.
I do not know how busy your server is, but it might be good enough to just do this:```
sudo tcpdump -tttt -n -i eth0
```

---

### Post by jakr2 on 2016-01-10
Im not using ethernet but yes, when I do ```
sudo tcpdump -tttt -n -i wlan0 port 22
``` My screen starts filling up so I cant tell where there coming from as its to fast.

---

### Post by nerdtron on 2016-01-10
Some connectivity test,
From another PC on the same LAN in your network, test port 22 and port 80:
```
telnet local.IP.address.ubuntu 22 
```
```
telnet local.IP.address.ubuntu 80 
```

If you see the below output and you are dropped to a prompt, then the ports are open:
```
Escape character is '^]'.
SSH-2.0-OpenSSH_6.6.1 
```

Now test using another PC from the internet (not your local PC).
```
ping  your.Public.IP.address 
```
```
telnet your.Public.IP.address 22 
```
```
telnet your.Public.IP.address 80 
```

If the test from the public internet is not successful, but test from the LAN is successful, then you might need to look at your router settings again. Be sure you've open the correct ports on it's firewall, no ACL blocking the ports and you configured port forwarding correctly.

---

### Post by jakr2 on 2016-01-10
From another PC on the same LAN in your network, test port 22 and port 80:
```
telnet local.IP.address.ubuntu 22 
```
```
telnet local.IP.address.ubuntu 80 
```

I get 
```
telnet ******Connecting To *****...Could not open connection to the host, on port 22: Connect failed
```

```
telnet ******Connecting To *****...Could not open connection to the host, on port 80: Connect failed
```
But the ports are open on my routher and the machine.

---

### Post by nerdtron on 2016-01-10
We'll you need to first verify if your server is listening to the ssh and http ports from the Local network:
Try to ping if is reachable from a different PC, (replace to the correct IP address of the ubuntu Server)
```
ping IP.address.ubuntu 
```

Then on the ubuntu server, run the following netstat command. You should see similar output as below:
```
[root@web-one ~]# sudo netstat -tulpn | egrep "ssh|http"
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      28544/sshd
tcp6       0      0 :::80                   :::*                    LISTEN      13219/httpd
tcp6       0      0 :::22                   :::*                    LISTEN      28544/sshd 
```

If you did not see any output, be sure that the services are running:
```
sudo service ssh start
sudo service apache2 start
```

---

### Post by jakr2 on 2016-01-10
Never mind when I do telnet I get what you said for a pc on the same network for port 22
```
SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3
```
For telnet 80 I dont get a return just blank

For netstat I get
```
netstatActive Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 192.168.0.3:http        192.168.0.4:57548       SYN_RECV
tcp        0      0 192.168.0.3:ssh         192.168.0.4:57415       ESTABLISHED
tcp        0      0 192.168.0.3:ssh         192.168.0.4:57431       TIME_WAIT
tcp6       0      0 ip6-localhost:60621     ip6-localhost:ipp       ESTABLISHED
tcp6       0      0 192.168.0.3:http        192.168.0.4:57494       ESTABLISHED
tcp6       0      0 ip6-localhost:ipp       ip6-localhost:60621     ESTABLISHED
udp        0      0 192.168.0.3:48337       hardy.teamspeak.4p:2010 ESTABLISHED


```

---

### Post by Doug S on 2016-01-10
> **jakr2 said:**
> Im not using ethernet but yes, when I do ```
sudo tcpdump -tttt -n -i wlan0 port 22
``` My screen starts filling up so I cant tell where there coming from as its to fast.From what I have read on this question, I do not understand why you would be getting constant spew here. Curious.

Anyway, I like nerdtron's advice. However, on my computer I have to use this command instead:
```
doug@doug-64:~$ sudo netstat -tulpn | egrep "ssh|[COLOR="#FF0000"]apache[/COLOR]"
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1776/apache2
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1270/sshd
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1776/apache2

```

EDIT: Oh, I see you have an active SSH session, so the spew is now understood.

---

### Post by jakr2 on 2016-01-10
Okay but I still cant connect from outside the network?

---

### Post by Doug S on 2016-01-10
> **jakr2 said:**
> Okay but I still cant connect from outside the network?Well, could you post what nerdtron asked for? i.e. post the output from netstat, but with the switches and filter specified. And could you tell us what you get for nerdtron's external telnet tests. We would be just guessing without this information, but if I were to guess I would suspect the port forwarding wasn't done correctly.

Now, to prevent excessive spew with the tcpdump stuff, try to just specify the external IP address you will be coming from. Say the IP address of your external testing computer is 123.123.123.123 then try:
```
sudo tcpdump -tttt -n -i wlan0 host 123.123.123.123
```

---

### Post by jakr2 on 2016-01-10
```
2016-01-10 17:06:05.492137 IP 192.168.0.3.42891 > 192.168.0.4.24800: Flags [P.], seq 865:873, ack 1292, win 33100, options [nop,nop,TS val 915669 ecr 31006701], length 82016-01-10 17:06:05.560344 IP 192.168.0.4.24800 > 192.168.0.3.42891: Flags [.], ack 873, win 64064, options [nop,nop,TS val 31006768 ecr 915669], length 0
2016-01-10 17:06:05.857889 IP 192.168.0.4.24800 > 192.168.0.3.42891: Flags [P.], seq 1292:1306, ack 873, win 64064, options [nop,nop,TS val 31007067 ecr 915669], length 14
2016-01-10 17:06:05.858216 IP 192.168.0.3.42891 > 192.168.0.4.24800: Flags [P.], seq 873:881, ack 1306, win 33100, options [nop,nop,TS val 915760 ecr 31007067], length 8
^C
269 packets captured
272 packets received by filter
0 packets dropped by kernel



```

---

### Post by Doug S on 2016-01-10
> **jakr2 said:**
> ```
# sudo tcpdump -tttt -n -i wlan0 host 123.123.123.123tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 65535 bytes

```
Nothing.The IP address I gave in my example was supposed to be replaced by the actual external WAN IP address you will be testing from.

First, run the tcpdump command on the server.
Then, from the external computer try to access via SSH and/or try to open a web page (or use nerdtron's telnet suggestion).
Then, observe any traffic listed by the tcpdump command.
If there is no traffic at all, then portforwarding has not been setup correctly.
If there is traffic, examine it for both incoming and outgoing packets. i.e. does the server reply.

---

### Post by jakr2 on 2016-01-10
Read above

```
2016-01-10 17:06:05.492137 IP 192.168.0.3.42891 > 192.168.0.4.24800: Flags [P.], seq 865:873, ack 1292, win 33100, options [nop,nop,TS val 915669 ecr 31006701], length 82016-01-10 17:06:05.560344 IP 192.168.0.4.24800 > 192.168.0.3.42891: Flags [.], ack 873, win 64064, options [nop,nop,TS val 31006768 ecr 915669], length 0
2016-01-10 17:06:05.857889 IP 192.168.0.4.24800 > 192.168.0.3.42891: Flags [P.], seq 1292:1306, ack 873, win 64064, options [nop,nop,TS val 31007067 ecr 915669], length 14
2016-01-10 17:06:05.858216 IP 192.168.0.3.42891 > 192.168.0.4.24800: Flags [P.], seq 873:881, ack 1306, win 33100, options [nop,nop,TS val 915760 ecr 31007067], length 8
^C
269 packets captured
272 packets received by filter
0 packets dropped by kernel



```

---

### Post by Doug S on 2016-01-10
I had not seen that post when I replied. Regardless, those are internal, LAN IP addresses. We want to filter via whatever external WAN IP address you are testing from, so as to reduce/eliminate unrelated spew.

Anyway, let's put tcpdump aside for the moment. Please post what Nerdtron asked for, and then I asked for. Example, again:

```
doug@doug-64:~$ [COLOR="#FF0000"]sudo netstat -tulpn | egrep "ssh|apache"[/COLOR]
[sudo] password for doug:
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1776/apache2
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1270/sshd
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1776/apache2

```

---

### Post by jakr2 on 2016-01-10
```
# sudo netstat -tulpn | egrep "ssh|apache"tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1170/sshd       
tcp6       0      0 :::22                   :::*                    LISTEN      1170/sshd       
tcp6       0      0 :::443                  :::*                    LISTEN      3527/apache2    
tcp6       0      0 :::80                   :::*                    LISTEN      3527/apache2  

```

---

### Post by Doug S on 2016-01-10
O.K., so your web server is not listening on TCP version 4, so that explains your earlier internal telnet result (or so I think). SSH should be O.K. though. I still suspect incorrect port forwarding for that issue.

---

### Post by jakr2 on 2016-01-10
Router 
[IMG]http://i.imgur.com/YpA0UkX.png[/IMG]

---

### Post by Doug S on 2016-01-10
O.K. What are you using for your external tests? It has to be some computer elsewhere on internet. I used to do such things from work, but then work stopped allowing outgoing SSH stuff.

If you PM me your external IP address, I'll PM you my external IP address. Then you can setup the tcpdump command and then I'll try to ssh to your computer. While I won't get in, we'll at least see if the traffic gets there and if the server responds.

---

### Post by jakr2 on 2016-01-10
Okay going to PM you now.

---

### Post by Doug S on 2016-01-10
> **jakr2 said:**
> Okay going to PM you now.For other readers: Our test worked fine. For SSH everything is working great.

---

### Post by jakr2 on 2016-01-10
> **Doug S said:**
> For other readers: Our test worked fine. For SSH everything is working great.
Correct, thank you.

---

