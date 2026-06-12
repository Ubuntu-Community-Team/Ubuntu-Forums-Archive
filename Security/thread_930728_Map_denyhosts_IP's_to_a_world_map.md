---
title: "Map denyhosts IP's to a world map?"
date: 2008-09-26
forum: Security
---

### Post by criticalbill on 2008-09-26
Hi all.

Is anyone aware of a tool or app for Ubuntu that can take my denyhosts IP list and then display them (perhaps by city or AS) on a world map?

I'm trying to get a visualization of where attacking sources are coming from. Thanks again.

- CB

---

### Post by moonpup on 2008-09-26
If you haven't already noticed, on the DenyHosts website they have a dynamic page showing most blocked hosts etc. Granted, not exactly what you're looking for but cool to see. You can configure your denyhosts to report back to that dynamic page.

---

### Post by criticalbill on 2008-09-26
Thank you for the quick reply.

I'm hoping to find something I can run locally to view my own data. Let's see what the Ubuntu community comes back with  :)

---

### Post by hyper_ch on 2008-09-26
you can use googlemaps api for that....

(1) readout the denyhosts file
(2) download a geoip db: [http://software77.net/cgi-bin/ip-country/geo-ip.pl](http://software77.net/cgi-bin/ip-country/geo-ip.pl)
(3) then map it to googlemaps

---

