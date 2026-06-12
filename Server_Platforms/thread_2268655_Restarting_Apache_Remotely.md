---
title: "Restarting Apache Remotely"
date: 2015-03-10
forum: Server Platforms
---

### Post by bsntech on 2015-03-10
Need some advice on how to start Apache remotely.

With Apache 2.2, I was able to do the following command:

ssh <server> 'service apache2 restart'

With Apache 2.4, I know get errors about apache PIDs already in process and when it attempts to restart, an error also occurs about timing out.

So I started doing the restarts using:

apachectl restart

However, it doesn't seem to be working when I issue the command remotely - like this:

ssh <server> 'apachectl restart'

I've also tried:

ssh <server> 'bash apachectl restart'

If I login to the server and do the 'apachectl restart', it works - but just not remotely like it used to.

Any advice?

---

### Post by volkswagner on 2015-03-10
Unless you are logging in as root (bad idea), you'll need to run:

```
sudo service apache2 restart
```

---

### Post by bsntech on 2015-03-10
That does not work with the new version of Apache.  With Apache 2.2, it worked - but not with Apache 2.4.

---

### Post by SeijiSensei on 2015-03-10
"sudo service apache2 restart" works on 14.04 with Apache 2.4.7 for me.  Something else is wrong.

Check the permissions on /var/run/apache2.  On my system it's owned by root, as is the apache2.pid file in that directory.  Try stopping Apache, then check the permissions and delete any stale apache2.pid file you might find.  Then restart Apache with "sudo service apache2 start".

---

### Post by bsntech on 2015-03-10
Wow.. something else must be going on.  Looked at the /var/run/apache2.pid file.  Owned by root.  Stopped apache (apachectl stop) and the file disappeared.  Tried to restart apache by doing 'sudo service apache2 start' and I get:


 * Starting web server apache2                                                   *
 * The apache2 instance did not start within 20 seconds. Please read the log files to discover problems

The /var/log/apache2/error.log file shows:

[Tue Mar 10 16:24:25.766768 2015] [mpm_prefork:notice] [pid 15425] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.6 OpenSSL/1.0.1f configured -- resuming normal operations
[Tue Mar 10 16:24:25.766832 2015] [core:notice] [pid 15425] AH00094: Command line: '/usr/sbin/apache2'

However, it does look like Apache started.. just don't know why I am getting that error.

---

