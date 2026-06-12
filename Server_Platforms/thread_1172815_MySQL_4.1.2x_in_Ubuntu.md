---
title: "MySQL 4.1.2x in Ubuntu"
date: 2009-05-29
forum: Server Platforms
---

### Post by cynergy73 on 2009-05-29
Because of a legacy application that I manage I need to have a 4.1.2x version of MySQL server installed on a Ubuntu server. I would prefer to have a newer version of Ubuntu installed but will do whatever I need to do to get MySQL working.

I have not had any luck with alien conversions of an RPM package or any source installs at this point.

Anyone have a DEB package or other solution to get this installed and running?

Thanks!

---

### Post by LepeKaname on 2009-05-29
I had a similar problem like you... I installed Linux VServer and now I have PHP4 running in the same server (with PHP5+MySQL5).

With Linux VServer, you can setup virtually any other version of ubuntu (or debian) inside your Ubuntu linux. In my case, my server is Intrepid, while the VServer is dapper. I believe the last supported version is dapper, and it has MySQL5 already... so you can just install the vserver and manually compile in there the MySQL 4 version.

It is not as complicated as it seems.. the advantage is that you will share memory, resources and even you can share the same network IP for that virtual setting. And if you screw it, you can cleanly start again... 

These are some useful links:
[http://linux-vserver.org/Installation_on_Ubuntu](http://linux-vserver.org/Installation_on_Ubuntu)
[http://support.uni-klu.ac.at/VServer](http://support.uni-klu.ac.at/VServer)
[http://linux-vserver.org/Documentation#Configuration](http://linux-vserver.org/Documentation#Configuration)

---

