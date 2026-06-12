---
title: "Dovecot won't show me my mail."
date: 2010-01-15
forum: Server Platforms
---

### Post by artheus on 2010-01-15
Hi!

I've got the problem that Dovecot won't show me my mail!

I've set up my mail_location to **maildir:~/Maildir/**, and set up a namespace

```
namespace private {
    separator = .
    prefix = INBOX.
    inbox = no
    hidden = no
}
```

And I've made a /etc/procmailrc

```
DROPPRIVS=YES
ORGMAIL=${HOME}/Maildir/
DEFAULT=${ORGMAIL}
```

And I've checked that it delivers the mail to the correct location.

I know I've made a post kinda like this before, but this time there's a different problem. This time I know it delivers the mail to the correct folder, and everything like that.
I've tried mail_location as **mbox:~/Maildir/** just incase.

I am able to copy mails from another account to the account on my server. But I've got no clue of where dovecot stores them. Not in **/var/mail** I've checked..

Can anyone help me, please?

BTW. This happened after I re-installed with a 9.10 Ubuntu Server disc.

//Artheus

---

### Post by artheus on 2010-01-15
Well.. I found out that if I remove the namespace

```
namespace private {
    separator = .
    prefix = INBOX.
    inbox = no
    hidden = no
}
```

I get to see the mail.

But then I don't get the folders inside my Inbox, like

```

 |Inbox
 |
 |--Folder
 |
 |---Trash
 |
 |---Drafts


```

which I want.


Am I forgetting something??

//Artheus

---

