---
title: "Firefox to KDE4?"
date: 2009-01-15
forum: The Cafe
---

### Post by Zlatan on 2009-01-15
Short question for those who knows: when Firefox3 will be ported to QT?
Thank you.

---

### Post by ghindo on 2009-01-15
I think you mean a [Qt]("http://en.wikipedia.org/wiki/Qt_(toolkit)") version of Firefox, not a KDE version.

I don't think there's any sort of roadmap for a Qt version of Firefox.  The most I've heard about it has been in an [Ars Technica article]("http://arstechnica.com/news.ars/post/20080818-nokia-helps-port-firefox-to-qt.html") a few months back.

---

### Post by Firestem4 on 2009-01-15
> **Zlatan said:**
> Short question for those who knows: when Firefox3 will be ported to KDE4?
Thank you.

I'm not sure but i was able to install Firefox 3 on my Kubuntu 8.10. I beleive i saw it in the repositories also. But i'm not sure.

In any case I used UbuntuZilla for my installation. [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Download the file it in temp, run the setup and then in Terminal
```

ubuntuzilla.py -a install -p firefox
```

Installation instructions are pretty self explanatory. Just follow the websites guide. 

My only issues is that for me, the Firefox process = firefox/firefox-bin; dont end when i close out of it. I'm trying to find a fix for that.

---

### Post by PmDematagoda on 2009-01-15
> **Zlatan said:**
> Short question for those who knows: when Firefox3 will be ported to KDE4?
Thank you.

There is already a port of Firefox to Qt4, however that is still very feature-incomplete and quite unstable. And since the port is not officially supported by Mozilla or the KDE community, there is a big chance(very unfortunately) that the port could die out. You can build the port yourself if you want to see how it looks like, but you will need to learn how to tweak the Firefox build configuration a bit and will need to obtain the mercurial sources of Firefox, also you will need to be prepared to see a lot of problems:).

---

### Post by mips on 2009-01-15
> **PmDematagoda said:**
> And since the port is not officially supported by Mozilla or the KDE community, there is a big chance(very unfortunately) that the port could die out. 

I doubt it though as Nokia has a stake in this & Mozilla is helping.
[http://arstechnica.com/news.ars/post/20080818-nokia-helps-port-firefox-to-qt.html](http://arstechnica.com/news.ars/post/20080818-nokia-helps-port-firefox-to-qt.html)
[http://dot.kde.org/1218543988/](http://dot.kde.org/1218543988/)

---

### Post by PmDematagoda on 2009-01-15
> **mips said:**
> I doubt it though as Nokia has a stake in this.

Yes, however they are only doing this as far as Maemo, so once they stop after it reaches what they want, who knows?

---

### Post by bufsabre666 on 2009-01-15
> **PmDematagoda said:**
> Yes, however they are only doing this as far as Maemo, so once they stop after it reaches what they want, who knows?

well given that nokia has lgpl'd qt and opened it completely, theres a very very good chance that if nokia and mozilla advance it far enough that others will continue it

---

### Post by PmDematagoda on 2009-01-15
> **bufsabre666 said:**
> well given that nokia has lgpl'd qt and opened it completely, theres a very very good chance that if nokia and mozilla advance it far enough that others will continue it

From what I've been seeing around the Firefox MLs, that seems to be what's happening at the moment, although if someone could prove me wrong, I would glad to know that I am wrong:).

---

### Post by bufsabre666 on 2009-01-15
> **PmDematagoda said:**
> From what I've been seeing around the Firefox MLs, that seems to be what's happening at the moment, although if someone could prove me wrong, I would glad to know that I am wrong:).

i hope thats whats happening, kde 4.2 is making a strong case for me to become a full time kde user (that and how stagnant gnome is) and i still want to use firefox, which the color and buttons theme fairly well but the tabs and the shading are terrible

---

### Post by PmDematagoda on 2009-01-15
> **bufsabre666 said:**
> i hope thats whats happening, kde 4.2 is making a strong case for me to become a full time kde user (that and how stagnant gnome is) and i still want to use firefox, which the color and buttons theme fairly well but the tabs and the shading are terrible

I think I may have phrased my earlier statement badly, I meant to say that from what I've seen on the Firefox MLs, it seems that Firefox Qt is now being developed by independent developers and isn't receiving much aid from Nokia or Mozilla.

---

### Post by HavocXphere on 2009-01-15
Slightly offtopic but it might help someone:):P

There is a Theme called "Kde4 + Firefox3" by Ramon Antonio Parada. Makes the FF experience in Kubuntu 8.10 a lot more bearable. Still got issues but on the whole it makes FF usable again.

---

### Post by sertse on 2009-01-15
gtk user here, so bear with me.

What's wrong with firefox drawn with the qt-gtk-engine from KDE?

---

### Post by bufsabre666 on 2009-01-15
[IMG]http://i22.photobucket.com/albums/b315/bufsabre666/snapshot1-3.png[/IMG]

bad shading on buttons, and incorrect bordeer rendering on the tabs, address bar and search bar

---

### Post by HavocXphere on 2009-01-15
> **sertse said:**
> gtk user here, so bear with me.

What's wrong with firefox drawn with the qt-gtk-engine from KDE?
Its a pain. bufsabre666's screenshot doesn't do the mess justice. I literally often couldn't figure out which tab is the current tab without clicking on a few to see what moves.

Thats also what the "Kde4 + Firefox3" theme fixes. The radio buttons, edit boxes and progress bars are still screwed though. The common "fix" is to theme all of FF with a weird win 3.11 look blocky theme.:mad:

---

### Post by Zlatan on 2009-01-15
Another comment from author- I try to choose an OS for my Asus EEE 900, currently I use Ubuntu Intrepid Ibex, but it would be interesting to try if pure Gnome or pure KDE Ubuntu or Kubuntu versions could be faster/lighter/more effective.
Another thing is that I have to use CRM system at work and it was displayed terribly bad by Konqueror and it is good with FF3 and Epiphany.
Oh, and I am a heavy Google services user (good for mobile person, netbook user). Another problem with Konqueror, I think. Though I love KDE4...
What would be your thoughts here...?

---

### Post by bufsabre666 on 2009-01-15
> **Zlatan said:**
> Another comment from author- I try to choose an OS for my Asus EEE 900, currently I use Ubuntu Intrepid Ibex, but it would be interesting to try if pure Gnome or pure KDE Ubuntu or Kubuntu versions could be faster/lighter/more effective.
Another thing is that I have to use CRM system at work and it was displayed terribly bad by Konqueror and it is good with FF3 and Epiphany.
Oh, and I am a heavy Google services user (good for mobile person, netbook user). Another problem with Konqueror, I think. Though I love KDE4...
What would be your thoughts here...?

try it out if you want, see if you like it, the bad windows rendering on firefox shouldnt be enough of an issue to not use it if you really like it.

---

### Post by stimpack on 2009-01-15
[http://ramonantonio.net/kde-firefox/](http://ramonantonio.net/kde-firefox/)

Theme made my Firefox look good in KDE, fixing all the tab stuff.

---

### Post by Zlatan on 2009-01-15
> **stimpack said:**
> [http://ramonantonio.net/kde-firefox/](http://ramonantonio.net/kde-firefox/)

Theme made my Firefox look good in KDE, fixing all the tab stuff.

I think thread name could be wrong. Idea ATM would be that FF3 on Kubuntu would bring lots of gnome libraries...
Anyway thanks for the link, will definitely check it out.

---

### Post by bufsabre666 on 2009-01-15
> **stimpack said:**
> [http://ramonantonio.net/kde-firefox/](http://ramonantonio.net/kde-firefox/)

Theme made my Firefox look good in KDE, fixing all the tab stuff.

it fixes the tab but ruins the buttons, and its very blocky, but at this point its one of the best options, there is also another one that i have that fixed the block problem but doesnt help the tabs

---

### Post by Changturkey on 2009-01-15
> **Zlatan said:**
> Another comment from author- I try to choose an OS for my Asus EEE 900, currently I use Ubuntu Intrepid Ibex, but it would be interesting to try if pure Gnome or pure KDE Ubuntu or Kubuntu versions could be faster/lighter/more effective.
Another thing is that I have to use CRM system at work and it was displayed terribly bad by Konqueror and it is good with FF3 and Epiphany.
Oh, and I am a heavy Google services user (good for mobile person, netbook user). Another problem with Konqueror, I think. Though I love KDE4...
What would be your thoughts here...?

I think whenever KDE/Konqueror uses Webkit for rendering, it will be much better. So probably 4.3/4.4.

---

### Post by Skripka on 2009-01-15
> **bufsabre666 said:**
> [IMG]http://i22.photobucket.com/albums/b315/bufsabre666/snapshot1-3.png[/IMG]

bad shading on buttons, and incorrect bordeer rendering on the tabs, address bar and search bar


I'd suggest finding a better FireFox theme for starters.  There are a few that look far better with KDE in mind....I have to go for now-but I'll post linkies later if you want.

---

### Post by Zlatan on 2009-01-15
Currently trying Ubuntu with gnome apps- epiphany instead of ff, abiword and gnumeric instead of OOo, pidgin instead of skype, at+f2 instead of gnome-do, tacker off, piddgin mail notify instead of gmail-notify. Poor eee 900 feels a little better and I must say than epiphany is much more responsible than ff3.
Would be very interestng to try similar thing with Kubuntu, but as I wrote before, there are probems with dislpaying company's CRM page and with Gmail.
Maybe someone has more experience in this field?
We can close this thread and start another or we can continue here, please advise:)
Thank you

---

### Post by happysmileman on 2009-01-15
> **PmDematagoda said:**
> I think I may have phrased my earlier statement badly, I meant to say that from what I've seen on the Firefox MLs, it seems that Firefox Qt is now being developed by independent developers and isn't receiving much aid from Nokia or Mozilla.

Maybe you're right but the official Mozilla source repository includes the Qt code, so this would imagine they at least expect it to eventually be supported or completed?

---

### Post by PmDematagoda on 2009-01-15
> **happysmileman said:**
> Maybe you're right but the official Mozilla source repository includes the Qt code, so this would imagine they at least expect it to eventually be supported or completed?

Hopefully Mozilla will see the light in supporting this port, but I imagine the port would need more progress before they do so.

---

### Post by DigitalDuality on 2009-01-15
d

---

### Post by vishzilla on 2009-01-15
Since I've jumped on the KDE bandwagon I surely hope the port will be well supported by Mozilla

---

### Post by LuisAugusto on 2009-01-16
> **Changturkey said:**
> I think whenever KDE/Konqueror uses Webkit for rendering, it will be much better. So probably 4.3/4.4.

Actually, I'm using Konqueror with Webkit right now. With flash support and all. You just need to build 4.2 against Qt 4.5, and change the engine to webkit-kpart.

It won't be default for 4.2 (since they're using Qt 4.4, obviously, since 4.5 hasn't been released XD). But maybe on 4.2.3 or something 

------------

And to be fair, why would we want Firefox? Webkit is a lot better than Gecko, I think we need to change Konqueror GUI approach (or make a new web browser for KDE), but Firefox and Gecko aren't exactly the best option out there...

---

### Post by happysmileman on 2009-01-23
> **LuisAugusto said:**
> And to be fair, why would we want Firefox? Webkit is a lot better than Gecko, I think we need to change Konqueror GUI approach (or make a new web browser for KDE), but Firefox and Gecko aren't exactly the best option out there...

It's the application I use more than anything else, whenever I change to Konqueror for a bit I always seem to find reasons not to use it, even if they're stupid, I guess it's a matter of getting used to it.

Strangely I never had this problem switching from IE to FF, never found a single reason to stay with IE :P.

I would hope Konqueror eventually gets a better plugin system, I'd love to be able to write a plugin/extension in Python or something and load it without having to compile or anything, I think this would see a lot more extension developers.

---

### Post by Evengard on 2009-06-17
I found for myself a possible solution...
Just install firefox, install the gtk-qt for KDE4, and download this theme: [https://addons.mozilla.org/ru/firefox/addon/7172](https://addons.mozilla.org/ru/firefox/addon/7172)
You can see the screenshot to see how it is... Yes, it isn't Oxygen theme or whatever theme of KDE, but still it is the best solution for me.
[IMG]http://i002.radikal.ru/0906/d9/a450d7f30bd2.jpg[/IMG]

---

### Post by 67GTA on 2009-07-19
The GTK theming mess and bluetooth are the only two things left that are keeping me from coming back to KDE. My bluetooth solution is blueman, so the GTK theme mess is the only thorn left. I love Firefox, but would like to try Konqueror with webkit. Does anyone know when this will happen? What engine is it using in 4.3?

---

### Post by OutOfReach on 2009-07-19
> **67GTA said:**
> I love Firefox, but would like to try Konqueror with webkit. Does anyone know when this will happen? What engine is it using in 4.3?
As I am aware, you can already do this. Install the webkitkde package, then launch Konqueror, visit a webpage and go the the View->View Mode menu and select WebKit. I'm not sure how to make it the default view.
I'm pretty sure that KHTML will stay default for future Konqueror versions.

---

### Post by Skripka on 2009-07-19
> **67GTA said:**
> The GTK theming mess and bluetooth are the only two things left that are keeping me from coming back to KDE. My bluetooth solution is blueman, so the GTK theme mess is the only thorn left. I love Firefox, but would like to try Konqueror with webkit. Does anyone know when this will happen? What engine is it using in 4.3?

```

apt-get install webkitkde

```

then

```

keditfiletype text/html

```

and move "WebKit (webkitpart)" in the "Embedding" tab to the top.

---

### Post by 67GTA on 2009-07-19
Thanks Skripka, that worked perfectly. I can tell a difference in speed and rendering of some websites. I just noticed that on the daily build live CD as of July 18th (using now) that the Arora browser is included. It uses webkit by default. Are they trying to squeeze out Konqueror?

---

### Post by Skripka on 2009-07-19
> **67GTA said:**
> Thanks Skripka, that worked perfectly. I can tell a difference in speed and rendering of some websites. I just noticed that on the daily build live CD as of July 18th (using now) that the Arora browser is included. It uses webkit by default. Are they trying to squeeze out Konqueror?

I've heard talk about Arora replacing Konqueror.  But just talk, it isn't going to happen for KDE4.3 at least.  There was also debate of making Webkit the default core for Konqueror rather than KHTML, that also went nowhere for the immediate time.

Arora is a nice fast minimalist webkit browser, the Qt4 analog ofGtk Midori...but much further along in development.  That being said, the biggest annoyance with the Webkit browsers is that there is no autoscroll--and with no adjustability in scrolling speed, it can take 10 or more full mouse wheel revs to scroll a *normal* sized webpage-even on a 1680X1050 monitor.

---

