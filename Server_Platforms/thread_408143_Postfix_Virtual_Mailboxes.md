---
title: "Postfix Virtual Mailboxes"
date: 2007-04-13
forum: Server Platforms
---

### Post by kooseefoo on 2007-04-13
Okay, I have a postfix server that's set up with the configuration in the ubuntu server guide. And it works great.

Now, I want to set it up to have virtual mailboxes. The howto below claims to cover it, but I can't seem to pick out the parts I need - it is a very different setup than I have.

[http://phparchitecture.com/howto_show.php?id=2](http://phparchitecture.com/howto_show.php?id=2)

The other issue is that I don't really have a sandbox installation, so I wanna make sure I know what I'm doing before I mess with anything.

It seems that I need to do 3 things here: set up my mysql database, configure the smtp_sasl_password_maps parameter so my virtual users will be allowed to send emails, and configure the virtual delivery agent with a whole mess of parameters found in the virtual manpage ([http://www.die.net/doc/linux/man/man8/virtual.8.html)](http://www.die.net/doc/linux/man/man8/virtual.8.html)).

Am I on the right track? Does anybody have any suggestions for me?


Thanks a ton!
Chris

---

### Post by kooseefoo on 2007-04-14
Well, I moved on to try to just go ahead and do this whole thing.

I have the virtual mailboxes working and receiving mail according to a mysql database.
All I had to do was add these entries to my main.cf file:

```
#Accept mail from this domain
virtual_mailbox_domains = mail.--removed--.com
#Added $virtual_mailbox_maps to make sure it doesn't immediately reject mail to
a virtual mailbox
local_recipient_maps = $alias_maps $virtual_mailbox_maps unix:passwd.byname
#Added to the beginning of stuff taken out of the virtual_mailbox_maps database
#Keeps a rogue mysql entry from dumping crap all over the system
virtual_mailbox_base = /home/vmail
#The location of the virtual maps - email-maildir, email-gid, email-uid
#GID is always 106, UID is always 101 (vmail:vmail)
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-maps.cf
virtual_gid_maps = mysql:/etc/postfix/mysql-virtual-gid.cf
virtual_uid_maps = mysql:/etc/postfix/mysql-virtual-uid.cf
```

And, the annotations are more notes to myself of what exactly I did.

The part I am trying to work on now is getting postfix to allow my virtual users to send emails. I can't find anything in the man pages that would help me out at all.

The only other idea I have is that I need to do something with SASL. A few howtos seem to mention doing something with /etc/postfix/sasl/smtpd.conf, but I can't find any documentation so I at least have an idea of what I'm doing...
Here's the aforementioned smtpd.conf file:

```
pwcheck_method: saslauthd
mech_list: plain login
```

Any help would be appreciated

Chris

---

