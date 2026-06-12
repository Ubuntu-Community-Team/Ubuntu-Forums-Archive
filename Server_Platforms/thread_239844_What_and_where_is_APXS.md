---
title: "What and where is APXS?"
date: 2006-08-19
forum: Server Platforms
---

### Post by Immerse on 2006-08-19
Hi!

I just installed Ubuntu a couple of hours ago, and it's running fine! I even got Apache2, PHP5 and MySQL running in no time, which surprised me as I've never installed a Linux server before.

Now I want to install the PHP Pecl package APC.

Unfortunately this doesn't go too well:

> 
alex@yuna:/usr/bin$ sudo pecl install apc

/* SNIP */

checking if nawk is broken... no
checking whether apc needs to get compiler flags from apxs...

Sorry, I was not able to successfully run APXS.  Possible reasons:

1.  Perl is not installed;
2.  Apache was not compiled with DSO support (--enable-module=so);
3.  'apxs' is not in your path.  Try to use --with-apxs=/path/to/apxs
The output of /var/tmp/pear-build-root/APC-3.0.11/y follows
/tmp/tmpWZWcLA/APC-3.0.11/configure: line 3197: /var/tmp/pear-build-root/APC-3.0.11/y: No such file or directory
configure: error: Aborting
ERROR: `/tmp/tmpWZWcLA/APC-3.0.11/configure --enable-apc-mmap=y --with-apxs=y' failed


OK, so it's looking for something called APXS. Now, as a linux newbie, I have no idea what that is. I checked the /usr/bin and /usr/sbin directories to see if there's something called apxs in there, but no luck.

I searched these forums, tried google and found some interesting posts, but nothing that was of enough help to fix this problem.

Anyone know what's going on? And how I can install APC?

Thanks!
Alex
:)

---

### Post by kkass on 2006-09-08
Install apache2-threaded-dev

---

### Post by Junx on 2006-09-09
[http://dotdeb.org/](http://dotdeb.org/)

Oh my, that site makes managing a Debian server so much easier (includes more [and up to date] packages).  That way you can just apt-get install php5-apc

---

### Post by Uluen on 2006-09-09
Have you tried the CPAN package for managing Perl? I haven't used it on Ubuntu though.

---

### Post by etcpool on 2006-09-19
after u install 

apache2-threaded-dev


it will be located in

/usr/bin/apxs2 for apache2

and probably in

/usr/bin/apxs for apache1


etc,

---

### Post by spp on 2006-09-22
apxs is the tool for building modules for Apache (apxs2 is for apache2, duh :)).

Anytime you compile against apache, that is what you call as it ensures modules compiled for apache can be loaded into apache.

SP

---

