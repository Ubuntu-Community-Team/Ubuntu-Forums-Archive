---
title: "Someone tried to view my desktop remotely"
date: 2012-02-22
forum: Security
---

### Post by Vistz on 2012-02-22
My laptop was suspended and when I turned it back on/connected to my university's wired network, I got a notification from ubuntu saying someone with an IP address xxx.xx.xxx.xxx is trying to access my desktop. I closed the dialog without recording the IP address. Is this information recorded in the logs anywhere?

Also, is there a way I can prevent this from happening in the future?

---

### Post by uRock on 2012-02-22
UFW doesn't log unless configured to do so. running the following command will block all incoming connections. You can install GUFW to configure the firewall to allow and/or log events. My signature offers the place to look for all log entries.```
sudo ufw enable
```

Moved to *Security Discussions*

---

### Post by cariboo on 2012-02-22
> **Vistz said:**
> My laptop was suspended and when I turned it back on/connected to my university's wired network, I got a notification from ubuntu saying someone with an IP address xxx.xx.xxx.xxx is trying to access my desktop. I closed the dialog without recording the IP address. Is this information recorded in the logs anywhere?

Also, is there a way I can prevent this from happening in the future?

Turn off desktop sharing, if you are actually using Lucid, it should be under the system menu.

---

