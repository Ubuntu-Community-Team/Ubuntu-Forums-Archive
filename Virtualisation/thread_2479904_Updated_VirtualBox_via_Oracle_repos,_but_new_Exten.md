---
title: "Updated VirtualBox via Oracle repos, but new Extension Pack not offered"
date: 2022-10-12
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2022-10-12
In light of [this information]("https://ubuntuforums.org/showthread.php?t=2477978&p=14107940&viewfull=1#post14107940"), I switched from manually downloading/installing the VirtualBox deb to using the Oracle repositories.  Today I got the first VirtualBox update by this method -
```
Upgrade: virtualbox-6.1:amd64 (6.1.38-153438~Ubuntu~jammy, 6.1.40-154048~Ubuntu~jammy)
```

That part worked.  But when I start the new VirtualBox, it does not prompt me to get the matching Extension Pack version?  And it still has 6.1.38 extension pack?
```
$ VBoxManage list extpacks
Extension Packs: 1
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      6.1.38
Revision:     153438
Edition:      
Description:  Oracle Cloud Infrastructure integration, USB 2.0 and USB 3.0 Host Controller, Host Webcam, VirtualBox RDP, PXE ROM, Disk Encryption, NVMe.
VRDE Module:  VBoxVRDP
Usable:       true 
Why unusable: 
$ VBoxManage --version
6.1.40r154048

```

How to get the notification ajgreeny described in the linked post?

---

### Post by lammert-nijhof on 2022-10-12
Download the 6.1.40 extension pack from the Oracle site and look on the download page for a sentence about 6.1 releases. Since 2009 I load all of my Virtualbox releases from that site without problems.
I uninstalled Virtualbox 7.0 too many relatively small issues, I wait for >=7.0.1.

---

### Post by &amp;KyT$0P# on 2022-10-12
> **lammert-nijhof said:**
> Download the 6.1.40 extension pack from the Oracle site and look on the download page for a sentence about 6.1 releases.

That's what I would've done before using Oracle repos, and I could just do that again if I need VirtualBox back working before this thread gets solved.  Are you saying it would be better not to get/use the notification?

> I uninstalled Virtualbox 7.0 too many relatively small issues, I wait for >=7.0.1.

Thanks for the heads up.  I was considering going for 7.0 soon but will wait for next release 7.0.2.

---

### Post by &amp;KyT$0P# on 2022-11-18
I never did figure this out, but this issue was eliminated by upgrading VirtualBox to 7.0.4, with which I no longer need the Extension Pack.

---

