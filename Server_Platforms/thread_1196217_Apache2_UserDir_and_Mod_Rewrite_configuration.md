---
title: "Apache2 UserDir and Mod_Rewrite configuration"
date: 2009-06-24
forum: Server Platforms
---

### Post by Antimidget on 2009-06-24
```

UserDir public_html
UserDir disabled root
<Directory /home/*/public_html>
    AllowOverride All
    Options FollowSymLinks
</Directory>

```the above code is what i have to configure UserDir, i have rewrite and userdir installed and enabled what i don't know is why the RewriteBase doesn't work for sites that fall under the UserDir filesystem (if thats what i call it)...

example:
.htaccess
```

Options +FollowSymLinks -MultiViews
RewriteEngine On

RewriteRule ^(.*)\.htm$ test.php?p=$1 [L]

```when i run a file by the url 'http://<serverip>/~user/page1.htm' i get a 404 error saying the page can't be found even though its there on the server in the same folder.

my guess is that RewriteBase doesn't work for UserDir Sites, if i add 
```
RewriteBase /
```to my .htaccess file it sends it to the root '/var/www' folder which isn't what i want, and if i add:
```
RewriteBase /home/user/public_html
```or
```
RewriteBase /user/public_html
```i get the same error

anyone know how i can setup UserDir and Mod_rewrite for users sites?

Cheers

---

### Post by Alan Zhao on 2009-07-27
I have the same issue recently when using ZendFramework for PHP development on Ubuntu Server 8.04.

---

### Post by Janoma on 2009-10-05
Same problem here, in Ubuntu and in Oracle Enterprise Linux.

---

### Post by Janoma on 2009-10-05
I think I finally found a solution to this problem. You simply have to change the value of the RewriteBase option to ~username. At least it worked for me.

```
RewriteEngine On
RewriteBase /~username/
```

---

