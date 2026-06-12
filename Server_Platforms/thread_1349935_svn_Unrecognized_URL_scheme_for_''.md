---
title: "svn: Unrecognized URL scheme for ''"
date: 2009-12-08
forum: Server Platforms
---

### Post by Goobie81 on 2009-12-08
For some reason I cannot commit this repo - I even rsync'd it to another machine and i got the same error, so i'm fairly confident the issue lies in the repo data. Whenever i google this error it's mostly issues with not compiling SSL support - but every result there is always a URL in the error (where as mine is blank)

This machine has previously done hundreds of commits until now and nothing has been changed (libraries/upgrades etc)

Details :```


root@server:/var/deploy# svn ci -m "Snom config updates, profile updates, new firmware"
svn: Commit failed (details follow):
svn: Unrecognized URL scheme for ''
root@server:/var/deploy# svn info .      
Path: .
URL: https://<snip>/deploy
Repository Root: https://<snip>/deploy
Repository UUID: e2e5a009-74a3-4e26-910d-381e982f2194
Revision: 126
Node Kind: directory
Schedule: normal
Last Changed Author: <snip>
Last Changed Rev: 126
Last Changed Date: 2009-07-26 19:48:06 +1000 (Sun, 26 Jul 2009)

root@server:/var/deploy# 
root@server:/var/deploy# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

root@server:/var/deploy# uname -a
Linux server 2.6.24-19-server #1 SMP Wed Aug 20 23:54:28 UTC 2008 i686 GNU/Linux

root@server:/var/deploy# svn --version
svn, version 1.4.6 (r28521)
   compiled Aug  7 2009, 00:14:48

Copyright (C) 2000-2007 CollabNet.
Subversion is open source software, see http://subversion.tigris.org/
This product includes software developed by CollabNet (http://www.Collab.Net/).

The following repository access (RA) modules are available:

* ra_dav : Module for accessing a repository via WebDAV (DeltaV) protocol.
  - handles 'http' scheme
  - handles 'https' scheme
* ra_svn : Module for accessing a repository using the svn network protocol.
  - handles 'svn' scheme
* ra_local : Module for accessing a repository on local disk.
  - handles 'file' scheme
```

**EDIT: Committing one file at a time works?**

---

