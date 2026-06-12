---
title: "Pros and Cons of Filesystem Hierarchy Standard?"
date: 2009-09-06
forum: The Cafe
---

### Post by keiichidono on 2009-09-06
I searched here and Google'd, but don't have concrete facts on the pros and the cons for the Filesystem Hierarchy Standard and deviations from the standard like PC-BSD, and Gobolinux. As far as i see it, the standard is widely used and intuitive compared to Mac OSX and Windows. While deviations are easier to read and understand for first timers. Help please. :confused:

[1] [http://en.wikipedia.org/wiki/GoboLinux](http://en.wikipedia.org/wiki/GoboLinux)
[2] [http://en.wikipedia.org/wiki/PC-BSD](http://en.wikipedia.org/wiki/PC-BSD)
[3] [http://en.wikipedia.org/wiki/Arch_Linux](http://en.wikipedia.org/wiki/Arch_Linux)
[4] [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Exodist on 2009-09-06
> **CalvinB said:**
> I searched here and Google'd, but don't have concrete facts on the pros and the cons for the Filesystem Hierarchy Standard and deviations from the standard like PC-BSD, and Gobolinux. As far as i see it, the standard is widely used and intuitive compared to Mac OSX and Windows. While deviations are easier to read and understand for first timers. Help please. :confused:

[1] [http://en.wikipedia.org/wiki/GoboLinux](http://en.wikipedia.org/wiki/GoboLinux)
[2] [http://en.wikipedia.org/wiki/PC-BSD](http://en.wikipedia.org/wiki/PC-BSD)
[3] [http://en.wikipedia.org/wiki/Arch_Linux](http://en.wikipedia.org/wiki/Arch_Linux)
[4] [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

The file system can be laid out any way you wish. The only pro is the way the basic linux setup is to protect your files, keep system and kernel files separate. I may be miss understanding what your actually asking tho.

---

### Post by keiichidono on 2009-09-06
> **Exodist said:**
> The file system can be laid out any way you wish. The only pro is the way the basic linux setup is to protect your files, keep system and kernel files separate. I may be miss understanding what your actually asking tho.

I'm just looking for all pros and cons, how you get confuse? :confused:

---

### Post by koenn on 2009-09-06
You have to look at some of the design and implementation principles of the OS. Here are some of the more relevant ones:

- strict seperation between system files and user files
- a directory hierchy that is independent of the underlying storage infrastructure ->  mount points -> need separation between files that need to be accessible before the all filesystems are mounted, and those  those that can wait till all filesystems are mounted
- files are organized by function, a.o. to accomodate shared resources (eg libraries)
- separation between system administration and 'normal use'

practical consideration : programs need access to files (eg config files, libraries, ...) and the location of these files needs to be known at compile time (I think - mybe you should look that up). 


The filesystem hierarchy is an attempt to accomplish those goals.
The FHS is itended to standardize the Linux/Unix filesystem hierarchy in order to support interoperability of applications, system administration tools, development tools, and scripts as well as greater uniformity of documentation for these systems.

Given all that, I guess you can come up with pros and cons yourself, or at least know where to look.

---

### Post by MaxIBoy on 2009-09-06
I think he may be asking for a comparison of FHS versus Windows-style drive letters (C:\ and D:\, etc.)



The main advantage of FHS is that it doesn't matter whether a given directory is actually on the same partition or even in the same continent as your installation. I.E. you can make /home on its own partition, or as an NFS share from another computer, without doing anything elaborate.

The "everything is a file" philosophy makes it very easy to control your devices as well.



Compare with the drive letter system: everything basically needs to be on one partition (no separate home partitions or swap partitions or whatever.) This can be circumvented, but the key word is **circumvented** here-- it goes contrary to the intended usage, and it's a hassle. 

The order you plug in removable media (such as USB flash drives) determines the drive letter you get, which limits how deeply you can integrate the contents of a flash drive with the contents of your C:\ drive (so you can't create a shortcut to F:\whatever on your desktop, because it might be G:\ next time you mount it.)

A name like E:\ is also nowhere near as descriptive as something like /media/cdrom0. 

By the way, I happen to know that if you get past the Z:\ drive, Windows moves on to AA:\, AB:\, AC:\, etc.

EDIT: So it turns out windows *can* do mountpoints instead of drive letters. Here's how: [http://support.microsoft.com/kb/307889](http://support.microsoft.com/kb/307889)

---

### Post by Exodist on 2009-09-06
> **CalvinB said:**
> I'm just looking for all pros and cons, how you get confuse? :confused:

18.5 hours of no sleep.. lmao

---

### Post by tgalati4 on 2009-09-06
Pros:  It's been around forever.
Cons:  If you haven't been around forever, then it looks foreign.

---

### Post by tgalati4 on 2009-09-06
> **tgalati4 said:**
> Pros:  It's been around forever.
Cons:  If you haven't been around forever, then it looks foreign.

Try pushing "HH" in the vending machine.  You don't get the candy bar, you get chips instead.  Then you realize that there's an "HH" button.

---

### Post by keiichidono on 2009-09-06
I was asking how something like Gobolinux using a deviation compared to Ubuntu using the File-system Hierarchy Standard, how did Windows and foreign vending machines get into this? :confused:

---

### Post by thisllub on 2009-09-07
> **CalvinB said:**
> I was asking how something like Gobolinux using a deviation compared to Ubuntu using the File-system Hierarchy Standard, how did Windows and foreign vending machines get into this? :confused:

If vending machines didn't have windows you wouldn't know what was in stock.

---

### Post by MikeTheC on 2009-09-07
> **thisllub said:**
> If vending machines didn't have windows you wouldn't know what was in stock.

Is *that* why they crash all the time?

---

### Post by keiichidono on 2009-09-07
What?

---

### Post by tgalati4 on 2009-09-07
HH was an obscure reference to the late comic Mitch Hedberg.  He also wanted to invent a vending machine of vending machines.  That would be huge.

At school (I won't say when or where) we wired up a coke machine with a modem so you could order a coke using the command line from across campus.  That seemed neat at the time, but not practical.  You still had to go get it.

We were running Unix at the time on DEC workstations.  And you know the file system was pretty much the same as it is today.  So that's the tie-in between file systems and vending machines.

[Q.E.D.]("http://en.wikipedia.org/wiki/Q.E.D.")

Personally, I would freak out if I sat down at a computer and saw:

HH:\

Seriously, using symbolic links you can rename the current standard linux file system structure to anything you want.  The kernel is open source, so you could also do a massive replace of /usr/bin with /executables or even better /my_proggies and do a recompile.

Some people don't like the layout of their keyboard.  Well, you can change that to.  Grab a screwdriver and pop off the keys and move them around.  Don't forget to modify your xmodmaprc file.

The standard is the standard because it has been around for a long time.  There are certainly better/easier file system layouts but they don't have wide adoption.

What was the question?

---

### Post by keiichidono on 2009-09-07
Yes, thank you.

---

