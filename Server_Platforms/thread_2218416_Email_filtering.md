---
title: "Email filtering"
date: 2014-04-20
forum: Server Platforms
---

### Post by sandyd on 2014-04-20
I currently have a hosting account at a serverhost that uses roundcube. I defined some filters to place emails in certain folders - but apparently they are only run when I open roundcube, as I can see my account unfiltered if I open from IMAP or SMTP.

Is there an external mail client or something that I can run on a separate server to filter the email into the correct folders?

---

### Post by CharlesA on 2014-04-20
I use Thunderbird to do my filtering for me.

Not sure if you'd want to do a push/pull or something to the current mail server or just connect a client to it and pull the mail from there via imap.

---

### Post by sandyd on 2014-04-20
> **CharlesA said:**
> I use Thunderbird to do my filtering for me.

Not sure if you'd want to do a push/pull or something to the current mail server or just connect a client to it and pull the mail from there via imap.

I have too many random clients that I connect using - and I dont keep my computer on 24/7

---

### Post by SeijiSensei on 2014-04-20
Install **procmail** on the server.  Then you can place "recipes" into a .procmailrc file that will sort your mail automatically upon delivery.  For instance, let's suppose you want anything with a subject that includes the word "Frozen" put in the "frozen" folder.  In ~/.procmailrc, you'd create this recipe:
```

:0
* ^Subject:.*frozen
frozen

```
Comparisons use extended regular expressions and are case-insensitive by default.  Read "[man procmailrc"]("http://linux.die.net/man/5/procmailrc") and particularly "[man procmailex]("http://http://linux.die.net/man/5/procmailex")" for details.

Sorting into folders is only one of many things you can do with procmail.  For instance, I wrote a script to handle non-delivery notices for some listservers I host:
```

# filter nondelivery notices
:0
* ^To:.*owner-*
* ^Subject:.*deliver|^Subject:.*failure|^Subject:.*returned|^Subject:.*ndn
| /home/scanner/ndn-handler

```
That pipes message to the non-delivery handler that are sent to "owner-something" and include one of the trigger keywords in the Subject line.  You can also have procmail examine the entire body of a message as well.

Procmail has sometimes been called the "Swiss army knife" for mail administrators with good reason.  It's installed by default on RedHat-flavored machines, but not on Ubuntu.

---

