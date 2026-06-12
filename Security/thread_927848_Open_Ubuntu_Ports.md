---
title: "Open Ubuntu Ports"
date: 2008-09-23
forum: Security
---

### Post by ChrisRob300 on 2008-09-23
I have a new install of ubuntu server version 8

I have installed firebird nad need to open port 3050.

Gow do I do this?

---

### Post by jerome1232 on 2008-09-23
By default iptables (the default firewall) allows all connections so there's nothing you need to do other than start the program up on the computer to open the port.


If you are behind a router then you will need to forward the port using the routers interface to your computer.

This site has some good guides for common router models if that is the problem
[http://portforward.com/](http://portforward.com/)

To determine the ip address you need to forward the port to type the following command, it will be under 'inet addr:'
```
ifconfig
```

---

### Post by cariboo on 2008-09-23
A quick way to scan for open ports is to go to System-->Administration-->Network Tools-->Port Scan and enter localhost in the Network Address. Beware that the version in hardy gives false positives on occasion.

Jim

---

### Post by ChrisRob300 on 2008-09-24
Hi

I have done an nmap from another PC and port 3050 is not open.  It is in the services file and firebird is funning?

Chris

---

### Post by kevdog on 2008-09-24
Can you list

sudo iptables -L

This should tell us if you have a firewall in effect.

---

### Post by ChrisRob300 on 2008-09-25
iptables -L

Chain INPUT (policy ACCEPT)                         target     prot opt source               destination                                                    Chain FORWARD (policy ACCEPT)                       target     prot opt source               destination                                                    Chain OUTPUT (policy ACCEPT)                        target     prot opt source               destination

Chris

---

### Post by jerome1232 on 2008-09-25
While the program is running what is the output of 
```
netstat -ltu
```

Was the other computer on the same local network? Is this computer behind a router?

---

### Post by ChrisRob300 on 2008-09-26
Hi

Both PCs are on the same network:
192.168.33.0 / 255.255.255.192
They are not exposed to the outside world at all.

There is a firewall between them and the outside world.

Chris

Output follows:


root@FMS50:/home/chris# netstat -ltu                                        Active Internet connections (only servers)                                  Proto Recv-Q Send-Q Local Address           Foreign Address         State   tcp        0      0 *:gds_db                *:*                     LISTEN  tcp        0      0 FMS50.CJR:mysql         *:*                     LISTEN  tcp        0      0 *:netbios-ssn           *:*                     LISTEN  tcp        0      0 *:www                   *:*                     LISTEN  tcp        0      0 *:telnet                *:*                     LISTEN  tcp        0      0 localhost:ipp           *:*                     LISTEN  tcp        0      0 *:microsoft-ds          *:*                     LISTEN  tcp6       0      0 [::]:ssh                [::]:*                  LISTEN  udp        0      0 FMS50.CJR:netbios-ns    *:*                             udp        0      0 *:netbios-ns            *:*                             udp        0      0 FMS50.CJR:netbios-dgm   *:*                             udp        0      0 *:netbios-dgm           *:*                             udp        0      0 FMS50.CJR:ntp           *:*                             udp        0      0 localhost:ntp           *:*                             udp        0      0 *:ntp                   *:*                             udp6       0      0 fe80::290:27ff:fe8d:ntp [::]:*                          udp6       0      0 ip6-localhost:ntp       [::]:*                          udp6       0      0 [::]:ntp                [::]:*

---

### Post by ChrisRob300 on 2008-09-26
Hi

I get the following on the windows machine:
ISC ERROR MESSAGE:
Unable to complete network request to host "192.168.33.50".
Failed to locate host machine.
undefined service gds_db/tcp

Chris

---

### Post by mariuz on 2008-10-08
try first to connect from the ubuntu server to the ubuntu server 

it should look like this 

 telnet localhost 3050
Trying 127.0.0.1...
Connected to borkstationx64.
Escape character is '^]'.

---

### Post by mariuz on 2008-10-08
here is what is going on 
there is No firebird entry in services file 

[http://www.firebirdfaq.org/faq227/](http://www.firebirdfaq.org/faq227/)

---

### Post by cariboo on 2008-10-08
I see nobody has aked you to check and see if firebird is actually running, at the prompt type:

```
ps ax | grep firebird
```

This should show you if firebird is running.

Jim

---

### Post by The Cog on 2008-10-10
And
```
sudo netstat -plnt
```
will configm if firebird is listening on that port.

---

