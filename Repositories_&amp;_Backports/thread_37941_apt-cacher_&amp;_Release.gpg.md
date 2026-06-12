---
title: "apt-cacher &amp; Release.gpg"
date: 2005-05-29
forum: Repositories &amp; Backports
---

### Post by venzen on 2005-05-29
apt-cacher is a really useful means of centralising our apt repository - all hoary clients on our network upgrade & fetch via the apt-cacher server which is efficient in terms of time and bandwidth. Apt's ability to authenticate packages residing on the Ubuntu mirrors is also really useful, but when running 'apt-get update' on the apt-cacher server the authentication function loses its bearings... Specifically, Synaptic complains that new packages selected for installation are 'NOT AUTHENTICATED' - altho it will install them. 

Extensive googling and searching thru  these forums has not yielded an answer as to why apt-cacher/Synaptic cannot authenticate via the Release.gpg files residing in ubuntu/dists/hoary.. 'apt-get update' gives the following output:

user@localhost:/var/cache/apt-cacher # apt-get update
Ign [http://localhost](http://localhost) hoary Release.gpg
Ign [http://localhost](http://localhost) hoary-updates Release.gpg
Ign [http://localhost](http://localhost) hoary-security Release.gpg
Hit [http://localhost](http://localhost) hoary Release
Hit [http://localhost](http://localhost) hoary-updates Release
Hit [http://localhost](http://localhost) hoary-security Release
Ign [http://localhost](http://localhost) hoary/main Packages
Ign [http://localhost](http://localhost) hoary/restricted Packages
34% [Working]
[snip]

So why are some files being ignored? I have fetched the Ubuntu repository gpg key as outlined in the unofficial starter guide - any ideas how I can get apt-cacher & Synaptic to authenticate with this key or otherwise?

---

### Post by reedlaw on 2005-08-11
I am having the same trouble, but with the added difficulty that apt-cacher frequently does not download packages.gz correctly either.  Sometimes it is incredibly slow downloading when I execute apt-get update.  I've had to copy /var/lib/apt/lists/ manually before to get it to work.

---

