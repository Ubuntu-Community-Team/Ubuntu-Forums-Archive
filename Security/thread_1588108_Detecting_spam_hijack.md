---
title: "Detecting spam hijack"
date: 2010-10-04
forum: Security
---

### Post by TheBigB86 on 2010-10-04
Hi there,

I have just been cut-off from my internet connection, due to spam coming from my connection.
Suspicions go to my Ubuntu server as the other PC's are squeaky clean and the logs on the server are suspicious.

Pretty much every entry in /var/log/messages is a UFW block entry, which gives me the idea I was bruted by a bot-net of some sort.
Weird thing is also that mail logs are empty and the local mailboxes are gone.

Is there a way I could detect any malicious script running?

Thanks

---

### Post by davidvandoren on 2010-10-04
I don't know too much about it myself but you could start putting this into your Terminal and see what the output is
```
grep nobody /etc/passwd
```

---

### Post by TheBigB86 on 2010-10-04
```
grep nobody /etc/passwd
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
```
I'm not an expert, but my gut says there shouldn't be /bin/sh there?

---

### Post by davidvandoren on 2010-10-04
your output is by default and as far I have figured it's dumb to be this way.

I got this from somewhere else 

```
sudo usermod -s /bin/nologin nobody
```
or
```
sudo usermod -s /bin/false nobody
```

will change that 

but better ask again since I am not an expert

---

### Post by davidvandoren on 2010-10-04
next you could run the netstat commands

```
netstat -pt
```

Look up what other netstat optione are available netstat -a 
netstat -n etc.

---

### Post by SeijiSensei on 2010-10-04
Are you running an SMTP server like Postfix or sendmail?  Are you sure it's locked down sufficiently so it's not an "open relay?"  Check your mail logs and make sure you're only sending out mail from valid addressees.  In general, having an open relay exploited is probably much more common on a Linux box than being incorporated into a botnet.

You have removed the server from the network, yes?

Take a good look in /tmp and make sure you know the origin of every file you see there.  If you can put /tmp on its own partition, you can mark it noexec when mounted so that an exploit can't drop a script there and execute it.

---

### Post by TheBigB86 on 2010-10-04
> **davidvandoren said:**
> next you could run the netstat commands

```
netstat -pt
```Look up what other netstat optione are available netstat -a 
netstat -n etc.
There's not much there as my connection is cut off.
Only oddity is that there is an active connection to the DNS server (while there is no physical connection).

---

### Post by TheBigB86 on 2010-10-04
> **SeijiSensei said:**
> Are you running an SMTP server like Postfix or sendmail?  Are you sure it's locked down sufficiently so it's not an "open relay?"  Check your mail logs and make sure you're only sending out mail from valid addressees.  In general, having an open relay exploited is probably much more common on a Linux box than being incorporated into a botnet.

You have removed the server from the network, yes?

Take a good look in /tmp and make sure you know the origin of every file you see there.  If you can put /tmp on its own partition, you can mark it noexec when mounted so that an exploit can't drop a script there and execute it.
I did fool around with the sendmail configuration, but I never got it to actually send mail.
Would be epic if someone else did.

Could fetchmail do any harm?

Only things I don't recognize in /tmp are orbit-gdm and .ICE-unix.
Anyway I'm going to reinstall the system, it's not that big of a deal.

It might very well be the sendmail, but keep the suggestions coming.
Won't be reinstalling in two days.

If there would be a way to prove to the ISP it's on that system, that would be awesome.

Thanks so far :)

---

### Post by davidvandoren on 2010-10-04
Before running a server you should really now what you are doing.
Installing one and getting it to run might be easy. Securing it is a little bit more difficult and requires a lot of reading, which I am too lazy to do. 
At least make sure you turn the firewall on and configure it to let your mail go through. 
Also I looked around to see if there was an easy step by step tutorial around that let's people like you and me setup a server without serving the ****** industry right away but I didn't find one.

---

### Post by TheBigB86 on 2010-10-04
I'm good at messing up configurations, but I always have a firewall running.
UFW has everything blocked except a couple of services like OpenSSH, Apache, Samba.

That being said I'm starting to wonder whether UFW is sufficient and whether I should start limiting the ALLOW From-ranges.

---

### Post by SeijiSensei on 2010-10-04
Never grant unrestricted public access to sensitive services like OpenSSH or Samba.  Make sure sshd_config has root access turned off.  I also turn off password authentication and rely entirely on shared keys.  In general I also restrict inbound access to only hosts I trust and block the rest.  I write my own firewalling scripts, so I can't help you with other products.  But you can run

sudo iptables -L -nv

and see a complete list of the rules and policies.  If the default policy is ACCEPT, then you need to make sure the last rule in the INPUT chain denies all inbound traffic that doesn't meet a prior rule.  The last two rules should be something like 
```

iptables -A INPUT -j LOG
iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited

```
which will log all non-matching packets and reject them.

I recommend you install a copy of nmap (from the repositories, also a Windows version) and scan your server from an external machine after you have it set up.  nmap will identify all the open ports it finds.  Be sure you know why each service it identifies is needed and turn off any that are not.

In /tmp, orbit-gdm and .ICE-unix are fine; on KDE machines you'll see kde-* directories as well.  Just make sure that none of the files belong to the nobody user or www-data if you run Apache, and make sure that any files (not directories) you find don't have the execute bit ("x") set by typing "sudo ls -lR /tmp".

[QUOTE=TheBigB86]I did fool around with the sendmail configuration, but I never got it to actually send mail. Would be epic if someone else did.[/quote]

Spammers run robots all the time that do nothing but scan IP addresses, look to see if port 25 is open, then try to push mail through any machines they find.

And, once again, you have disconnected this machine from the Internet already, yes?

---

### Post by TheBigB86 on 2010-10-04
> **SeijiSensei said:**
> Never grant unrestricted public access to  sensitive services like OpenSSH or Samba.  Make sure sshd_config has  root access turned off.  I also turn off password authentication and  rely entirely on shared keys.  In general I also restrict inbound access  to only hosts I trust and block the rest.

Will look into the shared keys thing.
> **SeijiSensei said:**
> I recommend you install a copy of nmap (from the repositories, also a Windows version) and scan your server from an external machine after you have it set up.  nmap will identify all the open ports it finds.  Be sure you know why each service it identifies is needed and turn off any that are not.

Gonna try that.
> **SeijiSensei said:**
> And, once again, you have disconnected this machine from the Internet already, yes?
Yes, my ISP cut me off.

---

### Post by TheBigB86 on 2010-10-04
Intense scan, all TCP ports
```
Starting Nmap 5.21 ( http://nmap.org ) at 2010-10-04 23:11 W. Europe Daylight Time
NSE: Loaded 36 scripts for scanning.
Initiating ARP Ping Scan at 23:11
Scanning 192.168.1.190 [1 port]
Completed ARP Ping Scan at 23:11, 0.68s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 23:11
Completed Parallel DNS resolution of 1 host. at 23:11, 5.53s elapsed
Initiating SYN Stealth Scan at 23:11
Scanning 192.168.1.190 [65535 ports]
Discovered open port 139/tcp on 192.168.1.190
Discovered open port 445/tcp on 192.168.1.190
Discovered open port 80/tcp on 192.168.1.190
Discovered open port 39218/tcp on 192.168.1.190
SYN Stealth Scan Timing: About 19.84% done; ETC: 23:14 (0:02:05 remaining)
SYN Stealth Scan Timing: About 47.15% done; ETC: 23:14 (0:01:08 remaining)
Completed SYN Stealth Scan at 23:13, 108.06s elapsed (65535 total ports)
Initiating Service scan at 23:13
Scanning 4 services on 192.168.1.190
Completed Service scan at 23:13, 11.01s elapsed (4 services on 1 host)
Initiating OS detection (try #1) against 192.168.1.190
Retrying OS detection (try #2) against 192.168.1.190
NSE: Script scanning 192.168.1.190.
NSE: Starting runlevel 1 (of 1) scan.
Initiating NSE at 23:13
Completed NSE at 23:14, 40.00s elapsed
NSE: Script Scanning completed.
Nmap scan report for 192.168.1.190
Host is up (0.00055s latency).
Not shown: 65522 filtered ports
PORT      STATE  SERVICE     VERSION
22/tcp    closed ssh
80/tcp    open   http        Apache httpd 2.2.14 ((Ubuntu))
|_html-title: Index of /
139/tcp   open   netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp   open   netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
631/tcp   closed ipp
5900/tcp  closed vnc
5901/tcp  closed vnc-1
5902/tcp  closed vnc-2
5903/tcp  closed vnc-3
5904/tcp  closed unknown
8080/tcp  closed http-proxy
9091/tcp  closed unknown
39218/tcp open   ssh         OpenSSH 5.3p1 Debian 3ubuntu4 (protocol 2.0)
| ssh-hostkey: 1024 xxxx (DSA)
|_2048 xxxx (RSA)
MAC Address: 00:15:F2:25:67:04 (Asustek Computer)
Device type: WAP|general purpose|broadband router
Running (JUST GUESSING) : Linksys Linux 2.4.X (96%), Linux 2.4.X|2.6.X  (96%), OpenBSD 4.X (95%), Belkin embedded (90%), D-Link Linux 2.4.X  (89%), Netgear embedded (89%)
Aggressive OS guesses: OpenWrt White Russian 0.9 (Linux 2.4.30) (96%),  OpenWrt 0.9 - 7.09 (Linux 2.4.30 - 2.4.34) (96%), OpenWrt Kamikaze 7.09  (Linux 2.6.22) (96%), OpenBSD 4.3 (95%), Linux 2.6.21 (92%), Linux  2.6.18-8.el5 (Red Hat Enterprise Linux 5) (91%), Linux 2.6.20 (91%),  Linux 2.6.20 (Ubuntu, x86_64) (91%), Linux 2.6.22 (91%), Linux 2.6.22  (Ubuntu, x86) (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop
Service Info: OS: Linux

Host script results:
| nbstat:  
|   NetBIOS name: MENDHAK, NetBIOS user: <unknown>, NetBIOS MAC: <unknown>
|   Names
|     MENDHAK<00>          Flags: <unique><active>
|     MENDHAK<03>          Flags: <unique><active>
|     MENDHAK<20>          Flags: <unique><active>
|     \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|     WORKGROUP<1d>        Flags: <unique><active>
|     WORKGROUP<1e>        Flags: <group><active>
|_    WORKGROUP<00>        Flags: <group><active>
|_smbv2-enabled: Server doesn't support SMBv2 protocol
| smb-os-discovery:  
|   OS: Unix (Samba 3.4.7)
|   Name: Unknown\Unknown
|_  System time: 2010-10-04 23:14:05 UTC+2

HOP RTT     ADDRESS
1   0.55 ms 192.168.1.190
```
39218 -> SSH port
5900 - 5904 -> VNC ports
631 -> CUPS web interface
9091 -> Transmission web interface
8080 -> SABnzbd web interface
445 + 139 -> Samba ports
80 -> Apache

22 has nothing running, SSH port is 39218.

---

### Post by TheBigB86 on 2010-10-15
I was reconnected pretty quickly

Now I found time to reinstall the server and I've configured shared key authentication.
I need the server to be accessible pretty much anywhere, so I'm not restricting inbound connections.
Though I have limited the number of ports that are accessible through the router.
(used to be DMZ; now a couple of port forwards)

> **SeijiSensei said:**
> In general, having an open relay exploited is probably much more common on a Linux box than being incorporated into a botnet.
[Here's]("http://pastebin.com/HsNVnC1C") a fraction of the UFW logs if you're curious.


Anyway thanks for all the suggestions :D

---

### Post by SeijiSensei on 2010-10-16
The logs show continuous repeated attempts to connect via UDP to port 51413/udp on October 3rd.  Did you run a UDP scan with nmap as well?  (nmap -sU rather than nmap -sT or -sS)

---

