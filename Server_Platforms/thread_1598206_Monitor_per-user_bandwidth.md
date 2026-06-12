---
title: "Monitor per-user bandwidth"
date: 2010-10-16
forum: Server Platforms
---

### Post by ts230 on 2010-10-16
Is there any way that I could somehow let one user use only 15 GB a month of bandwidth while the other user could get 100 GB a month? This is required since my server in all only has 500 GB/month for now, an I don't wanna let users just abuse that.

Any help is appreciated.

---

### Post by Fafler on 2010-10-17
It depends. Is it x gb of general data or only a specific protocol like FTP or HTTP?

In the first case, the only way i know of is making a virtual machine and limiting the amount of data the VM is allowed to transfer. I'm pretty sure it can be done with iptables.

In the second case, you should tell what protocol you need to limit and what software you use. Apache, ProFTPD etc.

---

### Post by ts230 on 2010-10-17
> **Fafler said:**
> It depends. Is it x gb of general data or only a specific protocol like FTP or HTTP?

In the first case, the only way i know of is making a virtual machine and limiting the amount of data the VM is allowed to transfer. I'm pretty sure it can be done with iptables.

In the second case, you should tell what protocol you need to limit and what software you use. Apache, ProFTPD etc.

Actually, I only need to limit FTP and HTTP since the users don't get anything else than mail, and mail won't generate more than 1GB a month, tops, and it's shared between all users.

If it matters, I use pure-ftpd for my FTP server, and apache2 for HTTP.

---

### Post by ts230 on 2010-10-21
*bump*

---

### Post by GreenDance on 2010-10-23
> **ts230 said:**
> *bump*

Hi, I think this is what your after for the HTTP side, [http://linhost.info/2009/07/bandwidth-limiting-in-apache2/](http://linhost.info/2009/07/bandwidth-limiting-in-apache2/)

---

### Post by ts230 on 2010-10-23
> **GreenDance said:**
> Hi, I think this is what your after for the HTTP side, [http://linhost.info/2009/07/bandwidth-limiting-in-apache2/](http://linhost.info/2009/07/bandwidth-limiting-in-apache2/)

That's the per-second speed, but what I need is letting a user transfer, for example, 5 GB a month. If it goes over, the connection will be refused. These users are all real users on the system, btw.

---

### Post by Fafler on 2010-10-24
Apache mas a mod called Apache Quota for just that. PureFTPd has build in quotas. With a litte work, you should be able to make them work together using a single file.

---

### Post by ts230 on 2010-10-24
I've had a go at using cband, but when running it with it configured in a virtualhost, I get this error:


 * Restarting web server apache2
 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
 ... waiting apache2: Syntax error on line 204 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/cband.load: Cannot load /usr/lib/apache2/modules/mod_cband.so into server: /usr/lib/apache2/modules/mod_cband.so: undefined symbol: truncf
   ...fail!

---

### Post by ts230 on 2010-10-30
*bump once more*

Seriously, no one knows what is happening?

---

