---
title: "mail server questions"
date: 2005-10-02
forum: Server Platforms
---

### Post by TravisNewman on 2005-10-02
OK here's the thing.

I have a spare machine that I want to turn into a multi-purpose server. I have file and print taken care of, now I'm looking to use it as a mail server as well.

I have googled this and haven't found anything that covers what I'm about to ask, as far as I can tell.

I want to set up the server to download my mail and her mail. Here's how the accounts are set up:

Me: 2 gmail accounts (this is tricky with fetchmail/postfix from what I hear), one pop3, one pop, one imap, soon another pop
Katie: 2 gmail accounts, one pop

I'd like to set up fetchmail/postfix on the server, so when we pop it in to any mail client (I use mutt, evolution, and thunderbird depending on which machine I'm on, she just uses thunderbird) with our separate user/pass it will give us the mail from all accounts, in the same folder structure. I guess the easiest way to do this would be to set up an IMAP server on it, no? I'd also like spamassassin and clamav to check it before it's sent.

Any help is appreciated. Most of you know I'm mostly proficient at Linux, I've just never done any mail server stuff at all before.

---

### Post by basketcase on 2005-10-05
[http://www.ubuntuforums.org/showthread.php?t=40047&highlight=spamassassin](http://www.ubuntuforums.org/showthread.php?t=40047&highlight=spamassassin)

Does that help?  Seems like a great resource.

---

### Post by TravisNewman on 2005-10-05
amazing, thank you. This will probably get me what I want.

---

