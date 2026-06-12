---
title: "Ubuntu 12.04 LTS upgrade to 14.04.3 LTS VMware VM Freeze on load"
date: 2016-02-09
forum: Virtualisation
---

### Post by dennis53 on 2016-02-09
I have a 12.04 LTS system (server only - no gui at all) that is running just fine with no issues to be seen.

After doing a 'do-release-upgrade' to upgrade to 14.04.3, everything appears to function normally during the upgrade process. There are no errors or indications that something might be wrong.

However, upon reboot so that it boots up into 14.04, the VM completely freezes.  It doesn't display anything on the screen, and doesn't appear to go through its Grub process.  It just sits there, black screen, no text, no response.

Because I can backup the machine vmdk, I reverted to a before-upgrade state, tried again, with the same result.  I migrated away from my normal Vmware center and onto a desktop running VMware player to test in another environment (using different hardware, etc).  The result was the same -- black screen upon boot.

Does anyone have any suggestions on how I might troubleshoot this?  The inability to break out of the black frozen screen and no error messages or ability to view a log makes it difficult.

---

### Post by vger2 on 2016-02-29
> **dennis53 said:**
> I have a 12.04 LTS system (server only - no gui at all) that is running just fine with no issues to be seen.

After doing a 'do-release-upgrade' to upgrade to 14.04.3, everything appears to function normally during the upgrade process. There are no errors or indications that something might be wrong.

However, upon reboot so that it boots up into 14.04, the VM completely freezes.  It doesn't display anything on the screen, and doesn't appear to go through its Grub process.  It just sits there, black screen, no text, no response.

Because I can backup the machine vmdk, I reverted to a before-upgrade state, tried again, with the same result.  I migrated away from my normal Vmware center and onto a desktop running VMware player to test in another environment (using different hardware, etc).  The result was the same -- black screen upon boot.

Does anyone have any suggestions on how I might troubleshoot this?  The inability to break out of the black frozen screen and no error messages or ability to view a log makes it difficult.

same here
Having 7 hosts (servers) on VMware ESXi 5.5.0 infrastructure with ispconfig3 cpanel...
recently upgraded from 10 LTS to 12.0.4.5 LTS and after clearing minor bugs and errors and stable working I tried to upgrade to 14.04 LTS.
Everything went well (almost with no single warning) but VM's wouldn't boot so I was forced to revert to snapshots.

the VM's have open-vm-tools installed because VMware sugests that VMware tools are not stable and that it is better to use open tools.

Will try to upgrade VM with VMware tools installed and report here...

Best regards,

V'ger

---

### Post by howefield on 2016-02-29
Moved to the "*Virtualisation*" forum.

---

### Post by vger2 on 2016-02-29
> **vger2 said:**
> same here
Having 7 hosts (servers) on VMware ESXi 5.5.0 infrastructure with ispconfig3 cpanel...
recently upgraded from 10 LTS to 12.0.4.5 LTS and after clearing minor bugs and errors and stable working I tried to upgrade to 14.04 LTS.
Everything went well (almost with no single warning) but VM's wouldn't boot so I was forced to revert to snapshots.

the VM's have open-vm-tools installed because VMware sugests that VMware tools are not stable and that it is better to use open tools.

Will try to upgrade VM with VMware tools installed and report here...

Best regards,

V'ger

same with VMware tools installed
it seems that it have something to do [with kernel bug]("http://ubuntuforums.org/showthread.php?t=2314723")

---

