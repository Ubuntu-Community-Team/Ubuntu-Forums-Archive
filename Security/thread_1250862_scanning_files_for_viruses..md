---
title: "scanning files for viruses."
date: 2009-08-27
forum: Security
---

### Post by wlraider70 on 2009-08-27
Is there a program that i can download to scan files for viruses.
I'm more concerned with "windows viruses" if thats a correct term.

i just want a program that can analyze a downloaded file so i know its clean.

does something like that exist or do i just want too much?

---

### Post by Agent ME on 2009-08-27
Run in a terminal "sudo apt-get install [clamav](apt:clamav)" (or click the link) to install ClamAV.

Then you can run it by typing "clamscan filename" in a terminal. Or you can scan a whole directory, by doing "clamscan -ri directory" (the r is for recursive, so it does all the files in a directory, and the i is so it only lists infected files). ClamAV does not do anything itself by default when it finds an infected file. It's your job to delete it or whatever you want to do to it.

It also does scan for Linux viruses and malware. These things do exist, but they are pretty rare for people not running servers (and people who don't randomly download and run every binary they find online).

---

### Post by lisati on 2009-08-27
There are plenty of answers, some of which might be "why?"

My favourite is AVG Free. The latest version, which can be downloaded [here]("http://http://free.avg.com/download?prd=afl") (don't forget to use the .deb version with Ubuntu), is command line only.

---

### Post by aljoriz on 2009-08-27
Many linux users would caution the use of antivirus, some of which are purely CLI based.  

This is my personal opinion:
Anti-Viruses for ubuntu is primary for the protection of our windows owner friends.  As the wine can be susceptible to viruses made for windows.

If you want a anti-virus take note that it MAY reduce boot time.

If you want a GUI based anti-virus AVAST for linux is a good choice.

---

### Post by cariboo on 2009-08-27
Even if you try to run a virus under wine, it is very unlikely that much would happen, as **W**ine **I**s **N**ot an **E**mulator. If any thing did happen it would be contained in you home directory.

---

