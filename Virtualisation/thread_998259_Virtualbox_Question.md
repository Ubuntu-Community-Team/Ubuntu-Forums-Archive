---
title: "Virtualbox Question"
date: 2008-11-30
forum: Virtualisation
---

### Post by celticbhoy on 2008-11-30
Can anyone tell me if it is possible to set up an installation of XP under VirtualBox which can be accessed by any user on a multi user system?

I would like to set up XP under VirtualBox with around 10-20G, but allow anyone of my family who all have there own accounts in my install to use the same virtual XP system. Is this possible, and if so how?
:confused:

---

### Post by canthus13 on 2008-11-30
Save the image to a shared folder.

---

### Post by celticbhoy on 2008-12-02
I have set Virtualbox so that all info is saved on a drive partition completely seperate from my home folder, and set up a virtual XP instalation using one account, but how do I access this install from another Ubuntu account, as when I open Virtualbox under any other account the install does not show. How do I set up or add the install to that users virtualbox menu ???

---

### Post by Paqman on 2008-12-02
Can you create a new VM and point it to the existing disk image? I'm pretty sure I remember that being an option in the VM setup process.

---

### Post by cozmicharlie on 2008-12-02
Do the other users have access to the partition that vbox is set up on?  If not then the first step is to grant them access.  The next step is to make sure they are set up as users in vbox.  Go to System>administration>users and groups.  Unlock it and you should have a group called vboxusers.  Add all your users to that group.  They then should be able to access it.

---

### Post by Dedoimedo on 2008-12-02
Hello,
On each of these hosts, mount the xp hard disk (vmdk,located somewhere accessible by all of these users) file using the volume manager. Create virtual machines that use this hard disks. Then, each user will be able to run the virtual machine and make changes to the hard disk.
Dedoimedo

---

