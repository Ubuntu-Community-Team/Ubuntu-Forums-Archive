---
title: "Is there a backdoor to C:?"
date: 2010-08-03
forum: Virtualisation
---

### Post by bigseb on 2010-08-03
So I can't get my usb to work (got XP running in VBox). Have some apps on there that I use. Is there a way to paste them into, say, the Documents and Setting folder in XP from Ubuntu. Is there way to find the C: drive and access it with nautilus?

---

### Post by endotherm on 2010-08-03
well, you can't really navigate to locations throught your vm (your guest can't touch the host, and the host can't touch the guest) except through "shared folders", which are supported in both virtualbox and vmware. 
here is a howto from virtualbox on getting it set up:
[http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868)

---

### Post by bigseb on 2010-08-04
Thanks! That looks the ticket. I'll try soon as I get a chance.

---

### Post by bigseb on 2010-08-04
:cry: :cry: :cry: :cry: :cry:

It won't do it. What am I doing wrong? I followed the instructions to the letter...

---

### Post by endotherm on 2010-08-04
> **bigseb said:**
> :cry: :cry: :cry: :cry: :cry:

It won't do it. What am I doing wrong? I followed the instructions to the letter...
what step is failing? did you install the host tools? after that, edit your virtual machine settings to create the shared folder. is that all set? if so, all that remains is to map the mount. if that fails it is likely a file permission issue.

---

### Post by bigseb on 2010-08-04
Found a different way:

Create a folder in host OS (Linux) as shared folder (give full read/write access and mark as shared for all users). In guest OS (Windows) open command prompt and type: net use C: \\vboxsvr\*sharename *and press enter. Reboot. Shared folder is now under My Computer. YAY!! Thanks for your help though. Much appreciated.

---

