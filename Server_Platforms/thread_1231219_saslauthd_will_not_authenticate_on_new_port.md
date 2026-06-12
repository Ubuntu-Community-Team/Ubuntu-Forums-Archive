---
title: "saslauthd will not authenticate on new port"
date: 2009-08-04
forum: Server Platforms
---

### Post by FawnOfFeist on 2009-08-04
I recently added port 587 to my postfix server's master.cf

# ================================================== ========================
smtp inet n - - - - smtpd
587 inet n - n - - smtpd


I can connect on this port now, but when I do and try to send a message, I get the following errors:


Aug  4 09:08:23 AlbPostfix02 postfix/smtpd[15023]: connect from static-64-246-146-231.albyny.csvoip.net[64.246.146.231]
Aug  4 09:08:23 AlbPostfix02 postfix/smtpd[15023]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Aug  4 09:08:23 AlbPostfix02 postfix/smtpd[15023]: warning: static-64-246-146-231.albyny.csvoip.net[64.246.146.231]: SASL LOGIN authentication failed: generic failure
Aug  4 09:08:23 AlbPostfix02 postfix/smtpd[15023]: lost connection after AUTH from static-64-246-146-231.albyny.csvoip.net[64.246.146.231]


Port 25 authenticates without an issue.  What am I missing for port 587 to work as well?

---

### Post by FawnOfFeist on 2009-08-04
Is there some other info I could provide that would make this easier to help with?

We are really stuck as Verizon sucks and has blocked port 25 for a few of our customers making them sending mail impossible.

---

### Post by FawnOfFeist on 2009-08-06
Anyone that has any info it would be greatly appreciated.

Still having this error when using port 587, but not 25.

---

### Post by FawnOfFeist on 2009-08-07
In case anyone else has this issue, the fix was to get rid of the 587 line I had added and uncomment this:

submission inet n       -       n       -       -       smtpd

I wasn't aware submission was 587

---

