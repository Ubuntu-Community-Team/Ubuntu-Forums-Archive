---
title: "use linux to scan windows partition for virus?"
date: 2010-05-12
forum: Security
---

### Post by brook adams on 2010-05-12
Hi,

I'm dual booting 10.04 with windows 7 and it occurs to me that I could scan the windows partition for viruses FROM linux.

Is anybody doing this sort of thing? Does that make any sense?

---

### Post by bodhi.zazen on 2010-05-12
Please see the sticky at the top of these forums

[http://ubuntuforums.org/showpost.php?p=9265657&postcount=9](http://ubuntuforums.org/showpost.php?p=9265657&postcount=9)

---

### Post by Chayak on 2010-05-13
Trying to scan for a virus from Linux is a poor solution at best.  In all honesty most anti-virus systems do rather poorly when up against the latest threats.  A really good example is Zeus. It's constantly changing and it should be one of the main ones to worry about.  As a malware analyst it'll take me a bit to get through all of the protections that have been built into it and by the time I have a report out on it a new version is already out.  Signature based malware detection is a loosing game.

That said Linux anti-virus solutions are behind windows solutions.  Two of the better I've seen for detecting unknowns is Kaspersky and Symantec's Sonar.

The safest way to operate these days is to have a Linux base with no remote services active, yes zero, not even ssh. Then use VirtualBox or VMware to create a windows VM and then snapshot it in a clean state.  You use it then revert it back to a clean state and update it from that clean state before snapshotting again.  You drag anything you want to keep onto the Linux system.

If you need to game then install a windows partition but don't use it for surfing, just for games.

I've used this sort of set up about three years at DEFCON (the most hostile wireless network on the planet) and walked away with a safe system which I based on forensic hashing and examination of all the files before and after.

---

### Post by Kinstonian on 2010-05-13
I'd say everything Chayak said is correct.  But to add on to what he said:

> Trying to scan for a virus from Linux is a poor solution at best; **if it's the only thing you do**.

There is a lot more to determining whether your computer is compromised than just AV software.  Registry analysis, Event log analysis, create a timeline, etc.  The downside is that they require more skill, where an AV scan isn't as effective, but is a lot easier to do.

However, if you take Chayak's suggestion of using a Virtual Machine where you can just revert back to a snapshot after using it, then you could probably skip all the work involved in trying to determine whether your computer is compromised.

---

