---
title: "how to prevent symlink attack"
date: 2014-08-11
forum: Security
---

### Post by ali_ahmady on 2014-08-11
hello everyone
I'm a little bit new to ubuntu server.
i was tryin to disable symlinks in apache2 as a challenge in my own localhost.
i changed apache2.conf contents like this to deny reading symlinked files :
[HTML]
<Directory /var/www/>
    Options Indexes SymlinksIfOwnerMatch
    AllowOverride None
    Require all granted
</Directory>
[/HTML]
it worked in apache and at address bar and i wasnt able to see the link  (403 error) but i still could read the file content using cat and php  functions.
since there is no easyapache and mod_hostinglimits for ubuntu (without  cpanel and cloudlinux) can you friends tell me how can i handle this?
thanks in advance :smile:

---

