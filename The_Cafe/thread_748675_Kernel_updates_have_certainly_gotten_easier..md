---
title: "Kernel updates have certainly gotten easier."
date: 2008-04-07
forum: The Cafe
---

### Post by kutjara on 2008-04-07
As an on-and-off Linux user since the late 90s, there was nothing I used to dread more than performing a kernel update, except perhaps getting wifi to work on a laptop. These two things have sent me screaming back to MacOS and (cough, cough) Windows more times than I'd like to mention over the years.

So it was with huge trepidation that I finally decided today to take the tiny step from 2.6.24-12 to 2.6.24-15. Ok, ok, I can hear all you Ubuntu gurus laughing your heads off that I was actually afraid to move three lousy revision numbers of the same kernel, but I've been burned so badly and so often by seemingly trivial kernel-related problems in the past that, for me, this was the equivalent of my first solo base-jump. Off the top of Everest.

Guess what? To quote Monty Python: "nothing happened." Or, rather, nothing untoward happened. I installed the new kernel from the Ubuntu repository, allowed the updater to edit menu.lst automatically, rebooted, hit ESC, selected the new kernel, finished the boot sequence, quickly recompiled the madwifi driver for my wireless card, edited menu.lst to remove the "quiet" and "splash" commands (I like my boots to be verbose), rebooted, logged in and voila! A beautifully working Hardy system with a fresh kernel in under five minutes. No screenfulls of error messages on bootup, no X-Server crash, no hours of hunting around for the one terminal command that would resurrect my DOA installation. Nothing. Not a sausage.

It may not seem much to those of you who have been with Ubuntu since the beginning but, for me, it's little short of a miracle.

I just had to get that off my chest. Now I can happily go back to fiddling around with my system until I break something else.

---

### Post by mkarnicki on 2008-04-10
I broke my compiz and wi-fi (ndiswrapper) updating from -10 to -11 version. I struggled to go back with drivers. Recently I turned to -15 (latest), and I'm a happy ubuntu user :)

---

### Post by bigbrovar on 2008-04-10
we breakup to make up  :lolflag:

---

### Post by mkarnicki on 2008-04-12
Yeah, step from 2.6.24-15 to -16 broke my ndis wireless, sound (pulse) and graphics (nvidia). We brake up, we shake up. I've got cpu scaling problems on -15, but everything (almost) works there.

---

