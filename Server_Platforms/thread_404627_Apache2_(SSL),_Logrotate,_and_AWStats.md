---
title: "Apache2 (SSL), Logrotate, and AWStats"
date: 2007-04-08
forum: Server Platforms
---

### Post by kooseefoo on 2007-04-08
Okay, I have a few questions that have really been puzzling me lately. Any help would be greatly appreciated...

The first is that I have an Ubuntu 6.10 server set up. It is all set up with apache2 and SSLsupport. A while ago I had to disable logrotate because logrotate's postrotate stuff restarts apache. In order to restart, apache requires my password for my SSL key. As such, apache crashes every time logrotate does its thing. Is there a way to have logrotate without storing the password or using an unencrypted key?

Also, should I get logrotate up and running again, would it interfere with AWStats at all (basically, would I lose statistics as logrotate deletes/compresses old logs?)? I have awstats set to update its statistics on an hourly cron job. Intuition tells me that awstats' only-look-at-new-records style reading of the logs should leave it unaffected, but could there be entries between awstats' run and logrotate that would be lost?


Thanks,
Chris

---

### Post by MJN on 2007-04-09
> **kooseefoo said:**
> Okay, I have a few questions that have really been puzzling me lately. Any help would be greatly appreciated...

The first is that I have an Ubuntu 6.10 server set up. It is all set up with apache2 and SSLsupport. A while ago I had to disable logrotate because logrotate's postrotate stuff restarts apache. In order to restart, apache requires my password for my SSL key. As such, apache crashes every time logrotate does its thing. Is there a way to have logrotate without storing the password or using an unencrypted key?

There sure is - see [http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#removepassphrase](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#removepassphrase)

> Also, should I get logrotate up and running again, would it interfere with AWStats at all (basically, would I lose statistics as logrotate deletes/compresses old logs?)? I have awstats set to update its statistics on an hourly cron job. Intuition tells me that awstats' only-look-at-new-records style reading of the logs should leave it unaffected, but could there be entries between awstats' run and logrotate that would be lost?

You're right, however logrotate allows specific things to be done before logs are rotated and in this case you can therefore make awstats update its database with anything in the logs before they disappear (as far as awstats is concerned at least). To do this, add a 'prerotate' section to /etc/logrotate.d/apache2 e.g.

```

prerotate
  /usr/lib/cgi-bin/awstats.pl -config=<location of your awstats config file> -update
endscript
```Mathew

---

### Post by kooseefoo on 2007-04-09
Great! For AWStats, the prerotate thing is exactly what I was looking for. Thanks a lot for the tip!

As far as apache goes, I was trying to avoid having to store my encryption key in plaintext. It seems like the security implications aren't worth it to me. Is there another way?

---

### Post by MJN on 2007-04-10
> **kooseefoo said:**
> As far as apache goes, I was trying to avoid having to store my encryption key in plaintext. It seems like the security implications aren't worth it to me. Is there another way?
 
If it's only readable by root (which it should be) then is it really a problem (for you)...?
 
Mathew

---

### Post by shubjero on 2007-04-11
OK it is a little unclear as to how the /etc/logrotate.d/apache2 should look if you want awstats to run an update before logrotate does its thing on apache's log files.

Here is an example of mine (which I am unsure is correct or not as it contains two lines called 'endscript'

Also please note that i have adjusted the default create which was 'create 640 root adm' originally.  This proved to cause problems for awstats as when logs got rotated, a new /var/log/apache2/access.log gets created (with new permissions) that are not readable by awstats, therefore i have changed the owners to root & www-data.

/var/log/apache2/*.log {
        weekly
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        create 640 root www-data
        sharedscripts
        prerotate
        /usr/lib/cgi-bin/awstats.pl -config=<location of your awstats config file> -update
        endscript
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}

---

### Post by MJN on 2007-04-11
Yep, that's right (I trust you have put the correct path to your awstats config file - I'm guessing you have.
 
The two 'endscripts' is fine - each is ending the 'prerotate' and 'postrotate' sections.
 
Mathew

---

