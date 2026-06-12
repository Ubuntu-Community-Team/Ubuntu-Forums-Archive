---
title: "Firewall tester other than grc.com"
date: 2017-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2017-04-27
HI,

Are there any other firewall testing web sites other than grc.com ?

---

### Post by anoda on 2017-04-28
Hi. You can use e.g. **nmap** - port scanning tool application to check your firewall setting. Here are some options/flag for **nmap** to make various system scan etc.:  

[COLOR=#666666]*# *[/COLOR][COLOR=#c20cb9][I][COLOR=#666666]OS detection 
[/COLOR][/I][/COLOR]**sudo nmap** -v -A localhost[COLOR=#666666][I]

# [/I][/COLOR][COLOR=#808080][I]Find out if OS is protected by firewall
[/I][/COLOR]**[B]sudo **nmap[/B] -sA localhost[COLOR=#666666]

[COLOR=#666666]*#*[/COLOR][I] TCP Xmas scan to check fireeall
[/I][/COLOR]**[B]sudo **nmap[/B] -sX localhost

[COLOR=#666666]*#*[/COLOR]* [COLOR=#808080]Stealth scan[/COLOR]*[B]
**sudo **nmap [/B]-sS localhost
[COLOR=#666666][I]
# [/I][/COLOR][COLOR=#808080]*OS fingerprinting*[/COLOR][B]
**sudo **nmap[/B] -sT localhost
  [COLOR=#666666][I]
# Scan [/I][/COLOR][COLOR=#808080]*host using TCP ACK and TCP SYN*[/COLOR][B]
**sudo **nmap[/B] -PS localhost[COLOR=#666666]
[/COLOR]
And many, many more options. (Please see an oficial **nmap** website for another examples.) An example command to scan system:   

$ sudo nmap -sS -Pn -T4 localhost
$ sudo nmap -v -sU -sT localhost 

**nmap** should be installed by default. If not You can install it using APT utility. It is pretty simple: 

$ sudo apt-get update
$ sudo apt-get install nmap

By the way; You have asked about another web site. Please check for example this one: [https://pentest-tools.com/network-vulnerability-scanning/tcp-port-scanner-online-nmap](https://pentest-tools.com/network-vulnerability-scanning/tcp-port-scanner-online-nmap) or even **nmap** online: [http://nmap.online-domain-tools.com/](http://nmap.online-domain-tools.com/) On both web sites You can set multiple various scan options etc. 

Cheers.

---

### Post by Habitual on 2017-04-28
canyouseeme.org

compare to 
```
sudo lsof -Pnl +M -i4
```
and nmap result.

---

### Post by linuxyogi on 2017-04-28
@anoda 

I want to scan my pfSense box. Scanning localhost wont do it.

@Habitual

canyouseeme.org lets you scan 1 port at a time. I want to scan all ports.

---

### Post by Habitual on 2017-04-28
You're welcome.

---

### Post by cariboo on 2017-04-28
You could try the nmap online tool:

[http://nmap.online-domain-tools.com/](http://nmap.online-domain-tools.com/)

---

### Post by linuxyogi on 2017-04-29
> **cariboo said:**
> You could try the nmap online tool:

[http://nmap.online-domain-tools.com/](http://nmap.online-domain-tools.com/)


> Starting Nmap 6.47 ( [http://nmap.org](http://nmap.org) ) at 2017-04-29 06:30 Coordinated Universal Time
Nmap scan report for 202.XXX.XX.79
Host is up (0.16s latency).
All 5000 scanned ports on 202.XXX.XX.79 are filtered
 
Nmap done: 1 IP address (1 host up) scanned in 288.91 seconds


Thanks. It worked.

---

