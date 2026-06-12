---
title: "GUI version of the command line (no, I definitely know what I'm talking about)"
date: 2018-12-10
forum: Ubuntu, Linux and OS Chat
---

### Post by freemedia2018 on 2018-12-10
When I were a lad, we didn't have the GUI. We didn't have hard drives neither.

It wasn't that bad really-- to run the graphical paint program, you had to type in its name. That's all. After a few times, you could do it faster than these kids with their fancy Desktop Environments can find and click an icon. Especially if DOS had included the ! shortcut that's in Bash. Then all you had to do was wait for the program to load. (Early versions of Firefox took longer to start in Windows than my paint program took to load from a floppy.) 

There was no framebuffer, just the hardware character drawing routines of the graphics adapter. 

The command line is a lot more friendly and powerful today. Bash is friendlier than the earlier proprietary UNIX versions. Some features are more complicated than the DOS counterparts, but you have many options. I've actually got my own shell that I designed to make the Windows command line more like the Bash one. 

```
find | isoname .txt | fsortplus | replace ":" "\n" | isoname " " | var t
```

That works in Ubuntu and Windows, too. Unlike WSL, it is running on the regular filesystem. I was just going to recommend UNXUTILS, but the last time I did it started installing a LOT more than it did when I used it. Mine is a single Python program. I'm not saying it's a good Bash replacement-- I only use it often, running Bash as much or more.

In Windows, find is translated to dir /b /a /s, isoname .txt is like grep "\.txt", fsortplus gives you two tab-separated columns of size/sha256/date/time and in the other column, the path and filename, replace ":" "\n" is like tr, isoname " " is like grep "\ " and | var t (which I really love) is like t=$(commands go here.)

This shell has no command substitution, it does loop through arrays: "forin v t ; cp $v foldername ; next" and it would be a lot nicer if I didn't try to make it work roughly the same in both operating systems.

However, a different route it could take would be to create Bash-like pipelines using a GUI instead of typing commands.

Take your favourite drag-and-drop language (I know, I'm not a huge fan either) and instead of drag and drop, just have some buttons for important tasks:

[ find ] [ reverse-line ] [ reverse-list ] [ isolate-lines ] [ remove-lines ] [ change-folder ] [ pipe-to-variable ] [ unpack-variable ] [ run-cmd-for-each-line ] [ run-command ] [ show-filelist-info ] [ isolate-file-types ]

Just to get you started. My own shell has features like "show output in rainbow colours based on indent-level or columns" but as fun as it is, it would be a lot better if it only targeted one operating system.

So for example, you could locate a file by selecting these buttons:

[ change-folder ] [ find ] [ isolate-lines ] 

When you selected change-folder, it would popup a dialog that let you select a folder from the usual tree/whatever or type in a path like / at the bottom. This box would then show in the window:

[ change-folder / ] 

When you selected find, it would let you option-select files and/or symlinks and/or folders. I know they're called "directories," dir was the first DOS command I learned, but "folders" is easier to type lots of times.

[ change-folder / ] | [ find -f -s ] 

When you selected isolate-lines, it would let you type in a box what you wanted to search for. You could select regex and type in a real regex, or by default it would just look for a substring (case-insensitive.)

[ change-folder / ] | [ find -f -s ] | [ isolate-lines -c -s s fox ]

So this is basically like:

cd / ; find -type fl | grep -i fox 

With two key differences:

1. it was composed using a method friendlier to people that love the GUI so much.
2. it can be used to teach the command line to people terrified of the command line.
3. because it maps to command line functions-- it can be used to do things that Most GUIs Cannot Do.

When you use a command shell, you can put features together in ways that a GUI designer would not anticipate. When I made my own shell, I let it mix native features with features from Bash. You can use tr instead of replace (but then the pipeline will not work in Windows.) You can "find | fsortplus | rev | sort" to find duplicate Names that differ in hash or filesize (I did not design fsortplus for that. But this is the nature of command pipelines, to have features even the designer didn't anticipate.)

Bash is a great introduction to programming concepts, but the syntax is a little wonky sometimes. Believe me, I appreciate its power. I wrote a small Logo interpreter in pure bash (ANSI output.) Because it has so many powerful features, it's not the most friendly environment for beginners-- And I still think DOS was very friendly. If it had more robust hardware support, I'd likely still be using it. 

So instead of:

```
cd / ; find -type fs | grep -i fox
```

You get: 

```
change-folder / | find -f -s | isolate-lines -c -s s fox
```

I understand that shorter commands are easier to type. I also designed a programming language inspired by logo, and I specifically chose typed commands over mouse-clicked ones-- I designed the language based on text, not GUI. Though the way it is designed, it would be very easy to make it into a drag-and-drop language. (Easier than most of the drag-and-drop languages, actually.)

Note that GNU find cannot do -type fl, it can do -type f or -type l but not both at once. 

After the program output too much, the user could then add [ isolate-file-types ] and select executable. This is a redundant design, because perhaps it belongs with the features of [ find ]

[ change-folder / ] | [ find -f -s ] | [ isolate-lines -c -s s fox ] | [ isolate-file-types -e ]

Now the GUI user is learning how to build command pipelines, and enjoying the power of both command line and GUI.

Maybe a bit of redundancy is alright. Maybe you could have a feature for [ find-program-files ]

[ change-folder / ] | [ find-program-files ] | [ isolate-lines -c -s s fox ]

Maybe you could "add user buttons" / shortcuts / scripts to it, so that the user could make their own [ find-program-files ] button to the program.

And then when it does locate /opt/firefox/firefox along with /opt/firefox/firefox-bin, you could just click on it (in the GUI output) and it would run it in the window. If you right click, you can select ("run without shell output / run with output in new shell window / tab")

Best of all, you could have a textbox at the bottom, so instead of telling users to "click this, select this" each button would map to a text command. So you could tell people:

"In the GUI-term, as user, run this command"

```
[ sudo ] | [ apt-get -install leafpad gdmap evince ]
```

And you are telling them what to mouse-click or what command line to run, at the same time.

Yes, I realise that sudo doesn't pipe to apt-get. And that it's apt-get install, not apt-get -install.

I tend to design smaller languages, with more consistent syntax. My favourite language goes strictly left-to-right, so mathphobes don't worry about parentheses.

Most lines start with a variable.

```
now "hello world" print
```

We can make coding a lot easier for beginners!

Just a reality-check-- I made my first wife a less elegant version of this GUI command shell, using standard Bash commands and Pygame. But I've created better shells since then.

In months, not years. By no means am I suggesting that we get rid of Bash or anything. I am suggesting we build a computing environment designed to make programming more accessible to everyone. 

That's the main thing I work on-- making coding friendlier. Bash is usable and Python is learnable, but until people realise that, we can give them some VERY powerful toys to play with. I have found that I use my "toy" version of Python/Logo more than I use Python itself. The main thing I use Python code for is creating other programmable interfaces than Python.

A GUI command shell like this wouldn't be the first thing like it, ever. Qt already has a term window that lets you click urls, I figure GNOME does too. In the days when I used Windows I made a wiki-inspired shell program that let you create links to scripts and then click them with the mouse. So clicking [[notes]] opened notes.txt and clicking [[*notepad]] ran notepad.bat-- but only if notepad.bat existed in a subfolder with the right name.

Not everyone would prefer this GUI term, of course. I mean I use that term window from LXQt, but I use xterm a lot more often-- it loads much faster and does what I want. I can open (and close) 5 xterm windows in less than two seconds, using Super-t-t-t-t-t CTRL-d-d-d-d-d, and I like that. That's a far cry from the days of loading programs from a floppy. But I would probably have at least one GUI-shell open, even if I still used xterm as a Run window.

---

