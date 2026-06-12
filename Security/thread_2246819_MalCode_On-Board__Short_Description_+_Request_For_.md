---
title: "MalCode On-Board:  Short Description + Request For Steerage"
date: 2014-10-03
forum: Security
---

### Post by Nagi_Mani on 2014-10-03
I have a simple five page (text and images only - no code-level stuff) pdf document showing more detail - if someone wants to provide me with directions on how to deliver the pdf doc.  For present purposes, a short version bullet-list follows:

1. suspicious "foreign" folder in home/user directory (can't be deleted, shredded, removed, erased, or Bleach-Bit-ed)
2. system monitor and gparted show altered and "foreign" devices/drives/partitions
3. top/htop (command line) results show suspicious line item "rootkit....-fork"
4. system monitor show suspicious process/process properties "rtkit-daemon"
5. clamtk shows two threats:
-a. usr/lib/mono/4.0/mscorlib.dll  (PUA.Win32.Packer.PrivateExeProte-7)
-b. usr/lib/mono/4.5/mscorlib.dll  (PUA.Win32.Packer.PrivateExeProte-7)

I'm not a gearhead or code-genie, so I can't say all the above are problems, or that they're even relevant to the problems.  But I've done my best to check and report anything suspicious on face value to me as a sorta-kinda-mid-level user of ubuntu/xubuntu and home-PC's.

Ideally, someone would provide me with a ten-character terminal command which would mystically, automatically and completely resolve this problem(s) in under ten seconds.  But with ShellShock, BadUSB, RootKits galore, and a genral light speed ramping up of all things malcode right now (and for the past six months), all I can do is:

1. ask for someone with serious code and forensic skills to take delivery of my pdf report, look it over and fire back at me (here or email), or
2. trash my xubuntu/asus-eeepc box, all USB's, and start from scratch

That's as concise as I can make this situation in the first post.  Standing by for comebacks or spankings, as the case may be.

End of problem-report and request for guidance.

/

Sidebar Comment on Linux AV and IP Scanners:

- Both McAfee and Kaspersky carry enterpise Linux AV products which can be purchased pretty cheaply by home users, but I do not YET know anything about how that process or the physical product would work.  Currently, clamav and clamtk ought to be slick enough by now to provide GUI's which are user friendly, and which AUTOMATICALLY update both virus sigs AND engines, but they don't.  Put another way, that ought to be the default state of those two AV packages, bit it isn't.  Unless / until that happens, I'll be looking at other AV packages... probably for a long time, since the current rash of malcode has (a) caught AV and OS industries with their pants down and asleep at the wheel, and (b) we're ALL gonna be dealing with the current malcode-rash aftermath for a long, long time (e.g., shellshock, badusb, et al).  That means years - not months, weeks or days.  If you don't believe that, just keep your bash / update logs for a year.  You will see this material again.

- I'm attempting to make correct settings for angryIPscanner so that it (the GUI) shows only open ports and any IP's connected to them,  That ain't working out too well.  I only mention this because I seem to recall using something very similar on my old U10.04 system which worked perfectly on both counts "out of the box" in GUI form.  Maybe this is a matter of degenerating user brain cells (mine), or maybe it's a result of leaving so many <!#%&$!> functions "user-elected" that the average user gets lost in setup.  File this one in "newer versions of EVERYTHING no longer JUST WORK".

I mention these two sidebar items for a reason which (I believe) relates to malcode vulnerability (among other things):  Newer versions, updates and upgrades of most e-products today are pumped out on a manic cycle of 30 to 180 days, along with altered product branding, design, taxonomy and even code-nomenclature.  That makes the products bloated, buggy, unnecessarily complicated, and require faster/shorter user learning curves.  That's bad juju for customers/users (if that matters to anybody out there), and it can't do the products sellers much good to dump substandard products on the market so fast that nobody has any genuine product/brand loyalty - except for people with single digit IQ's who follow logos instead of quality.  It also makes the products more vulnerable to malcode since even the products' code writers can't protect the product sufficiently before they drop kick it into the market place.

And not fer nothin', but whatever happened to writing instructions, manuals and user guides with
- keystroke-specific text instructions (for every single chronological step)
- accompanying screenshots (for every single chronological step)
- assuring that a chimpanzee can read, understand and follow the instructions and screenshots as presented (user-tested pre-release)

... my bad... that takes longer than a 30 day new product cycle allows.  :)

There endeth the rant.

Nagi

---

### Post by Habitual on 2014-10-03
Check your [Notifications]("http://ubuntuforums.org/usercp.php") (PMs)

---

### Post by Nagi_Mani on 2014-10-04
@ Habitual:  Done.  Standing by.

---

### Post by Habitual on 2014-10-04
and replied.

---

### Post by ventrical on 2014-10-04
Comodo Antivirus for 12.04


Works great with realtime guard.

Have to manually update sigs thorugh GUI.

Regards..

---

### Post by Habitual on 2014-10-04
Except for the mono files, I don't see anything that can't be explained.

---

### Post by cariboo on 2014-10-04
This type of thread really doesn't help anyone else that may be having a similar problem. If you are going to solve a problem via pm, please request that the thread be jailed, instead of making vague references to what may be going on.

---

### Post by Nagi_Mani on 2014-10-06
> **cariboo907 said:**
> This type of thread really doesn't help anyone else that may be having a similar problem. If you are going to solve a problem via pm, please request that the thread be jailed, instead of making vague references to what may be going on.

Be patient - I'm digitally challenged.  Update with non-sensitive detail to follow soonest.

Nagi

---

