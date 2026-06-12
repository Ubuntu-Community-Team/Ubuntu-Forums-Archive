---
title: "You have chosen to open: installer.pl which is a perl Script?"
date: 2007-03-23
forum: Server Platforms
---

### Post by cocotu on 2007-03-23
When I try to open this perl script from my browser I get this:

You have chosen to open: installer.pl which is a Perl Script:
What should Firefox do with this file?

I already installed libapache2-mod-perl2, clear the cache, restarted Apache and still get the same error. I'm trying to install the otrs Trouble ticket software. I did an apt-get install otrs and the files are in this path:

/usr/share/otrs/bin/cgi-bin

Should I move them to /var/www so Apache can see them? Not sure if that is the case. I had similar error with PHP but I was able to fix that by intalling the PHP parser for Apache.

Thanks for any help.

---

### Post by dannp on 2008-02-14
I am a beginner with all this so I will be as specific as possible.

I have installed otrs2 using

[http://localhost/otrs/installer.pl](http://localhost/otrs/installer.pl)

I go threw the steps and use my root password for my MySQL root user

and then I create a user named 'ericksonsotrs' with a password that matches my root (to make easy - I am a beginner so everything is the same for now)

I then navigate to [http://localhost/otrs/index.pl](http://localhost/otrs/index.pl) where I am greeted by the login screen. I try the root user and the new user that I created but it says "Login failed! Your username or password was entered incorrectly."

Then I try to retrieve the password of the users in the last field of the login screen where it says "Lost your password? - I type in the user name an it tells me "There is no account with that login name."

I am totally confused and have been at this for a  week. Please help this idiot out!

How do you setup the users and groups or better yet where do I edit them or link them to otrs? :confused::confused::confused:

---

### Post by faulkes on 2008-02-14
Check the /var/log/apache2/error_log for any errors relating to the installation you did and the login you attempted.

Faulkes

---

### Post by dannp on 2008-02-14
That's a little gray because I had so many attempts before I finally figured out how to do it with the browser. Do you want me to post the whole log.

Is there a way to just set users and permissions and allocate them to certain services such as mysql and otrs?:(

---

### Post by faulkes on 2008-02-14
> **dannp said:**
> That's a little gray because I had so many attempts before I finally figured out how to do it with the browser. Do you want me to post the whole log.

Is there a way to just set users and permissions and allocate them to certain services such as mysql and otrs?:(

I would go back through the log to a point at which you can see errors happening which are directly related to the timeframe in which you were doing stuff, the whole log, depending on how big could be quite cumbersome.  (if it's small, say under 20kb, then sure, post it).

As for allocating users specific rights, that is typically something done on a service by service level.  However, when you installed otrs it should have created the users for you (as your notes say), so I would be looking in the log for any failures related to that.

Faulkes

---

### Post by dannp on 2008-02-14
[http://doc.otrs.org/2.2/en/html/x677.html](http://doc.otrs.org/2.2/en/html/x677.html)

Here is the answer to my question:

The screen lets you enter a user name and a password. Because no users are created after a fresh installation of the system, you have to login as OTRS administrator first. To login as OTRS admin use "root@localhost" for user name and "root" for password.

Sorry for wasting time.:lolflag:

---

