---
title: "logging time of events to file"
date: 2006-02-14
forum: Server Platforms
---

### Post by art2003 on 2006-02-14
Ubuntu 5.10 breeze server and headless.

I have a script that checks whether the internet connection is up running
every 3 minutes with cron.
If it is up it does nothing.
If it is down it issues some commands to try and remedy the situation.

I would like it also to write a line on a log file showing something like:

Tue Feb 14 10:24:49 GMT 2006 - Internet down 
Tue Feb 14 10:27:59 GMT 2006 - Internet down
Tue Feb 14 10:31:03 GMT 2006 - Internet down  
etc etc for a period up to a week (if possible, but at the very least to get some sort of logging on when the service has been down)

Can anybody help?

---

### Post by heimo on 2006-02-14
I avoid referring to man pages, but I guess it's appropriate this time?
```
man syslog.conf
man logger

```

For example, put new line to /etc/syslog.conf
```
local0.*                        /var/log/custom.log
```

Restart syslogd:
```
sudo /etc/init.d/sysklogd restart
```

And then:
```
logger -p local0.alert "Internet Down"
```

And man [I]logrotate

[/I]As a bonus link:
[http://packages.ubuntu.com/breezy/net/nagios-common](http://packages.ubuntu.com/breezy/net/nagios-common)

---

### Post by art2003 on 2006-02-14
thanks, I had no idea about the existance of logger and thought it had to be done with a combination of pipes cat and echo. 

It certainly makes things easy!

thanks a lot.

The ubuntu forums are full of great people and particularly the server sub-forum!:-D

---

### Post by robert_pectol on 2006-02-14
Another way to do it would be to add a couple of simple things to your script and it will write to a logfile when the connection is found dead.  Somewhere near the beginning of the script, put:
```

timestamp=`date`

```
And then add something like the following, to the appropriate if...then:
```

echo "$timestamp - Internet Down!" >> /path/to/logfile

```
Give it its own unique file.  Do **NOT** use this method to write to a common logfile such as the system log, etc.  If you want to write to a system logfile, then use syslog as suggested previously.  If you want your new logfile rotated on a regualr basis, create an entry in /etc/logrotate.d and specify the appropriate options.  Pattern it after one of the existing entries found in your logrotate.d directory and/or view the manpage.  If you choose not to rotate it using logrotate, bear in mind that the logfile will keep growing as long as your script keeps running and finding the connection dead.  Good luck.

---

### Post by art2003 on 2006-02-14
Thanks a lot Robert, that's exactly what I wanted!

I had tried that with > instead of >> and obviously it wasn't working. I am not a total newbie but still have got lots of things to learn when it comes to scripting!

---

### Post by robert_pectol on 2006-02-14
Yeah, the single, ">" redirects output to the file specified and overwrites any previously existing data contained in it.  The double, ">>" redirects output to the file specified but appends to, instead of overwriting it.  Anyway, happy scripting!   :)

---

