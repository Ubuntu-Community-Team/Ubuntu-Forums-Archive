---
title: "[SOLVED] Open source antivirus?"
date: 2008-08-15
forum: The Cafe
---

### Post by mahela007 on 2008-08-15
hey guys... I was just thinking... Open source has brached into a LOT of areas in the software field. Wouldn't it be cool if there was a good, reliable open source antivirus? What do you guys think? (I really need one, thats why I started this thread)

---

### Post by mahela007 on 2008-08-15
i was just seaarching for an antivius programs when I bumped into Clam antivirus. It is an open source antivirus program. Has anyones used this? (unfortunately is it only available for windows).

---

### Post by steeleyuk on 2008-08-16
Its available for Linux as well. Its in the repo's.

---

### Post by maniacmusician on 2008-08-16
Is it? I thought that I saw it in our repositories, as clamav. It's a command line program, but if I remember correctly, it has various frontends; clamtk, avscan, klamav (for KDE). I even remember there being a clamfs (antivirus file system?), though I don't know if it's related or what it's supposed to do.

---

### Post by hansdown on 2008-08-16
Hi mahela007. Clamav finds windows viruses, etc. This is good if you share stuff with windows machines. Linux doesn't allow these things to run unless you give them permission. Even then, executable programs will not run.

---

### Post by LeoSolaris on 2008-08-16
Clam AV is available in the repos. It even has a GUI front end available in the repos.

The major point though, is that Linux is nearly free of viruses that plague Windows. The few viruses that do work on Linux tend to be patched faster, and usually only exist as proof of concepts rather than "in the wild." (That means randomly found online) 

There are other native Linux antivirus software, like Avast, and if you connect to a lot of Windows machines, it is polite to sweep your system occasionally to make sure your not transmitting any viruses to them.

Now rootkits...  that's a different story. You may want check for rootkits if ya install non-repo programs. (especially games) just search the repo with the term rootkit and you will come up with a few hits. I use chkrootkit and rkhunter, myself.

---

### Post by zmjjmz on 2008-08-16
ClamWin is a good antivirus for Windows.
If that's what you're looking for.

---

### Post by lisati on 2008-08-16
AVG free (sadly, not open source, as far as I know) also comes in a Linux version. It takes a little set up for the updates to work, usually adding the user to the avg user group.

---

### Post by mahela007 on 2008-08-16
thanks for the info guys

---

### Post by diwas on 2008-08-16
Why do u need antivirus in linux??

---

### Post by Dremora on 2008-08-16
ClamAV/ClamWIN has been fairly unreliable in detecting malicious software, it doesn't even have a real time scanner.

In Windows, you're better off just using some freeware like Avira or Avast (I won't ever recommend AVG though).

The idea of paying $30 a year to get Norton or Mcafee or Microsoft's antivirus is just absurd.

The theory has been around for a long time that antivirus companies actually make a lot of malicious software to increase business, but I find this increasingly doubtful, since the badware has gone from malicious with no point, to advertising porn sites and stuff. :lolflag:

---

### Post by lisati on 2008-08-16
> **diwas said:**
> Why do u need antivirus in linux??

Reason 1: some of us have Windows partitions and/or Windows VMs
Reason 2: Speaking for myself, I'm in regular contact with users of Windows and don't want a reputation for spreading malware, accidentally or otherwise.

---

