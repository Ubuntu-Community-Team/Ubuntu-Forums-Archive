---
title: "Proper way to backup/restore a VirtualBox guest OS?"
date: 2009-05-20
forum: Virtualisation
---

### Post by timzak on 2009-05-20
I'm just thinking ahead to my next Ubuntu install (Karmic).  I like to backup my data, format my drives, and install from scratch.  How would I back up my guest OSes in Virtualbox so I don't have to reinstall them as well?  Is there a proper way, or is it a simple copy/paste to a backup drive?

Thanks!

---

### Post by lazyart on 2009-05-20
They are simple files.  Copy them elsewhere and you're good.  Of course, Karmic is 5 months away, but it's always good to know your backup plan.

---

### Post by timzak on 2009-05-20
Does this still apply to my question?
[http://www.bgevolution.com/blog/virtualbox-backup-restore/](http://www.bgevolution.com/blog/virtualbox-backup-restore/)

That basically says the same thing the first respondent said.

However, this blog seems to indicate that it's not as simple as copy/paste:
[http://www.derekhildreth.com/blog/how-to-properly-backup-a-virtualbox-machine-vdi/](http://www.derekhildreth.com/blog/how-to-properly-backup-a-virtualbox-machine-vdi/)

I'm using Ubuntu 9.04 and version 2.2.2 of VirtualBox for AMD64.

What's the right procedure?

---

### Post by tkoco on 2009-05-23
Both answers are correct. The difference is in the "machine" settings. If a particular virtual machine has special settings, copying the "vdi" file will lose those machine settings. The better way to backup the "virtual machines" is to export them as a virtual appliance. Both the machine settings as well as the harddrive are saved. 
> **timzak said:**
> Does this still apply to my question?
[http://www.bgevolution.com/blog/virtualbox-backup-restore/](http://www.bgevolution.com/blog/virtualbox-backup-restore/)

That basically says the same thing the first respondent said.

However, this blog seems to indicate that it's not as simple as copy/paste:
[http://www.derekhildreth.com/blog/how-to-properly-backup-a-virtualbox-machine-vdi/](http://www.derekhildreth.com/blog/how-to-properly-backup-a-virtualbox-machine-vdi/)

I'm using Ubuntu 9.04 and version 2.2.2 of VirtualBox for AMD64.

What's the right procedure?

---

