---
title: "dns for websites"
date: 2006-01-21
forum: Server Platforms
---

### Post by kasemodz on 2006-01-21
I have a couple of websites running in my lan. They are just ftp and my media server. Right now I have to enter the ip address and the port to connect to. I don't mind doing this, but is there any program or something out there that would mask this ip and have words/numbers as address?

---

### Post by dbee on 2006-01-21
try your /etc/hosts file

---

### Post by kasemodz on 2006-01-21
i tried that already, however it doesn't work it takes me to some random site. This is what I put. > 192.168.15.101 tightvnc.ondemand.org I also checked /etc/host.conf and it did have host before bind. I don't know how to configure this.

---

### Post by kasemodz on 2006-01-21
One thing is that when I add these hosts, it works fine from my server just not anything else in my lan.

---

### Post by Horndog on 2006-01-22
[QUOTE=kasemodz]I have a couple of websites running in my lan. They are just ftp and my media server. Right now I have to enter the ip address and the port to connect to. I don't mind doing this, but is there any program or something out there that would mask this ip and have words/numbers as address?[/QUOTE]

Just get yourself a Domain Name and to access your ftp just inter [ftp://yourDomain.com/](ftp://yourDomain.com/) and people will connect to the right port (If you use a standard ftp port)

BTW, there are sites that offer free Domain Names but not very elegant.

---

### Post by MJN on 2006-01-22
> One thing is that when I add these hosts, it works fine from my server just not anything else in my lan.

Ah, well that nugget is the key - /etc/hosts is only applicable to the machine it's on.

Configure the /etc/hosts file (or whatever similar file their OSs may use) on your other PCs with the same entries as you've done on your server.

Mathew

---

