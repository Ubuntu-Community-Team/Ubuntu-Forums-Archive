---
title: "Fetchmail configuration"
date: 2009-10-31
forum: Server Platforms
---

### Post by ambre on 2009-10-31
Hi guys,

I am trying to use fetchmail to collect family emails from a number of pop3 servers.

If the remote login is of the form user "joe" password "xyz", everything works fine.

However, if the remote login is of the form "joe@domain" password "xyz" fetchmail doesn't like it and returns "Server CommonName mismatch: localhost != domain".

Can anyone explain to me what is happening and how I can overcome this.

Regards,
Ambre

---

### Post by MechaMechanism on 2009-10-31
Did you try replacing the @ with underscore (_).  In my fetchmailrc file my login is user_domain.tld instead of user@domain.tld.

---

### Post by ambre on 2009-10-31
Changing @ to _ produces an authorisation failure.

---

### Post by MechaMechanism on 2009-10-31
> **ambre said:**
> Changing @ to _ produces an authorisation failure.
Try -v to get verbose output.  Also is the fetchmail running as daemon or per account.  Is the mail going to /var/mail/ and is it 1 mbox for all email accounts or separate mbox per account.  Another thing is that fetchmail comes with a gui tool as well but I have never used it so I don't know anything about it.  I think the best bet at this point is verbose output.

Check the Ubuntu help page at [https://help.ubuntu.com/community/GmailPostfixFetchmail#Configuring%20Fetchmail](https://help.ubuntu.com/community/GmailPostfixFetchmail#Configuring%20Fetchmail)
Also be sure to check the fetchmail link in my sig.
And $man fetchmail

---

### Post by ambre on 2009-10-31
Well, it appears that the messages that are being logged are just warnings.

I have had a friend send me emails at all of our addresses and they have all been received!

Still not sure what the log is trying to tell me, but at least there does not seem to be any problem with the emails getting through.

Thanks for the responses, I should have done more testing before posting.

Regards,
Ambre

---

### Post by MechaMechanism on 2009-10-31
> **ambre said:**
> Well, it appears that the messages that are being logged are just warnings.

I have had a friend send me emails at all of our addresses and they have all been received!

Still not sure what the log is trying to tell me, but at least there does not seem to be any problem with the emails getting through.

Thanks for the responses, I should have done more testing before posting.

Regards,
Ambre
That is great that it worked out for you.

---

