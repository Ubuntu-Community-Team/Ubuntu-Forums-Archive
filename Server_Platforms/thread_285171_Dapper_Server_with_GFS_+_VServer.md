---
title: "Dapper Server with GFS + VServer"
date: 2006-10-26
forum: Server Platforms
---

### Post by cingo_curmudgeon on 2006-10-26
I have a HP Bladeserver environment with shared storage over fibre channel using GFS.  I want to migrate away from RedHat for a number of reasons.  I also want to deploy vservers.  Ubuntu seems to be be the best candidate so far - but I have reached a problem that has me stuck.  ](*,) 

I can get vservers working on Dapper using the uni-klu kernel and sources.

I can get GFS working on Dapper - although there are several problems which cause Ubuntu installation of redhat-cluster-suite to fail (to be the subject of another post).

But I can't get both at the same time.  The uni-klu "-server" kernels  linux-image-2.6.XX-XX-server don't include GFS cluster support.  In fact, only ONE Ubuntu "-server" image, 2.6.15-23-server, has GFS support.

Why would any true server image not support GFS?  Even without fibre channel, GFS filesystems can be shared using GNBD over GigE IP.  Works great with Ubuntu.

Can someone direct me to a instructions so I can apply the vserver patch to a Ubuntu source and build my own kernel with GFS + VServer support?

---

