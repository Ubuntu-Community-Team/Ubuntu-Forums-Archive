---
title: "Logon via SSH makes idle hard disks wake up?"
date: 2012-06-16
forum: Server Platforms
---

### Post by MichaelAnders on 2012-06-16
Hi folks,

I have a Ubuntu 12.04 x64 server running here with 10 hard disks. To save power, I use hdparm and let them go to sleep. So far so good.

However, once I log into the system via SSH all hard disks wake up. This is totally unneeded! As each hard disk wakes up after another it can take 20 seconds from entering the password till I can enter the first command.

Does anyone know what to do or how to narrow down what causes it? I searched the forum and the internet too but didn't find this.

Thanks!

---

### Post by LHammonds on 2012-06-16
From what I have read, the sleep vs standby modes can react different based on the kernel, driver, configuration, controller and physical drive.

I don't have Ubuntu installed outside a virtual environment so I'm not gonna be much help.  I looked around for you too but could not find anything conclusive.

It might be a read-ahead event or something like that.

Are the drives mounted?  Maybe if they remained unmounted until you needed them might solve the problem.

LHammonds

---

### Post by MichaelAnders on 2012-06-16
> Are the drives mounted? Maybe if they remained unmounted until you needed them might solve the problem.
Yeah, they are indeed mounted. I can't unmount them though - it's a file server and the files should be accessible instantly (after the related hard disk woke up).

---

### Post by guiclaw on 2012-11-02
Did you ever fix this issue? I'm getting the same thing with 5 drives, initial ssh after a while takes forever. I apt-get --purge remove landscape-common which removed the login information which I thought could be causing it by checking the usage on the drives but it still happens! :(

---

### Post by soundcheck on 2013-02-27
Today I stepped over this thread and figured it ended with a loose end.

I'd like to share a workaround that I digged out (lost the link reference - it's not my invention) later on.

It works for me when doing ssh or scp. My external disks remain parked.

The rule disables udisks polling, which is wakeing up all disks at certain events.

You'd need to configure a new udev-rule e.g. /etc/udev/rules.d/80-udisks.rules

add these lines to it:

```

KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="usb", ENV{DEVTYPE}=="disk", ENV{UDISKS_DISABLE_POLLING}="1"
KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", ENV{UDISKS_DISABLE_POLLING}="1"
KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="scsi", ENV{DEVTYPE}=="disk", ENV{ID_VENDOR}=="ATA", ENV{UDISKS_DISAB
LE_POLLING}="1"

```

Reboot.

Hope that helps. Let us know if it works for you too.

Cheers

---

### Post by Topfjoer on 2013-03-07
Hi Soundcheck,

I also had the issue of unnecessary/undesired disk spin-ups when ssh'ing into my server and I've been trying to find a solution for several days a few weeks ago without any success. I'm trying your solution/workaround for two days now and it appears to work. Haven't had any issues since!

Many thanks!

---

### Post by jvanhie on 2013-05-22
Hi all,

I also tried Soundcheck's solution since I gave up on this problem a while ago, but sadly enough it wasn't working for me. Rejuvenated by the prospect of finding a fix I restarted my search for the problem and found the culprit (on my system at least): **/usr/lib/update-notifier/update-motd-fsck-at-reboot**
It's a script called in **/etc/update-motd.d/** at each login to display which drives will be checked for errors on next reboot. For users still struggling with waking disks after Soundcheck's fix, it might be interesting to look at this.

See my answer at [askubuntu]("http://askubuntu.com/questions/282245/ssh-login-wakes-spun-down-storage-drives/") for some more details.

---

