---
title: "Error in apache2"
date: 2009-01-21
forum: Server Platforms
---

### Post by adamitj on 2009-01-21
I removed path /etc/apache2 accidentally, so I needed to remove and purge its installation (no problem, I was configuring it).

So now, I reinstalled using

[FONT="Courier New"]sudo apt-get install apache2[/FONT]

But when I try to start it, comes an error:

[FONT="Courier New"]apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory[/FONT]

I don't have any apache2.conf, so what I do to fix it?

Note: I removed, purged and reinstalled apache2.2-common and apache2 several times, but doesn't have effect...

---

### Post by scragar on 2009-01-21
```
sudo apt-get --reinstall install apache2
```

Failing that check the attachment.

---

### Post by spiderbatdad on 2009-01-21
and 
sudo apt-get install apache2.2-common?

---

### Post by adamitj on 2009-01-25
> **spiderbatdad said:**
> and 
sudo apt-get install apache2.2-common?

Unfortunately I tried this as long as I could... and nothing.

I fell that apt-get crashed up with these packages, so I used that apache2.conf file received from scragar and now it seems to be working with some warnings. 

After all, I'm planning to reinstall Ubuntu server to override this problem. Thanks all.

---

### Post by trentscott4 on 2009-01-25
I'd also recommend using Webmin -- it's a ton easier for configuration, especially for Apache.

[http://ubuntuforums.org/showthread.php?t=1049961&p=6616692](http://ubuntuforums.org/showthread.php?t=1049961&p=6616692)

---

