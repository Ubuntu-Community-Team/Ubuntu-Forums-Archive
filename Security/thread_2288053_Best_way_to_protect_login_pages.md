---
title: "Best way to protect login pages?"
date: 2015-07-24
forum: Security
---

### Post by peter1897 on 2015-07-24
On Ubuntu server if i have different cms installed like, wordpress, forum and so on, what is the best way to protect the login pages from brute force attacks and such?

---

### Post by Habitual on 2015-07-24
[http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress) is a good start.

```
END WordPress
<Files wp-login.php>
order deny,allow
deny from all
allow from <ip0>
Allow from <ip1>
</Files>
RewriteEngine on
...
```
in the appropriate place(s). .htaccess (better in site.conf!)

---

### Post by peter1897 on 2015-07-24
I am looking for universal way to do this for all platforms not just wordpress, so i guess i have to look in .htaccess and see what i can do.

---

### Post by Lars Noodén on 2015-07-25
> **Habitual said:**
> ... (better in site.conf!)

+1

There are a lot of guides that mention .htaccess but they are for those who do not have proper access to the virtual host's configuration file.  So remember that anything that *could* go in .htaccess, according to a tutorial, really ought to go in the configuration file itself.

---

