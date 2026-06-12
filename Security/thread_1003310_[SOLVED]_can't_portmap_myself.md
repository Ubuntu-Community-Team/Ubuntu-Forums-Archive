---
title: "[SOLVED] can't portmap myself"
date: 2008-12-06
forum: Security
---

### Post by icarid_17 on 2008-12-06
hello, I just learned about portmapping and it was cool so I portmapped myself (with nmap from another box) and it didn't work, so, also out of interest in my security I let ShieldsUp! test my security and everything'
s stealthed, so obviously i can't portmap myself (from what I understand, please correct me if I am wrong)from an external machine, however, what i could do was use nmap against my machine from a terminal running on the machine and it would tell me that i have two ports (ssh and RPC) open? (can't remember). i nmapped myself again and it won't work at all, gives me a "host seems down", why is this, one other question, if ALL:ALL is in my hosts.deny file, then how safe am I? (btw, ALL:ALL was in the file when i nmapped with the terminal running on my machine) also im currently using fedora (i know this is an ubuntu forum, but i would like to assume that this can be addressed by ubuntu users too)

---

### Post by icarid_17 on 2008-12-06
can anyone help me?

---

### Post by cariboo on 2008-12-07
Are you using your computer's ip address to run nmap eg:

```
nmap 192.168.1.100
```

Or are using your external ip address?

This is what I get running nmap on my home server:

```
 sudo nmap -sS -sV -O -p- -PI -PT 192.168.1.200

Starting Nmap 4.62 ( http://nmap.org ) at 2008-12-07 13:41 PST
Interesting ports on willy (192.168.1.200):
Not shown: 65522 closed ports
PORT      STATE SERVICE     VERSION
21/tcp    open  ftp         ProFTPD 1.3.1
22/tcp    open  ssh          (protocol 2.0)
80/tcp    open  http        Apache httpd 2.2.9 ((Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0)
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: APLUS)
445/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: APLUS)
631/tcp   open  ipp         CUPS 1.3
2049/tcp  open  rpcbind
3306/tcp  open  mysql       MySQL 5.0.67-0ubuntu6
10000/tcp open  http        Webmin httpd
42071/tcp open  rpcbind
55822/tcp open  rpcbind
57431/tcp open  rpcbind
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at http://www.insecure.org/cgi-bin/servicefp-submit.cgi :
SF-Port22-TCP:V=4.62%I=7%D=12/7%Time=493C4302%P=x86_64-unknown-linux-gnu%r
SF:(NULL,27,"SSH-2\.0-OpenSSH_5\.1p1\x20Debian-3ubuntu1\r\n");
MAC Address: 00:1B:11:B2:63:65 (D-Link)
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.17 - 2.6.23
Uptime: 0.429 days (since Sun Dec  7 03:23:43 2008)
Network Distance: 1 hop
Service Info: OS: Unix

Host script results:
|_ Discover OS Version over NetBIOS and SMB: Unix

OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 31.507 seconds
```

Jim

---

### Post by icarid_17 on 2008-12-08
port mapping myself, using my local ip, but my problem is that the first time i did it, nmap gave me a response (told me my interesting ports that were open and what OS i was using), now it just tells me that the "host seems down"  here's the output: 
Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-12-08 07:01 EST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN  (tried using -PN, i just don't get output, if i gave nmap a time to time-out it would) 
Nmap done: 1 IP address (0 hosts up) scanned in 2.074 seconds
whereas,

---

### Post by Dave_Connor on 2008-12-08
Add the -PN option to your command and then it should work.

---

### Post by Kinstonian on 2008-12-08
By default Nmap will attempt to do an ICMP and TCP ping to determine if the computer is up before it starts scanning.  If it doesn't get a response from the pings, it will abort the scan and tell you the host seems down.  You can force Nmap to scan without pinging by adding the -PN or -P0 options, so try that.  For example:

nmap -sS -PN -p 21,22,23,80 <your ip address>

That will scan 4 common ports and shouldn't take nearly as long as the default port scan which scans over a 1000 ports.  If that works, you can then try as many ports as you like and give it the time it needs.

---

### Post by icarid_17 on 2008-12-09
sweet, works, thanks Kinstonian, letting it map all ports now

---

