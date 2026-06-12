---
title: "Password protecting a file - problem"
date: 2008-10-12
forum: Server Platforms
---

### Post by R.Bucky on 2008-10-12
I am attempting to password protect a php page on my server. I added the following code to my httpd.conf file and created a password file. No problem.

[HTML]<Files filename.php>
    AuthType Basic
    AuthName "Protected Access"
    AuthUserFile /var/www/access/htpasswd
    Require valid-user
</Files>[/HTML]

The password dialog box pops up when I access my page, type in the password, and the dialog box comes back. Any ideas why I this is not letting me in?

My stats: Hosting my own web pages using Apache2, Ubuntu7.10, php5, mysql ( a standard LAMP)

---

### Post by bluefrog on 2008-10-12
try
[CODE]
<Files filename.php>
    AuthType Basic
    AuthName "Protected Access"
    AuthUserFile /var/www/access/htpasswd
<Limit GET>
    Require valid-user
</Limit>
</Files>

---

### Post by lykwydchykyn on 2008-10-12
Checkout /var/log/apache2/error.log.  It usually gives a pretty explicit error about why login fails.

---

