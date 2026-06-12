---
title: "Cannot update Server U10.4Lts"
date: 2011-11-25
forum: Server Platforms
---

### Post by Alpha99 on 2011-11-25
Hi Guys 
Can Anyone help here.

Running a Lamp Server with Webmin installed - However I have recently not been able to update the serve, theses are the errors displayed.

```
$ sudo sudo apt-get update && apt-get upgrade
Err [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg                               
  Temporary failure resolving &#8216;download.webmin.com&#8217;
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Err [http://webmin.mirror.somersettechsolutions.co.uk](http://webmin.mirror.somersettechsolutions.co.uk) sarge Release.gpg         
  Temporary failure resolving &#8216;webmin.mirror.somersettechsolutions.co.uk&#8217;
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB   
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Err [http://download.webmin.com/download/repository/](http://download.webmin.com/download/repository/) sarge/contrib Translation-en_GB
  Temporary failure resolving &#8216;download.webmin.com&#8217;
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB             
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Err [http://webmin.mirror.somersettechsolutions.co.uk/repository/](http://webmin.mirror.somersettechsolutions.co.uk/repository/) sarge/contrib Translation-en_GB
  Temporary failure resolving &#8216;webmin.mirror.somersettechsolutions.co.uk&#8217;
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB 
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB   
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB 
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Reading package lists... Done        
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;

W: Failed to fetch [http://download.webmin.com/download/repository/dists/sarge/Release.gpg](http://download.webmin.com/download/repository/dists/sarge/Release.gpg)  Temporary failure resolving &#8216;download.webmin.com&#8217;

W: Failed to fetch [http://download.webmin.com/download/repository/dists/sarge/contrib/i18n/Translation-en_GB.bz2](http://download.webmin.com/download/repository/dists/sarge/contrib/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;download.webmin.com&#8217;

W: Failed to fetch [http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/Release.gpg](http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/Release.gpg)  Temporary failure resolving &#8216;webmin.mirror.somersettechsolutions.co.uk&#8217;

W: Failed to fetch [http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/contrib/i18n/Translation-en_GB.bz2](http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/contrib/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;webmin.mirror.somersettechsolutions.co.uk&#8217;

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

I have tried with the firewall enabled and disabled in the hope that I had not configured the firewall correctly.
But No Success so far.Help Please.

Can anyone help here?

System:- Ubuntu 10.4Lts
Lamp Server - Webmin (No Webmin Modules Install)

---

### Post by volkswagner on 2011-11-25
Can you successfully run just update without failure:
```
sudo apt-get update
```

I had similar problem resolving ubuntu repos.  My issue was due to a malformed /etc/network/interfaces file.  I was missing the gateway definition for my static ip.  Odd thing was apt-get was not able to resolve but the host command and wget would not fail.

What do you get if you run host command against those domains?

```
host security.ubuntu.com
```

---

### Post by Alpha99 on 2011-11-30
> **volkswagner said:**
> Can you successfully run just update without failure:
```
sudo apt-get update
```

I had similar problem resolving ubuntu repos.  My issue was due to a malformed /etc/network/interfaces file.  I was missing the gateway definition for my static ip.  Odd thing was apt-get was not able to resolve but the host command and wget would not fail.

What do you get if you run host command against those domains?

```
host security.ubuntu.com
```

Many Thanks for your reply volkswagner.
I apologise for the delay in responding as my trusted and faithful Firefox Browser seems to have totally failed now moved to Chrom.

In reply to your first question, "can you successfully run just update without failure" : Sorry I can not successfully run just update without failure.

Moving on In regards to 'a malformed /etc/network/interfaces file' I have checked the primary network interface /etc/network/interfaces and i do not see any issues there - as it successfully updated before without any issues in addition the IP Address is stated correctly in the interface.

I assume this is what you mean- 
When i run sudo host security.ubuntu.com - the reply comes back ;; connection timed out; no servers could be reached.

If I have not understood you reply please advise.
Many Thanks for you assistance thus far.

---

### Post by cariboo on 2011-11-30
There are a couple of simple things you can check, as it looks like you may have a DNS problem. At the prompt type:

```
ping www.google.com
```

If that doesn't work try:

```
ping 173.194.33.19
```

If the second command works, but the first doesn't, could you paste the output of the following command in your next post:

```
cat /etc/resolv.conf
```

---

### Post by Alpha99 on 2011-12-02
> **cariboo907 said:**
> There are a couple of simple things you can check, as it looks like you may have a DNS problem. At the prompt type:

```
ping www.google.com
```

If that doesn't work try:

```
ping 173.194.33.19
```

If the second command works, but the first doesn't, could you paste the output of the following command in your next post:

```
cat /etc/resolv.conf
```

Thanks for your reply cariboo907, as requested please see the following below, as neither of these seem to work:-

1. $ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

2. $ ping 173.194.33.19
PING 173.194.33.19 (173.194.33.19) 56(84) bytes of data.
From 192.168.0.100 icmp_seq=1 Destination Host Unreachable
From 192.168.0.100 icmp_seq=2 Destination Host Unreachable
^C
--- 173.194.33.19 ping statistics ---
12 packets transmitted, 0 received, +9 errors, 100% packet loss, time 11063ms
, pipe 3

3. $ cat /etc/resolv.conf
nameserver 192.168.0.1

Hope This helps.

---

### Post by CharlesA on 2011-12-02
It looks like you can't even get out of your local network.

Post this please:

```
route
```

It's either a DNS issue or a problem with your ip address.

---

### Post by Alpha99 on 2011-12-02
> **CharlesA said:**
> It looks like you can't even get out of your local network.

Post this please:

```
route
```

It's either a DNS issue or a problem with your ip address.

As requested:-
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     192.168.0.1     255.255.255.0   UG    0      0        0 eth2
192.168.0.0     *               255.255.255.0   U     0      0        0 eth2
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth2
```

---

### Post by CharlesA on 2011-12-02
Route looks ok. Can you post this please:

```
sudo ifconfig -a
```

---

### Post by Alpha99 on 2011-12-02
> **CharlesA said:**
> Route looks ok. Can you post this please:

```
sudo ifconfig -a
```

```
$ sudo ifconfig -a
[sudo] password for webmaster: 
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:ce:38:2c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 

eth1      Link encap:Ethernet  HWaddr 00:0b:cd:ce:38:30  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 

eth2      Link encap:Ethernet  HWaddr 00:02:b3:aa:fc:37  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:feaa:fc37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:22029 (22.0 KB)  TX bytes:24649 (24.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6020 (6.0 KB)  TX bytes:6020 (6.0 KB)
```

---

### Post by CharlesA on 2011-12-02
Are you able to ping something locally?

It sounds like it just can't get out of your local network? Does any other local machine do this?

---

### Post by Alpha99 on 2011-12-02
> **CharlesA said:**
> Are you able to ping something locally?

It sounds like it just can't get out of your local network? Does any other local machine do this?

I have no problem in pinging local, as i control the server remotely.
Do You think i should just scrap this set-up and re install yet again or could this be an issue with the Webmin, being installed.

64 bytes from 192.168.1.99: icmp_seq=1 ttl=64 time=0.208 ms
64 bytes from 192.168.1.99: icmp_seq=2 ttl=64 time=0.152 ms

I have had problems earlier with Firefox 8 and the gateway; had to do a restart, problem solved apart from that everything is fine.

---

### Post by CharlesA on 2011-12-02
If other machines on the same network can get on the network can get to the internet, it's got to be a problem with that machine.

I don't think webmin would have caused it, but you can reinstall to see if it will start working (but try a livecd first)

---

### Post by Alpha99 on 2011-12-02
> **CharlesA said:**
> If other machines on the same network can get on the network can get to the internet, it's got to be a problem with that machine.

I don't think webmin would have caused it, but you can reinstall to see if it will start working (but try a livecd first)

Many thanks for your assistance I will let #you know if i solve the problem any other way.
Thanks again.

---

### Post by CharlesA on 2011-12-02
No problem.

I can't really think of a reason why it's not working. The IP is right, and the route looks right too, but it's just not working for some reason.

Good luck with the reinstall, if you decide to go that route.

---

### Post by MidAtlanticProf on 2012-08-31
I read with great interest this series of posts and responses.  I followed along and achieved the exact same results with my Unbuntu server 10.04 LTS. I cannot access the DNS - My tech guys who set the network confirmed that my numbers are correct and they are at a loss for the why. 

Basically I want to know what you did to solve it? if at all. Interestingly this problem occurred when I moved to a "newer" Dell server.  

Any help would be greatly appreciated.

---

### Post by chonybmx on 2012-10-25
Hi, Im Jonathan From Arg.
I have exactly similar problem.
I tested more sources but cannot update.

troubleshooting

I can ping to other servers on muy LAN an then can ping to others servers on Internet


UPDATE:
```

root@zimbra:~# apt-get update

Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid Release.gpg                                                                          
  No pude conectarme a ar.archive.ubuntu.com:80 (200.236.31.4). - connect (110: Expiró el tiempo de conexión)
Err [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/main Translation-es                                                          
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-es                                                    
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/universe Translation-es                                                      
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-es                                                    
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates Release.gpg                                                                  
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-es                                                  
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-es                                            
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-es                                              
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid Release                                                            
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-updates Release                                                    
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-backports Release                                                  
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/main Packages                                                      
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/restricted Packages                                                                  
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/main Sources                                                                         
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid/restricted Sources 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-backports/restricted Sources                                        
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-backports/universe Sources                                          
  No se pudo conectar a ar.archive.ubuntu.com:http:
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) lucid-backports/multiverse Sources                                        
  No se pudo conectar a ar.archive.ubuntu.com:http:
27% [Conectando a archive.canonical.com (91.189.92.191)] [Conectando a security.ubuntu.com (91.189.92.190)]^C

```


PING IP
```

root@zimbra:~# ping 91.189.92.191
PING 91.189.92.191 (91.189.92.191) 56(84) bytes of data.
64 bytes from 91.189.92.191: icmp_seq=1 ttl=58 time=216 ms
64 bytes from 91.189.92.191: icmp_seq=2 ttl=58 time=215 ms
64 bytes from 91.189.92.191: icmp_seq=3 ttl=58 time=215 ms
64 bytes from 91.189.92.191: icmp_seq=4 ttl=58 time=215 ms
^C

```


PING DOMAIN
```

PING archive.canonical.com (91.189.92.150) 56(84) bytes of data.
64 bytes from kudan.canonical.com (91.189.92.150): icmp_seq=1 ttl=58 time=216 ms
64 bytes from kudan.canonical.com (91.189.92.150): icmp_seq=2 ttl=58 time=216 ms
64 bytes from kudan.canonical.com (91.189.92.150): icmp_seq=3 ttl=58 time=216 ms
64 bytes from kudan.canonical.com (91.189.92.150): icmp_seq=4 ttl=58 time=216 ms
64 bytes from kudan.canonical.com (91.189.92.150): icmp_seq=5 ttl=58 time=216 ms
^C

```


RESOLV
```

root@zimbra:~# cat /etc/resolv.conf 
nameserver 8.8.8.8
nameserver 8.8.4.4
root@zimbra:~#

```


strange is this..
for my web browser can download this archive
[http://archive.canonical.com/ls-lR.gz](http://archive.canonical.com/ls-lR.gz)

but using wget cannot obtain the archive
```

root@zimbra:~# wget [http://archive.canonical.com/ls-lR.gz](http://archive.canonical.com/ls-lR.gz)
--2012-10-25 10:29:53--  [http://archive.canonical.com/ls-lR.gz](http://archive.canonical.com/ls-lR.gz)
Resolviendo archive.canonical.com... 91.189.92.150, 91.189.92.191
Conectando a archive.canonical.com|91.189.92.150|:80... falló: Expiró el tiempo de conexión.
Conectando a archive.canonical.com|91.189.92.191|:80... falló: Expiró el tiempo de conexión.
Reintentando.

```






SOURCES
```

root@zimbra:~# cat /etc/apt/sources.list
#deb cdrom:[Ubuntu-Server 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid main restricted

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid main
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid main

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
root@zimbra:~# 

```



ROUTE
```

root@zimbra:~# route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.15.1    0.0.0.0         UG    100    0        0 eth0
root@zimbra:~# 

```



PACKETS
```

root@zimbra:~# dpkg -l
Deseado=u:desconocido/Instalar/eliminaR/Purgar/H:mantener
| Estado=No/Inst/arch-Cfg/U:desemp/Fallo-cfg/H:medio-inst/W:espera-act/pTe-act
|/ Err?=(nada)/Requiere-reinstalación (Estado,Err: mayúsculas=malo)
||/ Nombre                    Versión                  Descripción
+++-=========================-=========================-==================================================================
ii  adduser                   3.112ubuntu1              add and remove users and groups
ii  apparmor                  2.5.1-0ubuntu0.10.04.4    User-space parser utility for AppArmor
ii  apparmor-utils            2.5.1-0ubuntu0.10.04.4    Utilities for controlling AppArmor
ii  apport                    1.13.3-0ubuntu2.1         automatically generate crash reports for debugging
ii  apport-symptoms           0.9                       symptom scripts for apport
ii  apt                       0.7.25.3ubuntu9.14        Advanced front-end for dpkg
ii  apt-transport-https       0.7.25.3ubuntu9.14        APT https transport
ii  apt-utils                 0.7.25.3ubuntu9.14        APT utility programs
ii  aptitude                  0.4.11.11-1ubuntu10lucid1 terminal-based package manager
ii  at                        3.1.11-1ubuntu5.1         Delayed job execution and batch processing
ii  base-files                5.0.0ubuntu20.10.04.5     Debian base system miscellaneous files
ii  base-passwd               3.5.22                    Debian base system master password and group files
ii  bash                      4.1-2ubuntu3              The GNU Bourne Again SHell
ii  bash-completion           1:1.1-3ubuntu2            programmable completion for the bash shell
ii  bc                        1.06.95-2                 The GNU bc arbitrary precision calculator language
ii  bind9                     1:9.7.0.dfsg.P1-1ubuntu0. Internet Domain Name Server
ii  bind9-doc                 1:9.7.0.dfsg.P1-1ubuntu0. Documentation for BIND
ii  bind9-host                1:9.7.0.dfsg.P1-1ubuntu0. Version of 'host' bundled with BIND 9.X
ii  bind9utils                1:9.7.0.dfsg.P1-1ubuntu0. Utilities for BIND
ii  bsdmainutils              8.0.1ubuntu1              collection of more utilities from FreeBSD
ii  bsdutils                  1:2.17.2-0ubuntu1.10.04.2 Basic utilities from 4.4BSD-Lite
ii  busybox-initramfs         1:1.13.3-1ubuntu11        Standalone shell setup for initramfs
ii  busybox-static            1:1.13.3-1ubuntu11        Standalone rescue shell with tons of builtin utilities
ii  byobu                     2.68-0ubuntu1.2           a set of useful profiles and a profile-switcher for GNU screen
ii  bzip2                     1.0.5-4ubuntu0.2          high-quality block-sorting file compressor - utilities
ii  ca-certificates           20090814ubuntu0.10.04.1   Common CA certificates
ii  command-not-found         0.2.40ubuntu5             Suggest installation of packages in interactive bash sessions
ii  command-not-found-data    0.2.40ubuntu5             Set of data files for command-not-found.
ii  console-setup             1.34ubuntu15              console font and keymap setup program
ii  console-terminus          4.30-2                    Fixed-width fonts for fast reading on the Linux console
ii  coreutils                 7.4-2ubuntu3              The GNU core utilities
ii  cpio                      2.10-1ubuntu2             GNU cpio -- a program to manage archives of files
ii  cpp                       4:4.4.3-1ubuntu1          The GNU C preprocessor (cpp)
ii  cpp-4.4                   4.4.3-4ubuntu5.1          The GNU C preprocessor
ii  cpu-checker               0.1-0ubuntu2              tools to help evaluate certain CPU (or BIOS) features
ii  cron                      3.0pl1-106ubuntu7         process scheduling daemon
ii  dash                      0.5.5.1-3ubuntu2          POSIX-compliant shell
ii  debconf                   1.5.28ubuntu4             Debian configuration management system
ii  debconf-i18n              1.5.28ubuntu4             full internationalization support for debconf
ii  debianutils               3.2.2                     Miscellaneous utilities specific to Debian
ii  dhcp3-client              3.1.3-2ubuntu3.4          DHCP client
ii  dhcp3-common              3.1.3-2ubuntu3.4          common files used by all the dhcp3* packages
ii  diffutils                 1:2.8.1-18                File comparison utilities
ii  dmidecode                 2.9-1.2                   Dump Desktop Management Interface data
ii  dmsetup                   2:1.02.39-1ubuntu4.1      The Linux Kernel Device Mapper userspace library
ii  dnsutils                  1:9.7.0.dfsg.P1-1ubuntu0. Clients provided with BIND
ii  dosfstools                3.0.7-1                   utilities for making and checking MS-DOS FAT filesystems
ii  dpkg                      1.15.5.6ubuntu4.6         Debian package management system
ii  e2fslibs                  1.41.11-1ubuntu2.1        ext2/ext3/ext4 file system libraries
ii  e2fsprogs                 1.41.11-1ubuntu2.1        ext2/ext3/ext4 file system utilities
ii  ed                        1.4-1build1               The classic UNIX line editor
ii  eject                     2.1.5+deb1+cvs20081104-7  ejects CDs and operates CD-Changers under Linux
ii  file                      5.03-5ubuntu1             Determines file type using "magic" numbers
ii  findutils                 4.4.2-1ubuntu1            utilities for finding files--find, xargs
ii  friendly-recovery         0.2.10                    Make recovery more user-friendly
ii  ftp                       0.17-19build1             The FTP client
ii  fuse-utils                2.8.1-1.1ubuntu3.1        Filesystem in USErspace (utilities)
ii  gcc-4.4-base              4.4.3-4ubuntu5.1          The GNU Compiler Collection (base package)
ii  geoip-database            1.4.6.dfsg-17             IP lookup command line tools that use the GeoIP library (country d
ii  gettext-base              0.17-8ubuntu3             GNU Internationalization utilities for the base system
ii  gnupg                     1.4.10-2ubuntu1.1         GNU privacy guard - a free PGP replacement
ii  gnupg-curl                1.4.10-2ubuntu1.1         GNU privacy guard - a free PGP replacement (cURL)
ii  gpgv                      1.4.10-2ubuntu1.1         GNU privacy guard - signature verification tool
ii  grep                      2.5.4-4build1             GNU grep, egrep and fgrep
ii  groff-base                1.20.1-7                  GNU troff text-formatting system (base system components)
ii  grub-common               1.98-1ubuntu13            GRand Unified Bootloader, version 2 (common files)
ii  grub-pc                   1.98-1ubuntu13            GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  gzip                      1.3.12-9ubuntu1.1         GNU compression utilities
ii  hdparm                    9.15-1ubuntu9             tune hard disk parameters for high performance
ii  hostname                  3.03ubuntu1               utility to set/show the host name or domain name
ii  ifupdown                  0.6.8ubuntu29.2           high level tools to configure network interfaces
ii  info                      4.13a.dfsg.1-5ubuntu1     Standalone GNU Info documentation browser
ii  initramfs-tools           0.92bubuntu78             tools for generating an initramfs
ii  initramfs-tools-bin       0.92bubuntu78             binaries used by initramfs-tools
ii  initscripts               2.87dsf-4ubuntu17.5       scripts for initializing and shutting down the system
ii  insserv                   1.12.0-14ubuntu0.2        Tool to organize boot sequence using LSB init.d script dependencie
ii  install-info              4.13a.dfsg.1-5ubuntu1     Manage installed documentation in info format
ii  installation-report       2.39ubuntu4               system installation report
ii  iproute                   20091226-1                networking and traffic control tools
ii  iptables                  1.4.4-2ubuntu2            administration tools for packet filtering and NAT
ii  iputils-arping            3:20071127-2ubuntu1       Tool to send ARP Requests for an IP address
ii  iputils-ping              3:20071127-2ubuntu1       Tools to test the reachability of network hosts
ii  iputils-tracepath         3:20071127-2ubuntu1       Tools to trace the network path to a remote host
ii  irqbalance                0.55+20091017-3ubuntu2    Daemon to balance interrupts for SMP systems
ii  iso-codes                 3.12.1-1                  ISO language, territory, currency, script codes and their translat
ii  kbd                       1.15-1ubuntu3             Linux console font and keytable utilities
ii  klibc-utils               1.5.17-4ubuntu1           small utilities built with klibc for early boot
ii  landscape-common          12.05-0ubuntu0.10.04      The Landscape administration system client - Common files
ii  language-pack-en          1:10.04+20110931          translation updates for language English
ii  language-pack-en-base     1:10.04+20110931          translations for language English
ii  language-pack-es          1:10.04+20110931          translation updates for language Spanish; Castilian
ii  language-pack-es-base     1:10.04+20110931          translations for language Spanish; Castilian
ii  language-selector-common  0.5.8                     Language selector for Ubuntu Linux
ii  laptop-detect             0.13.7ubuntu2             attempt to detect a laptop
ii  less                      436-1                     pager program similar to more
ii  libacl1                   2.2.49-2                  Access control list shared library
ii  libapparmor-perl          2.5.1-0ubuntu0.10.04.4    AppArmor library Perl bindings
ii  libapparmor1              2.5.1-0ubuntu0.10.04.4    changehat AppArmor library
ii  libatm1                   1:2.5.1-1.2               shared library for ATM (Asynchronous Transfer Mode)
ii  libattr1                  1:2.4.44-1                Extended attribute shared library
ii  libbind9-60               1:9.7.0.dfsg.P1-1ubuntu0. BIND9 Shared Library used by BIND
ii  libblkid1                 2.17.2-0ubuntu1.10.04.2   block device id library
ii  libbsd0                   0.2.0-1                   utility functions from BSD systems - shared library
ii  libbz2-1.0                1.0.5-4ubuntu0.2          high-quality block-sorting file compressor library - runtime
ii  libc-bin                  2.11.1-0ubuntu7.10        Embedded GNU C Library: Binaries
ii  libc6                     2.11.1-0ubuntu7.10        Embedded GNU C Library: Shared libraries
ii  libcap-ng0                0.6.2-4                   An alternate posix capabilities library
ii  libcap2                   1:2.17-2ubuntu1           support for getting/setting POSIX.1e capabilities
ii  libclass-accessor-perl    0.34-1                    Perl module that automatically generates accessors
ii  libcomerr2                1.41.11-1ubuntu2.1        common error description library
ii  libcurl3-gnutls           7.19.7-1ubuntu1.1         Multi-protocol file transfer library (GnuTLS)
ii  libcwidget3               0.5.13-1ubuntu1           high-level terminal interface library for C++ (runtime files)
ii  libdb4.8                  4.8.24-1ubuntu1           Berkeley v4.8 Database Libraries [runtime]
ii  libdbus-1-3               1.2.16-2ubuntu4.5         simple interprocess messaging system
ii  libdbus-glib-1-2          0.84-1ubuntu0.2           simple interprocess messaging system (GLib-based shared library)
ii  libdevmapper1.02.1        2:1.02.39-1ubuntu4.1      The Linux Kernel Device Mapper userspace library
ii  libdns64                  1:9.7.0.dfsg.P1-1ubuntu0. DNS Shared Library used by BIND
ii  libdrm-intel1             2.4.18-1ubuntu3           Userspace interface to intel-specific kernel DRM services -- runti
ii  libdrm-nouveau1           2.4.18-1ubuntu3           Userspace interface to nouveau-specific kernel DRM services -- run
ii  libdrm-radeon1            2.4.18-1ubuntu3           Userspace interface to radeon-specific kernel DRM services -- runt
ii  libdrm2                   2.4.18-1ubuntu3           Userspace interface to kernel DRM services -- runtime
ii  libedit2                  2.11-20080614-1build1     BSD editline and history libraries
ii  libelf1                   0.143-1                   library to read and write ELF files
ii  libept0                   0.5.30                    High-level library for managing Debian package information
ii  libexpat1                 2.0.1-7ubuntu1.1          XML parsing C library - runtime library
ii  libffi5                   3.0.9-1                   Foreign Function Interface library runtime
ii  libfont-afm-perl          1.20-1                    Font::AFM - Interface to Adobe Font Metrics files
ii  libfreetype6              2.3.11-1ubuntu2.6         FreeType 2 font engine, shared library files
ii  libfribidi0               0.19.2-1                  Free Implementation of the Unicode BiDi algorithm
ii  libfuse2                  2.8.1-1.1ubuntu3.1        Filesystem in USErspace library
ii  libgc1c2                  1:6.8-1.2ubuntu1.1        conservative garbage collector for C and C++
ii  libgcc1                   1:4.4.3-4ubuntu5.1        GCC support library
ii  libgcrypt11               1.4.4-5ubuntu2.1          LGPL Crypto library - runtime library
ii  libgdbm3                  1.8.3-9                   GNU dbm database routines (runtime version)
ii  libgeoip1                 1.4.6.dfsg-17             A non-DNS IP-to-country resolver library
ii  libglib2.0-0              2.24.1-0ubuntu1           The GLib library of C routines
ii  libgmp3c2                 2:4.3.2+dfsg-1ubuntu1     Multiprecision arithmetic library
ii  libgnutls26               2.8.5-2ubuntu0.2          the GNU TLS library - runtime library
ii  libgpg-error0             1.6-1ubuntu2              library for common error values and messages in GnuPG components
ii  libgpm2                   1.20.4-3.2ubuntu2         General Purpose Mouse - shared library
ii  libgssapi-krb5-2          1.8.1+dfsg-2ubuntu0.11    MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
ii  libhtml-format-perl       2.04-2                    format HTML syntax trees into text, PostScript or RTF
ii  libhtml-parser-perl       3.64-1                    collection of modules that parse HTML text documents
ii  libhtml-tagset-perl       3.20-2                    Data tables pertaining to HTML
ii  libhtml-tree-perl         3.23-1                    represent and create HTML syntax trees
ii  libidn11                  1.15-2                    GNU Libidn library, implementation of IETF IDN specifications
ii  libio-string-perl         1.08-2                    Emulate IO::File interface for in-core strings
ii  libisc60                  1:9.7.0.dfsg.P1-1ubuntu0. ISC Shared Library used by BIND
ii  libisccc60                1:9.7.0.dfsg.P1-1ubuntu0. Command Channel Library used by BIND
ii  libisccfg60               1:9.7.0.dfsg.P1-1ubuntu0. Config File Handling Library used by BIND
ii  libiw30                   30~pre9-3ubuntu4          Wireless tools - library
ii  libjs-jquery              1.3.3-2ubuntu1            JavaScript library for dynamic web applications
ii  libk5crypto3              1.8.1+dfsg-2ubuntu0.11    MIT Kerberos runtime libraries - Crypto Library
ii  libkeyutils1              1.2-12                    Linux Key Management Utilities (library)
ii  libklibc                  1.5.17-4ubuntu1           minimal libc subset for use with initramfs
ii  libkrb5-3                 1.8.1+dfsg-2ubuntu0.11    MIT Kerberos runtime libraries
ii  libkrb5support0           1.8.1+dfsg-2ubuntu0.11    MIT Kerberos runtime libraries - Support library
ii  libldap-2.4-2             2.4.21-0ubuntu5.7         OpenLDAP libraries
ii  liblocale-gettext-perl    1.05-6                    Using libc functions for internationalization in Perl
ii  liblockfile1              1.08-3ubuntu1             NFS-safe locking library, includes dotlockfile program
ii  liblua5.1-0               5.1.4-5                   Simple, extensible, embeddable programming language
ii  liblwres60                1:9.7.0.dfsg.P1-1ubuntu0. Lightweight Resolver Library used by BIND
ii  libmagic1                 5.03-5ubuntu1             File type determination library using "magic" numbers
ii  libmailtools-perl         2.05-1                    Manipulate email in perl programs
ii  libmpfr1ldbl              2.4.2-3ubuntu1            multiple precision floating-point computation
ii  libncurses5               5.7+20090803-2ubuntu3     shared libraries for terminal handling
ii  libncursesw5              5.7+20090803-2ubuntu3     shared libraries for terminal handling (wide character support)
ii  libnewt0.52               0.52.10-5ubuntu1          Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libnih-dbus1              1.0.1-1                   NIH D-Bus Bindings Library
ii  libnih1                   1.0.1-1                   NIH Utility Library
ii  libnl1                    1.1-5build1               library for dealing with netlink sockets
ii  libntfs-3g75              1:2010.3.6-1ubuntu1       ntfs-3g filesystem in userspace (FUSE) library
ii  libpam-modules            1.1.1-2ubuntu5.4          Pluggable Authentication Modules for PAM
ii  libpam-runtime            1.1.1-2ubuntu5.4          Runtime support for the PAM library
ii  libpam0g                  1.1.1-2ubuntu5.4          Pluggable Authentication Modules library
ii  libparse-debianchangelog- 1.1.1-2ubuntu2            parse Debian changelogs and output them in other formats
ii  libparted0debian1         2.2-5ubuntu5.2            The GNU Parted disk partitioning shared library
ii  libpcap0.8                1.0.0-6                   system interface for user-level packet capture
ii  libpci3                   1:3.0.0-4ubuntu17         Linux PCI Utilities (shared library)
ii  libpcre3                  7.8-3build1               Perl 5 Compatible Regular Expression Library - runtime files
ii  libpcsclite1              1.5.3-1ubuntu4.2          Middleware to access a smart card using PC/SC (library)
ii  libperl5.10               5.10.1-8ubuntu2.1         shared Perl library
ii  libplymouth2              0.8.2-2ubuntu2.2          graphical boot animation and logger - shared libraries
ii  libpng12-0                1.2.42-1ubuntu2.5         PNG library - runtime
ii  libpopt0                  1.15-1                    lib for parsing cmdline parameters
ii  libpython2.6              2.6.5-1ubuntu6            Shared Python runtime library (version 2.6)
ii  libreadline6              6.1-1                     GNU readline and history libraries, run-time libraries
ii  librpc-xml-perl           0.72-1                    Perl module implementation of XML-RPC
ii  libsasl2-2                2.1.23.dfsg1-5ubuntu1     Cyrus SASL - authentication abstraction library
ii  libsasl2-modules          2.1.23.dfsg1-5ubuntu1     Cyrus SASL - pluggable authentication modules
ii  libselinux1               2.0.89-4                  SELinux runtime shared libraries
ii  libsepol1                 2.0.40-2                  SELinux library for manipulating binary security policies
ii  libsigc++-2.0-0c2a        2.2.4.2-1                 type-safe Signal Framework for C++ - runtime
ii  libslang2                 2.2.2-2ubuntu1            The S-Lang programming library - runtime version
ii  libsqlite3-0              3.6.22-1                  SQLite 3 shared library
ii  libss2                    1.41.11-1ubuntu2.1        command-line interface parsing library
ii  libssl0.9.8               0.9.8k-7ubuntu8.13        SSL shared libraries
ii  libstdc++6                4.4.3-4ubuntu5.1          The GNU Standard C++ Library v3
ii  libsub-name-perl          0.04-1build1              Assigns a new name to referenced sub
ii  libtasn1-3                2.4-1ubuntu0.1            Manage ASN.1 structures (runtime)
ii  libterm-readkey-perl      2.30-4build1              A perl module for simple terminal control
ii  libtext-charwidth-perl    0.04-6                    get display widths of characters on the terminal
ii  libtext-iconv-perl        1.7-2                     converts between character sets in Perl
ii  libtext-wrapi18n-perl     0.06-7                    internationalized substitute of Text::Wrap
ii  libtimedate-perl          1.1900-1                  Time and date functions for Perl
ii  libudev0                  151-12.3                  udev library
ii  liburi-perl               1.52-1                    module to manipulate and access URI strings
ii  libusb-0.1-4              2:0.1.12-14ubuntu0.2      userspace USB programming library
ii  libuuid1                  2.17.2-0ubuntu1.10.04.2   Universally Unique ID library
ii  libwrap0                  7.6.q-18                  Wietse Venema's TCP wrappers library
ii  libwww-perl               5.834-1ubuntu0.1          Perl HTTP/WWW client/server library
ii  libx11-6                  2:1.3.2-1ubuntu3          X11 client-side library
ii  libx11-data               2:1.3.2-1ubuntu3          X11 client-side library
ii  libxapian15               1.0.18-1                  Search engine library
ii  libxau6                   1:1.0.5-1                 X11 authorisation library
ii  libxcb1                   1.5-2                     X C Binding
ii  libxdmcp6                 1:1.0.3-1                 X11 Display Manager Control Protocol library
ii  libxext6                  2:1.1.1-2                 X11 miscellaneous extension library
ii  libxml-libxml-perl        1.70.ds-1                 Perl interface to the libxml2 library
ii  libxml-namespacesupport-p 1.09-3                    Perl module for supporting simple generic namespaces
ii  libxml-parser-perl        2.36-1.1build3            Perl module for parsing XML files
ii  libxml-sax-expat-perl     0.40-1                    Perl module for a SAX2 driver for Expat (XML::Parser)
ii  libxml-sax-perl           0.96+dfsg-2               Perl module for using and building Perl SAX2 XML processors
ii  libxml2                   2.7.6.dfsg-1ubuntu1.6     GNOME XML library
ii  libxmuu1                  2:1.0.5-1                 X11 miscellaneous micro-utility library
ii  linux-firmware            1.34.14                   Firmware for Linux kernel drivers
ii  linux-headers-2.6.32-43   2.6.32-43.97              Header files related to Linux kernel version 2.6.32
ii  linux-headers-2.6.32-43-s 2.6.32-43.97              Linux kernel headers for version 2.6.32 on x86_64
ii  linux-headers-server      2.6.32.43.50              Linux kernel headers on Server Equipment.
ii  linux-image-2.6.32-38-ser 2.6.32-38.83              Linux kernel image for version 2.6.32 on x86_64
ii  linux-image-2.6.32-43-ser 2.6.32-43.97              Linux kernel image for version 2.6.32 on x86_64
ii  linux-image-server        2.6.32.43.50              Linux kernel image on Server Equipment.
ii  linux-server              2.6.32.43.50              Complete Linux kernel on Server Equipment.
ii  locales                   2.11+git20100304-3        common files for locale support
ii  lockfile-progs            0.1.13ubuntu1             Programs for locking and unlocking files and mailboxes
ii  login                     1:4.1.4.2-1ubuntu2.2      system login tools
ii  logrotate                 3.7.8-4ubuntu2.2          Log rotation utility
ii  lsb-base                  4.0-0ubuntu8              Linux Standard Base 4.0 init script functionality
ii  lsb-release               4.0-0ubuntu8              Linux Standard Base version reporting utility
ii  lshw                      02.14-1build1             information about hardware configuration
ii  lsof                      4.81.dfsg.1-1build1       List open files
ii  ltrace                    0.5.3-2ubuntu3            Tracks runtime library calls in dynamically linked programs
ii  lzma                      4.43-14ubuntu2            Compression method of 7z format in 7-Zip program
ii  make                      3.81-7ubuntu1             An utility for Directing compilation.
ii  makedev                   2.3.1-89ubuntu1           creates device files in /dev
ii  man-db                    2.5.7-2ubuntu1            on-line manual pager
ii  manpages                  3.23-1                    Manual pages about using a GNU/Linux system
ii  mawk                      1.3.3-15ubuntu2           a pattern scanning and text processing language
ii  memtest86+                4.00-2ubuntu3             thorough real-mode memory tester
ii  mime-support              3.48-1ubuntu1             MIME files 'mime.types' & 'mailcap', and support programs
ii  mlocate                   0.22.2-1ubuntu1           quickly find files on the filesystem based on their name
ii  module-init-tools         3.11.1-2ubuntu1           tools for managing Linux kernel modules
ii  mount                     2.17.2-0ubuntu1.10.04.2   Tools for mounting and manipulating filesystems
ii  mountall                  2.15.3                    filesystem mounting tool
ii  mtr-tiny                  0.75-2build1              Full screen ncurses traceroute tool
ii  nano                      2.2.2-1                   small, friendly text editor inspired by Pico
ii  ncurses-base              5.7+20090803-2ubuntu3     basic terminal type definitions
ii  ncurses-bin               5.7+20090803-2ubuntu3     terminal-related programs and man pages
ii  net-tools                 1.60-23ubuntu2            The NET-3 networking toolkit
ii  netbase                   4.35ubuntu3               Basic TCP/IP networking system
ii  netcat-openbsd            1.89-3ubuntu2             TCP/IP swiss army knife
ii  nmap                      5.00-3                    The Network Mapper
ii  ntfs-3g                   1:2010.3.6-1ubuntu1       read-write NTFS driver for FUSE
ii  ntpdate                   1:4.2.4p8+dfsg-1ubuntu2.1 client for setting system time from NTP servers
ii  openssh-client            1:5.3p1-3ubuntu7          secure shell (SSH) client, for secure access to remote machines
ii  openssh-server            1:5.3p1-3ubuntu7          secure shell (SSH) server, for secure access from remote machines
ii  openssl                   0.9.8k-7ubuntu8.13        Secure Socket Layer (SSL) binary and related cryptographic tools
ii  os-prober                 1.38                      utility to detect other OSes on a set of drives
ii  parted                    2.2-5ubuntu5.2            The GNU Parted disk partition resizing program
ii  passwd                    1:4.1.4.2-1ubuntu2.2      change and administer password and group data
ii  patch                     2.6-2ubuntu1              Apply a diff file to an original
ii  pciutils                  1:3.0.0-4ubuntu17         Linux PCI Utilities
ii  perl                      5.10.1-8ubuntu2.1         Larry Wall's Practical Extraction and Report Language
ii  perl-base                 5.10.1-8ubuntu2.1         minimal Perl system
ii  perl-modules              5.10.1-8ubuntu2.1         Core Perl modules
ii  plymouth                  0.8.2-2ubuntu2.2          graphical boot animation and logger - main package
ii  plymouth-theme-ubuntu-tex 0.8.2-2ubuntu2.2          graphical boot animation and logger - ubuntu-logo theme
ii  popularity-contest        1.48ubuntu1               Vote for your favourite packages automatically
ii  powermgmt-base            1.31                      Common utils and configs for power management
ii  ppp                       2.4.5~git20081126t100229- Point-to-Point Protocol (PPP) - daemon
ii  pppconfig                 2.3.18ubuntu2             A text menu based utility for configuring ppp
ii  pppoeconf                 1.19ubuntu1               configures PPPoE/ADSL connections
ii  procps                    1:3.2.8-1ubuntu4.3        /proc file system utilities
ii  psmisc                    22.10-1                   utilities that use the proc file system
ii  python                    2.6.5-0ubuntu1            An interactive high-level object-oriented language (default versio
ii  python-apport             1.13.3-0ubuntu2.1         apport crash report handling library
ii  python-apt                0.7.94.2ubuntu6.4         Python interface to libapt-pkg
ii  python-central            0.6.15ubuntu1             register and build utility for Python packages
ii  python-dbus               0.83.0-1ubuntu3           simple interprocess messaging system (Python interface)
ii  python-gdbm               2.6.5-0ubuntu2            GNU dbm database support for Python
ii  python-gnupginterface     0.3.2-9.1                 Python interface to GnuPG (GPG)
ii  python-gobject            2.21.1-0ubuntu3           Python bindings for the GObject library
ii  python-httplib2           0.7.2-1ubuntu2~0.10.04.1  comprehensive HTTP client library written in Python
ii  python-launchpadlib       1.6.0-0ubuntu1            Launchpad web services client library
ii  python-lazr.restfulclient 0.9.11-1ubuntu1.3         client for lazr.restful-based web services
ii  python-lazr.uri           1.0.2-1                   library for parsing, manipulating, and generating URIs
ii  python-minimal            2.6.5-0ubuntu1            A minimal subset of the Python language (default version)
ii  python-newt               0.52.10-5ubuntu1          A NEWT module for Python
ii  python-oauth              1.0a~svn1124-0ubuntu2     implementation of the OAuth protocol
ii  python-openssl            0.10-1                    Python wrapper around the OpenSSL library
ii  python-pam                0.4.2-12.1ubuntu1.10.04.1 A Python interface to the PAM library
ii  python-pexpect            2.3-1build1               Python module for automating interactive applications
ii  python-pkg-resources      0.6.10-4ubuntu1           Package Discovery and Resource Access using pkg_resources
ii  python-problem-report     1.13.3-0ubuntu2.1         Python library to handle problem reports
ii  python-pycurl             7.19.0-3                  Python bindings to libcurl
ii  python-serial             2.3-1                     pyserial - module encapsulating access for the serial port
ii  python-simplejson         2.0.9-1build1             Simple, fast, extensible JSON encoder/decoder for Python
ii  python-smartpm            1.2-5ubuntu0.2            Python library of the Smart Package Manager
ii  python-support            1.0.4ubuntu1              automated rebuilding support for Python modules
ii  python-twisted-bin        10.0.0-2ubuntu2           Event-based framework for internet applications
ii  python-twisted-core       10.0.0-2ubuntu2           Event-based framework for internet applications
ii  python-wadllib            1.1.4-1ubuntu1.1          Python library for navigating WADL files
ii  python-zope.interface     3.5.3-1ubuntu2            Interfaces for Python
ii  python2.6                 2.6.5-1ubuntu6            An interactive high-level object-oriented language (version 2.6)
ii  python2.6-minimal         2.6.5-1ubuntu6            A minimal subset of the Python language (version 2.6)
ii  readline-common           6.1-1                     GNU readline and history libraries, common files
ii  rsync                     3.0.7-1ubuntu1.1          fast remote file copy program (like rcp)
ii  rsyslog                   4.2.0-2ubuntu8.1          enhanced multi-threaded syslogd
ii  screen                    4.0.3-14ubuntu1.2         terminal multiplexor with VT100/ANSI terminal emulation
ii  sed                       4.2.1-6                   The GNU sed stream editor
ii  sensible-utils            0.0.1ubuntu3              Utilities for sensible alternative selection
ii  sgml-base                 1.26                      SGML infrastructure and SGML catalog file support
ii  sqlite3                   3.6.22-1                  A command line interface for SQLite 3
ii  strace                    4.5.19-2                  A system call tracer
ii  sudo                      1.7.2p1-1ubuntu5.4        Provide limited super user privileges to specific users
ii  sysstat                   9.0.6-2                   system performance tools for Linux
ii  sysv-rc                   2.87dsf-4ubuntu17.5       System-V-like runlevel change mechanism
ii  sysvinit-utils            2.87dsf-4ubuntu17.5       System-V-like utilities
ii  tar                       1.22-2ubuntu1             GNU version of the tar archiving utility
ii  tasksel                   2.73ubuntu26              Tool for selecting tasks for installation on Debian systems
ii  tasksel-data              2.73ubuntu26              Official tasks used for installation of Debian systems
ii  tcpd                      7.6.q-18                  Wietse Venema's TCP wrapper utilities
ii  tcpdump                   4.0.0-6ubuntu3            A powerful tool for network monitoring and data acquisition
ii  telnet                    0.17-36build1             The telnet client
ii  time                      1.7-23build1              The GNU time program for measuring cpu resource usage
ii  traceroute                2.0.13-2                  Traces the route taken by packets over an IPv4/IPv6 network
ii  tzdata                    2012e-0ubuntu0.10.04      time zone and daylight-saving time data
ii  ubuntu-keyring            2010.11.09                GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal            1.197                     Minimal core of Ubuntu
ii  ubuntu-serverguide        10.04.3                   The Ubuntu Server Guide
ii  ubuntu-standard           1.197                     The Ubuntu standard system
ii  ucf                       3.0025                    Update Configuration File: preserve user changes to config files.
ii  udev                      151-12.3                  rule-based device node and kernel event manager
ii  ufw                       0.30pre1-0ubuntu2         program for managing a Netfilter firewall
ii  update-manager-core       1:0.134.12.1              manage release upgrades
ii  update-notifier-common    0.99.3ubuntu0.1           Files shared between update-notifier and adept
ii  upstart                   0.6.5-8                   event-based init daemon
ii  ureadahead                0.100.0-4.1.3             Read required files in advance
ii  usbutils                  0.86-2ubuntu1             Linux USB utilities
ii  util-linux                2.17.2-0ubuntu1.10.04.2   Miscellaneous system utilities
ii  uuid-runtime              2.17.2-0ubuntu1.10.04.2   runtime components for the Universally Unique ID library
ii  vim                       2:7.2.330-1ubuntu3        Vi IMproved - enhanced vi editor
ii  vim-common                2:7.2.330-1ubuntu3        Vi IMproved - Common files
ii  vim-runtime               2:7.2.330-1ubuntu3        Vi IMproved - Runtime files
ii  vim-tiny                  2:7.2.330-1ubuntu3        Vi IMproved - enhanced vi editor - compact version
ii  w3m                       0.5.2-2.1ubuntu1.2        WWW browsable pager with excellent tables/frames support
ii  wget                      1.12-1.1ubuntu2.1         retrieves files from the web
ii  whiptail                  0.52.10-5ubuntu1          Displays user-friendly dialog boxes from shell scripts
ii  wireless-crda             1.12                      Wireless Central Regulatory Domain Agent
ii  wireless-tools            30~pre9-3ubuntu4          Tools for manipulating Linux Wireless Extensions
ii  wpasupplicant             0.6.9-3ubuntu3.1          client support for WPA and WPA2 (IEEE 802.11i)
ii  xauth                     1:1.0.4-1                 X authentication utility
ii  xkb-data                  1.8-1ubuntu8.1~10.04.1    X Keyboard Extension (XKB) configuration data
ii  xml-core                  0.13                      XML infrastructure and XML catalog file support
ii  zimbra-apache             7.2.1_GA_2790.UBUNTU10_64 Best email money can buy
ii  zimbra-core               7.2.1_GA_2790.UBUNTU10_64 Best email money can buy
ii  zimbra-ldap               7.2.1_GA_2790.UBUNTU10_64 Best email money can buy
ii  zimbra-logger             7.2.1_GA_2790.UBUNTU10_64 Best email money can buy
ii  zimbra-mta                7.2.1_GA_2790.UBUNTU10_64 Best email money can buy
ii  zimbra-snmp               7.2.1_GA_2790.UBUNTU10_64 Best email money can buy
ii  zimbra-spell              7.2.1_GA_2790.UBUNTU10_64 Best email money can buy
ii  zimbra-store              7.2.1_GA_2790.UBUNTU10_64 Best email money can buy
ii  zlib1g                    1:1.2.3.3.dfsg-15ubuntu1  compression library - runtime

```



someone have an idea to resolve this problem?
for the moment I'm searching the solution...
tks!

---

### Post by CharlesA on 2012-10-25
Try a different mirror.

---

### Post by chonybmx on 2012-10-25
> **CharlesA said:**
> Try a different mirror.

Hi, 
change different mirros but none work, install another server, and "copy paste" the mirrors, but neither works. that can not be...
tnks

---

### Post by chonybmx on 2012-11-14
Okay, install ubuntu server 12.04LTS and could reproduce the problem.
Once installed ubuntu server upgrade using "aptitude update && aptitude upgrade"
then the system needs to reboot and restart does not check for updates or check the wget
but
if I use "apt-get update && apt-get upgrade" I have this problem.

2 times the ubuntu install, check using "aptitude" and another installation using "apt-get"

with aptitude the system is broken and does not check updates, also tried changing the sources list no satisfactory results
the problem is when I use "aptitude"

What is the difference between "apt-get" and "aptitude"?
What could be the cuasa not check that the sources?

---

### Post by CharlesA on 2012-11-14
They are both frontends to dpkg, so there shouldn't be any difference outside of apt having super cow powers.. 

Maybe you should ask your ISP to check your line?

---

### Post by chonybmx on 2012-11-14
[B][SIZE="4"]newly installed ubuntu server
[/SIZE][/B]



```
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Wed Nov 14 12:01:15 ART 2012

  System load:  0.18               Processes:           76
  Usage of /:   2.5% of 155.79GB   Users logged in:     1
  Memory usage: 3%                 IP address for eth0: 192.168.1.12
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

[B]61 packages can be updated.
27 updates are security updates.[/B]

Last login: Wed Nov 14 12:00:25 2012 from 192.168.1.106
```

```
root@zimbra:~# **apt-get update**

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [54.6 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [187 kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [15.8 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,392 B]          
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [196 kB]          
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [4,419 B]         
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [61.6 kB]        
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]            
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [426 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]    
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [54.7 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,189 B]       
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [201 kB]   
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [8,366 B]                                     
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [153 kB]                                        
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,677 B]                                     
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [433 kB]                                             
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]                                       
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [54.9 kB]                                         
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,388 B]                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                                   
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [8,374 B]                                      
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [153 kB]                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                                                     
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,661 B]                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                  
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]                                                
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                             
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [17.7 kB]                                            
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]                                          
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]                                         
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]                                      
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [16.2 kB]                                     
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,489 B]                                   
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]                                          
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                       
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [16.2 kB]                                      
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                                                  
Fetched 2,264 kB in 8s (265 kB/s)                                                                                           
Reading package lists... Done
```

```
root@zimbra:~# **apt-get update && apt-get upgrade**

Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  accountsservice apparmor apport apport-symptoms apt apt-transport-https apt-utils aptitude base-files bind9-host
  coreutils dbus dnsutils gnupg gpgv isc-dhcp-client isc-dhcp-common landscape-common libaccountsservice0 libapt-inst1.4
  libapt-pkg4.12 libbind9-80 libc-bin libc6 libdbus-1-3 libdns81 libgc1c2 libisc83 libisccc80 libisccfg82 libldap-2.4-2
  liblwres80 libparted0debian1 libssl1.0.0 libudev0 libxcb1 libxml2 linux-firmware login lsb-base lsb-release
  multiarch-support ntfs-3g openssl parted passwd python-apport python-problem-report resolvconf tzdata ubuntu-keyring udev
  update-manager-core update-notifier-common wpasupplicant
55 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 46.7 MB of archives.
After this operation, 601 kB of additional disk space will be used.

Do you want to continue [Y/n]? ** Y**


Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main base-files amd64 6.5ubuntu6.4 [69.9 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main coreutils amd64 8.13-3ubuntu3.1 [2,216 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main login amd64 1:4.1.4.2+svn3283-3ubuntu5.1 [291 kB]           
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main tzdata all 2012e-0ubuntu0.12.04.1 [474 kB]                  
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libc-bin amd64 2.15-0ubuntu10.3 [1,181 kB]                  
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libc6 amd64 2.15-0ubuntu10.3 [4,653 kB]                     
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libapt-pkg4.12 amd64 0.8.16~exp12ubuntu10.5 [939 kB]        
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main ubuntu-keyring all 2011.11.21.1 [16.7 kB]                   
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main gpgv amd64 1.4.11-3ubuntu2.1 [185 kB]                       
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main gnupg amd64 1.4.11-3ubuntu2.1 [808 kB]                     
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main apt amd64 0.8.16~exp12ubuntu10.5 [1,100 kB]                
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libssl1.0.0 amd64 1.0.1-4ubuntu5.5 [1,011 kB]              
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libapt-inst1.4 amd64 0.8.16~exp12ubuntu10.5 [99.8 kB]      
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main lsb-base all 4.0-0ubuntu20.2 [10.4 kB]                     
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main resolvconf all 1.63ubuntu16 [53.5 kB]                      
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libdbus-1-3 amd64 1.4.18-1ubuntu1.3 [145 kB]               
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libudev0 amd64 175-0ubuntu9.2 [29.2 kB]                    
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main apparmor amd64 2.7.102-0ubuntu3.4 [357 kB]                 
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libldap-2.4-2 amd64 2.4.28-1.1ubuntu4.2 [186 kB]           
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libparted0debian1 amd64 2.3-8ubuntu5.1 [240 kB]            
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libxcb1 amd64 1.8.1-1ubuntu0.1 [44.8 kB]                   
Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libxml2 amd64 2.7.8.dfsg-5.1ubuntu4.2 [673 kB]             
Get:23 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main ntfs-3g amd64 1:2012.1.15AR.1-1ubuntu1.2 [608 kB]          
Get:24 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main update-notifier-common all 0.119ubuntu8.6 [222 kB]         
Get:25 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main multiarch-support amd64 2.15-0ubuntu10.3 [4,480 B]         
Get:26 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main passwd amd64 1:4.1.4.2+svn3283-3ubuntu5.1 [959 kB]         
Get:27 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main apt-utils amd64 0.8.16~exp12ubuntu10.5 [190 kB]            
Get:28 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main isc-dhcp-client amd64 4.1.ESV-R4-0ubuntu5.5 [289 kB]       
Get:29 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main isc-dhcp-common amd64 4.1.ESV-R4-0ubuntu5.5 [347 kB]       
Get:30 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main lsb-release all 4.0-0ubuntu20.2 [10.8 kB]                  
Get:31 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main udev amd64 175-0ubuntu9.2 [323 kB]                         
Get:32 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main accountsservice amd64 0.6.15-2ubuntu9.4 [44.1 kB]          
Get:33 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libaccountsservice0 amd64 0.6.15-2ubuntu9.4 [30.0 kB]      
Get:34 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main dbus amd64 1.4.18-1ubuntu1.3 [358 kB]                      
Get:35 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main apt-transport-https amd64 0.8.16~exp12ubuntu10.5 [16.3 kB] 
Get:36 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main bind9-host amd64 1:9.8.1.dfsg.P1-4ubuntu0.4 [55.4 kB]      
Get:37 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main dnsutils amd64 1:9.8.1.dfsg.P1-4ubuntu0.4 [148 kB]         
Get:38 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libisc83 amd64 1:9.8.1.dfsg.P1-4ubuntu0.4 [162 kB]         
Get:39 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libdns81 amd64 1:9.8.1.dfsg.P1-4ubuntu0.4 [705 kB]         
Get:40 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libisccc80 amd64 1:9.8.1.dfsg.P1-4ubuntu0.4 [17.6 kB]      
Get:41 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libisccfg82 amd64 1:9.8.1.dfsg.P1-4ubuntu0.4 [43.4 kB]     
Get:42 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main liblwres80 amd64 1:9.8.1.dfsg.P1-4ubuntu0.4 [38.3 kB]      
Get:43 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libbind9-80 amd64 1:9.8.1.dfsg.P1-4ubuntu0.4 [24.3 kB]     
Get:44 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main openssl amd64 1.0.1-4ubuntu5.5 [523 kB]                    
Get:45 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main parted amd64 2.3-8ubuntu5.1 [52.4 kB]                      
Get:46 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main update-manager-core amd64 1:0.156.14.11 [182 kB]           
Get:47 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main python-problem-report all 2.0.1-0ubuntu15 [9,796 B]        
Get:48 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main python-apport all 2.0.1-0ubuntu15 [79.7 kB]                
Get:49 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main apport all 2.0.1-0ubuntu15 [145 kB]                        
Get:50 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main apport-symptoms all 0.16.1 [14.2 kB]                       
Get:51 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main aptitude amd64 0.6.6-1ubuntu1.1 [2,373 kB]                 
Get:52 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main landscape-common amd64 12.05-0ubuntu1.12.04 [242 kB]       
Get:53 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgc1c2 amd64 1:7.1-8ubuntu0.12.04.1 [79.5 kB]            
Get:54 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-firmware all 1.79.1 [23.1 MB]                        
Get:55 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main wpasupplicant amd64 0.7.3-6ubuntu2.1 [490 kB]              
Fetched 46.7 MB in 2min 31s (308 kB/s)                                                                                      
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 48742 files and directories currently installed.)
Preparing to replace base-files 6.5ubuntu6.2 (using .../base-files_6.5ubuntu6.4_amd64.deb) ...
Unpacking replacement base-files ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
Setting up base-files (6.5ubuntu6.4) ...
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace coreutils 8.13-3ubuntu3 (using .../coreutils_8.13-3ubuntu3.1_amd64.deb) ...
Unpacking replacement coreutils ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up coreutils (8.13-3ubuntu3.1) ...
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace login 1:4.1.4.2+svn3283-3ubuntu5 (using .../login_1%3a4.1.4.2+svn3283-3ubuntu5.1_amd64.deb) ...
Unpacking replacement login ...
Processing triggers for man-db ...
Setting up login (1:4.1.4.2+svn3283-3ubuntu5.1) ...
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace tzdata 2012e-0ubuntu0.12.04 (using .../tzdata_2012e-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2012e-0ubuntu0.12.04.1) ...

Current default time zone: 'America/Argentina/Buenos_Aires'
Local time is now:      Wed Nov 14 12:03:24 ART 2012.
Universal Time is now:  Wed Nov 14 15:03:24 UTC 2012.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 48743 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10 (using .../libc-bin_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.15-0ubuntu10.3) ...
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.15-0ubuntu10.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.2 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.5_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace ubuntu-keyring 2011.11.21 (using .../ubuntu-keyring_2011.11.21.1_all.deb) ...
Unpacking replacement ubuntu-keyring ...
Setting up ubuntu-keyring (2011.11.21.1) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: public key "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" imported
gpg: key EFE21092: public key "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" imported
gpg: Total number processed: 4
gpg:               imported: 2  (RSA: 2)
gpg:              unchanged: 2
gpg: no ultimately trusted keys found
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace gpgv 1.4.11-3ubuntu2 (using .../gpgv_1.4.11-3ubuntu2.1_amd64.deb) ...
Unpacking replacement gpgv ...
Processing triggers for man-db ...
Setting up gpgv (1.4.11-3ubuntu2.1) ...
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace gnupg 1.4.11-3ubuntu2 (using .../gnupg_1.4.11-3ubuntu2.1_amd64.deb) ...
Unpacking replacement gnupg ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up gnupg (1.4.11-3ubuntu2.1) ...
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.2 (using .../apt_0.8.16~exp12ubuntu10.5_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp12ubuntu10.5) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace libssl1.0.0 1.0.1-4ubuntu5.3 (using .../libssl1.0.0_1.0.1-4ubuntu5.5_amd64.deb) ...
Unpacking replacement libssl1.0.0 ...
Setting up libssl1.0.0 (1.0.1-4ubuntu5.5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10.2 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.5_amd64.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace lsb-base 4.0-0ubuntu20 (using .../lsb-base_4.0-0ubuntu20.2_all.deb) ...
Unpacking replacement lsb-base ...
Setting up lsb-base (4.0-0ubuntu20.2) ...
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace resolvconf 1.63ubuntu15 (using .../resolvconf_1.63ubuntu16_all.deb) ...
Unpacking replacement resolvconf ...
Preparing to replace libdbus-1-3 1.4.18-1ubuntu1 (using .../libdbus-1-3_1.4.18-1ubuntu1.3_amd64.deb) ...
Unpacking replacement libdbus-1-3 ...
Preparing to replace libudev0 175-0ubuntu9.1 (using .../libudev0_175-0ubuntu9.2_amd64.deb) ...
Unpacking replacement libudev0 ...
Preparing to replace apparmor 2.7.102-0ubuntu3.1 (using .../apparmor_2.7.102-0ubuntu3.4_amd64.deb) ...
Unpacking replacement apparmor ...
Preparing to replace libldap-2.4-2 2.4.28-1.1ubuntu4.1 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.2_amd64.deb) ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace libparted0debian1 2.3-8ubuntu5 (using .../libparted0debian1_2.3-8ubuntu5.1_amd64.deb) ...
Unpacking replacement libparted0debian1 ...
Preparing to replace libxcb1 1.8.1-1 (using .../libxcb1_1.8.1-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libxcb1 ...
Preparing to replace libxml2 2.7.8.dfsg-5.1ubuntu4.1 (using .../libxml2_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb) ...
Unpacking replacement libxml2 ...
Preparing to replace ntfs-3g 1:2012.1.15AR.1-1ubuntu1 (using .../ntfs-3g_1%3a2012.1.15AR.1-1ubuntu1.2_amd64.deb) ...
Unpacking replacement ntfs-3g ...
Preparing to replace update-notifier-common 0.119ubuntu8.5 (using .../update-notifier-common_0.119ubuntu8.6_all.deb) ...
Unpacking replacement update-notifier-common ...
Preparing to replace multiarch-support 2.15-0ubuntu10 (using .../multiarch-support_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement multiarch-support ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
Setting up multiarch-support (2.15-0ubuntu10.3) ...
(Reading database ... 48743 files and directories currently installed.)
Preparing to replace passwd 1:4.1.4.2+svn3283-3ubuntu5 (using .../passwd_1%3a4.1.4.2+svn3283-3ubuntu5.1_amd64.deb) ...
Unpacking replacement passwd ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up passwd (1:4.1.4.2+svn3283-3ubuntu5.1) ...
(Reading database ... 48745 files and directories currently installed.)
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.2 (using .../apt-utils_0.8.16~exp12ubuntu10.5_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace isc-dhcp-client 4.1.ESV-R4-0ubuntu5.2 (using .../isc-dhcp-client_4.1.ESV-R4-0ubuntu5.5_amd64.deb) ...
Unpacking replacement isc-dhcp-client ...
Preparing to replace isc-dhcp-common 4.1.ESV-R4-0ubuntu5.2 (using .../isc-dhcp-common_4.1.ESV-R4-0ubuntu5.5_amd64.deb) ...
Unpacking replacement isc-dhcp-common ...
Preparing to replace lsb-release 4.0-0ubuntu20 (using .../lsb-release_4.0-0ubuntu20.2_all.deb) ...
Unpacking replacement lsb-release ...
Preparing to replace udev 175-0ubuntu9.1 (using .../udev_175-0ubuntu9.2_amd64.deb) ...
Adding 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Preparing to replace accountsservice 0.6.15-2ubuntu9.3 (using .../accountsservice_0.6.15-2ubuntu9.4_amd64.deb) ...
Unpacking replacement accountsservice ...
Preparing to replace libaccountsservice0 0.6.15-2ubuntu9.3 (using .../libaccountsservice0_0.6.15-2ubuntu9.4_amd64.deb) ...
Unpacking replacement libaccountsservice0 ...
Preparing to replace dbus 1.4.18-1ubuntu1 (using .../dbus_1.4.18-1ubuntu1.3_amd64.deb) ...
Unpacking replacement dbus ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.2 (using .../apt-transport-https_0.8.16~exp12ubuntu10.5_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace bind9-host 1:9.8.1.dfsg.P1-4ubuntu0.2 (using .../bind9-host_1%3a9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) ...
Unpacking replacement bind9-host ...
Preparing to replace dnsutils 1:9.8.1.dfsg.P1-4ubuntu0.2 (using .../dnsutils_1%3a9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) ...
Unpacking replacement dnsutils ...
Preparing to replace libisc83 1:9.8.1.dfsg.P1-4ubuntu0.2 (using .../libisc83_1%3a9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) ...
Unpacking replacement libisc83 ...
Preparing to replace libdns81 1:9.8.1.dfsg.P1-4ubuntu0.2 (using .../libdns81_1%3a9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) ...
Unpacking replacement libdns81 ...
Preparing to replace libisccc80 1:9.8.1.dfsg.P1-4ubuntu0.2 (using .../libisccc80_1%3a9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) ...
Unpacking replacement libisccc80 ...
Preparing to replace libisccfg82 1:9.8.1.dfsg.P1-4ubuntu0.2 (using .../libisccfg82_1%3a9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) ...
Unpacking replacement libisccfg82 ...
Preparing to replace liblwres80 1:9.8.1.dfsg.P1-4ubuntu0.2 (using .../liblwres80_1%3a9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) ...
Unpacking replacement liblwres80 ...
Preparing to replace libbind9-80 1:9.8.1.dfsg.P1-4ubuntu0.2 (using .../libbind9-80_1%3a9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) ...
Unpacking replacement libbind9-80 ...
Preparing to replace openssl 1.0.1-4ubuntu5.3 (using .../openssl_1.0.1-4ubuntu5.5_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace parted 2.3-8ubuntu5 (using .../parted_2.3-8ubuntu5.1_amd64.deb) ...
Unpacking replacement parted ...
Preparing to replace update-manager-core 1:0.156.14.9 (using .../update-manager-core_1%3a0.156.14.11_amd64.deb) ...
Unpacking replacement update-manager-core ...
Preparing to replace python-problem-report 2.0.1-0ubuntu12 (using .../python-problem-report_2.0.1-0ubuntu15_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport 2.0.1-0ubuntu12 (using .../python-apport_2.0.1-0ubuntu15_all.deb) ...
Unpacking replacement python-apport ...
Preparing to replace apport 2.0.1-0ubuntu12 (using .../apport_2.0.1-0ubuntu15_all.deb) ...
apport stop/waiting
Unpacking replacement apport ...
Preparing to replace apport-symptoms 0.16 (using .../apport-symptoms_0.16.1_all.deb) ...
Unpacking replacement apport-symptoms ...
Preparing to replace aptitude 0.6.6-1ubuntu1 (using .../aptitude_0.6.6-1ubuntu1.1_amd64.deb) ...
Unpacking replacement aptitude ...
Preparing to replace landscape-common 12.05-0ubuntu0.12.04 (using .../landscape-common_12.05-0ubuntu1.12.04_amd64.deb) ...
Unpacking replacement landscape-common ...
Preparing to replace libgc1c2 1:7.1-8build1 (using .../libgc1c2_1%3a7.1-8ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libgc1c2 ...
Preparing to replace linux-firmware 1.79 (using .../linux-firmware_1.79.1_all.deb) ...
Unpacking replacement linux-firmware ...
Preparing to replace wpasupplicant 0.7.3-6ubuntu2 (using .../wpasupplicant_0.7.3-6ubuntu2.1_amd64.deb) ...
Unpacking replacement wpasupplicant ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.5) ...
Setting up resolvconf (1.63ubuntu16) ...
Installing new version of config file /etc/ppp/ip-down.d/000resolvconf ...
Installing new version of config file /etc/ppp/ip-up.d/000resolvconf ...
Setting up libdbus-1-3 (1.4.18-1ubuntu1.3) ...
Setting up libudev0 (175-0ubuntu9.2) ...
Setting up apparmor (2.7.102-0ubuntu3.4) ...
Installing new version of config file /etc/apparmor.d/abstractions/nameservice ...
 * Starting AppArmor profiles                                                                                                Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                                                                      [ OK ]
 * Reloading AppArmor profiles                                                                                               Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                                                                      [ OK ]
Setting up libldap-2.4-2 (2.4.28-1.1ubuntu4.2) ...
Setting up libparted0debian1 (2.3-8ubuntu5.1) ...
Setting up libxcb1 (1.8.1-1ubuntu0.1) ...
Setting up libxml2 (2.7.8.dfsg-5.1ubuntu4.2) ...
Setting up ntfs-3g (1:2012.1.15AR.1-1ubuntu1.2) ...
update-initramfs: deferring update (trigger activated)
Setting up update-notifier-common (0.119ubuntu8.6) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.5) ...
Setting up isc-dhcp-common (4.1.ESV-R4-0ubuntu5.5) ...
Setting up isc-dhcp-client (4.1.ESV-R4-0ubuntu5.5) ...
Setting up lsb-release (4.0-0ubuntu20.2) ...
Setting up udev (175-0ubuntu9.2) ...
udev stop/waiting
udev start/running, process 18993
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up libaccountsservice0 (0.6.15-2ubuntu9.4) ...
Setting up dbus (1.4.18-1ubuntu1.3) ...
Setting up accountsservice (0.6.15-2ubuntu9.4) ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.5) ...
Setting up libisc83 (1:9.8.1.dfsg.P1-4ubuntu0.4) ...
Setting up libdns81 (1:9.8.1.dfsg.P1-4ubuntu0.4) ...
Setting up libisccc80 (1:9.8.1.dfsg.P1-4ubuntu0.4) ...
Setting up libisccfg82 (1:9.8.1.dfsg.P1-4ubuntu0.4) ...
Setting up libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.4) ...
Setting up liblwres80 (1:9.8.1.dfsg.P1-4ubuntu0.4) ...
Setting up bind9-host (1:9.8.1.dfsg.P1-4ubuntu0.4) ...
Setting up dnsutils (1:9.8.1.dfsg.P1-4ubuntu0.4) ...
Setting up openssl (1.0.1-4ubuntu5.5) ...
Setting up parted (2.3-8ubuntu5.1) ...
Setting up update-manager-core (1:0.156.14.11) ...
Setting up python-problem-report (2.0.1-0ubuntu15) ...
Setting up python-apport (2.0.1-0ubuntu15) ...
Setting up apport (2.0.1-0ubuntu15) ...
apport start/running
Setting up apport-symptoms (0.16.1) ...
Setting up aptitude (0.6.6-1ubuntu1.1) ...
Setting up landscape-common (12.05-0ubuntu1.12.04) ...
Setting up libgc1c2 (1:7.1-8ubuntu0.12.04.1) ...
Setting up linux-firmware (1.79.1) ...
Setting up wpasupplicant (0.7.3-6ubuntu2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for resolvconf ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
```

root@zimbra:~#  **reboot**








**[SIZE="4"]after restart[/SIZE]**




```
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Wed Nov 14 12:09:42 ART 2012

  System load:  1.82               Processes:           74
  Usage of /:   3.0% of 155.79GB   Users logged in:     0
  Memory usage: 0%                 IP address for eth0: 192.168.1.12
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Last login: Wed Nov 14 12:05:34 2012 from 192.168.1.106
root@zimbra:~# **apt-get update**
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done           
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
root@zimbra:~# 
root@zimbra:~#
```

---

### Post by chonybmx on 2012-11-14
I do not understand what the problem is, just update, reboot and then not work updates. Maybe it's the version change...
any ideas..??

---

### Post by CharlesA on 2012-11-14
[http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error](http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error)

See if you can ping something outside the local network from that machine - google.com or ubuntu.com or something like that.

Run this too:
```
ifconfig
```

---

### Post by chonybmx on 2012-11-15
here have copy paste of the test connectivity, I'm sure that not is a problem with connectivity or navigation,  this problem is when upgrade my version.
Go to check the link and re-test with my server.
Thanks!

root@zimbra:~# **ping [www.google.com.ar](www.google.com.ar)**
PING [www.google.com.ar](www.google.com.ar) (173.194.42.24) 56(84) bytes of data.
64 bytes from eze03s05-in-f24.1e100.net (173.194.42.24): icmp_seq=1 ttl=57 time=3.37 ms
64 bytes from eze03s05-in-f24.1e100.net (173.194.42.24): icmp_seq=2 ttl=57 time=2.02 ms
64 bytes from eze03s05-in-f24.1e100.net (173.194.42.24): icmp_seq=3 ttl=57 time=1.74 ms
64 bytes from eze03s05-in-f24.1e100.net (173.194.42.24): icmp_seq=4 ttl=57 time=1.94 ms
^C
--- [www.google.com.ar](www.google.com.ar) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 1.749/2.274/3.372/0.641 ms


root@zimbra:~#** ping 8.8.8.8**
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=29.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=28.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=28.8 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=57 time=29.0 ms
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 28.740/28.962/29.238/0.278 ms



root@zimbra:~# **ifconfig**
eth0      Link encap:Ethernet  direcciónHW 00:00:00:8b:75:f3  
          Direc. inet:192.168.1.28  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::000:00ff:fe8b:75f3/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:717134 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:874838 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:70533880 (70.5 MB)  TX bytes:771575740 (771.5 MB)


lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:1270748 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1270748 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:713305080 (713.3 MB)  TX bytes:713305080 (713.3 MB)



root@zimbra:~# **cat /etc/resolv.conf **
nameserver 192.168.1.14
nameserver 8.8.8.8
nameserver 8.8.4.4



root@zimbra:~# **cat /etc/hosts**
127.0.0.1	localhost
#127.0.1.1	zimbra

192.168.1.28 zimbra.midomain.gov.ar zimbra

# The following lines are desirable for IPv6 capable hosts
#::1     localhost ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters



root@zimbra:~# **traceroute [www.google.com.ar](www.google.com.ar)**
traceroute to [www.google.com.ar](www.google.com.ar) (173.194.42.23), 30 hops max, 60 byte packets
 1  192.168.1.50 (192.168.1.50)  1.548 ms  1.520 ms  1.484 ms
 2  190-16-53-1.static.impsat.net.ar (190.16.53.1)  137.966 ms  137.956 ms  137.931 ms
 3  64.208.27.34 (64.208.27.34)  2.026 ms  1.984 ms  1.974 ms
 4  209.85.251.86 (209.85.251.86)  1.950 ms  62.809 ms  62.817 ms
 5  209.85.251.194 (209.85.251.194)  2.549 ms  2.529 ms  2.665 ms
 6  eze03s05-in-f23.1e100.net (173.194.42.23)  2.087 ms  2.091 ms  2.070 ms
root@zimbra:~#

---

