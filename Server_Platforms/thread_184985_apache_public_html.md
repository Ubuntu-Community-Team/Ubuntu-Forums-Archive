---
title: "apache public_html"
date: 2006-05-30
forum: Server Platforms
---

### Post by hfranco on 2006-05-30
I'm currently hosting two personal websites on my computer.  website1.com and website2.com.  I have a public_html for a user named bob. How do I set it up so that I don't have to see website1.com/~bob and website2.com/~bob.  I just want to see bob's public_html on website1.com

Is there a way where I can specify what domain name I want to show public_html to?

-hfranco

---

### Post by bDerrly on 2006-06-03
You're going to want to create a virtual server configuration in /etc/apache2/sites-available.  I would just copy the default config and edit it as necessary.  The things you're going to want to change for certain is the <Directory /var/www/> to <Directory /home/bob/public_html> and possibly the cgi-bin configuration as well.  There are good docs on the apache website about virtual domains and the like.

Once you get your configuration done you'll need to symlink your config into the /etc/apache2/sites-enabled directory and reload apache.  Test and reconfigure as necessary.

---

