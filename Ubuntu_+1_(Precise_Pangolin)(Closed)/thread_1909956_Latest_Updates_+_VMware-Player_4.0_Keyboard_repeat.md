---
title: "Latest Updates + VMware-Player 4.0: Keyboard repeat-keys disabled"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-16
Holding any key (such as a letter or a keyboard arrow) produces the same effect as pressing it only once. Looking at system settings, repeat keys is enabled, speeds/rates are adjusted.

It looks like it only happens when VMware-Player is running. It's random. In some sessions, there won't be keyboard problems. In others, you get the problem as soon as you alternate from the VM to Ubuntu for the first time.

Just touching the sliders in System Settings / Keyboard (no need to move them to any side) resets this to the expected behaviour (repeat-keys starts to work again, in rate/speeds that seem to be exactly coherent to the System Settings / Keyboard sliders).

Keyboard integration problems between VMWare and Ubuntu, as well as potential workarounds, were reported repeatedly in websites and Launchpad in 2008 and 2012. This was fixed in 2010, but it looks like it's back now. None of the old proposed fixes worked for me.

Before opening the report, I'd like to confirm if others see the issue in their setups.

---

### Post by fjgaude on 2012-01-16
Well, I've tried just about everything I can think of without an issue. Keys, repeat keys, work as expected.

Running a default 12.04 with Player 4, with your patches. Works correctly with or without Player loaded.

---

### Post by harald.k on 2012-01-16
I see the very same symptoms as described by [effenberg0x0]("http://ubuntuforums.org/member.php?u=260143").

This is even on a recently installed/upgraded 11.10 (oneiric) of Ubuntu.

I am using vmplayer 4.0.1, 64bit version.

Harald.

---

### Post by effenberg0x0 on 2012-01-16
Maybe this is relevant? I am using Ubuntu 64-bit and Windows 7 64-bit VMs when the problem happens. 

@fjgaude: Are you running Ubuntu 32-bit or 64-bit? WHat about the VM Operating System?

---

### Post by fjgaude on 2012-01-16
> **effenberg0x0 said:**
> Maybe this is relevant? I am using Ubuntu 64-bit and Windows 7 64-bit VMs when the problem happens. 

@fjgaude: Are you running Ubuntu 32-bit or 64-bit? WHat about the VM Operating System?

I'm running 64-bit 12.04, 11.10, 11.04, and VM of Windows XP 32-bit. Player works fine with all three OS installs on three different drives, one an SSD, same homebuilt computer in signature. Oh, the Player is 64-bit!

---

### Post by cariboo on 2012-01-16
FYI, this was posted on the ubuntu-devel mailing list this morning by Bryce Harrington:

> On Mon, Jan 16, 2012 at 01:04:13AM -0800, Scott Ritchie wrote:
> Ubiquity has been crashing for me on VMware Player, both for dailies and
> Alpha 1.  This sounds like the sort of bug that wouldn't have survived
> long if vmware installs were part of the new smoke testing process.
bug #?

> Is there a "blessed" (ie, regularly tested working) VM for Ubuntu out there?
I don't know the answer to that, but we've been in coordination with
Vmware on the X side for the upcoming xserver/mesa deployment this week,
and expect breakage this week, with resolution later this week once the
vmware X driver is rebuilt against the new stuff.  So regardless of the
current state, we would expect it to be working within 1 week, or 2 at
the latest.

Bryce

---

