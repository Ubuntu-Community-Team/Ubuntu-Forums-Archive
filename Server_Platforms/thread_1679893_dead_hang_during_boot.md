---
title: "dead hang during boot"
date: 2011-02-01
forum: Server Platforms
---

### Post by Skaperen on 2011-02-01
On this one machine, the hardware seems OK, because I can boot the DVD OK, and within the DVD I can do lots of heavy I/O stuff to the disk and all works OK.  So if the hardware is OK, something must have gone wrong in the software that brings the system up.

It comes up to the point of fsck reporting the filesystems are clean, and how many files and blocks.  After that it just hangs.  There is no more activity and no more messages.  It sat that way for a few hours just to be sure.  On a similarly configure machine without the problem, the next message reports something about keymaps.  So apparently something done after fsck and before loading keymaps (I guess), something is done that just hangs.

How can I find out what all is being done between those actions so I can focus my investigation into what might be wrong?  The way Ubuntu boots up these days, there's no simple one script to look at all the steps being done.  There's too much "hand waving magic" going on by too many scripts to make this apparent.  And to add difficulty, I don't have physical access to the machine ... I've had to guide someone else in steps like booting up, and how to boot the DVD into the "try Ubuntu" mode and set it up so I can login via ssh (by which I have tested hardware and cannot see a failure).

Anyone around here understand the Ubuntu init system? I only know the simpler BSD/Slackware kind of stuff.

---

