---
title: "Sucessfully installed WinXP in vmware.  Runnung well but one question."
date: 2007-11-14
forum: Virtualisation
---

### Post by ascus4 on 2007-11-14
As stated in the subject line, it appears that I have muddled through an install of WinXP onto Gutsy using vmware.  I appreciate the help I was given.  
I have a question, if I may.

Upon cleaning up used files after install, I moved the 'WindowsXPPro.iso' and 'cdrom.img' files to another folder to keep them for posterity.

When I started vmware and windows, it said it couldn't find those moved files.
Fair enough, I didn't want it to.
But, it refused to mount the cdrom and floppies because of this and plastered me with error messages.
I fixed this with the floppies by changing 'floppy0.startconnected' from true to false.  I don't have a floppy on this machine so, not a problem.

I fixed the error message with the CDROM by moving the .iso file back into place BUT...... it always mounts this iso file in the CDROM.  It won't let me put a different disk into the CDROM for use.
I figure I need to change one of the 'ide1:0' devices in the vmx file but what do I change it to?

I want my CDROM to act like a normal CDROM.

Thanks in advance.

EDIT:  Ok, got it.  Set ide1:0.filename to 'auto detect' and set ide1:0.deviceType to 'cdrom-raw.
Hope that helps someone.  Sorry to bother you all.

---

