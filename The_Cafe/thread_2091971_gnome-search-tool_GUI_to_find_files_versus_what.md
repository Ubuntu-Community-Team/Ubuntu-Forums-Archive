---
title: "gnome-search-tool GUI to find files versus what?"
date: 2012-12-06
forum: The Cafe
---

### Post by sdowney717 on 2012-12-06
I wonder why this GUI search tool is not automatically included in the install?

What do experienced people use and what do newbies use seeing they would like this and dont seem to have anything else to do searches in a friendly manner?

I recently installed 64bit ubuntu and was really in some trouble trying to find this good working GUI search utility.
I had it installed in my 32 bit version for years and did not even think it is not part of the install.

---

### Post by monkeybrain2012 on 2012-12-06
Good question. I use the terminal for search, but what do they expect from new users? By the way, to use the gnome search for files you have to disable quick search for some reasons, otherwise it won't find anything even if you are staring at it on the desktop.

Also to use locate in terminal you need to "sudo updatedb" first or it wouldn't find anything between two automatic update of database. You usually don't find this advice from people who tell you to use the terminal. I was pretty frustrated for not being able to find things before I learned this.

I hope they put some work in fixing these oddities so that new users wouldn't think that Linux is so bad that it can't even find files.

---

### Post by sdowney717 on 2012-12-06
yes, it works decently. The drive to search must be mounted first even if it shows up in the gnome search tool list. So I use file manager to click on the drive, then do a search.

I just found all our old jpg files off an NTFS drive and moved them.
26,000 found in 30 seconds

---

### Post by monkeybrain2012 on 2012-12-06
> **sdowney717 said:**
> yes, it works decently. The drive to search must be mounted first even if it shows up in the gnome search tool list. So I use file manager to click on the drive, then do a search.

I just found all our old jpg files off an NTFS drive and moved them.
26,000 found in 30 seconds

Of course the drive has to be mounted. But your files are there before. Now let's do an experiment, move a file to the desktop or create one (it is not on the desktop before). Try search for it without rebooting. It never works for me unless quick search is disabled through gconf-editor.

---

### Post by sdowney717 on 2012-12-06
worked, it found it

I created an empty file in the Desktop folder called 'searchtest'

Then immediately did a search and it shows up

---

### Post by monkeybrain2012 on 2012-12-06
Weird. It never works for me unless I disable quick search.

---

### Post by sdowney717 on 2012-12-07
I decided to look at this some more. 
Installed that conf utility.
Disable quick search is not checked.

In the years I have used gnome-search-tool It has just worked for me without doing anything special.

---

### Post by blackbird34 on 2012-12-07
Control+F in Nautilus seems to search pretty well, including searching for filetypes (e.g. typing in ".mp3" without quotes in a music folder). I like that better than the standalone Gnome tool.
Otherwise I also use Recoll, Synapse and the Unity dash of course.

---

