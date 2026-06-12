---
title: "Help, My Webhost Doesn't Know Linux"
date: 2007-03-14
forum: Server Platforms
---

### Post by lunaz on 2007-03-14
i'm trying to set up my domain email to work with evolution but i can't get it working. i got it going w/ outlook on the windows comp but soon it won't be a windows comp anymore...  i emailed my host (parcom.net) about it, and they said they don't know the client & will look into it. that was last week...

---

### Post by rennen01 on 2007-03-15
Could you post a screenshot of the configuration page in Evolution please?

---

### Post by lunaz on 2007-03-15
here's my settings in outlook:
[http://www.lunaz.com/pics/emailpics/image1.jpg](http://www.lunaz.com/pics/emailpics/image1.jpg)
[http://www.lunaz.com/pics/emailpics/image2.jpg](http://www.lunaz.com/pics/emailpics/image2.jpg)
[http://www.lunaz.com/pics/emailpics/image3.jpg](http://www.lunaz.com/pics/emailpics/image3.jpg)

here's my settings for evolution:
[http://www.lunaz.com/pics/emailpics/screenshot-1.png](http://www.lunaz.com/pics/emailpics/screenshot-1.png)
[http://www.lunaz.com/pics/emailpics/screenshot-2.png](http://www.lunaz.com/pics/emailpics/screenshot-2.png)
[http://www.lunaz.com/pics/emailpics/screenshot-3.png](http://www.lunaz.com/pics/emailpics/screenshot-3.png)

---

### Post by Mr. C. on 2007-03-15
Pop before SMTP is not what you were using on Outlook.  You are using SMTP AUTH, which is what you will also need to configure on Evolution.

You likely also need a Secure connection.

MrC

---

### Post by lunaz on 2007-03-16
hm, i tried using tls & ssl connections, then all the auth types listed. there wasn't one for smtp-auth. i get this error: also my smtp server was smtp.lunaz.com, not mail.lunaz.com... server requires auth is checked also.

Error while performing operation.
SMTP server mail.lunaz.com does not support requested authentication type PLAIN.

---

### Post by Mr. C. on 2007-03-16
SMTP AUTH is SMTP authentication using something called SASL.  Your ISP appears to provide this (the "this server uses authentication" checkbox is the clue).  The PLAIN method means plain text passwords are passed.  Outlook uses a method called LOGIN.

Either way, it is likely your ISP requires an encrypted connection.   Please show me your Advanced tab on Outlook's Internet Email settings so we can verify.

Evolution does not support the LOGIN method - that is basically Microsoft-only.  Evolution should support MD5 and/or CRAM.

MrC

---

### Post by lunaz on 2007-03-16
[http://www.lunaz.com/pics/emailpics/image4.jpg](http://www.lunaz.com/pics/emailpics/image4.jpg)

---

### Post by Mr. C. on 2007-03-16
Your ISP appears to support smtp connections on port 25 only.  They do not support the submission port 587 nor the old SSL smtps port 465.

They do support: AUTH LOGIN and CRAM-MD5.  The "AUTH=LOGIN" line is strictly for broken Microsoft clients Outlook and Outlook Express:

250-reed.myinternetwebhost.com says hello
250-SIZE 0
250-8BITMIME
250-DSN
250-ETRN
250-AUTH LOGIN CRAM-MD5
250-AUTH=LOGIN
250 EXPN

Your ISP does not  appear to support TLS (no STARTTLS announced).

Evolution allows SMTP connections via: PLAIN, LOGIN, CRAM-MD5, DIGEST-MD5, KERBEROS_V4, NTLM.

So you will have to use CRAM-MD5 over port 25 for authentication.

Your ISP supports both POP and IMAP.

Evolution supports IMAP with: PLAIN, CRAM-MD5, DIGEST-MD5, KERBEROS_V4

This should give you enough information to configure your Evolution.

MrC

---

### Post by lunaz on 2007-03-17
using mail.lunaz.com:25 or smtp.lunaz.com:25 with cram-mds still gives that error, turning off the server requires auth doesn't make a difference, i always get this:

Error while performing operation.

SMTP server mail.lunaz.com does not support requested authentication type PLAIN.

i don't understand what all those 250- lines mean.

---

### Post by Mr. C. on 2007-03-17
I assume you mean CRAM-MD**5** (five, not s).

The hosts smtp.lunaz.com: and smtp.lunaz.com resolve to the same place, so you probably can use them interchangeably.

The 250 lines are server response codes from the server, and it is announcing to your client its capabilities. The mail server provides:
```

250-SIZE 0                 Unlimitzed sized emails
250-8BITMIME               8 bit MIME support
250-DSN                    Delay Status Notifications
250-ETRN                   Extended Turn
250-AUTH LOGIN CRAM-MD5    SASL authentication using either the LOGIN or CRAM-MD5 method
250-AUTH=LOGIN             Workaround SASL authentication w/LOGIN for MS clients
250 EXPN                   Server will alias expand
```

The error message you are receiving is indicating that your client is still trying to use the PLAIN method.  Your server requires CRAM-MD5.

Verify after you set the authentication type in Evolution, the you see something like: auth=CRAM-MD5@mail.lunaz.com/  in the file: ~/.gconf/apps/evolution/mail/%gconf.xml .

MrC

---

### Post by lunaz on 2007-03-17
ty for your patience lol :)

i'm probly missing something totally obvious....

i set both the sending & receiving mail auth types to CRAM-MD5, set both smtp & pop servers to mail.lunaz.com. for smtp i've tried mail.lunaz.com & mail.lunaz.com:25 & i still get that error.

i opened that file u mentioned with nano & replaced auth=LOGIN with auth=CRAM-MD5 & tried that, still the same error. then replaced 'smtp' with 'mail', and even added :25 to the end of ..auth=cram-md5@mail.lunaz.com line, still i get the same error :(

---

### Post by tturrisi on 2007-03-17
use mail.x.x for pop
use smtp.x.x for smtp

try setting evolution smtp as:
uncheck "server requires authentication".
(most isp smtp servers don't require any authentication)

if no joy, what available smtp auth types are available in evolution?
(this is the section where you have pop before smtp in screenshot)
select an auth type that the isp smtp server supports.

---

### Post by Mr. C. on 2007-03-17
Work on either sending or receiving, not both at the same time.

Your SMTP and IMAP server support different mechanisms.  Regardless, you appear to be using POP, not IMAP.

Work on receiving via POP first;  and then when that works, on sending.

Your POP server should be a simple POP (port 110) connection, with no encryption or authentication.

We can verify that CRAM-MD5 works for your username and password.  Contact me via PM and we'll discuss it.

MrC

---

### Post by Mr. C. on 2007-03-17
> **tturrisi said:**
> use mail.x.x for pop
use smtp.x.x for smtp

try setting evolution smtp as:
uncheck "server requires authentication".
(most isp smtp servers don't require any authentication)

if no joy, what available smtp auth types are available in evolution?
(this is the section where you have pop before smtp in screenshot)
select an auth type that the isp smtp server supports.

Both smtp.lunaz.com and mail.lunaz.com resolve to the same host.

$ host mail.lunaz.com
mail.lunaz.com has address 69.90.236.29
$ host smtp.lunaz.com
smtp.lunaz.com has address 69.90.236.29

His SMTP server provides *only* LOGIN and AUTH CRAM-MD5.

You are incorrect about most ISPs not requiring authentication - almost all do.

Evolution supports all the methods I posted earlier.

MrC

---

