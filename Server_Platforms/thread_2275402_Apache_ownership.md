---
title: "Apache ownership"
date: 2015-04-25
forum: Server Platforms
---

### Post by grizdog on 2015-04-25
First off, I should point out that I use this machine mostly as a desktop machine and configured it that way when I installed Ubuntu 14.04.  But I want to run an apache server, which I have done before.  I am having problems now, and would love to see some concrete, simple examples for working configuration files.  But I have another, more general question.

In the documentation, ownership of the Apache files is supposed to be user and group www-data  When I installed Apache, this user didn't show up.owning any files, or in the etc/passwd file.  am I supposed to create the user and chown things?  I don't mind doing it, but it seems like something that would get done for you.  

I am assuming the files and directories in /var/www/html - the document hierarchy - could be owned by pretty much anyone, the only concern there is security.  But what aboutthe files in /etc/apache2 ?  Those were all root:root, and changed them to be owned by me while I was editing them.  Is that a problem for testing?

Do I have to create the www-data user and group, and put everything in it?  By the way, apache works, but can't seem to follow any of my instructions in the  config files, in particular where to look for the the document root.

Thanks.

---

### Post by grizdog on 2015-04-26
Follow-up to my own post - When I look at these files with cat or more, and then do an ls -alurt on the directory, there is no update to the access time.  Likewise, when I restart or reload the daemon with service, and even when I reboot, ls -alurt doesn't update the access time.  Whate is going on?  I'm talking about the files in /etc/apache2

Nothing of interest in the error log, either.

Thanks

---

### Post by TheFu on 2015-04-26
> **grizdog said:**
> First off, I should point out that I use this machine mostly as a desktop machine and configured it that way when I installed Ubuntu 14.04.  But I want to run an apache server, which I have done before.  I am having problems now, and would love to see some concrete, simple examples for working configuration files.  But I have another, more general question.

The major version of apache changed recently, so googling for answers is NOT your friend.  Find a book (online version) that has the version you are running - hopefully, you are using 14.04 - nothing newer. Servers need an LTS release - always, IMHO.

> **grizdog said:**
> 
In the documentation, ownership of the Apache files is supposed to be user and group www-data  When I installed Apache, this user didn't show up.owning any files, or in the etc/passwd file.  am I supposed to create the user and chown things?  I don't mind doing it, but it seems like something that would get done for you.  

There aren't any files for it to own at install time.  The apache userid and group were created during install. If /etc/passwd (note the beginning / - IT MATTERS!@!!!!@#!@@!#!@#!@#!@!#@!#@).  File in /var/www/html/ need to be readable by the userid that apache processes run as.  If that is www-data, then as long as the file permissions allow whatever access is required for the website, all will be good.  Webapps usually have read-only areas and read-write areas (often a DB).  Getting these permissions wrong can lead to being completely hacked.  If you don't understand them - learn it now, today, this second.

> **grizdog said:**
> 
I am assuming the files and directories in /var/www/html - the document hierarchy - could be owned by pretty much anyone, the only concern there is security.  But what aboutthe files in /etc/apache2 ?  Those were all root:root, and changed them to be owned by me while I was editing them.  Is that a problem for testing?


/etc files need to be controlled by root 99.999999999% of the time.  DO NOT change them to be owned by you. This is a major security failure. Learn about file permissions. That leads into understanding processes permissions.

> **grizdog said:**
> 
Do I have to create the www-data user and group, and put everything in it?  By the way, apache works, but can't seem to follow any of my instructions in the  config files, in particular where to look for the the document root.


Apache is the kitchen sink of web servers, so it has many features you don't want or need.  Document root is usually controlled by files in the /etc/apache2/sites-enabled/ directory.  A single Apache box can host 5000 websites, so it is common to name files by the FQDN in the sites-available/ directory, then using a symlink into the sites-enabled/ directory to make a specific site active.  Reloading apache after any changed under /etc/apache2 is needed.

> **grizdog said:**
> 
Thanks.

For the best documents, be certain to check apache.org, help.ubuntu.com, and the ubuntu server guide: [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) - this is the LTS version.

If you want to [learn more about Linux.]("http://blog.jdpfu.com/2014/12/28/learning-linux")  It appears there is much background that would be helpful to you in the first 5 links on that page, especially the free PDF book start sections.

---

### Post by grizdog on 2015-04-26
Thanks very much - some great stuff there.  Yes, I am using 14.04, and while I still can't get it to take directives from the files and links I created in sites-available and sites-enabled, but it does work with the 000-default.conf file and link, so I have my main site up, and that is what it important.

Thanks for the help.

---

### Post by TheFu on 2015-04-26
> **grizdog said:**
> Thanks very much - some great stuff there.  Yes, I am using 14.04, and while I still can't get it to take directives from the files and links I created in sites-available and sites-enabled, but it does work with the 000-default.conf file and link, so I have my main site up, and that is what it important.

Thanks for the help.

In Apache 2.4 they changed the mandatory filenames for conf files.  I was burned by this too ... can't remember the details - thinking out loud ... filename ends in .conf?  Or must it start with 3 numbers and have a dash?  It was something like that.  Wouldn't hurt to recheck the log files in /var/log/apach* (whatever the name is).

I use apache only on 1 remaining website. Everything else switched to nginx about 8 yrs ago.

---

### Post by SeijiSensei on 2015-04-26
Configuration files must end in .conf as required by /etc/apache2/apache2.conf:
```

# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

```
The 000-default.conf file has that name to insure it loads ahead of the virtual host definitions.  Apache loads the files in /sites-enabled/ alphamerically.

---

### Post by grizdog on 2015-04-27
Thanks, folks. And thanks to those who read the post and gave it some thought, even if you didn't post.  I really appreciate the help.

---

