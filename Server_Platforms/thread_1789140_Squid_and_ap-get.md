---
title: "Squid and ap-get"
date: 2011-06-23
forum: Server Platforms
---

### Post by grimm08 on 2011-06-23
Has anyone been able to figure out how to use apt-get and a squid (proxy) server?

I currently have a ubuntu server that is running squid and I have internal network behind it, this network is not able to route to the external network so I have to run a proxy to get my updates.

If I move the client machine from the internal network to the external and use apt-get with out the proxy I get updates no problem.

I pretty sure the squid server is running correctly but I can not be sure, any help is greatly appreciated.

thanks
Grimm

---

### Post by koenn on 2011-06-23
it's pretty straightforward. 
It's also an excellent way of caching deb files for later reuse, if you have a large enough cache and allow caching of large objects. Saves on downloads if you have multiple machines or need to reinstall something.


First, the squid side

look for /etc/squid/squid.conf
use an editor with a search function, the file is huge (lots of comments)

by default, squid refuses connections, so you need to define a network and allow it access. look for the followuing, add/modify as needed 
```

acl our_networks src 192.168.0.0/24 
http_access allow our_networks
http_access allow localhost
http_access deny all

```

while you're at it, maybe set this one too:
```

maximum_object_size 40960 KB
minimum_object_size 0 KB

```
Debian squid comes with maximum_object_size large enough to cache debs.


Restart squid to make it read the config file;
if that doesn't show any errors, you can be pretty sure squid is running OK



Then, tell apt to use the proxy

there's probably a dedicated  for that somewhere in /etc/apt/conf.d, but you can also simply add something like the following to /etc/apt/apt.conf
```

Acquire::http::proxy "http://192.168.0.1:3128/";
Acquire::ftp::proxy "ftp://192.168.0.1:3128/";
Acquire::https::proxy "https://192.168.0.1:3128/";

```
obviously, the IP address should point to *your* squid

---

### Post by gmargo on 2011-06-23
I highly recommend the use of a caching proxy server designed for this: **apt-cacher-ng**.

[http://packages.ubuntu.com/natty/apt-cacher-ng](http://packages.ubuntu.com/natty/apt-cacher-ng)

You can even configure apt-cacher-ng to use the existing squid proxy as a backend.

---

### Post by koenn on 2011-06-23
> **gmargo said:**
> I highly recommend ... 

you might want to support your recommendation with a reasonable explanation as to why apt-cache is more suitable than just squid ...

---

### Post by gmargo on 2011-06-23
> **koenn said:**
> you might want to support your recommendation with a reasonable explanation as to why apt-cache is more suitable than just squid ...

 Ok, I'll try.  apt-cacher-ng bases its cache-cleansing on the Packages* files.  Squid bases its cache-cleansing on time.

---

### Post by koenn on 2011-06-24
OK. 
but first of all, the OP seems to be interested in getting web access for apt, through an existing proxy, so maybe he's not all that interesting in the actual caching. 

as to squid vs. dedicated apt caching tools, 
consider this :
squid will indeed remove objects from cache based on their age, if its cache is getting too full. 
So it will remove older packages, and keep the newer ones. Given enough disk space so packages don't need to compete with other cached objects, from normal web browsing, this is exactly the behaviour you want : newer packages stay in cache, older ones get removed if necessary. 

So by counting on the normal, expected behaviour of two generic tools, apt and squid, you get the exact effect you'd be aiming for, without the need to setup and maintain an additional tool.

squid is also distro-agnostic, and doesn'b build a repo-style directory tree so transition to newer releases/different release names is completely transparent. 


in short : same effect, less hassle.

---

