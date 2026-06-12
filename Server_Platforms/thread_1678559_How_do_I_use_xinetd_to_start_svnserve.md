---
title: "How do I use xinetd to start svnserve?"
date: 2011-01-30
forum: Server Platforms
---

### Post by Zanthir on 2011-01-30
I am trying to run svnserve on startup on an Ubuntu Server 10.04 machine using xinetd (as suggested [here]("https://help.ubuntu.com/community/Subversion")).

My repositories are at /home/svn, so the directory should be the same as in the example. Following the example, the owner should be www-data, I assume. (Is that right?) I've also tried the admin user account as as the svnowner (the one used to set the svnserver up).

I've never done any shell scripting, so I tried xinetd instead of using the startup script. But if I don't get any feedback for using xinetd that will be my next course of option.

For reference, the link above suggests adding ```
svn stream tcp nowait svnowner /usr/bin/svnserve svnserve -i -r /home/svn
``` to the /etc/inetd.conf file, replacing svnowner and /home/svn to the appropriate values (although I'm not 100% sure what those should be). I assume since I did a chown on the repo to www-data that www-data is the owner I need to put in that line, but it doesn't work.

It's just annoying to have to ssh in and type ```
svnserve -d --foreground -r /home/svn
``` every time I reboot.

Thank you all in advance for your help,
Zanthir

---

### Post by t0@d on 2011-01-31
Yes, that is totally annoying.  I would love help with that too.

---

### Post by SeijiSensei on 2011-01-31
No one uses inetd any longer, so don't bother with an inetd.conf file.  (Sounds like you're using some rather outdated instructions.)  Instead, create, as root, a file in /etc/xinetd.d following the pattern in the standard files you'll find there with the appropriate fields for svnserve.

Also you'll need to know what port svnserve will be using to define the "service" entry in your xinetd configuration file.  The name you use must correspond to an entry in /etc/services.  Standard services like smtp are already entered in /etc/services, so a file in /etc/xinetd.d for "service smtp" will automatically listen for connections on port 25.  I don't see "svnserve" in the standard file on my Ubuntu 10.10 machine, so you'll have to define the port and the service name yourself.  There's probably a well-known default port, so use that.

Then run "sudo service xinetd restart" and see if running "telnet localhost the-port-you've chosen" results in a reply from the svnserve daemon.

---

### Post by t0@d on 2011-02-01
> **SeijiSensei said:**
> No one uses inetd any longer, so don't bother with an inetd.conf file.  (Sounds like you're using some rather outdated instructions.)  Instead, create, as root, a file in /etc/xinetd.d following the pattern in the standard files you'll find there with the appropriate fields for svnserve.

Also you'll need to know what port svnserve will be using to define the "service" entry in your xinetd configuration file.  The name you use must correspond to an entry in /etc/services.  Standard services like smtp are already entered in /etc/services, so a file in /etc/xinetd.d for "service smtp" will automatically listen for connections on port 25.  I don't see "svnserve" in the standard file on my Ubuntu 10.10 machine, so you'll have to define the port and the service name yourself.  There's probably a well-known default port, so use that.

Then run "sudo service xinetd restart" and see if running "telnet localhost the-port-you've chosen" results in a reply from the svnserve daemon.

That sounds worth a try.  In the mean time, I found this article [ xinetd and svnserve ]("http://ubuntuforums.org/showthread.php?t=182156") which suggested putting the command in the _/etc/rc.local_ file:

svnserve -d -r /var/svn

It seemed to work OK.  There might be a better way to do it ~ but it hasn't presented any issues so far.

---

### Post by SeijiSensei on 2011-02-01
If it will run as a daemon directly without needing a "wrapper" like xinetd, that's by far the easiest solution.

---

