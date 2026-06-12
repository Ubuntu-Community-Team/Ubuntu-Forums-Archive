---
title: "Hosting multiple sites with apache"
date: 2007-09-27
forum: Server Platforms
---

### Post by thiago.addevico on 2007-09-27
Hi guys,

I've set up a Ubuntu 6.06.1 LTS LAMP server, and installed trac on it. Trac is running fine, but now I want to run another website, and access them like this:

localhost/trac to use trac
localhost/presenca to use my homemame php website

But all docs I've read only teaches to do like this:

trac.localhost
presenca.localhost

My trac VirtualHost is the same listed on [http://trac.edgewall.org/wiki/TracOnUbuntu]("http://trac.edgewall.org/wiki/TracOnUbuntu")

My personal app vhost is the default
Currently trac is accessible as the default host
What do I do to access them the way I wish?

Thanks
Thiago

---

### Post by kidders on 2007-09-28
Hi there,

> **thiago.addevico said:**
> localhost/trac to use trac
localhost/presenca to use my homemame php websiteThat only involves one site, so you won't want to configure virtual hosting. Apache is capable of serving your pages this way out of the box.

---

