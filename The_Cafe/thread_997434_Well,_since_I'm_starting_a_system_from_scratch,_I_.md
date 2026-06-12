---
title: "Well, since I'm starting a system from scratch, I need help on apps.."
date: 2008-11-29
forum: The Cafe
---

### Post by Exershio on 2008-11-29
hey everybody, recently I decided to try out my first system from scratch (Arch Linux) and I'm loving the lack of bloat! However, I'm not used to having like no applications for my daily tasks, so I could really use some advice.

I know the basics, like firefox, pidgin, rhythmbox, etc, but what I really need help with is the basic utilities. For example, I need a TAR/ZIP extractor for one. I also could use a decent file browser (right now I'm trying out thunar, way different from nautilus. dunno if I really like it)

**So, could anybody recommend me some good and useful utilities (such as an archiver, file browser, terminal, etc) I'll need to run my computer?**

I would really prefer lightweight programs, as I'm trying to keep a minimalist system. However, I won't gimp out on programs just because they're larger than others, so keep that in mind.

P.S. Sorry if this is in the wrong section, I dunno where to really put it.

---

### Post by Rokurosv on 2008-11-29
I think you meant rar, I think there are 2 RAR compressors, a free and a non-free, for 7z there's p7zip.

Browser alternatives: Midori, Dillo. I prefer Midori cause it's super fast, since it's based of Webkit. Dillo is ok, it's pretty slim but it takes care of your web browsing needs.

Archiver: you could try File Roller or Xarchiver.

Music Player: Sonata is a good app, it need MPD though, there's also Aqualung which is very nice.

Terminal: Eterm, it's very customizable and lightweight.

---

### Post by Exershio on 2008-11-29
Thanks, I'll definitely look into all those. :)

I also just found this page, so I'm excited now hehe. Plenty of software to check out ^_^

[http://wiki.archlinux.org/index.php/Lightweight_Software](http://wiki.archlinux.org/index.php/Lightweight_Software)

---

### Post by zmjjmz on 2008-11-29
I use Xarchiver on my lightweight systems, and mrxvt is a nice tabbed lightweight terminal.
Some good file browsers to check out:
mc
worker
EmelFM
ROX
PCManFM


Unfortunately most of those can't do FTP, but for that I use gFTP.

---

### Post by chucky chuckaluck on 2008-11-30
if you're using thunar and you don't want to just use the *tar* and *unzip* commands, you can use the thunar-archive-plugin ( a seperate installation) and pacman will tell you what it needs in order to operate (squeeze is pretty good).

if you went to arch for the lack of bloat, you might want to consider using less bloated apps. for example, you might want to try cplay, or cmus, instead of rhythmbox (which you could hold onto while you;re learning the others).

---

### Post by AnLGP on 2008-11-30
I like cmus for playing music.  It didn't take that long for me to get used to the keyboard shortcuts, either.  Give it a try.

---

### Post by Exershio on 2008-11-30
> **chucky chuckaluck said:**
> if you went to arch for the lack of bloat, you might want to consider using less bloated apps. for example, you might want to try cplay, or cmus, instead of rhythmbox (which you could hold onto while you;re learning the others).

I would, but the idea of moving to CLI apps kind of puts me off. I'm used to having a GUI for my common applications (except performing some tasks, such as copying/moving files, and of course installing and removing programs, etc)

I'll have to give it a shot though.

---

### Post by oldos2er on 2008-11-30
> **zmjjmz said:**
> I use Xarchiver on my lightweight systems, and mrxvt is a nice tabbed lightweight terminal.
Some good file browsers to check out:
mc
worker
EmelFM
ROX
PCManFM


Unfortunately most of those can't do FTP, but for that I use gFTP.

 mc does ftp; don't know about the others.

---

### Post by mips on 2008-11-30
[Worker]("http://www.boomerangsworld.de/worker/") file manager & more.

---

### Post by mikjp on 2008-11-30
I use the CLI tool tar for tarballs, mp3blaster for music, xterm as terminal, midnight commander is a text mode file browser.

---

### Post by sujoy on 2008-11-30
WM: openbox/xmonad
Shell: zsh
Editor: vim
Music: mpd+ncmpc/sonata
Video: mplayer
Compression: tar,unrar,unzip
FileManager: shell
Terminal: urxvt
Browser: firefox/midori
Image: mirage,gimp
Chat: weechat,bitlbee/pidgin

others: evince,gftp,iptables,yaourt (to install from AUR),xcompmgr

---

### Post by K.Mandla on 2008-11-30
Well ...

[http://kmandla.wordpress.com/software/](http://kmandla.wordpress.com/software/)

Maybe?

---

### Post by chucky chuckaluck on 2008-11-30
> **Exershio said:**
> I would, but the idea of moving to CLI apps kind of puts me off. I'm used to having a GUI for my common applications (except performing some tasks, such as copying/moving files, and of course installing and removing programs, etc).

cplay would be better than cmus, then, for you. it's simple. you type *cplay*, it show you a list of your /home directories, you navigate to your music directory, find the song you want and hit 'enter'. pretty simple and at so less a resource cost. i use a mix of gui apps, tui apps and cli apps. there are some things i can't figure out how to do with cli apps, so i still use gui apps for those activities. if you appreciate a minimal approach, you might find yourself not so put off by terminal apps.

---

### Post by Exershio on 2008-12-01
> **chucky chuckaluck said:**
> cplay would be better than cmus, then, for you. it's simple. you type *cplay*, it show you a list of your /home directories, you navigate to your music directory, find the song you want and hit 'enter'. pretty simple and at so less a resource cost. i use a mix of gui apps, tui apps and cli apps. there are some things i can't figure out how to do with cli apps, so i still use gui apps for those activities. if you appreciate a minimal approach, you might find yourself not so put off by terminal apps.

I gave MPD + Sonata a try and so far I'm loving it. The feature to be able to kill X and still have music playing... priceless :D

Anyways, I have everything I need so far. The only bloat I have is firefox. I gave midori a try, but it crashes too much and there's no adblock yet. It looks promising though.

Using openbox, thunar, mpd + sonata, pidgin, abiword (wtf's with the tons of dependancies?), gedit, xterm, xarchiver. I'll probably need something else soon, but until then, my desktop is sexy. :D (I'll post a screenshot later... I don't have a screenshot tool yet :P)

Thanks a ton for all the help everyone.

---

### Post by chucky chuckaluck on 2008-12-01
> **Exershio said:**
> I gave MPD + Sonata a try and so far I'm loving it. The feature to be able to kill X and still have music playing... priceless :D

if you're feeling adventurous, you might want to checkout ncmpc (terminal frontend for mpd). that way, when you've killed x, you can still pick out your next playlist.

> Anyways, I have everything I need so far. The only bloat I have is firefox. I gave midori a try, but it crashes too much and there's no adblock yet. It looks promising though.

midori can pass the acid3 test, so, if you spend a lot of time at the acid3 website, it might just be the right browser for you.

---

### Post by sujoy on 2008-12-01
> **Exershio said:**
> .....
Using openbox, thunar, mpd + sonata, pidgin, abiword (wtf's with the tons of dependancies?), gedit, xterm, xarchiver. I'll probably need something else soon, but until then, my desktop is sexy. :D (I'll post a screenshot later... I don't have a screenshot tool yet :P) ......

get scrot for taking screenshots

---

### Post by Exershio on 2008-12-01
Well here's my desktop so far. Openbox + PyPanel = sexy :D

---

