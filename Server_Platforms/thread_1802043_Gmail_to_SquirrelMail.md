---
title: "Gmail to SquirrelMail"
date: 2011-07-11
forum: Server Platforms
---

### Post by ubudog on 2011-07-11
Hi everyone.  I'm working on a mail server, and I want to take all my old Gmail messages and import them into my SquirrelMail account on my server.  Is this possible?  Are there any guides?  Thanks!

---

### Post by ruffEdgz on 2011-07-11
I could see you [forwarding](http://mail.google.com/support/bin/answer.py?answer=10957) any new messages to your SquirrelMail account right now just to have them but if you want any of the old emails to go into your SquirrelMail account, you will have to do something like this (in this order):
[list]
[*] Download/Install Thunderbird
[*] [POP emails from Gmail](http://mail.google.com/support/bin/answer.py?answer=12103) to Thunderbird
[*] IMAP your SquirrelMail account to Thunderbird
[*] Drag and drop the POP'ed emails into the IMAP account
[*] Delete both POP and IMAP accounts from Thunderbird
[/list]
I went through the SquirrelMail documentation myself and didn't find anything that would be able to IMAP/POP information from one account to another (like Google does). 

You might be interested in this document I found (but haven't tried) when grabbing emails from Google to your local computer: [http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html)

Cheers!

---

### Post by volkswagner on 2011-07-11
I have used [these scripts]("http://www.athensfbc.com/imap_tools/") in the past.  Most valuable!

If you enable IMAP in your gmail account you may be able to use the [imapcopy.py]("http://www.athensfbc.com/imap_tools/files/imapcopy.pl") script.

I'm not sure how to do it with Squirrelmail, but I have used them with Postfix and Citadel in the past.  It should get you going!

---

### Post by ubudog on 2011-07-11
Thanks!  I'll have a look at them.

---

