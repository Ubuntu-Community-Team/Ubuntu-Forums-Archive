---
title: "Basic Squid proxy"
date: 2014-07-22
forum: Security
---

### Post by newb85 on 2014-07-22
I'm trying to set up a basic Squid proxy server and it's proving to be more confusing than I'd imagined.

Web searches turn up all sorts of results like "easy Squid setup" or "set up squid in 5 minutes", or something like that.  Inevitably, they all involve adding a laundry list of lines to the squid.conf file, and each one looks very different.  The explanations are somewhat cryptic to me, so I have no idea what settings I want.

Basically, my prime motive for trying this (in addition to learning) is that I'll probably be installing Lubuntu on several machines, probably from mini.iso.  I was hoping to have the proxy server download all the package files during the first installation, and then supply them for the rest.  In a test case, I tried installing squid on the server machine and leaving the default configuration.  Then, when installing on another machine on the network from mini.iso, I tried to point it to the proxy server.  However, the result was that the client machine failed to connect to the mirror, so it couldn't proceed with installation.

Is there an easy way to accomplish what I want?  In reality, all I want is a deb proxy, but I don't know that I can make the mini.iso use a deb proxy.

Thanks!

---

### Post by newb85 on 2014-07-25
Um...bump...

---

### Post by Lars Noodén on 2014-07-25
Which version of Squid are you using?  The configuration options vary a little.  And on which version of Ubuntu?  Will it be on the same LAN as the clients using it?

Also, are you making a regular proxy or an intercepting proxy?  The latter was once known as a transparent proxy.76

---

### Post by SeijiSensei on 2014-07-25
You could set up a local repository mirror as described here: [http://dashohoxha.blogspot.com/2012/08/how-to-create-local-ubuntu-repository_8.html](http://dashohoxha.blogspot.com/2012/08/how-to-create-local-ubuntu-repository_8.html)

---

### Post by Lars Noodén on 2014-07-25
Apt-Cacher or Apt-Cacher NG is even easier to set up than squid.  You just need to point the client machines at it.   It is optimized for caching material from the repositories.  If you use it with a group of machines, do one first.  It will update at the usual speed.  Then once that is done you can do the other machines and they will pull from the local cache.

---

### Post by newb85 on 2014-07-26
I have already tried squid-deb-proxy.  It was really easy to set up.  The problem there is that the client machines won't use it until after Ubuntu has been installed, and I want to use a proxy for the packages downloaded during installation, too.

I'm using 14.04, and the version of squid in the repos (squid3, I think).

As far as regular vs. intercepting, I don't know.  I guess regular should work, since the installer on mini.iso asks if a proxy is to be used.

A local repo seems like overkill to me, especially since I'm setting this server up on a bridged VM (and at the moment, my test clients are also bridged VMs).

---

### Post by Lars Noodén on 2014-07-26
In squid.conf set up an ACL appropriate for your machine's internal VM network.   There are several examples in the configuration file that comes with the package.  Look for something like this:

```

acl localnet src 192.168.0.0/16        # RFC1918 possible internal network

```

and uncomment it and adjust it for your network.  

[http://www.squid-cache.org/Versions/v3/3.3/cfgman/acl.html](http://www.squid-cache.org/Versions/v3/3.3/cfgman/acl.html)

Then make sure the swap / cache is big enough and storing in the directory you want it to use.  

```

cache_dir ufs /home/squid/cache 5000 16 256

```

[http://www.squid-cache.org/Versions/v3/3.3/cfgman/cache_dir.html](http://www.squid-cache.org/Versions/v3/3.3/cfgman/cache_dir.html)

Then when you have squid configured, build the cache.  
```

sudo squid3 -z

```

[http://manpages.ubuntu.com/manpages/trusty/en/man8/squid3.8.html](http://manpages.ubuntu.com/manpages/trusty/en/man8/squid3.8.html)

This only needs to be done once.  Then you can start squid.

Keep an eye on the logs in the beginning to make sure you have the right amount of swap / cache.

---

### Post by newb85 on 2014-07-26
Thanks for the help.  What do the 3 numbers at the end of the swap/cache line represent?  Total cache, minimum size, maximum size, perhaps?  In MB?

---

### Post by Lars Noodén on 2014-07-26
> **newb85 said:**
> Thanks for the help.  What do the 3 numbers at the end of the swap/cache line represent?  Total cache, minimum size, maximum size, perhaps?  In MB?

They would be size in MB then the number of directories and number of subdirectories used by squid to store its swap files.  

[http://www.squid-cache.org/Versions/v3/3.3/cfgman/cache_dir.html](http://www.squid-cache.org/Versions/v3/3.3/cfgman/cache_dir.html)

The default configuration file /etc/squid3/squid.conf also has a lot of annotation in that regard.

---

