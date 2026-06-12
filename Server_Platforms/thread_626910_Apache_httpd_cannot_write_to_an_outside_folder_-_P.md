---
title: "Apache httpd cannot write to an outside folder - Permission denied"
date: 2007-11-29
forum: Server Platforms
---

### Post by zbog on 2007-11-29
I have Ubuntu 7.10 (desktop version). I'm trying to build a site in php + apache (lamp), but I stumbled on a problem: I need to give apache read/write access outside /var/www.

I have installed the apache and php packages from repository.
I heard it is much safer to keep certain files outside the space publicly available (outside /var/www). I have set up /var/outside for this purpose. In this outside folder I keep database settings files, session objects and Smarty templates and compiles.

Now, although both /var/www and /var/outside are owned by root:
drwxr-xr-x  5 root root  4096 2006-08-07 19:13 outside
drwxr-xr-x  4 root root  4096 2007-11-27 09:15 www
my Apache httpd / PHP cannot write to /var/outside, as it outputs the following:
*Warning: session_start() [function.session-start]: open(/var/outside/core/sessions/sess_5cb11fbd2458ae5f3f768c47f706cd78, O_RDWR) failed: Permission denied (13) in /var/www/exo/index.php on line 25*

Here is my process table:
ps aux | grep apache
root      7361  0.0  1.0  32756 10832 ?        Ss   20:16   0:00 /usr/sbin/apache2 -k start
www-data  7442  0.0  0.6  33236  6564 ?        S    20:16   0:00 /usr/sbin/apache2 -k start
www-data  7443  0.0  1.0  34880 11220 ?        S    20:16   0:00 /usr/sbin/apache2 -k start
www-data  7444  0.0  0.6  33236  6512 ?        S    20:16   0:00 /usr/sbin/apache2 -k start
www-data  7445  0.0  0.6  33236  6500 ?        S    20:16   0:00 /usr/sbin/apache2 -k start
www-data  7447  0.0  1.0  34948 10844 ?        S    20:16   0:00 /usr/sbin/apache2 -k start
www-data  8261  0.0  0.5  33104  5956 ?        S    20:56   0:00 /usr/sbin/apache2 -k start
www-data 15905  0.0  0.5  33104  5956 ?        S    21:43   0:00 /usr/sbin/apache2 -k start
www-data 15908  0.0  0.5  33104  5956 ?        S    21:43   0:00 /usr/sbin/apache2 -k start
www-data 15909  0.0  0.5  33104  5956 ?        S    21:43   0:00 /usr/sbin/apache2 -k start

To enable read/write from Apache do I need to change ownership of /var/outside to www-data?
How do I know under what user does apache run? How can I change that?

---

### Post by crouton on 2007-11-29
While /var/www might be owned by root, the folders underneath are likely? owned by www-data.  www-data is the apache 'user' and 'group'.

So you could try changing /var/outside to be owned by www-data:www-data and see if your website can write to it.

---

### Post by zbog on 2007-11-30
I did this:
*sudo chown -R www-data /var/outside*
And **it works!!!** Now apache can happily write to /var/outside !
Many thanks from a happy user!

However I have another question:

here is the contents of /var/www (zbog is my username):
zbog@bogdan:/var$ ls -lt /var/www
total 8
drwxr-xr-x 3 zbog zbog 4096 2007-11-27 22:38 exo
drwxr-xr-x 2 zbog root 4096 2007-11-23 07:46 apache2-default

Should I change ownership of these subfolders to www-data?
will it be more secure? What advantages would I have?

---

### Post by crouton on 2007-11-30
Because you have World read/execute access (last 3 chars in the permission string) there's nothing wrong with either folder as it is.  If you're up to some slightly heavy reading, [http://httpd.apache.org/docs/2.2/misc/security_tips.html](http://httpd.apache.org/docs/2.2/misc/security_tips.html) has some general security tips for Apache 2.2.

I can't find anything that specifically states that the folders should be owned by a specific user/group.  However, www-data:www-data appears to be the default so... choose wisely. :)

---

