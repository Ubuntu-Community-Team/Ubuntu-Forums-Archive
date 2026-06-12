---
title: "how do you configure mailx to use maildir"
date: 2007-08-17
forum: Server Platforms
---

### Post by glennric on 2007-08-17
I have set up Exim4 configured to use Maildir. I can send emails to a user using the commands 'mail' or 'sendmail', and the email shows up in the Maildir. However if I try to read mail with mailx it says there is no mail. If I configure Exim4 to use a mail file instead I can read the mail with mailx. I would prefer to use Maildir. How can I set up mailx so that I can do this? I am guessing I need to add something to the file /etc/mail.rc, but nothing I have tried seems to work. I read the man file for mailx, and that had no information about maildir versus mbox.

---

### Post by BoneKracker on 2007-08-18
I don't think you can.  However, there are numerous ways to work around this.  Here are a couple that come to mind:

1.  Use a local MDA to deliver the mail from mbox to maildir.  For example, you could use procmail.  Perhaps best in your case is to use the mda functionality that I assume exists in Exim (or its tool set - I assume it provides a local MDA).

2.  Read or deliver the mbox from your client.  If you are using mailx to process only system mail that you or a small number of people need to receive, it may be adequate to simply handle it with your MUA (client).  Any unix mail client can at least "import" mbox.  The good ones can fully operate on all three of the widely-used formats (mbox, maildir, mh) and offer automation (expressive rules processing and/or triggers for shell scripts) that you can use to essentially delivery the mail to your maildir when the client runs and during periodic checks.

3.  Don't use mailx.  In many cases, the applications/scripts that "depend" on mailx (/bin/mail) can actually use any sendmail (whatever you've got linked at /usr/sbin/sendmail, /usr/lib/sendmail, etc.) if you configure them to do so.

4.  Use Heirloom Mailx (used to be called 'nail'), which is a drop-in replacement for mailx (/bin/mail) but offers much more functionality (without checking, I bet it offers a variety of ways to get around this, one of which probably includes direct maildir delivery).

5. Write your own script.  Here are two features of mailx that might be useful.  When you send an email with mailx, the addressee (the address to which you are sending the mail) can be any shell command.  Mailx also has a command that lets you pipe existing messages from the mailbox (all or some by type -- like new, old, unread, etc.) to any shell command.

---

### Post by MJN on 2007-08-19
Looking at [http://lists.debian.org/debian-user/2007/02/msg00010.html](http://lists.debian.org/debian-user/2007/02/msg00010.html) it sounds like the version of 'mail' found in the 'mailutils' package will quite happilly read maildir mailboxes.

Note that mailx will have to be removed given mailutils provides its own mail program - it should still allow dependent programs to run with it.

Mathew

---

### Post by BoneKracker on 2007-08-19
I wasn't aware of that.  I've seen several email and forum threads in various places claiming that mailx "supports maildir", but I have seen no documentation to that effect.  (Except for heirloom mailx.).  And Debian doesn't use the GNU version of mailx by default? That also is surprising.

Are you sure these references are not just confusion caused by the fact that mailx has an environment variable named MAILDIR?  I've seen that go around before.

It's true that mailx can "read" any mail file (any text file for that matter) and can also "save" email to any location.  So, that might mean to some that it "supports" maildir.  But that's not the same as being able to use a maildir-style mailbox as a user's mailbox (which is what I think of when someone says they want to use it with maildir).  

The fundamental difference is that with maildir (and mh), a "mailbox" is a directory (containing individual files for each message), whereas with mbox, a "mailbox" is a single file (spool) of all a user's current messages.

---

### Post by glennric on 2007-08-27
I have tried mailutils and still can't read the mail in the Maildir.  Any idea how to configure it to do so?

---

### Post by MJN on 2007-08-27
I'm afraid not - I've never used it.

Mathew

---

### Post by BoneKracker on 2007-08-30
Like I said.

You can read an individual file with 'mail -f <filename>', but that's not what you really want.

For alternatives, see above.

---

