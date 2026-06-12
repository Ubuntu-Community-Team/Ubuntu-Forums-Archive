---
title: "[SOLVED] Samba Shares - Folder In Share Cannot Have Same Name As Share"
date: 2008-12-06
forum: Server Platforms
---

### Post by chris.zeman on 2008-12-06
One of my shares is named "Audio". I have been trying to organize my files and discovered that any directories I try to move onto the drive cannot have the name "Audio". It doesn't matter if the folder is nested deep within other directories. The error XP gives me is:
```
Cannot create or replace audio: Cannot find the specified file.
Make sure you specify the correct patch and file name.
```

Is this a problem with Windows or Samba?

Thank you,
Chris

---

### Post by kamaji792 on 2008-12-07
An interesting feature.

Not any help but can you create a directory called Audio on the share?

I have a Samba server running with a share called "App" and a directory called "App" just off the root of the share.  That works fine.

---

### Post by chris.zeman on 2008-12-07
Now this is funny. I tried what you suggested and created a directory called "Audio" in the root of my Audio share. It worked! I decided to then try creating directories called "Audio" within other folders and that worked, too! I don't understand it, but it's working just fine now. :confused:

Chris

---

