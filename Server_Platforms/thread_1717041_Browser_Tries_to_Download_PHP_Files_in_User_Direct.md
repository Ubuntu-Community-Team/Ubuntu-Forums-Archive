---
title: "Browser Tries to Download PHP Files in User Directory"
date: 2011-03-29
forum: Server Platforms
---

### Post by rossdub on 2011-03-29
I was having trouble getting php files to display properly on my ubuntu 10.10 LAMP setup.  Everything was installed with defaults and working properly.  testphp.php worked as long as it was in the sites parent directory, but any php files in user directories did not work.  All browsers tried to download the php files located in /home/user/public_html instead.  

I tried to use the help documents here, 
[URL="https://help.ubuntu.com/community/ApacheMySQLPHP"]
https://help.ubuntu.com/community/ApacheMySQLPHP[/URL]

but that didn't help me.  

Finally I was browsing around in the /etc/apache2/mods-available directory and looked at the php5.conf file.  Here is the relevant information from the file:


```
 
# To re-enable php in user directories comment the following lines 
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it 
# prevents .htaccess files from disabling it. 
      
# <IfModule mod_userdir.c> #Comment out this line
    #   <Directory /home/*/public_html> #comment out this line
    #        php_admin_value engine Off #comment out this line
    #    </Directory>  #comment out this line
#</IfModule>  #comment out this line

```

After I commented out the lines indicated above, restarted apache using sudo /etc/init.d/apache2 restart, and cleared my browser cache, everything worked great.  


Hope this helps someone.  I tried to edit the help document linked above but it says not to do so!  I couldn't find a reference for this fix anywhere else, so I decided to post it here.

---

### Post by cariboo on 2011-03-29
Have you got php5 enabled in /etc/Apache2/mods-enabled? if not at the prompt type:

```
sudo a2enmod php5
```

---

### Post by rossdub on 2011-03-29
Yes, php was enabled and working correctly as long as the file was in the site's root directory.  It just didn't work in user directories.  I used the UserDir option to allow [http://mysite.com/~user/index.php](http://mysite.com/~user/index.php) to display the file located at /home/user/public_html/index.php.  

Before I found the fix above, if I had two identical php files, one in /var/www/mysite/index.php and one at /home/user/public_html/index.php, the browser would display the one from /var/www/mysite and try to download the one in the user's home directory.  File permissions were not the issue, so eventually I found the solution above.  Hope that clarifies.

---

### Post by hawk2010 on 2011-03-29
Can you check the file ownership and permissions

---

### Post by rossdub on 2011-03-30
File permissions were set correctly, as I could access non-php (.html, .jpg, etc) from users directories.

---

