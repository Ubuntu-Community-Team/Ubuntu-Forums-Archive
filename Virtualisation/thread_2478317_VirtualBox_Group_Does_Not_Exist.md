---
title: "VirtualBox Group Does Not Exist"
date: 2022-08-22
forum: Virtualisation
---

### Post by Complete on 2022-08-22
Following on online youtube tutorial (am I allowed to post a link?).  I was trying to set up a shared folder.  It instructs me to open a command line terminal and add myself to a group 'vboxsf' (without the single quotes).    But it says this group does not exist.   Isn't this part of being connected to virtualbox that this group is generated?  I think I am connected because when I open the "Files" manager I see that when I click on "+ Other Locations" under Networks I see a couple folders "VIRTUALBOX (File Sharing)" that I am unable to access.

---

### Post by &amp;KyT$0P# on 2022-08-23
That group gets created when you install Guest Additions.

---

### Post by Claus7 on 2022-08-23
Hello,

and you might want to try bidirectional copy to clipboard or drag and drop to avoid the shared folder under Devices when you start your virtual machine and after you have installed Guest Additions.

Regards!

---

### Post by Complete on 2022-08-23
> **halogen2 said:**
> That group gets created when you install Guest Additions.

Great!  I assume it is Guest Additions on the Host, Virtual Box side.  But since this is a Ubuntu Forum, maybe there is something about Ubuntu that is a Guest Addition...?

---

### Post by Complete on 2022-08-23
The Devices menu has "Insert Guest Additions CD image"  So, when I saw it, I figured I needed to buy a CD from Oracle.  But I see that there already is a Drag and Drop option to click for "Host to Guest".  So I picked this.  But sadly, when I gave it a try to copy a folder onto the Ubuntu desktop, it did not work.  The mouse cursor was disabled.

[IMG]http://www.millionthompson.com/images/work/drag_and_drop.png[/IMG]

But clicking on "Insert Guest Additions CD image" seemed to have done SOMEthing.  When I looked at the "File" explorer, right about "+ Other Locations" there was a new item, "VBox_GAs_6.1.36"

I clicked on the "Run Software" button and something installed

[IMG]https://www.millionthompson.com/images/work/surprise.png[/IMG]

I rebooted and and now I could add myself to this group.

[IMG]https://www.millionthompson/images/work/itworks.png[/IMG]
[color=#00BF00]worker@virtualbox[/color]: $ whoami
worker
[color=#00BF00]worker@virtualbox[/color]: $ sudo adduser worker vboxsf
[sudo] password for worker:
Adding user 'worker' to group 'vboxsf' ...
Adding user woker to group vboxsf
Done.
[color=#00BF00]worker@virtualbox[/color]: $

But I am still "Unable to access location" when I click on any of the items in "Networks"
Please help.

---

### Post by &amp;KyT$0P# on 2022-08-24
> **Complete said:**
> now I could add myself to this group.

...

But I am still "Unable to access location" when I click on any of the items in "Networks"
Please help.

Did you log out and back in (or reboot the entire VM) after adding yourself to that group?
If you enable the shared folder to auto-mount in VirtualBox settings, can you access the shared folder from its /media/sf... mountpoint?

---

### Post by Claus7 on 2022-08-24
Hello,

after the successful installation of guest additions and rebooting your system you should enable bidirectional d&d and copy to clipboard. The steps you mentioned were prerequisites in order for the rest to work. 

Regards!

---

