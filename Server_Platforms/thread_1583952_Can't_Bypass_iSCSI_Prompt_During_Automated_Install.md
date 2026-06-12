---
title: "Can't Bypass iSCSI Prompt During Automated Installation"
date: 2010-09-28
forum: Server Platforms
---

### Post by bnied on 2010-09-28
Hello,

I'm trying to jump Ubuntu Server 10.04.1 x86_64 on an HP DL360 G5. After loading the modules for install, I'm greeted with an iSCSI prompt that cannot be bypassed. Hitting Finish brings me right back to the same iSCSI prompt.

[IMG]http://img442.imageshack.us/img442/372/screenshotof.png[/IMG]

The issue seems to be identical to [https://bugs.launchpad.net/ubuntu/+source/kickseed/+bug/548617](https://bugs.launchpad.net/ubuntu/+source/kickseed/+bug/548617)

My kickseed file is as follows:

```
#platform=x86, AMD64, or Intel EM64T
# System authorization information
auth  --useshadow  --enablemd5
# System bootloader configuration
bootloader --location=mbr
# Partition clearing information
clearpart --all --initlabel
# Use text mode install
text
# Firewall configuration
firewall --disabled
# System keyboard
keyboard us
# System language
lang en_US
url --url=http://192.168.1.1/cblr/links/Ubuntu-10.04.1-x86_64/
# Reboot after installation
#reboot

# Disable iSCSI
preseed --owner disk-detect disk-detect/iscsi/enable boolean true

# Auto-select network device
# preseed --owner d-i netcfg/choose_interface select eth1

# Always install the server kernel.
preseed --owner d-i     base-installer/kernel/override-image    string linux-server
# Install the Ubuntu Server seed.
preseed --owner tasksel tasksel/force-tasks     string server

# Root password
%include /tmp/rootpassword

# Admin Account
%include /tmp/adminpassword

preseed --owner d-i user-setup/allow-password-weak boolean true

# Do not configure the X Window System
skipx
# System timezone
timezone  America/New_York
# Install OS instead of upgrade
install
# Clear the Master Boot Record
zerombr

# Clear all partitions automatically
preseed --owner d-i partman-lvm/device_remove_lvm boolean true
preseed --owner d-i partman-md/device_remove_md boolean true
preseed --owner d-i partman-lvm/confirm boolean true
preseed --owner d-i partman/choose_partition select finish

# Specified partitions
%include /tmp/partitions

preseed --owner d-i partman/confirm_write_new_label boolean true
preseed --owner d-i partman/confirm boolean true
preseed --owner d-i partman/confirm_nooverwrite boolean true
preseed --owner d-i partman-md/confirm_nooverwrite boolean true
preseed --owner d-i partman-lvm/confirm_nooverwrite boolean true

# Popularity-Contest
preseed --owner popularity-contest popularity-contest/participate boolean false

%pre

%packages
openssh-server

%post
```

Is there a way to bypass this iSCSI prompt automatically?

---

### Post by koenn on 2010-09-28
take this with e few grains of salt, cause it's been a while since i did preseed, and never on a recent ubuntu server. But from (vague !) memory, here are a few things to look into:


if debian installer re-prompts, it's because you haven't supplied an adequate answer to a required installation step. So obviously, "Finished" is insufficient. That might mean that somewhere (in your preseed, in the preseed of the install medium, some default or other...) there's a setting that says you *want to* configure iSCSI targets. 
So you'd need to hunt that down, and unset it.
Running the installer "manually", possibly in Expert mode, might show you which one that is. 
Running ```
debconf-get-selections | less
``` might help you find the corresponding entry for your preseed file
maybe this ?:
```
disk-detect    disk-detect/iscsi/enable    boolean    false
```

----
edit: just noticed, 
you've already have disk-detect/iscsi/enable in your preseed, set to true. So you actually *want* iSCSI ? 
---


alternatuvely, this might just help to get rid of the prompt once you answered it once (by clicking 'finished")
```
# Display again already asked questions ?
d-i	debconf/showold	boolean	false
```



[I]
DISCLAIMER:
YMMV, NO WARRANTY, all usual disclaimers apply, use at own risk, caveat emptor, ....[/I]


otoh,, if it's actually a bug, you're going to have to wait for a fix or a workaround ...

---

### Post by bnied on 2010-09-29
> **koenn said:**
> take this with e few grains of salt, cause it's been a while since i did preseed, and never on a recent ubuntu server. But from (vague !) memory, here are a few things to look into:


if debian installer re-prompts, it's because you haven't supplied an adequate answer to a required installation step. So obviously, "Finished" is insufficient. That might mean that somewhere (in your preseed, in the preseed of the install medium, some default or other...) there's a setting that says you *want to* configure iSCSI targets. 
So you'd need to hunt that down, and unset it.
Running the installer "manually", possibly in Expert mode, might show you which one that is. 
Running ```
debconf-get-selections | less
``` might help you find the corresponding entry for your preseed file
maybe this ?:
```
disk-detect    disk-detect/iscsi/enable    boolean    false
```

----
edit: just noticed, 
you've already have disk-detect/iscsi/enable in your preseed, set to true. So you actually *want* iSCSI ? 
---


alternatuvely, this might just help to get rid of the prompt once you answered it once (by clicking 'finished")
```
# Display again already asked questions ?
d-i	debconf/showold	boolean	false
```



[I]
DISCLAIMER:
YMMV, NO WARRANTY, all usual disclaimers apply, use at own risk, caveat emptor, ....[/I]


otoh,, if it's actually a bug, you're going to have to wait for a fix or a workaround ...

I looked into that. The prompt actually started coming up on my test DL360 G5 only (my test DL360 G4 and G6 servers do not display this prompt) when there was no mention of iSCSI in the config. I added the ```
disk-detect    disk-detect/iscsi/enable    boolean    false
``` line later on to try and nuke it for good (switching around the boolean after false proved useless).

At this point, I'm inclined to think it's a bug, but I will try your suggestion of using Expert Mode in case there's a switch I missed.

Thanks!

---

### Post by bnied on 2010-10-06
Weirdly enough, with the exact same script, the 10.04 installer doesn't have this issue. So this seems to be limited to 10.04.1's installer.

---

### Post by koenn on 2010-10-06
> **bnied said:**
> Weirdly enough, with the exact same script, the 10.04 installer doesn't have this issue. So this seems to be limited to 10.04.1's installer.

I think you now have sufficient info to file a bug report, against the 10.04.1 installer.
You can, I think,  fall back to installing 10.04 and then upgrade, so I doubt the bug will be high priority, but it might get a fix by the next point release, or so.

---

