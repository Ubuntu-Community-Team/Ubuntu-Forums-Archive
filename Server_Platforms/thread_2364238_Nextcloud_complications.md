---
title: "Nextcloud complications"
date: 2017-06-20
forum: Server Platforms
---

### Post by pete0512 on 2017-06-20
I've been trying to install nextcloud on 16.04 desktop following the instructions here [https://docs.nextcloud.com/server/12/admin_manual/installation/command_line_installation.html](https://docs.nextcloud.com/server/12/admin_manual/installation/command_line_installation.html) and it was going well until I reached this line 
```
sudo chown -R www-data:www-data /var/www/nextcloud/
```
Then I got the information that /var/www/nextcloud/ did not exist and indeed a quick check revealed this to be true, so I tried locate and that found plenty of nextcloud folders but none in a www folder.
But there were a few in the ~/snap folder but when I tried to see them in file manager nothing to be seen apart from libreoffice files and ls -a revealed the same story. 
So has anyone any ideas what I'm doing wrong, and how is it that locate can find files that don't seem to be there

---

### Post by TheFu on 2017-06-20
```
sudo mkdir -p /var/www/nextcloud/
```
People often forget to make the directories - either you forgot or the instructions forgot. This is common.

I didn't look at those instructions, but do run nextcloud myself.  I used a different guide for the install and don't let nextcloud directly on the internet. Have to use either a VPN or SOCKS proxy to access my install. It is a security decision.

**locate** reads from the **updatedb** database. That gets updated daily/weekly depending on your settings. If you want an exact, current, view of file system, use **find**, but expect it to take much longer.  locate is a simple DB lookup, nothing more.

I don't know anything about snaps.

---

