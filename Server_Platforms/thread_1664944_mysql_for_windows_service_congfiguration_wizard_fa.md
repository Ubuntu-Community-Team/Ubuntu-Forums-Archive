---
title: "mysql for windows service congfiguration wizard failure fix"
date: 2011-01-11
forum: Server Platforms
---

### Post by sdowney717 on 2011-01-11
not sure where to put this but I found a solution for when it wont start
and for general information

delete all the associated mysql files
dont set the enable root remote login option which appears under the password fields.

then the configuration wizard will complete the configuration.
this had me dumbfounded until I found a post that mentioned how to get this going when it fails. personally think it must be a bug.

---

