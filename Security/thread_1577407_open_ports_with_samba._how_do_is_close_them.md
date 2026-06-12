---
title: "open ports with samba. how do is close them?"
date: 2010-09-18
forum: Security
---

### Post by newboyo on 2010-09-18
Hi all,
Just ran a nmap on my machine, which resulted in the following output -
<<I've included only the parts I thought indicate an open port, if you need the full output  will do so>>


Just wondering if my network is open. 192...8 is my machine and  192....10 is my wireless printer. I've installed SAMBA to permit share  of my documents between my linux box and virtual win 7.

FYI, I use karmic, on a T410 and have installed guarddog.

Thanks for your advise.



Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-09-18 19:40 EDT
NSE: Loaded 30 scripts for scanning.
Initiating Ping Scan at 19:40
Scanning 255 hosts [2 ports/host]
Completed Ping Scan at 19:40, 4.82s elapsed (255 total hosts)
Initiating Parallel DNS resolution of 255 hosts. at 19:40
Completed Parallel DNS resolution of 255 hosts. at 19:40, 0.03s elapsed
Initiating Connect Scan at 19:40
Scanning 5 hosts [1000 ports/host]
Discovered open port 23/tcp on 192.168.1.8
Discovered open port 80/tcp on 192.168.1.1
Discovered open port 53/tcp on 192.168.1.1
Discovered open port 80/tcp on 192.168.1.3
Discovered open port 139/tcp on 192.168.1.8
Discovered open port 80/tcp on 192.168.1.10
Discovered open port 445/tcp on 192.168.1.8
Completed Connect Scan against 192.168.1.8 in 0.14s (4 hosts left)
Discovered open port 21/tcp on 192.168.1.10
Discovered open port 515/tcp on 192.168.1.10
Completed Connect Scan against 192.168.1.6 in 9.84s (3 hosts left)
Completed Connect Scan against 192.168.1.1 in 10.05s (2 hosts left)
Completed Connect Scan against 192.168.1.10 in 10.05s (1 host left)
Completed Connect Scan at 19:40, 10.07s elapsed (5000 total ports)
Initiating Service scan at 19:40
Scanning 9 services on 5 hosts
Completed Service scan at 19:42, 66.31s elapsed (9 services on 5 hosts)
NSE: Script scanning 5 hosts.
NSE: Starting runlevel 1 scan
Initiating NSE at 19:42
Completed NSE at 19:42, 4.51s elapsed
NSE: Starting runlevel 2 scan
Initiating NSE at 19:42
Completed NSE at 19:42, 10.02s elapsed
NSE: Script Scanning completed.
Host unknown (192.168.1.1) is up (0.0043s latency).
Interesting ports on unknown (192.168.1.1):
Not shown: 978 filtered ports
PORT     STATE  SERVICE            VERSION
21/tcp   closed ftp
25/tcp   closed smtp
37/tcp   closed time
53/tcp   open   domain             dnsmasq 2.55
80/tcp   open   http?
|_ html-title: Error
|  http-auth: HTTP Service requires authentication
|_   Auth type: Basic, realm = HOME
110/tcp  closed pop3
143/tcp  closed imap
443/tcp  closed https
465/tcp  closed smtps
515/tcp  closed printer
631/tcp  closed ipp
993/tcp  closed imaps
1863/tcp closed msnp
5222/tcp closed unknown
6881/tcp closed bittorrent-tracker
6969/tcp closed acmsoda
7001/tcp closed afs3-callback
7002/tcp closed afs3-prserver
8000/tcp closed http-alt
8008/tcp closed http
8080/tcp closed http-proxy
8888/tcp closed sun-answerbook
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [http://www.insecure.org/cgi-bin/servicefp-submit.cgi](http://www.insecure.org/cgi-bin/servicefp-submit.cgi) :
SF-Port80-TCP:V=5.00%I=7%D=9/18%Time=4C954E0D%P=x86_64-unknown-linux-gnu%r
SF:(GetRequest,17B,"HTTP/1\.0\x20401\x20Unauthorized\r\nDate:\x20Sat,\x201
SF:8\x20Sep\x202010\x2023:40:55\x20GMT\r\nContent-Type:\x20text/html;\x20c
SF:harset=utf-8\r\nCache-Control:\x20no-cache,\x20no-store,\x20must-revali
SF:date,\x20private\r\nExpires:\x20Thu,\x2031\x20Dec\x201970\x2000:00:00\x
SF:20GMT\r\nPragma:\x20no-cache\r\nWWW-Authenticate:\x20Basic\x20realm=\"G
SF:HAR\"\r\nConnection:\x20close\r\n\r\n<html><head><title>Error</title></
SF:head><body><h2>401\x20Unauthorized</h2>\x20Unauthorized</body></html>")
SF:%r(FourOhFourRequest,17B,"HTTP/1\.0\x20401\x20Unauthorized\r\nDate:\x20
SF:Sat,\x2018\x20Sep\x202010\x2023:41:00\x20GMT\r\nContent-Type:\x20text/h
SF:tml;\x20charset=utf-8\r\nCache-Control:\x20no-cache,\x20no-store,\x20mu
SF:st-revalidate,\x20private\r\nExpires:\x20Thu,\x2031\x20Dec\x201970\x200
SF:0:00:00\x20GMT\r\nPragma:\x20no-cache\r\nWWW-Authenticate:\x20Basic\x20
SF:realm=\"HOME\"\r\nConnection:\x20close\r\n\r\n<html><head><title>Error<
SF:/title></head><body><h2>401\x20Unauthorized</h2>\x20Unauthorized</body>
SF:</html>")%r(Help,15E,"HTTP/1\.0\x20400\x20Invalid\x20Request\r\nDate:\x
SF:20Sat,\x2018\x20Sep\x202010\x2023:41:15\x20GMT\r\nContent-Type:\x20text
SF:/html;\x20charset=utf-8\r\nCache-Control:\x20no-cache,\x20no-store,\x20
SF:must-revalidate,\x20private\r\nExpires:\x20Thu,\x2031\x20Dec\x201970\x2
SF:000:00:00\x20GMT\r\nPragma:\x20no-cache\r\nConnection:\x20close\r\n\r\n
SF:<html><head><title>Error</title></head><body><h2>400\x20Invalid\x20Requ
SF:est</h2>\x20Invalid\x20Request</body></html>")%r(LPDString,15E,"HTTP/1\
SF:.0\x20400\x20Invalid\x20Request\r\nDate:\x20Sat,\x2018\x20Sep\x202010\x
SF:2023:41:20\x20GMT\r\nContent-Type:\x20text/html;\x20charset=utf-8\r\nCa
SF:che-Control:\x20no-cache,\x20no-store,\x20must-revalidate,\x20private\r
SF:\nExpires:\x20Thu,\x2031\x20Dec\x201970\x2000:00:00\x20GMT\r\nPragma:\x
SF:20no-cache\r\nConnection:\x20close\r\n\r\n<html><head><title>Error</tit
SF:le></head><body><h2>400\x20Invalid\x20Request</h2>\x20Invalid\x20Reques
SF:t</body></html>");

Host 192.168.1.3 is up (0.012s latency).
Interesting ports on 192.168.1.3:
Not shown: 999 filtered ports
PORT   STATE SERVICE    VERSION
80/tcp open  tcpwrapped

Host THINK (192.168.1.8  is up (0.00032s latency).
Interesting ports on THINK (192.168.1.8 :
Not shown: 997 closed ports
PORT    STATE SERVICE     VERSION
23/tcp  open  telnet      Linux telnetd
139/tcp open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
Service Info: OS: Linux

Host script results:
|  nbstat: NetBIOS name: SAM-LAPTOP, NetBIOS user: <unknown>, NetBIOS MAC: <unknown>
|  Name: SAM-LAPTOP<00>     Flags: <unique><active>
|  Name: SAMIR-LAPTOP<03>     Flags: <unique><active>
|  Name: SAM-LAPTOP<20>     Flags: <unique><active>
|  Name: WORKGROUP<1e>        Flags: <group><active>
|_ Name: WORKGROUP<00>        Flags: <group><active>
|  smb-os-discovery: Unix
|  LAN Manager: Samba 3.4.0
|  Name: Unknown\Unknown
|_ System time: 2010-09-18 19:42:01 UTC-4

Host MFC495CW (192.168.1.10) is up (0.0095s latency).
Interesting ports on MFC495CW (192.168.1.10):
Not shown: 978 filtered ports
PORT     STATE  SERVICE            VERSION
21/tcp   open   ftp                Brother/HP printer ftpd 1.13
|_ ftp-anon: Anonymous FTP login allowed
25/tcp   closed smtp
37/tcp   closed time
53/tcp   closed domain
80/tcp   open   tcpwrapped
110/tcp  closed pop3
143/tcp  closed imap
443/tcp  closed https
465/tcp  closed smtps
515/tcp  open   printer
631/tcp  closed ipp
993/tcp  closed imaps
1863/tcp closed msnp
5222/tcp closed unknown
6881/tcp closed bittorrent-tracker
6969/tcp closed acmsoda
7001/tcp closed afs3-callback
7002/tcp closed afs3-prserver
8000/tcp closed http-alt
8008/tcp closed http
8080/tcp closed http-proxy
8888/tcp closed sun-answerbook
Service Info: Device: printer

Read data files from: /usr/share/nmap
Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 255 IP addresses (5 hosts up) scanned in 96.00 seconds

---

### Post by newboyo on 2010-09-18
Hi all,
Just ran a nmap on my machine, which resulted in the following output -
<<I've included only the parts I thought indicate an open port, if you need the full output  will do so>>


Just wondering if my network is open. 192...8 is my machine and   192....10 is my wireless printer. I've installed SAMBA to permit share   of my documents between my linux box and virtual win 7.

FYI, I use karmic, on a T410 and have installed guarddog.

Thanks for your advise.



```
Starting Nmap 5.00 ( [http://nmap.org]("http://nmap.org/") ) at 2010-09-18 19:40 EDT
NSE: Loaded 30 scripts for scanning.
Initiating Ping Scan at 19:40
Scanning 255 hosts [2 ports/host]
Completed Ping Scan at 19:40, 4.82s elapsed (255 total hosts)
Initiating Parallel DNS resolution of 255 hosts. at 19:40
Completed Parallel DNS resolution of 255 hosts. at 19:40, 0.03s elapsed
Initiating Connect Scan at 19:40
Scanning 5 hosts [1000 ports/host]
[COLOR=Red]Discovered open port 23/tcp on 192.168.1.8
Discovered open port 80/tcp on 192.168.1.1
Discovered open port 53/tcp on 192.168.1.1
Discovered open port 80/tcp on 192.168.1.3
Discovered open port 139/tcp on 192.168.1.8
Discovered open port 80/tcp on 192.168.1.10
Discovered open port 445/tcp on 192.168.1.8[/COLOR]
Completed Connect Scan against 192.168.1.8 in 0.14s (4 hosts left)
[COLOR=Red]Discovered open port 21/tcp on 192.168.1.10
Discovered open port 515/tcp on 192.168.1.10[/COLOR]
Completed Connect Scan against 192.168.1.6 in 9.84s (3 hosts left)
Completed Connect Scan against 192.168.1.1 in 10.05s (2 hosts left)
Completed Connect Scan against 192.168.1.10 in 10.05s (1 host left)
Completed Connect Scan at 19:40, 10.07s elapsed (5000 total ports)
Initiating Service scan at 19:40
Scanning 9 services on 5 hosts
Completed Service scan at 19:42, 66.31s elapsed (9 services on 5 hosts)
NSE: Script scanning 5 hosts.
NSE: Starting runlevel 1 scan
Initiating NSE at 19:42
Completed NSE at 19:42, 4.51s elapsed
NSE: Starting runlevel 2 scan
Initiating NSE at 19:42
Completed NSE at 19:42, 10.02s elapsed
NSE: Script Scanning completed.
Host unknown (192.168.1.1) is up (0.0043s latency).
Interesting ports on unknown (192.168.1.1):
Not shown: 978 filtered ports
PORT     STATE  SERVICE            VERSION
21/tcp   closed ftp
25/tcp   closed smtp
37/tcp   closed time
53/tcp   open   domain             dnsmasq 2.55
[COLOR=Red]80/tcp   open   http?
|_ html-title: Error
|  http-auth: HTTP Service requires authentication
|_   Auth type: Basic, realm = HOME[/COLOR]
110/tcp  closed pop3
143/tcp  closed imap
443/tcp  closed https
465/tcp  closed smtps
515/tcp  closed printer
631/tcp  closed ipp
993/tcp  closed imaps
1863/tcp closed msnp
5222/tcp closed unknown
6881/tcp closed bittorrent-tracker
6969/tcp closed acmsoda
7001/tcp closed afs3-callback
7002/tcp closed afs3-prserver
8000/tcp closed http-alt
8008/tcp closed http
8080/tcp closed http-proxy
8888/tcp closed sun-answerbook
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [http://www.insecure.org/cgi-bin/servicefp-submit.cgi](http://www.insecure.org/cgi-bin/servicefp-submit.cgi) :
SF-Port80-TCP:V=5.00%I=7%D=9/18%Time=4C954E0D%P=x86_64-unknown-linux-gnu%r
SF:sad:GetRequest,17B,"HTTP/1\.0\x20401\x20Unauthorized\r\nDate:\x20Sat,\x201
SF:8\x20Sep\x202010\x2023:40:55\x20GMT\r\nContent-Type:\x20text/html;\x20c
SF:harset=utf-8\r\nCache-Control:\x20no-cache,\x20no-store,\x20must-revali
SF:date,\x20private\r\nExpires:\x20Thu,\x2031\x20D  ec\x201970\x2000:00:00\x
SF:20GMT\r\nPragma:\x20no-cache\r\nWWW-Authenticate:\x20Basic\x20realm=\"H
SF:OME\"\r\nConnection:\x20close\r\n\r\n<html><hea  d><title>Error</title></
SF:head><body><h2>401\x20Unauthorized</h2>\x20Unauthorized</body></html>")
SF:%r(FourOhFourRequest,17B,"HTTP/1\.0\x20401\x20Unauthorized\r\nDate:\x20
SF:Sat,\x2018\x20Sep\x202010\x2023:41:00\x20GMT\r\  nContent-Type:\x20text/h
SF:tml;\x20charset=utf-8\r\nCache-Control:\x20no-cache,\x20no-store,\x20mu
SF:st-revalidate,\x20private\r\nExpires:\x20Thu,\x2031\x  20Dec\x201970\x200
SF:0:00:00\x20GMT\r\nPragma:\x20no-cache\r\nWWW-Authenticate:\x20Basic\x20
SF:realm=\"HOME\"\r\nConnection:\x20close\r\n\r\n<  html><head><title>Error<
SF:/title></head><body><h2>401\x20Unauthorized</h2>\x20Unauthorized</body>
SF:</html>")%r(Help,15E,"HTTP/1\.0\x20400\x20Invalid\x20Request\r\nDate:\x
SF:20Sat,\x2018\x20Sep\x202010\x2023:41:15\x20GMT\  r\nContent-Type:\x20text
SF:/html;\x20charset=utf-8\r\nCache-Control:\x20no-cache,\x20no-store,\x20
SF:must-revalidate,\x20private\r\nExpires:\x20Thu,\x2031\x  20Dec\x201970\x2
SF:000:00:00\x20GMT\r\nPragma:\x20no-cache\r\nConnection:\x20close\r\n\r\n
SF:<html><head><title>Error</title></head><body><h2>400\x20Invalid\x20Requ
SF:est</h2>\x20Invalid\x20Request</body></html>")%r(LPDString,15E,"HTTP/1\
SF:.0\x20400\x20Invalid\x20Request\r\nDate:\x20Sat  ,\x2018\x20Sep\x202010\x
SF:2023:41:20\x20GMT\r\nContent-Type:\x20text/html;\x20charset=utf-8\r\nCa
SF:che-Control:\x20no-cache,\x20no-store,\x20must-revalidate,\x20private\r
SF:\nExpires:\x20Thu,\x2031\x20Dec\x201970\x2000:0  0:00\x20GMT\r\nPragma:\x
SF:20no-cache\r\nConnection:\x20close\r\n\r\n<html><head><  title>Error</tit
SF:le></head><body><h2>400\x20Invalid\x20Request</h2>\x20Invalid\x20Reques
SF:t</body></html>");

Host 192.168.1.3 is up (0.012s latency).
Interesting ports on 192.168.1.3:
Not shown: 999 filtered ports
PORT   STATE SERVICE    VERSION
[COLOR=Red]80/tcp open  tcpwrapped[/COLOR]

Host THINK (192.168.1.8  is up (0.00032s latency).
Interesting ports on THINK (192.168.1.8 :
Not shown: 997 closed ports
PORT    STATE SERVICE     VERSION
[COLOR=Red]23/tcp  open  telnet      Linux telnetd
139/tcp open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
Service Info: OS: Linux[/COLOR]

Host script results:
|[COLOR=Red]  nbstat: NetBIOS name: SAM-LAPTOP, NetBIOS user: <unknown>, NetBIOS MAC: <unknown>
|  Name: SAM-LAPTOP<00>     Flags: <unique><active>
|  Name: SAMIR-LAPTOP<03>     Flags: <unique><active>
|  Name: SAM-LAPTOP<20>     Flags: <unique><active>
|  Name: WORKGROUP<1e>        Flags: <group><active>
|_ Name: WORKGROUP<00>        Flags: <group><active>
|  smb-os-discovery: Unix
|  LAN Manager: Samba 3.4.0
|  Name: Unknown\Unknown
|_ System time: 2010-09-18 19:42:01 UTC-4
[/COLOR] 
Host MFC495CW (192.168.1.10) is up (0.0095s latency).
Interesting ports on MFC495CW (192.168.1.10):
Not shown: 978 filtered ports
PORT     STATE  SERVICE            VERSION
[COLOR=Red]21/tcp   open   ftp                Brother/HP printer ftpd 1.13
|_ ftp-anon: Anonymous FTP login allowed[/COLOR]
25/tcp   closed smtp
37/tcp   closed time
53/tcp   closed domain
80/tcp   open   tcpwrapped
110/tcp  closed pop3
143/tcp  closed imap
443/tcp  closed https
465/tcp  closed smtps
515/tcp  open   printer
631/tcp  closed ipp
993/tcp  closed imaps
1863/tcp closed msnp
5222/tcp closed unknown
6881/tcp closed bittorrent-tracker
6969/tcp closed acmsoda
7001/tcp closed afs3-callback
7002/tcp closed afs3-prserver
8000/tcp closed http-alt
8008/tcp closed http
8080/tcp closed http-proxy
8888/tcp closed sun-answerbook
Service Info: Device: printer

Read data files from: /usr/share/nmap
Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 255 IP addresses (5 hosts up) scanned in 96.00 seconds
```

---

### Post by CharlesA on 2010-09-18
Ok, so let's break this down:

```
Discovered open port 80/tcp on 192.168.1.1
Discovered open port 53/tcp on 192.168.1.1
```

Guessing 192.168.1.1 is your router. Having those ports open is fine, since it's probably running DNS and a web interface.

```
Discovered open port 80/tcp on 192.168.1.3
```

No idea what device, but it's got a web interface or is running a web server.

```
Discovered open port 23/tcp on 192.168.1.8
Discovered open port 139/tcp on 192.168.1.8
Discovered open port 445/tcp on 192.168.1.8
```

192.168.1.8 is your machine. I don't know why it's running telnet instead of SSH. Samba listens on TCP ports 139 and 445; UDP ports 137 and 138.

```
Discovered open port 21/tcp on 192.168.1.10
Discovered open port 80/tcp on 192.168.1.10
Discovered open port 515/tcp on 192.168.1.10
```

192.168.1.10 is the printer, 21 is ftp, which I am unsure why it's being run on the printer. 80 is for the web interface and 515 is the print spooler.

Overall it looks fine.

---

### Post by newboyo on 2010-09-18
thank you very much indeed. I've removed telnet server component.

---

### Post by CharlesA on 2010-09-18
The only real reason you'd need to firewall those ports is if they were allowed access to the internet. If they are just on yer local lan, they are fine as is.

---

### Post by cariboo on 2010-09-19
To check what ports are open to the world on your router, use [canyouseeme]("http://canyouseeme.org/").

---

### Post by cariboo on 2010-09-19
I merged your post from the other solved samba thread with this one, so there isn't a duplication of effort.

---

