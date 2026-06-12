---
title: "Binding a process to a port"
date: 2008-05-19
forum: Server Platforms
---

### Post by ianbobisveck on 2008-05-19
Hi. 

I want to know if I can manually bind a process to a specific port. In effect, this would be kind of like internal port forwarding, where a "wrapper" process is between mine and the network:
my process (off port xxxx) --> wrapper (off port yyyy) --> network. 

I mean, I *could* just change the source code and recompile, but if there is anything like what I am looking for it means I could run multipule instances of the same application, then 'bind' them to different ports via internal forwarding. 

Any suggestions?

---

### Post by azadpanchi on 2008-07-25
Most programs have configuration files associated with them, the best place to set this up would be in those configuration file.

If you have a real world scenario please update this post with that information.  If this is a program you are writing I would suggest creating a config file which will not require you to recompile if you want to make any changes.

---

### Post by fnjordy on 2008-07-25
That's a benefit of using [(x)inetd](http://en.wikipedia.org/wiki/Inetd) but the application has to be written to work with it.

---

