---
title: "Too Many Apaches!!"
date: 2009-08-29
forum: Server Platforms
---

### Post by Paulzy on 2009-08-29
I (for the first time) installed Apache 2.2.8 along with PHP 5.2.4 and MySQL Ver 14.12 Distrib 5.0.51a on Ubuntu 8.0.4.3. So after setting it up getting everything working and running fine, I look at my System Monitor and see multiple listings for the apache2 process ([see attached PNG file]("http://ubuntuforums.org/attachment.php?attachmentid=126758&stc=1&d=1251582347")).

Is this normal to have this many **apache2** processes? :confused:

Paulzy

---

### Post by braiamp on 2009-08-29
This is normal.
 
Apache create treats every time that somebody request something from your web page.

---

### Post by scorp123 on 2009-08-29
> **braiamp said:**
> Apache create treats ...  threads.

But never mind :)

---

### Post by scragar on 2009-08-29
No need to put up with the 8 or 10 if this is a local machine. A smaller number is probably a whole lot better.
```
sudo updatedb

sudo gedit "$(locate /etc/apache2 | grep "mpm.conf")"
```
I'd get a slightly faster way to help you, but ubuntu insists on calling the latest apache releases apache2, rather than the prefered httpd, which is making it very hard to get good solid information on where the config file would be.

---

### Post by hessiess on 2009-08-29
> **braiamp said:**
> This is normal.
 
Apache create treats every time that somebody request something from your web page.

Apache (By default) is multiprosess not multithreaded, you can compile it with a threading MPM (multi processing module), but it breaks a lot of modules which are not thread safe, i.e. mod_php.

---

### Post by Paulzy on 2009-08-30
> **scragar said:**
> No need to put up with the 8 or 10 if this is a local machine. A smaller number is probably a whole lot better.
```
sudo updatedb

sudo gedit "$(locate /etc/apache2 | grep "mpm.conf")"
```
I'd get a slightly faster way to help you, but ubuntu insists on calling the latest apache releases apache2, rather than the prefered httpd, which is making it very hard to get good solid information on where the config file would be.
I did notice that with regard to **httpd**. This is what I would expect (and expected) from I've learned from my OS/2 Apache experience, even XP (though brief as that was). But I don't exactly recall installing it the MPM way. In fact, I did a "straight" installation as followed by this link on both [LAMP and installing Apache/MySQL/PHP individually]("https://help.ubuntu.com/community/ApacheMySQLPHP") - I followed the individual path, step by step.

Also, I did the locate abd found that file here on my system:
```
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-mpm.conf
```

So before I do anything can you explain what needs be edited in the mpm.conf file, or I am reading that command wrong? (yes, probably)

thanks

---

### Post by Paulzy on 2009-08-30
> **scragar said:**
> No need to put up with the 8 or 10 if this is a local machine. A smaller number is probably a whole lot better.
```
sudo updatedb

sudo gedit "$(locate /etc/apache2 | grep "mpm.conf")"
```
I'd get a slightly faster way to help you, but ubuntu insists on calling the latest apache releases apache2, rather than the prefered httpd, which is making it very hard to get good solid information on where the config file would be.

When I did this
```
sudo gedit "$(locate /etc/apache2 | grep "mpm.conf")"
```
I got this:
```
** (gedit:4572): CRITICAL **: gedit_utils_make_canonical_uri_from_shell_arg: assertion `*str != '\0'' failed
: malformed file name or URI.

```

Besides I'm not running the MPM installation of apache, this i knwo.

---

### Post by meditatingfrog on 2009-10-10
I have the same situation.  I checked man apache2, and it does verify that apache will create child processes.  An interesting side note, it also mentions how to start apache in case you forget (like I have) to use /etc/init.d/apache2 start.

---

### Post by windependence on 2009-10-11
So...what is your goal here? Apache is working as it should creating a new process for each connection. It's totally normal - this is how Apache handles multiple connections. It does not take much in resources at all. 

-Tim

---

### Post by Lars Noodén on 2009-10-11
> **Paulzy said:**
> 
Is this normal to have this many **apache2** processes? :confused:


Yes.  As @ scragar   points out, the number in use can be adjusted.  As @ 
hessiess points out, one of the relevant modules is mpm.  I'll add that the other is prefork.

[list]
[*] [mod_mpm](http://httpd.apache.org/docs/2.2/mod/mpm_common.html)
[*] [mod_prefork](http://httpd.apache.org/docs/2.2/mod/prefork.html)
[/list]

Specifically you'll want to look at the following run time directives in /etc/apache2/apache2.conf

    [StartServers](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#startservers)
    [MinSpareServers](http://httpd.apache.org/docs/2.2/mod/prefork.html#minspareservers)     
    [MaxSpareServers](http://httpd.apache.org/docs/2.2/mod/prefork.html#maxspareservers)      
    [MaxClients](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#maxclients)          
    [MaxRequestsPerChild](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#maxrequestsperchild)   
    [MinSpareThreads](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#minsparethreads)     
    [MaxSpareThreads](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#maxsparethreads)      
    [ThreadLimit](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#threadlimit)          
    [ThreadsPerChild](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#threadsperchild)     

If you're the only one using the machine, you won't need as many.  The values need to match the load and respect the limitations of the machine and your network.  

HowToForge has a nice, short introduction in "[Configuring Apache for Maximum Performance](http://www.howtoforge.com/configuring_apache_for_maximum_performance)"

---

