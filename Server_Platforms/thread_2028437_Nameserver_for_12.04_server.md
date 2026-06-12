---
title: "Nameserver for 12.04 server"
date: 2012-07-18
forum: Server Platforms
---

### Post by geohei on 2012-07-18
Hi.

Stupid, but I don't get it.

I migrated from 10.04 to 12.04 server edition.

10.04 used to have the nameserver entry in /etc/resolv.conf, but 12.04 doesn't allow it.

Where/how can I enter a nameserver for a static IP interface.

Thanks,

---

### Post by papibe on 2012-07-18
Hi geohei.

You can add a 'dns-namservers' line to your /etc/network/interfaces file. Take a look at [this]("http://ubuntuforums.org/showpost.php?p=11844079&postcount=4") example.

Regards

---

### Post by geohei on 2012-07-18
Works perfectly.
Many thanks!

---

