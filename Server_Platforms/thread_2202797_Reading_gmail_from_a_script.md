---
title: "Reading gmail from a script"
date: 2014-01-31
forum: Server Platforms
---

### Post by bytesoup on 2014-01-31
Hi All,

I want to be able to read mail from a gmail account using a simple shell script. I'm currently using ssmtp to send emails from my server for logwatch for example, but as far as I can tell ssmtp cannot receive emails. I dont want to build a mail server, I only want to download emails into a simple text file or whatever is simplest. From what I've seen I need to use postfix? I've seen some talk about mutt too but im not sure if you cant invoke it from a script?

What I'm trying to acheive is a script I can run from a cron job where if it sees an email with a given subject, it will perform some actions on the server

Does anyone have some suggestions?

Thanks!

---

### Post by TheFu on 2014-01-31
Use **fetchmail** then script reading the mbox files as you like.
Fetchmail will pull ALL email local, not a specific subject.

Sending email uses SMTP protocols.
Reading email uses either POP3 or IMAP protocols.
If you want to receive emails, you must run an MTA with SMTP daemon running 24/7/265 - postfix, qmail, sendmail and others. There are some other things like DNS records and ports that the ISP must open too.

mutt and alpine are CLI versions of mail readers. Once the email is local, in a known mailbox format, all sorts of things are possible.  Most of the time, people with what I think you want run a mail server and use procmail to kickoff scripts.

gmail is a little weird, so I don't know if any of this will work. I know it works with normal email systems that support all the normal protocols.

---

### Post by SeijiSensei on 2014-01-31
> **bytesoup said:**
> What I'm trying to acheive is a script I can run from a cron job where if it sees an email with a given subject, it will perform some actions on the server

Another vote for fetchmail with the addition of [procmail]("http://www.procmail.org/") as the local delivery agent in Postfix.  Procmail lets you write "[recipes]("http://linux.die.net/man/5/procmailex")" to handle messages based on their characteristics.  For instance,
```

:0
* ^From:.*me@example.com
* ^Subject:.*reboot
! "/sbin/shutdown -r now"

```
This recipe would only work if the recipient is the root user.  In that case, a message from "me@example.com" with "reboot" in the subject line would trigger a restart.

The e-mail recipient's permissions will matter greatly if you try using a system like this to "perform some actions on the server."

---

### Post by bytesoup on 2014-02-04
Thanks guys, I didn't have postfix installed so I had to install that too. Fetchmail worked ok but without postfix you'll see errors because it seems to need to connect locally to postfix to deliver the mail. I did manage to get all the mail delivered into one file at /var/spool/mail/<user> but it is in one big file.

Im a bit foggy on all the components required for handling mail does someone have a good high-level guide? It seems there's a lot of info on the web but a lot of it goes into more detail than I want just for a brief overview.

Also for procmail, does that mean I can parse out this single large email file with this?

---

### Post by TheFu on 2014-02-04
procmail only works as email arrives.

Your question about email is huge without knowing it. Can you be more specific?  Or, I can recommend the O'Reilly book on postfix.  Any beginning system admin book will have diagrams of how email works - at least how SMTP works. There are a few different O'Reilly books for that too.

---

### Post by tgalati4 on 2014-02-04
Perhaps describe the use case in a little more detail.  If you are sending an email to a computer to activate scripts on a server, then what prevents you from using *ssh* to activate the script directly from your phone?  If the server is generating a condition that requires action, are you using *rsyslog* to capture the log message to another machine?  If that is the case, then a cron job on the computer capturing the rsyslog can parse the file and perform the script actions directly.  No email is needed.

---

### Post by andrew.46 on 2014-02-06
> **bytesoup said:**
> Im a bit foggy on all the components required for handling mail does someone have a good high-level guide? It seems there's a lot of info on the web but a lot of it goes into more detail than I want just for a brief overview.?

This old Ubuntu wiki page shows one way to do this:

[https://help.ubuntu.com/community/MuttAndGmail](https://help.ubuntu.com/community/MuttAndGmail)

---

