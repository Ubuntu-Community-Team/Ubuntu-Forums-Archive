---
title: "Setting up multiple apache server processes, or equivalent solution?"
date: 2011-01-21
forum: Server Platforms
---

### Post by mindrevelation on 2011-01-21
Hello,

I have an amf3 service running on an apache2 server using python via mod_wsgi.  All of this is on an Amazon EC2 instance running the AMI for Ubuntu 10.04 LTS.

The amf3 service performs much better in stress tests when I use the apache2-mpm-event package (as compared to the apache2-mpm-prefork package).  Unfortunately it seems that the event mpm for apache2 does not work with php5 for apache2.  And I want php5 for the web-based admin tools for the afm3 service.

I would like to run two instances of apache2 on the same server, where one is optimized for the amf3 service (with the event mpm package), and the other just a standard minimal apache2 setup with support for php5 (and the standard prefork mpm package).

I'm up for any manner of suggestions as to how to best solve this puzzle.  Performance of the amf3 service is the highest priority.  If I need to, I'll fall back to just running the admin tool on a second machine, but I would really like to keep it all together if possible.

A fix/hack to get php5 to cooperate with the apache2's event mpm model would be neat.  I think most thread safety issues that might occur can be either avoided or patched over since it is only for an admin tool which shouldn't have much traffic (at least not much traffic past the standard authentication prompt).

Or something else...

What do you people think?

---

### Post by wongo888 on 2011-01-22
Why not run the Worker MPM with mod_wsgi and open a port to the mysql. Then when you need to do maintenance spin up another AMI running Prefork MPM and PHP5 and remote connect to the mysql?

---

### Post by mindrevelation on 2011-01-22
Thanks for the reply.

I would do that if it were just me using it, but another entity will be needing access to the admin tools at their uncoordinated convenience.  They will probably be using the admin tools on a fairly regular basis every day with the potential for a multitude of admin users.

It seems overkill to spawn/kill such a machine so regularly (not to mention the overhead lag of boot time).  But I am leaning toward the approach of using two servers all the time (with the admin tools just on a really low-spec machine in the same aws security group).

The other obvious option is to just rewrite the admin tools to make use of the amf service, instead of using php at all.  That requires writing a client side application to access it, and would make it a larger task, but it might be worth it (also adds a layer of security since the admins would require both the admin application and the credentials to use it... then again that also seems like overkill).

Any other thoughts?

---

### Post by wongo888 on 2011-01-22
Lighttpd can be configured to run PHP on a different port. I'm running both Apache and Lighttpd on a dev machine right now and I haven't had any problems. It's not under any kind of load at all though.

[https://wiki.ubuntu.com/Lighttpd%2BPHP](https://wiki.ubuntu.com/Lighttpd%2BPHP)

I believe Plesk's management server is a modified Lighty.

---

### Post by mindrevelation on 2011-01-25
Cool, I'll take a look into that, thanks!

---

