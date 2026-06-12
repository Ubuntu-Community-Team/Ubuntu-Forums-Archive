---
title: "limit user access  with sftp"
date: 2009-04-14
forum: Server Platforms
---

### Post by zemon_ on 2009-04-14
Im running ubuntu server 8.10 and sharing with a few others.
How can I restrict users from accessing other users directorys when using sftp?

At the moment users can access anywhere they want on the server.

Thanks in advance

---

### Post by antikristian on 2009-04-14
you'll probably have to change the umask value to something like 066 which will cause new files created to only be readable by the creator.

Also you would have to chmod all the existing files with 0700 to apply the permission on the existing files.

Remember to test this out on a test user before you implement it system wide.

---

### Post by HermanAB on 2009-04-14
Hmm, there is only one way to safeguard TFTP: Turn it off.

TFTP is designed to work without authentication.

---

