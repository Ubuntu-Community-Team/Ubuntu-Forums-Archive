---
title: "UFW doesn't block anything"
date: 2019-12-16
forum: Security
---

### Post by kyliael on 2019-12-16
Hi there,

I though I had correctly setup my firewall, but I was wrong...
Pretty simple setup :

sudo ufw status verbose :

```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
22/tcp (OpenSSH)           ALLOW IN    Anywhere                  
8080                       ALLOW IN    Anywhere                  
80                         ALLOW IN    Anywhere                  
22                         ALLOW IN    Anywhere                  
443                        ALLOW IN    Anywhere                  
25560:25580/tcp            ALLOW IN    Anywhere                  
25560:25580/udp            ALLOW IN    Anywhere                  
22/tcp (OpenSSH (v6))      ALLOW IN    Anywhere (v6)             
8080 (v6)                  ALLOW IN    Anywhere (v6)             
80 (v6)                    ALLOW IN    Anywhere (v6)             
22 (v6)                    ALLOW IN    Anywhere (v6)             
443 (v6)                   ALLOW IN    Anywhere (v6)             
25560:25580/tcp (v6)       ALLOW IN    Anywhere (v6)             
25560:25580/udp (v6)       ALLOW IN    Anywhere (v6)   
```

But when I check from another computer with nmap :

```
sudo nmap -sU -p 389 mydomain.info


Starting Nmap 7.60 ( https://nmap.org ) at 2019-12-16 16:34 CET
Nmap scan report for mydomain.info (x.x.x.x)
Host is up (0.032s latency).


PORT    STATE         SERVICE
389/udp open|filtered ldap


Nmap done: 1 IP address (1 host up) scanned in 0.90 seconds



```

it shows that the port 389 is openned...

I really need some help :(
This is an example as I actually have all my ports opened, not only 389

---

### Post by deadflowr on 2019-12-16
filtered means it cannot determine one way or another,
see: [https://nmap.org/book/man-port-scanning-basics.html]("https://nmap.org/book/man-port-scanning-basics.html")

---

### Post by Frogs Hair on 2019-12-16
Hello and Welcome !

You can return to default which denies incoming and allows outgoing connections.   

```
sudo ufw default deny 
```

Basic ufw Commands that require sudo


Firewall


```
ufw enable : Turn on the firewall
ufw disable : Turn off the firewall
ufw default allow :  Allow all connections by
default
ufw default deny :  Drop all connections by
default
ufw status : Current status and rules
ufw allow port : Allow traffic on port
ufw deny port : Block port
ufw deny from ip : Block ip adress
ufw reset : Reset to default  


```

---

### Post by The Cog on 2019-12-16
You are not trying to get the host to nmap scan itself, are you? The host is always allowed to talk to itself on any port - lots of things break if it can't, so firewall rules always have to allow that.
So an nmap scan must always be conducted from a different machine.

---

### Post by kyliael on 2019-12-16
> **Frogs Hair said:**
> Hello and Welcome !

You can return to default which denies incoming and allows outgoing connections. 

```
sudo ufw default deny 
```

Hi,

if you look at my ufw status verbose, you can see it's already set : [COLOR=#000000][FONT=&amp]Default: deny (incoming)

[/FONT][/COLOR]

---

### Post by kyliael on 2019-12-16
> **deadflowr said:**
> filtered means it cannot determine one way or another,
see: [https://nmap.org/book/man-port-scanning-basics.html](https://nmap.org/book/man-port-scanning-basics.html)

Yes, filtered, but you can also see that it returns open

---

### Post by kyliael on 2019-12-16
> **The Cog said:**
> You are not trying to get the host to nmap scan itself, are you? The host is always allowed to talk to itself on any port - lots of things break if it can't, so firewall rules always have to allow that.
So an nmap scan must always be conducted from a different machine.

Hi, 

thank you, but as stated, I'm using nmap form another computer from another network.

---

### Post by The Cog on 2019-12-17
> **kyliael said:**
> Hi, 
thank you, but as stated, I'm using nmap form another computer from another network.
Oops. I didn't read carefully enough. Sorry.

But I'll happily go with deadflowr's answer that nmap says it's "either open or filtered".  
Try this command:
```
nc -vz mydomain.info 389 
```
Unless you get a successful connection then the port is indeed filtered.

---

### Post by deadflowr on 2019-12-17
You can also always compare ufw on to ufw off.
It'll probably say closed when off, which means that when on, it's being filtered.

---

### Post by bernard010 on 2019-12-17
I offer Documentation : [https://help.ubuntu.com/lts/serverguide/firewall.html](https://help.ubuntu.com/lts/serverguide/firewall.html) 

UFW firewall Manpage : [http://manpages.ubuntu.com/manpages/eoan/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/eoan/man8/ufw.8.html)

Uncomplicatd Firewall [https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
   This includes advanced functionality.
 
Basic Firewall  [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall)
I hope this may help.

---

