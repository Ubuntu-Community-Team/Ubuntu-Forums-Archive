---
title: "cnf content on mirror server"
date: 2021-06-16
forum: Server Platforms
---

### Post by Nigel_Pain on 2021-06-16
I manage a mirror server, using debmirror to maintain LTS versions. I recently added 20.04 LTS content to it but there appears to be new content with this version which is not getting mirrored, namely the cnf folders and contents. This is causing any updates on 20.04 machines to fail with the following error:

```
Err http://svrname/ubuntu focal-updates/main amd64 c-n-f Metadata 404  Not Found [IP: x.x.x.x 80]
```
and
```
W: Failed to fetch http://svrname/ubuntu/dists/focal-updates/main/cnf/Commands-amd64: 404  Not Found [IP: x.x.x.x 80]
```



I followed a suggestion I found online, using wget to download that content but this seems to get removed the next time that debmirror runs. Is there a way to get debmirror to include this content?

The mirror server is Ubuntu 16.04 LTS, which I know is out of support (just haven't had time to upgrade it yet). Could that be the cause?

Thanks.

---

### Post by MAFoElffen on 2021-06-18
Your problem is that your debmirror server is still running Ubuntu 16.04 LTS.

Please reference [Launchpad Bug #1821251:"please add cnf support to debmirror"]("https://bugs.launchpad.net/ubuntu/+source/debmirror/+bug/1821251")
> * Starting with Ubuntu Focal (20.04), the APT client expects APT sources to provide command-not-found (cnf) metadata files.
The "correct" patch was applied in Ubuntu 20.04.1 LTS  in package debmirror (1:2.27ubuntu2.20.04.1) in Focus-Updates Universe

So you would have to upgrade to do that. (I don't see any backports)

---

