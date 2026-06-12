---
title: "Open Ports"
date: 2010-04-10
forum: Security
---

### Post by Jeyaganeshdj on 2010-04-10
Hi,

  I installed Ubuntu 9.10 recently. I heard that there will be no open ports in the system unless I specifically open one. Please let me know how do I scan to find a open port in my system. Thanks..

---

### Post by lisati on 2010-04-10
One place to check is the Shields-up web site @ [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

(It's showing a "busy" screen at the moment for me)

---

### Post by Jeyaganeshdj on 2010-04-11
Hi, 
 I checked using the above url and this is my port scan status.

[I]GRC Port Authority Report created on UTC: 2010-04-12 at 02:56:46

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

    3 Ports Open
   17 Ports Closed
    6 Ports Stealth
---------------------
   26 Ports Tested

Ports found to be OPEN were: 21, 23, 80

Ports found to be STEALTH were: 25, 135, 139, 445, 1025, 5000

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.[/I]

Why do the system reply to the ping message.. Should it not discard it? Also how do I stealth my open ports?

---

### Post by robertcoulson on 2010-04-11
Jeyaganeshdj here is my OPEN PORT summary...Don't understand why you have so many open...???
Robert

---

### Post by 3rdalbum on 2010-04-11
Port 21 is for FTP, port 23 is for Telnet, and port 80 is for the web. What exactly are you running on your machine? If you are behind a router, are these ports being forwarded to another computer?

Ubuntu will not be listening to any of those ports by default.

Pings are not only harmless by themselves, they are also useful which is why Ubuntu, or your router, will usually reply to a ping. "Stealth" is also not terribly important either.

---

### Post by robertcoulson on 2010-04-11
3rdalbum...I hope you are talking to me, or I will look really stupid..I am using a router...Yes.
Robert

---

### Post by Jeyaganeshdj on 2010-04-12
Hi,

 How do I close my open ports and make the closed ones stealth??

---

### Post by karthick87 on 2010-04-12
Here is mine,

```
----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2010-04-12 at 18:23:26

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

[COLOR=Red]TruStealth: FAILED [/COLOR]- ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

----------------------------------------------------------------------
```Here [COLOR=Red]TruStealth [/COLOR]was [COLOR=Red]FAILED[/COLOR] why..?

---

### Post by 98cwitr on 2010-04-12
sudo apt-get install nmap
nmap -PN -p 1-65535 127.0.0.1

---

### Post by uRock on 2010-04-12
If you use nmap to scan yourself it will not show the proper results. To get true results you need to scan the system using another PC. For an example of this please see this recent thread- [http://ubuntuforums.org/showthread.php?t=1444825](http://ubuntuforums.org/showthread.php?t=1444825)
```
sudo ufw enable
``` will make your system invisible to the network.

---

### Post by Jeyaganeshdj on 2010-04-12
> **uRock said:**
> If you use nmap to scan yourself it will not show the proper results. To get true results you need to scan the system using another PC. For an example of this please see this recent thread- [http://ubuntuforums.org/showthread.php?t=1444825](http://ubuntuforums.org/showthread.php?t=1444825)
```
sudo ufw enable
``` will make your system invisible to the network.

even after using sudo ufw enable and when i tried to scan for open ports using grc I get the same error

GRC Port Authority Report created on UTC: 2010-04-12 at 02:56:46

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
119, 135, 139, 143, 389, 443, 445, 
1002, 1024-1030, 1720, 5000

3 Ports Open
17 Ports Closed
6 Ports Stealth
---------------------
26 Ports Tested

Ports found to be OPEN were: 21, 23, 80

Ports found to be STEALTH were: 25, 135, 139, 445, 1025, 5000

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
- NO unsolicited packets were received,
- A PING REPLY (ICMP Echo) WAS RECEIVED.

---

### Post by 98cwitr on 2010-04-12
cool, good point, from an external viewpoint. But regarding the OP, he wants to know what ports are open on his system. This will show him ALL the ports that are open...not just from another machine.

if you want to close the ports:

[http://ubuntuforums.org/showthread.php?t=378965](http://ubuntuforums.org/showthread.php?t=378965)

---

### Post by uRock on 2010-04-12
> **Jeyaganeshdj said:**
> even after using sudo ufw enable and when i tried to scan for open ports using grc I get the same error

GRC Port Authority Report created on UTC: 2010-04-12 at 02:56:46

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
119, 135, 139, 143, 389, 443, 445, 
1002, 1024-1030, 1720, 5000

3 Ports Open
17 Ports Closed
6 Ports Stealth
---------------------
26 Ports Tested

Ports found to be OPEN were: 21, 23, 80

Ports found to be STEALTH were: 25, 135, 139, 445, 1025, 5000

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
- NO unsolicited packets were received,
- A PING REPLY (ICMP Echo) WAS RECEIVED.

I don't know how you are getting those readings. Here are my readings and my ufw is disabled. My router is doing the filtering.

I think 3rdalbum may be right with thinking your router is forwarding those ports.

---

### Post by Jeyaganeshdj on 2010-04-14
Hi,

 I installed Ubuntu from the CD delivered by canonical.. so I think i didnt mess around anything while installing Ubuntu. Still I find open ports in my system and the closed ports is also not stealth.. how do i make all the ports stealth.. Thanks for your responses..

---

### Post by uRock on 2010-04-14
> **Jeyaganeshdj said:**
> Hi,

 I installed Ubuntu from the CD delivered by canonical.. so I think i didnt mess around anything while installing Ubuntu. Still I find open ports in my system and the closed ports is also not stealth.. how do i make all the ports stealth.. Thanks for your responses..

Stealth just means that there was no ICMP response packet to the port scanned.

Do you have another PC in your home that is running ubuntu or that can boot the LiveCD?

---

### Post by Jeyaganeshdj on 2010-04-14
No, I do not have another PC.. Why do I have open ports in my system?

---

### Post by uRock on 2010-04-14
I have no clue what you have installed or what has happened to your system to cause UFW to be nonfunctional and those ports to be open. I can enable ufw on one of my machines then go to another machine and run a port scan and come up empty handed every time.

I have just run some tests on my system using nmap which is a very strong network mapping system, and ssh to control one of my other machines remotely.

First I scanned the other PC using NMAP and it show the ports as listening.

Second I used ssh to connect to the other machine and enable ufw. Notice the warning that this may interrupt the connection.

Third, I ran another scan on the same PC as before an though it found the other system was up, it found no open or listening ports.

Fourth, I ran nmap to see what systems on my network were listening. Notice that the address used before returned no open ports.

Lastly I attempted to connect via ssh again. The other PC ignored the request.

________________________________________________________
rabbit@rabbit-desktop:~$ sudo nmap 127.0.0.11
[sudo] password for rabbit: 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-04-14 19:29 PDT
Interesting ports on 127.0.0.11:
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
MAC Address: 00:25:D3:7C:2C:D0 (AzureWave Technologies)

Nmap done: 1 IP address (1 host up) scanned in 1.98 seconds
rabbit@rabbit-desktop:~$ ssh xyz@127.0.0.11
xyz@127.0.0.11's password: 
Linux broken-windows 2.6.32-20-generic #30-Ubuntu SMP Mon Apr 12 15:19:41 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 (lucid)

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Checking for a new ubuntu release
No new release found


For official documentation, please visit:
 * [http://help.ubuntu.com/](http://help.ubuntu.com/)

27 packages can be updated.
0 updates are security updates.

Last login: Mon Apr 12 20:01:41 2010 from rabbit-desktop.local
xyz@broken-windows:~$ sudo ufw enable
[sudo] password for ronnie: 
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup
ronnie@broken-windows:~$ exit
logout
Connection to 127.0.0.11 closed.
rabbit@rabbit-desktop:~$ sudo nmap 127.0.0.11

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-04-14 19:31 PDT
All 1000 scanned ports on 127.0.0.11 are filtered
MAC Address: 00:25:D3:7C:2C:D0 (AzureWave Technologies)

Nmap done: 1 IP address (1 host up) scanned in 21.75 seconds
rabbit@rabbit-desktop:~$ sudo nmap 127.0.0.0/24

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-04-14 19:32 PDT
Interesting ports on 127.0.0.9:
Not shown: 996 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5900/tcp open  vnc

Interesting ports on 127.0.0.10:
Not shown: 995 filtered ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
2869/tcp  open  unknown
49156/tcp open  unknown
MAC Address: 00:24:2B:A7:1B:78 (Hon Hai Precision Ind.Co.)

All 1000 scanned ports on 127.0.0.11 are filtered
MAC Address: 00:25:D3:7C:2C:D0 (AzureWave Technologies)

Interesting ports on 127.0.0.12:
Not shown: 999 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh
MAC Address: 00:0F:B5:DD:BF:88 (Netgear)

Interesting ports on 127.0.0.14:
Not shown: 996 closed ports
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
49152/tcp open  unknown
49154/tcp open  unknown
MAC Address: 00:23:69:04:E1:5F (Cisco-Linksys)

Nmap done: 256 IP addresses (5 hosts up) scanned in 20.08 seconds
rabbit@rabbit-desktop:~$ ssh xyz@127.0.0.11
ssh: connect to host 127.0.0.11 port 22: Connection timed out

---

### Post by uRock on 2010-04-14
> **getyourkarthick said:**
> Here is mine,

```
----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2010-04-12 at 18:23:26

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

[COLOR=Red]TruStealth: FAILED [/COLOR]- ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   [COLOR="Blue"][SIZE="4"]- A PING REPLY (ICMP Echo) WAS RECEIVED.[/SIZE][/COLOR]

----------------------------------------------------------------------
```Here [COLOR=Red]TruStealth [/COLOR]was [COLOR=Red]FAILED[/COLOR] why..?

Because the ICMP PING reply was received. True stealth doesn't reply.

---

### Post by LeeDaugherty on 2010-04-15
Why has no one asked the most important question?  He said he was behind a router, his router has telnet, ftp, and web open.  Long story short, if that router is under your control, you need to do some serious config changes to it, and close all remote access, and at this point change passwords and the like.  And next time someone tells you to port-scan localhost with nmap, tell them to go port-scan themselves with two fingers.  First off, if you want to see what ports are open 'netstat -tunlap'  if it's on 127. it's listening locally.  If it's ::* 0.0.0.0 or your local IP, make sure it's something that should be listening on your local network.  If you want to check yourself, put another machine on your network and nmap between them.  NMap is the tool you want to use, and yes its confusing as hell, but it's the most flawless program under the sun.  and you can always just keep it easy and type nmap x.x.x.x or get zenmap.  And one other thing, good point uRock...open ports are one issue...if you are replying to ICMP requests, you aren't a sitting duck, but there isn't ever any point in brining attention to yourself.  If you can live without pinging yourself (and evryone should be able to), shut down most of your ICMP responses.  You'll live a longer life.

---

### Post by uRock on 2010-04-15
> **LeeDaugherty said:**
> He said he was behind a router, his router has telnet, ftp, and web open.
Just reread the whole thread, he/she never said that.

---

### Post by scottuss on 2010-04-15
> **uRock said:**
> Just reread the whole thread, he/she never said that.

Deleted

---

### Post by LeeDaugherty on 2010-04-15
Why are we splitting hairs...3rd or so post:

[I]Ports found to be OPEN were: 21, 23, 80

[/I]His router was responding to the port scan, which isn't a good sign.  Well depends on what your motives are I guess.  What router is sold with remote management ports open?

---

### Post by uRock on 2010-04-15
If the OP does have a router, it would be nice to know, so that NAT can be turned on. Most routers come with NAT or some other firewall already running by default.

---

### Post by LeeDaugherty on 2010-04-15
The NAT could be implied by the NMAP posting:

Interesting ports on 127.0.0.11:
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Since the 127 block is non-routable.  Even though .14 appears to be a router (NMap equipment detection through MAC address at the bottom).  And furthermore is confirmed since it has DHCP/53 and 80 for inside management.  Not the standard network layout, but there is nothing wrong with that!

---

### Post by rookcifer on 2010-04-15
> **98cwitr said:**
> sudo apt-get install nmap
nmap -PN -p 1-65535 127.0.0.1

Or you can do:

```
nmap -PN -sT -sU -p- 127.0.0.1
```

The -p- flag will do the same as 1-65535.  Also I specified to scan UDP as well as TCP.

---

### Post by uRock on 2010-04-15
> **LeeDaugherty said:**
> The NAT could be implied by the NMAP posting:

Interesting ports on 127.0.0.11:
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Since the 127 block is non-routable.  Even though .14 appears to be a router (NMap equipment detection through MAC address at the bottom).  And furthermore is confirmed since it has DHCP/53 and 80 for inside management.  Not the standard network layout, but there is nothing wrong with that!

I changed the addressing scheme in the post to 127.0.0.x to hide some of my internal info. I meant to use 172, but the sleep monster was kicking me last night. Yes, x.x.x.14 is my router. I try to throw curve balls at neighborhood thieves.

---

### Post by bodhi.zazen on 2010-04-15
IMO ShieldUP! is not such a great site.

First, if you have a router, it is scanning your router and not your Ubuntu machine.

Second "Stealth" is a made up term and unless you understand what it means it is meaningless.

"Stealth" mean iptables uses DROP rather then REJECT and your machine does not respond to a ping. "Stealth" is NOT more secure then a closed port, and DROP si not more secure then REJECT .

IMO you are better off stopping, understanding what you are doing, and scanning your box from a second machine on you LAN using either nmap or Zenmap. Zenmap is a graphical front end for nmap and is in the repositories.

You "close" a port either by stopping or removing the server or using iptables. For example, Apache uses port 80 by default.

So

```
sudo service apache2 stop
``` closes the port.

As does ```
sudo apt-get remove apache2
```

as does

```
sudo ufw enable
```

As does 

```
sudo iptables -A INPUT -p tcp --dport 80 -j DROP
```

As does

```
sudo iptables -A INPUT -p tcp --dport 80 -j REJECT
```

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by Jeyaganeshdj on 2010-04-19
Hi,

 Once i enabled the firewall on my router the grc site result shows all the ports were stealth.. I also scanned from another computer and find all my ports as stealth.. Thanks a lot..

---

### Post by uRock on 2010-04-19
Awesome!

---

