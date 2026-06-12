---
title: "Ubuntu VPN server , windows client"
date: 2010-11-06
forum: Server Platforms
---

### Post by fzerorubigd on 2010-11-06
I have an ubuntu server and configured for VPN server base on this guide : [http://www.ewdisonthen.com/how-to-setup-pptp-vpn-server-on-linux-tutorial-07577.php](http://www.ewdisonthen.com/how-to-setup-pptp-vpn-server-on-linux-tutorial-07577.php)

Then , I can simply connect to this server from an ArchLinux or Ubuntu desktop and ANY THING is ok.

but from windows client, I can connect to server and I can see many sites (for example facebook, Its not available in my country-Iran-, and I use VPN to access to this site) this site are not normally available without vpn.

But the problem is I can not see some other site only in windows client, not even ping to them.
  they are simply available from my Arch linux or ubuntu desktop. 

I think its DNS problem, so I change the DNS (in windows client setting and/or in  /etc/ppp/options file in server, first in server, then in client and at the end in both) I use google DNS , OpenDNS and 4.2.2.4 But no change. 
I check windows XP, Vista and Seven, ( linux clients : ubuntu , archlinux)

Server is Lucid (10.04)

---

### Post by Irregular Joe on 2010-11-06
Some sites block or discard pings as a security measure.  Some home routers also let you do this (it was a default on mine).  So, when I am on a remote server, I am unable to ping my server, however I can still connect to the web server it just fine.

If you can still access the services at that site (http, etc.), this would be the reason.

Hope this helps!

---

### Post by fzerorubigd on 2010-11-07
The problem is , I can not access this sites (any type of server for example http , https ) JUST in windows client. But in the same time with linux client , I can access that sites. (Same vpn server , same settings even same user and password for vpn)

---

### Post by abix_adam_pl on 2010-11-07
Do a test - from Linux and Windows make : ping and tracepath/traecrt the page, which you can see from both and the page, which you cannot see on windows. Then post here your effects - shoud looks like:

1. Ping from Linux:
```

adasiek@sea-star:~$ ping -c3 -w3 www.facebook.com
PING www.facebook.com (66.220.153.19) 56(84) bytes of data.
64 bytes from www-12-03-ash2.facebook.com (66.220.153.19): icmp_seq=1 ttl=241 time=122 ms
64 bytes from www-12-03-ash2.facebook.com (66.220.153.19): icmp_seq=2 ttl=241 time=121 ms
64 bytes from www-12-03-ash2.facebook.com (66.220.153.19): icmp_seq=3 ttl=241 time=121 ms

--- www.facebook.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 121.208/121.690/122.506/0.705 ms
adasiek@sea-star:~$ 

```From Windows:

```
Microsoft Windows XP [Wersja 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\adasiek>ping www.facebook.com

Badanie www.facebook.com [69.63.190.18] z u&#380;yciem 32 bajtów danych:

Odpowied&#378; z 69.63.190.18: bajtów=32 czas=128ms TTL=240
Odpowied&#378; z 69.63.190.18: bajtów=32 czas=119ms TTL=240
Odpowied&#378; z 69.63.190.18: bajtów=32 czas=132ms TTL=240
Odpowied&#378; z 69.63.190.18: bajtów=32 czas=123ms TTL=240

Statystyka badania ping dla 69.63.190.18:
    Pakiety: Wys&#322;ane = 4, Odebrane = 4, Utracone = 0 (0% straty),
Szacunkowy czas b&#322;&#261;dzenia pakietów w millisekundach:
    Minimum = 119 ms, Maksimum = 132 ms, Czas &#347;redni = 125 ms

C:\Documents and Settings\adasiek>

```Also post here ipconfig from Windows - like:
```

C:\Documents and Settings\adasiek>ipconfig
Konfiguracja IP systemu Windows
Karta Ethernet Po&#322;&#261;czenie lokalne:
        Sufiks DNS konkretnego po&#322;&#261;czenia :
        Adres IP. . . . . . . . . . . . . : 192.168.2.10
        Maska podsieci. . . . . . . . . . : 255.255.255.0
        Brama domy&#347;lna. . . . . . . . . . : 192.168.2.1
C:\Documents and Settings\adasiek>
```Traceroute from windows:

```
C:\Documents and Settings\adasiek>tracert -d www.facebook.com

Trasa &#347;ledzenia do www.facebook.com [69.63.190.18]
przewy&#380;sza maksymaln&#261; liczb&#281; przeskoków 30

  1     2 ms    <1 ms    <1 ms  192.168.2.1
  2     *        *        *     Up&#322;yn&#261;&#322; limit czasu &#380;&#261;dania.
  3     5 ms    13 ms     6 ms  89.75.2.161
  4    20 ms    47 ms    25 ms  84.116.252.125
  5    31 ms    36 ms    28 ms  84.116.252.113
  6     *       28 ms     *     84.116.252.101
  7     *        *       39 ms  84.116.252.205
  8    58 ms    37 ms    21 ms  84.116.132.129
  9    23 ms    41 ms    46 ms  84.116.132.170
 10    31 ms    46 ms    31 ms  80.81.194.40
 11   126 ms   127 ms   128 ms  204.15.20.221
 12   119 ms   121 ms   139 ms  74.119.78.85
 13   123 ms   118 ms   125 ms  74.119.77.53
 14   117 ms   130 ms   121 ms  69.63.190.18

&#346;ledzenie zako&#324;czone.
```Then we can see

---

### Post by fzerorubigd on 2010-11-07
Now I found the problem :( 
But no solution . 
Its because of Iran's censor ship . (some time I hate myself, my .... whatever .)
Now , I want to know exact difference between Linux pptp client settings and Windows client settings (may be its not a correct forum but just in case some one know some thing ) 

I attach my settings screen shot in my linux box , hopefully some one can help me to exactly create same connection on windows client.

Thanks and sorry if this is not a correct place.

---

### Post by ubun_user on 2011-06-13
Hi,

I have a similar problem. I have set up a pptp server on Ubuntu at home, when I connect to it using another ubuntu machine everything works fine. When I use windows I can connect, ping IPs and ping names but can not browse internet. Oddly, all google related sites work! I tried several machines and installed a Cisco vpn client on one of them which fixed it. When I compare two machines everything looks the same. The only difference I noticed is that when I run ipconfig /displaydns for the failing machine I see a long IP v 6 address 
1.0.0.0.0.0.0.0.0 ......IP6.arpa

I installed the cisco client on another machine but it didnot fix the problem on that one. 

My internet has no restrictions and everything works just fine with ubuntu clients and that fixed windows 7 one.

---

### Post by ubun_user on 2011-06-15
I managed to solve the problem by adding this filter rule to the server side. 

sudo iptables -I FORWARD -p tcp --syn -i ppp+ -j TCPMSS --set-mss 1356

you can run it from  terminal or put it in /etc/rc.local without 'sudo' so that it will be added after each restart. Now everything is working just fine.

---

