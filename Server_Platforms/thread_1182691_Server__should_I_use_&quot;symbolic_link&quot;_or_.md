---
title: "Server :: should I use &quot;symbolic link&quot; or option Directory in Apache virtual host"
date: 2009-06-09
forum: Server Platforms
---

### Post by derbouka on 2009-06-09
Hi!

I want to include a directory in my web project project and I would like to know which is the most "correct" (or efficient) way:
  * Creating a symbolic link in my web directory to *my_folder* that I want to include;
  * Creating a "<Directory *my_folder*>" entry in the virtual host file, letting apache do that;

Can anyone tell me which is the better way in a cpu usage perspective?

Best regards,
Daniel Botelho

---

### Post by blackxored on 2009-06-09
I normally use symbolic links to the root of my projects under VC, but that's a matter of personal choice. If you are unsure use symlinks, there are easiest, and less rigid that httpd config files.

---

