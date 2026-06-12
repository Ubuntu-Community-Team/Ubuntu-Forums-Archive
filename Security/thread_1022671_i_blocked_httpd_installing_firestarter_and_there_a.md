---
title: "i blocked httpd installing firestarter and there are many lines in syslog"
date: 2008-12-27
forum: Security
---

### Post by q.dinar on 2008-12-27
hello.
i have installed firestarter.

and then have seen this problem: syslog is filled with many lines like
Dec 27 07:40:52 qdb-desktop kernel: [40234.610521] Inbound IN=ppp0 OUT= MAC= SRC=66.249.70.212 DST=89.232.85.48 LEN=60 TOS=0x00 PREC=0x20 TTL=46 ID=28685 DF PROTO=TCP SPT=36690 DPT=80 WINDOW=5720 RES=0x00 SYN URGP=0
and this difference:
firewall check service in the internet showed all ports stealth.
and today when i opened the site from my computer it is refusing connection. (but it worked yesterday, may be started to refuce after i restarted connection today.)
i added rule in firestarter:
policy tab > inbound > allow service http for everyone. then clicked apply policy. but that does not work.
also i learned and tried some iptables commands. i see that i can flush rules and that is applied immediately. sites begin do not open.
poff and pon causes loading old rules with sites opening and my server is refucing.
also making outbound policy restrictive by default in firestarter and appliing starts to work instantly. and i can allow them back. opening sites by me. but i cannot allow site from my computer.

i tried some commands from [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) :
sudo iptables -F
then
$ sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$ sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

but this is not allowing my computer's 80th port (also by ip address). and also blocks opening sites by me as i remember, i think may be because dns is not allowed. however i did not refuced them also.

then i restart connection and then i can open sites.

please help me. i need to allow 80th port from outward and also of localhost and 6667 port at least of localhost (because it is for "cgiirc") and better also from outward, and smtp (25?) from outward and also of localhost, and 143 (imap) of localhost.

as i see there is no ufw here. this linux is ubuntu 7.10 .

must i edit /etc/network/interfaces to write line to load saved rules on every connection if i will use iptables?

would you recommend to use shorewall?

does shorewall convert its configs to iptables commands or does it work directly?

---

### Post by q.dinar on 2008-12-27
and now i can open sites so some asking dns form my computer is allowed i think, i need that leave.
the site that goes out from my computer use free dns service, so i do not need allow "bind" that is on my computer i think.

---

### Post by q.dinar on 2008-12-27
i use adsl modem. pppoe. this is difference from that how-to. so may be i should write iptables commands other way.

i have also one related problem. even before i installed firestarter i could no connect to my modem. i have remembered that, have known out its ip and tried but cannot, but once i connected to it when used windows.

one strange thing: yesterday when i checked with ports checking service they all (first near 1000) was stealth but i could connect to site on 80 port of my computer.

---

### Post by q.dinar on 2008-12-27
hello.
please help.
if nobody answer please explain why.

---

### Post by The Cog on 2008-12-27
Firstly, you are likely to have problems if you try to configure your firewall with both firestarter and iptables. Firestarter is just a GUI front end for configuring iptables, and it will keep undoing any manual changes you make. You are probably better off using just one method to configure iptables. Either just use firestarter, or just use iptables commands in a script. 

Secondly, I am not clear what your problem is. Are you having trouble visiting other web sites (outgoing connections), or are you running a web server on your own PC and visitors are having trouble connecting (incoming connectinons)?

---

### Post by q.dinar on 2008-12-28
incoming.

but i am going to do fresh installation.

---

### Post by cariboo on 2008-12-28
Why do a fresh install, when you can fix your problem in less time than the install takes.

I would suggest uninstalling firestarter using the following command:

```
sudo apt-get purge firestarter
```

then use the following commands to purge the iptables rules:

```
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -t mangle -F
sudo iptables -X


```

Then use gufw, which is the preferred firewall gui.

It is always easier  to fix a problem then it is to reinstall.

Jim

---

### Post by q.dinar on 2008-12-29
hello
i reinstall because my site was not opening long time and i think so this time i will reinstall because i wanted to reinstall long time but did not want to do because that is long to configure all services again. i wanted that because i think my computer is hacked.

i have found one idea and then other. first i changed in flushed iptables DROP policies to ACCEPT, but my site was not still opening, then i thinked that apache is not running, and checked, indeed, it is not running. i started it and it works.

---

### Post by q.dinar on 2008-12-29
my modem is "zte zxdsl 831 series". i try to open it this way:
[http://smartinfo.com.my/IT/PC_Hardware/TM_Net_Streamyx_ZTE_ZXDXL_831_Modem.htm](http://smartinfo.com.my/IT/PC_Hardware/TM_Net_Streamyx_ZTE_ZXDXL_831_Modem.htm)
but [http://192.168.1.1](http://192.168.1.1) is not opening.

can i make some configuration of modem for security?

i see in that page that i can select dns server.
i remembered one problem: once dns server of my provider was not working and i could not open sites. is there free dn servers to help people in that case? i found out where i can write dns servers: /etc/resolve.conf as i remember. but this is better to write in new topic. but i first will search and ask in my provider's forum i think.

and one more question:
i have heard-read about mac addresses. can i check and remember, write to a paper my ethernet device mac address and then check with it whether my that device is replaced with other? or is that address written with flash technology and can be changed? does my modem has that address?

---

### Post by cariboo on 2008-12-29
IF you can't open the management page on your modem, do as the page you linked to suggests and reset the modem

> i see in that page that i can select dns server.
i remembered one problem: once dns server of my provider was not working and i could not open sites. is there free dn servers to help people in that case? i found out where i can write dns servers: /etc/resolve.conf as i remember. but this is better to write in new topic. but i first will search and ask in my provider's forum i think.


You can use [Opendns]("http:///www.opendns.com/"), it is a free dns service.

> i have heard-read about mac addresses. can i check and remember, write to a paper my ethernet device mac address and then check with it whether my that device is replaced with other? or is that address written with flash technology and can be changed? does my modem has that address?

The easiest way to find the MAC address of your network adapter, is to type in a terminal:

```
ifconfig
```

You should get a result similar to this:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr **00:16:17:9c:84:b5**  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe9c:84b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:667343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:815311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:297750633 (297.7 MB)  TX bytes:384791313 (384.7 MB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98670 (98.6 KB)  TX bytes:98670 (98.6 KB)
```

In the above example, I highlighted the MAC address.

Your modem will also have a MAC address, you should be able to see what it is once you are able to access the management interface.

Jim

---

### Post by q.dinar on 2008-12-31
hello.
now i have installed new ubuntu 8.10 cd.

i have configured iptables.

now

sudo iptables-save -c

says:

# Generated by iptables-save v1.4.0 on Wed Dec 31 21:40:09 2008
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
[173:17935] -A INPUT -i lo -j ACCEPT 
[9045:9895021] -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
[659513:222335725] -A INPUT -j DROP 
[0:0] -A FORWARD -j DROP 
[76:8832] -A OUTPUT -o lo -j ACCEPT 
[0:0] -A OUTPUT -p tcp -m tcp --dport 8001 -j ACCEPT 
[0:0] -A OUTPUT -p tcp -m tcp --dport 6667 -j ACCEPT 
[222:14070] -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT 
[7979:1025881] -A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT 
[24:2130] -A OUTPUT -j DROP 
COMMIT
# Completed on Wed Dec 31 21:40:09 2008
# Generated by iptables-save v1.4.0 on Wed Dec 31 21:40:09 2008
*mangle
:PREROUTING ACCEPT [1487092:525187528]
:INPUT ACCEPT [668732:232249009]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [8397:1059956]
:POSTROUTING ACCEPT [8373:1057826]
[0:0] -A FORWARD -o ppp0 -p tcp -m tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1400:1536 -j TCPMSS --clamp-mss-to-pmtu 
COMMIT
# Completed on Wed Dec 31 21:40:09 2008
# Generated by iptables-save v1.4.0 on Wed Dec 31 21:40:09 2008
*nat
:PREROUTING ACCEPT [1477830:515225061]
:POSTROUTING ACCEPT [672:41360]
:OUTPUT ACCEPT [672:41360]
COMMIT
# Completed on Wed Dec 31 21:40:09 2008

i have several questions.

1. see first output rule of filter table:

-A INPUT -i lo -j ACCEPT 

if i delete this i can see sites except [http://localhost/](http://localhost/) .
so when i connect to it my browser sends another packet then tcp to 80th port. which protocol packet and to which port of localhost it sends.

2. what i can write to nat and mangle tables for security?

3. i have seen some information related to

-A FORWARD -o ppp0 -p tcp -m tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1400:1536 -j TCPMSS --clamp-mss-to-pmtu 

rule of mangle table in pppoeconf and man iptables (in tcpmss module and TCPMSS target chapters). can you tell some about that?
i can tell this: it appears after pon dsl-provider and disappears after poff dsl-provider automatically. if i delete it manually when internet is connected sites are opening which i have seen.

4. i have edited /etc/network/interfaces . now its content is:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
pre-up iptables-restore < /home/xxxxxx/doc/2008/12/30/iptables.txt
post-down iptables-save -c > /home/xxxxxx/doc/2008/12/30/iptables.txt

iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

(i replaced my login name with xxxxxx.)
when i have written 

pre-up iptables-restore < /home/xxxxxx/doc/2008/12/30/iptables.txt
post-down iptables-save -c > /home/xxxxxx/doc/2008/12/30/iptables.txt

lines this content was other.

iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

lines was not as i remember. i have read in that tutorial that i should write lines pre-up ... and post-down ... after something. i have not understood well. where i should write them exactly?
i ask this because this does not work fully: only restores after restart of OS but does not save iptables when "turn off" OS.

4.1. i have closed access to "/home/xxxxxx" directory "for others", should this work so?

---

### Post by q.dinar on 2009-01-01
i have found how why localhost did not work. i found this by logging. when i open localhost with browser destination port is 80 and source port a random, and then 80 port(also from localhost) sends a packet backward from 80th port to that random port of localhost. other time i opened that localhost that random port is other, but server-side port is always 80. so this rule solved it:

sudo iptables -I OUTPUT -o lo -p tcp --sport 80 -j ACCEPT

and filter table has become (output of "sudo iptables -L -v"):

```
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1217  347K ACCEPT     all  --  lo     any     anywhere             anywhere            
20313   21M ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
 290K   97M DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    6  1083 ACCEPT     tcp  --  any    lo      anywhere             anywhere            tcp spt:www 
 6532  375K ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:8001 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ircd 
  475 30079 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:domain 
  814  109K ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:https 
13573 1797K ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www 
   17  1230 DROP       all  --  any    any     anywhere             anywhere
```

---

