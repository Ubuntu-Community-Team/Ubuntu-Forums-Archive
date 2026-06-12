---
title: "The Dolphin File Manager"
date: 2007-06-25
forum: The Cafe
---

### Post by ThinkBuntu on 2007-06-25
I was very quick to write off the Dolphin file manager in the "Will KDE4 Kill GNOME?" topic, as I was using it with Metacity in GNOME and really didn't put it through its motions, but using it full-time in KDE, I must say that it's a great alternative as a simple file manager to Konqueror.

Although it's missing my most anticipated feature (a column navigation view, like in OSX, which is the best and most efficient file manager I've seen or used), it makes up for it with sane defaults and very user-friendly, compact design.

One thing I would've liked to see is Ctrl+W closing the window, but thanks to easy shortcut mapping, I was able to switch it away from Ctrl+Q. On the other hand, Ctrl+N is there to create a new folder (ah, takes me back to OS 7-9), F2 renames as expected, and the whole thing flows very well. The left pane can be used as a bookmarks section, or, as I prefer, a preview section that is comprehensive in its capabilities (loading HTML pages, images, etc, while showing all relevant file information). Ctrl+F opens a search window instantly, and F4 opens a terminal at this location. The odd Alt+Return is the default shortcut to view properties, which I quickly replaced with Ctrl+I.

There's a filter tool always visible, which is very useful for sorting through bunches of files. Granted, it doesn't search metadata a la Beagle, but its' still a nice tool to have. Ever-present are also a "Compress Here" button that converts a folder to .tar.gz, and an "Open as Root" button. At the top, just like Nautilus there's a breadcrumb navigation and a button to allow directory access by typing, e.g. /home/username/.cia_passwords/

Unfortunately, I haven't had the time to test this with other file systems, such as FTP, but the combination of Split View and FTP access could be very powerful and all but eliminate my need for Kasablanca.

These are all technicalities, and I'm sure that Dolphin is due for some major changes over time. I'm running Dolphin 0.8.2 over KDE 3.5.7, so depending on your version (say, Kubuntu 6.06), you may see a rougher version of Dolphin. But in any case, what really sets Dolphin apart are these things:
[LIST]
[*]Generally speedy
[*]Opens instantly
[*]Full-featured
[*]A path to separate online from local browsing for Konqueror users
[*]Nicely simplified interface without sacrificing functionality
[/LIST]
Granted, some will cry foul that there's no tree view, but for those of us with smaller screens, tree view is not very useful when the expanded contents of just a few folders grab more vertical space than we have. I'll be very pleased running Dolphin as my file manager in KDE for the forseeable future, and best of all, this will give me the chance to use Konqueror for what it really is: a web browser.

Note: I'll update this post once my Dolphin as default filesystem Tutorial is approved in the Tips & Tutorials forum.

---

### Post by GeneralZod on 2007-06-25
> **ThinkBuntu said:**
> 
Granted, some will cry foul that there's no tree view, but for those of us with smaller screens, tree view is not very useful when the expanded contents of just a few folders grab more vertical space than we have.

Actually, Dolphin SVN has had a Tree View for quite some time now (and also Metadata integration with Nepomuk, but I'm not sure if they've integrated search with it just yet), although like all other types of panel, it can be easily removed.

It's shaping up to be a nice File Manager in it's own right, rather than having "It's not Konqueror!" as its sole advantage ;) I'll probably be sticking with Konqueror come KDE4, though, but you never know - it might win me over completely :)

---

### Post by ThinkBuntu on 2007-06-25
I just have this expectation that, no matter how slow other apps are, the file manager should open nearly instantly if not instantly, unless I'm navigating to a particularly complex directory with thumbnails, etc. Granted, on my laptop, in Arch and Debian, Konqueror does just this. But it's nice to have a "normal" file manager to allow instant file access no matter your distro's speed, giving you more choices if this is important to you. In Pardus, which is speedy but not like Debian, Arch, Zenwalk, or {insert fast distro here}, Dolphin serves me well for my purposes.

---

### Post by fuscia on 2007-06-25
nice change of heart. i love dolphin. and, as you said in the other thread, it's the thunar of kde. it will be interesting to watch it develop.

---

### Post by Jucato on 2007-06-25
Just some quick notes:

1. Dolphin on KDE 3.5.x pales in comparison to the one currently on KDE 4. So hold your judgments until you see/use the real thing.

2. Like what GeneralZod said, there's a tree view already

3. Dolphin is a file manager, not a desktop search. :) Of course, with Strigi and Nepomuk on the way in KDE 4, a lot of the stuff you can do with Beagle can be made available not only to Dolphin but to all of KDE.

4. Dolphin breadcrumbs are more powerful than Nautilus'. Click and hold down on a particular "crumb" and a list of folders under that will show.

5. Works with almost any kioslave, except for a few (like http, man, etc). This means sftp:/, ftp:/, fish:/, smb:/, etc.


6. Still has the embedded Konsole for you to use if you want.

7. You can place the panels anywhere! Right, left, top, bottom, detached. :)

Lots of stuff going on in Dolphin as we speak. So hold your breath :)

---

### Post by ThinkBuntu on 2007-06-25
> **fuscia said:**
> nice change of heart. i love dolphin. and, as you said in the other thread, it's the thunar of kde. it will be interesting to watch it develop.
Seeing that you're very familiar with it, I have a couple quick questions. First, if I have a device icon on my desktop, as in "Create New > Link to Device > Hard Disk Device (select '/' partition)", how do I get it to work with Dolphin? Right now, those links produce a "could not mount, already mounted" error when clicked instead of opening in Dolphin. Second, from System desktop config file, which would normally open into a sysinfo:/ page (which I think is just XSL or PHP generated), why does it persistently open in Konqueror? There's no matching file association to match it to Dolphin.

---

### Post by fuscia on 2007-06-25
> **ThinkBuntu said:**
> Seeing that you're very familiar with it, I have a couple quick questions. First, if I have a device icon on my desktop, as in "Create New > Link to Device > Hard Disk Device (select '/' partition)", how do I get it to work with Dolphin? Right now, those links produce a "could not mount, already mounted" error when clicked instead of opening in Dolphin. Second, from System desktop config file, which would normally open into a sysinfo:/ page (which I think is just XSL or PHP generated), why does it persistently open in Konqueror? There's no matching file association to match it to Dolphin.

dude, i'm just a humble end user and have no idea what you're talking about.

---

### Post by ThinkBuntu on 2007-06-25
> **fuscia said:**
> dude, i'm just a humble end user and have no idea what you're talking about.
You use Dolphin as your default file manager, so I thought you'd have run into these issues by now. It's all good though, I'll track em down myself. I need to add the answers to these to my Tutorial.

---

### Post by Extreme Coder on 2007-06-25
Would be really nice of you if you would PM me the link to your torial when you're done with it, as I'm not around here a lot, so I'd probably miss it..

---

### Post by ThinkBuntu on 2007-06-25
> **Extreme Coder said:**
> Would be really nice of you if you would PM me the link to your torial when you're done with it, as I'm not around here a lot, so I'd probably miss it..
No problem.

---

### Post by Extreme Coder on 2007-06-25
Thanks! :)

---

### Post by Andrewie on 2007-06-25
I've been playing with the 3.5.x version of dolphin and its really grown on me, I can't wait till kde 4

---

### Post by forrestcupp on 2007-06-25
> **Andrewie said:**
> I've been playing with the 3.5.x version of dolphin and its really grown on me, I can't wait till kde 4

I just switched to Kubuntu from gnome, and I like the 3.5 dolphin a lot.  I like it better than nautilus.  No offense to nautilus users, it's just my preference.  If KDE 4's dolphin is better, that's cool.

---

### Post by ben::zen on 2007-06-28
I'm looking at KDE4, and deciding that I don't want to spoil it. (I just got my desktop effects working, and I'm happy.) I can't wait though!

---

### Post by SunnyRabbiera on 2007-06-28
well the latest version of dolphin works better for me then the last one, the last one crashed me out a few times.
But its still got a while to go like compatibility with quicklaunch in kicker and the trash bin on the desktop.
I hope it progresses but there are sstill things I dont like about it

---

### Post by stmiller on 2007-08-07
Bumping this thread. I've been trying out Dolphin and it's great. Here is the home page:

[http://enzosworld.gmxhome.de/](http://enzosworld.gmxhome.de/)

A version is available in Feisty, so:

apt-get install dolphin

and try it out! Nice and simple. Seems to resemble OS X Finder.

---

### Post by cb474 on 2007-08-26
I've been having a very odd problem with Dolphin. I installed it in regular gnome Ubuntu Feisty, because I really like the split screen option.

However, it breaks my laptop's ability to connect to the Internet. I can connect okay to my router, pull up the router's web pages for user settings and everything, but not to anything on the Internet. I know it's not the computer, because I dual boot with XP and everything is okay in XP.

It's either Dolphin or the various dependent files it installs that causes the problem. I made a backup image of my Ubuntu parition and restored it to the moment before I installed Dolphin, and everything was fine. Then installed Dolphin again and the same thing happened.

I'm using Firefox. Also, even though I can't pull up web sites in Firefox, with Dolphin installed, I can telnet to a remote Unix account from the terminal.

Any thoughts?

---

### Post by cb474 on 2007-08-31
No one has any ideas why Dolphin is breaking my network connection? Perhaps it sounds weird, but it's true.

---

