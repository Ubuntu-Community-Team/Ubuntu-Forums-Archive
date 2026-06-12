---
title: "Add signature to outbound email"
date: 2006-02-17
forum: Server Platforms
---

### Post by My-dial-up on 2006-02-17
My original post from 'The Absolute Beginner section';

[http://ubuntuforums.org/showthread.php?t=132062](http://ubuntuforums.org/showthread.php?t=132062)

I was advised to repost here.

I'm using Ubuntu as a mail relay for all my in/outbound email. How can I add a signature to all outbound email?

I'm using postfix, and all intranet/internet email passes through postfix on the ububtu server. At work we have half a dozen XP PCs all using this server, what I've been asked to do is add a 'disclaimer' on all outbound emails. 

Using the signature option in Outlook isn't an option as this can be modified on each PC.

Can anyone help please?

---

### Post by robert_pectol on 2006-02-18
You're asking the MTA to do something it has no business doing!  Message body content should never be altered by the MTA.  You're better off using a separate piece of software to do it for you, such as alterMIME:
[http://www.pldaniels.com/altermime/](http://www.pldaniels.com/altermime/)
I've never used it before but it claims to be able to do what you want.  Good luck.

---

