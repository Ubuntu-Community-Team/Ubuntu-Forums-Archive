---
title: "[SOLVED] slide show application"
date: 2008-11-24
forum: The Cafe
---

### Post by Silvernail on 2008-11-24
At the club xmas party I want to show a slide show of this years fishing trips. It is on my HD in directories by trip. Would like to keep it that way.

Is there an slide show application that will change directory when it encounters one and then back again? Also show some '.avi' movies.

I want to set this up to show thru a projector on the wall as background entertainment.

Would I be better off writing a script file to do all this?

TIA
Dave

---

### Post by meborc on 2008-11-24
check out [elisa media center]("http://elisa.fluendo.com/")... it looks good, plays movies, music and shows pictures... but i don't know how well the playlist function has been implemented...

if you still are in hardy heron, then check this ppa out [https://launchpad.net/~elisa-developers/+archive](https://launchpad.net/~elisa-developers/+archive) - you can just add the lines in that page to your sources file to get the latest and greatest elisa

unfortunately there is no ppa for intrepid, and the elisa version in the repos is not the latest

---

### Post by Silvernail on 2008-11-24
I tried the repos and it installed ok but did nothing. It is in the graphics menu, clicking on it show it in the tray at the bottom but goes away without any action.

From a command line it also does nothing, Not even showing an error.

Tried you ppa link. I'm in over my head on that one so I abandoned the attempt.

Tried your other link and got it to load and install. I get this error.

```
dave@gadabout:~$ elisa --help
Traceback (most recent call last):
  File "/usr/bin/elisa", line 28, in <module>
    load_entry_point('elisa', 'gui_scripts', 'elisa')()
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 277, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 2178, in load_entry_point
    raise ImportError("Entry point %r not found" % ((group,name),))
ImportError: Entry point ('gui_scripts', 'elisa') not found

```
What am I missing on my system?

Thanks for your help, where do I go from here?

Dave

---

### Post by init1 on 2008-11-24
I think Feh will do this
```

sudo apt-get install feh
feh picfolder/ -r -D 5

```
"picfolder" is the folder where your pictures are, and "5" is the delay between images. It won't do avi, though (you'll have to do that manually)

---

### Post by Silvernail on 2008-11-26
Thanks to everyone for their input.

I think I will use 'feh', I seem to have everything installed that I need to run it.

To be able to show the '.svi' files that 'feh' will not do, I am thinking about using a script.

```
#! /bin/bash
mplayer P6240073.AVI;
mplayer  P6240074.AVI;
feh . -r -D 5;

./slideshow.sh;
```

Call 'mplayer' to run the movies.
Call 'feh' to do the slide show.
Call this script again to do it again.

Problem -- I can not find any way to terminate 'feh' when it has finished going through the images so 'mplayter' will run again.


If this information is in the manual, I'm not picking up on what it is trying to tell me.

Has anyone got a solution or alternitive?

TIA
Dave

---

### Post by Silvernail on 2008-11-26
Need to marks this thread solved.

I found the answer to my problem with 'feh' in the help file but missed it in the manual.

I've corrected the script below if anyone cares.

```
#! /bin/bash
mplayer P6240073.AVI;
mplayer  P6240074.AVI;
feh . --cycle-once -r -D 5;

./slideshow.sh;
```

---

