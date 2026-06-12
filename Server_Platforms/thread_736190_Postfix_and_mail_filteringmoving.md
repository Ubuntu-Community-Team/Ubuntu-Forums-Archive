---
title: "Postfix and mail filtering/moving"
date: 2008-03-26
forum: Server Platforms
---

### Post by michellez on 2008-03-26
I feel like I'm going mad/being extremely stupid here!

All I have is a Postfix set up with Spamassasin. I just want to set it up so email marked as spam gets moved to a spam folder with in that users maildir. Also I would like it to be possible to do things like filter them in to folders depending on the address they were sent to, or the subject of the email.

Exim was driving me up the wall so I thought I would give Postfix a try. You can do this in Exim in a .forward file in the users home dir. Simple. Is there not a similar simple answer with Postfix?

Thanks,
Shell

---

### Post by michellez on 2008-03-29
I hate doing this, but has no one really got any suggestions except to go back to Exim? Seems a bit extreme for something that should be 'expected'.

Thanks,
Shell

---

### Post by MJN on 2008-03-29
There a million-and-one ways to do this, here's mine...

Use Procmail to actually manage the local delivery of mail i.e. get Postfix to pass mail to Procmail which can then manage it accordingly.

So, firstly install procmail (**sudo apt-get install procmail**) then configure it with some default site-wide settings in **/etc/procmailrc**:

```
DROPPRIVS=YES
ORGMAIL=$HOME/Maildir/
DEFAULT=$ORGMAIL
```Alter $HOME/Maildir/ to suit where your mailboxes/folders are located (mine are obviously in ~/Maildir/)

Next we need to add the filtering required - there are hundreds of procmail configuration guides on the web so I'll just tell you what I use and you can compare/dissect it against the guides and adjust to suit:

```
:0:
* ^X-Spam-FLAG: YES
$HOME/Maildir/.Spam/
``` (This will apply to all users. If you want specific per-user rules then they can have there own rules in **~/.procmailrc**)

Finally we need to tell Postfix to use Procmail for delivery by adding the following to **/etc/postfix/main.cf**:

```
mailbox_command = procmail -a "$EXTENSION"
```Restart Postfix and you should be good to go.

I hope this helps, if not just shout.

Mathew

---

### Post by michellez on 2008-03-30
Brilliant. That worked - thank you!

I did find something like this but it wouldn't work. Followed you word for word and it did :-)

I assume the code is identical for procmailrc whether it is a global or user file?

---

### Post by MJN on 2008-03-30
Yup, just the same.

Glad to hear you're up and running.

Mathew

---

### Post by hyper_ch on 2008-03-31
procmail is excellent :)

---

### Post by michellez on 2008-04-08
Currently got a good one I'm working out.. here goes if any one has any ideas!

I have a user rules file in /home/user/.procmailrc

One entry is:

:0:
* ^(From|Cc|To|Received).*me@mydomain.com
! yadayada@someotherdomain

When it sends this though is sends as user@localhost. SMTP is then set to go via my ISPs SMTP server. This then refuses it though as it is using @localhost !

If I forward email say from postfix this goes out fine using the original address.

I'm doing this because I am trying not to forward my spam.

---

### Post by michellez on 2008-04-08
Bingo! This is how as I'm sure it will help some one else one day

At the top section of the file I have added:

SENDMAILFLAGS=-rsomeone@domain.com

That is correct, -rNOSPACEemailaddress.

Now works fine, still shows as the original sender and not the above :-)

After playing recently I now have the below. This moves spam in to a Spam folder, then makes a local copy of the email before sending a copy to an external address. (I have my reasons!)

```
DROPPRIVS=YES
ORGMAIL=$HOME/Maildir/
DEFAULT=$ORGMAIL

# This is for logging/debugging
PMDIR=$HOME/.procmail
LOGFILE=$PMDIR/log

MAILDIR=$HOME/Maildir

SENDMAILFLAGS=-remail@domain.com

0:
* ^X-Spam-FLAG: YES
.Spam/

:0c:
* ^(From|Cc|To|Received).*me@mydomain.com
.me/
:0:
! otheraddress@otherdomain.com

```

I'm thinking I can replace the top section with the following, will removing ORGMAIL break anything though? Is it just an internally used variable or does something else out side this script use it?

```
DROPPRIVS=YES
MAILDIR=$HOME/Maildir
DEFAULT=$MAILDIR

# This is for logging/debugging
PMDIR=$HOME/.procmail
LOGFILE=$PMDIR/log

# Set 'from' address it uses to forward messages, gets round it going from @localhost and getting rejected by a SMTP smarthost
SENDMAILFLAGS=-remail@domain.com
```

---

### Post by MJN on 2008-04-09
> **michellez said:**
> I'm thinking I can replace the top section with the following, will removing ORGMAIL break anything though? Is it just an internally used variable or does something else out side this script use it?

It is used to specify the mailbox to be used. Why do you want to remove it? MAILDIR specifies the working directory and whilst this configuration works as it stands if you ever start changing the working directory in scripts you could land up in hot water. Your lack of trailing slashes may also break the MAILDIR format intent (as opposed to using MBOX).

Stick with what you had, and what you know works. Remember the old adage *If it ain't broke don't fix it!*

Mathew

---

