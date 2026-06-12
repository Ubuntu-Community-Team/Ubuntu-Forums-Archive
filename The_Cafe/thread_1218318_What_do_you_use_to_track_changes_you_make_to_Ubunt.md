---
title: "What do you use to track changes you make to Ubuntu?"
date: 2009-07-20
forum: The Cafe
---

### Post by dutchhome on 2009-07-20
I installed Jaunty from scratch this weekend and felt the pain of trying to remember what I like to install - packages, custom scripts, FireFox plugins,etc.

Do any of you have a cool system for keeping track of these kinds of things to help with setting up new installs?  Care to share?

Jon

---

### Post by raronson on 2009-07-20
Historically I've used plain text files to make notes or keep track of changes.  Lately I've been using Tomboy, due to my propensity to make lists of everything (including a personal ToDo list).

Here's an example:

```

Ubuntu Migration from OS X
==========================

!backup ubuntu files as well
    .I plan to reformat the drive    

https://help.ubuntu.com/community/OSXApplicationsEquivalents

.make sure to get a list of all your system spec before switching
    .and what type of macbook you have (~/Documents in OS X has this in a text file)
.need an airport utility
    .java util not working
.iTunes replacement
    .drm dumpster
    .need to replace iTunes client software
          #.plenty to choose from (looking at exaile), plus music stores
.virtual machine - VirtualBox
.hdmi connection to television


Things I like about OS X
------------------------
the interface, the integration, unix underneath, everything works seamlessly, macports.

Things I don't like about OS X
------------------------------
Application closing ("it's a feature"), the unix env is nerfed, a largely non-technical user-base
(though that's changing), it's proprietary, forced upgrade path, finder is nerfed.

Things that I need OS X for
---------------------------
to control my airport extreme?  Other than that, there's nothing I can't live without.
Safari to pay one bill online (but Wells Fargo is changing that hopefully).

```Did I mention that I make a lot of lists?

```

EMACS COMMANDS

core command
C-x C-c        exit emacs
Meta-x recover-session RET    recover a crashed session

canceling
C-g                cancel a command
ESC-ESC-ESC        cancel a command
M-x ESC-ESC-ESC    exit out of mode

help
C-h            invoke emacs help, '?' for list, 'q' to quit
C-h t        emacs tutorial
C-h k        provides description of key press entered after    
C-h m        help with modes

buffers
C-x C-b        list all buffers
C-x <-,  ->    previous, next buffers
C-x b        create buffer
C-x k        close buffer
C-x 1, C-x 2    single screen, split screen3
C-x o        switch screens
C-M-v        scroll other window

cursor commands
C-v, M-v        scroll up, down one page
C-l            places current line in the center of the buffer
C-u 0 C-l        places current line at top of buffer, see 'C-u' below
C-f, C-b        moves cursor one space forward, back
M-f, M-b        move one word forward, back
C-n, C-p        moves cursor to the next line, or previous line
C-a, C-e        moves to beginning, end of a line
M-a, M-e        move to beginning, end of sentence
M-<, M->    move to beginning, end of document

C-u {number}    numeric argument; perform a task x times
                ex. C-u 8 C-f    moves forward 8 char's
C-x z        repeat previous, ex. 'C-x z z z' repeats command 3 times

C-s, C-r        forward, reverse search (retype command for multiple iterations)

killing, deleting, & yanking
<Delback>    delete char just before the cursor
C-d            delete char after cursor
M-<Delback>    kill word immediately before the cursor
M-d            kill next word after cursor

C-k            kill from cursor to end of line
M-k            kill to end of current sentence

C-<SPC>        mark start of delete set
C-w            delete everything back to mark

C-y            yank, that is, reinsert killed text
M-y            scroll back through yanked text beyond 'C-y'

undo
C-X u        undo, recursively

file utilities
C-x C-f        find, open a file
C-x C-s        save a file
C-x C-w        save as

```

---

### Post by bryonak on 2009-07-20
Use a separate home partition.
This way, all your user data like bookmarks, application settings, themes, etc will be preserved across installs.

The only thing you have to do again is to reinstall the programs you used. In case of repository packages, this can be easily done with: ```
dpkg --get-selections > MY_PACKAGES

```

Save the resulting file on your home partition, reinstall the system partition and execute```
cat MY_PACKAGES | sudo dpkg --set-selections
```
This will mark the packages for installation. Now execute
```
sudo apt-get dselect-upgrade
```
and you should be ready to go ;)

For third party packages, I usually keep a folder with the .debs on my home partition and run ```
sudo dpkg -i
``` on them.


*Edit: in case you already saved the instructions, I've messed up the position of sudo in the 'dpkg --set-selections' part. Now the instructions work*

---

### Post by koenn on 2009-07-20
deleted

 wrong thread

---

### Post by Eviltechie on 2009-07-20
I write down a list of firefox plugins before I reinstall.

Other that those plugins, I don't want anything else on my computer. Thus a reinstall instead of an upgrade.

---

### Post by ramnarayan on 2009-07-20
i have a spreadsheet -with favorite packages and even dependencies, and every time i install afresh i put a date column and check against that, also have a remarks column and a b;lacklist column for software that really causes trouble (like dx4)


Also if you go to Synaptic --> File --> save Markings or save Markings As (use full state)

this it seems will allow you to know what has been installed, maybe at a later date when you want to figure out what all.

Have not used it but someone just told me on another thread.

---

### Post by MadCow108 on 2009-07-20
firefox plugins are easy.
just install the FEBE backup plugin. It can backup everything including your plugins.

My problem with the "copy the home directory" approach is that it clusters with hundreds of hidden folders and files with time of which I don't need more than a few.
My relativly fresh install has again 97 hidden folders... (sometimes I miss the windows registry, you at least don't see all the crap what colects in it :) )

So I usally just copy the most important stuff like data, opera profile and folder with my personal scripts and packages and delete everything else.
If it really was useful I'll remember to install it again sooner or later.

---

### Post by raronson on 2009-07-21
To elaborate a little on my previous post.  I use my own method called PunList.

```

PunList

PunList stands for "punctuated list."  It's a method that I've developed over the years
for organizing lists using punctuation and hierarchical outline format.

Key:

.list item
*.started item
%.stalled item
x.completed item
!.important item
#.note item
?.question item
@.answer item
< >.roll your own

A Couple of  Examples:


A PUNLIST ABOUT PUNLIST

?.what is PunList    
     @.a "punctuated" list that uses outline format for sorting information
.PunList is too complicated
     #.that's your opinion
?.what do I use PunList for
     @.for keeping track of and prioritizing information
           ?.how

SYSTEM NOTES

#.installed 64-bit Linux on 10 July, macbook4,1 (Lemmy)

x.patch/update system
     x.setup update manager
x.restore files from backup
     #.smb:///10.0.1.1/Airport/
          x.ajdust permissions
              #.scripts in ~/bin
x.get wireless working
     @.System --> Admin --> Hardware Drivers (deactive / activate broadcom, reboot)
x.set system & user prefs
     x.set up ~
     *.set up Gnome
     x.apply themes
*.install additional software
     x.xchat, eclispe, idle, gthumb, inkspace, gnome-do/docky
!.import music and setup rythmbox
     !.un-drm m4p tunes
     *.un-drm m4a tunes
         #.use sound converter
     .reformat iPod, use rhythmbox to manage
         @.mkfs.vat /dev/sdb3 (reformat iPod to FAT32)

```It keeps me sane...

---

### Post by myii on 2009-07-21
My short answer: debfoster
My long answer: If only I had the time to explain ...

---

### Post by bob-linux-user on 2009-07-21
I use a spreadsheet which also cross checks showing how you can do in Linux what you can in Windows. I also save a simple script to install all my applications when I upgrade. e.g.:-

sudo apt-get install wine
sudo apt-get install nautilus-image-converter
sudo apt-get install nautilus-actions
sudo apt-get install nautilus-open-terminal
sudo apt-get install nautilus-gksu

etc.

I call the file Setup.sh

---

### Post by dutchhome on 2009-07-22
Its great to hear what others are doing.  This is something I always think about whenever I set up a new machine or rebuild an old one.  I had hoped there was a tool designed for this, but its a complicated problem to solve with a dedicated app.  Personally, if I rebuild I typically keep the old HD contents around for a long time "just in case" and rebuild everything as new.  I get most of it, but there are always things I think about months later that I know I've seen before but were a pain in the butt to track down.

@raronson: I have to say I really like your solution.  Since your post I've been playing around with Tomboy.  I now have my work laptop sync'ed up with my workstation at home using sshfs.  This is some cool $#!*.  I'm not sure I'm ready to use your organization system, but I can appreciate why you developed it.  I've been busy documenting all the little things I can remember, why I wanted it, and a link to the original source when possible.  Would be nice if it would automatically publish itself on the web and my notes and tricks would be readily accessible to anyone.  I know it outputs to html so maybe I'll rig something up.

Jon

---

### Post by toupeiro on 2009-07-22
1.  I keep long CLI command histories
2. things in /var/log
3. a pretty good memory.


on production servers, I'm much more thorough.

---

### Post by raronson on 2009-07-22
> **dutchhome said:**
> 
@raronson: I have to say I really like your solution.  Since your post I've been playing around with Tomboy.  I now have my work laptop sync'ed up with my workstation at home using sshfs.  This is some cool $#!*.  I'm not sure I'm ready to use your organization system, but I can appreciate why you developed it.  I've been busy documenting all the little things I can remember, why I wanted it, and a link to the original source when possible.  Would be nice if it would automatically publish itself on the web and my notes and tricks would be readily accessible to anyone.  I know it outputs to html so maybe I'll rig something up.

Jon

Thanks.  PunList closes a necessary hole that you and I (and I suspect many others) have come to realize:  how do you keep track of changes to a complex system?  I've actually coded front-ends and things of the sort to process PunList, but I've long since abandoned that idea, as I have to install my own software on the system I'm working on first before I can start making notes about what I'm doing--while plain text is already available and works on every system.  In the past I used gedit in tabbed form to open up my multiple note files through a script, but now I just condense everything to Tomboy.

PunList is just something I've come up which makes sense to me (I was actually doing it as early as junior high school in my notebooks).  I wouldn't expect it to be the solution for everyone, but it really doesn't get much easier.

---

### Post by HappyFeet on 2009-07-22
I've done so many installs of ubuntu/linux, that I don't need to write anything down. It's permanently etched in my brain, and second nature to me.

When I first started, I used to use notes, but those days are long gone.

---

### Post by Ascenti0n on 2009-07-22
I've considered the very same issue too, especially since moving over to a Ubuntu Linux distro which updates versions every six months, and I can't not let a version swing by.

I keep a text file with Firefox extensions and app I've installed, but that is not enough.

I like the bash command file idea, it acts as both a list of apps installed and an automatic methos of re-isntalling them.

I think as long as you have access to Vim/Emacs, a backed up bash file and a PunList, you should have much of what you need to re-install.

---

### Post by koenn on 2009-07-22
I try to do as much customization as possible from the command line, so I can just copy the commands to a text file - either to run them again manually or wrap them in a script.

complex stuf usually gets documented in a wiki I have on one of my servers. The nice thing about a wiki is that you can hyperlink directly to other items that are related (like : nfs mounts on a workstation refer to nfs conf on a server), or to the web pages with the info that helped to set things up, etc. 
Problem is,  it takes some discipline, which I don't always have. 

I have a separate home partition, so user-specific settings should survive a re-install. Furthermore, I use LTS, and, IMO, an operating system should be upgradeable anyway so I don't reinstall all that often. I track changes more as  a disaster recovery plan or to be able to reinstall on a new machine in the future rather than to survive the 6-monthly  breakage cycle. 


that punlist looks like an interesting idea as well ..

---

### Post by automaton26 on 2009-07-22
First, I keep _all_ my non-media files under a single folder, which I regularly backup to DVD (encrypted), so I can quickly restore if my hard drive explodes.

Then, after each fresh install, I just have a few plain text files that list all my customizations, in order:

1_shell
2_networking
3_graphics
4_desktop
5_aptgetinstall
6_shortcutkeys
7_performance

---

