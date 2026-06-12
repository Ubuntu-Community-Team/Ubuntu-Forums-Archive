---
title: "syncing open files"
date: 2011-05-21
forum: Ubuntu One (CLOSED)
---

### Post by AntoineT on 2011-05-21
Hello,

I'm using natty on a fresh install. 

Is there a way to disable the syncing of open files ? When working on a document, I tend to save every time I make a small change to the file. U1 tries to sync the file every time, but sometimes I resave new changes before the previous syncing is complete, resulting in conflicts with the cloud version of the file, sometimes downloading back an already outdated version of the file I'm working on (in addition to the various .u1conflict files created in my folder). I think a sensible behaviour would be to (be able to) wait until the file is closed to start the syncing

Antoine

---

### Post by sanderd17 on 2011-05-21
This is a bug and needs to be solved by the Ubuntu one team. It's impossible to create conflicting copies if you only work from one computer. U1 should know that and just ignore the previous work and start uploading again. I know dropbox does it this way.

I do not know a standard solution for this, but maybe the sync could be delayed with the help of a script. You could work in one directory and have deja-dup (or another backup tool) set up to backup that directory to U1 every 5 minutes. I guess a download would be finished in 5 minutes, so that would solve the conflicts.

I didn't try if myself, it's only a possibility.

---

### Post by AntoineT on 2011-05-21
Thanks. I think U1 should have an option to sync only files that are not currently in use, and/or some kind of scheduler (sync every x minutes, or at some preset time, or manually) I guess this could be done through a script, but I'd rather check some boxes in the control panel...

Antoine

---

### Post by duanedesign on 2011-05-23
This is a known bug and one that a fix is being developed for.

---

