---
title: "Remove stop for missing entries in FSTAB on boot"
date: 2010-08-11
forum: Server Platforms
---

### Post by UnresponsiveBeeVictim on 2010-08-11
How do I keep the system from hanging up at boot if something that is in /etc/fstab isn't present in the computer at the time?  I don't want to remove the entries in the server, but it makes the system a pain if a HDD gets pulled quick and the system ends up rebooting - I have to go plug in a keyboard and press S so it will continue booting.  Really annoying.
Thanks.

---

### Post by bodhi.zazen on 2010-08-11
In the options column, add the option noauto

```
/dev/sdxy  /media/mount_point ext4 noauto 0 0
```

---

### Post by UnresponsiveBeeVictim on 2010-08-11
Wouldn't that make the harddrives not mount at boot and require me to manually mount them?

---

### Post by FuturePilot on 2010-08-11
Yes it would. See this post [http://ubuntuforums.org/showpost.php?p=9681911&postcount=2]("http://ubuntuforums.org/showpost.php?p=9681911&postcount=2")

---

### Post by UnresponsiveBeeVictim on 2010-08-11
> **FuturePilot said:**
> Yes it would. See this post [http://ubuntuforums.org/showpost.php?p=9681911&postcount=2]("http://ubuntuforums.org/showpost.php?p=9681911&postcount=2")

Yeah, I found that after searching.
> To workaround it you need to add "nobootwait" to the line in fstab but sadly this breaks the manual use of the mount command.
This makes it a non-option.  Pretty ridiculous to have a headless server breaking bug that gets no attention.

---

### Post by brettg on 2010-08-11
This is not a bug BTW, you probably shouldn't be pulling drives from production servers at random and then rebooting them really.

If you simply must do that for whatever reason then you simply need to use the "no auto" option as previously suggested and then add a script to /etc/rc.local that attempts to mount the drive(s) at the end of the boot sequence in whatever manner you require. If that fails to mount the drive your script should handle that gracefully and your "server" will still successfully boot sans that pulled drive.

As usual, linux gives you several ways to do whatever it is you are trying to do. Calling out "bug!" because the default method of achieving a goal (mounting disks at bootup) doesn't suit your <ahem> "unusual" usage patterns isn't particularly helpful. 

Good luck and HTH

---

### Post by UnresponsiveBeeVictim on 2010-08-12
> **brettg said:**
> This is not a bug BTW, you probably shouldn't be pulling drives from production servers at random and then rebooting them really.

If you simply must do that for whatever reason then you simply need to use the "no auto" option as previously suggested and then add a script to /etc/rc.local that attempts to mount the drive(s) at the end of the boot sequence in whatever manner you require. If that fails to mount the drive your script should handle that gracefully and your "server" will still successfully boot sans that pulled drive.

As usual, linux gives you several ways to do whatever it is you are trying to do. Calling out "bug!" because the default method of achieving a goal (mounting disks at bootup) doesn't suit your <ahem> "unusual" usage patterns isn't particularly helpful. 

Good luck and HTHThe reason it pissed me off is because I lost a drive and the server dropped off line later, only to not come back up because of this.  I had to drive 60 miles to press the S key on a keyboard.

Judging by this: [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444)
It -is- a confirmed bug.  Adding a fix (nobootwait) breaks the mount command, that's not a bug?  Yes, I understand that there are more ways to do this, but the point remains.

---

