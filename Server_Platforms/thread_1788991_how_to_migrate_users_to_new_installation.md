---
title: "how to migrate users to new installation?"
date: 2011-06-23
forum: Server Platforms
---

### Post by vernondcole on 2011-06-23
How do I migrate my user list to a new server installation? I thought that just copying /etc/passwd and /etc/shadow would be enough.
  I recently tried upgrading a lightweight bazaar server to 11.04, and the upgrade crashed.  I had to perform a new installation of Ubuntu to recover operation of the system.  I installed on a different hard drive. I had a dozen other people with user logins, so that they can get or modify bazaar repositories.
  The new installation is running, and I can read all of the files on my old system's / drive.  I tried copying the /etc/passwd and /etc/shadow files onto my new /etc -- but that did not seem to work. (When I looked using the System->Administration->Users-and-Groups GUI tool, there were no users visible, so I restored the old files.)
  What I intended to do was to clone the /etc and /home trees over to the new system.  What am I missing?
--
Vernon Cole

---

### Post by Beacon11 on 2011-06-23
This might be helpful: [http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/](http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/)

---

