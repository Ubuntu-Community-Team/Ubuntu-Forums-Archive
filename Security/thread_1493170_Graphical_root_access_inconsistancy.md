---
title: "Graphical root access inconsistancy?"
date: 2010-05-25
forum: Security
---

### Post by David Stodolsky on 2010-05-25
Due to lack of space, I temporarily placed a Back in Time backup into the root partition, by running it as root. However, I couldn't get it back out on the Desktop, so I opened a terminal window and ran 'sudo nautilus', which I now know should be avoided. 

I couldn't bring up "Properties" of the root folder, but I was able to open it and see the backintime folders. I then clicked on root, which was in the toolbar row  "< root backintime" and was able to get full access to properties. I flipped folder access to "create and delete files" for Other, after disconnecting from the network, and moved the folder to the Desktop. 

So, is this correct or is it inconsistent that I could open root from the toolbar and not from the folder listing when opening 'filesystem'?

---

### Post by David Stodolsky on 2010-05-25
After moving the backup folder to the Desktop, copying it to an external disk, sending it to the Trash, and emptying the Trash, I found that there was about 83% used in my root partition. So, I started a Terminal and deleted the 'trashed' backup folder, which was in the original place. However, I noticed that after all this there was still the same amount of space taken, 53% (46.4GB), in root, just as before starting this procedure.

When I shutdown, the machine hung with all dots red. A reset restarted the machine, which seems normal. The home directory, which I backed up twice to root is shown as 24.1GB in System Monitor. (Back in Time uses hard links during incremental backups, so I am not sure whether there was much space to recover.) So, can anyone tell me what happened?

---

### Post by David Stodolsky on 2010-05-25
Immediately after the install, root was showing 84.6 GB free. Current free space is 40.4 GB. This is from File System Properties, which is somewhat buggy.

I have added a few things to the 10.4 since the install, but not anything that would take lots of space. Previous kernel would probably be the biggest new thing.

---

### Post by mikewhatever on 2010-05-25
What tool bar are you talking about? As for the space problem, backups may take a lot of space. Perhaps it's time to delete the redundant ones. Hint: shift+del.

---

### Post by David Stodolsky on 2010-05-26
"Just below the toolbar, you will see a rep-
resentation of where you are currently browsing." From the new 10.04 manual.

I was assuming that deleting the incremental backup would free some space.

---

### Post by David Stodolsky on 2010-05-26
Deleting the backup folder from the Desktop had no effect on space free. Changing that required rm-ing.

---

### Post by mikewhatever on 2010-05-26
If you don't know what is taking the space, investigate it with 'du'. Start with 'sudo do -sh /*', then go into other directories as needed.
Edit: As for root access inconsistency, I don't see any. You've launched nautilus with root privileges, and so had root access.

---

