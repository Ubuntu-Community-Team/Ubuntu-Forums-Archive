---
title: "Ubuntu theme/appearance controls leave a lot to be desired."
date: 2013-03-31
forum: Ubuntu, Linux and OS Chat
---

### Post by HousieMousie2 on 2013-03-31
I will start by confessing that I started out using Kubuntu and held on with a death grip until KDE3 was no longer a suitable/workable option.  There wasn't much about KDE3 that I did not like, and not much about KDE4 that I did like.  Since then I have bounced around a bit, LXDE, XFCE, Mint, etc, but eventually settled for Ubuntu simply to avoid glitches and odd behaviors.  After some tweaks, I am largely a happy camper... with one exception.

Themes and overall appearance.

I am not talking about eye-candy.  I never wanted awn curves, a spinning cube of desktops nor did I use compiz fusion or the like.  It isn't flashy and slick that I am after, or fancy window animations, transparencies and such, since I have discovered I am allergic to bloat.  :)
As far as how the windows are drawn I have no complaints with the default themes, they have nice shapes, gradients, buttons, bars, etc... it's the colors of those themes that bug me.

It seems like the tendency these days is to have pale gray on light gray with medium gray (for extra pizzazz?)  For me that is boring as all get out, but for my aging father it is a serious problem.  The lack of contrast gives him fits, and let's face it the "High Contrast" themes are garishly ugly and harsh on the eyes because they have too much contrast.

Yes, there are tons of themes out there, though seeing what they really look like is iffy, finding out how well they work is a crapshoot and fishing through them is time consuming.

Ideally, what I would like to find is a theme, or UI for a theme rather, that would allow me (and more over my die hard Linux using Dad - since Slackware 0.9, though he started with System V UNIX) to select colors for a theme.  At the risk of being dogged on for using the W-word...  Something like what Windows has, but of course since this would be Ubuntu, it would be better.

Perhaps such a thing exists already?  Some theming wizard already create the perfect solution?  If they have, it seems to be safely hidden in the bowels of ubuntuthemes.org.

My wish for the future of default Ubuntu themes would be the ability to select colors for any of the existing default themes.  "Feeling your inner Irish today?  Green it is!  How about some reds and yellows for autumn?  Presto!" <--- read as: click, click, click, done.  :)

That's my two cents, for what it's worth.  What do you think about the colors of the default themes?

---

### Post by craig10x on 2013-03-31
I like the lighter theme (radiance) myself because it has a silver/grey metal type of look which to me looks nicer then the default dark theme....and that is the one i use...
But i would agree that it would be nice if, along with those two themes, they would add a bunch of extra options, much like gnome 2 use to offer...

---

### Post by deadflowr on 2013-03-31
I didn't even read the OP, as I wholly agree with the title.:)

---

### Post by ManamiVixen on 2013-04-01
So do I, in fact it isn't that hard to write a script for changing colors of a GTK 2 and 3 Theme. HECK! It's even be possible to write a GTK Ambiance recolor program. I've already isolated where all the hexadecimal colors values are located in the Ambiance theme. Really, the only thing needed to be done to recolor the Ambiance theme is simply swapping these values with other values. In turn, that will change it's colors. I unfortuantly can't program, so I cant write such a thing. But I can do a mock up picture showing off the interface I have in mind. I might do that tomorrow and present it here with all other details required to get it working.

---

### Post by thiebaude on 2013-04-01
Uncompilicated Themes is what I use. I have many choices to choose from.

---

### Post by kurt18947 on 2013-04-01
That seems to be an advantage that Gnome 3/gnome-shell has over Unity.  I believe that Gnome is not as 'locked-down' as Unity.

---

### Post by vasa1 on 2013-04-01
> **kurt18947 said:**
> That seems to be an advantage that Gnome 3/gnome-shell has over Unity.  I believe that Gnome is not as 'locked-down' as Unity.
The Ambiance theme isn't locked down. You can get in with sudo and a text editor and change whatever colors you want. I've been doing it for quite a while rather than hoping someone will make a theme that meets my needs. I've even posted a few threads here on the topic of increasing contrast, etc. If one copies the Ambiance theme folder over to ~/.themes then even sudo isn't needed.

Talking about locked down, the Adwaita theme is (or was, the last time I looked) somewhat locked down because it (or part of it) is supplied as a binary blob.

@OP,why don't you take a while to figure out themes? They're for the most part just text files that can be edited. You don't need to be a coder to take a theme and mod it.

---

### Post by Gyokuro on 2013-04-01
I was really surprised that Ubuntu Kylin has  /close/min/max buttons at the right site which  is one of the things in Unity that should the user be allowed to change and I want to have. The other are the themes: Ambiance, Radiance are not enough and I do not like any of them and Radiance is not very comfortable if you have to stare the whole day at a bright screen. To change themes in Unity is not very comfortable and to lock down the look feels like to work at a Mac (I don't like the Mac look only have to burden to update/administer it). A much darker theme is welcome and there are some good ones which get used at different Ubuntu flavours (like Digital CDE color scheme of KDE3).

---

### Post by HousieMousie2 on 2013-04-02
vasa1,
I know that one can take the time to fiddle with the text files until you have a recolored theme, and I have always enjoyed that aspect of Linux, that you can tweak the configuration files since many of them are fairly 'plain text'.
It is a time consuming proposition however.
My post was not a cry for help or seeking a solution, I know how...
It was more a wish for something in the future.  Yes, a point and click, something that comes standard, not something that every user would have to root through config files to manually tweak for themselves.

---

ManamiVixen,
I don't program either, but I would still like to see what you come up with.

---

### Post by vasa1 on 2013-04-02
> **HousieMousie2 said:**
> ...
It is a time consuming proposition however.
My post was not a cry for help or seeking a solution, I know how...
It was more a wish for something in the future.  Yes, a point and click, something that comes standard, not something that every user would have to root through config files to manually tweak for themselves.
...
Once you know how, how time-consuming can it be? Anyway, take a look here [http://ubuntuforums.org/showthread.php?t=2053698](http://ubuntuforums.org/showthread.php?t=2053698). I'm not sure how far it's gotten.

---

### Post by deadflowr on 2013-04-02
> [COLOR=#000000]It was more a wish for something in the future. Yes, a point and click, something that comes standard, not something that every user would have to root through config files to manually tweak for themselves.[/COLOR]

Like how the ole gnome2 worked.
With simply opening up the background setting feature and changing background, fonts, theme, and something else which I forget(been a year and a half), and if none of the themes work for you, a little link that says get more themes, which when clicked gets you to a site where you can download themes, which in turn auto-install and set as the theme in use. And if you don't like it, switch again.No harm.

---

### Post by HousieMousie2 on 2013-04-04
Exactly, deadflowr.

Thank you for the link, vasa1.  Looks interesting, I will have to fiddle with it later when I have the time.  lol  No telling whne that will be, maybe they will have it in the repos by the time I get around to it.  :)
And it is certainly more time consuming than selecting a color and hitting apply.  Lazy?  Maybe.  Or perhaps just pressed for time and not inclined to spend what little is available doing something that use to take just a few clicks.

---

### Post by codingman on 2013-04-04
How about trying some other DE/WM? I know that you have tried several others, but there are some other ones that you missed. You should take a look at OB and BB. You can also try some tiling WM's, and with those the themes are done via code, and you don't really notice the GTK of tiled windows.

---

### Post by vasa1 on 2013-04-05
> **deadflowr said:**
> Like how the ole gnome2 worked.
With simply opening up the background setting feature and changing background, fonts, theme, and something else which I forget(been a year and a half), and if none of the themes work for you, a little link that says get more themes, which when clicked gets you to a site where you can download themes, which in turn auto-install and set as the theme in use. And if you don't like it, switch again.No harm.

*gnome-color-chooser* is still available for gtk2 apps though it won't let you change themes but, IIRC, you can change aspects of the theme. (I could be wrong! It's a while since I used it.)

Then there are other, more customizable distros such as Lubuntu which has *lxappearance*, aka *Customize Look and Feel*. The image shows what can be tweaked. BTW, for whatever reason, widgets = themes!:

---

### Post by HousieMousie2 on 2013-04-08
codingman,
I will take a look at those.  Thank you for the suggestions!

vasa1,
I like lxde, it just gets a little squirrly on my machine... no idea why, since it behaves perfectly on my desktop and netbook. lol  I may give it another try soon... I do miss it.
I have tried gnome-color-chooser, which is not bad, except that it is not global.  If it were, it would be the answer to my prayers.  :)

Thanks again!

---

