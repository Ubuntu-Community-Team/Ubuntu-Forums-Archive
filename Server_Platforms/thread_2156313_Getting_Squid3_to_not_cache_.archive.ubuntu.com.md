---
title: "Getting Squid3 to not cache *.archive.ubuntu.com"
date: 2013-06-21
forum: Server Platforms
---

### Post by Lars Noodén on 2013-06-21
What is the right way to get squid3 to pass some web sites straight through and not cache them?  Specifically, I'd like security.ubuntu.com and everything in the *.archive.ubuntu.com domain to pass through without caching.

---

### Post by Lars Noodén on 2013-06-21
This is my guess but it seems not to be passing the requests straight through to the remote servers:

```

acl ubuntu dstdomain security.ubuntu.com
acl ubuntu dstdomain extras.ubuntu.com
acl ubuntu dstdomain .archive.ubuntu.com
always_direct allow ubuntu

```

---

### Post by koenn on 2013-06-21
google with 'squid exclude from caching' (w/o quotes) returns someblogs and forums  were a similar question is answered
eg [http://aacable.wordpress.com/2012/01/23/squid-howto-exclude-some-sites-exntension-from-caching/](http://aacable.wordpress.com/2012/01/23/squid-howto-exclude-some-sites-exntension-from-caching/)
[http://forums.freebsd.org/showthread.php?t=1882](http://forums.freebsd.org/showthread.php?t=1882)

or this : [http://ubuntuforums.org/showthread.php?t=1409351](http://ubuntuforums.org/showthread.php?t=1409351)

you probably need a "no-cache" or "cache deny" acl statement,
eg like so
```
acl no_cache_server1 dstdomain .domain.com
no_cache deny no_cache_server1
```
or
```
acl NO-CACHE-SITES dstdomain "/etc/squid/not-to-cache-sites.txt"
no_cache deny NO-CACHE-SITES
```

man squid or the squid.conf file probably explain more.

---

### Post by Lars Noodén on 2013-06-21
I'm trying those, too, but apt still seems to slow down and stop a little ways in to 'apt-get update'

```

...
Hit http://fi.archive.ubuntu.com saucy-backports Release.gpg
Ign http://fi.archive.ubuntu.com saucy Release
Hit http://fi.archive.ubuntu.com saucy-updates Release
45% [Waiting for headers]

```

The squid log entries are like this:

```

1371829494.873  60507 xx.yy.zz.aa TCP_MISS/503 3874 GET http://fi.archive.ubuntu.com/ubuntu/dists/saucy-backports/Release - HIER_DIRECT/130.230.54.102 text/html
1371829494.941     65 xx.yy.zz.aa TCP_MISS/404 503 GET http://fi.archive.ubuntu.com/ubuntu/dists/saucy/main/source/Sources.diff/Index - HIER_DIRECT/130.230.54.102 text/html

```

Edit: Even after waiting about 15 minutes, 'apt-get update' has not completed.

---

### Post by newbie-user on 2013-06-23
Looking at the squid log, you're getting 503 and 404 errors. That's probably why apt-get is taking so long. Try a different mirror as a possible solution.

---

### Post by Lars Noodén on 2013-06-23
Yes, that's what I thought they meant, too.  But if I set the packet filter to skip redirection for the ip numbers of the Ubuntu repositories, APT works just fine.  It seems to be tangling with Squid somehow.  I'd rather handle that via Squid and not have to keep a list of ip numbers for the filter.

---

### Post by koenn on 2013-06-23
> **Lars Noodén said:**
>  I set the packet filter to skip redirection for the ip numbers of the Ubuntu repositories, APT works just fine. 
You're doing transparent proxy ?

---

### Post by SeijiSensei on 2013-06-23
If you have a transparent proxy, one alternative to consider is using iptables to route around Squid for specific remote IP addresses.  I think a rule like this placed ahead of the REDIRECT to port 3128 might work:

```

/sbin/iptables -t nat -A PREROUTING -p tcp -d ip.of.archive.site --dport 80 -j ACCEPT

```

I've used a similar rule, with "-s" rather than "-d", to exempt specific internal hosts from being pushed through the Squid cache.

---

### Post by Lars Noodén on 2013-06-23
Yes, this is set as a transparent proxy.  APT seeems to be getting some kind of trouble from proxied repositories so I'd like to make an exception for *.archive.ubuntu.com and security.ubuntu.com

---

### Post by koenn on 2013-06-23
So we could assume that something in apt is not happy with the combination of being redirected and proxied, causing your apt-get to hang...

I've never setup or troubleshooted transparent proxies before so I don't know the finer points and I don't immediately see where the problem might be. 
If you want to get to the bottom of this you could perhaps do tcpdumps of a regular apt-get update, a plain proxied one , and a transparant proxied session and see how they differ.


maybe workaround : 
assuming you redirect port 80 : configure apt to use a proxy so it will use port 3128 (avoiding the redirection), then bypass it in squid with always_direct or no_cache or so ? saves you the trouble of listing the archive IP addresses in your packet filter

---

### Post by SeijiSensei on 2013-06-23
I never use the *.archive.ubuntu.com hosts.  The US ones are routinely slower than mirrors.  I usually pick either a local university from the mirror list or a high-bandwidth site like mirrors.xx.kernel.org and use that instead.  Taking that approach limits the number of IP address for which you'd need to write a rule.  For instance, mirrors.us.kernel.org resolves to just two IPs, 149.20.20.135 and 149.20.4.71.

For security.ubuntu.com, I get these IPv4 addresses:

```

$ host security.ubuntu.com
security.ubuntu.com has address 91.189.92.201
security.ubuntu.com has address 91.189.92.202
security.ubuntu.com has address 91.189.91.13
security.ubuntu.com has address 91.189.91.14
security.ubuntu.com has address 91.189.91.15
security.ubuntu.com has address 91.189.92.181
security.ubuntu.com has address 91.189.92.184
security.ubuntu.com has address 91.189.92.190

```

Rather than writing separate rules for each host, I'd just route 91.189.91.0/24 and 91.189.92.0/24 around the Squid proxy using the method I described above.

---

### Post by Lars Noodén on 2013-06-23
Here are the three ways I am trying within squid.  Maybe I have made a mistake with them because even with these rules APT is still hitting the cache.

```

acl ubuntu dstdomain security.ubuntu.com
acl ubuntu dstdomain extras.ubuntu.com
acl ubuntu dstdomain fi.archive.ubuntu.com
always_direct allow ubuntu
cache deny ubuntu

acl straight_through dstdomain security.ubuntu.com
acl straight_through dstdomain extras.ubuntu.com
acl straight_through dstdomain fi.archive.ubuntu.com
cache deny straight_through

acl NO-CACHE-SITES dstdomain "/etc/squid/not-to-cache-sites.txt"
cache deny NO-CACHE-SITES

```

'/etc/squid/not-to-cache-sites.txt' contains the above domains.

extras and security don't seem to have as much trouble with proxying as *.archive.ubuntu.com does.  Have I written it  correctly?

---

### Post by koenn on 2013-06-23
> **Lars Noodén said:**
> Here are the three ways I am trying within squid.  Maybe I have made a mistake with them because even with these rules APT is still hitting the cache.

```

acl NO-CACHE-SITES dstdomain "/etc/squid/not-to-cache-sites.txt"
cache deny NO-CACHE-SITES

```

'/etc/squid/not-to-cache-sites.txt' contains the above domains.

extras and security don't seem to have as much trouble with proxying as *.archive.ubuntu.com does.  Have I written it  correctly?
I don't see '*.archive.ubuntu.com' in your post. In any case, squid doesn't require a wildcard * ; '.archive.ubuntu.com' matches all hosts aans subdomains in the given domain  (note the leading dot)

You should also distinguish between proxy and cache : I don't think you can bypass the proxy since your iptables will redirect the traffic towards it. The only thing you control is how squid handles the requests


Other idea : 
While aimlesly wandering around, i came across this : 

```


disable-pmtu-discovery=
			Control Path-MTU discovery usage:
			    off		lets OS decide on what to do (default).
			    transparent	disable PMTU discovery when transparent
					support is enabled.
			    always	disable always PMTU discovery.

			In many setups of transparently intercepting proxies
			Path-MTU discovery can not work on traffic towards the
			clients. This is the case when the intercepting device
			does not fully track connections and fails to forward
			ICMP must fragment messages to the cache server. If you
			have such setup and experience that certain clients
			sporadically hang or never complete requests set
			disable-pmtu-discovery option to 'transparent'.

```
it's an option to "port",
[http://www.squid-cache.org/Versions/v3/3.3/cfgman/http_port.html](http://www.squid-cache.org/Versions/v3/3.3/cfgman/http_port.html)

assuming apt or the linux tcp/ip stack tries to do  download optimizations wrt MTU discovery or something along those lines, a proxy interfering with  MTU discovery (and the client being unaware of this situation because of the transparent redirect)   might be what"s causing apt-get to hang. Meybe it's worth a shot.

---

### Post by Lars Noodén on 2013-06-23
I've restore the domain to .archive.ubuntu.com

disable-pmtu-discovery sounds like it has potential.  Would the syntax for the option be like this?

http_port 127.0.0.1:3128 intercept disable-pmtu-discovery=transparent

---

### Post by koenn on 2013-06-23
> **Lars Noodén said:**
> 
 Would the syntax for the option be like this?

http_port 127.0.0.1:3128 intercept disable-pmtu-discovery=transparent

that's also what i understood from that manual.
check what version of squid you're using too, apparently a lot is new in squid3; i don't know what the current version in Ubuntu is.

---

### Post by Lars Noodén on 2013-06-23
Only the client is Lubuntu.  Squid is ver 3.2.11 on OpenBSD 5.3-stable. 

I have another client running Debian Wheezy and it also doesn't like running APT through Squid.  Both it and Lubuntu get stuck during 'apt-get update'

---

