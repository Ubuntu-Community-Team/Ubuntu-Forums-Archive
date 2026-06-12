---
title: "apachectl command not found"
date: 2006-11-23
forum: Server Platforms
---

### Post by satimis on 2006-11-23
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64
Apache2

Apache is running on this server.  On Firefox evoking "localhost/127.0.0.1" started default page of Apache site.

However
$ ps -ef | grep httpd```

satimis   6359  5605  0 23:20 pts/0    00:00:00 grep httpd
```
does not show it is running.

$ sudo apachectl -k graceful```

sudo: apachectl: command not found

```
can't find apachectl

$ which apachectl
No printout

I'm at a lost.  What mistake I have committed?  TIA


B.R.
satimis

---

### Post by MJN on 2006-11-23
> **satimis said:**
> Apache is running on this server.  On Firefox evoking "localhost/127.0.0.1" started default page of Apache site.

However
$ ps -ef | grep httpd```

satimis   6359  5605  0 23:20 pts/0    00:00:00 grep httpd
```does not show it is running.

But I bet **ps -ef | grep apache2** does... ;)

> $ sudo apachectl -k graceful```

sudo: apachectl: command not found

```can't find apachectl

$ which apachectl
No printoutIt's **apache2ctl** you're after... (however, see below)

> I'm at a lost.  What mistake I have committed?  TIAProbably just read the wrong HowTo! :)

To start/stop/restart Apache try **sudo /etc/init.d/apache2 start|stop|restart **as this method suffices to manage most other services so is good practice to get into.

 Mathew

---

### Post by satimis on 2006-11-23
Hi MJN,

Tks for your advice.

> **ps -ef | grep apache2** does
I got it.

$ ps -ef | grep apache2```

root      5364     1  0 22:37 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  5453  5364  0 22:37 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  5454  5364  0 22:37 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  5455  5364  0 22:37 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  5456  5364  0 22:37 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  5457  5364  0 22:37 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  5861  5364  0 23:03 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  5863  5364  0 23:03 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  5864  5364  0 23:03 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
satimis   6628  5605  0 23:58 pts/0    00:00:00 grep apache2

```


> It's **apache2ctl** you're after... (however, see below)
$ which apache2ctl
/usr/sbin/apache2ctl

> Probably just read the wrong HowTo
I followed;
[http://httpd.apache.org/docs/2.0/stopping.html](http://httpd.apache.org/docs/2.0/stopping.html)

> To start/stop/restart Apache try **sudo /etc/init.d/apache2 start|stop|restart **as this method suffices to manage most other services so is good practice to get into.
Noted with tks.


B.R.
satimis

---

### Post by MJN on 2006-11-23
> **satimis said:**
> I followed;
[http://httpd.apache.org/docs/2.0/stopping.html](http://httpd.apache.org/docs/2.0/stopping.html)

Yeah, well what would they know?! ;)

But seriously, the 'official' Apache documentation is not always directly relevent for the various distro-specific variations (i.e. Debian/Ubuntu).

In this case it is, however /etc/init.d/apache2 is akin to an 'intelligent frontend' to apachectl (which is iteself a frontend to httpd) and so is the preferable option to use not only because /etc/init.d/ service control is an essential tool to get used to using but also because the potential 'intelligence' of these scripts can ensure you do the right thing whereas us dumb users might not if left to dabble at the lower levels.

Mathew

---

### Post by satimis on 2006-11-23
Hi Mathew,

Your advice noted with tks.

On searching help.ubuntu.org, I found following documents.

Title Search: "apache"
21 results of about 2045 pages. (0.06 seconds)
   1. AideD'Installation/ApacheAvecFastCgi
   2. AideD'Installation/ApacheAvecModPython
   3. AideD'Installation/ApacheEtLinux
   4. AideD'Installation/ApacheEtMacOSX
   5. AideD'Installation/ApacheEtWin32
   6. ApacheMySQLPHP
   7. ApacheMySQLPHP/AptPhp4Output
   8. ApacheRailsFCGI
   9. ApacheTomcat5
  10. EnablingUseOfApacheHtaccessFiles
  11. HelpOnConfiguration/ApacheVoodoo
  12. HelpOnInstalling/ApacheOnLinux
  13. HelpOnInstalling/ApacheOnLinuxFtp
  14. HelpOnInstalling/ApacheOnMacOsx
  15. HelpOnInstalling/ApacheOnWin32
  16. HelpOnInstalling/ApacheWithFastCgi
  17. HelpOnInstalling/ApacheWithModPython
  18. HilfeZurInstallation/ApacheAufMacOsx
  19. HilfeZurInstallation/ApacheAufWin32
  20. forum/server/apache2
  21. forum/server/apache2/SSL

I think I have to follow them to fine tune Apache2.  Any comment?

Tks.

B.R.
satimis

---

### Post by MJN on 2006-11-23
I think my only comment would be to leave well alone. If it ain't broke don't fix it! ;)

Seriously though, are you having performance problems? Apache runs pretty fast by default so I'd be surprised if it causing any bottleneck in whatever you're trying to do...?

Mathew

---

### Post by satimis on 2006-11-23
HI Mathew,

> Seriously though, are you having performance problems? Apache runs pretty fast by default so I'd be surprised if it causing any bottleneck in whatever you're trying to do...?
If on running Apache I don't have.  I just completed its installation.  

I want to learn more to set up customers' a/c, resellers' a/c, allowing people creating their website, etc.  I must have some document for reference, not trying blindly.  Although all of them are on /var/www.  How to adminstrate them?  For such a reason I googled around for relevant reference as a base for starting my venture.  If the official document on Apache website is not for Ubuntu where can I find the necessary document?


B.R.
satimis

---

### Post by MJN on 2006-11-24
Oh I see. I'm afraid that's not really my area so can't offer much help.
 
However, the Apache documentation set will suffice for the general technical aspects - any distribution variation will only be subtle (they can't stray too far from the core otherwise future compatibility becomes at risk) and so you'll likely not come across (m)any other differences.
 
Mathew

---

