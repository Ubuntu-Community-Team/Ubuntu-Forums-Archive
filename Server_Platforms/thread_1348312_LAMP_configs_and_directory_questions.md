---
title: "LAMP configs and directory questions"
date: 2009-12-07
forum: Server Platforms
---

### Post by noobixide on 2009-12-07
Hello everyone!

This is my first server install of Ubuntu. I am running 9.04 on an old IBM.

I am trying to create a simple web server I can use while I develop my new website. I have had some experience with linux (IE. I know how to use 75% of the simple commands like apt-get, vi, etc)

During installation I selected the following to be installed, LAMP Server, Mail Server, and SSH. I'm using Putty as my SSH client to manage the server from my windows machine.

I have installed proftpd and it is working correctly. There are 2 main things i need to know. 

#1 Where in the world is httpd.conf for Apache and where is the root directory folder to place the contents of my website.

#2 How can i configure Proftpd to have the above directory as my home when i login. 

If you can only answer #1 I would be soooo much closer to my goal.


Ive looked at some documentation and such but cant really find anything useful. Sorry if this is a FAQ somewhere!

Thanks :D,


Noobixide

---

### Post by ubhi on 2009-12-07
1. your config file httpd.conf

/etc/apache2/httpd.conf

& ur root of web

/var/www/index.html

---

### Post by noobixide on 2009-12-07
[I]Thank you so much for the help! I have another question.

When I open  /etc/apache2/httpd.conf with vi its not a new file, rather an empty file. Should I paste into vi a default config, or am I looking at the wrong file?

[/I]**EDIT: **I actually found the answer myself, /etc/apache2/httpd.conf is not what apache is using for its config file. It IS using /etc/apache2/apache2.conf and then in the config file it has:

> # Include all the user configurations:
Include /etc/apache2/httpd.conf

---

### Post by Iowan on 2009-12-07
You already discovered some of the "secrets" - [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a help page with some more...

---

