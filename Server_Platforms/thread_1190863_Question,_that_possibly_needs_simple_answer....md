---
title: "Question, that possibly needs simple answer..."
date: 2009-06-18
forum: Server Platforms
---

### Post by psicloone on 2009-06-18
Hi, 

I`ve installed LAMPP, and deleted everything from htdocs (after all components were secured).
Now, when I go to localhost it takes me automaticly to localhost/xamp, which is of course empty.

I have to type localhost/index.php to get to the right place.

How to make it go there if I type only localhost?

---

### Post by ghen on 2009-06-18
Not sure exactly, but I tried googling:

lamp server index.php

and found this gem:

> Add index.php to the list of valid Directory Index files so that your "default page" in a directory can be named index.php.

[HTML]<IfModule mod_dir.c>
    DirectoryIndex index.php index.htm index.html
</IfModule> [/HTML]

Unfortunately I have no idea where that would go. So the next step would be to research Directory Index on LAMP.

---

### Post by psicloone on 2009-06-18
The problem was solved, after I restarted the PC - I don`t know how.

By the way, what mail configurations I have to do if I want to use this contact form script:

[http://www.ibdhost.com/contact/](http://www.ibdhost.com/contact/)

How to configure my mail server, anybody knows?

---

### Post by ghen on 2009-06-19
Ask in a new thread with a detailed subject line, I have no idea.

---

### Post by terazen on 2009-06-20
After you make changes to your apache config files or use something like a2ensite/a2enmod etc. just run `sudo /etc/init.d/apache2 restart`.  You shouldn't ever need to reboot.

---

### Post by terazen on 2009-06-20
Also, you just need to install postfix for the email form and the it should work fine.

When it asks you what type of mail server you want to make (internet, satellite, etc.) be sure to pick the right one or you'll need to run reconfigure.

---

