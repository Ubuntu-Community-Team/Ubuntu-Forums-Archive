---
title: "Runlevels in Ubuntu or the lack thereof"
date: 2010-01-23
forum: Server Platforms
---

### Post by roninhockley on 2010-01-23
I came up on RedHat. While I thoroughly embrace Ubuntu now, I miss the concept of runlevels. I installed all my CentOS servers with Gnome as a convenience on tap when needed. I boot them to runlevel 3 and open a vnc shell if i need gui. Then kill the vnc thus killing the gui. Just a fantastic compromise for me.

SOooo...how to replicate this behaviour in Ubuntu?

NOT a very broad topic on here that I can see. Anyone doing this? How?:confused:

---

### Post by BkkBonanza on 2010-01-24
Ubuntu still has runlevels but I believe they are setup so that 2-5 behave pretty much the same. If you wanted to adapt them to start in different ways then you would customize the links placed in the /etc/rcX.d directory (where X is runlevel). ie. Add/Remove the links for services/apps you want to start or not. 

Ubuntu does use Upstart now but most of the typical services still get started by the init scripts in the rcX.d directories for compatibility with traditional sysv startup. There may be some that are now started by configs in /etc/init/ and those can be customized by editing the "start on/stop on" directives in those files. To do that you would have to read up on Upstart basics.

---

### Post by BkkBonanza on 2010-01-24
Removed - duplicate post.

---

