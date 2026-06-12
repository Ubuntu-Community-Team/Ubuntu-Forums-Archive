---
title: "Nautilus and Termina using deleted files?"
date: 2010-09-07
forum: Security
---

### Post by KonfuseKitty on 2010-09-07
I haven't been able to find anything on the 'net about this: when running "rkhunter --enable all", I get this warning:


```
[09:30:46] Performing malware checks
[09:30:46] Info: Starting test name 'malware'
[09:30:46] Info: Starting test name 'deleted_files'
[09:30:47]   Checking running processes for deleted files    [ Warning ]
[09:30:47] Warning: The following processes are using deleted files:
[09:30:47]          Process: /usr/bin/nautilus    PID: 1775    File: /home/kkitty/.local/share/gvfs-metadata/home
[09:30:47]          Process: /usr/bin/gnome-terminal    PID: 2973    File: /tmp/vteHFH1IV
```


However, when I navigate to the gvfs-metadata folder, the home file is there, 124.8Kb in size, of unknown type and gedit can't open it. The file in /tmp/, on the other hand, doesn't exist.


Why is Terminal using a deleted file, and why is the home file being reported as deleted when it isn't?

---

### Post by kidders on 2010-09-08
Hi there,

> **KonfuseKitty said:**
> Why is Terminal using a deleted file, and why is the home file being reported as deleted when it isn't?More than likely, gnome-terminal just hadn't gotten around to releasing its unused open file handles ... Without looking at the source code, it's hard to be sure why though.

If you looked at their inodes, you'd probably have found that the file nautilus had open wasn't the same one you'd see if you ran **ls /home/kkitty/.local/share/gvfs-metadata/home**. The fact that they had the same name doesn't necessarily make them the same file. Since it started, nautilus had probably deleted and replaced the file, but was still retaining an open handle to the deleted version for some reason. Again, that's just a guess, but it *seems* reasonable.

I hope that helps.

---

### Post by KonfuseKitty on 2010-09-08
Yes, it does help, thank you. I have since been able to find other reports of similar "deleted file" findings by Rkhunter, so it probably isn't much to worry about.

---

### Post by kidders on 2010-09-08
No problem.

> **KonfuseKitty said:**
> I have since been able to find other reports of similar "deleted file" findings by Rkhunter, so it probably isn't much to worry about.That's true ... *nix style OSs don't have much of a problem letting processes continue to access files after they've been deleted, so it's fairly commonplace. Strictly speaking though, you should still read the list of processes rkhunter says are doing it, and make sure you're happy with it. There are quite a few malicious tricks involving deleted files.

---

