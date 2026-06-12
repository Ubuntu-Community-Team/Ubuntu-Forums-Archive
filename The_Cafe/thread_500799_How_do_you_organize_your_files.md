---
title: "How do you organize your files?"
date: 2007-07-14
forum: The Cafe
---

### Post by jordon on 2007-07-14
This topic has been discussed before, but moving all my important files from my Windows and Ubuntu desktops to my new Ubuntu laptop has made me think about this question more.

With all these files from my cluttered Windows XP desktop and my not-so-cluttered Ubuntu desktop coming onto this new computer, I've been thinking about the best way to organize them. It's common to organize files by type, which is what I've done. But I've also made more specific distinctions.

For example, I have ~/photos for images from my digital camera, and ~/images for all other images. I've created ~/music for my collection of ripped CDs and ~/audio for other audio, including music I've recorded myself. I currently have ~/video for both videos I've recorded myself (which I name according to a convention) and videos I've downloaded.

Should I follow the pattern and separate downloaded videos from videos I've recorded? Is it even worthwhile to distinguish between the sources of files? What do you think, and how do your organize your files?

---

### Post by fyllekajan on 2007-07-14
I usually save all my files in the ~/Desktop directory. Then when it gets too messy I do 
mv ~/Desktop ~/Desktop.old
mkdir ~/Desktop
:(

---

### Post by mdebusk on 2007-07-14
One of the first things I learned about storing stuff is that you can organize it one of two ways: to make it easy to get it in, or to make it easy to get it out.

Another of the first things I learned about storing stuff is that you should pretty much always choose the latter. The only real reason to store something is so you can get to it if you ever need it.

You're going to want to think about how you go looking for things. For example, when you're looking for a photo, do you care if you're the one who took it or if you downloaded it from flickr? If you do, then please store them that way; if not, maybe you will want to categorize them according to content (still life vs. animals vs. people, perhaps) or style (color vs. black-and-white, etc.).

My way is this: 
~/Pictures is for any visual stills. Within that directory I have directories for photos, artwork, etc.

~/Sounds is for anything that makes my speakers move. Within it I have directories for wavs, midis, mp3s, and so on.

~/Documents is for anything I've created in a word processor or spreadsheet.

~/Videos is for videos. I only have three or four in there right now, so there are no sub-directories.

~/eBooks is for (mostly) instructional PDFs I've snagged. In it there are directories for programming (and within that are directories for rexx, perl, python, c, and so on), Linux how-tos (I'm a n00b),  hypnosis articles (I'm a hypnotist), sudoku puzzles, and the like.

~/abcs is for "sheet music" written in abc format. I've been meaning to learn to read it. Gotta pick up my guitar, banjo, and mandolin and get back into practice.

~/learning is my scratch pad area for whenever I'm fumbling with something new. I'm a little embarrassed to admit it's empty right now.

I do it this way because that's how I think of something when I want to go looking for it. You may or may not have the SAME pattern, but you have SOME pattern that you tend to follow when searching. Make it easy on yourself.

---

### Post by herbster on 2007-07-14
I keep all my "stuff" on a separate partition. I use the folders:

- eBooks (subdirs by genre)
- Games (basically for me just quake and ET subdirs with all kinds of mods, maps and configs downloaded over the years)
- linuxbackup
- MP3
- mystuff (personal pics, docs, etc.)
- ubuntu-customizing (with subdirs like icons, themes, loginscreens, splashscreens, wallpaper, etc.)
- Video (subdirs like TV, Movies, Docs, Stand-Up, etc.)

And the ones I use most often are of course added into the nautilus bookmarks for quick access.

---

### Post by Nekiruhs on 2007-07-14
Well, my most organized folder is my ~/Programming so here is my tree -d output
```
|-- Documentation
|   |-- Python-Docs-2.5
|   |-- Source for Review
|   |   |-- exaile_0.2.10
|   |   |   |-- debian
|   |   |   |-- images
|   |   |   |   `-- default_theme
|   |   |   |-- lib
|   |   |   |-- mmkeys
|   |   |   |-- plugins
|   |   |   |-- po
|   |   |   |-- scripts
|   |   |   |   `-- exaile_system
|   |   |   |-- sql
|   |   |   `-- xl
|   |   |       `-- media
|   |   |-- mutagen-1.11
|   |   |   |-- man
|   |   |   |-- mutagen
|   |   |   |-- tests
|   |   |   |   `-- data
|   |   |   `-- tools
|   |   `-- quodlibet-1.0
|   |       |-- browsers
|   |       |-- devices
|   |       |-- formats
|   |       |-- library
|   |       |-- mmkeys
|   |       |-- parse
|   |       |-- plugins
|   |       |-- po
|   |       |-- qltk
|   |       |-- trayicon
|   |       `-- util
|   `-- pygtk2tutorial
|       |-- examples
|       |-- figures
|       `-- images
|-- Finished -> /home/nekiruhs/bin
|-- Python Programs
|   |-- Finished -> /home/nekiruhs/bin
|   |-- Unfinished -> /home/nekiruhs/Desktop/Programming/Unfinished
|   `-- Workspace -> /home/nekiruhs/Desktop/Programming/Python Programs/Unfinished/Pre-Alpha
|-- Unfinished
|   |-- Alpha
|   |-- Beta
|   |-- Pre-Alpha
|   |   |-- LocateFE
|   |   |   `-- src
|   |   |-- Testing Grounds
|   |   |   `-- test2
|   |   |       `-- lol
|   |   |           `-- templates
|   |   `-- Xdelta Update System
|   |       |-- Backend
|   |       `-- src
|   `-- Release Candidate
`-- Workspace -> /home/nekiruhs/Desktop/Programming/Python Programs/Unfinished/Pre-Alpha
```
Tree is almost exactly like DIR in windows, to get it do sudo apt-get install tree

---

### Post by yabbadabbadont on 2007-07-14
Chronologically, using the last time I thought of them as the timestamp....   I have to reorganize constantly.   ;)  :D

---

### Post by AndyCooll on 2007-07-14
Since there are two of us (me and the wife) I store my personal stuff in my home folder and the rest in shared folders. My home folder contains mainly documents, so within it  I have folders such as "finances" etc. I've then created a "share" folder which sits on the server. This has folders such as "music", "photos" etc. These are then broken down further into various types according to the folder.

:cool:

---

### Post by Erik Trybom on 2007-07-14
When you organize files - at least on your own computer - these are my guidelines:

Not important: How to choose directory structure. Use the scheme that makes most sense to you. It doesn't matter much if you organize your files by type, by application or whatever, as long as you can find what you're looking for.

Not important: Keeping the system logical. If you have a separate pictures directory, but want to place pictures belonging to a certain project in the corresponding project directory, then do so. We want to make the picture easy to find, not to classify it in a scientific sense.

Important: USE the directory structure. NEVER place anything on the desktop, or any other default directory where things tend to gather. Every time you recieve a file, create a file or download a file, save it in the proper directory. Better yet, give it a proper name too. Sure, it may take you ten more seconds, but when you want to open it again it's there. I've seen friends searching their desktop for minutes, unable to find that one pdf file which they wanted. Don't let this happen to you.

Mdebusk has a good point: "The only real reason to store something is so you can get to it if you ever need it." Let me rephrase that:

*If it's important enough to save, it's important enough to save in the right location.*

---

### Post by tbroderick on 2007-07-14
Downloads - torrents, etc
Files - saved configs, docs,  wallpapers, etc
Mail - maildir
Movies - feature films
Music - symlinked to /media/hdb1/Music for mpd
Programs - src, svn, cvs, etc. compiled software
Scripts - various scripts
Videos -  pron, really
Work - not for my job

---

### Post by strabes on 2007-07-14
/media/data:

**documents** - any text or pdf file, no matter the type or genre - many many subfolders
**downloads** - anything that I download (not including saved images) - many subfolders - wallpapers go in downloads/desktop_customization/wallpapers
**images** - if it's an image file, it goes in here (unless it's a wallpaper, see above) - many subfolders
**music** - subfolders are music (for my collection) and ringtones, which I make with songs from my collection
**videos** - not too many videos in here so I don't have any subfolders.
**websites** - old websites that I've built in the past.

Under each folder are tons of subfolders. For example, in documents, I have "lyrics & tabs" for songs which I have printed out the lyrics or guitar tabs for, and "school" for any document relating to school. In the "school" directory are the names of the various schools I've attended, inside those are the semesters with names like "06fall" etc, under those are the class names like "ENGL101" etc, under those are folders for exams and projects for that class. I separate my ooffice note files for each test. For example, in my ENGL101 folder I have the following folders: Confessions, Inferno, King Lear, Odyssey, Paradise Lost. In each folder are various documents pertaining to each book.

I'm kind of an organizational freak so I have tons of subfolders for everything. It makes things really easy to find in the long run though. Since it would be a pain to click through all of the subfolders each time, I just make bookmarks in konqueror (I use KDE) for the common locations, like the my current school semester's folder, etc.

My organizational system works perfectly for me and I never have problems finding anything, although I'm always open to new ideas.

---

### Post by bread eyes on 2007-07-14
With a computer. YUCK YUCK YUCK!

---

### Post by PrimoTurbo on 2007-07-14
I'm currently using Windows XP, but my general organizational scheme is the same.

Bittorrent - All bittorrent downloads, which are later organized
Downloads - Any other P2P or regular downloads
Music - sub-folders Albums/Songs/Unsorted
Videos - sub-folders Movies/TV
Files - sub-folders Apps/System/Work/Games

---

### Post by mdebusk on 2007-07-15
Something Erik Tryborn mentioned reminded me that I neglected to mention something about my attitude toward organizing.

I always download new files to my desktop. Why? Because I absolutely hate a cluttered desktop. If I put new downloads there, as opposed to a "downloads" directory where I can think "I'll work on that later", it'll bug me until I put it in its proper place.

---

### Post by wie6Ein0 on 2007-07-24
> **mdebusk said:**
> Something Erik Tryborn mentioned reminded me that I neglected to mention something about my attitude toward organizing.

I always download new files to my desktop. Why? Because I absolutely hate a cluttered desktop. If I put new downloads there, as opposed to a "downloads" directory where I can think "I'll work on that later", it'll bug me until I put it in its proper place.

That's my thoughts exactly! Although, I do wish that an application existed that allowed a user to fully organize their media library as well as other files by either using tags, keywords, or categories. It would really help me because I could keep all of my television shows, movies, and clips in the same folder but have them separated by category using a program.

---

### Post by ezsit on 2007-07-24
Like most people responding, I have a directory structure within my /home similar to this:

/backups -- temp storage folder for organizing a weekly backup
/distros -- place to keep linux distros I'm playing with
/downloads -- just like it says
/docs -- work and personal files
/movies -- mostly flash animations
/music -- my own ripped collection
/pictures -- my family photos
/other -- misc. stuff
/winapps -- collection of windows software handy for those family and friends with that other OS
/wallpapers -- just what is says

I have an external USB hard drive that contains a backup of the hard drive in the computer.

---

### Post by drewtown on 2007-07-24
Home
    -Videos
        --TV
        --Movies
        --Random/Funny
    -Music
        --Artist
            ---Album
    -Images
        --Date(Default when it comes off the camera)
    -Web(development stuff)
    -Torrent (I store the .torrent just in case I need to use them again)

Pretty standard tree, I like organization, especially my music.

---

### Post by xpod on 2007-07-24
I could`nt be bothered right clicking to "create folders".........i  waited a year for Gutsy to come round and do it for me:)

I just keep most stuff like photos & videos etc in an nfs share now so we can all access it on the individual machines.It`s only family photos & videos etc and nothing fancy.

---

### Post by Mr. Picklesworth on 2007-07-24
I have...

home/Documents (Stuff that is mine)
home/Documents/Software (Software that is mine)
home/Documents/Web (Web site I am working on)

home/Software (Software source code, sometimes already compiled programs, that is not mine. Either used as reference or compiled specially).

home/Media (Media that is not mine)
home/Media/Audio
home/Media/Images
home/Media/Video


Quite tidy.

What I really want, though, is an Archive button that I can press to have unused files and folders disappear from my way, but still be indexed by my search program, restorable and accessible as though they are still where they were. In my opinion, that would be the best way to get a search-based desktop without causing disorganized files or working against standards developed over the years.

---

### Post by Nekiruhs on 2007-07-24
Heres my layout, courtesy of the program tree (aliased to ls)
```
nekiruhs@Ubuntu:~$ ls -L 3
.
|-- 8434D43A.gpg
|-- Desktop
|   |-- Open Kix OS FTP Server.desktop
|   |-- Programming -> /home/nekiruhs/Programming
|   |-- XpDrive -> /media/sda1
|   `-- gridwars_0.0.0+20060309.orig.tar.gz
|-- FAHlog-Prev.txt
|-- FAHlog.txt
|-- FahCore_78.exe
|-- My Documents
|   `-- 523-Summer_Reading.doc
|-- My Music
|   |-- A
|   |   |-- All American Rejects
|   |   |-- All-American Rejects, The
|   |   `-- Avenged Sevenfold
|   |-- B
|   |   `-- Blue Oyster Cult
|   |-- C
|   |   |-- Children of Bodom
|   |   `-- Coldplay
|   |-- D
|   |   |-- Death Cab for Cutie
|   |   |-- Disturbed
|   |   `-- DragonForce
|   |-- E
|   |   `-- Eminem
|   |-- F
|   |   `-- F-Ups, The
|   |-- H
|   |   `-- Hoobastank
|   |-- K
|   |   `-- Kansas
|   |-- L
|   |   |-- Linkin Park
|   |   |-- LostProphets
|   |   `-- Lynard Skynard
|   |-- M
|   |   |-- Metallica
|   |   `-- My Chemical Romance
|   |-- N
|   |   `-- Nickelback
|   |-- O
|   |   `-- Ordinary Boys, The
|   |-- Q
|   |   `-- Queen
|   |-- S
|   |   |-- Shattersphere
|   |   |-- Styx
|   |   `-- Sugarcult
|   |-- Y
|   |   `-- Yellowcard
|   |-- test
|   `-- test2
|-- My Pictures
|   |-- 61266-compiz_fusion.jpg
|   |-- 61266-compiz_fusion.png
|   |-- Misc
|   |   |-- 160944315_59f9997051.jpg
|   |   |-- 200px-Lynyrdskynyrd.jpg
|   |   |-- ETC
|   |   |-- Skydome
|   |   |-- Ubuntu_wallpaper_by_ftpaddict.jpg
|   |   |-- gridwarslogo.png
|   |   |-- gridwarslogo.xcf
|   |   |-- kore.png
|   |   |-- media-playback-pause.png
|   |   |-- view1.png
|   |   `-- viewfinal.png
|   |-- snapshot1.png
|   `-- snapshot2.png
|-- My Videos
|   `-- RVB100.pls
|-- MyFolding.html
|-- Nautilus Scripts -> /home/nekiruhs/.gnome2/nautilus-scripts
|-- PDF
|-- Programming
|   |-- Applications
|   |   |-- IDEs
|   |   |-- glade-2.desktop
|   |   |-- kdevdesigner.desktop
|   |   `-- python2.5.desktop
|   |-- Documentation
|   |   |-- Python-Docs-2.5
|   |   |-- Source for Review
|   |   `-- pygtk2tutorial
|   |-- Finished -> /home/nekiruhs/bin
|   |-- Python Programs
|   |   |-- Finished -> /home/nekiruhs/bin
|   |   |-- QuadRatic.py
|   |   |-- QuadRatic.pyc
|   |   |-- Unfinished -> /home/nekiruhs/Desktop/Programming/Unfinished
|   |   |-- Workspace -> /home/nekiruhs/Desktop/Programming/Python Programs/Unfinished/Pre-Alpha
|   |   |-- YAY.py~
|   |   |-- gtktest.py~
|   |   |-- locateFrontEnd.py~
|   |   |-- locatefe.py~
|   |   `-- test.py
|   |-- Unfinished
|   |   |-- Alpha
|   |   |-- Beta
|   |   |-- Pre-Alpha
|   |   `-- Release Candidate
|   `-- Workspace -> /home/nekiruhs/Desktop/Programming/Python Programs/Unfinished/Pre-Alpha
|-- autosave
|-- bin
|   |-- easteregg
|   |-- fah
|   |-- gridwars~
|   |-- newpy
|   |-- newpy~
|   |-- syncmusic
|   `-- themeinfo
|-- client.cfg
|-- firefox_widgets_2.6
|   |-- AUTHORS
|   |-- BUGS
|   |-- README
|   |-- REVISIONS
|   |-- ff_widgets.glade
|   |-- ff_widgets.py
|   |-- form-widgets
|   |   |-- button.png
|   |   |-- checkbox-checked.png
|   |   |-- checkbox.png
|   |   |-- droparrow.png
|   |   |-- radio-active-checked.png
|   |   |-- radio-active.png
|   |   |-- radio-checked.png
|   |   |-- radio-disabled.png
|   |   `-- radio.png
|   |-- forms-extra.css
|   |-- forms.css
|   |-- graphic_installer
|   `-- install
|-- gtk-gnutella-downloads
|   |-- complete
|   |   |-- Eminem - Like Toy Soldiers.mp3
|   |   |-- LostProphets - Rooftops.mp3
|   |   |-- Lostprophets - 4 AM Forever.mp3
|   |   |-- Lostprophets - A Town Called Hypocrisy.mp3
|   |   |-- Lostprophets - Broken Hearts, Torn Up Letters And The Story Of A Lonely Girl.mp3
|   |   |-- Lostprophets - Can_t Catch Tomorrow _Good Shoes Won_t Save You This Time_.mp3
|   |   |-- Lostprophets - Everybody_s Screaming!!!.mp3
|   |   |-- Lostprophets - Goodbye Tonight.mp3
|   |   |-- Lostprophets - Wake Up.mp3
|   |   |-- Lynard Skynard - Free Bird.mp3
|   |   |-- Queen - Bohemian Rhapsody.mp3
|   |   |-- The Lostprophets - Last Train Home.mp3
|   |   |-- complete.tar.bz2
|   |   |-- lostprophets - burn burn.mp3
|   |   `-- lostprophets -To hell we ride.mp3
|   |-- corrupt
|   |   |-- Lynard Skynard - Free Bird.mp3
|   |   `-- Lynard Skynard - Free Bird.mp3.00
|   `-- incomplete
|-- machinedependent.dat
|-- nautilus-debug-log.txt
|-- pidgin_awn.so
|-- queue.dat
|-- unitinfo.txt
`-- work
    |-- core78.sta
    |-- current.xyz
    |-- logfile_03.txt
    |-- wudata_03.arc
    |-- wudata_03.bed
    |-- wudata_03.bxv
    |-- wudata_03.chk
    |-- wudata_03.dat
    |-- wudata_03.dyn
    |-- wudata_03.goe
    |-- wudata_03.log
    |-- wudata_03.pdo
    |-- wudata_03.sas
    |-- wudata_03.xtc
    |-- wudata_03.xvg
    |-- wudata_03.xyz
    |-- wudata_03CP.arc
    |-- wudata_03CP.arc.b
    `-- wuinfo_03.dat

78 directories, 103 files

```

---

### Post by mdebusk on 2007-07-28
I noted this on the re-read:

> **Erik Trybom said:**
> Not important: Keeping the system logical. If you have a separate pictures directory, but want to place pictures belonging to a certain project in the corresponding project directory, then do so. We want to make the picture easy to find, not to classify it in a scientific sense.

If it were I, I'd go ahead and use the logical system, and put symlinks to the pictures in the project directory. That way, if I wanted to use the same pictures in another project, I wouldn't have two or three copies of the same file.

---

