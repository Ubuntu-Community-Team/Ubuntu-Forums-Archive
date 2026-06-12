---
title: "IMAP email - nested folders"
date: 2007-05-29
forum: Server Platforms
---

### Post by Pitt Stains on 2007-05-29
Hello,

I am planning on setting up email services in the near future, and want to avoid a problem I've found with my current email service provider.  This is my first adventure in admin, so please bear with me.

The current setup precludes users from creating IMAP folders inside of other IMAP folders.  I don't know if this is a limitation of the mail delivery agent, or if "nested folders" is a setting that for whatever reason the admin has decided to turn off.  He's running a Debian OS, but I don't know what the MDA is.

It's important for my users to be able to use multiple levels of folders to organize their mail, so I want to make sure the package I choose allows them to do that.  It appears that Dovecot and Courier are the two of the more popular MDAs out there.  Do they both allow nested folders?

Thanks!
-Pitt Stains

---

### Post by jtc on 2007-05-29
I use nestled folders with my courier-imap.

Should be noted that subfolders aren't part of the original maildir format. They are however part of the rather widely supported extension maildir++.

---

### Post by MJN on 2007-05-29
Dovecot is more than happy with them too.

Looks like you won't have a problem here!

Mathew

---

### Post by Pitt Stains on 2007-05-29
Thanks!

---

### Post by Brazen on 2007-05-29
Here's some nice, easy Dovecot on Ubuntu documentation for you:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html#dovecot-server](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html#dovecot-server)

---

