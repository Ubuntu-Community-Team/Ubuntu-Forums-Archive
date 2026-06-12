---
title: "Why is Debian slow compared to Ubuntu"
date: 2005-11-21
forum: The Cafe
---

### Post by jsmidt on 2005-11-21
How is it that the Ubuntu developers are able to get many applications, like gnome 2.12 stable faster than Debian can get these packages into unstable.  Gnome 2.12 still isn't in Debian unstable, but has been on Breezy for over a month now in a stable condition.  I don't know much about debian but why is in slower in these ways?

---

### Post by ofek on 2005-11-21
Debian developers take thier time to check and recheck every package before even thinking about getting it to unstable. 
Debian isn't a bleeding edge distro its a stable distro a really stable distro, ubuntu on the other hand is more into the bleeding edge. Ubuntu may be stable but not as stable as debian

---

### Post by Brunellus on 2005-11-21
Debian has two priorities:  Freedom and Stability.  "pure" Debian is mainly a server OS, and as such stuff needs to be pretty rock-solid.

---

### Post by Stormy Eyes on 2005-11-21
[QUOTE=jsmidt]I don't know much about debian but why is in slower in these ways?[/QUOTE]

The Debian developers are paranoid when it comes to stability.

---

### Post by az on 2005-11-21
[QUOTE=jsmidt]How is it that the Ubuntu developers are able to get many applications, like gnome 2.12 stable faster than Debian can get these packages into unstable.  Gnome 2.12 still isn't in Debian unstable, but has been on Breezy for over a month now in a stable condition.  I don't know much about debian but why is in slower in these ways?[/QUOTE]
There are a lot fewer supported packages in ubuntu.  It is easier to release a small subset of packages than to release 14000 packages which all work together.

It has nothing to do with the individual packages since Canonical employ many key debian developers.  Some of the Debian gnome team work for Canonical.

Gnome 2.12 cannot enter testing probably because there are a few package blocking.  In Ubuntu, those packages are just not there, or are irrelevant in Ubuntu because of a version freeze that does not happen in debian unstable.

Ubuntu is not less stable than Debian.

---

### Post by poofyhairguy on 2005-11-21
[QUOTE=jsmidt] I don't know much about debian but why is in slower in these ways?[/QUOTE]

Because plain Debian is a server OS. With a server OS not upgrading a lot is a good thing.

---

### Post by jdong on 2005-11-21
Azz's comment about fewer packages officially supported (i.e. main) and also fewer platforms supported (though the most popular)...


There's also the thing about overparanoid stability ;)

---

### Post by Yagisan on 2005-11-22
[QUOTE=poofyhairguy]Because plain Debian is a server OS. With a server OS not upgrading a lot is a good thing.[/QUOTE] Sigh, While a lot of people use Debian as a server OS, it is not just specifically a server OS.

Debian is "slow" because of several reasons, the most common being
[LIST]
[*]It's all volunteer work - they do it when they have time
[*]they have a lot more arches then Ubuntu to support
[*]lots more packages
[*]stablity is a high priority
[/LIST]
But if you track experimental and unstable, you will find sometimes they can very quickly update (and break half your system in the process).

---

