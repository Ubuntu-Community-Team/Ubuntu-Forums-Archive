---
title: "Apache Traffic and Bandwidth Limiting"
date: 2010-12-29
forum: Server Platforms
---

### Post by Exaby1e on 2010-12-29
I want to put a traffic limit for different Virtualhosts on my Apache server. It didn't take me long to discover mod_cband which looked ideal at first look because it does exactly what I'm looking for.

The problem is that is hasn't been developed for over 4 years and has been removed from Debian a long time ago.

I tried to compile it manually and load Apache with it, but it fails due to some issue: /usr/lib/apache2/modules/mod_cband.so: undefined symbol: truncf

Anyhow, what do people use today to put a traffic and bandwidth limit per Virtualhost?
It's almost embarrasing that Apache does not support this out of the box.

---

### Post by loafimus on 2010-12-29
I can't even seem to figure out where to download the latest version of cband.  The developers site has a download link, but it's forbidden.

[http://codee.pl/cband.html](http://codee.pl/cband.html)

I've tried using the version off of sourceforge and get the same error as you.

---

### Post by HermanAB on 2010-12-29
Howdy,

Iptables nowadays has a rate limit filter built in.  It may be all you need:
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

---

### Post by Exaby1e on 2011-01-01
> **loafimus said:**
> I can't even seem to figure out where to download the latest version of cband.  The developers site has a download link, but it's forbidden.

[http://codee.pl/cband.html](http://codee.pl/cband.html)

I've tried using the version off of sourceforge and get the same error as you.

I found a copy at the bottom of this page: [http://montanalinux.org/mod_cband.html](http://montanalinux.org/mod_cband.html)

---

### Post by Exaby1e on 2011-01-01
> **HermanAB said:**
> Howdy,

Iptables nowadays has a rate limit filter built in.  It may be all you need:
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

This sounds interesting. How does it work more in detail?
I need to set a unique traffic limit on each virtualhost on my Apache server.

---

### Post by SeijiSensei on 2011-01-04
Iptables can't help with that because the rules are based on IP addresses.  It has no way of discriminating among different virtual hosts being handled by a single server with a single address.

There's an old Apache module called [mod_bandwidth]("http://www.cohprog.com/mod_bandwidth.html") lying around out there.  It might be what you need, though I have no idea how compatible it is with Apache 2.2.

---

### Post by wongo888 on 2011-01-04
Wouldn't it be easier to just monitor use and send a message to users that exceed their quota? This mod is buggy according to Debian.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463789](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463789)

As for your compile error, you might just be missing a header file. Ensure that your compiler knows where to look for the missing header file.

[http://gcc.gnu.org/onlinedocs/gcc/Directory-Options.html#Directory-Options](http://gcc.gnu.org/onlinedocs/gcc/Directory-Options.html#Directory-Options)

---

### Post by Exaby1e on 2011-01-04
> **wongo888 said:**
> Wouldn't it be easier to just monitor use and send a message to users that exceed their quota? This mod is buggy according to Debian.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463789](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463789)

As for your compile error, you might just be missing a header file. Ensure that your compiler knows where to look for the missing header file.

[http://gcc.gnu.org/onlinedocs/gcc/Directory-Options.html#Directory-Options](http://gcc.gnu.org/onlinedocs/gcc/Directory-Options.html#Directory-Options)

I know it's buggy, that's why I don't want to use it. I managed to compile it. But right now I'm writing a program that monitors the apache transfer log and counts the traffic for each of my users.

---

### Post by porl on 2011-01-19
> **Exaby1e said:**
> I know it's buggy, that's why I don't want to use it. I managed to compile it. But right now I'm writing a program that monitors the apache transfer log and counts the traffic for each of my users.

i'd be very interested in checking out your program if you are going to release it to the public. i'm sure i'm not the only one :D

---

### Post by Thirtysixway on 2011-01-19
There is a module called mod_bwlimited, however I believe you can only get it by purchasing cPanel, probably reseller/server version at that.  Unless you could find a 'copy' I'm not sure there are any modules up to date with 2.2 in development, at leat not that i've seen.

---

