---
title: "Ubuntu server 10.04"
date: 2010-05-10
forum: Server Platforms
---

### Post by Landi20 on 2010-05-10
How i have to make to put my server online
i only can acess in my network and i have to make to send an revice mail of other services
for exemple to [EMAIL="maria@mydomain.com"]maria@mydomain.com[/EMAIL] to [EMAIL="joaquim@iol.pt"]joaquim@iol.pt[/EMAIL]
to [EMAIL="maria@mydomain.com"]maria@mydomain.com[/EMAIL] to  [EMAIL="manuel@mydomain.com"]manuel@mydomain.com[/EMAIL] i can but to other mail services i can
and what i have to do to make a backup of my server

---

### Post by Kljuka on 2010-05-10
If you want to put your server online, you have to choose an IP that is visible from online (192.168.1.1 is not appropriate - this is LAN ip). Google, how to set up network. for example:
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)


Backing up can be made many different ways. Check rsync (for example this one: [http://ubuntuforums.org/showthread.php?t=15082](http://ubuntuforums.org/showthread.php?t=15082))

---

### Post by Landi20 on 2010-05-11
if i put the ip address of my no ip my server is gonna be online
???
what the ports i have to open for this services
postfix
mysql
ISPconfig
openssh
phpadmin
squerriel
Ftp

---

### Post by Kljuka on 2010-05-11
I'm not sure I understand your problem.

But if you're not using any firewalls, Ubuntu will listen to those ports automatically (with preconfigured installation). If you have a firewall, you have to open ports, depending on the service (eg. port 80 for http, ...):
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

---

### Post by Landi20 on 2010-05-11
the probleam its i can´t recive our send mail for other mail
for example hotmail,iol
if a open the ports of my router the my probleam is been solve you i have to do more things

---

### Post by Landi20 on 2010-05-12
I open the ports of my router and the firewall of my server but i can connect to other e-mail
someone can puts the ports of:
FTP
SMTP white SSL and TLS
POP white SSL and TLS
IMAP  white SSL and TLS
Domain
DNS
Websites
and where i can see all services i have in my server
I use to configurate the ISPConfig

---

### Post by Iowan on 2010-05-12
> **Landi20 said:**
> ...someone can puts the ports of:I doubt [this]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers") is what you were looking for - but the answer is probably buried in there.

---

### Post by jjcv on 2010-05-13
> **Landi20 said:**
> I open the ports of my router and the firewall of my server but i can connect to other e-mail


Have a look in /etc/services to see the default port number for various services.

---

### Post by Landi20 on 2010-05-13
Topic can be close becouse the problem as been solve

[EMAIL="maria@example.com"] [/EMAIL]

---

