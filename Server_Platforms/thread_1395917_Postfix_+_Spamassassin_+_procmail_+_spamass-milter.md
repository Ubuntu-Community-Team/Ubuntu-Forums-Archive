---
title: "Postfix + Spamassassin + procmail + spamass-milter"
date: 2010-02-01
forum: Server Platforms
---

### Post by sntwest on 2010-02-01
Sorry if this is the wrong place.
I have Postfix and Spamassassin setup on server 9.10. The mail is working perfectly. Spamassassin is correctly marking messages as spam. My problem is with the milter and procmail.
On past servers I was able to reject spam based on score via the spamass-milter. For whatever reason I can not get it to work. I have also tried with procmail, again, it does not work. Here are the relative lines in their respective config files:

postfix main.cf:
```
# Spamass-milter
milter_default_action = accept
# smtpd_milters = unix:/var/run/spamass.sock
non_smtpd_milters = unix:/var/run/spamass.soc

# mailbox_command = mailbox_command = procmail -a "$EXTENSION"
# mailbox_command = /usr/bin/procmail -f- -a "$USER"
mailbox_command = /usr/bin/procmail -a "$EXTENSION" DEFAULT=$HOME/Maildir/ MAILDIR=$HOME/Maildir
```The commented lines are lines that I have tried before.

procmail:
```
:0
* ^X-Spam-Level: \*\*\*\*\*\*
/dev/null
```spamass-milter:
```
# Reject emails with spamassassin scores > 15.
OPTIONS="-r 6"

```I even have EXTRA_FLAGS="-r 6" in /etc/init.d/spamass-milter

None of this is working and I can not figure it out. I am sure I am missing something simple.

Thanks

---

