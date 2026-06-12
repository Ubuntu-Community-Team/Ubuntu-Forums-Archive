---
title: "tgtd: Multiple Instances IP Assignment"
date: 2019-08-05
forum: Server Platforms
---

### Post by davbanks on 2019-08-05
Hi,

I'm working through a situation where I'd like to run two instances of tgtd each using a different IP address. I can use the --iscsi portal command to do this manually but I can't find a similar option for the tgtadm config file. So how would I config this to happen on reboot? Even the tgtadm command doesn't seem to have this option.

Platform: Ubuntu 18.04
tgtd Version: 1.0.72

Thanks for any help!

---

### Post by davbanks on 2019-08-07
Figured it out! Needed to modify the service script to start two instances of TGTd tied to the correct IPs then duplicate all of the admin commands for the two control ports.

---

