---
title: "Email Pickup by Daemon"
date: 2010-11-15
forum: Server Platforms
---

### Post by Xabi87 on 2010-11-15
Hello,

I'm currently experimenting with Ubuntu Server and I'm in need of some direction regarding the setup of an email server.

I have experience creating web apps, and server-wise (relating to this) I've created a perl script which runs as a daemon, picks up uploaded files to a folder and organises them in some way, updating a database at various points.

Can anyone please tell me if the following is possible...

I'd like to setup an email server, so when an attachment on an email is sent to [email]process@mydomain.com[/email] a modification of the above Perl daemon can grab the attachment and process it, as opposed to the file upload.

I've never setup an email server on Linux before. Once it's set up, are the emails delivered to a certain folder like I'm imagining?

Can anyone point me in the right direction regarding setting up an email server with the above capability?

(I'm open to using any version of Ubuntu Server, I can switch easily.)

Thank you very much in advance, and more details required please let me know.

Xabi

---

### Post by SeijiSensei on 2010-11-15
Read up on procmail ("man procmail"; "man procmailrc"; "man procmailex").  It enables you to do many useful things with an email message upon arrival.  In your case, you could have it read the headers of each message, and, if it sees the appropriate MIME header indicating the presence of the attachment, it can pipe it to your script.

procmail is a very useful tool that's seems to have fallen into obscurity in the past few years.

> **Xabi87 said:**
> I've never setup an email server on Linux before. Once it's set up, are the emails delivered to a certain folder like I'm imagining?

Each recipient needs a user account on the server (but not a shell); inbound mail is delivered to /var/spool/mail/username.  By default messages are stored in "mbox" format which is a single file where each message is delimited by a blank line.  You can also use the "maildir" format where each message is a separate file in a common directory.  In your case it probably doesn't matter which format you choose, since procmail will process the message before it's delivered.

---

### Post by Xabi87 on 2010-11-15
Sounds perfect, thanks very much :)

---

