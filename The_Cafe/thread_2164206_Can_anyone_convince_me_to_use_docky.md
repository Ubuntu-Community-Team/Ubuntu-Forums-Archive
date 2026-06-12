---
title: "Can anyone convince me to use docky"
date: 2013-07-30
forum: The Cafe
---

### Post by pqwoerituytrueiwoq on 2013-07-30
@mods/admins Was not sure where to put this feel free to move it
 
I have been using xubuntu 13.04 with a gnome2 layout for some time
when i have 5+ windows open i have found it annoying to deal with them in the bottom panel and have though having a side panel like unity has would be useful
I have been playing with docky in a virtualbox running xubuntu 13.10, there are a few issues i have with it's flexibility

[LIST=1]
[*]unable to remove the settings launcher, I would rather open it via the Accessories menu under xfce's Applications Menu 
[*]xfce4-terminal does not work and has a missing icon
[LIST]
[*]Tried a workaround i found for 12.04 but it did not work 
[/LIST]
  
[*]Thunar has the same issue as xfce4-terminal 
[*]I can't remove pined apps from docky 
[*]I can't place helpers on both sides of the launchers (tried using it as a replacement for my bottom panel) 
[*]Is there a way i can set my desktop icons to not end up under docky when using dock'y intelihide feature?
[LIST]
[*]Normally have a clean dekstop but i sometimes save projects to it when i am working on them 
[/LIST]
   
[/LIST]
on a side now where are these post autosaved to? i only ask cause i retyped 3/4 of this once

EDIT:
now using cario dock, i dont seem to have any issues with it, but if anyone knows a way to put a margin for desktop icons that would be useful

---

### Post by apollothethird on 2013-07-30
> **pqwoerituytrueiwoq said:**
> @mods/admins Was not sure where to put this feel free to move it
 
I have been using xubuntu 13.04 with a gnome2 layout for some time
when i have 5+ windows open i have found it annoying to deal with them in the bottom panel and have though having a side panel like unity has would be useful
I have been playing with docky in a virtualbox running xubuntu 13.10, there are a few issues i have with it's flexibility

[LIST=1]
[*]unable to remove the settings launcher, I would rather open it via the Accessories menu under xfce's Applications Menu
[*]xfce4-terminal does not work and has a missing icon
[LIST]
[*]Tried a workaround i found for 12.04 but it did not work
[/LIST]

[*]Thunar has the same issue as xfce4-terminal
[*]I can't remove pined apps from docky
[*]I can't place helpers on both sides of the launchers (tried using it as a replacement for my bottom panel)
[*]Is there a way i can set my desktop icons to not end up under docky when using dock'y intelihide feature?
[LIST]
[*]Normally have a clean dekstop but i sometimes save projects to it when i am working on them
[/LIST]
  
[/LIST]
on a side now where are these post autosaved to? i only ask cause i retyped 3/4 of this once

If you're having problems with docky, try Cairo-Dock (from the repository).  I believe this will resove the issues you describe.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by VinDSL on 2013-07-30
Generally speaking, I hate docks, but I love Plank.  Go figure.

Have you every tried Plank?

If so, I'd be curious to read your opinion(s) of it...

---

### Post by pqwoerituytrueiwoq on 2013-07-30
@[**[COLOR=#000000]apollothethird[/COLOR]**]("http://ubuntuforums.org/member.php?u=1176033") Now that seems better :)

@vindsl
what is the packages name, plank does not show up in synaptic

never messed with docks before, this is the 1st time i have takes interest in something dock like, i have used a gnome2 panel till now (before that i used the task bar on windows xp)
just playing with this in a virtualbox atm

thinking about using the dock in addition to my gnome to like panels

---

### Post by Faolan84 on 2013-07-30
Using Docky will enhance your libido and give you the ability to fly.  It will give you chest hair of steel and make women fawn over you immediately after seeing you.

Meh, Docky is awesome, especially if you are using Gnome, XFCE, or similar type environment.  It is fairly stable although it does have its weak points.  Like you mentioned it is a bit silly that the settings is accessed through its own button on the dock.  This should be a right-click option.  Personally, I am a KDE guy and prefer Icon Task, but there is also Fancy Tasks and Smooth Tasks that do similar things.  That is just my 2¢.
.
I have honestly found Cairo-Dock to be very buggy and not worth the trouble.  If want something designed for lighter systems try wbar, tint2, or pypanel.  There are quite a few routes you can take.

---

### Post by pqwoerituytrueiwoq on 2013-07-30
@Faolan84
not using xfce cause it is light weight, using it for the customization options
my desktop has plenty of power 12gb ram 3.7Ghz Phenom II CPU and a GTX 550 TI
i have seen a few display issue in cario dock in the launcer tooltips so far, just figure it is cause i am using it in a virtualbox via cpu rendering

---

### Post by VinDSL on 2013-07-30
> **pqwoerituytrueiwoq said:**
> @vindsl
what is the packages name, plank does not show up in synaptic...

Here's the version I'm running...

```
vindsl@Zuul:~$ apt-cache policy plank
plank:
  Installed: 0.3.0+bzr854-0ubuntu1~13.10~ricotz1
  Candidate: 0.3.0+bzr854-0ubuntu1~13.10~ricotz1
  Version table:
 *** 0.3.0+bzr854-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/docky/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$
```


Probably the easiest way to get it is:  [http://ppa.launchpad.net/ricotz/docky/ubuntu/pool/main/p/plank/](http://ppa.launchpad.net/ricotz/docky/ubuntu/pool/main/p/plank/)

Choose your poison...  ;)

EDIT

Here's a nice toot:  [http://wiki.go-docky.com/index.php?title=Plank:Installing](http://wiki.go-docky.com/index.php?title=Plank:Installing)

---

### Post by pqwoerituytrueiwoq on 2013-07-30
> **VinDSL said:**
> Here's the version I'm running...

```
vindsl@Zuul:~$ apt-cache policy plank
plank:
  Installed: 0.3.0+bzr854-0ubuntu1~13.10~ricotz1
  Candidate: 0.3.0+bzr854-0ubuntu1~13.10~ricotz1
  Version table:
 *** 0.3.0+bzr854-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/docky/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$
```


Probably the easiest way to get it is:  [http://ppa.launchpad.net/ricotz/docky/ubuntu/pool/main/p/plank/](http://ppa.launchpad.net/ricotz/docky/ubuntu/pool/main/p/plank/)

Choose your poison...  ;)

EDIT

Here's a nice toot:  [http://wiki.go-docky.com/index.php?title=Plank:Installing](http://wiki.go-docky.com/index.php?title=Plank:Installing)
*takes a look*
a bit lighter that i expected, but i should have expected you liking a light weight dock since you use a older system typically refereed to as a 'ancient iron'

---

### Post by VinDSL on 2013-07-30
> **pqwoerituytrueiwoq said:**
> [...] I should have expected you liking a light weight dock since you use a older system typically refereed to as a 'ancient iron'
[State_of_The_Art 2004]("http://www.tomshardware.com/reviews/p4-northwood-prescott-comparison-4,809-2.html"), baby!  :D

---

### Post by Paqman on 2013-07-30
Use Docky or the bunny gets it!
[IMG]http://www.hellonearth.com/movies/conair/plot11.jpg[/IMG]
Seriously though, I never got on with Docky. AWN was a staple on my machine for a long time, but I just use the Unity dock now.

---

### Post by pqwoerituytrueiwoq on 2013-07-30
> **VinDSL said:**
> State_of_The_Art 2004, baby!  :D
better than my ancient iron sitting on the self
[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=bph05264#N46](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=bph05264#N46)

---

### Post by VinDSL on 2013-07-30
> **pqwoerituytrueiwoq said:**
> better than my ancient iron sitting on the self
[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=bph05264#N46](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=bph05264#N46)
Whoa!  My CPU is a rare collector's item now...  LoL!  :D

[http://www.amazon.com/gp/offer-listing/B000YDSUXM/ref=dp_olp_0?ie=UTF8&condition=all](http://www.amazon.com/gp/offer-listing/B000YDSUXM/ref=dp_olp_0?ie=UTF8&condition=all)

---

### Post by Frogs Hair on 2013-07-30
I use Dockbarx with the XFCE session and don't have the problems listed in your first post .

---

### Post by Max Blyss on 2013-07-30
You can get rid of the Anchor Icon / Settings Launcher with Gconf-Editor...  Install it and go to apps/docky2/items/docky item and uncheck the box that says 'show docky item'...  Or at least you can in 12.04, don't know if same option is available later.

I used Docky for a long time, but in the end I had to admit to myself that I just used a dock for the big, pretty icons.

---

### Post by pqwoerituytrueiwoq on 2013-07-30
> **VinDSL said:**
> Whoa!  My CPU is a rare collector's item now...  LoL!  :D

[http://www.amazon.com/gp/offer-listing/B000YDSUXM/ref=dp_olp_0?ie=UTF8&condition=all](http://www.amazon.com/gp/offer-listing/B000YDSUXM/ref=dp_olp_0?ie=UTF8&condition=all)

My CPU just started going up in value (it is the high end for the AM3 socket)

---

### Post by pqwoerituytrueiwoq on 2013-07-30
> **Frogs Hair said:**
> I use Dockbarx with the XFCE session and don't have the problems listed in your first post .
how does it compare with cario dock, so far i like that one, reminds me of compiz, back when it was not broken as [insert game reference of your choosing]

---

### Post by craig10x on 2013-07-30
Hey...why not just use regular ubuntu with unity (since your hardware can certainly handle it)...unity IS a dock you know and works better then docky and cairo dock anyway....
ok...true, it's on the left instead of the bottom...but i am sure you will get use to it pretty quickly ;)

Or just think of the unity dock as a vertical taskbar cause actually it is kind of that too :D

---

### Post by pqwoerituytrueiwoq on 2013-07-30
> **craig10x said:**
> Hey...why not just use regular ubuntu with unity (since your hardware can certainly handle it)...unity IS a dock you know and works better then docky and cairo dock anyway....
ok...true, it's on the left instead of the bottom...but i am sure you will get use to it pretty quickly ;)

Or just think of the unity dock as a vertical taskbar cause actually it is kind of that too :D
lacks the options i have in xubuntu panels, i wanted to have my bottom and top panels + the unity like dock with a few common apps in it
[[img]http://www.zimagez.com/miniature/screenshot-07302013-111635pm.php[/img]](http://www.zimagez.com/zimage/screenshot-07302013-111635pm.php)

---

### Post by craig10x on 2013-07-31
Got you...I'm a one panel guy myself...actually, i usually only like my 1 panel on bottom (like on linux mint)...only reason i don't mind it being on top in the unity set-up is because of the global menu, so when my browser is open, i don't lose any space...

---

### Post by pqwoerituytrueiwoq on 2013-07-31
> **craig10x said:**
> Got you...I'm a one panel guy myself...actually, i usually only like my 1 panel on bottom (like on linux mint)...only reason i don't mind it being on top in the unity set-up is because of the global menu, so when my browser is open, i don't lose any space...on my desktop with 1920x1080 i can afford the extra 24px on a top an bottom panel, I may replace the bottom panel on my laptop with cairo dock where the screen resolution is 1366x768

---

### Post by vasa1 on 2013-07-31
> **pqwoerituytrueiwoq said:**
>  ...
 having a side panel like unity has would be useful
...
Xubuntu can give you an additional side panel with autohide without needing to  install any other software.

---

### Post by Copper Bezel on 2013-07-31
Not one that behaves like a dock, though, and Docky or Plank seems the best bet at the moment. I didn't realize they'd diverged so much, though! 

The pinned launchers and anchor icon in Docky *can* be removed [through gconf-editor]("http://askubuntu.com/questions/4942/remove-the-anchor-icon-in-docky") (which is weird in itself, since gconf is deprecated in favor of dconf) but why pinned launchers can't be removed by right-clicking is beyond me. There doesn't seem to be any convenient way to customize Docky without the anchor icon, though, so I can see why it's included (unlike Plank's, which gives an About page, but can also be removed, this time through the file manager.) Thunar appears in the dock just fine for me, but Docky doesn't distinguish web applications from the browser they're run in as in Unity (while Plank does.) Docky comes with some widgets, but they seem about as useful and functional as I'd have expected. (And about as consistent. Some require right clicks to do anything, some require left clicks, and some respond differently to each - silliness.)

Plank has fewer features, but seems to be the more complete and polished product at this point. 

I didn't realize that DockBarX was still active. It didn't work very well the last time I played with it, and that was a bit disappointing, as it was easily the best dock in the running a couple of years ago. Or to make that a bit clearer, it had the best feature set I've *ever* seen in a dock, with truly complete customization and a perfect clone of all the features from the Windows 7 taskbar and the Unity launcher, but the last time I tried it, some of the best features were simply broken. (Trying it again, the Compiz features still seem broken, and they're most of what made it stand out.)

Neither Plank nor Docky does anything the Unity launcher doesn't save for some very, very, *very* basic configuration, but Plank at least comes close to being at least a complete replacement, and I could see using it under Xfce.

---

### Post by makitso on 2013-07-31
> 2. xfce4-terminal does not work and has a missing icon
sudo cp /usr/share/applications/xfce4-terminal.desktop ~/.local/share/applications
> 3. Thunar has the same issue as xfce4-terminal
sudo cp /usr/share/applications/Thunar.desktop ~/.local/share/applications
> 4. I can't remove pined apps from docky
I believe you can right click on the docky icon and drag it to the desktop -- which will delete it.

I use Docky on xubuntu on 13.04 and 13.10.  Overall, I think its a bit better at auto hiding with a full screen app than Cairo.

---

### Post by Copper Bezel on 2013-07-31
> [COLOR=#000000]sudo cp /usr/share/applications/Thunar.desktop ~/.local/share/applications[/COLOR]
Weird fix. I wonder why it worked for me without this? I'm on 13.04, too.

Don't use *sudo* here, though. That'll make the new file owned by root instead of owned by the user, and you don't want that within your .local.

> [COLOR=#000000]I believe you can right click on the docky icon and drag it to the desktop -- which will delete it.[/COLOR]
Ordinary launchers can be dragged off, along with most docklets. It's a left-click and drag, not a right-click. (I'm guessing you didn't mean the Docky anchor icon, since that's not the bit you quoted. It can't be removed except through gconf.)

---

### Post by pqwoerituytrueiwoq on 2013-07-31
> **Copper Bezel said:**
> Weird fix. I wonder why it worked for me without this? I'm on 13.04, too.


that did not work on 13.10you could also make a symlink to do the same thing

---

### Post by Buntu Bunny on 2013-07-31
Someone may have already addressed this, but with Xfce, compositing has to be enabled in order for Docky to function properly.

---

### Post by pqwoerituytrueiwoq on 2013-07-31
> **Buntu Bunny said:**
> Someone may have already addressed this, but with Xfce, compositing has to be enabled in order for Docky to function properly.nope just you

---

### Post by darkaudit on 2013-08-01
> **makitso said:**
> sudo cp /usr/share/applications/xfce4-terminal.desktop ~/.local/share/applications

sudo cp /usr/share/applications/Thunar.desktop ~/.local/share/applications

I believe you can right click on the docky icon and drag it to the desktop -- which will delete it.

I use Docky on xubuntu on 13.04 and 13.10.  Overall, I think its a bit better at auto hiding with a full screen app than Cairo.

Quicker fix, navigate thunar to /usr/share/applications. Drag Thunar and xfce4-terminal to Docky and drop. :)

---

### Post by Hexxus on 2013-08-01
> **VinDSL said:**
> Here's the version I'm running...

```
vindsl@Zuul:~$ apt-cache policy plank
plank:
  Installed: 0.3.0+bzr854-0ubuntu1~13.10~ricotz1
  Candidate: 0.3.0+bzr854-0ubuntu1~13.10~ricotz1
  Version table:
 *** 0.3.0+bzr854-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/docky/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$
```


Probably the easiest way to get it is:  [http://ppa.launchpad.net/ricotz/docky/ubuntu/pool/main/p/plank/](http://ppa.launchpad.net/ricotz/docky/ubuntu/pool/main/p/plank/)

Choose your poison...  ;)

EDIT

Here's a nice toot:  [http://wiki.go-docky.com/index.php?title=Plank:Installing](http://wiki.go-docky.com/index.php?title=Plank:Installing)


Skimming the forums and I found your post, Yep I love it! Plank is great!

---

### Post by hasanazeez on 2013-08-01
I personally don't use Docky, don't like it. I'm not using a MAC!

---

### Post by pqwoerituytrueiwoq on 2013-08-01
> **vasa1 said:**
> Xubuntu can give you an additional side panel with autohide without needing to  install any other software.i know, but those would be launchers that would not own the main window

---

### Post by courseinmiracles2 on 2013-08-03
nope, sorry

---

### Post by kevdog on 2013-08-03
I just use Cairo Dock -- I use the git version however which is a lot more functional.  The developers are very responsive in their thread to making changes.

---

### Post by pqwoerituytrueiwoq on 2013-08-04
> **kevdog said:**
> I just use Cairo Dock -- I use the git version however which is a lot more functional.  The developers are very responsive in their thread to making changes.can i get a link to that?

---

