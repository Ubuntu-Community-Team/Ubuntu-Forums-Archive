---
title: "Revision Control For Multimedia"
date: 2008-02-13
forum: The Cafe
---

### Post by Spenzer4Hire on 2008-02-13
As a hobby I do recordings for friends/local bands, and occasionally I will record something of my own.  Often times in the recording/mixing process it would be useful to revert to previous versions, or create a fork of a project, etc.

I'd like to create a system to track my changes.  In most cases we are talking about a large amount of relatively static .wav files and an ever changing project file.  I'd like a system that can track changes of the project file as well as the .wav's, but taking full directory snapshots would start to consume alot of space.

I'm not a programmer, but my needs sound like something a revision control system would take care of.  Do you know of any that would be useful with multimedia files?  Or, am I asking too much?  Should I just settle for something like rdiff-backup?

I'd really like to be able to fork and merge branches.

Thanks for any suggestions you can provide.

---

### Post by 23meg on 2008-02-13
Have you actually tried using a regular modern VCS, such as git, Bazaar or Mercurial for this purpose? If you did, what are the shortcomings that you ran into?

---

### Post by Spenzer4Hire on 2008-02-14
No, I haven't tried any available VCS's.  I've been reading up on them and they sound like they should be able to fill my needs.

Is there a VCS that you can recommend?  I've been reading about SVN and it doesn't seem too difficult to implement, but might be overkill for a single user setup.  I'm going to look into DVCS's, but at first glance it was easier to wrap my head around a traditional client-server model.

---

### Post by Spenzer4Hire on 2008-02-14
Bazaar is looking pretty straightforward for a single user.  Any reason why I shouldn't use it?  SVN has been around longer and has methods for resolving corruption issues, etc.  Anything I should look out for?

---

### Post by Sunnz on 2008-02-16
Have you tried RCS?

RCS is probably the most basic version control you can get on any Unix like OS, it doesn't store over the network, it doesn't manage a whole folder, just a single file and it doesn't have all the fancy stuff, it just creates a foo.txt,v for a foo.txt on the same directory. It mostly just uses 2 commands: ci and co, for check-in and check-out.

If you like something really simple RCS may be the right thing, try it with some sample files in /tmp with ci -l and co -l... of course if you decide to use it you might want to look at man ci and man co.

---

### Post by 23meg on 2008-02-16
[QUOTE=Spenzer4Hire]Bazaar is looking pretty straightforward for a single user. Any reason why I shouldn't use it?[/QUOTE]

The only reason I can think of would be that it performs considerably slower than most systems. I don't have any experience with using it with binaries exclusively, but it seems to handle the few binaries here and there in my projects pretty fine. The Ubuntu artwork team also use it to track revisions to images.

[QUOTE=Spenzer4Hire]SVN has been around longer and has methods for resolving corruption issues, etc. Anything I should look out for?[/QUOTE]

I'd avoid the legacy systems. The fact that SVN has methods for resolving corruption issues should tell you something: that corruption issues actually do occur. They should not. If it couldn't be guaranteed that I'll be able to get out of the VCS exactly what I put in, at any future point, I'd never touch that system. git and Bazaar seem (according to my own experience and reports of others I've read) very reliable.

---

