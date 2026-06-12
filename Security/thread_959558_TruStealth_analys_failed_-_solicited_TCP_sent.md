---
title: "TruStealth analys failed - solicited TCP sent"
date: 2008-10-26
forum: Security
---

### Post by elixirium on 2008-10-26
I ran the TruStealth analysis at [http://www.grc.com/intro.htm]("http://www.grc.com/intro.htm") and this is what I got on the common ports:

```
GRC Port Authority Report created on UTC: 2008-10-26 at 19:08:26

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

    0 Ports Open
   26 Ports Closed
    0 Ports Stealth
---------------------
   26 Ports Tested

ALL PORTS tested were found to be: CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.
```

and for the service ports:

```
GRC Port Authority Report created on UTC: 2008-10-26 at 19:12:04

Results from scan of ports: 0-1055

    0 Ports Open
 1055 Ports Closed
    1 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

The port found to be STEALTH was: 646

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.
```

I'm sure it could have been far worse but this might represent a security issue. I am using (g)ufw as firewall.

I started using ubuntu 2 weeks ago so I am a newbie.

What should I do to get a perfect TruStealth rating?

I welcome and appreciate any help.

---

### Post by Nepherte on 2008-10-26
Actually, you're perfectly save. Whether it is stealth or closed doesn't really matter.

Btw if you're behind a router, the test scans your router instead of the firewall of your computer.

---

### Post by cariboo on 2008-10-26
You do realize the [www.grc.com](www.grc.com) is just a site set up to sell the owners products. Was this test run on your computer or on your router. If you are really concerned about this, run something like this:

```
 sudo nmap -sS -sV -O -p- -PI -PT locallhost
```

This is the output I get from the only Windows XP computer on my network:

```
Starting Nmap 4.62 ( http://nmap.org ) at 2008-10-26 14:13 PDT
Interesting ports on 192.168.1.104:
Not shown: **65532 closed ports**
PORT    STATE SERVICE      VERSION
135/tcp open  msrpc        Microsoft Windows RPC
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds Microsoft Windows XP microsoft-ds
MAC Address: 00:14:2A:EF:C2:18 (Elitegroup Computer System Co.)
Device type: general purpose
Running: Microsoft Windows XP
OS details: Microsoft Windows 2000 SP4, or Windows XP SP2 or SP3
Network Distance: 1 hop
Service Info: OS: Windows

Host script results:
|_ Discover OS Version over NetBIOS and SMB: Windows XP

OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 25.242 seconds
```

Note the number of ports check, I have bolded it, GRC only checks the first 1024 ports.

I have file and print sharing enable, thats why there are a couple of ports open. This is on my internal network behind a linksys wrt54gs router.

Nmap is available in the repositories and there is a gui called zenmap for those that are keybaord challenged.

Jim

---

### Post by bwallum on 2008-10-27
The best way to hide your pc on the internet is to be in stealth mode. To achieve this you could use NAT (network address translation) on your router. Most routers have NAT capability. Turn it on, ensure the default server is set to 0.0.0.0 (unless you know otherwise) and you will achieve full stealth rating. Closed rating is ok but it does mean that an attacker can see you and will mean that you are likely to be targeted more than one they can't see.

---

### Post by elixirium on 2008-10-28
> **Nepherte said:**
> Actually, you're perfectly save. Whether it is stealth or closed doesn't really matter.

Btw if you're behind a router, the test scans your router instead of the firewall of your computer.
You're propably right, i just want a perfect Stealth. In these days you need all the sucurity you can get. I'm not sure whether i tested my router or computer..

> **cariboo907 said:**
> You do realize the [www.grc.com](www.grc.com) is just a site set up to sell the owners products. Was this test run on your computer or on your router. If you are really concerned about this, run something like this:

```
 sudo nmap -sS -sV -O -p- -PI -PT locallhost
```

This is the output I get from the only Windows XP computer on my network:

```
Starting Nmap 4.62 ( http://nmap.org ) at 2008-10-26 14:13 PDT
Interesting ports on 192.168.1.104:
Not shown: **65532 closed ports**
PORT    STATE SERVICE      VERSION
135/tcp open  msrpc        Microsoft Windows RPC
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds Microsoft Windows XP microsoft-ds
MAC Address: 00:14:2A:EF:C2:18 (Elitegroup Computer System Co.)
Device type: general purpose
Running: Microsoft Windows XP
OS details: Microsoft Windows 2000 SP4, or Windows XP SP2 or SP3
Network Distance: 1 hop
Service Info: OS: Windows

Host script results:
|_ Discover OS Version over NetBIOS and SMB: Windows XP

OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 25.242 seconds
```

Note the number of ports check, I have bolded it, GRC only checks the first 1024 ports.

I have file and print sharing enable, thats why there are a couple of ports open. This is on my internal network behind a linksys wrt54gs router.

Nmap is available in the repositories and there is a gui called zenmap for those that are keybaord challenged.

Jim
Well, i'll keep in mind that grc is trying to sell me something, but i have read about other people getting perfect stealth rating.

Anyways, this is what I got when ```
 sudo nmap -sS -sV -O -p- -PI -PT locallhost
``` was entered:

```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-10-28 19:00 CET
Failed to resolve given hostname/IP: locallhost.  Note that you can't use '/mask' AND '1-4,7,100-' style IP ranges
WARNING: No targets were specified, so 0 hosts scanned.
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.381 seconds
```
Obviously, I have done something wrong.

> **bwallum said:**
> The best way to hide your pc on the internet is to be in stealth mode. To achieve this you could use NAT (network address translation) on your router. Most routers have NAT capability. Turn it on, ensure the default server is set to 0.0.0.0 (unless you know otherwise) and you will achieve full stealth rating. Closed rating is ok but it does mean that an attacker can see you and will mean that you are likely to be targeted more than one they can't see.
I'm not an expert at internet security, but I know that invisibility is worth it's "weight" in gold. I'll see if my router has NAT compatibility.

---

### Post by bwallum on 2008-10-28
> I'm not an expert at internet security, but I know that invisibility is worth it's "weight" in gold. I'll see if my router has NAT compatibility.To check your router you can use a browser and type in the ip address. Typically this will be 192.168.1.1 or 192.168.2.1 or 10.0.0.1 or something near. Your machines ip address will give you a clue```
ifconfig
```will give your machines inet address, mine is 192.168.1.15 for example. That tells me my router is probably on 192.168.1.1 (which it actually is).

Once you have found the router you will be asked to log on. You need to know the username (admin is a common default) and the password (some have no password, some have admin, there are a lot of variations). there is no way around this, you must know. Check out the router's spec on Google to find out the default username and password.

Once in look for NAT. Make sure it's on.

---

### Post by Sarmacid on 2008-10-28
Only need 1 l
```
 sudo nmap -sS -sV -O -p- -PI -PT localhost
```

And to see your router
```
sudo route
```

---

### Post by cariboo on 2008-10-28
I made an error the nmap command should have the ip address instead of localhost.

Jim

---

