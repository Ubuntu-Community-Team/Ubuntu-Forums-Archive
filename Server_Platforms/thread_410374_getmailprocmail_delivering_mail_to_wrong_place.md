---
title: "getmail/procmail delivering mail to wrong place"
date: 2007-04-15
forum: Server Platforms
---

### Post by computx on 2007-04-15
I am trying to set up getmail and procmail to retrieve mail from a pop server and sort out spam to a spam folder.
Using a howto I found on the web I have the following setup.
`/.getmail/getmailrc-foo contains this

[I]
[options]
verbose = 0
delete = True

[retriever]
type = SimplePOP3SSLRetriever
server = pop.foo.com
port=995
username = [email]user@foo.com[/email]
password = passwd

#[destination]
#type = Maildir
#path = ~/.maildir/

[destination]
type = MDA_external
path = /usr/bin/procmail
unixform = True
[/I]
I have a .procmailrc that looks like this

[I]PMDIR=$HOME/Procmail
VERBOSE=no
MAILDIR=$HOME/.maildir/
INCLUDERC=$PMDIR/rc.lists

[/I]

under ~/Procmail I have a rclists that looks like this

[I]:0
* ^Subject_[Bulk]
IN-Spam/
[/I]

Mail is getting delivered to /var/mail/user
instead of the users `/.maildir

Why is procmail or getmail putting the mail in the wrong place?

---

### Post by BoneKracker on 2007-04-16
Because you have no delivery recipe it is delivering to the default location (the system mail spool).

You have a recipe telling it what to do with things that say "Bulk Mail", but you don't have a recipe telling it what to do with the rest.  So it falls through and gets delivered to the default location.

Read the man page for procmailrc.

---

### Post by computx on 2007-04-16
I wasn't aware I needed a recipe for all else. I will look over the man page and try to put a recipe together.
Thanks

---

### Post by BoneKracker on 2007-04-17
What makes procmail so useful is that it is so flexible.  That's also what makes it a pain in the butt.  (Well, that plus the documentation is mostly scattered throughout etherspace in the form of people's mailing lists, blogs, email messages and such.

I've been using procmail on a different linux distribution (and don't know much to begin with), but I'll try to summarize a few key points that should be helpful.  You should confirm what I tell you here, but this should save you time and make it easier to find specifically what you need.

If a delivery recipe is not specified, then the mail gets delivered to the default address.

You can set the $DEFAULT variable in /etc/procmailrc explicitly to make the default delivery destination whatever you want instead of the default it was set up with at compile time.  However, that leaves you with no "failsafe" if a user has monkeyed around with their ~/.procmailrc file or mailbox(es).  Traditionally, $DEFAULT is a central location used as a "spool" for incoming messages (e.g., /var/mail or /var/spool/mail).  Sometimes therein are found a single mbox file per user(with all messages concatenated together), and sometimes a directory (maildir) per user (with a file per message).  

If a delivery recipe is not specified, then the mail gets delivered to the default address.

Procmail can be run by users/scripts, or it can be called by the system's MTA to handle a local delivery.  When it's called by MTA (with command "procmail -d")  it takes on the identity of the user to whom the message is going, it ignores the /etc/procmailrc, and it looks for ~/.procmailrc.  

It does what ~/.procmailrc says to do. Your ~/.procmailrc says (by way of included "lists") to do something with spam.  So, if it sees the indicated header, it will deliver that message to the indicated location.  "If" is the operative word there.  If not, it continues processing the ~/.procmailrc file, doing what it says.

If it completes processing the ~/.procmailrc file (and any included "lists") and it has not yet executed a "delivery" recipe, then it falls back to the /etc/procmailrc file and does what IT says.  If it completes processing the /etc/procmailrc file (and any included rc files) and it has not yet executed a "delivery" recipe, then it will deliver to $DEFAULT.  For example, for user "smokingfrog" it will deliver to /var/mail/smokingfrog.  The user can then retrieve that mail with a MUA (mail client) or by executing a MDA on their own.

So you have a choice:  set $DEFAULT to be user home mailboxes, or create a delivery recipe that specifies this.  That recipe can reside in each user's ~/.procmailrc (or included files) or in the system-wide /etc/procmailrc (or included files).  Following the style of configuration you appear to be using, this would be an additional included rc-file specifying delivery, and in the main ~/.procmailrc, iit should be listed after all other such included rc files:

```
INCLUDERC=$PMDIR/rc.lists
INCLUDERC=$PMDIR/rc.delivery
```

...or something like that.  And in that rc.delivery file, you would place your delivery recipe, which might be as simple as:

```
:0
IN/
```

Now a bit about mailbox format.  The mbox format is traditional, but the maildir format is used by several of the modern MTAs.  Which is best for you depends on message content and volume (and may have already been decided for the ubuntu people if you don't know how to compile from source).  In procmail-speak, "maildir" means "the root of the mail delivery structure for each user".  Don't get confused between that usage of the term "maildir" and the "maildir" format (which emerged later in qmail and courier).  This is especially confusing because procmail can deliver to mbox, maildir, and even mh style mailboxes.  So when you say "$MAILDIR" in procmailrc, this has nothing to do with what format mailbox you want.  You indicate the style of mailbox in the format of the delivery recipe (or default location as the case may be):

inbox           indicates a Berkeley-style "mbox" mailbox (which is a file)
inbox/         indicates a qmail-style "maildir" mailbox (which is a directory)
inbox/.        indicates a Mail Handler -style "mh" mailbox (which is a directory)

So, your spam recipe correctly indicates a maildir-style mailbox for spam.  You just need to create a similar one for the inbox (and whatever else).  You can put that recipe in the ~/.procmailrc, or in an included rc file (the one you already have, or a new one).

I hope that helps.    :D

---

### Post by BoneKracker on 2007-04-17
Oh, and I should also mention this:

Getmail itself can deliver mail.  You can use procmail to just act as a mail filter (and not do the delivery) by calling it with "procmail -m".

But you might as well have it do the delivery since you've already piped the messages to it.

And another point:

If you're not using mh (like if you are a claws-mail user like me), and you are processing some very large mail messages (with fat attachments for example), then you might want to consider using maildrop instead of procmail.

Maildrop takes more resources to just run, but it takes less resources to process large mail files.  (Procmail reads the whole message into RAM, whereas -- if configured properly -- maildrop reads it into a temporary file.)

---

### Post by computx on 2007-04-17
Thank you for the detailed information. Lots of good info here.
I am using a maildir setup with postfix/getmail/procmail/dovecot/squirrelmail
I actually had all this setup on a gentoo server and am just moving over to ubuntu for ease of maintenance. I hadn't used procmail before but since my isp filters my email and stamps Spam with the [Bulk] subject I thought some procmail filtering would be a nice addition.
I discovered a recipe of 
:0
new 
worked for me but [dovecot info]("http://wiki.dovecot.org/MailboxFormat/Maildir") I found says that is not a proper way to do it due to inodes being reused.
This is just for 3 peoples email so I think changing $DEFAULT may be the way I will go.

---

### Post by computx on 2007-04-17
FWIW to others.
After mulling this over I added the following to the end of ~/.procmailrc 
[I]:0
/home/user/.maildir/[/I]
and all is working ok.

---

### Post by BoneKracker on 2007-04-17
Good job.

Just one one more thing I remembered to help you refine this.

Typically, the delivery address specified in a recipe is relative to a variable called $MAILDIR (not to be confused with the fact that you are using maildir format).

To make a delivery address relative to $MAILDIR, just leave off the leading "/".  If your delivery address includes a leading "/", you are telling procmail that it is an absolute delivery address (i.e., it is relative to the linux root and not $MAILDIR).

You are using an absolute delivery address (which is fine).  If you're also setting $MAILDIR somewhere, it's probably reduntant, though, unless it's getting used in another recipe.  Either way is fine, but to make maintenance easier in the future, you should do it consistently one way.

By default, most distributions assume $MAILDIR to be $HOME (procmail doesn't do handle the "~" shell expansion).  You can set $MAILDIR in a variables section near the top of your ~/.procmailrc, or you can export it like any other system variable.

Good luck.  Glad it worked out.

---

### Post by andrew.46 on 2007-07-05
Hi,

 Thanks for clearing that point up for me:

> **BoneKracker said:**
> 
  In procmail-speak, "maildir" means "the root of the mail delivery structure for each user".  Don't get confused between that usage of the term "maildir" and the "maildir" format (which emerged later in qmail and courier).  This is especially confusing because procmail can deliver to mbox, maildir, and even mh style mailboxes.  So when you say "$MAILDIR" in procmailrc, this has nothing to do with what format mailbox you want. 

 I have been puzzling for ages why I am directing procmail to deliver its recipes to:

```
MAILDIR=$HOME/Mail
```

 when I was actually using the mbox format :-) This must be confusing more people than just me I suspect.

                   Andrew

---

