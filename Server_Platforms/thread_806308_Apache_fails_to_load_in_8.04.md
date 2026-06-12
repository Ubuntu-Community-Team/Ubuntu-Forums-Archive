---
title: "Apache fails to load in 8.04"
date: 2008-05-24
forum: Server Platforms
---

### Post by GurneyHalleck on 2008-05-24
Apache 1.x was working fine in 7.04 and 7.10, with PHP and MySQL built in.

Now I'm running 8.04, Apache fails to load, generating the following error:

$sudo ./apachectl configtest
Syntax error on line 205 of /usr/local/apache/conf/httpd.conf:
Cannot load /usr/local/apache/libexec/libphp4.so into server: libc-client.so.2002edebian: cannot open shared object file: No such file or directory


The libexec folder does contain libphp4.so, and line 205 of httpd.conf simply reads

LoadModule php4_module        libexec/libphp4.so

Is there something real obvious that I'm missing, or has 8.04 broken something else that the PHP module relies on?

---

### Post by RealPSL on 2008-05-25
It seems like you are having trouble loading a dependent module. Can you run the command below:

```
ldd /usr/local/apache/libexec/libphp4.so
```

This will help us determine which shared module might be missing.

---

### Post by GurneyHalleck on 2008-05-25
Another command I'd never heard of before today.

Anyway, running that gives me a lot of output, amongst which is a line that reads:

libc-client.so.2002edebian => not found

Apache was working fine before the upgrade to 8.04, so did the upgrade delete this 2002edebian file, or has something modified Apache?

I'm using Apache 1.3, and Ubuntu 8.04 seems to automatically install Apache 2. Apache 2 wouldn't have overwritten my Apache 1.3 build, would it?

---

### Post by RealPSL on 2008-05-25
Can you check to see if you still have this package installed on your systems libc-client.so.2002edebian?

```
dpkg --list libc-client.so.2002edebian
```

It is highly unlikely that Ubuntu did anything to your apache installation directly as you have it installed under /usr/local which is not standard for Ubuntu packages. It is more standard for self compiled installations. It is however very possible and in fact seems to be the case that one of the dependent packages might have been removed/changed. If the above package is not installed, install it and report back on your results.

---

### Post by windependence on 2008-05-26
> **GurneyHalleck said:**
> Another command I'd never heard of before today.

Anyway, running that gives me a lot of output, amongst which is a line that reads:

libc-client.so.2002edebian => not found

Apache was working fine before the upgrade to 8.04, so did the upgrade delete this 2002edebian file, or has something modified Apache?

I'm using Apache 1.3, and Ubuntu 8.04 seems to automatically install Apache 2. Apache 2 wouldn't have overwritten my Apache 1.3 build, would it?

Good to see someone running 1.3. Much simpler and more secure IMHO.

Looks like you are getting some good advice here, your module file is not where Apache is looking for it.

Try doing:

```
sudo locate libc-client.so.2002edebian 
```and tell us what the output is, if any.

-Tim

---

### Post by GurneyHalleck on 2008-05-26
Hello to both of you.

$ dpkg --list libc-client.so.2002edebian
No packages found matching libc-client.so.2002edebian.
$ sudo locate libc-client.so.2002edebian
[sudo] password: 
$ 

So it looks like a package that used to be there was indeed removed by the upgrade.

In Synaptic, I see listed a package called libc-client2002edebian, but it has no description, no maintainer, nothing. It's like a ghost entry. Is it safe to install such a dead-looking package?

Also, windependence, can you tell me what makes you wary of Apache 2?

---

### Post by windependence on 2008-05-26
Well, the Apache thing is kinda controversial. Just do a google search for Apache 1.3 vs 2.2 and have fun, it should keep you busy for a while. Some like 2 and some like 1.3. I dunno, I've just been using 1.3 like the big hosting companies.


-Tim

---

### Post by GurneyHalleck on 2008-05-26
Well, I even tried to install that ghost package for libc-client2002edebian, but it gives me a notice that the package does not have a version and has probably been obsoleted.

I even reconfigured, made and installed Apache and PHP, but I get the same error about that edebian library not being found.

Surely it's not the case that Ubuntu 8.04 has made it impossible to run Apache 1.3 with PHP 4?

---

### Post by windependence on 2008-05-26
Looks like it's not available for hardy:

[http://packages.ubuntu.com/libc-client2002edebian?arch=amd64&keywords=libc-client2002edebian](http://packages.ubuntu.com/libc-client2002edebian?arch=amd64&keywords=libc-client2002edebian)

You could, however, see if there is a newer version available.


-Tim

---

### Post by GurneyHalleck on 2008-05-27
Yeah, I found noticed that too. I can't find any sign of an alternative.

Looks like PHP 4 is dead so far as Hardy Heron is concerned.

Still, PHP 4 has been discontinued for a while. I can't blame anyone but my web host for the fact I'm still trying to support a dying version. Time to change web host, methinks.

---

