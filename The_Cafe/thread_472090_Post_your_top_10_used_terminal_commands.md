---
title: "Post your top 10 used terminal commands"
date: 2007-06-12
forum: The Cafe
---

### Post by earobinson on 2007-06-12
I recently made a [blog post]("http://earobinson.wordpress.com/2007/06/12/my-top-10-commands/") that received a lot of attention, asking people to post there top 10 terminal commands. So without further adoo do a ```
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
``` or ```
history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
``` (Thanks reclusivemonkey) in the terminal and post away. Here is mine:

    146 ls
    126 cd
     59 gnome-open
     41 ./a1q3.py
     40 svn
     15 python
     11 xpdf
     11 history
     10 geany
      5 ssh

---

### Post by LollYouSuckZor on 2007-06-12
Lol, A while ago they were.

```

Sudo apt-get install beryl beryl-core beryl-plugins emerald emerald-themes

```
```

Sudo apt-get remove beryl beryl-core beryl-plugins emerald emerald-themes

```

---

### Post by cunawarit on 2007-06-12
58 cd
     44 apt-cache
     29 ls
     25 su
     19 ps
     18 whois
     13 ping
     10 kill
     10 clear
      8 realplayer

And yeah, it is an everyday desktop :) No work there whatsoever...

---

### Post by daynah on 2007-06-12
Terminal didn't reply. :( Maybe I don't use it enough?

---

### Post by cunawarit on 2007-06-12
> **daynah said:**
> Terminal didn't reply. :( Maybe I don't use it enough?

Paste this is: 

```
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
```

---

### Post by thisllub on 2007-06-12
There is a problem with the post
It should read:

history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr

     96 ls
     57 cd
     49 ps
     30 mount
     21 ifconfig
     19 gvim
     18 killall
     18 history
     16 scp
     16 rm

---

### Post by Bachstelze on 2007-06-12
For myself :

```
  53 df
   7 sudo
   3 ls
   3 cd
   3 awk
   2 rm
   2 ln
   2 firefox
   1 screen
   1 pwd

```

For root :

```
  26 df
  16 cd
  12 make
   7 fdisk
   7 disklabel
   6 nano
   4 mount
   4 man
   3 useradd
   3 ls

```

I just installed it today and made my partitions a little too short, thus all the df's :p

---

### Post by dreadlord_chris on 2007-06-12
161 sudo
     34 ls
     17 cd
     14 cat
     13 sinstall
     13 man
     11 supdate
     11 cp
     10 whereis
      9 ps

sinstall = sudo apt-get install
supdate = sudo apt-get update

---

### Post by cunawarit on 2007-06-12
For root:

     46 apt-get
     23 exit
     23 apt-cache
     16 ls
     15 cd
      5 nano
      4 gedit
      4 10
      3 man
      2 su

Why I'm done su twice when I am already root... who knows... And the 10 was a pasting accident...

---

### Post by init1 on 2007-06-12
In mepis
     79 ls
     34 firefox
     31 VisualBoyAdvance
     21 rm
     20 bg
     18 df
     17 halt
     15 xmms
     12 wine
     10 killall

---

### Post by matthew on 2007-06-12
> **daynah said:**
> Terminal didn't reply. :( Maybe I don't use it enough?
Me either.
> **cunawarit said:**
> Paste this is: 

```
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
```That's better...thanks for saving me the trouble of thinking... :)

```
93 sudo
60 ssh
58 ls
40 cd
27 exit
25 tilda
19 man
18 rsync
13 beryl-manager
12 ooffice

```

---

### Post by dbott67 on 2007-06-12
```

     77 ls
     76 sudo
     58 cd
     40 cat
     39 man
     28 jobs
     24 kill
     23 ps
     20 fping
     11 netstat

```

---

### Post by earobinson on 2007-06-12
> **cunawarit said:**
> Paste this is: 

```
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
```
I assumed it was a joke

---

### Post by icechen1 on 2007-06-12
73 sudo
     25 ndiswrapper
      8 cd
      8 cat
      5 svn
      4 lspci
      4 ls
      3 wget
      2 uname
      2 sh

---

### Post by il-luzhin on 2007-06-12
anyone guess what's been given me probs lately?
     107 cd
     92 ls
     74 sudo
     22 gedit
     14 kill
     14 conky
     13 make_page
      8 pwd
      8 /home/luzhin/bin/make_page
      7 chmod

---

### Post by init1 on 2007-06-12
In Ubuntu 
     25 ls
     21 cat
     11 sudo
      8 df
      6 rm
      6 cd
      5 darcnes
      4 w3m
      3 wine
      3 twin
I don't use the command line in ubuntu very much. Thats why commands I rarely use are on the list. My mepis list is more accurate.

---

### Post by PatrickMay16 on 2007-06-12
110 cd
     77 ls
     43 sfxload
     38 aplaymidi
     29 xmp
     19 cat
     15 timidity
     14 play
     12 ping
     11 sudo
      3  cock-benis.sh

Oh boy!

---

### Post by matthew on 2007-06-12
> **PatrickMay16 said:**
> 3  cock-benis.sh

Oh boy!So, um, what is that last one?? Do we *want* to know?

---

### Post by thisllub on 2007-06-12
> **matthew said:**
> So, um, what is that last one?? Do we *want* to know?

I think it goes with init1's Visual BoyAdvance

---

### Post by ryanVickers on 2007-06-12
for me, I don't use it alot, but probably (not in any order):

top
cd
su
startx
mv
iwconfig
apt-get install
(and names of programs to start them)
sudo *

as you can see, ***really*** not used very much, these are pretty uncommon commands (some of them).

---

### Post by steveneddy on 2007-06-12
70 sudo
     34 cd
     25 xvncviewer
     24 gksudo
     15 uname
     15 cowsay
     13 locate
     12 conky
     11 glxgears
     10 aptitude
I'm a loser....

---

### Post by ryanVickers on 2007-06-12
I found that the command at the top of this page:
> awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
did nothing!  that's why I'm just going from memory.

I forgot probably mount /dev/* and umount /dev/*, but less now that I've been using the disk mounter applet in the panel

---

### Post by Kingsley on 2007-06-12
sudo apt-get update/upgrade/install
d (shortcut for edictionary)
de (shortcut for german dictionary)
ls
cd
rm -rf
cp
mv
killall
clear

---

### Post by PatrickMay16 on 2007-06-12
> **matthew said:**
> So, um, what is that last one?? Do we *want* to know?

Heh heh heh. Fear not, man. It's just a little script I wrote which takes a text file and a wave file, encodes the small wave file into mp3 format, converts the text to wav and then encodes that to mp3 format as well, and then joins both mp3 files together.

When I go to bed, I use a small mp3 player to listen to various articles from the internet. This mp3 player has no screen, so I put a little bit of a song before the text-to-speech starts, so I can identify what article will play. That's why I need the script.

---

### Post by Linux Killer! on 2007-06-12
* dangerous command moved *

Bonus points if you're in your home folder.

Double points if you're in a mounted NTFS drive with write capability.

Tripple points + bonus prize if you're in /, and you walk away to make a cup of coffee without realizing what you've done. :)

---

### Post by tgalati4 on 2007-06-12
Problems ripping a scratched disk:

     91 ls
     88 cd
     73 sudo
     30 cdparanoia
     29 eject
     24 ruptime
     22 more
     18 man
      8 rm
      8 exit

---

### Post by init1 on 2007-06-12
> **thisllub said:**
> I think it goes with init1's Visual BoyAdvance
oops...

---

### Post by reacocard on 2007-06-12
```
     66 sudo
     50 svn
     50 ./exaile
     45 ps
     41 kill
     35 ./ircbot.py
     22 python
     11 man
     11 cat
     10 apt-cache

```

heh, that's probably not a very accurate measurement. I use the terminal way too much, things don't stay in history more than a day or two. I need to figure out how to make it remember about 4 times as many.

EDIT: changed, remembers 5000 lines now instead of 500, I'll give it a few days to fill up and try again.

---

### Post by ynnhoj on 2007-06-12
```
     93 ls
     77 clear
     57 exit
     55 vim
     47 cd
     23 su
     22 startx
     18 which
     12 feh
     11 rm
```

and as root:
```
    138 pacman
     91 exit
     51 ls
     36 clear
     29 vim
     26 rm
     19 cd
     12 which
      7 reboot
      7 chown
```

nothing exciting.

---

### Post by Cows on 2007-06-12
I don't know what the numbers mean but these are my top 10, there all equal :).

sudo aptitude install
sudo aptitude purge
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
ls
ls -a
cd
rm -rf

There's more but i don't remember atm.

---

### Post by fumduck on 2007-06-12
12 sudo
      3 wget
      2 if
      1 quit
      1 history

I am still learning.. I love it!!!

---

### Post by ThinkBuntu on 2007-06-12
I use 
```
$ du -h /
```
often

---

### Post by CautionaryX on 2007-06-12
143 sudo
     67 clear
     20 cd
     17 firefox
     15 exit
     12 beagled
     11 echo
      9 aptitude
      8 man
      8 chmod

Well, I use sudo to update my antivirus... and apt-get upgrade, etc.

---

### Post by ryanVickers on 2007-06-12
>  ***

Bonus points if you're in your home folder.

Double points if you're in a mounted NTFS drive with write capability.

Tripple points + bonus prize if you're in /, and you walk away to make a cup of coffee without realizing what you've done. 
Reminds me of this dilbert joke:
a marketing person is telling dilbert and wally "now it's time for marketing to turn this backup product of yours into mass sales" or something
then dilbert says that it's not really finished because we said it would take 6 months and you only gave us 2
Then marketing waves that off and asks for the features to put in the manual
They say it freezes every 15 seconds and it erases your hardrive
unless you'r on a lan, then it erases everyones hardrives
"and god help you if you'r on a modem"
"what heppens then?"
"it calls all your friends and erases thier pc's too"
"we'll call it 'quikprotect'!"
"If you have a sound card it swares at you"
:lolflag:

---

### Post by ryanVickers on 2007-06-12
Edit: remove post
oops, double post, don't know how that happened?!

---

### Post by JT673 on 2007-06-12
75 sudo #kinda obvious
     53 cd
     43 ls
     32 cat
     28 dpkg
     20 catinput #self-made script
     18 echo
     11 man
     10 mkdir
     10 countdown #another self-made script

---

### Post by laredo7mm on 2007-06-12
139 sudo
    108 dir
     73 cd
     35 rm
     35 cd..
     29 unrar
     17 ./fah5
     10 sensors
     10 par2
     10 exit

dir is an alias for "ls -l", I think I learned dir from DOS or Fortran, back in the day. ;)

---

### Post by frup on 2007-06-12
133 sudo
     65 crontab
     30 ./test.sh
     30 cd
     27 ls
     21 ssh
     19 telnet
     11 postconf
      9 ~/./test.sh
      9 aptitude
lol thats interesting.

---

### Post by VirtualTiger on 2007-06-12
As MySelf:
```
   176 sudo
     96 ls
     35 cd
     25 locate
     24 gedit
     15 convert
     11 ./convert-bc.sh
      9 chmod
      6 fdisk
      6 clear
```

As Root:
```
     86 dir
     57 cd
     51 ls
     27 more
     25 rm
     17 grub-install
     15 gedit
     12 apt-get
     12 sudo    # Looks like I forgot I was already here...:(
     10 cp
```

---

### Post by Crashmaxx on 2007-06-12
194 sudo
     25 ping
     23 ssh
     23 cd
     21 man
     16 bdm
     13 ls
     11 test
     11 ./synergycheck
     11 ps

---

### Post by odiseo77 on 2007-06-12
sudo
ls
apt-get
less
vi
mc
cd
kill (well, sometimes :D )
ps
exit

---

### Post by Clay_Banger on 2007-06-12
177 sudo
    113 cd
     57 ls
     37 chmod
     15 kdesu
     15 exit
     11 wine
      9 export
      7 ./configure
      5 svn

---

### Post by Nikron on 2007-06-12
94 ls
     80 sudo
     66 cd
     38 pacman
     24 man
     23 cat
     18 vim
     16 echo
     11 zenity
      9 du


Not particularly interesting

---

### Post by herbster on 2007-06-13
154 sudo
111 cd
41 dir
39 svn
22 make
20 ./configure
17 autoreconf
7 file
6 ping
6 find

---

### Post by kuja on 2007-06-13
63 ls
     46 sudo
     34 show
     33 search
     32 install
     21 ./build.sh
     20 simple64
     12 rm
      9 man

---

### Post by ihatethedekoys on 2007-06-13
213 sudo
     31 ls
     26 cd
     18 locate
     15 wine
     14 fglrxinfo
     14 apt-cache
     12 cedega
      9 wget
      9 gcc

---

### Post by crimesaucer on 2007-06-13
```
 
    210 sudo
     66 ls
     48 acpi
     23 cd
     20 free
     12 twf
     12 conky
     11 mousepad
     11 killall
      9 ping

```

---

### Post by afljafa on 2007-06-13
This is one of our servers.

285 mc
     94 ls
     50 service
     39 dmesg
     34 mount
     33 make
     26 reboot
     24 rpm
     21 cp
     19 chown

---

### Post by v8YKxgHe on 2007-06-13
```
    230 svn
     54 cd
     46 sudo
     34 ssh
     18 ls
     12 chmod
     11 cowsay
      9 rm
      8 ping
      8 apt-cache
```

Cowsay! yay =D

---

### Post by bashologist on 2007-06-13
640 echo
    550 sed
    264 cd
    242 sudo
    227 man
    226 ls
    208 grep
    182 for
    146 date
    139 printf

This's awesome. Great idea. I have the biggest numbers so far. I love teh echoing. n_n

---

### Post by Tux Aubrey on 2007-06-13
80 sudo
     13 cd
     10 startx
      9 envy
      5 gksudo
      4 exit
      3 ls
      3 gedit
      3 emerald
      2 vim

Wot? no cowsay?

 _```
______________________________
< Time to edit xorg.conf again! >
 -------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

---

### Post by stimpack on 2007-06-13
111 cd
     76 ls
     42 screen
     37 wget
     30 dosbox
     14 truecrypt
     13 cedega
     10 sudo
     10 nano
     10 du

---

### Post by matthinckley on 2007-06-13
On my server (only box I have access to from work)

```
    155 ls
     84 cd
     61 exit
     40 mv
     39 mkdir
     35 mutt
     24 elinks
     12 sudo
      9 ssh
      5 route

```

---

### Post by christhemonkey on 2007-06-13
```
    151 g++
    111 ./task2.o
     50 ./task7.o
     35 ./task6.o
     20 ls
     13 ./12.o
     12 cd
      9 nano
      6 sudo
      5 ./task3.o

```

Anyone would think that im learning c++....

---

### Post by regomodo on 2007-06-13
102 sudo
     39 route
      5 iwlist
      5 ifconfig
      4 iwconfig
      4 htop
      3 ping
      3 ls
      3 cd
      2 nano

---

### Post by reclusivemonkey on 2007-06-13
I'm at work right now and couldn't get awk to work on cygwin :-S I made a few tweaks though and got there;

    217 vim
     24 man
     22 fortune
     14 less
     14 history
     14 grep
     12 rxvt.exe
     10 antiword.exe
      9 mv
      9 cat

I'll post the result from mother when I get home =]

Just in case anyone is interested, I used

```

history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr

```

From mother;

      77 sudo
     46 vim
     36 cd
     33 ls
     21 find
     18 man
     17 killall
     13 less
     11 cat
      9 cp

Yep, I likes me vim!

Oh, and thanks to earobinson for the mention at the start of the thread =]

---

### Post by bclark on 2007-06-13
81 cd
     66 ls
     44 sudo
     34 vi
     20 g++
     18 make
     16 wget
     14 java
     13 ssh
     12 svn

---

### Post by earobinson on 2007-06-13
> **reclusivemonkey said:**
> I'm at work right now and couldn't get awk to work on cygwin :-S I made a few tweaks though and got there;

    217 vim
     24 man
     22 fortune
     14 less
     14 history
     14 grep
     12 rxvt.exe
     10 antiword.exe
      9 mv
      9 cat

I'll post the result from mother when I get home =]

Just in case anyone is interested, I used

```

history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr

```


neat, thats a lot cleaner than mine, but then mine is quite hacked

---

### Post by bobbocanfly on 2007-06-13
85 cd
     79 sudo
     51 ls
     24 exit
     19 sh
     13 chmod
     12 uptime
     12 ruby
     10 svn
     10 rm

Need to use the terminal more. It is too much fun!

---

### Post by reclusivemonkey on 2007-06-13
> **earobinson said:**
> neat, thats a lot cleaner than mine, but then mine is quite hacked

I'd say using awk is better than sed; I think awk would be more robust at getting the right fields from history.

I use gawk on cygwin in another script I use and it seems to work fine there, but its acting on a file rather than on a command. Its not the first time something on cygwin has behaved strangely though!

---

### Post by cstudent on 2007-06-13
123 sudo
73 ls
64 cd
29 logout
20 cp
17 ssh
15 exit
9 htop
5 nano
4 rm

---

### Post by tact on 2007-06-13
My result...

  4743 evolution --force-shutdown
  4743 evolution --component=mail
   102 sudo
     62 ping
     29 gedit
     27 ls
     22 cd
     12 iwconfig
     10 exit
      9 locate

:) the first two may be exaggerations...

---

### Post by Celegorm on 2007-06-13
107 ls
58 cd
14 view
14 man
13 sudo
12 su
11 mv
8 mkdir
8 ./angband
7 date

---

### Post by mcduck on 2007-06-13
100 sudo
     22 man
     22 ls
     17 cd
     14 top
     14 ncmpc
     13 tail
     13 apt-cache
     12 mpdscribble
     12 locate

edit: these commands seem to give a bit different outputs. Here are the results using the other command:

  116 sudo
     36 man
     24 ls
     19 top
     18 tail
     17 cd
     16 apt-cache
     14 ncmpc
     14 mpdscribble
     13 killall

---

### Post by wakingrufus on 2007-06-13
173 sudo
     33 cd
     32 startx
     17 joy2key
     17 apt-get
     11 gpg
     10 winecfg
     10 dir
      9 envy
      7 umount

---

### Post by earobinson on 2007-06-13
> **mcduck said:**
> 100 sudo
     22 man
     22 ls
     17 cd
     14 top
     14 ncmpc
     13 tail
     13 apt-cache
     12 mpdscribble
     12 locate

edit: these commands seem to give a bit different outputs. Here are the results using the other command:

  116 sudo
     36 man
     24 ls
     19 top
     18 tail
     17 cd
     16 apt-cache
     14 ncmpc
     14 mpdscribble
     13 killall
which came from which, they gave me the same output

---

### Post by runningwithscissors on 2007-06-13
```
72 ./compile1
42 gdb
38 su
26 ../bin/game1
23 startx
18 exit
 6 rm
 5 ls
 5 grep
 2 top
```

---

### Post by bonzodog on 2007-06-13
Mine, on zenwalk. I use the terminal fairly often, and this is a clean install (for major version upgrade), only 3 days old.

     59 cd
     52 ls
     47 su
     30 ps
     16 killall
     15 locate
     14 conky
     12 make
     10 scummvm
     10 nano

locate is a popular one of mine :D

---

### Post by TBOL3 on 2007-06-13
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    108 sudo
     62 exit
     53 ls
     36 locate
     34 cd
     32 compiz
     18 mount
     10 timidity
     10 man
     10 chmod

---

### Post by happy-and-lost on 2007-06-13
76 sudo
     17 Eterm
     15 mousepad
     11 fbsetbg
      5 xbindkeys
      5 su
      5 gtk-theme-switch2
      5 du
      5 alsamixer
      4 xev

---

### Post by PatrickMay16 on 2007-06-13
> **cstudent said:**
> 123 sudo
73 ls
64 cd
29 logout
20 cp
17 ssh
15 exit
9 htop
5 nano
4 rm

29 logout? Heh heh! How did you manage that?

---

### Post by andrewpmk on 2007-06-13
62 ssh
     58 dir
     36 rm
     35 cd
     26 optipng
     26 advpng
     25 rsvg-view
     19 ../bin/pngout
     18 inkscape
     15 sudo

---

### Post by Hortinstein on 2007-06-13
hmmm i cant wait to get home and see where nethack is on my list....my guess is like #3

---

### Post by L14UX_1NS1D3 on 2007-06-13
that is a good question

mine are as follows: 
1. ls

2.  killall  (in most cases) 

3. nautilus &

4. thunar & 

5. pico

6. man 

7. find 

8. grep (used in conjunction with find)

9. exit 

10. mp3blaster (ncurses jukebox)
________________________________________________________________________________________________________

two great apps to use are yakuake and mp3blaster, by combining them you have a dropdown audio player on any virtual desktop. 8-)

---

### Post by Interestedinthepenguin on 2007-06-13
143 sudo
     82 cd
     55 python
     30 xwinwrap 
     28 man
     17 whereis
     13 tar
      9 iwconfig
      8 firefox
      7 ls

---

### Post by Old Pink on 2007-06-13
189 sudo
     52 ping
     33 locate
     18 /usr/bin/gconftool-2
     13 cd
     11 whereis
      9 /home/matt/bin/ppc.sh
      8 multisync
      8 chmod
      6 xcompmgr

---

### Post by tagra123 on 2007-06-13
71 cd
     70 dir
     60 sudo
     47 ssh
     21 mythfrontend
     12 gedit
     11 top
     10 ping
     10 ls
     10 exit

---

### Post by cstudent on 2007-06-13
> **PatrickMay16 said:**
> 29 logout? Heh heh! How did you manage that?

I ssh into my home desktop from work most days to build the [Ubuntu .deb for the Codeblocks developers]("http://developer.berlios.de/project/showfiles.php?group_id=5358"). I guess that's where that comes from.

---

### Post by lsalminen on 2007-06-13
155 sudo
     55 exit
     52 cd
     24 wget
     15 make
     10 mount
      9 transset
      8 top
      8 killall
      7 wine

---

### Post by screaminj3sus on 2007-06-13
haha on my fresh ubuntu install (Installed today)

     13 sudo
      3 history
      2 beryl-manager
      1 wget
      1 gconf-editor
      1 alsamixer

---

### Post by Ptero-4 on 2007-06-13
Mine:

167 sudo
95 cd
89 ls
30 rm
17 make
14 mv
12 pico
11 mount
7 umount
7 tar

---

### Post by james_2002uk on 2007-06-13
cd
ls -l
apt-get
apt-cache
ssh
nano
beryl-manager.... (followed a short time later by)
metacity
grep
killall

---

### Post by mocqueanh on 2007-06-13
gnochm
evince
man -k
df
cd
apt-cache show
gimp
kill %
top
rm

---

### Post by userundefine on 2007-06-13
59 ls
     57 sudo
     57 cd
     40 games/ut2004demo/./ut2004-demo
     36 screen
     26 kaffeine
     20 rtorrent
     20 mv
     19 killall
     17 irssi

---

### Post by frup on 2007-06-14
How can you increase the length of the history? Typing history by itself shows my last 500 or so commands the top 10 being the top 10 of those, I was using terminal a bit and then decided to look at it again and my sudo had gone down by 9. lol.

How do you clear the history if you want to? (I.e say I wanted to keep a log of all my commands each day and > to a file and then clear the history so I could graph how I used commands or something geeky like that?)

---

### Post by mthakur2006 on 2007-06-14
mine are:

```
 mtha@LENOVO:~$ beagle-status
mtha@LENOVO:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     73 sudo
     44 beagle-status
     18 </li>
     18 <li
     15 cd
     15 beagled
     14 iwconfig
     13 hddtemp
     12 beagle-index-info
     10 exit
mtha@LENOVO:~$ 


```

;)

---

### Post by eentonig on 2007-06-14
Rather obvious I just reinstalled and still busy to tune to my needs.


     68 sudo
     32 cd
     24 ls
     17 apt-cache
     16 psgrep
     11 more
     10 gnome-terminal
      9 htop
      9 gksudo
      8 man

---

### Post by mcduck on 2007-06-14
> **earobinson said:**
> which came from which, they gave me the same output

The first output was from the second provided command (the one that uses sed), and the other one uses the first command (with awk).

---

### Post by slimdog360 on 2007-06-14
41 sudo
     38 cd
     24 ls
     13 apt-cache
      4 ./configure
      3 thunar
      3 scilab
      3 make
      3 gksudo
      3 ./FretsOnFire

---

### Post by bashologist on 2007-06-14
Here are the top topcommands from this thread pages 1 to 9. Using a python script with regex here's the result:
```
satan@ubuntu:~$ ~/./topcommands.py | sort -nr
9486 evolution
7600 GS
2818 sudo
1806 cd
1527 ls
1509 -
500 or
200 exit
130 ssh
115 rm
109 dir
109 cat
107 ps
100 man
96 ping
91 locate
90 wget
88 apt-cache
87 make
84 su
78 screen
69 mount
65 crontab
61 killall
58 logout
55 python
```

Here's the python script:
```
#!/usr/bin/env python
#http://ubuntuforums.org/showthread.php?t=472090

import urllib, re, sys

top_commands = {}
forum_url = "http://ubuntuforums.org/showthread.php?t=472090"
page_source = urllib.urlopen(forum_url).read()
pattern_page = re.compile("page \d+ of \d+", re.IGNORECASE)
pattern_command = re.compile("\d+ .+<br />\r", re.IGNORECASE)
page_count = re.search(pattern_page, page_source).group().split()[-1]

for count in range(1, int(page_count) + 1):
	page_url = "%s&page=%i" % (forum_url, count)
	print "processing %s ..." % page_url
	page_source = urllib.urlopen(page_url).read()
	for command in pattern_command.findall(page_source):
		command = command.split("<br />")
		program = command[0].split()[1]
		number = command[0].split()[0]
		if program in top_commands:
			top_commands[program] += int(number)
		else:
			top_commands[program] = int(number)

for command in top_commands:
	print top_commands[command], command
```

---

### Post by daynah on 2007-06-14
43 sudo
     28 cd
     24 ls
     12 wine
      9 ./psclient
      7 ./pssetup
      6 winecfg
      5 gksu
      3 wget
      3 gksudo


Does this qualify me to be a gamer?

---

### Post by reacocard on 2007-06-14
> **frup said:**
> How can you increase the length of the history? Typing history by itself shows my last 500 or so commands the top 10 being the top 10 of those, I was using terminal a bit and then decided to look at it again and my sudo had gone down by 9. lol.

How do you clear the history if you want to? (I.e say I wanted to keep a log of all my commands each day and > to a file and then clear the history so I could graph how I used commands or something geeky like that?)

To increase history length, add a line like
```
export HISTSIZE=5000
```
to ~/.bash_profile

To clear the history, do
```
history -c
```

---

### Post by bashologist on 2007-06-14
What's everyones history size? That would be interesting to see also.

```
satan@ubuntu:~$ wc -l $HISTFILE
6621 /home/satan/.bash_history
satan@ubuntu:~$ wc -c $HISTFILE
323822 /home/satan/.bash_history
satan@ubuntu:~$ du -h $HISTFILE
324K    /home/satan/.bash_history
satan@ubuntu:~$ echo $HISTSIZE
99999
satan@ubuntu:~$
```

---

### Post by testube_babies on 2007-06-14
yikes...i think i might overdo the sudo

    182 sudo
     32 exit
     26 cd
     20 rm
     12 gksudo
     11 ls
     11 apt-cache
      8 python
      8 ssh
      6 wget

---

### Post by corney91 on 2007-06-14
109 sudo
     35 apt-cache
     20 cd
     15 ls
     15 jack
     12 wine
      9 history
      9 beagled
      7 gedit
      6 man

Recently reinstalled, otherwise jack would be much higher

---

### Post by Bluecircle on 2007-06-16
137 sudo
     33 aptitude
     32 tar
     17 vlc
     17 ps
     14 kill
     12 top
     12 ls
      9 thunderbird
      8 esd

---

### Post by Motoxrdude on 2007-06-16
```
sudo su
cd
ls
wine
apt-get update
apt-get install
rm
mv
tar 

```
eh, only 9 but that's basicly all i use

---

### Post by macogw on 2007-06-16
102 sudo
    102 ls
     98 cd
     42 apt-cache
     26 vi
     11 man
     11 915resolution
     10 ps
      7 ssh
      6 cat

---

### Post by mardawi on 2007-06-16
49 sudo
     29 cd
     26 ls
     13 kguitar
     11 ping
     10 ifconfig
      7 alsactl
      5 vmware
      5 timidity
      5 gst-launch

---

### Post by newlinux on 2007-06-16
104 ls
     98 cd
     67 ll
     36 sudo
     16 cls
     14 test-mpeg2
     12 pgrep
     11 rm
     11 mv
     10 ffmpeg

A couple of aliases in there

---

### Post by Bluecircle on 2007-06-17
> **newlinux said:**
> 
     16 cls

A couple of aliases in there

cls, an alias for clear, the DOS version?

---

### Post by vexorian on 2007-06-17
hmm 

1. cd
2. sudo nautilus
3. sudo gedit
4. ./xye
5. wine
6. ssh

---

### Post by Hobbsee on 2007-06-17
64 ls
     59 cd
     38 vi
     25 [apt-cache] search
     20 update (apt-get update && apt-get upgrade)
     16 sudo
     15 [apt-cache] show
     15 rm
     15 dch
     13 ssh

yay, aliases :)

---

### Post by newlinux on 2007-06-17
> **Bluecircle said:**
> cls, an alias for clear, the DOS version?

Yep, and ll and alias for ls -ulAFh

---

### Post by PartisanEntity on 2007-06-17
94 sudo
     66 cd
     47 ls
     24 python
      9 bzr
      8 man
      8 envy
      7 startx
      7 pwd
      6 touch

---

### Post by Afoot on 2007-06-17
**My account:**
    170 javac
     90 java
     59 sudo
     55 clear
     35 ls
     19 cd
     11 wine
      8 su
      8 nautilus
      6 cowsay
[B]
Root (yes, it's on Gentoo):[/B]
     63 emerge
     24 exit
     23 ls
     16 vim
     16 echo
     13 rc-update
      9 ifconfig
      8 adduser
      7 nano
      7 cd

---

### Post by Andrewie on 2007-06-17
./Nvidia.......run (nvidia driver)
kdm
init 3
init 5
mv
cp
mc
ls
shutdown -r now
poweroff

---

### Post by tanelt on 2007-06-17
Okay then, let's see...

In no particular order (except for the very last one on the list).


1. sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2. sudo dpkg-reconfigure xserver-xorg
3. sudo killall x
4. gksudo gedit /etc/X11/xorg.conf
5. sudo killall x
6. gksudo gedit /etc/X11/xorg.conf
7. sudo reboot
8. sudo nano /etc/X11/xorg.conf
9. sudo dpkg-reconfigure xserver-xorg
10. sudo reboot
[COLOR=Gray]11. sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
12. sudo dpkg-reconfigure xserver-xorg
13. sudo killall x
14. gksudo gedit /etc/X11/xorg.conf
15. sudo killall x
16. gksudo gedit /etc/X11/xorg.conf
17. sudo reboot
18. sudo nano /etc/X11/xorg.conf
19. sudo dpkg-reconfigure xserver-xorg
20. sudo reboot
21. sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
22. sudo dpkg-reconfigure xserver-xorg
23. sudo killall x
24. gksudo gedit /etc/X11/xorg.conf
25. sudo killall x
26. gksudo gedit /etc/X11/xorg.conf
27. sudo reboot
28. sudo nano /etc/X11/xorg.conf
29. sudo dpkg-reconfigure xserver-xorg
30. sudo reboot
31. sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
32. sudo dpkg-reconfigure xserver-xorg
33. sudo killall x
34. gksudo gedit /etc/X11/xorg.conf
35. sudo killall x
36. gksudo gedit /etc/X11/xorg.conf
37. sudo reboot
38. sudo nano /etc/X11/xorg.conf
39. sudo dpkg-reconfigure xserver-xorg
40. sudo reboot
41. sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
42. sudo dpkg-reconfigure xserver-xorg
43. sudo killall x
44. gksudo gedit /etc/X11/xorg.conf
45. sudo killall x
46. gksudo gedit /etc/X11/xorg.conf
47. sudo reboot
48. sudo nano /etc/X11/xorg.conf
49. sudo dpkg-reconfigure xserver-xorg
50. sudo reboot
51. sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
52. sudo dpkg-reconfigure xserver-xorg
53. sudo killall x
54. gksudo gedit /etc/X11/xorg.conf
55. sudo killall x
56. gksudo gedit /etc/X11/xorg.conf
57. sudo reboot
58. sudo nano /etc/X11/xorg.conf
59. sudo dpkg-reconfigure xserver-xorg
60. sudo reboot
61. sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
62. sudo dpkg-reconfigure xserver-xorg
63. sudo killall x
64. gksudo gedit /etc/X11/xorg.conf
65. sudo killall x
66. gksudo gedit /etc/X11/xorg.conf
67. sudo reboot
68. sudo nano /etc/X11/xorg.conf
69. sudo dpkg-reconfigure xserver-xorg
70. shutdown, boot back to Windows. Remove Linux.[/COLOR]

---

### Post by Dragonbite on 2007-06-17
123 sudo
    119 ls
     40 ps
     38 cd
     26 killall
     24 exit
     20 man
     10 vpnclient
     10 kill
      8 ping

---

### Post by Mr. Picklesworth on 2007-06-18
72 cd
     59 sudo
     36 ls
     29 blitzmaxide_ce
     17 pidof
     17 kill
     11 make
     11 date
     10 echo
      9 export

I thought my "kill" use was bad. Gee, Dragonbite, your terminal is a massacre! :P

---

### Post by dart1007 on 2007-06-18
186 sudo
53 btsco 
28 cd
27 hcitool
18 man
14 hidd
14 ./buildset
11 locate
11 aplay
9 uname

---

### Post by gushy on 2007-06-18
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     98 ssh
     78 exit
     36 sudo
     36 cd
     32 ps
     31 ls
     31 kill
     27 tn5250
     15 hamachi
      9 top


history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
     80 ssh
     60 exit
     32 cd
     30 sudo
     30 ls
     29 kill
     26 ps
     25 tn5250
     11 hamachi
      8 scp

---

### Post by frup on 2007-06-18
> **gushy said:**
> 
history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
     80 ssh
     60 exit
     32 cd
     30 sudo
     30 ls
     29 kill
     26 ps
     25 tn5250
     11 hamachi
      8 scp

laurent@lars:~$ history | sed -e 's/ / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
     99 
      1 500
      1 499
      1 498
      1 497
      1 496
      1 495
      1 494
      1 493
      1 492

A little different :S

---

### Post by ~LoKe on 2007-06-18
>     162 sudo
     69 cd
     57 ls
     39 clear
     26 gksudo
     19 ./et
     14 mplayer
     10 aplay
      7 ./et.sh
      7 cat
=]

---

### Post by Skrynesaver on 2007-06-18
```

    128 ls
     80 fg
     53 sudo
     45 ~/bin/anlyseServer.pl
     42 cd
     40 ~/bin/undate
     34 ssh
     29 less
     25 vim
     25 find

```

undate does translation of epoch-human time stamps from logs files ( A work thing)
analyseServer is a script to produce clear and readable output from the logs of various services and various utilities, a health check basically.

---

### Post by arsenic23 on 2007-06-24
This is for my laptop:
     122 find
     66 ls
     37 sudo
     30 cd
     28 ping
     27 rename
     21 cll
     15 vlc
     14 mv
     12 cl

If I had my desktop available I'm sure it'd be quite different.  
cll is an alias = cd ~/ &&clear&&ls
cl is an alias = clear && ls

---

### Post by ubuntu27 on 2007-06-24
>  history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr


 74 sudo
      9 ip
      5 ipconfig
      4 man
      4 killall
      2 xfce4-panel
      2 package
      2 network
      2 netconfig
      2 bash

> history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr


 18 sudo
      2 history
      2 aptitude
      1 suto
      1 amaya
      1 99
      1 98
      1 97
      1 96
      1 95

---

### Post by ice60 on 2007-06-24
on suse. 

    477 su
    325 sudo
    279 d
    265 locate
    237 cd
    225 ls
    177 wget
    139 l
    133 nohup
    132 smart

---

### Post by supersonicdarky on 2007-06-24
140 sudo
     90 clear
     42 cd
     35 conky
     23 killall
     21 dir
     19 exit
     10 history
      9 rm
      7 VirtualBox

nothing special

---

### Post by sabrewolf2006 on 2007-06-24
been prototyping a program using bash script, can ya tell? ;)
     64 sudo
     37 cat
     34 echo
     28 man
     23 sh
     23 cd
     22 ls
     18 grep
     18 egrep
     15 read

---

### Post by IYY on 2007-06-24
I haven't been using this particular machine for a long time, and haven't coded on it yet. So, there aren't many interesting commands...
```

    101 ls
     88 cd
     44 keyjnote
     31 sudo
     21 vi
     13 exit
      9 man
      7 apt-cache
      6 iwconfig
      6 cat

```

---

### Post by 67GTA on 2007-06-25
Linux Mint

115 sudo
     12 su
      7 killall
      7 cd
      6 gksudo
      6 ./configure
      5 make
      4 update-menu
      4 glxgears
      3 uname

---

### Post by Dokatz on 2007-06-25
67 ls
     49 cd
     34 dosbox
     19 sudo
      4 man
      2 wine
      1 wget
      1 lw
      1 ls]
      1 l

---

### Post by alan_daniel on 2007-06-25
Nice idea

49 ls
21 sudo
21 cd
13 vim
10 exit
8 uptime
6 mv
5 rm
5 mkdir
5 maxima

---

### Post by samjh on 2007-06-25
131 sudo
     90 cd
     76 ls
     47 gnat
     16 wine
     13 rm
     10 exit
      7 make
      7 java
      5 time

Interesting thread topic.

---

### Post by rishabh on 2007-06-25
I get a:
```
    175 sudo
     49 cd
     26 exit
     16 ls
     14 ping
     13 ./configure
     12 gnome-panel
      8 xwinwrap
      8 chmod
      8 cat

```

;)

---

### Post by Tachyon_ on 2007-06-25
```

     150 sudo
     25 cat
     24 killall
     22 dump
     19 make
     16 ls
     16 cd
     15 ./configure
     10 ps
      8 ./ut2004
```

:D

---

### Post by NeoLithium on 2007-06-25
107 ls
    100 sudo
     86 cd
     13 gpg
     11 firefox
      9 top
      8 gksu
      7 rm
      6 sh
      6 pidof

---

### Post by AriciU on 2007-06-25
64 nvclock
52 gedit
48 apt-get
32 cd
30 ls
29 ps
25 kill
24 cat
17 pymetar
17 cp

---

### Post by ceelo on 2007-06-25
85 su
     63 (WW)
     40 ls
     31 ncmpc
     29 cd
     16 killall
     15 tar
     15 screen
     14 kwin
     12 makepkg

No idea what (WW) is... :???:

---

### Post by harlan on 2007-06-25
170 sudo
     41 cd
     38 ls
     17 locate
     10 mysql
     10 less
      9 ps
      9 man
      9 aptitude
      8 mysqladmin

---

### Post by axel-vpk on 2007-06-25
103 cd
     85 ls
     80 sudo
     60 wine
     12 mount
     11 comix
     10 ssh
     10 gedit
      9 winecfg
      7 wget

---

### Post by konungursvia on 2007-06-25
history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
     93 sudo
     89 ls
     63 cd
     46 beryl-manager
     14 xkill
      6 rm
      4 killall
      4 deluge
      4 arecord
      3 tar

---

### Post by Qu4k3R on 2007-06-26
:D
> 
     77 sudo
     28 ls
     27 cd
     22 gcc
     14 exit
     13 man
     12 rm
     10 mv
     10 killall
     10 cat


---

### Post by lundish on 2007-06-26
slawek@113:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     92 sudo
     14 weechat-curses
     12 htop
      9 ln
      7 compiz
      6 wget
      6 ekg
      5 echo
      4 shutdown
      4 rm

---

### Post by Polygon on 2007-06-26
118 sudo
     82 cd
     57 ls
     12 python
     11 aoss
     10 zenity
      9 vol_id
      9 ssh
      8 wget
      7 svn

---

### Post by ironfistchamp on 2007-06-26
45 sudo
     31 cd
     24 ls
     10 ./waf
      5 killall
      5 gksu
      5 ./configure
      4 tar
      4 nano
      4 ./mountntfs

---

### Post by forrestcupp on 2007-06-26
Ha, the terminal!  The only reason to use it is
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Rui Pais on 2007-06-26
funny how one get this from history... 
i must check that command one day (i hate awk and sed but they are so useful...)

so, mine:
    192 sudo
     39 cd
     32 history
     29 cat
     20 ls
     20 ler
     12 ll
     11 svn
     10 free

ler is an alias for scite that i use as my base text editor (don't like scite name, short ler is just portuguese for read).
My 3rd is for history cause i use a lot of repeated svn commands (that i can't memorize) so just use history and a piped grep to get then number of a repeated line and then good old !X :)

---

### Post by justifier on 2007-06-26
81 cd
     79 sudo
     79 ls
     29 ssh
     22 telnet
     21 man
     17 apt-cache
     16 rm
     13 nano
     10 conky

---

### Post by moljac024 on 2007-06-26
102 sudo
     90 cd
     34 ls
     28 ps
     18 kill
     12 wget
     11 sh
     10 locate
      8 gksudo
      6 java

---

### Post by scrooge_74 on 2007-06-26
176 cd
    137 ls
     15 nano
     14 exit
      6 xscreensaver
      6 ps
      5 wine
      5 sudo
      4 unrar
      4 top

---

### Post by BeardlessForeigner on 2007-06-27
102 sudo
     39 cd
     28 ls
     12 alacarte
      9 man
      8 scheme
      7 wine
      7 python
      7 gedit
      6 make

---

### Post by a12ctic on 2007-06-27
83 sudo
     12 cd
      8 alsamixer
      5 make
      5 ./configure
      4 wine
      4 wget
      4 mount
      4 beryl-manager
      3 xvncviewer

---

### Post by haricharan on 2007-07-16
```
    137 sudo
     85 ls
     71 cd
     27 make
     21 pcp
     17 gksudo
     14 ./run.sh
     14 exit
      9 ./pricing
      9 ftp
```

---

### Post by earobinson on 2007-07-17
Wow its good to see this is still going, kinda cool looking at all the other comands people run!

---

### Post by xfile087 on 2007-07-17
240 sudo
     77 cd
     67 ls
     21 wine
     13 exit
     10 nano
      5 msiexec
      5 cp
      4 wget
      4 make

---

### Post by reacocard on 2007-07-17
93 sudo
     44 svn
     25 ps
     22 ./exaile
     19 ./vim-single-window.sh
     18 amixer
     17 python
     16 kill
     16 exaile
     14 ./repo.sh

---

### Post by esc1 on 2007-07-17
112 sudo
     55 cd
     35 ifconfig
     27 dir
     16 vlc
     15 ping
      4 history
      4 glxinfo
      4 beryl
      4 7z

---

### Post by antoxa on 2007-07-17
132 ./configure
     75 cd
     58 ./1.sh
     57 make
     51 su
     17 wget
     10 startx
      7 amule
      6 cmus
      5 uname
:popcorn:

---

### Post by Iandefor on 2007-07-17
>     124 sudo
     99 ls
     66 cd
     22 less
     16 man
     15 qemu
     14 grep
     13 history
     10 rm
     10 ./autogen.shI was throwing myself against various forms of splashy source yesterday, which I guess is where the ./autogen.sh comes from. Aside from that... qemu is pretty handy for testing remastered CD's.

---

### Post by smartboyathome on 2007-07-17
5 sudo
      2 history
      1 gnome-theme-manager
      1 glxgears
      1 gksudo

My install is very new ;)

---

### Post by mike102282 on 2007-07-17
1. sudo
It the only one i use.

---

### Post by Depressed Man on 2007-07-17
158 sudo
     61 cd
     58 dir
      9 wget
      8 ifconfig
      7 gksudo
      6 sh
      5 python
      5 azureus
      4 beagled

---

### Post by Mr.Auer on 2007-07-17
Hmm, this ones a pretty new install, had to change a broken motherboard yesterday and installed the whole system again while I was at it...
      19 sudo
      4 cd
      3 ifconfig
      2 w
      2 ssh
      2 make
      2 history
      2 gconf-editor
      2 free
      2 conky

And this one from my older box, few months in existance:
     188 sudo
     23 conky
     21 cd
     18 ssh
     18 ls
     16 mousepad
     13 avant-window-navigator
     11 make
      8 gkrellm
      8 gconf-editor

You can tell I dont do much real work in the CLI :p

---

### Post by tribaal on 2007-07-17
Love this bash hack :)

Bonus to anyone that gives me an alias line that does the same thing (got mixed up with the escape chars :( )

Here's my output:

     85 exit
     56 sudo
     53 cd
     52 ls
     43 fenris
     41 maj
     23 grendel
     22 nano
     12 metacity
     12 compiz

I'm an alias freak : Fenris and Grendel are two aliases for ssh connections, and "maj" is an alias to "sudo aptitude update && sudo aptitude upgrade" (maj is short for mise-à-jour, which is "update" in French)

So I'd love an alias for this...

alias mostused='...' ?

- trib'

---

### Post by Tuna-Fish on 2007-07-17
80 ifconfig
     56 sudo
     34 iptables
     25 defcon
     25 cd
     24 ls
     22 hdparm
     19 ps
     16 mousepad
     14 rar

The network was fubared for a while, due to a hardware failure at the other end. They blamed me first though, so I spent good 4 hours trying to get it to work. Talk about waste of time. Oh, and defcon is a great game.

---

### Post by stepan2 on 2007-07-17
cd
make
make install
apt-get install
apt-get remove
apt-get update
apt-get upgrade

---

### Post by Atreus12 on 2007-07-17
> 
     82 ls
     72 cd
     50 sudo
     22 exit
     20 ps
     15 man
     14 if
     12 feh
     11 cat
      9 screen


Cool :KS

-Andrew

---

### Post by kevinlyfellow on 2007-07-17
For the user account

     76 sudo
     71 ls
     62 cd
     46 exit
     28 locate
     23 less
     21 cat
     17 man
     10 time
     10 rm

root account
     99 ls
     71 cd
     40 cat
     38 rm
     35 make
     22 exit
     19 cp
     18 bzip2
     13 make-kpkg
     13 dpkg

---

### Post by godd4242 on 2007-07-17
> **init1 said:**
> In mepis
     79 ls
     34 firefox
     31 VisualBoyAdvance
     21 rm
     20 bg
     18 df
     17 halt
     15 xmms
     12 wine
     10 killall

Haha visualBoy

Good times

---

### Post by LookTJ on 2007-07-17
```
     75 sudo
     19 ls
     16 tar
      8 exec
      7 cat
      6 pacman
      5 wget
      4 startx
      4 rm
      3 vim

```

---

### Post by Hortinstein on 2007-07-19
101 ls
     46 cd
     40 exit
     27 sudo
     22 synergyc
     19 make
     19 iwlist
     13 locate
     12 nethack
     12 killall

---

### Post by tbroderick on 2007-07-19
Fresh install.
```

53 cd
41 fdm
40 vi
36 less
35 mplayer
33 rm
29 ncmpc
28 mutt
27 wget
27 ls

```

---

### Post by tomcheng76 on 2007-07-19
41 sudo
     22 ls
     21 cd
     18 ps
      7 history
      5 rm
      5 mv
      4 kill
      4 cat
      3 which

---

### Post by B-Con on 2007-07-19
> 159 sudo
     38 gcc
     30 man
     27 ls
     19 arp
     18 cd
     12 ping
     11 who
     10 tty
     10 find

Not representative of my average usage, though. "gcc" and "arp" are due to my developing an ARP related program in C at the moment. "who" and "tty" was me experimenting with login shells.

---

### Post by PrimoTurbo on 2007-07-19
New install of Ubuntu

     54 sudo
     11 dir
     11 cd
      4 gpg
      3 ./usp_update
      3 mkdir
      2 killall
      2 history
      1 svn
      1 rmdir

---

### Post by PrimoTurbo on 2007-07-19
Does everyone have a fresh install or something, because according to the numbers you guys don't use the computer much. My results are only after a 1 day install of ubuntu and I already have used sudo 54 times.

---

### Post by oddin85 on 2007-07-19
155 ls
    107 cd
     38 sudo
     25 make
     21 clear
     19 emacs
     13 ./main
     12 nautilus
     11 gedit
     10 rm

:popcorn:

---

### Post by PatrickMay16 on 2007-07-19
Here's the result for my desktop computer:
     97 cd
     51 ls
     44 timidity
     39 mplayer
     39 aplaymidi
     24 sudo
     24 exit
     22 dmesg
     20 sfxload
     12 gayload

Here's the result for my laptop computer:
     63 sudo
     58 cd
     57 ls
     29 nano
     21 cat
     20 ./ftest3
     18 exit
     16 ping
     14 cpufreq-selector
     13 timidity

---

### Post by Nikron on 2007-07-19
> **PrimoTurbo said:**
> Does everyone have a fresh install or something, because according to the numbers you guys don't use the computer much. My results are only after a 1 day install of ubuntu and I already have used sudo 54 times.

Your history file is usually limited.  Mine only goes to 500.

---

### Post by Starchild on 2007-07-19
204 sudo
     26 xkill
     26 cd
     23 ping
     21 killall
     19 ls
     19 locate
     14 mpd
     13 man
     10 ssh

---

### Post by fjf on 2007-07-19
Firefox    'clic'
[www.ubuntuforums.com](www.ubuntuforums.com)
Absolute Beginner Talk       'clic'
Make New Post           'clic'
Help!! How do you.....
(waits 5-30 minutes and reloads the thread and reads)
Post reply              'clic'
Thankyou Thankyou Thankyou Thankyou Thankyou Thankyou

---

### Post by Rocket2DMn on 2007-07-19
In no particular order:
sudo/gksudo - applies to some of the below commands as well
mount -a
umount
ls
cd
cat
less
ssh
gedit
emacs
apt-get install/remove

runlevel 3 owns.

---

### Post by tszanon on 2007-07-19
85 cd
     78 ls
     64 java
     24 nice
     22 exit
     19 rm
     17 rmdir
     15 sudo
     10 gedit
      9 cat


By cd and ls being the most used, you can see I often don't know what's in the current folder... :)

---

### Post by tbroderick on 2007-07-19
> **Rocket2DMn said:**
> In no particular order:
.

Shouldn't there be a definite order?

---

### Post by Rocket2DMn on 2007-07-19
> **tbroderick said:**
> Shouldn't there be a definite order?

Yes, I wasn't in front of my computer to get the actual commands, I was estimating, here's the real thing:
    162 sudo
     26 ssh
     23 ls
     18 exit
     16 fdisk
     15 cd
     12 whereis
     10 wine
      9 gksudo
      7 lspci

However, I have multiple machines with different commands, so it doesn't quite match my estimates.

---

### Post by AlexenderReez on 2007-07-19
mine
>  
91 sudo
     11 tsocks
      7 compiz
      5 which
      4 history
      3 socks
      3 netstat
      2 locate
      2 conky
      1 wget


---

### Post by Uzura on 2007-07-20
95 sudo
 42 clear
 21 locate
 20 exit
 20 cd
 16 echo
 15 apropos
 9 pidof
 8 nano
 8 ./configure

I really don't know why I used echo so many times, but there it is. And I clear compulsively.

---

### Post by Cappy on 2007-07-21
63 man
     60 sudo
     40 cd
     33 echo
     23 ls
     20 locate
      9 dpkg
      8 wget
      8 nano

I'm suprised "ldd" and "apt-cache search" isn't on there .. I've used them SO much.

Wait .. I just tried the second command and it brings up less numbers than the first one =-/

---

### Post by xlinuks on 2007-07-21
129 jc
    124 ja
     57 clear
     46 cd
     32 ls
     22 sudo
     13 ja6
     11 eject
      7 ./work
      6 man
-------------------
Kernel panic: No CPU found

---

### Post by spupy on 2007-07-22
45 q          =quit
     42 sudo
     40 +          =clear
     30 amixer
     16 cd
     12 mpc
     12 l          =ls
      9 ps
      9 killall
      9 go          =a script to start the music, check the repos and fetch the mail
      7 leafpad
      6 search          =apt-cache search
      6 install          =apt-get install

Aliases ftw :D

---

### Post by Nekiruhs on 2007-07-22
143 sudo
     25 man
     21 locate
     17 cd
     15 nautilus
     15 killall
     15 gksudo
     14 newpy
     14 fg
     13 ./autogen.sh

Newpy is a custom written bash script to generate a preformatted. chmod-ed, GPLed Python script file, then open it in gedit. We all should  know what ./autogen.sh is for.  Fg is up there 'cuz I use ctrl +Z alot. It just "unpauses" the process. I like man pages so man is up there (Usually its man tar, there are so many options I cant keep track of them)

---

### Post by Saner on 2007-07-22
Its a pretty new install


    12343434 whereis porn
    115 sudo
    111 cd
     69 ls
     22 cedega
     15 su
     15 kill
     14 ps
     10 exit
      6 wine
      6 rutilt

---

### Post by tszanon on 2007-07-22
> **Saner said:**
> 12343434 whereis porn
:lolflag:

---

### Post by blithen on 2007-07-22
8D

```
     102 sudo
     36 chmod
     25 cd
      9 traceroute
      8 wget
      5 vimtutor
      5 exit
      4 vim
      3 shutdown
      3 ./pbsetup.run
```

---

### Post by kknd on 2007-07-22
113 sudo
     88 cd
     76 ls
     21 ant
     17 make
     16 ./Teste
     12 locate
     12 java
     12 ./configure
     11 ssh

---

### Post by ivesjd on 2007-07-24
141 ls
    123 sudo
    110 cd
     23 exit
     15 mv
      9 cat
      7 fanspeed
      6 firefox
      6 ./coretemp
      4 top

Fanspeed is an alias to read out my fan speed, which would be something like "cat /sys/devices/platform/applesmc/fan0_actual_speed" I dont know what I would do without aliases!

---

### Post by Gadren on 2007-07-24
252 sudo
     37 truecrypt
     33 cd
     20 ls
      9 DISPLAY=:0
      8 fbsetbg
      7 gpg
      7 feh
      6 startx
      6 make
 :)

---

### Post by depeo on 2007-07-24
Here's my irc box :)

    107 screen
     63 sudo
     58 ls
     57 cd
     54 ping
     44 nano
     24 exit
     12 traceroute
     12 rm
     12 ps

---

### Post by Billy_McBong on 2007-07-27
```
[COLOR="Blue"]    135 sudo
     51 cd
     47 man
     22 exit
     20 compiz
     15 clear
     13 wminput
     13 ls
     10 wget
      9 fortune[/color]
```
> **Saner said:**
> I12343434 whereis porn

[COLOR="Blue"]ROFL:lolflag:[/COLOR]

---

### Post by runemaste644 on 2007-08-02
76 cd ( i change directories a lot)
     61 sudo (from sudo -i and sudo nautilus)
     23 ./configure (from configuring packages (doesnt always work))
     18 if (i knew i would say what i use it for) :lolflag:
     12 echo (same)
     11 print (same)
     11 make (from when ./configure worked)
     10 fi (i dont know)
     10 exitcode=1 (something)
     10 compiz (I have Compiz Fusion)

but now it says

     45 cd
     44 sudo
     38 figlet
     30 my
     26 compiz
     21 make
     17 aptitude
     10 =>
      9 d
      9 ./configure

---

### Post by tszanon on 2007-08-02
> **runemaste644 said:**
> 23 ./configure (from configuring packages (doesnt always work))
     11 make (from when ./configure worked)
From 23 tries, only 11 succeeded...yeah, sometimes, things don't work. :)

---

### Post by Ballena on 2007-08-02
My stats: 

```
     51 clear
     48 cd
     40 sudo
     27 ls
     21 unrar
     14 unzip
     14 cowsay
     10 exit
      6 cal
      5 rm
```

---

### Post by crimesaucer on 2007-08-02
```

blah@blah-blah:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    221 sudo
     56 for
     31 conky
     29 ls
     26 acpi
     22 killall
     19 free
     18 twf
     15 cd
      8 mv
blah@blah-blah:~$ 


```

---

### Post by BackwardsDown on 2007-08-02
>     121 make
     61 ls
     60 ./main
     36 ./tetris
     30 cd
     27 qmake-qt4
     22 sudo
     21 compiz
     11 clear
     10 qmake

Currently making my own tetris game :)

---

### Post by BDNiner on 2007-08-02
75 sudo
     14 ls
     12 cd
      9 novelclient
      6 gpg
      3 ./install-sh
      3 chmod
      2 svn
      2 idle
      1 wget

This is what i got.

---

### Post by drocko on 2007-08-02
108 ls
     74 cd
     66 sudo
     20 ps
     18 echo
     16 ssh
     15 vi
     14 apt-cache
     13 pdflatex
     13 man

I am glad that LaTeX made it on there!

---

### Post by milosz.galazka on 2007-08-02
#history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr

     45 cd
     38 route
     37 ls
     22 ps
     21 ifconfig
     20 cat
     18 vpnc
     13 vi
     13 man
     12 ping

$history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
     50 ls
     47 cd
     44 sudo
     40
     10 ps
     10 dls
      9 wine
      9 cat
      6 man
      6 make

---

### Post by thatswhatshesaid on 2007-08-02
history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
     67 ls
     62 exit
     55 ssh
     45 xvncviewer
     44 ping
     31 cd
     17 telnet
     11 sudo
     10 gedit
      8 diff

history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     89 ls
     73 xvncviewer
     70 exit
     59 ssh
     52 ping
     38 cd
     17 telnet
     14 sudo
     11 gedit
      9 df

...it's a work computer

---

### Post by coastdweller on 2007-08-06
85 sudo
     26 ssh
     21 exit
     21 cd
     16 ls
     11 ping
      5 sh
      5 pico
      5 locate
      4 w
edgymands

---

### Post by jamienos on 2007-08-06
133 sudo
     16 cd
      6 dir
      4 vdrift
      4 gpg
      4 frozen-bubble
      4 ./configure
      3 rm
      3 nautilus
      3 compiz

V drift can pretty much be ignored.. couldent even get it to work and i dont even have it anymore

133 sudo.. hmmm :P all that sudo apt-get and sudo gedit and sudo.... :)

---

### Post by bmathis on 2007-08-06
heres mine

    244 sudo
     56 dir
     25 cd
     18 ssh
      8 mysql
      7 ifconfig
      6 ls
      5 dig
      4 tail
      4 ping

---

### Post by g2g591 on 2007-08-06
lots of sudo here too
 114 sudo
     30 cd
     11 wine
      8 ls
      7 wget
      6 winecfg
      6 sh
      6 man
      6 gpg
      6 gksu
i don't even use wine anymore (given up on it working on the one thing i needed it to)

---

### Post by Ozor Mox on 2007-08-06
```
     
     72 ls (directory stuff)
     69 sudo (being a super user)
     64 cd (directory stuff)
     29 exit (for some reason I use this instead of clicking the X!)
     21 java (messing around trying to get Java to work)
     17 rsync (making backups to my external hard drive)
     16 ssh (logging in to my friend's remote server)
     14 gksudo (running graphical apps as root)
      7 update-java-alternatives (more messing with Java)
      7 man (making sure I won't blow up my computer with a command!)

```

Mine and why I use them!

---

### Post by Steve1961 on 2007-08-06
87 sudo
     54 cat
     20 ls
     18 smbtree
     17 aptup
     14 cd
     12 smbclient
     10 aptcl
      9 vncviewer
      8 wget

---

### Post by jagomez on 2007-08-06
123 sudo
     85 ls
     72 cd
     41 ps
     27 kill
     16 lspci
      9 effectv
      8 mkdir
      5 tar
      5 rm

---

### Post by asleepfromtheday on 2007-08-06
14 su
     11 cd
      9 ls
      3 history
      2 /usr/ktoon/./ktoon
      2 mv
      2 ./ktoon
      2 gnome-splashscreen-manager
      2 glxinfo
      2 compiz

for root

     22 ls
     17 apt-get
     13 nano
     12 cd
     11 splashy_config
      7 sudo
      6 splashy
      5 synaptic
      5 rm
      5 chmod

Mind you i formatted yesterday! :)

---

### Post by RideP2 on 2007-08-06
188 sudo
41 ls
36 cd
28 ./update
26 ./upgrade
12 make
9 top
9 svn
8 man
8 gksudo

---

### Post by RebounD11 on 2007-08-06
47 sudo
     14 cd
      9 ls
      3 svn
      2 yakuake
      2 winecfg
      2 vmware
      2 locate
      2 java
      1 wineprefixcreate

---

### Post by Xyhthyx on 2007-08-06
112 sudo
    111 cd
     69 ls
     29 ps
     21 svn
     17 nano
     12 irssi
     11 rtorrent
     10 parcelle
     10 cat

---

### Post by rahul_bhise on 2007-08-14
50 cd
 46 sudo
 25 ls
 25 ./configure
 20 vnstat
 19 exit
 13 make
 12 man
 11 whereis
 10 pwd

---

### Post by Dmole on 2007-08-15
user:
     75 ls
     69 screen
     60 ps
     52 man
     48 su
     35 cd
     33 exit
     22 top
     16 du
     13 rtorrent

root:
    111 vim
     62 ls
     24 ps
     18 exit
     18 cd
     17 rm
     16 mount
     16 cp
     15 top
     15 man

---

### Post by fluteflute on 2007-08-15
184 sudo
     41 cd
     20 aptitude
     15 ls
     10 man
      9 wine
      9 ps
      8 wget
      8 mysql
      8 apt-get

---

### Post by k0r3 on 2007-08-15
104 apt-get
     47 ls
     39 cd
     33 vi
     27 apt-cache
     16 ssh
     13 su
     12 ifconfig
     11 dpkg
      8 umount

---

### Post by andrew.46 on 2007-08-27
Hi,

 Fascinating exercise:

    113 exit
     89 slrn
     80 mutt
     41 man
     16 abcde
     11 sudo
     11 apt-cache
      9 whereis
      8 ncftp
      3 vim

But I notice that nobody else features 'exit'. Is everybody closing their Terminal window with a mouse?

               Andrew

---

### Post by PurposeOfReason on 2007-08-27
Most of the killall is for conky when I was editing it.

    129 sudo
     73 killall
     32 cd
     12 avatar-factory
     12 ./autogen.sh
     11 bzr
     10 conky
      8 locate
      8 links2
      7 make

---

### Post by LookTJ on 2007-08-27
me:

    141 sudo
     40 ssh
     37 exit
     28 ./.xinitrc
     19 armagetronad
     15 fusion-icon
     15 cat
     13 ls
      7 scrot
      6 top

---

### Post by reacocard on 2007-08-27
> **andrew.46 said:**
> Hi,

 Fascinating exercise:

    113 exit
     89 slrn
     80 mutt
     41 man
     16 abcde
     11 sudo
     11 apt-cache
      9 whereis
      8 ncftp
      3 vim

But I notice that nobody else features 'exit'. Is everybody closing their Terminal window with a mouse?

Alt + F4 mostly for me, it's faster than either mouse or exit. :D

---

### Post by markp1989 on 2007-08-27
189 sudo
     37 cd
     25 top
     14 fdisk
     13 switchmon
     13 startx
     10 umount
     10 mkfs.ext2
     10 cp
      8 zenity

---

### Post by P4oL1n0 on 2007-08-27
241 sudo
     56 cd
     19 dput
     11 wget
     11 exaile
      8 ls
      7 make
      7 debuild
      7 apt-cache
      6 pdebuild

Great Topic :lolflag:

---

### Post by Lux Perpetua on 2007-08-27
Fun topic. :-)

```
    118 g++
     99 a.out
     54 ls
     39 cd
     23 ssh
     21 cat
     16 exit
     13 tilda
     13 emacs
      8 sedtest
```(sedtest is a small script I was using to learn sed.)

---

### Post by Gwasanaethau on 2007-08-27
Mine are so boring!

117 sudo
60 ls
59 cd
45 echo
43 exit
27 gedit
24 sleep
16 bash
14 rm
12 gksu

---

### Post by red_Marvin on 2007-08-27
98 sudo
65 cd
57 ls
57 fbc
29 nano
25 ./et
12 ps
12 ping
11 man
11 killall

fbc: the freebasic compiler
et: enemy territory - a game

---

### Post by reclusivemonkey on 2007-08-27
> **andrew.46 said:**
> 
But I notice that nobody else features 'exit'. Is everybody closing their Terminal window with a mouse?

I'm just not closing my terminal =]

---

### Post by Kosimo on 2007-08-27
Here are mines:

     31 sudo
     18 cd
     11 ping
      9 dir
      5 wine
      3 glxinfo
      2 sudo-cache
      2 make
      2 iptables
      2 ./install.sh

---

### Post by reacocard on 2007-08-27
Update of mine:

Method 1:
```
    502 sudo
    138 svn
    102 cd
     85 ps
     77 man
     77 ls
     67 python
     64 bzr
     61 killall
     59 cat

```

method 2:
```
    480 sudo
    125 svn
     99 cd
     84 ps
     77 man
     77 ls
     64 python
     59 killall
     59 cat
     57 rm

```

---

### Post by Lux Perpetua on 2007-08-27
Current standings:

```
   16327 sudo
    9486 evolution
    8620 cd
    8074 ls
    1623 exit
    1312 man
     875 su
     862 echo
     796 ps
     793 ssh
     759 vim
     659 cat
     627 svn
     627 locate
     577 make
     577 clear
     569 rm
     561 dir
     550 sed
     475 ping
     470 killall
     441 wget
     358 apt-cache
     289 g++
     288 d
     285 mc
     279 screen
     273 grep
     271 nano
     266 kill
     265 ./configure
     252 apt-get
     248 wine
     243 gedit
     238 for
     232 python
     220 vi
     216 java
     211 ifconfig
     202 top
     184 find
     182 pacman
     174 mv
     170 javac
     167 gksudo
     165 conky
     164 date
     161 less
     158 cp
     156 chmod
     152 l
     149 history
     143 mutt
     139 mount
     139 printf
     133 nohup
     132 smart
     130 compiz
     129 jc
     127 startx
     124 ja
     116 ncmpc
     111 ./task2.o
     107 aptitude
     105 df
```If you posted twice, then you voted twice. Commands with fewer than 100 votes are not included. I'm actually surprised that so many people use sudo so often. It's not even in my top ten.

---

### Post by amazingtaters on 2007-08-27
108 sudo
     56 cd
     13 wine
      7 conky
      6 nmap
      5 wget
      5 top
      5 synclient
      5 gedit
      4 unrar

---

### Post by snowbalrog on 2007-08-27
Here's mine.. 

     55 wine
     26 sudo
     20 cd
     10 pwd
      7 winecfg
      7 ls
      7 ifconfig
      6 whois
      6 nautilus
      5 ping

Looks like I have a drinking problem :)

---

### Post by King_Critter on 2007-08-28
112 sudo
     50 cd
     19 make
     17 gksudo
     15 metacity
     14 compiz
     13 ls
     11 g++
     10 winecfg
      7 wget

---

### Post by Naralas on 2007-08-28
96 g++
     49 sudo
     48 clear
     42 ./chat
     29 cd
     24 gcc
     20 aptitude
     19 exit
     16 metacity
      9 ssh

./chat is there because its a program I was writing.
metacity because I gotta turn off compiz when I run WC3
Also, this install is only 2 weeks old or so.

---

### Post by cudaman73 on 2007-08-29
40 sudo
     14 cd
     13 ls
      7 tar
      5 ./configure
      4 wget
      3 rm
      3 mv
      3 mkdir
      3 echo


but i'm also running on a fresh install (less than a day old), so i suppose i'm where i'm supposed to be :P

fighting with compiz is what caused all the sudos

---

### Post by Pjotrovitz on 2007-08-29
84 java
     67 javac
     50 sudo
     30 cd
     23 ls
      3 cat
      2 wget
      2 mplayer
      2 mount
      2 info
 Just started learning java :p

---

### Post by PHuN on 2007-08-29
server:
```
   
     52 nano
     49 postconf
     44 apt-get
     15 cd
     11 openssl
     11 mysqladmin
     11 mkdir
     10 a2enmod
      9 ln
      8 cp

```

workstaion user:
```

      72 sudo
      5 wget
      5 glxgears
      4 su
      3 nano
      3 cd
      2 ls
      1 tremulous
      1 putty
      1 plog

```

workstaion su:
 ```

      23 sudo
      6 nano
      5 putty
      1 cp
      1 cd

```

**EDIT** Must not have realized that I was su to use all of theose sudo's **EDIT**

---

### Post by Lux Perpetua on 2007-09-01
Now that we have all this data, here's another fun game: **how does your terminal command usage compare to everybody else's?** Here's a quick python program that computes a "similarity score" based on your top 10 terminal commands and the totals in my previous post: ```
import math
import sys

def two_norm(a):
    total = 0
    for key in a:
        val = a[key]
        total += val*val
    return math.sqrt(total)

def dot_prod(a, b):
    total = 0
    for key in a:
        if key in b:
            total += a[key]*b[key]
    return total

def similarity(a, b): 
    return dot_prod(a, b)/(two_norm(a) * two_norm(b))

def tally(f):
    a = {}

    import re
    format = re.compile('\s*(\d+)\s*(\S+)')
    for line in f:
        match = format.match(line);
        if match:
            key = match.group(2)
            if key not in a:
                a[key] = 0
            a[key] += int(match.group(1))

    return a

try:
    print "Similarity score: ", 
    print 100*similarity(tally(open(sys.argv[1])),
                         tally(open(sys.argv[2]))),
    print "%"

except IOError:
    print "error reading files"

except ZeroDivisionError:
    print "undefined"

```To use it:
[list="1"][*]Save my program to a file, say **sim.py**. 
[*]Take the "top 10" output from the OP's shell command and save that to a file. For example, let's save PHuN's server top 10 (post before this one) to **top10.txt**:
```
   
     52 nano
     49 postconf
     44 apt-get
     15 cd
     11 openssl
     11 mysqladmin
     11 mkdir
     10 a2enmod
      9 ln
      8 cp
```[*]Take the thing you want to compare it to, namely my totals from the earlier post, and save that to a file, say **total.txt**: ```
   16327 sudo
    9486 evolution
    8620 cd
    8074 ls
    1623 exit
    1312 man
     875 su
     862 echo
     796 ps
     793 ssh
     759 vim
     659 cat
     627 svn
     627 locate
     577 make
     577 clear
     569 rm
     561 dir
     550 sed
     475 ping
     470 killall
     441 wget
     358 apt-cache
     289 g++
     288 d
     285 mc
     279 screen
     273 grep
     271 nano
     266 kill
     265 ./configure
     252 apt-get
     248 wine
     243 gedit
     238 for
     232 python
     220 vi
     216 java
     211 ifconfig
     202 top
     184 find
     182 pacman
     174 mv
     170 javac
     167 gksudo
     165 conky
     164 date
     161 less
     158 cp
     156 chmod
     152 l
     149 history
     143 mutt
     139 mount
     139 printf
     133 nohup
     132 smart
     130 compiz
     129 jc
     127 startx
     124 ja
     116 ncmpc
     111 ./task2.o
     107 aptitude
     105 df
```
[*]Run the command ```
python sim.py top10.txt total.txt
``` and post the output! In this example, the score is about 7.78%, which is quite low. My score is higher, but still low: 22.20%. [/list]

I think my program is pretty robust: your files can have garbage in them; it'll just be ignored. Also, you can have multiple lines with the same command, and they'll all be counted. 

If any of you is a statistician, feel free to replace my similarity test by something more sophisticated. As far as I know, my similarity score isn't a useful statistical measure of anything; it's just a rough sort of correlation.

---

### Post by mpgarate on 2007-09-01
203 sudo
     42 cd
     19 wget
     17 chmod
     13 tar
     11 xvidcap
     10 obexftp
      9 obex_test
      8 ./get_play_counts.rb
      8 cp

---

### Post by davtaine on 2007-09-02
63 su
     43 lsof
     28 exit
     23 top
     14 free
     14 apt-cache
     11 infobash
      9 glxgears
      5 htop
      3 w

---

### Post by ryno519 on 2007-09-02
> **andrew.46 said:**
> Hi,

 Fascinating exercise:

    113 exit
     89 slrn
     80 mutt
     41 man
     16 abcde
     11 sudo
     11 apt-cache
      9 whereis
      8 ncftp
      3 vim

But I notice that nobody else features 'exit'. Is everybody closing their Terminal window with a mouse?

               Andrew

     145 ls
     99 cd
     73 sudo
     60 exit
     22 clear
     17 make
     10 ./configure
      8 mkdir
      7 rm
      5 vrms

Guess this makes two of us. :P

---

### Post by Bothered on 2007-09-02
112 g++
     63 ./PrimeFind
     62 ls
     58 cd
     28 ./a.out
     14 sudo
     12 ./NumFind
      9 rm
      8 gedit
      6 less

Gives away my recent playing around with the GNU MP library.

---

### Post by Bert_2 on 2007-09-02
Here are mine:

154 sudo
61 cd
13 man
12 wine
12 java
11 nvidia-installer
10 rm
9 umount
8 ping
8 clear

---

### Post by hessiess on 2007-09-02
148 cd
     72 ls
     67 make
     60 sudo
     16 ./main
     16 alsamixer
      8 lspci
      7 nano
      7 exit
      6 uptime

---

### Post by Bachstelze on 2007-09-02
Updated :p

Myself@desktop :

    117 sudo
     46 ls
     41 cd
     29 echo
     17 wine
     13 unzip
     13 cat
     12 man
     11 mv
     11 mplayer


root@desktop :

     20 exit
     13 nano
     12 sudo
     11 echo
     10 emerge
      8 hibernate
      5 make
      4 mirrorselect
      4 chroot
      4 cd


Myself@server :

  66 cd
  56 ls
  45 sudo
  39 ps
  35 nano
  32 fortune
  22 mutt
  22 less
  19 echo
  18 exit

---

### Post by Skrynesaver on 2007-09-02
Curious idea, it might be worthwhile to see what similarity score is needed to fit everyone within say 3 groups and to see if we could classify the role of the computer on that basis.  Just goes to show even the most harmless revelation of information can reveal information you hadn't expected to reveal.

---

### Post by saxin on 2007-09-02
50 sudo
     25 cd
     17 ls
     15 ssh
     11 wine
      6 alsamixer
      5 apt-cache
      3 uname
      3 man
      2 vmware

---

### Post by Tea4all on 2007-09-02
Me :64 sudo
      39 cd
      38 ps
      24 ls
      20 wine
      11 echo
      11 a1=`ps
       9 man
       9 find
       8 winecfg

---

### Post by Dr Small on 2007-09-02
100 sudo
     50 crontab
     25 cd
     19 man
     19 date
     17 clear
     16 ssh
     15 tor
     15 killall
     13 exit

---

### Post by ryanVickers on 2007-09-02
first command (history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr):
> 
    116 sudo
     35 clear
     23 slow
     22 clean
     16 glxgears
     15 ls
     13 finder
     11 gconf-editor
     10 superclean
     10 ./slow.sh


second command(history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr):
> 
    108 sudo
     23 clear
     20 slow
     17 clean
     16 glxgears
     10 superclean
     10 gconf-editor
     10 cd
      9 ls
      9 gksudo


I don't use it alot! :)

superclean, clean, slow, and finder are all custom scripts :), which tend to use other commands, like gconf-cleaner and clean (from superclean)...

---

### Post by nest on 2007-09-02
140 sudo
     86 killall
     82 conky
     21 ls
     18 cd
     17 irssi
     11 exit
     11 apt-get
     10 fg
      9 python

---

### Post by Kolfinna on 2007-09-02
29 nano
     28 iwlist
     26 exit
     25 iwconfig
     23 apt-get
     15 ifconfig
     11 ls
     10 sudo
      9 man
      9 dhclient

---

### Post by pissedoffdude on 2007-09-02
162 exit
     64 sudo
     60 winecfg
     35 wine
     16 cd
     12 net
     11 killall
     10 python
     10 gksudo
      8 scrot

---

### Post by Dylnuge on 2007-09-02
Here are mine:
sudo
ls
cd
man
file
kill
python
echo
lspci
du

Of course, I use the terminal a lot, so this is really only slightly correct. If I went with my entire history, lspci, echo, and man would be lower on the list or off the list whatsoever, and apache2, mysql, and some other server stuff would be up there.

---

### Post by wormser on 2007-09-03
71 sudo
70 apt-cache
31 ls
27 cd
20 less
19 exit
12 ping
12 man
10 nmap
   9 ssh

---

### Post by nowshining on 2007-09-03
sudo
sudo gedit
sudo gedit /etc/hosts
gksudo nautilus
exit
apt-get install -f
apt-get autoremove
apt-get autoremove
sudo ipblock status
sudo

all are out of order and I cannot think of no more..

---

### Post by AirOnSkin on 2007-09-05
user:
    100 sudo
     77 cd
     48 exit
     43 ls
     20 clear
     18 rm
     14 renrot
     11 mount
      9 rsync
      9 man

super-user:
     40 cd
     24 ls
     16 clear
     13 exit
     13 chown
     12 chmod
      8 ./vmware-install.pl
      8 rm
      7 mount
      6 mkdir

hmm... what does that say now? ;)

---

### Post by j.miller565 on 2007-09-26
112 sudo
     48 cd
     23 make
     19 ./configure
     18 startx
     10 kcontrol
     10 envy
      5 autoconf
      4 dir
      3 shutdown

---

### Post by dbodner on 2007-09-27
Me:
    157 ssh
     72 ls
     69 ping
     17 cd
     15 rm
     14 vi
     14 scp
     12 history
     11 whois
     11 less

Root:
     69 vi
     67 ls
     28 cd
     26 ping
     18 getent
     17 rm
     15 sudo
     15 make
     12 ps
     12 grep

---

### Post by Chii on 2007-09-27
I've not used Ubuntu for long, so I do not think I even know ten commands in total, but I will post what I have used a number of times.

sudo gedit
sudo apt-get
cd
dir
ls
mann
wine
rm
rmdir
and I think it was rm rf?  To delete folders with files in them.

Okey so never mind.  I do have a list of 10 commands I've used/know how to use and as a result use them a lot :p

---

### Post by fuscia on 2007-09-27
reinstalled about two weeks ago

 107 sudo
     30 cd
     30 apt-cache
     24 killall
     22 ncmpc
     20 nano
     19 ls
     16 conky
     11 urxvt
      9 startx

i'm pretty sure the conky and urxvt reps were from setting them up.

---

### Post by Nevon on 2007-09-27
138 sudo
83 cd
34 ls
11 chmod
10 exit
9 rails
8 ruby
8 ./configure
7 dpkg
6 gksudo

---

### Post by daverich on 2007-09-27
133 sudo
     64 ls
     64 cd
     16 emerald
     15 man
     12 gdesklets
     10 powersave
      9 tar
      9 chmod
      7 metacity

like anyone cares ;)

---

### Post by Zamber on 2007-10-19
506 sudo
    328 mpc
    190 cd
    146 python
    100 man
     96 ls
     82 killall
     80 vim
     76 isup          # my script for automatic screen shoot taking and uploading on imageshack :)
     70 mplayer

I rock :P. :guitar:

---

### Post by Anessen on 2007-10-19
Mine are...
    103 sudo
     74 cd
     67 ls
     48 python
     19 conky
     14 man
     11 killall
     11 aptitude
      8 gedit
      8 chmod

---

### Post by mkzimms on 2007-10-19
143 sudo
     72 cd
     54 ls
     30 ssh
     26 ping
     19 clear
     16 vncviewer
     16 exit
     13 tilda
     13 find

---

### Post by iPower on 2007-10-19
102 sudo
     91 exit
     77 ifconfig
     64 uptime
     29 date
     19 ls
     15 cd
     10 glxgears
      8 ip
      7 ping

---

### Post by ravirdv on 2007-10-20
112 sudo
     24 ls
     22 ftp
     22 cd
     16 nmap
     14 wine
      9 ping
      8 exit
      7 netstat
      5 apt-get

---

### Post by -grubby on 2007-10-20
22 sudo
      4 exit
      3 dir
      2 synaptic
      2 kdm
      2 is
      1 firefox
      1 winecfg
      1 update-menus
      1 update-menu

---

### Post by RAV TUX on 2007-10-20
```
ravtux@CafeLinux:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     60 sudo
      1 wget
      1 update-manager
      1 sudp
      1 path/to/firefox-mozilla-thunderbird
      1 ~/.mozilla/
      1 mousepad
      1 kate
      1 history
      1 --fix-cvs-conflicts

```

---

### Post by arsenic23 on 2007-10-20
It's kind of interesting to look at my results from the beginning of this thread and compare them to my results now.

was:
> 122 find
66 ls
37 sudo
30 cd
28 ping
27 rename
21 cll ( cd ~/ && clear && ls )
15 vlc
14 mv


is:
> 73 ls
51 sudo
49 cd
35 mv
20 for
19 rename
13 acs ( apt-cache search )
12 python
9 cl ( clear && ls )
8 ln


---

### Post by TidusBlade on 2007-10-20
36 cd
     33 sudo
     26 xkill
     26 ls
     23 su
     14 rogue
      9 nethack
      8 winecfg
      7 uptime
      7 chmod
Not much being done there :p

---

### Post by feisty on 2007-10-20
144 sudo
     71 ls
     45 exit
     42 cd
     16 aircrack-ng
     15 ./configure
     13 john
     12 make
      6 airodump-ng
      5 tar

---

### Post by montres on 2007-10-20
Here is my list:

 76 cd
     61 sudo
     33 ls
     30 man
     22 wine
     11 clear
      9 top
      7 apt-file
      6 vi
      6 Code:

---

### Post by tatewaki on 2007-10-20
My list:

43 sudo
22 sshfs
15 cd
11 ps
9 kill
8 xbindkeys
8 nano
5 hping2
4 killall
4 kate

---

### Post by Arwen on 2007-10-20
105 sudo
     60 clear
     49 cd
     44 gcc
     34 javac
     33 ls
     25 ./a.out
     17 kill
     15 java
     13 ps

---

### Post by SS2 on 2007-10-21
My list:

     36 screen
     34 cd
     23 conky
     21 ls
     20 killall
     20 clear
     19 vim
     17 ssh
     12 qemu
     10 cat

Regards

---

### Post by fuscia on 2007-10-21
since installing gutsy on friday...

     66 sudo
     23 cd
     20 nano
     20 ls
     19 apt-cache
     13 ncmpc
      8 feh
      5 streamripper
      4 mplayer
      3 exit

---

### Post by x0as on 2007-10-21
75 ls
44 nano
42 cd
32 du
23 mencoder
22 more
19 rm
19 apt-cache
17 killall
15 vlc

---

### Post by bashveank on 2007-10-21
95 sudo
     57 ls
     46 cd
     32 ps   ; Freaking unstable Firefox
     23 kill   ; Freaking unstable Firefox
     11 tracker-status ; It's _still_ indexing
      9 unrar
      9 cp
      8 gksudo
      7 chmod

---

### Post by mcrae on 2007-10-24
```
  
   143 ll
     51 cd
     37 sudo
     20 cat
     15 less
     14 vim
     14 qcppc01    # alias for ssh hostname....
     13 palina        # alias for ssh .....
     13 mm            #alias for sshfs ....
     11 mmfqcppc #alias for sshfs ....

```

---

### Post by Acglaphotis on 2007-10-24
67 sudo
     46 vim
     42 python
     38 ls
     34 vimer # a vim launcher i made
     27 install # alias for sudo aptitude install 
     23 gnome-terminal
     23 cd
     22 ./vimer #same as above
     13 acpi

---

### Post by ahaslam on 2007-10-24
136 mencoder
     24 rm
     15 cd
     11 time
      7 sudo
      6 man
      5 mplayer
      3 gnome-terminal
      2 xkill
      2 top

^ Mainly been encoding since installing Gutsy ;)

---

### Post by RageOfOrder on 2007-10-24
For my user:
> 
     64 ls
     62 clear;
     52 cd
     28 su
     24 slocate
     20 cat
     18 java
     17 wine
     17 javac
     16 rm


For root:
> 
     88 emerge
     37 ls
     27 nano
     24 mkdir
     22 mount
     21 cd
     13 umount
     13 killall
     11 rm
     11 clear


---

### Post by pt123 on 2007-10-24
200 sudo
     51 cd
     41 sh
     28 mplex
     20 ls
     18 nano
     16 java
     14 ping
      7 ps
      7 gedit

---

### Post by Anonii on 2007-10-30
User:
     67 mplayer
     55 ls
     54 sudo
     53 cd
     43 irssi
     31 su
     23 nano
     19 gcc
     18 ./a.out
     15 gmplayer

Root:
     50 emerge
     15 su
     14 ls
     12 cd
      8 nano
      8 locate
      7 gvim
      7 dmidecode
      7 cat
      5 eix

---

### Post by RebounD11 on 2007-10-30
1  40  12.945%    cd
     2  38  12.2977%   ls
     3  32  10.356%    grep
     4  30  9.70874%   su
     5  22  7.11974%   glxinfo
     6  13  4.20712%   clear
     7  11  3.55987%   gedit
     8  8   2.589%     echo
     9  7   2.26537%   script
    10  7   2.26537%   man


Although I should mention I am using openSuSE 10.3 :D

---

### Post by ticopelp on 2007-10-30
```
215 sudo
     51 ls
     38 cd
     14 make
     14 ./configure
     11 aptitude
      8 top
      7 nano
      7 killall
      7 clear

```

:-k

---

### Post by drawman on 2007-10-30
1 wget
      1 tar
      1 man
      1 ./ies4linux
      1 I
      1 history
      1 gksu
      1 cd
      1 cat

Total rookie with brand new upgrade.  Took out one line as it identified my computer.

---

### Post by svtfmook on 2007-10-30
sudo apt-get porn

sudo apt-get remove money

---

### Post by altu on 2007-10-30
1. sudo apt-get
2. find
3. man
4. exit
5. ls 
6. cd
7. mc
8. ping

---

### Post by LaRoza on 2007-10-30
```

     61 clear
     58 ls
     53 cd
     42 exit
     20 sudo
     18 python
     15 ./practice.py
      9 vim
      8 g++
      6 ping

```

My programs are often called "practice", if it has no particular use. It is used for testing functions, before implementing them.

---

### Post by fuscia on 2007-10-30
> **svtfmook said:**
> sudo apt-get porn

sudo apt-get remove money

try this: *sudo apt-get "picture your 3rd grade teacher naked"*. you'll thank me.

---

### Post by err_ok on 2007-10-30
134 sudo
     66 ls
     54 cd
     48 ssh
     20 cp
     17 rm
     16 make
     15 screenlets-manager
     12 nano
      9 exit

---

### Post by TheMono on 2007-10-31
sudo
patch
svn
cd
make
kwin
kate
ls
gocompiz
aptdate

The last two are my own aliases, one to start compiz with the --replace flag, and one to run sudo apt-get update.

---

### Post by gustavoavellar on 2007-10-31
131 sudo
     34 ls
     33 iwlist
     29 ifconfig
     29 cd
     25 man
     23 exit
     20 make
     18 xmkmf
     18 iwconfig

---

### Post by Christmas on 2007-10-31
Here's mine:
```
    159 sudo
     71 ls
     64 cd
     48 apt-cache
     12 less
      9 mount
      9 locate
      9 chmod
      8 ./configure
      7 ps
```
However this doesn't reflect the commands I use most since I reinstalled a couple of days ago. I guess the commands I use the most would be:
cd
ls -l
cp
rm
irssi
emacs --no-window
sudo apt-get update
sudo apt-get upgrade
apt-cache search
oggenc
flac

---

### Post by shearn89 on 2007-10-31
Fairly even spread - "ls" and "exit"... and a lot of media playing!

     54 ls
     54 exit
     36 sudo
     34 clear
     30 mpc
     29 cd
     19 rm
     15 ncmpc
     12 mplayer
      9 nano

---

### Post by justinhj on 2007-10-31
62 ls
     56 find
     26 fg
     23 cd
     21 emacs
     16 g++
     12 etags
     10 exit
     10 cvs
      9 man

---

### Post by Dirty Ole on 2007-11-01
146 sudo
     35 exit
     32 nestra
     31 cc
     24 ./is.out
     22 cd
     18 man
     18 locate
     18 cat
     10 javac

---

### Post by FG123 on 2007-11-01
666 rm -rf *

I seem to have lost the re

---

### Post by vikrant82 on 2007-11-01
```

    148 sudo
     40 ps
     29 cd
     15 ls
     12 man
     11 watch
      9 ping
      7 nmap
      7 make
      6 netstat

```

---

### Post by JAPrufrock on 2007-11-01
113 ls
 109 cd
  67 sudo
  40 cat
  23 ssh
  17 mysql
  14 networking
  10 scanimage
  10 df
   7 wine

---

### Post by ft2482 on 2007-11-01
77 sudo
     62 vnstat
     62 exit
     17 man
     10 cat
      8 ls
      7 glxinfo
      7 free
      6 glxgears
      5 top

---

### Post by xc3RnbFO8P on 2007-11-01
72 sudo
     18 cd
      8 make
      7 wine
      6 ./configure
      6 apt-get
      5 ndiswrapper
      5 lsusb
      5 gksudo
      5 fgfs

---

### Post by Yarbo on 2007-11-01
98 cd
     80 sudo
     62 ls
     31 dir
     21 dig
     14 rm
     12 wget
     12 top
     11 ./build_patch.pl
      8 man
 
Those would be the commands I use the most.

---

### Post by teishu on 2007-11-01
lol, you can tell ive only installed a few days ago.. not used it much..

     20 sudo
      2 ls
      2 gparted
      2 ccsm
      2 apt-get
      1 su
      1 history
      1 cd
      1 apt-update

---

### Post by mysticrider92 on 2007-11-01
Been trying to get some stuff working right in Gutsy:

     48 sudo
     15 cd
     12 dir
      7 apt-cache
      5 setxkbmap
      5 cat
      3 rm
      3 naim
      3 links
      2 xprop

I don't even use the links web browser at all...

---

### Post by alwiap on 2007-11-01
38 sudo
 38 conky
 35 gedit
 35 cd
 25 killall
 13 ls
  9 pwd
  4 gksudo
  3 apt-get
  2 zcat

---

### Post by p_quarles on 2007-11-01
My desktop only displayed results from the current session, so I logged into my server:
    137 sudo
     74 ls
     64 exit
     39 a2log
     38 uptime
     31 netstat
     19 cd
     16 cat
     13 rm
     12 df
"a2log" is just an alias for cat (apache logs).

---

### Post by C.A.T.S. CEO on 2007-11-01
root:
```
      6 ls
      5 cd
      2 su
      1 ssh
      1 pico
      1 exit

```

myself:
```
      4 irssi
      4 exit

```

---

### Post by myle on 2007-11-21
146 gcc
     78 ./server
     61 ./client
     30 cd
     27 exit
     10 pon
     10 poff
     10 ls
      9 sudo
      4 clear

---

### Post by hellion0 on 2007-11-21
Very recent install...

     18 sudo
     14 cd
     11 ls
      4 mkdir
      2 rm
      2 mplayer
      2 history
      2 exit
      2 cp
      1 ssh

---

### Post by Zyphrexi on 2007-11-21
101 cd
     84 ls
     44 sudo
     26 man
     15 java
     14 cmake
     13 wine
      9 make
      7 sh
      6 mkdir

---

### Post by -grubby on 2007-11-21
47 sudo
     15 apt-cache
     14 man
      9 exit
      6 cowsay
      4 nautilus
      4 firefox
      3 xkill
      3 vrms
      2 volume.app

---

### Post by Lostincyberspace on 2007-11-21
```
 6 mysql
      1 su
      1 mysqld
      1 ls
      1 iptables
      1 history
      1 cd
```

not bad for a two hour hold install.

---

### Post by Tristam Green on 2007-11-21
75 sudo
     26 exit
     13 conky
      8 man
      7 ./info.sh
      5 wget
      5 rhythmbox-client
      3 echo
      3 chmod
      2 top

---

### Post by fedex1993 on 2007-11-21
72 sudo
     33 conky
     31 nano
     23 ls
     21 apt-cache
     20 cd
     15 youtube-dl
      7 scrot
      7 man
      7 ./info.sh

that is what i use the most. the ./info.sh is a screenshot taker it is realy nice.

---

### Post by samwyse on 2007-11-22
252 sudo
     44 cd
     27 ls
     15 wget
     11 wine
     11 sensors
      8 man
      7 ./speedcontrol
      7 mc
      6 konqueror

I'm mostly sudoing apt-get.

---

### Post by Malcolm on 2007-11-22
93 python
     64 cd
     50 ls
     39 sudo
     27 vi
     19 mysql
     14 gcc
     14 ./anagram
     12 echo
     11 less

---

### Post by Trail on 2007-11-22
111 sudo (apt-get ... mostly)
     56 man (woman)
     28 ll (ls -l of course)
     22 k (alias for kate or kwrite, dont remember which)
     22 cd
     19 g++
     16 ./a.out (quick tests)
     14 ping
     11 ps
     11 grep

From my ~ PC, I assume it would look like:

sudo apt-get update
sudo apt-get upgrade
cd .wine/drive_c/Program\ Files\FulDC (switched to linuxdcpp though)
wine DCPlusPlus.exe 
cd .wine/drive_c/Program\ Files\Diablo\ II
wine Diablo
sudo apt-get install ...
ssh -X trail-laptop
sudo reboot
sudo gedit /etc/X11/xorg.conf :)

---

### Post by jclmusic on 2007-11-22
41 sudo
     15 cd
     10 python
      6 killall
      4 snakebite
      4 export
      2 ffmpeg
      2 dpkg-buildpackage
      1 wget
      1 py

---

### Post by revenant_org on 2007-11-22
95 ls
     80 cd
     56 sudo
     25 rxvt
     23 vim
     14 svn
      8 xrdb
      7 ./eclipse
      7 df
      6 rm

:popcorn:

---

### Post by happyhamster on 2007-11-22
126 wine
    105 sudo      (apt-get, nano, mount, etc)
     47 winecfg
     43 ls
     24 cd
     21 WINEDEBUG=-all
     16 nvidia-settings
     14 sh
     12 WINEDLLOVERRIDES="dinput=n"
     10 WINEDEBUG=+loaddll

---

### Post by bluehue on 2007-11-22
45 cd
     39 sudo
     31 ls
     29 wget
     19 find
     13 make
     11 ssh
      8 rm
      7 mkisofs
      7 locate

---

### Post by Blutack on 2007-11-22
168 sudo
     33 ssh
     32 cd
     23 scp
     21 man
     19 java
     17 javac
     15 keyjnote
     15 fakeroot
     14 gpg

Makes me look a lot more hardcore than I am :-)

---

### Post by zach12 on 2007-11-22
./WIFIHELPER (wifi config program i've been working on)
 chmod 755 WIFIHELPER
cd
ls
su
apt-get install wine
sudo apt-get update

---

### Post by smartboyathome on 2007-11-22
103 sudo (so many uses it is hard to name them all :))
     52 cd
     14 gedit
     12 ls (so I don't have to keep opening up thunar or nautilus :mad:)
     11 enlightenment_remote (enlightenment settings changer from terminal)
     10 wget
      9 make
      8 patch
      7 gpg
      7 debuild (debian package builder)

---

### Post by TheOrangePeanut on 2007-11-22
82 ls
     76 cd
     61 exit
     34 sudo
     32 file
     23 java
     17 /opt/jgrasp/bin/jgrasp
     15 unrar
     15 man
     13 less

Interesting :)

---

### Post by corney91 on 2007-11-22
128 sudo
     41 apt-cache
     38 ls
     33 cd
     30 man
     22 killall
     22 gedit
     18 firefox
     14 export
     13 top

Too many sudos? They're generally installing/uninstalling/upgrading though.

---

### Post by CrAzYoNi on 2007-11-22
233 sudo
     52 cat
     48 ls
     36 exit
     32 cd
     11 ps
      8 gem
      7 which
      7 mysql
      7 conky

---

### Post by arashiko28 on 2007-11-22
53 sudo
     10 man
     10 cd
      8 compiz
      6 emerald
      4 ls
      3 >
      2 sh
      2 history
      2 apt-get

Freshly installed, 2 weeks ago :)

---

### Post by stauntonel on 2007-11-22
94 ls
     68 cd
     56 apt-get
     30 apt-cache
     19 chmod
     17 cat
     16 cp
     12 locate
     11 nano
      7 man

---

### Post by frup on 2007-11-22
Mine currently.
     72 sudo
     64 ssh
     38 ls
     35 gcc
     34 cd
     22 echo
     15 nano
     14 ./io
     11 wine
     11 ./test2.sh


     63 sudo
     43 ssh
     34 ls
     31 cd
     28 gcc
     14 ./io
     11 ./test2.sh
     11 nano
     10 wine
     10 id

---

### Post by gn2 on 2007-11-23
1: sudo aptitude install xubuntu-desktop
2: sudo apt-get install ubuntu-restricted-extras

3-10: There is no 3-10, I'm finished with the terminal after 1 & 2.

---

### Post by seventhc on 2007-11-26
141 sudo
     59 mutt
     22 ls
     21 cd
     10 man
     10 history
     10 echo
     10 cat
      7 ping
      7 chmod

---

### Post by fedex1993 on 2007-11-26
heres my update since last time 
```
    140 sudo
     63 cd
     46 ls
     35 nano
     35 conky
     33 apt-cache
     15 youtube-dl
     10 ./info.sh
      8 scrot

```

---

### Post by blithen on 2007-11-26
108 sudo
     56 cd
     38 python
     34 ls
     30 nano
     20 scons
     20 htop
     19 locate
     15 conky
     13 pi

---

### Post by lubosz on 2007-11-29
user:

     93 sudo              <= lol, i like beeing root
     73 cd
     38 ls
     16 qemu-img
     15 ./GLAnim         <= some opengl bin i made
     13 wget
     12 svn
      9 ps
      9 java
      9 bzr

root:

     17 ls
     16 cd
     10 vditool
      5 rm
      5 export
      5 exit
      4 echo
      3 sudo      <= wtf ^^
      2 chown
      1 vdir


well my historys are too short ^^

---

### Post by fanatik on 2007-11-30
666 ls
    374 cd
    368 sudo
    278 vi
    192 more
    165 ps
    137 aptitude
     69 mv
     60 rm
     51 man

---

### Post by mellowd on 2007-11-30
ls
vim
cat
cd
apt-get
tar
tail
less
rm
sudo

---

### Post by mellowd on 2007-12-01
I've actually just reinstalled Ubuntu server so what I think I use more often is slightly different to what it will be soon. This list will obviously change as I won't be installing so many apps again in one go:

     60 ls
     51 cd
     46 apt-get
     29 vim
     21 find
     18 mysql
     17 rm
     15 rtorrent
     15 cat
     12 htop

---

### Post by Kosimo on 2007-12-01
212 sudo
     45 cd
     40 exit
     14 Creeu-vos
     10 ./configure
      9 uname
      8 make
      6 vncviewer
      5 pidgin
      4 traceroute

---

### Post by Humph on 2007-12-01
82 sudo
     69 make
     68 gedit
     54 cd
     41 ls
     18 ./shellsort
     13 ./progbar
     12 ping
     11 ./scrolly
      8 chmod

---

### Post by toupeiro on 2007-12-01
105 cd
    104 ls
     63 sudo
     34 ps
     29 find
     19 man
     15 kill
     13 vi
      9 wine
      5 winecfg

---

### Post by sajro on 2007-12-01
> 96 sudo
     18 exit
     17 cd
     16 clear
     11 ls
      8 gdebi
      7 nslookup
      6 vim
      6 javac
      5 telnet
There's mine.

---

### Post by rfruth on 2007-12-01
. >  12 cd
      9 ls
      4 sudo
      1 sh
      1 history


---

### Post by schauerlich on 2007-12-01
107 cd
     83 ls
     70 sudo
     20 alias
     19 man
     19 gedit
     12 pi
     10 less
      8 mv
      8 ..

---

### Post by haggus on 2007-12-01
249 sudo
     83 cd
     72 ls
      7 wget
      7 lspci
      6 poweriso
      6 apt-get
      5 dmesg
      4 kdesu
      4 dvdshrink

---

### Post by nat6138 on 2007-12-01
136 sudo
     37 pulseaudio
     33 cd
     29 ./configure
     23 alsamixer
     16 make
     16 cmus
     16 beryl
     16 asoundconf
      8 amarok

Heh.

---

### Post by Scotty Bones on 2007-12-02
5 sudo
      2 qemu
      2 gpg
      2 cd
      1 wget
      1 VBoxManage
      1 mount
      1 lsusb
      1 history
      1 /etc/init.d/mountdevsubfs.sh

wow, pretty weak.

---

### Post by Eric_T on 2007-12-03
100 cd
     88 ls
     38 sudo
     26 xpdf
     19 bg
     14 tar
     12 gvim
     10 mv
     10 locate
      9 ssh

I write a lot of reports in LaTeX, that's why xpdf is so high on the list I guess.

---

### Post by bharadwaj on 2007-12-06
1. sudo 
2. nano
3. cd 
4. ls
5. smb
4. vmware
5. apt-get
6. rar
7. poff
8. pon 
9. gksudo
10. rm -rf

---

### Post by jtuchscherer on 2007-12-07
224 sudo
     50 vim
     41 cd
     19 ls
     13 ps
     12 man
     11 wget
     11 rake
      9 ruby
      7 javac

---

### Post by adamorjames on 2007-12-07
interesting... I don't think it's right but... here it is
     78 cd
     45 ls
     40 gnome-terminal
     21 svn
     18 sudo
     18 make
     13 nethack
     13 man
     12 telnet
     12 rm

EDIT: Hey Xavieran!

---

### Post by Xavieran on 2007-12-07
Intriguing...nethack is one of my most used commands!

    ```
 57 sudo
     51 cd
     43 nethack
     31 python
     22 dir
     20 exit
     15 man
     11 dd
      9 rm
      7 telnet

```

---

### Post by subs on 2007-12-07
here they are..     

> 
     79 cd
     74 ls
     70 sudo
     15 clear
     13 ndiswrapper
     10 wget
     10 iwconfig
      8 dosbox
      7 lspci
      7 dosemu


---

### Post by pmgr33r on 2007-12-13
sudo apt-get install

---

### Post by -grubby on 2007-12-14
```
    105 sudo
     74 espeak
     44 gksudo
     22 apt-cache
     14 exit
     10 fbdesk
      8 thunar
      6 man
      4 xkill
      4 killall

```

---

### Post by aaargh486 on 2007-12-27
```
     
     79 sudo
     38 perl
     20 echo
     16 tail
     16 nc
     15 man
     15 history
     15 gedit
     15 cd
     11 ls

```

I use Perl for piping hexcodes :)

---

### Post by mellowd on 2007-12-27
Now that my server has been running a bit, slightly different:

```
     91 ls
     62 cd
     54 screen
     46 rm
     40 mv
     26 aptitude
     22 vim
      9 locale
      8 moblock-control
      7 mkdir
```

---

### Post by verb3k on 2007-12-27
Nice topic :)

Here's mine:

```

     77 ls
     74 sudo
     71 cd
     33 less
     27 apt-cache
     19 clear
     10 man
     10 locate
      8 python
      8 gedit

```

---

### Post by daou on 2007-12-27
```
     99 ls
     99 cd
     54 sudo
     34 whois
     19 make
     15 svn
     13 ps
     11 ./configure
      9 apt-cache
      8 aptitude

```a lot of software development

---

### Post by new2*buntu on 2007-12-27
11 exit
      8 su
      7 apt-get
      4 cd
      2 ls
      2 history
      2 echo
      2 aptitude
      1 synaptic
      1 killall
In Debian, which I just installed a few hours ago. I will post soon with my Linux Mint history (which I also re-installed several hours ago.)

---

### Post by cwej on 2007-12-29
12 top
     10 man
      9 sudo
      9 netstat
      6 ls
      4 cd
      2 octave
      2 iwconfig
      1 wget
      1 q

---

### Post by Martje_001 on 2007-12-29
```
martijn@gutsy:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    143 sudo
     50 cd
     41 ssh
     41 ls
     24 tar
     19 wget
     11 wakeonlan
     11 make
     10 echo
     10 bash

```

---

### Post by sgartner on 2007-12-29
66 sudo
     61 ls
     30 exit
     14 cd
     13 clear
     11 mtasc
      7 vncviewer
      7 eclipse
      6 pwd
      6 ftp

---

### Post by tbrminsanity on 2007-12-31
70 sudo
     67 cd
     64 ls
     18 exit
     13 man
      5 rm
      4 cat
      3 ll
      3 dpkg-deb
      3 chmod

What a boring list.

---

### Post by Martin Witte on 2007-12-31
martin@toshibap200:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     56 sudo
     43 ls
     23 g++
     17 cat
     17 ./a.out
     16 cd
     15 find
      9 rm
      9 lspci
      6 ./test.sh

---

### Post by Tux.Ice on 2007-12-31
sudo
apt-get
su
nmap
qtparted
make
install
./configure

---

### Post by Sam on 2007-12-31
```
$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     66 ls
     64 cd
     49 vi
     45 sudo
     14 man
     14 aptitude
     12 ll
     11 killall
     10 top
      9 ssh
```

---

### Post by songo on 2007-12-31
work/home laptop

history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     69 ping
     43 telnet
     42 sudo
     27 ll
     19 ps
     19 cd
     17 ssh
     16 gnome-wm
     14 ifconfig
     13 l

 history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
     63 ping
     39 sudo
     26 telnet
     22 ll
     18 ps
     18 cd
     16 gnome-wm
     13 l
     12 ifconfig
     11 man

l=ls -CF

---

### Post by Mateo on 2007-12-31
anyone care to explain how that command works?

history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr

that's beyond my level of comprehension at the moment...

---

### Post by dlegend on 2007-12-31
1. sudo
2. gedit
3. apt-get
4. cd
5. ls
6. make
7. install
8. ./configure
9. top/htop
10. history | grep

---

### Post by dimbulb1024 on 2007-12-31
195 cd
    107 java
     99 sudo
      5 smartctl
      5 cp
      3 sh
      3 exit
      2 apt-get
      1 top
      1 time

---

### Post by mr.propre on 2007-12-31
50 sudo
     49 exit
     25 ping
     16 smbclient
     12 whois
     12 cd
     11 ssh
      9 ftp
      8 telnet
      8 talk

---

### Post by sloggerkhan on 2007-12-31
123 sudo
30 cd
19 gksudo
16 ls
15 man
11 glxinfo (usually piped | grep, I'd have thought.)
10 svn
10 glxgears
10 ./autogen.sh
7 gedit

not what I expected...
I thought cp would be up there for sure....

---

### Post by cartisdm on 2007-12-31
48 sudo
     31 exit
     16 gedit
     10 mkdir
     10 ./configure
     10 cd
      9 wine
      6 ls
      5 make
      4 xset

I really don't use it much....

---

### Post by -grubby on 2007-12-31
77 sudo
     54 exit
     32 apt-cache
     26 fbsetbg
     23 killall
     19 uptime
     18 gpe-screenshot
     17 xterm
     16 cd
     14 gksudo

---

### Post by kellemes on 2007-12-31
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
50 sudo
44 ls
39 vim
28 fbsetbg
22 locate
17 startx
14 cd
6 cp
4 su
3 thunar

fbsetbg? I've been struggling to get a background in fluxbox te last hour or so.. :popcorn:

---

### Post by -grubby on 2007-12-31
> **kellemes said:**
> history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
50 sudo
44 ls
39 vim
28 fbsetbg
22 locate
17 startx
14 cd
6 cp
4 su
3 thunar

fbsetbg? I've been struggling to get a background in fluxbox te last hour or so.. :popcorn:
yep, and it works in openbox too

---

### Post by p_quarles on 2007-12-31
103 ls
     50 cat
     49 cd
     40 man
     38 sudo
     35 apt-cache
     19 apropos
     15 vim
     12 ssh-huxley
     11 killall

See if you can spot the alias. ;)

---

### Post by new2*buntu on 2007-12-31
Anyway, here is mine (I have only had Debian installed for a day)
Regular user:
      8 su
      7 exit
      3 cd
      2 python
      2 ls
      2 history
      1 apt-get [moo]

And super user:
      23 apt-get
      7 cd
      6 exit
      5 ls
      4 nautilus
      4 dpkg
      2 synaptic
      2 gedit
      1 synaptix :lolflag: Typo.
      1 rmdir

I exit a lot :lolflag:

---

### Post by kellemes on 2007-12-31
> **new2*buntu said:**
> 
1 synaptix :lolflag: Typo.


If this happens more often you may consider creating an alias of it. :popcorn:

---

### Post by picpak on 2007-12-31
```
     48 lame
     39 sudo
     39 cd
     36 ls
     27 apt
     25 play
     22 text2wave
     22 del
     19 nano
     17 suedit
```

suedit, apt and del being custom aliases.

---

### Post by tekknokrat on 2008-01-05
174 sudo
     73 ssh
     28 ls
     23 ncmpc
     21 xrandr
     21 ping
     17 mpc
     14 man
     11 unzip
     10 DISPLAY=:0

Yes, obviously i have x11 problems and listen a lot to music :guitar:

---

### Post by Kimm on 2008-01-05
148 sudo
     55 cd
     36 ps
     30 killall
     23 wine
     20 JKA
     10 top
      9 winecfg
      9 kill
      9 ./configure

---

### Post by ST.x on 2008-01-05
```

&#9484;-(0112:Sun,06 Jan 08.seynthantx@stx-lappy)&#9472;&#9472;&#9472;&#9472;&#9472;(/home/seynthantx)&#9472;&#9472;
&#9492;&#9472;($)&#9472;> history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'rt|uniq -c | sort -n | tail | sort -nr
    342 cd
    104 gcc
     80 sudo
     71 ls
     46 killall
     44 make
     39 time
     33 ./DLL
     22 ./lab3
     20 ./arr

```

---

### Post by Sukarn on 2008-01-05
For me:
```
115 sudo
70 cd
45 ls
29 screen
23 rtorrent
16 rm
16 cp
16 aptitude
11 wget
10 killall
```


For root:
```

6 python
5 ls
3 rm
3 cd
2 trickle
2 su
2 sh
2 aptitude
1 winecfg
1 wget

```
I wonder why su has been used twice as root, exactly the same thing as someone said on the first page.

---

### Post by bravemosquito on 2008-01-12
**> history: not found**

:confused:

nevermind...

67 aptitude
44 exit
38 nano
32 ping
27 pico
22 cd
21 wine
19 /etc/init.d/networking
18 arp
16 man

---

### Post by Praadur on 2008-01-12
On first tread into this intrepid inquisition, I find that my history shows that I'm an overly obsessive neatfreak.  I can but shake my head and sigh exasperatedly at myself.

I will not reveal the numbers as that would simply be too much...

[LIST]
[*]ls
[*]sudo
[*]cd
[*]exit
[*]rm
[*]nano
[*]clear
[*]deborphan
[*]apt-cache
[*]top
[/LIST]

---

### Post by Reforced on 2008-01-12
40 sudo
     23 cd
      7 apt-get
      6 wget
      6 chmod
      5 ./steam
      4 su
      4 mkdir
      3 ./unrar
      3 java

I just started using Ubuntu today, was trying to install Java, and setting up a Counter-Strike source dedi server.

---

### Post by Rytron on 2008-03-13
111 sudo
80 cd
25 frotz
18 ls
14 ./configure
12 convert
10 su
10 make
9 pwd
7 ccd2iso

---

### Post by cartisdm on 2008-03-13
128 sudo
     35 cd
     24 exit
     16 firefox
     11 less
     11 evolution
     10 ls
     10 gedit
      9 python
      9 nautilus

---

### Post by legolas_w on 2008-03-13
```

 161 sudo
     60 cd
     29 exit
     23 ping
     17 kill
     16 ls
     14 ps
     10 slurm
      9 ant
      6 unrar


```

and
```

 134 sudo
     50 cd
     27 exit
     17 kill
     13 ps
     13 ls
     10 slurm
      9 ant
      8 ping
      6 unrar


```

---

### Post by John T. Monkey on 2008-03-13
76 cd
     75 ls
     59 exit
     47 mkdir
     45 top
     31 sudo
     23 mv
     16 pwd
     14 nano
     13 man

---

### Post by danbuter on 2008-03-13
aptitude install
aptitude update
ls
pwd
chmod 0700 /home/username

"it's a brand new install, if you can't tell.

---

### Post by Dr Small on 2008-03-13
```

     54 ssh
     53 netload
     30 exit
     28 sudo
     24 echo
     20 netloadall
     19 man
     17 reset
     16 cd
     16 cat

```

---

### Post by herbster on 2008-03-14
```
     93 ls
     81 sudo
     45 cd
     16 clr
     14 pac
     12 screen
     11 nvidia-settings
      9 df
      8 rm
      8 fstab
```

---

### Post by mssever on 2008-03-14
As you can see, I use the CLI extensively. I don't see how anyone can be productive without it. :)

On my laptop: ```
     59 cd
     54 ls
     34 ll
     25 fg
     24 feh
     23 less
     22 cd..
     21 rm
     16 sudo
     15 du
``` This list is somewhat atypical, as feh shouldn't normally be there, and p should. ll and p are aliases and/or programs I wrote.

On my desktop: ```
     47 fg
     43 cd
     41 ll
     39 vi
     38 rm
     31 exit
     29 falcon-update
     22 ls
     20 less
     17 p
``` This is probably representative for my desktop.

---

### Post by Mustard on 2008-03-14
97 sudo
     58 ls
     51 cd
     46 man
     26 ps
     22 apg
     21 cat
     13 make
     12 wine
     10 screenlets-manager

---

### Post by Trail on 2008-03-14
104 man
     48 sudo
     46 cd
     41 nc (netcat)
     25 ls
     19 valgrind
     19 ./udptest
     19 ps
     15 k (alias for kate)
     14 agu (alias for sudo apt-get update)

---

### Post by Gigamo on 2008-03-14
On a five day old install

```
[~]: history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    282 exit
    264 cd
    189 vim
    150 sudo
     43 killamazing
     29 rm
     25 cp
     24 c
     23 mv
     22 mkdir

```

I use the terminal alot. :<

---

### Post by Crushyerbones on 2008-03-19
```

     93 sudo
     80 gcc
     49 cd
     46 ./factoria.out
     43 man
     29 ./geany_run_script.sh
     25 gdb
     23 ./factorial.out
      8 clear
      7 make

```

Guess what I've been doing :P

---

### Post by holihue on 2008-03-27
Here is my output:


     82 xplanet
     65 sudo
     44 python
     31 make
     30 xbacklight
     22 sftp
     15 ./configure
     13 dbench
     12 gedit
     11 ls

---

### Post by 00arthuryu on 2008-03-27
76 ls
     70 sudo
     70 ssh
     49 cd
     47 ifconfig
     21 ping
     14 vncviewer
     11 mplayer
      9 iwconfig
      8 man

---

### Post by -grubby on 2008-03-27
Well I've only had this install for about 2 weeks or so (I think, I'm not absolutely sure), so here goes:
```

nathan@linda:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     66 pi
     40 sudo
     39 killall
     36 install
     19 php
     18 firefox
     17 cd
     16 dir
     12 root
      9 uptime

```

Also, it should be notes that i use several aliases

---

### Post by Joeb454 on 2008-03-27
Apparently mine are:

```
84 sudo
     30 clear
     22 cd
     20 make
     19 ./configure
     15 ssh
     14 ls
      7 rm
      7 mv
      6 killall
```

I do a lot of work over ssh / sftp :)

---

### Post by p_quarles on 2008-03-27
Currently:
```
     97 ls
     55 cd
     53 sudo
     23 vim
     23 fbsetbg
     23 du
     19 man
     18 killall
     17 mv
     16 less
```

---

### Post by hhhhhx on 2008-03-27
```
     59 sudo
     49 cd
     19 python
     17 ./super_pi
     12 print
     12 ./pixelmachine
     11 ls
     10 espeak
      9 thoggen
      9 man

```

---

### Post by peeple on 2008-04-12
```
~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    202 sudo
     34 exit
     32 iwconfig
     29 wlanconfig
     16 apt-get
     11 wget
      9 nautilus
      8 telnet
      8 su
      7 wine

```
```
~$ history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
    179 sudo
     32 iwconfig
     29 wlanconfig
     29 exit
     16 apt-get
      9 su
      9 nautilus
      8 telnet
      7 airmon-ng
      6 wget

```

neat

---

### Post by baumgc on 2008-04-12
```
Last login: Sat Apr 12 15:03:32 on ttys000
24-159-209-137:~ baumgc$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
 128 /Users/baumgc/Documents/College\
   5 killall
   4 ssh
   4 /Users/baumgc/test/build/Release/test
   3 sudo
   2 emacs
   2 defaults
   1 xdoctor
   1 sudo\
   1 ping
24-159-209-137:~ baumgc$ 
```

There you go....,
Obviously, I don't use my terminal much...

---

### Post by Breakage on 2008-04-12
mine, couple of alias' there.
>     253 pacman
    106 yogurt
     98 exit
     87 gksudo
     70 scrot
     66 startx
     40 f***off
     38 grep
     25 ncmpc
     17 rm

---

### Post by cardinals_fan on 2008-04-12
Kind of embarrassing...

     98 exit
     73 su
     27 killall
     22 dmenu
     20 clear
     18 xdotool
     17 xfrun4
     14 make
     13 pypanel
     12 medit

---

### Post by p_quarles on 2008-04-12
Current stats on my laptop. As me:
```
     96 ls
     86 sudo
     72 cd
     20 rm
     18 man
     15 vim
     14 startx
     14 mv
     13 gpg
     13 df
```
As root:
```
     22 ls
     16 cd
      8 mv
      8 apt-get
      5 exit
      4 make
      3 iwlist
      3 ifconfig
      3 dpkg
      3 checkinstall
```

---

### Post by klange on 2008-04-12
127 cd
     74 ls
     47 sudo
     38 killall
     28 wine
     19 compiz-send-event
     18 make
     11 smbget
     11 nautilus
     11 compiz-manager
Interesting...

---

### Post by days_of_ruin on 2008-04-12
101 vim
     61 ls
     60 cd
     30 wget
     29 rm
     20 exit
     19 python
     12 top
     11 mkfs
      7 eject

How long is the history?

---

### Post by DMcA on 2008-04-12
66 vi
     64 sudo
     44 fdupes
     39 mpc
     32 ls
     32 gcc
     29 man
     22 cd
     20 ncmpc
     18 ping

a bit flattering I think

---

### Post by bjschuma on 2008-04-12
107 g++
    104 ./a.out
     49 sudo
     49 cd
     47 sh
     43 ./battleship
     29 ls
     17 reset
     11 vlc
      7 rm

I'm not really surprised at the first 2.  I did expect ls to be higher.

---

### Post by tamoneya on 2008-04-12
```
tamoneya@ubuntu0:~$ history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
    226 sudo
     35 ls
     30 cd
     13 rm
      8 nano
      7 cat
      5 nmap
      4 who
      4 history
      3 make

```
The large number of sudo commands come from my compulsive updating of hardy :)

---

### Post by macogw on 2008-04-13
> **macogw said:**
> 102 sudo
    102 ls
     98 cd
     42 apt-cache
     26 vi
     11 man
     11 915resolution
     10 ps
      7 ssh
      6 cat

10 months later...

    102 ls
     92 cd
     54 vim
     46 sudo
     31 ./configure
     30 grep
     13 make
      9 rm
      9 mv
      7 cp

Yesterday I was doing a lot of opening up C files with vim, poking at them, and compiling them over and over to try to make a program work properly.

---

### Post by robertchahine on 2008-04-13
64 sudo
     63 cd
     13 ls
     11 exit
      9 cp
      7 VBoxManage
      7 tar
      7 gksudo
      6 locate
      5 python

---

### Post by matt79 on 2008-04-13
148 sudo
    132 ls
     92 cd
     17 exit
      9 cat
      8 cp
      7 mv
      6 history
      6 apt-get
      5 rm


btw does anyone know how to increase the amount of history that is stored? Mine is set to 500 but I would like it to be atleast 1000

---

### Post by diplomat.x on 2008-04-16
```

130 sudo
     46 cd
     34 sox
     33 wvdial
     28 ls
     16 scrot
     13 alsamixer
      9 tar
      7 wget
      7 make

```

---

### Post by sujoy on 2008-04-16
108 clear
     52 gcc
     49 vi
     40 ./tutorial
     25 ping
     25 ls
     21 cd
     11 pon
     10 ncmpc
      9 plog


well that tutorial is a project i have been working on ...

---

### Post by kutjara on 2008-04-16
145 sudo
     46 cd
     40 ls
      8 fdisk
      7 top
      7 compiz.real
      7 chmod
      6 compiz
      5 wget
      5 metacity

---

### Post by Gen2ly on 2008-04-16
just about expected this:

     74 ls
     72 cd
     64 sudo
     23 vim
     18 df
     17 eix
     14 e
     13 ll
     12 gentoo-update
     12 cdb

I'm doing a super super update in Gentoo (fifth day now) so most of these are for that.  e=emerge, ll=ls -l, cdb=cd ~/.bin.

---

### Post by Lostincyberspace on 2008-04-17
Here is mine using both of the different commands

```

lee@lee-minttop:~/Projects$ history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
     58 sudo
     29 cd
     22 ls
     14 python
      5 wget
      5 chmod
      4 java
      3 var.py
      3 svn
      3 ftp
lee@lee-minttop:~/Projects$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    114 sudo
     33 cd
     29 ls
     15 python
     10 wget
      5 chmod
      4 tar
      4 java
      4 ./configure
      4 calc


```

---

### Post by Xbehave on 2008-04-17
190 sudo............< well duh, if in using the terminal im doing something iportant
     55 ls..................<got to find out what im looking for 
     28 cd.................<got to get to where im going
     17 aticonfig
     13 googleearth .<shame it doesnt work
     10 wget............ <ahh the beauty of using a http server over a lan to tranfere files
     10 smssend 
     10 gnokii
      8 kmobiletools
      8 fglrxinfo.........<finally got that compiz working :S or did i :confused:

this is only on the last few commands obviously, how far does history go back?

---

### Post by Kingsley on 2008-04-17
216 yum
     87 /etc/init.d/mt-daapd
     50 cd
     46 ls
     41 service
     41 ifconfig
     32 ./configure
     30 make
     26 gedit
     26 cat

---

### Post by original_jamingrit on 2008-04-17
Cool.  Mine in my user account:

>      93 cd
     92 ls
     51 vim
     28 sudo
     24 su
     24 man
     20 xpdf
     13 firefox
     10 xine
     10 cp

And as root:

>      95 cd
     71 ls
     38 vim
     21 shutdown
     18 mount
     18 exit
     17 make
     17 installpkg
     16 killall
     13 man

---

### Post by ntowakbh on 2008-04-17
85 ls
     81 cd
     62 sudo
     16 firefox
     15 man
     15 apt-cache
     10 mv
      7 rm
      7 gpg
      7 alsamixer

---

### Post by james9876 on 2008-04-22
132 sudo
     46 dir
     21 cd
     17 make
     17 gedit
     16 dd
     12 ./configure
     10 conky
      8 dpkg
      7 ffmpeg

---

### Post by chucky chuckaluck on 2008-05-04
since switching to arch a week ago...

_user_
  151 cd
     80 nano
     62 elinks
     60 streamripper
     55 ls
     44 htop
     41 mplayer
     29 feh
     24 startx
     24 mc


_root_
   435 pacman
    102 nano
     45 cd
     32 reboot
     25 ls
     12 locate
     11 rm
     10 mplayer
      8 exit
      7 mv

---

### Post by Cresho on 2008-05-04
175 sudo
     26 cd
     22 modprobe
     20 ls
      9 ./configure
      8 make
      8 amarok_libvisual
      7 sh
      7 lsmod
      7 fdisk

Funny how sudo make install isn't in here.

---

### Post by klange on 2008-05-04
```
    102 cd
     95 ls
     55 sudo
     28 compiz-send-event
     17 /opt/xorg/bin/startX
     17 ./jasper
     15 xwininfo
     10 echo
     10 bash
      9 history

```
Interesting...
This fad needs to die.

---

### Post by cardinals_fan on 2008-05-04
On a relatively new installation:```
     57 vim
     54 exit
     52 su
     49 cd
     23 clear
     19 scores
     13 toast
     13 cat
     12 mutt
     12 fetchmail
```

---

### Post by Bruno Barrera on 2008-05-04
109 cd
     82 ls
     56 sudo
     22 man
     15 patch
     14 debuild
     14 debdiff
     12 dch
     11 make
     10 find

---

### Post by ghindo on 2008-05-05
```
 history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     78 sudo
     57 man
     45 update
     24 clean
     24 cd
     23 top
     20 killall
     17 alsamixer
     15 gedit
     12 ping

```My alias for update is```
sudo apt-get update && sudo apt-get upgrade
```and my alias for clean is```
sudo apt-get autoclean && sudo apt-get autoremove && sudo deborphan -Z && sudo apt-get clean
```

Great thread.  I'm learning a lot from these terminal commands! :)

---

### Post by retrow on 2008-05-05
I run
```
history -c
```
...before I exit terminal. Right now if I check the usage, I have less than 10 commands listed in there.

---

### Post by spec-chum on 2008-05-05
Mine are:
     85 ls
     74 cd
     35 exit
     25 sudo
     14 vi
     14 man
      9 type
      9 locate
      9 clear
      8 ps

---

### Post by Koori23 on 2008-05-05
29 htop
     14 sudo
     **10 install**
      8 links2
      **5 upgrade**
      5 ll
      **4 remove**
      4 ls
      3 youtube-dl
      3 xterm

The three in bold are my aliases for aptitude

---

### Post by bwhite82 on 2008-05-05
171 sudo
     93 python
     76 nano
     20 cd
     19 gedit
     14 ls
     13 weather
     12 rm
     12 emerald
     11 man

---

### Post by lesergi on 2008-05-05
114 sudo
     31 cd
     28 apt-get
     25 ls
     17 wlanconfig
     12 ifconfig
     11 modprobe
     11 cat
     11 apt-cache
     10 rmmod

---

### Post by diodoros on 2008-05-05
118 make
80 fg
32 ls
20 cd
13 tar
10 rm
 6 mv
 4 emacs
 3 sudo
 3 scp

---

### Post by snap on 2008-05-07
117 ls
     86 sudo
     54 cat
     42 cd
     17 cls
     13 killall
     13 exit
     10 conky
      9 most
      7 man

---

### Post by ghindo on 2008-05-14
```
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     69 nautilus
     64 sudo
     57 man
     32 clear
     28 update
     21 htop
     19 exit
     19 clean
     11 gedit
     10 thunar
```

---

### Post by Oldsoldier2003 on 2008-06-11
102 bzr
     80 sudo
     51 ls
     33 cd
     19 man
     17 truecrypt
     15 cat
     11 yelp
     11 apt-cache
     10 ./validate.sh

---

### Post by -grubby on 2008-06-11
128 python
     44 install
     33 sudo
     21 killall
     19 remove
     17 cd
     16 search
     15 dir
     12 echo
      9 top

---

### Post by Joeb454 on 2008-06-11
I'm going to repost mine, because I just got an alias working for it :)
```
:~$ top10
     46 clear
     39 ls
     33 vim
     30 g++
     29 sudo
     25 (conky &)
     19 cd
     18 q2
     16 ssh
     13 man
```

---

### Post by nick09 on 2008-06-11
```
     11 sudo
      6 $
      5 wget
      4 frostwire
      3 wine
      3 cd
      3 -c
      2 xsensors
      2 soundkonverter
      2 /etc/sensors.conf
```

Not much at all.

---

### Post by ghindo on 2008-06-11
Good to see this thread up and running again```
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     74 sudo
     57 ssh
     39 cd
     26 man
     24 mv
     23 nautilus
     17 ls
     15 htop
      9 rm
      8 ffmpeg
```

---

### Post by elashish on 2008-06-11
125 ls
     74 sudo
     38 exit
     35 apt-cache
     32 cat
     31 cd
     14 man
     11 xmodmap
      9 find
      8 chmod

as root:
     39 apt-get
     11 nano
      4 gedit
      3 touch
      3 find
      2 shutdown
      2 rm
      2 mv
      2 mount
      2 aptitude

I clearly need to use the terminal more :(

---

### Post by Nikayah on 2008-06-16
60 sudo
     45 cd
     24 make
     20 ./configure
     10 wget
     10 tar
      7 ping
      7 gksudo
      6 wminput
      6 blender

---

### Post by jakupl on 2008-06-16
Here is mine :)     


     158 sudo
     74 ps
     45 pkill
     24 cd
     20 ls 
     19 htop
     16 man
     14 finger
     13 gksudo
     10 conky

---

### Post by ForksHolder on 2008-06-16
Lol, Cool one.

    217 sudo
     91 cd
     19 ls
     17 ping
     10 make
     10 ln
      8 dpkg
      7 wine
      7 gedit
      6 wget

---

### Post by NovaAesa on 2008-06-16
```

    221 javac
    127 java
     68 cd
     33 ls
     10 clear
      6 mocp
      5 python
      3 whatis
      3 sudo
      3 rm

```
As you can see, I've been dabbling in Java alot lately :P

---

### Post by billgoldberg on 2008-06-16
I don't use the terminal that often, but if I use it, most of the time I use these commands.

1. sudo nautilus
2. sudo apt-get install xxx
3. sudo apt-get update
4. pkill xxx
5. killall xxx
6. sudo gedit xxx
7. cd
8. ls
9. cp
10. sudo apt-get autoremove --purge xxx

---

### Post by RiceMonster on 2008-06-16
115 exit
     60 sudo
     55 vim
     50 ls
     42 cd
     20 man
     12 killall
     11 tile
     11 ./configure
      7 acpi

---

### Post by cmay on 2008-06-16
> sudo 
apt-get install 
apt-get remove
nano
pwd
cd
rm
gcc -o hello./hello.c
w
who
whoami
whatis
i use these all the time but this
```
why! why! why! 
```
doesent seem to work :)

---

### Post by Kevbert on 2008-06-16
91 cd
83 ls
45 sudo
17 man
14 exit
12 gedit
10 lspci
9 free
9 doom3
8 mkdir

---

### Post by AIRAVO on 2008-06-16
hmm

---

### Post by Trail on 2008-06-17
61 netcat
     48 ls
     48 cd
     10 sudo
     10 man
     10 make
      9 ssh
      7 ./udptest
      7 g++
      6 tar

---

### Post by csc2ya on 2008-07-21
117 exit
     61 ssh
     55 sudo
     43 uptime
     40 ping
     15 top
     15 cd
     12 dir
     10 crontab
      8 aptitude

---

### Post by cdtech on 2008-07-21
119 ls
104 sudo
 54 cd
 36 pico
 23 ./Classify
 18 la
 14 cat
 13 install
 12 update
  7 ./cleandownloads

---

### Post by chickpea on 2008-07-22
148 ls
139 cd
 36 feh
 19 rename
 16 clear
 15 sftp
 14 mv
 10 file
  9 sudo
  9 rm

i migrated to linux 3 months ago just because i desperately wanted to stay away from windows. though it was not for a positive reason, now i become a linux fan. in contrast to windows, linux treats me as a person who has his own feelings and thoughts. and i've found CLI is the smartest way to do stuff on my computer. it's simple and powerful!

---

### Post by arsenic23 on 2008-07-22
The best thing about participating in this thread is not only seeing how other people use their terminal, but also watching my own habits change.

87 ls
46 cd
34 ffmpeg
32 rename
23 cl - *alias for 'clear&&ls'*
22 sshcl - *log into my media center*
20 sudo
15 mv
14 cat
13 python

---

### Post by Canis familiaris on 2008-07-22
ls
cd 
cat
less
mv
cp
rm
ln
sudo
mkdir

---

### Post by ghindo on 2008-07-22
```
michael@ubuntu:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    102 ssh
     95 mv
     50 scp
     44 cd
     43 sudo
     30 ls
     20 man
     14 htop
     12 nautilus
      9 rsync
```**Edit:**  Also, here's the list for my server:```
michael@michael-server:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    166 screen
     96 logout
     63 htop
     43 sudo
     21 man
     17 ./update.sh
     14 eject;
     12 nano
     10 ls
      7 cd
```

---

### Post by RATM_Owns on 2008-07-22
38 sudo
     26 nautilus
     26 cd
     22 mv
     19 echo
     18 saga (My alias for sudo aptitude update && sudo aptitude safe-upgrade)
     18 gedit
     15 gbrc (My alias for gedit ~/.bashrc && source ~/.bashrc)
     13 gksudo
     12 rm

---

### Post by wrtpeeps on 2008-07-22
144 sudo
     45 cd
     35 ls
     22 javac
     19 java
     14 killall
     14 dpkg
     13 nano
     13 devilspie
     12 fglrxinfo

:lolflag:

---

### Post by scragar on 2008-07-22
```
     52 cat
     43 grep
     38 ps
     27 locate
     19 ls
     16 cd
     14 sudo
     12 apt-cache
     11 apt-get
     10 pkill
```

I find it slightly disturbing that I use apt-cache more than apt-get...

---

### Post by collinp on 2008-07-23
I am sure that most of you use at least one command in a day inside terminal, I use terminal alot. I find it easier to use terminal than gui in some situations, but that is not the point. What commands does the community here use at least once a day?

---

### Post by Masoris on 2008-07-23
sudo

---

### Post by ghindo on 2008-07-23
See:

[http://ubuntuforums.org/showthread.php?t=472090](http://ubuntuforums.org/showthread.php?t=472090)

It's a pretty good thread on commonly used terminal commands :)

---

### Post by Bachstelze on 2008-07-23
> **ghindo said:**
> See:

[http://ubuntuforums.org/showthread.php?t=472090](http://ubuntuforums.org/showthread.php?t=472090)

It's a pretty good thread on commonly used terminal commands :)

Indeed. Threads merged.

---

### Post by ad_267 on 2008-07-23
59 cd
     53 sudo
     51 ls
     40 exit
     34 Linus
     17 apt-cache
     16 man
      9 file
      8 vim
      7 ./test

That "Linus" is there because I was trying to paste this: [http://www.linuxscrew.com/2007/10/28/fun-chuck-norris-vs-linus-torvalds/](http://www.linuxscrew.com/2007/10/28/fun-chuck-norris-vs-linus-torvalds/) into a file from the terminal and did something wrong.

---

### Post by wenuswilson on 2008-07-23
159 sudo
     22 cd
     18 xcalib  [xcalib -i -alter] very fun
     12 wine
      7 gksudo
      6 wget
      6 sh
      6 compiz
      5 tar
      5 mv

---

### Post by chucky chuckaluck on 2008-07-23
_user_

    186 sudo
    128 su
    104 nano
     68 feh
     60 cd
     50 cplay
     33 streamripper
     32 startx
     31 htop
     22 scrot


_root_


    192 pacman
     42 nano
     41 yaourt
     23 cd
     22 gpasswd
     21 echo
     15 thunar
     11 ls


i think this is the first time i've seen scrot hit the top ten. i thought it would be first by now. odd...

---

### Post by drewster1829 on 2008-08-02
139 sudo
     88 cd
     75 ls
     37 ssh
     34 cat
     21 sshfs
      8 exit
      7 ping
      7 man
      7 iptables

Many of the cds and cats (kitties? :)) are for checking my mprime status, since it runs as a daemon and ports the output to mprime.log. And many of the sshs are checking the status of mprime on my other system (because I'm too lazy to walk 5 feet).

---

### Post by markp1989 on 2008-08-02
mark@markspc:~$ history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr
    113 sudo
     47 ps
     44 conky
     27 cd
     22 ls
     14 scrot
     13 avant-window-navigator
     11 mousepad
      7 top
      7 rm
mark@markspc:~$

---

### Post by billgoldberg on 2008-08-02
183 mpc
115 sudo
37 mpd
24 killall
18 man
13 pkill
9 mount
8 cd
7 sonata
7 sleep

---

### Post by ion072002 on 2008-08-02
sudo apt-get install/autoremove
ls -a
rm
cd

---

### Post by billgoldberg on 2008-08-02
I just posted the one from my desktop, now the one from my laptop.

```
142 sudo
30 cd
16 ssh
16 mpc
16 gpg
15 mpd
9 ./configure
8 wget
8 totem
8 pkill
```

---

### Post by scragar on 2008-08-02
> **billgoldberg said:**
> I just posted the one from my desktop, now the one from my laptop.

```
142 sudo
30 cd
16 ssh
16 mpc
16 gpg
15 mpd
9 ./configure
8 wget
8 totem
8 pkill
```

w0w, someone else who uses pkill... most people go right for killall or xkill... Shame really, pkill is such a great alternative, more so thanks to the regexp capacity, as long as you don't coincidently have it kill itself when it runs(easier than you think using -n to kill newest process matching a pattern it does) :P

---

### Post by Der Alte on 2008-08-02
264 sudo
     147 cd
     98 ls
     63 chmod
     42 pon
     17 glxgears
     14 atc
      9 killall
      5 poff
      4 cat

From a somewhat fresh install on my laptop (1 week)

---

### Post by jerome1232 on 2008-08-02
```
132 sudo
48 ssh
42 ls
38 mail
37 cd
17 man
17 make
14 cat
13 tar
13 ./configure
```

for some reason system mail wasn't working so I was doing alot of testing on it. 

(now cron is annoying me about some cron job...)

---

### Post by tom66 on 2008-08-02
81 sudo
     57 cd
     28 ls
     28 ffmpeg
     20 watch
     19 wine
     16 flite
     16 espeak
     12 killall
      9 wget

---

### Post by munkyeetr on 2008-08-02
My account: My history gets flushed down the /dev/null memory hole. Umm, but probably:

ls -la
cd
mount
umount
sudo
gksudo
init 6
ps x
startx


My root account:

71 bash
62 rm
60 nautilus
53 sh
52 ls
23 exit
22 cd
20 mount
12 echo
8 mv

---

### Post by sisco311 on 2008-08-02
74 sed
     57 ls
     55 sudo
     47 cat
     33 cd
     28 tv
     23 time
     20 man
     18 nano
     17 mplayer

cat ~/bin/tv
> mplayer tv://$1 -hardframedrop -double -dr \
-ac hwac3,a52, -afm ffmpeg \
-vc ffmpeg12,mpeg12, -vfm ffmpeg,dshow,vfw \
-vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all \
-nocache \
-tv driver=v4l2:\
device=/dev/video0:width=320:height=240:\
input=0:fps=24:\
chanlist=europe-east:alsa:adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:\
immediatemode=0:norm=PAL:\
channels=27-tv2,\
SR1-rtl_klub,\
29-m1,\
R7-m2,\
SR5-duna,\
21-minimax_hu,\
SR17-animax_ro,\
R11-cartoon_network,\
34-jetix,\
R12-tvr1,\
SE3-tvr?,\
SR2-tvr_cultural,\
R9-pro_tv,\
R6-acasa,\
R8-antena1,\
25-antena2,\
23-antena3,\
SR3-prima_tv,\
SR4-discovery_channel,\
SR6-SR6,\
SR7-focus_tv,\
SR8-animal_planet,\
SR12-pro_cinema,\
SR13-kiss_tv,\
SR14-hallmark,\
SR15-b1,\
SR16-rai_uno,\
SR18-sport_ro,\
S21-sport_klub,\
S23-gsp_tv,\
S24-S24,\
S25-national_tv,\
S35-n24,\
S36-euro_sport,\
S38-kanal_d,\
22-pro7,\
30-otv,\
31-u,\
32-mtv,\
35-romantica,\
36-axn,\
39-tv5,\


---

### Post by Linuturk on 2008-08-02
102 ls
     78 sudo
     41 mv
     40 unison
     31 cd
     30 exit
     29 ssh
     24 nano
     22 rm
      6 scp

apparently, I like to know where I am (ie the ls)

---

### Post by cherva on 2008-08-02
90 cd
     63 sudo
     44 ls
     29 debuild
     20 gpg
     15 wineboot
     14 cat
     12 htop
     11 echo
     10 dh_make

---

### Post by MatthewPlanchard on 2008-08-08
181 sudo
     49 inst
     30 ./temp
     17 cd
     16 ls
     12 ./tempconverter
     11 temp
     11 man
     10 uninst
     10 ex

inst = sudo apt-get install
./temp, ./tempconverter, and temp are from writing a Fahrenheit to Celsius conversion script
uninst = sudo apt-get uninstall

I'm a little surprised that ex is on there.

---

### Post by SilverDragon on 2008-08-08
116 sudo
     77 cd
     37 java
     20 g++
     18 wget
     18 patch
     18 firefox
     10 make
     10 gksu
      8 ./test

Trying to learn C++ but failing miserably. Oh well, I'll try again soon.

---

### Post by brunovecchi on 2008-08-08
```
    
    112 ls
     98 cd
     33 cat
     28 rm
     20 sudo
     19 mv
     16 mkdir
     14 clear
     11 crontab
      8 touch

```

---

### Post by kitili on 2008-08-08
```
    147 sudo
     46 python
     35 yaourt
     28 cd
     26 gftp
     25 killall
     21 pacman
     19 ssh
     19 k3b
     18 gedit

```

---

### Post by Kingsley on 2008-08-09
As root:
```
    160 yum
     77 cd
     67 nano
     61 ls
     44 service
     34 rpm
     30 shutdown
     24 rm
     22 tar
     22 exit

```


As normal user:
```
    200 sudo
     97 cd
     75 ls
     73 yum
     48 su
     26 top
     25 wget
     24 wcalc
     16 ./pSX
     15 rpm

```

---

### Post by cdtech on 2008-08-09
```
 87 sudo
     81 ls
     63 cd
     56 cat
     20 la
     18 df
     16 pico
     12 ./wifitest
     12 gconf-editor
     11 update
```

---

### Post by armageddon08 on 2008-08-09
Mine are:
     49 cd
     43 sudo
     40 plog
     40 ls
     31 pon
     23 gedit
     22 exit
     18 killall
     17 man
     12 mencoder

---

### Post by Oldsoldier2003 on 2008-08-09
108 bzr
     51 ls
     45 cd
     24 cat
     20 sudo
     17 man
     13 apt-cache
      9 sh
      9 grep
      8 pwd

---

### Post by PmDematagoda on 2008-08-09
```
    100 sudo
     74 cd
     55 ls
     28 ./et-sdl-sound
     27 find
     21 man
     17 make
     17 cat
     11 wget
      7 patch
```

---

### Post by Pro-reason on 2008-08-30
For me:
```
     42 ls
     36 ll
     36 echo
     33 cd
     23 cat
     17 nano
     15 wget
     14 command2literal
     12 sudo
     10 zcat
```


For root:
```
     17 cd
     11 nano
     11 exit
      7 clear
      6 rm
      6 ll
      5 reboot
      5 ls
      5 id
      4 killall

```

---

### Post by mellowd on 2008-08-30
138 ls
116 cd
44 rm
28 screen
24 df
21 vim
21 aptitude
17 mv
15 du
11 mkdir

---

### Post by klange on 2008-08-30
```
    194 bzr
     72 sudo
     61 cd
     44 ssh
     31 ls
     10 nano
     10 git
      7 scp
      6 timidity
      5 make

```
Things I've been doing:
- Working on my forum, which is under a bazaar repository in Launchpad.
- Updating Compiz, from git.
- Listening to MIDIs.

---

### Post by crimesaucer on 2008-08-30
```

    184 su
    110 pacman
     90 makepkg
     78 cd
     67 ls
     60 dmesg
     57 man
     44 sudo
     22 free
     20 lspci

```

---

### Post by doas777 on 2008-08-30
254 sudo
     28 nslookup
     16 vncviewer
     16 ls
     15 ll
     13 ssh
     13 cd
     12 du
     10 ping
      9 exit

---

### Post by Ethyrdude on 2008-08-31
sudo apt-get whatever
sudo dpkg -l whatever
xhost +
sudo gedit  "Careful with this one, if you gedit the wrong file!"
update-menus
sudo updatedb
sudo /etc/init.d/gdm start
ls -all
cd /to various directories
uname -a

These are just a few I have used during the past week.

Here are a few I'm glad I'm not using
./configure
./make
./make install
Yes, I actually used to like FreeBSD.

---

### Post by doorknob60 on 2008-08-31
On my parent's Kubuntu laptop that I don't use much (not at home, I'm curious to see what the list is on my Desktop :D)

     129 sudo
     22 cd
     18 ls
     11 glxgears
      5 wine
      5 w3m
      5 make
      4 /usr/lib/kde4/bin/konqueror
      4 ndiswrapper
      4 exit

as root:

      9 iwconfig
      8 rmmod
      6 python
      5 exit
      4 sudo
      4 modprobe
      3 nano
      2 sh
      2 history
      2 cp

---

### Post by Saint Angeles on 2008-08-31
```
    248 sudo
     54 wavemon
     37 cd
     34 ls
     11 thunderbird
     11 ./configure
      9 gnome-panel
      6 wget
      6 make
      6 gksu
```

(i'm sorry if this list is offensive to any of the developers of programs that arent on my list. i wish you could all be on my list but it just didnt work out that way.)

---

### Post by kagashe on 2008-08-31
123 sudo
     77 exit
     34 ls
     32 ping
     27 free
     25 cd
     24 xrandr
     20 ps
     18 man
     17 mount

kagashe

---

### Post by gjoellee on 2008-08-31
I have have been using Ubuntu in about 1year now, and  l like to keep it easy (which means a stick to graphical installers etc....)
     12 sudo
      6 cd
      2 ls
      2 ./autogen.sh
      1 uname
      1 twf
      1 rm
      1 history
      1 --help
      1 help

---

### Post by stonerrob420 on 2008-10-07
130 sudo
     10 locate
      8 ls
      6 update-menus
      6 cd
      4 gksudo
      3 update-desktop-database
      3 torcs
      3 nvclock
      3 firestarter

---

### Post by InfinityCircuit on 2008-10-07
On my main machine:

```
dmoerner@x40:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    182 ls
    105 cd
     49 git
     35 vim
     13 rm
     13 git-buildpackage
     13 dpatch
      9 su
      9 dpatch-edit-patch
      9 aptitude
x40:~# history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    192 aptitude
     66 ls
     35 exit
     31 cd
     21 vim
     11 dpkg
     10 apt-show-versions
      9 rmadison
      9 /etc/init.d/gdm
      9 apt-cache

```

Sort of odd--9 uses of su but 192 uses of aptitude inside those root shells?

---

### Post by croucho on 2008-10-07
114 cd
82 ls
20 sudo
18 chmod
12 wine
4 echo
4 asoundconf
3 win
3 rm
3 gvim

---

### Post by david_lynch on 2008-10-07
50 ssh
     27 grep
     26 sudo
     26 ifconfig
     25 w
     20 dmesg
     17 cd
     16 ltr
     15 ping
     14 vi

---

### Post by Trail on 2008-10-07
New run:

```

    125 make
    113 ls
     89 cd
     87 ./REserver
     47 ssh
     40 man
     37 vi
     27 sudo
     25 proxychains # didn't work :|
     22 ./configure

```

---

### Post by davidyu on 2008-10-07
28 cd
     24 apt-get
     21 ls
     12 ps
     11 gedit
      8 dpkg
      7 ln
      6 ibm5250
      3 su
      3 kill

---

### Post by kpatz on 2008-10-07
On zuul (my firewall/dev/email box):

     84 ls
     63 cd
     50 sudo
     37 man
     34 vi
     18 diff
     18 cat
     15 mysqldump
     15 mount
     11 vnstat

On my mythtv box:

    117 ls
     87 cd
     66 sudo
     44 vi
     21 ./backupzuul.sh  (a backup script I've been working on)
     15 du
     14 rsync
     13 mount
     13 cat
     12 ps

---

### Post by littletinman on 2008-10-07
71 sudo
     16 cd
      9 wget
      4 tar
      4 gksudo
      3 service
      3 make
      3 ./ies4linux
      2 wine
      2 ./poweriso

I don't use a lot of terminal stuff on the partition i'm on right now. My other one I do a lot more tweaking with.

---

### Post by Dr Small on 2008-10-07
On Darkghost:
```
     87 ls
     77 :q
     52 cd
     48 sudo
     30 rm
     29 vim
     26 gpg
     25 ssh
     14 man
     11 pacman

```

On Mycroft:
```
    108 vim
     91 cd
     50 bzr
     28 chmod
     20 :q
     11 netstat
     10 rm
     10 gpg
      8 mv

```

---

### Post by bomanizer on 2008-10-07
I'm running a new installation now, this is a bit weighted.. but anyways:

```

     31 sudo
     11 cp
      5 ifconfig
      4 tail
      4 lsmod
      3 ls
      3 cd
      2 hdaps-gl
      2 cat
      2 apt-get

```

ps. Ibex looks good even as a beta :)

---

### Post by Flynn555 on 2008-10-07
```
107 sudo 
92 ls
70 cd
42 electricsheep
17 rm
11 electricsheep-preferences
8 su
8 nano
8 exit
7 lpstat
```

lol i think the last think i was working on was electric sheep as my background rofl

---

### Post by -grubby on 2008-10-07
```

nathan@linda:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     76 ls
     50 python
     33 cd
     31 sudo
     17 killall
     16 echo
     14 g-ssh
     10 mplayer
      9 mkdir
      9 man

```

---

### Post by Rhubarb on 2008-10-07
89 cd
     58 exit
     47 sudo
     41 ssh
     28 man
     24 java
     22 make
     20 ./configure
     16 ls
     14 gpsbabel

---

### Post by GooglePlexity on 2008-10-07
```
  
     88 ls
     79 cd
     41 sudo
     12 killall
     11 nm-applet
     10 ./install
      9 emerald
      9 ./change-colors
      8 ./backup.sh
      7 ssh

```

---

### Post by Pogeymanz on 2008-10-07
102 sudo
    101 yaourt
     66 go
     30 ssh
     30 ls
     20 emacs
     18 sensors
     17 echo
     16 vim
     16 killall

I use yaourt to update my system everyday (Arch Linux). You need root permissions to run it.

go is an alias for startx.

I ssh into my work computer to work at home.

I use emacs AND vim!!!

---

### Post by iKonaK on 2008-10-07
73 sudo
     67 ls
     53 cd
     52 man
     35 encfs
     34 fusermount
     17 top
     12 kill
     10 uptime
     10 apt-cache

---

### Post by kavon89 on 2008-10-07
>     231 sudo
     36 ifconfig
     29 clear
     28 ping
     23 top
     21 ./teamspeak
     20 cd
     15 man
     13 lynx
     10 netstat

thats my home server

---

### Post by jerome1232 on 2008-10-07
This is my home server, this used to be an admin account now I've seperated that out to another account (hence the use of sudo and su)

teamspeak is a script that starts/stops/restarts teamspeak and ts2perlmod.

```
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     82 ls
     72 exit
     61 cd
     60 su
     40 sudo
     30 vim
     17 teamspeak
     15 rm
     13 screen
     13 chmod
```

From the admin account, all I do  in this account now is run apt-get update && apt-get upgrade, shanty was a program that would convert a jpeg to a colored ascii banner using any text file, I made a nifty image using the source code for the Linux kernel.
```
155 sudo
     81 ls
     33 cd
     24 man
     14 rm
     14 exit
     11 screen
     11 nmap
     10 vim
      8 shanty
```

---

### Post by SuperSonic4 on 2008-10-09
```
13 cd
      9 ffmpeg
      7 cmake
      3 su
      2 wget
      2 tar
      2 make
      2 history
      2 ./configure
      1 this

```

---

### Post by extruct on 2008-10-09
143 sudo
     39 cd
     35 ls
     15 exit
     14 nvclock
     13 rm
     10 ps
      7 supertux2
      7 man
      7 gedit

---

### Post by Le-Froid on 2008-10-09
Here's mine:

    223 cd
    164 ls
    104 sudo
     76 svn
     70 rm
     43 make
     29 ./configure
     24 ./autogen.sh
     15 g++
     13 nano

---

### Post by cobolt01 on 2008-10-09
53 cd
     21 ls
     16 clear
      8 pwd
      7 man
      7 dir
      5 sudo
      5 figlet
      5 cat
      4 find

:):):):):):):):)

---

### Post by hellion0 on 2008-10-10
127 ivtv-radio
44 nano
41 mplayer
39 killall
35 rar
31 conky
23 sudo
21 screen
21 ps
20 rm

---

### Post by ghindo on 2008-10-10
```
michael@ubuntu:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    112 sudo
    109 mv
     33 rm
     27 ssh
     26 ls
     21 mkdir
     17 nautilus
     16 python
     15 nano
     15 cd
```

---

### Post by chucky chuckaluck on 2008-10-10
i reinstalled arch yesterday (to switch from reiser to jfs). from the looks of the output, it seems like i was lost for most of the time.

_user_

     63 cd
     43 feh
     38 nano
     35 sudo
     31 su
     24 ls
     11 streamripper
      9 mount
      7 obmenu
      6 rm


_root_

     39 pacman
     15 chmod
     13 nano
     12 cd
      9 feh
      7 reboot
      7 gpasswd
      7 echo
      5 pwd
      5 ls

---

### Post by kavon89 on 2008-10-10
```
    202 sudo
     55 netstat
     46 ping
     33 xset
     25 ssh
     18 man
     12 cd
     10 iwconfig
      7 git
      7 clear

```

Whenever my wireless drops out and I have to reconnect, I have to fix the default gateway with route. :s

---

### Post by psychomichael on 2008-10-18
22 sudo
      6 gconftool-2
      6 cat
      5 dmesg
      5 aplay
      2 wget
      2 lspci
      2 history
      2 cd
      1 uname

---

### Post by dariusdwtt on 2008-12-06
176 conky
143 kill

(lol)

---

### Post by GeorgeVita on 2008-12-06
Hi, top 10 terminal commands for my Ubuntu 8.04 on a laptop and a 3G modem for internet connection:

$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    143 sudo
     35 wvdial
     33 man
     24 ls
     21 minicom
     19 cd
     18 lsusb
     11 cat
     10 grep
      8 plog

Most sudo commands were 'sudo wvdial' or 'sudo gedit'.

Note that 8.04 was my first Linux O.S. installed 6 months ago.

---

### Post by jakupl on 2008-12-06
```
$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
```
    132 sudo
     61 man
     47 ls
     46 cd
     25 gksudo
     14 ps
     13 wipe
     11 locate
     11 ccrypt
     10 htop

---

### Post by rudihawk on 2008-12-06
Here is mine:
```
106 sudo
     62 vnstat
     29 ls
     21 cd
     15 gedit
     15 fbsetbg
     13 top
     11 conky
     10 nautilus
      9 ./script_main.sh

```

---

### Post by k@e on 2008-12-06
```
    158 javac
    105 sudo
     65 java
     35 hamachi
     14 pasuspender
     13 wine
      7 ls
      6 javadoc
      6 ./exaile
      5 ./configure

```

Indeed, I am learning Java right now. ;)

---

### Post by sujoy on 2008-12-06
6 cd
      3 sudo
      2 vi
      1 tar
      1 makepkg
      1 ls
      1 ifconfig
      1 clear

---

### Post by RATM_Owns on 2008-12-06
>      62 sudo
     32 cd
     31 rm
     17 ./twintig
     15 zenity
     12 make
     12 find
     11 ./toolchain.sh
     11 gcc
     10 svn
sudo = Duh
cd = Duh
rm = Duh
./twintig = Wii savegame unpacker or repacker (I forget which one :P )
zenity = Duh
make = Duh
find = Duh
./toolchain.sh = Setup for PSP Dev Kit
gcc = Duh
svn = Duh

---

### Post by bobbocanfly on 2008-12-06
On my brand new Debian Etch web/mail/db server (just set it up yesterday):

>      48 postconf
     47 apt-get
     44 cd
     38 ls
     26 /etc/init.d/postfix
     17 nano
     15 htop
     14 cat
     12 useradd
     12 /etc/init.d/spamassassin


---

### Post by -grubby on 2008-12-06
```

     94 ls
     76 mkdir
     59 cd
     40 gr-ssh
     30 python
     27 mplayer
     17 rm
     16 uptime
     16 sudo
     12 chmod

```

---

### Post by catchytune on 2008-12-06
85 sudo
56 ps
52 cd
39 ls
27 audacious
26 ulimit
24 unp
20 pwgen
18 gpg
13 kill

lots of music in it!

---

### Post by frankleeee on 2008-12-06
pseudo apt-get a-life

---

### Post by doorknob60 on 2008-12-06
```
austin@austin-desktop ~ % history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
      6 sudo
      2 y
      2 man
      2 less
      1 winecfg
      1 mount
      1 ls
      1 locale
austin@austin-desktop ~ %

``` Sounds way wrong lol, I'm assuming that it only counts bash, not zsh (which is my default). y would probably be my most used, followed by sudo, then ls, then nano. y is an alias to yaourt, a frontend to pacman, Arch's package manager. And it doesn't need sudo so it would count in here.

---

### Post by Neovos on 2008-12-06
user:
```
    173 sudo
     71 ls
     63 cd
     18 scanimage
     13 mount
     12 zenity
     10 date;
      9 lilypond
      9 dmesg
      9 anacron

```
root:
```
      4 su
      3 smartctl
      3 gedit
      1 rmdir
      1 rm
      1 ls
      1 history
      1 cd

```

---

### Post by rokytnji on 2008-12-06
After New Ubuntu 8.04 LTS  dedicated install on IBM M57 Desktop

16 sudo
      2 sensors
      2 lspci
      2 /etc/modules
      1 wget
      1 tar
      1 su
      1 sensors-detect
      1 htop
      1 hotbabe

---

### Post by arbosis on 2008-12-06
[FONT="Courier New"]     77 sudo
     33 top
     23 ssh
     22 cd
     20 ps
     18 ls
     13 pkill
     13 make
     12 man
     10 locate[/FONT]

I really love **top**

---

### Post by meg23 on 2008-12-06
92 sudo
     58 elinks
     42 cat
     23 man
     19 firefox
     17 cd
     11 ls
     11 clear
      8 for
      7 lynx

---

### Post by bsharp on 2008-12-06
Here's mine:
```
    129 sudo
     25 exit
     21 ssh
     19 ls
     19 cd
      8 aptitude
      6 startx
      6 ffmpeg
      6 apt-get
      5 tar
```

This isn't accurate since I only reinstalled last week.

---

### Post by chucky chuckaluck on 2008-12-06
my latest count -

    194 nano
    184 sudo
     78 feh
     59 su
     56 cd
     49 htop
     43 cplay
     29 elinks
     28 scrot
     23 rm

i think most of those nano entries are from constantly messing with .Xdefaults and .pypanelrc. (kind of surprised scrot was so low on the list.)

---

### Post by mssever on 2008-12-06
> **arbosis said:**
> I really love **top**
If you like top, you'll love htop. Seriously. I doubt I've used top even once since discovering htop.

---

### Post by cdtech on 2008-12-07
```

177 sudo
 95 ls
 48 cd
 24 cat
 20 man
 19 la
 13 ..
 12 update
 11 ssh
  8 dd
```

---

### Post by gnuvistawouldbecool on 2008-12-07
115 sudo
     44 cd
     28 wget
     23 top
     18 ls
     15 sh
     13 svn
      8 xsnow
      8 ps
      8 cat

Not sure how xsnow got there, I only messed around with it once.

I'm suprised metacity --replace and compiz --replace aren't on there actually.  Oh well

---

### Post by dannytatom on 2008-12-07
140 sudo
     24 ls
     21 cd
     13 shell-fm
     10 make
      9 killall
      6 clear
      5 telnet
      5 htop
      3 irssi

---

### Post by ronnielsen1 on 2008-12-07
> 48 sudo
     12 ls
      8 cd
      6 gksudo
      5 lspci
      3 wine
      2 winecfg
      2 wget
      2 kwikdisk
      1 su

The last one is because I keep forgetting Ubuntu doesn't do that ](*,)

---

### Post by abhilashm86 on 2008-12-07
for root    
     61 cd
     58 gedit
     48 ls
     44 cc
     33 pwd
     28 ./a.out
     26 exit
     25 sudo
     19 rm
     14 apt-get

for myself
     158 sudo
     62 ls
     48 cd
     44 pwd
     35 exit
     25 man
     18 ./a.out
      6 gnome-do
      6 g++
      5 su

nopes i keep changing directories alwayzzzz,hey ppl is this summary of one month or total linux use???????

---

### Post by abhilashm86 on 2008-12-07
> **chucky chuckaluck said:**
> my latest count -

    194 nano
    184 sudo
     78 feh
     59 su
     56 cd
     49 htop
     43 cplay
     29 elinks
     28 scrot
     23 rm

i think most of those nano entries are from constantly messing with .Xdefaults and .pypanelrc. (kind of surprised scrot was so low on the list.)

may i know whats nano please????

---

### Post by bobbocanfly on 2008-12-07
> **abhilashm86 said:**
> may i know whats nano please????

Its a little CLI text editor. Does the same job as Vim, but is a lot easier to use. [http://en.wikipedia.org/wiki/Nano_(text_editor](http://en.wikipedia.org/wiki/Nano_(text_editor))

---

### Post by chucky chuckaluck on 2008-12-07
> **abhilashm86 said:**
> may i know whats nano please????

only the very greatest of all text editors. open up a terminal and type *nano*. it's installed in ubuntu by default, if i'm not mistaken. it's like vim without the bloat.

---

### Post by dynamethod on 2008-12-07
```

history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr


     69 sudo
     48 ls
     25 cd
     20 clear
     17 exit
     11 kill
     10 pgrep
     10 g++
      9 dig
      8 nano


```

---

### Post by spupy on 2008-12-07
I see I've been writing/testing too much scripts and programs lately (zenity, notify-send, configure, make):
```
     33 zenity
     27 cd
     23 q
     19 make
     17 gpsa
     17 ./configure
     15 su
     14 sudo
     14 notify-send
     13 0
```
And for root:
```
     37 cd
     34 ant
     32 lillypad
     29 cd+
     20 q
     20 l
     18 /etc/init.d/acpid
     13 0
     12 cat
     10 emerge
```

---

### Post by SuperSonic4 on 2008-12-07
7 su
5 ./converter
4 wget
4 sensors
      3 rm
      3 amarok
      2 top
      2 sudo
      2 /opt/kde3/share/applications/kde/amarok.desktop
      2 mkdir

not too surprising, ```
./converter
``` is my flv to mp3 script. I'm surprised at rm though

---

### Post by mssever on 2008-12-07
> **chucky chuckaluck said:**
> only the very greatest of all text editors. open up a terminal and type *nano*. it's installed in ubuntu by default, if i'm not mistaken. it's like vim without the bloat.
:)

Actually, there's a bunch of stuff that vim can do that nano can't, so I beg to differ. It *is* easier for newbies, though.

---

### Post by ad_267 on 2008-12-08
> **mssever said:**
> :)

Actually, there's a bunch of stuff that vim can do that nano can't, so I beg to differ. It *is* easier for newbies, though.

I think he meant it's like vim but without all the really useful features. :p

For bloat see emacs.

---

### Post by davidfg4 on 2009-01-23
432 cd
    420 sudo
    350 ls
    170 cat
    138 man
    121 javac
     85 ssh11
     83 find
     67 nano
     59 crontab

ssh11 is an alias I have to ssh to my server

---

### Post by dnRoyston on 2009-01-23
**Me**:
```
    140 sudo
     39 cd
     18 dir
     18 bash
     17 perl
     15 conky
     13 cat
     12 killall
     10 python
      8 scrot

```

**Sudo**:
```
    1  exit
    2  chmod /etc/sudoers 440
    3  chmod 440 /etc/sudoers
    4  reboot
    5  chmod root:root
    6  chmod root:root /etc/sudoers
    7  chmod root /etc/sudoers
    8  chown root:root /etc/sudoers
    9  reboot
   10  history
```
I only have 10 terminal commands USED as root, the others are all just sudo'd

---

### Post by toneman77 on 2009-01-24
```
tone@tones:~$ cat .bash_eternal_history | awk '{print $5}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
   1799 sudo
   1015 cd
    774 ll
    585 ssh
    476 cat
    407 ps
    328 ping
    166 nano
    162 locate
    142 killall
```

---

### Post by billgoldberg on 2009-01-24
258 sudo
     31 killall
     25 startx
     22 conky
     15 cd
     14 pkill
     14 ping
     14 pacman
     13 yaourt
     13 startxfce4

xfce4 isn't even installed anymore :p

---

### Post by Cosimix on 2009-01-24
**Strange I have only one entry:**

[COLOR="Red"]**1841335484 sudo nice -n -20 firefox && firefox youporn.com &**[/COLOR]

:) AH AH AH 

    170 sudo
     44 ls
     35 ssh
     34 ifconfig
     31 ping
     24 exit
     22 cat
     18 brctl
     17 cd
     12 route

---

### Post by jimi_hendrix on 2009-01-24
sudo, cd, ls, make, vim, gvim, ./programName, mount, umnt, echo, cat

---

### Post by hatten on 2009-01-24
22 sudo
     22 ls
     20 cd
     13 g++
     10 ./German
      9 file
      7 rhythmbox-client
      3 man
      3 less
      3 bash

---

### Post by karlmp on 2009-01-24
karl@karlzt:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort
|uniq -c | sort -n | tail | sort -nr
    102 sudo
     77 top
     33 reset
     31 ping
     22 xkill
     22 rtorrent
     22 python3
     15 rm
     14 bzr
     12 man
karl@karlzt:~$ history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | s
ort -n | tail | sort -nr
     92 sudo
     67 top
     28 reset
     24 ping
     22 xkill
     22 rtorrent
     14 python3
     12 man
     10 history
      9 screen

---

### Post by Darkspark on 2009-01-24
Here are mine:

    152 sudo
     34 cd
     28 ls
     19 clear
     13 ./MacAddr.sh
     13 lsl
     12 pwd
     10 virtualbox
     10 g++
     10 exit

---

### Post by Sprut1 on 2009-01-24
189 sudo
     83 cd
     33 iwconfig
     17 man
     15 python
     15 kdesu
     15 iwlist
     14 wpa_supplicant
     14 ifconfig
     10 ls

I like networking :popcorn:

---

### Post by cmnorton on 2009-01-24
39 sudo
     38 ls
     13 cd
     11 exit
     10 ps
      9 telnet
      8 man
      7 find
      5 ftp
      4 vi

---

### Post by OrbJinzo on 2009-01-24
76 sudo
      8 gksudo
      6 cd
      5 uname
      4 ping
      4 iwconfig
      3 winetricks
      3 wget
      3 gparted
      2 lspci

---

### Post by ajcham on 2009-01-24
91 sudo
65 man
33 ls
20 exit
14 cd
13 mplayer
10 mv
 9 top
 9 less
 8 python

---

### Post by linux_tech on 2009-01-26
68 sudo
     18 cat
     13 ps
     12 ls
     12 hdparm
     10 python
     10 lspci
     10 cd
      9 make
      9 gksudo

---

### Post by abhilashm86 on 2009-01-26
abhilash@abhi:~$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    201 vim
    182 python
     59 mocp
      9 man
      8 ls
      7 pyhton
      4 sudo
      4 htop
      3 samba
      3 pan

ha ha take look at pyhton,how it came there,maybe spelling mistake,huh:)

as root
root@abhi:/home/abhilash# history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
     91 ls
     75 cd
     55 sudo
     39 mutt
     29 exit
     24 vim
     20 pwd
     20 mocp
     19 gedit
     17 chmod

---

### Post by Niksko on 2009-01-26
Maybe It's just me but I had to make the code read 'history 1' in order to get my entire history. Anyhow:

118 ls
96 vim
71 cd
22 g++
17 man
16 ./rightdock.sh
13 sudo
11 ./leftdock.sh
10 history
8 rm

---

### Post by ghindo on 2009-01-26
```
[michael@arch ~]$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    168 sudo
    111 yaourt
     48 pacman
     37 man
     35 nano
     17 nautilus
     17 locate
     14 xinit
     11 scrot
     11 ls
```

---

### Post by Rolaulten on 2009-01-26
199 sudo
     38 exit
     30 cd
     25 killall
     20 top
     20 clit
     14 /home/dorian/gbchange
     12 gedit
     10 ls
      8 make


...yea thats a lota work done...funny as it does not show the fact that most of those sudo's are for random apt-get commands...

---

### Post by missfroguk on 2009-02-02
101 cd
     73 ls
     45 ssh
     30 openoffice
     26 mv
     22 xpdf
     13 cp
     10 sftp
      9 rm
      9 find

---

### Post by nlz on 2009-02-19
151 sudo
     79 cd
     47 ls
     23 locate
     19 killall
     14 wine
     14 ps
     12 conky
     12 cat
     11 gedit

---

### Post by jeterfan1 on 2009-02-20
114 plog
     95 pon
     30 acpi
     28 sensors
     24 ifconfig
     20 xrandr
     19 conky
     17 sudo
     17 poff
     14 cd

---

### Post by Metallion on 2009-02-20
143 ls
119 cd
74 sudo
17 go
15 ./hello.rb
12 mv
11 cat
10 apt-cache
6 rsync
6 pushd

Doesn't really show much what I use most since sudo is put in there as a separate command. I use the terminal a lot though. It's basically my file manager. :)

---

### Post by adamlau on 2009-02-20
Mostly aliases...

84 ht = htop -u adamlau --sort-key PERCENT_MEM
65 mks = makepkg -e -c
63 rem = sudo pacman -Rns
61 nano
54 dl = aria2c -s 8 -d /file/Downloads --enable-http-pipelining=true 
50 inst = sudo pacman -Up
37 cfg = ./configure --help > /tmp/cfg; mousepad /tmp/cfg & exit
36 thx = sudo thunar /
33 upg = sudo pacman -Syu --ignore truecrypt && sudo abs
33 mn = alias mn='manout'
manout () {
   man $1 | col -b > /tmp/$1 && mousepad /tmp/$1 & exit
}

---

### Post by jimi_hendrix on 2009-02-20
i have the tendency to type dir into console...*ducks*

---

### Post by Metallion on 2009-02-20
> **jimi_hendrix said:**
> i have the tendency to type dir into console...*ducks*

*Catches tomato and throws back at the sender* Why not make an alias in bashrc that calls the ls command when you type dir? Linux mint did it. :)

---

### Post by jimi_hendrix on 2009-02-20
thats BRILLIANT!

---

### Post by Warpnow on 2009-02-20
91 sudo
     55 cd
     54 dir
     12 mount
      6 useradd
      5 usermod
      3 wbar
      3 ./Symphonyrc
      2 ./unetbootin-linux-304
      2 ./storybook.sh

---

### Post by hyperdude111 on 2009-02-20
132 sudo
     33 cd
     16 make
      6 ./configure
      4 sh
      4 firefox
      4 ./ffmpeg/ffmpeg
      4 ffmpeg
      3 emerald
      2 whoami

---

### Post by velja27 on 2009-02-20
```
109 sudo
     75 cd
     39 make
     22 phoronix-test-suite
     12 hamachi
     12 ./configure
     12 ./3dpong
     10 cmake
      9 sdl-config
      9 cowsay


```
Thats my list :)

---

### Post by crimesaucer on 2009-02-20
```

[seventy3@HPdv9920us ~]$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
    507 sudo
     70 pacman
     48 md5sum
     40 man
     39 ls
     30 cd
     25 makepkg
     21 twf
     20 dmesg
     18 killall

```

---

### Post by calrogman on 2009-02-20
41 (while
     36 sudo
     33 cd
     29 figlet
     26 nc
     20 man
     17 clear
     15 exit
     15 cal
     13 ls

(while is from back in the countdown to 1234567890, figlet proves all I do is muck around.

---

### Post by Kinetic Being on 2009-02-20
User:

     89 ls
     62 su
     40 nano
     30 cd
     19 htop
     17 man
     14 emerge
     14 alsamixer
     11 rm
     10 startx


Root:

    138 ls
     59 cd
     53 nano
     51 emerge
     33 euse
     20 man
     15 rm
     14 equery
     11 mv
     10 emacs


I've been learning to use emacs lately, been using it more and more--I really like it for code/cfg editing...The reason it dosn't have a bigger number is because once you open it you can just use the keyboard shortcuts to open files, and do basically everything...

I've only been using this setup since a little after the new year...

If you couldn't tell by the commands, I'm using Gentoo...

---

### Post by Swagman on 2009-02-20
dpkg --configure -a

---

### Post by avaralom on 2009-02-20
82 ls
     60 cd
     56 ssh
     49 sudo
     23 iwconfig
     22 xload
     15 nano
     12 irssi
     12 fbsetbg
     11 write

none of those are too surprising XD

---

### Post by BazookaAce on 2009-02-20
89 sudo
19 exit
17 clear
16 su
12 nautilus
12 killall
11 conky
11 apt-get
10 gnome-system-monitor
8 top

---

### Post by hey_ram on 2009-03-04
my top 10 most used terminal commands:

    130 ./h
    129 gcc
     25 valgrind
     23 gdb
     22 man
     22 cat
     19 vim
      9 cd
      7 ls
      3 which


i guess i have been doing a lot of C these days!

---

### Post by dragos240 on 2009-03-04
```

    144 sudo
     49 cd
     21 clear
     20 pilot-xfer
     16 dir
     13 aptitude
     12 info
     11 iwlist
     11 fdisk
     10 mplayer

```

---

### Post by shadowdude1794 on 2009-04-14
Mine
```

    134 sudo
     40 cd
     19 gpg
     18 ls
     16 mkdir
     12 getgrub2
     12 ../configure
     10 wine
     10 svn
      8 apt-get

```

---

### Post by PurposeOfReason on 2009-04-14
```

     75 clear
     51 ls
     44 cd
     43 vim
     36 sudo
     28 su
     20 sensors
     14 x
     14 ,
     13 cp

```

I went sensors happy for a while when I put in a new cpu.

---

### Post by rucadulu on 2009-04-14
cd
ls
ps
cat
rm
rsync
find
locate
vi
./*.sh
more
netstat
top
kill
tar

---

### Post by Eviltechie on 2009-04-14
65 sudo
     34 clear
     32 cd
     28 exit
     21 ./unreal
     21 ssh
     11 ls
     10 ping
      6 /usr/local/tonido/tonido.sh  <Not foss btw
      6 killall

---

### Post by GammaRay256 on 2009-04-15
On my laptop:
```
142 ping
65 ssh
44 exit
33 cd
18 wine
18 sudo
15 ls
13 midi
8 ifconfig
6 wget

```

Looks like I've used ping way too much... I've been having a lot of problems in the last couple days with my wireless bridge...

---

### Post by CraigPaleo on 2009-04-15
Right click 
Paste 
Enter

Okay, seriously. 

     46 sudo
      9 apt-get
      5 cd
      2 kdesudo
      2 ./configure
      2 chkconfig
      1 wget
      1 w
      1 /usr/sbin/chkconfig
      1 uptime

---

### Post by Mr Tim on 2009-04-15
Here we go...
     96 exit
     78 sudo
     53 cd
     32 ls
     29 ssh
     25 gcc
     22 ./a.out
     12 vim
     12 gpg
     11 pypanel
So I exit a lot, that can't be helped.

---

### Post by Newuser1111 on 2009-04-15
```
     24 sudo
     14 zenity
     12 cd
      5 wine
      4 toilet
      4 ls
      3 uname
      3 ghex
      3 dir
      3 apt-get

```[COLOR="White"]Text[/COLOR]

---

### Post by ks07 on 2009-04-15
90 sudo
     41 exit
     18 cd
      8 gksudo
      6 locate
      6 fdisk
      4 mount
      4 killall
      4 glxgears
      3 realplay
[LEFT]
^--- Shows how little I use the terminal. :p 
[/LEFT]

---

### Post by matmatmat on 2009-04-15
:)
> 
     93 vim
     87 javac
     67 java
     42 cd
     39 ls
     37 sudo
     27 kate
     13 wine
     13 python
      9 rm


---

### Post by Mehall on 2009-04-15
135 exit
     86 sudo
     63 ssh
     24 cd
     22 ping
     19 ls
     18 apt-cache
     10 nano
      9 ps
      7 man


it worries me I use "exit" more than sudo :/

And nano count I thought would be MUCH higher.

---

### Post by crazyfuturamanoob on 2009-04-20
I don't use much terminal.
> 
    122 make
    105 ./output
     56 cd
     45 sudo
     25 clear
     18 ls
     16 locate
     11 ./testing
      8 ./md2
      8 LD_LIBRARY_PATH=/usr/lib32


---

### Post by nandemonai on 2009-04-20
Desktop:

    144 sudo
     37 ssh
     33 ls
     15 sshfs
     14 pidgin
     13 df
     12 htop
     12 cd
     11 cat
     10 sleep

Server:

    120 sudo
     54 screen
     46 ls
     25 exit
     21 cat
     18 cd
     15 clear
     14 htop
      7 make
      6 ps

---

### Post by wmcbrine on 2009-04-20
113 less
     80 pytivo
     73 ls
     63 git
     43 cd
     25 pine
     23 tint
     11 cp
     10 clear
      7 pytivo-commit

---

### Post by steelcap on 2009-04-20
65 ping
     64 ssh
     48 exit
     40 sudo
     40 ls
     33 cd
     27 telnet
     18 traceroute
     13 startvpn
     10 stopvpn

---

### Post by ibuclaw on 2009-04-20
140 ls
     84 cd
     49 vim
     20 rm
     16 exit
     14 sudo
     13 make
      9 dpkg
      8 mv
      7 for

---

### Post by cariboo on 2009-04-20
75 sudo
     62 cd
     40 ssh
     35 ls
     26 cat
     19 mc
     15 scan_all*
     12 man
      9 ps
      8 df

* scans for ip addresses of computers on the network

Jim

---

### Post by Guillaumeb on 2009-04-20
[HTML]apt-get laid[/HTML] :roll:  Ok i'm out

---

### Post by skillllllz on 2009-04-20
70 ssh
36 ping
22 nmap
19 sudo
14 rdesktop
5 man
4 export
4 exit
3 telnet
3 clear

Does this say anything about me?

---

### Post by VCoolio on 2009-04-20
132 conky
 86 killall
 42 kill
 24 sudo
 19 ps
 16 cd
 11 wget
 10 ls
 8 man
 6 locate

Yes, I've discovered conky lately and messed around, but I'm satisfied with it now so I reckon it'll come down in the short future. Little surprised that gksudo isn't in the list, does it count as sudo?

---

### Post by BazookaAce on 2009-04-20
195 sudo
     21 update-manager
     19 su
     19 exit
     11 mplayer
      7 emerald
      6 iwconfig
      6 gnome-system-monitor
      6 clear
      6 cd

---

### Post by KhaaL on 2009-04-20
86 sudo
     45 pulseaudio  (usually with the switch -k, and -D, and if i'm really energic -vvv)
     31 p3 (alias to swedish public radio)
     28 gpg
     24 aptup (apt-get update & upgrade in one command)
     24 aptitude
     22 wine
     22 aptin (aptitude install)
     20 killall 
     11 sh

---

### Post by gmjs on 2009-04-20
82 cd
71 exit
69 sudo
45 ls
33 wget  
27 du
16 mysql
15 gtypist
10 rm
 9 tesseract

---

### Post by CharmyBee on 2009-04-20
49 cd
     34 sudo
     27 dir
     23 wine
     12 make
     10 man
      9 desmume-cli
      7 dgen
      6 sh
      6 sabresdl

I never ls'd once.

---

### Post by sekinto on 2009-04-20
```
    131 sudo
     30 pacman
     21 cd
     20 su
      9 nano
      8 tar
      6 startx
      6 make
      6 ls
      6 ./configure
```

It isn't fair data though since this is a fresh install.

---

### Post by dubhear on 2009-04-20
178 sudo
     58 cd
     52 dmraid
     21 ls
     16 exit
     15 dir
      7 apt-get
      5 mount
      4 umount
      4 dpkg-buildpackage

---

### Post by gokussj4nr on 2009-04-21
175 ls
130 sudo
108 cd
21 git
6 rm
5 cat
4 vi
4 su
4 exit
4 echo

---

### Post by Tmi on 2009-04-21
53 cd
     52 ls
     47 conky
     42 nano
     42 killall
     25 fbsetbg
     22 sudo
     15 rm
     12 find
     12 alsamixer

Haven't used the CLI all that much in Ubuntu.

---

### Post by gnomeuser on 2009-04-21
I am trying to cut down my terminal use.. quite succesfully I might add:

      7 sudo
      4 echo
      4 cat
      3 top
      3 ps
      2 mv
      2 kill
      2 for
      1 mkdir
      1 history

---

### Post by wingnux on 2009-04-21
>     136 sudo
     89 cd
     51 ls
     24 wine
     19 exit
     17 make
     15 gedit
     10 ./mame
     10 amsn
      8 svn

On a recently installed Jaunty.

---

### Post by Wiebelhaus on 2009-04-21
Super cool thread.

---

### Post by Sub101 on 2009-04-21
110 sudo
     49 cd
     43 javac
     39 java
     21 jar
     15 make
     10 man
     10 locate
     10 apt-get

---

### Post by JordyD on 2009-04-21
110 ls
     67 cd
     53 vim
     46 exit
     38 g++
     21 sudo
     19 man
     19 cat
     14 echo
     10 mv

Yay ls! I type it a lot, even when I don't want to. It just comes out. Sort of like whenever I go to type google, it expands itself to google.com<enter>. Very annoying at times.

---

### Post by blackgr on 2009-05-05
66 ls
     56 cd
     44 cat
     42 sudo
     30 hachoir-metadata
     18 ps
     17 man
     12 mplayer
     10 ssh
      7 if

---

### Post by chucky chuckaluck on 2009-05-05
lately, it's been **pacman -S kdemod** followed by **pacman -Rs kdemod** five minutes later.

---

### Post by benj1 on 2009-05-05
i only seem to have one entry

1 rm -rf /

:)

seriously

     45 cd
     39 man
     32 tnote
     22 sudo
     21 emacs
     15 aptitude  #not sure why ??? don't use aptitude
     14 apt-cache
     13 play  #alias for randomplay
     13 less
     13 ipy   #alias for ipython

---

### Post by wsonar on 2009-05-05
ls
cd
cp
rm 
ssh
gedit
nano
apt-get
mkdir
chmod

---

### Post by happysmileman on 2009-05-05
```
174 cd
    111 ls
     90 sudo
     48 ./kdesvn-build
     46 grep
     31 nano
     30 rm
     30 echo
     30 cat
     26 make
```

Or (using second command in OP post):
```
160 cd
    111 ls
     78 sudo
     46 grep
     39 ./kdesvn-build
     31 nano
     30 cat
     27 echo
     26 rm
     26 make
```

Not sure why this difference is there, but though I'd post both

---

### Post by dmazzone on 2009-06-23
non-root:
    108 vim
    103 tweet
     69 sudo
     29 man
     12 ls
     11 echo
     10 cd
      9 vnc_server.sh
      9 locate
      6 wget

root:
      7 ls
      4 exit
      3 smbpasswd
      3 man
      3 cd
      2 cat
      1 while
      1 touch
      1 sudo
      1 rm

---

### Post by Tibuda on 2009-06-23
```
     65 make
     64 ls
     34 bzr
     32 exit
     25 sudo
     22 ./G
     20 cd
     12 rm
     10 update
      9 man
```
G is an application I'm working on, and update is an alias.

---

### Post by JordyD on 2009-06-23
```
    190 sudo
    187 exit
    125 pacman
     49 su
     46 man
     44 cd
     25 ls
     20 locate
     18 ps
     17 alias
```

I know I already posted here before, but whatever.

---

### Post by SuperSonic4 on 2009-06-23
```
221 sudo
    100 cd
     87 ffmpeg
     48 y
     39 ls
     36 ping1
     36 cp
     26 mv
     22 man
     18 wget
```

y is an alias for yaourt -  a frontend for the AUR
ping1 is pinging google

---

### Post by aj_ on 2009-06-23
134 sudo
116 cd
70 startx
50 vim
46 mv
37 ls
34 scp
32 rm
24 pacman
21 cmus

---

### Post by chucky chuckaluck on 2009-06-23
haven't done this in a while...

    451 sudo
     91 nano
     62 cd
     54 htop
     53 mc
     29 su
     28 ls
     21 feh
     18 cplay
     14 ./change-type.sh  (i guess i've changed the hydroxygen icon setup a few times)

as root:
     71 pacman
     40 nano
     31 dimmo  (this is an alias i use for shutting off the damn light sensor on my laptop)
     13 cd
     10 reboot
     10 gpasswd
      6 mv
      6 ls
      5 rm
      4 mc

---

### Post by RandomJoe on 2009-06-23
Interesting...

This machine:
```
    121 ls
     51 cd
     33 vim
     23 exit
     18 mv
     16 cat
     15 ssh
     11 ./rip
     11 mplayer
     11 chmod
```
I wouldn't have thought 'exit' would be so high!  Mplayer because I encode all my movies on here.  'Rip' is a script I wrote to rip the DVDs.

The other often-used machine:
```
     87 cd
     76 ls
     41 exit
     34 uptime
     34 joe
     26 vim
     23 sudo
     21 ./datalogger.py
     11 less
      6 tail
```
...and there's 'exit' again!  Guess I don't like to keep windows open when not in use...

Datalogger is a script I wrote to log my solar system's performance.  

And 'uptime' scores so high because the blasted 'wview' process that talks to my weather station keeps locking up.  I periodically check 'uptime' and see if the system load is at 1.  If so, time to restart wview.  I really ought to automate that!  Or maybe try to figure out what's wrong with it...!

---

### Post by cmay on 2009-06-23
```
1}'|sort|uniq -c | sort -n | tail | sort -nr
     67 ./error_template
     10 exit
      6 ./fil
      5 chmod
      4 sudo
      2 ls
      2 finger
      1 who
      1 w
      1 vlc--guide.sh
```
thats a surprise. 
i would have thought  to have chmod nano and gcc as the commands i used most.

---

### Post by DirtDawg on 2009-06-23
This seems like fun. Nothing terribly interesting in my results though:
```
    110 sudo
     97 ls
     55 cd
     48 aptitude
     15 vim
     14 cat
     13 history
     11 gksu
     10 firefox
      9 lsusb
```

---

### Post by dioltas on 2009-06-23
Great idea for a thread! Here's mine:

  [B]  234 sudo
     63 ls
     59 man
     58 vi
     49 ncmpcpp
     48 cd
     26 ./scripts/wihm
     24 ibam
     23 alsamixer
     20 wicd-client
[/B]

---

### Post by sim-value on 2009-06-24
>  44 sudo
     21 gpg
     18 ls
     17 cd
     11 gcc
     11 firefox
     10 man
      9 apt-cache
      7 ./system
      7 gedit




^^ lol sudo

---

### Post by xinel on 2009-08-02
153 sudo
     74 cd
     73 ls
     30 ssh
     20 ifconfig
     19 ping
     18 clear
     13 mcrypt
     10 man
      6 ps

---

### Post by Jimleko211 on 2009-08-02
33 sudo
      6 startx
      5 pacman
      5 obmenu
      5 gedit
      4 nano
      4 banshee-1
      3 tar
      3 rtorrent
      3 ls

---

### Post by JillSwift on 2009-08-02
75 ls
     49 cd
     39 sudo
     35 mplayer
     26 ps
     22 find
     21 exit
     18 gnome-mplayer
     15 rm
     15 man

Seems I watch a lot of video, after spending an inordinate amount of time looking for it ;)

---

### Post by MikeTheC on 2009-08-02
sudo

ls

ssh

ln


That's about all I can think of.

---

### Post by slakkie on 2009-08-02
It is a top 9 for me, since i use the zsh_history file which also stores something about sessions (which is the 110 items of : ).

```

cat .zsh_history | awk '{print $1}' |sort|uniq -c | sort -nr | head -10
    110 :
     92 cd
     77 rm
     73 mplayer
     66 sudo
     42 aptitude
     41 cat
     32 dpkg
     29 vi
     23 ssh

```

---

### Post by Tipped OuT on 2009-08-02
sudo apt-get
top
history

---

### Post by Sublime Porte on 2009-08-02
```

     94 ls
     69 sudo
     64 valac
     59 cd
     55 leafpad
     33 ./textview
     32 df
     26 vi
     20 sudo
     15 cat

```

---

### Post by iman1000000 on 2009-08-02
62 x #Starts X, I boot into tty
     23 sudo
     22 ls
     21 man
     21 exit
     18 screen
     18 htop
     17 ssh
     16 cd
     15 paci #sudo aptitude install

---

### Post by Ian dewhurst on 2009-08-02
29 sudo
14 exit
3 cd
2 xf86-video-ati
2 lspci
2 history
1 wget
1 udo
1 prism
1 lxdream

---

### Post by Parvo on 2009-08-03
107 ls
     68 cd
     44 sudo
     40 exit
     35 ps
     28 nano
     20 whereis
     20 sh
     17 screen
     14 clear

---

### Post by cariboo on 2009-08-03
109 sudo
     60 cd
     49 ls
     25 whois
     17 ssh
     17 ps
     16 mc
     14 gpg
     13 ping
     11 dmesg

---

### Post by Viva on 2009-08-03
98 sudo
     49 glxgears
     19 python
     17 killall
     15 trayer
     10 cd
      8 wget
      7 lynx
      7 clear
      6 playonlinux

---

### Post by ahmatti on 2009-08-03
```

  80 ls
  71 cd
  37 sudo
  29 emacs
  21 python
  12 R
  10 prosper
  10 mmtek
   9 cat
   8 sorkka

```

Few commands are my own aliases for connecting to ssh servers ...

---

### Post by amitabhishek on 2009-08-03
ls
sudo
ping
ssh
ps
kill
mount
nano 
mount
mkfs

---

### Post by saintthomas on 2009-08-03
38 exit
     25 remban
     23 orban
     15 exenable
      9 cd
      4 wget
      4 clear
      4 apt-get
      3 mkdir
      3 ls
remban, orban and exenable are my personal commands!

---

### Post by coldReactive on 2009-08-03
```
sudo apt-get update
```

```
sudo apt-get install
```

bleh. Not much else, as all my other commands are through Start-up apps or something. I'm not really one who likes the command line.

---

### Post by scragar on 2009-08-03
Modified version of the list since my switch to arch.

```
     16 sudo
     14 nano
     14 lsl (alias for "ls -lh" list files and folders in human readable long format)
     14 locd (function locates a file/folder and CDs to it/it's directory)
      8 g+sdl (alias for "gcc -g -Wall -I/usr/include/SDL -lSDL" AKA compile with SDL libs)
      6 pgtk (php-gtk wrapper)
      6 p++ (alias for "sudo pacman -Syu" same as "apt-get update; apt-get upgrade")
      6 p+ (alias for "sudo pacman -S" same as "apt-get install")
      5 p- (alias for "sudo pacman -Rd" same as "apt-get remove")
      1 p-- (alias for "sudo pacman -Rs" same as "apt-get --purge autoremove")

```
Oh, and I've emptied my list a few times when I experiment with something and wind up with a few hundred entries of my history that go something like```
nano foo
./foo
nano foo
./foo
nano foo
```You get the idea.

---

### Post by x33a on 2009-08-03
my list
```

    868 sudo
    762 ls
    418 cd
    341 ifconfig
    186 plog
    181 man
    167 htop
    143 sensors
    126 cat
    125 exit
```

i have set my history file size to 5000.

---

### Post by Viva on 2009-08-04
Just wondering, if you use sudo apt-get install something, is it registered as sudo or apt-get in history?

---

### Post by Tibuda on 2009-08-04
> **Viva said:**
> Just wondering, if you use sudo apt-get install something, is it registered as sudo or apt-get in history?

It logs the whole command (see history | tail), but the OP command counts it as "sudo".

---

### Post by tom66 on 2009-08-04
112 gcc
    109 python
    103 ./a.out
     51 cd
     25 sudo
     17 reset
      8 watch
      8 ping
      8 ls
      4 sensors

---

### Post by barnex on 2009-08-04
88 cd
     47 kate
     34 clear
     24 svn
     22 javac
     19 ls
     17 java
     16 make
     15 barnexml
     11 sudo

---

### Post by coolbrook on 2009-08-04
hot-babe

---

### Post by Viva on 2009-08-04
> **coolbrook said:**
> hot-babe

:lolflag:

---

### Post by epsolon77 on 2009-08-04
104 sudo
     94 cd
     83 ls
     34 faxstat
     20 sh
     18 cu
     14 q
      7 q}
      7 echo
      7 cp


It's a newly reformed hylafax server, hence the faxstat.  I'm actually surprised that "hylafax restart" wasn't on there considering how many times I flubbed the config files.

---

### Post by decoherence on 2009-08-04
A Mac that was imaged from another Mac that I recently set up

  11 sudo
   8 login
   6 say
   5 tail
   5 ssh
   4 mount_afp
   4 clear
   3 ping
   3 ls
   1 what's

Not sure about that last entry... pretty boring, really, though "say" has interesting uses.

---

### Post by x33a on 2009-08-05
> **epsolon77 said:**
> I'm actually surprised that "hylafax restart" wasn't on there considering how many times I flubbed the config files.

if you are using it with sudo, only sudo will show here, with the OPs command.

---

### Post by afeasfaerw23231233 on 2009-08-05
42 ping
     38 ls
     35 ifconfig
     35 dmesg
     34 nslookup
     31 cd
     27 ps
     26 sudo
     26 netstat
     25 cat

---

### Post by Tclarkie on 2009-08-05
su 
sudo 
apt-get
 man
wget
cd
chown
kill
top
ping

---

### Post by sideaway on 2009-08-05
216 sudo
     28 smbclient
     17 smbnetfs
     16 samba
     11 fusesmb
     10 rsync
     10 mkdir
      9 wine
      6 smbmount
      6 smb


Needless to say, I had trouble getting samba to work.

---

### Post by starcannon on 2009-08-05
70 sudo
     53 clear
     28 cd
     19 ls
     17 zenity
     16 scrot
     13 man
     12 echo
     11 pkill
     10 ./icon*.sh

---

### Post by xir_ on 2009-08-05
71 sudo
     45 ls
     38 gfortran-4.3
     37 ./a.out
     34 cd
     26 ssh
     19 gedit
     11 history
      9 ifort
      8 more


looks like i am becoming a Fortran monkey

---

### Post by matthew1471 on 2009-08-05
Mine are 

     81 ls
     57 sss
     31 cd
     28 sudo
     25 ssh
     19 cat
     17 vim
     11 man
     11 less
      9 ps

---

### Post by Anxious Nut on 2009-08-05
1. sudo nautilus
2. killall
3. ping
4. cd
5. ls
6. man
7. wget
8. apt-get
9. gcc
10. ssh

---

### Post by nothingspecial on 2009-08-05
Meaning to do this for a while -

headless box -
     117 ls
     58 cd
     54 cp
     48 sudo
     37 screen
     27 rm
     16 exit
     15 nautilus
     14 get_iplayer
     13 rtorrent

laptop (recent install)
     225 sudo
     30 server
     25 cd
     24 ls
     12 squeezeslave
     12 apt-cache
     10 chmod
      9 gksudo
      9 dmesg
      7 lspci

broken netbook (used for streaming video mainly)
     90 ls
     77 cd
     39 sudo
     29 mplayer
     21 mv
     17 server
     13 logout
      8 ssh
      6 rm
      6 apt-cache

netbook (used most)
     75 sudo
     71 ls
     58 cd
     54 server
     21 cat
     17 apt-cache
     16 rm
     15 ssh
     11 scp
      9 squeezeslave

"server" is an alias to ssh into my headless box.
"squeezeslave" is a command line streaming music client used in conjunction with [[COLOR="Blue"]squeezecenter[/COLOR]]("http://wiki.slimdevices.com/index.php/SqueezeCenter").

---

### Post by BslBryan on 2009-08-05
224 sudo
     50 gdmthemetester
     46 export
     31 cd
     20 gksudo
     18 echo
      9 rm
      8 tar
      7 wget
      5 ssh

---

### Post by coolbrook on 2009-08-06
> **Viva said:**
> :lolflag:

A traumatizing Edubuntu experience to say the least.

---

### Post by jjgomera on 2009-08-06
123 python
     54 ls
     50 cd
     31 sudo
     27 curl
     11 locate
      9 man
      9 ls
      9 aptitude
      8 mpc

---

### Post by Possum Films on 2009-08-06
[LIST=1]
[*]sudo
[*]mplayer
[*]espeak
[*]cd
[*]exit
[*]ls
[*]wget
[*]screen
[*]make
[*]xbill
[/LIST]
I was actually quite surprised at what came up.

---

### Post by fennec_fox on 2009-08-06
179 ssh
  95 ls
  25 cd
  22 exit
  17 hostname
  16 df
  14 pwd
  14 cat
  12 mv
  10 sftp

---

### Post by idlehands on 2009-08-06
76 ls
     44 sudo
     39 cd
     21 exit
     17 screen
     14 rm
      9 mv
      8 ps
      8 df
      7 vi

---

### Post by SolarisSDK on 2009-08-07
229 sudo
     16 man
     12 nslookup
     12 cd
      8 htpasswd
      7 xfwm4
      6 ls
      6 grep
      6 g++
      6 ar

---

### Post by del_diablo on 2009-08-08
62 sudo
     44 make
     31 cmake
     23 svn
     17 cd
     12 p7zip
     10 ./dungeonhack
      9 xset
      9 aticonfig
      8 unrar

---

### Post by aaaantoine on 2009-08-08
If anyone can tweak the script to show the next parameter when sudo is the command, that would be maybe a bit more useful.

Here's mine:
    180 sudo
    131 yaourt
    118 ls
     59 timidity
     48 cd
     39 pacman
     35 ./restart-plasma
     33 awk
     26 sed
     16 nano

I'd have you guess what distro I'm using, but it's already in my sig. ;)

---

### Post by thunk77 on 2009-08-08
241 sudo
     44 ls
     37 uptime
     25 gksudo
     22 cmus
     14 killall
     14 cd
      7 wget
      6 man
      6 clear

---

### Post by aaaantoine on 2009-08-08
> **aaaantoine said:**
> If anyone can tweak the script to show the next parameter when sudo is the command, that would be maybe a bit more useful.

I ain't no slouch. :P

```
history | awk '{ if ($2 == "sudo") {print $3} else {print $2} }' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
```

   131 yaourt
    118 ls
     83 pacman
     66 nano
     59 timidity
     48 cd
     35 ./restart-plasma
     33 awk
     26 sed
     26 netcfg

You could also do this for more accurate information:
```
history | awk '{ if ($2 == "sudo") {print $2 " " $3} else {print $2} }' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr
```

    131 yaourt
    118 ls
     59 timidity
     50 sudo nano
     48 cd
     44 sudo pacman
     39 pacman
     35 ./restart-plasma
     33 awk
     26 sed

So you see what the actual command was you issued with sudo instead of just "sudo".

---

### Post by wingnux on 2009-08-08
73 cd
     71 sudo
     38 ls
     29 wine
     17 aacgain
     14 killall
     11 env
     10 ffmpeg
      9 rm
      9 make

---

### Post by gabo.cr on 2009-08-08
128  sudo
120  ls
109  cd
46   exit
23   ping
11   top
9    mysql
9    ifconfig
6    ipconfig (?)
5    mount

I always seem to confuse "ifconfig" with "ipconfig" !

**Shame on me !!!**

:confused:

---

### Post by j.bell730 on 2009-08-08
```
     128 cp
     95 ls
     58 mv
     43 sudo
     33 cd
     26 find
     15 rm
     13 rename
     11 history
     10 man
```
Wow, I like the command!

---

### Post by SlugSlug on 2009-08-08
my week old system toaday !! (happy birthday box)

     92 sudo
     79 ls
     65 cd
     19 mv
     18 df
     14 ps
     13 rm
      9 vi
      9 pkill
      9 du

---

### Post by mrgnash on 2009-08-09
51 cd
44 ls
36 vim
35 sudo apt-get
19 unrar
19 cmus
17 mv
15 gnome-mplayer
14 mencoder
14 alsamixer

---

### Post by lethalfang on 2009-08-09
76 ssh
     69 ll (alias for ls -lh)
     60 cd
     51 echo
     26 cat
     20 scp
     16 nano
     14 exit
     10 ~/rna_folding/count_bases.sh (script to count the different bases in an RNA molecule)
     9 wc


I think the reason SSH is so high up there is that I've been out of the country for 2 weeks, and I often log into my computer at home, in my office, and the computing clusters, etc.

---

### Post by frt975 on 2009-08-09
16 sudo
      7 ./configure
      7 cd
      5 make
      4 blackbox
      2 hg
      2 compiz
      2 apt-cdrom
      1 wget
      1 The

---

### Post by Redsandro on 2009-08-21
Nice command line construction to get this list!
This is on my media center, I don't use the command line that much.

```
    123 ls
    105 cd
     49 sudo
     16 wine
     15 ping
     13 exit
     12 cat
     11 hl
     11 chmod
     10 umount
```

---

### Post by ks07 on 2009-08-23
After reinstalling ubuntu to upgrade to 9.04 and messing around with the new install for a few months now, I have a different set of results (shock-horror :P)
```
    136 sudo
     56 exit
     45 cd
     17 man
     12 shutdown
     11 make
     10 gksudo
      6 locate
      6 fdisk
      5 sauerbraten

```

---

### Post by hobo14 on 2009-08-23
165 java
    102 javac
     43 cd
     40 svn
      9 sudo
      9 ls
      5 ./runtests
      4 make
      2 vn
      2 runtests

---

### Post by RabbitWho on 2009-08-23
16 sudo
      4 echo
      2 lm_sensor
      1 wvdial
      1 up
      1 sensors
      1 lm_sensors
      1 kcontrol
      1 history
      1 cd


Ha ha, I'm such a newb.. some of those aren't even real commands.

---

### Post by TheNessus on 2009-08-23
my most used commands are

cd
cd Desktop
sudo cp .conkyrc /home/*****

I got two of this, one in the home folder and one of the desktop, for backup and editing.
but now I've perfected my conky, so there's no need for this. Or the command line.

---

### Post by gradinaruvasile on 2009-08-23
One of my terminals:

```
     169 sudo
     30 SystemUpdate
     28 ls
     19 ping
     19 killall
     18 locate
     18 grdc
     17 cd
     16 ChromiumUpdate
     13 alsamixer
```

SystemUpdate = sudo apt-get update && sudo apt-get dselect-upgrade
ChromiumUpdate = a script that fetches the latest Chromium build from their buildbot, unpacks it and makes a menu link

---

### Post by stanca on 2009-08-23
Same as in the beginning almost:
sudo
apt-get
update
upgrade
dpkg -i
sudo gedit
scrot
exit
;)

---

### Post by mintochris on 2009-08-23
165 sudo
     55 cd
     31 ls
     21 mencoder
     19 ushare
     13 ffmpeg
     10 ssh
      9 umount
      9 rm
      9 ifconfig

Playing with converting movies for my media box has skewed mine a bit

---

### Post by Pavel1114 on 2011-10-07
151 ls
    135 cd
    111 mplayer
     76 sudo
     76 man
     47 vim
     44 rm
     38 mpc
     34 mpd
     28 aptitude

---

### Post by nothingspecial on 2011-10-07
Back to sleep.

---

