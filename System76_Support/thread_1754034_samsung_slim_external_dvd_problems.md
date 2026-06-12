---
title: "samsung slim external dvd problems"
date: 2011-05-09
forum: System76 Support
---

### Post by calypso77 on 2011-05-09
Hi, I bought the samsung slim external dvd writer with my system 76 netbook, but when I try to run the DVD-WRITER.EXE file that is shown in window for the dvd writer drive, ostensibly to install the software necessary for me to run the programs, burn cds, etc, I get this message.

Archive:  /media/DVD-WRITER/DVD-WRITER.exe
Zip file size: 2829312 bytes, number of entries: 29824

   [/media/DVD-WRITER/DVD-WRITER.exe]:
     Zipfile is disk 34294 of a multi-disk archive, and this is not the disk on
     which the central zipfile directory begins (disk 3569).

A similar thing happens if I try to run other software from the cd drive when its connected.

What am I missing here to make this work?

---

### Post by robtg on 2011-05-09
Unless I'm missing something, I think you're trying to run a Windows program (software bundled with the DVD writer).  

Rob

---

### Post by isantop on 2011-05-10
Rob's got it. That software is for getting the device working in Windows. For Ubuntu, you actually don't need to do anything at all. Just it in. You can use the program "Brasero" to create CDs and DVDs. It comes preinstalled in Ubuntu.

---

### Post by calypso77 on 2011-05-27
Well that explains part of it. Thanks. 

For whatever reason I do not have Brasero on my system.  When I went into the synaptic package manager it also didn't recognize me having it, so I installed it.  When I did, though, I still couldn't find any runnable program for it, just a whole bunch of package components that I don't know what to do with.  I have un and reinstalled it a few times, but to no avail, and now when I try to I get even less far because it says it requires installing unauthenticated software:

libeagle

Any idea what is going on?

Thanks for the help in all my confusion.

---

