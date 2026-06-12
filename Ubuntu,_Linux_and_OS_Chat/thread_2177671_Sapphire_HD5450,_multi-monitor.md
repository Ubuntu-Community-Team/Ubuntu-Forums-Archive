---
title: "Sapphire HD5450, multi-monitor"
date: 2013-09-29
forum: Ubuntu, Linux and OS Chat
---

### Post by SteveHillier on 2013-09-29
I gave myself a headache last week.  
I decided to upgrade my computer with an AMD Bulldozer 8120 processor, new motherboard, new HDD and RAM but keeping my old graphics cards.
Thought I should upgrade to 13.04 so I installed, copied my data and so on and I was ready to attach my monitors.
If you followed my thread last year [http://ubuntuforums.org/showthread.php?t=2042265](http://ubuntuforums.org/showthread.php?t=2042265) then you will note that I attach 4 monitors to my computer and the last post in the thread gives you what I did to make them work.
So gaily following my own work I downloaded the drivers from AMD and installed them and I got a message on my screens saying I had unsupported hardware.  This I tracked to my graphics cards.  I have 2 x Sapphire HD5450 cards which give VGA and DVI-I output.  I have no monitors that accept DVI input.
So I did another full install of 13.04 but this time I downloaded a backlevel version of the drivers from AMD - go to their site directly - do not use apt-get.
In trying to get the monitors configured I kept finding my user output crippled.  No output other than what was on the desktop.  No task launcher. Then I broke X11 altogether and could only get command line access.
So another full install and more attempts and then a lucky happenchance.  On boot I had a list of about 10 Linux Kernels to run from so I used a back level kernel and booted.  But unexpectedly I booted from my old hard disk which was still in my machine following data transfer.  It worked.  My screens were still configured.
So I took out the new disk with the new installation and I am running 12.04 good as gold.

Now the interesting thing is this.  I have changed from a 4 core processor to an 8 core processor.  I have changed the motherboard with all the bits on it - chipset etc.  And Ubuntu worked without the need to re-install everything.  I cannot imagine Windows ever doing something like that.
All power to the God that is Linux.

---

### Post by mörgæs on 2013-09-30
Not a support question, so moved.

---

