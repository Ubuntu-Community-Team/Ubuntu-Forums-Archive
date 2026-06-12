---
title: "Help with VitualBox Sharing."
date: 2013-10-15
forum: Virtualisation
---

### Post by websterandy42 on 2013-10-15
If you are unintrested in backstory and just want to see the problem skip this paragraph.

So  i decided to start playing Fallout New Vegas again, since getting games  to work in linux is always pretty fun. but vanila fallout is pretty damn  boring by now so i decided to try and mod it using Nexus Mod Manager (a  program that is currently broken in wine). My solution to this was to:  set up a virtualbox Win7, then using VB share function to let NMM mod  the game files while remaining safely in VB. AND IT IS SOOO CLOSE TO  WORKING! it recognises the game files but says it is denied access.


I  can access/edit the shared files through the Win7 file manager but it  seems that VB does not let guest programs edit host files even if they  reside in the shared folder. Let me know if there is any way around this  or something small i'm missing.

---

### Post by JKyleOKC on 2013-10-16
In the Shared Folders area of the Settings dialogs for your VM, there's a column headed "Access" that probably says "Read only" at the present time. Click the "edit" button while viewing this list, and change the Access setting to "Full" then restart the VM and you should be in business.

---

### Post by websterandy42 on 2013-10-16
Thanks for the reply! Your advice worked (with a few tweaks to Win7 security settings). Wiith some tinkering New Vegas is starting get pretty close to stable.
If anyone else wants a full workthrough of how i did it just let me know.

---

