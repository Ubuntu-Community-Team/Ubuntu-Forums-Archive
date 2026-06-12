---
title: "How to get email notifications from DenyHosts?"
date: 2009-05-11
forum: Security
---

### Post by MountainX on 2009-05-11
I installed DenyHosts and I edited these values in /etc/denyhosts.conf

SMTP_HOST = smtp.gmail.com
SMTP_PORT = 465
SMTP_USERNAME=me@my_google_apps.com
SMTP_PASSWORD=my_password

I want to get email notices from DenyHosts.

But I don't think it's going to be as simple as setting these value, although I wish it was.

Is there a very simple way to get this to work without installing anything like ssmtp or postfix?

---

### Post by cariboo on 2009-05-12
Do you exim or some other mta installed?

---

### Post by MountainX on 2009-05-12
> **cariboo907 said:**
> Do you exim or some other mta installed?

Well, I do have [phpmailer]("http://phpmailer.sourceforge.net/"). Drupal (my blog) uses it. I have never directly used it and I don't know php. 

[One site]("http://www.askapache.com/php/phpfreaks-eric-rosebrocks-phpmailer-tutorial.html") says, "PHPMailer is a fully featured email transfer class for PHP that I would put above all of the other E-Mail handlers that I’ve used."

Is it possible to utilize phpmailer for DenyHosts?

---

### Post by MechaMechanism on 2009-05-12
> **MountainX said:**
> I installed DenyHosts and I edited these values in /etc/denyhosts.conf

SMTP_HOST = smtp.gmail.com
SMTP_PORT = 465Would DenyHosts know to use SSL?

---

### Post by MountainX on 2009-05-12
> **MechaMechanism said:**
> Would DenyHosts know to use SSL?

You're right. DenyHosts probably doesn't know to use SSL. So I switched to my ISP's smtp and port 25. Do you think that will work? Or do I need some mta like ssmtp (I hope not).

---

### Post by MechaMechanism on 2009-05-12
> **MountainX said:**
> You're right. DenyHosts probably doesn't know to use SSL. So I switched to my ISP's smtp and port 25. Do you think that will work? Or do I need some mta like ssmtp (I hope not).
You don't need an MTA if your ISP mail works.  I assume that your ISP provided email account is the typical port 25 and no SSL?  If your ISP mail is simple, then I would go that route.  I don't use gmail but I think you can forward the ISP mail to Google, maybe Google has an account fetcher.  A friend of mine gets his ISP mail through Google somehow.

---

### Post by MountainX on 2009-05-12
> **MechaMechanism said:**
> You don't need an MTA if your ISP mail works.  I assume that your ISP provided email account is the typical port 25 and no SSL?

Thanks. Do you know if there is an easy way to verify that I have DenyHosts set up correctly? I am using my ISP mail with port 25 and I have tested those settings using telnet (works). Now I just need to see if DenyHosts will use them (without an mta installed). But I'm not sure how to test that.

---

### Post by MechaMechanism on 2009-05-12
Well I assume your using DenyHosts because you have an SSH server.  If you do indeed have SSH server then I would do a bogus SSH login attempt, with bad username and password 10 times in a row or something like that.  The main thing is to generate bad SSH login attempts.  Obviously if the SSH server is remote, like say greater than 30 minutes away it might be painful to lock your self out for a test.  If the server is local then you can simply do a local login and edit hosts.deny.

P.S. Or you can just wait for an legitimate evil attempt. :twisted:

---

### Post by MountainX on 2009-05-12
Thanks. I'll just wait for a real case. What I'll do is monitor hosts.deny and when an IP gets added, if I don't get an email, I'll know there is a problem.

---

### Post by eignerchris on 2010-05-09
google's smtp server requires a starttls command before authentication can take place. see below...


starting DenyHosts:    /usr/bin/env python /usr/local/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg
Error sending email
(530, '5.7.0 Must issue a STARTTLS command first. 

denyhosts doesn't support ssl/tls right now, but there is a feature request for it: [http://sourceforge.net/tracker/?func=detail&aid=1592189&group_id=131204&atid=720422](http://sourceforge.net/tracker/?func=detail&aid=1592189&group_id=131204&atid=720422).

---

### Post by masticazzi on 2011-03-29
Hi,

all you need to do is to use *stunnel* as a client for the GMail server.

example conf file:

```
; Use it for client mode

client = yes

; Service-level configuration

[ssmtp]
accept  = 25
connect = smtp.gmail.com:465
```


once properly configured, just set denyhost to send an email to your port 25

```
#######################################################################
#
# SMTP_HOST and SMTP_PORT: if DenyHosts is configured to email 
# reports (see ADMIN_EMAIL) then these settings specify the 
# email server address (SMTP_HOST) and the server port (SMTP_PORT)
# 
#
SMTP_HOST = localhost
SMTP_PORT = 25
```


Success! :guitar:

Regards
Alessandro

---

### Post by MountainX on 2011-03-29
> **masticazzi said:**
> Hi,

all you need to do is to use *stunnel* as a client for the GMail server.


Perfect! Thanks.

EDIT: solved after 2 years!!!

---

