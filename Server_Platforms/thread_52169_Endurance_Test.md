---
title: "Endurance Test"
date: 2005-07-26
forum: Server Platforms
---

### Post by manofsteel on 2005-07-26
I want to run Ubuntu as a server, but I want to makesure its durable on my machine, so is there a shell script that I can run and have Ubuntu running the same script for like three days strait to see if it crashes? I basicly want like a endurace test kinda thing.

---

### Post by safecracker on 2005-07-26
That depends, what exactly do you want to test. System stability is a complex matter you need to take into account hardware used, applications being used and for which purposes as well as the connection your using to the network or internet.

---

### Post by ubuntp on 2005-07-26
What kind of server? Is there a windows share anywhere in that network? A good testcase would be compiling the kernel, while running dd if=/dev/random of=somefile to create a 1GB file and transfer that file to some windows share. Over and over for 3 days. If there's also an internet connection wget some large file (like the ubuntu cd) over and over.

That'll stress CPU, HD and the network card nicely and keep load average high.

---

### Post by manofsteel on 2005-07-26
any way to get the system to move a file from one folder to another for a couple of days strait? I just want to make sure it can handle being up for long periods of time and having files and folders moved around.

---

### Post by safecracker on 2005-07-26
moving 1 big file across a network is not a true test of stability. You must remember most network activity is moving small peices of info. To be honest your really testing the hardware more then the OS. In most cases your using proven software on a server anyway (meaning the flavor of Linux isn't really an issue from a stability standpoint when it's based on something solid).

If using MySQL: [http://cvs.sourceforge.net/viewcvs.py/ltp/utils/database/dbgrinder/](http://cvs.sourceforge.net/viewcvs.py/ltp/utils/database/dbgrinder/)

Test the kernel and some other key features including network componants: [http://sourceforge.net/projects/ltp/](http://sourceforge.net/projects/ltp/)

If you have a webserver:

[http://node.to/hacks/](http://node.to/hacks/) pagepoker
[http://hammerhead.sourceforge.net/](http://hammerhead.sourceforge.net/)

---

### Post by LordHunter317 on 2005-07-27
[QUOTE=ubuntp]A good testcase would be compiling the kernel, while running dd if=/dev/random of=somefile to create a 1GB file and transfer that file to some windows share.[/quote]No, this is a very poor test.  It won't stress any component to it's limit.

> That'll stress CPU, HD and the network card nicely and keep load average high.It won't stress anything but HDD and memory (assuming you have less than 1GB), and even then, I doubt hte load average will peak above 1 ever, after the first transfer.

[quote=manofsteel]any way to get the system to move a file from one folder to another for a couple of days strait? I just want to make sure it can handle being up for long periods of time and having files and folders moved around.[/quote]I believe ttcp can do sustained bandwidth testing, which will give your NIC a good exercise.  Other than that, run a prime95 torture test and memtest86.

Most stability issues for a file server are caused by flakey hardware.  The generic tests for flakey hardware should be more than sufficent for you.

---

### Post by manofsteel on 2005-07-27
thats basicly what i want to test is that Ubuntu will go along time without failing on this system and the loads that it can take before failing. how do i do the prime95 and the  memtest86?

---

### Post by safecracker on 2005-07-28
[QUOTE=LordHunter317]No, this is a very poor test.  It won't stress any component to it's limit.

It won't stress anything but HDD and memory (assuming you have less than 1GB), and even then, I doubt hte load average will peak above 1 ever, after the first transfer.

I believe ttcp can do sustained bandwidth testing, which will give your NIC a good exercise.  Other than that, run a prime95 torture test and memtest86.

Most stability issues for a file server are caused by flakey hardware.  The generic tests for flakey hardware should be more than sufficent for you.[/QUOTE]

You mean MPrime not Prime95 as Prime95 is the windows version, MPrime is the Linux version.

Memtest86 can be run in two seperate modes:

Independent boot process (memtest from the boot loader on startup.)

Running memtest from within Linux,

I recommend using memtest86+ as it is a more up to date version of memtest86 and can be found [here](http://www.memtest.org/) 

Making a memtest boot floppy or enabling the memtest option in your bootloader is probably best.

---

### Post by relix42 on 2005-07-29
[QUOTE=manofsteel] I basicly want like a endurace test kinda thing.[/QUOTE]

Try VA-CTCS.  Its the burn in software that VA Linux used to use on their machines to exercise the box and make sure things were up to snuff.  Can run for as long as you like.

IIRC CTCS became a project on sourceforge.

---

