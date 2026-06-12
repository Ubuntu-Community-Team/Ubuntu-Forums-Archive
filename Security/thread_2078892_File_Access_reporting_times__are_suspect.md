---
title: "File Access reporting times  are suspect"
date: 2012-10-31
forum: Security
---

### Post by Matt 6:27 on 2012-10-31
Not certain this belongs in Security Discussions, but I just noticed that ALL of my files... documents, images, encrypted stuff, etc., are reporting an access time somewhere between about 8:39AM and 8:49AM this morning (Oct. 31). For the record, I didn't open every one of my files this morning.  What's curious is I can open a .txt file, view it in gedit, close it, and when I go back and right-click for Properties, it shows the access time as about 8:40 this AM again.  Is this a Hack or hiccup?  Anyone else seeing this?  Thanks

---

### Post by movieman on 2012-11-01
What are the mount options on that disk? Using noatime or relatime can cause the access times to do things you don't expect, since they're either not updated or only updated in some circumstances.

---

### Post by Matt 6:27 on 2012-11-02
> **movieman said:**
> What are the mount options on that disk? Using noatime or relatime can cause the access times to do things you don't expect, since they're either not updated or only updated in some circumstances.

Not certain how to determine mount options and have not modified settings since my clean install of 12.04.  That said, I assume the mount options are whatever the defaults are.

---

### Post by Ms. Daisy on 2012-11-02
Did a backup run?

---

### Post by Matt 6:27 on 2012-11-03
> **Ms. Daisy said:**
> Did a backup run?

Did not run a backup, but have been playing around with photorec... which has uncovered a different issue for me, but that's another story for another thread.

I wonder if photorec affected the reporting times?  I can't put my finger on exactly what's going on in the background, as in some instances I've opened say a PDF, then closed it, and when I check access reporting times for that PDF, it still goes back to that Oct 31st date & time.

---

### Post by Ms. Daisy on 2012-11-03
I've never used photorec, but the [webpage ]("http://www.cgsecurity.org/wiki/PhotoRec")says it makes read-only access to the files. That would change the accessed time stamp on the folders it accessed.

Could be what you're seeing, but I can't swear to it.

---

### Post by Matt 6:27 on 2012-11-03
> **Ms. Daisy said:**
> I've never used photorec, but the [webpage ]("http://www.cgsecurity.org/wiki/PhotoRec")says it makes read-only access to the files. That would change the accessed time stamp on the folders it accessed.

Could be what you're seeing, but I can't swear to it.

Thanks, Daisy!

---

