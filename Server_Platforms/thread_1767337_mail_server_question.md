---
title: "mail server question"
date: 2011-05-25
forum: Server Platforms
---

### Post by moonpup on 2011-05-25
I have setup a mail server using 10.04.2 LTS. I have installed and configured postfix, dovecot, heirloom-mailx and created a self signed certificate following the directions from the server guide. I'm only using pop3s and listening on port 995. Everything works perfectly for my domain except for one thing.

Why is it that when I'm ssh'd into the server and from the command line I type mail, it reports I have no new mail even though there are messages in my Maildir/new directory?

---

### Post by Lars Noodén on 2011-05-25
> **moonpup said:**
> ...I'm only using pop3s ...

(You might look at IMAPS instead. IMAP gives you more options than POP.)

So you can read your mail with 'mail' but it is not reporting that you have new messages?

---

### Post by moonpup on 2011-05-25
Hi Lars, for this situation POP3S is appropriate. Anyway, I can't read mail from the command line. When I type mail it says no new mail. I know I have new mail because I can see it in the Maildir/new directory. I can't figure out what is preventing the mail command from seeing it. If I connect over pop3s using my email client or mobile device I get new mail just fine.

---

### Post by Lars Noodén on 2011-05-26
That's because the client 'mail' does not support POP or IMAP.  If you use another program, like Alpine, you should be able to read your POP mail.  However, I'd still recommend IMAP even if you want to download all your mail before reading it.

---

### Post by moonpup on 2011-05-26
Hi Lars, thanks for the answer. So the bottom line is 'mail' which is provided by either heirloom-mailx or mailutils packages is not pop3 or imap aware? If your only running an MTA like postifx and it delivers mail to the default location, the mail command will work. I'm surprised mail won't work in this situation. I thought I had something configured wrong...

---

