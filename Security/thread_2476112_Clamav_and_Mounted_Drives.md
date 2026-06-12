---
title: "Clamav and Mounted Drives"
date: 2022-06-16
forum: Security
---

### Post by knoppys on 2022-06-16
Hi

I have clamav installed on ubuntu and a mounted dropbox drive using the dbxfs package. 

When I try to run clamav on files in the mounted drive I get a permission denied error. Any ideas?

---

### Post by TheFu on 2022-06-16
Remote root access to network devices is generally not possible, if that is what's happening.

ClamAV cannot scan FTP/rsync/sftp storage either, so not scanning Dropbox isn't really surprising.
Not all network file systems implement a sufficient number of the expected file system API that could be required by some programs.

I suspect Dropbox uses a form of WebDAV - -  eeeew, I feel dirty.

Some people created something called DBShield as a college project at NCSU.  They used ClamAV, but downloaded all the files to a temporary directory before scanning. I wasn't able to find their code and a few other people used the same name for other projects where the same name actually makes more sense to me.

---

