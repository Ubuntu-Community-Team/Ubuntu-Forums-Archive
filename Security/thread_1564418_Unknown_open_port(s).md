---
title: "Unknown open port(s)"
date: 2010-08-30
forum: Security
---

### Post by KonfuseKitty on 2010-08-30
I have a fairly clean Lucid install with no servers, firewall enabled, and have also recently got Privoxy for added security. I think with this setup I should have no ports open to the outside. Yet, a scan of my IP with nmap reveals:

```
Not shown: 65532 closed ports
Reason: 65532 resets
PORT      STATE    SERVICE    REASON      VERSION
23/tcp    filtered telnet     no-response
8080/tcp  filtered http-proxy no-response
59153/tcp open     tcpwrapped syn-ack
```

I've done some searches, and from other people's prior experience, it may be that port 23 is from my dsl modem/router, but I can't turn it off as there's no setting for it. I've denied it with ufw, but it still shows up in the scan. Port 8080 is most likely Privoxy, though I'm surprised it comes up as I thought it would only listen internally. Which leaves the strange 59153 - what is that?

I've also run netstat -panel, with this result:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      115        4791        1199/privoxy    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      0          4829        1244/cupsd      
tcp        1      0 192.168.1.34:34268      91.189.89.31:80         CLOSE_WAIT  1000       38065       2359/gvfsd-http 
tcp        1      0 192.168.1.34:34273      91.189.89.31:80         CLOSE_WAIT  1000       38347       2359/gvfsd-http 
tcp        1      0 192.168.1.34:44484      91.189.89.31:80         CLOSE_WAIT  1000       53798       2359/gvfsd-http 
tcp        1      0 192.168.1.34:58076      91.189.89.31:80         CLOSE_WAIT  1000       24493       2359/gvfsd-http 
tcp        1      0 192.168.1.34:44481      91.189.89.31:80         CLOSE_WAIT  1000       53668       2359/gvfsd-http 
tcp        1      0 192.168.1.34:53110      91.189.89.31:80         CLOSE_WAIT  1000       30387       2359/gvfsd-http 
tcp        1      0 192.168.1.34:34274      91.189.89.31:80         CLOSE_WAIT  1000       38358       2359/gvfsd-http 
tcp6       0      0 ::1:631                 :::*                    LISTEN      0          4828        1244/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          12407       1945/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           104        4646        1012/avahi-daemon: 
udp        0      0 0.0.0.0:56452           0.0.0.0:*                           104        4647        1012/avahi-daemon:
```

It all seems fine, although I don't understand what dhclient and avahi-daemon do. And port 59153 doesn't seem to be showing up. How can I establish what this is and whether it's a security risk?

---

### Post by anomie on 2010-08-30
Some of those netstat flags you're using supercede others. :) Since you're scanning tcp ports, try simply: 
**$ sudo netstat -ltnp**

At a glance you have privoxy and cups listening. (No surprises, right?) Note that dhclient and avahi-daemon (both udp) are for DHCP client address aquisition and aspects of network client managment, respectively. See their manpages. Also read [this entry](http://en.wikipedia.org/wiki/Zero_configuration_networking) for more info on the latter. Likely nothing weird there. 

No idea about the syn-ack response on tcp port 59153.

---

### Post by scorp123 on 2010-08-30
> **anomie said:**
>  No idea about the syn-ack response on tcp port 59153. UPnP maybe? Maybe a P2P program (Frostwire? BitTorrent? Vuze? ...) running somewhere? They usually use such high ports e.g. to avoid getting blocked by some ISP's who usually block the traditional ports for P2P traffic (e.g. 6881).

Just guessing here.

Another good way to check which process may have ports open is using the "**lsof**" tool, e.g.
```
sudo lsof -n -i -P
```

---

### Post by BkkBonanza on 2010-08-30
These comments are just meant to be helpful suggestions.

It's unclear from your post whether your nmap scan is of your "public ip" and hence, your router, or of your "private ip" and hence, your local machine. There is a big difference as the first will tell you how your router is behaving in regard to the internet, and the second only tells you how your machine is behaving in regard to your LAN and router. 

I think you may have done the public scan based on the output. There really should be a way to disable telnet for public access on your router. In fact, I would say if there isn't then you should get rid of it and get a new one. It may not allow disabling it but there usually will be an option for "public access on/off". If you really can't then be sure you use a very strong password because it will get targetted and also if you ever access it from "outside" then it can be listened to, in plain text. Betters routers support ssh instead of telnet.

If you scanned the public ip (router) then you will not see a match up with the netstat command because they tell you info about different machines. Usually the filtered state indicates the port is blocked ie. it can tell it is there but not if open/closed. Which is probably ok. If your router forwards 8080 to 8118 on your machine then that could be privoxy, but otherwise I see no indication. Just because the numbers are similar doesn't mean they are related, and in this case they are for ports on different devices (it appears).

dhclient is used to update a service like dyn-dns with a dynamic ip address and allows you to use a domain name to access the ip even when it changes. If you have this feature built into your router (many do) then you wouldn't also need it on the local machine.

privoxy should only be listening on your local machine, not on the public/outside interface. So there is no reason why it would appear on a scan of the public IP. If it did it would be a security concern as anyone publicly could proxy through it and you don't want that. (I don't believe it is in this case either - probably 8080 on the router is for the web control panel but it seems to be blocked).

---

### Post by an0dos on 2010-08-30
I don't know if this applies to you, but you need to run nmap from a different computer than the one you are scanning.

---

### Post by KonfuseKitty on 2010-08-31
Thank you all! To clarify, the nmap scan is of my outside IP. Scanning 192.168.1.1 gives similar results. This is on my own computer, I don't have access to another computer to perform the scan remotely.

Running "sudo lsof -n -i -P" I get this, very similar to netstat:

```
COMMAND    PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae 1058   avahi   13u  IPv4   4802      0t0  UDP *:5353 
avahi-dae 1058   avahi   14u  IPv4   4803      0t0  UDP *:48570 
dhclient  1093    root    5w  IPv4   4721      0t0  UDP *:68 
privoxy   1239 privoxy    4u  IPv4   4877      0t0  TCP 127.0.0.1:8118 (LISTEN)
cupsd     1292    root    6u  IPv6   4984      0t0  TCP [::1]:631 (LISTEN)
cupsd     1292    root    7u  IPv4   4985      0t0  TCP 127.0.0.1:631 (LISTEN)
```

Are these lists by netstat and lsof exhaustive, is there nothing else that could have open ports on the computer? Meaning any other open ports are router's?

A UDP scan of 192.168.1.1 (public IP scan takes too long as it goes through the firewall) reveals more open ports:

```
Interesting ports on *** (192.168.1.1):
Not shown: 65530 closed ports
Reason: 65530 port-unreaches
PORT      STATE         SERVICE REASON       VERSION
53/udp    open          domain  udp-response
67/udp    open|filtered dhcps   no-response
520/udp   open|filtered route   no-response
1900/udp  open|filtered upnp    no-response
32768/udp open|filtered omad    no-response
```

When I ran this scan last night, it also reported three more ports open, at 463321 463322 (if I remember right) and at 56400. But the first two in the list above, 53 and 67 weren't showing as open. So it's clear the open ports keep changing and I probably can't specifically close each of them with ufw rules, I can only hope the overall deny policy catches them all. Is there any chance ufw may let traffic through despite the deny setting?

How much of a risk is the router's telnet port, if ufw is blocking it?

---

### Post by KonfuseKitty on 2010-08-31
> **BkkBonaza said:**
> There really should be a way to disable telnet for public access on your router. In fact, I would say if there isn't then you should get rid of it and get a new one. It may not allow disabling it but there usually will be an option for "public access on/off". If you really can't then be sure you use a very strong password because it will get targetted and also if you ever access it from "outside" then it can be listened to, in plain text. Betters routers support ssh instead of telnet.


There is a setting to enable hosting of some sort, with a long menu of applications one can choose, including Apache and other "server-type things", but mostly games. Would that be done through telnet?


I'm not sure how I could replace the router as it belongs to the phone company. I guess I could ring them and tell them to send a new one sans telnet...

---

### Post by BkkBonanza on 2010-08-31
If you know the make/model# I could probably find out if you can disable telnet (via google). You can likely replace the router all on your own and the phone co. would never know. There would be some adsl settings that need to be copied over correctly. In the past I've been given free phone co. modems and just used my own instead. I suppose it may depend on the company though - some are known for being restrictive.

I think you still have confusion between your router and your machine. At least I do about what you are saying. UFW doesn't do anything on your router, (unless your desktop and router are the same machine). So using ufw to block ports on your router doesn't make sense - it only blocks ports on your desktop. Likewise blocking ports on your router has no effect or bearing on the open ports on your desktop. Though, of course, for a hacker to gain access to your PC they have to get through both the router and ufw on your PC.

Scanning the 192.168.1.1 (your router right?) makes little sense because you are scanning the private inside port of the router. You have to scan the router from the public IP because that is the side that is of interest to hackers. It may be slow but that's because nmap will timeout on "dropped" ports, which takes a long time. If the ports were open/closed it would be fairly fast because the router is responding. But ideally you want most ports to be "dropping" since that doesn't even expose that the router exists on the net. A good compromise is to use [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) online port scanner. There's also good info to read at that site.

---

### Post by KonfuseKitty on 2010-08-31
I've gone trough the modem/router settings again, and note that the Remote Access feature is disabled. I think this uses telnet. I have also disabled the UPnP feature and another thing to do with TV service (don't really know why it's there as this is an ADSL modem, but the telco does offer cable TV).

I have re-run all the commands to have everything in one place. (The only thing I haven't yet done is UDP scan over public IP.) It's clear the changes haven't made any difference. Further, I don't understand why TCP scans of both public IP and the router (192.169.1.1) are so similar if the devices being scanned are different. And the question remains, what is port 59153 doing and is it vulnerable?

ShieldsUp! reports ports 0 and 23 as stealth, the rest of the first 1056 ports as closed.

sudo nmap -p 1-65535 -sT -sV --reason 192.168.1.1:

```
Not shown: 65532 closed ports
Reason: 65532 conn-refused
PORT      STATE SERVICE    REASON  VERSION
23/tcp    open  telnet     syn-ack Cisco or Edge-core switch telnetd
80/tcp    open  tcpwrapped syn-ack
59153/tcp open  tcpwrapped syn-ack
```

sudo nmap -p 1-65535 -sT -sV --reason (public IP): 

```
Not shown: 65532 closed ports
Reason: 65532 conn-refused
PORT      STATE    SERVICE    REASON      VERSION
23/tcp    filtered telnet     no-response
8080/tcp  filtered http-proxy no-response
59153/tcp open     tcpwrapped syn-ack
```

sudo nmap -p 1-65535 -sT -sV --reason localhost: 

```
Not shown: 65533 closed ports
Reason: 65533 conn-refused
PORT     STATE SERVICE    REASON  VERSION
631/tcp  open  ipp        syn-ack CUPS 1.4
8118/tcp open  http-proxy syn-ack Privoxy http proxy 3.0.16
```

sudo nmap -p 1-65535 -sU -sV --reason 192.168.1.1: 

```
Not shown: 65531 closed ports
Reason: 65531 port-unreaches
PORT      STATE         SERVICE REASON       VERSION
53/udp    open          domain  udp-response
67/udp    open|filtered dhcps   no-response
520/udp   open|filtered route   no-response
32768/udp open|filtered omad    no-response
```

sudo nmap -p 1-65535 -sU -sV --reason localhost: 

```
Not shown: 65532 closed ports
Reason: 65532 port-unreaches
PORT      STATE         SERVICE  REASON      VERSION
68/udp    open|filtered dhcpc    no-response
5353/udp  open|filtered zeroconf no-response
43648/udp open|filtered unknown  no-response
```

sudo netstat -ltnp:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      1211/privoxy    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1260/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1260/cupsd
```

sudo lsof -n -i -P:

```
COMMAND    PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae 1027   avahi   13u  IPv4   4613      0t0  UDP *:5353 
avahi-dae 1027   avahi   14u  IPv4   4614      0t0  UDP *:43648 
privoxy   1211 privoxy    4u  IPv4   4784      0t0  TCP 127.0.0.1:8118 (LISTEN)
cupsd     1260    root    6u  IPv6   4812      0t0  TCP [::1]:631 (LISTEN)
cupsd     1260    root    7u  IPv4   4813      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient  2346    root    5w  IPv4  10332      0t0  UDP *:68
```

---

### Post by BkkBonanza on 2010-08-31
Looking at your various scans the only remaining item I think questionable is the port 59153 on the public ip of your router. 

tcpwrapped is a linux service that handles stuff to do with xinetd, which is related to handling dynamic port management when services start/stop. I usually disable xinetd on my servers because I don't like the idea of ports opening according to services being started, and it's one less vulnerability to worry about. But I don't know in the context of your router what it's actually doing or why. I would interpret this as meaning that nmap thinks this port is handled by tcpwrapped (whether or not it really is, is another question, nmap only guesses according to fingerprints or tables of usual defaults), and so maybe your router runs linux with xinetd as part of it's config. Which doesn't really answer anything about what to do about it.

I find it odd that most of the router's public ports report as closed rather than stealth but I guess that's just the way they set it up. I know on my router any port not opened is reported as stealth by ShieldsUp. But at least you know the public ports for telnet and the web control panel are not open.

---

### Post by OpSecShellshock on 2010-08-31
I'm just guessing, so take it as offered, but it looks to me like port 59153 (as it's open on the router but not the devices behind it as well as ending in 53) might be used for those situations where DNS gets routed over TCP instead of UDP (not sure if this still happens or not, but it used to happen when the query exceeded a certain byte size). Granted, that doesn't precisely make sense since I'd figure that should be on the server side rather than the client side. However, if an ISP's client allows 53 over UDP and blocks it over TCP, I could see where there would be situations that long queries would cause errors, and so the ISP would consider it more cost effective to ship the modem/routers with an alternate port, but one they'd still recognize.

Just a wild guess since so many alternate ports tend to end in the same digits as their reserved counterparts.

---

### Post by BkkBonanza on 2010-08-31
Seems plausible except that it would have to be open on the internal network rather than on the public external side. It's a bit disconcerting having it open to the world. DNS servers will often open tcp port 53 as well as udp port 53 to handle requests bigger than 512 bytes. Oddly this router doesn't seem to do that.

It is interesting it ends with ...53 though, as if a hint.

edit: my mistake, I see now it's open on both sides. So maybe that's related but it would mean any program would have to know what port to use so it's still quite odd.

---

### Post by an0dos on 2010-08-31
> **BkkBonaza said:**
> Seems plausible except that it would have to be open on the internal network rather than on the public external side. It's a bit disconcerting having it open to the world. DNS servers will often open tcp port 53 as well as udp port 53 to handle requests bigger than 512 bytes. Oddly this router doesn't seem to do that.

It is interesting it ends with ...53 though, as if a hint.

edit: my mistake, I see now it's open on both sides. So maybe that's related but it would mean any program would have to know what port to use so it's still quite odd.

For scanning your external ip you may want to use  [http://nmap-online.com/]("http://nmap-online.com/").

---

### Post by KonfuseKitty on 2010-09-01
Thanks, but I'm not keen to have my ports scanned by a site I don't know, so I haven't performed the nmap-online test. I've now performed similar scans from a different computer (a Mac) but using the same router and got the same results. I take it from this test and from what has been said here that the open port 59153 is most likely on the router. Assuming ufw is successfully denying all ports on the computer, what could an attacker do to an open port on the router? My password on the router (for accessing its settings) is strong, but is that good enough?

---

### Post by OpSecShellshock on 2010-09-01
> **KonfuseKitty said:**
> Thanks, but I'm not keen to have my ports scanned by a site I don't know, so I haven't performed the nmap-online test. I've now performed similar scans from a different computer (a Mac) but using the same router and got the same results. I take it from this test and from what has been said here that the open port 59153 is most likely on the router. Assuming ufw is successfully denying all ports on the computer, what could an attacker do to an open port on the router? My password on the router (for accessing its settings) is strong, but is that good enough?

Well, even if an attacker were able to crack the password for the administrative interface of your router, they'd have to do it from inside your LAN per the settings of the device itself. It isn't open to the web. So that's good.

Since you received the router from the ISP and it also evidently acts as the modem for their service, it's probably something that they have configured. It may be worth contacting their support staff to find out, but be warned that the first couple of people you talk to during that process will likely have absolutely no idea.

---

