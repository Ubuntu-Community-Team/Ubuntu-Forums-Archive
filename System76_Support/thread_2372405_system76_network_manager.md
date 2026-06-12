---
title: "system76 network manager"
date: 2017-09-25
forum: System76 Support
---

### Post by Newbunto on 2017-09-25
I notice a couple of updates available relating to network manager that appear to be system76-specific.

What are those about? When would I need them? When would I not need them? Should I install them?

Example:

[FONT=fixedsys]Changes for network-manager-gnome versions:
Installed version: 1.2.6-0ubuntu0.16.04.3
Available version: 1.2.6-0ubuntu1~system76~1[/FONT]

---

### Post by xeboc2 on 2017-09-25
James from System76 here.

We fixed a bug with network manager connecting to enterprise WPA networks. The work was accepted upstream but hasn't been added to Xenial yet, so we're provided the new, fixed version, through our PPA.  See the PPA packages here:

[https://launchpad.net/~system76-dev/+archive/ubuntu/stable/+packages](https://launchpad.net/~system76-dev/+archive/ubuntu/stable/+packages)

And the changelog here:

[https://launchpadlibrarian.net/337461052/network-manager-applet_1.2.6-0ubuntu1~system76~1_source.changes](https://launchpadlibrarian.net/337461052/network-manager-applet_1.2.6-0ubuntu1~system76~1_source.changes)

---

### Post by xeboc2 on 2017-09-25
The actual change was in Ubiquity, where choosing a WPA2 Enterprise access point during install with crash the installer and leave the user with no user account.  Here is the Ubiquity fix:

[https://launchpadlibrarian.net/337450068/ubiquity_2.21.63.4+system76+1_source.changes](https://launchpadlibrarian.net/337450068/ubiquity_2.21.63.4+system76+1_source.changes)

---

### Post by Newbunto on 2017-09-27
Thanks for the work in fixing that, and for responding.

For my  info ... what will happen when this fix goes upstream and comes through  on the normal Ubuntu repos? Will your fix automatically be superseded?

---

