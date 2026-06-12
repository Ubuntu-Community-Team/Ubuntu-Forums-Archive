---
title: "[SOLVED] Need help starting VirtuallBox"
date: 2007-12-30
forum: Virtualisation
---

### Post by jmagick07 on 2007-12-30
I can't find a "group" setting anywhere

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=54668&stc=1&d=1199017720[/IMG]

---

### Post by ubukool on 2007-12-30
Hi,

go to system -->Administration---->Users and Groups

click on 'manage groups'

Scan down the list, there should be a group called 'vboxusers'. If there is, double click on it and make sure that your username is ticked so that you are a member of the group. If there is no group, create one by clicking on 'Add Group', typing vboxusers in the group name field and making sure that your user name is ticked so that you are a member. Then, log out and log back in again. When you a start your virtual machine, everything should work!

---

### Post by jmagick07 on 2007-12-30
well that fixed the groups problem.  Now it's telling me "no bootable medium".  I even tried putting in a Windows CD and it still says that!

What do I do now?

---

### Post by ubukool on 2007-12-30
have you installed XP and selected it as a virtual disk as explained in this guide?

[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)


This is the most useful guide I found for installing windows as a virtual machine within ubuntu

---

### Post by jmagick07 on 2007-12-30
> **ubukool said:**
> have you installed XP and selected it as a virtual disk as explained in this guide?

[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)


This is the most useful guide I found for installing windows as a virtual machine within ubuntu

Thanks, now I got it working :)

---

