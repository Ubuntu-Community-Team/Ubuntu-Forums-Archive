---
title: "IP Uptime Monitoring Tool"
date: 2010-05-26
forum: Security
---

### Post by drhiii on 2010-05-26
That's all I am looking for.  Something I can monitor IP uptime, so I can assign several servers, routers and workstations to a map and watch to see if they are up or down.  Logging would be ideal, but if just realtime, that would be cool enough.  Graphical output also nice but not imperative.

Recommendations?  I am running Ubuntu Desktop on the machine I'd like to use to monitor with...

Any ideas?  

tx

---

### Post by CharlesA on 2010-05-26
I know that [Intermapper ]("http://www.intermapper.com/")can do that.

---

### Post by tgalati4 on 2010-05-27
rwho, ruptime, osd-notify script

---

### Post by drhiii on 2010-05-27
Thank you for the recommendations folks.  Was just looking for some monitoring tools for an internal network with some mesh routers in the mix.  Unfortunately rwho and associated tools had to be installed on the remote hosts.  Can't do that with routers, at least I don't think so.  I just needed to be able to send ICMP packets and see if devices were alive is all.  

So I took the lazy way and installed ntop and am letting it monitor simple broadcast traffic and am able to create a map of uptimes from that.  A bit sloppy, but it is workable...

I appreciate the responses very much.

regards

---

