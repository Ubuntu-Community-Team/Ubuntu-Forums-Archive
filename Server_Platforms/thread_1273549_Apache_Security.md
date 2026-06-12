---
title: "Apache Security"
date: 2009-09-23
forum: Server Platforms
---

### Post by johnnywins on 2009-09-23
Hi everyone, thanks in advance for any help you can provide.

I just got my Apache2 Webserver set up on my Ubuntu 9.04.  Now I need to make sure it is secure.

I am in the process of creating my own website and I want to have a Members Only section so that only people who have usernames and passwords created by me can access specific pages of the site.

So basically, the home page is index.html.  From there, I want to have two main links, one for Members and one for Non-Members.  I want members to be prompted for username/password once they click the links, then be taken to members.html.  I want to create accounts for specific people.  What is the easiest way to do that?

Also what other secutiry settings to I need to get set up in order to protect myself? 

Thanks!

---

### Post by openfly on 2009-09-23
apache can do what's called "basic" http auth.  This is accomplished using either an .htaccess file or in the directory parameters of your apache's config for that site... be it a vhost or the default.

---

### Post by mihalisla on 2009-09-24
Why won't you setup apparmor to secure your apache server?
There are plenty tutorials of apparmor in the forum.
 You should also have a look at this : 
[http://ubuntuforums.org/showthread.php?t=1142222](http://ubuntuforums.org/showthread.php?t=1142222)

That should do

---

### Post by johnnywins on 2009-09-24
Thanks guys I figured it out.  This was the link I needed: [http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html)

---

### Post by TheFuturian on 2009-09-24
Hi All,

I'd be really interested to hear if there are any steps other then .htaccess and frequent updates that are required in order to safely host a webserver on the net? I have checked out the apparmour tutorial, I am running 8.04LTS at the minute so it looks like I could be in for a hard time if I was to install the mods.. My I ask if it is still safe to use my LAMP setup for t~internet purposes in today's climate?

---

### Post by TheFuturian on 2009-10-09
Looks like I'm on my own? :(

---

### Post by lykwydchykyn on 2009-10-09
You have kind of a wide open question there... 

In theory Apache should be secure out of the box, and should flaws & exploits arise they should be patched (and the patches made available via updates).

Other than that, mod_chroot might be of interest to you:

[https://wiki.ubuntu.com/ModChroot](https://wiki.ubuntu.com/ModChroot)

I've never heard of any major "you-must-do-this-extra-thing-or-you-will-be-HACKED!" issues with Apache, but then security is always relative.

---

### Post by kathir678 on 2009-10-10
In typical operation, Apache is started by the root user,     and it switches to the user defined by the [**User**]("http://httpd.apache.org/docs/1.3/mod/core.html#user")     directive to serve hits. As is the case with any command that     root executes, you must take care that it is protected from     modification by non-root users. Not only must the files     themselves be writeable only by root, but also the     directories and parents of all directories.If you allow non-root users to modify any files that root     either executes or writes on then you open your system to root     compromises. For example, someone could replace the httpd     binary so that the next time you start it, it will execute some     arbitrary code. If the logs directory is writeable (by a     non-root user), someone could replace a log file with a symlink     to some other system file, and then root might overwrite that     file with arbitrary data. If the log files themselves are     writeable (by a non-root user), then someone may be able to     overwrite the log itself with bogus data.
___________________________________________________________
[number plates](http://www.4plates.co.uk/builder.asp)  [laboratory automation](http://labface.com/Laboratory-Automation-7)

---

### Post by TheFuturian on 2009-12-08
> **lykwydchykyn said:**
> You have kind of a wide open question there... 

In theory Apache should be secure out of the box, and should flaws & exploits arise they should be patched (and the patches made available via updates).

Other than that, mod_chroot might be of interest to you:

[https://wiki.ubuntu.com/ModChroot](https://wiki.ubuntu.com/ModChroot)

I've never heard of any major "you-must-do-this-extra-thing-or-you-will-be-HACKED!" issues with Apache, but then security is always relative.

> **kathir678 said:**
> In typical operation, Apache is started by the root user,     and it switches to the user defined by the [**User**]("http://httpd.apache.org/docs/1.3/mod/core.html#user")     directive to serve hits. As is the case with any command that     root executes, you must take care that it is protected from     modification by non-root users. Not only must the files     themselves be writeable only by root, but also the     directories and parents of all directories.If you allow non-root users to modify any files that root     either executes or writes on then you open your system to root     compromises. For example, someone could replace the httpd     binary so that the next time you start it, it will execute some     arbitrary code. If the logs directory is writeable (by a     non-root user), someone could replace a log file with a symlink     to some other system file, and then root might overwrite that     file with arbitrary data. If the log files themselves are     writeable (by a non-root user), then someone may be able to     overwrite the log itself with bogus data.
___________________________________________________________
[number plates](http://www.4plates.co.uk/builder.asp)  [laboratory automation](http://labface.com/Laboratory-Automation-7)

These two replies are ace! Just wish I'd been back to read them sooner. Thanks :D

---

### Post by HighCommander540 on 2009-12-08
> **kathir678 said:**
> In typical operation, Apache is started by the root user,     and it switches to the user defined by the [**User**]("http://httpd.apache.org/docs/1.3/mod/core.html#user")     directive to serve hits. As is the case with any command that     root executes, you must take care that it is protected from     modification by non-root users. Not only must the files     themselves be writeable only by root, but also the     directories and parents of all directories.If you allow non-root users to modify any files that root     either executes or writes on then you open your system to root     compromises. For example, someone could replace the httpd     binary so that the next time you start it, it will execute some     arbitrary code. If the logs directory is writeable (by a     non-root user), someone could replace a log file with a symlink     to some other system file, and then root might overwrite that     file with arbitrary data. If the log files themselves are     writeable (by a non-root user), then someone may be able to     overwrite the log itself with bogus data.
___________________________________________________________
[number plates](http://www.4plates.co.uk/builder.asp)  [laboratory automation](http://labface.com/Laboratory-Automation-7)

> **lykwydchykyn said:**
> You have kind of a wide open question there... 

In theory Apache should be secure out of the box, and should flaws & exploits arise they should be patched (and the patches made available via updates).

Other than that, mod_chroot might be of interest to you:

[https://wiki.ubuntu.com/ModChroot](https://wiki.ubuntu.com/ModChroot)

I've never heard of any major "you-must-do-this-extra-thing-or-you-will-be-HACKED!" issues with Apache, but then security is always relative.

There is actually one other thing that I would like to point out that Ubuntu itself. Says is really a flaw (but they still keep it for some reason.

In the file "/etc/apache2/sites-available/default" there is a section of code that looks like this:

```
<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
```

This is very insecure, because then users can view any file pretty much that they want on the server. Only in certain cases (but it still works). So you need to change it to this:

```
<Directory />
		Options FollowSymLinks
		AllowOverride None
		Deny from all
	</Directory>
```

This is actually on the wiki page for directory securing that Ubuntu provides.

---

