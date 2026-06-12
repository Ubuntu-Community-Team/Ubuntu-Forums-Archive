---
title: "Cheat Sheet for new users."
date: 2006-11-18
forum: The Cafe
---

### Post by sunexplodes on 2006-11-18
EDITED 2007/03/19

My Cheat Sheet is essentially a cleaned-up version of some notes i've taken while learning to use linux. I'm releasing it because I think it might help some other noobs. 

It contains: a list of useful directories and files, a brief intro to the terminal, wireless networking with ndiswrapper, some recommended applications, and lots of other stuff.

[http://kyle.monoperative.net/cheat.html](http://kyle.monoperative.net/cheat.html)

Please feel free to suggest any good tips for basic config and use that i might be missing.

---

### Post by RudolfMDLT on 2006-11-18
Very nice! Thank you!

---

### Post by nickpaton on 2006-11-18
Excellent - thanks!

---

### Post by sunexplodes on 2007-02-12
I've made a pretty big update to the cheatsheet. Lots of new info, better formatting, more up-to-date. 

Hope somebody finds it useful.

It's an OpenDocument text file inside the archive.
[ATTACH]25164[/ATTACH]

---

### Post by C-A on 2007-02-13
nice, thanks!

---

### Post by lenn/art on 2007-03-02
Tnx! 

As a newbie i would recommend also to add this:
* how to mount (a hdd, a usb stick)
* what is su(do) and why? 
* some tips for windows users

* remove how to add something to the kernel - why whould a newbie do that?

---

### Post by sunexplodes on 2007-03-04
Those aren't bad ideas at all.

As for the modprobe question, it's included because it has to be done in order to set up ndiswrapper, which is something a lot of newbies are going to have to deal with, and it's nice to know what the commands you're using actually DO.

Anyway, the next revision is going to contain:

* how to mount (a hdd, a usb stick)
* what is su(do) and why?

 as you've suggested, and i'll definately compile a list of windows transition tips.

also:

* how to restore a verbose boot screen (like in dapper)
* a revised ndiswrapper section, as edgy makes it a bit more difficult
* getting back/forward mouse buttons working
* mounting and dealing with ipods

and possibly a couple more things.

---

### Post by castoroil97 on 2007-03-04
very good, this will be very helpful.

I have been very pleased with Ubuntu thus far, people like you make it even better!

Thanks again.

---

### Post by castoroil97 on 2007-03-05
I think I found an error under--
COMMON COMMANDS AND USAGE

Change to Parent Directory: cp .. 
Change directory: cp /directory 

should it be

Change to Parent Directory: cd .. 
Change directory: cd /directory

---

### Post by hyper_ch on 2007-03-05
It's nice :)

I use a mediawiki for my notes :)

For the commands it would be good to add what the -R (recursive) is doing... especially when you want to delete folders :)

---

### Post by tkjacobsen on 2007-03-05
you should add "updatedb" or "sudo updatedb" together with locate... Alternatively use

find . -name "hello.cpp"

or more general:

find path options "searchpattern"

path: "." means this directory and all subdirs.. use "/" to search entire system (SLOW)
good options are -name or -iname, the last is the same as the first but not case sensitive.
searchpattern should be exact - but wildcards are allowed using * like  "*.cpp"

---

### Post by sunexplodes on 2007-03-19
I've been working towards adapting the cheatsheet to html, but i've been a bit low on time lately, so it's somewhat incomplete so far. I'm going to keep working at it, so feel free to check back for updates.


[http://kyle.monoperative.net/cheat.html](http://kyle.monoperative.net/cheat.html)

---

### Post by Dirigo on 2007-03-21
Thank You!  I'm just getting started with Linux, too, and this will be very useful!

---

### Post by BLTicklemonster on 2007-04-09
> 4. Common Terminal Commands
Copy Files: cp /original/path /new/path
Delete: rm /file
[B]Change to Parent Directory: cp ..
Change directory: cp /directory[/B]
Rename a File: mv oldfilename newfilename
Find Files: locate keyword
Add Something to the Kernel: modprobe [whatever]
To get information on a command: man -k keyword
To fix broken packages: dpkg-reconfigure [package name, ex "xserver-xorg" or "gdm"]


Should that not be 

Change to Parent Directory: cd ..
Change directory: cd /directory


and add 

Make Directory mkdir /newdirectory (sudo mkdir /newdirectory where applicable)


perhaps, unless it's too early, and the coffee hasn't hit yet?


Great stuff, thanks for taking the time!

*edit: oh, castoroil97 already mentioned the cd stuff, sorry.

---

### Post by overdrank on 2007-04-09
> **sunexplodes said:**
> I've been working towards adapting the cheatsheet to html, but i've been a bit low on time lately, so it's somewhat incomplete so far. I'm going to keep working at it, so feel free to check back for updates.


[http://kyle.monoperative.net/cheat.html](http://kyle.monoperative.net/cheat.html)

Hi and thanks, great help and keep up the great work!=D>

---

### Post by battleshipterry on 2007-04-09
I had to say THKS this helps the learning curve and brings newbees from the dark side =D> 


Obi-wan has taught you well 8-)

---

### Post by nhandler on 2007-04-09
For changing the current directory in a terminal, you have cp written. I think you meant cd. Also, in order for the locate command to be any good, you need to perform a sudo updatedb. One last thing you could add is nano. In my opinion, nano is easier and more user friendly for people knew to the terminal than vi.

---

### Post by aleska on 2007-04-10
Excellent work!  

Agree completely with the Automatix sentiments.  Kyle, might you consider adding a link to [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) on your cheat sheet?  You can explain that for those folks who consider turning to Automatix just for codec / restricted format support, they can instead simply follow the straightforward instructions in the RestrictedFormats section of the Ubuntu Community Documentation site.

Thanks for sharing this!
-Aleska

---

### Post by aysiu on 2007-04-11
I've moved this to the Cafe, as it is more of announcement/discussion than a support request.

I've also extracted to [this thread](http://ubuntuforums.org/showthread.php?p=2425221#post2425221) the arguments about the validity of Automatix.

---

### Post by tscook on 2007-04-11
there should be more vi functions in there. At least i and a

---

### Post by BLTicklemonster on 2007-04-11
> **aysiu said:**
> I've moved this to the Cafe, as it is more of announcement/discussion than a support request.

I've also extracted to [this thread](http://ubuntuforums.org/showthread.php?p=2425221#post2425221) the arguments about the validity of Automatix.

lmao toss me in the frying pan for crying out loud. I voted #1 in there a while back, and support automatix, and on a new install of feisty, would have used it, but I never saw where it supported Feisty, so I did stuff myself. The first thing I did when I installed Feisty was go to google and look up automatix. I was in a hurry, and wanted stuff up right away. I'd done it myself without Automatix on the last dapper install, because I wanted to do it that way, but prior to that, I was an automatix junky. 


(wow, I just figured something out. if you type something in Firefox and it has red underlinings, right click it and add it to the dictionary, and it stops acting like you're stupid.)

---

### Post by Pacsun on 2007-04-11
Feel free to Digg his article at:

[http://digg.com/linux_unix/Ubuntu_Edgy_Eft_Cheat_Sheet](http://digg.com/linux_unix/Ubuntu_Edgy_Eft_Cheat_Sheet)

---

### Post by macogw on 2007-04-11
> **BLTicklemonster said:**
> Should that not be 

Change to Parent Directory: cd ..
Change directory: cd /directory


and add 

Make Directory mkdir /newdirectory (sudo mkdir /newdirectory where applicable)


perhaps, unless it's too early, and the coffee hasn't hit yet?


Great stuff, thanks for taking the time!

*edit: oh, castoroil97 already mentioned the cd stuff, sorry.
You'd probably want to leave the / off because if you're in ~ and try to
mkdir /movies
it'll try to put it up under / instead of as ~/movies, so it should just be
mkdir movies
ya know, unless you're wanting to use an absolute path from /

---

### Post by BLTicklemonster on 2007-04-11
Excellent point. I should have mentioned to cd mkdir /full path to directory i.e. 

```
sudo cd mkdir /usr/bin/laden/isa/jerk
``` 

or something.

---

### Post by Phatfiddler on 2007-04-11
cp != cd

Please make sure the change directory command is "cd" and not "cp"

---

### Post by Cariboo1938 on 2007-04-19
I think> /grub/boot/menu.lst would be another useful file to mention in your section "1. Useful Files and Folders". 
Here are some other useful commands that I had to use while learning:> A collection of useful commands. 
Open a terminal and type/copy-paste the commands for specific issues.

1) What kernel? Code: "uname -a" (or option -r)
2) What is connected to USB ports: "lsusb" (with -options)
3) What is connected to the MoBo: "lspci" (with -options)
4) Find a specific item, for example VGA card: "lspci | grep VGA"
5) X server settings: "nvidia-settings"
6) Partition Table: "fdisk -lu"
7) Reactivate XServer: "sudo dpkg-reconfigure -phigh xserver-xorg"
I don't know if it makes sense to include them in your section "4. Common Terminal Commands".
Just a thought.

---

### Post by sunexplodes on 2007-04-20
A lot of those are great and will definately be in the next revision. 

Sorry about the shoddy vi instructions, guys. I didn't know any better and I just used the first cl text editor i found. I'll switch over to nano in the future. 

About Automatix, the suggestion to use it will be removed in the next version, as Feisty's made it pretty much obsolete. I will be including instructions on enabling those codecs though. 


Plus, a few other goodies I've picked up around the forums, and on my aventures moving to the Feisty Fawn. 

Thanks for the input!

---

### Post by SlayerMan on 2007-04-20
Very nice work, thank you!

---

