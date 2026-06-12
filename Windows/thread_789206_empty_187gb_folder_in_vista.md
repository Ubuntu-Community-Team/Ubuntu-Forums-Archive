---
title: "empty 187gb folder in vista"
date: 2008-05-10
forum: Windows
---

### Post by motoperpetuo on 2008-05-10
so, i'm at work on saturday, and since it's slow the boss brought in his home computer, which he wants me to fix. it's running the current OS of the masses, vista home premium, and his hard drive is always full. the computer has a host of other problems, all of which i think are related to the hard drive being almost completely full. i've narrowed it down to this folder, which is taking up 187gb of space:

c:\program data\aol\aoldiag\aol\servicehostusgm\win32\15.5.1.2

thing is, there seems to be nothing in the folder. i try to delete it from vista and it just hangs. i tried booting into puppy linux and deleting it that way and i get the error "ERROR: File Exists."

another strange thing is that there doesn't seem to be any AOL software on this computer except AIM (which won't uninstall).

his anti-virus is also out of date (i think it's one of those trial versions and it's expired). i believe i've seen references to a hackerish trick where you can make a folder or file report its size as much larger than what it is in reality, thus jacking up a computer in this way. i'm leaning towards that being what's going on, especially since his anti-virus is out of date.

anyone have any suggestions, aside from reinstalling the OS?

---

### Post by smoker on 2008-05-10
you don't mention what is the actual capacity of the hard drive, and the amount of data on the drive in total. if the drive is approaching full capacity, you can expect errors in the file system, ntfs needs around 15% of free space just for optimal operation, the less free space, the more likely you are to encounter errors. if the disk is full, remove some data and defrag a few times.

as to the 'ghost' file, you could try deleting from the command line in safe mode, or check if any services connected to aol are running, and close them first. (if the file is in use, or deemed to be, the os won't allow it's deletion)

the antivirus is little better than useless if it is out of date. if you cannot update it, then get rid of it and install a decent up to date scanner and run a few scans, there are free ones available like 'AVGfree' or 'Avast'

best of luck

---

### Post by ch_123 on 2008-05-11
Give another Live CD a try, my favourite being SystemRescueCD. If that doesnt get rid of, I think there's something serious fecked up with it, and you'll need to reformat.

---

### Post by Jiraya on 2008-05-13
You can use ubuntu live cd, works as well.

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by motoperpetuo on 2008-05-26
after hours and hours of trying different stuff, i just reinstalled the OS. nevertheless, thanks to everyone for the suggestions.

---

