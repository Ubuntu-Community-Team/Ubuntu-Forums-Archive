---
title: "Virtualbox Shared Folder and Zone.Identifier files"
date: 2010-05-11
forum: Virtualisation
---

### Post by nderic77 on 2010-05-11
Host: Lucid x64
Guest: XP SP3 32-bit
Virtualization: Virtualbox 3.1.6 r59338

Whenever I move files from my XP Guest to the Virtualbox shared folder, two things happen:

1. File date statistics get reset to current time (for Create, Modify and Access). This is frustrating.

2. For every file, a companion file with the extension: ".Zone.Identifier:$DATA" appears. For example, if I were to move test.xls from XP's "My Documents" to \\Vboxsvr\Documents , I would get two files:
test.xls (created / modified / accessed at present time) and
test.xls:Zone.Identifier:$DATA (with original create / modify / access times)

I suspect this is a Windows XP SP3 issue rather than a Virtualbox or Ubuntu issue, but was curious if any of you had encountered this and found a way to:

1. retain file attributes when copying from a windows folder to a Virtualbox shared folder and
2. Not create those zone identifier files

Many thanks.

---

### Post by Mizanthrope on 2010-12-24
> **nderic77 said:**
> 

1. retain file attributes when copying from a windows folder to a Virtualbox shared folder and
2. Not create those zone identifier files


The answer can be found here:
[http://forums.virtualbox.org/viewtopic.php?f=1&t=4814&start=0&sid=4619e20fc3e88c9fcfc34fe225a91b49](http://forums.virtualbox.org/viewtopic.php?f=1&t=4814&start=0&sid=4619e20fc3e88c9fcfc34fe225a91b49)

The latter file is supposed to be a stream on the former file, but it  ends up being created as a separate file.  THE FILENAME CONTAINS A COLON  WHICH IS INVALID IN WINXP. 

My purpose is not to try to get this fixed - according to the vbox  bug reports, this has been reported many times but the bugs get closed  as "not going to be fixed". 

Anyways, there's an easy way in the guest XP OS to prevent the  streams from being created.  Start up the group policy editor  (gpedit.msc), and drill down to: 

**User Configuration -> Administrative Templates -> Windows Components -> Attachment Manager** 

Locate setting: **Do not preserve zone information in the file attachments **and ENABLE IT! 

Now, when running in the virtual XP, any IE downloads that are  written to an NTFS share will NOT have the Zone.Identifier stream  created.

---

### Post by sf_basilix on 2011-03-17
I am running windows xp pro sp3 and when I run gpedit.msc, I cannot drill down to:

[B]User Configuration -> Administrative Templates -> Windows Components -> Attachment Manager 
[/B]
I can get as far as Windows Components, but I do not see any "**Attachment Manager**"

Any thoughts on how to configure this option without using gpedic.msc?

Thanks!

---

### Post by redmorning on 2011-09-09
> **sf_basilix said:**
> I am running windows xp pro sp3 and when I run gpedit.msc, I cannot drill down to:

[B]User Configuration -> Administrative Templates -> Windows Components -> Attachment Manager 
[/B]
I can get as far as Windows Components, but I do not see any "**Attachment Manager**"

Any thoughts on how to configure this option without using gpedic.msc?

Thanks!
Hi,

I'm running win xp 64 bit sp2.
Maybe you didn't recognize it, "**Attachment Manager**" is not in the left menu under the "**Windows Components**" but if you click "**Windows Components**", you will find it in the main window, in the list.

---

### Post by sf_basilix on 2012-02-08
> **piratejackus said:**
> Hi,

I'm running win xp 64 bit sp2.
Maybe you didn't recognize it, "**Attachment Manager**" is not in the left menu under the "**Windows Components**" but if you click "**Windows Components**", you will find it in the main window, in the list.

SOLVED: I am running windows xp sp3 and the option for "Attachment Manager" is nowhere to be found. I found another article online that explained why. It's because it is missing a template. Here is how to fix it:

(after following the gpedit.msc steps above in post #2, do the following)
If you do not see a folder called "Attachment Manager," scroll to the top of the window.
Right-click on the "Administrative Templates" folder under "Computer Configuration" and click "Add/Remove Templates."
Click the "Add" button, then double-click "system.adm." Click "Close."
Scroll back to the "Windows Components" folder. The "Attachment Manager" folder will be present.
([https://forums.virtualbox.org/viewtopic.php?f=7&t=47052](https://forums.virtualbox.org/viewtopic.php?f=7&t=47052))

---

### Post by sf_basilix on 2012-02-08
OK, so apparently after I made the changes, it's still creating the zone identifier files. I've noticed that it doesn't really do it when I copy a small text file over or even a small .exe file, but it does it every time I copy over a large .bin file.

Can anyone confirm if this happens with Windows 7?

---

