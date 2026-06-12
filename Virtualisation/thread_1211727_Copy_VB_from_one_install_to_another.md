---
title: "Copy VB from one install to another"
date: 2009-07-13
forum: Virtualisation
---

### Post by PerfectReign on 2009-07-13
I've searched and cannot find an appropriate answer. I've read this - [http://ubuntuforums.org/showthread.php?t=1181742&highlight=copy+virtual+box+vdi](http://ubuntuforums.org/showthread.php?t=1181742&highlight=copy+virtual+box+vdi) - thread but no luck.  I've also seen items on the virtualbox forums.

I recently migrated/upgraded my mom's computer over from openSUSE 10.2 (KDE 3.5x) to Ubuntu 9.0x (GNOME 2.x).

I changed her username from francie to fc and thus her home partition. I copied over her .Virtualbox folder to the new system and tried to load up VB. I seem to be running into errors.

I've tried editing VirtualBox.xml file but keep getting UUID errors. I tried copying what I can, but am having issues. 

Here's teh latest error I get:

> Could not find a CD/DVD image with UUID  {393112d2-9048-4f9a-bf5a-38f30435dd04} in the media registry  ('*/home/francie/*.VirtualBox/VirtualBox.xml'). 
Result Code: 
VBOX_E_OBJECT_NOT_FOUND (0x80BB0001) 
Component: 
VirtualBox 
Interface: 
IVirtualBox {3f4ab53a-199b-4526-a91a-93ff62e456b8} 

Any ideas?  I could recreate Vista and reload all the apps, but that is SUCH a pain.

](*,)

---

### Post by quixote on 2009-07-14
I'm not sure what the magic bullet is.  I've had both ways work and both not work: 1) copy over .VirtualBox from /home/me and all the virtual machines, including fussy old Windoze, are there, and 2) do the same thing and wind up having to reinstall the stupid thing.

Have you tried setting up a "new" machine in vbox that points to an "existing harddisk", ie the install of Vista that you're trying to get it to recognize?  I did that once and it worked.

Alternatively, I wonder whether it might be worth setting up a new Vista vm, checking to see what its UUIDs are, and then using those in the Vista vm you actually want to use.  ??  I doubt it'll work, but it might be worth trying before spending several days reinstalling everything.

---

