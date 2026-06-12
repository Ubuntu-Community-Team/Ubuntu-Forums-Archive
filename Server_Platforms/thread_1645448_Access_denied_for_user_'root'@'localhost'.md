---
title: "Access denied for user 'root'@'localhost'"
date: 2010-12-14
forum: Server Platforms
---

### Post by najmul002 on 2010-12-14
I am new to ubuntu terminal. I have installed mysql-server, but i have  no access. I have set the password during installation process. Please  help me..

_**Used command:**_
mysql -u root -p

_**error message:**_
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

OS: ubuntu 10.10
RAM: 1.5GB
processor:Intel pentiumD 3.00GHz

---

### Post by Joeb454 on 2010-12-14
Is the MySQL server running?

Also, it sounds simple, but are you sure you entered the password correctly?

---

### Post by stlsaint on 2010-12-14
When you set the password at installation are you sure you set it for root and not another user?

If you set it for another user than you need to use:

```

mysql -u username -p mysql
```
then enter the password when prompted, OR :

To setup root password for first time, use mysqladmin command at shell
prompt as follows:
```
mysqladmin -u root password NEWPASSWORD
```
However if you want to change (or update) a root password, then you need
to use following command:
```
mysqladmin -u root -p oldpassword newpassword
```

---

### Post by maninthemoon on 2010-12-16
I have the same issue. I am using Ubuntu 10.10. I have found this question asked all over the Internet in various forums, and it is never answered. A hundred different people ask, is the server started, or other obvious things. Then they suggest all kinds of wild and crazy hacker stuff that should never have to be done to begin with.

I followed the instructions at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) and used tasksel to install lamp-server. The instructions don't say anything about needing to do a whole bunch of arcane hacks just to make it work. 

I have started the server. I have tried all sorts of suggested things. The bottom line is that no matter what I do, typing:
mysql -u root
results in:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Since hundreds of people (at least) have had this same issue, and it happens with lamp-server "right out of the box" then clearly, the "box" needs to get fixed. At the very least, the instructions do.

I am able to login to mysql successfully with "mysql -u root" if I start the server with skip-grant-tables, but then of course, I can't create any users, assign a root password, or do anything else that requires permissions.

I would really like to see someone figure out what is the bug here, and yes, I would call something that happens this regularly to this many people who are just trying to do something this elementary a bug. And then once it's figured out, all the how-tos, tutorials, and other instructions that neglect to mention this vital info need to be updated and fixed.

Sorry I can't help you, najmul002, but there are a whole lot of us in the same boat.

---

### Post by maninthemoon on 2010-12-17
I believe I may have found an answer, and it may have to do with the screwy way Ubuntu implements security.

It appears that you cannot invoke mysql as root (mysql root user, not the superuser) with no password. I was able to assign one using mysqladmin as follows:

mysqladmin -u root -p password mypassword

After that I was able to start mysql using:

mysql -u root -p

and providing my password.

See if this works for you.

---

### Post by koenn on 2010-12-17
> **maninthemoon said:**
> 
mysql -u root -p

Glad to see that after all that ranting about "getting this fixed" you've finally figured out that a command's meaning changes according to which options (like -p) you invoke it with. 
It also has very little to do with "the screwy way Ubuntu implements security."

---

### Post by koenn on 2010-12-17
> **najmul002 said:**
> I am new to ubuntu terminal. I have installed mysql-server, but i have  no access. I have set the password during installation process. Please  help me..


first, look at what stlsaint posted earlier. you need to use the correct "database root user" name. It can be root, but you've also been given the option to change that during setup.

And, of course, be sure you type in the password correctly. 


if that didn't help, you might what to try and (re-)set a mysql root password.

Here's one way :

1. Stop MySQL
2. Restart it manually with the skip-grant-tables option:
 mysqld_safe --skip-grant-tables

3. Run the MySQL client: mysql -u root

4. Reset the root password manually with this MySQL command: 
UPDATE mysql.user SET Password=PASSWORD('password') WHERE User='root';

5. Flush the privileges with this MySQL command: FLUSH PRIVILEGES;

From [http://stackoverflow.com/questions/489119/mysql-error-1045-access-denied](http://stackoverflow.com/questions/489119/mysql-error-1045-access-denied)


Other methods described here : [http://dev.mysql.com/doc/refman/5.5/en/resetting-permissions.html#resetting-permissions-unix](http://dev.mysql.com/doc/refman/5.5/en/resetting-permissions.html#resetting-permissions-unix)

---

### Post by maninthemoon on 2010-12-17
"Glad to see that after all that ranting about "getting this fixed"  you've finally figured out that a command's meaning changes according to  which options (like -p) you invoke it with. 
It also has very little to do with "the screwy way Ubuntu implements security."

First of all, I didn't "finally figure out" anything. Your statement has nothing to do with my post. The instructions didn't say to use -p because no password had been set yet. What I said is exactly what I meant. It has everything to do with Ubuntu's security, because on every other system I've done this (Fedora, OpenSuse, Knoppix) the command "myslq -u root" (or mysqld depending on installation) has worked just fine (assuming the root user has no password yet). It doesn't work in Ubuntu because (I'm guessing) they've locked it down so that you can't log in as the root user without a password having been set. Admitedly, it's been at least a year since I've installed a lamp configuration on those, so they may have changed it in other distros as well, or even in mysql itself for all I know.

The instructions for setting this up, in the link I provided, which is an Ubuntu article, mention nothing about this, and following those instructions does not work.

Your excellent suggestion indicates that if you start mysql as the root user, then you bypass the grant tables altogether. I did not realize that; that's useful to know. Thank you also for the links. As you know, there's so much stuff "out there" that you can spend hours chasing Google results and still not find the right solution.

Still...all this should be irrelevant. The instructions shouldn't say "do this" if doing that isn't possible and doesn't work.  If you are an expert at this stuff, or do it all the time, great. There are many things that many of us only have to do once in a while, and when we do, we can't remember everything off the tops of our heads, and even if we did, changes have probably happened since. Therefore, we must follow the howto or other instructions. When those instructions don't work, and hours of research online still can't turn up an answer to something (that isn't some obscure hardware issue or strange bug, but something commonplace and widespread), something is wrong. And I'm not frustrated because I ran into one wrong instruction somewhere, or even occasionally as could be expected. It's because almost every time I try to do something relatively basic that requires following a set of instructions that should be easy and straightforward, something isn't right and I have to spend hours that I don't have trying to figure it out.

Regardless of the snide put-down, I thank you for taking the time to respond and for the helpful info.

---

### Post by koenn on 2010-12-17
I'm not in the mode for an extended flame war right now, so I'll be brief

I know there's a lot of info out there. If you want to get things right, you don't mindlessly copy "this worked for me" commands from blogs; you look at the documentation for your distribution and the official manuals for the software you're dealing with. That narrows it down a bit, and is usually more accurate.

On Ubuntu and Debian, dpkg prompts for a password when setting up mysqld, so it's always ''mysql ...  -p''. 


You 're right that "can't log on to mysql" seems to happen a lot. I haven't really looked in to it, but usually it comes down to
- user forgot password, or mistypes it
- user forgot account name, or mistypes it
- the user did not get to see all relevant questions during the setup of mysql-server, so the package is installed with a broken config, or with values the user is not aware of. This happens eg when the packager made a judgement error as to the importance of those questions.


None of those have anything to do with "how ubuntu does security". It's either user error, or a flaw in the mysql-server packege in Ubuntu (and meybe Debian). In the latter case, '' dpkg-reconfigure mysql-server-...''  might sometimes be an alternative fix, as it then shows additional prompts or lets you reset values.


the snide putdown - well that's just a normal reaction to people ranting about something they don't understand, afaik. 
I don't consider myself an expert in Linux, or mysql-server, but I know what a database is and how to read a reference manual. 


In brief :
learn to look for good info, learn to distinguish it from irrelevant info, and try to understand what's going on. Especially with servers, you need to know at least a bit of what you're doing - some stuff just can't be dumbed down to copy/paste instructions that will 'just work' in any and all situations.

---

