---
title: "Mencoder in Ubuntu"
date: 2008-09-16
forum: Ubuntu Studio
---

### Post by luchin4u on 2008-09-16
We are trying to run a program that can control the Mencoder, we run a system with 3 or 4 cameras, so we need to write something that can make the encoder encode video from those sources for 30 minutes then re-run Mencoder for another 30 minutes files and so on, but in between those process we need to rename the files and ftp them over the internet. Any help would be appreciate it, we are nuw to Linux, we use currently win2000 machines for our video system so we are trying to migrate to Ubuntu.

Mencoder is reading and encoding directly form the cameras, we got it to record for 30 minutes just fine, but need a script of instructions to get the whole process to run automatically, is a survillance system so we need just to be 30 minutes clips to be easy to browse later if needed, i hope someone can help us with this matter, we are pretty new at Linux so any help would be appreciate it.

This are our commands:

For Cam1
mencoder tv:// -endpos 30:00 -tv driver=v4l2:norm=ntsc:input=0:width=240:height=176 :device=/dev/video0 -nosound -ofps 10 -ovc lavc -lavcopts vcodec=wmv2:vbitrate=30 -o testcam1.wmv

For Cam2
mencoder tv:// -endpos 30:00 -tv driver=v4l2:norm=ntsc:input=1:width=240:height=176 :device=/dev/video0 -nosound -ofps 10 -ovc lavc -lavcopts vcodec=wmv2:vbitrate=30 -o testcam2.wmv

And so forth just changing the testcam name and input number

To watch the Video live we use:
mplayer tv:// -tv driver=v4l2:norm=ntsc:input=0:width=240:height=176 :device=/dev/video0:fps=10 -nosound

We hope you can help us.

Thanks

---

### Post by richardcoates on 2008-09-19
lots of possibilities, what about something like...

hashbang /bin/bash
# this script could be called from cron

function1 ()
{mencoder commands..camera1.. > /dir/filenamecam1'date'
sleep 30m
break }

function2 ()
{mencoder commands..camera2......>  /dir/filenamecam2'date'
sleep 30m
break }

# call function 1 ,output file has date/time appended to name
function1

# optional other commands..

# call function 2
function2

# when complete copy/move files..
ftp /path/dir/filenamecam* destination

exit0

---

