---
title: "Modifying Text Files for configuration"
date: 2009-10-12
forum: The Cafe
---

### Post by msimon1960 on 2009-10-12
Just a suggestion for the Ubuntu development team:

Please connect a high voltage source to the 'sudo gedit' command so that everytime someone on the team tries to tweak the system into working by modifying one of the hundreds of background configuration files they get a lethal electrical shock.

In the short term there will be a slight decrease in the members of your team but in the long run many of the 'bugs' will mysteriously disappear.

It looks to me that it's too easy for the propellor heads to tweak something instead of actually fixing it.

Pick a few things, do them very well, and then move on.  Please start with the Ubuntu <--> Windows networking!  There will be no acceptance of Ubuntu Linux until it learns to network.

I'm just saying...:lolflag:

Matt

---

### Post by Grifulkin on 2009-10-13
It networks just fine, with Samba.

---

### Post by matthew.ball on 2009-10-13
> **msimon1960 said:**
> There will be no acceptance of Ubuntu Linux until it learns to network.
As far as I am aware, and this forum is a pretty good indication of that, Ubuntu *has* already been accepted.

---

### Post by msimon1960 on 2009-10-13
Samba?  shiver...I've tried samba versions bundled with Dapper through Jaunty.  Never worked without SERIOUS tweaking...and with only marginal functionality.

Name resolution appears to be the Achilles heel of the system when connecting to Windows shares.  I'm currently struggling with browsing to a D-link DNS-323 NAS (Samba Server 3.0.24) configured for SMB.

The browsing GUI doesn't work (per usual) but I can force name resolution by modifying the hosts file (there should be a GUI for this).

I nearly trashed the system using the permissions GUI.  Fixed with the help of some linux experts on this forum (for which I'm grateful) who applied backdoor solutions to reset what the GUI had done and could not undo.

---

### Post by Mike'sHardLinux on 2009-10-13
I've been using Samba since the 90's and it has worked fantastically for me! I even set up my previous employer with a Linux server serving a Windows network and Samba does most of the work -- beautifully. It has been running for years. 

I am by no means an expert at this stuff. It is not that hard as you seem to think.

Don't form your opinion of Samba based on some limited piece of hardware. A lot of people end up hacking that device to make it more functional.

---

### Post by msimon1960 on 2009-10-13
Obviously posted tongue-in-cheek.

I did find a GRUB GUI editor -- works very well and the more common options are available. I hope they continue to expand on it.

I'm just saying that GUI's for the common text configuration files would be a huge benefit in reducing the learning curve for new linux users.

My favourites would include:

- GRUB
- The hosts file
- the fstab (and related files)

Matt.

---

### Post by Mike'sHardLinux on 2009-10-13
I thought there already was a GUI for fstab?  And the hosts file....there's almost nothing to it. I cannot imagine how a GUI would help????

:guitar::popcorn::lolflag:

---

### Post by cariboo on 2009-10-13
Most configuration files are so well commented, that you really don't need a gui to edit anything.

The problem with using a gui to set up configuration files is that you don't learn anything. You then have to depend on someone else to help you fix something when you screw it up.

---

### Post by mehaga on 2009-10-13
> **cariboo907 said:**
> Most configuration files are so well commented, that you really don't need a gui to edit anything.

The problem with using a gui to set up configuration files is that you don't learn anything. You then have to depend on someone else to help you fix something when you screw it up.

No, you depend on *something* else - the GUI ;) And, being just a regular user, I see nothing wrong with that. I edit config files very rarely, and when I do, I always wish I had a GUI. Not only to help me edit the thing, but also to save me from horror of looking for it :)

---

### Post by msimon1960 on 2009-10-19
I don't find the configuration files well commented at all -- the syntax is not explained in most cases.  For instance, look at /boot/grub/menu.lst -- some of the options are there but the syntax is not documented and there is not much explanation of concept and useage.

In a GRUB GUI the options would be available for selection with context sensitive help files for conceptual/useage issues.

I absolutely understand where some long-time linux users are coming from -- I started in the scripting world of JCL (job control language) and MS-DOS batch files.  I was so used to working that way I found GUI's kinda clunky (and many were in the early days of MS-DOS/Windows) -- I now realize their value in getting things done in complex systems.

Matt.

---

