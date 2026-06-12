---
title: "php server"
date: 2006-12-29
forum: Server Platforms
---

### Post by dskloet on 2006-12-29
Hi,
I want my web server to parse php but when I open the php file from [http://localhost](http://localhost) my browser wants to download it. I installed **apache2** and **libapache2-mod-php5** and ran **a2enmod php5** and **/etc/init.d/apache2 restart**, but it didn't help. Any ideas?
Thanks in advance.

---

### Post by Brazen on 2006-12-29
> **dskloet said:**
> Hi,
I want my web server to parse php but when I open the php file from [http://localhost](http://localhost) my browser wants to download it. I installed **apache2** and **libapache2-mod-php5** and ran **a2enmod php5** and **/etc/init.d/apache2 restart**, but it didn't help. Any ideas?
Thanks in advance.

I'm not sure what dependancies are grabbed by libapache2-mod-php5.  Is php5 also installed?  You can try "sudo apt-get install php5" and see if it installs anything.

---

### Post by dskloet on 2006-12-29
Yes, php5 is already installed.

---

### Post by Brazen on 2006-12-29
> **dskloet said:**
> Yes, php5 is already installed.

The other thing I've heard then is this is a problem from your browser.  Try accessing it from a different workstation or try a different browser.

There really isn't that much to getting php on Apache running.  Really, in my notes (which I have copy/pasted from many times), my install instructions for a webserver is one line:

```
sudo apt-get update && sudo apt-get -y install php5-mysql php5-mcrypt php5-gd
```

Just a note: I install the php5-mysql package, but I do NOT use a webserver as a database server; MySQL goes on a seperate server.  Also, the Apache php plugin should be enabled by default, no need for a2enmod.  This line of command also grabs apache as a dependency; this is really the only thing I do to setup a webserver (other than putting html and php files on it of course, and installing the base system, of course).

One more thing:  I've heard of this problem existing on Edgy, but I have not heard of it on Dapper.  I would suggest using Dapper regardless.

---

### Post by Stillness on 2006-12-29
I had this problem, but fixed itself after totally closing out my browsing app and opening it again, i'm guessing there was some kind of caching involved.

---

### Post by Brazen on 2006-12-29
oh, also, I meant to mention... you tried stopping and restarting the Apache service, right?

---

### Post by dskloet on 2006-12-29
Yes, I did try. But apparently I even failed to shut down apache (1 not 2). I think it's working now but I'm afraid that when I reboot it will be apache running again instead of apache2. Any idea how I make it so that apache2 with php is running from startup?
Thanks.

---

### Post by Brazen on 2006-12-29
Not sure.  I always use Webmin to control what services start at boot.

---

### Post by dskloet on 2006-12-29
Thanks, I'll look at it.
The web server doesn't seem to do anything with my .htaccess. Is there anything I should install? I believe what I need is the Rewrite module but I thought is was included.

---

### Post by Brazen on 2006-12-29
the rewrite module is included, but not enabled by default ( do "sudo a2enmod rewrite" and then reload Apache).  You do not need rewrite for .htaccess files to work (unless you are using rewrite rules in your .htaccess, of course).

Whether or not Apache uses .htaccess files depends on the AllowOverride directive.  If there is no AllowOverride directive, then it defaults to "all" which is what you want.  This directive MUST be under your <directory> options for the directory containing the .htaccess file (otherwise it uses the default of "all").  However, Ubuntu may have changed this default (maybe for security reasons?).  Either way, you can try adding "AllowOverride all" under your <directory> options for the directory containing the .htaccess file.

---

### Post by dskloet on 2006-12-29
I removed both apache and apache2 and the installed apache2 and php5 again, hoping to get a more clean install. But now php isn't working again. And also, I can't start the server with **/etc/init.d/apache2 start** but I can stop it with **/etc/init.d/apache2 stop** (after starting it with **/usr/sbin/apache2**).
I feel so stupid.

Edit: I started it with **/usr/sbin/apache2ctl** and now it works... what is this ctl anyway?

---

### Post by dskloet on 2006-12-29
I do want to use rewrite rules but I don't believe it's working at all.
My **/var/www/.htaccess** now contains```
Order Deny,Allow
Deny from All
```
But I'm still able to access [http://localhost/](http://localhost/)
I'm not sure what you mean by "<directory> options", where do I find those?
Thanks.

---

### Post by Brazen on 2006-12-29
You never answered: is this Edgy or Dapper?

You might try uninstalling everything again, but use the --purge option.  Then reinstall everything again, maybe try using the install line I posted above.

Apache2ctl is a program installed by Apache, but the /etc/init.d/apache2 start should work (as  you know).

As for the <directory> options:  Look in /etc/apache2/sites-available/default.  This is where all your configurations should go.  There is a section there between <directory /var/www> and </directory> tags.  That is where the "AllowOverride all" needs to be.

---

### Post by not_cool on 2006-12-29
> **Brazen said:**
> You might try uninstalling everything again, but use the --purge option.  Then reinstall everything again, maybe try using the install line I posted above.

I had the same problem, having the browser want to download the php files, and I fixed it by going into synaptic and selecting the completely remove option for ALL of the packages (apache, php) and then reinstalled them. You can also do this with "aptitude purge package." See this [post]("http://ubuntuforums.org/showthread.php?t=325555"), it is the exact same problem.

---

### Post by Brazen on 2006-12-30
> **not_cool said:**
> I had the same problem, having the browser want to download the php files, and I fixed it by going into synaptic and selecting the completely remove option for ALL of the packages (apache, php) and then reinstalled them. You can also do this with "aptitude purge package." See this [post]("http://ubuntuforums.org/showthread.php?t=325555"), it is the exact same problem.

The "completely remove" option in Synaptic is the same as the "--purge" option in apt-get.

---

### Post by dskloet on 2006-12-31
> **Brazen said:**
> You never answered: is this Edgy or Dapper?
Oh, I thought you could see that at the upper right of my post. It's Edgy.

I found the directory option. It said "AllowOverride None" so I changed that to "All" and now it works. Thanks a lot!

---

