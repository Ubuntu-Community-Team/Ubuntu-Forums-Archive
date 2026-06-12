---
title: "[postfix] how to redirect a virtual user mail to /dev/null"
date: 2010-03-12
forum: Server Platforms
---

### Post by zespri on 2010-03-12
Hello,

I followed guide posted here:  [http://neranjara.org/article/title/How_to_configure_PostFix_and_Dovecot_for_Virtual_Users_with_out_a_Database_](http://neranjara.org/article/title/How_to_configure_PostFix_and_Dovecot_for_Virtual_Users_with_out_a_Database_) and all worked great. 

However I'm not sure how can I set up a virtual user to redirect all mail to /dev/null without just deleting their mailbox on schedule.

I tried to put them in virtual_alias_maps:

```
trash@example.com nobody
```

and then set up an alias like this:

```
nobody: /dev/null
```

Unfortunately it didn't work as I have a catch all address in virtual_mailbox_maps:

```
@example.com example.com/catch-all/
```

So in the log I see that mail to [email]trash@example.com[/email] has been delivered to [email]nobody@example.com[/email] and the mail itself appears in the catch-all mailbox.

How do I work around this?

---

### Post by zespri on 2010-03-16
Silence here
Silence in a postfix news group
Silence in #postfix IRC
Much harder to get support for *nix stuff than for windows related questions.

---

### Post by KB1JWQ on 2010-03-16
That's interesting-- neither here, newsgroups, nor a non-freenode IRC network are official Postfix support forums; perhaps you should be more diligent in researching the proper venue for your questions?

That being said, you could create a local user aliased to /dev/null and redirect mail to that virtual user to that local user via virtual_alias_maps.

Failing that, look up DISCARD in the access maps, it may do what you need.

Failing that, you could create a pipe transport to /dev/null in master.cf and reroute mail for that user over that specific transport.

---

### Post by KB1JWQ on 2010-03-16
Oh, and there's also a DISCARD transport.

---

### Post by zespri on 2010-03-16
First of all, thank you for replying.

> **KB1JWQ said:**
> That's interesting-- neither here, newsgroups, nor a non-freenode IRC network are official Postfix support forums; perhaps you should be more diligent in researching the proper venue for your questions?
It was freenode IRC. Asked the question three times during the course two days (roughly every 12 hours). Just out of curiosity where else but "official" IRC and a mailing list listed on the "official" site could I go? However, this is beside the point. 

> **KB1JWQ said:**
> That being said, you could create a local user aliased to /dev/null and redirect mail to that virtual user to that local user via virtual_alias_maps.
This is exactly how I tried to set it up, see my original post. It didn't work. Catch-all kicked in first and although I didn't have virtual mail box for this user it redirected the mail to catch all address. I may be set it up wrongly, I explained how I did this in the OP.

> **KB1JWQ said:**
> Oh, and there's also a DISCARD transport.
This one is what has finally worked. Thank you for the tip.

---

