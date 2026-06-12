---
title: "[SOLVED] sound issue, tried seemingly all advice"
date: 2007-12-15
forum: System76 Support
---

### Post by Shaktipwr on 2007-12-15
Ok, If I missed anything I apologize, I tried everything my newbie mind could think of!

My sound is not working.  I originally started with a problem with Gutsy upgrade, had to hit esc at grub something and chose an older edition to be able to use my computer. I am sure you see how new I am now with my *non* lingo.  Anyway I followed some advice i found on another posting and it worked!
So, I had kubuntu installed and decided that I would remove it cause I never used it (although wanted to but didn't get kde).  Did so and also did auto remove to get rid of excess baggage.
I then installed system76 driver because I usually have problems with sound after updates and need to do that.  Well that's when I noticed the problem.  NO SOUND!
I searched and found suggestions and tried all:
 -Check alsi levels    
 - Check gstreamer drivers
 - double checked volume controls
 - Checked my nvidia card (don't know what that is but when I looked for it on my computer nothing seemed to have to be done to it.

Maybe i am missing something but I don't know what else to do.
PLS HELP!  Thx

---

### Post by Shaktipwr on 2007-12-16
I forgot to add that I have a gazelle model #S62FM and am on Ubuntu 7.10 Gutsy.  I noticed no one has any answers.......even a suggestion would rock!  Thanks all

---

### Post by asmiller-ke6seh on 2007-12-17
I reccomend that you backup the contents of your /home directory, and start with a fresh install from a good Gutsy install CD, then restore your /home directory.

This will probably take a lot less time than trying to analyze and fix your problem - which may (or may not) have been caused by upgrading, or any of the other things that you might have done while making major changes to your installation.

---

### Post by thomasaaron on 2007-12-17
You might also try double-clicking on your speaker icon.
In the resulting window, go to edit > preferences and select all available checkboxes.

Then, go to the "switches" tab and try enabling/disabling (ext amp).

---

### Post by Shaktipwr on 2007-12-18
Thanks for the responses
-thomasaaron - Thank you.
I went to the volume control and checked all, then went to switches and I only had a "mix" check box.  I checked that and then I got more boxes to check for enabling and disabling.  I had the external amplification enabled so I disabled it.  It worked.

---

### Post by edc80 on 2008-02-23
-thomasaaron - Thank you.
-Shaktipwr - Thank you.

Disabling the external amplifier switch worked for me too after I had tried everything else.

I just posted the steps I took in:
[http://ubuntuforums.org/showthread.php?p=4386184#post4386184](http://ubuntuforums.org/showthread.php?p=4386184#post4386184)

Again thanks!!

---

