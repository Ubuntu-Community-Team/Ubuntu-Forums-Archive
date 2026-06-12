---
title: "Problem with excecutables"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bobman321123 on 2012-04-07
Ubuntu 12.04 seems to have a problem opening all executables......
How do I fix or figure out what's wrong with this?

---

### Post by na5h on 2012-04-07
Have you tried this? Right-click on the file-> properties -> permissions tab-> check the "Allow executing file as program" box.

---

### Post by bobman321123 on 2012-04-07
That doesn't work for me. 12.04 seems to have issues opening executables.

---

### Post by Toz on 2012-04-07
What kind of (Linux, windows) and which executables? Are you getting error messages? Where are the files located (hard drive, external drive, network)? 
It would be helpful if you could provide some more info.

---

### Post by cariboo on 2012-04-07
Your are running executables, any time you click on an icon, what particular executable are you having a problem with? If it's the same problem as in your other thread, I'll merge the two.

---

### Post by bobman321123 on 2012-04-08
> **cariboo907 said:**
> Your are running executables, any time you click on an icon, what particular executable are you having a problem with? If it's the same problem as in your other thread, I'll merge the two.

My other thread is about .desktop files not allowing me to click on them, this thread is about trying to run an executable directly, which doesn't let me. 

It's a linux executable, I'm running Ubuntu 12.04, and when I either double click the executable or go in terminal and write ./executable, it tells me I have no program to run an executable. 

And yes, before you say it, I'm VERY sure this is a linux executable, I had it working perfectly in 11.10.

---

### Post by cariboo on 2012-04-08
Could you tell us the name of this executable, or what it is supposed to do?

---

### Post by mc4man on 2012-04-08
> **cariboo907 said:**
> Could you tell us the name of this executable, or what it is supposed to do?
I'm showing this in his other post - the binary can not nor is it designed to be run directly.
The app uses a launcher script to run the binary

(when the app is installed it creates a Desktop launcher with proper permissions & sets the path to the app launcher script based on the location from where the app was first installed

---

### Post by bobman321123 on 2012-04-08
Could we please keep the two different posts separate?

The first post is about all my .desktop files not working.
I have about 10 of them, Desura is just one example.

THIS post is about a program called Sublime Text 2, whose executable refuses to run for some reason.

---

### Post by oldos2er on 2012-04-08
> **bobman321123 said:**
> THIS post is about a program called Sublime Text 2, whose executable refuses to run for some reason.

Did you download the correct bitness (32- or 64-) for your system?

---

### Post by cariboo on 2012-04-09
> **bobman321123 said:**
> Could we please keep the two different posts separate?

The first post is about all my .desktop files not working.
I have about 10 of them, Desura is just one example.

THIS post is about a program called Sublime Text 2, whose executable refuses to run for some reason.

What happens when you try to start the app from a terminal?

---

### Post by bobman321123 on 2012-04-10
> **cariboo907 said:**
> What happens when you try to start the app from a terminal?

If I try to run it as a regular user, ```
./sublime_text
```
I get a "you are not allowed to run this" message.
If I try to run it as sudo, it accepts it, but nothing happens.

---

### Post by bobman321123 on 2012-04-11
I've tried it on several different executables, including a few very simple ones I've compiled myself. My system is incapable of running excecutable files either by .desktop files or directly running via ./executablenamehere

@oldfred Yes, 64bit program, 64bit ubuntu.

---

### Post by cariboo on 2012-04-11
I just had a look at Sublime Text 2, I downloaded it, used file-roller to extract it (I just doubled-clicked Sublime Text 2 Build 2181 x64.tar.bz2) to Downloads. I then double-clicked the Sublime Text 2 icon, once in the directory I double-clicked sublime_text. I worked without a problem. 

The ownership in my case is my user - cariboo and permissions are 755

---

### Post by bobman321123 on 2012-04-11
> **cariboo907 said:**
> I just had a look at Sublime Text 2, I downloaded it, used file-roller to extract it (I just doubled-clicked Sublime Text 2 Build 2181 x64.tar.bz2) to Downloads. I then double-clicked the Sublime Text 2 icon, once in the directory I double-clicked sublime_text. I worked without a problem. 

The ownership in my case is my user - cariboo and permissions are 755

Yes, I've found that it's a problem with all/most executables, not just that one.

---

