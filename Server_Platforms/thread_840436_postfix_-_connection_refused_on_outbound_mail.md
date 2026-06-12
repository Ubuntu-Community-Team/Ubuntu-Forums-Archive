---
title: "postfix - connection refused on outbound mail"
date: 2008-06-25
forum: Server Platforms
---

### Post by asmweb on 2008-06-25
Hi there,

on my company I'm trying to set up a mailserver using Postfix. I did install the service and I guess configure it:

here is my main.cf

mydomain = xxx.it
mydestination = $myhostname, localhost.$mydomain, $mydomain,
myorigin = $mydomain, localhost
inet_interfaces = all
relay = 

....

well when I try to send a mail to, lets say gmail, I get the connection refused:


un 25 17:40:22 hostname postfix/smtp[12937]: connect to alt1.gmail-smtp-in.l.google.com[209.85.147.114]: Connection refused (port 25)
Jun 25 17:40:22 hostname postfix/smtp[12937]: connect to alt1.gmail-smtp-in.l.google.com[209.85.147.27]: Connection refused (port 25)
Jun 25 17:40:22 hostname postfix/smtp[12937]: connect to gsmtp147.google.com[209.185.147.27]: Connection refused (port 25)
Jun 25 17:40:22 hostname postfix/smtp[12937]: connect to gsmtp183.google.com[64.233.183.27]: Connection refused (port 25)
Jun 25 17:40:22 hostname postfix/smtp[12937]: 87E3A61E0D: to=<xxx@gmail.com>, relay=none, delay=0, status=deferred (connect to gsmtp183.google.com[64.233.183.27]: Connection refused)


Actually I can not understand why that's happening. Any help would be appreciated.

thanks

---

### Post by unixbills on 2008-06-25
Google will not accept the connection becuase they can't do a reverse lookup on your mail server.  You look like an open spammer.  You need to be a valid host from a valid domain that they can lookup.  Where does your SMTP from your clients go now?  Point your SMTP to your ISP's mail server.

I don't know anything about postfix.  Here is something on DNS and SMTP:
  [http://bind8nt.meiway.com/itsaDNSmess.cfm](http://bind8nt.meiway.com/itsaDNSmess.cfm)

---

### Post by asmweb on 2008-06-26
No, I don't think I've all those information configured. I've just a static IP that the company has and we're planning to host a dozen of domains into it (none yet active) and I thought to go ahead with virtual domains setup.
So, what should I do is I need to have a DNS record that points to the IP of the machine, am I correct?

---

### Post by justinlawrence on 2008-09-15
thanks for the help. i see our server didn't have reverse dns record and have sorted it out!

---

