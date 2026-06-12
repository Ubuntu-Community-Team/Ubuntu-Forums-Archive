---
title: "Contents of ~/bin/"
date: 2007-05-12
forum: The Cafe
---

### Post by weresheep on 2007-05-12
Hi all

I think one of the greatest things about GNU/Linux (and UNIX in general) is how easy it is to incorparate scrips into your daily work flow. Simple (and sometimes complex) tasks that other operating systems require full blown GUI programs for can be accomplished with a little Bash knowledge. With that in mind, whats in your ~/bin/ ?

Here are mine...

```

-rwxr-xr-x 1 gavin gavin  573 2007-04-01 09:14 banstatus
-rwxr-xr-x 1 gavin gavin  247 2007-04-20 15:06 bday
-rwxr-xr-x 1 gavin gavin  979 2007-04-17 11:14 filterlog
-rwxr-xr-x 1 gavin gavin  491 2007-05-06 12:09 gprune
-rwxr-xr-x 1 gavin gavin  464 2007-05-10 21:43 gsync
-rwxr-xr-x 1 gavin gavin  226 2006-11-22 19:23 money
-rwxr-xr-x 1 gavin gavin  910 2007-04-01 09:15 parselog
-rwxr-xr-x 1 gavin gavin  642 2007-05-05 16:07 profilelog
-rwxr-xr-x 1 gavin gavin  928 2006-11-23 09:43 rip
-rwxr-xr-x 1 gavin gavin 9493 2007-01-09 15:38 sum
-rwxr-xr-x 1 gavin gavin  329 2006-11-23 09:44 trimws
-rwxr-xr-x 1 gavin gavin 3392 2007-05-10 21:31 upmusic

```

banstatus - a script that looks through /var/log/fail2ban.log and lists the addresses that have been banned recently.

bday - loops through the entries in ~/doc/people/ and checks for anyone with a birthday this month. I am moving away from this one now that I've discovered 'remind' and so I'll probably delete it at some point.

parselog, filterlog - two scripts I wrote to filter /var/log/auth.log. Parselog extracts all the failed (or successful depending on argument) log in attemps and prints the date, time, username and address of each one. Filterlog works on the output of parselog to do such things as count the number of times a specific user name has been tried etc.

profilelog - uses parselog and filterlog to check for addresses that have made multiple attacks.

gsync, gprune - these two scripts keep my home folder synchronised between my computers.

rip, upmusic - music processing scripts. Rip runs cdparanoia to rip a CD and renames the WAV files into my naming convention. Upmusic is the largest script I have written. It loops through every directory in my music folder looking for WAV files and encodes them to FLAC. It also is responsible for renaming and tagging all the FLAC files.

money, sum - Money is a script that looks through ~/doc/money/in.txt and ~/doc/money/out.txt and prints my current money situation. Sum is a C program I wrote to sum up successive numbers from STDIN (I haven't figured out an elegant way to do it in a script yet) and is called by the money script to do the additon.

trimws - trims trailing white space from text files. A very simple script but its handy.


So thats it. I've recently pruned my bin directory to remove a lot of old and unused scripts but those listed above get used all the time. As you can see from the large number of security scripts I've written I was a bit paranoid when I first exposed SSH access to the internet :-D 

Anyone else fancy sharing?

---

### Post by victorbrca on 2007-05-12
I'm a noob... and the only thing I was able to write up to now was a little script that would remove all the empty space from my ripped cd songs, and rename it by crosschecking with a second file with the list of the songs that I downloaded from the Internet!!! 

  Looks something like this:

```
#!/bin/bash

rename 's/ *//g' *.ogg

cat tracks2 | sed 's/ /-/g' | sed 's/\.//g' | sed 's/-$//g' > tracks

d=1 ;
e=$(cat tracks | grep $d) ;

for i in `ls *.ogg` ;
   do mv $i $e".ogg"
   d=$[d+1]
   e=$(cat tracks | grep $d) ;
done
```


Vic.

---

### Post by jariku on 2007-05-13
```

jariku@uhura:~$ ls -l ~/bin
total 0
lrwxrwxrwx 1 jariku jariku 31 2007-04-23 20:54 ie5 -> /home/jariku/.ies4linux/bin/ie5
lrwxrwxrwx 1 jariku jariku 32 2007-04-23 20:54 ie55 -> /home/jariku/.ies4linux/bin/ie55
lrwxrwxrwx 1 jariku jariku 31 2007-04-23 20:54 ie6 -> /home/jariku/.ies4linux/bin/ie6

```

---

### Post by pmj on 2007-05-13
Well, I write my scripts in Python, but I hope I can still reply in this thread. :)

I have:
a batch renamer of zip and rar files to cbz and cbr (comic book archives)
a script that extracts ebooks hidden in jpegs. Yes, I have use for this. Really.
a script I use in Nautilus that mounts RAR files
a script that creates SFV files out of the checksums it finds in the names of the files in the directory. Useful for anime.
a script that creates a playlist for the music files in the directory
a simple GUI SFV checker
a script that creates a web gallery for the image files in the directory. I'm sure I'll have need of this one some day...

---

### Post by Mateo on 2007-05-13
Why not put them in /usr/local/bin?  In ~/bin you have to stare at the directory every time you open it up.  For me that's no good.  Good looking scripts though.  here's my /usr/local/bin:

```
-rwxr-xr-x 1 matthew matthew   536 2007-03-14 09:20 autopuz
-rwxr-xr-x 1 matthew matthew   141 2007-04-18 10:41 binarycreate
-rwxr-xr-x 1 matthew matthew    85 2007-05-12 23:35 bit
-rwxr-xr-x 1 matthew matthew   184 2007-05-12 22:12 bitqueue
-rwxr-xr-x 1 root    root       43 2007-05-01 09:05 buffymud
-rwx------ 1 matthew matthew   175 2007-02-24 00:15 economista
-rwxr-xr-x 1 matthew matthew   272 2007-05-10 01:24 monster_backup
-rwxr-xr-x 1 matthew matthew   211 2007-04-19 21:36 moveavis
-rwx------ 1 matthew matthew   141 2007-01-28 21:53 playlist
-rwxr-xr-x 1 matthew matthew    39 2007-04-05 20:40 startadesklets.sh
-rwxr-xr-x 1 matthew matthew   276 2007-02-27 01:24 zombie_backup
```

autopuz: prints the daily crossword and sends a copy of the answers to my ~/Documents folder.  Instructions in my sig.

binarycreate: creates a usenet binary archive of a file.

bit: runs btdownloadcurses with my settings.

bitqueue: reads all of the torrent files in my ~/.downloads folder and downloads them one by one.

buffymud: logs on to a mud I used to play.

economista: downloads a newspaper from a website.  doesn't work anymore since the newspaper went subscription only.

monster_backup: backs up my website.

moveavis: finds AVIs in a directory and then removes everything else after moving them to ~/Video.

playlist: shows the playlists on my media player.

startadesklets.sh: delays the running of adesklets on startup.

zombie_backup: backs up a book i'm writing.

---

### Post by weresheep on 2007-05-13
[QUOTE=pmj]Well, I write my scripts in Python, but I hope I can still reply in this thread.[/QUOTE]

Absolutely, any language is fine. I am more interested in how people are customizing their environment through personal scripts and programs than learning about any particular language

[QUOTE=Mateo]Why not put them in /usr/local/bin?[/QUOTE]

Well, my scripts are personalised to work with my set up and my files and putting them in /usr/local/bin would mean exposing them to other users. Besides I don't mind having a ~/bin :D 


Some cool scripts there people, thanks for sharing.

-weresheep

---

### Post by PatrickMay16 on 2007-05-13
I have a few I made for myself.

gayload - automatically loads my preferred soundfont to my soundblaster live card, with some special options. (to save time typing the whole command out)

mkautobackup - archives and compresses the current state of my midi file collection, zsnes save state collection, and other small stuff, and puts it all in a folder on my desktop. I run that once a week... it's my weekly backup.

nutloader - automatically opens /etc/timidity/timidity.cfg in nano so I can edit the soundfont being used by timidity, and other options I might want to change in timidity.

cock-benis - starts qemu with my windows 98 disk image and some other options that I prefer to have it with.

---

### Post by picpak on 2007-05-13
I used to have a lot, but I've since turned them into aliases. All I have left is *list*, a script that lists the files installed within a package.

---

### Post by BoyOfDestiny on 2007-05-13
amiga-uade
A small script with rsync that gives me awesome amiga tunes from the folks that make uade.

dist-upgrade
When I ran the alpha version of various Ubuntu, just to update regularly

find_deps a small script to spit out dependencies of an app from ./configure (didn't write this one, found it on the debian maintainer guide site)

mycheckinstall
a small script that I never really finished, basically would run custom commands depending the app I just compiled (i.e. add package descreption to checkinstall etc...) As Ubuntu's repos have grown though, it's a small handful of apps that I compile from source...

QEMU
a script to launch qemu with appropriate settings

sync_files
rsync my games, music, videos, on to my "server box"

su_chroot
chroot script, currently running i386 version, but it may come in handy again if those ia32-libs aren't up to snuff yet ;)

:guitar:

---

