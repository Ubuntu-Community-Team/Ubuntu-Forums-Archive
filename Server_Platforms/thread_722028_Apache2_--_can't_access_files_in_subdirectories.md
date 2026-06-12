---
title: "Apache2 -- can't access files in subdirectories"
date: 2008-03-12
forum: Server Platforms
---

### Post by mkotzev on 2008-03-12
Hi all,

I'm pretty new to Apache (though I have some Linux experience) so bear with me. I am trying to create a php-based web app but things aren't going to so well. Everything is fine when I have files in /var/www/, but for some reason my scripts can't access any of the subdirectories i've made, including /var/www/cgi-bin/ where I have some vital form-processing php scripts. I'm not sure if there has to be a specific user owning the subdirectories or if it is simply a matter of setting some directives in a .conf file somewhere. Either way, I would like at least to be able to type in the url manually and be able to visit a page inside /cgi-bin/. Any ideas?

I'm running Apache2 on Ubuntu 7 with an out-of-the-box LAMP installation.

~Miro

---

### Post by jamestech on 2008-03-14
I had a similiar problem, it was down to permissions. Right click the folder, choose the permissions tab, and check the "Folder Access" on both Group and Others (I expect only one needs to be set but not sure which), set them both to "Access Files" and you should then be able to read them.

---

