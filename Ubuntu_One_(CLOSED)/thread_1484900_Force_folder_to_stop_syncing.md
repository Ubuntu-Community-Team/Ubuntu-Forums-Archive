---
title: "Force folder to stop syncing"
date: 2010-05-16
forum: Ubuntu One (CLOSED)
---

### Post by Jim Danner on 2010-05-16
The files on my account are out of sync with the ones on my computer (through some connection issues and some faults of my own), so I'm getting a lot of sync conflicts and my local files get renamed with ".u1conflict" appended.

No big problem, I can handle the renaming issue, but I'd like to empty the online storage for the moment to sort out the files on my computer. However, when I right-click the synced folders and select *Stop synchronizing on Ubuntu One*, nothing changes: it keeps syncing and this command gets grayed out in the context menu.

Is there a way to force Ubuntu One to stop syncing a folder?

---

### Post by joshuahoover on 2010-05-17
> **Jim Danner said:**
> The files on my account are out of sync with the ones on my computer (through some connection issues and some faults of my own), so I'm getting a lot of sync conflicts and my local files get renamed with ".u1conflict" appended.

No big problem, I can handle the renaming issue, but I'd like to empty the online storage for the moment to sort out the files on my computer. However, when I right-click the synced folders and select *Stop synchronizing on Ubuntu One*, nothing changes: it keeps syncing and this command gets grayed out in the context menu.

Is there a way to force Ubuntu One to stop syncing a folder?

The best way to do this right now is to do the following:


[LIST=1]
[*]In a terminal session (Applications->Accessories->Terminal)  run: u1sdtool --list-folders
[*]Copy the ID of the folder you want to stop synchronizing
[*]In a terminal session run (replacing ID-COPIED-FROM-STEP-2):  u1sdtool -q; u1sdtool --start; u1sdtool --delete-folder=ID-COPIED-FROM-STEP-2;  u1sdtool -c
[/LIST]
 Note, syncdaemon will do a local rescan of the folder you  unsubscribed (stopped syncing) which means it will take some time  processing this folder one last time, but will not attempt to do a sync.  After that, the folder will no longer be processed.

This is something we will be fixing, as I captured a bug for it here: [https://launchpad.net/bugs/576080](https://launchpad.net/bugs/576080) 

Thank you,

Joshua

---

### Post by Jim Danner on 2010-05-17
Thanks Joshua.

---

### Post by uiberto on 2010-05-18
Thanks for the update.

I had this same problem. The u1sdtool --delete=ID just hung for 15 minutes on a small folder so I canceled my subscription altogether then rebooted. Then, I went back and renamed the .u1conflict files. Problem solved.

It's a little scary that Ubuntu One was apparently making changes to my files directly instead of using copies of the data.

Hope you can address this .u1conflict. Would love to use the product in the future.

uiberto

---

### Post by Jim Danner on 2010-05-18
> **uiberto said:**
> It's a little scary that Ubuntu One was apparently making changes to my files directly instead of using copies of the data.

Hope you can address this .u1conflict.As far as I understand (maybe I am seeing it wrongly?) the creation of .u1conflict files serves precisely to *avoid* making changes to files directly. When it detects a version conflict, Ubuntu One keeps your file unchanged and only renames it by appending .u1conflict to its name. You can then put the originals back using the terminal with a command like ```
IFS=$'\n'; for i in $(find -name "*.u1conflict"); do mv -f "$i" "${i%.u1conflict}"; done
```

What I don't understand, however, is the series of conflict files: filename.u1conflict.1, filename.u1conflict.2, etc., each with a different timestamp. What are these files (what is their content) and why are they created?

---

### Post by joshuahoover on 2010-05-18
> **Jim Danner said:**
> As far as I understand (maybe I am seeing it wrongly?) the creation of .u1conflict files serves precisely to *avoid* making changes to files directly. When it detects a version conflict, Ubuntu One keeps your file unchanged and only renames it by appending .u1conflict to its name. You can then put the originals back using the terminal with a command like ```
IFS=$'\n'; for i in $(find -name "*.u1conflict"); do mv -f "$i" "${i%.u1conflict}"; done
```What I don't understand, however, is the series of conflict files: filename.u1conflict.1, filename.u1conflict.2, etc., each with a different timestamp. What are these files (what is their content) and why are they created?

The conflict files are created when the Ubuntu One syncdaemon detects that there is a difference between the file on the server and the file on the local computer. As you pointed out, we do this so data is not loss. Now, why you're getting multiple conflict files, I'm not sure. If you'd like to help us figure out why, you can do the following, which will provide us with more detailed debug info:

[LIST=1]
[*]Open (or create if it doesn't exist):  ~/.config/ubuntuone/syncdaemon.conf
[*]Add the following 2 lines to this file and save: 
[main] 
 log_level = DEBUG
[*]Run: u1sdtool -q; u1sdtool --start
[*]Try to reproduce behavior that caused the multiple conflict files to appear
[*]File a new bug report at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)
[*]Run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######
[*]Attach  ~/.cache/ubuntuone/log/syncdaemon.log and  ~/.cache/ubuntuone/log/syncdaemon-exception.log to the bug report
[/LIST]
Thank you,

Joshua

---

### Post by Jim Danner on 2010-05-19
> **joshuahoover said:**
> The conflict files are created when the Ubuntu One syncdaemon detects that there is a difference between the file on the server and the file on the local computer. As you pointed out, we do this so data is not loss. Now, why you're getting multiple conflict files, I'm not sure. If you'd like to help us figure out why, you can do the following, which will provide us with more detailed debug info:
At the moment my sync problems are already over, so I'm not getting these files anymore. If it happens again, I'll send you that debugging information.

Cheers, Jim

---

### Post by Jim Danner on 2010-05-19
> **Jim Danner said:**
> At the moment my sync problems are already over, so I'm not getting these files anymore. If it happens again, I'll send you that debugging information.

Cheers, JimIt has started again: in the past hour, I have accumulated 274 .u1conflict files (all of them in the extensions in my Firefox profile), while the server still tells me "0.0 KB Used (0.0 %)". Since all the files on the server are still "uploading" and are 0 kB, there haven't even been any old versions returned from the server; only the renaming took place; there are no files by the original names. *EDIT:* The files that are being renamed to .u1conflict aren't present on the server at all (not even at 0 kB), so apparently the server was in the process of syncing and then suddenly got the impression it had a complete copy of the state of my folders; then it thought there was a conflict...

I have started debugging, and when the .u1conflict.1 files start appearing I will upload the logfiles.

---

### Post by joshuahoover on 2010-05-20
> **Jim Danner said:**
> It has started again: in the past hour, I have accumulated 274 .u1conflict files (all of them in the extensions in my Firefox profile), while the server still tells me "0.0 KB Used (0.0 %)". Since all the files on the server are still "uploading" and are 0 kB, there haven't even been any old versions returned from the server; only the renaming took place; there are no files by the original names. *EDIT:* The files that are being renamed to .u1conflict aren't present on the server at all (not even at 0 kB), so apparently the server was in the process of syncing and then suddenly got the impression it had a complete copy of the state of my folders; then it thought there was a conflict...

I have started debugging, and when the .u1conflict.1 files start appearing I will upload the logfiles.

OK, let me know the bug number here and I'll make sure it gets looked into ASAP.

Thanks,

Joshua

---

### Post by Zemblan on 2010-05-23
> **joshuahoover said:**
> The best way to do this right now is to do the following:


[LIST=1]
[*]In a terminal session (Applications->Accessories->Terminal)  run: u1sdtool --list-folders
[*]Copy the ID of the folder you want to stop synchronizing
[*]In a terminal session run (replacing ID-COPIED-FROM-STEP-2):  u1sdtool -q; u1sdtool --start; u1sdtool --delete-folder=ID-COPIED-FROM-STEP-2;  u1sdtool -c
[/LIST]
 Note, syncdaemon will do a local rescan of the folder you  unsubscribed (stopped syncing) which means it will take some time  processing this folder one last time, but will not attempt to do a sync.  After that, the folder will no longer be processed.

This is something we will be fixing, as I captured a bug for it here: [https://launchpad.net/bugs/576080](https://launchpad.net/bugs/576080) 

Thank you,

Joshua

I have followed the procedure for removing the folders from being synced, and it seems to have worked, but it appears that the data is still on the server, using up a big chunk of my allowance. How can I remove this data from the server?

Edit: apologies, it just took a couple of hours for the servers to update after running the commands, I guess things are still running a bit slow.

---

### Post by spaceballl on 2011-01-27
I'm having these conflict files created as well. This is terribly annoying. I just want to turn off this whole syncing thing. Perhaps it was a stupid decision by me, but i'm doing my work on this computer, and Ubuntu One was going to be used to backup my files. Now I don't care about the backup... I just want it to stop messing up my local files!!

---

### Post by spaceballl on 2011-01-27
When I try the following...
```
u1sdtool --list-folders

```
I get...
```
Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```
Oops, I am screwed.

---

### Post by duanedesign on 2011-02-02
Are the files that are creating conflicts being edited on more then one computer?

If these folders you are syncing are not the Ubuntu One folder but a UDF (user designated folder) you can follow these steps to stop syncing the folders even if files are still in the queue.

**u1sdtool --list-folders** - note the ID that is used by new UDF
**u1sdtool --unsubscribe-folder=$ID** (where $ID = id that was received by running list-folders)
**u1sdtool --quit** - this will quit the syncdaemon and drop the queue
**u1sdtool --start** - start syncdaemon again, but do not connect
(open a new terminal, since this will not release the terminal right away) - **u1sdtool --delete-folder=$ID**
**u1sdtool --connect**

You might have better luck copying your files to your Ubuntu One folder at the end of the day instead of syncing a folder where the working copy of the file is stored.

**NOTE:** the delete-folder command only deletes the files on the server. It leaves your local copy untouched.

thank you,
duaneedsign

---

