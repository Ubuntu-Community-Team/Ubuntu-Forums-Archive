---
title: "DropIt alternative for Linux"
date: 2020-06-18
forum: Ubuntu, Linux and OS Chat
---

### Post by hanngrand on 2020-06-18
Hi guys,

I need alternative to the opensource app for Windows DropIt for Ubuntu.

Tried "organize" script but the disadvantages are there is no option to move folders to another folder, for example:

Main Folder
   - Subfolder
       - Movies Folder
       - Files Folder

There is no rule for moving "Movies Folder" and "Files Folder" to "Main Folder (or I'm not aware how).

If you could recommend something it will be a life-saver!

Thanks in advance !

---

### Post by TheFu on 2020-06-18
I use a combination of bash scripts and **inotify** for workflow management.   No GUI, sorry. GUIs don't work on servers, shell does.

I checked out 'organize'. If it only works with extensions, that won't work for me.

My rules use simple patterns for specific input files and I manually run the script.  inotify launches a script to process a file when it shows up in a specific directory. When that processing finishes, the file is moved up 1 directory. I do some manual processing then run another script to place the finished files in specific locations on another system. This handles movies, TV shows, videos, photos and some other stuff.

I looked at DropIt a bit. The code is all autoit3 scripts.  AutoIT is Windows only. My quick search for a Linux tool that would handle those scripts failed. Sorry.

---

### Post by hanngrand on 2020-06-19
> **TheFu said:**
> I use a combination of bash scripts and **inotify** for workflow management.   No GUI, sorry. GUIs don't work on servers, shell does.

I checked out 'organize'. If it only works with extensions, that won't work for me.

My rules use simple patterns for specific input files and I manually run the script.  inotify launches a script to process a file when it shows up in a specific directory. When that processing finishes, the file is moved up 1 directory. I do some manual processing then run another script to place the finished files in specific locations on another system. This handles movies, TV shows, videos, photos and some other stuff.

I looked at DropIt a bit. The code is all autoit3 scripts.  AutoIT is Windows only. My quick search for a Linux tool that would handle those scripts failed. Sorry.

Thanks for the reply!

I did try "organize" and it is working for my needs, kind of. Biggest issue is that I cannot find a bash command that organize deep layers of subfolders into folders, for example:

```
Main
|
Videos
             |
             Sub Video Dir 1
             |
              Sub Video Dir 2
                                           |
                                           Another video folder
```

And I would like to move "Another video Folder" " The two subfolders" "Videos" into" "Main" (Main is not home), Without touching the files in the folders.

I guess this is some kind of bash script but cannot figure it out.

Although "DropIt" does not do it automatically it is absolute gem, when I open "tree structure" of the file browser and use it as "drag and drop". Saved me so much time ...

Anyway, I did the search too - nothing even close for Linux, so if someone figure it out for himself, will be much appreciated - I'm about to organize 10TB manually :(

---

### Post by TheFu on 2020-06-19
> Without touching the files in the folders???

Some basic file system knowledge is needed here.  

Every file system object has a parent (except the / directory which doesn't have a parent).  An "object" is a file, directory, hard link, symbolic link, named pipe, fifo, shared memory and a few other types.  For 99.999% of our needs, file and directory and links are it.

When the parent gets moved, any "child objects" get moved with it. Within the same file system, moving is nearly instant, since it is literally just changing 1 tiny record for the parent and updating the parent with a new child.  Have you ever heard that "on Unix, everything is a file or a process?"  That's true.  If it doesn't show up in the process table (see top or htop), then it is a file. Files are files. Symbolic links are files. Directories are files.  You can actually use a text editor on a directory "file" if you want, but we shouldn't since that's a good way to orphan the children objects and never be able to access them again.

Moving to a different file system is implemented as a _copy+delete_.  In the old days, moving to a different file system wasn't supported and we manually did the cp -r then manually deleted the source files.

So ... if you _move_ "Videos" into "Main", you get all the children files and directories with that 1 "object" change.  If that is your desire, fantastic.  
But if you really just want to copy the directory structure without any files from "Sub Video Dir 1" to "Main", then that is NOT a move. That is more of a directory clone without files. With this specific knowledge, would you try to describe what it is you want again please?


BTW, if you have files and directories with spaces or {}[]() in the names, any bash scripting will be significantly more complicated. Bash treats a space as a delimiter by default, so you'll need to quote all filenames and all directory names carefully, every time. For non-trivial scripts, that isn't easy.  I specifically remove spaces and special characters from all files on my systems just to avoid that problem.  The different parenthesis also have special meanings inside bash, so I remove those whenever a new file gets created too.  Scripting without those things is 1000x easier.

I should say that I'm not a GUI user very much.  For me, my workstation GUI is about having an easy way to manage terminals. Right now I have about 20 windows open. 16 of those are terminals on different systems. The 4 others are firefox, claws, an alarm-clock and handbrake. I work from the terminal most of the time. It is much quicker for me. I use bash globbing a bunch, so moving hundreds of directories isn't a big deal. The mouse careful select, cut+paste doesn't work for me. Much too slow.

Most media center programs require a similar structure
[LIST]
[*]/data/Movies
[*]/data/TV
[*]/data/Videos
[*]/data/Pictures
[/LIST]

Eventually, you'll need to add more, so
[LIST]
[*]/data/M2
[*]/data/TV2
[*]/data/V2
[*]/data/P2
[/LIST]
It is tempting to think we need to move all the TV shows to a new HDD and consolidate the Movies onto 1 disk, but that isn't needed.  Media Center programs know that we'll have 5 different Movie directories and will merge those into a single view.
My exact setup is:
```
$ tree -d -L 2 |more
.
&#9500;&#9472;&#9472; D1
&#9474;** &#9500;&#9472;&#9472; ebooks
&#9474;** &#9500;&#9472;&#9472; M
&#9474;** &#9500;&#9472;&#9472; Photos
&#9474;** &#9500;&#9472;&#9472; R
&#9474;** &#9500;&#9472;&#9472; T
&#9474;** &#9500;&#9472;&#9472; V
&#9500;&#9472;&#9472; D2
&#9474;** &#9500;&#9472;&#9472; M2
&#9474;** &#9500;&#9472;&#9472; R2
&#9474;** &#9500;&#9472;&#9472; recoll-index
&#9474;** &#9500;&#9472;&#9472; T2
&#9474;** &#9500;&#9472;&#9472; V2
&#9500;&#9472;&#9472; D3
&#9474;** &#9500;&#9472;&#9472; M3
&#9474;** &#9500;&#9472;&#9472; R3
&#9474;** &#9492;&#9472;&#9472; T3

```
We keep R-rated movies separate so the kids don't see it on the main Kodi player. The sub-directories like M3 really don't need the numbers. Next time I probably wouldn't bother.  The recoll-index is there because I've setup Recoll to index all the files on that system daily. Recoll is like our own internal google search. It reads all the metadata from the files and makes finding stuff instant, though we also have PlexMS and **locate** to search for files too.

Hopefully, something above is useful to someone.

---

