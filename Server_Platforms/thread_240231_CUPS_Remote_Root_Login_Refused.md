---
title: "CUPS Remote Root Login Refused"
date: 2006-08-20
forum: Server Platforms
---

### Post by jobertel on 2006-08-20
From remote PC on the LAN it is possible to access CUPS web management interface. When trying to perform administrative functions am prompted for a username and password, but get the message: "Unauthorized
Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing)."

The box on which I am trying to run CUPS is Ubuntu 2.6.12-9-686, a recent version of Ubuntu server. Gnome and KDE are not installed since I ultimately want to run this as a headless print and file server. The root account has been enabled, and I can login remotely as root using ssh.

Below is the /admin portion of cupsd.conf.

<Location /admin>

AuthType Basic
AuthClass System

## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow from 192.168.1.0/24

#Encryption Required
</Location>

From what I have read root is by default a member of the lpadmin group. Therefore I should not have to do anything with a cupsys shadow group unless I want to enable some other user to perform administrative duties in CUPS.

Since this might be due to the unique way Ubuntu uses the root account I am posting this on both cups and ubuntu forums.

John B.

---

### Post by ethridgt on 2006-08-20
I couldn't get it working either.  However, I did get my printer configured.  Check out a howto post I just posted.  Search for "howto configure cups command line".

I hope that helps.

---

### Post by jobertel on 2006-08-21
Thanks,

It took enabling the shadow password per the debian README file.

John B.

---

