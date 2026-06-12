---
title: "Installing Wordpress on Ubuntu"
date: 2023-07-24
forum: Server Platforms
---

### Post by palexeim on 2023-07-24
Hi.
I'm working on the test task and have some issues.

I need to install LEMP server (Nginx, MySQL, PHP)
Then I need to configure 3 virtual hosts of Wordpress.
The 1st vh should be processed via PHP 8 through the socket.
The 2nd vh should be processed via PHP 7.4 through the port and should be processed to the 'www' pool.
The 3d vh should be processed via PHP 7.3 through the port and should be processed to the 'inet' pool.

I need to create 3 WP directories and - if I understood correctly - unzip there Wordpress (however I still don't know if there're should be 3 WP instances according to each directory).

The only thing I know that each virtual host need to demonstrate phpinfo.php while it'd opened.

---

### Post by TheFu on 2023-07-25
Seems like a good list of exercises.  Good luck.

I don't see any question or any attempts at solving it yourself.  Just know that MariaDB is the default DBMS, not mysql.  They are API compatible, just without Oracle's fingers involved.

I use LEMP - Nginx, MariaDB, Perl all the time, though nginx really is just a redirector/TLS termination point to starman which does the load balancing for perl with PSGI interface.

If you have a specific question, ask it. Best to post your config that isn't working too and any how-to guide links you have followed.  There are lots of them for Ubuntu and wordpress.

---

### Post by SeijiSensei on 2023-07-25
Why do you need different versions of PHP? Have you tested the apps to see if they all work on PHP 8. You'll have a devil of a time trying to use different versions. WP doesn't care about which version of PHP you're using. Do you have other PHP apps tied to specific versions? I'd test them and fix any code imcompabilities, then use PHP 8 for everything.

---

### Post by QIII on 2023-07-25
When is your assignment due?

---

