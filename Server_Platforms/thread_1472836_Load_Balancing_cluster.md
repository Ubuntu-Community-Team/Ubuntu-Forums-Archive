---
title: "Load Balancing cluster"
date: 2010-05-04
forum: Server Platforms
---

### Post by bufferoverflow on 2010-05-04
Hi all.
I'm looking after about 8 servers that have minimal load at any one time, and was wondering was there any way of setting up a load balancing cluster using these machines. I know people doing some fairly intensive computational projects, some of which take weeks to run at a time currently, and would salivate over the chance to use our system, and since all the servers are doing damn all most of the time, I thought why not let them use our servers?

Now the hitch, some of these servers are running our mail, some running apache etc. and for redundancy reasons the services are spread out across the rack, can I have a cluster running on them, but still have individual boxes? As in, each server runs it's services as normal, just the free cpu time is used for the computational analysis? And can the cluster work be run as nice to give our primary services priority?

Any input would be much appreciated.

---

### Post by ghost_ryder35 on 2010-05-04
man this is similar to what the seti project does ([http://setiathome.berkeley.edu/info.php](http://setiathome.berkeley.edu/info.php)).  they wrote boinc in house for their needs.  it is available on the internets.  i have no experience with it though.

---

### Post by bufferoverflow on 2010-05-05
Ah yeah, I know of seti@home and boinc, but I know guys in computational physics research in the university here who would love to get time on our servers. I just really want to know if it is possible to run this type of cluster, where the individual machines still run their services.

---

### Post by waloshin on 2010-05-06
Couldn't he run a load balancing servers?

---

### Post by bufferoverflow on 2010-05-10
Yeah, that's what I want to know. Any ideas anyone?

---

