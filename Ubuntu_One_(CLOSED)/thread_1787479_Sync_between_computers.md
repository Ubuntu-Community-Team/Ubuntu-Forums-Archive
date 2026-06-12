---
title: "Sync between computers"
date: 2011-06-21
forum: Ubuntu One (CLOSED)
---

### Post by McHenry on 2011-06-21
I have three computers connected to my Ubuntu One account

The three computers keep files in the Ubuntu One folder.

I have to rebuild one of the computers so I have copied everything from the user's documents folder to the Ubuntu One folder. Theory being once synced I can wipe the PC reinstall then resync then the files will be back.

The problem is the PC to be rebuilt shows that the sync is up to date and all the files display the "tick" the other computers also show the sync is up to date however the files from one are not showing in the Ubuntu One folder on the other, some are but some aren't.

Should all PCs not show the same contents in the Ubuntu One folder?

---

### Post by duanedesign on 2011-06-23
Yes all PCs should show the same contents in the Ubuntu One folder. Since files from both PC's are missing on the third PC lets look at the third PC where the files are not showing up.

Can you open a Terminal and run the following to see if their are any files in the queue still waiting to sync:

```
u1sdtool --waiting | wc -l

```
Could you check to see if their is anything in this file
~/.cache/ubuntuone/log/syncdaemon-exceptions.log
You may need to hit Ctrl + h, or View > Show Hidden Files to see the .cache directory. You can also use this command in a Terminal to check the contents of the file.

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log
```

thank you,
duanedesign

---

