---
title: "Can't Create Object File Error"
date: 2015-01-28
forum: Ubuntu Application Development
---

### Post by cranberries2 on 2015-01-28
[h=2][FONT=comic sans ms]Hi, [/FONT][/h][COLOR=#000000][INDENT][SIZE=2][FONT=comic sans ms]I am new to open source development. And, I am getting the following error in the path which I compile for arm; 

Assembler messages:
Fatal error: can't create bin/arm1176/blabla.o: No such file or directory
*** Error code 1
clearmake: Error: Build script failed for "bin/arm1176/blabla.o"

I've checked the related makefile. And it includes the following rules for blabla ; [/FONT][/SIZE]

[COLOR=#666666]# Libraries[/COLOR][COLOR=green]
[/COLOR][COLOR=green]

[OBJECTS]("http://devices-dev.global-ad.net:8080/openstage_v3r3/s?refs=OBJECTS") = [/COLOR]$([TESTOBJS]("http://devices-dev.global-ad.net:8080/openstage_v3r3/xref/Opera_Platform_Linux/GPAL/USB/makefile#TESTOBJS"))$([COLOR=#990099]LIBOBJS[/COLOR])[COLOR=green]
[/COLOR][COLOR=green]
[LIBOBJS_arm]("http://devices-dev.global-ad.net:8080/openstage_v3r3/s?refs=LIBOBJS_arm") = \
[/COLOR]$([BIN]("http://devices-dev.global-ad.net:8080/openstage_v3r3/xref/Opera_Platform_Linux/GPAL/USB/makefile#BIN"))[COLOR=green]/[blabla.o]("http://devices-dev.global-ad.net:8080/openstage_v3r3/s?path=StringTokenizer.o") \
[/COLOR]
[SIZE=2][FONT=comic sans ms]Could you please mention about the possible causes of the problem ?[/FONT][/SIZE][COLOR=green]
[SIZE=2][FONT=comic sans ms]Thanks in advance for the replies, [/FONT][/SIZE][/COLOR][/INDENT]
[/COLOR]

---

### Post by steeldriver on 2015-01-28
Hello and welcome to the forums

The part of the makefile that you posted doesn't seem to be a rule - just a list of objects

Can you provide more background information? like what you're trying to compile, what exact commands you typed, a larger excerpt of the error message and of the makefile? Also please post terminal output and makefile contents in [CODE] tags as it preserves the formatting (crucial for makefiles!)

---

### Post by cranberries2 on 2015-01-29
Hi, 
I try to make arm compilation for an embedded linux device. I can only provide the more detailed output of the terminal as follows ; 

Assembler messages:
Fatal error: can't create bin/arm1176/blabla.o: No such file or directory
*** Error code 1
clearmake: Error: Build script failed for "bin/arm1176/blabla.o"

By the way, It compiles OK when I compiled for mips . As far as I know, both (mips and arm) read the same makefile. So, do you have any idea about the possible reason ? 

Thanks in advance,

---

### Post by steeldriver on 2015-01-29
With so little information I can only **guess** (which is not the best way to debug issues like this) but maybe the makefile expects the directories to exist already? does bin/arm1176/ exist? if not what happens if you create it (e.g. [FONT=courier new]mkdir -p bin/arm1176/[/FONT])

You could post the whole makefile via pastebin

---

