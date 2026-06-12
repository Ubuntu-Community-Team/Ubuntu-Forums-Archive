---
title: "Ubuntu server up-to-date?"
date: 2020-01-06
forum: Server Platforms
---

### Post by diktio on 2020-01-06
Hi,

I have a question about an Ubuntu server running 16.04.6 LTS (xenial). On this server is installed Nginx, MariaDB and PHP. I am updating the server via apt-get update and apt-get upgrade. 

What I would to know if the server and packages are up-to-date with the latest updates because of security? 

I have been looking on the Ubuntu website and I can see this are the latest versions. 

nginx                          1.10.3-0ubuntu0.16.0
mariadb-server            10.0.38-0ubuntu0.16
PHP 7.0.33-0ubuntu0.16.04.7 (cli) ( NTS )
Copyright (c) 1997-2017 The PHP Group


Do I need to upgrade to the latest versions of Nginx, mariadb, php? Or can I keep using those version safely without the new functionality in newer versions? 


What happens when I upgrade to version 18.04.3 LTS? Are the packages Nginx, mariadb and php also upgraded? 

Regards,

Rob

---

### Post by deadflowr on 2020-01-06
Ubuntu patches for security and light bug fixes when they can.
the goal is to keep things as stable as possible.

Packages from the Ubuntu repositories get upgraded to whatever the versions are on the new release
when upgrading to a newer Ubuntu release.

---

### Post by TheFu on 2020-01-06
> **diktio said:**
> 
What happens when I upgrade to version 18.04.3 LTS? Are the packages Nginx, mariadb and php also upgraded? 


Always make a know-you-can-restore backup AND test any upgrades on non-production systems before doing them on live, production, machines.  Sometimes upgrade fail. Sometimes that failure is small and sometimes it is a major failure.  

Had an email communications server that took me 5 attempts to do a migration from LTS to LTS before I got it right.
About a year ago, I migrated about 10 systems.  8 of them went cleanly, with just config changes needing to be updated due to changes in server software versions.  Do not expect those config changes due to server version upgrades to be automatically handled. Except it will not.
   2 migrations needed some special care after some failure.  Of those 2, 1 took me over 6 hrs to solve the failure.  It was because I had specific, different, versions of perl installed for my development which were found and used during the upgrades instead of the system perl version.  I ended up starting from a fresh install and migrating data, then doing fresh installs of the specific services/daemons on that machine.  I tried 3 times first before giving up the "upgrade" method.

I believe that is representative - 80% of the time, things are reasonable and just configuration changes need to be manually handled. Then 20% need lots of manual help.  

YMMV. Of course.

---

### Post by LHammonds on 2020-01-06
For security reasons, you really should keep the OS updated along with the associated application systems.   Staying on an old version of Ubuntu and forcing installs of newer applications...or...updating to newer version of Ubuntu and forcing older versions of applications can cause issues.  The application might mandate this scenario but then the security risk is now on those requiring the use of that application and the company supporting it.

You need to ENSURE/VERIFY you have a good backup of your system before doing anything.

When a new OS comes out and start creating virtual machines of the new OS and documenting how to install and configuring them like I did for the prior version.  Once I am familiar enough with the OS and basic packages, I then start to setup the latest versions of the application systems and document how to get them running.  The last step is setting up replacement servers for existing older servers by installing the new OS, new application and migrating the data over and see if I can get the system running on the new software.  Once I validate that I can get the system running, I make sure my documentation on how I did it is solid and then do it again with the intent of replacing the old server.

If you are running virtual servers, it is as simple as just swapping the IP address once migration is complete.  If you are running baremetal servers and do not have another physical server to migrate to, it becomes a bit more labor intensive.

You could also do an in-place upgrade but make sure you test this as best as you can such as restoring your backup into a virtual machine and doing the upgrade there to see how it goes.  But because it is different environments, there is no guarantee that the process will work the same.

LHammonds

---

### Post by diktio on 2020-01-07
Thanks,

Steps to follow;

- create a good back-up 
- Document application systems 
- better control when migrating than upgrading. 
- keep the existing OS (16.04) and applications updated ( with apt-get update and apt-get upgrade). How do I keep the mentioned application updated, is running apt-get update and apt-get upgrade enough to keep the applications secure, PHP, MariaDB, Nginx, Sendmail ? 
- build a new server with new OS, new applications and migrate data. ( change IP address) 

How do I keep the mentioned application updated, is running apt-get update and apt-get upgrade enough to keep the applications secure, PHP, MariaDB, Nginx, Sendmail ? 

Regards,

Rob

---

### Post by TheFu on 2020-01-07
No.  Security isn't just about patching, but that is an important part.  The underlying code has to be created with security in mind and those programmers have to be skilled.  Over the decades, I've found that average php programmers are terrible at security.  The ease that php can be slapped together is both a good thing to encourage beginners and a liability because lots of published code is written by beginners and full of problems.

The other tools have liabilities because they are each highly configurable to meet the needs for different environments.  In general, the administrator is responsible for understanding the needed configuration and setting up not just the local configuration, but setting up the network protections to prevent bad packets from even accessing the server(s) or daemons.

Because there are thousands of different needs for each of those tools, depending on the local requirements, it is impossible for anyone but the local administrator to know which settings will be secure for any specific setup.

---

### Post by SeijiSensei on 2020-01-07
> **TheFu said:**
> Over the decades, I've found that average php programmers are terrible at security.  The ease that php can be slapped together is both a good thing to encourage beginners and a liability because lots of published code is written by beginners and full of problems.
That's not really a criticism of the security of the PHP interpreter itself though. The folks at Zend are pretty conscious of security issues.

PHP 7 deprecates some things that PHP 5 supported, particularly the regular expression functions like ereg(). PHP 7 pretty much now supports only Perl-compatible regular expressions, e.g., preg_match().  I had to go back and rewrite the code in some of my applications to handle this change.  

At this point I'd consider waiting a few months until 20.04 LTS is released in April. If you have a test server (e.g., one running as a VM in an app like VirtualBox), you can start testing with the 20.04 beta: [http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/)

---

### Post by TheFu on 2020-01-07
> **SeijiSensei said:**
> That's not really a criticism of the security of the PHP interpreter itself though. The folks at Zend are pretty conscious of security issues. 

Professionally written php webapps that have been configured correctly aren't nearly as likely to have simple security issues as those created by relative noob programmers.  That is true for all languages, C, C++, Perl, Java, Lisp, Erlang, Ruby, Python, Javascript, whatever.  Core parts of those tools, when properly configured, have reasonable security.  If there are addons, created by relatively new programmers, then those would be where my greatest concern would lay.  It is well-understood that wordpress themes and addons often cause security problems for the entire wordpress php webapp.  That isn't because wordpress is created by non-professionals. It is because the people often creating themes and addons aren't professionals or don't fully understand the correct ways to securely integrate into wordpress.

I've assumed that Nginx and mariadb are written by programmers with greater experience. I'm very comfortable with that assumption and use both of those tools myself, nginx extensively.  I use a few php webapps, but don't trust them enough to allow them to be available on the internet.  Wallabag and Nextcloud.  I also don't allow ZNC (an IRC bouncer) to be directly accessed on the internet.

These same consideratins apply to all programming languages and all programmers.

---

### Post by #&amp;thj^% on 2020-01-07
Just adding my 2 cents worth here, PHP is a popular language for web development. It is so popular that In some cases companies do run a few bounty programs in which they invite different security experts to analyse their application/'s from the core and suggest critical PHP security best practices for it. 
I subscribe to TheFu's rational for trust issues.
PHP is the most criticized scripting language when it comes to security. : [https://www.cloudways.com/blog/php-security/](https://www.cloudways.com/blog/php-security/)

---

### Post by SeijiSensei on 2020-01-07
Again, that link at cloudways describes common security problems in PHP programming (protecting against cross-site scripting attacks, SQL injection, etc.). It's not an indictment of the security of the application itself.

---

