---
title: "Best way to change email server on a live system?"
date: 2012-07-12
forum: Server Platforms
---

### Post by rs2k on 2012-07-12
I'm current using Citadel as my email server for sending, receiving and webmail.

I'm currently having "game breaking" issues with citadel and think I shows find something else to replace it with. i.e. Message filters imply don't work.

What's the safest way to switch from one email server to another without loosing emails?

The reason I'm using citadel is because it was very easy to use and setup. What other options are out there? I've used Postfix and Sendmail in the past, but have always had trouble setting them up. The email server is the one part of the system I'm not comfortable with.

---

### Post by newbie-user on 2012-07-12
Set up your MX records to list both your email servers. That way if one goes down, the other will still pick up email.

As for other options, I traditionally used postfix and courier, later dovecot. But then I recently switched my company over to Google Apps and let Gmail handle all the email.

---

### Post by rs2k on 2012-07-12
will gmail let you use "admin@mycompany'surl.com"?

---

### Post by Cheesemill on 2012-07-13
Yes.

[http://www.google.com/intl/en_uk/enterprise/apps/business/products.html](http://www.google.com/intl/en_uk/enterprise/apps/business/products.html)

---

### Post by rs2k on 2012-07-15
That looks good, how would I set it up so the server can send a massage if there's no email server on the server?

I use the mail() function quite often in php.


I found some instructions for a single email below, but how would I do it so I can send email from 10 different domains and 3 or 4 different users on each domain:

> Easiest way to do this is to avoid using exim and to use sSMTP which is a lightweight MTA.

All you need to do is install it:

sudo apt-get install ssmtp mailx

and configure it (edit /etc/ssmtp/ssmtp.conf) to use your Google Mail servers see:

root=noreply@yourdomain.com
mailhub=smtp.gmail.com:587
UseSTARTTLS=yes
UseTLS=yes
AuthUser=youremail@yourdomain.com
AuthPass=password
FromLineOverride=YES

I've been using this set-up for a while now and it just works - It's also nice to not need to be running exim when it's not necessary and let Google's mail servers handle everything for you.


---

### Post by LHammonds on 2012-07-15
Zimbra has a free, open source version.  I am in the process of setting up a Zimbra mail server to replace our current MS Exchange 2003 server.

Check my sig for a like to my click-for-click setup documentation.

LHammonds

---

