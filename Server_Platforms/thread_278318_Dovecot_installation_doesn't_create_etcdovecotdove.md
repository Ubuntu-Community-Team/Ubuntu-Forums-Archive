---
title: "Dovecot installation doesn't create /etc/dovecot/dovecot.conf"
date: 2006-10-16
forum: Server Platforms
---

### Post by AndrewClarke on 2006-10-16
I'm fairly new to Ubuntu but have been running Dovecot on Debian successfully for a year or two.  I just got a new Intel Core 2 duo server and installed Ubuntu x64 in a VMWare virtual machine as my new email server.

I've tried "sudo apt-get install dovecot-common dovecot-imapd" but I get an error that it can't create /etc/dovecot/dovecot.conf.

I tried creating a blank file here, and that got rid of the error, but the installation process didn't put anything in there.  I tried "dpkg-reconfigure dovecot-common" but that didn't add anything either.

I tried copying the dovecot.conf file from my working Debian server and modifying accordingly, and got Dovecot to sort of start, but the best I could get was that it would "sort of" work, in that running "/etc/init.d/dovecot start" wouldn't thrown an error, but I couldn't reliably telnet to port 143 or 993 (I usually just have IMAPS open).

Does Dovecot just not work in x64 or am I doing something wrong here?

Thank you very much,
- Andrew Clarke.

---

### Post by AndrewClarke on 2006-10-17
I have this working.  I copied my working dovecot configuration from my Debian server, and realized my problem was due to incorrect firewall rules.  I was forwarding the wrong port.  Duh.

I still see a problem with the installation where it doesn't create /etc/dovecot/dovecot.conf but at least I have it working.

- Andrew.

---

