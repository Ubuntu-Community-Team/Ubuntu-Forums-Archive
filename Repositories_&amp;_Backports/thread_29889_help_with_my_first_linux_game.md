---
title: "help with my first linux game"
date: 2005-04-26
forum: Repositories &amp; Backports
---

### Post by necorium on 2005-04-26
as the time of my first linux OS approaches i find myself looking at games. now i know most of my windows games won't work but i'm talking about real linux games. i've found one which i really like the look of. the only problem is that when i go to the download page i see that there are different versions to download for different versions of linux. this really confuses me - there's no mention of ubuntu there either and i'm not sure which ones are close to ubuntu and that would work, the games download page is [http://www.wormux.org/en/download.php](http://www.wormux.org/en/download.php)  please can someone point me to the right version to get for ubuntu (i'm downloading the latest versionof ubuntu)

thanks a lot - you guys rock \\:D/

---

### Post by heimo on 2005-04-26
Here's a thread you want to look:
[http://ubuntuforums.org/showthread.php?t=5153]("http://ubuntuforums.org/showthread.php?t=5153")
 
I play games very rarely, but I really enjoy some tucracing (tucracer) when I want to relax. Avaiable in Ubuntu repositories.
```
 sudo apt-get install tuxracer
```
 
EDIT: Oh... and you don't want to miss xbill.

---

### Post by fordfan753 on 2005-04-26
Download the source (.tar.bz2) file.
Extract it using...

$ bzip2 -d [file]
$ tar -xvf [file]

Then
$ cd [extracted directory]
$ ./configure
$ make
$ sudo make install

This is the method used to install 90% of source files, hope it helps.

---

### Post by fordfan753 on 2005-04-26
[QUOTE=fordfan753]
$ bzip2 -d [file]
$ tar -xvf [file]
[/QUOTE]

Instead of 
$ bzip2 -d [file]
$ tar -xvf [file]
a lot of source packages are .tar.gzip format
this requires
$ gunzip [file]
$ tar -xvf [file]

---

### Post by heimo on 2005-04-26
[QUOTE=necorium]i'm not sure which ones are close to ubuntu and that would work
[/QUOTE]
 
Debian. You could try (at your own risk) to add these to /etc/apt/sources.list
```
deb http://download.gna.org/wormux/package/debian/ /
deb-src http://download.gna.org/wormux/package/debian/src/ / 
``` And running on terminal:
```
 sudo apt-get install wormux 
```

---

### Post by necorium on 2005-04-26
hmm.. i really don't understand any of that.
is there no way i can just download a game and unzip it?
this is starting to scare me..

---

### Post by necorium on 2005-04-26
what games come bundled with the latest version of ubuntu?

---

### Post by necorium on 2005-04-26
ok the bit i really understand is thta i must get the tar.bz2 file. thats understandable but i don't understand any of the code??

---

### Post by fng on 2005-04-26
there are a lot of games that come with ubuntu :
nethack, tuxracer, supertux, frozen bubble, crack-attack, bastet, slashem, ...

How to install them?
Here is a how-to for frozen-bubble : [http://ubuntuguide.org/#frozen-bubble](http://ubuntuguide.org/#frozen-bubble)
It works the same way for all the above games.
And there are a lot more.

---

### Post by bored2k on 2005-04-26
America's Army is a must have FPS [if you don't know what FPS in gaming means, you don't need to play this]. YOu can get the linux version from americasarmy.com and simply in a command line terminal doing: sh filename.sh.

---

### Post by necorium on 2005-04-26
yeah i know fps games. i'm a quake III junkie. downloaded AA a while ago but i just hate the words AMERICA and ARMY too close to each other. also i like frantic deathmatches not simulation of what its supposedly like to be in americas army. Its sorta like propoganda when you think about it. Little kids play AA and wanna join the army cause its so fun to shoot people. 

On another note i'd like to thank all of you with your help. i think i'm starting to come to grips with things. can't install linux till next week - don't wanna risk messing up pc until presentations r over.. so long :( anyway i'm sure i'll be posting a zillion questions when i have it installed

later :-#

---

### Post by Zyphrexi on 2007-02-21
enemy-territory is good.

---

### Post by nubbe on 2007-02-21
Why not dl the static linux version, uncompress, make the file launch.sh executable, 

chmod +x launch.sh

and then run it with :

sh launch.sh

---

### Post by WW on 2007-02-21
Before Zyhprexi, the last post in this thread was from 2005.  If you follow the link provided by the original poster, you will find that ubuntu versions of the game are now available.

---

