---
title: "Linux tool speeds up computer forensics for cops"
date: 2008-03-21
forum: The Cafe
---

### Post by The Fire Fly on 2008-03-21
Australian university students have developed a Linux-based data forensics tool to help police churn through a growing backlog of computer-related criminal investigations. 

The tool was developed by students from Edith Cowan University's School of Computing and Information Sciences and will help the Western Australian Police Computer Crime Squad process their forensic investigations. 

Called Simple (for Simple Image Preview Live Environment), the software allows investigators to view and acquire forensic data at the scene of the crime without compromising the integrity of data as it is collected. 

"It's a Linux Live CD that we have built from the ground up. We customized the kernel and the underlying operating system so that when it runs it's incapable of writing to the hard disk or any other storage," Peter Hannay, the software developer behind the forensic acquisition tool told ZDNet Australia. 

The operating system has had some features removed so that investigators can view data without affecting the host machine. 

"We stripped out a large amount of functionality because we want to maintain the integrity of data collected, so we removed all network support and the ability to write to disk. Also, if for some reason a disk is writeable, the system will halt automatically," he added.

"Our software will launch on top of the operating system and will interrogate the hard disk, locate all the images on system and then present those to the operator." 

The Simple tool searches the system for specific file types like MPEG or JPEG files, saving time on the often lengthy search process. 

Hoping to achieve even greater automation during the collection of evidence, Simple will soon be equipped with skin-tone analysis capabilities to help detect relevant files. 

The idea for the tool first came when the Western Australian Police approached the university in 2006, since its investigators could not handle the amount of computer forensic data requests, which relate mostly to child pornography and bestiality. 

Normally police need to take the PCs back to the station to begin acquiring forensic data, but with this tool, according to Hannay, police will be able to collect the data on the spot.:)

---

### Post by regomodo on 2008-03-21
why are you copying from websites? It is usually better to place what you copy in quotes 

---

### Post by RAV TUX on 2008-03-21
> **The Fire Fly said:**
> Australian university students have developed a Linux-based data forensics tool to help police churn through a growing backlog of computer-related criminal investigations. 

The tool was developed by students from Edith Cowan University's School of Computing and Information Sciences and will help the Western Australian Police Computer Crime Squad process their forensic investigations. 

Called Simple (for Simple Image Preview Live Environment), the software allows investigators to view and acquire forensic data at the scene of the crime without compromising the integrity of data as it is collected. 

"It's a Linux Live CD that we have built from the ground up. We customized the kernel and the underlying operating system so that when it runs it's incapable of writing to the hard disk or any other storage," Peter Hannay, the software developer behind the forensic acquisition tool told ZDNet Australia. 

The operating system has had some features removed so that investigators can view data without affecting the host machine. 

"We stripped out a large amount of functionality because we want to maintain the integrity of data collected, so we removed all network support and the ability to write to disk. Also, if for some reason a disk is writeable, the system will halt automatically," he added.

"Our software will launch on top of the operating system and will interrogate the hard disk, locate all the images on system and then present those to the operator." 

The Simple tool searches the system for specific file types like MPEG or JPEG files, saving time on the often lengthy search process. 

Hoping to achieve even greater automation during the collection of evidence, Simple will soon be equipped with skin-tone analysis capabilities to help detect relevant files. 

The idea for the tool first came when the Western Australian Police approached the university in 2006, since its investigators could not handle the amount of computer forensic data requests, which relate mostly to child pornography and bestiality. 

Normally police need to take the PCs back to the station to begin acquiring forensic data, but with this tool, according to Hannay, police will be able to collect the data on the spot.:)

This has already been developed and around for a while, the most successful and widely used is [Helix]("http://www.e-fense.com/helix/").

[CENTER][URL="http://www.e-fense.com/helix/index.php"][IMG]http://ubuntuforums.org/attachment.php?attachmentid=63346&d=1206135016[/IMG]
[/URL][/CENTER]
 
> Helix is a customized distribution of the Knoppix Live Linux CD. Helix is more than just a bootable live CD. You can still boot into a customized Linux environment that includes customized linux kernels, excellent hardware detection and many applications dedicated to Incident Response and Forensics. 

Helix has been modified very carefully to NOT touch the host computer in any way and it is forensically sound. Helix wil not auto mount swap space, or auto mount any attached devices. Helix also has a special Windows autorun side for Incident Response and Forensics. 

Helix focuses on Incident Response & Forensics tools. It is meant to be used by individuals who have a sound understanding of Incident Response and Forensic techniques. That said Helix is used by the following organizations for Incident Response/Forensics Training:

e-fense: [Helix Incident Response & Computer Forensics]("http://www.e-fense.com/helix/training.php") 
NW3C: [Linux Forensics]("http://www.nw3c.org/training_courses.html") 
SANS Track 508: [System Forensics, Investigation and Response.]("http://www.giac.org/certifications/security/gcfa.php") 
InfoSec Institute: [Computer Forensics Training]("http://www.infosecinstitute.com/courses/computer_forensics_training.html") 
SEARCH: [Basic Investigators Training]("http://www.search.org/programs/hightech/courses.asp") 
[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

Here is further documentation on Helix:

> **[COLOR=yellow]FORENSICS:[/COLOR]**

[Forensic Examination of Digital Evidence]("http://www.e-fense.com/helix/Docs/Forensic%20Examination%20of%20Digital%20Evidence.pdf"). (U.S. DOJ - 2004)
[Test Results for Disk Imaging Tools: dd GNU fileutils 4.0.36,Provided with Red Hat Linux 7.1]("http://www.e-fense.com/helix/Docs/dd.pdf"). (U.S. DOJ - 2002)
[Digital forensics of physical memory]("http://www.e-fense.com/helix/Docs/forensics-physical-memory.pdf"). (Mariusz Burdach - 2005)
[Preservation of Fragile Digital Evidence by First Responders]("http://www.e-fense.com/helix/Docs/Jesse_Kornblum.pdf"). (Jesse Kornblum - 2002)
[The Law Enforcement and Forensic Examiner Introduction to Linux A Beginner's Guide]("http://www.e-fense.com/helix/Docs/Law.Enforcement.Linux.Intro.2.0.5.pdf"). (SA Barry J. Grundy - 2004)
[Forensic Analysis of Microsoft Windows Recycle Bin Records]("http://www.e-fense.com/helix/Docs/Recycler_Bin_Record_Reconstruction.pdf"). (Keith J. Jones - 2003)



 **[COLOR=yellow]HELIX:[/COLOR]**

[Helix for Beginners]("http://www.e-fense.com/helix/Docs/Helix0307.pdf") (BJ Gleason & Drew Fahey)
 


 **[COLOR=yellow]MISC:[/COLOR]**
[Chain of Custody form ]("http://www.e-fense.com/helix/Docs/coc.pdf") (NEW) for forensic images (e-fense - 2006)
[http://www.e-fense.com/helix/docs.php](http://www.e-fense.com/helix/docs.php)

---

