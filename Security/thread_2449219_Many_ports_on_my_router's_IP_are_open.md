---
title: "Many ports on my router's IP are open"
date: 2020-08-22
forum: Security
---

### Post by linuxyogi on 2020-08-22
I have asked this question on another distro forum but I really want to know what my friends will say about the topic.
I ran a scan on grc.com & it passed the test but when I run a nmap scan on my router's local interface I got the following :

```
$ nmap 192.168.225.1
Starting Nmap 7.70 ( https://nmap.org ) at 2020-08-22 18:16 IST
Nmap scan report for embms.jio.local (192.168.225.1)
Host is up (0.013s latency).
Not shown: 995 closed ports
PORT     STATE    SERVICE
53/tcp   filtered domain
80/tcp   open     http
5555/tcp filtered freeciv
6666/tcp open     irc
7777/tcp open     cbt

Nmap done: 1 IP address (1 host up) scanned in 1.54 seconds
```

Is this serious ? What can I do ?

---

### Post by SeijiSensei on 2020-08-22
If your router provides DNS services to the local network (pretty common) and offers a web interface for management, then ports 53 and 80 need to be open.  As for the other three, I have no idea.  They're not a big security hole since they are blocked from the outside.  Perhaps the router's manual has an explanation, or you can contact their support.

My Archer router shows no open ports on the public side but 21, 22, 53, and 80 on the side facing my LAN.  I suspect it uses FTP (21) to upload local firmware updates and offers an SSH (22) interface I don't use.

---

### Post by kevdog on 2020-08-22
Make sure you scan your router based on LAN and WAN address or scan router from your phone when phone not connected to wifi.  It will give you a better sense of what is open to the outside world and not just the LAN.

---

### Post by linuxyogi on 2020-08-23
> **kevdog said:**
> Make sure you scan your router based on LAN and WAN address or scan router from your phone when phone not connected to wifi.  It will give you a better sense of what is open to the outside world and not just the LAN.

Nothing is open to the outside world. I know this coz I ran a scan by visiting grc.com. Whatever is open is open to the LAN.

Thanks to both.

---

