---
title: "a linux rescue usb flash drive"
date: 2009-08-01
forum: The Cafe
---

### Post by Post Monkeh on 2009-08-01
hi.

i've been playing about these past few weeks with various "small" linux distros (dsl, puppy, that sort of thing) just for fun, installing them on a 128mb usb flash drive - puppy linux is awesome for the size of the little bugger.

but it got me to thinking. i'm by no means a computer expert, but i know way more than most people i know, and i'm usually the one people run to when they've stuffed up their computer.  surely there's a way for me to make an ubuntu (or any other linux distro) installation on a ;arger (1 - 2 gb) usb stick that provides me with the tools i could need to easily repair computers.

i'm not talking about things like major system files having been deleted. most of the problems i'm trying to sort are systems having been infected with spyware/viruses, and the main problem in trying to get rid of them is that they prevent avg (my anti virus program of choice for windows) from even starting, let alone getting rid.   
i thought it would be great to be able to make a bootable usb installation that means i can totally bypass whatever os (and associated virsues) normally loads, then scan from a virus free environment.

can the linux anti virus programs also pick up viruses in windows?  what is the best one? i'm not fussed on having to update the database, ubuntu easily picks up my mobile when its attached via usb, so i could easily download the latest virus database any time i needed to.

what about spyware programs, are there any for linux that can pick up spyware on a windows file system?

what about file/disk recovery programs for windows and linux?  if i'm going to have a rescue os, might as well make it able to rescue linux installations as well as windows?


what would everyone recommend as a must-have app for a rescue disk?  amd would ubuntu be your os of choice, or is there another distro out there that is better suited (or even designed) for the task?

---

### Post by Ubun2 Us3r on 2009-08-05
if you can access the Windows file-system, then yes, Linux virus-scanning programs would pick up the Windows viruses as most virus-scanners are designed for Windows programs.
This sounds like a good idea, you could definitely boot off a flash drive and restore systems. I might try this myself.

---

### Post by tgalati4 on 2009-08-06
Ultimate Boot CD is a similar concept, it's a collection of tools on a bootable CD.  There's probably a USB version of UBCD out there.

---

### Post by magmon on 2009-08-06
The solution is to install avast antivirus. Higher detection rate than avg, and it denys access to it's process so it cannot be taken down like avg can.

I agree that this is a cool concept though, perhaps this is the future of windows-saving tech xD

---

### Post by jmszr on 2009-08-06
Post Monkeh,

You might find this of interest: [http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12) . It can be put on a flash drive or a CD-RW, the download is 119 MB.

For more explanation: [http://en.wikipedia.org/wiki/Trinity_Rescue_Kit](http://en.wikipedia.org/wiki/Trinity_Rescue_Kit) .

---

### Post by The Real Dave on 2009-08-06
> **jmszr said:**
> Post Monkeh,

You might find this of interest: [http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12) . It can be put on a flash drive or a CD-RW, the download is 119 MB.

For more explanation: [http://en.wikipedia.org/wiki/Trinity_Rescue_Kit](http://en.wikipedia.org/wiki/Trinity_Rescue_Kit) .

+1

TRK has gotten me out of some right spots in Windows installs, and stays in my pocket all the time :D Just in case

Just read the documentation for it, I added it to my flashdrive, as I can never remember commands :D

EDIT: Here's the [_**link**_]("http://trinityhome.org/Home/Print_Collate.php?collate_pages=37,38,54,55,56,57,39,40,42,43,45,46,50,47,53,49,51,52,48,58,59,60,61,62,63,64,66,67,68,69,70,71,72,73,74,75,76,33,124,128") to the online documentation, all in one long page :D

---

### Post by init1 on 2009-08-06
I highly recommend using a distro with Testdisk on your flash drive. It has saved my data twice, even after my partition table was damaged.

---

### Post by Post Monkeh on 2009-08-07
thanks for the info.

i presume trk is command line only?


seems that it has nearly everything you could want, and the help file also gave me some good advice about the use of commands. i always wondered what the "dmesg | grep" thing was all about sometimes when i was reading tutorials, i now know how to pipe one command through another. every day's a school day.

---

