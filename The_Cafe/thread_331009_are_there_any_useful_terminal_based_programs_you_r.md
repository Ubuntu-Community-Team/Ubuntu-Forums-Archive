---
title: "are there any useful terminal based programs you recommend?"
date: 2007-01-04
forum: The Cafe
---

### Post by ice60 on 2007-01-04
i really like some of the terminal based programs like irssi, tcptraceroot, p0f, mpg321, normalize etc, etc (i just saw someone mention htop in another thread which made me think about this. BTW htop is great :D)

so, are there any more terminal based programs you recommend?

[color=red]**EDIT[/color]:[color=blue] i just thought it might be a good idea if you show which switches you like to use with the programs. so, if you have already posted can you repost showing the switches you use with the program, please?[/color]**

---

### Post by aysiu on 2007-01-04
imagemagick

---

### Post by Arisna on 2007-01-04
The Vim editor can be a very powerful tool.

---

### Post by raul_ on 2007-01-04
aptitude has a terminal interface: 
```

sudo aptitude

```

---

### Post by taurus on 2007-01-04
```
wget
links2
```

---

### Post by grte on 2007-01-04
screen,  mpd/ncmpc, mutt, multitail, elinks, qalc, ncftp.

---

### Post by tagra123 on 2007-01-04
dd
top
du
df
scp
ssh
nano

Great programs when working on a remote machine using the terminal.

scrabble (for fun)

I burn all my video dvds from the commandline using dvdauthor and mkisofs

---

### Post by ~LoKe on 2007-01-04
+1 for mpd/ncmpc.

---

### Post by userundefine on 2007-01-04
I just learned **screen** and I must say it's a godsend.  Makes you want to do so much more from the terminal.  Go screen!

---

### Post by kuja on 2007-01-04
sed, uptime, lsb_release, cut, dpkg -S, dpkg -L, slocate, find, startkde ;)

---

### Post by riven0 on 2007-01-04
Can't believe no one has recommended Lynx yet. Awesome web browser!

---

### Post by Somenoob on 2007-01-04
"file", "vi" and of course most programs with networking capabilities.

---

### Post by grte on 2007-01-04
> **riven0 said:**
> Can't believe no one has recommended Lynx yet. Awesome web browser!

It's certainly good, but a bit oudated.  I would recommend elinks or links2, which have already been mentioned, over it.

---

### Post by tbroderick on 2007-01-04
Besides the ones already mentioned; tagger  (id3tag editor), cmus (music player), wget-queue  (perl script to create a download queue), hnb (hierarchical notebook), bsd-games (text based games), cdrecord (burn cd's), abcde (cd ripper), gramofile (record vinyl records), rtorrent (torrent downloads), mc (file manager), bitlbee (instant messenger), snownews (rss reader), nethack (dungeon game), and bash of course. Bash is really usefull for one-liners and such;

```
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$i" && oggenc -q 4 audiodump.wav -o "`basename "$i" .wma`.ogg"; done; rm -f audiodump.wav 
```

---

### Post by JoeC21 on 2007-01-04
+2 for mpd/ncmpc

---

### Post by TLE on 2007-01-04
+ 1 for cmus as a music player. Whats even better is that as of Edgy it is in repo's.

---

### Post by fuscia on 2007-01-04
pine mail is great - [http://www.washington.edu/pine/](http://www.washington.edu/pine/)

saved my butt once. i somehow screwed up X and couldn't figure out how to undo the damage, so i decided to reinstall. there were some files i hadn't backed up, but, as i could get into the console, i just used pine to email the files to myself and got them after i reinstalled. (i'm sure there's an easier way to do all that.](*,)  )

---

### Post by Kindred on 2007-01-04
screen for sure.

---

### Post by 3rdalbum on 2007-01-04
Gramofile is a good audio recording program, which works right on the terminal.

MPlay is a good curses-based MPlayer frontend.

---

### Post by nsleiman on 2007-01-04
sudo apt-get :)

---

### Post by amgeex on 2007-01-04
I have to say, mpd + ncmpc, bash, grep, awk, irssi, and most compilers, like javac, g++, etc. :D

---

### Post by jdhore on 2007-01-04
> **amgeex said:**
> I have to say, mpd + ncmpc, bash, grep, awk, irssi, and most compilers, like javac, g++, etc. :D

irssi FTW!! 
but i'd have to say:
top
irssi
htop
dd
apt-get

BTW, to all those who said "sudo apt-get" or "sudo aptitude", sudo and apt applications are 2 different things...

---

### Post by raul_ on 2007-01-04
I said "sudo aptitude" because it's the command to enter the aptitude "graphical" interface

---

### Post by ffi on 2007-01-04
wget
links2 (a lot faster than links or lynx)
mc (midnight commander, invaluable when x crashes again, like links2.....)

---

### Post by fuscia on 2007-01-04
elinks is also a great text browser and it's easier to get into my yahoo with it rather than with links2.

anyone mention nano and xkill yet?

---

### Post by amgeex on 2007-01-04
nano is great!

---

### Post by tbroderick on 2007-01-04
> **TLE said:**
> + 1 for cmus as a music player. Whats even better is that as of Edgy it is in repo's.

There's a newer version out  which adds  compilation tag support.

---

### Post by fistfullofroses on 2007-01-04
As you can see everyone likes their terminal based programs, but I think that Ubuntu was built for DEs. On my laptop I run Slackware, and have nothing but non-graphical Linux. Runs well. I can do anything I want on it that others would normally do.

---

### Post by amgeex on 2007-01-04
> **fistfullofroses said:**
> As you can see everyone likes their terminal based programs, but I think that Ubuntu was built for DEs. On my laptop I run Slackware, and have nothing but non-graphical Linux. Runs well. I can do anything I want on it that others would normally do.

Well, ubuntu can run equally well any of those terminal apps you may use on slackware, so I guess your statement that ubuntu was built for desktop environments isn't necessarily true. [-(

---

### Post by raul_ on 2007-01-04
> **fistfullofroses said:**
> As you can see everyone likes their terminal based programs, but I think that Ubuntu was built for DEs. On my laptop I run Slackware, and have nothing but non-graphical Linux. Runs well. I can do anything I want on it that others would normally do.

I fail to see the correlation

---

### Post by mips on 2007-01-04
As a terminal itself try [yakuake]("http://yakuake.uv.ro/")

---

### Post by pormogo on 2007-01-04
htop is awesome but doesn't run the right way in screen for me, netiher does iptraf :( I love screen with all my heart that's totally on my list. Since I'm on the topic of top I haven't seen anyone bring up iftop yet :)

---

### Post by ice60 on 2007-01-04
[color=blue]***hi, i just thought it might be a good idea if you show the switches you use with the programs you recommend; i'll edit the first post to say so. if you have already recommended something which works well with certain switches will you repost showing the whole command, please?***[/color]

---

### Post by ice60 on 2007-01-04
here are some nice netstat commands i use. they just show your network connexions. i've put them in my bash_aliases and i've posted them as they are in my bash_aliases file. to use them outside bash alias i'll show how the first one would be -
```
watch --interval=2 "sudo netstat -apn -l -A inet"
``` NOTE i took away the last ' at the very end too :) i like it because it autoupdates every 2 seconds :cool: 


```
alias net1='watch --interval=2 "sudo netstat -apn -l -A inet"'
alias net2='watch --interval=2 "sudo netstat -an --inet --inet6"'  
alias net3='sudo lsof -i'
alias net4='sudo netstat -ano -l -A inet'
alias net5='watch --interval=2 "sudo netstat -tulpan"'
alias net6='sudo netstat -tulpan'
alias net7='watch --interval=2 "sudo netstat -utapen"
```

---

### Post by ice60 on 2007-01-04
here's a nice du command which shows, in order of size, disk space usage of the directory you run it in -

du -skc * | sort -rn

NOTE: it might take a while if you run it in a directory with a lot of stuff in.

---

### Post by ice60 on 2007-01-04
whatis is a nice command. what it does is give you the man page description of a program

```
whatis opera
opera (1)            - a standards-compliant graphical Web browser


```

---

### Post by raul_ on 2007-01-04
vnstat - lets you monitor your traffic ;)

---

### Post by glabouni on 2007-01-22
> **ice60 said:**
> whatis is a nice command. what it does is give you the man page description of a program

```
whatis opera
opera (1)            - a standards-compliant graphical Web browser


```

a complementary command would be whereis:

```
NAME
       whereis - locate the binary, source, and manual page files for a command
```

```
 whereis opera
opera: /usr/bin/opera /usr/lib/opera /usr/X11R6/bin/opera /usr/bin/X11/opera /usr/share/opera /usr/share/man/man1/opera.1.gz

```

for those of you using netcat, you might want to try [cryptcat]("http://farm9.org/Cryptcat/"):
> Cryptcat is the standard netcat enhanced with twofish encryption with ports for WIndows NT, BSD and Linux. 


some more commands, some I've found in [linux.com sysadmins toolboxes]("http://www.linux.com/search.pl?tid=129") and [linux.com magic CLI]("http://www.linux.com/search.pl?tid=89"), some I already knew by myself:
slocate,curl, youtube-dl, pwgen, tripwire, iptraf, bwm-ng, iftop, lokkit, gpart, dwdiff, wuzzah, w3m, chroot, watch, monit, partimage

also check the packages moreutils and num-utils for goodies

for those of you who don't know yet about command line interface (cli) and want to learn it and the basic commands, try these links:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

---

### Post by Mateo on 2007-01-22
youtube-dl

downloads youtube movies to your harddrive, so you can watch them full screen on mplayer or watch at your convenience.

---

### Post by ice60 on 2007-04-24
i just installed mp3blaster, i tried cmus first, but i perfer this because it's so easy to get working.
[http://mp3blaster.sourceforge.net/](http://mp3blaster.sourceforge.net/)

here's an article about it
[http://www.linux.com/article.pl?sid=06/03/23/191237](http://www.linux.com/article.pl?sid=06/03/23/191237)

---

### Post by Pobega on 2007-04-24
abook for address storage.
mutt for email management.
irssi for IRC.
raggle for RSS feed reading.
mplayer for videos.
links2 for browsing (With images)
centericq for instant messages.

---

### Post by fuscia on 2007-04-24
am i on crack, or has no one mentioned mplayer yet? (too obvious?)

---

### Post by Pobega on 2007-04-24
> **fuscia said:**
> am i on crack, or has no one mentioned mplayer yet? (too obvious?)
Crack. (Scroll up)

---

### Post by fuscia on 2007-04-24
> **Pobega said:**
> Crack. (Scroll up)

uh...mplayer for music. did anyone say that yet?

---

### Post by Pobega on 2007-04-24
> **fuscia said:**
> uh...mplayer for music. did anyone say that yet?

Why bother with mplayer for music in a terminal? You could just use a normal music player :)

---

### Post by ice60 on 2007-04-24
mplayer is pretty cool in a terminal. it's just like running mpg321 -vv. you can run gaim in a terminal too i think.

---

### Post by karellen on 2007-04-24
centericq
uptime
df
du
ls
links
apt-get/aptitude
top
ps -ef
kill (!)
wget
tar
gunzip

---

### Post by Spr0k3t on 2007-04-24
I have to throw down for weechat v2.4+.  It's such an awesome IRC client very much like irssi but with a very robust plugin system.  As a software developer, I like weechat much more than I do irssi.  However, if you are not in to development, they are about the same.

---

### Post by fuscia on 2007-04-24
> **Pobega said:**
> Why bother with mplayer for music in a terminal? You could just use a normal music player :)

why not?

---

