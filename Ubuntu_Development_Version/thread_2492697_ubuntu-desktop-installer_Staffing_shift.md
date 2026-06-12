---
title: "ubuntu-desktop-installer Staffing shift"
date: 2023-11-20
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2023-11-20
I have bugs, enhancements, and questions filed in the issues at the GitHub for ubuntu-desktop-installer... (And an unanswered question at Launchpad)

They were not getting answered or addressed, so I filed this as a bug:
[URL="https://github.com/canonical/ubuntu-desktop-installer/issues/2383#top"]Issues, Questions and Enhancements Not being Addressed #2383
[/URL]
I figured it might at least get their attention... After over a month (today), it did:
> 
The installer project is being handed over between developers so there will be a period of quiet.

Since this issue is not anything specific about the code I am going to close it.

This is still the correct place to discuss installer issues. And no I am not one of the new installer developers. Your patience is appreciated.

"*there will be a period of quiet*" <-- Is that like a moment of silence?

So it took someone who is loosely related to the project to review and close it? Curious that it took a "staffing change" to even trigger looking at issues. I admit, that doesn't specifically relate to the code, but is an "Issue" with their Project, that they are not addressing anything related to the code, any replies to enhancements or questions.

I know, it was filed tongue in cheek... I do sort of have a twisted sense of humor. But my original question there is still open and unanswered, like it's corresponding question at Launchpad.

Which are these:
[https://github.com/canonical/ubuntu-desktop-installer/issues/2361](https://github.com/canonical/ubuntu-desktop-installer/issues/2361) <-- Which directly relates to [Issue #2360]("https://github.com/canonical/ubuntu-desktop-installer/issues/2360").
[https://answers.launchpad.net/ubuntu/+source/subiquity/+question/708132](https://answers.launchpad.net/ubuntu/+source/subiquity/+question/708132)

Where do I find those answers and/or who to talk to that might know where to look? I am still looking for answers to those questions and it has been 2-3 months now. No-one can even tell me "what" the new installer's 'partitioner' is named, to try to research it myself. I'm sort of at a dead-end with that.

FYI -- After I filed bugs at Launchpad on the TPM backed installer script ([https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2039741](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2039741)), and added reasoning and support to users at the ubuntu-desktop-installer GitHub Issues (and linked those back to that bug report) that were having problems with that installer scripts results... I can see they dropped that Experimental option for Noble.

---

### Post by Claus7 on 2023-11-20
Hello,

some questions to the above:
1) is the new installation a snap package?
2) could you please explain what do you mean "change partitioning on the fly"?
I do know about manual partitioning and that's it.
3) if legacy installation will be available as well, is it not possible for you to continue doing what you have been doing all this time long?

I do know that the latter is not the "answer" you would expect from someone, yet my speculation is that, the new installer seems to have issues. I do not remember in the past an ubuntu amd iso to take so much time in order to be available and to remain to pending state for a reasonable amount of time. From my experience, non latin language installations have some issues that are hard to address, so I suppose that the new installation task is not so trivial. Once again, not answers to your questions, yet having a small experience, I could share it with you.

Regards!

---

### Post by rayanclass on 2023-11-21
So, there's been this interesting staffing shift happening with the "ubuntu-desktop-installer" team, and it's got everyone talking. The folks who were initially responsible for managing this essential component of Ubuntu's desktop installation process have handed off their duties to a new group of talented individuals. It seems like a breath of fresh air for the project, as these new recruits bring in a wealth of expertise and passion for streamlining the desktop installer experience. From what I've gathered, they've been hard at work brainstorming creative ways to enhance user friendliness and improve performance. This change in personnel has injected a newfound sense of energy into the team, and it's exciting to see how it will shape the future development of Ubuntu. Here's hoping that their efforts result in an even more user-friendly and efficient desktop installer!

---

### Post by MAFoElffen on 2023-11-21
@Claus7 --

1) Yes, ubuntu-desktop installer is a Snap Application, installed in the Subiquity installer. This has some advantages, in that the installer can be updated and refreshed, without requiring a respin of the whole image. It can also be set to check for an update at the github, and/or to use a different channel (Stable, beta. etc)...

2) The old installer was Ubiquity , and used partman as the partitioner. First, partman "IS" volume manager aware, so it recognises LVM2, LUKS containers, mdadm RIAD arrays, BTRFS volumes, etc... So it allowed us to set those up from the commandline, start up the installer, choose other > the partitioner saw the layout > you configured the mounts and let the installer continue to install into it...

The new installer's partitioner in not Volume Manager aware. So we lose that ability above...

In the old partitioner, if you used one the the installer scripts... You could change the layout, example /tmp/zsys-setup/layout. You could change sizes of the partitons in the scripts in either /usr/lib/partman/recipes/ (for legacy boot) or /usr/lib/partman/recipes-amd64-efi/ (for UEFU). You could modify the fstab entries in /usr/lib/partman/fstab.d/. And the mount options in /usr/lib/partman/mount.d and /usr/lib/partman/mount.d. So, it the past, we could tweak things even with the canned installers scripts...

I used to jump out to the commandline, setup my own sized partitions, LVM with my own PV's, VG's, LV's... Separate Home's LVM RAID arrays... Jump back into the installer, let the partitioner see it, point the mounts to where i wanted them, then conitinue the installer to install into the filesystem framework.

The partitioner in Flutter... No one will tell me what it is using. Or where it is using files from. It does not even see LVM2: Bug Report: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

One of the big complaints about the new installer it that if you use a canned script for the install, you have no control over the size of the EFI partition or boot partition. Because the partiotner is not Volume Manager aware, the only thing you can create manually and still have the installer's partitioner 'see' to use it to install in an "other" option, it just flat partitions, with no Volume Manager definitions.

#3) Eventually, AFAIK, the plans are for the old installer to go away.

---

### Post by Claus7 on 2023-11-22
Hello,

thank you for your response. 
1) even if it has advantages, I guess that it might be a little bit slower.
2) so you could tamper with the volume manager aware scripts and continue manually with the installations. According to this:
[https://wiki.ubuntu.com/Ubiquity/AdvancedPartitionerRewrite](https://wiki.ubuntu.com/Ubiquity/AdvancedPartitionerRewrite)
I consider partman and the procedure you are following to be an alternative to gparted, command line oriented vs graphically oriented, in order to setup your installation. 
If you have time, could you please explain the term canned script? I have never heard about it. I searched and found that it can be used in screen sharing and other procedures, yet from the name, I suspect that is a somehow routine script.
3) as long as it is called legacy, it seems normal for this to happen, so readjusting seems necessary.

Thank you for your response, hope that soon will be clarified.

Regards!

---

### Post by MAFoElffen on 2023-11-22
@Claus7 --

RE: On the link given in #2 of Post #5...

No. that was Ubiquity and partman, and written in 2008, when they were adding more feature to partman. 

This Snap installer app is Flutter installer based is running on top of Subiquity. Partman is not present there any more on the Image. I do not know exactly what it is using... Reviewing installer logs again today. 

"Canned default installer scripts" <-- Not sure what the official name is for them, but the scripts the installer uses for:

[LIST]
[*]Erase and install Ubuntu
[*]Install Ubuntu alongside (something else)
[*]Advanced- Erase all & Install LVM
[*]Advanced- Erase all & Install LVM with Encryption
[*]Advanced- Experimental Erase all and Install ZFS
[*]Advanced- Experimental Hardware backed Encryption
[/LIST]

---

### Post by Claus7 on 2023-11-23
Hello,

> **MAFoElffen said:**
> 
...

"Canned default installer scripts" <-- Not sure what the official name is for them, but the scripts the installer uses for:

[LIST]
[*]Erase and install Ubuntu
[*]Install Ubuntu alongside (something else)
[*]Advanced- Erase all & Install LVM
[*]Advanced- Erase all & Install LVM with Encryption
[*]Advanced- Experimental Erase all and Install ZFS
[*]Advanced- Experimental Hardware backed Encryption
[/LIST]

Thanks, crystal clear!

Regards!

---

### Post by MAFoElffen on 2023-11-23
I found it...

Buried in the snap image is example autoinstall.yaml scripts for different scenarios... 
```

ubuntu@ubuntu:~$ ls /snap/ubuntu-desktop-installer/1276/bin/subiquity/examples/
ai-zfs-efi-simple.yaml  prefill-system-setup-complete.yaml
ai-zfs-efi.yaml         prefill-system-setup-missing-identity.yaml
ai-zfs-guided.yaml      prefill-system-setup-missing-locale.yaml
answers                 prefill-system-setup-missing-realname.yaml
autoinstall             prefill-system-setup-missing-username.yaml
curtin-events           prefill-system-setup-missing-welcome.yaml
dry-run-configs         snaps
lsb-release-focal       sources
lsb-release-impish      uaclient-status-expired.json
machines                uaclient-status-valid.json
postinst.d              umockdev

ubuntu@ubuntu:~$ ls /snap/ubuntu-desktop-installer/1276/bin/subiquity/examples/autoinstall
ad.yaml                invalid.yaml            system-setup-no-shutdown.yaml
apt-legacy.yaml        most-options.yaml       system-setup.yaml
fallback-offline.yaml  reset-only.yaml         user-data.yaml
hybrid.yaml            short.yaml
interactive.yaml       system-setup-full.yaml

```
When the Snap first came out, I thought these were just example yaml files, but the installer actually uses them to build the directives for the installer... So, I'm thinking thse can be tweaked to change the outcome of the installs (bigger EFI & Boot partitions). 

The installer uses and interacts with those files to build the autoinstall-user-data file, which it uses as if it is the autoinstall.yaml file
```

sudo grep . /var/log/installer/autoinstall-user-data
[sudo] password for mafoelffen: 
#cloud-config
autoinstall:
  apt:
    disable_components: []
    fallback: abort
    geoip: true
    mirror-selection:
      primary:
      - country-mirror
      - arches: &id001
        - amd64
        - i386
        uri: http://archive.ubuntu.com/ubuntu/
      - arches: &id002
        - s390x
        - arm64
        - armhf
        - powerpc
        - ppc64el
        - riscv64
        uri: http://ports.ubuntu.com/ubuntu-ports
    preserve_sources_list: false
    security:
    - arches: *id001
      uri: http://security.ubuntu.com/ubuntu/
    - arches: *id002
      uri: http://ports.ubuntu.com/ubuntu-ports
  codecs:
    install: true
  drivers:
    install: true
  identity:
    hostname: noble-d02
    password: [redacted-filter]
    realname: [redacted-filter]
    username: mafoelffen
  kernel:
    package: linux-generic-hwe-22.04
  keyboard:
    layout: us
    toggle: null
    variant: ''
  locale: en_US.UTF-8
  network:
    ethernets:
      enp1s0:
        dhcp4: true
    version: 2
  oem:
    install: auto
  source:
    id: ubuntu-desktop
    search_drivers: true
  ssh:
    allow-pw: true
    authorized-keys: []
    install-server: false
  storage:
    config:
    - ptable: gpt
      path: /dev/vda
      wipe: superblock-recursive
      preserve: false
      name: ''
      grub_device: false
      id: disk-vda
      type: disk
    - device: disk-vda
      size: 1127219200
      wipe: superblock
      flag: boot
      number: 1
      preserve: false
      grub_device: true
      offset: 1048576
      path: /dev/vda1
      id: partition-0
      type: partition
    - fstype: fat32
      volume: partition-0
      preserve: false
      id: format-0
      type: format
    - device: disk-vda
      size: 2147483648
      number: 2
      preserve: false
      offset: 1128267776
      path: /dev/vda2
      id: partition-1
      type: partition
    - device: disk-vda
      size: 4454350848
      wipe: superblock
      flag: swap
      number: 3
      preserve: false
      offset: 3275751424
      path: /dev/vda3
      id: partition-2
      type: partition
    - fstype: swap
      volume: partition-2
      preserve: false
      id: format-1
      type: format
    - path: ''
      device: format-1
      id: mount-1
      type: mount
    - device: disk-vda
      size: 19112394752
      number: 4
      preserve: false
      offset: 7730102272
      path: /dev/vda4
      id: partition-3
      type: partition
    - vdevs:
      - partition-1
      pool: bpool
      mountpoint: /boot
      pool_properties:
        ashift: 12
        autotrim: 'on'
        feature@async_destroy: enabled
        feature@bookmarks: enabled
        feature@embedded_data: enabled
        feature@empty_bpobj: enabled
        feature@enabled_txg: enabled
        feature@extensible_dataset: enabled
        feature@filesystem_limits: enabled
        feature@hole_birth: enabled
        feature@large_blocks: enabled
        feature@lz4_compress: enabled
        feature@spacemap_histogram: enabled
        version: null
      fs_properties:
        acltype: posixacl
        atime: null
        canmount: 'off'
        compression: lz4
        devices: 'off'
        normalization: formD
        relatime: 'on'
        sync: standard
        xattr: sa
      default_features: false
      id: zpool-0
      type: zpool
    - pool: zpool-0
      volume: BOOT
      properties:
        canmount: 'off'
        mountpoint: none
      id: zfs-0
      type: zfs
    - vdevs:
      - partition-3
      pool: rpool
      mountpoint: /
      pool_properties:
        ashift: 12
        autotrim: 'on'
        version: null
      fs_properties:
        acltype: posixacl
        atime: null
        canmount: 'off'
        compression: lz4
        devices: 'off'
        dnodesize: auto
        normalization: formD
        relatime: 'on'
        sync: standard
        xattr: sa
      default_features: true
      id: zpool-1
      type: zpool
    - pool: zpool-1
      volume: ROOT
      properties:
        canmount: 'off'
        mountpoint: none
      id: zfs-2
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t
      properties:
        canmount: 'on'
        mountpoint: /
      id: zfs-3
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var
      properties:
        canmount: 'off'
      id: zfs-4
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/lib
      properties:
        canmount: 'on'
      id: zfs-5
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/lib/AccountsService
      properties:
        canmount: 'on'
      id: zfs-6
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/lib/apt
      properties:
        canmount: 'on'
      id: zfs-7
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/lib/dpkg
      properties:
        canmount: 'on'
      id: zfs-8
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/lib/NetworkManager
      properties:
        canmount: 'on'
      id: zfs-9
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/srv
      properties:
        canmount: 'on'
      id: zfs-10
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/usr
      properties:
        canmount: 'off'
      id: zfs-11
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/usr/local
      properties:
        canmount: 'on'
      id: zfs-12
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/games
      properties:
        canmount: 'on'
      id: zfs-13
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/log
      properties:
        canmount: 'on'
      id: zfs-14
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/mail
      properties:
        canmount: 'on'
      id: zfs-15
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/snap
      properties:
        canmount: 'on'
      id: zfs-16
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/spool
      properties:
        canmount: 'on'
      id: zfs-17
      type: zfs
    - pool: zpool-1
      volume: ROOT/ubuntu_nshf9t/var/www
      properties:
        canmount: 'on'
      id: zfs-18
      type: zfs
    - pool: zpool-0
      volume: BOOT/ubuntu_nshf9t
      properties:
        canmount: 'on'
        mountpoint: /boot
      id: zfs-1
      type: zfs
    - path: /boot/efi
      device: format-0
      id: mount-0
      type: mount
    swap:
      size: 0
  timezone: America/Los_Angeles
  updates: security
  version: 1

```
So playing with that and seeing how and what can be done with that...

EDIT: Reading through these files, I actually learned that Subiquity got it's name "[S]ubiquity" from "Ubiquity for Servers"...

---

### Post by lammert-nijhof on 2023-11-24
I already try for many weeks to install Ubuntu 24.04 in Virtualbox, but the new installer is crap! It freezes at the the user / password form all the time. I tried everything; safe graphics, 3D graphics ON/OFF; VBoxVGA. I tried it on my Ryzen 3 2200G desktop and on my old laptop with an i5-2520M.  Maybe in desperation I will clone Ubuntu 23.10 and try a very early system upgrade to 24.04. 
I have installed 4 flavors without any issue in VBox, fortunately they still use the old installer. 
I completely agree with the reorganization of the Ubuntu installer development team. If  that has no results in the next fortnight, cancel the whole project and  go back to the proven installer still used by the flavors.

---

### Post by MAFoElffen on 2023-11-24
@lammert-nijhof --

Keep an eye on this thread: [https://ubuntuforums.org/showthread.php?t=2492322](https://ubuntuforums.org/showthread.php?t=2492322)

Everyone has been pretty good on updating it with which dailys are working or not, with which bugs noticed on each. 

Also check the ISO tracker, where we log the daily ISO QA tests: [https://iso.qa.ubuntu.com/](https://iso.qa.ubuntu.com/) <-- quiverc is really on top of tracking that.

I do daily, then have other that were debian-upgraded (via sources.list) from Mantic, that I keep around to track daily updates to them.

---

### Post by Claus7 on 2023-11-25
Hello,

> **lammert-nijhof said:**
> ...It freezes at the the user / password form all the time. I tried everything; safe graphics, 3D graphics ON/OFF; VBoxVGA. ...
you might have tried to increase ram devoted for the virtual machine, as well as increasing the number of cpus, yet I'm proposing them here, since I didn't see a specific mention to them. I was facing similar behavior and without tampering with the above, installation was almost impossible.

> **lammert-nijhof said:**
> 
I completely agree with the reorganization of the Ubuntu installer development team. If  that has no results in the next fortnight, cancel the whole project and  go back to the proven installer still used by the flavors.
As mentioned by *MAFoElffen* the new installation provides some benefits to the developers: the thing is how many are these, if the most basic step of using ubuntu is to be able to install it without impediments. Fingers crossed, since it is still under development. Legacy installation, even if I haven't tested it lately, is still available under ubuntu download page.

Regards!

---

### Post by jbicha on 2023-11-25
The staffing situation was briefly mentioned on [Discourse]("https://discourse.ubuntu.com/t/pulse-19-ubuntu-desktop-engineering-roundup/38921") where it was said that the lead engineer for Ubuntu's new desktop installer has left Canonical. Some new developers are getting up to speed on the desktop installer (and other projects).

---

### Post by corradoventu on 2023-11-26
I can't find the Legacy ISO for Noble, has it been abandoned?

---

### Post by Claus7 on 2023-11-26
Hello,

> **corradoventu said:**
> I can't find the Legacy ISO for Noble, has it been abandoned?

I haven't come across legacy iso for noble. 23.10 has that option under the download page. If I'm not mistaken 22.04 has the legacy installation by default, since at that time the new installation wasn't available.

Regards!

---

### Post by jbicha on 2023-11-26
Our goal is to not provide a legacy installer for the Ubuntu Desktop 24.04 LTS release.

---

### Post by Dennis N on 2023-11-26
> **jbicha said:**
> Our goal is to not provide a legacy installer for the Ubuntu Desktop 24.04 LTS release.

Where is this goal documented?

---

### Post by oldfred on 2023-11-26
I think that makes sense as full Ubuntu does not really work for old systems that are legacy. 
Legacy/BIOS/CSM only systems need one of the lightweight flavors.

And new systems starting in about 2020 are UEFI only.

I wish installer would not install in UEFI mode to MBR systems. We find users who (incorrectly) installed Windows in BIOS/MBR mode on UEFI systems & then when Ubuntu installs in UEFI mode, break Windows system boot, by moving boot flag to new ESP. Needs some extra warning messages for those new users that do not understand UEFI vs. BIOS.

---

### Post by jbicha on 2023-11-26
> **Dennis N said:**
> Where is this goal documented?

It is vaguely mentioned in the [notes]("https://discourse.ubuntu.com/t/flavor-sync-meeting-notes-september-11-2023/38588") from the September desktop flavor sync meeting. There is a goal to move away from the old ubiquity installer, perhaps for all the desktop flavors. Canonical does not want Ubiquity to be in*main* any longer. If no other official flavor is using it, it can be dropped from *universe *&#8203;too.

---

### Post by MAFoElffen on 2023-11-26
As far as I can see... And remembering the DEV Cycle tests. The legacy installer 'was' supposed to die at 23.04... But then it wasn't 100% "for all systems" and they had to respin a legacy ISO to fill in the gap there. 

Subiquity took over the Server Edition (Live) Installer side with 20.04. I thought then, that the future Desktop plans were to move to the same installer (down the road), so that both used cloud-init and autoinstall.yaml. Well, since 23.04, here we are.

I always figured that is was still the goal for it to go away, once things were worked out for Desktop Edition being Subiquity with the Snap 'ubuntu-desktop-installer'.

But I am just a normal user and tester, like everyone else here. I am not in the decision, information or plan loop. (I wish I was privy to some of those things.) I am just a bystander, having to go with the flow, and deal with what is presented, and try to help make it work.

---

### Post by Dennis N on 2023-11-26
My particular issue with the installer is the lack of full LVM support (use existing LVs when installing an OS). An interesting discussion can be found in this thread (which I had bookmarked) - there are some good remarks posted in there.

[Feature request: Screen 8, custom LVM layout]("https://github.com/canonical/ubuntu-desktop-installer/issues/229")

---

### Post by #&amp;thj^% on 2023-11-26
> **Dennis N said:**
> My particular issue with the installer is the lack of full LVM support (use existing LVs when installing an OS). An interesting discussion can be found in this thread (which I had bookmarked) - there are some good remarks posted in there.

[Feature request: Screen 8, custom LVM layout]("https://github.com/canonical/ubuntu-desktop-installer/issues/229")

Thanks Dennis N that is a interesting read.
Sounds to me like the left hand knows nothing about what the right hand is doing. :o
Growing Pains.....

---

### Post by MAFoElffen on 2023-11-26
> **Dennis N said:**
> My particular issue with the installer is the lack of full LVM support (use existing LVs when installing an OS). An interesting discussion can be found in this thread (which I had bookmarked) - there are some good remarks posted in there.

[Feature request: Screen 8, custom LVM layout]("https://github.com/canonical/ubuntu-desktop-installer/issues/229")
+5000 -- Mine to. 

RE: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

Please Join that Bug as Affected...

No one will tell me what the new partitioner "is" (still). It's not PartMan. It doesn't recognize LUKS containers either.

I remember that is was mentioned on Discourse, in one of the discussions on ubuntu-desktop-installer, that the decision for going to the new partitioner was that it recognises "bitlocker"... <-- ??? BitLocker is Window OS. Why did recognising a Window OS encrypted container, and losing seeing any Linux Volume Managers and encrypted containers leverage the decision on that? That to me just seems backwards.

PartMan is the partitioner on the Server Live Installer, which is Subiquity, and uses Snaps for the install images... It already works.

---

### Post by corradoventu on 2023-12-17
ubuntu-desktop-installer 1278 is available but ISO still has the 1276 version. I successfully installed using the new version: [https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results)
Why ISO still has the old one?

---

### Post by MAFoElffen on 2023-12-17
I keep mentioning that in bug reports, that the installer is not finding newer gits, nor asking for a refresh... I think it's now time to report that as "the subject" of a bug report so that it doesn't keep getting skipped over, and not getting turned back on... It's just one boolean that turns that feature on in the installer.

@corradoventu -- Can you boo up that image > Use try > Open a terminal and do
```

ubuntu-bug subiquity

```
To report that as separate, with a title similar to: "Noble ubuntu-desktop-installer does not refresh"

Subject: 
Noble Ubuntu Daily 20231216 (or whatever your iso image was)

ubuntu-desktop-installer 1278 is available but ISO still has the 1276 version. Installer does not have refresh process turned on. Has been reported in other previous bug reports, but not separately, so keeps getting skipped over. This has still not turned on for this release cycle. 

Does not look for newer git, so does not recognize that there is a newer git, nor does not present the panel to update the installer to the newer git. That option is still turned off in the installer.

We need to test this process. please turn that on so we can test that process.

[HR][/HR]
I tried downloading today's ISO twice already. I can't boot today's daily. No graphics layer for me. Not even in the safe graphics mode. Filing a bug on that.

---

### Post by lammert-nijhof on 2023-12-19
Sunday I tried again to install Ubuntu 24.04 and it froze again in the user/password screen.  I have given up! 
I cloned the Ubuntu 23.10 VM and did a "do-release-upgrade -d" and now I have a working version of Ubuntu 24.04, but with the kernel 6.5.0.14 :)

---

### Post by MAFoElffen on 2023-12-19
Is a 'timing thing'... That is expected from time-to-time in the dev cycle. 

The Ubuntu 'installer' in the daily's is broken at the moment... Though Noble itself works and the repo is up.

---

### Post by corradoventu on 2023-12-20
Opened bug [https://bugs.launchpad.net/subiquity/+bug/2047034](https://bugs.launchpad.net/subiquity/+bug/2047034)
Thanks

---

### Post by MAFoElffen on 2023-12-20
@corradoventu --

Thank you.

I joined it as affected. (As everyone else testing Ubuntu & Budgie should also be affected right now with this...)

---

### Post by corradoventu on 2023-12-21
My last successful install was with ISO dated 2023-12-10 
[https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1743/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1743/results)
[https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results)
After this installer starts with a blank empty window 
[https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915)
When is a working ISO expected? Please post a message HERE so I can resume testing.
Thank you

---

### Post by Irihapeti on 2023-12-21
Just wondering, how does upgrading the installer work when you have WiFi only?  If you boot straight to the installer, as the test docs say, then you don't get an opportunity to update anything until you're asked if you want to connect to an SSID. Nor can you check the release notes link, but that's a separate issue.

Perhaps the connect to WiFi dialogue should come earlier in the piece, before the other online stuff?

---

### Post by MAFoElffen on 2023-12-22
I've really not thought about that that way... That is a good point.

When I tell people to use the Installer LiveUSB, I usually tell them first to use "Try" and then connect to their Home WiFi network, if that is what they use for networking... I have never tried to use the newer installers without a network connection. That hasn't been a condition in my test-cases in years.

Hmmm.

---

### Post by corradoventu on 2023-12-22
I install in English with Italian keyboard, so I start with 'Try ubuntu' connect to wifi, add and change my keyboard, do some test for the live and then start the install.
If checking with 'snap info ubuntu-desktop-installer' I see a new installer is available I refresh the installer and then start the install.
see my testcase [https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results)

Question: installer (both 1276 and 1278) was ok for me in ISO 2023-12-10, then in the following ISOs it fails with bugs 2043915 and 2044101. But installer is a snap, shouldn't it be independent from the rest of the environment?

---

### Post by MAFoElffen on 2023-12-22
Didn't one of us report ubuntu-desktop-installer not check nor recognize that a git was newer than the snap so did not ask to refresh? 

I can' find that this morning. I thought we did file it against Subiquity. If not, the I'll file it... I just really assumed one of us did.

---

### Post by corradoventu on 2023-12-22
You mean today installer recognize that a git was newer?
My bug for this problem: [https://bugs.launchpad.net/subiquity/+bug/2047034](https://bugs.launchpad.net/subiquity/+bug/2047034)

---

### Post by MAFoElffen on 2023-12-22
LO! Thank you... (And I was already attached to that Bug as affected.)

---

### Post by corradoventu on 2023-12-29
In the recent ISOs starting ubuntu-desktop-installer I have just a white blank window: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915)
Same starting snap-store.
for snap-store in Ubuntu 23.10 problem has sbeen solved: [https://github.com/canonical/snapcraft.io/issues/4489](https://github.com/canonical/snapcraft.io/issues/4489)

---

### Post by MAFoElffen on 2023-12-29
Yes. That was originally back last month, 2023.11.18. I am a part of that one.

It was resolved for a sort while, then after 2023.12.12, we have not had a successful ISO since that data. Since that one was still open. So we just keep referring back to that one.

EDIT: I forgot to say about the Snap Store... That problem actually started with 22.04.x, with an update/ snap refresh... It affects the Snap Store with releases 22.04.x and newer... (So pretty much almost all supported releases and newer.) I don't know exactly how it still hangs around after an update, but it does. And it doesn't really go away unless you reinstall it. This is how I have been leading people out of in the support sections, through that is this.
```

sudo snap refresh --edge snap-store
sudo snap refresh --stable snap-store

```
That will reinstall it and get rid of the bug.

Background for the next... The new install instead of downloading packages for a system base, it has a compressed system image inside the snap, that it extracts into the Live Image Environment's /tmp directory, then rsync's that image into the filesystem structure mounted to at /target.

What I don't understand is that, if we have known about this since forever, and we know the work-around is to reinstall it... Then you would think that they would replace that in the new system images. Then why are we getting new ISO image with this problem still in the git's system image? I'm fairly intelligent, and do not claim to know everything, but there seems like there is a disconnect with that, right? I know it is in the Snap, but... I guess maybe I don't just understand the "why" of that. If that is still in the system image as broken, then the new installations are just creating more victims. Right?

---

