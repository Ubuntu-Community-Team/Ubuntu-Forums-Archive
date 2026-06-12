---
title: "Still not showing up in the Domain"
date: 2012-05-24
forum: Server Platforms
---

### Post by DRouleau on 2012-05-24
Using Ubuntu 12.04 Server, I'm trying to get my Server to join the Domain and so far no luck. In smb.conf I changed the workgroup = line to the new domain rather than workgroup.   resolv.conf is showing the proper domain name.  I did a domain join using likewise and it said that it was successful.  Yet when I browse my network from my Windows PC it's not showing up and now Workgroup isn't accessable anymore.

---

### Post by DRouleau on 2012-05-24
Ok I have made some progress... I can now see the server I just can't access it.  I get prompted for a username and password and nothing I enter seems to work.  I think I mentioned it but this is part of a Win 2k3 Domain with AD.

---

### Post by DRouleau on 2012-05-24
Actually I'm going to close this and start a new "on topic" question...
I'm not really sure what I did to get it working, I dropped the .local from the Domain Name and a few other things, not sure if that was it though.

---

