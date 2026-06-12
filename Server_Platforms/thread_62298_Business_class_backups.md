---
title: "Business class backups?"
date: 2005-09-04
forum: Server Platforms
---

### Post by moopere on 2005-09-04
Hi folks,

I'm really struggling with this so I hope I can generate some discussion.  

What are ppl in business/enterprise using for backups of dozens or even hundreds of machines?

Usually, whenever backups are mentioned a lot of folks fill up the thread with this script or that script, almost always based on Tar or derivatives...however, I wouldn't class this as a business or enterprise solution.   The reason is that funky scripts provide unmaintainable backups when you exceed just a couple of machines.  Getting user data back after a failure can be really interesting (and slow).

Imagine: 2-3 servers looking after say 50-100 desktops with users distributing files across the server space as well as locally on their desktop machines.  Lets say we want to run something like a GFS backup, so we might end up with 100 or more tapes within a single year.  

Scripts, removable hard drives, burning CD/DVD's etc etc just are not a reliable solution to even  small scenario as described above.  Something along the lines of Retrospect, Backupexec, Brightstor, Tivoli, etc etc is whats required, but almost none of these solutions offer a Linux server, and of those that do even less....in fact none (I've found so far) offer a Debian/Ubuntu backup solution.

As debian based systems are apparently extremely popular in Linux server space, what are the admins of these (presumably) huge Debian server farms using as backup software?  Is there a powerful Windows box hiding under someones desk with backupexec or netbackup on it?

Interested in people suggestions.
Craig

---

### Post by Beernut on 2005-09-04
Check out backupPc I have not used it yet but it sounds like what you are looking for.  Here is a link  [http://backuppc.sourceforge.net/info.html](http://backuppc.sourceforge.net/info.html)  Hope this helps.

---

### Post by LordHunter317 on 2005-09-04
Amanda and backula are two solutions to look at.

Rdiff-backup is another, that would work well for a server farm, at least.

Most enterprises are using pay software like BRU or Vertias BackupExec (or whatever the heck that crap is called).  That includes for Linux.

---

