---
title: "file permissions from a cd"
date: 2008-05-24
forum: Security
---

### Post by jaime77 on 2008-05-24
hi,
before hardy every time i copy a folder (with files) from a cd, it was copied with permissions read and write, i like it, in fact i stop using kubuntu and return to ubuntu because kubuntu set the permissions of the files read only, that dont work for me, why they change that in hardy?
what logic in that files copied from a media to home folder are read only?
its more likely people copy the files so they can work with them, otherwise they will keep it in a read only cd.
also, i use kino (and for some settings permissions changed 2 or 3 versions before, now i have to run kino with sudo or cant get video from ieee1394 or firewire or ilink, whatever) so every video i capture or made is owned by root, i can move those videos from folder to folder (i think i cannot move some file owned by root that was read only) without problems or sudo, is something wrong with permissions or just is the way it works.
thx

---

### Post by Steve413z on 2008-05-24
CD's usually don't have file permissions, I think it might be some weird settings in konqueror that were setting the permissions weird

---

### Post by jaime77 on 2008-05-26
i may not explain myself good enough
im using ubuntu hardy, and when copy folders and files from a cd to my home or desktop directory, nautilus copy them with read only permissions
how i change that?
so every time i copy some folder from a cd to home, has read and write permissions (like in every prior version of ubuntu)

---

### Post by rustyz on 2008-05-27
been trying to solve this simple task for over three weeks...

stil no go...

tried all sorts of permission changes... 

the last was run "chmod u+rw -R <folder name>"

and that didnt work...

on gutsy til this is solved...

rz

---

### Post by jaime77 on 2008-05-28
hey rusty,
i can change the fold and file permission after copied to home.
cant you?
what i want is that everytime i copy some file or folder to home from a cd it has read and write permissions by default.
its the way its always been work in ubuntu, so no idea why they changed it in hardy

---

### Post by hyper_ch on 2008-05-28
a cd is by definition read-only and I tend to think linux (as well as windows) will respect that and copy the files as read-only to your harddisk.

---

### Post by rustyz on 2008-05-29
i have used CD-R's to do this on Feisty, and Gutsy...

i do believe the CD-R vs CD-RW is for re-writable on the disk itself...

stil a no go on this matter...

have seen this was a problem with the old Dapper Drake...

lets keep searching for a fix!

and a simple one...

rz

---

### Post by jaypmcwilliams on 2009-01-01
TO: jaime77 


I know EXACTLY what you speak of. I'm currently having the same issue with Ubuntu Intrepid AMD64. You're right, 7.10/Gutsy did EXACTLY what you speak of & it had NOTHING to do with respect, rights or licensing. The other responders in this matter just do not seem to get it. Therefore, we will report this issue DIRECTLY to the correct people. As well as, our development team taking a direct look at it. So far, it IS in Nautilus & you can change permissions. However, when you click on "Apply permissions to Enclosed Files" It DOES NOT change them too. the tree only goes one level deep & needs to be addressed deeper. LOL... It gets VERY annoying when try to restore backup files from CDs/DVDs to home.

---

### Post by jaypmcwilliams on 2009-01-01
> **jaypmcwilliams said:**
> TO: jaime77 


I know EXACTLY what you speak of. I'm currently having the same issue with Ubuntu Intrepid AMD64. You're right, 7.10/Gutsy did EXACTLY what you speak of & it had NOTHING to do with respect, rights or licensing. The other responders in this matter just do not seem to get it. Therefore, we will report this issue DIRECTLY to the correct people. As well as, our development team taking a direct look at it. So far, it IS in Nautilus & you can change permissions. However, when you click on "Apply permissions to Enclosed Files" It DOES NOT change them too. the tree only goes one level deep & needs to be addressed deeper. LOL... It gets VERY annoying when try to restore backup files from CDs/DVDs to home.

OK... Figured it out. They used to have this EXACT problem in Konqueror not Nautilus. Now it's REVERSED! because they integrated Konqueror tabbing into nautilus using Konqueror protocols. I used Konqueror to change permissions & applied to other folders/files & it worked. It seems that in Nautilus, it may be a security risk & disabled the feature. However, for the time being, Konqueror will save time. the button in Nautilus does NOTHING past one level. it's an update/patch/fix they need to address. hope this helps you. It helped me. END.

---

