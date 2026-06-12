---
title: "Update apt-cacher cache automatically"
date: 2010-03-04
forum: Server Platforms
---

### Post by StooJ on 2010-03-04
Is it possible to configure a cron script to update the packages in /var/cache/apt-cacher/packages?

When a client machine updates a package, apt-cacher checks that it's cached package is up-to-date, and downloads a new version if it is not.

I'd like apt-cacher to check it's cached packages every night and download any updated ones, on the premise that since it exists in the apt-cacher cache, someone has that package installed and is going to want to update it.

Is this possible? Does apt-cacher do this anyway, and I haven't noticed?

Cheers

---

### Post by StooJ on 2010-03-05
OK, apt-cacher does support this, but I haven't found any documentation on how to do it yet.
The appropriate script is /usr/share/apt-cacher/apt-cacher-precache.pl

There is a cron job for apt-cacher in /etc/cron.daily/apt-cacher

apt-cacher-precache.pl needs to be called before the clean up, so I inserted a call to the script above it.

Don't know if it works yet - will need to wait until some packages update.

---

### Post by StooJ on 2010-03-08
Right, this is working fairly smoothly now.

To turn on the apt-cacher pre-caching functionality, you need to edit **/etc/cron.daily/apt-cacher**

Insert the following above the line: # Run the cache cleaner
```
# Run the pre-cacher
/usr/share/apt-cacher/apt-cacher-precache.pl -d"main|universe" > /dev/null
```

The "main|universe" argument is a filter to apply to the sources. Only packages in main & universe will be pre-cached in this case.

You need to include something here - the script only pre-caches debian archives by default.

---

