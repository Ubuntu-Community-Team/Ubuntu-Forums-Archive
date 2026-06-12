---
title: "SUGGESTION to make it possible on all ubuntu to select install location"
date: 2021-04-06
forum: Ubuntu, Linux and OS Chat
---

### Post by zmate32 on 2021-04-06
of the software. It is a lacking feature as i have noticed. I want a drive with full of software and files and i want a drive for the system files

---

### Post by oldfred on 2021-04-06
With Ubuntu the applications are small. And they are actually installed in multiple places in /. 
You can have /home or a large data partition on another drive and have all you data on separate drives.

Some with servers do split other folders into separate partitions, but desktops rarely require that.
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)

---

### Post by guiverc on 2021-04-06
With the use of the *file-system table* (/etc/fstab) you can control which directory gets mounted onto which device.  The added complexity though can create issues with maintenance down the road, so it's generally best to stick with organization policies, or a simple structure.

The most common is to separate user files (/home) and the rest of the system (/) which @oldfred already mentioned. It's easy, extremely common, and for some GNU/Linux distributions is mandatory if you want to re-install and not lose data (isn't a worry with Ubuntu and *flavors* of Ubuntu as they'll install into a non-formatted / but not all will meaning data is /home gets lost unless it's a separate partition).

Other than packages get installed into specific predefined directories, you have almost full control using the "*Something else*" (or "*Manual Partitioning*") installer options (or if you change your mind, you can adjust using *live* media post-install).

---

### Post by QIII on 2021-04-06
While there are ways to do exactly what you suggest, they are not the default ways for a reason.  I highly recommend oldfred's links.

When you have mastered Linux, you will be able to make any changes you wish -- even to the point of creating for yourself an unmanageable and unmaintainable system.

---

### Post by grahammechanical on 2021-04-09
I wonder if the original poster is thinking of Windows applications? Run Setup.exe or Install.exe and the user gets to choose which directory/folder the application is installed into.

Ubuntu developers cannot deviate from the file structure that was worked out many years ago. Ubuntu is built on the Debian distribution which uses the Linux kernel. Both Debian and Ubuntu developers must comply with the directory structure decided upon many years ago by the Linux developers. And having developed the kernel to the status that it now has reached it would be very difficult, if not impossible, for the Linux developers to change things.

There would be massive disagreement throughout the Free and Open Source Software community as to whether the purposed changes were necessary and worth the time and effort making the changes. Every Linux programmer and application developer would need to accept the changes and make them all at the same time.

There is one type of Ubuntu operating system that deviates from the standard directory file structure and that is Ubuntu Core. It is not a server or desktop OS but is designed for the Internet of Things type of devices. Even there the user does not get to choose which directories or partitions applications are installed into. 

Regards

---

### Post by CharlesA on 2021-04-09
> **grahammechanical said:**
> I wonder if the original poster is thinking of Windows applications? Run Setup.exe or Install.exe and the user gets to choose which directory/folder the application is installed into.

That's what it sounds like.

I know you can compile stuff yourself and stick it in /usr/local or ~/bin, but that's as much  of the "store programs separately" that you can get without breaking everything into separate partitions.

---

### Post by CatKiller on 2021-04-09
> **grahammechanical said:**
> Both Debian and Ubuntu developers must comply with the directory structure decided upon many years ago by the Linux developers.
Earlier than that. Most of it came from Unix - that's why we have a Unix System Resources (/usr) directory. Some things have been added or moved around since to serve Linux' requirements.

There *is* a Linux distro whose unique selling point is that they put an overlay on the filesystem so that users don't have to see the Unixy filesystem tree, but I can't remember which one it is off the top of my head.

OP is just used to Windows' way of things, though, agreed.

To clarify for the OP, in case they haven't read oldfred's links, Windows arranges files by *source* so man+dog's installer dumps a bunch of files in a directory in Progra~1 or wherever, and you end up with data and executables and config files all jumbled up in the same directory; Linux (and Unix) arranges files by *type*, so all your executables go one place, all your libraries go a different place, your configuration files have their place, documentation has its own place, and all your user settings and data are in your very own Home folder.

---

### Post by QIII on 2021-04-10
Hmmm ...

The user made a Windows-like request and hasn't been back since.

---

