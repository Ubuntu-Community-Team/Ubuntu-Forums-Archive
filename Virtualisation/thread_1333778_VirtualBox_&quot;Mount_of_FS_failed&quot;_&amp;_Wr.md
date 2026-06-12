---
title: "VirtualBox &quot;Mount of FS failed&quot; &amp; Writing in recovery mode"
date: 2009-11-21
forum: Virtualisation
---

### Post by nrthguy on 2009-11-21
Hello all, 

Just earlier I had problems booting a wubi installation so ditched that to get on a fresh VB install. All's working, then I was editing my fstab so it'd mount a VirtualBox shared folder, 

The folder name was in caps and only after i shutdown the virtual machine i read I shouldnt be doing this, and now i cant boot, so i think this is the reason (its pretty much a clean install & updated without updating "installscripts" that seems to be braking the boot for some users since last week)

(btw it starts spitting some messages as soon as the black/white logo should be pulsing before the logon screen shows up, only then displays the error message and gives me recovery console, the boot menu is intact with its regular boot recovery memtest and memtest with something)

OK so I'm in recovery mode, but cant edit s*ite cos its in write mode eventho as sudo. 

Says something like "write only file system" and in vim "unable to open swap file for "/etc/fstab", recovery impossible"

I'd Really like to go around this without reinstalling.

---

