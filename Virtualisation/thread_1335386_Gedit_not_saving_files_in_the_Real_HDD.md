---
title: "Gedit not saving files in the Real HDD"
date: 2009-11-23
forum: Virtualisation
---

### Post by wasim2050 on 2009-11-23
I installed Ubuntu 9.10 in VirtualBox. VirtualBox is installed in Windows 7. Everything is working fine but when I try to save a file in gedit on the real HDD it is giving an error although Gedit is saving files in the virtual HDD. So I installed other text editors in Ubuntu and those editors were able to save the file in the real HDD so I think the problem is with Gedit.

What do you guys think?

What should I do to correct this problem and where I should report this problem?

---

### Post by fjgaude on 2009-11-23
Frist off, when you save a file with gedit, where is it set to save the file? In Windows or in Ubuntu?

Have noticed where the other editors point to when they save?

The error message says the file is busy. That would mean that the host OS has control over the file. Maybe you should look into this.

---

### Post by wasim2050 on 2009-11-23
> **fjgaude said:**
> Frist off, when you save a file with gedit, where is it set to save the file? In Windows or in Ubuntu?

Have noticed where the other editors point to when they save?

The error message says the file is busy. That would mean that the host OS has control over the file. Maybe you should look into this.
Its D: formatted with NTFS so yes it is a Windows partition but Gedit is giving error while other editiors were able to save it in the same partition.

---

### Post by wasim2050 on 2009-11-23
> **fjgaude said:**
> Frist off, when you save a file with gedit, where is it set to save the file? In Windows or in Ubuntu?

Have noticed where the other editors point to when they save?

The error message says the file is busy. That would mean that the host OS has control over the file. Maybe you should look into this.
No the file was not busy in anyway it was a freshly created file to recreate the error so that I can show you guys the screenshot.

---

### Post by fjgaude on 2009-11-23
Was the file to be saved in Windows or Ubuntu? In what directory?

Okay, what other Linux editors are you using?

It would seem to go from Linux filesystem you would have to go through Samba to get to a Windows filesystem, I guess through Shares under VBox?

---

### Post by wasim2050 on 2009-11-23
> **fjgaude said:**
> Was the file to be saved in Windows or Ubuntu? In what directory?

Okay, what other Linux editors are you using?

It would seem to go from Linux filesystem you would have to go through Samba to get to a Windows filesystem, I guess through Shares under VBox?


I am using Nedit by installing it from Synaptic Pakage manager to save the files in Windows Partitions.

Yes I am sharing windows partitions in VitualBox see the screenshots.

Thanks.

---

### Post by fjgaude on 2009-11-23
Well, well... the only thing left is to make sure when you save in **gedit** you see the path through which it is to save. **Save As**, and then the path should show where the file is to go.

If it shows D:/<something> then there is something wrong with gedit. **Leafpad** is another good simple editor you might find works.

As for knowing where to post a bug report, open the **Help** menu of gedit, and click on** Report a Problem**. That should do it, all you can do for now.

---

### Post by wasim2050 on 2009-11-23
> **fjgaude said:**
> Well, well... the only thing left is to make sure when you save in **gedit** you see the path through which it is to save. **Save As**, and then the path should show where the file is to go.

If it shows D:/<something> then there is something wrong with gedit. **Leafpad** is another good simple editor you might find works.

As for knowing where to post a bug report, open the **Help** menu of gedit, and click on** Report a Problem**. That should do it, all you can do for now.
Thank you fjguade for ur help.

Yes I see the path through which I have to save the file.

I installed Leafpad and it is also working perfect in saving files in Windows Partitions.

---

### Post by fjgaude on 2009-11-23
I can't think of anything else to suggest... report the issue.

---

### Post by dcstar on 2009-11-24
> **fjgaude said:**
> I can't think of anything else to suggest... report the issue.

Chances are gedit is trying to read/write an attribute not supported by the underlying Windows file system, whereas the other editors don't.

Just another example of the problems of VMs accessing host resources directly and bypassing the (controlled) VM environment.

---

### Post by fjgaude on 2009-11-24
David, I don't know about that... I have a four-drive raid5 with ext3 formating which I access through the WinXP guest, using programs like Adobe InDesign and have no issues. I tell you, InDesign uses lots of control-codes to do its formatting of very complex text as well as graphics. Attributes can go from one file format to another without issue, I do believe.

I think if there's not enough RAM on the host or guest we run into much disk thrashing, causing lots of delay.

---

### Post by dcstar on 2009-11-25
> **fjgaude said:**
> David, I don't know about that... I have a four-drive raid5 with ext3 formating which I access through the WinXP guest, using programs like Adobe InDesign and have no issues. I tell you, InDesign uses lots of control-codes to do its formatting of very complex text as well as graphics. Attributes can go from one file format to another without issue, I do believe.


NTFS does not support the same attributes as a Linux filesystem, only a subset.

If Gedit tries to use an unsupported attribute, it will not be happy - it probably expects a Linux filesystem.

---

### Post by dcstar on 2009-11-26
> **wasim2050 said:**
> I installed Ubuntu 9.10 in VirtualBox. VirtualBox is installed in Windows 7. Everything is working fine but when I try to save a file in gedit on the real HDD it is giving an error although Gedit is saving files in the virtual HDD. So I installed other text editors in Ubuntu and those editors were able to save the file in the real HDD so I think the problem is with Gedit.


Ok, now I reckon I know **exactly** what the issue is.

Gedit - by default - creates a hidden backup file when you open something to edit. The filename is "."+ the name of the file you are editing + "~".

In NTFS, it is illegal to have a filename starting with "."

Turn off the Backup creation option in Gedit and the problem will go away.

This is just another example of the perils of using Linux apps on non-Linux filesystems.

---

### Post by wasim2050 on 2009-12-03
> **dcstar said:**
> Ok, now I reckon I know **exactly** what the issue is.

Gedit - by default - creates a hidden backup file when you open something to edit. The filename is "."+ the name of the file you are editing + "~".

In NTFS, it is illegal to have a filename starting with "."

Turn off the Backup creation option in Gedit and the problem will go away.

This is just another example of the perils of using Linux apps on non-Linux filesystems.


Nope its not working. Even after turning off the Backup creation option in Gedit it is giving the same error... :(

---

