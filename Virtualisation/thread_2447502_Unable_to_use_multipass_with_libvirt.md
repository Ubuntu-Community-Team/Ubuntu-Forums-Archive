---
title: "Unable to use multipass with libvirt"
date: 2020-07-20
forum: Virtualisation
---

### Post by electricworry on 2020-07-20
Following the [instructions]("https://multipass.run/docs/using-libvirt") I am unable to get multipass to work with libvirt.

I am using Ubuntu 20.04 Desktop and I can confirm that I have libvirt-daemon-system installed. My user's groups are "adm cdrom sudo dip plugdev lpadmin lxd sambashare wireshark libvirt docker", and multipass is installed as follows:

[FONT=courier new]$ snap list
Name                 Version                     Rev    Tracking          Publisher       Notes
multipass            1.3.0                       2259   latest/stable     canonical&#10003;      -[/FONT]

I have attempted to enable the libvirt driver, but then when I attempt to launch a machine I get an error:

[FONT=courier new]$ sudo multipass set local.driver=libvirt
[sudo] password for bob: 
$ multipass get local.driver
libvirt
$ multipass launch ubuntu
launch failed: Cannot connect to libvirtd: Failed to open file '/etc/libvirt/libvirt.conf': Permission denied
Please ensure libvirt is installed and running.[/FONT]

Running the last command with sudo has no improvement.

I'm presuming that this is due to the snap sandboxing of multipass. I have not tried installing the snap in classic mode (as that's not indicated in the documentation). Can anyone advise please?

---

### Post by electricworry on 2020-07-20
Found the answer:

[https://github.com/canonical/multipass/issues/1554](https://github.com/canonical/multipass/issues/1554)

"you will need to snap connect multipass:libvirt now that Multipass is strictly confined (on edge). We'll improve the error message to suggest that, however."

Looks like the problem made it from edge to stable but the issue is still open so the intent is probably there to fix it at some point.

---

