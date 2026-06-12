---
title: "block external mail to root account?"
date: 2006-04-25
forum: Server Platforms
---

### Post by Brocco on 2006-04-25
I'm new to Postfix and have run into a problem that I imagine everyone has, and I'm amazed that I can't find the solution to this simple use case.  I feel like I'm drowning in a sea of Postfix documentation and mailing lists.

I installed Postfix on Ubuntu, and the Ubuntu package created an aliases file to redirect mail addressed to "root" to my user address ("brocco").

So now I'm getting spam that's addressed to [email]root@mydomain.com[/email].  I want to continue to receive mail that's sent to root locally, but not from the Internet.

Doesn't everyone have this problem?  Why isn't mail sent to root from the Internet automatically blocked?

I've seen people on the Postfix mailing list talk about setting root to be a "local only" account but I can't figure out how to do that.  Please fix my stupidity.

Thanks,
Brocco

---

