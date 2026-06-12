---
title: "Storing secure keys on Ubuntu web server"
date: 2012-12-07
forum: Server Platforms
---

### Post by Sencha on 2012-12-07
Hi all,

I'm running Ubuntu 12.04 Precise with a DUNG (Django, Unix, Nginx & Gunicorn) environment and my app (as well as various config files) is stored in a python virtual environment inside /srv, which the www-data user has access to.

The nginx & gunicorn processes are all run as www-data.

My web app requires secure credentials which I am storing in an environment.sh file. This file contains various exports and is run using source before the gunicorn processes execute.

My concern is the location of the environment.sh file and it's permissions. Will it be okay storing this file inside the /srv folder where the www-data has access to it? Or should it be stored and owned by root somewhere else such as /var/myapp/environment.sh?

Also, regarding the www-data user, if any of my web processes (which are run as www-data) are compromised and someone gains access to them, does that mean that the user could potentially read any file on the system, even if they can't write? Including my secure keys?

Many thanks!

---

### Post by TheFu on 2012-12-07
It is impossible to provide a 100% accurate answer without logging into your system and checking thousands of things AND having a complete understanding of each of those tools.  I know UNIX and nginx.  Truly securing a web server is not easy. A good, if not complete, understanding of file permissions is necessary to start.  A good, if not complete, understanding of process ownership and environments is also needed.
A good, if not complete, understanding of who your hosting provider has set everything up is also needed.  Not all hosting providers really care about security. Most seem to get something working and stop there. It is left to you to ensure a level of security that will meet your application needs.  It is hard to know if this is the case unless you understand how everything fits together.

I think you have valid concerns based on what you've written.  Placing any sensitive data anywhere that the web server can access is a bad idea.  Storing credentials inside files is a bad idea too - you do require passphrase to open the keys, right?

I should point out that security is usually a compromise. We compromise security for convenience all the time.  The easiest example is when we don't set a passphrase to access keys so that the keys can be available automatically after a reboot without human intervention. I'll admit that I do this too. Convenience won in my situation.

If all these processes run as the same user, I think your options are limited. If nginx runs as a different user from the other processes and you have nginx handling all the SSL aspects for the app, then you should just follow an nginx best practices guide for securing SSL.  [http://www.nginx.org/en/docs/http/configuring_https_servers.html](http://www.nginx.org/en/docs/http/configuring_https_servers.html) is where I'd start, but I'd look over the best practices guides for Django too.

You want the minimal access required to make everything work, no more.

---

### Post by Sencha on 2012-12-07
Hi TheFu, thanks for the the quick and detailed response.

Appreciate the advice regarding users, permissions and ownership! I don't suppose you could recommend any good books or websites on the subject?

Regarding the sensitive data required for my web servers, they will be such things as AWS access keys and secrets, usernames & passwords for MySQL connections. These will be stored as environment variables to allow the web application to use the credentials.

I understand it's hard to advise while not knowing more about the setup, however as you mentioned that you have done this too, where would you recommend storing the (unprotected) file which contains the environment variable exports?

As a site note, we're hosting on AWS EC2 instances, and with the ability to auto-scale and spin up instances on demand, the ability for them to read the credentials from a file is really almost a requirement.

Thanks again for the advice, really appreciate it.

---

### Post by TheFu on 2012-12-07
> **Sencha said:**
> where would you recommend storing the (unprotected) file which contains the environment variable exports?


I am over my head for some of your setup. I've never used EC2 for anything except stuff that I wanted 100% public.  I do not trust cloud (someone else's) computers.

On most UNIX systems, having any file "unprotected" takes an positive action on your part using a chmod 777 command (never do that).  

The most secure way to limit who can see your credentials and other "secret" data is to set the file with 600 permissions with root.root as owner and group.  No other user will be able to read the file. It is best to place that file in a directory with similar user/group ownership. This will make it harder for other users to access - since they will not be able to use 'ls' to get the file name.  On my installations, nginx starts as root, then changes to www-data for worker processes and the cache manager. This means that it may be able to read those files during startup, gather environment variables, and pass them onto www-data workers securely.  Just an idea.

Avoid passing sensitive information between programs using command line parameters. These can be seen by any ID on the system in the process table. 

As you can see, deploying a secure app requires subtle knowledge of file permissions and process ownership.  There are probably other subtle issues that I haven't mentioned at all.  Again, look for "best practices security {topic}" in your favorite search engine.

I learned all this stuff years ago. I doubt any of the materials I learned from still exist, plus being a cross-platform C/C++ developer provided additional insights that non-programmers would not learn ("some programmers" in certain cross platform languages don't often learn anything about the OS from my experience).  
O'Reilly has books on **Practical System and Unix Security** that might be good, but you probably don't have time to learn the material.  An **Advanced Unix Programming** from Addison is also a favorite.

You are asking the right questions. I'm sure that you will find some good answers, but only time and being burned is likely to ensure complete understanding.  Just because a website doesn't get cracked, that doesn't mean it is secure.

---

