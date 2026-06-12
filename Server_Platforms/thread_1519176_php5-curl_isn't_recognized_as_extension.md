---
title: "php5-curl isn't recognized as extension"
date: 2010-06-27
forum: Server Platforms
---

### Post by Jon914 on 2010-06-27
I'm developing a Facebook app, and curl is required for that. The problem is that no matter what I do, php isn't recognizing curl.

What I did:

1) I installed curl and php5-curl from the package manager.
2) I edited /etc/php5/apache2/php.ini and added extension=curl.so
3) I restarted apache. No luck so far.
4) I double-checked that I was editing the correct php.ini based on phpinfo(). I was.
5) I checked phpinfo() to see the extensions directory and visited that directory. curl.so is in there.
6) I checked /etc/php5/apache2/conf.d/ and found curl.ini in there, with the proper contents.

The one clue I have is that when I look at phpinfo(), the other ini's are loaded, but curl.ini is conspicuously missing. Moreover, other PHP extensions such as GD are loading in properly.

Where could this be going wrong?

Thanks!

---

### Post by Ryan Dwyer on 2010-06-27
You shouldn't need to edit php.ini. When you install php5-curl it puts curl.ini in /etc/php5/apache2/conf.d/ which contains extension=curl.so. So your PHP is trying to load the extension twice.

Undo your changes to php.ini then restart Apache.

---

### Post by Jon914 on 2010-06-28
Thanks for your help. Unfortunately, that doesn't work.

Here's part of phpinfo(), if this helps. The server's running on 9.04.

```
PHP Version 5.2.6-3ubuntu4.5

Server API	Apache 2.0 Handler
Virtual Directory Support	disabled
Configuration File (php.ini) Path	/etc/php5/apache2
Loaded Configuration File	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files	/etc/php5/apache2/conf.d
additional .ini files parsed	/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini
PHP API	20041225
PHP Extension	20060613
Zend Extension	220060519

[...]

extension_dir	/usr/lib/php5/20060613+lfs
```

---

### Post by Ryan Dwyer on 2010-06-28
That sure is strange. I don't suppose curl.ini has a different owner or permissions than the other files?

If it's the same as the others, my next step would be to apt-get purge php5 and php5-curl then reinstall them.

---

### Post by Jon914 on 2010-06-28
Nope, I just checked and found that it has the same permissions/owner. The only other thing that perplexes me is that other extensions like gd and mysql are in the same folder and load up just fine. I also noticed another extension in that directory, mcrypt, which does not load up (but I don't care about that).

I guess I'll try the reinstall option unless anyone else has other ideas.

---

### Post by teeny2000 on 2011-01-08
Hi,
 
first i had same problems.
 
Reading the command-line output during 'sudo apt-get install php5-curl' gave me the final hint: Some packages could not be installed.
 
Solution for my case was to update the packagelists and run a new install:
sudo apt-get update
sudo apt-get install php5-curl
 
(no configuration at php.ini was needed)
 
maybe this helps - good luck.
 
GJ

---

