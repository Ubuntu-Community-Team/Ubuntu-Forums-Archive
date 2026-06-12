---
title: "file roller crash (extract to)"
date: 2013-05-17
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-05-17
right click tar.gz (in file browser) -> extract to -> some place/any place
files are extracted properly
crash report detected (it is file roller)
open report
[xfce4-indicator-plugin crashes]("http://ubuntuforums.org/showthread.php?t=2146095") 
re-launch
tell apport yes i want to report it (file roller)
nothing ever happens

---

### Post by mc4man on 2013-05-17
> **pqwoerituytrueiwoq said:**
> 
tell apport yes i want to report it (file roller)
nothing ever happens

Likely just being sent to a crash db as LP reports were turned off just prior to raring release & not yet re-enabled in S

---

### Post by pqwoerituytrueiwoq on 2013-05-17
is the crash db local or on a Canonical server?

---

### Post by QIII on 2013-05-17
I'm not even getting that far.  Starts up for a moment, just long enough to see the GUI, and then disappears.

Had to install XZipper or whatever it's called.

---

### Post by mc4man on 2013-05-18
> **pqwoerituytrueiwoq said:**
> is the crash db local or on a Canonical server?
Not local, otherwise I don't particularly care to explore ..

changelog  - 
> apport (2.9.2-0ubuntu6) raring; urgency=low

  * etc/apport/crashdb.conf: Disable Launchpad crash/kernel reports for the
    raring release. Only report to [http://errors.ubuntu.com](http://errors.ubuntu.com) from now on.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Thu, 11 Apr 2013 12:42:27 +0200

Take it as you may, the diff - 
```
--- apport-2.9.2/etc/apport/crashdb.conf
+++ apport-2.9.2/etc/apport/crashdb.conf
@@ -20,6 +20,7 @@
         'bug_pattern_url': 'http://people.canonical.com/~ubuntu-archive/bugpatterns/bugpatterns.xml',
         'dupdb_url': 'http://people.canonical.com/~ubuntu-archive/apport-duplicates',
         'distro': 'ubuntu',
+        'problem_types': ['Bug', 'Package'],
         'escalation_tag': 'bugpattern-needed',
         'escalated_tag': 'bugpattern-written',
     },


```

---

### Post by cariboo on 2013-05-18
Does this happen on a specific flavour? As I'm running a pretty vanilla Saucy Ubuntu install here, and file-roller works as it should here. I just purchased a service manual for my car, and it came as a zip file, with rared pdfs inside of it, everything decompressed without any drama here.

---

### Post by pqwoerituytrueiwoq on 2013-05-18
it is a clean install of saucy+updates only a couple days old
using xubuntu, try a tar.gz file
edit: looks like it was fixed in the 3.8 release, that updated the other day

---

