---
title: "Brasero and K3b get track information wrong"
date: 2010-06-29
forum: Ubuntu Studio
---

### Post by il lupo on 2010-06-29
This may well be a general question, but I believe that the application is specific enough that Ubuntu Studio users will know what to do.

I'm new to Linux and Ubuntu Studio, so I'll just describe what I want to do and then tell you all what is happening.

I wish to burn a CD of performances of my compositions.  I used Audacity to edit unwanted applause and spaces between movements.  When storing the edited performance on my hard drive, I recorded as much text about the pieces as possible.  Rhythmbox shows all of this information.

I have tried many times to copy these tracks to discs.  Before using K3b, Brasero simply listed everything as Track 1, Track 2, etc.  I installed K3b and attempted to burn the same performances.  Unfortunately, Rhythmbox lists me as the composer, Henry Goodall.  The title of my CD is "The Lord Is My Shepherd."  While I do sing in church, my compositions are abstract and have nothing to do with "Lords," "Shepherds," or anything else, for that matter.  Also, the titles of the tracks continue in the same vein and do not resemble the titles of my compositions.  I installed cdda2wav, and now Brasero gives me the same problem.

By the way, both programs have the same problem when I try to burn tracks from actual CDs.  Has anyone making CDs of their own music encountered this problem?  I'd love to know your solution.

il lupo (bill)

---

### Post by Pablo_F on 2010-07-01
Hi!

Read this thread. I think it sheds some light:

[http://www.64studio.com/node/681](http://www.64studio.com/node/681)

Cheers! Pablo

---

### Post by il lupo on 2010-07-02
Thank you, Pablo.  Between your thread and exchanges with the authors of these programs, I've learned a great deal.

The problem is that while both Brasero and K3b correctly burn the CD-TEXT, they also assign the disc a CDDB discid.  Here are the options for my own music:

This CD could be:

1: Ali Gator / Ali - ism
2: The Futureheads / Decent Days And Nights
3: DJ Damien / Legend of Art (Super Limited Edition Working Disc)
4: Belgian Asociality / Kriep kriep
5: Howard Goodall / The Lord Is My Shepherd

Here's the funny part:  When both K3b and Rhythmbox are open, one reads the CD as Ali Gator, while the other reads it as Howard Goodall.  Disc ids obviously get priority, and i was able to disable a few of the K3b plugins, forcing the program to read just the text.  That doesn't seem to be an option in Rhythmbox.

My next step is to explore wodim and cdrecorder.  If I can get either to burn my discs without assigning those ids, I will be taking a good step forward.

Thanks again, Pablo!

Best,
il lupo (bill)

---

