---
title: "management tool for multiple server instances - webmin no longer supported"
date: 2010-06-20
forum: Server Platforms
---

### Post by nicolasdiogo on 2010-06-20
Hi,

i started to look into upgrading my LTS ubuntu server instances to Lucid.

one the notable things that i have discovered is the lack of support for Webmin; it seems that Debian is no longer supporting packages required by Webmin.  But it also appears that ubuntu team believes that Webmin may actually cause problems as it works in a different way than that presumed by Ubuntu.

so i am now left with no way to manage my 10+ instances of ubuntu server that i used for studying and research.

it seems that i am left with cluster-ssh as an alternative.

but are there other alternatives, ideally similar to webmin?

thanks very much for your responses.

Nicolas

---

### Post by CharlesA on 2010-06-20
Got a source?

I'm running Webmin on 10.04 with no problems, just had to download and install the latest version from [webmin.com](http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb).

Granted I do most of my admin tasks via SSH instead of webmin, it was nice to have it for setting stuff up.

---

### Post by HermanAB on 2010-06-20
Well, cluster SSH or Parallel SSH require less effort than Webmin if you have more than one identical server.

---

### Post by stmiller on 2010-06-20
webmin is only for managing one server.


Virtualmin does multiple.

---

### Post by nicolasdiogo on 2010-06-21
thanks guys for taking the time.

stmiller - you are referring to Apache Virtual Domains, and you are correct these are better administrated with Virtualmin - but that is not what i want.

CharlesA - maybe you have not noticed problems as you do not use webmin extensively as i tend to do.

HermanAB - you are spot on! these are identical installations of MySQL, Apache, and Tomcat/Java which i had clustered in webmin and used WebminCluster to manage many machines in one interface.

so i will have to get used to cluster SSH or Parallel SSH

and it also seems that webmin has updated their packages to keep up with ubuntu
[https://bugs.launchpad.net/ubuntu/+bug/542798](https://bugs.launchpad.net/ubuntu/+bug/542798)


many thanks,

Nicolas

---

