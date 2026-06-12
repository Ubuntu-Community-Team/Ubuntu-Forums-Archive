---
title: "bw_mod Exclusions"
date: 2008-01-22
forum: Server Platforms
---

### Post by ericbarch on 2008-01-22
I just configured bw_mod with my apache server and was wondering if there is any way to set exceptions. I would like to throttle bandwidth from all IPs except 192.168.*.*. Is there any easy way to do this? Here is my VirtualHost in apache2.conf:

<VirtualHost *>
DocumentRoot /var/www/
<Directory "/var/www/">
ServerSignature On
allow from all
Options +Indexes
</Directory>
BandwidthModule On
ForceBandWidthModule On
Bandwidth all 65536
MinBandwidth all 21846
</VirtualHost>

I need fast access for the LAN. Thanks!

---

### Post by ericbarch on 2008-01-23
In the readme it shows you can use subnets. Is there a way with subnets to apply the filter to only users connecting from the WAN?

---

