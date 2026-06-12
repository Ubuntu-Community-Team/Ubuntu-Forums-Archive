---
title: "Citadel domain issues"
date: 2014-02-18
forum: Server Platforms
---

### Post by Ewan_Frost on 2014-02-18
I've set up Citadel on a VPS hosted by servergrove, but I'm having some issues. The node only is receiving emails for [email]user@server.domain.com[/email] and not [email]user@domain.com[/email]. Any advice?

---

### Post by volkswagner on 2014-02-18
Check the logs:

```
tail -f /var/log/mail.info
```

Then send a message to [email]user@domain.com[/email]

Do logs show any info?

Create a new user and see if this new user can receive mail.

What version are you using?

If you don't see any info in log, do you have mx records for domain.com?

Does sender message get returned?  What error do they get?

---

### Post by Ewan_Frost on 2014-02-18
[COLOR=#333333][FONT=Helvetica Neue]Thanks for the reply. No changes in the logs. Versions are [/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]Ubuntu 12.04.4 LTS, and [/FONT][/COLOR]Citadel 7.86.[COLOR=#333333][FONT=Helvetica Neue]

One thing I noted is that servergrove defaults the VPS to server.domain.com, and enforces the hostname of server and FQDN on restart. Having changed this via the control panel however, it had no effect.[/FONT][/COLOR]

---

### Post by volkswagner on 2014-02-18
Sounds like you don't have mx record setup.

Check the mx records for you domain at [mxtoolbox.com]("http://mxtoolbox.com/SuperTool.aspx")

You need dns entries so the world know where to send mail for domain.com.

---

### Post by Ewan_Frost on 2014-02-18
MX records are set. The mail domain is my domain, and the Mail Exchanger is set to mx.servergrove.com, is that right?

Given a hostname of "server", a FQDN of server.domain.com, is a mailname of domain.com correct, and what is correct node name and Fully qualified domain name within Citadel? Really do appreciate all the help man.

---

### Post by volkswagner on 2014-02-18
That does not sound correct.

Lets say your citadel server will host mail for domain.com.
Your citadel server name is server.domain.com.

You'll want MX records for domain.com to point to server.domain.com.
Youll want a DNS A record for server.domain.com to point to your server's public ip address.

So when you put domain.com into mxrecords.com it should show
10 server.domain.com or the priority number you set.

You'll also want your reverse DNS set to server.domain.com.

Hope this helps.

---

### Post by Ewan_Frost on 2014-02-19
Day two of using a Linux server, got the original set up working and have since broken it again, but having a lot of fun doing so.

I've now set up two virtual hosts for domainA and domainB. The hostname is server.domainB.com, and it uses servergrove's webmail functionality and as such the mx records point to that. 
Any idea how I would configure the mx records for serverA to recieve email via [email]user@serverA.com[/email]?

---

### Post by Ewan_Frost on 2014-02-19
Nevermind. Figured it out, got the hang of mx records now

---

