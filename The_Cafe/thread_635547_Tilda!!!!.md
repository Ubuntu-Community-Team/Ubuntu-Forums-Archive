---
title: "Tilda!!!!"
date: 2007-12-08
forum: The Cafe
---

### Post by blithen on 2007-12-08
Holy crap! Does anyone else use Tilda as their main terminal.
I use it a TON considering I hate useless open windows, (Such as CMUS) I mean every other music player out there doesn't have to be shown down below 24/7 and now CMUS doesn't either!!! That's why I use it.
Anyone else out there?

---

### Post by igknighted on 2007-12-08
> **blithen said:**
> Holy crap! Does anyone else use Tilda as their main terminal.
I use it a TON considering I hate useless open windows, (Such as CMUS) I mean every other music player out there doesn't have to be shown down below 24/7 and now CMUS doesn't either!!! That's why I use it.
Anyone else out there?

The concept for tilda is great, but I've always found its way to buggy in practice to be useful.  I've found Yakuake to be a much much better drop-down terminal.

---

### Post by crimesaucer on 2007-12-08
> **blithen said:**
> Holy crap! Does anyone else use Tilda as their main terminal.
I use it a TON considering I hate useless open windows, (Such as CMUS) I mean every other music player out there doesn't have to be shown down below 24/7 and now CMUS doesn't either!!! That's why I use it.
Anyone else out there?

I had buggy problems when I first installed it... devils pie and yakuake also were strange.


Then I used Compiz Fusion and this thread for an embedded terminal in both gnome and xfce: [http://ubuntology.com/2007/10/25/howto-embedded-terminal-on-your-gutsy-desktop/](http://ubuntology.com/2007/10/25/howto-embedded-terminal-on-your-gutsy-desktop/)


...but now that I'm not using Compiz Fusion, I just have the embedded look (but I still have a button on my task panel):

Large View: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-3-2.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-3-2.png)
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-3-1.png[/IMG]


I might try to install it again because I did like the drop down terminal and the way you could just use a simple hot-key binding to start it and close it.

---

### Post by dnns123 on 2007-12-08
I love Tilda, but sometimes, the default Terminal is better...

---

### Post by n3tfury on 2007-12-08
i found it buggy also, and it looked like crap, but being so buggy i never bothered finding out if its appearance could have been modified.

---

### Post by Kingsley on 2007-12-08
Yakuake is much better.

---

### Post by n3tfury on 2007-12-08
how is it "much better"

---

### Post by Matt Yun on 2007-12-08
I love Tilda, but agree that Yakuake (KDE) is better.  I had to install Tilda from cvs because the default Gutsy package doesn't work.

---

### Post by crimesaucer on 2007-12-08
> **n3tfury said:**
> i found it buggy also, and it looked like crap, but being so buggy i never bothered finding out if its appearance could have been modified.

Just tried it again... same thing as last time. Buggy, multiple config files being used at the same time... not saving things correctly... showing only a blank white screen when I took animations off... then when putting animations back on... it still only showed the white screen.


Buggy drop down effect... didn't like the fact there was no "embedded" option. And I didn't like the effect of the borders around tilda... 100% transparent should be completely showing nothing.


It could be really cool, but I preferred the Compiz embedded terminal... and since I have stopped using compiz, I guess I'll try devilspie again.

---

### Post by Gadren on 2007-12-08
I love Tilda, and although I currently use KDE and Yakuake, it's a great program.

---

### Post by n3tfury on 2007-12-08
yeah, that's the problems i had - it wasn't transparent like was claimed and the drop down effect in general was NOTHING like the Q3 console.  i still play Q3 to this day so i know how it "feels" and looks like.  i was so disappointed because i really wanted to like this.

---

### Post by kungfooguru on 2007-12-14
[Tilda 0.9.5]("http://tilda.sf.net") was just released. While I admit it probably didn't fix all the bugs (ok, it didn't), it is much better now. 

Please check it out and let me know if you have any problems.

Tristan

---

### Post by toupeiro on 2007-12-14
I love tilda!  I use it constantly.  I have noticed bugs usually on startup, but reloading it manually usually stabilizes it, and it stays stable after that.

---

### Post by smartboyathome on 2007-12-14
I liked Tilda when I used it, but am now considering using Guake instead.

---

### Post by blithen on 2008-01-03
Can someone make me a deb of the newest tilda?
I can't get it to compile right..

---

### Post by ticopelp on 2008-01-03
I did like tilda, even though I ended up using yakuake because it was better behaved and just seemed to work more smoothly. 

I use yakuake for background tasks I don't need to monitor, like big apt-gets, and the regular terminal for doing more lengthy CLI work. The fact that you can't easily cut and paste with keyboard shortcuts in yakuake is the big thing stopping it from being my main terminal. That and I often tend to hit the ~ key on accident...

---

### Post by notwen on 2008-01-03
I use tilda for my main term.  No more eterm/xterm windows all over the place.  One centralized window that I can hide/unhide works for me. =]  I wish they would fix the transparency bug, other than that I'm a happy camper.

---

### Post by Perfect Storm on 2008-01-03
> **blithen said:**
> Can someone make me a deb of the newest tilda?
I can't get it to compile right..

```

sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install build-essential checkinstall
sudo aptitude install gettext flex libgtk2.0-dev libwxgtk2.6-dev libglade2-dev libvte-dev libconfuse-dev libx11-dev libglib2.0-dev



cd ~/Desktop
wget http://downloads.sourceforge.net/tilda/tilda-0.9.5.tar.gz?modtime=1197518186&big_mirror=0
tar zxfv tilda-0.9.5.tar.gz
cd tilda-0.9.5
./configure
make
sudo checkinstall

```

---

### Post by herbster on 2008-01-03
Just started using Tilda, really really liking it! I had so many terminals open all the time on each workspace before, Tilda really makes things clean and easy. Haven't encountered any bugs I can think of.

Is there any terminal whose transparency is not the desktop background? I mean, transparency shows whatever is behind the terminal instead of the doggone wallpaper.

---

### Post by Perfect Storm on 2008-01-03
Tilda 0.9.5 supports compiz-fusion, so it's real tranparency.

---

### Post by Hells_Dark on 2008-01-04
I love tilda, but i use it because of its desktop integration. I never hide it.
And that's always the same apps that are running in it, i have no prompt.
By the way, i will try the new one instead of my patched tilda for transparency :)

---

### Post by herbster on 2008-01-04
> **Artificial Intelligence said:**
> Tilda 0.9.5 supports compiz-fusion, so it's real tranparency.

Is real transparency possible sans compiz? ie., With just flux or what have you.

---

### Post by Perfect Storm on 2008-01-04
I dunno with fluxbox - I'm diehard gnome, maybe someone else can answer that question.

Sorry.

---

### Post by smartboyathome on 2008-01-04
I don't use tilda anymore, I use guake. It is very nice. :)

---

### Post by blithen on 2008-01-04
> **Artificial Intelligence said:**
> ```

sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install build-essential checkinstall
sudo aptitude install gettext flex libgtk2.0-dev libwxgtk2.6-dev libglade2-dev libvte-dev libconfuse-dev libx11-dev libglib2.0-dev



cd ~/Desktop
wget http://downloads.sourceforge.net/tilda/tilda-0.9.5.tar.gz?modtime=1197518186&big_mirror=0
tar zxfv tilda-0.9.5.tar.gz
cd tilda-0.9.5
./configure
make
sudo checkinstall

```

: D Thanks. And where can I find that wallpaper, it's beautiful!!

---

### Post by Perfect Storm on 2008-01-04
1600x1200 - [http://gnome-look.org/content/show.php/Gnome+Finest+2.2.1?content=39092](http://gnome-look.org/content/show.php/Gnome+Finest+2.2.1?content=39092)

I have a modified one I made for widescreens 1680x1050: [http://polarbeardk.blogspot.com/2007/11/wallpaper-for-widescreen-part-1.html](http://polarbeardk.blogspot.com/2007/11/wallpaper-for-widescreen-part-1.html)

---

### Post by cawill on 2008-01-04
I have a problem with tilda, it seems to 'forgot' my settings, anyone else with this problem?

---

### Post by blithen on 2008-01-04
> **Artificial Intelligence said:**
> 1600x1200 - [http://gnome-look.org/content/show.php/Gnome+Finest+2.2.1?content=39092](http://gnome-look.org/content/show.php/Gnome+Finest+2.2.1?content=39092)

I have a modified one I made for widescreens 1680x1050: [http://polarbeardk.blogspot.com/2007/11/wallpaper-for-widescreen-part-1.html](http://polarbeardk.blogspot.com/2007/11/wallpaper-for-widescreen-part-1.html)

You are a helping machine!!
Thanks again.

---

