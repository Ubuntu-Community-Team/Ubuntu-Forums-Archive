---
title: "Synchronization upload keeps getting interrupted"
date: 2011-09-11
forum: Ubuntu One (CLOSED)
---

### Post by Arancaytar on 2011-09-11
My desktop computer (on 10.10) is having trouble with syncing files.

I checked ~/.cache/ubuntuone/log for some indications.

Initial troubles appeared to be caused by invalid character encoding in some filenames copied over from an old Windows partition. However, now these appear to be pretty much fixed (no more log entries to syncdaemon-invalid-names.log for the past 15 minutes).

The main log file is getting flooded (really flooded, generating about 1MB / 4000 lines per minute) by messages like 

[time] - ubuntuone.SyncDaemon.local_rescan - INFO - Resuming upload because it was interrupted: '[path]'

This happens to the same files about every five seconds.


Edit: There is negligible network traffic, so the program likely does not connect at all. The internet connection clearly works, however.

---

