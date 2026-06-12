---
title: "Apache Service Won't Start Unless Using apachectl - Upgraded from 12.04 to 14.04"
date: 2015-03-21
forum: Server Platforms
---

### Post by bsntech on 2015-03-21
Upgraded from Ubuntu 12.04 to 14.04 a couple weeks back.

Before, I would always restart the server using "service apache2 restart".  No problems, worked well.

Now with the upgrade, it will no longer work.

If I do a "service apache2 stop", I receive:

```
 * Stopping web server apache2
 *
 * There are processes named 'apache2' running which do not match your pid file which are left untouched in the name of safety, Please review the situation by hand.

```

It does not stop the service.  Doing a "pidof apache2" returns about ten processes.

If I do a "service apache2 start", I receive:

```
 * Starting web server apache2
 *
 * The apache2 instance did not start within 20 seconds. Please read the log files to discover problems

```

If I do a "apachectl stop" and try the "service apache2 start", I still receive the same thing, although it DOES start the server.  Error log line shows:

```
[Sat Mar 21 08:26:12.009175 2015] [mpm_prefork:notice] [pid 3747] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.6 OpenSSL/1.0.1f configured -- resuming normal operations
[Sat Mar 21 08:26:12.009237 2015] [core:notice] [pid 3747] AH00094: Command line: '/usr/sbin/apache2'

```

I'm unable to use the 'apachectl' command to start and stop the service based on some coding that has been done. If 'apachectl' is used, it also does not seem to generate the log files for the VirtualHosts. To top that off, sometimes the "apachectl" doesn't even work unless I specifically login to the server and issue the command locally as opposed to over a remote connection.

As for the configuration after the upgrade, only two lines were commented out of the apache2.conf file to get the service to start.  Those lines were:

LockFile /var/lock/apache2/accept.lock
DefaultType text/plain

---

### Post by bsntech on 2015-03-22
Solved this today.

Fully removed the configuration files and set them back up to get the default config files for the apache install.

There may have been something in the apache2.conf file that caused the problem.

---

