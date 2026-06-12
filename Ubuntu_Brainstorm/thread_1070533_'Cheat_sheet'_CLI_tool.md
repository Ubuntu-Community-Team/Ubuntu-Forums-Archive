---
title: "'Cheat sheet' CLI tool"
date: 2009-02-15
forum: Ubuntu Brainstorm
---

### Post by Afromonkey0 on 2009-02-15
I've recently made a little tool for myself (a very little tool) called 'cheat'. It is a command line tool which functions like a linux command line cheat sheet. Currently it consists of a .cheatrc file, containing a tab-separated table of handy commands and a description of what they do, and a script in /usr/bin which cats the file, greps for a search term and pipes to column for pretty printing.
So whenever I come across a nifty bash command, i add it to my .cheatrc file and can find it easily later, with 'cheat <search term>'

For example suppose i want to find some info about my hard disk, if i run 'cheat disk', i get this;

dd bs=1M if=/dev/sda | gzip | ssh user@remote 'dd of=sda.gz'  Backup harddisk to remote machine
du -s * | sort -k1,1rn | head                                 Show top disk users in current dir. See also dutop
fdisk -l                                                      Show disks partitions sizes and types (run as root)
smartctl -A /dev/sda | grep Power_On_Hours                    How long has this disk (system) been powered on in total
hdparm -i /dev/sda                                            Show info about disk sda
hdparm -tT /dev/sda                                           Do a read speed test on disk sda
badblocks -s /dev/sda                                         Test for unreadable blocks on disk sda


In future i want to add the ability to add cheats via the command line with 'cheat -a', 'cheat --add' or something.

The tool is almost ridiculously simple but i find i use it all the time, so my question is, do you think this project is worth developing into a full tool, releasing the source and trying to get it included in ubuntu releases? It certainly wouldn't waste much space on a live CD.
Or has this been done already? Is there a better tool extant? Searching google for any combination of 'CLI' 'Cheat sheet' 'linux' and 'tool' only gives hundred of PDF linux cheat sheets, so i can't tell.
What's your opinion?

[edit] The forum ignores tabs, so assume that the above output is all lined up in nice neat columns.

---

### Post by Sprut1 on 2009-02-15
I just use the "man" function and it works very well.

---

### Post by Mud.Knee.Havoc on 2009-02-15
Sometimes man is too confusing, or one forgets exactly which switches to use.  Even though I know exactly which command I want, sometimes I end up googling the command for examples.  I find that I make good use of the Zim desktop wiki for this.  I've got a page full of linux tips with commands that I found myself googling multiple times (such as mencoder original.file -oac mp3lame -ovc xvid -xvidencopts bitrate=1700 -o output.filename.avi to convert media files to .avi).  Zim is great for taking little notes, just make sure to have it start at each session.

---

### Post by Afromonkey0 on 2009-02-15
Yeah, it seems almost everyone has their own little system to do this or something similar. Everyone I've talked to at least keeps a list of nifty commands, whether or not they have a tool to search or add to them.

I'm thinking the community could really benefit from a de facto standard for the files, with a standard linux tool that can read them. I'm imagining sites maintaining communal lists of clever commands in the right format online, with 'cheat --update' to download the latest file from your preferred source. Blogs could offer cheatrc files to append to your own at the end of posts that contain clever command line tricks.

---

### Post by Mud.Knee.Havoc on 2009-02-15
> **Afromonkey0 said:**
> append to your own at the end of posts that contain clever command line tricks.

I think you might be onto something with this.  I'd like to have a commandline tool that would allow me to save a number of customized strings that I would never remember (the long mencoder commands come to mind again).  So if I want to convert a media file to .avi to watch on my set-top DVD/divx player, I could run, say "cheat mencoder" and pick the "convert to avi" customized command, but if I wanted to convert a media file to the tiny .mpg to watch on my Sansa, I could run the same "cheat mencoder" command to search for the "convert to Sansa" custom command.  

Maybe I'm not making a lot of sense with these examples, but I can definitely see that this could be useful.

You have no idea how many times I've looked through my bash terminal command history to find a long, complex command - but can't find it because I used it way too long ago. :(

---

### Post by lswb on 2009-02-15
The command 

man -k keyword

kind of does the same thing, doesn't it?

---

### Post by Afromonkey0 on 2009-02-15
> The command

man -k keyword

kind of does the same thing, doesn't it? 

Not really. man -k or apropos will tell you what tools are related to a keyword, but man -k will never tell you that

ps -e -orss=,args= | sort -b -k1,1n | pr -TW$COLUMNS

lists all processes by memory usage, or that

dd bs=1M if=/dev/sda | gzip | ssh user@remote 'dd of=sda.gz'

backs up your hard disk to a remote machine.

Cheat lets you keep a record of clever command line tricks, rather than just what individual tools are for.

---

