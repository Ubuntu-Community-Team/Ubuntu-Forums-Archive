---
title: "Shared Mailbox / Folders at Dovecot"
date: 2011-02-14
forum: Server Platforms
---

### Post by Do$ on 2011-02-14
Dear Sirs.
I'm new user at ubuntu.
I have made some little mail server (postvix+dovecot+fetchmail) at ubuntu. The mail serve is using system accounts.
Now I want to creat Shared mailbox. I have found some information, but I can't understand it correctly. Can U view the below information and correct me.

I have several accounts: Oleg (my account - /home/oleg/Maildir/); pankov (/home/pankov/Maildir); cv ( /home/cv/Maildir/). I want to share the mailbox of CV user:
I have add the follwoing information to dovecot.conf:

# You need to create also a private namespace:
namespace private {
  separator = /
  prefix = 
  #location defaults to mail_location.
  inbox = yes
}

namespace shared {
  separator = /
  prefix = shared/%%u/
  location = maildir:%%h/Maildir:INDEX=/home/cv/Maildir/%%u
  subscriptions = no
  list = children
}

protocol imap {
  mail_plugins = acl imap_acl
}
protocol lda {
  mail_plugins = acl
}
plugin {
  acl = vfile
}

But it doesn't work. Can U write, whta's the problem and what I have to correct.
Thanks in advance.

---

### Post by elico on 2011-02-14
you need to build a standard settings and on the filesystem to link the mail dir directories from one user to the other using the
ln -s 
command.

---

