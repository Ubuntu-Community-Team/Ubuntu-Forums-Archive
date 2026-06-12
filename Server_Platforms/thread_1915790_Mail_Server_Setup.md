---
title: "Mail Server Setup"
date: 2012-01-26
forum: Server Platforms
---

### Post by 1-Up on 2012-01-26
I'm new to trying to setup a mailserver.

I followed this guide: [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
and installed: Postfix, PostfixAmavisNew, PostfixGreylisting, and Dovecot.

Postfix is configured for system mail name to be cybertechind.com (is prefix needed/required?)

I also followed this guide on dovecot wiki to potentially setup virtual users: [http://wiki.dovecot.org/HowTo/SimpleVirtualInstall](http://wiki.dovecot.org/HowTo/SimpleVirtualInstall)
With the quota option I created 1 test user with a plain text password.

To connect with an email client is this all I need to setup?  I could not seem to get any results when trying to connect with Opera Mail and using POP3 with or without TLS encryption.  I used cybertechind.com as incoming/outgoing server.

Does anything else have to be done in terms of the domain name to get a mail server working?  I'm kind of lost in what could be messed up or not setup yet.

---

### Post by 1-Up on 2012-01-28
bump

---

### Post by HermanAB on 2012-01-29
Howdy,

You need a domain name registered and DNS configured with A, PTR and MX records, otherwise fuhgeddaboudit...

---

### Post by 1-Up on 2012-01-29
I've got a domain name registered and it works with website, game servers, etc.  I'm not familiar with what A, PTR and MX records are. Do I need to install anything else on my Ubuntu server for this stuff, or are these settings I need to mess with in my godaddy account?

Edit:
Ok, I found A and MX settings in my domain controls, however I did not see a PTR setting.  I changed anything related to email to mail.cybertechind.com.  I need to change all the server email software settings to reflect this, yes?

---

### Post by 1-Up on 2012-02-01
Is there something else I could be missing or doing wrong?

---

### Post by 1-Up on 2012-02-03
bump

---

### Post by lisati on 2012-02-03
The cpanel for one of my domains doesn't seem to have an option for me to set PTR either, I'm able to receive mail through that domain without having to tinker with it.

---

### Post by volkswagner on 2012-02-04
> **1-Up said:**
> Is there something else I could be missing or doing wrong?

It looks like you have the MX setup correctly.

I believe you need an A record also for mail.yourdomain.com to point to the ip address of your mail server.

---

