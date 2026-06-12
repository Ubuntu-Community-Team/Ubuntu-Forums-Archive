---
title: "Can't boot to dmraid"
date: 2012-02-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by OliW on 2012-02-13
So I did an upgrade earlier. It didn't go well. The upgrade process was all over the place and ended up in a sort of half-upgraded state thanks to an issue in with the available packages list. Anyway. I rebooted into the broken half-upgraded state and fired off a apt-get install -f and everything else installed.

On reboot there's only one problem but it's a big one: I can't mount my root disk. I'm getting thrown to the floor with the excuse "ALERT!  /dev/disk/by-uuid/<MY UUID> does not exist". I check /dev/disk/by-uuid/ and it's accurate - my disk isn't in there.

This is a dm_raid45-handled array so I checked the /proc/modules and it's there. I fired off dmraid -ay and my root disk immediately showed up in /dev/disk/by-uuid/. LiveCD'd and chrooted into the system. Everything looks fine. I've added dm_raid45 to the initramfs-tools modules but that doesn't do anything additional (the module was loaded up before anyway).

So I'm not sure what to do now. I'm strongly contemplating a fresh install but I'd rather avoid it. Is there a way to force the boot sequence to run dmraid -ay as it boots? I reckon that would fix it. Any other tips?

---

### Post by Ibidem on 2012-02-13
> **OliW said:**
> So I did an upgrade earlier. It didn't go well. The upgrade process was all over the place and ended up in a sort of half-upgraded state thanks to an issue in with the available packages list. Anyway. I rebooted into the broken half-upgraded state and fired off a apt-get install -f and everything else installed.  On reboot there's only one problem but it's a big one: I can't mount my root disk. I'm getting thrown to the floor with the excuse "ALERT!  /dev/disk/by-uuid/ does not exist". I check /dev/disk/by-uuid/ and it's accurate - my disk isn't in there.  This is a dm_raid45-handled array so I checked the /proc/modules and it's there. I fired off dmraid -ay and my root disk immediately showed up in /dev/disk/by-uuid/. LiveCD'd and chrooted into the system. Everything looks fine. I've added dm_raid45 to the initramfs-tools modules but that doesn't do anything additional (the module was loaded up before anyway).  So I'm not sure what to do now. I'm strongly contemplating a fresh install but I'd rather avoid it. Is there a way to force the boot sequence to run dmraid -ay as it boots? I reckon that would fix it. Any other tips?  First, do old kernels--especially the oldest 3.2.x kernel you have--work? (is it the latest kernel or initramfs-tools that broke the scripts?)  Second, if you must change the init script, it's in /usr/share/initramfs-tools/init. Look for "maybe_break mount", and add dmraid -ay before it

---

### Post by OliW on 2012-02-13
> **Ibidem said:**
> First, do old kernels--especially the oldest 3.2.x kernel you have--work? (is it the latest kernel or initramfs-tools that broke the scripts?)The last Kernel I had was from Onieric. Sorry I should have made that clearer. This is an issue that has come about from upgrading to Precise. 

> **Ibidem said:**
> Second, if you must change the init script, it's in /usr/share/initramfs-tools/init. Look for "maybe_break mount", and add dmraid -ay before itUnfortunately that resulted in it just hitting a massive endless loop of things not found.

In an effort to get *something* up and running tonight, I did a clean install from today's daily-live CD. Tested the media (all okay!), had a royal battle blacklisting Nouvuea (which seems desperately unstable at the moment) but eventually managed to install it.

And after all that, nuking a year of data and configuration in the process  (I did do a backup), I got *Precise*ly nowhere. Same error about the disk missing only this time the initramfs doesn't have dmraid on hand so I can't even manually attempt to push it through. ](*,)

Seems like an epic bug with dmraid/initramfs and I honestly don't know what to try next. I'll wait to see what people suggest but if we can't get this worked out tomorrow, I'll have to fall back to 11.10.

---

### Post by Ibidem on 2012-02-14
> **OliW said:**
> The last Kernel I had was from Onieric. Sorry I should have made that clearer. This is an issue that has come about from upgrading to Precise. 

Unfortunately that resulted in it just hitting a massive endless loop of things not found.
...
And after all that, nuking a year of data and configuration in the process  (I did do a backup), I got *Precise*ly nowhere. Same error about the disk missing only this time the initramfs doesn't have dmraid on hand so I can't even manually attempt to push it through. 

Please file a bug report on Launchpad; this would be a serious issue.

You can add dmraid to the initramfs yourself, if you want to bother trying: [http://forums.debian.net/viewtopic.php?f=16&t=73452](http://forums.debian.net/viewtopic.php?f=16&t=73452)

---

### Post by treepleks on 2012-02-18
I have the same problem. I fall back on Busybox and have to issue a dmraid -ay and then exit to boot.

I solved this issue temporarily by editing the script at

```
/usr/share/initramfs-tools/scripts/local-top/dmraid

```

just adding the line in the middle of the 3 below

```

# Activate any dmraid arrays that were not identified by udev and vol_id.
dmraid -ay
if devices=$(dmraid -r -c); then

```

It works fine now... You need to have your initrd rebuilt. I just required the last kernel image to be reinstalled.

If you have filed a bug on launchpad, which number is it ? 
I will also "complain" :wink:

---

### Post by tista on 2012-02-19
> **treepleks said:**
> I have the same problem. I fall back on Busybox and have to issue a dmraid -ay and then exit to boot.

I solved this issue temporarily by editing the script at

```
/usr/share/initramfs-tools/scripts/local-top/dmraid

```

just adding the line in the middle of the 3 below

```

# Activate any dmraid arrays that were not identified by udev and vol_id.
dmraid -ay
if devices=$(dmraid -r -c); then

```

It works fine now... You need to have your initrd rebuilt. I just required the last kernel image to be reinstalled.

If you have filed a bug on launchpad, which number is it ? 
I will also "complain" :wink:

Hi treepleks,

What a nice tricks!! ;)
Yep exactly I've been waiting such solution for Intel RAIDs...
Even though I've already roll-backed (=reinstalled) my pp to oo, ASAP I would try it out...

Really nice! Then did you suppose what was the evil in precise system? If you've already tracked this issue down, please let us know... :)

Cheers,
Tista

---

### Post by woutervandergraaf on 2012-03-13
Is this the bug report?

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/941874](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/941874)

Wouter

---

