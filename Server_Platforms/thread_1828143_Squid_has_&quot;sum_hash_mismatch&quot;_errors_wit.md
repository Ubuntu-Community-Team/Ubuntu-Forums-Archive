---
title: "Squid has &quot;sum hash mismatch&quot; errors with bz2 files"
date: 2011-08-18
forum: Server Platforms
---

### Post by profediego on 2011-08-18
hi, 
Ive been experiencing problems with my squid3 recently, i am using 10.04.3 LTS. Configured squid as always have been configuring since 8.04.04, but its not working as it should be.

Ive been having issues with bz2 files, in my LAN when i try to do an apt-get update, it just says some indexes could not be downloaded cause of a sum hash mismatch.

If you check squid log, for that kind of file it says

TCP_REFRESH_UNMODIFIED/206 

Google around i read thats ssquid cache keeppin the files more than usual, so i add this hoping to solve the problem:

refresh_pattern -i \.bz2$       0       0%      60      override-lastmod refresh-ims override-expire

I dont know if thats well written or not, but it doesnt have solve the problem, and now squid log shows,

TCP_REFRESH_UNMODIFIED/304

but the same behaviour of the hash sum mismatch, please if someone could throw a ligth in here. The only fix to this problem so far is deleting all cache and recreate it every morning, which is far from a solution.

Any help will be greatly apreciate it.

regards.

---

### Post by profediego on 2011-08-23
Anyone? Someone? nope? :$

regards.

---

### Post by TrinitronX on 2012-01-19
I have been seeing similar issues with both apt-get on Ubuntu and yum on CentOS behind a squid proxy.

One workaround is to clear the local package manager caches, however this is far from a good solution IMHO.

Here's how to do it:

**Ubuntu**
```
sudo find /var/lib/apt/lists/ -type f -exec rm -f {} \;
```

**CentOS**
```
sudo rm -f /var/lib/rpm/__*
sudo rpm --rebuilddb
sudo yum clean all
```


Note: There is also a potential squid.conf solution here:
[http://veejoe.net/blog/2009/05/trouble-with-apt-get-and-squid/](http://veejoe.net/blog/2009/05/trouble-with-apt-get-and-squid/)

However, after enabling this option, I was still able to reproduce apt-get problems.

There has been some discussion here about it as well:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565555](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565555)

---

