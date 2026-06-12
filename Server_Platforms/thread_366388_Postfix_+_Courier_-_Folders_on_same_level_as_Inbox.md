---
title: "Postfix + Courier - Folders on same level as Inbox"
date: 2007-02-20
forum: Server Platforms
---

### Post by jmacdonagh on 2007-02-20
I followed a tutorial on setting up PostFix + Courier on my Edgy server:

[http://www.urbanpuddle.com/articles/2006/12/20/setup-a-postfix-mail-server-on-ubuntu-edgy-eft](http://www.urbanpuddle.com/articles/2006/12/20/setup-a-postfix-mail-server-on-ubuntu-edgy-eft)

It works fine, but there is one small annoyance. I'm used to having folders on the same level as Inbox for Sent, Trash, and Junk. However, with my current setup, I can only create folders inside the Inbox folder.

Now, is that a limitation of a) Postfix or b) Courier? It seems that it's a limitation of Courier, although I would have thought Postfix has something to do with it as well. Postfix is the application that's doing the delivering, right? I would want Postfix to deliver new mail to /home/vmail/mydoman.com/myusername/.Inbox/new instead of /home/vmail/mydomain.com/myusername/new .

I'm all confused. What can I do to get this feature?

Thanks

---

### Post by Mr. C. on 2007-02-22
Neither postfix nor Courier are the problem.   Postfix delivers to Maildirs, but only to the inbox (it knows nothing about folders).

Your MUA doesn't have its IMAP namespace configured correctly.  It needs to be "INBOX." with the period at the end.

What MUA are you using (mail user agent... your mail reader)?

---

### Post by jmacdonagh on 2007-02-23
Thanks for the reply. You're correct. Since my post I learned all about IMAP namespaces. I now know how Maildirs work :).

The new issue is, no matter what namespace i force my client to use (KMail, Evolution, Thunderbird) the folders always appear under Inbox. Some combinations of namespace choices and clients either don't show my additional folders, or show them on the correct level, but clicking on them doesn't show any of the messages that I know are in there.

The Personal namespace needs to be INBOX. correct? I've tried to force my clients to use INBOX. inbox. "INBOX." and "inbox." . According to KMail, my server is seding INBOX. as the namespace.

The location of my mailbox is:
/home/vmail/domain.com/username

And in there are the standard cur tmp and new directories. Should I create an additional directory, either /.INBOX or /Maildir ? 

Thanks

---

