---
title: "File -&gt; Quit"
date: 2007-09-30
forum: The Cafe
---

### Post by Mr. Picklesworth on 2007-09-30
I can't be alone in this hatred I have for the File menu, which is, in my opinion, a key part in one of the biggest blunders of GUI design...

Firstly, Quit. Does anybody actually use the Quit option? Really?
There are a few programs where this is necessary. A *very* small number. These are programs that do not directly deal with documents; photo managers, configuration tools...
Problem 1: Regardless of how unnecessary (and stupid) it is to include the Quit option, I see it in programs such as text editors and word processors.
Problem 2: Even in that second set, where Quit *could* make sense, it is redundant! Closing the window quits the program whenever the window represents the program. (That is, practically any program which is not dealing with "documents").
Problem 3: Quit sounds sharp; like I am abandoning something, unfinished. I would rather my computer *not* accuse me of this.

In the GNOME Human Interface Guidelines, the Notification Area is not to be used as a mini task list, but as (*gasp*) *a notification area*, where, if something is actually *happening*, a notification can appear there. I think that makes sense; if somebody wants a program to get out of his way, he will move it to another workspace or minimize it. If I click "the X", I expect whatever that window is dealing with to be gone - crossed out - nill - void!
When I close a window, I certainly do not expect it to be resurrected in the notifcation area.

This is really quite simple: A window represents a document. We can probably agree on this (assuming the bubonic plague -- tabbed interfaces -- never occured). When all the documents are closed, the program closes. The joy of this? You don't have to think about the program. You should *never* have to think about the program! That is the whole point of this. That is why the file manager and your web browser, in the title bar, do not proudly display their own name, but that of what they are displaying. That is why a desktop environment uses a consistent user interface toolkit; so that programs feel similar, and so that data glides between them, like water, thanks to interfaces like drag & drop.
I really like using the Epiphany browser, because it knows when to go away. I close tabs and windows using File -> Close (it Does Not offer "Quit"), and when I have closed everything, it quietly goes away and lets me go about my business. I do not need to *think* about Epiphany. For all I know, it's a different browser. (I know that it is Epiphany, though, since most other browsers I have installed do not follow this elementary bit of interface design).

As soon as a program adds Quit, it is breaking from that design. It is needlessly complicating matters by treating each document (each window) not as its own entity, but as a segment of a program. When the user hits Quit, every document closes. This is illogical; they were opened at different times, they should not close at the same time. Everything that uses Files should have Close, but *never* Quit.

What really gets on my nerves here is not just how redundant the whole Quit / Close thing is, but where these options - among others - are placed. *The menu* -- and not just that: The File menu!
As an example, today I decided to try a BitTorrent program called Transmission. (Neat little program, by the way). At the top, it has a single word: "File". Under File, there is a single file-related operation: Add. This menu, however, contains: "Add, Start, Stop, Remove, Properties, Open debug window, Preferences, Close, Quit."
No, not even "Close" is related in that same respect; it Closes the window. (A landslide of interface design absurdity). Quit? Oh, that closes the window too, but it doesn't resurrect it in the Notification Area.
Why must the File menu exist? Hell, why must the menu exist as such a key element? It seems that the thinking is some kind of unfounded childish jealousy, along the lines of "that program has one, so I should, too!" even when it is unknown what this menu even does for that other program. Program Preferences are not related to a File. According to the metaphor so carefully suspended by the file's content type, it is not even a "file", but a torrent! It is the *torrent* which we are adding, stopping, removing and viewing the properties of. It is the *program* for which we are editing User Preferences, whose debug window we are opening, and which we are Closing.

Program menus are worse than [mystery-meat navigation](http://en.wikipedia.org/wiki/Mystery_meat_navigation).
Yes, worse.
With mystery meat, there *is* no hope of better; there never was. It is consistently a nightmare. These program menus could be made better by a few trivial little changes that are in no way difficult (or even time-consuming):

Get rid of the Quit / Close confusion! Nobody understands this. It makes even less (read: No) sense when Close and Quit are both in the context of "File". A single file cannot be "Quit", but it *can* be Closed. Quit means nothing in that context, and if it had to mean something, it would mean the same thing as Close.

Program menus are worse than blindness! Help files work. Google works. People actually check these to find guides that effectively instruct them to go through menus and click a button. Why can't we just skip the middle-man, have the menus act like Google or the help file? That is, make them searchable, organized into sectors by *what they do*.
If not that, at least, for the love of God, make them readable. "File" and "Preferences" are simply not enough information. Check your nearest word processor, without the blindness to its stupidity which you have gained over the years, for even more horrifying examples. Use titles that make sense, and use menu items more than a word long. There is a lot of space on the screen! These menus are compressed into expanding boxes for a reason: So that they can be *big*. So, make them big! There is a lot of space here, and the menu is not going to consume that space until it is opened. Make it descriptive; make it useful. Don't be afraid to have menu titles that other programs do not use; every program is a program that other programs are not, so of course it'll be different. Just because one program has a File menu doesn't mean another should even when it really does not suit it.
Mac OS's 'unified menu bar at the top' design does at least one thing right, and that is the "program name" menu. This menu has stuff specific to the program: Program preferences and Quit, for example. That, finally, makes sense. When I Quit the program, I am not quitting the *file*; I am quitting the program! This makes it quite clear what Quit means, and that - as with everything else in the "program name" menu - the effect of that selection is global.

Another one that gets on my nerves is "Edit -> Preferences". Why would Preferences be in there? Edit describes editing stuff; it is a verb. That is illogical enough as it is, since most other menu titles are nouns; they describe *things*, or scenarios, with the choices inside them being actions, or resolutions. Edit is an action on its own, so it reverses the pattern. By this, anything that has anything to do with Editing something could be in that menu! In other words, anything that does *anything* should be in the Edit menu. Saving a file is an action of Editing data, opening a file is a matter of editing memory.
Finding *anything* in a menu is a chore of poking through the sections like a blind person. At least with mystery meat, it couldn't be better.

Bottom line: File -> Quit is not a standard. Please, stop pretending it is; it doesn't deserve to be. Program menus should never be a standard, actually, and it scares me that people try to make them such. The only standard should be simple: When you design them - if you design them - *please* do it right.

---

### Post by slimdog360 on 2007-09-30
wow... no really just wow.

---

### Post by cogadh on 2007-09-30
Yes, but how do you really feel? :-k

Seriously though, while I *might* agree that the use of "quit" is not necessarily the best word to use for exiting a program (ooh, what about that; File > Exit?), the original purpose of the "File" menu was to perform file functions, i.e. open a new file, open an existing file, close a currently active file, open recent files, save files, etc. and its use dates back to the earliest gui programs, mostly text editors. Since then it has become part of the universally accepted standards for GUI design, though what is included on the menu is obviously not universal. The quit/close/exit function was most likely originally placed there because it didn't really fit anywhere else. You say that it is not required, but I say thee nay! I can't tell you how many times that some bug or glitch has caused those wonderful little buttons in the top right corner of the window to either stop working or disappear completely. The only way left to gracefully exit out of the program is through the File menu.

As for your problem with the Edit menu, I would say that the preferences makes perfect sense there, since by making changes to your settings, you are actually editing some kind of configuration file. I do find it interesting that on Linux, the standard seems to be Edit > Preferences, while on Windows, it is usually Tools > Options. Not sure which one makes more sense, though.

In conclusion....
Actually, I don't have much more to say, other than I think you will find that most people don't really think or care this much about the menu design of your average program (well, programmers might). As long as the program works and you can use the menus, who really cares?

---

### Post by popch on 2007-09-30
***Close*** is supposed to ask the user what to do with the results which have not been committed to a permanent state, whatever that state might be.

***Quit*** is supposed to discard any unsaved results and close the application with a minimum of fuss and - above all - without blocking the user interface with dialog windows requiring additional clicking.

The placement of the preferences menu is awkward in practically every case I have met. However, I would much prefer it to be in the same place for every application I use. What's the use of it being in optimal position for every application when I have to hunt for it? Also be thankful that, nowadays, it is called 'preferences' in quite a few applications.

---

### Post by phen on 2007-09-30
haha

my mother never got that START -> STOP thing from windows. (dont know the real english term used for stop ...).

Some things should be changed to a structure making more sense. file quit and edit -> preferences are surely two of them.

they would fit under the new top menu "program", like system is it for gnome panel....

---

### Post by Havoc on 2007-09-30
File -> Quit is *not* redundant. Many window managers do not have a close button, and anyways, applications assuming things about their environment is bad practice. I use Linux on an HPC, where most applications start up fullscreened (no window decorations), and Ctrl+Q or File -> Quit gets used a lot.

Not to mention mouseless environments, where everything has to be done with the keyboard.

---

### Post by conehead77 on 2007-09-30
English isnt my 1st language, but shouldnt it be "application->quit" rather than "file->quit"?

---

### Post by slimdog360 on 2007-09-30
> **conehead77 said:**
> English isnt my 1st language, but shouldnt it be "application->quit" rather than "file->quit"?

no, perhaps its different in different languages?

---

