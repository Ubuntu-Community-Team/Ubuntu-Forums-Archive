---
title: "Ubuntu + LigHTTPd: Server requests taking ages"
date: 2010-05-25
forum: Server Platforms
---

### Post by ctrl_freak on 2010-05-25
Rather than repeat myself, here is [a question I asked on superuser.com]("http://superuser.com/questions/144285/ubuntu-lighttpd-server-requests-taking-ages"):

> I've had an issue since upgrading my distro a couple of weeks ago from hardy; receiving data after making a request has increasing intervals of nothing, as you can see from the picture below.

[http://i49.tinypic.com/2w5lvr9.png]("http://i49.tinypic.com/2w5lvr9.png")

I have since reinstalled fresh from an Ubuntu 10.04 Server (i386) disk, but am still having the same issues. I'm running on a LigHTTPd, MySQL, PHP5 stack. The surprising thing is, that local browsing using lynx is super fast, as expected. Initially, after reinstalling, I copied over the old configuration files from the previous installation, but have since reinstalled LigHTTPd and rebuilt the config file from scratch. The only correlation I could find, was that I attempted installation of ionCube and Zend Optimizer for a script I was testing, however I would think that it could no longer impact seeing I had reinstalled the OS. I have also removed Suhosin just in case, however it had no impact.

I'm thinking it possibly has something to do with networking, but I wouldn't know where to start. The server is manually assigned an IP by it's MAC address on the router.

The fact that the time seems to be exponential (to a point) worries me. I've tried strace'ing the LigHTTPd and MySQL processes, however I couldn't see anything obvious, not that I'd really know what I'm looking for. RAM and CPU usage don't seem to be out of the ordinary, but I can't say its perfect..

I'm hoping someone has experienced the same, or can point me in a direction, as searching has proved fruitless as I don't know anything specific. Config files can be posted, if requested.
Source: [http://superuser.com/questions/144285/ubuntu-lighttpd-server-requests-taking-ages]("http://superuser.com/questions/144285/ubuntu-lighttpd-server-requests-taking-ages")

As you can see, I have had some suggestions from another helpful user, however nothing sofar seems to have helped. I'm hoping someone here has an idea, or further course of action.

---

### Post by ctrl_freak on 2010-05-31
*bump*

Unfortunately, superuser.com was a dead end, so my hope lies here. Else, I think I'll have to try moving to Debian for any servers I set up, which I want to avoid.

---

### Post by NullHead on 2010-05-31
Perhaps it's your disk I/O? 

Use iotop to see.

---

### Post by ctrl_freak on 2010-06-07
After monitoring disk usage, it seems all normal.

Added to that, using lynx on the local machine works perfect.

---

### Post by NullHead on 2010-06-07
My next guess is it's your network. 

When you get such slowdowns, try pinging the server for a wile and see if the milliseconds go up.

---

### Post by ctrl_freak on 2010-06-23
After installing Debian, it seems its still having the same issue. I'm guessing it's either my hardware, or the combination of Debian drivers with my hardware.

Time to replace the machine.

Thanks anyway.

---

