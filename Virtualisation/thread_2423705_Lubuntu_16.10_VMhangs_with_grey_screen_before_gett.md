---
title: "Lubuntu 16.10 VMhangs with grey screen before getting to login prompt"
date: 2019-07-27
forum: Virtualisation
---

### Post by ianmanning on 2019-07-27
I've been running Lubuntu 16.10 in an ESXi VM for a couple of years. I needed to expand the boot disk size, and managed to do this by booting to a Gparted ISO. Now the OS will not boot to the UI - I get past the Lubuntu splash screen but then I just get a grey screen. I can TTY into it, I just can't get the GUI.
Any ideas for how I can fix this?

---

### Post by TheFu on 2019-07-27
No reason to bother solving this issue.  Support for 16.10 ended in mid-2017.  Please move to a supported release.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Review the "standard support" column for when free support ends.

You could check the fstab and blkid are still correct.

---

### Post by ianmanning on 2019-07-28
fstab problem sounds likely, but I have no idea what may be wrong with it, or how to fix it (I'm a Linux noob). My fstab is pretty vanilla:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
/dev/sda1               /               ext4            errors=remount-ro      0       1
# swap was on /dev/sda5 during installation
/dev/sda5               swap            swap            sw              0       0
```

and this is what I get when I run blkid:
```
/dev/sr0: UUID="2017-10-11-10-08-40-00" LABEL="GParted-live" TYPE="udf" PTUUID="2d876634" PTTYPE="dos"
/dev/sr1: UUID="2017-10-11-10-08-40-00" LABEL="GParted-live" TYPE="udf" PTUUID="2d876634" PTTYPE="dos"
```

Can anyone suggest how to diagnose/fix? 

The terminal at startup includes this error:
```
XOpenDisplay("") failed
Trying again with XAUTHLOCALHOSTNAME=localhost
***XOpenDisplay("") failed. No -display or DISPLAY
***Trying ":0" in 4 seconds
```

---

### Post by ianmanning on 2019-07-28
Hmmm...according the the df command it looks like /dev/sda1 has been mounted, but not /dev/sda5 (which is where the swap partition should be)

---

### Post by TheFu on 2019-07-28
swap isn't "mounted" in a way you'll see in df.  Unimportant.
The lack of UUIDs being used in the fstab and that blkid isn't showing any for those partitions **is** an issue.

More reasons to move to a supported LTS release.
Not worth trying to fix.

---

### Post by oldos2er on 2019-07-28
Moved to *Virtualisation*.

---

### Post by ianmanning on 2019-07-28
> **TheFu said:**
> swap isn't "mounted" in a way you'll see in df.  Unimportant.
The lack of UUIDs being used in the fstab and that blkid isn't showing any for those partitions **is** an issue.

More reasons to move to a supported LTS release.
Not worth trying to fix.

I'm not seeing how moving to a supported release would help. Would an in-place upgrade fix the blkid issue and restore the broken XWindows system? It would almost certainly break some other aspects of my setup, which is why I don't have time to routinely upgrade to each new release.

Can someone clarify - is this forum strictly limited to support for current releases? If so, where would be the best place to pose general Ubuntu/Linux support queries which are not release-dependent?

---

### Post by guiverc on 2019-07-30
If you don't like release-upgrading every 6-9 months, stick to LTS or long-term-support releases, which have 5 years of support for main Ubuntu (desktop, server) or 3 years for flavors like Lubuntu. Had you have installed Lubuntu 16.04 LTS, it was supported from 2016-April until 2019-April .

Stack Exchange's Unix & Linux I don't believe has rules about EOL releases; but older releases are harder because software changes, `man` pages are no longer easily accessed due to EOL status of your release, so it takes more effort, may require some guess work (eg. we do have 16.04's manual pages, and 18.04's but not the EOL releases between) thus is more likely to consist of errors.  Sticking to LTS releases does make support easier if you don't like the regular release-upgrades.

---

### Post by ajgreeny on 2019-07-30
Upgrades are not really a viable option for you as you would have to go first to 17.04 then from there to 17.10 and finally to 18.04, and as the repos are no longer active, or not in their usual place anyway, you would be working entirely with EOL repos.  This would be a long and tedious activity, and very prone to problems which will be just as difficult to solve as this 16.10 problem.

Do yourself a big favour and do a clean install of 18.04 in place of your 16.10 VM; alternatively keep your 16.10 and add 18.04 to the list of VMs you have, assuming that is possible with ESXi, about which I know nothing at all having used VirtualBox only.

---

### Post by ianmanning on 2019-08-02
> **ajgreeny said:**
> Upgrades are not really a viable option for you as you would have to go first to 17.04 then from there to 17.10 and finally to 18.04, and as the repos are no longer active, or not in their usual place anyway, you would be working entirely with EOL repos.  This would be a long and tedious activity, and very prone to problems which will be just as difficult to solve as this 16.10 problem.

Do yourself a big favour and do a clean install of 18.04 in place of your 16.10 VM; alternatively keep your 16.10 and add 18.04 to the list of VMs you have, assuming that is possible with ESXi, about which I know nothing at all having used VirtualBox only.

Thanks for your reply. If I do a clean install of 18.04 is there a fairly straightforward way of migrating my existing packages from the old to the new platform? I have a Home Assistant and Mosquitto-MQTT running in Docker containers and also a Mediawiki site. I set these up years ago, and it would be painful to work out how to re-install it all.
This was very much intended as a "set and forget" server, so the need to upgrade regularly due to the unavailability of legacy repositories to fix things when they break is a real problem for me, particularly as I have extremely limited Linux expertise and not a whole lot of time to devote to keeping the platform running.

---

### Post by ajgreeny on 2019-08-02
Sorry but "Home Assistant and Mosquitto-MQTT running in Docker containers and also a Mediawiki site" means very little to me and I do not know them, nor how they are set up in a Ubuntu OS, so I'm afraid you will have to await a reply from someone else who is more able to help with those questions.

I have been using a separate /home partition for many years so a clean install is possible without losing any of my own folders or files; any edits I have made to system files are noted and kept in backups in my /home so they can be restored if necessary.

---

### Post by guiverc on 2019-08-02
My favorite way of 'skipping' releases (or going backwards; eg. back to a prior LTS) is to backup obviously, boot installer-ISO, and use the 'something else' option (it's called *Manual Partitioning *in modern Lubuntu) and select my partitions and ensure I don't have format selected.

The installer takes note of your installed apps, wipes system directories (doesn't touch your /home), installs the system, then adds back the software you've added if available for the new release in the repositories. It works very well with Ubuntu repos, wasn't intended for 3rd party sources and I haven't used it with containers.  Key to this is not selecting format.  (it disables PPA's or 3rd party; you just let this run and fix the 3rd party stuff yourself if you still need it)

If you want a 'set and forget', you should use a LTS or long-term-support release; ie. had you used 16.04 LTS it is still supported (~21 months of life left), and release-upgrading that is easy (longer grace applies to LTS and you can always opt to switching to ESM). Using a non-LTS release was a mistake.

---

### Post by TheFu on 2019-08-02
> **ianmanning said:**
> 
This was very much intended as a "set and forget" server, so the need to upgrade regularly due to the unavailability of legacy repositories to fix things when they break is a real problem for me, particularly as I have extremely limited Linux expertise and not a whole lot of time to devote to keeping the platform running.

Wish that someone would have told me I didn't need to do  backups or patch weekly.   Life would have been so much easier these last decades.

 I want what you have!

---

