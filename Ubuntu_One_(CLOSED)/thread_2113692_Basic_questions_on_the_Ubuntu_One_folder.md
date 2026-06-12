---
title: "Basic questions on the Ubuntu One folder"
date: 2013-02-08
forum: Ubuntu One (CLOSED)
---

### Post by lads on 2013-02-08
Hello everyone, I'm trying to understand how U1 works since I'm struggling to share files across several computers. Here's an example:

[LIST]
[*]On computer **A** I copied a new folder to */home/user/Ubuntu One* that contains about ten files. This operation is finished and there are no indicators of a synchronisation still going on.

[*]If I log in to **UbuntuOne.com** I can see this new folder, but inside there are only four files, not the ten I copied. Could this mean the upload to the cloud isn't finished yet? In total these files sum up to 30 Mb and where copied to the *Ubuntu One* folder days ago.

[*]I have the same U1 account configured in computer **B** but if I list the contents of */home/user/Ubuntu One* this new folder doesn't show up.
[/LIST]
I have two questions then:

[LIST]
[*]How can I make sure that a folder or file copied to */home/user/Ubuntu One* has been fully uploaded?

[*]How can force computer **B** to download what has been uploaded from elsewhere to the cloud?
[/LIST]

Thank you.

---

### Post by Isamu715 on 2013-02-13
Does Nautilus(the file manager) display a tick emblem on all the files in your folder?
> How can force computer **B** to download what has been uploaded from elsewhere to the cloud?In the Ubuntu One control panel check the "Sync Locally?" checkbox next to the folder you want to have fully downloaded.

---

### Post by lads on 2013-02-14
Hi Isamu715, thanks for replying.

> **Isamu715 said:**
> Does Nautilus(the file manager) display a tick emblem on all the files in your folder?

Yes, all files and folders under the *Ubuntu One* folder have a tick.

> **Isamu715 said:**
> In the Ubuntu One control panel check the "Sync Locally?" checkbox next to the folder you want to have fully downloaded.

I don't have a check box for the *Ubuntu One* folder, it simply says "Always in sync".

Regards.

---

### Post by Isamu715 on 2013-02-16
Do you use the same OS on both PCs? Or more precisely, do you use the same filesystem? Some filesystems have limitations when it comes to filenames and that may prevent some files from being synced to certain devices. For example, I have a folder with colons in its name and it syncs fine on Ubuntu systems but is inaccessible on my Android phone because of FAT32 limitations.

---

### Post by lads on 2013-02-26
Hello everyone, I continue to have issues like the one I reported initially.

This time I'm trying to synchronise my notes through the Ubuntu One files service, since they are deactivating their notes service. In computer **A** I moved the tomboy folder to */home/user/Ubuntu One* and then created a link to it in */home/user/.local/share/tomboy*. In computer A tomboy works as before and recognises all notes correctly.

Now in computer **B** I did a similar thing, removed the old tomboy folder and then created the symlink from */home/user/.local/share/tomboy* to */home/user/Ubuntu One/tomboy*. After doing this Tomboy doesn't recognise any notes in computer **B**. If I list */home/user/Ubuntu One/tomboy* in this computer it says it is empty.

What the hell is going on here? I'm using Ubuntu 12.04 on both computers, same kernel and the same file system. I have no warnings or errors from the Ubuntu One dameon. What can I do to sort this out?

Thank you.

---

