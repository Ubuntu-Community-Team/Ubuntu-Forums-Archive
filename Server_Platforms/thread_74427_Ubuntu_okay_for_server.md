---
title: "Ubuntu okay for server?"
date: 2005-10-11
forum: Server Platforms
---

### Post by nyheat on 2005-10-11
I run a small Apache-based web server on Win2003, we host about 140+ people but it's slowly growing. It's an Apache2 webserver with PHP, MySQL, Perl, the works..

I would like to migrate everything from Win2k3 to Linux, but would Ubuntu be the best distribution for this?

I ran Ubuntu on my laptop and I loved apt-get, that's why I thought I should ask the folks at Ubuntu forums for advice..

---

### Post by Zelut on 2005-10-11
Well I run ubuntu 5.04 on a home apache server.  I don't know that I have the traffic that you do but I'm sure it'll work fine.  I don't see any reason why it wouldn't.

In the 'outside world' I think slackware is generally a popular server distro, but I've never liked it that much.

---

### Post by cactus on 2005-10-11
I would recommend mailine Debian, Slackware, CentOS, or Archlinux for a server.
The last is my favorite server os, so I might be biased. ;)

Nothing would stop you from using Ubuntu as your server though. It will work, and work quite well (it is after all, just a desktop polished Debian).

---

### Post by mpettitt on 2005-10-11
There is no particular reason why you couldn't use Ubuntu for a web server, but it is really optimised for desktop use, so you might find that one of the distros designed for server use would be more secure by default.
Take a look at [http://distrowatch.com/search.php?category=Server]("http://distrowatch.com/search.php?category=Server")
 for a list of Server style distros.

Personally, I run FreeBSD on my main hosting server, and Debian on my secondary host. My test box runs Slackware, and it is only my devel workstation that runs (K)Ubuntu.

---

### Post by skoal on 2005-10-11
Isn't there an old wive's tell which says, "What's good for the debian, is good for the gander"?

That stupid analogy of mine works either way too, so don't ask me why I chose Ubuntu as the male duck.  I think it just rolls off the tongue better...

\\//_

---

### Post by Glut on 2005-10-11
Which leads us to the new Ubuntu server version 7.10; Gregarious Gander.;) 

On a more serious note, We have found that using Ubuntu as a server is not less secure than Debian - security patches seem to be released quickly. The biggest problem is probably stability. Though, it's not particularly unstable - in the 6 months we've been running an Ubuntu server it's had substancially less downtime than any of our windows servers and it's downtime is not far off our vanilla Debian servers. 

I would argue that it offers few compelling reasons for switching from Debian. Possibly the best is that it has a very well defined turn around time. This is important to us.

Other possible advantages are faster support of new hardware and
well defined corporate support through Canoniacle (sp?)

I don't think that you would find a headless server version of Ubuntu very different from standard Debian. From memory it installs slightly less packages, so you may find Debian easier to setup intially.

---

