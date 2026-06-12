---
title: "Emails blocked?"
date: 2013-04-04
forum: Server Platforms
---

### Post by Gogeden on 2013-04-04
Hello, I just recently set up a mail server using Ubuntu Server 12.04.
I use fetchmail and sendmail and Mutt to deal with emails and I pull my email from Riseup's mail servers.

I receive emails just fine.
My problem lies with sending emails.

No matter what MSP I send to, I get blocked by their spam filters and the mail gets returned to me with a description that it was labeled as spam.
I'm thinking it's the domain name of my server but I'm not sure.

Does anyone have any ideas?

Thanks!

---

### Post by spynappels on 2013-04-05
You could check your IP address against a spam blacklist:

Go to [http://mxtoolbox.com/blacklists.aspx](http://mxtoolbox.com/blacklists.aspx)
Enter your domain and/or your public IP

---

### Post by smtp on 2013-04-05
Would be possible to provide here error you getting?

---

### Post by darkod on 2013-04-05
Also, sometimes residential IPs are blocked for sending mails. Providers have the ranges assigned and residential ranges can have limitations.

It even hapenned with our static public IP at work even though we are a company. It was blocked for sending emails as a residential range. I had to do a procedure to unblock it so we could send emails.

---

### Post by lisati on 2013-04-05
Are you sending emails directly from your server? If so, is it on a dynamic public IP address?

---

### Post by Azrayal on 2013-04-05
Check if your ISP has a SMTP server available for use, some ISP's restrict users to using only provided SMTP gateways.

---

### Post by Gogeden on 2013-04-23
I will get back to you all later on today. I had forgotten I posted this. Thanks for the responses!

---

