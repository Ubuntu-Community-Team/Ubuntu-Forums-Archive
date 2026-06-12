---
title: "httpd (no pid file) not running"
date: 2008-07-10
forum: Server Platforms
---

### Post by antilog on 2008-07-10
So I was getting a
```
 httpd (pid xxxx?) not running 
```
So I followed this instruction:
[http://ubuntuforums.org/showthread.php?t=573126]("http://ubuntuforums.org/showthread.php?t=573126")

And am now getting 

```
 httpd (no pid file) not running 
```

Googling, searching these forums, restarting Apache2 and rebooting is not helping.

Any ideas?

Thanks

---

### Post by antilog on 2008-07-10
So I had created VirtualHosts.  Viewing the /var/log/apache2/error.log, I found errors for the specific domain error logs missing.  I mkdir ' ed the folders I specified in the sites-available, rebooted, and it is serving up html.

Now to get VirtualHosts working...

Thanks for the help.

---

### Post by carcdrcdr on 2008-07-10
Hehe, I hate when that happens :(  I just had this issue a few weeks back on a Solaris 10 boxen... anywho it should like the way you are starting apache is NOT leaving a pid file.

So first off how are you starting apache?  With
$ apache2ctl -k start
or
$ /etc/init.d/apache2 start

Second:
In your apache2.conf (should be /etc/apache2/apache2.conf) what do you get when you run a:
```
grep -i pidfile /etc/apache2/apache2.conf
```

---

### Post by antilog on 2008-07-10
Oh sorry I didn't make it more clear:

looking at the error log showed that apache2 couldn't find my specific domain error logs specified in my sites-available configs (none of the virutalhosts tutorials mentioned having to create each individual error directory, along with not mentioning a lot of other necessary details!!!), so I created the directories, rebooted, and it is now working.  So the lesson I learned that instead of literally figuring out how to create the pid, look at the erro log and see what is preventing apache2 from recreating the pid upon restart.

Thanks for the reply!

---

### Post by wlan-11g on 2009-07-21
Hello all, 

Getting the same error as the OP, but I have no idea how to troubleshoot the issue

I checked the error.log 

Output from errorlog:

Sun Jul 19 21:34:09 2009] [error] Insecure dependency in chdir while running with -T switch at /usr/share/perl/5.8/File/Path.pm line 178.\nCompilation failed in require at (eval 5) line 1.\n
[Sun Jul 19 21:34:09 2009] [error] Can't load Perl file: /usr/share/request-tracker3.4/libexec/webmux.pl for server 127.0.1.1:0, exiting...
[Mon Jul 20 20:39:52 2009] [error] Insecure dependency in chdir while running with -T switch at /usr/share/perl/5.8/File/Path.pm line 178.\nCompilation failed in require at (eval 5) line 1.\n
[Mon Jul 20 20:39:52 2009] [error] Can't load Perl file: /usr/share/request-tracker3.4/libexec/webmux.pl for server 127.0.1.1:0, exiting...
[Tue Jul 21 21:45:00 2009] [error] Insecure dependency in chdir while running with -T switch at /usr/share/perl/5.8/File/Path.pm line 178.\nCompilation failed in require at (eval 5) line 1.\n
[Tue Jul 21 21:45:00 2009] [error] Can't load Perl file: /usr/share/request-tracker3.4/libexec/webmux.pl for server 127.0.1.1:0, exiting...

---

### Post by wlan-11g on 2009-07-21
Any suggestions?

---

### Post by johannesri on 2011-06-23
this fixed it for me:
```
/bin/hostname -F /etc/hostname
```

thx to [http://www.linuxquestions.org/questions/linux-server-73/httpd-no-pid-file-not-running-607589/#post2994568](http://www.linuxquestions.org/questions/linux-server-73/httpd-no-pid-file-not-running-607589/#post2994568)

---

