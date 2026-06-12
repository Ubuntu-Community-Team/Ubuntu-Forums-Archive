---
title: "Accessing HD from Live CD"
date: 2007-05-08
forum: Windows
---

### Post by PulpSpy on 2007-05-08
Pardon the complete noob question, but I have a Live CD of Ubuntu 5.04 which I can boot into. I want to simply delete a file that is on my harddrive (a mallicious dll that I can't delete from windows because its attached itself to the logon process).

How do I access the hard-drive?

Sorry if this has been asked a million times--I tried to find an older post that addressed it.

---

### Post by LaRoza on 2007-05-08
If you can read the drive, you just mount it as read write and delete it.

If the drive is NTFS, you'll need something else because Ubuntu can't read NTFS with an app.

I think Knoppix will do what you want.

---

### Post by aberry5555 on 2007-05-08
You can also delete this file in the windows recovery console. If you still have it, put in the original Windows CD and let it load up the installer, then select repair, then repair with windows recovery console. This will give you some basic MS-DOS style functionality and, hopefully, unless there are some weird permissions or it's entered in the registry to re-create itself from a back-up file hidden somewhere, you should be able to cd to the folder and delete the file.

---

### Post by LaRoza on 2007-05-08
You can, in recovery, change attributes and delete files, but be careful, if you do not know what you are doing, you can do some damage,

```

DIR *.dll /S

```

will find all dll files, removing /S will find a specific file as in  DIR virus.dll.

```

DIR /A:h /S 

```

will find all hidden files

If you want to change attributes, you use 

```

ATTRIB [+|- H]  [+|-R] [FileName]

```

```

DEL fileName

```

Deletes file.

---

### Post by PulpSpy on 2007-05-08
Thanks for the advice so far. I don't have a recovery disk, unfortunately, which is why I'm resorting to using Ubuntu. I tried using safe mode with console and the dll was still linked. I also tried to delete on reboot using HijackThis and another utility called the Avenger.

Anyways, the drive is NTSF so I guess I'm out of luck with Ubuntu live CD?

I'll try Knoppix.

---

