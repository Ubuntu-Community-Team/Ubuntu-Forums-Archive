---
title: "maildrop mailfilter usage examples / tutorial?"
date: 2010-06-08
forum: Server Platforms
---

### Post by superradical on 2010-06-08
So I have some extremely high-volume email to deal with and I need to get maildrop going.  It's installed but the /etc/maildroprc is the standard commented do-nothing file.

this site:
[http://www.courier-mta.org/maildropex.html](http://www.courier-mta.org/maildropex.html)

That is the best resource I've seen yet but it is extremely vague.  Where can I find information on this syntax that isn't that page or the man page?

Is there any syntax to declaring something a rule or can you just drop "if" statements everywhere and it works?  Do you need to restart any daemon after modifying maildroprc?  Is there a reference for the pattern-matching or are they posix regular expressions?

---

### Post by superradical on 2010-06-08
I found some old mailing list threads that were useful and have narrowed the problem down to this:

Our actual email is in /var/mail/virtual  and our users are handled virtually in mySQL table.  So setting DEFAULT="$HOME/Maildir" seems like it would have unwanted results.  Also, I notice most "if" rules use a to Mail/subfolder format.

Now, our virtual mail folders just have hidden folders for the 'special' folders.  So am I correct in assuming that I can just add:

if (/^Subject: *special subject/)
{
  to .special_folder
}

Will place any message with "special subject" in special_folder for that user?

---

