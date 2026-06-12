---
title: "Folder/Structure sugestion"
date: 2008-03-11
forum: Ubuntu Brainstorm
---

### Post by oasmar1 on 2008-03-11
One thing that I do not like in ubuntu (im not sure if this is something with all linux distributions) is the folder structure. There seems to be far too many folders in the root of the system and i do not understand why a more organised system is used (I am a beginner to ubuntu and i might learn and get used to it in the future and i do not know much about programming so i don't have a clue to whether it can even be modfiied).
I would much prefer a system where the files are something like this:
/Programs/ - this is where most of the data for programs and applications would go.

/User/*account name*/Documents
/User/*account name*/Program settings etc

/Ubuntu/ This is where all the things that most people need never look at for example libraries and drivers and all that other stuff.

It doesnt have to be like this but i think it would be a great improvement if most of the files would go under a ubuntu folder if they were not ever changed by the user.

---

### Post by smartboyathome on 2008-03-11
I have already suggested such a file system, which can be done through the use of Gobohide. It hasn't come welcome though. If you want to see the discussion, see [here]("http://ubuntuforums.org/showthread.php?t=589916").

---

### Post by Oldsoldier2003 on 2008-03-11
> **oasmar1 said:**
> One thing that I do not like in ubuntu (im not sure if this is something with all linux distributions) is the folder structure. There seems to be far too many folders in the root of the system and i do not understand why a more organised system is used (I am a beginner to ubuntu and i might learn and get used to it in the future and i do not know much about programming so i don't have a clue to whether it can even be modfiied).
I would much prefer a system where the files are something like this:
/Programs/ - this is where most of the data for programs and applications would go.

/User/*account name*/Documents
/User/*account name*/Program settings etc

/Ubuntu/ This is where all the things that most people need never look at for example libraries and drivers and all that other stuff.

It doesnt have to be like this but i think it would be a great improvement if most of the files would go under a ubuntu folder if they were not ever changed by the user.

the thing is that Linux has a "standard" setup that makes it easy to use in a multi user mode. It's actually not as hard as you think, you just have to de-windowize your mindset.

[http://www.ahinc.com/linux101/structure.htm](http://www.ahinc.com/linux101/structure.htm)

---

### Post by coolen on 2008-03-13
This has been discussed before, and I can assure you, no action will be taken.

This is not due to stubbornness. The current filesystem structure is a standard, common to most *nix type systems. It has been standard for a long time now.

Changing to the Gobo FS would require a lot of work in the kernel, the individual applications, the package manager...basically, everything, and there's no good reason for it.

Standards are good. You can't reinvent them because of a handful of use cases, especially when they're as basic as the filesystem tree.

---

### Post by bruce89 on 2008-03-13
There has been work to minimise the difference between Debian and Ubuntu packages. Replacing the FHS would put this down the toilet, as well as waste huge amounts of developer time on vanity I'm not even going to mention the fact that this would mean Ubuntu was not LSB compliant.

---

### Post by gashcr on 2008-03-13
I actually like this structure a lot more than that horrid chaos windows filesystem is. At least nobody but root can mess the whole system up.

Once you get used to it, it is easier to manage. Anyway, most of the time you won't need to go beyond your home folder, so I think there's no need to do any changes.

Let's just obey that good old saying: "If it ain't broken son, don´t try to fix it"

---

### Post by smartboyathome on 2008-03-13
By the way, unlike what has already been said, the Gobo system would NOT break packages or anything else for that matter. Everything is symlinked, and it would just require the kernel module being compiled into the kernel and the userland application installed. Maybe the kernel module can be made into a package and put into the repos? Then bugs can be worked out and it could be used by the people who want it.

---

### Post by coolen on 2008-03-13
That's the general idea, yes.

Background info for others: GoboLinux uses symlinks so packages not built for it can still find everything where it;s expected to be. It uses a kernel patch to hide these symlinks from the user, presenting them with the tree they love.

It's the general idea, but you can't tell me this wouldn't be without bugs. It wouldn't be a drop-in replacement for the current tree. There would be bugs. There would be many, many bugs. It would probably require three release cycles to iron out all of these bugs, causing Ubuntu to not only lose its stability, but also lose a great deal of its functionality, not to mention blocking access to the latest FOSS developments ("wow, look at all the great things Tracker can do now. Too bad *Tracker doesn't work*!").

---

### Post by smartboyathome on 2008-03-13
> **coolen said:**
> That's the general idea, yes.

Background info for others: GoboLinux uses symlinks so packages not built for it can still find everything where it;s expected to be. It uses a kernel patch to hide these symlinks from the user, presenting them with the tree they love.

It's the general idea, but you can't tell me this wouldn't be without bugs. It wouldn't be a drop-in replacement for the current tree. There would be bugs. There would be many, many bugs. It would probably require three release cycles to iron out all of these bugs, causing Ubuntu to not only lose its stability, but also lose a great deal of its functionality, not to mention blocking access to the latest FOSS developments ("wow, look at all the great things Tracker can do now. Too bad *Tracker doesn't work*!").

I doubt there would be as many bugs as you claim (check symlinks, they redirect traffic) so everything would remain compatible. Like I said, package it and put it in the repos so people can test it, and don't include it yet.

---

### Post by coolen on 2008-03-13
I think you underestimate the complexity of your system, and the differences between different distirbutions.

There will be bugs. Many bugs. It's too much trouble for almost no advantage.

---

### Post by smartboyathome on 2008-03-13
> **coolen said:**
> I think you underestimate the complexity of your system, and the differences between different distirbutions.

There will be bugs. Many bugs. It's too much trouble for almost no advantage.

You don't seem to understand it is actually SIMPLER than you think. All the symlinks should cover everything. I am going to try again with the hardy kernel to see if I can get it compiled again and see all these bugs. ;)

---

### Post by coolen on 2008-03-15
No matter, it still won't happen.

---

### Post by tom56 on 2008-03-17
Changing the structure now would be complicated and pointless.

You never need anything outside of your home anyway. What's so complicated about that?

---

