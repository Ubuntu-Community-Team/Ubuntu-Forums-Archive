---
title: "apache php module broken after Hardy upgrade"
date: 2008-05-02
forum: Server Platforms
---

### Post by sp00n on 2008-05-02
I have upgraded from 7.10 Server to 8.04 server via update-manager.

now, if I try to view any pages served by apache, i get:

[HTML]Failed to Connect        

Firefox can't establish a connection to the server at 10.101.101.9:8090.[/HTML]

if I try

```
sudo a2dismod php5
sudo /etc/init.d/apache2 restart
```

and reload in firefox, then I get served the .php file as a download link, so my firewall is not the problem.

My /etc/apache2/mods-available/php5.conf looks like this:

```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```

does anybody know how to fix this?

---

### Post by sp00n on 2008-05-02
solved.

had to purge apache / php, delete the etc/apache2 and etc/php5 dirs, and reinstall from scratch.

---

### Post by yee379 on 2008-07-10
hi,

i'm having the same problem :( could you provide step by step details of how you managed to solve it please?

thanks,

---

