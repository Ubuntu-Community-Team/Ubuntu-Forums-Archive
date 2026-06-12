---
title: "Apache2 userdir module permissions problem"
date: 2009-05-23
forum: Server Platforms
---

### Post by phinullfermata on 2009-05-23
Hi,

I've tried to enable the userdir module in apache2, and for some reason it isn't working properly.  I used  a2enmod to enable userdir, I edited the mods-enabled/userdir.conf to change the public_html directory to the name www in both places, and for some reason my browser is saying I don't have permission to view the web page.

I ran chmod 777 on the folder www and all its contents, so it can't just be file permissions... is there anything I"m missing here? Are there any other files I need to edit? Any help would be greatly appreciated.

Thanks in advance.

[EDIT]

UserDir is working now, I needed to set my home directory to be executable.

---

