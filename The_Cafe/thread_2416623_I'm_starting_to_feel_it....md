---
title: "I'm starting to feel it..."
date: 2019-04-12
forum: The Cafe
---

### Post by tempest-anastasia on 2019-04-12
This last week I've managed to put Linux on all my old systems and its installed great on all of them (Except sadly my current desktop, Some weird issue involving the DVI -> VGA converter maybe you can help me? [https://ubuntuforums.org/showthread.php?t=2416481](https://ubuntuforums.org/showthread.php?t=2416481) I'm having to run Ubuntu in a full screen VM there).

So I'm currently looking at my desktop and there are several terminal windows all open each connected to an old system. I don't think this is something I could have ever done on windows and it does feel pretty cool (Although my office is a total mess with all these old laptops and towers humming away). However I am starting to get that feeling that is best described by the LinuxChix logo. 

Trouble is this really is about the extent of my knowledge when it comes to this kind of thing. I know how to install it and how to use this to web browse and type the odd command in the terminal but I still have mountains to learn about everything else. 

So what I'm wondering is if there's any real point to doing this? Outside of the learning experience of course and making me feel a little more confident with SSH, which seems to be a pretty important skill. 

With their powers combined can these systems summon captain plan....uh....work together somehow?

Many thanks from a complete rookie.

---

### Post by jdeca57 on 2019-04-12
You're looking at it from the opposite side. First, there should be a need to do something and then you collect hardware and then you try to achieve whatever you wanted to do. Here, you say that you have this great network and ask what to do with it but that's not a question another person can answer. What do you do with a Windows computer? First of all, simply work... ;-)

---

### Post by tempest-anastasia on 2019-04-12
Well I probably do need to spend some more time getting to grips with the basics of the system and I do understand that. I want to try living in the command line for a few days soon just to really get to grips with it. I understand you can listen to music with it and web browse in a very limited sense and do just about everything the GUI can do if not more. It still feels very weird to me to be using it so much and I want that weird feeling to go away.

I think what I'm really looking for is more inspiration for projects out there, just as a topic of conversation rather than asking specifics about my network. Is distributed computing really much of a thing that people do or is that more that people use one machine for one task. It would be great to hear what people do with multiple machines. I do need to stop being so lazy with my computers and doing little more than web browsing though because I know they can do so much more. I just need to get my head in the right direction.

---

### Post by yetimon_64 on 2019-04-13
> **tempest-anastasia said:**
> ... I want to try living in the command line for a few days soon just to really get to grips with it. I understand you can listen to music with it and web browse in a very limited sense and do just about everything the GUI can do if not more. It still feels very weird to me to be using it so much and I want that weird feeling to go away...

If you are new to linux and want to get further into learning the command line one useful resource for that is [[COLOR=#0000ff]--here--[/COLOR]]("http://linuxcommand.org/index.php") (link in the blue text). [noparse]linuxcommand.org[/noparse] is a good _*starting point*_ for getting some skills on the command line and scripting.

If you do find you like working on the command line but don't like so much typing then "bash aliases" are worth setting up. A long command can be replaced with just a few characters saving much time and effort. By adding an alias to the file ~/.bash_aliases allows you to use such typing shortcuts. In case you haven't come across it already the "~" symbol indicates your home folder eg /home/<your-username>.

Some longer examples from my ~/.bash_aliases file ...
... this one is for taking a screenshot while using a console (tty consoles accessed with Ctrl + Alt + F#, where # is 1,2,3,4,5 or 6). The second one shown is for setting a time delay on the first one; note how I've strung the first alias within the second. Aliases can be "daisy chained" together for some interesting effects. This particular example requires the fbc and imagemagick packages installed to work.
```
alias fbc.tkss='sudo fbcat > ~/Screenshots/screenshot.ppm && convert ~/Screenshots/screenshot.ppm ~/Screenshots/screenshot_$(date +%d-%b-%Y_%I:%M:%S-%p).png && \rm ~/Screenshots/*.ppm >/dev/null 2>&1' 
alias fbctkss.dl='sleep 5 && fbc.tkss'
```
...these next 2 are for viewing images on the console; the second one finds many different common image types and lets me view them with the "fbi" (framebuffer image) package.
```
alias fbpic='fbi --noverbose -a >/dev/null 2>&1'
alias viewdir='fbpic $(ls $(find $PWD -maxdepth 1 -name "*.jpg") $(find $PWD -maxdepth 1 -name "*.JPG") $(find $PWD -maxdepth 1 -name "*.jpeg") $(find $PWD -maxdepth 1 -name "*.JPEG") $(find $PWD -maxdepth 1 -name "*.png") $(find $PWD -maxdepth 1 -name "*.PNG") $(find $PWD -maxdepth 1 -name "*.bmp") $(find $PWD -maxdepth 1 -name "*.BMP") $(find $PWD -maxdepth 1 -name "*.tif") $(find $PWD -maxdepth 1 -name "*.TIF") $(find $PWD -maxdepth 1 -name "*.tiff") $(find $PWD -maxdepth 1 -name "*.TIFF") $(find $PWD -maxdepth 1 -name "*.gif") $(find $PWD -maxdepth 1 -name "*.GIF") | sort -u)'

```
The last ones here are for video display on the consoles using mplayer (just 2 shown of the 10 sizes I've set up for mplayer output)...
```
# 960x540 output...
alias mplay.med='mplayer -vo fbdev2 -zoom -slang en -x 960 -y 540 -geometry 95%:50% -cache 16384 -cache-min 30 -cache-seek-min 50 -nolirc >/dev/null 2>&1'

# Full screen 1920x1080 output...
alias mplay.hd='mplayer -vo fbdev2 -zoom -slang en -x 1920 -y 1080 -geometry 95%:50% -cache 131072 -cache-min 40 -cache-seek-min 60 -nolirc >/dev/null 2>&1'
```
As you can see you can save yourself heaps of time and typing with aliases; my current alias count is about 670 :-).

A screenshot of video viewing on a console...
[ATTACH=CONFIG]283019[/ATTACH]

I must admit I've never had anything to do with distributed computing, but I do have a local network set up with 3 raspberry pi units and a laptop. Using VNC any of the rPi-s can have full desktop control of, and file access from, my laptop. VNC has limitations with passing video over the network so videos/files on my laptop can also be watched/accessed by any of the rPi-s over samba as well. Depending on your Ubuntu flavor VNC may not be usable without a lighter desktop installed, I either use XFCE or Mate with VNC and they work fine; I have heard the standard DE on Ubuntu may be a bit heavy for VNC usage. There may also be some security concerns with VNC if not set up right so very strong passwords should be used etc.

I mentioned samba in the previous paragraph; my laptop is located in my bedroom so with one of the rPi-s connected to the TV in the lounge I can watch videos/movies stored on my laptop on the much bigger TV screen.  With VNC I also often sit in the lounge on the large screen and do my web surfing and general computer usage. Using a much bigger screen in the lounge is the main example for network use here :-).

Enjoy exploring your new network and set up, cheers, yeti.

---

### Post by CatKiller on 2019-04-14
> **tempest-anastasia said:**
> Trouble is this really is about the extent of my knowledge when it comes to this kind of thing. I know how to install it and how to use this to web browse and type the odd command in the terminal but I still have mountains to learn about everything else. 

You don't need to learn about everything else. Not really. To the extent that you want to do a particular task, or a particular item doesn't work as you'd like, you might need to learn about that particular area, but there's no licence requirement before you're allowed to use your own computers.

Some parts are *interesting*, but which parts those are varies by person. That's why we have all this software at all: someone was interested enough to write a thing, and someone else was interested enough to contribute to the thing, and someone else was interested enough to use the thing. For each value of thing.

Just keep using your computers for whatever you use them for, and pick up new information and skills as you go. Then, pass on that information and the benefit of those skills, that you have and others lack, to those other people here.

---

### Post by freemedia2018 on 2019-04-14
If you really think about it, every interface is text-based, more or less. The titles of the icons, (some are more like symlinks than filenames, though still text-based) the alt-text of images on the web, the query you type into Google-- the URL that brings you to this forum, as well as the HTML and other text that creates the webpages (including this forum.) 

Strip away the mostly unnecessary (sometimes helpful!) graphical elements of any GUI, and what you have left is the text. That's what the term is-- a very efficient system, when you're doing repetitive tasks.

To someone less familiar, (familiarity takes time and practice) the command line seems like a waste of time, There are wonderful, time-honoured reasons for many of the things that dont make any sense. Why call it "ls" instead of list? Well, how many times do you want to type "list"? (tab-completion is wonderful.)

Remember that even the command line can be customised. Although with experience comes (for most) less desire to customise, you can enjoy creating links to commands just as you create icons with graphical applications. If you really prefer "list" to ls, you can make a link for it.

But even better than this, is you can learn to create (not just name) your own commands. It is less work to create command line utilities than graphical ones, mostly. You can even make easy graphical applications (simple ones) with a program like zenity or yad. This may (or may not) seem like it's getting way ahead. Sure, but if you started using computers in the days of DOS, rather than Windows, there wasn't as much to do. Creating a commmand to make a task easier was common. If you gain an interest in that, feel free to post about it on the forum, there are people who can help you learn. There are lots of tutorials as well. But this is something where you can start small, just creating simple tools to help with your computer work. The option is there. Good luck!

---

### Post by DuckHook on 2019-04-14
> **tempest-anastasia said:**
> &#8230;I want to try living in the command line for a few days soon just to really get to grips with it.
&#8230;
I think what I'm really looking for is more inspiration for projects out there,
&#8230;
It would be great to hear what people do with multiple machines.
&#8230;
I know they can do so much more.
I gather from the above that you wish to understand the power of the command line over the GUI:

[LIST]
[*]It is more compact and efficient. Simple example: command line jockeys can rename a mess of different files in one line without having to mouse through five different menus, select radio buttons, toggle switches, then end up having to type in the same search-&-replace parameters anyway.
[*]The above can be stored, easily retrieved and then run at will.
[*]One can string together a collection of already powerful command line functions into one awesomely powerful script doing actions too complex for GUI utilities to dream of matching.
[*]Using the command line gets you one step closer to the actual inner magic of the OS.
[*]Deleting a GUI and replacing it with a CLI-only environment can revitalize old HW and make them useful again. It also eliminates e-waste. It also saves you money. Not least, it is also deeply satisfying. My three servers are all rehabilitated boxes that would long ago have been put out to pasture were they running GUIs. Instead, they give me redundancy, backup, peace of mind, and collectively cost me less than $500 (mostly spent on big new HDDs). Not possible for three GUI machines.
[/LIST]
Consider using CLI machines for:

[LIST]
[*]File server
[*]Mirrored file server
[*]Backup server
[*]Torrent server
[*]VPN server
[*]Printer server
[*]NTP server
[*]Media server (eg MythTV backend)
[*]VM server
[*]OwnCloud server
[*]Web/e-mail server
[*]Gateway/router/switch/WIFI station
[/LIST]
None of the above require GUIs and the possibilities are almost endless. It is true that there is no "need" to use or to even understand the command line. But freeing yourself from the GUI gives you an added element of freedom, flexibility and power that you never even knew existed until you've been exposed to it.

You may be interested in the links in my sig: *A Great CLI Guide* & *Resources for Newcomers*

---

### Post by freemedia2018 on 2019-04-15
> **DuckHook said:**
> My three servers are all rehabilitated boxes that would long ago have been put out to pasture were they running GUIs.

At the moment I'm not running any old machines with a command-line only environment. I do think it's better to run a server without a GUI, but another nice thing about the command line is that even when you want to run programs like GIMP and IceCat (or whatever browser you like) you may find yourself sceptical of the bloated, resource-hungry GUI environments like GNOME and KDE. 

It's great to just drop down to a modest desktop (XFCE is friendly, and when you are used to the command line, even IceWM works a treat-- using virtually no resources at all) and allocate the ram to things like programs, not desktop jewelry. Though if you have extra ram to throw away, there's nothing wrong with the latter (if it makes you happy.) I would still recommend XFCE over the other large desktops, but it's up to you.

---

### Post by tempest-anastasia on 2019-04-15
Thanks for the comments guys, lots for me to think about!

So I had a long hard think about what is duplicated over my network, then it hit me! Roms!

I love retro gaming, I have roms on pretty much everything including my partners macbook. 

I've set up ubuntu server on my old acer netbook, found a guide on how to stop it going standby on lid close and how to turn off the screen remotely. Partner saw me turn off the screen from the other side of the room and now thinks I'm a hacker hehehe. I've FTPed some roms over and I've decided to treat myself to a raspberry pi 3 for the living room television.

Will I be able to open the roms remotely easily when I get the pi 3? Well I guess I'll find out :) 

This is a new way of thinking and I'll have to learn a lot before it starts to sink in but I'm sure this will be second nature soon :3

---

### Post by freemedia2018 on 2019-04-16
The main difference with a pi is the bootloader and installing the image. Apart from that, it should be very familiar (as much as Ubuntu is.)

For the most part, the command line is one of the things that is relatively consistent. So if you're comfortable with it on one system, it should be pretty familiar on others. Slight variations (in terms of what's installed and what's default) may occur. You'll now find that macOS is also pretty familiar, as it has a similar (more traditional UNIX) command line as Ubuntu. It even includes bash and nano.

---

### Post by 1clue on 2019-04-16
@tempest-anastasia,

It's very difficult to have equipment and then try to figure out a project to use all that stuff. You have mentioned 2 things that seem to be of interest to you so I'll focus on those:

Retro gaming is a thing, but I don't do it, so I can't help much. Where I live (USA) you legally need to own each ROM that you use. While I think it would be neat to play some of the old games, I don't think it's so neat that I'd want to buy a bunch of ROMs.

Command line:  Here I can help.

The corporate world has an incredible number of UNIX servers. Most of them are Linux. Almost every Linux server is headless and a large quantity have no GUI software at all. This includes not only traditional servers but networking equipment like firewalls or routers, or almost anything with a relatively large embedded processor. 

What I'm saying is that if you intend to use your Linux knowledge professionally, then it's a really good idea to know the command line.

So here's my advice for now:
[LIST=1]
[*]Turn off all the old devices for now.
[*]As you learn the command line, take notice of the types of things you want to do and what would make it easier.
[LIST=1]
[*]Someone already mentioned aliases.
[*]What doesn't work as an alias you might explore as a shell script.
[*]Then you might be interested in python or some of the other languages available.
[/LIST]

[*]You will want a good editor. On the command line there are really two:
[LIST=1]
[*]vim is a 'modal' editor. It's what I use.
[LIST=1]
[*]**sudo apt install vim-nox** gets you the full version of the non-gui editor.
[*]There are GUI versions but having used vim since 1996 or so I can't as yet figure out why I would want that version.
[/LIST]

[*]emacs uses control keys similar to apps you may be familiar with.
[LIST=1]
[*]I don't use that so I can't really help much here.
[/LIST]

[*]Both these editors have many extensions available.
[*]Both have a vast following.
[*]Both are comparable to any GUI programming editor in features and capability.
[*]Both allow you to incorporate Linux commands, your scripts or apps, and external plugins to facilitate your editing.
[*]There has been a (usually friendly) war going on for decades about which editor is better.
[/LIST]

[*]You will want a terminal multiplexer.
[LIST=1]
[*]This tool allows you to ssh into a remote system, and then split your ssh session into a number of 'windows' (think of tabs) which can each be further split into panes which are all visible at the same time.
[*]You can break out of the session and disconnect from your shell, meaning logout or timeout.
[*]You can reconnect from the same computer or some other computer, and then reconnect to your session.
[*]All your apps are in the same place, or in the case of jobs running they will have continued to run until they complete.
[*]You can create a configuration file on each server and when you start the multiplexer your favorite tabs will already be created and in the correct directory, possibly having executed some commands.
[*]There are two terminal multiplexers of note:
[LIST=1]
[*]**screen** is the older one. If you don't get too carried away then this one is probably fine.
[*]**tmux** is newer and more able to handle complex configurations.
[*]Neither is more capable
[/LIST]
[/LIST]

[*]As you learn things, you will discover more things you want to do or learn.
[*]Pick up a book (or ebook) on regular expressions (or **regex**). It seems like greek at first, but regex simplifies searching and modifying character data. It is pervasive in Linux, UNIX and programming in general. Regex knowledge will make your understanding of Linux and UNIX come easier.
[*]Learn about **git**. It's a source code control system. It lets you keep the same scripts on all your Linux boxes, and tweak from any of them.
[/LIST]

With respect to the command line:
Keep in mind that there is NOTHING you might need to do on a Linux server that can't be done on the command line.

Linux functionality is in libraries. These are compiled files of machine code loaded on your system. The GUI apps use these libraries, and the command line uses the same libraries. Typically the command line version is developed first because it's easier to develop. So unlike DOS commands being a small subset of what you can do in Windows, the only things you can't do on the command line are things that inherently require a GUI of some sort. Like a point-and-click video game, or photo editing. And actually there are tools to modify photos which do not require a GUI.

Linux owns the server market. If you go to top500.org, you will find that every one of the fastest supercomputers in the world run Linux. Every datacenter, every "cloud" has Linux and it has a lot of it. People who work with these systems do not lack any tools to get the job done. If you perceive a missing feature, then it's likely your knowledge that is incomplete rather than the feature.


With respect to interactive developer environments:

The whole IDE thing. It all started with an editor, and then somebody added a tool to it to make something easier to do, and they could do it from within the editor. Then they add another tool, and another and another. After awhile you have something like Eclipse or IntelliJ. They have almost every feature you would want for any purpose, especially if you include plugins.

That said, in my experience I rarely or never use most of those features. The best IDE is one which has every feature you need but none you don't. These IDEs not only have what I consider to be useless features, but they waste screen space giving me buttons for those features.

You can go to youtube for demonstrations, there are tons of them. 'vim, tmux, ctags' or 'emacs tmux ctags' is a good place to start.  Or use 'screen' instead of 'tmux'. Find out how your editor works. Become an expert in it, get a good set of tutorials and follow it to the end. Use those features every time. Learn how to shell out commands. Learn the commands which help you program in your chosen language. Get plugins that actually help you. Make your own scripts and plugins. You will have a very lean IDE made by you, which does exactly what you want. And it won't need a GUI.


I didn't intend for this to become a book. So I'll let you go now.

Good luck and have fun.

---

### Post by freemedia2018 on 2019-04-17
> **1clue said:**
> You can go to youtube for demonstrations, there are tons of them. 'vim, tmux, ctags' or 'emacs tmux ctags' is a good place to start.  Or use 'screen' instead of 'tmux'. Find out how your editor works. Become an expert in it,

And getting a serious text editor, like emacs or vim, will make you a very powerful user indeed. 

I do most of my coding in leafpad, the longest program I've written is about 2100 lines. With multiple tabs and a few other options, Geany makes a better IDE than leafpad, I'm sure. 

Neither of those are for the command line, but I thought I'd weigh in on the IDE thing since it was on the table.

The joke is there's an old war (rivalry) between vi ("vim") and emacs. The truth is people like the tools they like. I have no horse in the vim/emacs race, though I got farther with vim personally. These are not just text editors, they let you manage files and run code. Except leafpad. Leafpad is just a plain old text editor, with nothing fancy. You have choices, you'll figure out what you like.

---

### Post by 1clue on 2019-04-17
I'm not claiming that learning vim or emacs will make you a power user of some sort, I'm just saying that neither is lacking anything in particular.

I've been using Linux since about 1995, got serious in 1996. Started using it professionally in 1996. I started learning vim back in 96 too. Around 2000 or so I started using GUI systems on Linux.

Since then I've looked at almost every IDE that has come available that works on Linux, pay or free. IMO the GUI world tops out with Sublime Text 3 (payware) as a pure editor, and IntelliJ (payware) for an IDE. But in spite of having paid for a Sublime Text license, about half the time I'm using vim because its features are easier for the task at hand. Sublime works on Windows, Mac and Linux, and the licensing is per human. You can install it on any number of computers, even someone else's computer, and put the license in **your** user's account. Other people can use it too, but if they want to avoid the gentle reminders every now and then they need to buy their own license.

I "have a horse" in the race, but I don't try to put my favorite as an absolute best. One size does not fit all, and so it goes with high quality text editors in the command line. There are two very good options available, and they lack for nothing of importance if you want to learn to use the terminal.

Both of these editors have **evolved** for decades. I know of no other programming text editor that can make that claim, either curses-based or GUI, on any platform. They are not something that programmers use because there is nothing else to use, they are something that programmers use and have tweaked such that there's nothing else they want.

---

### Post by freemedia2018 on 2019-04-17
I'm waiting for a Python-based Vim-like thing.

I'm sure emacs is a better editor than vim, and that's not a troll (but this is...) but it doesn't matter as I only have 10 fingers, not the 16 required for emacs use. (I respect emacs, I just don't like its shortcuts.)

---

