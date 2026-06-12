---
title: "postfix: where's my smtpd.conf file?"
date: 2006-08-23
forum: Server Platforms
---

### Post by psyncho on 2006-08-23
Hi, 

I don't seem to have this file:
/etc/postfix/sasl/smtpd.conf

I was following the simple howto on the ubuntu server guide when trying to do this:

echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf

generated an error. So I went to the directory to see if I couldn't just edit it in myself, to find that there is no file there.  What gives?

thanks, 
John

---

### Post by ciscosurfer on 2006-08-23
There are many ways to do this, just bear that in mind...and mine is only one way:
If the file doesn't exist yet, simply create it and add 'pwcheck_method: saslauthd' to the file```
sudo touch /etc/postfix/sasl/smtpd.conf
sudo su
echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf
```

---

### Post by JeevesBond on 2006-08-23
Perhaps someone needs to be told to update the tutorials though? Not good if they're incorrect/incomplete. Should this be raised on launchpad?

---

### Post by psyncho on 2006-08-24
> **ciscosurfer said:**
> There are many ways to do this, just bear that in mind...and mine is only one way:
If the file doesn't exist yet, simply create it and add 'pwcheck_method: saslauthd' to the file```
sudo touch /etc/postfix/sasl/smtpd.conf
sudo su
echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf
```

Thanks.  I was going to do this but thought the missing file might be indicative of other things being wrong...thus just creating the file might not be a "fix".  I'll give it a shot.

John

---

### Post by ciscosurfer on 2006-08-25
> **JeevesBond said:**
> Perhaps someone needs to be told to update the tutorials though? Not good if they're incorrect/incomplete. Should this be raised on launchpad?
An update to the tutorials may be in order, however, launchpad is for bugs, and I don't believe this problem is a bug so-to-speak.  Then again, I suppose it could be.  But anyone, please, correct me if I'm wrong. :D

---

### Post by psyncho on 2006-08-25
just creating the file seemed to do the trick.  I guess someone just left out of the tutorial "create this file"..or maybe something wierd happend with my install?  anyway, sasldauth seems to be working.  I only don't seem to be having local delivery but I'm porting over from exim4 using maildirs, so perhaps I have to tweak postfix for that to work.  Remote delivery from local host, and testing using telnet gave the impression that the tls auth was working.

Thanks!  Let me know if I should give you props somehow through this forum thing.

John

---

### Post by ciscosurfer on 2006-08-25
"Props" are always appreciated and respected, but are not necessary.  I'm glad (almost) everything is working for you. ;)

---

