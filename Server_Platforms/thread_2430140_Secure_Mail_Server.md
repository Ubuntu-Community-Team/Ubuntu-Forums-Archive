---
title: "Secure Mail Server"
date: 2019-10-28
forum: Server Platforms
---

### Post by lordofscripts on 2019-10-28
Can anybody point me to how I can configure ubuntu desktop to also fulfill the function of a secure/robust mail server?

---

### Post by TheFu on 2019-10-28
> **lordofscripts said:**
> Can anybody point me to how I can configure ubuntu desktop to also fulfill the function of a secure/robust mail server?

Not possible these days.  Definitely not possible with a desktop/GUI loaded.
Perhaps in 1995, it was, but email is the front lines for attacks. the last 15 yrs.
I don't even allow my email server direct access to the internet.  There is a gateway email box that handles in/out and nothing else.

Here's an option for someone who isn't expert at Unix and email security:
[http://www.scrolloutf1.com/](http://www.scrolloutf1.com/) is an easy email gateway. Just be certain to lock down the webapp so it cannot be accessed except from localhost (via ssh tunnel).  Then you can setup your *real email server* on a secured network that isn't accessible by the bad people on the internet.

---

### Post by kevdog on 2019-10-28
Shoot I don't have a link however I am aware there are plenty of tutorials on how to set up a postfix,dovecot servers (try searching Ars Technica -- they had a large story by one of the contributors who did this as a project).  If you are trying to run this from home in the US, please be aware the port 25 and other ports are commonly blocked by many ISPs to prevent the home user from running an email server.  What I did, was set up an regular gmail account, purchased a domain name and use Cloudflare as my DNS provider (domain name not free but Cloudflare is free).  I then use a service called mailgun (also free), which is an email forwarder so people can email me at my domain name and then it gets forwarded to my gmail address.  You need to alter your DNS records with txt and mx entries for this to work however with Cloudflare its pretty easy to do.  You might also have to enable DMARC (mxtoolbox has a lot of information on this) for your domain as well.  This also can be configured through mailgun and Cloudflare.  All in all setting up an email server -- although tempting -- is really a pain in the ass, and requires a lot of maintenance.

---

### Post by SeijiSensei on 2019-10-29
I have three mail servers, one that only receives and forwards all the traffic over an OpenVPN tunnel to a second server which does spam and virus processing.  That server delivers the outgoing mail. I have a third server in my house for my family's email and a couple of friend's accounts also connected via an OpenVPN tunnel.  Only the first server accepts inbound traffic. 

Having the OpenVPN tunnel between my home server and my sending server in the cloud gets around the fact that my ISP blocks outbound traffic to remote SMTP servers. (This practice arose not so much to block home email servers, but to block the millions of Windows computers that were converted by malware into running spambots about a decade ago.)

I've been running mail servers for two decades now.  It still requires attention to keep up with all the additional anti-spam armament providers have added to their servers.  I just added DKIM signing to my servers that originate mail for that reason. I manage listservers and still have to open tickets at Yahoo and cope with Mimecast to insure our mail gets delivered promptly. (Yes, I have SPF records, but I don't use Domain Keys. I figured DKIM was enough.)

I run my own DNS servers on my cloud machines.

If we haven't yet discouraged you from running a mail server, the first thing you need to determine is whether your machine can even send mail.  Open a terminal and run the command:
```
telnet gmail-smtp-in.l.google.com 25
```
If you're not blocked, you'll see a banner like this:
```
220 mx.google.com ESMTP a12si3393689pjw.50 - gsmtp
```
If the connection fails, you cannot run a mail server over your current Internet connection.

---

