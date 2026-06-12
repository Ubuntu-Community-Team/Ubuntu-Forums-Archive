---
title: "newApplications &amp; newFavourites"
date: 2007-04-23
forum: Ubuntu System Panel
---

### Post by Quikee on 2007-04-23
Hello..

I have created 2 plugins, which are a replacement for "Applications" plugin, which is actually the "center" of USP.

[LIST]
[*]"NewApplications" plugin is a search/browse plugin through applications and additionally settings and files (through Tracker and maybe Beagle - however it is not functional in this release).

The additional functionality is also a smarter "search" entry field, which can also do other things depending on what you write in it:

[LIST]
[*]"$<command>"  will execute the <command> - for example: "$gedit" will start gedit. 

[*]"$$<command>" will execute the <command> as super user - for example:"$$gedit" will start gedit as super user (it will execute gksudo gedit)

[*]"=<expr>" will evaluate the expression - for example: "=1+1" will calculate 1+1 and write the result into the entry field.

[/LIST]


[*]The second plugin is "NewFavourites" which is a placeholder for favourite applications, settings and files (and possibly something else in the future). 

[/LIST] 

This is the early "alpha" release of the plugins so they might be unstable and not containing all the functionality planned.

Any suggestions are welcome...

---

### Post by delfick on 2007-04-23
cool :D

unfortunately i don't have time to test it now, but i will later :D

---

### Post by Quikee on 2007-05-21
OK I have been working "hard" for the last couple of weeks and it is time for a new newApplications and newFavourites release. 
Both have been rewritten completely (that's why newApplication is newApplications3 and newFavourites is newFavourites2) with a more modular structure. 

Both plugins don't depend on any width/height setting to make them more correctly displayed in various scenarios. The only setting is the "number of character" setting for left "menu" buttons (currently non adjustable).

The new release brings drag and drop support. You can now:
- drag items from newApplications and drop them in newFavourites (including files found with Tracker).
- drag applications from "usual" gnome menu and drop into newFavourites.
- drag (local) items from nautilus and drop into newFavourites.
- drag tabs/pages from firefox/epiphany and drop into newFavourites.
Other combinations might also work.

Both plugins are dependent on menu-xdg, python-xdg and xdg-utils packages which they use instead of gnome or "usp" own solutions. 

If agreed, applicaiton, favourites and shortcuts plugis will be replaced by those to in the future. 

Any suggestions are welcome!

---

### Post by delfick on 2007-05-22
cool :D

how do we use them ??

thnx

---

### Post by Quikee on 2007-05-22
> **delfick said:**
> cool :D

how do we use them ??

thnx

Sorry. Just put the content of the .tar.gz into ~/.usp/plugins/ and add "newApplications3" and "newFavourites2" as plugins in uspconfig or gconf editor. 

Also use the latest USP on svn whcih can automatically open usp when drag and dropping.

---

### Post by delfick on 2007-05-22
> **Quikee said:**
> Sorry. Just put the content of the .tar.gz into ~/.usp/plugins/ and add "newApplications3" and "newFavourites2" as plugins in uspconfig or gconf editor. 

Also use the latest USP on svn whcih can automatically open usp when drag and dropping.


ahhhh, i already tried that, but didn't have the capital letters......


i like them......though, can there be an easy option to import your current favourite apps to the newFavourites2 plugin ??

and can there be a possibility to have both plugins occupy the same space in the menu and just have a button to switch between them ?? (somewhat like what is now the case)

thnx :D

---

### Post by Quikee on 2007-05-22
> **delfick said:**
> ahhhh, i already tried that, but didn't have the capital letters......

i like them......though, can there be an easy option to import your current favourite apps to the newFavourites2 plugin ??


Yes.. it could check on startup if current favourite apps exist and add them but I won't currently do this as other thing have priority. =)

> **delfick said:**
> 
and can there be a possibility to have both plugins occupy the same space in the menu and just have a button to switch between them ?? (somewhat like what is now the case)


Yes I could do this but it was my intention to separate them. :D I am experimenting with "task" oriented design and newFavourites would be place holders for "tasks"  - each tab for a task. In each such "task" tab you would have only programs, files, links, whatever which you need to perform a task. For example a tab could be named "web browsing" and would have firefox or some favourite links to sites you usually begin "web browsing". Another example would be for example task named "usp development" where you could have "gedit" that automatically opens the usp soure code, "kdesvn" which automatically opens usp repository and scripts which executes "usp run-in-window" in a terminal window. 

On the other hand "newApplications3" purpose would only be to search for applications and files with which you could perform a task. 

I hope I was clear what I'm actually trying to achieve. I am generally more ore less experimenting with usability and I'm not nearly done yet. ;) 

Any comments are welcome.

---

### Post by delfick on 2007-05-22
> **Quikee said:**
> but I won't currently do this as other thing have priority. =)
no probs :D


> Yes I could do this but it was my intention to separate them. :D 

that's what i thought.....

a question to malac and chanders, is it possible to be able to make two plugins share the same spot in the menu, and give us the ability to easily switch between the two ??

> For example a tab could be named "web browsing" and would have firefox or some favourite links to sites you usually begin "web browsing". Another example would be for example task named "usp development" where you could have "gedit" that automatically opens the usp soure code, "kdesvn" which automatically opens usp repository and scripts which executes "usp run-in-window" in a terminal window. 

ok then... 


> I hope I was clear what I'm actually trying to achieve. I am generally more ore less experimenting with usability and I'm not nearly done yet. ;) 

ok then, that's cool :D

---

### Post by Malac on 2007-05-24
Hi delfick,
> **delfick said:**
> a question to malac and chanders, is it possible to be able to make two plugins share the same spot in the menu, and give us the ability to easily switch between the two ??That was sort of what the send to sidepane was meant to be. If you list the plugin in the same "newpane" and set the sizes the same they can be switched with two clicks. It may be possible to "tie" two plugins together so they work off one click. i.e. if "plugin1" is showing then "plugin2" minimizes to the sidepane, I'll add it to the requests for USP3 features. :)

Hi Quikee,
Nice work, I finally got a chance to try these.> **Quikee said:**
> I am experimenting with "**task**" oriented design and newFavourites would be place holders for "**tasks**" - each tab for a **task**. In each such "**task**" tab you would have only programs, files, links, whatever which you need to perform a **task**. For example a tab could be named "web browsing" and would have firefox or some favourite links to sites you usually begin "web browsing". Another example would be for example **task** named "usp development" where you could have "gedit" that automatically opens the usp soure code, "kdesvn" which automatically opens usp repository and scripts which executes "usp run-in-window" in a terminal window.I really like the idea of this plugin however as the above is the intention of "newFavourites2" plugin might I suggest you call it "tasks" as this is really a different concept than the favourites in applications. I could see that this could be used in addition to the favourites in the standard applications plugin rather than as a replacement.

The point of USP going to plugins was to separate out functions so that if you didn't need one on your system you could, not load that plugin. With "newApplications3" combining the applications and tracker plugins this sort of breaks this concept to me. So, and I stress, *for me*, I wouldn't want this to replace the original/standard applications plugin. However this is an open project so perhaps if you could give it a different name, not sure what :), then the user could choose whichever of the two suited their way of working. Then again chanders may feel differently and want to go with this concept.

Keep up the good work.

---

### Post by delfick on 2007-05-24
> **Malac said:**
>  I'll add it to the requests for USP3 features. :)

cool :D

*insert obligatory question about status of usp3 here :P :D*

---

### Post by Quikee on 2007-05-24
> **Malac said:**
> 
Hi Quikee,
Nice work, I finally got a chance to try these.I really like the idea of this plugin however as the above is the intention of "newFavourites2" plugin might I suggest you call it "tasks" as this is really a different concept than the favourites in applications. I could see that this could be used in addition to the favourites in the standard applications plugin rather than as a replacement.

Yes I wanted to rename the plugin to "Tasks" too.. but didn't yet done this as it is not "task oriented" yet. 


> **Malac said:**
> 
The point of USP going to plugins was to separate out functions so that if you didn't need one on your system you could, not load that plugin. With "newApplications3" combining the applications and tracker plugins this sort of breaks this concept to me. So, and I stress, *for me*, I wouldn't want this to replace the original/standard applications plugin. However this is an open project so perhaps if you could give it a different name, not sure what :), then the user could choose whichever of the two suited their way of working. Then again chanders may feel differently and want to go with this concept.

Keep up the good work.

Yes the "tracker" or better "general file searching" (waiting for freedesktop "xesam" specification and implementation) in "newApplications" might break the plugin concept. It all depends how you look at it - for me "Favourites" and "Applications" did break this concept when I looked from my perspective. I wanted "newApplications" to be a general "search"  plugin (or general selector for tasks) beacuse it made more sense to me than have x plugins all with x search capabilities (and only one of them gets the focus anyway). 

Maybe a lot better alternative would be that USP would handle the "search entry" and on "search entry" change it would notify "registered" plugins to act. This way applications, favourites, recent, shortcuts,... all could filter its entries. Maybe something for USP3? Could this be achieved as a plugin? (maybe plugins could register actions other plugins could trigger or something like that)

You should also check "helperFunctions.py" as much of what is there could easily replace the current in USP2 or even USP3.

---

