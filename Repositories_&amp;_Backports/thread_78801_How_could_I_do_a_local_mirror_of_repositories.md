---
title: "How could I do a local mirror of repositories ?"
date: 2005-10-18
forum: Repositories &amp; Backports
---

### Post by kurtkraut on 2005-10-18
I intend to do a Install Party of Ubuntu. I won't be able to provide good internet conection for all visitors, so it would be good if I could download all packages at once and provide it thru local network by changing temporaly sources.list from visitors.

What is the easiest way to do that ? Is it possible ?

Thanks

---

### Post by doclivingston on 2005-10-19
There are two ways of doing this:

1) use apt-proxy (which is in universe)

What apt-proxy does is act as an intermediate server for packages. The first time someone wants a package, it retrieves it from the normal repository. On any subsequent requests, it just sends the cached copy.

If you are having an "online" install-party, where the site does have Internet access, this is the best option because it doesn't download anything that no-one wants. You could also "pre-download" any packages that you expect people to want. To use it, install "apt-proxy" from Universe and edit /etc/apt-proxy/apt-proxy.conf, I've put the one I use below.


2) mirror the entire repository

This is basically copying the entire Ubuntu repository onto a local machine.

This is good if you have "offline" install-party, where the site does not have any internet access, and you want to download everything before. The big disadvantage of this is that you have to download everything, including packages that people may not want.

For instructions on how to do this, see [http://www.ubuntu.com/download/mirror/document_view](http://www.ubuntu.com/download/mirror/document_view)



I use apt-proxy on my home network, which has two Ubuntu machines, so that packages only need to be downloaded once. This is the apt-proxy.conf that I use
```
[DEFAULT]

;; Server IP to listen on
;address = 192.168.0.254

;; Server port to listen on
port = 9999

;; This makes apt-proxy continue downloading even if all
;; clients disconnect.  This is probably not a good idea on a
;; dial up line.
complete_clientless_downloads = 1

;; Cache directory for apt-proxy
cache_dir = /var/cache/apt-proxy

;; Use HTTP proxy?
;http_proxy = host:port

;;--------------------------------------------------------------
;; Cache housekeeping

;; Time to perform periodic housekeeping:
;;  - delete files that have not been accessed in max_age
;;  - scan cache directories and update internal tables
cleanup_freq = 1d

;; Maximum age of files before deletion from the cache
max_age = 120d

;; Maximum number of versions of a .deb to keep per distribution
max_versions = 2

;;---------------------------------------------------------------
;;---------------------------------------------------------------
;; Backend servers
;;
;; Place each server in its own [section]

[ubuntu]
backends =
	http://au.archive.ubuntu.com/ubuntu
	http://mirror.isp.net.au/ftp/pub/ubuntu/

[ubuntu-security]
backends = http://security.ubuntu.com/ubuntu

[ubuntu-backports]
backends =
	http://public.planetmirror.com/pub/ubuntu-backports/
	ftp://ftp2.caliu.info/backports/
	http://ubuntu-backports.mirrormax.net/
	http://acm.cs.umn.edu/ubp/
```

You'll probably want to change the upstream locations, which are set for Australian mirrors (because that's where I am). If the site you are as uses a http proxy, set the "http_proxy" line. The "cache housekeeping" section probably won't make any different for an install-party, it's useful for long-running apt-proxy servers though.

The line to put in the sources.list will be ```
deb http://machine.name:9999/ubuntu/ breezy main restricted universe multiverse
deb http://machine.name:9999/ubuntu-security/ breezy-security main restricted universe multiverse
deb http://machine.name:9999/ubuntu/ breezy-updates main restricted universe multiverse
```
obviously replacing "machine.name" with the name or ip of the machine that is running apt-proxy.

---

### Post by kurtkraut on 2005-10-19
Hi,

I don't have enough space for all packages from all architectures. What I need is all packages to x86 and AMD64. How could I select all packages for these architectures ?

 Thanks

---

### Post by doclivingston on 2005-10-19
Using apt-proxy wold be much easier, but if you can't use it (you're planning to download at a different site, or whatever) you should be able to do a partial mirror - but I'm not sure how to do it.

---

### Post by khirsha on 2005-10-20
I've some PC with kubuntu installed on, that are not connected to the net, that i like to mantain updated.
I use the program [COLOR="Blue"]**"debmirror"**[/COLOR] (you find it in the official repositories) to mantain a copy of the repositories of i386 acrhitecture without source package in a external HD.

[B]"debmirror -v --host=archive.ubuntu.com --method=http --root=ubuntu --arch=i386 --dist=hoary,hoary-updates,hoary-security --section=main,multiverse,restricted,universe --nosource --passive hoary
"[/B]
  It works very well, i've just some problem with the signature of the release file of the security section so i've to append the option --ignore-release-gpg

It takes about 9,9 GB of disc space.

---

### Post by rndinit0 on 2005-11-18
topic: apt-proxy

Ok I got it all setup, here are some questions though.

Client Side:
How do i force clients to check the proxy first, then other source. In my case this is important cause Im using a laptop. And I wont have access to my internal lan from work. 

The download speed seems to be capped to 20kB/s. Is there any way I can stop the throttling?

Server Side:

The server doesnt use its own cache to install programs. 

Thats it for now.

---

### Post by doclivingston on 2005-11-18
[QUOTE=rndinit0]The download speed seems to be capped to 20kB/s. Is there any way I can stop the throttling?[/quote]

That's odd, mine doesn't do that.


> Server Side:

The server doesnt use its own cache to install programs. 

Change the /etc/apt/source.list on the server to point to proxy as well. e.g. "deb [http://localhost:9999/whatever](http://localhost:9999/whatever) ..."

---

