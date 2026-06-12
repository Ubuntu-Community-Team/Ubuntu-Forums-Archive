---
title: "server out of memory"
date: 2009-06-04
forum: Server Platforms
---

### Post by brockangelo on 2009-06-04
Starting this morning around 11am my server came to a crawl. I noticed that of the 1.25GB of memory, 1.2G was being used. I learned a lot about top today, along with free -m and the fact that linux uses all of your memory until it is needed.

However, my buffer is low as well. Here is my free -m:

```
brockangelo@black:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1257       1235         21          0          1         18
-/+ buffers/cache:       1216         40
Swap:         3678        431       3247

```

As soon as I stop either the apache or mysql servers, everything goes back to normal:

```
brockangelo@black:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1257        123       1133          0          2         34
-/+ buffers/cache:         86       1170
Swap:         3678        118       3560

```

I haven't changed anything in my apache2.conf, http.conf or my.cnf that would warrant the sudden change, but now I'd like to understand how to diagnose what appears to be an issue with Apache or MySQL hogging all the memory. I don't think it is a spike in web activity.

Any help or suggestions are appreciated. I've just started a cron job that outputs this hourly because that was mentioned in another thread this morning:

```

echo `date` >> /var/log; echo ================= >> /var/log; ps uaxwwww | sort -g -k 6 | tail -5 >> /var/log/ps.log
```

---

### Post by albinootje on 2009-06-04
> **brockangelo said:**
> 

```

echo `date` >> /var/log; echo ================= >> /var/log; ps uaxwwww | sort -g -k 6 | tail -5 >> /var/log/ps.log
```

That probably needs to be something like this :
```

echo `date` >> /var/log/ps.log; echo ================= >> /var/log/ps.log; ps uaxwwww | sort -g -k 6 | tail -5 >> /var/log/ps.log

```

---

### Post by brockangelo on 2009-06-04
Thanks - I've made the change.

---

### Post by brockangelo on 2009-06-04
It would appear that I am under some sort of DOS. Here's why I think that:

I host my server at home. I use a dynamic IP and update it with a service similar to DynDNS. I have a failover server off-site. As soon as I pointed the hosted websites to the failover server, the master server's memory was restored, and the failover's was tanked.

I've been reading about DOS attacks, and I have filters setup to protect against anonymous requrest, and all the typical filters on basic wireless routers. Any other suggestions for fighting this? Or if anyone knows about DOS, I'd like to figure out if there is a way to block the source.

---

### Post by brockangelo on 2009-06-04
And it appears to have stopped. For the archives, the only thing I did was make sure that all of my hardware firewall filters were enabled. I think the only thing that is on that wasn't before was blocking anonymous ping requests, though I honestly doubt that would have lead to all of this.

Hope that helps someone somewhere someday.

---

