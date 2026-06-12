---
title: "Cool things that can be done from terminal?"
date: 2007-05-26
forum: The Cafe
---

### Post by wie6Ein0 on 2007-05-26
I was just wondering... What are all the neat things that can be done from the terminal.

I've already figured out the following: wget, whois, time, uptime, date, etc.

---

### Post by Darkriser on 2007-05-26
Try starting [here]("http://www.linuxcommand.org") and once done, continue [here]("http://www.google.com/search?hl=en&q=linux+command&btnG=Google+Search") ;)

Marcel

---

### Post by Spr0k3t on 2007-05-26
sudo apt-get moo

---

### Post by bobbocanfly on 2007-05-26
That is just too much fun in Ctl+Alt+F1

---

### Post by xyz on 2007-05-26
Just a couple of concrete things I've learnt from members here:

 dmesg > ${HOME}/Desktop/dmesg.txt

sudo /etc/init.d/networking restart

 shred -fuzv 03FC4DE2d01  42FFC800d01  _CACHE_001_  _CACHE_002_  _CACHE_003_  _CACHE_MAP_

 sudo aptitude update && sudo aptitude upgrade

 sudo aptitude clean
 sudo aptitude autoclean

sudo gedit /etc/popularity-contest.conf

 gksudo gedit /etc/apt/sources.list

 sudo touch forcefsck

---

### Post by kevinlyfellow on 2007-05-26
vi
lynx
bash wildcards
aplay
bash scripting
[http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/](http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/)
tracepath
echo "hello world" >> ~/README
alias back='cd $OLDPWD' ; cd /usr/share/icons ; back
vim ~/.bashrc
lpr -o page-set=odd -o outputorder=reverse filetoprint.ps
lpr -o page-set=even filetoprint.ps

edit: more
sudo apt-get install bb; bb
telnet towel.blinkenlights.nl

---

### Post by jarvis13 on 2007-05-26
Lynx!

---

### Post by moma on 2007-05-26
$ [COLOR="SeaGreen"]banner moo[/COLOR]
```
[COLOR="PaleTurquoise"]                                                         
                                                ################## 
                                           ############################ 
                                         ################################ 
                                       #################################### 
                                     ######################################## 
                                   ############################################ 
                                  ############################################## 
                                 #############                      ############# 
                                #########                                ######### 
                                #######                                    ####### 
                               ######                                        ###### 
                               #####                                          ##### 
                              #####                                            ##### 
                              ####                                              #### 
                              ####                                              #### 
                              ####                                              #### 
                              ####                                              #### 
                              #####                                            ##### 
                              #####                                            ##### 
                               #####                                          ##### 
                               ######                                        ###### 
                                #######                                    ####### 
                                #########                                ######### 
                                 #############                      ############# 
                                  ############################################## 
                                   ############################################ 
                                     ######################################## 
                                       #################################### 
                                         ################################ 
                                           ############################ 
                                                ################## 
[/COLOR]
```

---

### Post by Bachstelze on 2007-05-26
*fortune* ftw !

---

### Post by B0rsuk on 2007-05-26
```

sudo apt-get install tree aview

tree
asciiview picture.jpg
telnet crawl.akrasiac.org

```

---

### Post by 3rdalbum on 2007-05-26
The "at" and "batch" commands are great - being able to schedule a task to run only when the system is at under 80% load is really cool.

---

### Post by cody50 on 2007-05-26
well, you can change the background of it to your favorite color or picture by going to Edit-> current profile (gnome terminal). thats sorta cool. Especially if you have a nice black and white picture of Maria Sharapova.

---

### Post by happy-and-lost on 2007-05-26
```

jo@mithos:~$ cowsay -f sodomized -e 00 Moo?
 ______
< Moo? >
 ------
      \                _
       \              (_)
        \   ^__^       / \
         \  (00)\_____/_\ \
            (__)\       ) /
                ||----w ((
                ||     ||>> 

```

---

### Post by meng on 2007-05-26
Um, okay...

I like batch converting/renaming files in shell! That's pretty darn cool.
ImageMagick is your friend.

---

### Post by v8YKxgHe on 2007-05-26
> **happy-and-lost said:**
> ```

jo@mithos:~$ cowsay -f sodomized -e 00 Moo?
 ______
< Moo? >
 ------
      \                _
       \              (_)
        \   ^__^       / \
         \  (00)\_____/_\ \
            (__)\       ) /
                ||----w ((
                ||     ||>> 

```

ahahahah :D:lolflag::lolflag:

---

### Post by icechen1 on 2007-05-26
aptitude moo
There are no Easter Eggs in this program.
 aptitude -v moo
There really are no Easter Eggs in this program.
 aptitude -vv moo
Didn't I already tell you that there are no Easter Eggs in this program?
 aptitude -vvv moo
Stop it!
 aptitude -vvvv moo
Okay, okay, if I give you an Easter Egg, will you go away?
 aptitude -vvvvv moo
All right, you win.
                                     /----\
                           -------/      \
                           /               \
                          /                |
   -----------------/                  --------\
   ----------------------------------------------

Happy?
 aptitude -vvvvvv moo
What is it?  It's an elephant being eaten by a snake, of course.

---

### Post by rolando2424 on 2007-05-26
--> sudo apt-get install ncmpc
--> ncmpc

And voilá, music player in the console :D

--> sudo apt-get install centericq
--> centericq

Instant messaging in the console

--> sudo apt-get install weechat-curses
--> weechat-curses

Irc in the command line (You can also use irssi)

--> telnet towel.blinkenlights.nl

Star Wars 4 in the terminal :D

And I can't remember anymore programs...

---

### Post by kevinlyfellow on 2007-05-26
Learn cron and anacron

Master the program grep

bsd games!  sudo apt-get install bsdgames

---

### Post by nalmeth on 2007-05-26
mplayer -vo caca video.ogg

Watch videos in color Ascii Vision.


And pretty much everything else you can do from the terminal:
Browse web, ftp, ssh, file management, package management, text editing, ...

EDIT: I hope mods keep a close eye on this one, something nasty could slip in ;)

---

### Post by chili555 on 2007-05-26
```
ssh -l Sylvia@192.168.1.118
vim beer.txt
*Sylvia, you know I love you, but I'll love you even more if you bring me a cold beer and some chips, oh, and salsa, too. Thanks, hon!*
text2wave beer.txt beer.wav
aplay beer.wav
```

Assuming your Sylvia has her speakers turned up, a cold beer may appear in front of you. Try getting a cold beer from Vista!

---

### Post by tehkain on 2007-05-26
the 'sl' train.

---

### Post by kevinlyfellow on 2007-05-26
> **chili555 said:**
> ```
ssh -l Sylvia@192.168.1.118
vim beer.txt
*Sylvia, you know I love you, but I'll love you even more if you bring me a cold beer and some chips, oh, and salsa, too. Thanks, hon!*
text2wave beer.txt beer.wav
aplay beer.wav
```

Assuming your Sylvia has her speakers turned up, a cold beer may appear in front of you. Try getting a cold beer from Vista!

Instead of opening vim you could just 
```
echo "Sylvia, you know I love you, but I'll love you even more if you bring me a cold beer and some chips, oh, and salsa, too. Thanks, hon!" > beer.txt
```

---

### Post by Tundro Walker on 2007-05-26
```
sudo apt-get abs-guide
```

Advanced Bash-Scripting Guide

---

### Post by icechen1 on 2007-05-26
Here is an other:
```
telnet towel.blinkenlights.nl
```
and press 2 time [enter] enjoy the ASCII movie! :popcorn:

---

### Post by hakimaki on 2007-05-28
amazing... lol

---

### Post by PatrickMay16 on 2007-05-28
> **xyz said:**
> Just a couple of concrete things I've learnt from members here:

 dmesg > ${HOME}/Desktop/dmesg.txt

Just to let you know, that's a bit overdone. This does the same but with less stuf to type:

dmesg > ~/Desktop/dmesg.txt

Just so any newbies know, the > causes the output of a program to be written to a file, so as you see there the output of dmesg will become dmesg.txt. And >> appends the output of a program to an existing file. 
I don't actually know this very well, so I've probably made some mistake or said something wrong. Hopefully I'll be corrected if that is the case.

---

### Post by Somenoob on 2007-05-28
Putting "&" at the end for background jobs/tasks, so you can continue using your shell if you launch any GUI app from it.

---

### Post by energiya on 2007-05-28
> **westoncampbell said:**
> I was just wondering... What are all the neat things that can be done from the terminal.

I've already figured out the following: wget, whois, time, uptime, date, etc.

Well, you can do just about anything: watching movies, listening to music, programming with syntax highlight, read/write mail, surf the internet, chat or use IM, control any little thing that happens in you PC, and, well, the list goes on. I actualy boot to init 3 and only start X when I have to open a lot of windows at the same time.

---

### Post by darklemming54 on 2007-05-28
telnet towel.blinkenlights.nl

---

