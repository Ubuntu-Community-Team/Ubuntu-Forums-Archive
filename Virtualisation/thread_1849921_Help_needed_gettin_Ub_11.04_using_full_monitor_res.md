---
title: "Help needed gettin Ub 11.04 using full monitor res in VM, and others"
date: 2011-09-25
forum: Virtualisation
---

### Post by SweetBearCub on 2011-09-25
Hi folks.

I'm running Ubuntu 11.04 x32 as a guest, in VirtualBox (latest version) on a Windows 7 Ultimate x64 host.

When I press Host+F to make the VM go full-screen, Ubuntu is only running at 1024x768, centered on my (1280x1024) screen. When I go to System - Preferences - Monitors, the maximum resolution is listed as 1024x768, and currently selected.

The VM has 12 MB of vram allocated, which should be enough, correct?

Speaking of, the VM detected that I was running Ubuntu when I named the VM, and chose several default settings. The only things I changed were to delete the floppy drive and to lower the allowed CPU cap to 40%.

Also, even though I have enabled shared folders, picked a host folder, and given it a nme for it to show up in the VM as, Ubuntu does not see it. How should I troubleshoot that?

Also, I left clipboard sharing set to "Bidirectional", as my password manager is on my host, but when I copied a password to the host's clipboard, the VM's clipboard was blank. How can I fix that as well?


Thanks!

---

### Post by SweetBearCub on 2011-09-26
Somewhat fixed. I had forgotten to install the VirtualBox VM Guest Additions. I will make a separate post on any further specific issues.

---

### Post by DAB4970 on 2011-09-29
That would've been my first suggestion -- Guest Additions.

---

