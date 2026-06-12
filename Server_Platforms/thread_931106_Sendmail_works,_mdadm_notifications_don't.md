---
title: "Sendmail works, mdadm notifications don't"
date: 2008-09-26
forum: Server Platforms
---

### Post by Uaine on 2008-09-26
I've been testing my raid array, trying to get e-mail notifications to go through when mdadm is running in monitor mode.

I'm using esmtp as my MTA. My sendmail command works fine normally.  However, when mdadm tries to send an email, I receive an error:

[email]name@gmail.com[/email]: 550 [PERMFAIL] gmail.com requires valid sender domain

I thought that mdadm simply invokes sendmail to send email notifications.  If this is the case, why could my sendmail be malfunctioning for this, but working for everything else?  If I am misunderstanding how mdadm works, can somebody please enlighten me?

edit:
Okay, the more I read, the more I find the consensus that ESMTP is not a good MTA to use.  The reason I went with it is because I only need a simple MTA that sends email out - that's it.  I have no need to receive.

I managed to get exim4 working, after a lot of trouble.

---

### Post by Krupski on 2008-09-30
> **Uaine said:**
> I've been testing my raid array, trying to get e-mail notifications to go through when mdadm is running in monitor mode.

I'm using esmtp as my MTA. My sendmail command works fine normally.  However, when mdadm tries to send an email, I receive an error:

[email]name@gmail.com[/email]: 550 [PERMFAIL] gmail.com requires valid sender domain

I thought that mdadm simply invokes sendmail to send email notifications.  If this is the case, why could my sendmail be malfunctioning for this, but working for everything else?  If I am misunderstanding how mdadm works, can somebody please enlighten me?

edit:
Okay, the more I read, the more I find the consensus that ESMTP is not a good MTA to use.  The reason I went with it is because I only need a simple MTA that sends email out - that's it.  I have no need to receive.

I managed to get exim4 working, after a lot of trouble.

Did you edit your /etc/mdadm/mdadm.conf file and put your email address onto the 'MAILADDR' line?

Like this:

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#
<snipped out>
# instruct the monitoring daemon where to send mail alerts
MAILADDR **[COLOR="Red"]email-name@domain.com[/COLOR]**
<snipped out>

```

---

