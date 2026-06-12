---
title: "Noob Q: Configuring Apache www dir"
date: 2011-04-15
forum: Server Platforms
---

### Post by killerclick on 2011-04-15
So I've installed Apache but the web folder is /var/www which needs administrator privileges to open and modify. Obviously this is not how it's supposed to work but for some reason no one has seen fit to explain this in any place I've looked.

Could someone please point me to an explanation where and how I should put my websites without referring to some third party GUI?


Thanks

---

### Post by Ryan Dwyer on 2011-04-15
It's supposed to be like that. If the directory was writable by normal users then anyone with shell access to the machine could deface your website.

If you're the only user who will be editing the files, you can create a directory in your home folder such as /home/yourname/www/ and change Apache's DocumentRoot to it (in /etc/apache2/sites-available/default).

Or just change the owner of everything under /var/www/ so you can write to it.

---

### Post by espressobeanie on 2011-04-15
I'm not really understanding the question. What's the third party GUI? AFAIK, there are no GUI's for apache. As Ryan Dwyer says, Apache by default has to assume that you're not the only user on your machine. 

To change this,simply 'cd /var/' and 'chown yourusername -R www'

---

