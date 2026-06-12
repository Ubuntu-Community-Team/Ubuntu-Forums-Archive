---
title: "Fetchmail marking messages as read"
date: 2011-10-07
forum: Server Platforms
---

### Post by viperce on 2011-10-07
Hi I am having a problem with Fetchmail, I have set it to leave a copy of the message on my ISP's pop3 server so clients with blackberry's and other phones can still collect the mails from my ISP. But fetchmail is marking the emails that it is downloading as read and the clients are phones are not collecting the emails since they are marked as read.

Is there any way i can get fetchmail to leave the emails marked as unread?

thanks

---

### Post by viperce on 2011-10-10
no one have any ideas on how to fix this?

---

### Post by viperce on 2011-10-11
Example of the config i am using.

> 
poll pop.gmail.com
        proto imap
        user "user@gmail.com"
        pass "password"
        is [email]user@gmail.com[/email]
        fetchall
        keep
        ssl


---

### Post by SeijiSensei on 2011-10-12
> poll pop.gmail.com
proto imap


Are you using POP3 or IMAP?  GMail's IMAP server is imap.gmail.com; the POP3 server is pop.gmail.com.  Maybe it's just the result of this conflict.

I'd just use IMAP everywhere so that clients see the identical mail structure regardless of how they're getting their mail.  Read messages will be marked accordingly, but they should still all appear in the clients' inboxes.

---

### Post by viperce on 2011-10-13
was using pop3 then i read somewhere that if u changed it to imap it would leave mail unread on the server...
Didnt work back to pop3 now :(

---

### Post by viperce on 2011-10-13
changed config to 
> poll imap.gmail.com
        proto imap
        user "user@gmail.com"
        pass "password"
        is [EMAIL="user@gmail.com"]user@gmail.com[/EMAIL]
        keep
        ssl
mails are still being flagged as read :(

maybe it is not possible to do this using fetchmail?

---

### Post by SeijiSensei on 2011-10-13
Are the phone clients set up to use IMAP?  If so, I don't see what different the "read" flag makes.  The phone client should show all the messages in the inbox with the read/unread flag set as appropriate.  Does the phone only show the unread messages?  That's a strange configuration for an IMAP client.

---

