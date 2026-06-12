---
title: "File containing server name"
date: 2006-11-26
forum: Server Platforms
---

### Post by satimis on 2006-11-26
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64

Please advise which file contains "server name" ?

TIA


B.R.
satimis

---

### Post by Iowan on 2006-11-26
I presume you're looking for more than **/etc/hostname**?

---

### Post by satimis on 2006-11-26
> **Iowan said:**
> I presume you're looking for more than **/etc/hostname**?
Hi Iowan,

Tks for your advice.

$ cat /etc/hostname
ubuntu


Would it be;
ubuntu=localhost

Or
they are 2 different things?

TIA


B.R.
satimis

---

### Post by breezyfox on 2006-11-27
> **satimis said:**
> Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64

Please advise which file contains "server name" ?

TIA


B.R.
satimis

Hi satimis
THere are two things here. I guess you are looking for your machine name ( the name you choose when you install OS. secondly the name as appears on your boot menu.
Boot menu name is in :

/boot/grub/menu.lst

The file which contains your server or machine name is stored in /etc and the file name is hosts. This file does not have any file extension and simply is called hosts.
You can see by folowing command in terminal.

cat /etc/hosts

or if you want to edit: sudo gedit /etc/hosts 

and make changes. Be aware if you make some mistake then you may not be able to access remotely or sometimes locally by name.
You can change the name of your machine easily. try it. if you want to avoid some website not to become available on your machine add them as following
127.0.0.1 <url of site>
127.0.0.1 <url of another site>
127.0.0.1 <url of one more site >


BZ

---

### Post by satimis on 2006-11-27
Hi breezyfox,

Tks for your advice.

Postfix can't send mail to Internet.  Port 25 seems either blocked by ISP or without enabling port forwarding, 25 to server, on iptables.

Postfix can send mail to myself, unable sending mail to yahooo/gmail and another free mail websit.  No error found on /var/log/mail.err. only an empty file.

On /var/log/mail.log```

......
Nov 27 14:21:40 ubuntu postfix/smtp[5600]: connect to h.mx.mail.yahoo.com[209.191.118.103]: Connection timed out (port 25)
Nov 27 14:21:40 ubuntu postfix/smtp[5597]: connect to h.mx.mail.yahoo.com[209.191.118.103]: Connection timed out (port 25)
Nov 27 14:21:40 ubuntu postfix/smtp[5600]: 8452B754052: to=<satimis@yahoo.com>, relay=none, delay=232642, status=deferred (connect to h.mx.mail.yahoo.com[209.191.118.103]: Connection timed out)
Nov 27 14:21:40 ubuntu postfix/smtp[5597]: 1A25F754050: to=<satimis@yahoo.com>, relay=none, delay=232996, status=deferred (connect to h.mx.mail.yahoo.com[209.191.118.103]: Connection timed out)
Nov 27 14:21:40 ubuntu postfix/smtp[5598]: connect to h.mx.mail.yahoo.com[66.196.97.250]: Connection timed out (port 25)
Nov 27 14:21:40 ubuntu postfix/smtp[5598]: 58B9D75404C: to=<satimis@yahoo.com>, relay=none, delay=365906, status=deferred (connect to h.mx.mail.yahoo.com[209.191.118.103]: Connection timed out)
Nov 27 14:21:40 ubuntu postfix/smtp[5596]: connect to h.mx.mail.yahoo.com[209.191.118.103]: Connection timed out (port 25)
Nov 27 14:21:40 ubuntu postfix/smtp[5596]: 172E6754048: to=<satimis@yahoo.com>, relay=none, delay=410465, status=deferred (connect to h.mx.mail.yahoo.com[66.196.97.250]: Connection timed out)
Nov 27 14:21:40 ubuntu postfix/qmgr[5587]: D50EC754060: to=<satimis@yahoo.com>, relay=none, delay=66296, status=deferred (delivery temporarily suspended: connect to h.mx.mail.yahoo.com[209.191.118.103]: Connection timed out)
Nov 27 14:22:44 ubuntu postfix/smtpd[5970]: connect from localhost.localdomain[127.0.0.1]
Nov 27 14:25:27 ubuntu postfix/smtpd[5970]: 72999754068: client=localhost.localdomain[127.0.0.1]
Nov 27 14:25:53 ubuntu postfix/cleanup[5981]: 72999754068: message-id=<20061127062527.72999754068@server1.example.com>
Nov 27 14:25:53 ubuntu postfix/qmgr[5587]: 72999754068: from=<myself@satimis.homelinux.com>, size=416, nrcpt=1 (queue active)
Nov 27 14:25:53 ubuntu postfix/qmgr[5587]: 72999754068: to=<satimis@yahoo.com>, relay=none, delay=44, status=deferred (delivery temporarily suspended: connect to h.mx.mail.yahoo.com[209.191.118.103]: Connection timed out)
Nov 27 14:26:00 ubuntu postfix/smtpd[5970]: disconnect from localhost.localdomain[127.0.0.1]

```

stop iptables also without result.

$ sudo /etc/init.d/firewall stop
Removing all iptables rules:  [End of flush]

$ cat /boot/grub/menu.lst | grep hostname/host/hosts
all no printout

$ cat /etc/hosts | grep hostname/host/hosts
also no printout


> You can change the name of your machine easily. try it. if you want to avoid some website not to become available on your machine add them as following
127.0.0.1 <url of site>
127.0.0.1 <url of another site>
127.0.0.1 <url of one more site >
Sorry I can't follow.  Please explain in more detail.  TIA


B.R.
satimis

---

### Post by Iowan on 2006-11-27
> **satimis said:**
> ...
Or
they are 2 different things?

TIA


B.R.
satimis
They are two different things - localhost is *sortof* what the machine calls itself.  It generally has the IP address 127.0.0.1.  The **hostname ** is the name by which other machines will know this one (depending on a few things like DNS, WINS, and/or **/etc/hosts**).
[http://www.debianhelp.co.uk/hostname.htm]("http://www.debianhelp.co.uk/hostname.htm")
Here's more information... I used to have a link for *HowTo Change Hostname* in my signature, but I replaced it with the *HowTo Disable IPV6* link.

---

### Post by breezyfox on 2006-11-27
[QUOTE=satimis;1812389]Hi breezyfox,

Tks for your advice.

Postfix can send mail to myself, unable sending mail to yahooo/gmail and another free mail websit.  
---------------------------------------------
You need to edit the main configuration file and point relayhost  to smtp server of your desired mail server.
sudo gedit /etc/postfix/main.cf
change or add like this:
relayhost = smtp.google.com
-----------------------------------------------

$ cat /boot/grub/menu.lst | grep hostname/host/hosts
all no printout

$ cat /etc/hosts | grep hostname/host/hosts
also no printout
------------------------------------------------------
do as following:You don't need to use grep command:
cat /boot/grub/menu.lst
cat /etc/hosts
and to make changes or edit use gedit or nano
sudo /boot/grub/menu.lst
sudo /etc/hosts
-------------------------------------------------------

Sorry I can't follow.  Please explain in more detail.  TIA
------------------------------------------------------------
These are the hosts file, befour your browser look for the website's ipaddress in DNS name server, every browser first looks locally and if found locally in hosts file, browser don't procede further. it is that simple.
Now lets take an example: if you  want that site [www.google.com](www.google.com) should not be available from your machine (PC) than you add the entry in your host file ike this:
127.0.0.1<one space or tab>[www.google.com](www.google.com)
Now the browser will presume that site google.com ip address is 127.0.0.1 which is local host and will not procede further because it found the ip adress of google.com which is incorrect.THis way you can block the sites which send spam or ads.

Hope now more clear

Bz
-----------------------------------------------------------------------

---

### Post by satimis on 2006-11-28
Hi Iowan,

Tks for your advice and URL

> [http://www.debianhelp.co.uk/hostname.htm]("http://www.debianhelp.co.uk/hostname.htm")
Here's more information... 

$ uname -n```

ubuntu
```

$ hostname -a```



```
Empty printout here.

$ hostname -s```

ubuntu

```
$ hostname -d```

com

```
Why the domain becomes "com"?  Which file I have to check?  Tks.

$ hostname -f```

ubuntu.com

```
$ hostname```

ubuntu

```

> I used to have a link for *HowTo Change Hostname* in my signature, but I replaced it with the *HowTo Disable IPV6* link.
Where can I find "HowTo Disable IPV6" URL.  Tks.


B.R.
satimis

---

### Post by satimis on 2006-11-28
Hi breezyfox

> ---------------------------------------------
You need to edit the main configuration file and point relayhost  to smtp server of your desired mail server.
sudo gedit /etc/postfix/main.cf
change or add like this:
relayhost = smtp.google.com
-----------------------------------------------
$ cat /etc/postfix/main.cf | grep relayhost```

relayhost =

```

Sorry, I'm not clear here.  If I also want sending mails to Yahoo, vista, etc., whether I have to add:
relayhost = smtp.yahoo.com
relayhost = smtp.vista.com
etc.

Then I have to add many entries here?  I suppose it is for webmail only NOT for normal email address?

> 
$ cat /boot/grub/menu.lst | grep hostname/host/hosts
all no printout

$ cat /etc/hosts | grep hostname/host/hosts
also no printout
------------------------------------------------------
do as following:You don't need to use grep command:
cat /boot/grub/menu.lst
cat /etc/hosts
and to make changes or edit use gedit or nano
sudo /boot/grub/menu.lst
sudo /etc/hosts
-------------------------------------------------------

Oh, sorry.  I haven't made it clear here.

Actually I ran;
$ cat /boot/grub/menu.lst | grep hostname
$ cat /boot/grub/menu.lst | grep host
$ cat /boot/grub/menu.lst | grep hosts

respectively to find out whether there are such entries.

Others noted with thanks.


B.R.
satimis

---

### Post by Iowan on 2006-11-28
dupe

---

### Post by Iowan on 2006-11-28
> **satimis said:**
> Where can I find "HowTo Disable IPV6" URL.
Quick way is to click on the link in my signature labelled [[Disable ipv6]]("http://www.ubuntuforums.org/showthread.php?t=87798")
... or, go here: [http://www.ubuntuforums.org/showthread.php?t=87798]("http://www.ubuntuforums.org/showthread.php?t=87798")

---

