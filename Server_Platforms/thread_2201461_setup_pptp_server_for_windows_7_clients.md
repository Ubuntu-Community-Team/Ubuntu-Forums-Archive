---
title: "setup pptp server for windows 7 clients"
date: 2014-01-24
forum: Server Platforms
---

### Post by charles18 on 2014-01-24
[SIZE=2]good day all

**UPDATED1**: Check bottom of post
**UPDATED2**: port checks to server

Backround:

[I]for the past 3-4 months I have been trying all in my power, porbably  got a suspension or two from serverfault aswel trying to get my  pptp/openvpn server setup

first I had CentOS, so I tried openvpn at first, and after 15 tutorials  and 3 system reloads later, I decided to try pptp, which was also  fruitless, and the ISP was kind enough to supply me with a tut or two on  how to get setup, which quite frankly was no help at all...[/I]

problem:

I switched to a different ISP, rented a VPS again and now I am trying to  setup a pptp again, since my instutution allows pptp connections

first off, I have tried these 2 tutorials, with no luck (I followed  every step EXCEPT setting the ms-dns and local/remoteip, as I figure  this does not affect the connection issues)
[URL="http://riobard.com/2011/11/12/pptp-vpn-on-ubuntu/"]
[SIZE=2]http://riobard.com/2011/11/12/pptp-vpn-on-ubuntu/[/SIZE][/URL] 
[/SIZE][SIZE=2][https://www.digitalocean.com/community/articles/how-to-setup-your-own-vpn-with-pptp](https://www.digitalocean.com/community/articles/how-to-setup-your-own-vpn-with-pptp)[/SIZE]

note: to the creators of these tutorials (please dont feel offended, I  am using this as a basis so others can troubleshoot why these dont work  for me)

So I tried another tutorial I came across on these forums, here is the complete output as from **putty**: (I included 3 notes at the bottom)

_______________________________________________________________________________________________________________________________

[https://help.ubuntu.com/community/PPTPServer](https://help.ubuntu.com/community/PPTPServer)

-----------------------------------------------------------------------------------------------------------------------

login as: root
root@196.28.97.204's password:
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-21-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Fri Jan 24 15:31:25 UTC 2014

  System load:  0.0               Processes:           73
  Usage of /:   7.4% of 19.69GB   Users logged in:     1
  Memory usage: 12%               IP address for eth0: 196.28.97.204
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Last login: Fri Jan 24 14:45:08 2014 from 192.96.15.27
root@vpnserver:~# sudo apt-get install pptpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
pptpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@vpnserver:~# sudo nano /etc/pptpd.conf -----------------------------SEE NOTE 1
root@vpnserver:~# sudo nano /etc/ppp/pptpd-options --------------------SEE NOTE 2
root@vpnserver:~# nano /etc/ppp/chap-secrets
root@vpnserver:~# nano /etc/ppp/chap-secrets
root@vpnserver:~#  /etc/init.d/pptpd restart
Restarting PPTP:
Stopping PPTP: pptpd.
Starting PPTP Daemon: pptpd.
root@vpnserver:~# nano /etc/sysctl.conf 
root@vpnserver:~# sysctl -p
net.ipv4.ip_forward = 1
root@vpnserver:~# nano /etc/rc.local-------------------------------------SEE NOTE 3
root@vpnserver:~# reboot
root@vpnserver:~#
Broadcast message from root@vpnserver
        (/dev/pts/1) at 16:26 ...

The system is going down for reboot NOW!
login as: root
root@196.28.97.204's password:
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-21-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Fri Jan 24 16:31:35 UTC 2014

  System load:  0.0               Processes:           75
  Usage of /:   7.4% of 19.69GB   Users logged in:     0
  Memory usage: 7%                IP address for eth0: 196.28.97.204
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Last login: Fri Jan 24 15:31:25 2014 from 192.96.15.10
root@vpnserver:~# netstat -ntlp | grep 1723
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN      794/pptpd --------------- SEE NOTE 4
root@vpnserver:~#



-----------------------------------------------------------------------------------------------------------------------

NOTE1[I]_ip configuration_
localip 10.0.0.1
remoteip 10.0.0.10-100[/I]

NOTE2[I]_-dns rename_
ms-dns left as is, not edited

[/I]NOTE3[I] - _rc.local file_
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE
iptables -A FORWARD -p tcp --syn -s 10.0.0.0/24 -j TCPMSS --set-mss 1356
exit 0

[/I]NOTE 4 - telnet
Notice that it is listening with port 1723 but:
Microsoft Telnet> o
( to ) 196.28.97.204:1723
Connecting To 196.28.97.204:1723...Could not open connection to the host, on por
t 23: Connect failed
Microsoft Telnet>

_______________________________________________________________________________________________________________________________

-------------------------------------------------------------
**UPDATE 1**

I tried connecting at my instutution, it shows connecting (pptp) and  after 10s it returns with Error 807, the network connection between  your computer and the VPN server was interupted.

however, I tried  connecting through my mobile phone, it connects via (pptp) ->   verifying username and password -> register computer on the network  and returns with error 629: the connection was closed by the remote compuer
-------------------------------------------------------------

-------------------------------------------------------------
**UPDATE 2**

I thought since I am able to connecting to my instututions VPN from outside its network, I might be able to VPN (PPTP) out

So I did a zenmap scan (using a traceroute to the server and zenmaping each server ip):

*(ordered from me to google.co.za, checking port 1-1724)*

[SIZE=4]1.[/SIZE]
Host is up (0.019s latency). (Cisco Systems)
Not shown: 1719 closed ports
PORT    STATE    SERVICE
22/tcp  open     ssh
23/tcp  filtered telnet
80/tcp  open     http
443/tcp open     https

[SIZE=4]2.
[SIZE=2]Host is up (0.034s latency).
All 1724 scanned ports on 196.21.199.153 are filtered[/SIZE]

[SIZE=4]3.
[SIZE=2]Host is up (0.025s latency).
All 1724 scanned ports on 196.21.199.222 are filtered[/SIZE]

[SIZE=4]4.
[SIZE=2]Host is up (0.029s latency).
All 1724 scanned ports on 10.108.16.1 are filtered[/SIZE]

[SIZE=4]5.
[SIZE=2]Host is up (0.032s latency).
Not shown: 1707 filtered ports
PORT    STATE  SERVICE
21/tcp  closed ftp
22/tcp  closed ssh
53/tcp  closed domain
80/tcp  closed http
81/tcp  closed hosts2-ns
110/tcp closed pop3
113/tcp closed ident
123/tcp closed ntp
143/tcp closed imap
182/tcp closed audit
443/tcp closed https
554/tcp closed rtsp
587/tcp closed submission
902/tcp closed iss-realsecure
903/tcp closed iss-console-mgr
993/tcp closed imaps
995/tcp closed pop3s
[/SIZE]
[SIZE=4]6.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
Nmap scan report for 155.232.240.42 (google.co.za)
Host is up (0.046s latency).
Not shown: 1721 filtered ports
PORT    STATE  SERVICE
80/tcp  open   http
113/tcp closed ident
443/tcp open   https

Instutution IP addresses not shown for security and safety reasons

-------------------------------------------------------------

Any help would be appreciated!!!

---

### Post by TheFu on 2014-01-24
Are you certain - ABSOLUTELY CERTAIN - that the necessary ports are open? It is often necessary to setup daemons on port 443 to get though firewalls and proxies.  This applies to hotels and universities and to connections trying to escape some country "protections."

Also, you must be aware that pptp has been considered "broken" for years now, so it is unclear that deploying it provides the protection people using a VPN would want.

---

