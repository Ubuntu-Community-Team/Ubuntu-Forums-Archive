---
title: "Document Manager Suggestions"
date: 2010-09-01
forum: The Cafe
---

### Post by hambone79 on 2010-09-01
I have been on a quest for the past couple of months to totally digitize all of my documents. I started out with a HP flatbed scanner, but recently upgraded to a ScanSnap S1300 connected to my Windows 7 machine (I absolutely love this scanner!). I have scanned about 300 documents, but I'm not quite sure what to do with all of them.

About a week ago I installed Alfresco on my home file server, but I'm not really that impressed with it...especially considering the painful 5 hours I spent trying to get it to play nice with my ebox installation. I would really like to find something with a better interface with the following features:

1. Access to the document repository via CIFS or WebDAV.
2. Revision tracking and the ability to rollback if necessary
3. Good security since I will be storing financial records
4. Cross platform - I have a mix of Linux, Windows XP, and Windows 7 on my home network.
5. Easy to backup and restore.

Any suggestions?

---

### Post by hambone79 on 2010-09-03
I have almost decided that my best option may be to create my own Subversion+Samba hybrid...Samba will take care of sharing the files with all my computers and Subversion will take care of the revision control. Anyone know how to setup this sort of system?

---

### Post by jhuckabee on 2010-09-03
I too have been in search of the perfect document management solution for Ubuntu.

I started using NeatReceipts several years ago when it first came out (on the Mac) and it continues to be the only reason I haven't ditched my last Mac machine (currently a Mac Mini).

What's holding me back is:
[LIST=1]
[*]Software:  To date, I haven't found anything in the open source world that does what neat receipts does.  The biggest benefit of NeatReceipts that I see at the moment is the OCR feature.  I know there are several OCR libraries in the wild (thanks Google) that could assist in an open source solution.  Simple scan is awesome, but its not meant to compete with a program like NeatReceipts.
[*]Hardware: My ScanSnap S1500M works on my linux machines.  Mostly.  I can initiate a scan from my machine, but not from the scanner.  Yes, I understand this is Fujitsu's fault for not providing a driver.  The xsane people have worked wonders on providing what support we do get.  And finally, I haven't been able to get double sided scanning working, which is critical IMO.
[/LIST]

I think this is prime real estate for someone looking to tackle a new development project.  Done correctly, I think it would be a hugely popular piece of software.  And, I would love to finally get rid of my last Mac machine.  :-)

Cheers,
Josh

---

