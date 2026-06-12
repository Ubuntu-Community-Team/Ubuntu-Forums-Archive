---
title: "juju bootstrap failed"
date: 2016-08-31
forum: Ubuntu Cloud and Juju
---

### Post by ymor22 on 2016-08-31
Hi,I'm new to the community of Ubuntu.I have installed Ubuntu+MAAS+juju for Openstack test environments.
I have failed to juju bootstrap:confused:

[my environment]
Ubuntu 14.04.5 LTS
MAAS 1.9.4
juju 1.25.6
[B]
[ERROR message]
Bootstrap failed, destroying environment
ERROR failed to bootstrap environment: cannot start bootstrap instance: gomaasapi: got error back from server: 400 BAD REQUEST ({"distro_series": ["'xenial' is not a valid distro_series.It should be one of :",'ubuntu/trusty'."]}) 
[/B]
Do you have any idea whats going on? 

Tnank you.

---

### Post by reese1379 on 2016-09-01
Let me see if I understand you correctly, you're trying to install an image deployment utility (MAAS) and a software deployment tool (Juju), with no previous experience, on an unfamiliar OS, I must say I admire your audacity.

---

### Post by ageiger-at-intellic on 2016-09-14
Can you check that MAAS configuration says that the default distro is Trusty and not Xenial? MAAS may have updated and gotten the Xenial image and Juju took the most recent (I'm guessing, but I've had some issues with MAAS 2.0 with image sync).

---

