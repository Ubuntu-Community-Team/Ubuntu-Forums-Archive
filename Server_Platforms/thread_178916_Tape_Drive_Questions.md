---
title: "Tape Drive Questions"
date: 2006-05-18
forum: Server Platforms
---

### Post by dk_pa on 2006-05-18
I've never really worked with tape drives before but i have been using the commands mt and working with tar to get use to one at work.

I really have no idea how fast/slow recovery or reading from a tape drive SHOULD be so feel free to inform me.

Today I tried to get a listing of files on an old tape just to see what was actually on the tape I used the command

tar tvf /dev/nst0 > tape_index.txt

I let the tape run for almost 5 hours and it never completed that.  The txt file was huge of course (around 10 GB should be on the tape) but I thought in 5 hours that should have finished.  I then rewound the tape with

mt -f /dev/nst0 rewind

Next thing was restoring a file.  Doing the tar tvf /dev/... command lists the files there and I picked a file that showed up in the first 10 files listed. I used the command

tar xvf /dev/nst0 Cypher/opt....filename.file  

I let this run for almost 2 hours and never got the file off the tape (ctrl-c'd it). 

Am I doing something wrong, are tape drives that slow, or is something wrong with our drive/tape possibily?  

p.s. I've only been working at this place for 1 month so I'm not totally sure of all the details dealing with the backups yet.

---

### Post by Glut on 2006-05-18
Tapes are easiest to deal with if you know what wrote to the tape originally - the os, the program, etc.
Yes tapes are slow, but it very much depends on what type of tape you are using. Feel free to inform us. 
You may want to pull the first blockish (try 126k) off /dev/nst0 with dd to find out the block size. with that and the first block off /dev/sd0 you should be able  to figure out what made them. Lots of tapes have peculiarities so having this information is very useful.

---

