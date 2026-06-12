---
title: "Differences between anonymous access and a system user access"
date: 2011-03-29
forum: Server Platforms
---

### Post by overdraft on 2011-03-29
Hi,

I have installed and configurated proftpd successfully. I have activated the anonymous section too and all is working fine.

Then I have created a guest account creating a user in the system (Debian 6) and writing another anonymous section. The username is roger, and my anonymous section is like this:

<Anonymous ~roger>
User roger
Group roger
AnonRequirePassword off
</Anonymous>

So, now I can log in my ftp by introducing roger as username, and an email address (I don't have to introduce the password).

The question is: What's the difference between log in that way (anonymous access) and log in the ftp with my user (roger) credentials (user and password) after commenting the anonymous section above? I doubt about the real difference. Maybe permissions or security?

Please, some help...

---

