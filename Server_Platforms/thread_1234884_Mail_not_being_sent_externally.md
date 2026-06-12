---
title: "Mail not being sent externally"
date: 2009-08-08
forum: Server Platforms
---

### Post by GHowlerson on 2009-08-08
Hi,

I've just migrated a site onto a new dedicated server (Ubuntu), and am having a problem.

The site's domain, call it mydomain.com, has its DNS hosted elsewhere. We've pointed A records for @ and WWW to the IP address of the new server. This works great, and the web end of things is working nicely. Email for mydomain.com is handled elsewhere.

The website sends emails using PHP's mail() function. Some of those emails go to @mydomain.com email addresses. However, the server is not attempting to send these out externally, so they aren't reaching the mail server handling mail for mydomain.com.

Emails sent to other addresses (not @mydomain.com) are sent fine, so there isn't a problem with sendmail.

Any idea what I need to change on the server to allow it to send the emails for @mydomain.com externally?

---

### Post by The Tronyx on 2009-08-08
Greetings.  If I had to guess, the server is trying to deliver the mail locally which shouldn't be the case.  You can test this by trying to send mail to [email]realaddress@mydomain.com[/email] but make sure that [email]realaddress@mydomain.com[/email] does NOT exist on your dedicated server.  You should see something in the mail log about how a mailbox for that user does not exist.  This indicates that it is trying to send the mail locally and it cannot deliver it to that address since obviously, that address does not exist on the local server.

I am not sure what mail service you are using but if it's Exim, you may want to look into local_domains and remote_domains.  You can explicitly set which domains are NOT to be handled locally.

Best of luck.

---

### Post by GHowlerson on 2009-08-08
Thanks very much for your reply. Yes, I'm pretty sure that the server is trying to deliver the mail locally. 

Any idea what the default mail server is on Ubuntu 8.04? I haven't configured anything mail-wise on this machine; it's just a web server, but needs to send out some emails using PHP mail().

---

### Post by The Tronyx on 2009-08-08
> **GHowlerson said:**
> Thanks very much for your reply. Yes, I'm pretty sure that the server is trying to deliver the mail locally. 

Any idea what the default mail server is on Ubuntu 8.04? I haven't configured anything mail-wise on this machine; it's just a web server, but needs to send out some emails using PHP mail().

Unfortunately I am not totally sure what the default mail service is on Ubuntu since pretty much all of my server experience is on RH/CentOS.  You could however try ps aux | grep -i exim or ps aux | grep -i mail which should tell you what is doing what.  

It could also be that it is just using sendmail but sendmail is fairly insecure and lacks good logging by default.  As a result, sendmail can often be wrapped in another mail service for better logging, i.e. a call to sendmail will actually use exim.

There may be a similar implementation for local_domain/remote_domain for plain old sendmail but I cannot be positive on that.

---

