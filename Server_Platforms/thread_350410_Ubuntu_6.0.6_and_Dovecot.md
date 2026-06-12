---
title: "Ubuntu 6.0.6 and Dovecot"
date: 2007-01-31
forum: Server Platforms
---

### Post by apastuszak on 2007-01-31
I am getting ready to install a new home server for email.  In the past I had been using Fedora Core 3, but have decided to switch to a Linux distribution that is free, but provides long term support, I am strongly leaning towards Ubuntu Dapper.

I looked at the 6.0.6 LTS release and saw that it come with Dovecot 1.0-beta 3.  6.10 comes with Dovecot 1.0-RC2.  RC19 is the current version available at dovecot.org.

I guess my question is, when Dovecot finally goes 1.0 Gold, will this be made available for the 6.0.6 LTS release by Ubuntu/Canonical, or is 6.0.6 LTS stuck at beta 3 for the next 5 years?

Andy

---

### Post by MJN on 2007-01-31
Whilst not a direct answer to your question, is there any reason you'd want the new(er) version?

Mathew

---

### Post by Cosmic_Crusader on 2007-01-31
I for one would like the later version of Dovecot as it contains numerous bug fixes and improvements.

I'm still getting errors like:
Maildir /home/cosmic/Maildir sync: UID inserted in the middle of mailbox (2463 > 2461, file = msg.ZwVQD:2,)

These errors actually seem to screw up my email!

(I'm using Postfix and procmail as well)

---

### Post by MJN on 2007-02-01
That doesn't sound like a bug, but rather Dovecot saying the mailboxes have errors.
 
Are you getting these constantly? You haven't recently upgraded have you? You say it's actually screwing up your e-mails - in what way?
 
I would expect only to see that kind of error the once (per mailbox/folder) as it should reparse the messages. If you want to force this try removing all your index files as per my post at [http://www.ubuntuforums.org/showpost.php?p=1812974&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1812974&postcount=2).
 
Mathew

---

### Post by apastuszak on 2007-02-01
Well, the issue I am having is the index file getting corrupt and needing to delete the index file in order to see my inbox.  This was supposedly fixed in RC14 or so, so I would hope that the gold release will get released and is fully supported by Canonical.

Andy

---

### Post by MJN on 2007-02-01
You mentioned you're using Procmail[1] - are you using MH instead of maildir to deliver new mail? (your .procmailrc would be useful)
 
Do you ever get the errors in any folder other than Inbox? (if not, then this strongly leans towards procmail)
 
Any log entries for those representing other folders?
 
Mathew
 
P.S. If you're certain it's a Dovecot issue you could always install the latest Debian backport.
 
[1] Oops, no you didn't - that was somebody else! Anyway, are you using procmail? If so, MH or Maildir? If not, what MTA and what mail format?

---

### Post by apastuszak on 2007-02-01
Nope. not using procmail.  Just using postfix and Maildir.  It's a known issue that has been discussed on their mailing list.

Is there an IMAP server other than dovecot that someone could recommend that can use Maildir?

---

### Post by MJN on 2007-02-01
Courier comes highly recommended (indeed I think it *only* supports maildir).

Mathew

---

### Post by Cosmic_Crusader on 2007-02-01
For me, I am using procmail with Maildir, and getting frequent errors in my INBOX as well as some other folders.  It seems to happen most when a new email arrives, but could be associated with an EXPUNGE command.

It screws up my email connection with Evolution so that it never sees new email unless I disconnect and reconnect.  With Squirrelmail I get a disconnect error quite frequently.

Occaisionally I have noticed it currupts an email, with the heads from one email but the body from another (and recently I'm sure it corrupted the content as well).

It's disconcerting.

I have the backports repository but no sign of a newer version of Dovecot anywhere?

---

### Post by MJN on 2007-02-01
It's in the Debian backports:

[http://backports.org/debian/pool/main/d/dovecot/](http://backports.org/debian/pool/main/d/dovecot/)

Mathew

---

