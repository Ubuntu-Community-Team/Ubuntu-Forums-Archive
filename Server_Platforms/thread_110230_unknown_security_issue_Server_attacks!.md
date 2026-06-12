---
title: "unknown security issue: Server attacks!"
date: 2005-12-30
forum: Server Platforms
---

### Post by linuxone on 2005-12-30
Hi,

a few days ago I upgraded my Internet server from an old Mandrake installation to Ubuntu-Server 5.10. Of course all updates were installed. Upgrade means: backup all data, mkfs * and do a complete new install of Server OS and all used applications.
Basic configuration of all services was taken from the old Mandrake installation, which runs without any problem or error since a few years.

Today the server was no longer available. After some research and network sniffing I found what happened:

-> From one IP address thousands of TCP packets were send to one server IP. Content was:

Source port: 3434  (attacker)
Destination port: 37520 (my server)
Flags: PSH, ACK

Data contents:
PING : *.0:127.0.0.1 PONG 12.0.0.1 :iavorlkvd
PING : *.%:127.0.0.1 PONG 12.0.0.1 :iavorlkvd
PING : *.@:127.0.0.1 PONG 12.0.0.1 :iavorlkvd
....

After many of these TCP packets the content changed:

root! ~root@127.0.0.1 PRIVMSG $127.0.0.1 : dos 99999 h | <domain_url>

Server Responce:
root : starting.

-> Immidately my server started to request foreign Web pages on another IP address. These requests eats 100% bandwidth, up to >500 request processes where running at once.
------------------

Bad. Real bad. I know.

I checked it several times:
-> no listening service on port 37520 found !
-> all updates where installed! Really. And sources.lst contains the correct rep's.
-> all configurations were correct and secure (IMO), from my experiences of 10 year server Admin
-> chkrootkit + rkhunter (fresh downloads from their homepages!) reports NO problem
-> virus scan of the entire file system reports NO problem (Kaspersky 5.0.5 for Linux Mail servers)
-> neither nmap nor nessus reports any serious problems

To be certain I reinstalled several packages (apt, libc6, coreutils, modprobe, find) and redo all scans. No changing.

All log files looks ok, especially the apache2 log. No suspect entries, no suspect PHP requests.

I can't find any answer what real happened. Of course this answer is necessary to secure my (and not only my own) server and prevent future attacks.

Running services:
http, https (apache2), smtpd/pop3 (netqmail), php4, mysql, ssh, proftpd (login required), inn2 (local news only), snmpd (for mrtg), hylafax.

Any idea is welcome.

Thomas

---

### Post by marks_linux on 2005-12-30
if not already you can put the ip address in /etc/hosts.deny

---

### Post by linuxone on 2005-12-30
Hi,

[QUOTE=marks_linux]if not already you can put the ip address in /etc/hosts.deny[/QUOTE]

thanks. But unfortunately this does not solve the problem.

It's only a cosmetic changing and the reason for this security problem still exist. And, also important: it does not help. Because daemon connections still works .... means: you still can get mails from your POP3 account (vpopmail as part of netqmail install), can request web pages, can download files via FTP (proftpd, daemon mode) and so on ...

Instead of hosts.deny I used iptables to drop all packets to and from this specific IP. But if the attacker changes his IP address, all will begin again because the security problem is still unknown and so unfixed. :( 

Thomas

---

### Post by fct on 2005-12-30
You should set up your firewall so only the ports of the services are open to external connections. The rest should drop any request (avoid returning denial of service messages).

In the case of the FTP server, you'll have to set it up as passive. Fortunately, proftpd allows you to specify a range of ports for data transfer that you can open up on your firewall.

Anyway, I'm curious about this. Perhaps you missed something on your config, but it might as well be a exploit on the wild. Do you have some valuable logs for the security staff at ubuntu?

---

### Post by fordfan753 on 2005-12-30
OK, so I know a little about networking, and even less about servers, but it looks like you got DoS'd...isn't there a way you can help prevent this by setting the que length longer and the timeout shorter?

---

### Post by LordHunter317 on 2005-12-31
You were compromised already, before this occured.  What you saw was the rootkit that was installed being told to do something, and then responding apporpriately.

***DISCONNECT THE BOX FROM THE INTERNET, NOW***

Then, boot from a rescue CD.  If you can, take an image of the system's disks to do forensics on.  If not, do your forensics there.  Don't trust any image on the system's disks.  Do not reconnect it to the Internet.

Then, start with a fresh Ubuntu install.  Install a single service, configure it, test it.  Continue this way until all your services are back up, and you're confidient you're running nothing that can be compromised.  If you have questions, post here or in the server thread.

Then, restore your data, slowly and carefully.  You'll need to audit it as you restore it to make sure it hasn't been compromised.  For some stuff, this is as simple as a virus scan.  For other things (like configuration files, hand written shell scripts) this means actually looking at them and making sure they're correct.

---

### Post by juuva on 2006-01-01
[QUOTE=linuxone]-> From one IP address thousands of TCP packets were send to one server IP. Content was:

Source port: 3434  (attacker)
Destination port: 37520 (my server)
Flags: PSH, ACK

Data contents:
PING : *.0:127.0.0.1 PONG 12.0.0.1 :iavorlkvd
PING : *.%:127.0.0.1 PONG 12.0.0.1 :iavorlkvd
PING : *.@:127.0.0.1 PONG 12.0.0.1 :iavorlkvd
....

After many of these TCP packets the content changed:

root! ~root@127.0.0.1 PRIVMSG $127.0.0.1 : dos 99999 h | <domain_url>

Server Responce:
root : starting.

-> Immidately my server started to request foreign Web pages on another IP address. These requests eats 100% bandwidth, up to >500 request processes where running at once.

[/QUOTE]


For me that looks like irc-conversation.

Your server as client and attacker who runs irc-server.. and your server is used as zombie which actually attacks to some other server.
```
netstat -anp
``` should atleast tell what process is using those ports.

---

### Post by SeekerOfSecurityGrail on 2006-01-06
[QUOTE=linuxone]
Running services:
http, https (apache2), smtpd/pop3 (netqmail), php4, mysql, ssh, proftpd (login required), inn2 (local news only), snmpd (for mrtg), hylafax.

Any idea is welcome.
[/QUOTE]

Hi,

IMHO thats too many functions to put onto one machine - when one service gets compromised, all functionality goes down. I think its better to spend a little money on  some outdated 500-800mhz boxes to separate the functionality so they dont All get killed at once. You can get cheap old boxes from dealers which sell out-of-lease corporate equiptment or ebay. 

When you reinstall your machine, Install aide, and copy the conf and db onto CD or usb drive. So that next time when something happens, you may perhaps find what the heck they installed and can remove them without doing another reinstall. 

Good luck.

---

### Post by LordHunter317 on 2006-01-06
[QUOTE=SeekerOfSecurityGrail]IMHO thats too many functions to put onto one machine - when one service gets compromised, all functionality goes down.[/quote]That's not necssarily true.  Proper chrooting can reduce the impact of a compromise to just that service, if one is careful.

> So that next time when something happens, you may perhaps find what the heck they installed and can remove them without doing another reinstall. Unless the AIDE DB is compromised and you don't have a recent backup, of course.

---

### Post by SeekerOfSecurityGrail on 2006-01-06
Very true, LordHunter.  Backups of aide conf and db (and perhaps the package also) are a necessity.  I didnt mean to disagree with your post - a fresh install IS the best thing to do after a compromise. That was just thrown in as a glimmer of hope for a busy admin. (perhaps-perchance-maybe-somehow.magically he doesnt have to reinstall :)  )

---

### Post by LordHunter317 on 2006-01-06
[QUOTE=SeekerOfSecurityGrail](perhaps-perchance-maybe-somehow.magically he doesnt have to reinstall :)  )[/QUOTE]No, at this point he must reinstall (and I cannot stress that enough to everyone).  You are quite correct however, that properly maintained and handled, that AIDE can let you properly assess the damage and prevent the need for a reinstall.

It's all about having a complete audit trail.  If you can completely audit what they did, you don't have to reinstall.  If you can't, then you must and assume everyone on the box was suspect.

Even if you choose/must reinstall with AIDE, it can help you determine what must be audited in a reinstall. :)

---

