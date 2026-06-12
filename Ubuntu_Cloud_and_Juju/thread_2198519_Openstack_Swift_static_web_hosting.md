---
title: "Openstack Swift static web hosting"
date: 2014-01-09
forum: Ubuntu Cloud and Juju
---

### Post by rjharv on 2014-01-09
Hi all,

I wonder if anyone can help. I have a fully working swift install integrated with keystone. The next step is to enable static web hosting form the containers. I believe this should now be configured after following this guide:

[http://docs.openstack.org/api/openstack-object-storage/1.0/content/Create_Static_Website-dle4000.html](http://docs.openstack.org/api/openstack-object-storage/1.0/content/Create_Static_Website-dle4000.html)

Now thats all well but what URL do I use to view the container *website-test*?

I'd tried: *[https://object.example.com/website-test/](https://object.example.com/website-test/)* but i just get a message returned saying **"bad URL"**

For extra info I access the proxy service via HAProxy which handles SSL termination and removed the need for the users to specify port 8888 or 8080

If there a swift command that tells me what URL I should be accessing the container on for static web hosting?

Any help greatly appreciated.

Ric

---

