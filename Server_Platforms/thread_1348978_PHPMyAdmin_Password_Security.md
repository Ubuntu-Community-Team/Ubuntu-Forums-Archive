---
title: "PHPMyAdmin Password Security?"
date: 2009-12-07
forum: Server Platforms
---

### Post by Kiwi76 on 2009-12-07
I'm trying to setup a Ubuntu 8.04 LTS server, and for the most part, it's been fun and gone well, and I've learned some things.

My problem, which isn't with Ubuntu itself, is this. I installed PHPMyAdmin (using the "sudo apt-get install phpmyadmin" command), and it installs well, but when I go to log on, there's confusing things happening.

1. When trying to login using my username for either the server or MySQL (they're both the same anyway) and password (again, they're the same), it fails!

2. If I try logging in using "root" and my user's password, it succeeds (why the heck does the user's password work for "root" and not for the user name?). So, it works, then what is the problem? Well...

3. If I try logging in using a name (just any old name at all! seemingly anything other than "root") without a password, it works! This means any old person with any old name without a password at all can get in. Seemingly, when "logged in" this way, I cannot create a database,m and maybe other things can't be done, but this has me questioning if this a security hazard if they can even get in and do anything.

How can I fix this, and why is PHPMyAdmin even like this by default!?

Sorry if this is in the wrong place. I realize it's a PHPMyAdmin thing and not Ubuntu, but since I'm trying to get a Ubuntu server going and this is holding me up from putting it live, hopefully I can get help from people who I assume know about this probably common and basic issue. If any more information is needed/I left anything out, just ask. Thanks in advance for any help.

---

### Post by windependence on 2009-12-07
Well, it works with any name, but you didn't notice they can't do anything. You have the MySQL "guest" account enabled. 

You also need to create your MySQL user, and lock down MySQL. I would suggest reading the documentation on post install setup. Generally, you don't just install it and use the defaults.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

-Tim

---

### Post by Kiwi76 on 2009-12-07
I did notice they couldn't do much, but I wasn't sure if they could do anything. So then anyone being able to get in and view those pages is really of no concern? I was under the impression that if they're not a user, they shouldn't be able to get in at all. How would I disable this guest account?

This is what I used, if it helps any.

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

I have a user and password for MySQL. As I said though, the problem is, those details don't work. I get the 1045 error. The password does work, but only for the "root" user, not the user it should be working for. So, I can get in, just under the "root" account, not the one I created.

---

### Post by windependence on 2009-12-07
```
shell> mysql -u root
mysql> DROP USER '';

```
The DROP statement applies both to Windows         and to Unix. On Windows, if you want to remove only the         anonymous account that has the same privileges as         root, do this instead:       
 ```
shell> mysql -u root
mysql> DROP USER ''@'localhost';

```
That account allows anonymous access but has full privileges, so         removing it improves security.

You wan to remove those anonymous accounts before you expose the database to the internet.

-Tim

---

### Post by HighCommander540 on 2009-12-07
> **Kiwi76 said:**
> I did notice they couldn't do much, but I wasn't sure if they could do anything. So then anyone being able to get in and view those pages is really of no concern? I was under the impression that if they're not a user, they shouldn't be able to get in at all. How would I disable this guest account?

This is what I used, if it helps any.

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

I have a user and password for MySQL. As I said though, the problem is, those details don't work. I get the 1045 error. The password does work, but only for the "root" user, not the user it should be working for. So, I can get in, just under the "root" account, not the one I created.

If you mean you created a use in Ubuntu for your MySQL service. That has nothing to do with database users. You need to log in as root and create a new user in MySQL itself. Also, yeah delete the anonymous user.

Also, if you did actually create a user in MySQL. It seems that your problem is that you are trying to access the database from somewhere else, other than what the server has given that user permissions from. MySQL is cool, because it only allows certain users from certain hosts. You need to modify your user to be able to access from "%" if you want to access from other than just localhost. Or it could be set up to not allow connections for that user from anywhere yet. So you would need to let it have access from localhost.

---

### Post by Kiwi76 on 2009-12-07
Okay, a few clarifications.

1. I will be accessing the Ubuntu server remotely from Windows (Putty for SSH and FileZilla for FTP), as the server will be run headless and with no keyboard or anything.

2. As per the user confusion, yeah, that was my mistake. I haven't created any users in MySQL yet.

3. For permissions, I want the "root" user to be the only one to be able to get in, or should I not be using the root user at all and instead create a new one? Either way, I want the ability to even browse into PHPMyAdmin from ***any*** other non-existing names to be denied period (i.e., for them to continuously be shown the log-in screen unless they use a valid user/password combination, as that's how it should be). I can get in with ***any*** name and just look around. I don't want anyone to be able to do that. Last I checked, I couldn't do that on any other servers. Can I do this from the "User overview" page in PHPMyAdmin?

4. For the anonymous account, I never knew there were any. How would I go about removing it (sorry to sound dense, but I don't know where to start with windependence's instructions)?

Thanks for all the help so far!

---

### Post by Kiwi76 on 2009-12-08
Okay, I think I have gotten things how I want them.
I read over the page you linked to more thoroughly, nd also read this, which is where your commands came from.

[http://dev.mysql.com/doc/refman/5.1/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.1/en/default-privileges.html)

It makes more sense now (the "shell>" and "mysql>" things threw me off because I didn't know if I was supposed to type them like that or not, but now I get it). I found out, however, that this could had just as easily been done in PHPMyAdmin itself.

So let me see if I have this now.

1. The MySQL "root" account has a password set.

2. A separate user with limited abilities for one database was created rather than using the "root" user.

3. All guest and anonymous accounts were dropped.

Is this correct? This doesn't pose any security concerns?

Another question (about Apache).

> if you want to make /var/www your own. **(Use only for non-production web servers - this is not the most secure way to do things.)**

$ sudo chown -R $USER:$USER /var/www
This is what I did, but apparently it's not a good idea. How do I "disown" it? If I do disown it, won't I not be able to transfer files to and/or from the server via FTP?

---

### Post by HighCommander540 on 2009-12-08
> **Kiwi76 said:**
> Okay, I think I have gotten things how I want them.
I read over the page you linked to more thoroughly, nd also read this, which is where your commands came from.

[http://dev.mysql.com/doc/refman/5.1/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.1/en/default-privileges.html)

It makes more sense now (the "shell>" and "mysql>" things threw me off because I didn't know if I was supposed to type them like that or not, but now I get it). I found out, however, that this could had just as easily been done in PHPMyAdmin itself.

So let me see if I have this now.

1. The MySQL "root" account has a password set.

2. A separate user with limited abilities for one database was created rather than using the "root" user.

3. All guest and anonymous accounts were dropped.

Is this correct? This doesn't pose any security concerns?

Another question (about Apache).


This is what I did, but apparently it's not a good idea. How do I "disown" it? If I do disown it, won't I not be able to transfer files to and/or from the server via FTP?

Ok, two things I would like to point out to you. As I am a private server owner myself. Trying to learn all the tings I need to make a good secure server. For later commercial use.

1. Good, and yes you can just use phpMyAdmin. Its easy to do for people that don't like command line stuff. And it is a good thing that you created the other user, but what you might want to do is still allow it to create new databases and edit other ones. Just disable it from using the mySQL database and the schema database. So that you can do something on more than one database. Unless you are just going to create a user for each database (which is actually a good idea). Also, very good on dropping the quest users. IDK, why those ever even get set-up (its stupid). I personally use the root account to manage my databases and then for applications I make a new user to control that application's database (learned it from others).

2. On the Apache note. I have found that it is not wise to make the files your own. And this is from advice of others here as well. Not to do this. Because it makes it so that Apache can't actually load it (you can but it makes the files so insecure its not worth it). To switch back you would use the same command just for the apache user and apache group.

```
sudo chown -Rf www-data:www-data /var/www/
```

*Note: www-date is Apache

---

### Post by Kiwi76 on 2009-12-08
Okay, it sounds like I'm starting to get on the right track.

I'll probably only be using just this one database, so it shouldn't be a problem if it's limited to just the one.

This is what I followed for taking ownership of the "/var/www-data" directory.> Now that you've got everything all set up, you'd probably like to add a website to it. By default, all of the files Apache serves up to the internet are located at "/var/www/". However, you cannot write to this folder. Let's make it so you can:

sudo usermod -g www-data [YOUR USERNAME]
sudo chown -R www-data:www-data /var/www
sudo chmod -R 775 /var/www

What happened there was you added yourself to the "www-data" group, and made the website folder writable to the members of the "www-data" group.I assumed this was making ownership mine since I had to input my username in the first command, but if www-data is apache, then it looks like I have it right? The second command is almost the same as yours (it's just missing the "f" after the "-R").

---

### Post by HighCommander540 on 2009-12-08
> **Kiwi76 said:**
> Okay, it sounds like I'm starting to get on the right track.

I'll probably only be using just this one database, so it shouldn't be a problem if it's limited to just the one.

This is what I followed for taking ownership of the "/var/www-data" directory.I assumed this was making ownership mine since I had to input my username in the first command, but if www-data is apache, then it looks like I have it right? The second command is almost the same as yours (it's just missing the "f" after the "-R").

Haha, wow. Yeah, you actually did use the guide that I used myself. Doing that is one of the best ways to do it, because you still want www-data to have ownership over the files.

If that is what you did. That is what I was going to tell you to do.

I add f because it means force. Which if an error possibly happens it just forces the permissions anyway.

---

### Post by windependence on 2009-12-09
It is not necessary to force permissions or ownership, especially if you are root. Apache must own the root directory or it won't be able to read your web files and serve them. So, you simply set your root directory (whatever it is, it doesn't matter) to be owned by www-data and the group as www-data. This is the proper way to do things. Also, permissions can be set as tight as 0644 generally and still work fine, as long as ownership is correct.

On PHPMyAdmin, it's fine to use as an admin tool. You would normally log in as a privileged user (you can create one by logging on as root) and then make it impossible to log in as root. Set your admin user to be able to do everything you want, but NOT as much as root. Name your user something other than admin or of course root. The idea here is to make a hacker guess not only the password, but also the user name. I might put the candy out there, but I'm not gonna gift wrap it, get it? Use good passwords (in other words, NOT words) and you will be set. Your database user for applications should only have the abilities it needs and no more. Most of you don't even need a MySQL database unless you run forums or blogs. For static web sites, you only need Apache.

-Tim

---

### Post by HighCommander540 on 2009-12-09
> **windependence said:**
> It is not necessary to force permissions or ownership, especially if you are root. Apache must own the root directory or it won't be able to read your web files and serve them. So, you simply set your root directory (whatever it is, it doesn't matter) to be owned by www-data and the group as www-data. This is the proper way to do things. Also, permissions can be set as tight as 0644 generally and still work fine, as long as ownership is correct.

On PHPMyAdmin, it's fine to use as an admin tool. You would normally log in as a privileged user (you can create one by logging on as root) and then make it impossible to log in as root. Set your admin user to be able to do everything you want, but NOT as much as root. Name your user something other than admin or of course root. The idea here is to make a hacker guess not only the password, but also the user name. I might put the candy out there, but I'm not gonna gift wrap it, get it? Use good passwords (in other words, NOT words) and you will be set. Your database user for applications should only have the abilities it needs and no more. Most of you don't even need a MySQL database unless you run forums or blogs. For static web sites, you only need Apache.

-Tim

I actually agree with you on the second part. That was basically what I was trying to get across. Especially never give an application user the grant access. The tis where it kills servers, because then other users an be created with full permissions to everything.

I agree with you partially on the first section, but only partially. If you look at this link here: [Server Permissions]("http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_10_1077830297"). It proves that yes 644 is a good idea, but only if you are not using PHP or any script. If you are you need to have it at 755.

Also, the difference between that and my 775. It that I allow other people (user directories) to upload files to have a web server. So I need the group settings to be 7. Because the files are owned by the user and the group is always set to www-data. It makes it so all users can create, edit, delete their files, but also Apache can still server them to the net.

---

### Post by Kiwi76 on 2009-12-28
Interesting information. I'm sure it will help. I am running forums, by the way. I am using a user with the permissions it needs (and no more), and I'm not sure if I have the root account locked out. Wouldn't that lock me out as well if I did?

P.S. Someone can mark this as solved, if they wish.

---

### Post by phillw on 2009-12-28
> Set your admin user to be able to do everything you want, but NOT as much as root. Name your user something other than admin or of course root. The idea here is to make a hacker guess not only the password, but also the user name.

I create a 'super' admin with an obscure name - and get rid of the root account - every script kiddie on the planet looks for root. Same as i have the root account disabled on my box (i.e. you can't su to it)

Oh, to mark a thread solved, You'll see "Thread Tools" near the top of the page, click on theat, then click on "mark solved"

Regards,

Phill.

---

