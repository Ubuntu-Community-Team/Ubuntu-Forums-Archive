---
title: "Main Proxy"
date: 2011-06-18
forum: Security
---

### Post by gabrielshier on 2011-06-18
Hey, 

A new guy's question, but i wish all of my internet connections will go through a proxy server. HTTP as well as FTP, and every other type of link. How can i do that? 
On top of that, is there a free ubuntu-users' public proxy list?

Thanks

---

### Post by wacky_sung on 2011-06-18
What i did is to install [Privoxy]("http://www.privoxy.org/"), [Ziproxy]("http://ziproxy.sourceforge.net/") and [Squid3]("http://www.squid-cache.org/").

What you need to do is to use privoxy forward to ziproxy and ziproxy forward to squid3. Your internet browsing will drastically improve.

---

### Post by gabrielshier on 2011-06-18
WHAT?! why?

why do you want all of those? 
can't you have something normal? like a single app with a db of public proxies you can go through?

---

### Post by wacky_sung on 2011-06-18
**_[Ziproxy]("http://en.wikipedia.org/wiki/Ziproxy")_**
Ziproxy is a forwarding, non-caching, HTTP proxy targeted for traffic optimization. The ziproxy software is regarded as lightweight in terms of memory and processing power consumption.
This software works by recompressing pictures (such as JPEG, GIF, PNG, JPEG 2000), gzipping text and HTML/JS/CSS data optimization. Additionally it offers latency reduction by preemptive name resolution.
Further functionalities of compression are supplied by means of optimization of code, named HTMLopt, CSSopt and JSopt (HTML/CSS/JS) which are analogous with Minification (programming).
Currently there are ports being maintained by third-parties for Debian Linux, Gentoo Linux and FreeBSD.

**_[Squid3]("http://en.wikipedia.org/wiki/Squid_cache")_**
Squid is a proxy server and web cache daemon. It has a wide variety of uses, from speeding up a web server by caching repeated requests; to caching web, DNS and other computer network lookups for a group of people sharing network resources; to aiding security by filtering traffic. Although primarily used for HTTP and FTP, Squid includes limited support for several other protocols including TLS, SSL, Internet Gopher and HTTPS.[2]
Squid was originally designed to run on Unix-like systems, but also runs well on Windows-based systems. Released under the GNU General Public License, Squid is free software.

**_[Privoxy]("http://en.wikipedia.org/wiki/Privoxy")_**
Privoxy is a non-caching Web proxy with advanced filtering capabilities for enhancing privacy, modifying Web page data and HTTP headers before the page is rendered by the browser. Privoxy is a "privacy enhancing proxy", filtering Web pages and removing advertisements. Privoxy can be customized by users, for both stand-alone systems and multi-user networks.[1]
Privoxy is based on the Internet Junkbuster and is released under the GNU General Public License. It runs on GNU/Linux, OpenWRT, Windows, Mac OS X, OS/2, AmigaOS, BeOS, and most flavors of Unix. Almost any Web browser can use it. The software is hosted at SourceForge.
Privoxy is frequently used in combination with Tor and Squid and can be used to bypass Internet censorship.

See [here]("http://en.wikipedia.org/wiki/Web_accelerator") for you to see what is the chart for each proxy server functions.

What you seek after is not a local proxy but to keep you from being anonymous. [Tor]("http://en.wikipedia.org/wiki/Tor_proxy") is just what you want.

---

### Post by gabrielshier on 2011-06-20
Thanks alot! This really works for me! :)

---

### Post by wacky_sung on 2011-06-20
Welcome:guitar:

---

