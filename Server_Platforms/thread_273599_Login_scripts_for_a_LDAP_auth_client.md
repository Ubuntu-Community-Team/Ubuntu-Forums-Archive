---
title: "Login scripts for a LDAP auth client?"
date: 2006-10-08
forum: Server Platforms
---

### Post by Dalik on 2006-10-08
I setup openLDAP and I am able to login using a user I created in LDAP.
Now I am trying to do things the windows way and I am having some issues but this post will be for login scripts.

I want to use login scripts for ldap logins, I should be able to set a login script file and or path and that is executed by the client right after login.

This to me should be an easy task and almost native to linux.  openLDAP "should" I believe anyway have a field to put in a login script path and that path is then "mounted" and the script executed for the client so for example, that machine can have mounted drives or map drives.

I wouldnt think I had to manage this on a per user scale via home directoies, and editing config files to me this goes against the LDAP theme(single administration point).

Any ideas on a somewhat easy way to do this, I really hope its something that you dont need to spend a good few hours sorting out.

Cheers

---

