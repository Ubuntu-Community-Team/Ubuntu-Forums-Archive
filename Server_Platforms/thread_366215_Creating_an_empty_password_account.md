---
title: "Creating an empty password account"
date: 2007-02-20
forum: Server Platforms
---

### Post by vetlin97 on 2007-02-20
In ubuntu 6.10, is there an easy way to create an account with an empty password?  By this I mean when a user types in his username, there is no password prompt.  This is not for a gui login but for a console login so this goes beyond an X setting to auto-login.  I have tried removing the password from the /etc/shadow file and then tried removing the "x" from /etc/passwd.  I have also tried setting the /etc/pam.d/common-* files from "required" to "sufficient" which did not work.  Any help will be greatly appreciated.  Thanks.

--Frank

---

