---
title: "dd for remote backup"
date: 2010-10-05
forum: Server Platforms
---

### Post by tapas_mishra on 2010-10-05
Is it possible in dd to use it for the output file to be stored at some remote location.
I do not have free space on the LVM partition whose backup I want to have via dd.

---

### Post by viralmeme on 2010-10-05
> **tapas_mishra said:**
> Is it possible in dd to use it for the output file to be stored at some remote location
Use [Rsync]("http://www.linux.com/archive/feature/113847")

---

### Post by HermanAB on 2010-10-05
Howdy,

Yes, you can pipe dd through gzip and netcat.  Here is an example:
[http://www.aeronetworks.ca/netcat-howto.html](http://www.aeronetworks.ca/netcat-howto.html)

---

### Post by tapas_mishra on 2010-10-05
> **HermanAB said:**
> Howdy,

Yes, you can pipe dd through gzip and netcat.  Here is an example:
[http://www.aeronetworks.ca/netcat-howto.html](http://www.aeronetworks.ca/netcat-howto.html)
That was gr8.

---

