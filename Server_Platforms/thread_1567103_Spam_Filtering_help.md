---
title: "Spam Filtering help"
date: 2010-09-03
forum: Server Platforms
---

### Post by rostjd on 2010-09-03
I have set up a spam filter based on the documentation listed via the following link. 

[https://help.ubuntu.com/8.04/serverguide/C/mail-filtering.html](https://help.ubuntu.com/8.04/serverguide/C/mail-filtering.html)

IT is working very well but I am having difficulty whitelisting email from a particular user/domain. 

I have added the white list to the /etc/amavis/conf.d/40-policy_banks but the emails are still being scanned and marked as spam from this user. 

Any help would be appreciated

---

### Post by Vishal Agarwal on 2010-09-03
As per my opinion you require to create the whitelist for spamassassin. Because amavis is the antiviruse interface which works with the help of installed anti virus  and spamassassin is the spam filter.

---

### Post by rostjd on 2010-09-03
The configuration from the documentation state to add the configuration form AMavis. I have tried to add the entries to spamassassin as well without any result.  The messages are still being flagged as spam.

---

### Post by lisati on 2010-09-03
Sometimes looking at the headers of the incoming email provides clues as to why the email is being flagged as spam. Because this isn't an option if amavis etc. decides to drop the email, I've configured it on my server to send a notification to me at an email address that I've set up specifically for that purpose, and a copy of the "spam" to another of my email addresses. It took me a little bit of googling to initially figure out how to do this. What I did was to have some lines in /etc/amavis/conf.d/21-ubuntu_defaults as follows:
```

# destination for notifications 
$virus_admin = "spamreport\@$mydomain";
$spam_admin = "spamreport\@$mydomain";
$newvirus_admin = "spamreport\@$mydomain";
$banned_admin = "spamreport\@$mydomain";
$bad_header_admin = "spamreport\@$mydomain";

# sender info for notifications
$mailfrom_notify_admin = "virusalert\@$mydomain";
$mailfrom_notify_recip = "virusalert\@$mydomain";
$mailfrom_notify_spamadmin = "spam.police\@$mydomain";

# desination for quarantined emails
$virus_quarantine_to = "spams\@$mydomain";
$banned_quarantine_to = "spams\@$mydomain";
$bad_header_quarantine_to = "spams\@$mydomain";
$spam_quarantine_to = "spams\$mydomain";

```
Some of the lines might already exist and just need editing, others will need to be added. 

What this does is direct suspect messages to an email user "spams" on my system and a notification/explanation to another user "spamreport" on my system.

---

