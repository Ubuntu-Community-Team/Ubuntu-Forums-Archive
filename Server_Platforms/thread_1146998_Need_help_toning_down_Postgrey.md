---
title: "Need help toning down Postgrey"
date: 2009-05-03
forum: Server Platforms
---

### Post by Dy1anW on 2009-05-03
Still a bit shakey on my feet when it comes to mailservers, but I've been having problems with Postgrey, having checked the logs almost religiously, it seems it's been rejecting some legitimate mail.  How can I tone this down so all legitimate mail gets through?

For now I've just removed the daemon and reconfigured Postfix to work without it, but it would be (probably?) a good idea to have it running.

---

### Post by Dy1anW on 2009-05-03
Managed to find a solution to that.  Edit /etc/default/postgrey  with the option --auto-whitelist-clients

Edit /etc/postgrey/whitelist_client to include the domain of legitimate senders

---

