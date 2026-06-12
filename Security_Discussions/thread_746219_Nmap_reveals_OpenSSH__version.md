---
title: "Nmap reveals OpenSSH  version"
date: 2008-04-05
forum: Security Discussions
---

### Post by zapcojake on 2008-04-05
Hello, when I run nmap -T Aggressive -A -v <mylocalmachine>  against a Ubuntu 7.10 32 bit box on my local network the OS detetction fails but OpenSSH identifies itself as an Ubuntu package.  It seems like that serves just as well to ID the OS regular OS detection.  Is this normal? If not should somebody be made aware?

Here is the output:
Starting Nmap 4.60 ( [http://nmap.org](http://nmap.org) ) at 2008-04-05 14:48 UTC
Initiating ARP Ping Scan at 14:48
Scanning 192.168.1.101 [1 port]
Completed ARP Ping Scan at 14:48, 0.02s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 14:48
Completed Parallel DNS resolution of 1 host. at 14:48, 0.00s elapsed
Initiating SYN Stealth Scan at 14:48
Scanning andoria.domain.invalid (192.168.1.101) [1715 ports]
Discovered open port 22/tcp on 192.168.1.101
Discovered open port 5900/tcp on 192.168.1.101
Completed SYN Stealth Scan at 14:48, 1.88s elapsed (1715 total ports)
Initiating Service scan at 14:48
Scanning 2 services on andoria.domain.invalid (192.168.1.101)
Completed Service scan at 14:48, 0.06s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against andoria.domain.invalid (192.168.1.101)
Retrying OS detection (try #2) against andoria.domain.invalid (192.168.1.101)
Retrying OS detection (try #3) against andoria.domain.invalid (192.168.1.101)
Retrying OS detection (try #4) against andoria.domain.invalid (192.168.1.101)
Retrying OS detection (try #5) against andoria.domain.invalid (192.168.1.101)
Host andoria.domain.invalid (192.168.1.101) appears to be up ... good.
Interesting ports on andoria.domain.invalid (192.168.1.101):
Not shown: 1713 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 4.6p1 Debian 5ubuntu0.2 (protocol 2.0)
5900/tcp open  vnc     VNC (protocol 3.7)
MAC Address: 00:40:F4:E6:7D:9A (Cameo Communications)
No exact OS matches for host (If you know what OS is running on it, see [http://nmap.org/submit/](http://nmap.org/submit/) ).
TCP/IP fingerprint:
OS:SCAN(V=4.60%D=4/5%OT=22%CT=1%CU=33654%PV=Y%DS=1%G=Y%M=0040F4%TM=47F7915B
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=D1%GCD=2%ISR=EF%TI=Z%II=I%TS=A)SEQ(SP=D1%G
OS:CD=1%ISR=EF%TI=Z%II=I%TS=A)OPS(O1=M5B4ST11NW5%O2=M5B4ST11NW5%O3=M5B4NNT1
OS:1NW5%O4=M5B4ST11NW5%O5=M5B4ST11NW5%O6=M5B4ST11)WIN(W1=16A0%W2=16A0%W3=16
OS:A0%W4=16A0%W5=16A0%W6=16A0)ECN(R=Y%DF=Y%T=40%W=16D0%O=M5B4NNSNW5%CC=N%Q=
OS:)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=Y%DF=Y%T=40%W=16A0%S
OS:=O%A=S+%F=AS%O=M5B4ST11NW5%RD=0%Q=)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%R
OS:D=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=
OS:0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U
OS:1(R=Y%DF=N%T=40%TOS=C0%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUL=G%RU
OS:D=G)IE(R=Y%DFI=N%T=40%TOSI=S%CD=S%SI=S%DLI=S)


Uptime: 0.000 days (since Sat Apr  5 14:48:36 2008)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=209 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux

Read data files from: /usr/share/nmap
OS and Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 13.634 seconds
           Raw packets sent: 1818 (83.800KB) | Rcvd: 1792 (85.654KB)

---

### Post by netlogic on 2008-04-05
i'm not following you. this app has been around for many years now. most people are aware. that's what this app supposed to do. it is a network finger printing tool. it isn't only designed for a security penetration.

---

### Post by brian_p on 2008-04-05
> **netlogic said:**
> i'm not following you. this app has been around for many years now. most people are aware. that's what this app supposed to do. it is a network finger printing tool. it isn't only designed for a security penetration.

I think he is concerned about

22/tcp open ssh OpenSSH 4.6p1 Debian 5ubuntu0.2 (protocol 2.0)

giving information about the operating system being used. It's not the operation of nmap he is questioning.

---

### Post by netztier on 2008-04-05
> **zapcojake said:**
> It seems like that serves just as well to ID the OS regular OS detection.  Is this normal? If not should somebody be made aware? 


No need to run nmap for that, just telnet to port 22 of the machine you are running SSH on:

```

marc@cube:~$ **telnet blaze 22**
Trying 172.20.125.30...
Connected to blaze.roots-hell.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1.1
```

I don't think that we should worry about this. Very probably, this string is customizable in SHH's source code and you could configure/compile a version with a less meaningful output, should it be of importance to you or the environment you're working in.

regards

Marc

---

### Post by The Tronyx on 2008-04-05
As someone above pointed out, Nmap is also used for service and OS identification.  It is not necessarily the source code that identifies the service.  Fingerprinting can be done either by analyzing a known service response string or getting the banner for the service.  The banner can be changed.  The individual above me who used telnet to identify the service is grabbing a banner.

---

### Post by zapcojake on 2008-04-05
Is is the fact that OpenSSH gives the OS away.  I didn't know if that was always the case or not.  It would seem more secure to me if it did not.

---

### Post by netlogic on 2008-04-05
If you are patched with a good security management, why do you worry?
People get hacked, because they aren't patched and they use dictionary passwords. Something like ssh will get patched within 24 to 48hrs with a known vulnerability.  Many people watch others codes in the open source world. I don't know people are so paranoid here. It isn't like windows that you have to wait entire month for patches. If you are truly paranoid, search the net for how to make a ssh key. Also, how many ssh servers are out there? Are you saying, you rather have it called something else? Like Nike ssh?

---

### Post by zapcojake on 2008-04-05
I'm not worried, I just thought I would make it known in case it had not happened before.

---

### Post by netlogic on 2008-04-05
Most of the time, people are looking for Windows machines and outdated distro machines. Ubuntu is very active and things are always patched.  It is a new Debian reborned in a bizarre way.

If you have a ssh paranoia
1.  change your password very frequently such as every month, 
2.  use ssh key with least 16 characters passphrase.
3.  always patch
4. move your ssh port to the higher port, but nmap will usually find it.

People who work on the Openssh project take security seriously. I wouldn't worry. The entire opensource community depends on them.

---

