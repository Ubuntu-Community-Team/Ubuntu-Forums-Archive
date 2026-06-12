---
title: "[SOLVED] lightweight but easily configurable wm - help me choose!"
date: 2007-07-02
forum: The Cafe
---

### Post by buuntuu! on 2007-07-02
hi everybody, today i've got a difficult one (i foresee religious disputes)
(it's not really caffè, but still, see line one)

i am setting up a box for a friend of mine whom i've converted from window$.
he's a  techno-illiterate enduser, not caring much about how things work if they just work :)
the box is at the lower end: 
athlon xp-m: 1.8 GHz
192MB RAM

i want to show off with linux and prof how much faster his box will be but at the same time provide a nice GUI and make it easy to configure the desktop to his liking.

i'm sure you are getting the problem i'm in...
i personally would go for openbox which i personally use, but opening the shell for making adjustments is not an option here. with fluxbox, icewm, fvwm i do not have any experience... and xfce will be too much of a "resource hog" for swift computing i'm afraid.

want to share your expertise?

---

### Post by Rui Pais on 2007-07-02
i would suggest fluxbox ([here with a nice theme and screenshot]("http://ubuntuforums.org/showthread.php?t=320104")).

[e17 is great]("http://www1.get-e.org/Screenshots/User_Submitted/") but may be more unstable (depends on the date you pick the source)

---

### Post by buuntuu! on 2007-07-02
how about customizability? gui or cli?

---

### Post by pseudonym on 2007-07-02
> **buuntuu! said:**
> the box is at the lower end: 
athlon xp-m: 1.8 GHz
192MB RAM
If you think that machine is at 'the lower end', you should check out [this thread]("http://ubuntuforums.org/showthread.php?t=478237"). Anyway, with another stick of inexpensive RAM that machine should run straight Ubuntu quite well.

Also, it depends what you mean by 'easily configurable'. Of the window managers, [icewm]("http://www.icewm.org/") is arguably the easiest to configure. The configuration files are easy to edit and there's plenty of documentation out there on how (the GUI configurators aren't as good as simple hand-editing of icewm, believe me).

But if you want more built-in features I'd say Xfce4 is probably the best option - lighter than GNOME, and with easy-to-use GUI configuration tools. Note I say Xfce4, not the Xubuntu distribution, which has become bloated in recent releases and will run the same as GNOME on a system like that above (in which case GNOME would be better because it has more features).

I have Xfce4 running (along with [Openbox]("https://help.ubuntu.com/community/Openbox") ) on a custom install from the [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") , on
a P3 550 MHz with 384MB RAM and it runs quite nicely indeed, though of course Openbox is a little snappier.

---

### Post by cunawarit on 2007-07-02
If he is computer illiterate, I think the best choice would be not using Ubuntu at all, but opting for something like Puppy Linux. Perhaps Ubuntu + fluxbox isn&#8217;t ideal unless you set it all up for him with easy ways to mount drives, manage files, etc... With Puppy you get all of that done for you.

Yes you could use a modern distro like Etch or Feisty with Fluxbox, but I still don&#8217;t think he would get a huge speed benefits if he is coming over from Windows 98, not unless his Windows machine was truly wrecked and unusable, which thinking about it, is of course quite probable.

---

### Post by kerry_s on 2007-07-02
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Rui Pais on 2007-07-02
> **buuntuu! said:**
> how about customizability? gui or cli?

well for the cases i suggested, fluxbox has a minimal GUI for conf (fluxconf) and configuration is made with plain text files easy to edit and understand (even for some one non-tech)

for e17 everything can be configured from a GUI (and of course from the cli too). 
Check [elive distro]("http://www.elivecd.org/") too, they pick stable times of the cvs tree and make a nice debian based. They have screenshots of the guis too.

edit: a screenshot of my e17 with some config GUIs:
[ATTACH]37095[/ATTACH]

---

### Post by kerry_s on 2007-07-02
okay, that E17 shoot looks F'N sweet! are you using repos or did you compile?

---

### Post by Erik Trybom on 2007-07-02
When it comes to window managers, there's really no excuse for not trying them out and decide for yourself. Apt-get or Synaptic make the installations quick and easy (E17 is somewhat more tricky, search for the how-to). Asking on a forum won't help as everyone will just name their favourite.

Me, I'd go for Xfce.

---

### Post by fuscia on 2007-07-02
e17 is nice and fast, but it can be a little bit  like playing fetch with a cat: sometimes, the cat will fetch, while other times, it'll just stare at you like you're a total moron.

---

### Post by init1 on 2007-07-02
> **buuntuu! said:**
> hi everybody, today i've got a difficult one (i foresee religious disputes)
(it's not really caffè, but still, see line one)

i am setting up a box for a friend of mine whom i've converted from window$.
he's a  techno-illiterate enduser, not caring much about how things work if they just work :)
the box is at the lower end: 
athlon xp-m: 1.8 GHz
192MB RAM

i want to show off with linux and prof how much faster his box will be but at the same time provide a nice GUI and make it easy to configure the desktop to his liking.

i'm sure you are getting the problem i'm in...
i personally would go for openbox which i personally use, but opening the shell for making adjustments is not an option here. with fluxbox, icewm, fvwm i do not have any experience... and xfce will be too much of a "resource hog" for swift computing i'm afraid.

want to share your expertise?
TWM. Very configurable. I don't think it works to well in Ubuntu though. But it is great in Slax and Vector. Try Sawfish.

---

### Post by Rui Pais on 2007-07-02
> **fuscia said:**
> e17 is nice and fast, but it can be a little bit  like playing fetch with a cat: sometimes, the cat will fetch, while other times, it'll just stare at you like you're a total moron.

> **kerry_s said:**
> okay, that E17 shoot looks F'N sweet! are you using repos or did you compile?

thanks :)
i always compile from source. And i always do (or adapt/mix from others) the themes i use.
The point in using a pre-alpha like e17 is deal directly with cvs source. Nothing is set, a simple API change can make it unusable. The great thing of cvs is that one can pick the tree source in any specific time. 
So if today updates are broken but yesterday work smooth get again yesterday tree, and seat for a while with the thing on your lap doing rrrr rrrr (try again a weak later, to see if the wild beast is closer again to domestic animal :lol:... seems fuscia and i share the love for cats :))
Btw, now is stable and well behaved. 

here a link to an how-to that links to a superb installation script (from the one develop and maintainer of e site):
[http://ubuntuforums.org/showthread.php?t=97199](http://ubuntuforums.org/showthread.php?t=97199)
is a little out-dated, but last posts usually have some tips on what needs to be changed.



here 2 more screenies of mine (vanitas, vanitas):
[ATTACH]37131[/ATTACH][ATTACH]37132[/ATTACH]

---

### Post by fuscia on 2007-07-02
qvwm is pretty fast. there's not much to configure, either. you right-click and open up an xterm to launch an app. you can do the wallpaper with feh, or leave it 'do it until you go blind' blue. it looks like windows 95 (almost like my beloved windows ME). flwm and 9wm are similar in that there aren't a whole lot of options, but they're fast and rock solid.

---

### Post by kerry_s on 2007-07-02
> **Rui Pais said:**
> thanks :)
i always compile from source. And i always do (or adapt/mix from others) the themes i use.
The point in using a pre-alpha like e17 is deal directly with cvs source. Nothing is set, a simple API change can make it unusable. The great thing of cvs is that one can pick the tree source in any specific time. 
So if today updates are broken but yesterday work smooth get again yesterday tree, and seat for a while with the thing on your lap doing rrrr rrrr (try again a weak later, to see if the wild beast is closer again to domestic animal :lol:... seems fuscia and i share the love for cats :))
Btw, now is stable and well behaved. 

here a link to an how-to that links to a superb installation script (from the one develop and maintainer of e site):
[http://ubuntuforums.org/showthread.php?t=97199](http://ubuntuforums.org/showthread.php?t=97199)
is a little out-dated, but last posts usually have some tips on what needs to be changed.



here 2 more screenies of mine (vanitas, vanitas):
[ATTACH]37131[/ATTACH][ATTACH]37132[/ATTACH]


Well no E17 for me, the repo gives me dependency hell, it's sweet, but not worth that much work compiling. i had the main setup installed i was in there but i couldn't install all the good stuff, so i just said forget it and uninstalled all of it. :(

---

### Post by IYY on 2007-07-02
If he adds just one more stick of RAM, even Gnome (default Ubuntu) will work very fast on it. Even without, Xubuntu should be perfectly good. It really isn't a slow computer!

---

### Post by Rui Pais on 2007-07-02
> **kerry_s said:**
> Well no E17 for me, the repo gives me dependency hell, it's sweet, but not worth that much work compiling. i had the main setup installed i was in there but i couldn't install all the good stuff, so i just said forget it and uninstalled all of it. :(

Do you followed the how-to on the links of my post?

Well, but i agree it can be a little annoying to get it at first (after compiled/installed requires only a minimum work).
 
Another way is to use debs made for Ubuntu, and as long as it work avoid updates (or keep backups of the previous debs in case of worst):
[How To Install Enlightenment E17 The Easy Way ]("http://ubuntuforums.org/showthread.php?t=319336")

---

### Post by kerry_s on 2007-07-02
> **Rui Pais said:**
> Do you followed the how-to on the links of my post?

Well, but i agree it can be a little annoying to get it at first (after compiled/installed requires only a minimum work).
 
Another way is to use debs made for Ubuntu, and as long as it work avoid updates (or keep backups of the previous debs in case of worst):
[How To Install Enlightenment E17 The Easy Way ]("http://ubuntuforums.org/showthread.php?t=319336")

I'm on debian, i used the unstable repo, all cvs stuff. i can make it work, i logged into it and all, but i couldn't install the extra features(e17-extras,e17-desktop,etc...) just plain e17 installed just fine, but i couldn't get the file manger, the stuff to edit my menus, etc...
i'll proably try again later. i was also reading the site and it say's it's still alpha, the last time i used it, it was alpha, seems like it's been alpha forever. i'm kinda thinking i really don't feel like using alpha, aka:buggy, stuff right now, i just got this old beast(vaio 450mhz 256ram) to it's sweet spot, where everythings working great. i'll think on it.

---

### Post by buuntuu! on 2007-07-03
**@ IYY:** you are perfectly right!
when i first saw this box perform i labeled it as "low system specs" and was shocked myself finding out that the processor was faster than my own ;) but still, with 192MB RAM and the way it slugged with xp i just couldn't imagine what happened next: as i waited for replies i gave  it a shot with the standard xubuntu install  (just for the fun of it) and the box really flew! (compared to a totally infested xp that is).
 ease of use and eyecandy is also there, so i think i'll pass it over to my friend like it is...
added soundjuicer, deluge, iceweasel and amule, now he's ready to go!
cleaning out the dust i found the empty slot for additional ram, so i'll suggest a little investment and a perfectly fine box will have come out of this :)
viva gnu/linux!

---

### Post by graabein on 2007-07-03
I did the same with an old box of mine. No way it could perform with XP but it was just great with Xubuntu.

---

