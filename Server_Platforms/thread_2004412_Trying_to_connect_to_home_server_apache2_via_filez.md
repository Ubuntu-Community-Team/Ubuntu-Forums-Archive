---
title: "Trying to connect to home server apache2 via filezilla"
date: 2012-06-15
forum: Server Platforms
---

### Post by csharp100 on 2012-06-15
Hello everyone, 
I have set up a home server using Ubuntu Server 64 bit. I have apache2, php5, mysql and shorewall installed. As far as I can tell they are all installed correctly. I set this server up using a tutorial [here]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/"). I have typed into my browser the addy for my server and I get the "It Works!" page with no problems, although when I reload the page it seems to take forever to come back up.
 
My problem is when I try to connect via filezilla I get the following:
```

[SIZE=2]Status: Connecting to 192.168.x.xx...[/SIZE]
[COLOR=#008000][SIZE=2][COLOR=#008000]Response: fzSftp started[/COLOR][/SIZE][/COLOR]
[COLOR=#000080][COLOR=#000080][SIZE=2]Command: open [/SIZE][EMAIL="clint@192.168.x.xx"][SIZE=2]clint@192.168.x.xx[/SIZE][/EMAIL][SIZE=2] 22[/SIZE][/COLOR][/COLOR]
[COLOR=#ff0000][SIZE=2][COLOR=#ff0000]Error: Connection timed out[/COLOR][/SIZE][/COLOR]
[COLOR=#ff0000][SIZE=2][COLOR=#ff0000]Error: Could not connect to server[/COLOR][/SIZE][/COLOR]
[SIZE=2]Status: Waiting to retry...[/SIZE]
[SIZE=2]Status: Delaying connection for 1 second due to previously failed connection attempt...[/SIZE]
[SIZE=2]Status: Connecting to 192.168.x.xx...[/SIZE]
[COLOR=#008000][SIZE=2][COLOR=#008000]Response: fzSftp started[/COLOR][/SIZE][/COLOR]
[COLOR=#000080][COLOR=#000080][SIZE=2]Command: open [/SIZE][EMAIL="clint@192.168.x.xx"][SIZE=2]clint@192.168.x.xx[/SIZE][/EMAIL][SIZE=2] 22[/SIZE][/COLOR][/COLOR]
[SIZE=1][COLOR=#ff0000][SIZE=1][COLOR=#ff0000][SIZE=2]Error: Connection timed out[/SIZE][/COLOR]
[COLOR=#ff0000][SIZE=2]Error: Could not connect to server[/SIZE][/COLOR]
[/SIZE][/COLOR][/SIZE]
```[SIZE=1][COLOR=#ff0000]
 
[SIZE=1][COLOR=#ff0000][SIZE=2][COLOR=#000000]I did set up a site in filezilla's sitemanager using SFTP. I am hoping someone can tell me what I might do to solve this.[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#000000]A few more details:[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#000000]Server: Dell 1800 with Ubuntu Server installed[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]Desktop: Dell with Windows 7 Pro[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]Both server and desktop are connect via wire to Motorola SURFBoard Cable Modem/Router[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#000000]I am accessing the server inside my home through the Cable Modem/Router[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#000000]If you need any more info please let me know.[/COLOR][/SIZE]
 
[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by kanikilu on 2012-06-15
This may seem obvious, but you didn't specify, so just to be sure: have you installed the SSH server yet? If not, you need to do that first.

```
sudo apt-get install openssh-server
```

---

### Post by csharp100 on 2012-06-15
> **kanikilu said:**
> This may seem obvious, but you didn't specify, so just to be sure: have you installed the SSH server yet? If not, you need to do that first.
 
```
sudo apt-get install openssh-server
```
 
Yes, openssh is installed. As a matter of fact I can SSH to the server within the server. Now when I try to ssh from Windows using SSH Secure Shell, I get the following error message:
```

The host '192.168.x.xx' is unreachable. The host may be down, or may be a problem
with the network connection.  Sometimes such problems can also be caused by a 
misconfigured firewall.

```
 
In which I also tried the above and filezilla with shorewall stopped.

---

### Post by kanikilu on 2012-06-15
Ok, it seems like port 22 is not open if you can ping it, but can't  SSH or sFTP to it from your Windows PC. I know you said you disabled the firewall, so, I'm not really sure what to suggest. Can you scan the host and see what ports are in fact open?

[http://nmap.org/download.html#windows](http://nmap.org/download.html#windows)

---

### Post by csharp100 on 2012-06-15
> **kanikilu said:**
> Ok, it seems like port 22 is not open if you can ping it, but can't SSH or sFTP to it from your Windows PC. I know you said you disabled the firewall, so, I'm not really sure what to suggest. Can you scan the host and see what ports are in fact open?
 
[http://nmap.org/download.html#windows](http://nmap.org/download.html#windows)
 
This is what I got assuming I did it correctly:
```

Starting Nmap 6.00 ( [http://nmap.org](http://nmap.org) ) at 2012-06-15 18:15 Central Daylight Time
NSE: Loaded 93 scripts for scanning.
NSE: Script Pre-scanning.
Initiating ARP Ping Scan at 18:15
Scanning 192.168.0.19 [1 port]
Completed ARP Ping Scan at 18:15, 0.41s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 18:15
Completed Parallel DNS resolution of 1 host. at 18:15, 0.34s elapsed
Initiating SYN Stealth Scan at 18:15
Scanning 192.168.0.19 [65535 ports]
SYN Stealth Scan Timing: About 22.52% done; ETC: 18:17 (0:01:47 remaining)
SYN Stealth Scan Timing: About 56.96% done; ETC: 18:17 (0:00:46 remaining)
Completed SYN Stealth Scan at 18:16, 91.21s elapsed (65535 total ports)
Initiating Service scan at 18:16
Initiating OS detection (try #1) against 192.168.0.19
Retrying OS detection (try #2) against 192.168.0.19
NSE: Script scanning 192.168.0.19.
Initiating NSE at 18:17
Completed NSE at 18:17, 0.00s elapsed
Nmap scan report for 192.168.0.19
Host is up (0.0019s latency).
Not shown: 65534 filtered ports
PORT    STATE  SERVICE VERSION
113/tcp closed ident
MAC Address: 00:14:22:0A:FD:5A (Dell)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop
 
TRACEROUTE
HOP RTT     ADDRESS
1   1.86 ms 192.168.0.19
 
NSE: Script Post-scanning.
Read data files from: C:\Program Files\Nmap
OS and Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 99.71 seconds
           Raw packets sent: 131178 (5.776MB) | Rcvd: 78 (3.108KB)

```
 
It seems like no ports are open. I put the ip addy of 190.162.x.xx in the target window of the program you linked me to and did an intese scan, all TCP ports. Is that what it seems to you?

---

### Post by kanikilu on 2012-06-15
Yeah, it seems like the ports aren't open. Are you sure the firewall is disabled? Going by the IP address (192.168...), it seems to be on an internal/home network, so the firewall shouldn't really be necessary, at least for now. Maybe try removing it??

I've never used shorewall before, so can't really help troubleshoot it, but if it creates iptables rules, you can check them with: ```
sudo iptables -L
```

---

### Post by csharp100 on 2012-06-16
> **kanikilu said:**
> Yeah, it seems like the ports aren't open. Are you sure the firewall is disabled? Going by the IP address (192.168...), it seems to be on an internal/home network, so the firewall shouldn't really be necessary, at least for now. Maybe try removing it??
 
I've never used shorewall before, so can't really help troubleshoot it, but if it creates iptables rules, you can check them with: ```
sudo iptables -L
```
 
I believe the problem was with shorewall. I am sure I did not configure it correctly. What I did was reinstall Ubuntu Server with the openssh and lamp packages and it is going now.

---

