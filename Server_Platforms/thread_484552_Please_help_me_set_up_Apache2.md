---
title: "Please help me set up Apache2"
date: 2007-06-25
forum: Server Platforms
---

### Post by spaceW on 2007-06-25
I have been having more trouble setting up Apache than I expected.  Here are my present questions:

I ran into [this problem]("http://www.mail-archive.com/debian-apache@lists.debian.org/msg08762.html").  I had no httpd.conf in /etc/apache2/.  So, I commented out that line in apache.conf.  Should I have a httpd.conf file, or is it ok to go without one?

Now, when I try to restart the server (I don't know that it is started in the first place or not.) I get this:
```
$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...
httpd (no pid file) not running
                                                              [fail]
```

And that is true.  I have no apache.pid file in /var/run.  Should I?

In /var/log/apache2 the access.log is blank.  And error.log has several lines like this:
```
[Mon Jun 25 22:15:23 2007] [error] (2)No such file or directory: Cannot create SSLMutex with file '/var/run/apache2/ssl_mutex'
Configuration Failed
```

Does that mean that I should have an apache2 directory in /var/run ?
Or do I need to know more about ssl_mutex?

I would really appreciate any help.
-spaceW

---

### Post by got_nix on 2007-06-26
HOw did you install apache 2? manually or via apt-get? if via apt then you shouldn't be having this problem

Try looking through your apache config n seeing if you find any occurences of sslmutex maybe try commenting it out. and then restarting the service (which it seems your having difficulty doing as wel). you could opt to uninstall and re-install. 

dunno I've never had much problem with appache except not having a FQDN

---

### Post by spaceW on 2007-06-26
Thanks for the reply got_nix.  

I installed apache with apt-get (or aptitude, I don't know which.)  I installed Ubuntu just a few days ago with the server edition.  I think it gave me some stuff related to Apache at least.  I have also tried messing around with svn and ssl a bit, but I don't think those are giving me my current problems.

I checked my aptitude.conf and there is no occurrence of "ssl".  I do have an ssl folder in /etc/apache2.  And there are a few lines for ssl in one of my sites-available files.

I still don't know why I don't have a httpd.conf or what it is meant to contain, or if I should have one.

Similarly, I don't know what it means for there to be no apache.pid file.  Those files only store a number for the operating system to keep track of them, right?

You might be onto something with that uninstall and reinstall idea.  I did try that with just the apache2 package.  Maybe I should try apt-get autoremove to get rid of all of the dependencies.  I will try that if I can't figure anything else out.

---

### Post by spaceW on 2007-06-26
YES!!! finally!  I can see the "It Works!" page!  gaaaah!

What I did:
```
/var/run$ sudo mkdir apache2
```
and then
```
$ sudo /etc/init.d/apache2 start
```

And it started!!!  I have an apache.pid file now!  good.

I wouldn't have thought that the existence of a folder would make such a difference.

But I am still wondering about the httpd.conf, but as long as things are working, it's not a big deal.

Thanks again nix

---

### Post by got_nix on 2007-06-26
ahh yeh sure. and i wasn't talking about your apt config but your apache2.conf. matters not either way you got it working. congrats. I'm trying to figure out why the set up via apt-get didn't create the folder for you.

---

### Post by spaceW on 2007-06-26
Oops, I think I meant to write apache.conf and not aptitude.conf.  Haha.

Yeah... about that folder, IDK.  But it is working!

Now, I just have to figure SVN, Trac, and hopefully Ruby on Rails out. : )

---

### Post by juantao on 2007-06-26
I'm new to apache2 as well and was also confused about the httpd.conf file being empty. I think I have this right and that is apache2 has backwards compatibility for using a httpd.conf file if you want to (I am) but it's not needed as there is a 'new fangled' method of doing virtual hosting using the 'sites-available' directory or some such thing, but for me - I merely copied the 'virtual hosts' section of my old apace1 httpd.conf file into the blank httpd.conf file that came with the LAMP server and restarted apache and BAM! there's my domains!

---

