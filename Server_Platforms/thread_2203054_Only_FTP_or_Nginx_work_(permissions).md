---
title: "Only FTP or Nginx work (permissions)"
date: 2014-02-01
forum: Server Platforms
---

### Post by lucas11 on 2014-02-01
Hello guys,

I've for too long used to work with windows web server and now im migrating to linux.

I've created a new server running Ubuntu 12.10 x64.

Installed Nginx, tested, it is ok.

Installed vsFTPd, tested, it is ok.

But only when each one have permissions set to it.

I have a user manga. its home directory is /var/www/manga

I've created a public_html folder, which is the root of the ServerBlock.

When i apply chown of that folder to manga, the VSFTPD upload work, but the NGINX gives me 403 error.

When i apply chown of that folder to www-data, the NGINX work, but VSFTPD denies me uploads.

I've tried to set the chmod to 755 of /var/www
I've tried to make manga user of the group www-data (using $sudo usermod -aG www-data manga)

Even thought, i cant make all work normally.

Please someone take this headache of my head haha

Thank you

sorry my english.

---

### Post by cariboo on 2014-02-01
This is more a question about servers, than a security question. Moved.

---

