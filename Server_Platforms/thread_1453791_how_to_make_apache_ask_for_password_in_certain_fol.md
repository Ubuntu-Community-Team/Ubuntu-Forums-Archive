---
title: "how to make apache ask for password in certain folders"
date: 2010-04-13
forum: Server Platforms
---

### Post by nerdy_kid on 2010-04-13
ok first off please dont say "go read the man page". I need instructions for newbies 

I basicly want certian folders to deny access to all clients exept those that supply the correct user name and password. I tried following the directions here (for the basic authentication), but its not working.

i have
```

Deny from all
AuthType Basic
AuthName "Please enter username and password"
AuthUserFile /etc/apache2/passwords
Require user guest
Require valid-user

```
in .htaccess in the folder i want to restrict, thats all i know.

(i created the user "guest" with htpasswd -c /etc/apache2/passwords)

 Someone kind enough to help out a confused person like myself?

---

### Post by s_ø on 2010-04-14
Cant see the link you posted. But the apache documentation is a good reference [http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html)

When you have access to the server you dont need to use .htaccess files, so you could put all authorization in the httpd.conf file.

**The httpd.conf way would be to do this.**
Open httpd.conf as root.
```
 sudo nano /etc/apache2/httpd.conf
```Then for each directory you will restrict access to you need a directory directive.
Substitute **/path-to-directory** with the path to the directory you wish to restrict access to.
Substitute **/path-to-password-file** with the path to your password file.
```
<Directory /path-to-directory>
    AuthType Basic
    AuthName "Please enter username and password"
    AuthBasicProvider file
    AuthUserFile /path-to-password-file
    Require valid-user
</Directory>
```Then restart apache and test it.
```
sudo service apache2 restart
```If you want to restrict access to certain users (Admin as an example) replace **Require valid-user** with **Require user Admin**

[B]
The .htaccess way

[/B]Create a .htaccess file in the directory you need to protect.
```
sudo nano /path-to-directory/.htaccess
```Then add the following
```
AuthType Basic
AuthName "Please enter username and password"
AuthBasicProvider file
AuthUserFile /path-to-password-file
Require valid-user
```Then you need to edit the config files and allow .htaccess override
Assuming you use the default site in the apache setup.
```
sudo nano /etc/apache2/sites-available/default
```Then add the following
```
<Directory /path-to-directory-you-need-to-protect>
AllowOverride AuthConfig
</Directory>
```Restart server and test.
```
sudo service apache2 restart
```You can combine the 2 methods if you like

Edit:
If it doesnt work, open the error.log and look for clues there.
```
nano /var/log/apache2/error.log
```

---

### Post by nerdy_kid on 2010-04-14
thank you!  that did the trick :D

---

