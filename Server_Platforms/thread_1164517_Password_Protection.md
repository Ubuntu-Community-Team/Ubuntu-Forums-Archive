---
title: "Password Protection"
date: 2009-05-19
forum: Server Platforms
---

### Post by vidgpersonrsw on 2009-05-19
How in the world can I password protect directories? I have tried htaccess files but I have yet to get them working. Is there anyway I can use webmin to do this? I am so sick of trying to get this to work and failing miserably. It should not be this hard yet I can't get it to work.


Thanks,
vidg

---

### Post by windependence on 2009-05-19
Try this:

[http://www.thesitewizard.com/apache/password-protect-directory.shtml](http://www.thesitewizard.com/apache/password-protect-directory.shtml)

Don't forget, you need to set up the password file also, AND it needs to have the correct permissions and be owned by the right user.

-Tim

---

### Post by vidgpersonrsw on 2009-05-21
> **windependence said:**
> Try this:

[http://www.thesitewizard.com/apache/password-protect-directory.shtml](http://www.thesitewizard.com/apache/password-protect-directory.shtml)

Don't forget, you need to set up the password file also, AND it needs to have the correct permissions and be owned by the right user.

-Tim

That was probably my problem (the permissions and owner). What should those be?

---

