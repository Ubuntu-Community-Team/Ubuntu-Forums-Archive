---
title: "Apache stop option missing"
date: 2014-01-15
forum: Server Platforms
---

### Post by cupid.callin on 2014-01-15
How do I stop my local apache server? The following 2 commands gives only 3 options -- `restart`, `start` and `status`

```

/etc/init.d/apache2
service apache2

```

---

### Post by rubylaser on 2014-01-15
You are missing a bunch of options.  Here is what should show up on a default install for those two commands.
```

# /etc/init.d/apache2 
 * Usage: /etc/init.d/apache2 {start|stop|graceful-stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean|status}
# service apache2 
 * Usage: /etc/init.d/apache2 {start|stop|graceful-stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean|status}

```

I would probably purge your apache install and re-install.
```

sudo apt-get remove --purge apache2 -y
sudo apt-get autoremove
sudo apt-get install apache2

```

---

### Post by TheFu on 2014-01-15
Are you certain that apache2 is running?  That could explain why the stop option is not listed?

Try**sudo stop apache2**
Also,
sudo /etc/init.d/apache2 stop
and 
sudo service apache2 stop
should work, provided apache2 is actually the init.d cmd/service name.

I don't have apache on any boxes - switched to nginx a few years ago - so I can't tell you the exact command.

Of course, there was a new version of apache with 13.10 ... so the name of the service may have changed ... perhaps apache24?  I don't know.  I would use tab cmd completion to find it.

If you tell which Ubuntu release or which apache package is loaded ... **dpkg -l|grep apache** will tell us that ... then someone can probably provide the exact cmd needed with certainty.

---

### Post by tfrue on 2014-01-15
To stop, *sudo service apache2 stop*

To start,  *sudo service apache2 start*

To stop then start, *sudo service apache2 restart*

Good luck,
Chris

---

