---
title: "[SOLVED] You got new mail?"
date: 2008-07-31
forum: The Cafe
---

### Post by billgoldberg on 2008-07-31
If you boot into ubuntu without a graphical login you always get "you got new mail". On the bottom.

What does it mean?

Or did someone just tried to be funny?

```
rw@legend:~$ ssh -x rw@192.168.1.4
rw@192.168.1.4's password: 
Linux legend 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
**You have new mail.**
Last login: Thu Jul 31 11:32:22 2008
```

---

### Post by zenwalker on 2008-07-31
i think, saying mail cmd will let u know its content. not sure though.

---

### Post by Vishal Agarwal on 2008-07-31
just check the mail with 
pine -f /var/spool/mail/<username>

Once the mail will be marked read, it should not appear like "you have new mail"

---

### Post by billgoldberg on 2008-07-31
> **Vishal Agarwal said:**
> just check the mail with 
pine -f /var/spool/mail/<username>

Once the mail will be marked read, it should not appear like "you have new mail"

This is the file @ /var/spool/mail/me

> From root@legend Thu Jul 24 09:51:15 2008
Return-path: <root@legend>
Envelope-to: root@legend
Delivery-date: Thu, 24 Jul 2008 09:51:15 +0200
Received: from root by legend with local (Exim 4.69)
	(envelope-from <root@legend>)
	id 1KLvbX-0007Tv-HZ
	for root@legend; Thu, 24 Jul 2008 09:51:15 +0200
Subject: [rkhunter] legend - Daily report
To: root@legend
Message-Id: <E1KLvbX-0007Tv-HZ@legend>
From: root <root@legend>
Date: Thu, 24 Jul 2008 09:51:15 +0200

Warning: The SSH and rkhunter configuration options should be the same:
         SSH configuration option 'PermitRootLogin': yes
         Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /etc/.sudoers.tmp.swo: Vim swap file, version 7.1
Warning: Hidden file found: /etc/.sudoers.tmp.swp: Vim swap file, version 7.1

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

From root@legend Fri Jul 25 10:06:51 2008
Return-path: <root@legend>
Envelope-to: root@legend
Delivery-date: Fri, 25 Jul 2008 10:06:51 +0200
Received: from root by legend with local (Exim 4.69)
	(envelope-from <root@legend>)
	id 1KMIKB-0007OL-K2
	for root@legend; Fri, 25 Jul 2008 10:06:51 +0200
Subject: [rkhunter] legend - Daily report
To: root@legend
Message-Id: <E1KMIKB-0007OL-K2@legend>
From: root <root@legend>
Date: Fri, 25 Jul 2008 10:06:51 +0200

Warning: The SSH and rkhunter configuration options should be the same:
         SSH configuration option 'PermitRootLogin': yes
         Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /etc/.sudoers.tmp.swo: Vim swap file, version 7.1
Warning: Hidden file found: /etc/.sudoers.tmp.swp: Vim swap file, version 7.1

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

From root@legend Sat Jul 26 07:57:35 2008
Return-path: <root@legend>
Envelope-to: root@legend
Delivery-date: Sat, 26 Jul 2008 07:57:35 +0200
Received: from root by legend with local (Exim 4.69)
	(envelope-from <root@legend>)
	id 1KMcmc-000877-U6
	for root@legend; Sat, 26 Jul 2008 07:57:34 +0200
Subject: [rkhunter] legend - Daily report
To: root@legend
Message-Id: <E1KMcmc-000877-U6@legend>
From: root <root@legend>
Date: Sat, 26 Jul 2008 07:57:34 +0200

Warning: Users have been removed from the passwd file:
         gdm:x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false
Warning: Groups have been removed from the group file:
         gdm:x:114:
Warning: The SSH and rkhunter configuration options should be the same:
         SSH configuration option 'PermitRootLogin': yes
         Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /etc/.sudoers.tmp.swo: Vim swap file, version 7.1
Warning: Hidden file found: /etc/.sudoers.tmp.swp: Vim swap file, version 7.1

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

From root@legend Sun Jul 27 08:42:09 2008
Return-path: <root@legend>
Envelope-to: root@legend
Delivery-date: Sun, 27 Jul 2008 08:42:09 +0200
Received: from root by legend with local (Exim 4.69)
	(envelope-from <root@legend>)
	id 1KMzxI-0007NC-QB
	for root@legend; Sun, 27 Jul 2008 08:42:08 +0200
Subject: [rkhunter] legend - Daily report
To: root@legend
Message-Id: <E1KMzxI-0007NC-QB@legend>
From: root <root@legend>
Date: Sun, 27 Jul 2008 08:42:08 +0200

Warning: The SSH and rkhunter configuration options should be the same:
         SSH configuration option 'PermitRootLogin': yes
         Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /etc/.sudoers.tmp.swo: Vim swap file, version 7.1
Warning: Hidden file found: /etc/.sudoers.tmp.swp: Vim swap file, version 7.1

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

From root@legend Sun Jul 27 08:42:09 2008
Return-path: <root@legend>
Envelope-to: root@legend
Delivery-date: Sun, 27 Jul 2008 08:42:09 +0200
Received: from root by legend with local (Exim 4.69)
	(envelope-from <root@legend>)
	id 1KMzxJ-0007On-GP
	for root@legend; Sun, 27 Jul 2008 08:42:09 +0200
From: Anacron <root@legend>
To: root@legend
Subject: Anacron job 'cron.daily' on legend
Message-Id: <E1KMzxJ-0007On-GP@legend>
Date: Sun, 27 Jul 2008 08:42:09 +0200

/etc/cron.daily/logrotate:
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

From root@legend Mon Jul 28 08:04:27 2008
Return-path: <root@legend>
Envelope-to: root@legend
Delivery-date: Mon, 28 Jul 2008 08:04:27 +0200
Received: from root by legend with local (Exim 4.69)
	(envelope-from <root@legend>)
	id 1KNLqN-0001RL-Il
	for root@legend; Mon, 28 Jul 2008 08:04:27 +0200
Subject: [rkhunter] legend - Daily report
To: root@legend
Message-Id: <E1KNLqN-0001RL-Il@legend>
From: root <root@legend>
Date: Mon, 28 Jul 2008 08:04:27 +0200

Warning: The SSH and rkhunter configuration options should be the same:
         SSH configuration option 'PermitRootLogin': yes
         Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /etc/.sudoers.tmp.swo: Vim swap file, version 7.1
Warning: Hidden file found: /etc/.sudoers.tmp.swp: Vim swap file, version 7.1

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

From root@legend Tue Jul 29 09:18:02 2008
Return-path: <root@legend>
Envelope-to: root@legend
Delivery-date: Tue, 29 Jul 2008 09:18:02 +0200
Received: from root by legend with local (Exim 4.69)
	(envelope-from <root@legend>)
	id 1KNjT8-0007NY-D2
	for root@legend; Tue, 29 Jul 2008 09:18:02 +0200
Subject: [rkhunter] legend - Daily report
To: root@legend
Message-Id: <E1KNjT8-0007NY-D2@legend>
From: root <root@legend>
Date: Tue, 29 Jul 2008 09:18:02 +0200

Warning: The SSH and rkhunter configuration options should be the same:
         SSH configuration option 'PermitRootLogin': yes
         Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /etc/.sudoers.tmp.swo: Vim swap file, version 7.1
Warning: Hidden file found: /etc/.sudoers.tmp.swp: Vim swap file, version 7.1

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

From root@legend Wed Jul 30 08:03:33 2008
Return-path: <root@legend>
Envelope-to: root@legend
Delivery-date: Wed, 30 Jul 2008 08:03:33 +0200
Received: from root by legend with local (Exim 4.69)
	(envelope-from <root@legend>)
	id 1KO4ma-0007Oo-Oe
	for root@legend; Wed, 30 Jul 2008 08:03:32 +0200
Subject: [rkhunter] legend - Daily report
To: root@legend
Message-Id: <E1KO4ma-0007Oo-Oe@legend>
From: root <root@legend>
Date: Wed, 30 Jul 2008 08:03:32 +0200

Warning: The SSH and rkhunter configuration options should be the same:
         SSH configuration option 'PermitRootLogin': yes
         Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /etc/.sudoers.tmp.swo: Vim swap file, version 7.1
Warning: Hidden file found: /etc/.sudoers.tmp.swp: Vim swap file, version 7.1

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

From root@legend Thu Jul 31 08:59:43 2008
Return-path: <root@legend>
Envelope-to: root@legend
Delivery-date: Thu, 31 Jul 2008 08:59:43 +0200
Received: from root by legend with local (Exim 4.69)
	(envelope-from <root@legend>)
	id 1KOS8V-0007Jg-0n
	for root@legend; Thu, 31 Jul 2008 08:59:43 +0200
Subject: [rkhunter] legend - Daily report
To: root@legend

It seems rkhunter is sending them.

---

### Post by Hells_Dark on 2008-07-31
System mails.
For instance, cron send mail to theh system when it does something.

---

### Post by Vishal Agarwal on 2008-07-31
Once a user is added, his mail account is automatically created as a standard process in Linux system. Some times the system is generating mail automatically, which are delivered to user accounts and appears up as a new mail.

---

### Post by billgoldberg on 2008-07-31
Well, you learn something new every day.

Thanks for clearing it up.

---

