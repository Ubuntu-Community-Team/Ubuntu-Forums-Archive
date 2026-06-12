---
title: "Fetchmail + procmail"
date: 2006-04-14
forum: Server Platforms
---

### Post by christian8287 on 2006-04-14
Hi!

I want to install an email server. Therefore I have created 3 mailboxes with cyradm. I can send emails via my server, but procmail doesn't deliver the emails to the right mailbox. fetchmail works right. All mails go to the /var/spool/mail/fetchmail - file. 

Here is my ~/.fetchmailrc:
```
poll mailbox.aon.at protocol pop3 user "xxxxxxx" there with password "xxxx" mda "/usr/bin/procmail ~/.procmailrc" 

```

Here is ~/.procmailrc
```
# Macros
DELIVERMAIL="/usr/sbin/cyrdeliver"
:0 w
*^TO.*christian\.kloimuellner@aon\.at
| $DELIVERMAIL -e -a christian -m user.christianaon
```

Do I need a user called christanaon? I think it must be right to have a user called christian and a mailbox christianaon. User christian has more than one email. If I need a user christianaon I need for every email address christian has an local account? Naturally a user christianaon was created using saslpasswd2.

Do you know, what I made false? Can someone post his/her procmail, fetchmail file?

If you need more information, like main.cf, imapd.conf, cyrus.conf, master.cf, please contact me.

Thank you!

regards,
Christian.

---

