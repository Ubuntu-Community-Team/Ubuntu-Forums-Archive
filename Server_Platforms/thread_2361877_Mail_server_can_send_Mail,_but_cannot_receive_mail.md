---
title: "Mail server can send Mail, but cannot receive mail!"
date: 2017-05-21
forum: Server Platforms
---

### Post by whitekitty00 on 2017-05-21
Hello Ubuntu Community, I'm new to such type of forum, so please dont mind any amateur failures I may do!

I've used Webmin and an online tutorial to setup an Mail server and said accounts, I can successfully send E-Mails, even using ThunderBird (Still cant use Windows Mail to login, dont know why *Shrugs*), But I absolutely cannot receive mail, well, I DO receive mail, I saw them locally on my ftp (READABLE in a file?!), but ThunderBird and Webmin cannot find/access the file somehow, I'm Using PostFix & Dovecot for the Mail service, I do not know what exactly you need, like what configs and such, so please tell me what files I've to post here.

Best regards,

- Lisa.

---

### Post by TheFu on 2017-05-21
DNS and MX working?
ISP allowing SMTP on the port specified in the MX or do they block it?
Where is this mail server?  VPS, data center, company connection?  Or at home, behind a residential ISP?

Don't want to ask anything more until those questions are answered CLEARLY, please.

---

### Post by Michael_McKenney on 2017-05-22
I just setup two Exchange 2016 servers.  One on each ISP.   I needed to have A and MX record with public IPs for each server.  I have registered IP blocks inside my network.   I had to setup forwarding rules to go from the A/MX record through the firewall to the Exchange servers.   The MX record means your server is a real mail server.  A record is the IP address that is publically known for it.  You need both on your ISP to get inbound mail.

---

### Post by lisati on 2017-05-22
If the incoming mail is visible in a file on the server, then it's more likely to be a configuration issue on the mail server (or the email client) than DNS records and port blocking by the ISP. A check of the mail log might provide some clues as to what is happening.

---

### Post by whitekitty00 on 2017-05-24
> **lisati said:**
> If the incoming mail is visible in a file on the server, then it's more likely to be a configuration issue on the mail server (or the email client) than DNS records and port blocking by the ISP. A check of the mail log might provide some clues as to what is happening.

I've checked the mail.log & mail.error files, both showing nothing, infact, the mail.log only shows the successfull incomming of the E-Mail, I'm hosting it on an VPS hosted in germany, frankfurt, as said, using webmin to 'setup' the servers, I also enabled the debugging mode, but no error is showing, both, postfix & dovecot are running. I do not know what I shall do! I setup A & MX Records, the only error I get is sometimes 'Do not use the domain in both $mynetwork..' But I've looked online and dont see anyone saying that this is a problem.

Regards.

EDIT: I've just checked the mail.err log again, apparently it didn't update for me, its showing an sendmail error:

```
May 22 19:10:52 box postfix/sendmail[22205]: fatal: usage: sendmail [options]

```

---

