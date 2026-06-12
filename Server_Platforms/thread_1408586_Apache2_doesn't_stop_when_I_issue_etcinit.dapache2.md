---
title: "Apache2 doesn't stop when I issue /etc/init.d/apache2 stop"
date: 2010-02-16
forum: Server Platforms
---

### Post by Nexum on 2010-02-16
I have a simple Apache2 install, when I restart my server I get a bunch of apache2 processes, so I think it looks like it's being started up by init.d.

However, when I issue "/etc/init.d/apache2 stop" I get a message "Stopping web server apache2 ...done.", which seems great, but my apache2 processes are still running (did a 'ps aux') and my site is still available.

Any ideas on where I'm going wrong?

The apache2 processes look like this in ps: "/usr/sbin/apache2 -k start".

Any help would be fantastic, I'm sure this is a newbie error.

Thanks!

- Nex

---

### Post by Satoru-san on 2010-02-16
> **Nexum said:**
> I have a simple Apache2 install, when I restart my server I get a bunch of apache2 processes, so I think it looks like it's being started up by init.d.

However, when I issue "/etc/init.d/apache2 stop" I get a message "Stopping web server apache2 ...done.", which seems great, but my apache2 processes are still running (did a 'ps aux') and my site is still available.

Any ideas on where I'm going wrong?

The apache2 processes look like this in ps: "/usr/sbin/apache2 -k start".

Any help would be fantastic, I'm sure this is a newbie error.

Thanks!

- Nex

Try this.

```
kill `ps aux | grep apache2 | grep -v grep | awk '{print $2}'`
```
then do this

```
sudo /etc/init.d/apache2 zap
```

then you can start it.

---

### Post by Nexum on 2010-02-16
The kill command worked fine, although I had to run it as sudo, and I had no more apache2 processes running (and indeed, the site is down).

However, my apache2 doesn't seem to understand the zap command:

'* Usage: /etc/init.d/apache2 {start|stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean|status}'

Any ideas?

My apache version is:

Server version: Apache/2.2.12 (Ubuntu)
Server built:   Aug 18 2009 13:02:39

Must I upgrade?

Thanks for all your help.

---

### Post by Satoru-san on 2010-02-16
do this
```
sudo /etc/init.d/apache2
```

you should get something like this

```
Usage: apache2 [ flags ] < options >

Normal Options:
    start stop restart pause **zap**
      Default init.d options.

Additional Options:
    configdump configtest fullstatus graceful gracefulstop modules reload virtualhosts
      Extra options supported by this init.d script.


```

post that for me. ^ that is mine.

---

### Post by Nexum on 2010-02-16
Mine appears different :-/ :

```

>/var/www$ sudo /etc/init.d/apache2
> * Usage: /etc/init.d/apache2 {start|stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean|status}

```

---

### Post by cdenley on 2010-02-16
I'm guessing you were originally running "/etc/init.d/apache2 stop" as a non-root user. This seems to indicate that it completed successfully, but it obviously does not.
```

sudo /etc/init.d/apache2 stop
sudo ps -ef|grep "[a]pache"

```

---

### Post by Nexum on 2010-02-16
Cdenley: You are a clever fellow.

That is exactly what the issue was. Thanks again for both of your help. Making a post-it note for this issue for next time ;-).

Thanks again.

- Nex

---

### Post by Satoru-san on 2010-02-16
I guess try to start apache again. You can use that kill command I gave you to kill it if it doesnt respond again. You might get an error when you try to start like it appears to have been running.

The Zap command will mannually reset to stopped state.

Stating it will tell you the location of the lock file probably in /var/lock/ and you can rm it.

---

