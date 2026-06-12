---
title: "need help with mysql and php getting errors..."
date: 2007-03-24
forum: Server Platforms
---

### Post by hockey97 on 2007-03-24
Hi I got mysql and php5 installed also apach but in my localhost when I click on html files they open and show in the window of firefox but when I click on mysql or php files I get errors. 
The errors are   Warning: include(database/mysql.php) [function.include]: failed to open stream: No such file or directory in /var/www/ZPanel/database/db.php on line 18

Warning: include() [function.include]: Failed opening 'database/mysql.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/ZPanel/database/db.php on line 18

Fatal error: Call to undefined function mysql_pconnect() in /var/www/ZPanel/database/db.php on line 27   that's from the mysql object it's a database type object in mysql.

here is the php error well it's not a php error thing but I installed myphpadmin it was supposed to be a mysql database type thing also using php scripts for window interface in firefox .. here is the error I get .....

Cannot load mysql extension. Please check your PHP configuration. - Documentation

that's what I get I been working on this for 3 months I really need the help. I tried in other areas asking this in thise fourm place things but got not much response but what I got from people was to reinstall mysql.


I am new to linux and  if their is any steops to be done I really need exact steps like all the commands to put in becuse I don't know all commands ect, I only know is wget command.


Thanks for your time.   :guitar:

---

### Post by conjur3r on 2007-03-25
# sudo apt-get install php5-mysql

After which, restart apache and test.

---

### Post by hockey97 on 2007-03-25
what commands do I use to restart apache??? 

when I install php and mysql do I need to config anything???

---

### Post by hockey97 on 2007-03-25
HI I just reinstalled the stuff and restarted my apache  server and now I get new erros,

here is one of them.

Probably reason of this is that you did not create configuration file. You might want to use setup script to create one.
Error

MySQL said: Documentation
#1045 - Access denied for user 'root'@'localhost' (using password: NO) 

it looks I need to config stuff or at least give public acess or somthing.

here is another one

Warning: include(database/mysql.php) [function.include]: failed to open stream: No such file or directory in /var/www/ZPanel/database/db.php on line 18

Warning: include() [function.include]: Failed opening 'database/mysql.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/ZPanel/database/db.php on line 18

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /var/www/ZPanel/database/db.php on line 27
Access denied for user 'www-data'@'localhost' (using password: NO)

it look's that I have to do some config or reinstallation for zpanel ect, 

but have no clue where to start, I am somewhat intermideiate person with linux spend only like 4 or 5 months' with linux and kinda getting a hang with linux but still I don't know some basic commands like I need the commands to give permissions to the data base in mysql.

thanks for your help....getting excited now becuse I am getting close to done, overall I been working with ubuntu installing it ect for 4 months now and happy that I am getting closer to finish it.

---

### Post by conjur3r on 2007-03-26
> **hockey97 said:**
> what commands do I use to restart apache???

There are many ways to do it but one that I use the most is the following:
# sudo apache2ctl graceful

You could have also used your system init script:
# sudo /etc/init.d/apache2 reload

Run either without the graceful/reload and it'll give you a set of options.

> **hockey97 said:**
> when I install php and mysql do I need to config anything???

I don't remember changing anything apart from setting the default privileged account's password (root) to something other than blank!

Just make sure that you restart apache everytime you change the php configuration.

---

### Post by conjur3r on 2007-03-26
Looks like your problem now is simply mysql authentication.  It also looks like you've changed your priviledged account's (root) password which is probably why you can't log in using root and no password.  Just to confirm, try this at the console:

# mysql -u root

Does it let you right in?  If not, try specifying a password after entering:

# mysql -u root -p

Can't remember it?  No worries, reset it [http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

After you've sorted that out, you'll probably need to create a new mysql user account for zpanel and run through its setup process.

---

### Post by hockey97 on 2007-03-26
I tired the mysql -u  root and I get an error it is ...

root@DemonicProductions:/# mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

but I can get in with mysql -u root -p 

it gives me a password prompt and I can put in a password which I made when installing mysql which I can get in mysql root oinly this way.

---

### Post by conjur3r on 2007-03-27
That's good.  Your mysql sounds operational.  Now try reinstalling your web apps.

---

### Post by hockey97 on 2007-03-28
What do you mean by try reinstalling web apps??? do you mean zpanel???
or should I restart all my service apps like mysql,apache,php,bind9??

---

### Post by matthew.kreh on 2007-04-02
hockey97,

  I'm sure he meant to reinstall zpanel.

  I've never worked with ZPanel before, but I was having similar mysql_pconnect() errors.

  I fixed the errors by creating a mySQL user account specifically for my web-app. 

  Here's what I did.  Maybe it will help ya out.

from the terminal I ran
```

# mysql -u root -p

```
entered my password and created a database for the web-app
```

mysql> Create Database WebAppName

```
Next I created a mysql user for that database
```

mysql>GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP
        ->     ON WebAppName.*
        ->     TO 'WebAppName_admin'@'%'
        ->     IDENTIFIED BY 'admin_pass' WITH GRANT OPTION;

```
Obviously replace "WebAppName" and "admin_pass" with your own information.

This code makes a user "WebAppName_admin" who can connect to the server from anywhere.  If you only need it to access from the local computer (webserver and mysql server are on the same machine) then you can replace the '%' with 'localhost'

Next I uploaded the php web-app to my server and ran it's install.php

Now you shouldn't have the mysql_pconnect() errors anymore.



as far as the other errors you listed, here goes:

```

Warning: include(database/mysql.php) [function.include]: failed to open stream: No such file or directory in /var/www/ZPanel/database/db.php on line 18

Warning: include() [function.include]: Failed opening 'database/mysql.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/ZPanel/database/db.php on line 18

```

Check to make sure that this file exists

/var/www/ZPanel/database/mysql.php

if it does then we will look inside of /var/www/ZPanel/database/db.php to see what is wrong with it's include statement for mysql.php

Hope this helps,
   Matthew Kreh

---

### Post by hockey97 on 2007-04-02
Hi  I found out later about the mysql.php thing it was in a different folder so I put it in the database folder where I guess the db.php file was lookiing for this file ect.

I read the above and I did made a database in mysql and did assing a user to it. 

But what is the code to upload the webapp content into the database???
and what kind of data could I input, becuse in the future I want to create a 3d online game,
option for a game application that runs on your computer ect.

Thanks for your time.

---

### Post by matthew.kreh on 2007-04-03
As for a 3d online game, feel free to open a new forum thread for that topic.  I feel that we should stick with the topic at hand (php and mysql errors) with this threaded discussion though...

So after moving mysql.php you no longer have the function.include() errors, right?  If that's taken care of then the only problem remaining (that I know of) is getting VPanel configured to use your mySQL database.

I do not have experience with VPanel, so in order to help ya out I will have to get VPanel and try installing it on my server. I will let ya know what happens.  

> But what is the code to upload the webapp content into the database???

Typically php code projects have an installation script that takes care of that for you.  Then you use their interface (in your browser) to do the rest, but I'll see how VPanel does it tonight.

  -- Matthew Kreh

---

### Post by matthew.kreh on 2007-04-03
Step by step of how I installed VPanel.  I am following the instructions contained in the Readme.html that was inside of the zip file from Step 1.

1. Downloaded ZPanel-v2.zip

2. (Before Install) edit php.ini  ```
/etc/php5/apache2/php.ini
```
3. (Before Install)Restart server    ( in terminal ) ```
# /etc/init.d/apache restart
```

4. (Install) Unzip or Unrar ZPanel and upload it to your server.
      -- This creates a ZPanel folder within your server
5. (Install) CHMOD the zpanel directory to 777
      -- In terminal, browse to your webserver's root folder and run```
# chmod 777 ZPanel
```
6. (Install) Open and edit zpanel/database/db.php
      --  I don't understand what they want me to edit, so I skipped this step
7. (Install) Create a new database on your MySQL server where you'd like ZPanel to install to
     -- I created a "ZPanel" database with a "ZPanel_admin" user that can access it
8. (Install) Go to [http://yourdomain/zpanel-directory/admin/install.php](http://yourdomain/zpanel-directory/admin/install.php) and it will guide
you through the rest of the installation.

   8a. Step 1 --> Clicked Continue
   8b. Step 2 --> Entered my info and clicked Continue
                   Server        : localhost
                   Username   : ZPanel_admin
                   Password    : ZPanel
                   Database    : ZPanel
   8c. Step 3 --> Entered my info and clicked Continue
         (Note : after clicking continue an alert box popped up stating "all updated")
   8d. Step 4 -->  Entered my system's info and clicked Continue
         (Note : after clicking continue an alert box popped up stating "all updated")
   8e. Step 5 --> Clicked Continue

Next I was redirected to [http://localhost/ZPanel/index.php](http://localhost/ZPanel/index.php) which presented me with a login screen.  I entered my username/password and entered the ZPanel interface.

It worked for me on my end, let me know if you run into any problems.

  -- Matthew Kreh

---

### Post by matthew.kreh on 2007-04-04
Ok....  It did install fine, but it doesn't work 100%.

Apparently ZPanel is made for Windows servers and is being ported to work with Linux at the moment.

From ZPanel's website:
> ZPanel is a hosting control interface developed for both Windows and Linux hosts. We will soon be developing two different distributions to fit the needs of both platforms.

Example : 
  In services.php when I click in the link to restart apache, it calls upon this php code:
     ```
			if ($_GET['cmd'] == 'restartapache') {

			echo exec('c:\services\restartapache.bat');

			echo '<font color=red>'.$lang_serrestarted.'</font>';

			}


```

This works fine on a windows box, but it does nothing on my Ubuntu server.  
And this is just one short-coming, I am sure that there are many more pieces of functionality that are broken (Like the disk space listings).

 Hopefully ZPanel will release a Linux version soon.

  -- Matthew Kreh

---

### Post by hockey97 on 2007-04-04
Hi I got xampp installed and stuff went wrong so I am thinking to delete it also to delete every mysql file on my computer also apache2 ect and going to restart all over. 

So is it possible for me to delete every file related to mysql and apach2, could you give me the code to do such task if I can't do it that way where it would find all mysql related files in my computer becuse I found out I installed more than one mysql server and their is some conflict so I want to delete everything that deals with mysql and apache2.
if their isn't a way then just tell me the code to uninstall the mysql and apache2 server.
Thanks I figured it out and what you said is correct I didn't do the grant code right.

---

