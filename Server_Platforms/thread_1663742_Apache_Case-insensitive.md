---
title: "Apache Case-insensitive"
date: 2011-01-10
forum: Server Platforms
---

### Post by PJOS13 on 2011-01-10
Hi, recently I've been migrating my development environment to ubuntu (desktop edition, because this is not a server, is just my computer) and I've been having some problems with apache case-sensitive (I'm an absolute beginner with it).

I want to make apache case-insensitive, but I didn't find a complete and easy to follow solution online more than doing this:

[LIST=1]
[*]From the command line, type sudo su to get root privileges.
[*]nano /etc/apache2/mods-available/speling.conf
[*]Type CheckSpelling on and hit ctrl-x, y to exit and save the file.
[*]type a2enmod and then speling and hit enter.
[*]type /etc/init.d/apache2 reload to reload apache.
[*]Mistype a url to test it.
[/LIST]

I found that here: [http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/](http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/)

It worked for some things but I'm still having a lot of problems with capitalization. Any suggestions? :confused:

Please, help me! I don't wanna go back to windows an ISS. And fixing my file name by hand won't be a solution it will take to long. :(

BTW I'm using ubuntu 10.10 desktop edition 32-bits, and I've not moved any apache configuration more than that described above.

---

### Post by aceofspades686 on 2011-01-10
While I've never delved too far into this subject, I believe that Apache is case sensitive because the operating system is case sensitive.  Sorry I can't be of more help, but this might hopefully get you moving in the right direction.

P.S. As a web developer who sometimes has to work with Windows servers, its worth pointing out that Apache can run on Windows as well, so you can avoid the IIS nastiness altogether

---

### Post by sj1410 on 2011-01-10
what you did was right. this is not 100% workable. you can also think of URL Rewriting Engine, refer to the following URLs

[http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html#RewriteRule](http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html#RewriteRule)

[http://httpd.apache.org/docs/1.3/mod/mod_speling.html](http://httpd.apache.org/docs/1.3/mod/mod_speling.html)

[http://httpd.apache.org/docs/1.3/misc/FAQ-H.html#rewrite-nocase](http://httpd.apache.org/docs/1.3/misc/FAQ-H.html#rewrite-nocase)

---

### Post by PJOS13 on 2011-01-10
> **sj1410 said:**
> what you did was right. this is not 100% workable. you can also think of URL Rewriting Engine, refer to the following URLs

[http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html#RewriteRule](http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html#RewriteRule)

[http://httpd.apache.org/docs/1.3/mod/mod_speling.html](http://httpd.apache.org/docs/1.3/mod/mod_speling.html)

[http://httpd.apache.org/docs/1.3/misc/FAQ-H.html#rewrite-nocase](http://httpd.apache.org/docs/1.3/misc/FAQ-H.html#rewrite-nocase)

How can I configure the rewrite module? Sorry for asking I'm new to apache. :smile:

---

