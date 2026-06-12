---
title: "Mailserver problems"
date: 2007-03-09
forum: Server Platforms
---

### Post by FitzChivalry on 2007-03-09
Heya, I've been having immense problems with setting up a mailserver. I followed the instructions @ [Urban Puddle](http://www.urbanpuddle.com/articles/2006/12/20/setup-a-postfix-mail-server-on-ubuntu-edgy-eft) which not really worked.

I can check mail with POP3, IMAP won't work because of inbox errors, squirrelmail returns these errors:[COLOR=#cc0000][/COLOR]

**Left Frame**
**[COLOR=#cc0000]ERROR: Connection dropped by IMAP server.[/COLOR]**[COLOR=#cc0000]
Query: SUBSCRIBE "INBOX.Sent"

[/COLOR]**Right Frame**
**[COLOR=#cc0000]ERROR: Could not complete request.[/COLOR]**[COLOR=#cc0000]
Query: SELECT "INBOX"
Reason Given: Unable to open this mailbox.[/COLOR]

SMTP won't send via PLAIN because the method isn't supported (even though it's in the mech_list in /etc/pam.d/smtpd). LOGIN returns an authentication error.

I have my passwords encrypted in the mysql database used by postfix & courier, all the directives needed are set for encryption, etc.

I'm really stuck on how to resolve this one. Any help would be greatly appreciated!

Many Thanks!

---

### Post by elst on 2007-03-10
I haven't used Courier, so these are just general suggestions:

1) Try IMAP without SSL first, just to make things simpler
2) Use Thunderbird for testing before you move on to Squirrelmail, as using TB as an IMAP client cuts out a layer (the Squirrelmail config)
3) Find the logs, then do try one login attempt, and see what messages are added

If you can find Postfix or Courier error messages in your logs, but don't understand them, then either try copying them into Google, or posting them here.

---

### Post by Mr. C. on 2007-03-10
Frankly, you're trying to do too much at once.

The problem I have with all these "tutorials" available on the net, is that when the slightest thing goes wrong, users are stuck with a mess.

First, get your basic SMTP mail working (postfix).  Once that works correctly, then go on to Courier-IMAP, and then to Squirrelmail.  Its simply not possible to debug all of these at the same time.

MrC

---

