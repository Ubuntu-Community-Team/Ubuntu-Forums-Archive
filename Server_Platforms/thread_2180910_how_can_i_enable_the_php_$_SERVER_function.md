---
title: "how can i enable the php $_SERVER function?"
date: 2013-10-15
forum: Server Platforms
---

### Post by LTs74eR on 2013-10-15
Hello,

i have a ubuntu LAMP server running and i need for SSO the $_SERVER function. I can not find this value in my php configuration (because i need the correct key - REMOTE_USER or AUTH_USER). How can i enable/install this feature?

ubuntu0.12.04.1
Apache/2.2.22
PHP Version 5.3.10


Thanks and best regards,
Steffen

---

### Post by SeijiSensei on 2013-10-15
The $_SERVER[] array is available by default.  You can view its contents by creating a page called "info.php" with the contents:

```
<?php phpinfo() ?>
```

and accessing it from a browser.  

If you want to see the AUTH_USER value, just use "echo $_SERVER['AUTH_USER']".

---

### Post by LTs74eR on 2013-10-15
Hi [COLOR=#000000]SeijiSensei[/COLOR],

thank you very much for the reply. I created a info.php with the contents

<?php phpinfo() ?>

if i access this file i get a lot of informations but i dont find any value called auth_user

You told me that i just use "echo $_SERVER['AUTH_USER']", can you please explain how to use this command?

---

### Post by SeijiSensei on 2013-10-15
The report from the phpinfo() command includes a section called "Apache Environment."  That displays the contents of the $_SERVER array.  However there won't be either a REMOTE_USER or AUTH_USER entry unless you have configured the site to use "HTTP Basic Authentication."  The REMOTE_USER entry will contain the user name entered into the pop-up box triggered by basic authentication.  You can force basic authentication either from [within PHP]("http://php.net/manual/en/features.http-auth.php") or, more commonly, by [Apache directives]("http://httpd.apache.org/docs/2.2/howto/auth.html").

All that said, how much experience do you have with web servers and PHP? If you are just starting out, I'd begin with creating a simple site that uses basic authentication via the Apache directives.  If you put the info.php page into that site, you should see entries for REMOTE_USER and AUTH_USER after you have logged in.

Most sites these days do not use these mechanisms for logging in.  Instead they use "[sessions]("http://php.net/manual/en/features.sessions.php")" and "[cookies]("http://www.php.net/manual/en/features.cookies.php")" to manage users, typically with the log in information stored in a back-end SQL database.  This site handles authentication that way, as do most forums and blogs.  If you have never done anything with PHP or server-side web programming before, I'd start with simple HTTP authentication before diving into session management.

---

