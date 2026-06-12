---
title: "Internet connection test?"
date: 2011-01-19
forum: Server Platforms
---

### Post by pehden on 2011-01-19
Odd question but maybe good one, is there a script that I can set to run with cron to check if the server has an internet connection and if not restart server or network settings.

---

### Post by SeijiSensei on 2011-01-19
Just write up a script that pings a remote host ([www.google.com](www.google.com) is a good choice) and takes the necessary action if a connection can't be made.

---

### Post by SeijiSensei on 2011-01-19
double post

---

### Post by pehden on 2011-01-19
> **SeijiSensei said:**
> Just write up a script that pings a remote host ([www.google.com](www.google.com) is a good choice) and takes the necessary action if a connection can't be made.

This is why i asked is there one made like this already cause i have know idea what i would need to do for this to work. I only know how to use php but I dont think it will work because im not going to set up php to run as root.

---

### Post by SeijiSensei on 2011-01-20
I don't know if there's any sort of canned script that does this.  Most people roll their own.  Here's a start for you:

```

#!/bin/bash

TEST=$(ping -c3 www.google.com | grep ' 0% packet loss')

if [ "$TEST" == "" ] 
then
    # can't connect; restart network
    /usr/sbin/service networking restart
fi

exit 0

```

I put admin scripts in /usr/local/sbin.  Don't forget to use "chmod u+x" to make the script executable.

I don't know exactly what you want to do if there's no connection.  Above I tell it to restart the networking service.  You might choose to replace that with the "reboot" command if that's what you want to do.

> im not going to set up php to run as root

I'm not sure what you mean by this.  There's a php binary that you can run from the command line to execute PHP scripts.  There are no security implications arising from running that as root.  For instance, I have a script that runs on one client's mail server that uses the PHP IMAP functions to examine each user's mailboxes and delete any spam-tagged messages it finds that are over thirty days old.  This has to run as root so it can have privileges to all the mailboxes.  I wrote it in PHP because I'm comfortable with the language, and because it has extensive built-in functions for handling mailboxes with IMAP.

---

### Post by pehden on 2011-01-20
> **SeijiSensei said:**
> 


I'm not sure what you mean by this.  There's a php binary that you can run from the command line to execute PHP scripts.  There are no security implications arising from running that as root.  For instance, I have a script that runs on one client's mail server that uses the PHP IMAP functions to examine each user's mailboxes and delete any spam-tagged messages it finds that are over thirty days old.  This has to run as root so it can have privileges to all the mailboxes.  I wrote it in PHP because I'm comfortable with the language, and because it has extensive built-in functions for handling mailboxes with IMAP.

I have read alot of things where it was a security issue for php to be able to run as root, but your script here looks like its would do exactly what i need.

---

### Post by pehden on 2011-01-20
Double post.

---

### Post by SeijiSensei on 2011-01-20
> **pehden said:**
> I have read alot of things where it was a security issue for php to be able to run as root, but your script here looks like its would do exactly what i need.

Most of the time these are references to running PHP as part of a web server.  Yes, it would be a big security hole if webservers ran as root, since any exploitation of the server would give the intruder full control over the system.  That's why software like the Apache server is designed to start as root then switch to an unprivileged user (like the "www-data" user in Ubuntu) once launched. 

Some of the things you may have read might apply to using PHP in a "[cgi-bin]("http://httpd.apache.org/docs/current/howto/cgi.html")" situation, but that hasn't been common practice in years.  mod_php for Apache is far easier to install and safer to implement than "roll-your-own" solutions that use a cgi-bin executable.  Still even in these situations, the cgi-bin executables are typically run with the same permissions as the Apache user.  What you don't want, or typically need, to implement are solutions that rely on sudo or [suPHP]("http://www.suphp.org/Home.html") to grant a PHP script root privileges.  Navigating the restricted permissions of the Apache user can be a pain at time, but it's nowhere near as painful as having your server rooted.

---

### Post by pehden on 2011-01-21
suPHP , how do i enable that mod and how do i use it.

---

### Post by SeijiSensei on 2011-01-21
I wouldn't do that if I were you.  Why do you need to run things under another user instead of "www-data"?

For documentation on suPHP, just follow the link I gave you earlier.

---

### Post by pehden on 2011-01-21
> **SeijiSensei said:**
> I wouldn't do that if I were you.  Why do you need to run things under another user instead of "www-data"?

For documentation on suPHP, just follow the link I gave you earlier.

Oh I miss read that post you said I dont need to do that.

---

