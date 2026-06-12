---
title: "eraser"
date: 2009-07-29
forum: Security
---

### Post by num on 2009-07-29
Hello,

Is there a program for Ubuntu like eraser? [http://eraser.heidi.ie/](http://eraser.heidi.ie/)

Where I can erase all unused space with the Guttman algorithm?

---

### Post by vmatherly on 2009-07-29
secure-delete is in the repos. It is a collection of tools to wipe files, free disk space, swap and memory. two of the programs it installs are sfill for wiping free space, and srm to securely delete files.

---

### Post by num on 2009-07-29
> **vmatherly said:**
> secure-delete is in the repos. It is a collection of tools to wipe files, free disk space, swap and memory. two of the programs it installs are sfill for wiping free space, and srm to securely delete files.
are they command line or is there a gui version to them?

---

### Post by vmatherly on 2009-07-29
All command line. But totally simple to use. A gui would be overkill. There is also DBAN [http://www.dban.org/](http://www.dban.org/). That has a GUI and does a great job though I cant remember if it has an option to only wipe free space.

---

### Post by juancarlospaco on 2009-07-29
For GUI use [Blechbit]("apt:/bleachbit"), it have a SHRED option, just **FILE--->SHRED**
:)

---

### Post by ajgreeny on 2009-07-29
And *shred* is already in your system.  See ```
man shred
``` for more info.  It's cli only, but dead simple to use.  Just make sure you only shred the files you want to shred as once done there is no going back.

---

