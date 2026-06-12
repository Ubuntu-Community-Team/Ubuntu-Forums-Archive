---
title: "View Dovecot Mailbox from Command Line"
date: 2016-09-09
forum: Server Platforms
---

### Post by terencewklau on 2016-09-09
Hi,

I've got Dovecot running on Ubuntu Server 16.04.  I'll looking for a way to view the mailboxes from the command line like the application mutt.

Mutt however requires postfix to be installed and I don't want that.  I've got postfix installed on a separate server.

I understand I can use telnet to view the mailbox but it doesn't list the email's details like mutt does (from, subject, timestamp etc).

I only need to view the mailbox and don't need to send email from it.  Its just for troubleshooting purposes while I'm on the dovecot server.

Any suggestions would be much appreciated.  Thanks.

---

### Post by thomaschr on 2016-09-09
mutt has a '-f'-Flag which should do the trick.
Of course, it needs to be one single file with all mails in it (mbox-Format).
I don't know if mutt can read maildir-Format as well.

Thomas

---

### Post by bob_jones2 on 2016-09-09
I can use telnet

:confused::confused::confused::confused::confused::confused::confused::confused:

Please tell me you meant to write SSH.... please !  
NOBODY.  AND I MEAN NOBODY. SHOULD BE USING TELNET IN 2016 !

---

### Post by terencewklau on 2016-09-11
mutt does read maildir.  I've used it previously when I had dovecot and postfix on the same server.

But now that its separated, I don't really want to install mutt on the dovecot server as it wants to install postfix as well.

Telnet is just to read the mailbox while on the dovecot server.

---

### Post by terencewklau on 2016-09-20
For those looking for an MUA without a full blown MTA, I installed the lightweight ssmtp which then filled the dependency requirement for mutt.

Cheers.

---

### Post by SeijiSensei on 2016-09-20
My favorite command-line mail client is alpine, the GNU rewrite of pine from the University of Washington.  If you are on the server where the mail is stored, you can reference folders with their file names like /home/user/mail/Sent.  Otherwise you can use IMAP with the syntax "{server_name}folder", e.g., "{my_server}INBOX".  

If you use the filesystem method, alpine will usually find your inbox.  Otherwise you can try "/var/mail/username".

---

### Post by SeijiSensei on 2016-09-20
My favorite command-line mail client is alpine, the GNU rewrite of pine from the University of Washington.  If you are on the server where the mail is stored, you can reference folders with their file names like /home/user/mail/Sent.  Otherwise you can use IMAP with the syntax "{server_name}folder", e.g., "{my_server}INBOX".  

If you use the filesystem method, alpine will usually find your inbox.  Otherwise you can try "/var/mail/username".

> **bob_jones2 said:**
> ***_NOBODY.  AND I MEAN NOBODY. SHOULD BE USING TELNET IN 2016 !_***

There are lots of valid reasons to use telnet when you are connecting to TCP based services like SMTP or IMAP.  For instance, if you want to test whether you can send mail to a remote system you can use "telnet server_name 25" to connect to the server's SMTP port.  Using "telnet server_name 143" connects to IMAP.  You'll see the server display a banner if the connection succeeds. You can also type the same plain-text commands that these servers expect.  Here's a sample SMTP session:
```

$ [color=blue]telnet some_mail_server 25[/color]
Trying xxx.xxx.xxx.xxx
Connected to some_mail_server
Escape character is '^]'.
220 some_mail_server ESMTP Sendmail 8.13.8/8.13.8; Tue, 20 Sep 2016 21:40:49 -0400
[color=blue]helo localhost[/color]
250-some_mail_server Hello localhost [127.0.0.1], pleased to meet you
[color=blue]mail from: me@example.com[/color]
250 2.1.0 me@example.com... Sender ok
[color=blue]rcpt to: someone@ubuntuforums.org[/color]
250 2.1.5 someone@ubuntuforums.org... Recipient ok
[color=blue]data[/color]
354 Enter mail, end with "." on a line by itself
[color=blue]Here is my message.
.
[/color]
250 2.0.0 unique_message_id Message accepted for delivery

```
Items in blue are typed by you.  This dialogue is with a machine running sendmail.  With Postfix or exim or some other SMTP server, you'll see slightly different responses.

---

