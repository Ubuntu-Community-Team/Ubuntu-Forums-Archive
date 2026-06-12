---
title: "Fetchmail/exim IMAP folders delivery issue"
date: 2012-07-20
forum: Server Platforms
---

### Post by melvinlopez06 on 2012-07-20
Hi everyone,
Im having an issue with fetchmail (I believe).

I've set up a local mail server using fetchmail, exim and courier-imap/pop on ubuntu server 11.10

I'm on testing phase
I've configured an account in fetchmail (using /etc/fetchmailrc) to get all imap folders.

```
poll domain
user ‘usuario2@domain’ there with password ‘password’ is ‘usuario’ here options sslproto ‘tsl1’ fetchall folder INBOX, INBOX.Sent, INBOX.Drafts, INBOX.CustomFolder
```

Fetchmail downloads all mail, I believe that exim does the delivery I don't know, the problem: all folders (sent, drafts, customs) are delivered to the inbox, not to the respective sent, drafts, custom folders on maildir user account.

To configre exim I just ran the debconf, the configuration type is smarthost receiving by smtp or fetchmail and maildir format on user's home.

The local account has the imap folders, owner and permissions (usuario:mail 700), the tree folders is:
~/Maildir/cur , new, tmp
~/Maildir/.Sent
~/Maildir/.Drafts
~/Maildir/Customs

Any idea??
How can I handle the mail delivery to these folders?

---

