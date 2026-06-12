---
title: "Wordpress on one server with two sites."
date: 2009-04-04
forum: Server Platforms
---

### Post by ciborium on 2009-04-04
I just installed Wordpress on my Ubuntu Server 8.10 using the tutorial at [http://www.cydeweys.com/blog/2006/12/15/ubuntu-linux-610-wordpress-installation-walkthrough/](http://www.cydeweys.com/blog/2006/12/15/ubuntu-linux-610-wordpress-installation-walkthrough/) 

I am currently hosting two (empty) websites from that server.
I'll call them "first.com" and "second.com"

I installed wordpress using "first.com/blog/wp-admin/install.php"

"www.first.com/blog/" works great, 
but "www.second.com/blog/" redirects to "www.first.com/blog/"

When I tried to use "second.com/blog/wp-admin/install.php" it said that Wordpress was already installed.

How do I set it up so that I have two seperate blogs for the two sites?

---

### Post by koenn on 2009-04-04
[http://codex.wordpress.org/Installing_Multiple_Blogs](http://codex.wordpress.org/Installing_Multiple_Blogs)

---

### Post by dtoronto on 2009-04-04
you need to set up Wordpress in two separate directories.  Keep the one that is already set up in the current directory and put another set of wordpress directories in another location in the /var/www/ directory, or wherever you have your web hosting directory.  You need to route your second domain to the second wordpress directory in the /apache2/sites-available/ directory and make the symbolic link to the sites-enabled.

---

### Post by tubezninja on 2009-04-04
The Ubuntu package installation for wordpress seems like it's really meant to handle only one instance of the software per server. For more than one instance, it's really better to download the software from the wordpress download page, untar it, and run the install that way.

It's still possible to use the existing pacakge you've already installed for your first blog on first.com.  For second.com, here's what I recommend:

1. Go into your second.com Virtualhosts's subdirectory, and issue the following command:

```
wget http://wordpress.org/latest.tar.gz
```

This retrieves the latest version of wordpress.  Note: you may need to install wget ('sudo apt-get install wget') if you don't already have it.

2. Then untar the file:

```
tar -xvvzf latest.tar.gz
```

This will create a subdirectory named something like "wordpress-2.7.1" (or whatever the current version ends up being when you read this)  use mv to rename the directory to whatever you want it to be (i.e. "secondblog")

Then, use your previous instructions to create a new database for this blog, but the name of the database MUST be different from the previous one:

```
$** mysql -u root -p**

mysql> **CREATE DATABASE secondwordpress;**
Query OK, 1 row affected (0.00 sec)

mysql> [B]GRANT ALL PRIVILEGES ON secondwordpress.* TO 'secondwordpress_user'@'localhost' IDENTIFIED BY 'otherpassword' WITH GRANT OPTION;
[/B]Query OK, 0 rows affected (0.00 sec)


mysql> **FLUSH PRIVILEGES;**
Query OK, 0 rows affected (0.00 sec)

mysql> **quit;**
Bye

```

Now, use a web browser to navigate to [http://second.com/secondblog](http://second.com/secondblog) and Wordpress should guide you through finishing the install of the second blog.  You'll need to enter in the name of the second wordpress database, second wordpress user and password, etc.  It should only take a minute or so.

There is a drawback to this setup: when you [update your ubuntu server's software]("http://ubuntuforums.org/showthread.php?t=881873"), the second wordpress software won't update using this method.  However, it does have it's own built-in[ Automated Core Upgrader feature]("http://codex.wordpress.org/Version_2.7#WordPress_Upgrader"), and as long as you use that, you'll probably have even newer features and capabilities than the version in Ubuntu's repository.

Generally, the wordpress package in ubuntu is good for people who are only going to run one blog on their server and don't want to ever be bothered with maintaining mySQL databases and the like.  But, for people who will ever be running more than one blog on the same server or intends to expand and learn these things over time, I recommend that you download the code from wordpress and make them separate installations.  Installing wordpress "from scratch" is exceedingly easy if you know some basics about linux, or want to learn.

---

### Post by ciborium on 2009-04-04
Thanks all!

@ koenn:
From what I could tell, that link doesn't really apply to what I was doing, but I appreciate the info.  It will prevent me from creating what would probably have been another Wordpress post later on.

@ dtoronto:
I appreciate your reply because it addressed my question as asked.  Usually that's what I want.  Had I been hovering over my post waiting for a reply, I would have probably implemented your solution right away.  

@ scaredpoet:
This seems to be the best option to fix my problem, rather than patch my mistake.  Since there isn't any content on the blog yet (or the sites, for that matter,) I'll remove wordpress and reinstall in both directories per the instructions.

---

### Post by koenn on 2009-04-04
> **ciborium said:**
> Thanks all!

@ koenn:
From what I could tell, that link doesn't really apply to what I was doing, but I appreciate the info.  It will prevent me from creating what would probably have been another Wordpress post later on.


That link isn't all that different from scaredpoet's explanation, except that it's a bit more concise and  assumes you set up WordPress from the tarball on the site to begin with.

 I didn't realize there was an ubuntu package for it, but as there is, it would have wrapped the details of setting up databases etc in a debconf install script, so I can see how it article I pointed to didn't make sense.

But they do have some very good info on their site.

---

### Post by ciborium on 2009-04-04
You're right.  I guess I got confused about its applicability when I saw the single database information.  That was the part that I mentioned I might use later.

Also, a note to anyone who reads this thread because you did the same thing:

If you remove Ubuntu's Wordpress and install the tar.gz per the website's instructions, make sure you go back and re-edit the "/etc/apache2/apache2.conf" file to remove the alias info, otherwise you'll get 404s when you try to access your blog folder.

---

