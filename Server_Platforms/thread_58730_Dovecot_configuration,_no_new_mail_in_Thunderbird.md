---
title: "Dovecot configuration, no new mail in Thunderbird"
date: 2005-08-21
forum: Server Platforms
---

### Post by kblood on 2005-08-21
Hello,

I have Dovecot more or less successfully installed and running. My main user has all the mail in ~/.maildir, as recommended in the official Ubuntu wiki (for very good reasons, I think).

So I have Dovecot configured like this:

default_mail_env = maildir:%h/.maildir:INBOX=/var/mail/%n

According to the documentation of Dovecot, that should put all the mail in the home/.maildir folder, but get the Inbox from the /var/mail/username file.
I have checked, and certainly that file exists, and the contents look right. I even tried sending an email from an outside web account, and that email is now in that file. So Postfix is doing its job fine, it seems.

However, when I open Thunderbird, I can log in to the Dovecot IMAP server, and I see an empty Inbox. I tried sending an email, and it got sent fine, to that external web account. And it's copied just fine to the Sent folder in Dovecot. I also can see it in the .maildir folder.

So... why is Dovecot not picking up the mails from the /var/mail/username file?

Any suggestions?

---

### Post by kblood on 2005-08-21
Now, one more test, and it was quite surprising:

I tried copying a couple of emails to the Inbox with Thunderbird, and I saw the emails getting added to the /var/mail/username file!
And they were showing in Thunderbird as well!

So it seems that Dovecot knows about the file, and it's using it.

I changed my configuration in dovecot.conf to this:

default_mail_env = maildir:%h/.maildir:INBOX=mbox:/var/mail/%n:INDEX=%h/.indexes

but no change, I still can't get the emails that are in the Inbox file to show in Thunderbird.

Any advice would be really appreciated.

---

