---
title: "configure: error: pcre-config not found, install the pcre-devel package or build with"
date: 2010-08-03
forum: Server Platforms
---

### Post by tapas_mishra on 2010-08-03
I am installing lighttpd on Ubuntu 9.04.
As per instructions on [this]("http://redmine.lighttpd.net/projects/lighttpd/wiki/InstallFromSource") page
I did ```

svn checkout svn://svn.lighttpd.net/lighttpd/branches/lighttpd-1.4.x/
cd lighttpd-1.4.x
./autogen.sh
```and then when executed ```
./configure
```Got following error
```

configure: error: pcre-config not found, install the pcre-devel package or build with --without-pcre
```then went to synaptic software sources and installed every thing that I could get with name pcre after which error went.
But is there some logical and shorter way to reduce that.
also following error

```
configure: error: bzip2-headers and/or libs where not found, install them or build with --without-bzip2
```
the above problem of bzip2 was solved by 
```

apt-get install libbz2-dev
```

I checked a blog 
[http://macombcomputersupport.com/it-support-blog/2009/07/24/guide-installing-a-linux-web-server-ubuntu-lighttpd/](http://macombcomputersupport.com/it-support-blog/2009/07/24/guide-installing-a-linux-web-server-ubuntu-lighttpd/)

has mentioned similar problems 

but libpcre3-dev does not exist.
What is that complaining about ?
I have to do it on many servers.

---

### Post by Bachstelze on 2010-08-03
Why not just install lighttpd from the repos?

---

### Post by tapas_mishra on 2010-08-03
> **Bachstelze said:**
> Why not just install lighttpd from the repos?
Did 
```

apt-get install lighttpd

```
did not worked.


But the question is not I have not been able to install.It did install I am asking the problem of pcre library how could that be solved.
I do not want to go and check all the pcre libraries from Synaptics.
Which is the exact one that is needed ?

---

### Post by glauber.gallego@gmail.com on 2011-06-22
> **tapas_mishra said:**
> 
Which is the exact one that is needed ?

try libpcre3-dev

---

