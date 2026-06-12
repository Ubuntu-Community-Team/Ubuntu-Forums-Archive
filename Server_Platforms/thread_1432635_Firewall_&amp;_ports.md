---
title: "Firewall &amp; ports"
date: 2010-03-18
forum: Server Platforms
---

### Post by mfcallahan on 2010-03-18
I'm having a bit of trouble setting my firewall on my Ubuntu server.  Gufw is set as follows:

Enabled
By default Deny

Allow:
21/tcp
135/tcp
445/tcp
631/tcp
1024/tcp
5900/tcp
139/tcp
137/tcp
138/tcp
389/tcp
901/tcp
442/tcp



Ubuntu nmap output:

mattserv@mattserv-server:~$ sudo nmap 192.168.1.201
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-03-17 21:40 MST
Interesting ports on mattserv-server (192.168.1.201):
Not shown: 994 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1024/tcp open  kdm
5900/tcp open  vnc

Nmap done: 1 IP address (1 host up) scanned in 0.41 seconds


and windows nmap output:

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2010-03-17 21:52 US Mountain Standard Time

Nmap scan report for matt-vaio (192.168.1.133)

Host is up.

rDNS record for 192.168.1.133: Matt-VAIO

PORT      STATE   SERVICE
7/tcp     unknown echo
9/tcp     unknown discard
13/tcp    unknown daytime
21/tcp    unknown ftp
22/tcp    unknown ssh
23/tcp    unknown telnet
25/tcp    unknown smtp
26/tcp    unknown rsftp
37/tcp    unknown time
53/tcp    unknown domain
79/tcp    unknown finger
80/tcp    unknown http
81/tcp    unknown hosts2-ns
88/tcp    unknown kerberos-sec
106/tcp   unknown pop3pw
110/tcp   unknown pop3
111/tcp   unknown rpcbind
113/tcp   unknown auth
119/tcp   unknown nntp
135/tcp   unknown msrpc
139/tcp   unknown netbios-ssn
143/tcp   unknown imap
144/tcp   unknown news
179/tcp   unknown bgp
199/tcp   unknown smux
389/tcp   unknown ldap
427/tcp   unknown svrloc
443/tcp   unknown https
444/tcp   unknown snpp
445/tcp   unknown microsoft-ds
465/tcp   unknown smtps
513/tcp   unknown login
514/tcp   unknown shell
515/tcp   unknown printer
543/tcp   unknown klogin
544/tcp   unknown kshell
548/tcp   unknown afp
554/tcp   unknown rtsp
587/tcp   unknown submission
631/tcp   unknown ipp
646/tcp   unknown ldp
873/tcp   unknown rsync
990/tcp   unknown ftps
993/tcp   unknown imaps
995/tcp   unknown pop3s
1025/tcp  unknown NFS-or-IIS
1026/tcp  unknown LSA-or-nterm
1027/tcp  unknown IIS
1028/tcp  unknown unknown
1029/tcp  unknown ms-lsa
1110/tcp  unknown nfsd-status
1433/tcp  unknown ms-sql-s
1720/tcp  unknown H.323/Q.931
1723/tcp  unknown pptp
1755/tcp  unknown wms
1900/tcp  unknown upnp
2000/tcp  unknown cisco-sccp
2001/tcp  unknown dc
2049/tcp  unknown nfs
2121/tcp  unknown ccproxy-ftp
2717/tcp  unknown unknown
3000/tcp  unknown ppp
3128/tcp  unknown squid-http
3306/tcp  unknown mysql
3389/tcp  unknown ms-term-serv
3986/tcp  unknown mapper-ws_ethd
4899/tcp  unknown radmin
5000/tcp  unknown upnp
5009/tcp  unknown airport-admin
5051/tcp  unknown ida-agent
5060/tcp  unknown sip
5101/tcp  unknown admdog
5190/tcp  unknown aol
5357/tcp  unknown unknown
5432/tcp  unknown postgresql
5631/tcp  unknown pcanywheredata
5666/tcp  unknown nrpe
5800/tcp  unknown vnc-http
5900/tcp  unknown vnc
6000/tcp  unknown X11
6001/tcp  unknown X11:1
6646/tcp  unknown unknown
7070/tcp  unknown realserver
8000/tcp  unknown http-alt
8008/tcp  unknown http
8009/tcp  unknown ajp13
8080/tcp  unknown http-proxy
8081/tcp  unknown blackice-icecap
8443/tcp  unknown https-alt
8888/tcp  unknown sun-answerbook
9100/tcp  unknown jetdirect
9999/tcp  unknown abyss
10000/tcp unknown snet-sensor-mgmt
32768/tcp unknown unknown
49152/tcp unknown unknown
49153/tcp unknown unknown
49154/tcp unknown unknown
49155/tcp unknown unknown
49156/tcp unknown unknown
49157/tcp unknown unknown


 I am not able to see the linux box on the network or map a drive in Windows7 when the firewall is on; everything is OK when the firewall is off.  I have a few extra ports open on the firewall in my attempts to fix this, and it seems that there are alot of ports in use on my windows machine.  Any suggestions on optimizing my setup?

Thanks much,
Matt

---

### Post by kamaji792 on 2010-03-18
Hi,

I think the reason you can't see your Linux box from your Windows box is because you have opened the ports all as TCP and at least 2 of them should be udp.

Just let me google:

Here are the ports:

Port 135/TCP - used by smbd
Port 137/UDP - used by nmbd
Port 138/UDP - used by nmbd
Port 139/TCP - used by smbd
Port 445/TCP - used by smbd

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html)
Scroll down to the section **Using a Firewall**

So I think you need to allow UDP on 137, 138.

All the best

---

### Post by mfcallahan on 2010-03-18
yep - opening those two ports UDP was the solution.  Thanks again for the link and your help.

Matt

---

### Post by CharlesA on 2010-03-18
Interesting. The only ports I have open on my Linux box running Samba are 139 and 445, and both are TCP.

I opened 139, so I could ping the box.

---

