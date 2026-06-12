---
title: "OpenVPN port problem"
date: 2010-11-10
forum: Server Platforms
---

### Post by viperce on 2010-11-10
I have setup a openvpn server and it is working on my lan i can connect to on port 1194 on both network cards.

My problem is i am trying to connect through the internet from home and i can not seem to get it working....
i have forwarded the ports from my Dlink DSL-2540u to my openVPN server but if i check my open ports using Angry ip scanner it shows me port that all my other ports to the other servers are open & working but port 1194 to the VPN server is not in the list.

I then checked on the lan & i get the same result Openvpn has no ports open.

i did a iptables -L

root@ubuntu:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

i also checked
netstate -plntu

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State                                                                                                         PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN                                                                                                        812/mysqld

tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN                                                                                                        1042/perl

tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN                                                                                                        1120/sshd
tcp        0      0 0.0.0.0:3128            0.0.0.0:*               LISTEN                                                                                                        906/(squid)
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN                                                                                                        797/named
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN                                                                                                        885/dovecot
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN                                                                                                        885/dovecot
tcp6       0      0 :::53                   :::*                    LISTEN                                                                                                        797/named
tcp6       0      0 :::22                   :::*                    LISTEN                                                                                                        1120/sshd
tcp6       0      0 ::1:953                 :::*                    LISTEN                                                                                                        797/named
**udp        0      0 0.0.0.0:1194           0.0.0.0:*                                                                                                                             864/openvpn**
udp        0      0 0.0.0.0:10000           0.0.0.0:*                                                                                                                             1042/perl
udp        0      0 0.0.0:53      0.0.0.0:*                                                                                                                             797/named
udp        0      0 10.8.0.4:53             0.0.0.0:*                                                                                                                             797/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                                                                                                                             797/named
udp        0      0 0.0.0.0:3130            0.0.0.0:*                                                                                                                             906/(squid)
udp        0      0 0.0.0.0:52068           0.0.0.0:*                                                                                                                             906/(squid)
udp6       0      0 :::53                   :::*                                                                                                                                  797/named

i found openvpn in the list but it is not listening on 1194...

can someone please tell me how to solve this problem..

---

### Post by SeijiSensei on 2010-11-10
Yes, it is. See the 0.0.0.0:1194 in the bolded entry?  That reports a udp listener on all addresses at that port.  The 864 is the process ID of the OpenVPN daemon.

Are you sure you forwarded both TCP and UDP through your router?

Try using some random high port like 22222 with the "port" directive in the OpenVPN .conf files on client and server.

---

### Post by viperce on 2010-11-10
ye i double checked it...if i forward to that server on say 1194 it does not work...if i forward to the other linux box say 5900 (ubuntu desktop machine) it works for some reason it does not want to work on the VPN :( 
> Yes, it is. See the 0.0.0.0:1194 in the bolded entry?  That reports a  udp listener on all addresses at that port.  The 864 is the process ID  of the OpenVPN daemon.

i saw that it was in there, but it did not say listening next to it that is why i put it in bold

---

### Post by SeijiSensei on 2010-11-10
> **viperce said:**
> i saw that it was in there, but it did not say listening next to it that is why i put it in bold

LISTEN appears only with TCP services.

If you can forward port 5900 then try using some other random high port for OpenVPN and see if that works.

---

### Post by viperce on 2010-11-10
i tried that this morning, used port 5900 on the vpn box set the openvpn to use port 5900 aswell forwarded the port to the vpn server as i did with the ubuntu desktop machine & it still not working :'(

i installed nmap on the vpn box & ran it 

root@ubuntuvpn:/etc/openvpn# nmap -sS -p- localhost

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-11-10 15:57 SAST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 65528 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
3128/tcp  open  squid-http
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt

i thought ok maybe with all my messing around i messed it up more, so i formated & reloaded everything from scratch & it still has the same problem :(

---

### Post by SeijiSensei on 2010-11-10
Well you'd need to use "nmap -sU -p 1024-65535 localhost" to scan for UDP on high ports. -sS does a "stealth" scan against TCP listeners.

Are you running a firewall on the box itself?  What's the result of "sudo iptables -L -nv"?

---

### Post by viperce on 2010-11-10
thanks Seijisensei,
root@ubuntuvpn:/etc/openvpn# nmap -sU -p 1024-65535 localhost

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-11-10 16:23 SAST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 64508 closed ports
PORT      STATE         SERVICE
1194/udp  open|filtered unknown
3130/udp  open|filtered squid-ipc
10000/udp open          unknown
38606/udp open|filtered unknown


i see it there :( must be something on my router then...

root@ubuntuvpn:/etc/openvpn# sudo iptables -L -nv
Chain INPUT (policy ACCEPT 262K packets, 12M bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 485 packets, 102K bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 263K packets, 12M bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by TSJason on 2010-11-10
If it's a router bug (which is completely possible) I would recommend switching your openvpn config to use TCP instead of UDP (making sure your router and client configs reflects the same changes).

I've seen several routers that simply fail to deal with udp only services.

---

### Post by viperce on 2010-11-11
Ok i did a firmware update on the router which seemed to work, only problem i am having now is the connection drops after about 1min :( at least it is connecting tho :)

---

