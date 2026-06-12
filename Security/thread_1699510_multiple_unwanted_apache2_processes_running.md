---
title: "multiple unwanted apache2 processes running"
date: 2011-03-03
forum: Security
---

### Post by frazerr on 2011-03-03
Hi,

my computer is often very slow, to the point of stalling.

I tty'd in and when I ran ps -ef I noticed about 10
/usr/sbin/apache2 -k start

I dont even want 1 apache running.  Any suggestions why these are running, or how to stop it?

Well, I can stop it with a sudo killall,  but how can I make sure it doesnt happen again?

Thanks

---

### Post by cariboo on 2011-03-03
You can either completely remove apache2 using the purge option of apt-get:

```
sudo apt-get purge apache2
```

or if you still need it occasionally just make the apache2 script in /etc/init.d/apache2 non-executable:

```
sudo chmod -x /etc/init.d/apache2
```

btw you can stop and start any service using the following command:

```
sudo service apache2 stop
```

for version before 10.10 and:

```
sudo /etc/init.d/apache2 stop
```

use start to start a service instead of stop in the above commands.

---

### Post by frazerr on 2011-03-03
Thank you.  I've stopped it, and made the init file -x.

Any idea why there was 7 of these processes?  Or even 1 for that matter?

---

### Post by cariboo on 2011-03-03
That's normal for apache, I actually have 8 instances running on my server, and server load is at 0.0.

The reason apache2 is running, is because you installed it, it starts at boot normally.

---

### Post by amauk on 2011-03-04
Server daemons (like apache) almost always spawn multiple instances of themselves
this is to ensure that when 2 or more requests come in at the same time, they can all be dealt with in a timely manner (as opposed to quickly backing up in a queue)

I thought, by default, that apache spawned 5 processes (as opposed to 8), but I may be wrong about that

---

### Post by hawkmage on 2011-03-04
The number of processes depends on a couple of things.  In the default install of Apache2 in Unbuntu 10.10 the /usr/sbin/apache2 binary has been complied to use "Worker" process model.  If you look in the apache2.conf file there is a section that starts off with "<IfModule mpm_worker_module>".  In that section you will see an entry "StartServers", the default is 2, that defines how many Apache process get started.  With this config when you first start Apache you should see 3 Apache processes, one running as root which is the main controlling process and then 2 as the Apache user defined in the config file which are the 2 servers for the StartServers entry.

To see how your apache2 binary was compiled run the command:
```
/usr/sbin/apache2 -V
```

---

