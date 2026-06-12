---
title: "Problems setting up apt-cacher"
date: 2009-04-24
forum: Server Platforms
---

### Post by AncientPC on 2009-04-24
I followed these [instructions]("https://help.ubuntu.com/community/Apt-Cacher-Server").

While the Apache server works, [http://server/apt-cacher](http://server/apt-cacher) does not.  I restarted apt-cacher on the server and verified it was running by calling `ps aux | grep cacher`.

Is there a particular reason why apt-cacher is failing?

---

### Post by cariboo on 2009-04-24
Did you restart apache2 after installing apt-cacher?

```
sudo /etc/init.d/apache2 restart
```

---

### Post by AncientPC on 2009-04-25
Yes.

I found that the documentation is wrong because even though [http://server/apt-cacher](http://server/apt-cacher) fails, as long as I point my client to the server apt-cacher is still responding to requests and caching packages locally at /var/cache/apt-cache/packages/.

---

### Post by MJWitter on 2009-04-25
> **AncientPC said:**
> I followed these [instructions]("https://help.ubuntu.com/community/Apt-Cacher-Server").

While the Apache server works, [http://server/apt-cacher](http://server/apt-cacher) does not. 

Try [http://server:3142](http://server:3142) , just change the number to the port of apt-cacher.
That works for me.  Also adding a /report to the end will give you the usage thus far.

Hope this helps!

---

### Post by AncientPC on 2009-04-25
> **MJWitter said:**
> Try [http://server:3142](http://server:3142) , just change the number to the port of apt-cacher.
That works for me.  Also adding a /report to the end will give you the usage thus far.

Hope this helps!

That works for me, thanks!  I guess the documentation needs to be updated.

---

