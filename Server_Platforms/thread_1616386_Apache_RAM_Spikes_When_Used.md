---
title: "Apache RAM Spikes When Used"
date: 2010-11-08
forum: Server Platforms
---

### Post by FlintyV on 2010-11-08
Hello,

I've done a little search for this but didn't really turn up anything. I've tweaked it to get low memory usage and both MySQL and Apache2 sit at around 90MB when they're idle but when someone accesses a Wordpress blog on the server, Apache eats up most of the ram sending it up to around 800MB from just one person hitting the blog.

Is there something wrong with my Apache install? 

I know Nginx is available but for me that's a last resort as I like the easy install of Phusion Passenger and ModSpeed on Apache. 

This is 10.04 32-bit server BTW.

---

### Post by Vegan on 2010-11-08
Servers need lots of RAM, so install as much as you have available.

Linux however will make do with whatever is available.

I have seen Apache2 on my server use lots when the load rises. That is to be expected.

This is especially so when PHP is invoked.

---

### Post by dtfinch on 2010-11-08
I haven't seen this. 800mb is quite a bit.

Counting total memory used by Apache and other prefork servers can be a little tricky though. When it forks to multiple processes, it looks like it's using more ram, but the memory is shared, only being duplicated when a page is actually changed.

If your browser's configured to use much more than the default connections, that could cause a spike, as every connection gets its own apache process. I can't imagine that hitting 800mb easily though.

How many apache processes are there when it spikes, and how much memory does one process use?

---

### Post by FlintyV on 2010-11-09
I've worked out for some reason Ubuntu installed Apache2-mpm-itk. I'm not entirely sure which flavour that is but I switched out to apache2-mpm-prefork and now RAM usage never breaks 500MB and quickly frees the RAM once it's done.

---

