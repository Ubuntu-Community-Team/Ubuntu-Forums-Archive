---
title: "One virtual host or multiple in Apache, Nginx, and other webservers?"
date: 2016-07-13
forum: Server Platforms
---

### Post by SchnappiJedi on 2016-07-13
Does putting all your configurations into a single file in Apache, Nginx, and other similar webservers make a given webserver slower or faster as compared to using separate virtual hosts with separate configuration files for each site?

Basically is putting everything into 
```
/etc/apache-or-nginx/sites-available/yoursite 
faster than creating
/etc/apache-or-nginx/sites-available/yoursite1
/etc/apache-or-nginx/sites-available/yoursite2
/etc/apache-or-nginx/sites-available/yoursite3
```

---

### Post by wildmanne39 on 2016-07-13
*Thread moved to **Server Platforms**.*

---

### Post by Vegan on 2016-07-13
s single server is fine for moderate workloads but using several servers scales up more easily

---

### Post by Habitual on 2016-07-14
A general rule I follow:
One domain.com = One domain.conf

but that's just "me", *or is it*?

---

### Post by SchnappiJedi on 2016-07-15
Can anyone comment about speed of one approach versus the other?

---

### Post by TheFu on 2016-07-16
Update: *Oops. It was late (for me) with this completely-miss-the-question reply. I'll leave it since "virtual hosts" can mean different things to different people, though the use above is 100% correct i.e. my misunderstanding.*

I agree with Habitual  and SeijiSensei, except that long-term maintenance trumps performance 99.9999% of the time for me. Basically, performance has to be really, really bad before I'd merge multiple sites into a single file. **Use separate files.** I can't imagine there would be any difference in performance after startup with startup time probably only imperceptibly longer, with multiple config files. Sure, there's overhead of opening, reading, parsing, and closing each of the files, but that is so small as to not matter for the last 15 yrs.  I'd be very surprised if the resulting graph in RAM was any different between 1 or 50 files with settings. Plus the ease of doing common website things with separate files just makes life a little easier.

OTOH, if you really care this much, test both.  I will be happily corrected by facts. ;)  Should also mention that I've been using nginx for about 6 yrs for static websites and as a reverse-proxy and load-balancer for web-apps.  The smartest thing I did for performance was to enable micro-caching. Think I wrote an article about the before-after with that. ...  I remember the results were impressively faster for DB-based sites - like 1000 pgs/sec vs 46 on very modest equipment. Straight static files with apache (still using it for an old toy website) were in the 2K pgs/sec.  Because WAN bandwidth wasn't unlimited, **enabling compression** in the reverse proxy was very important. The slowdown here was WAN bandwidth, not server performance.

**Wrong Answer, but full of HVM vs Container concepts:**
The reason to separate web sites into either separate VMs or separate containers is to limit the harm that might happen when any single website gets hacked. Expect them to be hacked. It will happen, eventually.  You might want to split the separation around the technologies deployed ---- php-based websites on one VM, Ruby On Rails websites on another, put the DB in a different network zone which isn't available over the internet, just from the servers that need it.  Plus you might want the reverse proxy for all of these all alone so there is 1 place to go when you need to add more back-end servers.  Don't forget to enable micro-caching - really will help with performance.

Speed isn't usually a concern. Security and ease of management is.  It isn't like you will develop on the production systems anyway, so set these up in all the ways you think smart in the test environment, run some performance testing, see how high the page loading can go. Either it is sufficient or it isn't. 

VMs will probably be slower. There is more software between the hardware and the applications.  The isolation with VMs is probably better. I treat VMs like regular hardware machines for everything important on a server except storage. Backups, patching, performance management, networking .. all the same - or am I doing it wrong?

Containers will probably be faster (less software between the application and HW), but realize that management of a container is intended to be like creating zombies. If you don't like the current zombie (container), shoot it in the head and make a new one using the latest/greatest of all the pieces, and deploy it. In 2 weeks when that zombie needs patching for security issues, shoot it in the head, rebuild the container using the latest/greatest of all the pieces, and deploy it.  THAT is the best practice for container use.  If the container has an sshd running, I think you are doing it wrong.  Oh - get a config file wrong?  Shoot it in the head, fix the container creation to use the new config, build it, and redeploy the container.  Containers do provide some level of isolation. For me, only time can determine whether that isolation is sufficient or not. I use a container to bring up a browser when forced to use flash or javascript, so at some level I do hope that isolation is working.  I also force the container to setup a storage overlay (tmpfs) which prevents any file system changes from actually being written to disk, so if something bad happens inside the browser and flash or whatever starts writing to disk, it is gone when the browser process is closed.  Containers can be run on any hardware that Linux runs on. No VT-x/AMD-v support required. That means your $150 chromebook running Ubuntu can be the development environment, if you use containers.

Which is better?  I cannot say. If you use DevOps methods and tools, I don't think it matters.  "Speed" can be about website performance or developer efficiency or admin efficiency.  There are nearly infinite combinations of things that make up "total speed."

---

### Post by SeijiSensei on 2016-07-17
If we're talking just about Apache virtual hosts there should be no performance difference once the server is running.  I suppose it might take a microscopically longer amount of time to load the sites from separate files, but once they're loaded they're running in memory.

I vastly prefer have separate configuration files for each virtual host.  It's easier to manage and less unwieldy as the number of sites grows.

---

