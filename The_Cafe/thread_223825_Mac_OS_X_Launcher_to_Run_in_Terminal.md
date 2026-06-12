---
title: "Mac OS X Launcher to Run in Terminal"
date: 2006-07-27
forum: The Cafe
---

### Post by aysiu on 2006-07-27
[I've Googled around for this](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=%22run+in+terminal%22+launcher+%22mac+os+x%22&btnG=Search) to no avail.

You know how in Gnome you can right-click, Add to Panel, Create Custom Application Launcher, and then select for it to **Run in Terminal**?

Anyone know how to create something similar on the Dock of Mac OS X?

I have a backup script for my wife. It uses *rsync* and the command is simple, but I think my wife is afraid to use the command-line, even if it's a simple command. If she had a launcher on the dock that ran the script in the terminal, that'd be great... but how do I do that? Any ideas?

By the way, I've already tried [RSyncX](http://archive.macosxlabs.org/rsyncx/rsyncx.html) (the graphical frontend for *rsync*), and it doesn't work in her computer (or maybe it doesn't work at all). The command-line *rsync* works.

---

### Post by simonn on 2006-07-27
Off the top of my head (I am at work, my iBook is at home)...

Create a shell script doing what you want to do.

Drag it to the dock.

---

### Post by aysiu on 2006-07-27
And that will open it in the terminal? I'm an idiot for not even thinking of that. I'll try it...

---

### Post by jasay on 2006-07-27
I've never used a mac, so I don't know what I'm talking about, but I would think a shell script with "rsync blahblah" in it would run rsync silently in the background rather than open a terminal and run inside it.

What I would suggest is to write a script that starts a terminal and feeds said terminal some commands.  For xterm it might look something like ```
xterm -e "rsync -options /stuff/to/be/backed/up /backup/location"
```which should open an xterm window and run rsync in that terminal.  You might have to play around with the man pages of whatever terminals OSX has to find the right option.

---

### Post by aysiu on 2006-07-27
Thanks, jasay. I'll try that tonight.

---

### Post by gThree on 2006-07-27
Slightly off-topic, but you might want to check this out for future reference:
[http://www.macupdate.com/info.php/id/9283]("http://www.macupdate.com/info.php/id/9283")
[http://www.macupdate.com/info.php/id/11050]("http://www.macupdate.com/info.php/id/11050")
Worked great in 10.2.8, no experience with it beyond that.

More on-topic, you could also consider wrapping it in an Applescript GUI.  Pre-Yahoo! Konfabulator wasn't bad for that sort of thing either.  Not sure about latest versions.

---

### Post by aysiu on 2006-07-27
Well, according to [this page](http://www.sm.luth.se/~alapaa/file_fetch/unixcdbookshelf/mac/ch01_03.htm), the *xterm* thing won't work.

I have a few more fundamental problems before I can play around with this. 

1. I can't find the shell script in order to do drag-and-drop. In the terminal, I can find it--I put it in /usr/local/bin. But in the GUI, I can't get to /usr.

2. My wife is deep into a website design project and doesn't have a lot of time for me to be poking around on her computer.

I'll update this thread when I've had more time to try a few things.

---

### Post by simonn on 2006-07-27
I had a little play with this last night.

Create a shell script, then right click on it and select info/information/whatever (sorry - I am useless at remembering the names of GUI stuff, you basically want the OS X equivalent of properties) and set the script to be run by terminal.app (which is in Applications/Utilities by default).

---

### Post by aysiu on 2006-07-27
Awesome. Thanks, simonn. I just have to *find* the script now...

---

### Post by dabear on 2006-07-27
> **aysiu said:**
> Awesome. Thanks, simonn. I just have to *find* the script now...

Didn't you have the command to be run? 
```

#!/bin/sh
rsync -options /stuff/to/be/backed/up /backup/location

```

---

### Post by aysiu on 2006-07-27
Yeah, I created the script in the terminal--the terminal can find anything.

But in the GUI Finder, I can't locate the /usr directory or any of the top-level directories...

---

### Post by aysiu on 2006-07-27
Success! Thank you all for your help.

I found a way to temporarily show hidden folders in Finder. I changed ownership of the shell script to my wife's account.

Then I did Cmd-I to change the application that it opens with and also to change the icon (my wife wanted the Link Tux).

I dragged the script to the dock, changed ownership back to root, and then turned off showing hidden files.

Thanks once again for your help. Ubuntu's community's great at offering support... even for other platforms!

---

