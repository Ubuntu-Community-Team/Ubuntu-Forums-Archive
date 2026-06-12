---
title: "Set password for single database of phpmyadmin"
date: 2012-03-19
forum: Server Platforms
---

### Post by pavi_elex on 2012-03-19
A php website is uploaded on linux server. The server looks like same as Ubuntu filesystem. Xampp has been installed in /opt and website folder has been copied into htdocs. This is a user account.
Lampp has been restarted using **$ sudo /opt/lampp/lampp start. **
When server's ip address is run into browser, it redirects on xampp index page.
```
Ex- http://xx.xx.xxx.xx is run it reaches on xx.xx.xxx.xx/xampp
```when **[http://xx.xx.xxx.xx/website-directory-name](http://xx.xx.xxx.xx/website-directory-name)** is run, the website is opened.
that is why ** xampp's index.php** has been redirected to **website-directory-name**
so when **[http://xx.xx.xxx.xx/](http://xx.xx.xxx.xx/) **or **[http://xx.xx.xxx.xx/xampp](http://xx.xx.xxx.xx/xampp) **is run, it redirects to  **[http://xx.xx.xxx.xx/website-directory-name](http://xx.xx.xxx.xx/website-directory-name)** & website is opened.

But the problem is anyone can open phpmyadmin using  **[http://xx.xx.xxx.xx/phpmyadmin](http://xx.xx.xxx.xx/phpmyadmin)**

and if I set password for phpmyadmin using .htaccess, this password will be same for other databases of phpmyadmin. Right now there is only one database but this is very big project with unlimited memory. There will be number of databases of uncounted web-projects.
I want to set individual password for each database so even when I will try to open database, it should ask password. Right now i I have set it through privileges option. but it does not ask me password.
i want that it should work like c-panel of hostmonster/hostgator etc.

---

