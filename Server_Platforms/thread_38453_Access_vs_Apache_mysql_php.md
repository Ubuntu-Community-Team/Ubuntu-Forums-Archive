---
title: "Access vs Apache mysql php"
date: 2005-05-31
forum: Server Platforms
---

### Post by ensenadaubuntulover on 2005-05-31
I hear a lot around here of the benefits of linux against windows ( a lot is an understatement) so far I have managed my office (law firm) for years now with windows access and all people around the office is happy with the results. Except me, because I use access 97 and make my oun distributions but with the new access it came interlaced with vba and made my life hard so we stayed with the 97 version ( not to mention the prices of the new programs that did exactly the same) so I want to change because the new operative sistems even if they are for microsoft are not going to run my application ( that is the way windoze works) so BRIGHT IDEA!!! :) USE LINUX
a) more robust
b) more secure
c) less costly
d) you can make aplications plataform independent (with its servers) so any machine I buy in the future or even old ones will work.
E) BECAUSE I LIKE IT

but...

Bad as it will may be, Access is still working and making my bread and butter.

MySQL looks promising but I am finding it very very hard to manage because of this password thing that UBUNTU makes it harder with its sudo scheme.

so out in my nightmare I am writing this and hoping I find a voice in the darknes that shows me the light.

I have tried XAMMP it works wonderful but if you try to do something by yourself it is hard.

and in UBUNTU if you make more secure as they recomned

/opt/lammp/lammp security 

and put passwords you will find that it becomes so secure that nobody can enter to the pages not even sudo or anything so what will you recomend?

 :???:

---

### Post by thrift on 2005-05-31
I'd recommend not to use Ubuntu for this type of server.  Look into a distrobution that is expecting people without a huge amount of Linux experience to be able to set up enterprise level services without knowing all the guts and internals.

Try SuSe.  For the services you are talking about SuSe makes life very easy.
RedHat would also be a good one.

If you have the time to become more familiar with these services I'd say try out Debian or Slackware for the server.

---

### Post by Moobert on 2005-05-31
the newer openoffice is adding a databae program:

[http://www.openoffice.org/product2/base.html](http://www.openoffice.org/product2/base.html)

a for mysql and php... check out phpMYadmin

[http://www.phpmyadmin.net/](http://www.phpmyadmin.net/)

.htaccess files are the things for secuiring apache... also good firewall rules.

[http://httpd.apache.org/docs/howto/htaccess.html](http://httpd.apache.org/docs/howto/htaccess.html)

---

### Post by jdonnell on 2005-05-31
[QUOTE=ensenadaubuntulover]
MySQL looks promising but I am finding it very very hard to manage because of this password thing that UBUNTU makes it harder with its sudo scheme.
[/quote]

Can you be more specific? I'm not sure what your talking about.

> 
I have tried XAMMP it works wonderful but if you try to do something by yourself it is hard.


I've never used xammp, but I don't find it too hard to install apache, php, and mysql on ubuntu. I'm sure we can help you get it up and running.

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=ensenadaubuntulover]Except me, because I use access 97 and make my oun distributions but with the new access it came interlaced with vba and made my life hard so we stayed with the 97 version[/quote]What are you talking about?  97 has tons of VBA support.  It's quite useful, too.

> so I want to change because the new operative sistems even if they are for microsoft are not going to run my application ( that is the way windoze works)If you have an Access database that's dependent on anything but the version of Access (and a backend store if you're using one), you're probably doing something wrong.

> a) more robust
b) more secure
c) less costly
d) you can make aplications plataform independent (with its servers) so any machine I buy in the future or even old ones will work.None of these are true in the hands of less than fully competent administrators and developers.


> MySQL looks promising but I am finding it very very hard to manage because of this password thing that UBUNTU makes it harder with its sudo scheme.MySQL accounts and passwords are completely unrelated from system accounts passwords.  This is a difficult concept to understand, but fundamental.

If you're having issues with getting into MySQL, it's simply PEBKAC.  Your account on the system means absolutely nothing but the default account to try to connect as.  That's it.  Every MySQL command supports overriding the username you connect as.  Use the -u option to change the account.  

Lots of guides will tell you have to be root to do such and such, but for most MySQL related stuff that's not starting/stopping services or editing configuration files, that's simply not true.  If you see something like this, ask and someone will hopefully tell you the proper way.  Sadly, there's a lot of misinformation out there about the right way to do things with MySQL.

---

### Post by jdonnell on 2005-05-31
[QUOTE=LordHunter317]
None of these are true in the hands of less than fully competent administrators and developers.
[/QUOTE]

I think linux in the hands of a less than competent admin is more secure than windows in the hands of a less than competent admin :) Simply keeping the system updated is the most important thing and this is easier and cheaper on ubuntu than windows.

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=jdonnell]I think linux in the hands of a less than competent admin is more secure than windows in the hands of a less than competent admin :)[/quote]I used to believe that, but I really don't believe that's true anymore.  Linux is more complicated than it was some time ago and Window's security record is getting better.

>  Simply keeping the system updated is the most important thingThis is simply not the case on any platform.  It's an integral part, but if it were that easy, then everyone would turn on autoupdate and every box would be secure.

---

### Post by ensenadaubuntulover on 2005-06-01
I've never used xammp, but I don't find it too hard to install apache, php, and mysql on ubuntu. I'm sure we can help you get it up and running.[/QUOTE]

ok apache mysql php installed

putting a file in /var/www an be watched in 127.0.0.1 and in other machines using this machine adress ( hence I assume its working)

next I would test php and mysql to see if it is ok

$  mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4 to server version: 4.0.23_Debian-3ubuntu2-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>


looks like mysql works

---

### Post by tncmmngs on 2005-06-01
See these links for a good general discussion of the pros and cons of Access versus a client/server SQL solution. 

Access does have limitations, but it might be acceptable depending upon your needs and environment.

[http://www.expresstechnology.com/TechBulletins/SQLCompare.htm](http://www.expresstechnology.com/TechBulletins/SQLCompare.htm)

[http://support.microsoft.com/default.aspx?scid=kb;en-us;889588](http://support.microsoft.com/default.aspx?scid=kb;en-us;889588)

---

### Post by jdonnell on 2005-06-01
[QUOTE=LordHunter317]I used to believe that, but I really don't believe that's true anymore.  Linux is more complicated than it was some time ago and Window's security record is getting better.[/quote]

Windows compels users to run as the administrator. This is inherently less secure, and is just one example of why windows is less secure. Everyone in my family has spyware and virus problems except my grandmother. She has a Mac and the rest have windows. She also uses her computer more than the rest of them. 

I know this is anecdotal, but I've seen it over and over again. I've had two windows servers hacked, but none of our linux servers have been hacked and we don't even keep up with the latest patches on the linux servers.


Simply keeping the system updated is the most important thing
> This is simply not the case on any platform.  It's an integral part, but if it were that easy, then everyone would turn on autoupdate and every box would be secure.

It's not? What is the most important thing then? I think you misread my statement.
I said nothing is more important than keeping up with security patches. I did not say that this is all one needs to do. Let's be honest though, this is all a typical user is going to do and they really shouldn't have to do more. A person shouldn't need to be an expert to use a computer safely.

---

### Post by LordHunter317 on 2005-06-01
[QUOTE=jdonnell]Windows compels users to run as the administrator. This is inherently less secure, and is just one example of why windows is less secure. Everyone in my family has spyware and virus problems except my grandmother. She has a Mac and the rest have windows. She also uses her computer more than the rest of them. 

I know this is anecdotal,[/quote]It's also invalid.  You're making a comparion about Windows on the desktop to  Windows on the server.   It's not valid.  

> It's not? What is the most important thing then?Everything is equally important.  There is no magic bullet, and I'm not of the mind that one thing is more important than anything else anymore.  You ought to being doing everything that's economically fesible (ignoring other requirements) to secure your machines.  Which almost assuredly means more than staying up-to-date with security patches.

> I think you misread my statement.
I said nothing is more important than keeping up with security patches.No, I understood it just fine.  I don't believe that it is true.  It's an integral part, but it's not the most important thing.   Everything is of equal importance on a server in my mind. 

> I did not say that this is all one needs to do. Let's be honest though, this is all a typical user is going to do and they really shouldn't have to do more. A person shouldn't need to be an expert to use a computer safely.You're making apples to oranges again. On a desktop or home machine, I'm generally inclined to agree with you.  On a server, the administrator ought to be a professional.  That means that the expectation that they are an expert is reasonable.  As is the expectation that they will do more than just run the autoupdate service.  Now, once could say in an ideal world that would be all that's needed, and perhaps they'd be right, but that's not the reality of the situation.

---

### Post by ensenadaubuntulover on 2005-06-01
[QUOTE=jdonnell]Can you be more specific? I'm not sure what your talking about.



I've never used xammp, but I don't find it too hard to install apache, php, and mysql on ubuntu. I'm sure we can help you get it up and running.[/QUOTE]

installed apache 2 and mysql and php but cannot read .php documents (example from php.net tutorial)

<html>
 <head>
  <title>PHP Test</title>
 </head>
 <body>
 <?php echo '<p>Hello World</p>'; ?>
</body>
</html>

named hello.php

but firefox or konkeror said if I want to download or use some aplication

---

### Post by jdonnell on 2005-06-01
[QUOTE=LordHunter317]
No, I understood it just fine.  I don't believe that it is true.  It's an integral part, but it's not the most important thing.   Everything is of equal importance on a server in my mind. 
[/QUOTE]

Reading through log files is part of good system security, but it's not nearly as important as staying current with the latest security patches. I know what your saying though. Keeping your system patched won't make a difference if your root password is 12345  [-X

---

### Post by ensenadaubuntulover on 2005-06-01
hwen I posted this thread was on the idea that I could get some help but it went into a discussion of what is better it seems to me that is a matter of preferences.

the idea here is how to make UBUNTU work with apache mysql and php

why?

because there are many many people in the wold who actualy work on old machines and could not depend on Mr. Gates economic scheme and because (I think at least) 
THIS IS AN UBUNTU FORUM

correct me if I am wrong

I am still at a loss on how to make thing work

I used kinaptic because the ease of use and works beautifully for us linux/debian non experts

chose apache dowloaded ok chose mysql but have many options so chose server and client but it seems to work

(still some issues with passwords)

chose php it says 4 is most recent (I know it is 5 but i am talking kinaptic here)

and installed ok but i can not manage to make things work

thanks for your concern everybody anyway I apreciate.

LETS MAKE UBUNTU RULE!!!

---

### Post by jdonnell on 2005-06-02
[QUOTE=ensenadaubuntulover]installed apache 2 and mysql and php but cannot read .php documents (example from php.net tutorial)
but firefox or konkeror said if I want to download or use some aplication[/QUOTE]

I'm going to assume you installed them with apt-get. It won't work this way if you didn't

run this command
> ls /etc/apache2/mods-enabled/
You shouled see php4.conf and php4.load is that directory. 

If not then run
> 
sudo ln -s /etc/apache2/mods-available/php4.load /etc/apache2/mods-enabled/php4.load
sudo ln -s /etc/apache2/mods-available/php4.conf /etc/apache2/mods-enabled/php4.conf


Now you need to restart apache
> 
sudo /usr/sbin/apache2ctl restart


---

### Post by LordHunter317 on 2005-06-02
[QUOTE=jdonnell]I'm going to assume you installed them with apt-get. It won't work this way if you didn't

run this command

You shouled see php4.conf and php4.load is that directory. 

If not then run


Now you need to restart apache[/QUOTE]
 Instead of running those nasty ln commands, you should just use:```
sudo a2enmod php4
```instead.

---

### Post by jdonnell on 2005-06-02
I always forget about that command :) 

Btw, I really like the way ubuntu/debian do the apache confs. I use suse and redhat and I like it much better than those two.

---

### Post by ensenadaubuntulover on 2005-06-02
[QUOTE=jdonnell]I always forget about that command :) 

Btw, I really like the way ubuntu/debian do the apache confs. I use suse and redhat and I like it much better than those two.[/QUOTE]

first of all a big THANK YOU for your response.

so far I have managed to install apache2 mysql and php and all are working ok

I can put some web pages (HTML) and I can see them
did some test with .php (which were very difficult because I was missing a module 

libapache2-mod-php4.[B]

that Mr. rostved (ubuntu php forum) gracefully pointed me and everithing worked

now here comes the biggie

[COLOR=Red]how to create a usr in mysql who has permissions to create a database and tables in it?[/COLOR]

it has something to do with GRANT so I need to do some more homework but your help will be greatly apreciated.

---

### Post by jdonnell on 2005-06-02
This should help
[http://dev.mysql.com/doc/mysql/en/grant.html](http://dev.mysql.com/doc/mysql/en/grant.html)

---

### Post by GrumpySimon on 2005-06-03
[QUOTE=ensenadaubuntulover]it has something to do with GRANT so I need to do some more homework but your help will be greatly apreciated.[/QUOTE]

Yep. There are a number of privileges you can give the users, each has a different function. For example. SELECT allows the user to (surprise!) select stuff. The link jdonnell posted will give more information, but what you're after is something like:

```

GRANT SELECT, INSERT, UPDATE, DELETE, CREATE ON *.* TO `username`@`localhost` IDENTIFIED BY 'password';
FLUSH PRIVILEGES;

```

(We need to flush the privilege tables after the changes to make them happen).

You can replace the *.* with databasename.* if you want to lock it down to databasename only. 

You can even go crazy and make another root (superuser) account by using GRANT ALL ON... etc (not really a good idea).

--Simon

---

### Post by LordHunter317 on 2005-06-03
[QUOTE=GrumpySimon](We need to flush the privilege tables after the changes to make them happen).[/quote]Actually, you don't.  You only need to do that if you alter the tables directly.  GRANT implictly does a FLUSH PRIVILEGES.

> You can replace the *.* with databasename.* if you want to lock it down to databasename only. Which is a **really** good idea, unless you're creating like a global backup account or something.

---

### Post by deuce868 on 2005-06-03
You can also use phpmyadmin to help work with the permissions.

Personally once I install the various LAMP components I pull up phpmyadmin set a root password through it and then use that from then on for interfacing with the mysql server. (unless I need to do something like setup a slave server obviously)

You'll find that this setup is much nicer than an ASP interface built over an access database. I started out the Access route and always had syncing troubles because I would have to take down the access database from the server in order to modify the database at all (create a new table or alter the field limitations). Using mysql as a server with php as the front end has been a extremely flexible solution.

---

### Post by GrumpySimon on 2005-06-03
[QUOTE=LordHunter317]Actually, you don't.  You only need to do that if you alter the tables directly.  GRANT implictly does a FLUSH PRIVILEGES.[/QUOTE]

True, but I figure it's good practice to get into the habit of flushing privileges after grant table changes - I forget how many times I've seen people ask why their grant changes didn't work because they just didn't flush.

[QUOTE=LordHunter317]
Which is a **really** good idea, unless you're creating like a global backup account or something.[/QUOTE]

Amen. IMHO it's best to go with one power user per database, and one user ('mysql') who can only SELECT.

--Simon

---

### Post by LordHunter317 on 2005-06-03
[QUOTE=GrumpySimon]True, but I figure it's good practice to get into the habit of flushing privileges after grant table changes - I forget how many times I've seen people ask why their grant changes didn't work because they just didn't flush.[/quote]This doesn't make any sense.  IF you run GRANT, you don't need to do FLUSH PRIVILEGES.  Period.  If it doesn't work after running GRANT directly, something else is wrong (likely, you b0rked the syntax).

You only need the FLUSH PRIVILEGES if you modify the permissions table directly.

> Amen. IMHO it's best to go with one power user per database, and one user ('mysql') who can only SELECT.Actually no, this isn't the best policy.  It's rarely the best policy.

---

### Post by ensenadaubuntulover on 2005-06-03
[QUOTE=jdonnell]This should help
[http://dev.mysql.com/doc/mysql/en/grant.html](http://dev.mysql.com/doc/mysql/en/grant.html)[/QUOTE]

thanks for your pointer.

this is page 789 from the manual so I think I still have a [COLOR=Red]huge[/COLOR] homework in fron of me!!!

this mysql is proving to be a difficult beast to tame but I still have some determination to understand it but the peaople who created this were determined to be used by very few people.

because for using it you have to start in the middle of the manual and then backwards.

logical (acording to me)

[COLOR=Red]STEP BY STEP[/COLOR]

1) Download/Install MySQL

2) NAME A SUPERUSER (or root user or main or whatever)

3) create a user (THE ONE WHO ACTUALY CAN WORK ON A DATABASE)

4) create a database

5) populate the database with table(s)

6) use php to insert data easy on said tables

7) querry the tables

9) make a report of those querrys

so I I am in step 1 and MAYBE if I figure out step 2 I could be on my way.

---

### Post by LordHunter317 on 2005-06-04
[QUOTE=ensenadaubuntulover]2) NAME A SUPERUSER (or root user or main or whatever)[/quote]You can't do this.  The DB superuser is always called root.  That's the default.  I'm not even sure it really can be changed short of dicking with the permissions tables directly, and it's not a good idea.

> 3) create a user (THE ONE WHO ACTUALY CAN WORK ON A DATABASE)

4) create a databaseWith MySQL, you create the DB first (as the superuser), then create and grant a user permissions to use it, as needed.  Most non-development installations will end up having a user with only the permissions needed to run the application using the database.  It's rare that anyone besides the superuser will have extensive permissions, assuming the application is properly designed.  Most applications only need SELECT,UPDATE,INSERT,DELETE permissions, if that.

> so I I am in step 1 and MAYBE if I figure out step 2 I could be on my way.Your step 2 being impossible is part of your problems.  Reading the the offical documention carefully would help you immensely.

---

### Post by jdonnell on 2005-06-04
[QUOTE=LordHunter317]You can't do this.  The DB superuser is always called root.  [/QUOTE]

This is simply wrong. You can call the superuser whatever you want. All the dedicated servers I've gotten are setup with a superuser called 'admin'. This may be a plesk thing, I"m not sure, but I actually like it better because people that are just learning linux and mysql get confused when root is the name for both the system account and the database account. They often think they are the same account.

---

### Post by jdonnell on 2005-06-04
[QUOTE=ensenadaubuntulover]
this is page 789 from the manual so I think I still have a [COLOR=Red]huge[/COLOR] homework in fron of me!!!
[/QUOTE]

MySql is actually very easy to learn, but that manual is horrible. I'd recommend getting a short book and learn from it. I used [MySQL: Visual QuickStart Guide](http://www.amazon.com/exec/obidos/tg/detail/-/0321127315/qid=1117858221/sr=8-4/ref=pd_csp_4/102-2790373-6894527?v=glance&s=books&n=507846). This will get you up and running with the basics. After that you can use the internet for the detailed information. 

Btw, feel free to ask any questions you have. I'm more than happy to help if I know the answer. You really only need to know how to 
1. Administration
-login/logout 'mysql -u username -p' 
-create users 'from the mysql prompt:'
```
grant select, insert, update, delete on databaseName.* to username@localhost identified by 'password';
```
-make backups 'from the linux shell' 
```
mysqldump -u root -p databasename > fileName.sql
```
2. queries
- creating databases and tables (these are longer so ask if you can't find it)
- inserting data ```
insert into tableName (field1, field2, ...) values (value1, value2, ....)
```
- selecting data ```
select * from tableName [optional parameters]
```

---

### Post by LordHunter317 on 2005-06-04
[QUOTE=jdonnell]This is simply wrong.[/quote]Yes, I verified that it is possible to rename the root account and it works fine.  However, the default installed account is still root, and there's not much point to changing it.

>  but I actually like it better because people that are just learning linux and mysql get confused when root is the name for both the system account and the database account.I don't think my opinion on that line of thinking needs to be stated.

---

### Post by GrumpySimon on 2005-06-04
[QUOTE=LordHunter317]This doesn't make any sense.  IF you run GRANT, you don't need to do FLUSH PRIVILEGES.  Period.  If it doesn't work after running GRANT directly, something else is wrong (likely, you b0rked the syntax).

You only need the FLUSH PRIVILEGES if you modify the permissions table directly.
[/QUOTE]

As I said, I've seen many people (>20) who've done something with the privilege tables (directly or not), which didn't work. All of these were fixed with flush privileges. The extra 15 or so characters you have to type is hardly strenuous.

[quote=LordHunter317]
Actually no, this isn't the best policy.  It's rarely the best policy.
[/quote]

What? By poweruser I mean someone with SELECT, INSERT, UPDATE & DELETE. Why isn't it a good idea to lock them into one database? You can go with less & that's fine - you want the least privileges given. What would you do? To state that this isn't the best policy is rather moot when you don't propose one yourself, right? 

However, this is getting off topic, but if you want to discuss this we can make a new thread.

[quote=LordHunter317]
You can't do this. The DB superuser is always called root. That's the default. I'm not even sure it really can be changed short of dicking with the permissions tables directly, and it's not a good idea.
[/quote]

Dick free solution: GRANT SUPER ON *.* TO 'simon' IDENTIFIED BY....

or directly: UPDATE mysql.user SET user = 'simon' WHERE user = 'root';

Edit: changing the name of the 'root' account is [recommended](http://www.onlamp.com/pub/a/onlamp/2002/07/11/MySQLtips.html) as cheap protection against brute force attacks.

Edit2: ensenadaubuntulover - I recommend looking at [SQLCourse.com](www.sqlcourse.com). It's a free 10 minute or so interactive walk through of some basic SQL. 

--Simon

---

### Post by LordHunter317 on 2005-06-04
> **jdonnell]MySql is actually very easy to learn, but that manual is horrible.[/quote]Actually the manual is a reasonably excellent and authorative reference.  No worse than any other F/OSS proejct out there.

The problem is that it's not an awesome tutorial.   I don't know any. 

[quote]```
grant select, insert, update, delete on databaseName.* to username@localhost identified by 'password' said:**
> Noting of course, that if either the username or hostname has any special character in it, they must be in the form:```
'username'@'hostname'
```nothing the seperate set of single quotes for each.

[quote]-make backups 'from the linux shell' 
```
mysqldump -u root -p databasename > fileName.sql
```This won't take a proper, consistent backup on any MySQL version besides 4.1 and even on 4.1, it may not take a consistent backup in all situation.

Now you see why there are no good tutorials: doing things the right way on MySQL is uncessarily complicated.

---

### Post by LordHunter317 on 2005-06-04
[QUOTE=GrumpySimon]The extra 15 or so characters you have to type is hardly strenuous.[/quote]But it's pointless, and it's pointless advice.  If you run GRANT and it didn't work, something else is wrong.  You're simply telling people bad advice.



> What? By poweruser I mean someone with SELECT, INSERT, UPDATE & DELETE.That's not a poweruser.  CRUD isn't power using.  That's just about standard permissions required to do any work.

Full/Power permissions means the ability to DROP, CREATE, and ALTER entities as well.  Really, it means GRANT ALL PRIVELEGES in this specific case, but that's a digression.

>  Why isn't it a good idea to lock them into one database?It is You can go with less & that's fine - you want the least privileges given. 

> What would you do? To state that this isn't the best policy is rather moot when you don't propose one yourself, right? Generally, a single root account for adminsitration, and one account per application with the most limited permissions possible, on a production server.   There's generally little need for more on MySQL.  Possibly a backup account with system-wide read permissions, but I've never had the need.  If you were backing up remotely, that would probably be worthwhile.  

Development servers typically have human-accessible accounts with wider permissions on a per-database basis.  How wide is situationally dependent.

> Edit: changing the name of the 'root' account is [recommended](http://www.onlamp.com/pub/a/onlamp/2002/07/11/MySQLtips.html) as cheap protection against brute force attacks.Which is also bad advice, for other reasons.  It won't make the attacks go away, and it won't make you immune to them in the long run.  It'll just make the attackers try harder.

The only proper defense against brute force password attacks of that form is proper paswords.  End of story.  IMO, bothering with other defenses is just a waste of time.

---

### Post by ensenadaubuntulover on 2005-06-04
[QUOTE=jdonnell]This is simply wrong. You can call the superuser whatever you want. All the dedicated servers I've gotten are setup with a superuser called 'admin'. This may be a plesk thing, I"m not sure, but I actually like it better because people that are just learning linux and mysql get confused when root is the name for both the system account and the database account. They often think they are the same account.[/QUOTE]

You are geting my point!
[COLOR=Red]
STEP BY STEP[/COLOR]

INSTALL (ok)

sudo /usr/bin/mysql_install_db
(from the manual
then 

CREATE the main person (root or what ever is you like to call it MASTER OF EVERYBODY)

MySQL uses this and is _diferent_ from the root of the machine  :) 

so we have to do this...

/usr/bin/mysqladmin -u root password 'yourfavorite password'

also...

sudo /usr/bin/mysqladmin -u root -h machinename password 'favoritepasswordformachine'

and with this you are able to use [COLOR=Green]phpmyadmin[/COLOR]

which is very helpful tool!!! :) 

now you can create a DATABASE

mysql> CREATE DATABASE firstbase

now the user business...

GRANT ALL ON firstbase.* TO _dauser_@localhost;

and quit

now _dauser_

can log on phpmyadmin and create tables more easyly in firstbase!!! :)  :)  :) 

so far I have got there

about the manual

IS VERY COMPLETE but

looks like the mesenger drop it at the subway station in its way to the printers and got help to pick it up by the people around him and the printers thougt that was the order.

---

### Post by GrumpySimon on 2005-06-05
[QUOTE=LordHunter317]
It is You can go with less & that's fine - you want the least privileges given. 
[/quote]

Of course.

[QUOTE=LordHunter317]
Generally, a single root account for adminsitration, and one account per application with the most limited permissions possible, on a production server.   There's generally little need for more on MySQL.  Possibly a backup account with system-wide read permissions, but I've never had the need.  If you were backing up remotely, that would probably be worthwhile.  [/quote]

I believe that's basically what I said - one 'power user' (you disagree with terminology, fine, but say "user with enough privileges for the application"), per database. Each application has it's own database & account. One system admin account.

[quote=LordHunter317]
Which is also bad advice, for other reasons.  It won't make the attacks go away, and it won't make you immune to them in the long run.  It'll just make the attackers try harder.[/quote]

I did say "cheap security" not "excellent security", or "the best way to secure". Nor did I say "I agree with this".

[quote=LordHunter317]
The only proper defense against brute force password attacks of that form is proper paswords.  End of story.  IMO, bothering with other defenses is just a waste of time.[/QUOTE]

I disagree with that. Simply, the more defenses the better. 

--Simon

---

### Post by jdonnell on 2005-06-06
> changing the name of the 'root' account is recommended as cheap protection against brute force attacks.

[QUOTE=LordHunter317]
Which is also bad advice, for other reasons.  It won't make the attacks go away, and it won't make you immune to them in the long run.  It'll just make the attackers try harder.

The only proper defense against brute force password attacks of that form is proper paswords.  End of story.  IMO, bothering with other defenses is just a waste of time.[/QUOTE]

This is so completely wrong that I didn't even want to waste my time responding but I felt I needed to incase someone thinks you know what you are talking about. I took a security class in college and we downloaded a security guide from one of the big security organizations. I don't remember which one and I can't seem to find it, but it had a list of tasks to perform for hardening a system and one of the main ones was to change the username of the default adiminstrator account. For example, change the windows 2k 'Administrator' username to something else. This is an extremely effective way to defend against brute force attacks and it's easily explained mathematically. Let's say there are 8^26 possible passwords for a given username. If we know the username is root then the brute force only has to try 8^26 passwords. However, if the username can change as well and there are 8^26 possible usernames then the brute force attack will have to try (8^26)^(8^26). Obviously this is a very effective defense against brute force attacks. 

Here is a question for you LordHunter. If a bruteforce script can try 100 passwords a second, how much time will it take to try all possible passwords if the username is known versus if it isn't? Now, try to tell me this isn't a valid and effective defense.

---

### Post by deuce868 on 2005-06-06
Why are we all so worried about brute force attacks? Surely we're all locking accounts after a few wrong attempts aren't we?  :grin:

---

### Post by LordHunter317 on 2005-06-06
> **GrumpySimon]I believe that's basically what I said - one 'power user' (you disagree with terminology,[/quote]Yes, we're in agreement here.  It's your use of 'power user' that confuses me.  The entire idea of a power user is one that has the ability to install/remove things (at least in the windows world, where the term has a defined meaning).  It's a term you do have to be careful with.

> I did say "cheap security" not "excellent security", or "the best way to secure". Nor did I say "I agree with this".Any of this is relevant how?  The link you posted recommends a bad techinque for dealing with brute force attacks.

> I disagree with that. Simply, the more defenses the better.This isn't true.  Adding a second deadbolt to my front door doesn't do me any good if the bolt isn't long enough, so on, and so forth.

[quote=jdonnell]
This is so completely wrong that I didn't even want to waste my time responding but I felt I needed to incase someone thinks you know what you are talking about. I took a security class in college and we downloaded a security guide from one of the big security organizations[/quote]So because you've taken a class at college using a guide who's name you can't remmber from a company you don't name, you have more expertise than me?  Starting off with multiple logical fallicies isn't a good way to refute someone you believe is wrong.

> Let's say there are 8^26 possible passwords for a given username. If we know the username is root then the brute force only has to try 8^26 passwords. However, if the username can change as well and there are 8^26 possible usernames then the brute force attack will have to try (8^26)^(8^26). Obviously this is a very effective defense against brute force attacks.This is fallicious reasoning, but the reason why isn't obvious.

An attacker of this nature cannot try 8^26 passwords anyway&mdash said:**
> Here is a question for you LordHunter. If a bruteforce script can try 100 passwords a second, how much time will it take to try all possible passwords if the username is known versus if it isn't?More time than any attacker is willing to spend using that method.  If we assume 8^36 (lowercase letters and numbers), at 100 passwords/s, it would still take 102 **quintillion** years to exhaustively search the space.

Which is why that sort of brute-force attack is totally infeasible remotely.  Which is why your book's logic against is totally illogical.

[edit]Update the time units.  I was in a hurry and mistakenly wrote days instead of years.  Not that it matters terribly much at that scale...

---

### Post by jdonnell on 2005-06-06
[QUOTE=LordHunter317]
These days, with the advent of rainbow tables, having /etc/shadow stolen or your Windows account passwords means instant (well, close-enough) compromise of every password of every account on the system.  In which case, renaming the Administrator account doesn't help because they get the password anyway.[/QUOTE]

I don't have time to argue with you point by point, and yes my example was contrived, but it still holds. I'll just comment on one of your points. If I give you my /etc/shadow file can you give me my passwords by tomorrow?

---

### Post by LordHunter317 on 2005-06-06
> **jdonnell]I don't have time to argue with you point by point, and yes my example was contrived, but it still holds.[/quote]But it doesn't hold.  Show me a case where's its valid.  It doesn't hold for automated remote attacks.  It doesn't hold for compromises of the password file.  It doesn't hold for social engeinerring attacks.

It's security by obscurity at best.  Which generally doesn't give you anything in a digital world.  

And besides, we all know that adding usernames into the mix doesn't make the problem any harder said:**
> I'll just comment on one of your points. If I give you my /etc/shadow file can you give me my passwords by tomorrow?If I had a rainbow table on hand, sure.  I don't personally so I couldn't recover your passwords that quickly, but its presumable someone who was going to attempt to steal /etc/shadow would have already generated or purchased one for use.

Seriously.  If you don't believe me, google for them.  You can find videos of Windows machines being sliced in mere minutes, and you can find tables for purchase for NTLM and MD5; tables that will slice a near-exhaustive 14-character password space.

---

### Post by jdonnell on 2005-06-06
Well, I've decided to argue with you a bit more :)

Here is an example of why it's a good reason to use a different account name. It takes two things to login to a system and it's just common sense that if one is known half the battle is lost. Maybe someone in my office im's a coworker and says "what's the password to our server account" and the person im's them the password. Now some hacker got this password. There job is done if the username is the default. There are many ways in which someone could get the password, but not know the username. Changing the username to something other than the default is a very valid defense.

---

### Post by jdonnell on 2005-06-06
[QUOTE=LordHunter317]
If I had a rainbow table on hand, sure.  I don't personally so I couldn't recover your passwords that quickly, but its presumable someone who was going to attempt to steal /etc/shadow would have already generated or purchased one for use.[/QUOTE]

Show me or are you wrong? Let me know when your ready and I'll give you a /etc/shadow file.

---

### Post by LordHunter317 on 2005-06-06
I myself don't have to perform the action for it to be true:
Read this page and learn about rainbow-tables, including a link to the paper that developed them: [http://www.antsight.com/zsl/rainbowcrack/](http://www.antsight.com/zsl/rainbowcrack/)

You'll note the last demonstration is a demonstration of 10 MD5 hashes being cracked using a 36 character password space.  Takes 35 minutes.

Watch the video if you don't believe me.  I don't know what other proof I can provide.  Demanding that I perform it myself is a logically fallacy and something I simply don't have the money, time, or computing resources to do personally.  If you want to pay for my purchase of a rainbow table, then sure, I'll be happy to crack your shadow file.  If not, then you'll just have to read the paper and watch the videos like everyone else.

---

### Post by jdonnell on 2005-06-06
I can show you videos of all kinds of things that don't represent reality. I can fudge the facts or setup and ideal that doesn't exist, then tape it and show it to you.

---

### Post by jdonnell on 2005-06-06
You don't need to buy a table. You can generate one in about 3 days.

[http://www.antsight.com/zsl/rainbowcrack/rcracktutorial.htm](http://www.antsight.com/zsl/rainbowcrack/rcracktutorial.htm)

I think I'll make one and see how well it works. Care to offer a /etc/shadow file once I get the table generated? Pick some bad passwords and some good ones and we'll see how well it works.

---

### Post by LordHunter317 on 2005-06-06
[QUOTE=jdonnell]I can show you videos of all kinds of things that don't represent reality. I can fudge the facts or setup and ideal that doesn't exist, then tape it and show it to you.[/QUOTE]
 I find it funny you refuse to believe a video of something that's based on a published, accepted research paper written by some very smart cryptographers.  The link to the paper and the way the attack is done is on that site.

So, if these rainbow table attacks don't represent reality, why don't you care to show me where the paper is factually, logically, or mathmatically incorrect?

Oh wait, it's none of those things.  Because the attacks exist.  The tables exist.  The equipment to reasonably generate them exists.  The only thing that doesn't exist is their current widespread use because most attackers don't have the CPU time to generate their own tables  nor are they willing or afford to pay for a pregenerated table and it's shipping (which is difficult as they encompass double-digit GBs for any reasonable space).

I don't have to convince you.  You can either accept the proof given or refute it.  If what I'm saying is untrue and these attacks don't exist, then provide reasoning as to why they're not true.  

Saying that you can provide a video of something that isn't real isn't refutation.  You must show **why** the videos I've linked to aren't real.  Which I think you're going to find is difficult.

---

### Post by LordHunter317 on 2005-06-06
[QUOTE=jdonnell]You don't need to buy a table. You can generate one in about 3 days.

[http://www.antsight.com/zsl/rainbowcrack/rcracktutorial.htm](http://www.antsight.com/zsl/rainbowcrack/rcracktutorial.htm)

I think I'll make one and see how well it works. Care to offer a /etc/shadow file once I get the table generated? Pick some bad passwords and some good ones and we'll see how well it works.[/QUOTE]
 Sure, I'll provide you with a /etc/shadow file.  Tell me the charset first so I can make sure the hashes include at least one password solely composed of the charset.

Also, the length of the plaintext the table is written for, for the same reason.

---

### Post by jdonnell on 2005-06-06
[QUOTE=LordHunter317]I find it funny you refuse to believe a video of something that's based on a published, accepted research paper written by some very smart cryptographers.  [/QUOTE]

I accept it. However, doesn't this throw a wrench in some of the reasoning you've used in this discussion. If 99% of passwords with less than 15 characters can be cracked in less than 30 minutes why bother. I guess we need to start using passwords that are > 30 characters for all of our accounts. 

My main point in this discussion is that it's a good idea to do something like changing the default account because it's easy to do and makes hackers jobs harder even if it doesn't make it harder in all cases. You seem to being saying, and correct me if I'm wrong, that it's pointless to do something like this if in some cases, possibly the most common, it doesn't help.

---

### Post by LordHunter317 on 2005-06-06
[QUOTE=jdonnell]I accept it. However, doesn't this throw a wrench in some of the reasoning you've used in this discussion.[/quote]To some extents, yes.  There currently is no reasonable and good defense against rainbow-table attacks in the event of a password file compromised.

>  If 99% of passwords with less than 15 characters can be cracked in less than 30 minutes why bother.Because there are other attack types that cannot function that quickly where it's beneifical.  Remote-based attacks will never be able to operate that quickly.  Interactive attacks (i.e., guy walks in and sits down on a console) will never be able to either.


> My main point in this discussion is that it's a good idea to do something like changing the default account because it's easy to do and makes hackers jobs harder even if it doesn't make it harder in all cases.But it doesn't make it harder.  It just changes what they carry in the problem space they will try.

Let's assume I have a dictionary of 10 million words.  Now, if I want to go from one user to 100 and still only perform 10 million attempts, I have to reduce my dictionary to 100 thousand words.  

So the questions are: is 100 usernames enough to keep my hit rate the same? And is reducing my passwords to try to only 100 thousand per-user going to reduce it any?  I don't know the answers to this (nor have any hard math), but obviously some attackers think it is, as remote brute-force attacks exist that still try a username.

So what you've done is make them make a tradeoff.  The problem is that I can make that tradeoff to some degree and still compromise tons of accounts.  Proof is out there: website crackers and that SSH worm.  

The fact that the problem space for 8-character passwords and 8-character usernames is 8^128 instead of 8^64 is irrelevant.  I wasn't even going to try that space in the first place, I was only going to try a fixed set of that space.  The fixed set that I hope is going to yield me the most compromises. The problem is that set is pretty flexible and I change it pretty readily (including to have usernames instead of just passwords) without compromising my ability to crack systems.


>  You seem to being saying, and correct me if I'm wrong, that it's pointless to do something like this if in some cases, possibly the most common, it doesn't help.Yes, but rainbow tables aren't the only reason.  What I'm pointing out is that if I stole /etc/shadow from your box, it doesn't matter if you changed "root" to really be account bob with UID 1002.  I'm going to get every password for every account anyway, so it doesn't matter.  That's once case.

I pointed out that changing the username is irrelevant in social engineering cases because if I can get a password from you, it stands to reason I can also get a username from you.  Humans are always the weakest link, sadly.

But in the specific case of remote exploits: my reasoning is the reasoning above: simply adding complexity to the problem space doesn't make their problem anymore complicated.  

They're only interested in trying the **most common** passwords.  Making them try usernames as well doesn't increase complexity by a large number.  Certainly not enough to stop automated attacks.

>  It takes two things to login to a system and it's just common sense that if one is known half the battle is lost.If this was really true then public-key cryptography wouldn't work.  It's not really true anyway.  Everyone and their mother can find out my name.  Not everyone can  find out my SSN.  But you need both to be employed under my name.  The same is somewhat true with directories.

If you were talking about true two-factor authentication methods like SSH public-key pairs, you would be correct.  But a username/password really isn't a two-factor method.

> There are many ways in which someone could get the password, but not know the username.Not really, not generally.  Only if passwords are being secured in bad ways.   And generally, usernames are much eaiser to learn than passwords, even if I recover a password first.

> Changing the username to something other than the default is a very valid defense.Not against a remote brute-force attack.  The simple truth is either your username (and password) are in the set of pairs they will try, or it's not.  End of story.  The only defense is to make sure one or the other (or both) isn't in that set.  And if one or the other isn't in that set, you're done (both doesn't gain you anything in this case).  But, usernames are more common than passwords and it's much eaiser to have a hard-to-guess password (especially where humans are involved) than it is to have a hard-to-guess username.

---

### Post by jdonnell on 2005-06-06
I agree with you almost 100%. However, changing the username does decrease the chances and it's very easy to do. 

> 
So what you've done is make them make a tradeoff. The problem is that I can make that tradeoff to some degree and still compromise tons of accounts. Proof is out there: website crackers and that SSH worm.


True, but my account probably won't be one of the compromised if I change my username and use a decent password. You really just made my case with this statement. You've given examples of attacks that brute force in such a way that changing the username reduces the number of accounts they will compromise.

Btw, I'm going to try to start computing the rainbow table later this week. Should be done by monday. I'll let you know. I'm going to do a small one at first.

---

### Post by LordHunter317 on 2005-06-06
> **jdonnell] However, changing the username does decrease the chances[/quote]**But it doesn't**.  Your username/password are either in the space or not.  You only have to have one **or** the other not in the space.  Having both not in the space is zero gain.

> True, but my account probably won't be one of the compromised if I change my username and use a decent password.It won't if you **just** use a decent password to begin with.

>  You've given examples of attacks that brute force in such a way that changing the username reduces the number of accounts they will compromise.But it doesn't.  It just changes **which** accounts they compromise, not how many.  I'm not sure it reduces the number of sucessful compromises in any real way (no way to tell though, as hard data doesn't really exist publically) .

It also doesn't reduce the number of attacks they make on you.  They're still going to try their password list.  

So, I can do three things, ultimately:[list][*]Pick a strong password I know they'll never try (too long, too complex, too weird) and ignore the attacks.  This is what I'm suggesting[*]Just change the username and hope it's not on their list and they don't try to crack it.  This is risky, as usernames are more common than passwords.  Your odds of your username/password pair being in the problem-space is higher this way.[*]Do both of the above.  This is fine, but pointless, like I said above.  If they don't have the password, they can't login, even if they do have the username.  End of story.  So why should I bother?[/list]

To be clear, my problem with suggesting changing usernames is this: on it's own, it's not sufficent security.  The odds of an attacker randomly guessing your username is higher than randomly guessing your password.  The odds of an attacker learning your username is higher than them learning their password (e.g., search for "Adam Skutt" on google, get LordHunter317 back). 

So in the end, you **still** have to have a strong password.  Changing the username is no substitute for having a proper password.  Something I think we all can agree with.

So, in my mind, I don't see the point of changing the username.  If I've already created a password strong enough to prevent them from compromising my account, I don't care.  It's not like changing my username is going to suddenly make the attacker disappear from my logs.  And it's not like I'm going to change it to a username they're not likely to guess or discover eventually anyway (i.e., I'm not going to call it r00t$l33thax0r!! or something else as complicated as my password).  So, what's the real gain?  I suppose it gives some people some piece of mind, but that's it.

This goes in the same category as the recommendation of removing server version strings.  That sounds like a good idea in theory but in reality, it doesn't matter, because the attacker isn't going to bother to look at the version said:**
> Btw, I'm going to try to start computing the rainbow table later this week. Should be done by monday. I'll let you know. I'm going to do a small one at first.Wonderful.  PM me or reach me by e-mail and I'll be happy to send you a file to try to crack.

---

### Post by jdonnell on 2005-06-06
[QUOTE=LordHunter317]
So, I can do three things, ultimately:[list][*]Pick a strong password I know they'll never try (too long, too complex, too weird) and ignore the attacks.  This is what I'm suggesting[*]Just change the username and hope it's not on their list and they don't try to crack it.  This is risky, as usernames are more common than passwords.  Your odds of your username/password pair being in the problem-space is higher this way.[*]Do both of the above.  This is fine, but pointless, like I said above.  If they don't have the password, they can't login, even if they do have the username.  End of story.  So why should I bother?[/list]
[/QUOTE]

Ok, I see where our disagreement is. We are starting from different assumptions. You are right in that if we use a good enough password then we don't need to change the user names. However, your thinking from an individuals stand point. I'm thinking from an organizational standpoint. I can't depend on people to use good passwords and they always do something stupid like emailing the passwords around. In this situation it's good to do all the little things because I can't depend on the passwords alone

---

### Post by LordHunter317 on 2005-06-06
[QUOTE=jdonnell]  I'm thinking from an organizational standpoint.[/quote]But how hard would it be to get a list of usernames at your organization?

For most groups it's pretty easy.  I could always just buy a email list from a spammer and filter for your domain(s).  That would probably give me a pretty sky-high hit-rate.

So you see my point.  So, unless you change your username to not be one of those and not to be something common (e.g., root -> admin), you still lose. Which you could do, I suppose.  But if you're going to go through all that bother, why not do the right thing?  You just ultimately end up advocating a solution that's just as complicated (r00tl33thax0r ;)) and not as secure.  At best, you get shielded from all the random brute-force attacks that are out there, which is admittedly the core of launched attacks on the Internet.  But it won't save you from a targeted attack, certainly.  

I understand there's a social problem of having strong passwords in organizations.  But that doesn't mean that the existence of a social problem should influence your technical decisions in an ultimately negative way.

Protecting something that wasn't ever meant to be hidden is just silly.

---

### Post by jdonnell on 2005-06-07
[QUOTE=LordHunter317]But how hard would it be to get a list of usernames at your organization?

For most groups it's pretty easy.  I could always just buy a email list from a spammer and filter for your domain(s).  That would probably give me a pretty sky-high hit-rate.
[/QUOTE]

Our email addresses are not the usernames on our servers or databases. I really don't see how someone would get those.

---

### Post by LordHunter317 on 2005-06-07
[QUOTE=jdonnell]Our email addresses are not the usernames on our servers or databases. I really don't see how someone would get those.[/QUOTE]
 Your organization is an exception rather than a rule then, IME.

Save for one my employers that all gave us ID numbers to login, my account name has always been my email address.  Also, with the advent of Active Directory, accounts I have on servers tend to be the same as well, since I only have one account with credentials everywhere. Including in some databases at some point.  Integrated SQL Server authentication is a blessing.

The attack won't work in all situations, but the point is the same: it's tough to make a generalized case for changing usernames as a security measure.  You can make a few specific ones, but that's about it.   Databases are a weird case, addmittedly.

---

### Post by ensenadaubuntulover on 2005-06-14
finaly figured out now I am triing to populate the database with php but...
the tutorial I found are very alike

make an .html file and a .php file

so far so good I input data on the form but it does not get the data to the table or print it

any ideas anybody


so far Accesss is being better than mysql php and apache combination

---

### Post by ensenadaubuntulover on 2005-06-14
By Far

---

### Post by GrumpySimon on 2005-06-15
[QUOTE=ensenadaubuntulover]By Far[/QUOTE]
 Can you show me your code?

--Simon

---

### Post by ymeyer on 2005-06-15
For those which understand french a toto at:


[http://wiki.ubuntu-fr.org/serveur/lamp](http://wiki.ubuntu-fr.org/serveur/lamp)

---

### Post by jdonnell on 2005-06-15
[QUOTE=ensenadaubuntulover]
so far Accesss is being better than mysql php and apache combination[/QUOTE]

Access is not equivalent to mysql php and apache.
Access, asp, and IIS are equivalent to mysql php and apache, and I'm sure you'd have the same troubles with that combo. If you post your code we can help.

---

### Post by LordHunter317 on 2005-06-15
[QUOTE=jdonnell]Access is not equivalent to mysql php and apache.[/quote]Actually it is (in a sense), save for the webserving part, and more featureful in a lot of ways.

A LAMP setup can't generate forms or queries out of the box with a nifty GUI tool.  You actually have to write code to generate them.  

The only thing it can't do is serve webpages on it's own.  But it can almost do that.  It makes deploying to IIS stupidly simple in later versions.  It also makes creating them about as stupidly simple as a form.

While they're not the same **type** of application, they can be used for similar **roles**.  And in a lot of situations, Access excels (no pun intended), especially if your data doesn't need a lot of programming behind it (i.e., you're really just doing CRUD, don't need fancy formatting) and you don't care about web access.  It's when you have to start writing VBA that I start calling into the question the value of Access as a solution.  But for anything before that, Access (or Filemaker or similiar) is very tough to beat.

It's frequently discounted due to hell that is Jet, and I suppose that's not-undeserved.  Also, due to the fact it's part of Office Pro only and that carries a high pricetag.  However, it's one that business are willing to pay for a self-contiained, easy to create database application tool.

Which for most projects Access is used for, you don't.  They're inherently internal.

That being said, the OP needs to post the code to get some help.

---

### Post by jdonnell on 2005-06-15
php is a programming language, and apache is a webserver. Comparing access to them is silly. Maybe there isn't a free gui form builder for mysql, I'm not sure what this is because I don't know much about access, but saying that php mysql and apache are harder than access is comparing apples to oranges.

---

### Post by LordHunter317 on 2005-06-15
Stop looking at the technology and looking at the solution they're creating.  That's what's confusing you in his and mine's comparsions.  We're talking about generated solutions.

I have several databases in Access where simply creating the reports in PHP and getting them to format and paginate properly would take more time then I spent building the whole database.

For CRUD applications without many users, Access is very tough to beat.

---

### Post by ensenadaubuntulover on 2005-06-15
[QUOTE=GrumpySimon]Can you show me your code?

--Simon[/QUOTE]
<HTML>
<HEAD>
<TITLE> Form Handling with PHP </TITLE>
</HEAD>
<BODY BGCOLOR="#FFFFFF">
<center>
<FORM METHOD=POST ACTION="miadd.php">
<input type="hidden" name="id" value="NULL">
<TABLE>
<TR height="20"><TD colspan="2"><FONT SIZE="+0" face="verdana">
Below is a Sample Form for our PHP tutorial</TD></TR>
<TR height="50">
<td></td></TR>
<TR><TD align="left"><FONT SIZE="+0" face="verdana">
<b>Your Name <br>Your E-Mail Address</b></td>
<td><INPUT TYPE="text" NAME="name"><br><INPUT
TYPE="text" NAME="email"><p></TD>
</TR>
<tr><td colspan="2"><center>
<SELECT NAME="opinion">
<option value="is great">I like your site</option>
<option value="is OK">Your Site is OK</option>
<option value="is horrible">Your Site is
horrible</option>
</SELECT><p><INPUT TYPE="submit" value="Tell
us!"></td></tr>
</TABLE></FORM></BODY></HTML>





<?
$DBhost = "localhost";
$DBuser = "userhere";
$DBpass = "passwordhere";
$DBName = "jokes";
$table = "information";
mysql_connect($DBhost,$DBuser,$DBpass) or die("Unable to connect to database");

@mysql_select_db("$DBName") or die("Unable to select
database $DBName");

$sqlquery = "INSERT INTO $table
VALUES('$id','$name','$email','$opinion')";

$results = mysql_query($sqlquery);

mysql_close();

print "<HTML><TITLE> PHP and MySQL </TITLE><BODY
BGCOLOR=\"#FFFFFF\"><center><table border=\"0\"
width=\"500\"><tr><td>";
print "<p><font face=\"verdana\" size=\"+0\"> <center>You
Just Entered This Information Into the
Database<p><blockquote>";
print "Name : $name<p>E-Mail : $email<p>Opinion :
$opinion</blockquote></td></tr></table>
</center></BODY></HTML>";
?>


and thaks for your concern :)

---

### Post by ensenadaubuntulover on 2005-06-15
[QUOTE=jdonnell]php is a programming language, and apache is a webserver. Comparing access to them is silly. Maybe there isn't a free gui form builder for mysql, I'm not sure what this is because I don't know much about access, but saying that php mysql and apache are harder than access is comparing apples to oranges.[/QUOTE]


sorry I am looking for a solution here where sould I go then?

---

### Post by ensenadaubuntulover on 2005-06-15
[QUOTE=LordHunter317]Stop looking at the technology and looking at the solution they're creating.  That's what's confusing you in his and mine's comparsions.  We're talking about generated solutions.

I have several databases in Access where simply creating the reports in PHP and getting them to format and paginate properly would take more time then I spent building the whole database.

For CRUD applications without many users, Access is very tough to beat.[/QUOTE]



The idea is porting whatever I already have, any ideas?

---

### Post by GrumpySimon on 2005-06-16
Ok - I've rewritten that (removed a lot of html markup to make things easier to follow), fixed a few errors, and heavily commented things. Haven't tested this, but it should work. If you don't follow anything, let me know :)

--Simon

[php]
<?php
<html>
<head>
	<title> Form Handling with PHP </title>
</head>
<body>

<?php
/**
 ok - now, I've basically combined you two pages.
 what happens is we check if there's a value in $_POST
 called 'submit'. If there is, then we store the data 
 in MySQL, if not, then we just show the form.

*/

# if you want to see exactly what's being transferred via
# post, then uncomment this:

# echo '<pre>';
# print_r( $_POST );
# echo '</pre>';


if ( isset( $_POST['submit'] ) )
{
	# Ok, the form has been submitted, lets process it.	
	$DBhost = "localhost";
	$DBuser = "userhere";
	$DBpass = "passwordhere";
	$DBName = "jokes";
	$table = "information";
	
	$linkid = mysql_connect($DBhost,$DBuser,$DBpass) or die( mysql_error() );
	# 1) good idea to store the connect id in a var. I'll use $linkid.
	# 2) EVERY time you're debugging a php & mysql script, add the "or die"
	# bit to echo mysql_error() - this will tell you EXACTLY what mysql is 
	# complaining about.
	# You'll want to remove them when the site goes live, as showing these
	# errors when something goes wrong will make things nice and easy to hack.
	
	mysql_select_db("$DBName") or die ( mysql_error() );
	
	# Ok, now we're not checking if the values have been submitted or not.
	# you'll want to use something like !is_empty( $_POST['value'] ) to make sure.


	# now - your problem was that these values aren't set. 
        #The tutorial you're following must be fairly old. 
        # Everything that comes via a posted form will be in the
	# superglobal array $_POST

	# We also need to do input checking to avoid SQL injection attacks. 
        # To do this, we use mysql_real_escape_string()

	$id = mysql_real_escape_string( $_POST['id'] );
	# I'm not sure what you're doing with the id value, I'd just make the field
	# auto-increment in MySQL, and let MySQL handle it.
	# Also - if we're expecting a number, then instead of mysql_real_escape_string()
	# we can just type cast it directly to an integer like this:
	# $id = (int) $_POST['id'];
	
	$name = mysql_real_escape_string( $_POST['name'] );
	$email = mysql_real_escape_string( $_POST['email'] );
	$opinion = mysql_real_escape_string( $_POST['opinion'] );

	$query = "INSERT INTO $table (id, name, email, opinion) VALUES ('$id','$name','$email','$opinion')";
	# Note that I changed your query a bit - it's best to specify the fields you're inserting into.
	
	$result = mysql_query( $sqlquery ) or die( mysql_error() );
	
	mysql_close();
	
	# Also note, that it's very easy and quick to jump in and out of php: 
	?>
	<p><strong>You Just Entered This Information Into the Database:</strong>
	<?php
	# You'd usually use it for a few more lines than that, but that show you how
	# to do it.
	echo "Name : $name <br />";
	echo "E-Mail : $email<br />";
	echo "Opinion : $opinion <br />";
	echo '</p>';
}
else
{
	# Form has not been submitted. So, we'll show it for the user.
	?>
	<form 
		method="post"
		action = "<?php echo $_SERVER['PHP_SELF'];?>"
		enctype="application/x-www-form-urlencoded"
	>
	<?php 
		# ok - by getting the form to submit to $_SERVER['PHP_SELF'] - i.e.
		# THIS page (itself), we only need one page. 
	?>
	<input type="hidden" name="id" value="NULL">
	<p>
	   <strong>Below is a Sample Form for our PHP tutorial:</strong><br />
		Your Name: <input type="text" name="name" /> <br />
		Your Email:	<input type="text" name="email" /> <br />
		<select name = "opinion">
			<option value="is great">I like your site</option> <br />
			<option value="is OK">Your Site is OK</option> <br />
			<option value="is horrible">Your Site is horrible</option> <br />
		</select>
		<input type="submit" name="submit" value="Tell us!">
	</p>
	</form>
	<?php
} ?>
</body>
</html>
[/php]

---

### Post by ensenadaubuntulover on 2005-06-17
thanks I am going to make my homework during the week end and I will let you know

meanwhile I make a GRUMPY directory so I tart fresh from there!

let me print it and study ok?

---

### Post by ensenadaubuntulover on 2005-06-18
> **GrumpySimon]Ok - I've rewritten that (removed a lot of html markup to make things easier to follow), fixed a few errors, and heavily commented things. Haven't tested this, but it should work. If you don't follow anything, let me know :)

--Simon

[php]
<?php
<html>
<head>
	<title> Form Handling with PHP </title>
</head>
<body>

<?php
/**
 ok - now, I've basically combined you two pages.
 what happens is we check if there's a value in $_POST
 called 'submit'. If there is, then we store the data 
 in MySQL, if not, then we just show the form.

*/

# if you want to see exactly what's being transferred via
# post, then uncomment this:

# echo '<pre>' said:**
>  ) )
{
	# Ok, the form has been submitted, lets process it.	
	$DBhost = "localhost";
	$DBuser = "userhere";
	$DBpass = "passwordhere";
	$DBName = "jokes";
	$table = "information";
	
	$linkid = mysql_connect($DBhost,$DBuser,$DBpass) or die( mysql_error() );
	# 1) good idea to store the connect id in a var. I'll use $linkid.
	# 2) EVERY time you're debugging a php & mysql script, add the "or die"
	# bit to echo mysql_error() - this will tell you EXACTLY what mysql is 
	# complaining about.
	# You'll want to remove them when the site goes live, as showing these
	# errors when something goes wrong will make things nice and easy to hack.
	
	mysql_select_db("$DBName") or die ( mysql_error() );
	
	# Ok, now we're not checking if the values have been submitted or not.
	# you'll want to use something like !is_empty( $_POST['value'] ) to make sure.


	# now - your problem was that these values aren't set. 
        #The tutorial you're following must be fairly old. 
        # Everything that comes via a posted form will be in the
	# superglobal array $_POST

	# We also need to do input checking to avoid SQL injection attacks. 
        # To do this, we use mysql_real_escape_string()

	$id = mysql_real_escape_string( $_POST['id'] );
	# I'm not sure what you're doing with the id value, I'd just make the field
	# auto-increment in MySQL, and let MySQL handle it.
	# Also - if we're expecting a number, then instead of mysql_real_escape_string()
	# we can just type cast it directly to an integer like this:
	# $id = (int) $_POST['id'];
	
	$name = mysql_real_escape_string( $_POST['name'] );
	$email = mysql_real_escape_string( $_POST['email'] );
	$opinion = mysql_real_escape_string( $_POST['opinion'] );

	$query = "INSERT INTO $table (id, name, email, opinion) VALUES ('$id','$name','$email','$opinion')";
	# Note that I changed your query a bit - it's best to specify the fields you're inserting into.
	
	$result = mysql_query( $sqlquery ) or die( mysql_error() );
	
	mysql_close();
	
	# Also note, that it's very easy and quick to jump in and out of php: 
	?>
	<p><strong>You Just Entered This Information Into the Database:</strong>
	<?php
	# You'd usually use it for a few more lines than that, but that show you how
	# to do it.
	echo "Name : $name <br />";
	echo "E-Mail : $email<br />";
	echo "Opinion : $opinion <br />";
	echo '</p>';
}
else
{
	# Form has not been submitted. So, we'll show it for the user.
	?>
	<form 
		method="post"
		action = "<?php echo $_SERVER['PHP_SELF'];?>"
		enctype="application/x-www-form-urlencoded"
	>
	<?php 
		# ok - by getting the form to submit to $_SERVER['PHP_SELF'] - i.e.
		# THIS page (itself), we only need one page. 
	?>
	<input type="hidden" name="id" value="NULL">
	<p>
	   <strong>Below is a Sample Form for our PHP tutorial:</strong><br />
		Your Name: <input type="text" name="name" /> <br />
		Your Email:	<input type="text" name="email" /> <br />
		<select name = "opinion">
			<option value="is great">I like your site</option> <br />
			<option value="is OK">Your Site is OK</option> <br />
			<option value="is horrible">Your Site is horrible</option> <br />
		</select>
		<input type="submit" name="submit" value="Tell us!">
	</p>
	</form>
	<?php
} ?>
</body>
</html>
[/php]
 I cut and paste your code and first got a message error about something in line 2, so I removed *<?php* and then the form apeared I put a name and a mail and an opinion choice and got  *Query was empty* response

then I uncommented

 echo '<pre>';
 print_r( $_POST );
 echo '</pre>';

and I got


Array
(
    [id] => NULL
    [name] => rik
    [email] => sepp
    [opinion] => is OK
    [submit] => Tell us!
)

Query was empty

response


when I run the form in dillo

all the code apears and at the bottom the form and in the status bar the legend

File Not Found /home/whatever/<?php echo $_SERVER[

I googled $_SERVER and tells me about a server variable.

It is true that the tutorial is old is php3 an I am using php4
but I dont know that much It is much difference?

I will apreciate if you point me to a newer tutorial because I have tried all kinds and for what you are telling me **THEY ARE DIFFERENT!**[I]

thanks

---

### Post by GrumpySimon on 2005-06-19
Ok - 

1) First problem, remove the <?php on the first line. My bad :)

2) Yeah, that's an old tutorial you've got - you used to be able to access any form variables directly (ie: the form var. "Simon", got put in $Simon), but this was a huge security risk, so they changed that and now all post variables are in the "superglobal" array $_POST (eg: $_POST['Simon'] ), all get variables are in $_GET, etc.

3) Again, my mistake - a typo in the query line. I didn't change the variable name ($sqlquery -> $query) . So change this line:
[php]
$result = mysql_query( $sqlquery ) or die( mysql_error() );
[/php]

to this:
[php]
$result = mysql_query( $query ) or die( mysql_error() );
[/php]

4) $_SERVER is another one of those superglobal arrays. This one contains information about the current page, and webserver request information etc. The one we're interested in in $_SERVER['PHP_SELF'] which just means "this page". 

5) There's a fairly good tutorial [here](http://www.tizag.com/phpT/forms.php), which talks you through it as well. 

--Simon

---

### Post by jdonnell on 2005-06-21
[QUOTE=LordHunter317]
I have several databases in Access where simply creating the reports in PHP and getting them to format and paginate properly would take more time then I spent building the whole database.
[/QUOTE]

Weird, the forums aren't emailing me about replies as it used to. Anyway, I understand what the two of you are saying. I'm simply saying that you can't expect to setup a fully featured webserver, a programming language, and a client server database as easily as access. If access alone does the job then by all means use access. Just watch out for the MS lock in. Your app will grow and then you'll realize that access alone isn't enough. Since you already have access working you'll decide that it's cheaper and easier to setup some asp pages off the access db. The next thing you know your paying $10,000 for a sql server license because it's cheaper than redeveloping the app, but the app would have been far cheaper if originally done with open source.

ensenadaubuntulover, GrumpySimon has you going in the right direction. When I am completely stuck with code I always start over and add one thing at a time until it fails and then I know what the problem is. Keep asking questions if you need to. I would have replied sooner but I didn't get an email that there were replies and GrumpySimon beat me to it :)

---

### Post by ensenadaubuntulover on 2005-06-21
> **GrumpySimon]Ok - 

1) First problem, remove the <?php on the first line. My bad :)

2) Yeah, that's an old tutorial you've got - you used to be able to access any form variables directly (ie: the form var. "Simon", got put in $Simon), but this was a huge security risk, so they changed that and now all post variables are in the "superglobal" array $_POST (eg: $_POST['Simon'] ), all get variables are in $_GET, etc.

3) Again, my mistake - a typo in the query line. I didn't change the variable name ($sqlquery -> $query) . So change this line:
[php]
$result = mysql_query( $sqlquery ) or die( mysql_error() ) said:**
> 

to this:
[php]
$result = mysql_query( $query ) or die( mysql_error() );
[/php]

4) $_SERVER is another one of those superglobal arrays. This one contains information about the current page, and webserver request information etc. The one we're interested in in $_SERVER['PHP_SELF'] which just means "this page". 

5) There's a fairly good tutorial [here](http://www.tizag.com/phpT/forms.php), which talks you through it as well. 

--Simon
 IT WORKED IT WORKED !!!

now that feels goooooood!!

GRUMPY SIMON my man!!! it worked like a charm!!!

it still appears
Array
(
    [id] => NULL
    [name] => rich
    [email] => elmail@elmail
    [opinion] => is horrible
    [submit] => Tell us!
)

from the uncommented lines but gives the correct response and puts the information on the database!

but now I am a step closer

THANKS!!!

---

### Post by ensenadaubuntulover on 2005-06-21
ensenadaubuntulover, GrumpySimon has you going in the right direction. When I am completely stuck with code I always start over and add one thing at a time until it fails and then I know what the problem is. Keep asking questions if you need to. I would have replied sooner but I didn't get an email that there were replies and GrumpySimon beat me to it :)[/QUOTE]

the idea is to promote UBUNTU and steer away from m$, :)  a lot of people in the third (whole) world apreciate that,  for me its BETTER (I never said EASIER) but thanks to this forums and people like GRUMPYSIMON and yourself and dumb people like myself who ask a bunch of questions can make it happen

so keep up the good work and thank you  :-P thats COOL!!

---

### Post by GrumpySimon on 2005-06-21
Not a problem :)

Those Array (...etc) lines are just to help you debug (they're showing you exactly what's coming through the form. If it's working you can comment them out (put a # in from of them), or remove them completely.

--Simon

---

