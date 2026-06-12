---
title: "echo phpinfo(); showing blank page"
date: 2017-10-28
forum: Server Platforms
---

### Post by aaronjohnaj on 2017-10-28
Hey,

I am learning to be a web developer and so I set up lamp so that I can start learning php. 
This is what I did

1. Installed apache2

2. Installed php7.0

3. edited the /etc/hosts file and added the line 
    [I]127.0.0.1 test.dev
 [/I]
4. made directory using 
    [I]sudo mkdir -p /var/www/test
[/I]
5. changed the permision using[I] 
    sudo chown -R $USER:$USER /var/www/test [/I]
    [I]sudo chmod -R 755 /var/www
[/I]
6. made a file inside test using [I]
    touch /var/www/test/index.php
[/I]
7. opened in sublime and added[I] 
    <?php echo phpinfo(); ?>[/I]    and saved it.

8. then I hooked IP address to actual folder using [I]
    sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/test.dev.conf
 [/I]
9. then edited the test.dev.conf file and added 
    *Server Name test.dev*
    *Server Admin [EMAIL="admin@test.dev"]admin@test.dev[/EMAIL]*
    *Document Root /var/www/test*    and saved the file
 
10. then I enabled the site using 
      [I]sudo a2ensite test.dev.conf
 [/I]
11. then reloaded the apache server. 

but when i type test.dev in browser a blank page appears? why?
any help would be appreciated.

thank you in advance.

---

### Post by SeijiSensei on 2017-10-29
phpinfo() writes its output directly to the screen.  You do not need to use "echo".  Remove the "echo" and see if it works now.  

I prefer to use the "lamp-server" package to install Apache and PHP to insure all the parts are there.  For instance, PHP requires the libapache2-mod-php[5,7] package to be installed as well.  So if things still don't work after removing the "echo" then try:
```
sudo apt-get install lamp-server^
```
The carat ("^") is important. See this for details: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

One other important thing is to learn how to read logs.  PHP errors appear in /var/log/apache2/error.log.  If you get a blank page, take a look there.  In fact I'll often open a Terminal app in another window and run the command

```
tail -f /var/log/apache2/error.log
```

in that window so I can watch the log when I visit the web page.

---

