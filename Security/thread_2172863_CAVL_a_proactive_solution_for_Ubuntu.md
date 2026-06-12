---
title: "CAVL: a proactive solution for Ubuntu"
date: 2013-09-06
forum: Security
---

### Post by ventrical on 2013-09-06
I just downloaded CAVL to another install and appears all download and virusdata updates bugs are fixed. (Mind you I only have it working on 12.04 LTS.

  The 'on access" scanner will not even allow you to download any of the eicar files without the Guard Alert popping  up. And there is absolutely no effect on performance. With the On Access guard .. it performs a little better than the Avast solution for linux.

[http://www.comodo.com/home/download/download.php?prod=antivirus-for-linux](http://www.comodo.com/home/download/download.php?prod=antivirus-for-linux)

regards..

---

### Post by Soul-Sing on 2013-09-07
Yeah. Based in the US. Please stick to open source stuff/software in these days folks. Or at least use the off. ubuntu software sources. The best tip to be safe imho.

---

### Post by Velnias on 2013-09-07
Yeah, but for advertising open source antivirus one get no money and, without Comodo, NSA gets no backdoor in Ubuntu ;-)

---

### Post by ventrical on 2013-09-07
CAVL is free software. License Agreement - yes .  However it is a good GUI for the noob  to work with as well as more advanced users.  I was impressed at how quickly it was able to detect the EICAR script even before it had a chance to download!!  Not a performance hog either. Also has a drag 'n drop feature  if you hook up other SATA/IDE drives through USB bridge and scan Windows drives for clients.

  I am going to try Thunderboid or Evolution and see how the e-mail scanner works.

regards..

---

### Post by Velnias on 2013-09-07
For antivirus addicts there is free and open source antivirus - ClamAV antivirus. And please explain - if Comodo antivirus lets viruses when running in Windows, how it detects when in Ubuntu?

As for mail - no antivirus helps ever if you read spam ( commercial antivirus effectiveness never got better than 50-90%, so you get infected sooner or later ).
Use spam filtering and brains.

---

### Post by ventrical on 2013-09-07
> **Velnias said:**
> For antivirus addicts there is free and open source antivirus - ClamAV antivirus. And please explain - if Comodo antivirus lets viruses when running in Windows, how it detects when in Ubuntu?

You scan a windows based hdd using CAVL while running CAVL in Ubuntu 12.04. This is to say that clients (of mine) who still use Windows , can have their hard drives scanned by using a SATA/IDE USB2.0 bridge converter. Hook hdd up to converter, plug in to Ubuntu 12.04 desktop with CAVL install and scan /media/. If you have legacy desktop with 12.04 with CAVL you can hotplug hdd into IDE/SATA cable. CAVL will detect it and you can drag the /media/ file over in preferences. *note* not all hardrives will work in this fashion. The prerequisite is that you have lots of hard drives about and more than one desktop. If you are using VM, tablet or droid then this is not for you. but it still may work in standard fashion. I'm just tester. I haven't tested all scenarios.

---

### Post by ventrical on 2013-09-07
> **Velnias said:**
> For antivirus addicts there is free and open source antivirus - ClamAV antivirus. 

Useless.. at least here. Avast is much better.

---

### Post by Velnias on 2013-09-08
No need running all the time antivirus for occasionally Windows scans. For that purposes are Antivirus CD's. I cant believe - you disassemble computer just for Comodo virus scan! So horror stories - virus killed PC - you need a new one - are true!

Still puzzles me - why not install antivirus in Windows and run from there? If Windows users get infected when running Comodo or Avast antivirus - how you clean it with antivirus running in Ubuntu? Im sure virus detection rate when running in Ubuntu are lower or, at best, the same.

---

### Post by ventrical on 2013-09-12
> **Velnias said:**
> No need running all the time antivirus for occasionally Windows scans. For that purposes are Antivirus CD's. I cant believe - you disassemble computer just for Comodo virus scan! So horror stories - virus killed PC - you need a new one - are true!


No, no , no ... I worked for a security company and beta tested their software.  Through time I would collect malware in quarantine and use that hdd to test other security software I was beta testing.  I called it 'malware ping-pong'. It is a must if you want to be good security IT. I have many hdds  to test.  I do not diassemble PCs for Comodo. Your wrong assumption.  When surplus hdd is static , I scan through linux kernel. Not Windows kernel. That makes no sense (IMO).

---

### Post by ventrical on 2013-09-12
> **Velnias said:**
> 
Still puzzles me - why not install antivirus in Windows and run from there? If Windows users get infected when running Comodo or Avast antivirus - how you clean it with antivirus running in Ubuntu? Im sure virus detection rate when running in Ubuntu are lower or, at best, the same.

If malware is polymorphic/stealth in Windows service then there are still traces. Scan through linux while windows is sleeping. While windows sleeping, malware also sleeping.

 How else can we test if we do not try scans?

My apologies. I should take this to  U+1 since I am mostly tester.

---

