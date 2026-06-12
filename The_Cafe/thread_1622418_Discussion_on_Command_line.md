---
title: "Discussion on Command line?"
date: 2010-11-15
forum: The Cafe
---

### Post by Alpha101 on 2010-11-15
Simple question:

I've been messing with command line a bit, liking the apt-get command a bunch, but I still feel like I'm groping around to understand this thing.
I've gone onto the documentation site, as well as browsed the net and here to get a better understanding of everything, even found a -badass- teeshirt on thinkgeek.com that had an entire linux cheatsheet on it. Yet even now I feel like even though I can see and know the command, I dont quite know what to -do-.
I mean, sure I can make a directory, I can make a file, I can move files, I can even copy and do those things, but whats so advanced about that? I mean, the GUI allows the same thing.
So...honestly, what I'm asking is; is there a class or something I can take to maybe..I unno, find the more advanced method of command tools and their usages? Perhaps courses online? Teachers? Linux is a do-it-yourself thing, I understand that. But honestly even if you know all of these things, with the way GUI interfaces allow to do much the same thing, why try?

---

### Post by czr114 on 2010-11-15
Command line knowledge is a powerful tool, and will remain so for a long time.

Simple tools and powerful commands can be built upon a command line interface with relative ease. By contrast, abstracting tasks via a GUI involves much more programming, and offers much less flexibility. The GUI route is more code-intensive and requires interface creation for every task, whereas a command line app can simply look at an args[] array and do what it's told.

Likewise, giving verbatim instructions on the command line is much simpler. For example, to add a PPA, you'd type "sudo add-apt-repository ppa:<PPA NAME>", whereas through a GUI, you'd have to read through a description of where to find the right dialog, and how to interact with it. I've seen tutorials of the GUI regularly consist of many screenshots, which were all a substitute for a few simple verbatim commands in a terminal.

In a perfect world, we'd have infinite development resources, and could provide a GUI to do everything ever needed. In the real world, developers often must choose between adding new functionality and adding a GUI for existing functionality.

The best way to learn the command line is to use it. Courses and books might help if you're training to be a sysadmin, but for normal usage, don't shy away from command line instructions and tutorials when you have a use for them. Look at every step, and before moving on, try and understand what it does, and why it needs doing. The common tasks will begin to stick in your mind after that.

Memorizing a cheat sheet might give you some names of commands, but it's equally important that you know why they're useful, when they're used, and what real-world situations they apply to.

---

### Post by endotherm on 2010-11-15
I got a lot out of my schools unix administration class. some perl, some bash, and a whole lot of administration concepts.

---

### Post by jennybrew on 2010-11-15
I think with the terminal its one of those things where practice really does make perfect.
If you put the work in you will reap the benefits.

---

### Post by Alpha101 on 2010-11-15
> **czr114 said:**
> Command line knowledge is a powerful tool, and will remain so for a long time.

Simple tools and powerful commands can be built upon a command line interface with relative ease. By contrast, abstracting tasks via a GUI involves much more programming, and offers much less flexibility. The GUI route is more code-intensive and requires interface creation for every task, whereas a command line app can simply look at an args[] array and do what it's told.

Likewise, giving verbatim instructions on the command line is much simpler. For example, to add a PPA, you'd type "sudo add-apt-repository ppa:<PPA NAME>", whereas through a GUI, you'd have to read through a description of where to find the right dialog, and how to interact with it. I've seen tutorials of the GUI regularly consist of many screenshots, which were all a substitute for a few simple verbatim commands in a terminal.

In a perfect world, we'd have infinite development resources, and could provide a GUI to do everything ever needed. In the real world, developers often must choose between adding new functionality and adding a GUI for existing functionality.

The best way to learn the command line is to use it. Courses and books might help if you're training to be a sysadmin, but for normal usage, don't shy away from command line instructions and tutorials when you have a use for them. Look at every step, and before moving on, try and **understand what it does, and why it needs doing.** The common tasks will begin to stick in your mind after that.

Memorizing a cheat sheet might give you some names of commands, but it's equally important that you know why they're useful, when they're used, and **what real-world situations they apply to.**


On the first bold: But how do I begin to understand such? I understand that a file can be made, and simply put, that it's "making a file" more or less. How far must I understand to really get a concept?

Second bold: But...in my day to day usage, without a set objective as to what needs be done, it's like doing things on whim, to just see what it does. I've never been given a job where I can see where these things apply in real-world circumstances, and I feel that without it I'm lacking something.

---

### Post by whiskeylover on 2010-11-15
Get a good book on Bash. Learn a scripting language like python/perl. Get a book on networking.

---

### Post by czr114 on 2010-11-15
> **Alpha101 said:**
> On the first bold: But how do I begin to understand such? I understand that a file can be made, and simply put, that it's "making a file" more or less. How far must I understand to really get a concept?

Second bold: But...in my day to day usage, without a set objective as to what needs be done, it's like doing things on whim, to just see what it does. I've never been given a job where I can see where these things apply in real-world circumstances, and I feel that without it I'm lacking something.
Suppose you're installing Wordpress.

At some point, you'll probably be asked to fire off something like ' cd directory ; chmod -R 755 *'

What would that do?

A zero level of understanding would answer, "Install Wordpress."

A basic level of understanding would answer, "Set up permissions for Wordpress."

A complete level of understanding would answer, "Enter the installation directory, target all objects recursively, granting full permission to the user owner, read and execute permission to the group owner, and read and execute permission to other users (probably httpd running as nobody), so that I can do everything with my files, and the system can read them, serve them to the user, and access them for backup."

Complete understanding would begin with the understanding of the need to change the permissions in that directory. That would be accomplished by entering that directory with cd, and modifying permissions with chmod. The cd/chmod combo is your interface to filesystem permissions, with an easy syntax that's easily memorized once you understand what each part does, and why it's doing it.

Of course, you could right click the folder in Nautilus, click properties, tab to permissions, and use the checkboxes to accomplish the same thing. There's often more than one way to do it, and that's a good thing. In some situations, however, you won't have Nautilus, such as a hosting account intended for Wordpress.

Once you understand you're targeting a directory with a permissions modification, you could just as easily fire off 'chmod -R 755 /path/to/wordpress/directory', which would identify the same directory with the same permissions change, but without using a current working directory to identify the target.

If all you do is enter the command from a readme or an installation guide, you might understand that permissions are being set, but the command line will remain mysterious, as you'll remain unaware of why those permissions are being set, which objects are being affected, or how the command you're copying is affecting them.

For casual users, not systems administrators, it's a lot easier to gain understanding by asking why during the course of your normal usage. Over time, it will come to you more naturally than memorizing that cd changes directories, and chmod changes permissions. Even if you memorize those commands, the cheat sheet will leave you without understanding of how current working directories matter in the shell, how chmod operates, or why it's useful.

With full mastery of that example command, it's a breeze to transition it to other instances, such as 'chmod -R 700 /path/to/my/backup/directory', which performs a similar function, but limits object access to your account only.

In our hypothetical installation, when there is a problem with the script writing uploaded images, you'll intuitively know to find the image upload directory, and target it with world access, using permissions 777. When you're paying attention to security, a chmod -x on that directory will intuitively mean that nothing needs to execute in there, while preserving the read and write access necessary to make it work.

Linux howtos using the command line are opportunities for learning and understanding. Don't shy away from them, and don't go to step two until the code in step one makes as much sense as natural language.

---

### Post by Alpha101 on 2010-11-15
Czr114, you've honestly opened my eyes to something there.
I mean, you've literally lost me on most of the programming dialect you said, but..that makes me -want- to understand it.
I mean..hell with that way of doing things I could create a dummy account for my guests to use, but ensure they cant run certain things, perhaps even make things disappear completely. I never really...thought about it in that manner.
Maybe just having it shot out in a complex manner as you've explained helped me understand that.
I didn't even KNOW about these...755 things and 777...
Hmm.

How exactly, did you begin to understand all of this? I mean, what made you need to learn these things? Was there some reason you began learning into it? And how exactly did you go about it?

---

### Post by czr114 on 2010-11-15
For example, something like 755 refers to full/read+execute/read+execute on user/group/world. Each digit represents the permission state, with that digit arrived at through binary bit positioning.

For example, in binary, 001 (one in the one's position) means execute, 010 (one in the two's position) means write, and 100 (one in the four's position) means read. A read+execute would be 100+001 (binary) or 101 (1x4+0x2+1x1), which converted to oct/dec would yield 5.

5 lacks write, so to enable write access, you can change it to 7, or you can use +w, because both imply positive authority for the underlying concept of modifying an object.

If you never understand what write access is, or why it might be useful, then no amount of cheat sheet reading will help. In that situation, one might be able to recall how to add write access if asked, but they'll never have a chance to apply their knowledge for lack of understanding of when to do so.

By understanding what needs to be done and when, it makes the underlying commands more real and tangible, and less like memorized book trivia. When you understand that you're adding write access as you do it, the concept has a greater chance of sticking in your mind. When you need to add write access again, you'll be able to recall how to do so with greater ease, as you've done it before. If you were just copying and pasting without understanding, then all you're really building is your copy and paste skills - in that situation, you're not issuing your own add write command, you'd be copying and pasting somebody else's unknown-but-presumed-useful command, which doesn't build deep understanding.

The way I learned was by needing to do, which uses substantially different mental circuits than simply doing a step-by-step exercise, which is itself a step above chart memorization.

This is why so many compsci graduates have great recall, but are functionally useless for the first few years of their career. Current education theory in many compsci departments ends up teaching the test, which is why so many employers focus heavily on positive past work experience (Stanford CS, et. al. as the few exceptions).

I began learning it before university, because it genuinely interested me, which quickly morphed into a need to perform underlying tasks by instinct in order to reach the next level of understanding and ability in programming or systems management. When a user makes a mistake on step one, he can't proceed any further until he masters it. If he misses question one on a 100 question bubble test, he can still get an A+, even though his functional implementation would receive an F from the computer which wasn't ready for #2.

---

### Post by Alpha101 on 2010-11-15
Uhm..
Pardon my stupidity.

You should make a book.

And now I'm off to figure out things..too bad I have a server 2008 class in...an hour.
Which I havent done homework for.
Damnit.

---

### Post by juancarlospaco on 2010-11-15
L.P.I.+ is the answer

---

### Post by Alpha101 on 2010-11-15
Googling that right now also...As I do homework

---

### Post by 3Miro on 2010-11-15
Linux (and FOSS in general) is oriented towards functionality and not interface. When a program is made, first you have some library that does whatever you want it to do (i.e. edit an image file), then you make an interface to work with the library. Since CLI is by far the easiest to code, the interface becomes CLI interface. Only then would someone make a GUI to call corresponding commands on the CLI. As a result of that, GUI doesn't always address all the functionality of the system. (for contrast on windows, you always get the shiny interface first and only then try to connect the functionality behind the buttons)

Different distributions and desktop environments often have different GUI tools, however, those would never cover the entire system. All of Linux shares the same CLI and underlying libraries and all the functionality can be achieved from the same CLI (there are some very minor differences).

Simple example:
```
 cp /home/Downloads/*park* /home/Pictures/Park/ 
```
how would you do that with Nautilus or any other file manager.

There are other many administration things that can only be accessed via text files in the terminal: setting up SSH server, setting up NFS server (actually setting up pretty much any kind of server), changing the sytem time form UTC to Local, setting lm_sensors, setting individual user permission for who can turn the computer off or mount external drives and many others.

---

### Post by Alpha101 on 2010-11-15
> **3Miro said:**
> 
```
 cp /home/Downloads/*park* /home/Pictures/Park/ 
```how would you do that with Nautilus or any other file manager.




That code..looks like its meant to copy a "park" file from downloads and move it to pictures...correct?

edt-
I'm feeling incorrect..

---

### Post by Alpha101 on 2010-11-15
With this type of silence from the forums, I'm most definitely incorrect.

---

### Post by czr114 on 2010-11-15
> **Alpha101 said:**
> That code..looks like its meant to copy a "park" file from downloads and move it to pictures...correct?

edt-
I'm feeling incorrect..
The * is a wildcard. It matches anything.

The cp is a copy command.

What that command does is locate all files in /home/Downloads which contain 'park' in the file name, and places a copy in the /home/Pictures/Park directory.

The command would be highly useful when the goal is moving everything containing 'park' from downloads to a directory created apparently for organizing only those files.

It could be accomplished with a load of ctrl+click through Nautilus, with your brain acting as the wildcard match for locating the files containing 'park' in the file name.

When you want everything with 'park', you'd need to reach for a wildcard. With the wildcard mastered, '*park*' has a distinct meaning, and might be refined to '*park*.jpg' to leave 'park.zip' out of a photo directory in which it might not belong. That modification becomes seamless based on a greater understanding of the goal.

---

### Post by cgb on 2010-11-15
It would copy any file in the Downloads directory with the word "park" as part of the filename.  

eg: filenames like 1parkfun or 2parkforme would both be copied..

*looks like czr114 beat me to it and was more descriptive...**

---

### Post by 3Miro on 2010-11-15
> **Alpha101 said:**
> With this type of silence from the forums, I'm most definitely incorrect.

It takes all files that start with something, have a park in the middle and then end on something. Like:

today_in_the_park.jpg
park_afternoon.jpg
another_park_picture.jpg
someone_called_james_parker.jpg

Suppose you have a ton of pictures. If you have pictures that start with park, you can sort by name on a graphical file manager, then you can just copy them. However, you cannot sort by name in the middle. Actually now I think that Dolphin may be able to do that, so this is probably not the best example, but you can make more complicated examples with file names.

---

### Post by endotherm on 2010-11-15
> **juancarlospaco said:**
> L.P.I.+ is the answer
I need to look into the LPI. I need a new cert.

---

### Post by Alpha101 on 2010-11-15
Czr,cgb,3mir

-Dayum.
Okay so the ** means wildcard, and refining it to .zip or .jpg will refine the copy, this allows me to now *NOT* have to ctrlclick things and run everything automatically..

Badarse.EDIT-Fixedtheswearword

See? These are things I'd have never known had I not gotten on this forum.

---

### Post by mcduck on 2010-11-15
> **Alpha101 said:**
> Simple question:

I've been messing with command line a bit, liking the apt-get command a bunch, but I still feel like I'm groping around to understand this thing.
I've gone onto the documentation site, as well as browsed the net and here to get a better understanding of everything, even found a -badass- teeshirt on thinkgeek.com that had an entire linux cheatsheet on it. Yet even now I feel like even though I can see and know the command, I dont quite know what to -do-.
I mean, sure I can make a directory, I can make a file, I can move files, I can even copy and do those things, but whats so advanced about that? I mean, the GUI allows the same thing.
So...honestly, what I'm asking is; is there a class or something I can take to maybe..I unno, find the more advanced method of command tools and their usages? Perhaps courses online? Teachers? Linux is a do-it-yourself thing, I understand that. But honestly even if you know all of these things, with the way GUI interfaces allow to do much the same thing, why try?

If you ask me, the real power of command line comes from the ability of doing very complex things with a single command, and furthermore, combining simple commands into even more complicated scripts.

And of course, at least in Linux, the large amount of available command-line based programs which can be added to these scripts to get almost endless amounts of functionality.

For example I have a simple script that downloads RAW pictures from my camera, creates JPG images out of them using correct color profiles & settings, resizes & compresses the images for web use and creates thumbnails out of them, builds a multi-page web gallery and a petty index page out of them (using EXIF data from images for titles) and uploads everything into my web site.

Sounds very complicated, but I really don't even have any programming skills, this was just something I did when I wanted to learn shell scripting, and all the complicated things are actually handled by ready-made programs (UFRaw for RAW to JPG conversion, Imagemagick for rest of the image processing, exiftool to read the metadata, awk for some processing of the metadata and file names, and of course some built-in stuff from the shell).

So, with very little actual programming skills you can create really complicated tools to do exactly what you want. Try combining graphical apps to work together this way, and you'll realize why people still like using CLI for many things. :D

Besides, it's often quicker to pop open a terminal and run some command than it would be to open a graphical tool and navigate through it's options to do the same task. Not to even mention repetitive tasks, which can easily be scripted to work automatically.

---

### Post by paulsarmiento on 2010-11-15
Hi,

Working either in the command line or gui doesn't really matter. What matters most is where you effectively get the job done. Most of the time, the command line will really help you get ball rolling.

By getting inclined in the command line really gives you the full capability of the program just like what 3miro posted

> 
Suppose you have a ton of pictures. If you have pictures that start with park, you can sort by name on a graphical file manager, then you can just copy them. However, you cannot sort by name in the middle. Actually now I think that Dolphin may be able to do that, so this is probably not the best example, but you can make more complicated examples with file names.


---

### Post by 3Miro on 2010-11-15
There is a really powerful command that I found somewhere on this forum. Suppose that you mess up the permissions on a whole bunch of files. How do you fix that? You can recursively chown, however, files usually have 644 permissions while folders have 755. Here is a command that will start form the current folder, then go in recursively and change the permission of all files and folders to 644 or 755 respectively:

```
 find .  \( -type d -exec chmod -v 755 '{}' \; \) -o \( -type f -exec chmod -v 644 '{}' \; \) 
```

If you have many levels of sub-folders, this can be a real nightmare on a GUI file manager.

---

### Post by nothingspecial on 2010-11-15
Don`t use X

Boot your computer, at the login screen hit Ctrl - Alt - F1

type ```
sudo service gdm stop
```Then start computing.

It took me a few weeks to do this, I always hit Ctrl - Alt -F7 to get back to the gui, for one reason or another. The important thing for me was to find apps that do what I usually do. So here goes.

Music - cmus (a full featred music player)
           mplayer ( all you really need - with aliases)

Video - mplayer (again.... - you don`t actually need X to watch video)

email - alpine (much easier to configure than evolution)

images (photos etc) - fbi

torrents - rtorrent (so good, I use this on X systems)

downloads - wget

irc/chat - irssi/bitlbee (irssi does the irc bit but with bitlbee you can have most chat clients plus twitter and facebook)

browser - elinks/links2 (elinks is THE text browser but it doesn`t support images, links2 supports images but doesn`t have the features of elinks)

cd ripping - abcde

media file conversion - ffmpeg / mencoder / sox

ipod - gnupod (again, you need aliases to make this efficient)

games - bsd-games (my kids love boggle, the older one loves the text based adventure games)

Once you have your basic computing needs covered, without X, you will start to learn the cli. cd this and mkdir that and so on and so forth untill you are a cli master.

I would suggest a basic grip on find, sed and grep

[http://www.thegeekstuff.com/2009/03/15-practical-linux-find-command-examples/](http://www.thegeekstuff.com/2009/03/15-practical-linux-find-command-examples/)

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

[http://regexlib.com/CheatSheet.aspx](http://regexlib.com/CheatSheet.aspx)


With these "powers", you don`t need a gui.

****** Disclaimer........ I don`t have a text only (non gui) system. I just choose not to use it. If I want to, I can start gnome with full compiz (the cube et al). It`s just that after starting getting interested in this ...... I tend not to.............

I am in no way an expert in this, however, this wo/man (99% positive kmandla is a man, but.....) is

[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)

---

### Post by Alpha101 on 2010-11-15
Hmm...I'll look into it when I get home, almost done with class so it's gonna be a long night of work on Linux.

---

