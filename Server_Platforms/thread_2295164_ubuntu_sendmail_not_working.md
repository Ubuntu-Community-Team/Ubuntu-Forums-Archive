---
title: "ubuntu sendmail not working"
date: 2015-09-16
forum: Server Platforms
---

### Post by illinois2 on 2015-09-16
good morning everybudy, i try to be as more information i can to explain my problem: since i got this new server in cloud i do constantly have problem with sending mails. here my log of sendmail 


       Deferred: Connection timed out


i have now 4000 mail in mailq to be sent


this is working:


     ```
telnet localhost 25
```


this is not (178.239.178.51 is my ip):


```
telnet 178.239.178.51 25
```


this is not:


```
telnet mx3.hotmail.com 25
```


Hosts file in etc/

```

     127.0.0.1 blueserver.localdomain blueserver localdev localhost
     10.1.1.55    ubuntu
     178.239.178.51 fanta-trade.eu
     178.239.178.51 geowar.eu
     178.239.178.51 grimaldi-web.com
     178.239.178.51 myonpa.com


     # The following lines are desirable for IPv6 capable hosts
     ::1     ip6-localhost ip6-loopback
     fe00::0 ip6-localnet
     ff00::0 ip6-mcastprefix
     ff02::1 ip6-allnodes
     ff02::2 ip6-allrouters
     10.12.0.134    ubuntu-test
     10.12.124.39    update-imm-ubuntu-12.04-lts
     10.12.8.5    blueserver

```

netstat -ntlp:
```

Proto Recv-Q Send-Q Local Address           Foreign Address    State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*        LISTEN      686/mysqld
tcp        0      0 0.0.0.0:9292            0.0.0.0:*        LISTEN      560/python
tcp        0      0 0.0.0.0:80              0.0.0.0:*        LISTEN      1270/apache2
tcp        0      0 0.0.0.0:21              0.0.0.0:*        LISTEN      557/vsftpd 
tcp        0      0 0.0.0.0:22              0.0.0.0:*        LISTEN      401/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*        LISTEN      937/sendmail: MTA:
tcp        0      0 127.0.0.1:8891          0.0.0.0:*        LISTEN      862/opendkim
tcp        0      0 0.0.0.0:5666            0.0.0.0:*        LISTEN      734/nrpe
tcp        0      0 0.0.0.0:9191            0.0.0.0:*        LISTEN      559/python
tcp6       0      0 :::22                   :::*             LISTEN      401/sshd  

```


firewall

```

    ufw status
    Status: active
    25   ALLOW       Anywhere

```

some sendmail.mc config

```

     dnl DAEMON_OPTIONS(`Family=inet6, Name=MTA-v6, Port=smtp, Addr=::1')dnl
     dnl DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl
     dnl DAEMON_OPTIONS(`Family=inet6, Name=MSP-v6, Port=submission, M=Ea, Addr=::1')dnl
     dnl DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, M=Ea, Addr=127.0.0.1')dnl
     dnl DAEMON_OPTIONS(`Name=MTA, Addr=127.0.0.1, Port=smtp')dnl
     dnl DAEMON_OPTIONS(`Name=MSP, Addr=127.0.0.1, Port=submission')dnl


     MAILER_DEFINITIONS
     MAILER(`local')dnl
     MAILER(`smtp')dnl
     define(`confDOMAIN_NAME', `fanta-trade.eu')dnl
     INPUT_MAIL_FILTER(`opendkim', `S=inet:8891@localhost')

```


dns

```

[COLOR=#555555][FONT=Monaco]fanta-trade.eu.   172800   IN   A       178.239.178.51[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]fanta-trade.eu.   172800   IN   MX   10   m-13b.th.seeweb.it.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]fanta-trade.eu.   172800   IN   MX   20   smtp-avas-th.seeweb.it.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]fanta-trade.eu.   172800   IN   MX   15   fanta-trade.eu.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]fanta-trade.eu.   172800   IN   NS       ns1.th.seeweb.it.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]fanta-trade.eu.   172800   IN   NS       ns2.th.seeweb.it.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]fanta-trade.eu.   172800   IN   SOA       ns1.th.seeweb.it. hostmaster.seeweb.it. 2015091300 86400 7200 2592000 172800[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]fanta-trade.eu.   172800   IN   TXT       "v=spf1 a mx ip4:178.239.178.51 ~all"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]fanta-trade.eu.   172800   IN   TXT       "v=DKIM1\; k=rsa\; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDHHu81Ku5FESjz2SDao+vuxp8wMFP/Wnn8ROLKT3J4dlYrqDMUo5p/whM5ayfxI2D1wirY1zwRK9eLgj+pB6w4erUDuJAIiNx4yxeblniMcF1Z9L3CinTP1XxGDCtcej6ZYx9P4wsHLukzIMj39mawnXWwH23UvztUDz5dOr4ziQIDAQAB"
[/FONT][/COLOR]
```

i'm not in any mail blacklist



if u need more info please ask.
please belive me i spent hours checking here and there (please do not link to a generic sendmail configuration tutorial)


thanks to all

---

### Post by MAFoElffen on 2015-09-16
Networking issue?

178.239.178.51 is the local host's NIC's static IP right? I see the port open. I see you can connect to local host through the sendmail port 25 via telnet... but not to the IP address of the same(?) I can see that the port is open through your firewall. Since you can connect through local host, I can assume the the sendmail daemon is running.

What I do not see is that you can connect any other way via your IP. I also see some arbitrary references inside your host file where you reference your IP to domains, without ever telling it your host's hostname....
```

# ip                          fqdn                hostname
xxx.xxx.xxx.xxx      hostname.example.com      hostname

```
Please post your hostname (/etc/hostname) and the result of your fqdn (dnsdomainname -v)... Please post the results of a ping to your IP address. Then post the result of ifconfig -a

Like I said, if I suspect a networking issue, then I go through the layers and make sure everything is in place to make physical and logical connections, at all the pertinent networking layers.

EDIT-- I'm presently on my way out the door to go to work, and will look at it again when I get back. This is what I would look at in the meantime... Just a generic framework to debug any service that has a listener.
-Straighten out the Hostname and fqdn.
-Confirm you can connect/see your IP address. If you can connect you your IP form that same machine, then the machine's NIC is functioning.
- confirm that your can connect to that IP externally from another machine. 
- Use something like shield's up to see the open ports of that machine from an external source.

---

### Post by SeijiSensei on 2015-09-16
```
telnet mx3.hotmail.com 25
```
Are you unable to connect with that command from the server itself?  Then your ISP has likely blocked outbound connections to port 25 on remote servers.  This is a common anti-spam policy on residential networks and probably some small-business ones as well.  Often the ISP will provide a relay server you can use to send mail, unless running a mail server violates your Terms of Service with the ISP.  Give your ISP a call and ask if they block outbound SMTP connections.

---

### Post by illinois2 on 2015-09-17
> **MAFoElffen said:**
> Networking issue?

178.239.178.51 is the local host's NIC's static IP right? I see the port open. I see you can connect to local host through the sendmail port 25 via telnet... but not to the IP address of the same(?) I can see that the port is open through your firewall. Since you can connect through local host, I can assume the the sendmail daemon is running.

What I do not see is that you can connect any other way via your IP. I also see some arbitrary references inside your host file where you reference your IP to domains, without ever telling it your host's hostname....
```

# ip                          fqdn                hostname
xxx.xxx.xxx.xxx      hostname.example.com      hostname

```
Please post your hostname (/etc/hostname) and the result of your fqdn (dnsdomainname -v)... Please post the results of a ping to your IP address. Then post the result of ifconfig -a

Like I said, if I suspect a networking issue, then I go through the layers and make sure everything is in place to make physical and logical connections, at all the pertinent networking layers.

EDIT-- I'm presently on my way out the door to go to work, and will look at it again when I get back. This is what I would look at in the meantime... Just a generic framework to debug any service that has a listener.
-Straighten out the Hostname and fqdn.
-Confirm you can connect/see your IP address. If you can connect you your IP form that same machine, then the machine's NIC is functioning.
- confirm that your can connect to that IP externally from another machine. 
- Use something like shield's up to see the open ports of that machine from an external source.


hi...  thanks for the support... i'm not an IT guy so i'm trying my best (sorry if i'll not follow you in all passages :D)

so 

ifconfig -a


```

eth0      Link encap:Ethernet  HWaddr fa:16:3e:3a:19:e4  
          inet addr:10.12.8.5  Bcast:10.12.8.15  Mask:255.255.255.240
          inet6 addr: fe80::f816:3eff:fe3a:19e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2267312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5113235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1305386306 (1.3 GB)  TX bytes:2118217600 (2.1 GB)
          Interrupt:31 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:188486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18284583 (18.2 MB)  TX bytes:18284583 (18.2 MB)
```


dnsdomainname -v

```
localdomain
```

---

### Post by illinois2 on 2015-09-17
i changed etc/hosts in 

```

127.0.0.1 blueserver.localdomain blueserver localdev localhost
10.1.1.55	ubuntu
178.239.178.51 blueserver.fanta-trade.eu blueserver
178.239.178.51 blueserver.geowar.eu blueserver
178.239.178.51 blueserver.grimaldi-web.com blueserver
178.239.178.51 blueserver.myonpa.com blueserver


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
10.12.0.134	ubuntu-test
10.12.124.39	update-imm-ubuntu-12.04-lts
10.12.8.5	blueserver

```

but noresult

---

### Post by illinois2 on 2015-09-18
hi... i contacted my isp... they say they do not put any limitation... my server is in cloud and i have full access to it.

---

### Post by SeijiSensei on 2015-09-18
Can you connect to other places and services from the server?  What if you run "telnet [www.google.com](www.google.com) 80"?  You should see:
```

$ telnet www.google.com 80
Trying 63.117.68.59...
Connected to www.google.com.
Escape character is '^]'.

```

---

### Post by MAFoElffen on 2015-09-18
Stop... Back up a step.

Who and what is at IP 178.239.178.51? What I assumed by your first post was that 178.239.178.51 was your own machine's IP address, but now suspect that that is a a server on another network, outside of your own, right? Because your local network ID is 10.0.0.0... which you would go through a gateway (thru a router) to outside of that.  Any domain outside of your own local network would not be in your hosts file, but rather get it's name from a nameserver (dns). That is where those domains would get their name/ip mappings. 

So instead of, what I thought you where trying to query your own IP, from the outside (not from localhost), you were trying to connect to an external server?

The hosts file is usually for mapping servers IPs/ServerNames on your own local network, if  you do not have a local dns server on your own local network.

If the machine that owns the public address of 178.239.178.51 is on one of your own networks, then there should be a router or route between that and your own local network. Whether yours or not... Can you post the results of
```

ping -c 4 178.239.178.51
traceroute 178.239.178.51
nslookup -query=mx fanta-trade.eu
nslookup -query=mx geowar.eu
nslookup -query=mx grimaldi-web.com
nslookup -query=mx myonpa.com

```

nslookup should return the ip address of a domain. The query mx option queries all mail servers of that domain...

EDIT-- See attachments... This is what I see with those commands (attached)

I see all those domains mapped to IP address 178.239.178.51. I see ports 10 and 20 open on them with an mx query. I do not see port 25 open on any of them. So is 178.239.178.51 yours?

Since I can see that from the US, from one of my machines, which just happanes to be one of my DC'es/DNS'es... you should not have to map them in your hosts files, because they are already mapped in external DNS servers.

What I see open on those domains is sSmtp mail service, which is both ports 10 and 20. Why are you not trying to use sSmtp to send mail to them? That is what they are using...

---

### Post by illinois2 on 2015-09-18
> **SeijiSensei said:**
> Can you connect to other places and services from the server?  What if you run "telnet [www.google.com]("http://www.google.com") 80"?  You should see:
```

$ telnet www.google.com 80
Trying 63.117.68.59...
Connected to www.google.com.
Escape character is '^]'.

```

yep this is working

---

### Post by illinois2 on 2015-09-19
[COLOR=#000000]178.239.178.51 is my server ip, is a cloud server.[/COLOR]

[COLOR=#000000]ping -c 4 178.239.178.51

[/COLOR]```

[COLOR=#000000]PING 178.239.178.51 (178.239.178.51) 56(84) bytes of data.[/COLOR]
[COLOR=#000000]64 bytes from 178.239.178.51: icmp_req=1 ttl=63 time=2.33 ms[/COLOR]
[COLOR=#000000]64 bytes from 178.239.178.51: icmp_req=2 ttl=63 time=0.374 ms[/COLOR]
[COLOR=#000000]64 bytes from 178.239.178.51: icmp_req=3 ttl=63 time=0.391 ms[/COLOR]
[COLOR=#000000]64 bytes from 178.239.178.51: icmp_req=4 ttl=63 time=0.500 ms[/COLOR]

[COLOR=#000000]--- 178.239.178.51 ping statistics ---[/COLOR]
[COLOR=#000000]4 packets transmitted, 4 received, 0% packet loss, time 2999ms[/COLOR]
[COLOR=#000000]rtt min/avg/max/mdev = 0.374/0.900/2.336/0.830 ms
[/COLOR]
```[COLOR=#000000]
[/COLOR][COLOR=#000000]nslookup -query=mx fanta-trade.eu[/COLOR][COLOR=#000000]
[/COLOR]```

Server:         212.29.131.88
Address:        212.29.131.88#53

Non-authoritative answer:
fanta-trade.eu  mail exchanger = 20 smtp-avas-th.seeweb.it.
fanta-trade.eu  mail exchanger = 10 m-13b.th.seeweb.it.
fanta-trade.eu  mail exchanger = 15 fanta-trade.eu.

Authoritative answers can be found from:
fanta-trade.eu  nameserver = ns1.th.seeweb.it.
fanta-trade.eu  nameserver = ns2.th.seeweb.it.
m-13b.th.seeweb.it      internet address = 217.64.195.241
fanta-trade.eu  internet address = 178.239.178.51
smtp-avas-th.seeweb.it  internet address = 217.194.8.27
smtp-avas-th.seeweb.it  has AAAA address 2001:4b78:1:20::27
ns1.th.seeweb.it        internet address = 217.64.201.170
ns2.th.seeweb.it        internet address = 95.174.18.147 [COLOR=#000000]ns2.th.seeweb.it        has AAAA address 2001:4b78:2100:2::1[/COLOR]
```[COLOR=#000000]
[/COLOR]

---

### Post by illinois2 on 2015-09-19
> **MAFoElffen said:**
> Stop... Back up a step.

Who and what is at IP 178.239.178.51? What I assumed by your first post was that 178.239.178.51 was your own machine's IP address, but now suspect that that is a a server on another network, outside of your own, right? Because your local network ID is 10.0.0.0... which you would go through a gateway (thru a router) to outside of that.  Any domain outside of your own local network would not be in your hosts file, but rather get it's name from a nameserver (dns). That is where those domains would get their name/ip mappings. 

So instead of, what I thought you where trying to query your own IP, from the outside (not from localhost), you were trying to connect to an external server?

The hosts file is usually for mapping servers IPs/ServerNames on your own local network, if  you do not have a local dns server on your own local network.

If the machine that owns the public address of 178.239.178.51 is on one of your own networks, then there should be a router or route between that and your own local network. Whether yours or not... Can you post the results of
```

ping -c 4 178.239.178.51
traceroute 178.239.178.51
nslookup -query=mx fanta-trade.eu
nslookup -query=mx geowar.eu
nslookup -query=mx grimaldi-web.com
nslookup -query=mx myonpa.com

```

nslookup should return the ip address of a domain. The query mx option queries all mail servers of that domain...

EDIT-- See attachments... This is what I see with those commands (attached)

I see all those domains mapped to IP address 178.239.178.51. I see ports 10 and 20 open on them with an mx query. I do not see port 25 open on any of them. So is 178.239.178.51 yours?

Since I can see that from the US, from one of my machines, which just happanes to be one of my DC'es/DNS'es... you should not have to map them in your hosts files, because they are already mapped in external DNS servers.

What I see open on those domains is sSmtp mail service, which is both ports 10 and 20. Why are you not trying to use sSmtp to send mail to them? That is what they are using...

mmm sorry man... for me i hard to follow you... i'm not a IT guy and... 
your point at the end is that i should chage etc/hosts?
thanks a lot for your help your really putting your head on it

---

### Post by SeijiSensei on 2015-09-19
See if you can connect to my mail server:
```
telnet 50.116.11.117 25
```
I do only limited filtering at the doorstep, and nothing that would affect your ability to connect.

If that works, try:
```
telnet gmail-smtp-in.l.google.com 25
```
Does that work, too, but you still cannot connect to mx3.hotmail.com?

The problem lies either at your end or at the receiving server's end.  I'm trying to figure out which it is.  The fact that you can connect successfully to remote server's port 80 rules out some possibilities like a misconfigured firewall that didn't accept reply packets.  So now we're left with the mystery of why you cannot connect to port 25 on remotes.

---

### Post by MAFoElffen on 2015-09-20
Sorry, I am a Cisco network guy, among other things. I'll target the explanation a bit more basic.

Yes, remove all the extras (fanta-trade.eu, geowar.eu, grimaldi-web.com, myonpa.com) from your hosts file. The domains you put in there are not needed. They are externally listed by public (internet) DNS servers already, so need for you to list them again.

Next, none of those domains (fanta-trade.eu, geowar.eu, grimaldi-web.com, myonpa.com) have port 25 open. So you not being able to connect to them... is actually correct. They are using port 10 and 20 for their mail services. In fact, what you posted. If I can't connect to them on port 25, then you are not going to be able to connect to those either. They just don't seem to have port 25 open on them...

I can connect with Telnet to what SeijiSensei posted (gmail-smtp-in.l.google.com port 25 and 50.116.11.117 port 25) and to mx3.hotmail.com port 25)...

So I agree with SeijiSensei in his thought that you are possibly having a problem connecting to port 25 on remotes. Either on your end... or through your ISP.

---

### Post by illinois2 on 2015-09-20
> **SeijiSensei said:**
> See if you can connect to my mail server:
```
telnet 50.116.11.117 25
```
I do only limited filtering at the doorstep, and nothing that would affect your ability to connect.

If that works, try:
```
telnet gmail-smtp-in.l.google.com 25
```
Does that work, too, but you still cannot connect to mx3.hotmail.com?

The problem lies either at your end or at the receiving server's end.  I'm trying to figure out which it is.  The fact that you can connect successfully to remote server's port 80 rules out some possibilities like a misconfigured firewall that didn't accept reply packets.  So now we're left with the mystery of why you cannot connect to port 25 on remotes.



```
[COLOR=#000000][FONT=Ubuntu Mono]telnet 50.116.11.117 25[/FONT][/COLOR]
```

not working

i tried to disable the firewall but nothing

isp is swearing they do not enable or disable anythign on network


](*,)

---

### Post by illinois2 on 2015-09-20
i cancelld 

178.239.178.51 blueserver.fanta-trade.eu blueserver
178.239.178.51 blueserver.geowar.eu blueserver
178.239.178.51 blueserver.grimaldi-web.com blueserver
178.239.178.51 blueserver.myonpa.com blueserver

from hosts file...

it has sent some mail and than it has stopped again...

---

### Post by illinois2 on 2015-10-05
hosts... like this... it workssssss!


```

127.0.0.1 blueserver.localdomain blueserver localdev localhost
10.1.1.55	ubuntu
178.239.178.51 fanta-trade.eu geowar.eu grimaldi-web.com myonpa.com blueserver

```

---

### Post by illinois2 on 2015-10-05
it stopped working again

---

