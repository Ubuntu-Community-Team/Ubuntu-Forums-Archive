---
title: "&quot;.translation&quot; files randomly appear on desktop and in some folders"
date: 2023-08-06
forum: Security
---

### Post by mikjosjon on 2023-08-06
I started up my computer tonight to see twice as many files on my desktop as usual - half of them ".translation" files.

They seem to be extracted from .csv spreadsheet files, with each translation file corresponding to a column in the source .csv file. For example. if I have a .csv spreadsheet "spreadsheet.csv" that contains columns with the first cell in each named "column1", "column2", and "column3" respectively, there will be translation files "spreadsheet.csv.column1.translation", "spreadsheet.csv.column2.translation" etc. 

There are other folders that contain .csv files and now also have corresponding translation files for each. I haven't swept through the whole computer to see if every .csv has been "translated", but I'm assuming that is the case.

My first thought was that I might be the victim of some sort of ransomware attack, but then I noticed that all of the original .csv files are still present, intact, and readable. 

Has my security been compromised? Fortunately, none of these files contain any critical information that will lead to my identity being stolen or my accounts being hacked. But now I'm concerned that my computer in general might be compromised.

Should I be concerned? Is this the result of some sort of virus or malware, or is it just some fluke? The timestamps on the files suggest they were created last night about the time I would have been shutting my computer off or maybe a little bit before.

---

### Post by Rubi1200 on 2023-08-07
Hi and welcome to the forums :-)

I've been racking my brains thinking about this one and I am, quite honestly, stumped. I can find little or no evidence online for such an odd occurrence with the .translation file extension.

So, here are some questions and things to look at that might help narrow this down.

1. is this a dual-boot with Windows or Mac and do you use some kind of file-sharing between operating systems?
2. if you use Windows have you run a malware scan?
3. have you recently installed any applications that might have messed up some configuration files?
4. have any language or localization settings been changed recently?
5. do you have any cron jobs scheduled that might unintentionally be creating these extensions?
6. have you recently updated/upgraded the system?
7. have you checked log files to see if there is any unusual activity?
8. do you have inotifywait installed? If not, I would install it and run this command to see if it helps discover what is going on:

```
inotifywait -m ~/Desktop
```

I hope this in some way helps you move in the right direction.

---

### Post by mikjosjon on 2023-08-08
1. It is dual boot. No file sharing.
2. I can't recall if I've scanned Windows or not. However, I am aware of how vulnerable Windows is, so if I'm going to do anything remotely risky I do it in Ubuntu. I mostly only use windows for steam gaming - and that is even pretty rare now that steam games can (mostly) run in linux.
3. No.
3. No.
5. No.
6. Apparently I'm 3 versions behind at 20.04.6. Hmmm... I know I was overdue for an upgrade, but I didn't realize I had fallen this far behind.
7. Which log files should I check? What am I looking for?
8. No. I will try this, though it won't really help me to figure out anything about the .translation files that were already created. 

**A BIG IMPORTANT NOTE**: with a little more digging, I realized that the translation files are secondary to corresponding .import files for each .csv!
Here's an example of what one of these files looks like:

> 
[remap]


importer="csv_translation"
type="Translation"
uid="uid://bctddxkru3h58"


[deps]


files=["res://Desktop/csvfilename.column1.translation", "res://Desktop/csvfilename.column2.translation"]


source_file="res://Desktop/csvfilename.csv"
dest_files=["res://Desktop/csvfilename.column1.translation", "res://Desktop/csvfilename.column2.translation"]


[params]


compress=true
delimiter=0


Have you ever seen anything like this? Google is turning up nothing that seems relevant. 

Also, this forum seems pretty dead and I hope to get more eyes on this post to increase the likelihood of finding an answer. Would it be appropriate for me to copy/move this thread to one of the support forums or something?

---

### Post by mikjosjon on 2023-08-08
I may be getting somewhere...

[https://github.com/godotengine/godot/issues/80096](https://github.com/godotengine/godot/issues/80096)

This is the first result to come up when I google:

> "compress=true" "delimitter=0"

I still don't entirely know what this is about, what purpose these import files serve or how I even create them from within Godot, but I DO use the godot game engine and I likely opened it the night, even the time, these files were generated.

at this point it seems overwhelmingly likely Godot is the culprit somehow, though why it would have created import files for every .csv on my system is beyond me as I definitely never intentionally did anything remotely related.

I'm scratching my head at this point, but at least I'm somewhat confident this isn't the result of Malware at this point. Godot is open-source and community developed and it has it's little bits of jank and bugs here and there, so I'm guessing this is just some crazy bug I triggered somehow.

---

### Post by Rubi1200 on 2023-08-08
I'm not a security expert but I would agree that it seems likely you encountered/triggered some kind of bug. I would suggest following up with the developers over there to see if they have a fix/solution to clean things up.

By they way, the Security sub-forum tends to be more quiet than others mostly because questions asked here are often very specific and not all users have the knowledge to answer.

I only answered because I found the whole thing rather curious and wanted to see if I could help get you moving in the right direction (which I hope has happened).

---

### Post by mikjosjon on 2023-08-08
I solved it.

I was correct that Godot did this, however it was not a bug *per se*; more like a design flaw that allows users to do something in contexts where it makes no sense to do it.

Godot allows users to import project files with the extension ".godot". When you first open Godot, there are options to create new project, **import new project**, etc. When you click "import project", it spawns a popup with a text field to enter the path to the file you want to import.

By default, this directory is your home directory. And when you import a ".godot" file, Godot imports not only the project file but the *entire filesystem structure within the folder the .godot file is contained in, including all subfolders; *And, you guessed it, when it imports ".csv" files it creates these .import and .translation files, too. 

The real important point here is that you don't actually have to specify a .godot file; you an just point to a directory that *contains* one of these files.

It just so happened that I had a .godot file in my home directory, so godot considered my home directory a valid filepath to import a project from. 

So basically, all you have to do to be a "victim" of this "hack" is open godot, click "import project", and hit enter.

This has to be what I did. I don't remember specifically doing it, but I can easily see how it would have happened, as I do recall absent-mindedly opening godot when I meant to open VSCode. I was a bit distracted so I probably also absent mindedly hit "import" and just clicked or pressed enter through the screens without paying attention. Just like that, every .csv file in my home directory got "translated" and my home directory is now polluted with these extra useless files that I get to go through and clean up. I created a small test directory containing a .godot file and a sub folder which itself contained a csv file and verified this same behavior by importing that directory into godot.

It's a minor inconvenience and entirely my fault when it comes down to it. It probably would be wise for the godot contributors to require you to specify a .godot file instead of just a directory in order to prevent others from having to mop these garbage files up from their system, but its nothing system-breaking or dangerous.

---

### Post by Rubi1200 on 2023-08-08
Glad to hear you solved it!

Please mark the thread Solved using Thread Tools at the top of your first post. This way, anyone encountering the same problem will know how to resolve it.

---

