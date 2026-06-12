---
title: "New Mail Server"
date: 2009-09-06
forum: Server Platforms
---

### Post by master_script_maker on 2009-09-06
Hi everyone. I just recently installed Ubuntu Server 9.04 with the Lamp and mail options, and I'm new to this, so I'd like to install a gui on the server. But now to my main question, how could I set up the mail server to get it up and running so I can send and receive emails.

---

### Post by TheFuturian on 2009-09-07
The Ubuntu Serverguide gives a good place to start:-

[https://help.ubuntu.com/9.04/serverguide/C/email-services.html]("https://help.ubuntu.com/9.04/serverguide/C/email-services.html")

---

### Post by hessiess on 2009-09-07
GUI, use webmin.

---

### Post by master_script_maker on 2009-09-07
Okay, I installed postfix and tested using telnet. How do I send a test msg to another email?

---

### Post by TheFuturian on 2009-09-08
Easiest way is to use a client like Outlook/Thunderbird then tail the mail log:-

```
tail -f -n 100 /var/log/mail.log
```

If you don't want the hassle of setting up a client I think there's a 'Simple SMTP Mailer' tool as part of the NetTools suite:-

[http://users.telenet.be/ahmadi/nettools.htm]("http://users.telenet.be/ahmadi/nettools.htm")

You can also throw commands directly at the telnet session:-

```
EHLO domain.suffix
MAIL FROM:john@suffix.com
RCPT TO:dave@suffix.local
DATA
Hello Dave
.
QUIT
```

---

### Post by HermanAB on 2009-09-08
$ mail -s Whatever [email]joe@server.com[/email]
.



---
NAME

     mail, mailx, Mail - send and receive mail

SYNOPSIS

     mail [-eIinv] [-a header] [-b bcc-addr] [-c cc-addr] [-s subject] to-addr
	  [...] [-- sendmail-options [...]]
     mail [-eIiNnv] -f [name]
     mail [-eIiNnv] [-u user]

---

### Post by master_script_maker on 2009-09-08
> **HermanAB said:**
> $ mail -s Whatever [email]joe@server.com[/email]
.



---
NAME

     mail, mailx, Mail - send and receive mail

SYNOPSIS

     mail [-eIinv] [-a header] [-b bcc-addr] [-c cc-addr] [-s subject] to-addr
	  [...] [-- sendmail-options [...]]
     mail [-eIiNnv] -f [name]
     mail [-eIiNnv] [-u user]

I tried doing this, but the email address I sent it to didn't receive it. I'm sorry but I very new to a mail server. What I have done is install Ubuntu 9.04 with LAMP and mail server options, installed postfix and then installed dovecot-postfix.

---

### Post by HermanAB on 2009-09-08
Did you remember to type the little DOT on the next line?

A period on a new line signals the end of the mail command.

---

### Post by master_script_maker on 2009-09-08
yes

---

### Post by TheFuturian on 2009-09-09
Can you initiate a telnet session to the SMTP port (25) from another machine? Do the commands I supplied work?

---

### Post by master_script_maker on 2009-09-10
yes

---

### Post by TheFuturian on 2009-09-23
Do you get any kind of "bounce-back" message returned to the sender's mailbox? Can you print the output of this command after attempting a send?

```
tail -n 50 /var/log/mail.log
```

---

