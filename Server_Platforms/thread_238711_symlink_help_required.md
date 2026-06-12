---
title: "symlink help required"
date: 2006-08-18
forum: Server Platforms
---

### Post by caffine_fizz on 2006-08-18
hey all,

i have configured apache2 and seem to have the problem that when i type the domain name into the browser the systems default directory is being displayed, after some reading i realised i hadn't created a symlink for the virtual host file.

I'm a little confused about making the symlink between the file i created in /etc/apache2/sites-available/mydomain.com and /etc/apache2/sites-enabled/.

i have read the syntax for it, but would just like some conformation that i have it right?

should i just type:

symlink /etc/apache2/sites-available/mydomain.com /etc/apache2/sites-enabled/mydomain.com

any help apreciated, the linux noob
caffine_fizz

---

### Post by 23meg on 2006-08-18
The command should be *ln -s * instead of *symlink*.

---

### Post by caffine_fizz on 2006-08-18
i just used a2ensite and presto, fixed it up.

but if your still reading will ln -s */dir/file* */dir/file* do the same thing? (just for future reference)

caffine_fizz

---

### Post by huggy77 on 2006-09-06
you might want to add a number prefix to your symlink - the number denotes priority... my enabled directory looks like:

000-default  001-apFtp  002-aerialphotosofnj

---

