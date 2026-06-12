---
title: "Project 64in wine: gamingwindow dissapears somewhere after choosing game"
date: 2009-07-08
forum: Wine
---

### Post by rusma on 2009-07-08
Hello! 

Previously today the N64 emulator 'Project 64' was running Ocarina of Time just fine on my Lenovo laptop (Ubuntu 9.04) under wine. Here is my problem now: 


[LIST]
[*]I start Project 64 in Wine
[*]The applications main window turns up as before
[*]I choose a game
[*]the window disappears so the gaming window can turn up instead
[*]but, it never shows up
[*]I can hear the music though (Eponas hooves:)) and I can see Project64.exe in the list of processes, so i suppose the window is just "hidden" or something.
[/LIST]
What to do? 

It is not present on the other desktops.

* Sorry, typing errors in header too...

---

### Post by cogadh on 2009-07-08
This doesn't really address your problem, but is there a specific reason you need to use an emulator through Wine and not a Linux native emulator like Mupen64Plus? More often than not, it is better/easier to use a native app instead of a Windows app through Wine.

---

### Post by rusma on 2009-07-08
> **cogadh said:**
> This doesn't really address your problem, but is there a specific reason you need to use an emulator through Wine and not a Linux native emulator like Mupen64Plus? More often than not, it is better/easier to use a native app instead of a Windows app through Wine.

I've already tried mupen64plus, but found that the Rice plugin refused to work, and Glide64 just works for some time and then gives a fps of 0 and uses up all system resources. This thread is for one computer. I've gotten mupen64plus to work on [another machine]("http://ubuntuforums.org/showthread.php?p=7582601"), but have some other problems there :)

---

### Post by rusma on 2009-07-10
It did not recover after a few reboots either. I find it very strange. It is like the whole application is disappearing behind a curtain or something..

---

### Post by rusma on 2009-07-11
Got tired and just purged wine from synaptic, and deleted ~/.wine. Reinstalled project 64 1.6, and now it is not hiding in the background anymore. 

Of course this was not the best solution, but it works.

---

