---
title: "Does anyone know any apps that need a new frontend"
date: 2009-03-16
forum: The Cafe
---

### Post by jimi_hendrix on 2009-03-16
so i want to learn a gui toolkit for linux, but i cant think of any apps that need a good frontend?

i have been told wine and apparmor need one, but any other suggestions?

---

### Post by MikeTheC on 2009-03-16
... *Gimp?* ...

*runs out of thread*

---

### Post by cmay on 2009-03-16
i plan on when i get to GUI programming(if ever) that i will create a gui version of wc
there is many of the small commandline tools i suspect could be made into gui versions if as long as it only for the practice.

---

### Post by jimi_hendrix on 2009-03-16
> **cmay said:**
> i plan on when i get to GUI programming(if ever) that i will create a gui version of wc
there is many of the small commandline tools i suspect could be made into gui versions if as long as it only for the practice.

i would want a slightly more complex program...so i could contribute a little more than a gui for cd xD

---

### Post by vishzilla on 2009-03-16
I know there are front-ends for rtorrent, but its a fantastic CLI app. Why not give it a shot? ;)

---

### Post by bashveank on 2009-03-16
A Linux gui for ffmpeg, something along the lines of VisualHub for the Mac, would be amazing.

---

### Post by cmay on 2009-03-16
there is a small program i would like to have a GUI for. its called something like youtubedownload but i cant remember it. its a commandline app that should download you tube videos but i could not get it to work. i would love to get a application that could download some music videos from you tube or google video for that matter. ( i assume its legal to download those)

---

### Post by treesurf on 2009-03-16
> **bashveank said:**
> a linux gui for ffmpeg, something along the lines of visualhub for the mac, would be amazing.

+1

---

### Post by Mehall on 2009-03-16
Make an LCARS Window Manager!

---

### Post by Joeb454 on 2009-03-16
Make a front end for bash :)

[/sarcasm] ;)

---

### Post by Skripka on 2009-03-16
delete pls.

---

### Post by Skripka on 2009-03-16
> **MikeTheC said:**
> ... *Gimp?* ...

*runs out of thread*
bam 

=D> =D> =D> =D> =D> =D> =D> =D>

---

### Post by bsharp on 2009-03-16
FFmpeg would be good.

YATM would be even better. I use it to slow down songs so I can learn difficult drum/guitar parts and it's a hassle to use it from the command line. A gui would be so much easier.

---

### Post by bikeboy on 2009-03-16
pdftk. I believe there's a Windows GUI, and a Linux one would be very handy to help with the intricacies of the program. Would likely also increase the usage of this mighty useful little program.

---

### Post by jimi_hendrix on 2009-03-17
> **Joeb454 said:**
> Make a front end for bash :)

[/sarcasm] ;)

i think someone in PT was working on that at one point a while back

---

### Post by SunnyRabbiera on 2009-03-17
I would like to see a new frontend for xmame, KXmame seems dead and the gmame project isnt as good.

---

### Post by jimi_hendrix on 2009-03-17
i will start with yatm because it is simple

---

### Post by ugm6hr on 2009-03-17
How about a GUI for disk label changing (mlabel, e2label etc).

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

A nautilus / thunar plugin would be even nicer :)

---

### Post by spupy on 2009-03-17
What is YATM?

Also, do you people realize that ffmpeg has an insane amount of options.
The highlight of creating a GUI for a command line program shouldn't be to just stuff all the options in an interface that will afterwards look bloated and as confusing as the CLI version.
I would like to have the most-used options presented in a more newbie-friendly manner, while the rest is somewhat hidden from the eyes of the beginner, but still there for the hands of the advanced users.

---

### Post by bashveank on 2009-03-17
> **spupy said:**
> What is YATM?

Also, do you people realize that ffmpeg has an insane amount of options.
The highlight of creating a GUI for a command line program shouldn't be to just stuff all the options in an interface that will afterwards look bloated and as confusing as the CLI version.
I would like to have the most-used options presented in a more newbie-friendly manner, while the rest is somewhat hidden from the eyes of the beginner, but still there for the hands of the advanced users.

I think VisualHub is a great example of this. Shame the developer "resigned."

---

### Post by jimi_hendrix on 2009-03-17
> **spupy said:**
> What is YATM?

basically a mpeg player that lets you slow mpegs down and stuff
> 
Also, do you people realize that ffmpeg has an insane amount of options.
The highlight of creating a GUI for a command line program shouldn't be to just stuff all the options in an interface that will afterwards look bloated and as confusing as the CLI version.
I would like to have the most-used options presented in a more newbie-friendly manner, while the rest is somewhat hidden from the eyes of the beginner, but still there for the hands of the advanced users.
thats why i picked YATM...it doesnt have a lot of options

---

### Post by pelle.k on 2009-03-17
> there is many of the small commandline tools i suspect could be made into gui versions if as long as it only for the practice.

I really think it's a great idea to learn wxpython/pygtk or whatever, but when it comes to "front-ends", making a gui to a command line tool is often the most horrible approach. It's why there was (getting better day by day) so many crappy GUI apps back in the early linux days. People were just tacking GUIs to popular cli tools, and tried to parse output from stdout to make any sense of what was happening.

What you preferably should do (when writing any app) is to make a "lib" wich has the core functionality, with a pretty API, and then you may write a CLI and/or a GUI part which accesses the "lib".
In the case of python, you already have many libs (although you may write new ones if you want to), like gstreamer to control audio playback (without using a command line audio player through python) and lots of other libs like "os" (copying, opening, reading, writing etc) without using say /bin/cp, /bin/cat and wrestling bash or any other command line tool.

I hope that made some sense, even though it's much more clear when you actually have some programming experience.
Let me give you an example. In the case of "arch linux" there's a package manager called "pacman". It's a command line tool, built on top of the **libalpm** library, which has the core functionality.
The ugly approach, would be to call /bin/pacman from python, parsing the output from stdout trying to figure out if an action did succeed etc. The good approach would be to access libalpm directly, from your GUI app, and get rid of the middle man (pacman, the cli tool).

jimi_hendrix, i really do wish you the best of luck though :)

---

### Post by jimi_hendrix on 2009-03-17
> **pelle.k said:**
> called "pacman". It's a command line tool, built on top of the **libalpm** library, which has the core functionality.


yarout ftw :D

i will try this on the gui i try after yatm...yatm is small enough to work well

---

### Post by Bodsda on 2009-03-17
> **cmay said:**
> i plan on when i get to GUI programming(if ever) that i will create a gui version of wc
there is many of the small commandline tools i suspect could be made into gui versions if as long as it only for the practice.

Its called youtube-dl and i plan on doing something similar when i get finished with the C++ tuto's and start on GTK tutorials, im unsure why you have had problems with it, it works perfectly for me, as long as you are not blocked from a video because of your region it should work fine.

```
youtube-dl full/url/goes/here/
```

^^ will download the video at the address in flv format

---

### Post by billgoldberg on 2009-03-17
> **Bodsda said:**
> Its called youtube-dl and i plan on doing something similar when i get finished with the C++ tuto's and start on GTK tutorials, im unsure why you have had problems with it, it works perfectly for me, as long as you are not blocked from a video because of your region it should work fine.

```
youtube-dl full/url/goes/here/
```

^^ will download the video at the address in flv format

ffmpeg gui = winff

There is already a youtube download gui, but it does more than just download the .flv, it lets you convert the flv to avi or mp3, ... called pytube.

That last one isn't under development anymore, but it still works.

-

how about a gui for cron jobs?

---

### Post by aeiah on 2009-03-17
> **bikeboy said:**
> pdftk. I believe there's a Windows GUI, and a Linux one would be very handy to help with the intricacies of the program. Would likely also increase the usage of this mighty useful little program.

+1 for pdftk. perhaps you could extend it's functionality with batch processing since its strength on the command line is really about incorporating it in bash/perl/python scripts

---

### Post by aeiah on 2009-03-17
> **billgoldberg said:**
> 

how about a gui for cron jobs?

[http://gnome-schedule.sourceforge.net](http://gnome-schedule.sourceforge.net)

---

### Post by bsharp on 2009-03-17
> **jimi_hendrix said:**
> i will try this on the gui i try after yatm...yatm is small enough to work well

I can't wait. I've been wanting something for this for a while but lack the skills to do it myself (for now ;))

---

### Post by Polygon on 2009-03-17
start small, dont just jump into stuff like wine and apparmor.

i vote vobcopy, if someone doesn't make a gui for it, i will eventually =)

---

### Post by Chilli Bob on 2009-03-18
GPBabel works brilliantly, but is a pain to use.  It could really use a GUI.

[http://www.gpsbabel.org/](http://www.gpsbabel.org/)

---

