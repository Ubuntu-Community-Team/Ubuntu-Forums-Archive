---
title: "[SOLVED] Apache localhost only lets me download unparsed files."
date: 2008-08-10
forum: Server Platforms
---

### Post by Jesdisciple on 2008-08-10
I'm seeing symptoms similar but different to those I described at [XAMPP Crippled by KDE?]("http://ubuntuforums.org/showthread.php?t=881392")  (By the way, the stuff about redirecting was incorrect.  An HTML file was in the server root; I was looking in the wrong folder.)

No files give any content in the browser.  All of them are simply downloaded; no PHP is ever parsed.  And although that HTML file that tricked me before is now deleted, Apache continues to serve it normally if I request the root (localhost/).  If I explicitly request it (localhost/index.html), I get 404.

This is the only thing I know to post; the second command was involved in solving that other problem.```
chris@Jesdisciple-laptop:~$ sudo /etc/init.d/apache2 stop
 * Stopping web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
chris@Jesdisciple-laptop:~$ sudo netstat -n -atp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      5264/mysqld     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      18469/smbd      
tcp        0      0 0.0.0.0:20433           0.0.0.0:*               LISTEN      6354/python     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5186/cupsd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      18469/smbd      
tcp        0      0 127.0.0.1:20433         127.0.0.1:45457         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45450         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45456         TIME_WAIT   -               
tcp        0      0 192.168.1.64:55683      64.233.167.18:80        ESTABLISHED 4595/firefox    
tcp        0      0 192.168.1.64:36955      72.14.223.18:80         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45464         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45447         TIME_WAIT   -               
tcp        0      0 192.168.1.64:55278      66.151.149.78:80        ESTABLISHED 4595/firefox    
tcp        0      0 127.0.0.1:20433         127.0.0.1:45449         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45460         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45465         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45461         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45448         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45459         TIME_WAIT   -               
tcp        0      0 127.0.0.1:20433         127.0.0.1:45463         TIME_WAIT   -               
chris@Jesdisciple-laptop:~$
```

---

### Post by Jesdisciple on 2008-08-11
Update:  Now that [I set ServerName]("http://ubuntuforums.org/showthread.php?p=5567798"), I can view normal HTML files and traverse the filesystem, but PHP files are still downloaded unparsed.

Also, my server's IP address is 127.0.1.1 instead of 127.0.0.1...  Why would that be?

---

### Post by MJN on 2008-08-11
> **Jesdisciple said:**
> Update:  Now that [I set ServerName]("http://ubuntuforums.org/showthread.php?p=5567798"), I can view normal HTML files and traverse the filesystem, but PHP files are still downloaded unparsed.

Is the PHP module enabled? Check for php5.load|conf) in /etc/apache2/mods-enabled/ - and post the contents of php5.conf if it's there.

> Also, my server's IP address is 127.0.1.1 instead of 127.0.0.1...  Why would that be?

As mentioned in your other thread you have not told Apache what it is called hence it is being left to work this out for itself. In this instance it has most likely looked at the host machine name (via a system call which is ultimately advised by /etc/hostname) and performed a lookup on that name. In this case the name is 'jesdisciple-laptop' and an entry on your /etc/hosts file maps this name to 127.0.1.1. Fix your Servername as suggested and you will remove this unpredictability that you're now facing.

Note that all 127/8 (i.e. 127.*) address are loopback addresses hence they all refer to the local machine.

Mathew

---

### Post by Jesdisciple on 2008-08-11
> **MJN said:**
> Is the PHP module enabled? Check for php5.load|conf) in /etc/apache2/mods-enabled/ - and post the contents of php5.conf if it's there.There is no filename beginning with "php" in /etc/apache2/mods-enabled/.

> **MJN said:**
> As mentioned in your other thread you have not told Apache what it is called hence it is being left to work this out for itself. ...No, I respectfully insist that this is a different, deeper issue.  Please see my post in the other thread.

---

### Post by MJN on 2008-08-11
> **Jesdisciple said:**
> There is no filename beginning with "php" in /etc/apache2/mods-enabled/.

Okay, that's good - it means the PHP module isn't enabled (and hence no ability to parse PHP). Enable it with **sudo a2enmod php5**

> No, I respectfully insist that this is a different, deeper issue.  Please see my post in the other thread.I've already given you the explanation for what you're seeing in that thread. I suggest leaving the PHP stuff in this thread, and deal with your server naming in your other thread.

Mathew

---

### Post by Jesdisciple on 2008-08-11
```
$ sudo a2enmod php5
Module php5 installed; run /etc/init.d/apache2 force-reload to enable.
$ sudo /etc/init.d/apache2 force-reload
apache2: Syntax error on line 186 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory
   ...fail!
```

---

### Post by MJN on 2008-08-11
That's quite some nested error!

The one we're really interested in is the ultimate one - /usr/lib/apache2/modules/libphp5.so not found. This comes as part of the Apache PHP library which I assumed to be installed by default, but possibly not so install that with **sudo apt-get install libapache2-mod-php5**

Mathew

---

### Post by Jesdisciple on 2008-08-11
OK, the download was successful and it says the module is enabled when I go to enable it.  But I'm still asked to download my PHP.

Maybe the weird behavior is due to the weird history.  After I had determined that the normal LAMP server wasn't fully installing, I tried to get rid of it because XAMPP was working fine.  But I kept getting an error message from apt-get that MySQL couldn't configure itself, which I ignored.

Then I installed KDE which apparently fixed the problem with normal LAMP and so XAMPP stopped working.  The day after I discovered the normal LAMP and started using it (1 or 2 days ago, I think), it stopped working.  I don't think I rebooted my computer in between, but I know I stopped and started LAMP, trying to make it work.  (XAMPP is still behind LAMP just in case this doesn't work.)

Maybe if I tell apt-get to install everything again, it will fix this?

---

### Post by MJN on 2008-08-11
Holy crap, what a mess. I'm not normally one to suggest reinstalling as I prefer to fix the specific problem, but in this case it might prove easier than unpicking the web of previous work.

Have you searched the forums and tried the suggestions given? PHP parsing issues in Apache are one of the all-time FAQs and the solutions are limited in number so working through them should help.

As a parting suggestion, check the Addtype directives are in /etc/apache2/mods-enabled/php5.conf (or at least that's how the handlers are managed in 6.06 - I have a feeling this method may have been superceded in more recent distro versions).

Mathew

---

### Post by Jesdisciple on 2008-08-12
[A dumb question](http://ubuntuforums.org/showpost.php?p=5209729&postcount=3) got it fixed for me.  That figures, lol.

---

