---
title: "deep freeze clone"
date: 2010-07-12
forum: Security
---

### Post by JakeFrederix on 2010-07-12
Hi everyone,

I'd like to make an open-source version of a program called "Deep Freeze".
Basically it prevents users from making permanent changes to a computer.
Convenient for computers in libraries, public places, ...

You can still do pretty much anything with the computer, but as soon as you reboot it, all changes have gone.

So, I was thinking of going about it this way;
1) monitor each harddrive, when a change is made log it to a hidden file
2) at startup, read the logfile, reverse all

I know this is a bit simple (and the log file poses a security gap), but it's a good start.
I cannot find any way to monitor changes on the harddrive though.

I'd program this in C++ by the way.

Anyone got any ideas?

Jake

---

### Post by viralmeme on 2010-07-12
> **JakeFrederix said:**
> I'd like to make an open-source version of a program called "Deep Freeze". Basically it prevents users from making permanent changes to a computer.

No need to write your own app, you can already do that with the current Ubuntu,. Just create a standard user and add a line to .bash_logout to remove any newly created files at logout.

---

### Post by JakeFrederix on 2010-07-12
Perhaps I should clarify.
I want to make this application available not only for Linux, but for Windows as well as Mac. I see no reason not to share such a good utility.
Also, most libraries or computer in public places run Windows.

---

### Post by Sporkman on 2010-07-12
Just keep a backup disk image somewhere, then for each file on the system, if the modification date > the backup image's file's modification date, copy the backup file over to the current one.

Or perhaps have rsync do that for you...

---

### Post by JakeFrederix on 2010-07-12
Backing up the entire disk is an expensive (in terms of algorithmic cost) operation.
It would be easier to restore only the affected areas.

---

### Post by viralmeme on 2010-07-13
> **JakeFrederix said:**
> Backing up the entire disk is an expensive (in terms of algorithmic cost) operation.
It would be easier to restore only the affected areas.
You could try running a chroot environment and reset that at each logout ..

[en.wikipedia.org/wiki/Chroot]("http://ubuntuforums.org/en.wikipedia.org/wiki/Chroot")

---

### Post by theozzlives on 2010-07-13
You maybe can set a mandatory profile where changes cannot be made. I don't know if that is possible in Mac, as I have never worked with a Mac.

---

### Post by HermanAB on 2010-07-13
Use Virtualbox and every night, restore the VM from a tar ball.

---

### Post by JakeFrederix on 2010-07-13
I am not looking for suggestions on how to go about implementing this clone.
Storing an archive, mirror, resetting everything to default, all are good suggestions, but they are not what I want.

I am looking for a driver I can put over a harddisk, that will record any changes made.

Kind regards,
Jake

---

### Post by Sporkman on 2010-07-15
I just saw this package in synaptic, & it reminded me of this thread:

**loggedfs**

> Fuse-filesystem daemon logging every filesystem operations

LoggedFS is a transparent fuse-filesystem which allows you to log every
operation that takes place in the backend filesystem. Logs can be written
to syslog, into a file, or to the standard output.

You can add filters to an XML file to filter on users, operations (open,
read, write, chown, chmod, etc.), filenames and return codes.
Since it is fuse-based, you don't need to change anything in your kernel
or on your hard disk partition to use it.

This of course only applies to linux. In the linux case, maybe you could process the operations from the log output, and restore backed-up versions of modified files. Or, hack the package to do other stuff above & beyond the logging.

---

### Post by movieman on 2010-07-15
Surely the best solution is to implement this at the filesystem level like a live CD, where the filesystem is read-only but you can 'update' it by writing to RAM disk filesystem?

That way there's no need to copy anything as the new 'files' are in RAM and disappear on the next reboot.

---

### Post by JakeFrederix on 2010-08-14
I am not trying to be mean, honestly.
But why is everyone so keen on changing my question?

---

### Post by cariboo on 2010-08-14
You have probably asked this question in the wrong sub-forum, if you want to create an application. I would suggest you ask your question in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") sub-forum.

---

### Post by Quinn2 on 2010-10-21
Jake, did you ever figure out how to create what you want?  My boss and I were just discussing this very thing.  Why isn't there an Open Source version of Deep Freeze?  It's exactly what we are looking for.  We have a 45-station public computer lab at a library.  We're currently using SteadyState, as we have XP machines.  We want to move to Windows 7, but in Microsoft's ultimate wisdom, they have discontinued compatibility.  They apparently started out offering something like SteadyState to use with Windows 7 and then took it away.  I would think there would be thousands of small internet cafes, public libraries and schools that are looking for the same thing.  I'm surprised I can't find anything.  If you come up with something, I would love to try it:

---

### Post by theller on 2011-07-22
Are you still working on this project? Have you seen this thread <[http://ubuntuforums.org/showthread.php?t=1294501&highlight=rsync+freeze](http://ubuntuforums.org/showthread.php?t=1294501&highlight=rsync+freeze)>?

---

