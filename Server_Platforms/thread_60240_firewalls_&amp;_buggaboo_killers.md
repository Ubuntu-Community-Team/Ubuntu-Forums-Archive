---
title: "firewalls &amp; buggaboo killers"
date: 2005-08-27
forum: Server Platforms
---

### Post by Nopposan on 2005-08-27
I read a very good review of GuardDog in Tux magazine.  Will GuardDox only run with KDE?  If so, then which firewalls are good for novices running Gnome?  I have nothing against KDE, it's just that I'm not eager to change a good thing; 'just started learning to use Gnome.

Another question: Do I need anti-spyware?

---

### Post by amohanty on 2005-08-27
[QUOTE=Nopposan]I read a very good review of GuardDog in Tux magazine.  Will GuardDox only run with KDE?  If so, then which firewalls are good for novices running Gnome?  I have nothing against KDE, it's just that I'm not eager to change a good thing; 'just started learning to use Gnome.

Another question: Do I need anti-spyware?[/QUOTE]


Windows user, I presume  :smile: 

AFAIK you dont really need anti-spyware. As to firewalls did you try the one that comes packaged with Ubuntu. Instr here:
[http://ubuntuforums.org/showthread.php?t=26483&highlight=firewall](http://ubuntuforums.org/showthread.php?t=26483&highlight=firewall)

Moreover if you are not running any world facing daemons like a web server, mail server, etc you dont really need a firewall. To see what ports might be open, use synaptic to install nmap and then at the terminal type:

nmap -sS -vv -p 0-65535 <machine ip address>

To find your machines IP address at the terminal type:
ipconfig eth0

HTH
AM

---

