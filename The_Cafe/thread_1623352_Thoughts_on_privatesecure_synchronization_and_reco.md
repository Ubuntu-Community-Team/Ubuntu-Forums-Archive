---
title: "Thoughts on private/secure synchronization and reconciliation of ~/ data, settings."
date: 2010-11-16
forum: The Cafe
---

### Post by czr114 on 2010-11-16
I use two primary systems, a laptop and a desktop, both on Lucid x64. Currently, it's a mess to keep any sort of synchronization between the two, for things as large as an entire Thunderbird mail folder (everything stored locally), down to a newly added bookmark or adblock filter, and encompassing everything from keys imported to GPG to work in progress in MonoDevelop.

The machines share a LAN, and it's not too terribly difficult to keep them roughly identical through export and import functions, with data shared over sshfs locally, and copied when the laptop must break LAN connectivity with the desktop. Wholesale repetitive folder moves are accomplished with shell scripts. The whole process is repetitive and annoying.

The current mainline thinking for solving this problem is some sort of cloud or remote storage approach which involves full data surrender to a commercial third party. This is a non-solution for reasons of privacy and security.

The local synchronization angle is simple enough. Backup tools or even custom scripts are able to quickly place one set of data in another location.

Problem one is the trouble of reconciliation, which might be necessary if one system is not completely locked out while the other is used.

Problem two is the bandwidth. Straight copying of ~2GB of data is not feasible over anything but a LAN link.

Problem three is the annoyance. Having to check out profile settings and saved data from one to another is a repetitive task which any power user should want to eliminate.

I have come up with only three solutions: 

1. Make the laptop overwhelmingly thin, and reducing using it almost entirely
2. Write custom backup software to run differential copies on what can be moved that way, and attempt to reconcile things like bookmarks and mail, using personal webspace as the exchange point for the whole package, and GPG to keep everything safe in transit.
3. Put up with the annoyance.


Any ideas from the crowd?

---

### Post by earthpigg on 2010-11-16
wonky and not fully thought out idea, but here goes:

if you tell nm-applet to make your wifi 'available to all users', it will connect before you login.

use 'startup applications' to run a script that mounts key dotfolders and dotfiles on the desktop in your local home folder the moment you log in.

if you are ever on the road and need access to the data, and you left your desktop turned on, then you can access the data as needed.

---

### Post by cariboo on 2010-11-16
How about setting up cloud storage yourself on a third computer, and having it accessible from everywhere?

---

### Post by czr114 on 2010-11-16
That might be the solution, but it seems a bit heavy for personal use.

---

### Post by handy on 2010-11-16
I use Xmarks to keep my Firefox Bookmarks synchronised, it works very well, & you can encrypt them too.

I don't know if you could set up rsync to work both ways on your systems?

---

