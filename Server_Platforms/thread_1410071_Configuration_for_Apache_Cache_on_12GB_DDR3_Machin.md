---
title: "Configuration for Apache Cache on 12GB DDR3 Machine"
date: 2010-02-18
forum: Server Platforms
---

### Post by moskit on 2010-02-18
Hi,
I'm beginner administrator. 
I have got server with Core i7 and 12GB RAM only for WWW, DB and E-mail.
I use 4 drives in RAID5 but I would like to improve read performance by enabling CACHE in Apache. This will be server with quite a lot of domains on it. 
Most sites will be in PHP+MySQL (CMS).

I enable modules: cache, disk_cache, file_cache and mem_cache.

Can you take a look on my configuration files? Should I increase some variables to get better performance?

**Mod_disk_cache**
```
<IfModule mod_disk_cache.c>
        CacheRoot /var/cache/apache2/mod_disk_cache
        CacheEnable disk /
        CacheDirLevels 5
        CacheDirLength 3
```[B]
Mod_mem_cache[/B]
```
<IfModule mod_mem_cache.c>
        CacheEnable mem /
        MCacheSize 4096
        MCacheMaxObjectCount 100
        MCacheMinObjectSize 1
        MCacheMaxObjectSize 2048
</IfModule>

```

Should I interest in something else to increase performance?

---

