---
title: "Postfix, Dovecot, password problem"
date: 2018-07-07
forum: Server Platforms
---

### Post by JKyleOKC on 2018-07-07
I'm moving my production activity from Xubuntu 14.04 LTS to 16.04, now that 18.04 has been released -- and I'm having a problem getting my intra-LAN email set up. Both boxes on the LAN have Postfix installed (to provide sendmail capability), and the production box also has Dovecot to provide a POP3 mail user agent to feed Thunderbird. The problem is that when I attempt to get all new messages from Dovecot via Thunderbird, I'm only getting a "bad password" error. When Tbird attempts to enter a new password, the error persists.

Before I installed Dovecot, messages from the other box wound up in /var/mail/jk and I could read them using mutt in a terminal window. Now, they are ending up in ~/Maildir/new but not getting out from there.

And I'm finding the help files to be rather silent about such matters. Tbird itself seems to have problems with creating a new mail account from a very private server, though I finally did get it to acknowledge a copy of its 14.04 server list. Dovecot has nothing that I've been able to find, yet, and I've trusted the mail-stack-delivery package to have configured Postfix properly when I installed that to provide the linkage to Dovecot.

Suggestions? There's not a huge need to have this working immediately, but it galls me to have parts of the system non-functional and be unable to fix it!

---

### Post by SeijiSensei on 2018-07-07
What authentication method is dovecot using? Have you tried deleting the account in TBird and letting it recreate it? TBird will try to find a compatible method.

You can jack up debugging in dovecot so it logs the entire transaction, too.

---

### Post by JKyleOKC on 2018-07-07
Seems to be working now; Dovecot was wanting my user-login password, like sudo did before I changed sudoers, rather than any password referred to in the man pages for doveadm and dovecot! I'll mark this as solved, but it might be good to mention in the help files or the wiki here that this needs doing. And I've yet to discover how to jack up the debugging for dovecot to see the entire transaction, which might have helped a bit. It was just a blind guess that let me discover the magic word!

---

### Post by SeijiSensei on 2018-07-07
I use CentOS. My dovecot configuration is split between a main /etc/dovecot/dovecot.conf, and a set of additional configuration files in /etc/dovecot/conf.d/. The 10-logging.conf in that directory holds the key item for me:
```
auth_debug_passwords = yes
```
There are other more verbose options available as well.

Don't know if Ubuntu follows the same arrangement.

---

