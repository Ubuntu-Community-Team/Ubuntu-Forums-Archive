---
title: "Problems with setting up Postfix"
date: 2011-09-09
forum: Server Platforms
---

### Post by Ir77 on 2011-09-09
Hello,

For some days now I've been trying to get postfix working right.

The situation is like this

I have a ubuntu server running 10.04 lts and some workstations running also 10.04 lts and thunderbird mail. Also 3 users logging on with vpn (using windows 7 and mac os).

- retrieving a catchall pop box with getmail 
- dovecot as imap mailserver
- postfix as mta

There is one central imap mailbox that all the users can access. I can access the imap mailbox from all the machines and I can receive new mail.

I want also all the sent mail be collected in one sent box on the imap server. So everybody can see what has been sent.

I can send e-mail from the server itself, but I'm unable to send e-mail through the clients using the server as smtp server. Think it must be an authentication problem.

when I do sudo dpkg-reconfigure postfix. I don't know exactly what to fill in in hostname (I use the local server name now)

I configured everything using the [guide]("https://help.ubuntu.com/community/Postfix")
Doing telnet doesn't give me

```

250-STARTTLS 250-AUTH

```When I try to send an e-mail thunderbird comes up with a 5.7.1 relay access denied error


I found it myself allready

in main.cf I had to change my networks to add the local domain 192.68.2.0/24 

now I can send e-mail :)

---

