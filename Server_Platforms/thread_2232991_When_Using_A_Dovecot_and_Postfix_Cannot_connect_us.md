---
title: "When Using A Dovecot and Postfix Cannot connect using a domain only IP Address?"
date: 2014-07-05
forum: Server Platforms
---

### Post by T_V on 2014-07-05
[COLOR=#333333][FONT=UbuntuRegular]I have setup a Postfix, Dovecot, and RoundCube Sever On Ubuntu 12.04.4 x64 and It works great. I can use my url mail.myurl.com and it points to my roundcube and i can send and receive email. If I use Outlook or another other mail program i can connect to IMAP if i use my server static IP Address but not my url. i don't want to have to memorize an ip address when setting up emails on outlook and our phones. Any ideas where this may be? My hosts file has my url in it with my static ip address.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2014-07-05
[http://computer.howstuffworks.com/dns.htm](http://computer.howstuffworks.com/dns.htm)

Is your domain registered at a DNS registrar like [DirectNIC]("http://www.directnic.com/")? If not, that's the first step.  If so, you'll need to create an "A" record in your DNS records that points to the externally-visible IP of your mail server.

---

