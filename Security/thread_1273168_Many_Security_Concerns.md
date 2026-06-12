---
title: "Many Security Concerns"
date: 2009-09-23
forum: Security
---

### Post by dvlchd3 on 2009-09-23
I followed the three sticky guides above to help increase security.

Installed snort-mysql with base (apache, mysql, php, etc)
Installed ossec with web interface
Installed AppArmor with several profiles
Installed checklog, portsentry, and chkrootkit.
Hardened Firefox - NoScript, disabled cookies, bfilter, etc.
Installed Firestarter

Now, after browsing at my local coffee shop, I realized I had been port scanned twice:
```

#5-(3-6) 	 [snort] (portscan) UDP Portsweep 	 2009-09-22 11:12:22 	 192.168.1.103 	 192.168.1.255 	 Raw IP
#6-(3-7) 	[snort] (portscan) UDP Portsweep 	2009-09-22 12:47:12 	192.168.1.103 	192.168.1.255 	Raw IP

```
ossec did not blacklist the ip like it should have, and the port scan was successful.  Infact, even when I use nmap, like in the example, from another computer, ossec does nothing.

Also, I ran chkrootkit, and a few things were different then after the initial install:
```
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/jvm/java-6-sun-1.6.0.16/lib/visualvm/visualvm/.lastModified /usr/lib/jvm/java-6-sun-1.6.0.16/.systemPrefs /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/firefox-3.0.14/.autoreg /usr/lib/xulrunner-1.9.0.14/.autoreg /lib/modules/2.6.28-15-generic/volatile/.mounted /lib/init/rw/.ramfs
```

```
Checking `bindshell'...                                     INFECTED (PORTS:  15 24 6667 31337)
```

```
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[3815], /sbin/dhclient3[6013], /usr/sbin/snort[7370])
```

The infected bindshell really scares me, not sure if it should.

Nmap results:
```

Starting Nmap 4.76 ( http://nmap.org ) at 2009-09-23 03:07 EDT
Initiating Parallel DNS resolution of 1 host. at 03:07
Completed Parallel DNS resolution of 1 host. at 03:07, 0.02s elapsed
Initiating SYN Stealth Scan at 03:07
Scanning 10.3.51.121 [1000 ports]
Discovered open port 80/tcp on 10.3.51.121
Discovered open port 79/tcp on 10.3.51.121
Discovered open port 6667/tcp on 10.3.51.121
Discovered open port 32771/tcp on 10.3.51.121
Discovered open port 143/tcp on 10.3.51.121
Discovered open port 119/tcp on 10.3.51.121
Discovered open port 1524/tcp on 10.3.51.121
Discovered open port 31337/tcp on 10.3.51.121
Discovered open port 2000/tcp on 10.3.51.121
Discovered open port 1080/tcp on 10.3.51.121
Discovered open port 1/tcp on 10.3.51.121
Discovered open port 12345/tcp on 10.3.51.121
Discovered open port 32774/tcp on 10.3.51.121
Discovered open port 111/tcp on 10.3.51.121
Discovered open port 32772/tcp on 10.3.51.121
Discovered open port 32773/tcp on 10.3.51.121
Completed SYN Stealth Scan at 03:07, 0.10s elapsed (1000 total ports)
Host 10.3.51.121 appears to be up ... good.
Interesting ports on 10.3.51.121:
Not shown: 984 closed ports
PORT      STATE SERVICE
1/tcp     open  tcpmux
79/tcp    open  finger
80/tcp    open  http
111/tcp   open  rpcbind
119/tcp   open  nntp
143/tcp   open  imap
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  callbook
6667/tcp  open  irc
12345/tcp open  netbus
31337/tcp open  Elite
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 0.37 seconds
           Raw packets sent: 1000 (44.000KB) | Rcvd: 2016 (84.704KB)

```

Where the heck did all those open ports come from!?!?!?

So, I'm rather confused as to what happened.  I made attempts to strengthen the security of my system, however, it kind of seems like it has lessened??

So my question is, what does all of this mean, and where do I go from here?

---

### Post by kerry_s on 2009-09-23
paranoid? :lolflag:

you added a lot of stuff do you even know what they actually do, how they work using ports.
you only need a few, at the most, try not to overlap. some of that stuff you installed needs to be setup correctly to work.

there is such a thing as a false positive. if you really need to be that secure disconnect from the internet. :lolflag:

---

### Post by dvlchd3 on 2009-09-23
First of all, since when is being too security conscious paranoid??

Anyway, nothing overlaps, everything is configured correctly.  After looking through the logs, I found there were several brute force attempts to gain access to my machine.  Apparently, this guy at the coffee shop has nothing better to do then to sit around all day and attack people's computers.

Since then, I have restored from a known good backup, and everything seems to be back to normal (even with all my paranoid applications installed :) )

chkrootkit reports all fine, and only open port is port 80 (for webserver).

Also, I now drop all packets coming from his ip address.

I just thought someone may have been able to provide some intuitive explanation for the above, but perhaps I was incorrect.  Especially since most of the open ports (besides port 80) are all used to provide information regarding my system and services running, as well as provide a means to install backdoors or execute other exploits.

---

### Post by openfly on 2009-09-23
> 
First of all, since when is being too security conscious paranoid??


paranoid
    adjective
    °Of, related to, or suffering from paranoia.
    °Exhibiting extreme and irrational fear or distrust of others.
    "Maybe I'm paranoid, but that doesn't mean that they are not out to get me."

---

### Post by cdenley on 2009-09-23
You installed portsentry, which listens on many common TCP and UDP ports to detect port scans, then you are concerned when a port scanner shows open ports? Don't install software if you don't know what it does.

---

### Post by openfly on 2009-09-23
lsof will tell you which processes have which ports open.

---

### Post by HermanAB on 2009-09-23
Hmm, why not just uninstall all that and go back to the Ubuntu defaults, then relax and enjoy it...

---

### Post by ikt on 2009-09-23
The security utilities featured in the sticky are more for servers than general desktops.

I think effectively setting up a firewall would provide more protection than 10 utilities pretty much sitting around doing nothing but increasing your attack vector.

That's just me though, I'd like to hear more opinions on this.

---

### Post by dvlchd3 on 2009-09-24
> paranoid
adjective
°Of, related to, or suffering from paranoia.
°Exhibiting extreme and irrational fear or distrust of others.
"Maybe I'm paranoid, but that doesn't mean that they are not out to get me." 

Ok, well then I guess I am paranoid, however, I don't see that as an issue.  In my opinion, the whole world should be paranoid about security.

> 
The security utilities featured in the sticky are more for servers than general desktops.

I think effectively setting up a firewall would provide more protection than 10 utilities pretty much sitting around doing nothing but increasing your attack vector.

That's just me though, I'd like to hear more opinions on this. 

AND

> Hmm, why not just uninstall all that and go back to the Ubuntu defaults, then relax and enjoy it... 

I have since gone back to defaults.  (On a side note, my backup tar file was corrupt, so I had to go ALL the way back to defaults...sigh)  I have also reinstalled snort ossec and apparmor.  I was completely unaware of the purposes of the other utilities, however, I guess I was in a, lets screw around with this stuff mood...

Also, Apache is configured to only accept requests from localhost (since it is for dev only).  And happily, nmap shows NO open ports.

I guess I did kind of jump the gun here, however, I was defintely not expecting to get any sort of results with snort of ossec, or any of the other tools within the first 24 hours of installation!!!  Perhaps I truly am paranoid.  Wait, does this forum track me??  Are you following me??  WHY!?!?  :lolflag:

Anyway, thank you for putting up with my brief insanity.

---

### Post by cdenley on 2009-09-24
You're always going to get some "attacks". Scripts and bots everywhere scan IP's at random, and if they find a server, they attempt to guess passwords or try to exploit known vulnerabilities which may not be patched. This will happen often. If you configure and maintain your system right, and especially if there are no services listening for remote connections, there is no reason to pay any attention to such things.

---

