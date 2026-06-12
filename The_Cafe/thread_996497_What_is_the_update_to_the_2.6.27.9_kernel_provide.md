---
title: "What is the update to the 2.6.27.9 kernel provide?"
date: 2008-11-28
forum: The Cafe
---

### Post by kevdog on 2008-11-28
Just wondering about the new features of the new 2.6.27.9 kernel that was available on the Intrepid repositories.  I downloaded and installed the kernel -- I want to know what was fixed from the previous kernel?

---

### Post by Eclipse. on 2008-11-28
Just bug fixes.

Head over to launchpad to see the changelog.

---

### Post by jpeddicord on 2008-11-28
It was sent out as a result of a USN, which caused an ABI break, meaning the version number had to be bumped.

[http://www.ubuntu.com/usn/usn-679-1](http://www.ubuntu.com/usn/usn-679-1)

In other words, just a security update. Doesn't mean you should put it off though.

---

### Post by Grant A. on 2008-11-28
> **jacobmp92 said:**
> In other words, just a security update. Doesn't mean you should put it off though.

The words "Security Update" usually prompt me to update post haste.

---

### Post by ajcham on 2008-11-30
I've mentioned this on another thread already, but it may be worth mentioning here.  Since installing the kernel update (2.6.27.9.13) I've had serious problems in which my system completely freezes during large file operations, forcing me to hard reset. I'm not sure if the kernel update is the cause or not, but the timing seems to suggest so.

Is anyone else having problems?

EDIT:
Turned out to be a hardware problem unrelated to the kernel update - the timing was just a coincidence.

---

### Post by Pekkalainen on 2008-11-30
Ehm... I might be hallucinating. But since the new kernel update all the buttons on my mouse have started to work with no effort at all from my side. I didnt bother to configure them when I did a clean install of Ibex. What is going on? :o

---

### Post by Magneto on 2008-11-30
Fixed my buggy as hell ACPI issues except for the totally broken thermal module.

---

