---
title: "SendMail - Gmail Relay Header"
date: 2009-11-29
forum: Server Platforms
---

### Post by carthmen on 2009-11-29
Hello

  While getting sendmail set-up on a new server box, i ended up with this problem.  Sendmail is sending and receiving email.  I am using gmail's smtp server for sending the emails.  I set this up via this [link's]("http://www.phinesolutions.com/sendmail-gmail-smtp-relay-howto.html") tut.

  The problem is that gmail says that the email address that sent the email is from the gmail account used for the email, not the address in the headers.  I think this is becuase sendmail is putting in the header that the email is from user@localhost instead of [EMAIL="user@something.com"]user@something.com[/EMAIL].

  Anyone have any experience with this. Attached is my modified mc, with the domains changed to something.com

 Any help would be greatly appreciated.

Thanks 
Roger B.

---

### Post by carthmen on 2009-11-29
UPDATE:

Ok, after doing some additional research, google will no matter what replace it, or so it seems, but even then the header should not be reporting user@localhost.

So still looking for a solution to that.

---

