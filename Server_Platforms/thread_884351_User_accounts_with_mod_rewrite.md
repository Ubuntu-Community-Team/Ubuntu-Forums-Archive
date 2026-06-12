---
title: "User accounts with mod_rewrite"
date: 2008-08-08
forum: Server Platforms
---

### Post by TrevorNet on 2008-08-08
My server set-up is such that each user account has a public_html folder. Using the URL: [http://127.0.0.1/~trevor/](http://127.0.0.1/~trevor/) drops me into my directory. The benefit to this set-up is that it allows me easy access to manage my development site w/o running into permission problems.

In the past I've enjoyed playing around with mod_rewrite. I've been all over the web looking for an answer on how to enable "AllowOverride All", but the only thing I come up with is by manipulating the global file at /etc/apache2/sites-available. This does nothing for me (yes I restart apache after modding this file ::grin::).

Does anyone know where the file is that will allow me to enable this on user accounts? I can't even remember where the tute is that helped me create this configuration.

Thank You!!!
Trevor

---

