---
title: "Problem with virtualhosts and ssl"
date: 2012-02-24
forum: Server Platforms
---

### Post by mdmerajali on 2012-02-24
Dear All,
I just started configuring **mod_ssl**; all went fine BUT then I faced this warning when I restarted **apache2**  saying: **[warn] _default_ VirtualHost overlap on port 80, the first has precedence**. So I re-checked my steps for mod_ssl cofiguration as follows inorder to make my apache2 listen to port 80 but redirects to 443 (i.e SSL only)

1. sudo a2enmod ssl
2. sudo a2ensite default-ssl
3. sudo /etc/init.d/apache2 restart
4. I kept **ports.conf** as it is (i.e **NameVirtualHost *:80 **and** Listen 80)**
**5. **I added in **httpd.conf** the following lines:  
[INDENT][LEFT]<IfModule mod_ssl.c> 
<VirtualHost *:80> 
        ServerName xyz.org 
        Redirect / [https://xyz.org](https://xyz.org)
</VirtualHost>
</IfModule>

[/LEFT]
[/INDENT][LEFT][LEFT]6. Then I added the following two lines (see** highlighted **text below) in **defaut-ssl** of **sites-available** which then automatically updates **default-ssl **of **sites-enabled**.
[INDENT]<IfModule mod_ssl.c>
<VirtualHost _default_:443>
ServerAdmin [email]admin@xyz.org[/email]
**ServerName xyz.org **
**ServerAlias xyz.org**

[/INDENT][LEFT]7. Finally I restarted my apache2 webserver; happy to see no errors or warns. 
8.Checked whether the redirection of non SSL traffic is diverted towards SSL(443) or not.
9. Found to be working fine.
10. That's it!-No messing around. Hope that this will help others ease their task.

[CENTER]Thanks to the **members of UBUNTU forum** for posting all the material required.
[/CENTER]

[/LEFT]

[/LEFT]
[/LEFT]

---

