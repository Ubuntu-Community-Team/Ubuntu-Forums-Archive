---
title: "Support for &quot;minimize&quot; install opton via pxe / subiquity / curtin / cloud-init?"
date: 2022-04-21
forum: Ubuntu Development Version
---

### Post by Tazi on 2022-04-21
I just started messing with  22.04 a couple days ago, so am fairly new to Jammy.  This is also my first run at using the cloud-init / nocloud-net process.

After a couple of evenings of trial and error, I have a working auto install stack that uses pxe and cloud-config to automatically deploy a 22.04 server directly from boot without human interaction.

Unfortunately I have been unable to find any method of telling this automatic install process to use the "minimize" option available through the Subiquity GUI.  If there is a switch, environment variable, or curtin hook that can be used to to set this potion please let me know.

I have dug through the docs for Subiquity and Curtin, checked all the install logs for both normal and "minimize" installs, and spent too much time Googling and digging through other sites.

Overall I think available documentation available through Ubuntu's websites for getting all of this working was mediocre at best.  There was a lot of text, but most of it had limited context which made it fairly difficult to glue all the whole user-data file together.  And even needing to have the file specifically named user-data was something that seemed to be made much clearer outside of Ubuntu's documentation.

Also I have had a bunch of problems with Subiquity / Curtin and multi-homed (multiple NIC) VMs using DHCP.  The install process seems to always want to configure the last network interface in the stack as the default for network communications, even when that interface has been issued DNS or gateway information by the DHCP server.  Over the last two days this led to many hours of frustration while trying to figure out exactly why things kept breaking.

On top of that, the install process seems to now ignore the "live-netdev=" option I have previously been able to use to for the installer to always use the correct interface.

Overall I'm enjoying Jammy, but I'd really like to sort out these couple of issues.

---

### Post by ov2k2 on 2022-05-20
I don't think this feature has been added to subiquity autoinstalls yet.  The source subiquity uses is defined by /cdrom/casper/install-sources.yaml.  You just have to change which source is the default.  One way to do this is to have a subiquity early command mount an overlayfs over /cdrom/casper and then overwrite the file with whatever you want.

---

### Post by Tazi on 2022-06-09
Thank you for the info.

Since I only need to spin up new Ubuntu instances occasionally, it probably makes more sense for me to ignore the cloud-init auto-install process until it becomes more mature.

---

