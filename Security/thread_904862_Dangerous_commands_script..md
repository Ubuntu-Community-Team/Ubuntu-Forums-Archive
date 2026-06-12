---
title: "Dangerous commands script."
date: 2008-08-29
forum: Security
---

### Post by MadnessRed on 2008-08-29
Hi, I am relatively new to Ubuntu. I started with Ubuntu 7.04 and have used 7.10 and 8.04 since. TBH it took me a while to get used to Linux and make it work for me, so as you can image I spent the best part of a year blindly following commands to make stuff work.

Thankfully I don't think I did any harm to my computer. At least not since April since I last install Ubuntu. However, I have heard of people who tell noob users like I was to run commands like sudo rm-rf, and people like me would have run them without knowing any better.

What I am now planning of doing is writing a script that the user can enter the command and then will be told in standard language how safe it is and what it will do.

For example.

"sudo gedit /boot/grub/menu.lst" would output
As admin, Open "/boot/grub/menu.lst" in Text Editor

This is based on the three parts of the command.

$sudo. - run a basic check for "sudo *" in the string. (If there $sudo = "As Admin, "

$operation - each command will have an assigned operation, eg gedit = "Open"

$file_command - what file or commands are being run. Eg int eh example above the file is "/boot/grub/menu.lst"

$program_info - what the program is (eg "in Text Editor").

-----

I could either program this for php or I could try c.

Advantages of PHP are that I am more confident in that language and it might be easier for peopel to run the command online.

Advantages of c is that some1 could just do

checkcommand sudo rm-rf

before running it and be saved.

-----

I would quite like some feedback on this, what people think. Prehaps a list of the real danger commands which I could check for first.

Also if this has beendone before, because if it has there is no point me doing it again.

-----

ps: (edit)

if this is in the wrong place feel free to move it, I wasn't sure where to put it.

---

### Post by ApUUbunU on 2008-08-29
Sounds like a quite good idea MaddnessRed. However, it overlaps a bit with man *command*, which shows info on what the command does, and how it is used. The descrption is probably good enough for newbies, and there is a good deal of information in most man pages for more advanced users.

---

### Post by inteluser on 2008-08-29
Perl might be a good choice - it has excellent string handling abilities, and can be run from the command line as a shell script.  Of course, php probably can too, but I'm not sure.

It may be worth thinking about the sheer volume of malicious commands one could author.  For example, it would be very difficult to detect the bash fork bomb (the one that begins with **:(){**) or a rot-13 command that un-rot'ed and then run.  A good start would be trying to catch everything in the Malicious Commands announcement on this forum.

Another good step would be to support analyzing shell scripts - chkcommand script.sh could go through the script line-by-line, analyzing each line.

Seems like a tough project.

---

### Post by MadnessRed on 2008-08-30
if man already exists then there s little point me re-doing it, however a basic php script might be useful.

---

