---
title: "Crash Linux? np, hold this button for 10 seconds."
date: 2006-07-21
forum: The Cafe
---

### Post by Engnome on 2006-07-21
I noticed that pressing the calculator button on my new keyboard often started many calculators. So in the spirit of "lets see what happens" I held it down for about 5 seconds. The result is displayed in attached pic. So I closed them down and decided to see how many calculators I could have runnning before something interesting happens. (note: after closing all those calculators there was still an extra 100mb in ram more normal:confused: ) So I held it down for 10 seconds. many calculators started; and when they seemed to have stopped plopping up I tried to start the system monitor. No success. Had to force reboot, haven't done that for quite some time so that was an reminder of what I had left. Think I'm gonna map that key to do something else...

Weird that something as simple as this can crash yours OS,

[QUOTE= Douglas Adams]A common mistake that people make when trying to design something completely foolproof is to underestimate the ingenuity of complete fools. ~ Douglas Adams[/QUOTE]

Maybe I should file a bug report:-k 

So how many calculators do you think it will take to crash your system?:p 

Note: I have 512mb ram and 300mb swap.

---

### Post by Lord Illidan on 2006-07-21
I would have tried to go to the console, CTRL + ALT + F1 , logged in, and did a quick

killall nameofcalculatorexecutable

or else CTRL + ALT + BACKSPACE and killed X. Probably would work.

---

### Post by Engnome on 2006-07-21
> **Lord Illidan said:**
> I would have tried to go to the console, CTRL + ALT + F1 , logged in, and did a quick

killall nameofcalculatorexecutable

or else CTRL + ALT + BACKSPACE and killed X. Probably would work.

Ctrl + alt + backspace didn't work. Neither did the other.

---

### Post by Lord Illidan on 2006-07-21
Ok...Then I would have..............pressed the restart button...:D

---

### Post by erikpiper on 2006-07-21
I doubt he has a restart button... Havent seen one of those on a prebuilt in a LONG time.. Mine has one, but I built it....


LOL


That is pretty interesting...

---

### Post by bruce89 on 2006-07-21
> **erikpiper said:**
> ...Havent seen one of those on a prebuilt in a LONG time...
What, and they ship windows?  The reset button is required for any computer running windows.

---

### Post by Horizon on 2006-07-21
> **bruce89 said:**
> What, and they ship windows?  The reset button is required for any computer running windows.
I think he is talking about those cases that have a power button and also a little button that "resets"(restarts) it. Does anyone actually know if and why that button is useful? They obviously stopped putting these on computers for a reason :-k. Even when I had one I never, ever, used it so I wouldn't know how useful it is...

---

### Post by djsroknrol on 2006-07-21
> Does anyone actually know if and why that button is useful? 

I thought there were 2 reasons Horizon...

1) To mess with people

2) To make them "kidproof"

The 2nd reason worked well for me...kept the curtain climbers off of my rig...;)

---

### Post by Randomskk on 2006-07-21
My case has one (although the computer isn't pre-built, I made it) and I use it all the time when linux freezes up.
It's quicker than holding down power for 10 seconds, then pressing it on again, plus a hot reboot tends to be quicker than a cold one.

---

### Post by Kimm on 2006-07-21
Its not at all strange that the computer crashes after having too many apps open, after all they all need memory.. memory that the system need to function.

---

### Post by Skia_42 on 2006-07-21
All in the pursuit of knowledge...I don't think there is really any bug to report. It's like when a child complains that his neck hurts after he rotates his head more than 90 degrees. The simple soultion is to not do it.

---

### Post by bailout on 2006-07-21
> **bruce89 said:**
> What, and they ship windows?  The reset button is required for any computer running windows.

I have one on my pc and can't remember using it with windows as I can't remember windows crashing since I went to XP. I have had to use the restart button several times with linux though ;)

I think the advantage with the restart was that it rebooted without stopping and restarting the drives and maybe some other hardware.

---

### Post by erikpiper on 2006-07-21
> **Horizon said:**
> I think he is talking about those cases that have a power button and also a little button that "resets"(restarts) it. Does anyone actually know if and why that button is useful? They obviously stopped putting these on computers for a reason :-k. Even when I had one I never, ever, used it so I wouldn't know how useful it is...


Well, it is better than the power button method.. And motherboards still come with the connections!

---

### Post by Engnome on 2006-07-21
> **Kimm said:**
> Its not at all strange that the computer crashes after having too many apps open, after all they all need memory.. memory that the system need to function.

Memory wich a good OS wouldn't give them! The OS should just say No! no more I'll go down in flames! Someone told me the kernel wouldn't give memory when it had to little so I thought I was relatively safe. This is almost like a fork bomb and is easy to set off if you find an unguarded computer.

> All in the pursuit of knowledge...I don't think there is really any bug to report. It's like when a child complains that his neck hurts after he rotates his head more than 90 degrees. The simple soultion is to not do it.

Maybe, of course if you do sudo rm /home you only have yourself to blame as you have to give security clearence but this is so easy! I set of by mistake! (honestly didn't think my session would go fubar) Thats why this shouldn't be possible, I mean if you turn your head to much something stops it, you  *can't* turn it so much that you would inflict seriuos damage onto yourself (without using your hands wich is like saying *sudo* suicide)

---

### Post by slimdog360 on 2006-07-21
I just thought Id say that winXP only lets you open it once, it recognises that you have it open and wont open another calculator. Perhaps this is something which could be used in Ubuntu.

---

### Post by Skia_42 on 2006-07-21
Oh whats the fun in that, part of the reason Ubuntu is so fun is you can dig yourself a nice neat little hole and then spend a week crawling out...

---

### Post by Horizon on 2006-07-21
> **slimdog360 said:**
> I just thought Id say that winXP only lets you open it once, it recognises that you have it open and wont open another calculator. Perhaps this is something which could be used in Ubuntu.Except that there are plenty of reasons I might want more than one calculator open. One of which being that ubuntu supports multiple desktops. Which means I can leave things I was doing and do other things...other things which may include the use of a calculator as well. XP isn't exactly known for making multi-tasking easy...

In terms of how the application is used, saying the calculator should sense when one is already running and refuse to launch is like saying if I have an instance of a text editor (that doesn't support tabs) open it should refuse to open a new window...the word ridiculous comes to mind :mad:](*,)

---

### Post by palintheus on 2006-07-21
> I just thought Id say that winXP only lets you open it once, it recognises that you have it open and wont open another calculator. Perhaps this is something which could be used in Ubuntu.

I can open more than one calculator in XP....I have never ran into an issue with having more than one instance.

---

### Post by slimdog360 on 2006-07-22
true true, I can see why if someone wants more than one calculator open it could be a problem. To palintheus that doesnt look much like XP but if it is opening more than one calculator for me was impossible, at least by pressing the button on the keyboard to open it. I never tried to open it by any other means.

---

### Post by slimdog360 on 2006-07-22
here mine, I was able to open 200 calculator with no problems.
[IMG]http://img156.imageshack.us/img156/6561/screenshot1we3.png[/IMG]

---

### Post by TravisNewman on 2006-07-22
my wife: "How many times do you get to see someone crash a PC with a calculator?"

---

### Post by palintheus on 2006-07-22
> **slimdog360 said:**
> To palintheus that doesnt look much like XP 

I use the classic windows theme, I just think it looks cleaner.

---

