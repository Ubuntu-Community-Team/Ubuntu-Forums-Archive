---
title: "noauto ignored in fstab in 20.04?"
date: 2020-07-18
forum: Server Platforms
---

### Post by iamsrp on 2020-07-18
I have some entries with the "noauto" option in my my fstab. These are local disks, attached via esata. Since around 20.04 it appears that the noauto option is no longer being respected. Has anyone else seen this?

I am pretty sure I didn't see this in the previous LTS release.

Steve

Example entry:
[FONT=courier new]
#<file system>                            <mount point>     <type>  <options>                                <dump>  <pass>
UUID=4a90a13d-9eab-4fb0-a646-6cedee6be036 /disk/XXX         ext4    defaults,relatime,noauto                 0       1
[/FONT]

---

### Post by rbmorse on 2020-07-18
I've got one in my fstab that works as expected.  I put noauto as the first item in the option section, but I don't know if that makes a difference.

---

### Post by iamsrp on 2021-06-27
I figured this out in the end. It was because I was exporting the directory over NFS. As such it looks like systemd(?) figured out the dependency and forced the mount to happen. Removing the partition from [FONT=courier new]/etc/exports[/FONT] stopped it from being mounted at boot time.

Steve

---

### Post by MAFoElffen on 2021-06-27
So this is "Solved" now? It appears to me, in your last post, that it is.

If so... Just saying... You could mark it as such, so others with a similar problem can find what helped you solve it.

---

### Post by TheFu on 2021-06-27
If you'd like storage mounted as needed, on demand, use **autofs**.

Somewhere around 16.04, systemd-mount took over control of the fstab processing. It broke a number of things, like the trick to force an fsck on a partition at the next boot by doing **sudo touch /forcefsck**.  <--- that doesn't work any more and I haven't found any easy way to force an fsck at boot without console access.  The possible solutions require modifying the grub boot options or using tune2fs to force an fsck much more often.

I suspect the fstab issue is with having "defaults" listed, when you don't want all the defaults. The manpage says:
```
              defaults
                     use default options: rw, suid, dev, exec, auto, nouser, and async.
```
So the line says auto, then no auto.  Which is it?

---

### Post by LHammonds on 2021-06-28
> **TheFu said:**
> I suspect the fstab issue is with having "defaults" listed, when you don't want all the defaults. The manpage says:
```
              defaults
                     use default options: rw, suid, dev, exec, auto, nouser, and async.
```
So the line says auto, then no auto.  Which is it?
What do you mean?  It just says **auto** and then **nouser**.

LHammonds

---

### Post by TheFu on 2021-06-28
defaults,relatime,noauto
becomes
 rw,suid,dev,exec,[COLOR="#FF0000"]auto[/COLOR],nouser,async,relatime,[COLOR="#FF0000"]noauto[/COLOR]
after expansion. Those options conflict. The actual implementation should cleanly address it, but bugs like that are common.

---

### Post by LHammonds on 2021-06-28
Ah gotcha.  You were talking about the OP's usage...not the "defaults" by itself.  But if the end-user has "defaults" in the line, they should really know what that contains and only use it "if" they need each of those settings.  But I get wanting the system to correct such mistakes but that means it would need to cancel an option...and at least error log the situation.  Is there no error log entry if auto and noauto is used on the same line?

LHammonds

---

### Post by Morbius1 on 2021-06-29
But ..... that's not how fstab is implemented. It is read from left to right so if "defaults" is used first and that means "auto" it is replaced with "noauto" ( and any other subsequent settings ) as it is read until the end of the fstab record.

Order matters. If "defaults" appeared after "noauto" the situation is different. That's why you often see folks follow the "user" option with "exec" since "user" sets noexec.

Anyhoo, "defaults" is basically only used when you have no other options since you can't leave an empty field in the fstab record. The default settings will always be applied first if "defaults" is there or not because .. well ... those are the defaults for that filesystem.

---

### Post by TheFu on 2021-06-29
I see in the fstab manpage that LINES are interpreted from top to bottom.

The mount(8) manpage says:
```
The usual behavior  is  that  the
       last option wins if there are conflicting ones.
```
So the last option seen wins. Confirmed.  I need to check all my mounts .... found 1 system where "defaults" came after an option. That system probably started around 2006 and has been upgraded since.  Don't think the added option conflicted.

---

### Post by MAFoElffen on 2021-06-29
So it reads left to right, and if an option to the right conflicts, then it overrides the previous (that was to the left of that)? That is what I read from the last two posts from Morbius1 and TheFu, right?

---

### Post by TheFu on 2021-06-29
> **MAFoElffen said:**
> So it reads left to right, and if an option to the right conflicts' then it overrides the previous (that was to the left of that)? That is what I read from the last two posts from Morbius and TheFu, right?

Yep.  I think of it as there's 1 slot for each setting.  The default values are what gets placed into each slot.  If any newer value is seen, then it replaces the existing slot regardless.  That could be to affirm or to change.

Sorta like how in bash scripting, the last value setup is the value used.

```
#!/bin/bash
CONT="yes"
CONT="no"
echo $CONT
```
The "yes" is there, until the "no" overwrites it.

---

