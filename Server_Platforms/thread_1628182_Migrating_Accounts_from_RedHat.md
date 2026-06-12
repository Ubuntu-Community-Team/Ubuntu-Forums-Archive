---
title: "Migrating Accounts from RedHat"
date: 2010-11-22
forum: Server Platforms
---

### Post by lavajumper on 2010-11-22
Hey All!

We're currently replacing our Red Hat servers with Ubuntu. We've got the scripts written to migrate the existing Red Hat accounts, which includes copying all the home directories, adjusting UID/GID then copying the correct entries to passwd, group and shadow files. While testing the migration scripts I noticed that Ubunutu is using sha512 while our Red Hat uses md5. 

My limited understanding of encryption tells me that there is no way to convert these hashes to sha512 without the password.

Is there an intelligent way to handle this? Perhaps a Pam entry that checks an md5 and converts to sha512 on authentication?

We are trying to avoid having to tell all our clients they have to set passwords, and our policies dictate that we don't keep a record. Also, I'd prefer not to 'break' the ubuntu installation by changing everyone to md5.

---

### Post by SeijiSensei on 2010-11-22
Read /etc/pam.d/common-password.  It looks like you can just remove the sha512 option from the password directive and revert back to md5.

I don't think you'll find anything to convert the hashes.  You might be able to use "rainbow tables" to find the hashes for common words, but any relatively complex password should be nearly impossible to break even with md5.  So I'd just switch back to md5 and use it throughout.

---

