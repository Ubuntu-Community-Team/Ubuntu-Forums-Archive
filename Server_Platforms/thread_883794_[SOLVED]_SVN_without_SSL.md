---
title: "[SOLVED] SVN without SSL"
date: 2008-08-08
forum: Server Platforms
---

### Post by SPW06 on 2008-08-08
Hello.

My web (debian based) host offers SVN, and a simple script to set up trac. But, I don't want to pay an extra $99/year for SSL. So, I was wondering if SVN logins are venerable without SSL. I know everything will be sent in the clear. I don't care about my source being read, its going to be open anyway. :p I do worry about my SVN login being stolen, and someone wreaking my repo. Is there as least password hashing (MD5)?

---

### Post by tamoneya on 2008-08-08
a common solution is to put it through ssh.  That should be plenty secure for sending passwords.  You would have to ask you host though to see if they can configure this for you.

---

