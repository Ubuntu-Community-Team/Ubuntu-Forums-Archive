---
title: "[SOLVED] Any Other person having issues with Amarok"
date: 2008-01-31
forum: The Cafe
---

### Post by bigbrovar on 2008-01-31
Music is a priority on my laptop and ever since i have shited to linux .. became addicted to amarok.. it is the best music player i have ever come across.. but the problem i have been having with it is that there seem to be no way to prevent it from frequent crashes that i always experience using amarok.. there seem to be no pattern and i dont know how to prevent the next one from happening.. the sad thing is that when ever it crashes it never recovers.. not ever when i restart it .. it would take forever to load all my playlist.. and i use a core 2 duo 2.0ghz,2gb ram system which should not have any performance issues at lease not with loading playlists.. 
 i read somewhere that if u delete the amarok folder in /home/.kde/share/app and reinstall amarok things would go back to normal.. even where that is the case no sooner will amarok crash again making me to go thru the process of uninstalling and reinstalling.. there seem to be no end to the circle and it can be really frustrating.. i have tried  rythmbox ,listen,banshee,exaile and many other players.. while there are stable .. non come close to amarok when it come to feature and total music  experience.. is there anything i can do to improve the stability of amarok on ubuntu...

---

### Post by SunnyRabbiera on 2008-01-31
sometimes things are like this, each computer has its quirk.
Me I never had any issues with amarok, not one.

---

### Post by maniacmusician on 2008-01-31
> **bigbrovar said:**
> Music is a priority on my laptop and ever since i have shited to linux .. became addicted to amarok.. it is the best music player i have ever come across.. but the problem i have been having with it is that there seem to be no way to prevent it from frequent crashes that i always experience using amarok.. there seem to be no pattern and i dont know how to prevent the next one from happening.. the sad thing is that when ever it crashes it never recovers.. not ever when i restart it .. it would take forever to load all my playlist.. and i use a core 2 duo 2.0ghz,2gb ram system which should not have any performance issues at lease not with loading playlists.. 
 i read somewhere that if u delete the amarok folder in /home/.kde/share/app and reinstall amarok things would go back to normal.. even where that is the case no sooner will amarok crash again making me to go thru the process of uninstalling and reinstalling.. there seem to be no end to the circle and it can be really frustrating.. i have tried  rythmbox ,listen,banshee,exaile and many other players.. while there are stable .. non come close to amarok when it come to feature and total music  experience.. is there anything i can do to improve the stability of amarok on ubuntu...
you could try running amarok from the command line, which should produce an error for you when Amarok crashes. With that information, you can troubleshoot it further.

It works really well for me though, I hardly ever experience crashes. Maybe the reason is your excessively large playlist? Do you simply load a playlist when you open Amarok, or do you actually have your collection indexed? To do this, you go to Settings > Configure Amarok > Collection, and select the locations that you want to scan for media.  When you do this, you'll have your music neatly organized in your "Collection" tab on the left side of the window.

To make it load playlists from your collection faster, you can also use MySQL as the database backend instead of SQLite. I get noticeable speed improvements when I do that. This link shows you how to use MySQL instead of SQLite: [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

---

### Post by qazwsx on 2008-01-31
> **bigbrovar said:**
>  i read somewhere that if u delete the amarok folder in /home/.kde/share/app and reinstall amarok things would go back to normal.. 
You shold also check /home/you/.kde/share/config/
and remove  amarok related stuff


Sometimes ~/.xine gives me troubles so I delete that folder (note there might be also your tvchannels config file so don't delete that if you watch tv with your computer)

---

### Post by bigbrovar on 2008-01-31
i have over 3000 song in my library ..but am working on some of the suggestion given .. that is what makes ubuntu soooo super .. one minute u have a problem the next 3 pple are on the ready to offer their help.. there are something u never can get on windows...

---

### Post by Linuxratty on 2008-01-31
I never had any problems with amarok, never...It's been great!

---

### Post by Lostincyberspace on 2008-01-31
As was mentioned earlier I would use mysql for your collection. I have a larger playlist than you with moodbar in it and mine loads in 3 seconds or so.

---

### Post by bufsabre666 on 2008-01-31
i have almost 15000 songs in my library and i never have such problem, but i just switch to rythmnbox for its simpler interface

---

### Post by Christmas on 2008-01-31
You can try to install a clean version of Amarok, the latest stable release (1.4.8 from [their website](http://amarok.kde.org)). First, uninstall the version you have:
```
sudo apt-get remove --purge amarok
```
Next, delete all the remaining configuration files:
```
rm -r ~/.kde/share/apps/amarok
rm ~/.kde/share/config/amarokrc
```
Install the development dependencies needed to compile Amarok:
```
sudo apt-get build-dep amarok
```
Untar Amarok source, go to its directory, compile and install it:
```
./configure
make
sudo make install
```
This version shouldn't cause any crashes (hopefully).

---

### Post by bigbrovar on 2008-01-31
> As was mentioned earlier I would use mysql for your collection. I have a larger playlist than you with moodbar in it and mine loads in 3 seconds or so. am trying to use myqql with amarok but when i try to configure it i get this [B]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
[/B]

i dont know what to do next....
> 
You can try to install a clean version of Amarok, the latest stable release (1.4.8 from their website). First, uninstall the version you have:
Code:

sudo apt-get remove --purge amarok

Next, delete all the remaining configuration files:
Code:

rm -r ~/.kde/share/apps/amarok
rm ~/.kde/share/config/amarokrc

Install the development dependencies needed to compile Amarok:
Code:

sudo apt-get build-dep amarok

Untar Amarok source, go to its directory, compile and install it:
Code:

./configure
make
sudo make install

This version shouldn't cause any crashes (hopefully).

thanks man am working on that hope it helps ...

---

### Post by bigbrovar on 2008-01-31
when i typed sudo apt-get build-dep amarok in amarok i got this 
 Build-dependencies for amarok could not be satisfied.

---

### Post by Christmas on 2008-01-31
Install the essential ones manually:
```
sudo apt-get install kdebase-dev kdelibs4-dev libmusicbrainz4-dev libxine-dev libtag1-dev libtagc0-dev build-essential libperl-dev libqt3-dev
```
These aren't all, so if when you issue './configure' it might complain about some other development libraries. Search for them and install them too.

---

### Post by bigbrovar on 2008-01-31
thanks man i will try that

---

### Post by Xbehave on 2008-01-31
i have really issues with amarok, its a windows like program inthat it runs fine for agers then gets weird for a few days for no reason. compiling amarok from source may help, however most of their development is on amarok2

i think investigating using mysql is something to look into as compiling from source can bring its own problems.

do you have mysql installed?

---

### Post by swoll1980 on 2008-01-31
How is it the best if it crashes all the time? Sometmies I think we are fooling ourselves.

---

### Post by maniacmusician on 2008-01-31
> **bloor75 said:**
> How is it the best if it crashes all the time? Sometmies I think we are fooling ourselves.
If you'd read the responses, you would have noticed that most people don't have such a problem. This would logically indicate that the problem has to do with something on the OP's machine. That means there's either an obscure bug at work, or there's something wrong with the OP's configuration, an issue that should be solvable. One bug that doesn't happen for most people doesn't mean that the application is bad. It has the most popular available feature set among FOSS applications.

---

### Post by swoll1980 on 2008-01-31
The post is directed to the person with the issue. How can he/she think it's the best if it crashes al the time? Not to everyone that uses it. If you used it and it didn't crash all the time I could see how it could be the best

---

### Post by swoll1980 on 2008-01-31
The reason I say this in the first place is because I have convinced my self that firefox is better than IE7 but it crashes every 15 minutes yet I have never had a crash on IE all the way back since 98-vista not once has IE ever crashed on me. So how can it be better? Am I fooling myself?

---

### Post by Christmas on 2008-01-31
When I used Firefox on Kubuntu 6.06 I had no crashes at all. Now I use Konqueror and no crashes at all. If you think IE is more stable, why don't you use it?

---

### Post by bigbrovar on 2008-02-01
Hey  i would like to say a big thanks to everybody that helped me out with suggestions.. it really helped .. and to top it all i have learn yet another lesson in the awesome ways of Linux... i was able to fix the problem i had with amarok by using mysql as my database manager... and after following guides i found here [http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html]("http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html")
everything just worked like a charm.. now my amarok is fast and very responsive than it ever was.. not even when i was in feisty was it this fast.. further more no more crashes at least non since making the changes.. everything it just the way it should be...
i dont know what to say but u guys at the Ubuntu forums really made my day.. its pple like u that make Ubuntu thick.. Now i can use the greatest piece of code ever developed for playing music without hassle.. thanks to u . :guitar:

---

### Post by Trail on 2008-02-01
> **bloor75 said:**
> The reason I say this in the first place is because I have convinced my self that firefox is better than IE7 but it crashes every 15 minutes yet I have never had a crash on IE all the way back since 98-vista not once has IE ever crashed on me. So how can it be better? Am I fooling myself?

Because 'better' is not the same as 'stable'. Stability is, of course, a factor that determines how good something is, but is not the only deciding factor.

By your measure, Notepad in windows has never crashed on me, while OpenOffice has. This means that Notepad is clearly the best text editor?

I cannot even being to compare amarok with any other music player I have tried. It is so full of features, yet not cluttered and is useable... The more I've been using it, the more features I've discovered. For me it's entirely on another level. "Rediscover your music" is actually not optimistic. And I remember amarok crashing once or twice. I don't care.

---

