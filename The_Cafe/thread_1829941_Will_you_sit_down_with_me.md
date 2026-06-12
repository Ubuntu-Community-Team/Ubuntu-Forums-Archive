---
title: "Will you sit down with me?"
date: 2011-08-21
forum: The Cafe
---

### Post by oldarney on 2011-08-21
My original title was "linux poweruser/dev beginner guide?"

After finally accepting that Linux is an OS by developers, for developers... I've come to love the terminal. I recently found out that Ctrl+Alt+T opens the terminal, this would have saved me years of my life! And I am now using ~/.bashrc as my notes file, whenever I need to remember a complicated command, I save it there.

Where can I find all of these massively useful shortcuts and configs? I am not looking for a "what is the terminal?" or a "ubuntu begginers guide," [B]I'm looking for stuff you usually learn by sitting down with ubuntu friends... which I have none irl.

[/B]on the other hand, you could just drop your most indispensable ideas about how to use Linux as a power user.

---

### Post by IWantFroyo on 2011-08-21
I always thought it was ctrl-alt-t... That's probably my favorite shortcut, though.

cltrl-alt-f1 for CLI, ctrl-alt-f7 for GUI, plus alt-f(2,3,4,5,etc.) to switch between ttys.

---

### Post by Megaptera on 2011-08-21
Hi,
I find this very useful as I stumble around!!

"CLI Companion is a tool to store and run Terminal commands from a GUI. People unfamiliar with the Terminal will find CLI Companion a useful way to become acquainted with the Terminal and unlock its potential. Experienced users can use CLI Companion to store their extensive list of commands in a searchable list."

Here: [https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

Hope it's of interest?

---

### Post by NightwishFan on 2011-08-21
Another tip I have when learning is a nice personal wiki. Have one built right in with Tomboy (or Gnote). You can make a group of notes and have linkable titles and search your notes as well. Just copy down a bit of interesting tidbits or insights as you go.

---

### Post by IWantFroyo on 2011-08-21
> **NightwishFan said:**
> Another tip I have when learning is a nice personal wiki. Have one built right in with Tomboy (or Gnote). You can make a group of notes and have linkable titles and search your notes as well. Just copy down a bit of interesting tidbits or insights as you go.

That's a good idea. I never thought of that...

Also you know you can make your own keyboard shortcuts? The tool's preinstalled.

---

### Post by oldarney on 2011-08-21
> **IWantFroyo said:**
> I always thought it was ctrl-alt-t... That's probably my favorite shortcut, though.
  
  cltrl-alt-f1 for CLI, ctrl-alt-f7 for GUI, plus alt-f(2,3,4,5,etc.) to switch between ttys.
  
 Oops, I actually did mean Ctrl-Alt-T to open the terminal.
 
 > **NightwishFan said:**
> Another tip I have when learning is a nice  personal wiki. Have one built right in with Tomboy (or Gnote). You can  make a group of notes and have linkable titles and search your notes as  well. Just copy down a bit of interesting tidbits or insights as you  go.
 
 I actually made a private wiki with several pages on how to hack into  univeristy printers and computers. But that relies on a server, that I  have to maintain or pay for. I wish there was a better way to store  documents and search through them, without a heavy backend.
 
> **IWantFroyo said:**
> That's a good idea. I never thought of that...

Also you know you can make your own keyboard shortcuts? The tool's preinstalled.

I have always stayed away from making my own shortcuts because of  portability issues. I have yet to find any use for TTY's when I could  just open a terminal and press F11... I can't even play music on them.

---

### Post by ninjaaron on 2011-08-21
Best terminal command of all time:

```
|
```

Especially nice with a [FONT="Courier New"]grep[/FONT] after it. more on that [here]("http://www.codecoffee.com/tipsforlinux/articles/24.html").

****
Another trick I invented recently is sending the output of man pages to a text file for easier reading in gedit or libreoffice.  I'm getting more comfortable with [FONT="Courier New"]less[/FONT], so I don't use it as much any more, but it has been a big help in the past.  It's like this:

```
$ echo "`man grep`" > grep-help
```

Replace "grep" with whatever you like.  I used grep because everyone should learn how to use it.  This creates a text file in the current directory with the contents of the man page, ready to be opened by whatever program you prefer for reading text.

****
Another tip is to learn basic vim keybindings.  Install vim (sudo apt-get install vim) and go through the vim turor by typing [font="Courier New"]vimtutor[/font].  Then use vim as your text editor, at least for a little while.  The point of this is not to actually use vim (though it is wonderful).  The point is learning the vim keybindings.  The keybindings for navigating documents in vim are used in MANY programs inside and outside the terminal (including Banshee, oddly enough), and if you learn them once, you can use them for everything.

If you really want to force yourself to learn it, there is an extension for firefox called "pentadactyl" that turns on vim keybindings in the browser, which will make you learn them really fast, and also allows you to surf the web without taking your hands from the keyboard, which I like.

****
The real way to get the most out of the terminal is by writing scripts.  Bash scripts are programs, but they are programs written with just a bunch of terminal commands executed one after another.  This may sound stupid, but it is actually extremely powerful because you can make all of the different terminal programs talk to each other . What you learn by scripting, you will always be able to use in the terminal, and you can even use it to mess around with your friends' Macs.

Plus, scripting is wonderful.  Yesterday, I wanted to download a bunch of files from a website, but the files were in directories that were not accessible to the public.  I could only access them one at a time by following links.  I wrote a script with wget (ok, I used curl, but you could do it with wget, which is already on your computer) that would find the right links, follow them, and download the correct files.  I started the script up, went for coffee, came back, and had the 2000+ files I was looking for already on my computer (This is more or less exactly how Mark Zuckerberg "hacked" the Harvard servers to get the images for creating "facemash" as portrayed in "The Social Network").

Scripts like this can also be used to rename or re-sort thousands of files in one go.  It's not something you have to do every day, but when it needs to be done, it is much better to know how to write a script than to do it all manually.  I actually started with scripting because I needed to change the names of 4000 files from uppercase to lowercase, and I really didn't want to do that manually.

You can also use scripts to get your machine doing some slick things both on the surface and below board.  I used scripts that makes seven or eight different programs talk to each other to basically build a bunch of new UI elements for my Inpiron duo (tablet/netbook thing).

There are many great tutorials and reference guides for bash scripting on the internet. If you learn that way, great.  I used tutorials a little, but I found it easiest to learn by looking at other people's scripts and modifying them for my needs.  As I started to write my own scripts, goggling a command almost always got me where I was going.  If you need more help, there are always lots of people on the forums who know bash well (much better than I do, that's for sure), and there are other Linux and Unix forums with boards dedicated especially to bash.

That's all I got for now.

---

### Post by koleoptero on 2011-08-21
I have the shortcut for opening a terminal set to ctrl+` (` is next to space on my laptop's keyboard so they're close) to open terminals when I want them.

---

### Post by ninjaaron on 2011-08-21
> **oldarney said:**
> I have always stayed away from making my own shortcuts because of  portability issues. I have yet to find any use for TTY's when I could  just open a terminal and press F11... I can't even play music on them.

Yes you can. If you have a music going on the desktop, it will play when you login at the tty.  You can also have a CLI player like cmus running in one tty and be working in another.  It's graphics that are the real problem.

---

### Post by Copper Bezel on 2011-08-21
Not true on 11.04, how ever it is that it handles things. The desktop is basically suspended while you're at TTY. You can start a song, jump to TTY, run things for ten minutes, and come back to find the song on the same beat.

---

### Post by ninjaaron on 2011-08-21
I do it all the time in 11.04.  I'm doing it now with Banshee.  In fact, if I'm doing something that's heavy on resources, I run cmus from the tty and listen in the GUI.  I only started this recently, and I have the backports and proposed repos enabled, so maybe it's something new since the release?

---

### Post by Copper Bezel on 2011-08-21
Maybe, yeah. Weird.

---

### Post by Linuxratty on 2011-08-21
> **IWantFroyo said:**
> I always thought it was ctrl-alt-t... That's probably my favorite shortcut, though.

cltrl-alt-f1 for CLI, ctrl-alt-f7 for GUI, plus alt-f(2,3,4,5,etc.) to switch between ttys.

 I just sit the terminal icon on my task bar. One click and I'm there.

---

### Post by oldarney on 2011-08-21
> **ninjaaron said:**
> 

```
|
```Especially nice with a [FONT=Courier New]grep[/FONT] after it. more on that [here]("http://www.codecoffee.com/tipsforlinux/articles/24.html").

****
The keybindings for navigating documents in vim are used in MANY programs inside and outside the terminal (including Banshee, oddly enough), and if you learn them once, you can use them for everything.
****
Plus, scripting is wonderful.  I actually started with scripting because I needed to change the names of 4000 files from uppercase to lowercase, and I really didn't want to do that manually.


I have been using the basic features of grep recently, but I have been trying to learn regex for 4 years... I still can't remember anything more complicated then .[0-9]*

I was forced to learn haskell in emacs and learned a few shortcuts. I also use nano allot. But I'll take a look... I need to use emacs again for the fall semester.
 
While I love scripting, in windows I used to script visually to automate the usage of anything by auto clicking images... I ripped a book from a website that showed single pages that way. **Is there anything in linux for automating less accessible programs like flash?** Mouse automation in linux has paled so far compared to SCAR, from what I've seen.

> **Copper Bezel said:**
> Not true on 11.04, how ever it is that it handles things. The desktop is basically suspended while you're at TTY. You can start a song, jump to TTY, run things for ten minutes, and come back to find the song on the same beat.

Just checked... your destop TTY1 music freezes, but playing music on TTY2 does not stop when you switch to TTY1, just checked with pianobar which uses gstreamer.

> **Linuxratty said:**
> I just sit the terminal icon on my task bar. One click and I'm there.

I used to do that, but when you use the terminal for half of what you do, its easyer to shortcut it.

---

### Post by nothingspecial on 2011-08-21
If you want to write a script "on the fly", press Ctrl-X Ctrl-E

That will open your $EDITOR which by default in ubuntu is nano. You can change this.

When you save and close, bash will execute the script.

---

### Post by keithpeter on 2011-08-21
Nice thread

I like silly things like

[http://onethingwell.org/post/457674798/a-poor-mans-notational-velocity](http://onethingwell.org/post/457674798/a-poor-mans-notational-velocity)

I run dwm at present as a sort of experiment in [maximalism]("http://kmandla.wordpress.com/2010/05/05/maximalism-is-a-better-word/"). 

I also publish my web site using a few bash scripts and lftp rather than maintaining a WordPress install or similar,

[http://bodmas.org/pages/20100221--web_how_this_site_is_published.html](http://bodmas.org/pages/20100221--web_how_this_site_is_published.html)

---

### Post by oldarney on 2011-08-22
> **nothingspecial said:**
> If you want to write a script "on the fly", press Ctrl-X Ctrl-E

That will open your $EDITOR which by default in ubuntu is nano. You can change this.

When you save and close, bash will execute the script.

Thats exactly why I started this thread. I just found use for that. I can't paste a multiline command in terminal without having it execute before I can edit. With that shortcut I can open nano and change it before it runs.

> **keithpeter said:**
> Nice thread

I run dwm at present as a sort of experiment in [maximalism]("http://kmandla.wordpress.com/2010/05/05/maximalism-is-a-better-word/"). 

I also publish my web site using a few bash scripts and lftp rather than maintaining a WordPress install or similar,

[http://bodmas.org/pages/20100221--web_how_this_site_is_published.html](http://bodmas.org/pages/20100221--web_how_this_site_is_published.html)

Old school. Wordpress is a no brainier to use, although it may be big on the inside, its small on the outside. On the other hand... its what you say that matters, not how you say it.. right?

---

### Post by Erik1984 on 2011-08-22
In Unity you could also use windows/super key + number where number is the position of the terminal on the launcher. for me it's the third icon from the top so super + 3 opens a new terminal window if none is opened. Otherwise it brings the active terminal window to the front.

---

### Post by nothingspecial on 2011-08-22
Ok, a few others

Ctrl-R will start bash's reverse search where you type the first bit of a really complicated command and then continue pressing Ctrl-R until you get the right one.

Use extended globs for more powerful matching. For example say you have a directory full of music and want to keep all the .flac and .ogg files but delete everything else
```

shopt -s extglob; rm !(*.ogg|*.flac)
```

The first command turns extended globs (of which ! is one) on. In the second command everything within the brackets (seperated by a |) is matched but the ! glob means match everything that isn't in the brackets....... I'm not explaining this very well.......

```
$ls
1.ape   1.m4a  1.png  2.ape   2.m4a  2.png  3.ape   3.m4a  3.png  4.ape   4.m4a  4.png  5.ape   5.m4a  5.png
1.flac  1.mp3  1.txt  2.flac  2.mp3  2.txt  3.flac  3.mp3  3.txt  4.flac  4.mp3  4.txt  5.flac  5.mp3  5.txt
1.jpg   1.ogg  1.wma  2.jpg   2.ogg  2.wma  3.jpg   3.ogg  3.wma  4.jpg   4.ogg  4.wma  5.jpg   5.ogg  5.wma
$shopt -s extglob; rm !(*.ogg|*.flac)
$ls
1.flac  1.ogg  2.flac  2.ogg  3.flac  3.ogg  4.flac  4.ogg  5.flac  5.ogg
$
```

---

