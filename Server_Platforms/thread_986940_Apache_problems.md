---
title: "Apache problems"
date: 2008-11-19
forum: Server Platforms
---

### Post by Drezard on 2008-11-19
I'm having a few problems when using apache. One of the main ones 
is that its using far too much memory.

Doing some googling (as I always do before bugging people in the forums), i found out about apache2-mpm-prefork. now from what I understand this starts fewer threads thus decreasing memory somehow. how exactly does this mpm-prefork module work? 

ive done a apt-get install apache2-mpm-prefork, do i need to do or get anything else for this to work? 

When I ps aux | grep apache, there are still a heck load of threads/processes all using like 2 - 3 mb each. ideas?

Daniel

---

### Post by Philio on 2008-11-19
There are a bunch of configuration options for mpm-prefork to control the number of processes Apache spawns.

Refer to the docs for more info: 

[http://httpd.apache.org/docs/2.2/mod/mpm_common.html#startservers](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#startservers)
[http://httpd.apache.org/docs/2.2/mod/prefork.html](http://httpd.apache.org/docs/2.2/mod/prefork.html)

There are 2 different mpms for Apache:

Worker - Uses multiple threads
Prefork - Uses multiple processes

What are you hosting on your server? If you have PHP installed you would have had mpm-prefork already, for example.

---

