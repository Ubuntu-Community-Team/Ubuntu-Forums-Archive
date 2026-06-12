---
title: "Need to remove duplicate emails from maildir"
date: 2008-03-21
forum: Server Platforms
---

### Post by ZippZapp on 2008-03-21
Hello!

keywords: pst-files, maildir, duplicate, email, reformail, AMD64, Ubuntu server 7.10

After many years of problems with overfilled and crached pst-files from outlook, I have many 1-2GB pst-files which many of them contains more or less much of the same emails.

How do I merge these and remove all the redundant emails?
Total volume is approx. 30GB of pst-files and I will guess after removing all redundant emails, there would be 4-6GB left.

I have set up a courier-imap mailserver on my ubuntu server and I'm planning to open each of the pst-files (one-by-one)  in outlook, dragging its contents to the ubuntu-courier-imap-maildir.

I have tested this with two of my pst-files, and so far all seems OK.

But how do I remove all the duplicates from the Maildir?

I have only found one suggested solution to this, here:
[http://kremvax.net/howto/mail-duplicates.html](http://kremvax.net/howto/mail-duplicates.html)

It involves the use of "reformail", which is not installed on my Ubuntu Server 7.10. 

Questions:
- How do I get / install "reformail"?
- Do you have any better suggestions for merging and removing all the redundant email?


----------:confused:

---

### Post by rb-cohen on 2008-03-23
Hi Zippzapp,

I had a similar request and stumbled across this post. I'd seen the suggestion over at [http://kremvax.net/howto/mail-duplicates.html](http://kremvax.net/howto/mail-duplicates.html) and installed reformail but it didn't work for me.

Reformail was both really slow and incorrect in its reports of messages to keep/delete so I decided to create my own solution the only way I knew how, PHP. If you can install PHP on your machine/already have it installed I've put the code up here: [http://www.blograndom.com/blog/deleting-duplicate-mdir-emails-using-php/](http://www.blograndom.com/blog/deleting-duplicate-mdir-emails-using-php/)

If you still want to try reformail it is part of a courier package, I think maildrop.

---

### Post by ZippZapp on 2008-03-23
Thank you, rb-cohen!

I had to try it out at once.

I installed php5-cli and tried to run your script, but i got into parsing errors.
Unfortunately, I don't understand much of the code, but it seemed to me that it did not like the single-quotes.
By replacing llr the single-quotes ( ' ) with double-quotes  ( " ) it parsed without syntax-errors untill the final echo-section, but then it complained about some unexpected ">" which I did not understand why.

Any clue?

Best regards
ZippZapp.

---

### Post by Mr. C. on 2008-03-25
You might find it more reliable to do this from within Outlook, and then export what remains as you see fit.

See: [http://www.slipstick.com/addins/contacts_dups.asp](http://www.slipstick.com/addins/contacts_dups.asp)

for possible duplicate remover solutions.

---

