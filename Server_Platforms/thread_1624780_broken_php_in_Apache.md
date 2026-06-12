---
title: "broken php in Apache"
date: 2010-11-18
forum: Server Platforms
---

### Post by bobnw on 2010-11-18
I messed up my Apache2 config files and reloaded Apache 2      Now  the index page comes up.  but I am no able to open PHP files in Firefox.    I reloaded PHP 5,  restarted Apache  and deleted the cache in Firefox,  but this did not help.  

 What should I try next?

Thanks in advance for your suggestions.

---

### Post by trentscott on 2010-11-18
Are you getting any error messages in your browser? Can you post your Apache logs?

---

### Post by bobnw on 2010-11-18
Thanks for your suggestions. 

when I try to open a PHP fle or a site with index.php,  Firefox pops up a message window that says 
       "you have chosen to open [filename] which is a PHP script
        What do you want to do.."
The message suggest opening the file with Bluefish.  This message does not leave any record in the Apache error log. 

When I restart Apache the error log contains the following

     PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/gd.so' 

A couple of other *.so files are also not found.


root@t160:~# a2enmod php5
returns:
Module php5 already enabled

I expect that there is some text in one of the Apache2 config files that is missing,  I am looking in Google,  but no luck so far.

---

### Post by wongo888 on 2010-11-18
Do those files exist? Can you post:

```
$ ls -l /usr/lib/php5/
```

or try

```
$ ls -l /usr/lib/php5/20090626/gd.so
-rw-r--r-- 1 root root xxxxxx 2010-05-13 20:16 gd.so

```

If the GD shared library is missing or is unreadable by PHP then that is a problem.

Check your php5 load file. Is it similar?

```
$ cat /etc/apache2/mods-available/php5.load | grep php5
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

Copy and paste the actual errors from your error.lo into CODE blocks and post them here:

```
$ cat /var/log/apache2/error.log | grep "PHP Warning"
```

---

### Post by bobnw on 2010-11-19
Thanks again for the information.

I have discovered that the is probably in Firefox .6.12 for Ubuntu,  and not in the Apache setup.  I installed the KDE Konqueror browser and php pages and sites that load with index.php render OK using Konqueror. 

 I tried using Firefox> tools > Clear Recent History with Cache checked,  but it doesn't fix the problem.  This may have has something to do with the my Firefox profile bring on a different partition than Ubuntu.  I will check with the Firefox group and report back when the problem is solved.

---

