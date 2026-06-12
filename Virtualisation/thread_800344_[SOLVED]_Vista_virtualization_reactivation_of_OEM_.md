---
title: "[SOLVED] Vista virtualization reactivation of OEM copy"
date: 2008-05-19
forum: Virtualisation
---

### Post by ACGilbert on 2008-05-19
I used VMware Converter to virtualize an OEM copy of Vista and am running it in Ubuntu Hardy Heron using Virtualbox 1.6.
The virtualized Vista is requesting reactivation.
I'm pretty sure I can do that over the phone if necessary.
Will I still be able to use the original Vista? 
I don't want to delete it for a while just in case virtualization does not work out for me.

Credit for such a noob being able to get this far with virtualization goes to these forums and an article in Linux Format issue 101 by Jack Knight.

AC

---

### Post by FoH on 2008-05-21
From what I gather you are only allowed to have ONE installation of Vista on the hardware setup that your OEM license is bought with, virtualized or not. So if you do activate your VM Vista you would probably break the law. But there's a solution to your problem. If you run the command [FONT="Courier New"]slmgr -rearm[/FONT] in Vista "terminal" you get another 30 days. You can do this up to three times I believe :) Should give plenty of time to deside if it's working for you.

Personally, I'm trying to find out if the Dell installation DVD is valid for installation in a VM. I'm assuming the Vista license that came with my Dell computer is like any other OEM license, but when dealing with Microsoft and it's licenses you never can be too sure.

---

### Post by ACGilbert on 2008-05-22
Thanks for the reply FoH,
I'll give that command a try.
I'm off to other threads now to deal with USB.
Virtualbox sees them, but virtual Vista has them grayed out.
Other than that I'm in good shape so far.
AC

---

### Post by ACGilbert on 2008-06-07
This just seems to have solved itself.
Vista (virtualized) never asked again about reactivating.


FYI 

AC

---

