---
title: "Can anyone create a detailed guide for a postfix server running on at&amp;t internet?"
date: 2011-04-18
forum: Server Platforms
---

### Post by paul.bono on 2011-04-18
Hey I'm a newbie when it comes to postfix/email setup.  I currently have a personal use server setup in my home and would like to be able to send emails from my domain name.

At&t blocks the standard ports used so some form of forwarding would have to be used.  I've looked at other guides and followed them to the key but it appears I'm always missing something.

So my question here is could anyone write a detailed guide from start to finish on how to install a postfix server behind an at&t connection complete with MX record and firewall configuration information?  It would be greatly appreciated.

Thanks!

---

### Post by falko on 2011-04-19
If standard ports are blocked, I'd set up email accounts on a server in a data center/at your ISP/some other mail provider and then use fetchmail or getmail to retrieve emails from this server:

[http://www.howtoforge.com/debian_etch_fetchmail](http://www.howtoforge.com/debian_etch_fetchmail)
[http://www.howtoforge.com/debian_etch_getmail](http://www.howtoforge.com/debian_etch_getmail)

To send emails, set up relaying: 

[http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver)

---

### Post by hawk2010 on 2011-04-19
Hey here is one site which helped me

[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)

Also main points you should consider when settings up a mail server are

1. Enable SMTP-Authentication - Prevent Open Relay
2. Enable Submission 
3. Enable TLS security
4. You need to contact AT&T to put the reverse DNS entry (this is vital or mails will get dropped from most places)
5. Have a backup MX record
6. Port forwarding at the DSL router


> **paul.bono said:**
> Hey I'm a newbie when it comes to postfix/email setup.  I currently have a personal use server setup in my home and would like to be able to send emails from my domain name.

At&t blocks the standard ports used so some form of forwarding would have to be used.  I've looked at other guides and followed them to the key but it appears I'm always missing something.

So my question here is could anyone write a detailed guide from start to finish on how to install a postfix server behind an at&t connection complete with MX record and firewall configuration information?  It would be greatly appreciated.

Thanks!

---

### Post by paul.bono on 2011-04-19
> **falko said:**
> If standard ports are blocked, I'd set up email accounts on a server in a data center/at your ISP/some other mail provider and then use fetchmail or getmail to retrieve emails from this server:

[http://www.howtoforge.com/debian_etch_fetchmail](http://www.howtoforge.com/debian_etch_fetchmail)
[http://www.howtoforge.com/debian_etch_getmail](http://www.howtoforge.com/debian_etch_getmail)

To send emails, set up relaying: 

[http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver)


This definitely seems like an option, would you possibly be able to suggest any cheap email service that would send on behalf of my domain?  I've looked around and found fastmail.fm but in order to send from my domain I would need to pay 39.99 a year which for personal use seems steep.

Found google apps.

---

### Post by hawk2010 on 2011-04-21
Well I really do not know about paid relays. But you can use Dyndns and have your mx record pointed to that so your mail will get delivered and you will be able to send as well

---

