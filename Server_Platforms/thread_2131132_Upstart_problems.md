---
title: "Upstart problems"
date: 2013-03-31
forum: Server Platforms
---

### Post by Firepowerforfreedom on 2013-03-31
I've been having MAJOR pains with Upstart lately. No matter what I try, I can't seem to get some of my applications to run with Upstart. I can usually start them just fine manually, but that's getting to be a pain. I'll focus on one application in particular: aerofs-cli. My script runs like this:

```

# aerofs-cli
#
# Starts the AeroFS server


description  "Starts the AeroFS server"


start on runlevel [2345]
stop on runlevel [!2345]
setuid austin
setgid sudo
expect fork


exec aerofs-cli

```

I can see it trying to start just before the login screen hits, but it blinks by so fast that I can't tell if it failed or succeeded. When I open htop and try to filter by "aero", I see no sign of it. :confused:

Obviously, I'm open to try just about anything. I'm running Ubuntu Server 12.10 i386 Quantal.

---

