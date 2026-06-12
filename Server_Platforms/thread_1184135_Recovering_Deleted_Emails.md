---
title: "Recovering Deleted Emails"
date: 2009-06-10
forum: Server Platforms
---

### Post by faustcoder on 2009-06-10
I've been planning on creating a imap server to replace current pop3 server but I need more info on two things.

1) Deleted Emails
My users constantly delete "important" emails and we have to retrieve them. Since we use pop3 we open the catch all email account, "archive", in a mail client and search for the message. We then forward it to the user. This method is **very** difficult to manage, especially when you have over 3 years of emails in the account. (Don't ask it was like that when I got here.)

So how would you recover deleted or stripped (emails stripped by content filter) emails with a imap server?

2) Archiving
Our current method involves dumping the *archive* user's PST file then splitting it, (size has exceeded 5 gigs), then burning it to disk or storing to backup server.

This is a extremely unreliable and dangerous backup method that I want to get away from ASAP. So how would one go about backing up, archiving, and restoring a imap server?

3) Security
One of our clients is requesting for us to use TLS and I don't know much about configuring it with Ubuntu.

I want to use Ubuntu's dovecot-postfix for the mail server but want to know how to properly perform the items mentioned above. Yes I have googled and read multiple docs but they aren't very detailed. Since this will be in production these items are a must. Any help/advice is appreciated.

---

### Post by HermanAB on 2009-06-10
Howdy,

I think that you should use a mail server that has a proper database back-end, for example Citadel.  It uses Oracle BerkeleyDB and can handle up to 256 terabytes of mail.  

Managing and backing it up is very easy.  

It supports every mail protocol you can shake a stick at and it is very easy to install - takes about 20 minutes using their Easy Install script.

---

### Post by faustcoder on 2009-06-11
Yeah I really enjoy Citadel but I don't remember seeing much info on retrieving deleted emails. However I do remember reading a few faqs on doing backups w/ Citadel. Guess I'll ask #citadel more on this thanks.

---

