---
title: "Create Archive/HP HDD 320gb Bug"
date: 2011-11-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ruinairas on 2011-11-10
I think it would be nice to have a default function that allows you to create a archive file by right clicking the desktop, or in a folder, and select create new .zip or .rar archive.


I also like to put out that I have an issue transferring files to my HP external harddrive. It's brand new and works perfectly on windows so I know the problem isn't because of the HDD itself. When I transfer files over to my HDD it says it is there, but when I disconnect it and connect it back up the files are not there. This gets very annoying. I always have to do it a couple times before it actually works.

---

### Post by cariboo on 2011-11-10
THe first question I have, is, are you running Precise? The second question is what error messages if any are you seeing in the log files?

To check the log files when transferring files. open a terminal and type the following command:

```
tail -f dmesg
```

If you do get any error messages, could you paste them in your next post. You don't have to include the whole dmesg file, just the last 15 entries, using the following command:

```
dmesg | tail -n15
```

---

### Post by seeker5528 on 2011-11-10
> **ruinairas said:**
> I think it would be nice to have a default function that allows you to create a archive file by right clicking the desktop, or in a folder, and select create new .zip or .rar archive.

Select some files/folders you want in an archive, right click, choose 'compress...'.

Don't know if this is by default or from something I installed extra, but when I right click an existing archive and choose 'Open with...', then 'Archive mounter' is listed as an option, which when selected will cause the archive to show in the 'Network' section of the side panel.

Later, Seeker

---

### Post by effenberg0x0 on 2011-11-11
> **seeker5528 said:**
> Select some files/folders you want in an archive, right click, choose 'compress...'.

Don't know if this is by default or from something I installed extra, but when I right click an existing archive and choose 'Open with...', then 'Archive mounter' is listed as an option, which when selected will cause the archive to show in the 'Network' section of the side panel.

Later, Seeker

Just checked that it is a default. I'm running on a default fresh install and have the "compress" context-menu option on Nautilus.

---

### Post by seeker5528 on 2011-11-11
> **effenberg0x0 said:**
> Just checked that it is a default. I'm running on a default fresh install and have the "compress" context-menu option on Nautilus.

The compress/extract type options I think are pretty common among the file managers. It was the 'archive mounter' option I was wondering about and if it is standard, I'm kinda wondering why it is not the default 'Open' option for archives.

If you compare to Windows built in support for .zip, Windows will let you browse an archive just as if it were another directory, but if you want to run something from within the archive, it works if it doesn't rely on anything else, fails if the executable relies on .dll or other support files within the archive.

Since archive mounter actually mounts the archive and it shows up as if it were a partition, running stuff from the archive that depends on other stuff from within the archive shouldn't matter.

Later, Seeker

---

### Post by ruinairas on 2012-02-29
Thanks for the help guys, I've gotten used to Ubuntu now. I got the hang of how most of it works. I love the support for Linux. It's amazing :)

---

