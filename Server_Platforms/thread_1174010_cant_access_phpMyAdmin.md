---
title: "cant access phpMyAdmin"
date: 2009-05-30
forum: Server Platforms
---

### Post by kapi on 2009-05-30
just installed phpMyAdmin but now none of the usernames or passwords work

can anyone help please?

Thanks

---

### Post by nandemonai on 2009-05-30
> **kapi said:**
> just installed phpMyAdmin but now none of the usernames or passwords work

can anyone help please?

Thanks

MySQL doesn't use your standard Linux users. When you installed MySQL it should have asked you to set a root password. The login will be root and whatever password you set at install of MySQL itself.

Once in phpMyAdmin you can then create new users.

---

### Post by superprash2003 on 2009-05-30
reinstall again and set passwords.. you might have forgotten them , otherwise you should get access

---

### Post by kapi on 2009-05-30
Thanks will try now

---

### Post by kapi on 2009-05-30
Nope sorry no joy here,

is it just the SQL I reinstall or the whole lamp?

Kapi

---

### Post by cariboo on 2009-05-30
You don't have to reinstall anything, all you have to do is reconfigure mysql and set a proper password:

```
sudo dpkg-reconfigure mysql-server-5.0
```

Enter a password when asked.

---

### Post by kapi on 2009-05-31
sorry this doesn't seem to work either, apologies for being a nuisance.

Do you think its better to reinstall SQL?

---

### Post by mcduck on 2009-05-31
> **kapi said:**
> sorry this doesn't seem to work either, apologies for being a nuisance.

Do you think its better to reinstall SQL?

Could you explain a bit more thoroughly *how* it doesn't work? What happens when you run the command cariboo907 suggested?

---

### Post by kapi on 2009-06-01
Hi the reset password function worked ok,

its when I try to log in to phpMyAdmin that nothing happens, I try the ubuntu user name used for signing in to ubuntu and the password that I rest.

Funnily enough I can gain access to MySQL Administrator using 'root' as user name and the new re set password. 

I'm just baffled by the phpMyAdmin login because it doesnt provide feedback like 'incorrect user name or password'

Thanks 

Kapi

---

### Post by mcduck on 2009-06-01
> **kapi said:**
> Hi the reset password function worked ok,

its when I try to log in to phpMyAdmin that nothing happens, I try the ubuntu user name used for signing in to ubuntu and the password that I rest.

Funnily enough I can gain access to MySQL Administrator using 'root' as user name and the new re set password. 

I'm just baffled by the phpMyAdmin login because it doesnt provide feedback like 'incorrect user name or password'

Thanks 

Kapi

user names & passwords for MySQL are not the same as the users on the system itself.

In other words, "root" user on MySQL isn't the same as root user on your computer. The default account for MySQL is root, if you want  to create other users just log int PhpMyAdmin as "root" and then use it to create the additional database users you want.

---

### Post by kapi on 2009-06-01
thanks but thats just my problem - I can't log in, no matter what I enter

---

### Post by kapi on 2009-06-02
no matter what I try I cant gain access to phpmyadmin. I can access mySQL Admin and see the account setting, even reset passwords but for the life of me I can't get the login screen to give me access to phpmyadmin

could someone out there please help

---

### Post by Celauran on 2009-06-02
You've created a user already? What error(s) are you getting from [http://localhost/phpmyadmin?](http://localhost/phpmyadmin?)

---

### Post by kapi on 2009-06-02
not getting any errors at all, I just input the word user name (have a few specified in mySQLadmin) and then the password and when I click go then nothing happens.

---

### Post by Celauran on 2009-06-02
Did you check that you have cookies enabled for localhost (or 127.0.0.1 as the case may be) in your browser?

---

### Post by kapi on 2009-06-02
sorry how do I do that? 

feel rather silly now

---

### Post by kapi on 2009-06-02
actually I've just checked and there seems to be cookies from 127.0.0.1 in the cookies list, I presume thats them accepted OK

---

### Post by unutbu on 2009-06-02
kapi, I noticed that if I install phpmyadmin before installing apache2, then phpmyadmin is not automatically setup right. However, if I install apache2 then phpmyadmin, then phpmyadmin works "out-of-the-box".

So perhaps try uninstalling both phpmyadmin and apache2, and then reinstalling in the "correct" order:
```

sudo apt-get purge phpmyadmin apache2
sudo apt-get install apache2
sudo apt-get install phpmyadmin
```

---

### Post by kapi on 2009-06-02
configured system as suggested but now when I input localhost/phpmyadmin it says cannot be found on server

---

### Post by Celauran on 2009-06-02
What about if you just go to localhost? Is Apache still working at least?

---

### Post by kapi on 2009-06-02
yeah apache2 works fine, I can see the php web pages that I designed all looks well. its just the log in I'm finding a real pain. There is a sym link between the usr file and the www, the SQL works ok because I can access it using the root user name and the password I set.

---

### Post by unutbu on 2009-06-02
Perhaps check that 
```

ls -l /etc/apache2/conf.d/phpmyadmin.conf
```

returns
```

lrwxrwxrwx 1 root root 28 2009-04-10 16:46 /etc/apache2/conf.d/phpmyadmin.conf -> ../../phpmyadmin/apache.conf
```
```

ls -l /etc/phpmyadmin/apache.conf 
```

returns```


-rw-r--r-- 1 root root 983 2008-08-27 20:23 /etc/phpmyadmin/apache.conf

```
and 
```

head /etc/phpmyadmin/apache.conf
```

begins with
```

# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin
```

The last line above, I think, is what makes [http://localhost/phpmyadmin](http://localhost/phpmyadmin) call /usr/share/phpmyadmin/index.php.

---

### Post by kapi on 2009-06-04
have removed apache2, mySQL and php5

Then reinstalled apache2 and went to test it on localhost , now i get nothing failed to connect. What I really want is to install lamp and get phpmyadmin working. 

I've been at this for days, could someone please help

Thankyou

kapi

---

### Post by Celauran on 2009-06-04
Have you confirmed that Apache is running?

---

### Post by kapi on 2009-06-04
typed in apache2 in the console and got this:

apache2: Syntax error on line 52 of /etc/apache2/apache2.conf: Could not open configuration file /etc/phpmyadmin/apache.conf: No such file or directory

---

### Post by Celauran on 2009-06-04
```
sudo vim /etc/apache2/apache2.conf
```

Comment out line 52 (and anything else relating to phpmyadmin), then

```
sudo /etc/init.d/apache2 restart
```

---

### Post by kapi on 2009-06-04
sorry not up to speed with unix commands
 how to you save the corrections?

---

### Post by Celauran on 2009-06-04
Press i to enter insert mode, add # to the beginning of lines as required, press esc to leave insert mode, type :wq to save and quit.

---

### Post by kapi on 2009-06-04
still keep getting message:

 * Restarting web server apache2                                                apache2: Syntax error on line 279 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
             

isn't there a way to simply reinstall a fresh version and over write the older files?

---

### Post by Celauran on 2009-06-04
> **kapi said:**
> 
isn't there a way to simply reinstall a fresh version and over write the older files?

```
sudo aptitude purge apache2
```

Probably easier to just delete /etc/apache2/conf.d/phpmyadmin

---

### Post by kapi on 2009-06-04
you are right! thankyou, 

I take it I should install mySQL then PHP5 then phpmyadmin in that order

---

### Post by Celauran on 2009-06-04
Doesn't sound like you ever uninstalled phpmyadmin. I generally install everything in one fell swoop.

```
sudo aptitude install apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
```

---

### Post by kapi on 2009-06-04
You are fantastic - thanks very much for all your help, you have no idea what a pain it has been

Kapi

---

### Post by kapi on 2009-06-04
thanks very much for all your help,

---

### Post by kapi on 2009-06-05
Have installed phpmyadmin for about the sixth time and stillthe login screen does not respond when I input root as the username and the password.

I get nothing, no incorrect username or password - it just sits there

Many people have had thijs same problem but no one seems to have any answers

could someone - anyone please help

---

### Post by SunnyRabbiera on 2009-06-05
Ubuntu doesnt have a root user by default, it is disabled.
But it can be bypassed with sudo.

---

### Post by kapi on 2009-06-05
to log in to phpmyadmin root is supposed to work, either way any of the usernames and passwords I try don't work

---

### Post by billgoldberg on 2009-06-05
[http://en.kioskea.net/faq/sujet-673-phpmyadmin-access-denied-for-user-roota-localhost](http://en.kioskea.net/faq/sujet-673-phpmyadmin-access-denied-for-user-roota-localhost)

---

### Post by Celauran on 2009-06-05
> **kapi said:**
> to log in to phpmyadmin root is supposed to work, either way any of the usernames and passwords I try don't work

Have you specifically set up the accounts in MySQL? Your regular login credentials won't cut it. You should have been prompted for a root password when you set up MySQL. Try logging in from the command line to make sure you've got the right password.

```
mysql -u root -p
```

Once that works, I recommend setting up a proper user in MySQL.

---

### Post by kapi on 2009-06-05
Celauran, I appreciate your patience. . Right I did as you asked and my password opens mySQL in the command line with no problems, so whats next?

do you think it's something wrong with the phpmyadmin login screen?

---

### Post by cliffdover88 on 2010-12-10
This is the first site when i was trying to search for the solution but there isn't clear here... The problem of this phpmyadmin problem is PHP. I solved it purging php5* files, deleting /etc/php5 and reinstalling all erased packages.

---

