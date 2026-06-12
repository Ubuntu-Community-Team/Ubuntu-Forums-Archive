---
title: "What are the best Terminal programs and why"
date: 2024-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by Omnios on 2024-04-30
What are your favorite Terminal and Terminal programs such as Nala alternative to Apt and why. I really want to get into Linux terminal usage and programs. Also how does MPV work?



EDIT: I was thinking more on the lines of applications that run in the terminal not just Terminal programs. I have played with a few before such as the Tintin ++ text based Mud client. Read there is a web browser for the terminal and a video program to watch videos. Also read about Nola Command line Frontend For APT which is prettier than APT. These are things I would be interested in learning.

---

### Post by TheFu on 2024-04-30
xterm.  small. lite, supports utf8.  does the job.  What do you want from a terminal?  More code mean more bugs.  xterms have been around 30 yrs.
Don't confuse a terminal with a shell or a CLI program. They are each different.

1 question per thread please.

---

### Post by VMC on 2024-05-01
Terminal = bash. When I want to edit a file, I use 'vi'... because of my 30yr on Unix.

---

### Post by him610 on 2024-05-01
The one I use is *xfce4-terminal* that comes with Xubuntu. I have tried others, but the XFCE Terminal Emulator does everything I need it too. I do a little scripting now and then, but no heavy coding.

---

### Post by Tadaen_Sylvermane on 2024-05-02
One I wrote for myself. It makes searching for packages in repositories much less cumbersome by eliminating need to pipe through different commands to find only what I want. Breaks down to package name only and saves me time in particular when I'm searching for -doc packages. It's dumb, but it makes my life easier.

[https://gitlab.com/jmgibson1981/apt-sort](https://gitlab.com/jmgibson1981/apt-sort)

---

### Post by Omnios on 2024-05-02
> **Tadaen_Sylvermane said:**
> One I wrote for myself. It makes searching for packages in repositories much less cumbersome by eliminating need to pipe through different commands to find only what I want. Breaks down to package name only and saves me time in particular when I'm searching for -doc packages. It's dumb, but it makes my life easier.

[https://gitlab.com/jmgibson1981/apt-sort](https://gitlab.com/jmgibson1981/apt-sort)

Not dumb but sounds like fun. I am trying to learn Python to do similar fun stuff. Thinking a lot about getting into Terminal stuff.

---

### Post by TheFu on 2024-05-02
> **Omnios said:**
> Not dumb but sounds like fun. I am trying to learn Python to do similar fun stuff. Thinking a lot about getting into Terminal stuff.

You mean CLI and shell stuff, I think.  

A terminal is just a program that emulates a popular type of hardware device to display text.  For decades, a vt-102 was the standard terminal to be emulated, so nearly all "terminal programs" we see in Unix and Linux default to that emulation.

Being technically correct is important. As you can see, sloppy terms resulted in many different interpretations of the question.
If you want to learn the command line - CLI - then start here: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)  It is best to learn things in an order that builds on previously presented knowledge rather than hunt for answers as you need them.  At least having some background before assuming that point-n-click is the best way to start anything would be helpful.  That link goes to a free PDF that you can download, probably in your native language, or go to any bookstore and buy an outdated version.  Fortunately, at the CLI, very few things become outdated too quickly.  Anyway, start from chapter 1 of that book and work through everything for about the first 250 pages to get the background for how things actually work and learn why the CLI and a good shell program are much more efficient than most GUIs.  Of course, there are a few tasks where the GUI is actually faster/better, but often, people who don't know their shell very well will assume the GUI **is** the most efficient way because they don't know any better or don't want to be bothered to learn a different way to accomplish things.

OTOH, GUIs change drastically every 2 yrs, so if you learn only 1 GUI, you'll always be learning a new one because distros and programmers often confuse "new" with "better", which is seldom actually true.  

I say these things so often, I feel like a broken record.  Doing things the UNIX way is something that needs to be learned.  Usually, it requires unlearning the way those other, proprietary, OSes have forced people to work.  People who know their shell program well get really frustrated when forced to use other OSes that don't have anything as useful/similar.

---

### Post by Omnios on 2024-05-07
[COLOR=#000000]Edited fist post as : I was thinking more on the lines of applications that run in the terminal not just Terminal programs. I have played with a few before such as the Tintin ++ text based Mud client. Read there is a web browser for the terminal and a video program to watch videos. Also read about Nola Command line Frontend For APT which is prettier than APT. These are things I would be interested in learning.[/COLOR]

---

### Post by TheFu on 2024-05-07
> **Omnios said:**
> [COLOR=#000000]Edited fist post as : I was thinking more on the lines of applications that run in the terminal not just Terminal programs. I have played with a few before such as the Tintin ++ text based Mud client. Read there is a web browser for the terminal and a video program to watch videos. Also read about Nola Command line Frontend For APT which is prettier than APT. These are things I would be interested in learning.[/COLOR]

If you want to be employed doing Linux, you should stick with things that are installed by default on the system, or at least in the core repos provided from Canonical (i.e. NOT the Universe Repo).  Many employers prohibit installing software outside the core repos.

If this is for home use only.  Go crazy.

CLI web browser is links or lynx.  Think both exist.  No images. No javascript.  Sometimes that's all you want - just the text.  Also check out pandoc to pull webpages local and convert them into formats you prefer.

CLI video player is mpv.  But it requires a GUI.  There are others, but mpv is 1000x better than the others.

CLI programs I can't live without - vim, qmv, let me check my history ... 
[LIST]
[*]tsp - Task Spooler
[*]bash and many of the built-in features of the shell.
[*]yt-dlp
[*]du/df
[*]lsblk
[*]inxi
[*]egrep
[*]locate
[*]recoll
[*]
[/LIST]

Most of the other things in my history are scripts I've created to do more complex things like searching specific file systems, play back audio playlists on remote systems, rename files using specific patterns, 

For example, sometimes I don't want to wait for Linux to clear buffers. I know all the large files I've been working with won't be needed, so I tell the OS to clear them.
$ more ~/bin/free-drop-disk-buffers 
```
#!/bin/bash

free -h && sync 
echo 3 |sudo /usr/bin/tee /proc/sys/vm/drop_caches 
free -h

```
Simple and after I have this script, I don't need to recall exactly how it works anymore.  When run, 
```
$ free-drop-disk-buffers 
              total        used        free      shared  buff/cache   available
Mem:           30Gi       6.7Gi       263Mi       137Mi        [COLOR="#FF0000"]23Gi[/COLOR]        23Gi
Swap:         4.1Gi       1.2Gi       2.9Gi
3
              total        used        free      shared  buff/cache   available
Mem:           30Gi       6.8Gi        23Gi       137Mi       [COLOR="#008000"]707Mi[/COLOR]        23Gi
Swap:         4.1Gi       1.2Gi       2.9Gi

```
See the difference?

Some others, 
[LIST]
[*]cal
[*]ansible
[*]and all ssh stuff - ssh, sftp, scp, rsync ... 
[*]Plus cron and at for batch processing at specific times.
[/LIST]
Sometimes I need to count the lines in a file, **wc -l**.  

I could list hundreds and hundreds of CLI tools.  I'll often put them into a file where the output from 1 tool is read as the input to another  to accomplish more complex tasks. If a script is over 1 screen in length, it is usually too complicated for bash, so I'll switch to some other language with better data structures.  Perl is generally my choice, but I'll use Ruby sometimes.  Others would use python, which is a great language for general use needs and easy to learn with lots of Python groups in most cities and colleges to help.

---

### Post by currentshaft on 2024-05-07
soa

---

### Post by 909mjolnir on 2024-06-17
I think at the Devuan forums there's a conversation (old one) about minimalist programs like mpg321 (to play audio files), etc.

---

### Post by currentshaft on 2024-06-18
> **TheFu said:**
> xterm.  small. lite,

Surely you jest, sir/madam.

xterm? The same xterm with the man page that begins with

[INDENT]Abandon All Hope, Ye Who Enter Here

This is undoubtedly the most ugly program in the distribution.  It was one of
the first "serious" programs ported, and still has a lot of historical baggage.
Ideally, there would be a general tty widget and then vt102 and tek4014
subwidgets so that they could be used in other programs.  We are trying to
clean things up as we go, but there is still a lot of work to do.[/INDENT]

xterm is the antithesis of a small and lite program designed to do one thing well.

---

### Post by 909mjolnir on 2024-06-19
lol ^^^^

good point about xterm

personally, i try to become familiar with xfce4-terminal because it's always there in xfce and it looks nice and makes sense to my brain.  
in my college years i learned some other terminal stuff, but i can't remember it anymore.  

for a while i tried some fancy looking VT console emulator with nice vintage antique special effects, but it was just eye candy.  
mate-terminal is pretty good too if you're used to MATE instead of XFCE.  Nicely, you can use a variety even across DE's.  
But if you use Thunar, you'll need xfce4-terminal for compatibility from within Thunar, etc.  

I think what matters more is how you customize the interface in the prefs, and what you run with them, and how you trigger them via keyboard or shortcut, etc.

---

### Post by TheFu on 2024-06-20
I'm completely serious.  xterm RAM use is measured in KB, not MB.  For your reference:
```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
1385293 tf        20   0   29168   9256   5092 S   0.0   0.0   0:02.77 xterm
2901008 tf        20   0   29664  11724   5696 S   0.0   0.0   0:01.90 xterm
2969047 tf        20   0   27776   6164   4556 S   0.0   0.0   0:00.14 xterm
2969048 tf        20   0   29112  10960   5132 S   0.0   0.0   0:01.64 xterm
2969049 tf        20   0   28328   9208   4304 S   0.0   0.0   0:01.08 xterm
2969050 tf        20   0   35360   9052   5664 S   0.0   0.0   0:15.76 xterm
2969051 tf        20   0   31024  11980   4760 S   0.0   0.0   0:03.68 xterm
2969052 tf        20   0   32224   9884   5232 S   0.0   0.0   0:00.75 xterm
```

Under 12KB used for each of them.  And for full disclosure, I use uxterm to have UTF8 support, but that's part of the xterm code now.

gnome-terminal ... on a different system, 
```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
3868907 tf        20   0  226900  15244  12840 S   0.0   0.3   0:00.01
```
That's 16KB for a simple terminal. Look at the virtual RAM claimed 220KB vs 33KB.  Bloated.

Since I don't use any DE, I avoid much of the bloat from all the DE-specific programs.  To each their own.  If you like cheese/bloat and find it valuable, great.

---

### Post by Holger_Gehrke on 2024-06-20
@TheFu: is that output from 'top' ? Then it's in kbyte, so it's less than 12 MByte (which is what I see in top), not less then 12 KByte. 'xterm' has some functionality that is rarely useful, e.g. Tektronix 4014 emulation. I haven't found any software that expects that kind of graphics terminal. Unicode support in xterm also depends on the font you use with it and setting fonts in xterm is kind of difficult - either use various command line switches or X-resources. And the classic X11 syntax for font descriptions is ever so slightly nightmarish ('-misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso10646-1' is the default font for utf-8 set in /etc/X11/app-defaults/XTerm).

Holger

---

### Post by TheFu on 2024-06-20
Holger_Gehrke, you are correct as usually about top showing KB by default. I regret the mistake.

I use the ~/.Xresources and have for about 30 yrs. Not a nightmare for me, but I was an X/Windows  programmer and sent to corporate training on it.  Maybe I'm just old and set in my ways. I know how to use the menus in an xterm and they are 2nd nature for me.  I like the ease of choosing tiny/small/medium/large/huge fonts easily, especially when giving presentations.  Plus, I hate terminals with colors and light backgrounds, so all of mine are run with specific options, for specific placement on my workspaces, for uses I've decided over the decades so I know which terminal in which location has what types of uses (and pwd) just by location.

Everyone should use the tools they like that make them productive.  I've found mine.

---

