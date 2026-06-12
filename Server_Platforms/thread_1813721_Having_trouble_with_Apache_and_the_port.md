---
title: "Having trouble with Apache and the port"
date: 2011-07-28
forum: Server Platforms
---

### Post by Fuchur84 on 2011-07-28
Hello :).

Just to let you know: I am quiet a newbee with linux in general, so please be a bit patient with me if I say something wrong or have not yet learned everything... I am trying and willing to learn :). Hopefully this is the right forum. Sorry for posting that much code, but I tried a few things to get through the problems I have and couldn't get it to run properly.

My problem:
I have a Root-Ubuntu-Server (as webserver with PHP and MySQL) at my webhoster with Plesk as administration-tool and SSH-root-access.

The website(php- and mysql-based) run like it should and worked. Then I restarted my webserver to read in a new php.ini-file and now the website is no longer available using the browser. (I still have FTP and SSH-access and Plesk is still working too).

So I logged onto the server using SSH and had a look. The apache2-process was still running, but since it didn't show my website in the browser, I tried to restart it just in case:
```
apache2ctl restart
```I got the following error-message:
```
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down

```I googled it and found out, that it in general means that some other programm is already using port 80 and I had to kill the other procress:
```
root@h1922070:~# lsof -i :80
```and got:
```

COMMAND  PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
apache2 3652 www-data    4u  IPv4  19079      0t0  TCP *:www (LISTEN)

```So I killed that process with:
```
kill 3652
```But after trying again to start the apache again with:
```
apache2ctl start
```I still got the same error-message. So I tried to search for :www instead of the :80, but got no output. (nothing found)

So I thought: Okay have a look manually what is running:
```
ps -e
```and got quite a list, but no apache2-process.

Next I tried to test the ports and services with this command I found on the net and got this:
```

sudo nmap -T Aggressive -A -v 127.0.0.1 -p 1-100

Starting Nmap 5.00 ( http://nmap.org ) at 2011-07-28 12:58 CEST
NSE: Loaded 30 scripts for scanning.
Initiating SYN Stealth Scan at 12:58
Scanning localhost (127.0.0.1) [100 ports]
Discovered open port 25/tcp on 127.0.0.1
Discovered open port 53/tcp on 127.0.0.1
Discovered open port 22/tcp on 127.0.0.1
Discovered open port 21/tcp on 127.0.0.1
Discovered open port 80/tcp on 127.0.0.1
Completed SYN Stealth Scan at 12:58, 0.10s elapsed (100 total ports)
Initiating Service scan at 12:58
Scanning 5 services on localhost (127.0.0.1)
Completed Service scan at 12:59, 116.11s elapsed (5 services on 1 host)
Initiating OS detection (try #1) against localhost (127.0.0.1)
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34163 > 127.0.0.1:21  ttl=45 id=39260 iplen=60  seq=220756754 win=128 <wscale 10,nop,mss 265,timestamp 4294967295 0,sackOK>
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34164 > 127.0.0.1:21 SFPU ttl=49 id=24418 iplen=60  seq=220756754 win=256 <wscale 10,nop,mss 265,timestamp 4294967295 0,sackOK>
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34165 > 127.0.0.1:21 A ttl=59 id=4572 iplen=60  seq=220756754 win=1024 ack=336315290 <wscale 10,nop,mss 265,timestamp 4294967295 0,sackOK>
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34167 > 127.0.0.1:1 A ttl=48 id=16901 iplen=60  seq=220756754 win=32768 ack=336315290 <wscale 10,nop,mss 265,timestamp 4294967295 0,sackOK>
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34168 > 127.0.0.1:1 FPU ttl=55 id=64351 iplen=60  seq=220756754 win=65535 <wscale 15,nop,mss 265,timestamp 4294967295 0,sackOK>
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34163 > 127.0.0.1:21  ttl=47 id=46076 iplen=60  seq=220756754 win=128 <wscale 10,nop,mss 265,timestamp 4294967295 0,sackOK>
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34164 > 127.0.0.1:21 SFPU ttl=57 id=61389 iplen=60  seq=220756754 win=256 <wscale 10,nop,mss 265,timestamp 4294967295 0,sackOK>
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34168 > 127.0.0.1:1 FPU ttl=40 id=9350 iplen=60  seq=220756754 win=65535 <wscale 15,nop,mss 265,timestamp 4294967295 0,sackOK>
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34163 > 127.0.0.1:21  ttl=47 id=32223 iplen=60  seq=220756754 win=128 <wscale 10,nop,mss 265,timestamp 4294967295 0,sackOK>
sendto in send_ip_packet: sendto(4, packet, 60, 0, 127.0.0.1, 16) => Operation not permitted
Offending packet: TCP 127.0.0.1:34164 > 127.0.0.1:21 SFPU ttl=47 id=11658 iplen=60  seq=220756754 win=256 <wscale 10,nop,mss 265,timestamp 4294967295 0,sackOK>
Omitting future Sendto error messages now that 10 have been shown.  Use -d2 if you really want to see them.
Retrying OS detection (try #2) against localhost (127.0.0.1)
Retrying OS detection (try #3) against localhost (127.0.0.1)
Retrying OS detection (try #4) against localhost (127.0.0.1)
Retrying OS detection (try #5) against localhost (127.0.0.1)
NSE: Script scanning 127.0.0.1.
NSE: Starting runlevel 1 scan
Initiating NSE at 13:00
Completed NSE at 13:00, 10.06s elapsed
NSE: Script Scanning completed.
Host localhost (127.0.0.1) is up (0.000059s latency).
Interesting ports on localhost (127.0.0.1):
Not shown: 95 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     ProFTPD 1.x.x
22/tcp open  ssh     OpenSSH 5.3p1 Debian 3ubuntu6 (protocol 2.0)
|  ssh-hostkey: 2048 a1:b2:c3:d4:e5:f6:78:g9:101:h1:i2:j3:kl:14:15:16 (DSA)
|_ 2048 f0:11:22:3a:f4:g5:67:89:0h:i1:jk:2l:m3:no:4q:56 (RSA)
25/tcp open  smtp    Postfix smtpd
|_ smtp-commands: EHLO h10125.stratoserver.net, PIPELINING, SIZE 10240000, ETRN, STARTTLS, AUTH DIGEST-MD5 CRAM-MD5 PLAIN LOGIN, XFORWARD NAME ADDR PROTO HELO SOURCE PORT, ENHANCEDSTATUSCODES, 8BITMIME, DSN
53/tcp open  domain  ISC BIND none
80/tcp open  http?
No exact OS matches for host (If you know what OS is running on it, see http://nmap.org/submit/ ).
TCP/IP fingerprint:

Uptime guess: 0.085 days (since Thu Jul 28 10:57:45 2011)
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=202 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: Host:  h10125.stratoserver.net; OSs: Unix, Linux

Read data files from: /usr/share/nmap
OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 138.67 seconds
           Raw packets sent: 155 (9990B) | Rcvd: 355 (20.020KB)

```(I changed the fingerprint, the server-url and the ssh-hostkey, just to be sure that it can not be used to get access to the server but left the structure as it is)

Port 80 is open, no processes I can see which should be a problem.

So I am quite at the end of what I could find in google that could be a solution. How can I get the port-problem solved?

Could somebody give me a tipp what I have to do to get the server back running?
It would be great, if I would not have to upload all the stuff again, because we are talking about several GBs of data and it would take quite a time to get the stuff back online. Can I reinstall Apache2 without loosing the website-data and Plesk?) or repair it somehow?

Thanks you so much for reading till the end and thank you very much in advance for any comment and tipps you can give me... :)

See you and thanks again
*Fuchur*

---

### Post by Fuchur84 on 2011-07-28
Finally I found the problem... most important if your problems was not solved by just killing and restarting the process:

```

cat /var/log/apache2/error.log

```

This will open the Log-Files of the apache (even so it tells you when you tried to start it before that it could not open them). For me it was an mis-configurated APC-modul, that created the problems. 

Hope it helps someone else too!

See you und thanks again
*Fuchur*

---

### Post by Lars Noodén on 2011-07-28
You might like using [less](http://manpages.ubuntu.com/manpages/natty/en/man1/less.1.html) instead of **cat**

---

