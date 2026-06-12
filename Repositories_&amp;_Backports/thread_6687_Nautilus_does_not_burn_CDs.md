---
title: "Nautilus does not burn CDs"
date: 2004-11-30
forum: Repositories &amp; Backports
---

### Post by littlegreenman on 2004-11-30
Hi all,

Have installed Ubuntu a week ago, and today I've tried for the first time to burn a cd.

I've tried both the live ubuntu .iso and a data cd (mp3).

And doesn't work. For instance the mp3 CD does play some of the mp3s but not all. I think about 100MB of the data is actually working. If I 'ls' the directories all files are aparently there, but not playing. 

Don't know what might be causing this as I don't even know where to start to look. My cd burner was recognised by Ubuntu, or at least it did not tell me anything otherwise.

Plus, there is no easy way I see to configure the Nautilus CD Burner function (by easy I mean opening Nautilus and choose option or something) plus on terminal mode I don't even know where to start to see what I can do about it.

Ubuntu wiki doesn't seem to cover this (after my brief, 2 seconds I'm frustrated, search  :) )

Help needed... Installing X-CD-Roast from synaptic... will tell you what happens.

Thank you.  :-&

************
update
************

X-CD-Roast works fine. Just burned an mp3 cd and it works fine. I set up speed at 32x (my cd recorder max speed is 52x which is the only speed nautilus records at with me).

can i change nautilus spped, maybe that is the prob....

---

### Post by jdodson on 2004-11-30
i thought you could right click an iso and the option, burn to cd was available.   perhaps i am wrong on this one.

---

### Post by littlegreenman on 2004-11-30
you are right. you have the .iso file you right click on it and say burn to cd.

nautlius does some reading, some recording, the red light in my cd recorded lights up, a bit later it's over, the cd ejects, but I do not have an ISO image recorded on my CD......

---

### Post by littlegreenman on 2004-11-30
when I run

sudo cdrecord -scanbus

it says this:

Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .



going to install the cdrtools-doc

---

### Post by jdong on 2004-11-30
Application->System Tools->Configuration Editor.

Navigate to /apps/nautilus-cd-burner

Turn on Burnproof.
Change default_speed to something you feel is suitable.

---

### Post by littlegreenman on 2004-11-30
Thank Jdong  :mrgreen: 

 :mrgreen: 
 :mrgreen: 

Live CD is burned on a CD... now I can start flogging it to my friends....

Great... I am happy again  8)

---

