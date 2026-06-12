---
title: "Get smtp-auth to check against my virtual users instead of real system users."
date: 2007-07-30
forum: Server Platforms
---

### Post by nibbo on 2007-07-30
So I now have a working mailsystem on my server. The system consists of posfix with a mysql database to keep track of the virtual users. The database is administrated with postfixadmin.

I only have one small problem left. To send mail with the smtp-server you have to auth. The auth goes via saslauth. However, the system now, for some reason checks if the user is a system user and won't let my virtual users send mail. 

Any ideas on what to change to get it to work?

Sorry for bad english :)

---

### Post by deuce868 on 2007-07-30
look into using pam-mysql with saslauthd

---

