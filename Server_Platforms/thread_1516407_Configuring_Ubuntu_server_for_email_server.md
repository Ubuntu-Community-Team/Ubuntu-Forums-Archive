---
title: "Configuring Ubuntu server for email server"
date: 2010-06-23
forum: Server Platforms
---

### Post by three_jeeps on 2010-06-23
Hello:
I am looking for some pointers on how to set up postfix as a mail server. Before I do that, I need to know if what I have done is sufficient:
I am running ubuntu 8.04 server. I use DynDns free web host redirects - my domain is
foo.homeunix.com, my  isp (comcast) is 24.168.22.34 (fictious address), my ubuntu server has a 
static ip address of 192.168.0.100 and behind a cable modem router.

I have configured my DynDNS host as a record pointed to an IP address to map my local server IP address to the comcast ISP address.  
Question: Is this configuration sufficient to allow postscript on my server to operate as a mail server
(when properly configured?)
If not, what needs to be done? DynDns also has a service that sets the MX records for my host.
Question: Do I need to configure the MX records for my host to make it email routing work?

Question:  Assuming the above is sufficient (and if necessary MX records configured), is there a guide that
will explain how to configure postfix as an outbound only server?

I understand that Postfix is the default MTA in Ubuntu server. Question: what is the default mail program (e.g. what I run from the CL to read email) in ubuntu server 8.04? Do I need to disable it to run postfix?


Alternative approach: If I want to configure Postfix as an outbound only server, relaying through my 
gmail account, how can this be done? Is the above configuration through DynDns sufficient? if not, what is missing.
Thank you for your help
-J

---

### Post by jbrown96 on 2010-06-23
You will need to forward ports from your router. [http://www.emailaddressmanager.com/tips/mail-servers.html]("http://www.emailaddressmanager.com/tips/mail-servers.html")

For the guide, I hate to be a jerk but seriously. [http://lmgtfy.com/?q=ubuntu+postfix]("http://lmgtfy.com/?q=ubuntu+postfix")

---

### Post by three_jeeps on 2010-06-23
> **jbrown96 said:**
> You will need to forward ports from your router. [http://www.emailaddressmanager.com/tips/mail-servers.html]("http://www.emailaddressmanager.com/tips/mail-servers.html")

Thank you....forgot about that....

> **jbrown96 said:**
> For the guide, I hate to be a jerk but seriously. [http://lmgtfy.com/?q=ubuntu+postfix]("http://lmgtfy.com/?q=ubuntu+postfix")

Well, seriously though, I did google it...problem is, and I thought I described it in my post, I need to know if my base configuration is correctly set up...Specifically, I need to have verified that by signing up for ip mapping at dyndns, and port forwarding for IMAP, that if I send an email to [email]user@foo.homeunix.com[/email] that the packet will hit the server.
Only after that can I begin to work through the tutorials I have.
Thanks
-J

---

### Post by jbrown96 on 2010-06-24
If dyndns points to your IP address and you have your MX record set up, then it won't be an issue at all.

---

