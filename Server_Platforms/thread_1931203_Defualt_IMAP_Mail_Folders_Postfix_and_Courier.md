---
title: "Defualt IMAP Mail Folders Postfix and Courier"
date: 2012-02-25
forum: Server Platforms
---

### Post by nat45928 on 2012-02-25
Hi,
 
I recently set up a mail server on Ubuntu by following the basic  tutorial section on flurdy.com/docs/postfix/ But when I logged into  SquirrelMail I noticed that all the folders for Sent, Drafts and Trash  were subfolders of Inbox. With my old email hoster (GoDaddy) I had a few  folders that were made and permanently in the same level as inbox. Is  there a way to have postfix create these folders when the mailbox for  the virtual mail account is created for use on an IMAP connection?
 
Basically im looking for this:
 
 
[LIST]
[*]INBOX
[*]SENT
[*]DRAFTS
[*]TRASH
[/LIST]

instead of:
 
 
[LIST]
[*]INBOX
[LIST]
[*]SENT
[*]DRAFTS
[*]TRASH
[/LIST]
 
[/LIST]

 
 
Thanks,
Nat[URL="http://www.linuxforums.org/forum/#"]
[/URL]

---

### Post by nat45928 on 2012-02-27
Bump, anyone?

---

### Post by tpinet on 2012-06-14
I am also curious if you were able to figure this out. I am having the same issue.

---

