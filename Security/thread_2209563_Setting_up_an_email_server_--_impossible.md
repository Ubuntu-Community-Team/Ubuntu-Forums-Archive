---
title: "Setting up an email server -- impossible?"
date: 2014-03-06
forum: Security
---

### Post by ljungkvist on 2014-03-06
So I've been trying to set up a combined postfix / dovecot server for receiving and sending mails, mostly following this guide:

[http://superuser.com/questions/605521/the-simplest-way-to-set-up-a-secure-imap-email-server](http://superuser.com/questions/605521/the-simplest-way-to-set-up-a-secure-imap-email-server)

I've now managed to get most things working including ssl/tsl. However, I'm still not able to receive emails at all. Also I cannot send email out of the server if I do not specify a relayhost (in that case it works perfectly). I can send emails using telnet both from within the server, and from within the local network. However, I cannot access it from outside the network.

Here is where I'm confused. I can ssh into the server from outside the network, so it certainly is accessible, even on a custom ssh port. Also, I can telnet into port 25 from within the local network. And if i do an nmap from within the network, ports 25 and 465 are open. However, from outside the local network, all ports are listed as 'filtered', except for port 22 which is 'closed' and my custom ssh port which is 'open'. What does it mean for a port to be filtered, and how can I determine the reason for this, and possibly fix it? Finally, am I trying to do something which cannot be done -- is it impossible to have different email providers, such as google, etc, deliver mail directly to my server?

---

### Post by SeijiSensei on 2014-03-06
Your ISP may block inbound port 25.  Most residential Internet accounts ban servers, and some ISPs enforce the rule by blocking inbound traffic.  You'll need to read your Terms of Service and talk to them to see if this is the case for you.

---

### Post by ljungkvist on 2014-03-07
The server is at my work network, for which the ISP seems to be SUNET -- the swedish univeristy network. I honestly don't know what their policy is on this matter. I'll look into this.

Anyway, is it true that with port 25 blocked, it will be impossible to have mail delivered to it? What about the other ports, 465 and 578? As I said above, connecting by SSH on many different ports works. Here is probably where I'm confused.

---

### Post by sh4d0w808 on 2014-03-07
> **ljungkvist said:**
> The server is at my work network, for which the ISP seems to be SUNET -- the swedish univeristy network. I honestly don't know what their policy is on this matter. I'll look into this.

Anyway, is it true that with port 25 blocked, it will be impossible to have mail delivered to it? What about the other ports, 465 and 578? As I said above, connecting by SSH on many different ports works. Here is probably where I'm confused.

If a port is blocked then you can't communicate with it. One possible solution is to ask your ISP to release block on port 25.

---

### Post by Thee on 2014-03-07
Did you setup a MX record for your domain?

---

