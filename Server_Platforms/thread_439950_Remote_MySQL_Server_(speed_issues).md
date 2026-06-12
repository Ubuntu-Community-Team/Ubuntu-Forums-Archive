---
title: "Remote MySQL Server (speed issues)"
date: 2007-05-11
forum: Server Platforms
---

### Post by bobsta63 on 2007-05-11
Hi all,

Quick queston... I have in the past tryed to run a web server (Apache, PHP, Perl etc.) that connects to and uses a remote MySQL server (connected to the LAN) both servers are running on the same subnet and both servers have a connection speed of 100mb/s.

The queston is, previously when I tried this I noticed that the speed of running SQL queries on the Webserver (that would connect to the remote db serveR) seemed really slow compared to 'loaclhost', I know that it would be alittle slower (obviously) but it will really slow!!! - I did comment out the 'skip-networking' bit and had the account setup correctly for the user to access from any host '%'.

Could anyone tell me why this would be slow?, Is there anything I should tweak when having a seperate remote MySQL Server? Do I need to increase memory buffers sizes?

Hope someone can help.

Kindest regards,

Bobby

---

### Post by craigp84 on 2007-05-12
Hi Bobsta,

When i see slowness like this, my first thought is normally DNS.

However you say MySQL is setup with % for host. To my mind that means it shouldn't be paying attention to DNS, but i really wouldn't be surprised if it still was (maybe for logging client hostnames in the logs).

There's a few other reasons that could cause this too, but really the fastest way to figure it out would be to get a packet trace running on the server, and if that doesn't cast any light, maybe run one on the client too. Remember *not* to restrict the trace to just to the port mysql is running on, you'll most probably find the clues are on port 53 (DNS!).

If that doesn't lead you to the answer, i'd probably just sanity check that server's load, and the mysql configuration too.

There's lots of stuff you should tweak anyway with MySQL, normally people go with the default configs, and in some cases i;ve seen, it's been possible to improve performance by around 75% just by going through the config and santising it. "High Performance MySQL" by the legendary JWZ is a pretty good read.

Hope this helps,

Craig

---

