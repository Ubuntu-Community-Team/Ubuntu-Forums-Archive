---
title: "windows f*cked me, then linux saved the day"
date: 2006-08-06
forum: The Cafe
---

### Post by siman on 2006-08-06
preface: I'm so very pissed at windows, so please excuse my language. I wanted to spend my sunday afternoon playing games, not learning about partition tables, sectors and cylinders.

I spent the last four hours fixing a problem, that windows caused: it messed up my partition table. So now I'm still angry, and my options are: tell the story or kick someone very hard.

In the past four hours I was close to re-formating the disk and even throwing it away. All I had were the error message "DeviceReady SeekComplete DataRequest Erorr" and "SectorIdNotFound" - it was a long way from finding the error messages to finally fixing the problem.

I still don't know exactly what happend, but I think the NTFS partition had a problem, windows tried to fix it and because of the ext3 partition on the same drive it totally messed things up (cfdisk informed me about "Partition begins after end-of-disk")

I'm just glad that I have my data back, and from now on windows gets it's own hard-drive and I'll try and to everything to hide the others HDs from it.

If you have problems with your partition table or generally think that your harddrive has a problem, try this: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

