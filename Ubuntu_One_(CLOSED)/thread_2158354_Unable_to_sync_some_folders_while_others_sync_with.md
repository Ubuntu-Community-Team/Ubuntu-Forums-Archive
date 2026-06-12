---
title: "Unable to sync some folders while others sync without problem"
date: 2013-06-28
forum: Ubuntu One (CLOSED)
---

### Post by actionmystique on 2013-06-28
Hello to everyone,

Platform: **Windows 7 64 bits / Ubuntu One 4.2.0**

[FONT=arial]I have uninstalled Google Drive client from my Windows 7 64 bits laptop approximately one week ago.[/FONT][FONT=arial]I used to share only two **folders **online.[/FONT]

[FONT=arial]Since then, I've been using Ubuntu One client.[/FONT]
[FONT=arial]I can sync all my folders online, except just those 2 reluctant folders. the weird part is that Ubuntu One says "File Sync In Progress", but nothing shows up in the current transfers...[/FONT]
[FONT=arial]
[/FONT][ATTACH=CONFIG]244238[/ATTACH][ATTACH=CONFIG]244239[/ATTACH][ATTACH=CONFIG]244240[/ATTACH][FONT=arial]
[/FONT]
[FONT=arial]Apparently, something was not completely done during uninstallation of Google Drive client (last release). For example,[/FONT]
[FONT=arial]- all **desktop.ini hidden files** were left behind inside all Google Drive folder and sub-folders. Removing them does not solve this aforementioned issue.[/FONT]
[FONT=arial]- the **permissions **of Google Drive were left assigned only to my account, instead of the usual 'Personal account, administrators and System". Changing these permissions do not solve this aforementioned issue either.

I've tried to contact Google Drive support team, but they are apparently ignoring this issue (like others I've run into, that's why I left...).
I've tried to contact Ubuntu One support Team, no answer so far.

Has anyone encountered (and solved would be so nice ;)) the same issue or does anyone have an idea about the possible source of this error?
[/FONT]

---

### Post by Irihapeti on 2013-06-28
From what I've seen, the Ubuntu One support team doesn't appear to be a very fast responder. It might be worth your while reporting a bug on Launchpad as well. I've had a response (though not immediate) when I've done that.

A workaround might be to define new folders from scratch and move your Google drive documents to those. Then you can delete the Google drive folder (since it will have nothing useful in it). You can mark these new folders as ones that need syncing.

If you do that, in my experience you don't need to upload everything again. The server somehow knows that the files just need to be moved.

---

### Post by actionmystique on 2013-06-29
Yes, your workaround should work, but this tree is very deep and wide (2600 files and 450 folders), so that's a lot of work for getting round a Google bug.
I would prefer another solution, which should help others as well.

These reluctant folders properties must be marked somehow with something that prevent them from being synced by Ubuntu One. I've tried to copy my local backuped folders to my drive and tried to sync them (with a different name) without any luck.

I've checked the registry with regedit and of course, Google left some dirt x3 under: 
[LIST]
[*]HKEY_CLASSES_ROOT
[*]HKEY_CURRENT_USER/Software/Classes
[*]HKEY_USERS/Long String/Software/Classes
[/LIST]

[ATTACH=CONFIG]244249[/ATTACH]

If anyone knows how to safely remove these, that might help.

---

### Post by Irihapeti on 2013-06-29
Wow! That is way above my pay grade. I'll leave it for someone else to answer.

I didn't realise that so many files were involved.

---

### Post by actionmystique on 2013-06-29
Hurrah! I've just found a trick to be able to sync those 2 reluctant folders online with Ubuntu One through a VM!

1) I've copied them and all their arborescence inside an Ubuntu 13.04 VM (VirtualBox)
2) I've moved them back to Windows NTFS file system with different top names next to the old folders.
3) I've deleted the old folders in Windows 7 NTFS.
4) I've renamed the new ones with the old names.
5) I've added them in Ubuntu One.
6) They are synced online! 

:D

It was a little more bumpy than it sounds though in the Ubuntu -> Windows direction.

---

### Post by Irihapeti on 2013-06-29
I'm glad you've got it sorted, even if it was more complicated than it needed to be.

And I love the word "arborescence". :)


Please would you mark the thread "solved". (See [http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730) for how to.)

---

### Post by actionmystique on 2013-06-29
I would not call that solved... just a workaround.

---

