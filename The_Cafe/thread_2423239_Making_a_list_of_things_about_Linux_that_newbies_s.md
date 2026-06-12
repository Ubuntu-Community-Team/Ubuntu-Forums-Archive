---
title: "Making a list of things about Linux that newbies should learn"
date: 2019-07-19
forum: The Cafe
---

### Post by maitland02 on 2019-07-19
[COLOR=#242729][FONT=Arial]For those of us who are learning Linux, we need to create a list of things to test our knowledge. To determine how proficient we are at Linux and what we need to know next.
It's very frustrating when I search for Linux courses on Udemy and they're all about moving files around. Which is useless because I use Nautilus. They don't cover the important things, such as:
[/FONT][/COLOR]

[LIST]
[*]How to use 3rd party software for PC peripherals that don't support Linux (*Which is just about **everything***).
[*]How to install Universal (*Community created*) packages.
[*]How to view and stop tasks like you can on Windows.
[*]How to launch Ubuntu programs from the command-line.
[*]How to tweak system settings, such as the ability to enable or disable the ability to click on a programs icon within the Dock (*Task-bar*) to minimise it.
[/LIST]
[COLOR=#242729][FONT=Arial]
There's probably a lot more I need to know, but I can't ask about them because I don't know they exist yet.
[/FONT][/COLOR]
Also, do you have any good tutorials? [Perhaps on this server?]("https://ubuntuforums.org/forumdisplay.php?f=100")

---

### Post by TheFu on 2019-07-19
Most Linux systems don't have a GUI at all.  Understanding how the underlying OS works is very important.
People ask me all the time how to learn linux: [https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux) is my answer.

If you keep trying to use Linux like you previously used Windows, you will be very frustrated.  They are different OSes based on vastly different philosophies.  Nothing is more frustrating than having to use some bloated GUI program when a tiny CLI interface would be 1,000x more efficient.  80% of the power from computers comes from non-GUI stuff.

If you are using a mouse, then you are doing it wrong almost always.

---

### Post by uRock on 2019-07-19
> **maitland02 said:**
> For those of us who are learning Linux, we need to create a list of things to test our knowledge. To determine how proficient we are at Linux and what we need to know next.
It's very frustrating when I search for Linux courses on Udemy and they're all about moving files around. Which is useless because I use Nautilus. They don't cover the important things, such as:

How to use 3rd party software for PC peripherals that don't support Linux (*Which is just about **everything***).
Such as? Just about everything I plug in works OOTB.
> How to install Universal (*Community created*) packages.
That depends on the application. Start a support thread asking how to install one of them and you'll likely know what to do with all of them afterwards.
> How to view and stop tasks like you can on Windows.
System Monitor can do this. Personally, I use **htop** which is a command line tool.
> How to launch Ubuntu programs from the command-line.
You'll have to find the program's name. Such as Google Chrome launches with **google-chrome**
> How to tweak system settings, such as the ability to enable or disable the ability to click on a programs icon within the Dock (*Task-bar*) to minimise it.
[https://itsfoss.com/click-to-minimize-ubuntu/](https://itsfoss.com/click-to-minimize-ubuntu/)

> 
There's probably a lot more I need to know, but I can't ask about them because I don't know they exist yet.
Also, do you have any good tutorials? [Perhaps on this server?]("https://ubuntuforums.org/forumdisplay.php?f=100") The best way to learn is to find something you want to do, search for Ubuntu documentation for that task, then give it a go. If all else fails, then ask for help here or on the #ubuntu IRC. I've taken a class in college for Intro to Linux. I did it for the easy A, but I still learned some stuff. File management is everything in Linux, because everything is a file.

---

### Post by TheFu on 2019-07-19
> **uRock said:**
> File management is everything in Linux, because everything is a file. 

The real statement should be "*everything is a file OR a process.  If it isn't a process, then it is a file.*"
Most humans can recognize a process, so anything else is a file.  Files have owners, groups, permissions, ACLs, and a few other attributes which can be altered, managed, locked down.  From that very simple idea grows everything about file and process management on **EVERY** Unix-like OS.   And when we think about popular OSes, there is Windows and everything else.  If it isn't Windows, then it is almost certainly based on Unix.

Very simple idea. Very powerful repercussions.  Permissions control access to files, directories, drivers, devices, pseudo-devices.  That means the keyboard is a file, the monitor is a file, the partition is a file, the whole disk is a file.

We can copy files.  We can append data to files. We can redirect data and files to other places.  From these very simple ideas amazing things are possible.

---

### Post by uRock on 2019-07-19
> **TheFu said:**
> The real statement should be "*everything is a file OR a process.  If it isn't a process, then it is a file.*"
Most humans can recognize a process, so anything else is a file.  Files have owners, groups, permissions, ACLs, and a few other attributes which can be altered, managed, locked down.  From that very simple idea grows everything about file and process management on **EVERY** Unix-like OS.   And when we think about popular OSes, there is Windows and everything else.  If it isn't Windows, then it is almost certainly based on Unix.

Very simple idea. Very powerful repercussions.  Permissions control access to files, directories, drivers, devices, pseudo-devices.  That means the keyboard is a file, the monitor is a file, the partition is a file, the whole disk is a file.

We can copy files.  We can append data to files. We can redirect data and files to other places.  From these very simple ideas amazing things are possible.

Agreed! I only had enough coffee to brew one cup this morning. Incomplete thoughts are my doom for the day.

---

### Post by TheFu on 2019-07-19
> **uRock said:**
> Agreed! I only had enough coffee to brew one cup this morning. Incomplete thoughts are my doom for the day.

You've been completing some of mine for years, uRock!  In the end, the total statement is more complete for the original poster, that's what matters. ;)

There is so much more to Unix systems than point-n-click users realize. I think that's our main point.  With a slight understanding of what is really happening deep inside, way passed the GUI, things become much clearer when the copy/move via Nautilus doesn't work as fast as expected.

For example, a **move** within the same file system is nearly instantaneous for any size file, but if you move a file across different file systems, it is actually implemented as a copy + delete.  That's the difference cause when the move only need update an inode but not actually touch any data at all.  It is also why using hardlinks in versioned backups are so very fast compared to making all new copies.  People without the slightly deeper understanding often do things the least efficient ways.

---

### Post by lammert-nijhof on 2019-07-19
Are we talking about Ubuntu 15 years ago?? None of the things you mention should be learned by any newbie, because the chance they will need it is minimal. Are you trying to chase away newbies??
Why should any user understand, what happens under the hood of Linux. I don't really understand what happens under the hood of my modern car, but I still use it happily each day. 
Only in badly designed OSes, you have to understand, what happens under the hood. Ubuntu/Linux is not a badly designed OS and I'm qualified to judge it, because I designed an OS myself during my 40 years in IT.

---

### Post by cruzer001 on 2019-07-19
Just maybe

[https://wiki.ubuntu.com/Training?action=AttachFile&do=get&target=DesktopCourseStudentGuide.pdf](https://wiki.ubuntu.com/Training?action=AttachFile&do=get&target=DesktopCourseStudentGuide.pdf)

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[https://tutorials.ubuntu.com/](https://tutorials.ubuntu.com/)

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by uRock on 2019-07-19
> **lammert-nijhof said:**
> Are we talking about Ubuntu 15 years ago?? None of the things you mention should be learned by any newbie, because the chance they will need it is minimal. Are you trying to chase away newbies??
Why should any user understand, what happens under the hood of Linux. I don't really understand what happens under the hood of my modern car, but I still use it happily each day. 
Only in badly designed OSes, you have to understand, what happens under the hood. Ubuntu/Linux is not a badly designed OS and I'm qualified to judge it, because I designed an OS myself during my 40 years in IT.

The OP said they want to learn Linux, not just use it. The OP also stated they'd like recommendations for Linux educational courses. That gave to impression they wanted to know what's happening under the hood. 

I'm a 100% DYI guy. Leaky roof, I can fix it. Truck needs brakes, water pump, thermostat, shocks, or whatever, I'm going to do it. I don't trust mechanics, I don't trust contractors, and, thanks to MS, I don't always trust GUIs.

PS, I am finally drinking my second cup of coffee.

---

### Post by mastablasta on 2019-07-22
> **maitland02 said:**
> 

[LIST]
[*]How to use 3rd party software for PC peripherals that don't support Linux (*Which is just about **everything***).
[/LIST]

well these are workarounds

if you have linux compatible peripherals there is no need for 3rd party software, because drivers are in the kernel and they automatically load on boot. if they are not linux compatible there are few options, and each involve a different procedure (scripts, PPAs, compiling from source, not working at all). but in any case it is not how they were meant to be used.

---

### Post by PJs Ronin on 2019-07-22
Patience.

---

