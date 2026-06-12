---
title: "how to store backup files on ubuntu one?"
date: 2009-10-09
forum: Ubuntu One (CLOSED)
---

### Post by RavanH on 2009-10-09
Hi,

I am trying to use Déjà Dup to take a weekly **Backup** from my e-mail folder and store it on my Ubuntu One folder. 

Déjà Dup creates multiple 5Mb sized encrypted files in the format of:
```
duplicity-full.2009-10-09T15:37:18+02:00.vol1.difftar.gpg
```

However, in U1 it turns out the uploaded files are called
```
duplicity-full.2009-10-09T13:11:27+02:00.vol1.difftar.gpg.u1conflict
``` (notice the u1conflict postfix)

The file sizes are correct and no errors were reported but with this new extension, these files are useless for a **Restore**...

What went wrong here?

---

### Post by joshuahoover on 2009-10-15
> **RavanH said:**
> Hi,

I am trying to use Déjà Dup to take a weekly **Backup** from my e-mail folder and store it on my Ubuntu One folder. 

Déjà Dup creates multiple 5Mb sized encrypted files in the format of:
```
duplicity-full.2009-10-09T15:37:18+02:00.vol1.difftar.gpg
```However, in U1 it turns out the uploaded files are called
```
duplicity-full.2009-10-09T13:11:27+02:00.vol1.difftar.gpg.u1conflict
``` (notice the u1conflict postfix)

The file sizes are correct and no errors were reported but with this new extension, these files are useless for a **Restore**...

What went wrong here?

It's hard to say for sure what went wrong without more information. We'd like to help figure it out! If you can tright-click on the Ubuntu One Client and select "Report a Problem" this will start filing a bug report with some log information. We'll also likely need you to attach your ~/.cache/ubuntuone/log/syncdaemon.log file to the bug. Note that attaching syncdaemon.log will show filenames you are attempting to sync with Ubuntu One. If you do not want this to be public, please mark the bug as private and this bug report will only be available to you and the Ubuntu One team.

Thank you,

Joshua

---

### Post by RavanH on 2009-10-23
Hi Joshua,

Thanks for helping figure this out. I hesitate to file it as a bug immediately because I am not sure how to describe or what went wrong and where exactly... So if you can tell more from the syncdeamon.log file, here is a snippet regarding the first of the backup volume files. All other files have similar log entries.

Should I go ahead and make a report about it?

> ...
2009-10-23 18:21:09,309 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=18 miss=5) ----
2009-10-23 18:22:20,618 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ffde4a65-2933-48e7-a426-f05c48a03321 [root:ffde4a65-2933-48e7-a426-f05c48a03321] ''Ubuntu One/duplicity-full.2009-10-23T18:22:11+02:00.vol1.difftar.gpg'' | Called new_local_file (In: F:NA:NA)
2009-10-23 18:22:20,656 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ffde4a65-2933-48e7-a426-f05c48a03321 [root:ffde4a65-2933-48e7-a426-f05c48a03321] ''Ubuntu One/duplicity-full.2009-10-23T18:22:11+02:00.vol1.difftar.gpg'' | Called calculate_hash (In: T:NONE:F)
2009-10-23 18:22:20,805 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F ffde4a65-2933-48e7-a426-f05c48a03321 [root:ffde4a65-2933-48e7-a426-f05c48a03321] ''Ubuntu One/duplicity-full.2009-10-23T18:22:11+02:00.vol1.difftar.gpg'' | Called put_file (In: T:NONE:F)
2009-10-23 18:22:21,047 - ubuntuone.SyncDaemon.ActionQueue - WARNING - MakeFile                     share:''                                       node:'ffde4a65-2933-48e7-a426-f05c48a03321'   MakeFile(marker="'ffde4a65-2933-48e7-a426-f05c48a03321'", parent_id="'e9985643-5875-4961-ac5a-a2139eb70c62'", share_id="''", name="u'duplicity-full.2009-10-23T18:22:11+02:00.vol1.difftar.gpg'") failure INVALID_FILENAME
2009-10-23 18:22:21,052 - ubuntuone.SyncDaemon.sync - INFO - -:-:- ffde4a65-2933-48e7-a426-f05c48a03321 [-:-] ''-'' | Called file_not_created_remove (In: T:LOCAL:F)
2009-10-23 18:22:21,056 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Upload                       share:''                                       node:'ffde4a65-2933-48e7-a426-f05c48a03321'   Upload(share_id="''", hash="'sha1:f0bef99ebda24085deb001afaa51fc56b47a5595'", fileobj_factory='<bound method FSKey.open_file of <ubuntuone.syncdaemon.sync.FSKey object at 0x2b78230>>', node_id="'ffde4a65-2933-48e7-a426-f05c48a03321'", crc32='2596473747L', previous_hash="''", size='5212248') unable to build fileobj (user deleted the file, maybe?) so cancelling the upload.
2009-10-23 18:22:21,062 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Upload                       share:''                                       node:'ffde4a65-2933-48e7-a426-f05c48a03321'   Upload(share_id="''", hash="'sha1:f0bef99ebda24085deb001afaa51fc56b47a5595'", fileobj_factory='<bound method FSKey.open_file of <ubuntuone.syncdaemon.sync.FSKey object at 0x2b78230>>', node_id="'ffde4a65-2933-48e7-a426-f05c48a03321'", crc32='2596473747L', previous_hash="''", size='5212248') failure CANCELLED
2009-10-23 18:22:21,063 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - [:ffde4a65-2933-48e7-a426-f05c48a03321] ''-'' | Called nothing (In: F:NA:NA)
...

---

### Post by RavanH on 2009-10-25
ahhhh... think i located the problem. if a filename has a colon (:) in it, the problem (.u1conflict) will occur. 

but when i upload a file *without* a colon in the name, and then rename it to something *with* a colon, then there will be no problem... funny ;)

anyway, now i know what to report as bug!

---

### Post by mikix on 2009-10-27
Deja Dup in Karmic no longer uses colons.

---

