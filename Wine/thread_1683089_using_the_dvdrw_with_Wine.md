---
title: "using the dvd/rw with Wine"
date: 2011-02-07
forum: Wine
---

### Post by electroken on 2011-02-07
I have a windows specific copy program called Magic DVD copier which is able to copy a VR_video mode dvd video and change it over to a regular TS_video mode. None of the disks I am trying to copy are a copywrite issue but the result of recording off tv to a stand-alone dvd burner and not on a computer. The resulting disk cannot be duplicated by any other known windows disk copy program except for Magic Dvd Copier.
I can get Wine to install the Magic Dvd Copier program ok and it will run and copy my VR mode dvd only to a file folder. I am almost certain that the file is copied to a virtual directory or someplace that is not accessed until the copier needs it to write to the disk. It may even delete it as soon as you stop the program. I am not certain that a normal Linux burning program could be used at this point.
The problem I have is that the program running under Wine does not see the dvd/rw as a destination for the copy at all. It acts like windows running under wine does not have the correct driver for the dvd etc. Is there a way to make Wine use some sort of driver/codec for the dvd/rw in my machine?
I already know that Ubntu copiers also report the equal of a crc redundancy error when reading the VR mode disk and cannot make a copy of it.

---

