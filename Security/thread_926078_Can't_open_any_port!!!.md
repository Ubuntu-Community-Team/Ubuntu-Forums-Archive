---
title: "Can't open any port!!!"
date: 2008-09-21
forum: Security
---

### Post by k.h.a on 2008-09-21
Hi!

I have a real problem. I run [http://localhost/ganglia/](http://localhost/ganglia/) and receive the following message:
```

Warning: fsockopen() [function.fsockopen]: unable to connect to 127.0.0.1:8652 (Connection refused) in /var/www/ganglia/ganglia.php on line 304
There was an error collecting ganglia data (127.0.0.1:8652): fsockopen error: Connection refused

```

I think port 8652 is closed:
```

$ nmap -p8652 localhost
Starting Nmap 4.53 ( http://insecure.org ) at 2008-09-22 02:07 ICT
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE
8652/tcp closed unknown

$ telnet localhost 8652
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```

then I try to open it:
```

sudo iptables -I INPUT -p tcp --dport 8652 -j ACCEPT
sudo iptables -I INPUT -p udp --dport 8652 -j ACCEPT

```

But it's still closed:
```

$ nmap -p8652 localhost
Starting Nmap 4.53 ( http://insecure.org ) at 2008-09-22 02:07 ICT
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE
8652/tcp closed unknown

$ telnet localhost 8652
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```

I used to open several ports before. But now I can't open any.
Please give me a direction.

Thanks!

p/s: My Ubuntu version is 8.04 for desktop

---

### Post by nowshining on 2008-09-21
did u setup a firewall beforehand?? try using -d instead of --dport, etc..

---

### Post by Drezard on 2008-09-21
Yea, I would be doing a check for other firewalls such as firestarter and ufw. 

Daniel

---

### Post by k.h.a on 2008-09-21
I tried using -d instead of --dport, but nothing happended. My ufw is disable. And I didn't setup any other firewall such as firestarter, ...

Thanks!

---

### Post by kevdog on 2008-09-21
What is the output of 

sudo iptables -L

---

### Post by k.h.a on 2008-09-21
> **kevdog said:**
> What is the output of 

sudo iptables -L

```
~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:51235 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:51235 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:8652 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8652 
ACCEPT     udp  --  anywhere             0.0.33.204          
ACCEPT     tcp  --  anywhere             0.0.33.204          

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Port 51235 (for azureus) is open (this port was opened before, and it's opened when system start-up by start-up script), but port 8652 is closed.

Thanks!

---

### Post by tarun.winlin on 2008-09-22
> **k.h.a said:**
> 
```

sudo iptables -I INPUT -p tcp --dport 8652 -j ACCEPT
sudo iptables -I INPUT -p udp --dport 8652 -j ACCEPT

```

Did you do an 'iptables-restore' after changing that entry in iptables configuration file.

---

### Post by kevdog on 2008-09-22
> **k.h.a said:**
> ```
~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:51235 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:51235 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:8652 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8652 
ACCEPT     udp  --  anywhere             0.0.33.204          
ACCEPT     tcp  --  anywhere             0.0.33.204          

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Port 51235 (for azureus) is open (this port was opened before, and it's opened when system start-up by start-up script), but port 8652 is closed.

Thanks!

I don't understand what you are saying.  Port 8652 is open on the firewall.  Now that doesnt mean any process is listening on that port, however the firewall here is not the problem.

How are you writing your firewall rules (with a program - ufw, firestarter, or by hand through a script file)?

---

### Post by The Cog on 2008-09-22
Thank you kevdog.

Just to reiterate though,
Thre are two different meanings to "opening" a port. 

First, to be able to connect to a port, it has to be opened in the OS, by an application listening for incoming calls on it. In your case, this is not happening - there is no application listening so your connection request is being refused.

Second, if a firewall is blocking packets, configuring it to allow packets for the port in question to pass through is often also referred to opening the port. In your case, your firewall is not blocking anything, so this is not your problem.

Your problem is not that connections are being blocked, it is that there is nobody listening.

---

### Post by wirelessmonkey on 2008-09-22
It looks like either ganglia or apache may not be running properly, this isn't a firewall issue.

---

### Post by k.h.a on 2008-09-24
Thanks all,

Yeah, I understands. After reconfigured ganglia, I killed this problem.

But now I have a new problem. Before, I opened port 51235 for azureus by the following commands:
```
sudo iptables -I INPUT -p tcp --dport 51235 -j ACCEPT
sudo iptables -I INPUT -p udp --dport 51235 -j ACCEPT
```
and azureus worked in NAT ok status. Now it works in Firewalled status with any port opened by the above commands.

Is this a issue of iptables? What should I do to fix it?

---

### Post by kevdog on 2008-09-24
I don't understand your question, can you rephrase it?

---

### Post by k.h.a on 2008-09-24
I'm sorry, my English is very bad :">

Now I can't configure port to use Azureus in "NAT ok" status though I did it before.Is this a iptables issue?

---

### Post by The Cog on 2008-09-24
I still don't understand what your problem is now.

---

### Post by nowshining on 2008-09-24
> **k.h.a said:**
> Thanks all,

Yeah, I understands. After reconfigured ganglia, I killed this problem.

But now I have a new problem. Before, I opened port 51235 for azureus by the following commands:
```
sudo iptables -I INPUT -p tcp --dport 51235 -j ACCEPT
sudo iptables -I INPUT -p udp --dport 51235 -j ACCEPT
```
and azureus worked in NAT ok status. Now it works in Firewalled status with any port opened by the above commands.

Is this a issue of iptables? What should I do to fix it?

did you go into the torrent program and change to a static port - 'cause if you didn't it's probably using random ports..

---

### Post by k.h.a on 2008-09-25
Thank you all,

In short, now I can't open port for my torrent-client program: azureus.

---

### Post by nowshining on 2008-09-25
> **k.h.a said:**
> Thank you all,

In short, now I can't open port for my torrent-client program: azureus.

again did you change the port seeings in the torrent program? do u look in the prefs?? 'cause again many by default use random torrents and one may have to set it up to use one port only...

---

### Post by k.h.a on 2008-09-27
> **nowshining said:**
> again did you change the port seeings in the torrent program? do u look in the prefs?? 'cause again many by default use random torrents and one may have to set it up to use one port only...
My torrent program use a static port informed in preferences. I opened port 51235 using iptables and inform it in preferences. But the torrent program announced "Firewalled"

---

### Post by nowshining on 2008-09-27
when u opened the port - did u restart the torrent program??

---

### Post by k.h.a on 2008-09-30
Of course! :)

---

### Post by k.h.a on 2008-09-30
OK, I solve my problem.

I don't know why my network was reset as dynamic IP (my IP was other than the one the ports in my router settings were looking for), so I turned it to static.

---

### Post by wrightrocket on 2009-01-12
!

---

