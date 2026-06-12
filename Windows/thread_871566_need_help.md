---
title: "need help"
date: 2008-07-27
forum: Windows
---

### Post by mhesler on 2008-07-27
I am totally clueless.   I have a copy of ubuntu.  I was looking at it on my other computer.  I did not install it.  But now my other computer will not start because files are missing or corrupt.  <window root>\system32\hal.dll
My other computer wants me to re-install a copy of the file.

---

### Post by Sef on 2008-07-27
Moved to Windows Discussions.

---

### Post by perlluver on 2008-07-27
You are going to have to find that file either online, or off the CD and reinstall it.

---

### Post by cpetercarter on 2008-07-27
Havea look at [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm]("http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm")

---

### Post by werries on 2008-07-27
DO NOT REPLACE YOUR HAL.DLL WITH ONE FROM THE INTERNET.
this is a file very specific to the computer. Often times, as with mine, your hidden boot.ini file is now pointing to the wrong partition and so windows freaks out a bit.
If you don't know how to do this, a simple repair operation with the windows CD can fix this.

---

### Post by mhesler on 2008-07-27
I am really ignorant.  I obviously should not have even been looking at the ubuntu cd.  I feel horrible and fear I turned my computer into a doorstop.  I have gone thru all of the steps that I know to do based on the about.com directions.  :(

I have used a recovery discs but nothing changes. 

What do you mean by, "a simple repair operation with the windows CD can fix this."  I didn't get a windows CD when I purchased my computer.

---

### Post by cpetercarter on 2008-07-28
If, as you say, you did not install Ubuntu on your computer,but just ran the Live Disc, then Ubuntu will not have damaged your Windows installation. Did you make any changes in order to run Ubuntu e.g. did you change the boot order so that your computer looks first for an OS in the CD drive? If you did, then change things back to the way they were, and try re-booting.
You don't have a Windows installation disc? If you have a paid-for copy of Windows on your computer, it surely came with an installation disc. If your Windows installation is not paid-for, well that's one of the problems about trying to get Windows on the cheap.

---

### Post by werries on 2008-07-29
you should have been given a reinstallation cd. where do you buy from?

also don't feel bad, i had the same error in my earlier ubuntu days. i know better now than to overwrite my hal.dll and reinstall windows. =P my boot.ini was just pointing the wrong partition.

---

