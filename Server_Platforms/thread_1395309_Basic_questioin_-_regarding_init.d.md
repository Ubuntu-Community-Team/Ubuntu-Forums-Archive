---
title: "Basic questioin - regarding init.d"
date: 2010-01-31
forum: Server Platforms
---

### Post by Truefire on 2010-01-31
Hi folks,

I've been using Ubuntu on my desktop and server for awhile now.


Ok, that had nothing to do with it.

Whatever. My issue is, up until yesterday, I had a beautiful little server under my desk ticking along, serving up my proxy and wordpress installations. I said to myself, "{insertmyrealnamehere), let's update webmin, etc!" 

So, I ran the classic

<code>
"sudo apt-get update && apt-get upgrade"

</code>

And it finished. Yay. I restart for good measure, and now it's serving up a lot of nothing. It just sits there. I can't use SSH, FTP, HTTPD, nothing.

Luckily, I have it hooked up to my dual-input monitor, and can still get backend access. 

I have a feeling since I updated the system, somehow it killed my autostart init.d whatever.

The problem is, I have no idea how to start the stuff again.

Any help would be appreciated. 

If this extra info helps anyone, this install was based on a Turnkey Linux installation, prebuilt server images.

Cheerio,

Truefire

---

### Post by yogesh.girikumar on 2010-02-09
Hi,


       This could be an issue with "Upstart" which is an event based init daemon. To know what that means, please see: [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

To give you a head start, see here: [http://swiss.ubuntuforums.org/showthread.php?p=8501091](http://swiss.ubuntuforums.org/showthread.php?p=8501091)
and here: [http://www.sourcecode.de/content/fun-upstart](http://www.sourcecode.de/content/fun-upstart)

Also, an you please post the contents of the file 
```
/etc/init/rc-sysinit.conf
```Just curious,..

Let me know if this helps.

---

### Post by Truefire on 2010-02-10
Thank you so much for replying. I haven't looked at those yet, but I will. 

Using Midnight Commander, I wasn't able to find the file you requested. I am using Ubuntu 8.04 as the server. (turnkeylinux optimized)

---

### Post by yknivag on 2010-02-12
Can you start the daemons manually?

```

cd /etc/init.d/
sudo ./apache2 start

```

Running ```
ls /etc/init.d
``` will give you a list of the services and daemons you can start in this way.

---

### Post by Truefire on 2010-02-16
Yep, that worked, thanks!

---

