---
title: "SquirrelMail on Ubuntu/Postfix doesn't accept my password"
date: 2007-02-01
forum: Server Platforms
---

### Post by qwert231 on 2007-02-01
I've gone through the procedure here:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

And have SquirrelMail coming up on my server. I can even telnet into postfix and do mail. But when I try to log in via SquirrelMail it fails. I'm wondering where to start to look to find a fix for this.

---

### Post by JamieC on 2007-02-01
What error message do you receive? Have you tried any other web-based IMAP clients (such as Round Cube Webmail)? Did you use exactly the same credentials when using telnet? 

Can you please post the output of your virtual user table?:
```

sudo <editor> /etc/postfix/virtusertable

```
(Note: this will contain your e-mail addresses, feel free to paste the contents as a private message if you do not wish to disclose them here).

---

### Post by qwert231 on 2007-02-01
virtusertable doesn't exist... Hmm... should be using mySql for users.

---

### Post by qwert231 on 2007-02-01
Ok... one thing I noticed... I hadn't set the default domain, so if I just used username and not [email]username@domain.com[/email] I couldn't log in. Now, I get:
ERROR:
ERROR: Connection dropped by IMAP server.

Postfix
Courier
Squirrelmail

Any thoughts? Ideas?

---

### Post by qwert231 on 2007-02-01
Okay... I went into the Virtual folder and created a folder called username. I gave permissions to virtual. Now with Squirrelmail I get 2 frames:
ERROR:
ERROR: Connection dropped by IMAP server.
Query: SUBSCRIBE "INBOX.Sent"

ERROR:
ERROR: Could not complete request.
Query: SELECT "INBOX"
Reason Given: Unable to open this mailbox.

My log says I login successfully.

What gives?

---

### Post by qwert231 on 2007-02-02
Okay... I've gotten down and dirty. I telnet into 127.0.0.1 143 and do some low level imap commands.
mark@linux800:/etc/courier$ telnet 127.0.0.1 143
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2005 Double Precision, Inc.  See COPYING for distribution information.
a login user password
a OK LOGIN Ok.
a list "inbox" "*"
* LIST (\HasNoChildren) "." "INBOX.Drafts"
* LIST (\HasNoChildren) "." "INBOX.Trash"
* LIST (\HasNoChildren) "." "INBOX.Sent"
a OK LIST completed
a subscribe inbox
* BYE [ALERT] Fatal error: No such file or directory
Connection closed by foreign host.
mark@linux800:/etc/courier$ 

The folder /var/mail/virtual/mark (which is the username) shows .Sent. .Trash, and .Drafts
However, I created mark using mkdir, and assigned virtual as owner and group. Don't know if that was correct.
.Sent was created the first time I tried to log in with SquirrelMail. '.Trash' and '.Drafts' I created in another session of telnet into 143. Again, I don't know if that is correct but I wanted to see what I could do.

So, obviously I need to subscribe. But I can't. (Maybe I'm going down the wrong path.) What can I do?

---

### Post by rekon on 2007-07-31
Just curious if this problem has ever been solved? I am having the exact same issue and I cannot figure out what to do. This is the only topic I've found regarding this. Thanks.

---

### Post by wtkad on 2007-09-12
I'm stuck at the exact same point as post #5.  Is there a solution for this issue?

---

### Post by Raybdbomb on 2008-06-26
same exact issue here...

---

### Post by wtkad on 2008-06-26
I don't remember how I got past it - I'm not sure I even knew how I did it at the time.

I do know that now when I create a new email address, I have to send an email to that address before SquirrelMail will login successfully.  Otherwise, it errors out because it can't find all the folders it wants.  But they are set up correctly when an email is delivered.

---

