---
title: "djbdns issues"
date: 2009-08-26
forum: Server Platforms
---

### Post by BillGod on 2009-08-26
If anyone has experience with djbdns or tinydns I need a little help.  I have it setup and functional.  My issue is this.

My dns server 192.168.15.150
ISP dns servers 68.94.157.1 and 68.94.156.1

If I setup my Ubuntu Desktops with my dns server as the first in the list everything works fine with the exception of REALLY slow lookups for anything other than local. I am assuming this is due to a timeout on dns lookup.  after it fails on mine then it looks on my ISP  right??  This makes for surfing very slow..

If I setup my dns server as the last in the list.  I can only access A Records.  CNames no longer work??  

Anyone have any ideas?

Yes I have my domain name setup to search..

Here is my resolv.conf

domain insta-tek.com
search insta-tek.com

nameserver 192.168.15.150
nameserver 68.94.157.1
nameserver 68.94.156.1

---

### Post by BillGod on 2009-08-26
Wow really no one with any ideas?

---

