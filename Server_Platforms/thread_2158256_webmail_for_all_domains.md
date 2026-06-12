---
title: "/webmail for all domains"
date: 2013-06-28
forum: Server Platforms
---

### Post by tiagoev on 2013-06-28
[COLOR=#333333][FONT=Helvetica Neue]I have apache installed on Debian 7 and would like webmail in all areas of my VPS, when a field visit [www.yourdomain.com/webmail](www.yourdomain.com/webmail) goes to the webmail software that is installed in /var/www/webmail/[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]How can I do this? I have to put in the vhost file for each domain?[/FONT][/COLOR]

---

### Post by SeijiSensei on 2013-06-28
There are a variety of methods for this if you are using Apache.  You can add an "alias" directive to each domain that points to the common mailserver software:

```

<VirtualHost *:80>
ServerName www.domain1.name
Alias /webmail /var/www/webmail
[stuff]
</VirtualHost>

<VirtualHost *:80>
ServerName www.domain2.name
Alias /webmail /var/www/webmail
[stuff]
</VirtualHost>

```

Handling outbound addressing in this setting can be tricky.  In SquirrelMail, for instance, you'll need to use its personalization features so each person sends mail with the proper user@domain.  Without this you can end up with everyone having "From: [email]user@yourdomain.com[/email]" addresses rather than "From: [email]user@herdomain.com[/email]".

If you have some experience with PHP (I'm guessing that is what the webmail software is written in), you could design a custom login page where the person enters [email]user@domain.name[/email] and a password.  You would then parse the domain from the login address and proceed accordingly.

---

### Post by tiagoev on 2013-06-28
Was putting a file in the directory webmail.conf /etc/apache2/conf.d/


With the following content:


Alias &#8203;&#8203;/webmail  /var/www/webmail/


<Directory "/var/www/webmail/">
Options Indexes FollowSimlinks
AllowOverride None
Order allow, deny
Allow from all
AddDefaultCharset off
</ Directory>


This recognizes the way I want, but this appears "No input file specified.".


I'm doing it right? How can I fix this error?

---

### Post by SeijiSensei on 2013-06-28
FollowS**y**mLinks is misspelled.

Also your first stop in debugging is to check /var/log/apache2/error.log.

---

### Post by tiagoev on 2013-06-28
No error on the case.


[Fri Jun 28 15:26:13 2013] [notice] caught SIGTERM, shutting down
[Fri Jun 28 15:26:14 2013] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Fri Jun 28 15:26:14 2013] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Fri Jun 28 15:26:14 2013] [notice] Digest: generating secret for digest authentication ...
[Fri Jun 28 15:26:14 2013] [notice] Digest: done
[Fri Jun 28 15:26:14 2013] [notice] FastCGI: process manager initialized (pid 18721)
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Fri Jun 28 15:26:14 2013] [error] python_init: Python version mismatch, expected '2.7.2+', found '2.7.3'.
[Fri Jun 28 15:26:14 2013] [error] python_init: Python executable found '/usr/bin/python'.
[Fri Jun 28 15:26:14 2013] [error] python_init: Python path being used '/usr/lib/python2.7/:/usr/lib/python2.7/plat-linux2:/usr/lib/python2.7/lib-tk:/$
[Fri Jun 28 15:26:14 2013] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Fri Jun 28 15:26:14 2013] [notice] mod_python: using mutex_directory /tmp
[Fri Jun 28 15:26:14 2013] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Fri Jun 28 15:26:14 2013] [notice] Apache/2.2.22 (Debian) DAV/2 mod_fastcgi/mod_fastcgi-SNAP-0910052141 mod_fcgid/2.3.6 PHP/5.4.4-14+deb7u2 mod_pytho$

---

### Post by SeijiSensei on 2013-06-28
You might see whether [one of these solutions](https://www.google.com/search?client=ubuntu&channel=fs&q=No+input+file+specified&ie=utf-8&oe=utf-8) helps.

---

