---
title: "World of Warcraft and Wine"
date: 2009-08-28
forum: Wine
---

### Post by Blackwolf795 on 2009-08-28
I've searched for a couple of days and so far have been unable to tweak or fix my World of Warcraft to work completely with linux. This is a fresh install of linux, so I'm not sure if my drivers are completely correct. 

Anyway on to the problem, I can load WoW, log in, select my character, however as soon as I get into the game it bugs and locks up. It doesn't give me any sort of error per say, but if I run it from the terminal I get a debug message from Wine. Also the graphics seem a bit off, almost wireframe on character models.

Here's some screenshots of in game:

Character Select screen:
[IMG]http://i884.photobucket.com/albums/ac42/voicelessbass/Screenshot.png[/IMG]

In game:
[IMG]http://i884.photobucket.com/albums/ac42/voicelessbass/Screenshot-1.png[/IMG]

And here is the code for the debug thing that wine does:

*********************************WARN_ONCE*********************************
File r300_state.c function r500SetupRSUnit line 1907
Don't know how to satisfy InputsRead=0x00000008
***************************************************************************
fixme:imm:ImmReleaseContext (0x30062, 0x133028): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x3adad4,0x00000000), stub!
failed to open Z:/home/jonathan/World of Warcraft/Data/Interface/Icons
failed to open Z:/home/jonathan/World of Warcraft/Interface/Icons
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0027), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:003afc70 EBP:003afcd0 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:000083f1 EBX:00008000 ECX:00000de1 EDX:1337f500
 ESI:00000000 EDI:1306ba40
Stack dump:

That's just a small amount of it I can post more if it matters.
Anyhow the game locks up right after this. I tried it without a terminal and it still locks up at the same point.

I've tried all of the various things on ubuntu wow install guides and the like including registery keys and various file edits.

Here are some of my pc specs for reference:
Video card: ATI Technologies Inc Radeon Mobility X1400
Don't remember what these are but more info:
Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express 

Sorry for the super long post.
Any help is much apreciated. Thanks in advance :)

---

