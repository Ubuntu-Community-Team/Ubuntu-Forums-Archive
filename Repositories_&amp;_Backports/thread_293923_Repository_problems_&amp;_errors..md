---
title: "Repository problems &amp; errors."
date: 2006-11-05
forum: Repositories &amp; Backports
---

### Post by BanjoBoy on 2006-11-05
I am having a lot of problems lately updating my Ubuntu Edgy, it seems that the download fails when running "sudo apt-get update", because only a part of the file are downloaded (I think the connection are closed by the server) and the uncompression fails, I get errors like these:
```
Get:13 http://security.ubuntu.com edgy-security/multiverse Packages [2223B]                                                                                                
93% [13 Packages bzip2 0] [Connecting to archive.ubuntu.com (195.248.90.38)] [Connecting to security.ubuntu.com (82.211.81.138)] [Waiting for headers]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://security.ubuntu.com edgy-security/multiverse Packages                                                                                      
  Sub-process bzip2 returned an error code (2)

```

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Now I am having the problems with security.ubuntu.com, but a few days ago I was having it also with archive.ubuntu.com.

I skipped SUSE Linux because of the version 10.1 problem with updating and started to use Ubuntu and have now used Ubuntu Dapper Drake and installed fresh version of Edgy (not an update) when it was released. While using Dapper I did not have any problem and it has now been here for a few weeks, I think after release of Edgy?!

Are Ubuntu doing something to solve this problem? Is it bandwidth or server problems or what do I do to get it working so I get stable repository updates.

---

