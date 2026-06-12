---
title: "Postgres in Cluster (and I don't want it)"
date: 2010-07-10
forum: Server Platforms
---

### Post by Randd on 2010-07-10
I'm running a Xen vhost, I mess up Postgres, try re-installing it but it's no longer working, ok, I think not the end of the world, I fabricate a new instance and start re-installing it get it all up only to find out Postgres is sitting there NOT serving the data. It seems it's setup a cluster having no experience and not needing a cluster I purge and reinstall to no avail.... right... ok, there goes 10.04, make a new instance, make a mirror of it right before I install Postgres, install it and vola, another cluster, I sift around hoping to find someone has delt with this but oh no, I seem to be the only idiot to be cursed with this, I switch to the mirror, install, guess what happened, yes, cluster haunting me. 

Enough of the raving, I'm hoping one of you good people has an easy answer with my greatest hope being that I can use the completely setup image. Simply put I do not need/want Postgres in any-kind of cluster, I just need it to be the normal every-day server it use to be.

Thanks for going through this.

---

### Post by BuchuBaron on 2012-07-20
Old post, but for those finding this in Google:
'Cluster' is the postgres name for an instance of the postgres server.  It is a grouping of all the databases running on the same version with the same access control and configuration settings.

It is not a group of servers or whatever else you might think it is.  So relax - a Postgres Cluster is just what you want: a database server.

The beauty of the postgres setup, is that you can run more than one 'cluster' on a server, each with its own configuration, postgres version and databases.

Don't worry, the term confused me at first also.

---

