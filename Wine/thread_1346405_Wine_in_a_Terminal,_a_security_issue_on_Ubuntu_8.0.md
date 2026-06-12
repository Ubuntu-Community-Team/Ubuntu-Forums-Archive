---
title: "Wine in a Terminal, a security issue on Ubuntu 8.04?"
date: 2009-12-05
forum: Wine
---

### Post by webpilot on 2009-12-05
Hello,

&#8195;I find the following Wine behavior on my system is _not_ a good idea.  I've been unable to find an answer to this question using Google, so I am posting here.

&#8195;&#8195;Many years ago, I wrote some number crunching software using C on a µSoft windows '98 SE machine.  I believe I was using gcc as the compiler for that platform.

&#8195;&#8195;Just recently, I found the software again and attempted to run it using Wine on an Ubuntu 8.04 machine.  The OS has all the updates.  My program did not need to be installed.  It was just an executable I copied into a file folder. 

&#8195;&#8195;To run, I simply found the file using Nautilus, right mouse clicked on the executable, left mouse clicked *Open with "Wine Windows Program Loader"* and the code ran in a small Wine black and white terminal window, prompting me for number input, as it should.  I was pleased the code ran under this OS, too.

&#8195;&#8195;I later found the executable can be run in a Terminal session a couple of ways.


[LIST]
[*] by typing wine and the program name (e.g. *wine ./prog_name.exe*) or
[*] [COLOR=Red][COLOR=Black]by typing [/COLOR]the program name (e.g. *./prog_name.exe*) only !
[/COLOR]
[/LIST]
&#8195;The 2nd method only works if permissions of the file is set to 

&#8195;&#8195;&#8195;***Execute:** Allow _e_xecuting file as program*

&#8195; However, I don't remember setting this.  I believe it was set when I copied the file from my flash drive.

&#8195;So, I am asking is there something I can do to my system to alter this behavior?

&#8195;Namely,

[LIST]
[*]how to force any and all windows .exe files to run only when prefixed by wine at the command prompt
[*]how to set all windows .exe file properties to ***dis** Allow _e_xecuting file as a program *by default.
[/LIST]

Thanks in advance.

**PS** Naturally, if I use Synaptic and uninstall wine, I cannot run the program.

---

### Post by hikaricore on 2009-12-05
I fail to see how this is a security issue.
Considering you can double click on a Windows binary on your desktop easier than you can run it from a terminal by typing.

If you don't want programs runnable without the wine prefix simply:

chmod -x program.exe

I suspect your flash drive is FAT based and linux probably creates a set of default permisions upon copying a file to an actual drive.

---

