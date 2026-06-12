---
title: "LVS HA UltraMonkey - Anyone!?"
date: 2008-07-02
forum: Server Platforms
---

### Post by IbuildDW on 2008-07-02
I used the search function and found a couple old posts with no replies.

Has anyone configured a Ubuntu Load balancing HA cluster ?

I have 2 Red Hat servers with LVS & Ultramonkey routing HTTP and HTTPS to 3 servers.  It's worked well for the last four years, but I'd like to move it to Ubuntu.  I'm willing to document a howto, I'm hoping that there are others who have already done this and can help should I run into problems.

TIA

Jeff - TX

---

### Post by mbiggers on 2009-01-28
Hello - so did you do this?  I am interested in a similar config,
with L7-Ultramonkey fronting Apache(s) which are proxying for Plone.org
CMS sites...

:)

---

### Post by IbuildDW on 2009-01-28
> **mbiggers said:**
> Hello - so did you do this? 

 - Nope, not yet.. I'm still running the Red Hat config.

---

### Post by ghettofreeryder on 2009-01-28
I used this, LVM HA does not work in 8.10 server, so i used 8.04.1

[http://www.howtoforge.com/the-perfect-load-balanced-and-high-availability-web-cluster-with-2-servers-running-xen-on-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/the-perfect-load-balanced-and-high-availability-web-cluster-with-2-servers-running-xen-on-ubuntu-8.04-hardy-heron)

Ignore the xen stuff if you want stand alone servers, i set up 2 load balancers and 2 webservers, with 1 mysql test db in ESXi.  Works good

---

