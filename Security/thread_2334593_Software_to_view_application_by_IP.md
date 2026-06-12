---
title: "Software to view application by IP"
date: 2016-08-20
forum: Security
---

### Post by cscott0108 on 2016-08-20
Hey everyone,

I'm looking for software for Ubuntu 16.04 that will let me see what IP addresses and what ports an application is trying to use. I don't want to block it necessary, I just want to make sure that packets are getting out and coming in because I'm having trouble reaching a particular website via this app/game but I can ping it. I don't have the firewall enabled so it shouldn't be blocking it and I know it works on other computers with Windows.

I know windows has an app for this as I use it pretty regularly but that wouldn't be useful for this application in Ubuntu. If you know of something like this that would be helpful, I added it to the security forum since it kinda goes with security.

Thanks.

---

### Post by &amp;KyT$0P# on 2016-08-20
Terminal, [FONT=Courier New]netstat[/FONT].  Given how generic your post is I don't know an exact command for you.  Keep in mind that some parts of netstat only work if it's run as root.

For information on how to use netstat, refer to its man page:
```
man netstat
```


EDIT That's for listing IP addresses and ports.  For packet sniffing, install wireshark:
```
sudo apt-get install wireshark
```

---

### Post by SeijiSensei on 2016-08-20
You can determine which ports on the remote host are open with nmap.  
```
sudo nmap -sT some_host
```
will attempt to connect to large number of ports using TCP.  You must be root to do anything other than a ping scan with nmap.  See [this](https://nmap.org/book/man-port-scanning-techniques.html) for details.

nmap is extremely flexible.  You can scan all the ports with "-p 1-65535" or just a single port with "-p 80".  You can do UDP scans and "stealth" scans as well.  See the document I linked to for details.

---

### Post by cogset on 2016-08-27
Maybe something like ```
watch -n2 ss -aptn state syn-sent
``` may also help here, allowing you to spot which connections are trying to go through but can't, because something is blocking them.

         Then it's time to dig further using nmap and/or wireshark, as suggested.

---

### Post by ian-weisser on 2016-08-27
Etherape is a pretty good application for monitoring bi-directional network activity. It's in the Ubuntu repositories.

---

