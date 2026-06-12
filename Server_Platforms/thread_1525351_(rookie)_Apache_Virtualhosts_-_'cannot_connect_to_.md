---
title: "(rookie) Apache Virtualhosts - 'cannot connect to server'?"
date: 2010-07-06
forum: Server Platforms
---

### Post by pearce on 2010-07-06
Hey Everyone,

I apologise if I'm in the wrong place for this but I'm stumped. I set up a virtual server with Rackspace and put ubuntu 10.04 on it to have a play with - installed apache, php, mysql, all that fun stuff.

Then went to try to use Virtual hosts, in the /etc/apache2/hosts-available directory
and ran the command a2ensite (domain)
restarted apache
And suddenly, accessing the domain returns could not connect to server, and also accessing the IP address (which used to return 'IT WORKS!') comes back the same.

I'm not entirely sure what I've done, I've followed instructions I've read to the tee, all the while learning and understanding them so I can do it by myself someday, but there's no guidance about this and I'm stumped.

Would very much appreciate a few helping words from anyone who knows what I've done wrong - or just how stupid I'm being.

Take care guys,

George

---

### Post by Skaperen on 2010-07-06
Did apache really restart?  There should be messages when you start it in the service command.  Or check "netstat -Wantp | grep LISTEN" to see if apache2 processes are running (and if so, what IP and what port).

---

### Post by arrrghhh on 2010-07-06
Yea, I also suspect apache is not running.  There's several ways to ensure it is running, ```
ps -A |grep apache
``` is one of them.  The netstat command should work as well... Just not sure what that "-Wantp" switch that Skaperen put on there does...

---

