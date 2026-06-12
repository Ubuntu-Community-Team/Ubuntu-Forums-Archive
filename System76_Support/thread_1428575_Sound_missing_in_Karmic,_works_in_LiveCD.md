---
title: "Sound missing in Karmic, works in LiveCD"
date: 2010-03-12
forum: System76 Support
---

### Post by phyzome on 2010-03-12
I have a Pangolin Performance (panp4i) that had working sound in Intrepid. I upgraded to Karmic, and while sound worked fine in the LiveCD, it no longer works in my installed version. Unfortunately, I do not recall if it ever worked after installation.

I have attached some diagnostic screenshots and command line dumps in a tgz file. It contains two folders:

[LIST]
[*]current diagnostics
[*]liveCD diagnostics
[/LIST]

Each contains these files:

[LIST]
[*]gnovolman hardware.png
[*]gnovolman input.png
[*]gnovolman output.png
[*]lsmod.txt
[*]lspci.txt
[*]packages.lst
[/LIST]

The screenshots are of gnome-volume-manager. You can see that the LiveCD version has devices listed, but the current version is empty or has a dummy entry.

There is also a file called "package.lst.diff" that contains the diff of the sorted respective packages.lst files.

I would be grateful for any assistance in this matter, as I currently have absolutely zero audio capability.

---

### Post by riseringseeker on 2010-03-13
> **phyzome said:**
> I have a Pangolin Performance (panp4i) that had working sound in Intrepid. I upgraded to Karmic, and while sound worked fine in the LiveCD, it no longer works in my installed version. Unfortunately, I do not recall if it ever worked after installation.

I have attached some diagnostic screenshots and command line dumps in a tgz file. It contains two folders:

[LIST]
[*]current diagnostics
[*]liveCD diagnostics
[/LIST]

Each contains these files:

[LIST]
[*]gnovolman hardware.png
[*]gnovolman input.png
[*]gnovolman output.png
[*]lsmod.txt
[*]lspci.txt
[*]packages.lst
[/LIST]

The screenshots are of gnome-volume-manager. You can see that the LiveCD version has devices listed, but the current version is empty or has a dummy entry.

There is also a file called "package.lst.diff" that contains the diff of the sorted respective packages.lst files.

I would be grateful for any assistance in this matter, as I currently have absolutely zero audio capability.

If you haven't already, take a look under System->Administration->Hardware Drivers and see if the Software Modem is active, if it is, disable it.  It has worked for other folks here on the board.

---

### Post by phyzome on 2010-03-13
> **riseringseeker said:**
> If you haven't already, take a look under System->Administration->Hardware Drivers and see if the Software Modem is active, if it is, disable it.  It has worked for other folks here on the board.

Brilliant! It worked immediately! Thank you so much.

---

### Post by riseringseeker on 2010-03-14
> **phyzome said:**
> Brilliant! It worked immediately! Thank you so much.

<Gentle chiding mode on>

Two things.  

1) This had been covered in multiple threads both inside the System76 sub-forum as well as other sub-forums on this board and others.  Please do a little more searching before posting a question.  

I realize the search function here leaves more than a little to be desired ofttimes, but you can also search here perhaps a little more efficiently by using google to specifically search this site - in the google search window, type something like  "site: ubuntuforums.org [SOLVED] no sound with karmic".  The first result listed for that search has the same solution in post #3.

You can also use the [_http://www.google.com/linux_](_http://www.google.com/linux_) search function.  There are also many many linux help sites that I have found answers to even though they were not specifically *buntu sites.

2) You saw above I used google to search for solved threads.  When you do ask a question, and get a working solution, (like here), please mark it solved.  You can do so on any threads you started by clicking on "Thread Tools".

<chiding mode off>

Most everyone on this (and other) board(s) are always happy to help and glad when a proposed solution works for you, glad I could help.

---

### Post by tlroche on 2010-03-14
> **riseringseeker said:**
> in the google search window, type something like  "site: ubuntuforums.org [SOLVED] no sound with karmic".

On the same tip, it would help the next poor <bleep/> if you=phyzome would edit the original post (in this thread) such that the title begins with "[SOLVED]". I believe only you (the post originator) can do that (though perhaps a moderator can as well).

---

### Post by riseringseeker on 2010-03-14
> **tlroche said:**
> On the same tip, it would help the next poor <bleep/> if you=phyzome would edit the original post (in this thread) such that the title begins with "[SOLVED]". I believe only you (the post originator) can do that (though perhaps a moderator can as well).

I guess you didn't read the second point of **my** post.

---

### Post by phyzome on 2010-03-16
> **riseringseeker said:**
> 1) This had been covered in multiple threads both inside the System76 sub-forum as well as other sub-forums on this board and others.  Please do a little more searching before posting a question.

I usually have pretty good google-fu, but it apparently failed me on this one. I think it is because there are *so damn many* sound problems in Ubuntu -- all I was getting was noise, no signal. (Pardon the pun.)

> **riseringseeker said:**
> 2) You saw above I used google to search for solved threads.  When you do ask a question, and get a working solution, (like here), please mark it solved.  You can do so on any threads you started by clicking on "Thread Tools".

Done, thanks for reminding me.

---

### Post by riseringseeker on 2010-03-17
[QUOTE=phyzome;8976625]I usually have pretty good google-fu, but it apparently failed me on this one. I think it is because there are *so damn many* sound problems in Ubuntu -- all I was getting was noise, no signal. (Pardon the pun.)

I know the feeling, that's why I use google/linux, or the "site:" thing in google itself.  Returns better results than the search function on the board.

---

