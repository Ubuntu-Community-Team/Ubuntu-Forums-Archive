---
title: "Create a lightweight and massively productive system with Gnome-do Docky!"
date: 2009-04-08
forum: The Cafe
---

### Post by Mazza558 on 2009-04-08
[IMG]http://img147.imageshack.us/img147/5361/desklayout.jpg[/IMG]

**I should clarify: lightweight as in "lightweight on screenspace".**
[B][SIZE="6"]
[Demo Video]("http://www.youtube.com/watch?v=9LVag6i42Og") [/SIZE][/B]

[**Digg it here if you liked this!**]("http://digg.com/linux_unix/HOWTO_Create_an_awesome_productive_desktop_with_Gnome_do")

I've been fiddling with my panel layout for a while, trying to combine it well with compiz and gnome-do. I think I have the perfect layout now, which really makes using ubuntu than much more awesome.

This layout will give you:

- Maximum screenspace
- The fastest way to "do" things
- Great window management using Compiz

and it feels much more fluid than regular gnome, in my opinion.

Here's a guide to set it up!

**Prerequisites**

- Gnome-do 0.8+ - [http://do.davebsd.com/download.shtml]("http://do.davebsd.com/download.shtml")- Add the repository for gnome-do, update your sources and then open a terminal and install it with "*sudo aptitude install gnome-do*"
*P.S - I recommend making sure gnome-do performs well enough on your system before going through the whole guide.*

- Compiz - Most people have this enabled already, so this is no problem.

- Ubuntu 9.04 is recommended, purely for the speed increases and the new notifications which improve the experience quite a bit.

**Step 1 - Panels**

- Get rid of all panels but one
- Add what applets you want to this - any which aren't covered by gnome-do. For example, I use the original ubuntu menu, the notification area, and the volume icon. 
- Set this panel to "top", enable autohide and untick the "expand" box.

*Now for some gconf tweaks to make it more usable.*

- Press Alt-F2 and type 

```
gconf-editor
```

- then go to edit > find, and search for "panel"
- Scroll down for something along the lines of "/toplevel/panel_0", and click on it.
- For "auto-hide size", change this to "1" (anything lower doesn't make a difference))
- Untick "enable animations"
- For "hide delay", change this to something much lower, like "50".
- Scroll down and do the same for "unhide delay"
- Move your mouse up to the hidden panel and try out the speedy hide and unhide. Adjust to your taste, and when you're happy, move to the next step. Keep gconf open.

**Set up gnome-do**

*Assuming you've just installed gnome-do, do the following, if not, ignore these steps and move on to the further instructions:*

- Open gnome-do for the first time. You'll get a little bar with two boxes.
- Click on the down arrow and go to preferences.
- Go on "appearance" and change the theme to "Docky". You'll get the dock at the bottom of the screen. Resize to your liking.
- On "general", tick "start gnome-do at logon"
- Add whatever features you want in the plugins tab. 
- On docky, right-click the gnome-do icon (far left) and tick "automatically hide" here.

*_Further instructions for gnome-do_*

- in gconf, do another search, this time for "gnome-do"
- scroll down in the results for "Docky/Utilities/DockPreferences"
- change "summontime" to something slightly lower - perhaps the same as what you set for the panel.
- Change anything else you want here too - you can do this later.
- You might want to change the shortcut for gnome-do's search - go to the "keyboard" tab. I like to use CTRL-Space.

**Compiz**

- I recommend allowing the scale plugin to activate in the bottom left/right corner. This makes managing windows without a panel much easier.

**Done! **

- You can search in gnome-do by activating the keyboard shortcut. It can do almost anything - refer to the gnome-do homepage for more info here.

_______________________

Enjoy this layout - I know I am enjoying it :)

---

### Post by Mazza558 on 2009-04-08
Thoughts?

---

### Post by TheOrangePeanut on 2009-04-08
I don't use Gnome, but it does look really nice.  I'd be curious to see it in action.

---

### Post by oasmar1 on 2009-04-08
I have been using a very similar layout to you, Docky is just so great, ever since I switched to Ubuntu and got Docky I have found that it integrates much better than AWN. I do miss some of the features of the Dock in Leopard, but the way it is like QuickSilver and the Dock in one single thing it is fantastic. I sure hope gnome-do makes it into gnome itself.

---

### Post by cariboo on 2009-04-08
I've done basically the same thing. I also have wallpaper-tray installed, it changes the wallpaper every 15 minutes.

Jim

---

### Post by Joeb454 on 2009-04-08
> **cariboo907 said:**
> I've done basically the same thing. I also have wallpaper-tray installed, it changes the wallpaper every 15 minutes.

Jim

The one in the screenshot was pretty cool.

I don't have enough to change wallpaper a lot, I'll have to find some good ones and look into it :)

---

### Post by benj1 on 2009-04-08
@mazza 558
i would have thought the 2 mouse cursors would make it very productive too ;)

---

### Post by Mazza558 on 2009-04-08
> **benj1 said:**
> @mazza 558
i would have thought the 2 mouse cursors would make it very productive too ;)

Lazy image-editing, that's what :)

It was the only way to show both panels at the same time in the screenshot.

---

### Post by ghindo on 2009-04-08
"Lightweight" is a bit of a misnomer.  Gnome-Do has a lot of GNOME and Mono dependencies, and Compiz isn't exactly light.

But that's just my 2¢.  Thanks for the tutorial.

---

### Post by SomeGuyDude on 2009-04-08
> **ghindo said:**
> "Lightweight" is a bit of a misnomer.  Gnome-Do has a lot of GNOME and Mono dependencies, and Compiz isn't exactly light.

But that's just my 2¢.  Thanks for the tutorial.

Compiz is a lot lighter than it seems to get a rap for. Running it standalone it uses almost no more memory than Openbox did. Some higher CPU, sure, but not a lot.

Anyway, I'd love to try this thing, but again, I don't have GNOME and don't want the ~200MB of dependencies.

---

### Post by ghindo on 2009-04-08
I suppose "light" is a relative term ;)

---

### Post by kidux on 2009-04-08
I've got a similar setup, except I'm using XFCE with Docky, and completely removed the panels, with systray on auto-hide.

---

### Post by blithen on 2009-04-08
Damn that looks nice! I dare you to make a script to do it all! :P.
Edit: Infact ***_I TRIPLE DOG DARE YOU!!!_*** Dun Dun Dunnnnn

---

### Post by Orlsend on 2009-04-09
Is docky lighter than AWN? I already use Gnome-Do so I will think about it if saves me more ram. I had a friend that had problems with it badly.

---

### Post by Mazza558 on 2009-04-09
> **Orlsend said:**
> Is docky lighter than AWN? I already use Gnome-Do so I will think about it if saves me more ram. I had a friend that had problems with it badly.

From my experience it's much lighter, simply because I can have a dock AND a launcher in one app, saving memory.

The fact that you're loading less panel applets speeds things up a bit too.

---

### Post by primolarry on 2009-04-12
Hi there,
Nice guide, my configuration is very similar but I use conky to monitor temperatures, free space, etc:

[http://ubuntuforums.org/attachment.php?attachmentid=109585&stc=1&d=1239564619](http://ubuntuforums.org/attachment.php?attachmentid=109585&stc=1&d=1239564619)

I wouldn't state that compiz is light, but it is true that it is ligher than what one would think. I tried enabling metacity's compositing feature, so I could use docky without compiz. The fact is, with my nvidia 9800GT, metacity with compositing enable rated about 3000 FPS, and with compiz it rates about 9000 FPS.

Orlsend, I tried AWN couple of months back, and I find docky way more lighter. Bad news is, to have gnome-do 0.8 in ubuntu 8.04 will take you some time, as in the gnome-do repository for hardy they only deliver up to gnome-do 0.6. You'd have to compile it yourself, add some repositories, etc. I did manage to do it but it took me some time, I would recomend trying it in a VM before doing it in your PC, it may broke some dependencies.

Regards,

---

### Post by LasherHN on 2009-04-12
I agree, that's not exactly "light" I've been using docky/compiz for a while now and when sometimes when I have a lot of stuff going on I get up to 1.1 GB of RAM use, which is not really a lot when you take into account that I'm using stuff like Firefox with 4+ tabs, amarok, nautilus, kate, a couple of terminals sometimes Gimp too and my video card is integrated.

Thanks for the extra tips you give here they save me some screen space! ^^

---

### Post by blithen on 2009-04-12
Well I just changed to this, and I love it. Great  job I'm going to keep this FOREVER.

---

### Post by Mazza558 on 2009-04-12
> **blithen said:**
> Well I just changed to this, and I love it. Great  job I'm going to keep this FOREVER.

Thanks :)

---

### Post by primolarry on 2009-04-13
Mazza558, which icon set are you using?How did you change the gnome-do icon?

Thanks, regards

---

### Post by Mazza558 on 2009-04-13
> **primolarry said:**
> Mazza558, which icon set are you using?How did you change the gnome-do icon?

Thanks, regards

The icon set is Meliae Dark - which changes the Do Icon.

---

### Post by RaZe42 on 2009-04-13
You could go one step further by replacing the panel with a standalone system tray(I used stalonetray) and compiz-deskmenu(menu on desktop with middle-click)

Only problem with compiz-deskmenu is that you have to manually add all the launchers to it, otherwise I think the setup is perfect

---

### Post by gnomeuser on 2009-04-13
I would love to do something like this, however due to the way gnome-do and the plugins packages are currently packaged I would be forced to install Firefox, rhythmbox and evolution. There is absolutely no flexibility.

They really need to be split up into some subpackages.

[https://bugs.launchpad.net/ubuntu/+source/gnome-do-plugins/+bug/351535](https://bugs.launchpad.net/ubuntu/+source/gnome-do-plugins/+bug/351535)

---

### Post by Tibuda on 2009-04-13
> **gnomeuser said:**
> I would love to do something like this, however due to the way gnome-do and the plugins packages are currently packaged I would be forced to install Firefox, rhythmbox and evolution. There is absolutely no flexibility.

They really need to be split up into some subpackages.

[https://bugs.launchpad.net/ubuntu/+source/gnome-do-plugins/+bug/351535](https://bugs.launchpad.net/ubuntu/+source/gnome-do-plugins/+bug/351535)

I have Gnome Do and plugins, but I don't have Rhythmbox installed.

---

### Post by RuleMaker on 2009-04-13
I tried using cairo dock and AWN and I didn't like them. I find myself less productive.
If I have, for example, 3 instances of firefox (bad example), I have to move my mouse over each to see the title and I will lose a second for it.
Gnome panels are less eyecandy but, at least in my opinion, way more productive.

---

### Post by K.Mandla on 2009-04-13
> **ghindo said:**
> "Lightweight" is a bit of a misnomer.
That was my first reaction. What do you mean by "massively productive?"

---

### Post by loomsen on 2009-04-13
> **RuleMaker said:**
> I tried using cairo dock and AWN and I didn't like them. I find myself less productive.
If I have, for example, 3 instances of firefox (bad example), I have to move my mouse over each to see the title and I will lose a second for it.
Gnome panels are less eyecandy but, at least in my opinion, way more productive.

#2
Been through all of em, AWN (like 1 day :D ), kiba, cairo, gnome-do, stalonetray, some others I don't remember the names of.

stalonetray ate up around 80MB of RAM back then just for being there. I mean, cmon, not even Compiz takes that much.
Pretty much the same made me stop using gnome-do in like in hardy or so.

So..
[quote=ghindo]
But that's just my 2¢
[/quote]
make it 4

---

### Post by Mazza558 on 2009-04-13
> **K.Mandla said:**
> That was my first reaction. What do you mean by "massively productive?"

I should clarify: lightweight as in "lightweight on screenspace". As for massively productive, I mean that Do is a lot faster than using menus, especially for web tasks.

---

### Post by conundrumx on 2009-04-13
> **primolarry said:**
> 
Orlsend, I tried AWN couple of months back, and I find docky way more lighter. Bad news is, to have gnome-do 0.8 in ubuntu 8.04 will take you some time, as in the gnome-do repository for hardy they only deliver up to gnome-do 0.6. You'd have to compile it yourself, add some repositories, etc. I did manage to do it but it took me some time, I would recomend trying it in a VM before doing it in your PC, it may broke some dependencies.

Running GNOME Do 0.8 and later on Hardy (8.04) is unsupported.  It can be done, and I know of a few others that have, but the developers don't support it, and it's very irritating to do.

---

### Post by DBO on 2009-04-13
If you are brave I do suggest running GNOME Do trunk.  Docky now has 100% fixed Drag and Drop interaction so that there are no more swallowed DND effects.  Also slightly better performance and less memory consumption.

---

### Post by cegpope on 2009-04-29
for anyone interested in Do, but not liking the need for compiz, Gnome-Do will run just fine under metacity if you turn compositing on. (gconf-editor, apps > metacity > general, check compositing_manager)




does anyone know how to move or remove the gnome-do icon that is on the far left of the docky interface?

---

### Post by Mazza558 on 2009-05-06
> **DBO said:**
> If you are brave I do suggest running GNOME Do trunk.  Docky now has 100% fixed Drag and Drop interaction so that there are no more swallowed DND effects.  Also slightly better performance and less memory consumption.

Is that the compiled version then? 

How far behind (development-wise) is PPA from trunk? On the video in the OP, I was using trunk. Now I'm using the PPA and there's not much difference.

Having said that, Trunk does have a really nice GUI configuration now for Docky, meaning no more hunting through gconf to change the dock orientation.

---

### Post by Luggy on 2009-05-06
I love Gnome-Do, I just don't like Docky very much.

Also, Gnome-Do (and Docky) are in the Jaunty repos by default.

---

### Post by Mazza558 on 2009-05-06
> **Luggy said:**
> I love Gnome-Do, I just don't like Docky very much.

Also, Gnome-Do (and Docky) are in the Jaunty repos by default.

Not the PPA though, which has several improvements over the original.

On another note, I've been trying the dock on top for a while now, and it seems to be a better way of doing things. I have scale for the bottom left for quick window management.

---

### Post by NightwishFan on 2009-05-06
I have no idea how to use GNOME-Do's advanced features. I agree about Compiz, though it is very neat and lightweight. I would think it is nearly as soft as the Xp compositor when using the same features, and far more usable and light than aero.

---

### Post by Mazza558 on 2009-05-06
> **NightwishFan said:**
> I have no idea how to use GNOME-Do's advanced features. I agree about Compiz, though it is very neat and lightweight. I would think it is nearly as soft as the Xp compositor when using the same features, and far more usable and light than aero.

Which advanced features?

---

### Post by nothingspecial on 2009-05-06
Well I find gnome-do "massively productive", as a keyboard short-cut junky it`s my favourite app. Which is why I fail to understand the point of docky.
I use gnome-do to free up screen space so I don`t need a dock or panel.

I don`t like menu bars or screen decoration either - although I have to play with a new app for a while before I can do without them.

[[IMG]http://www.picamatic.com/show/2009/05/06/09/43/3542884_bigthumb.png[/IMG]](http://www.picamatic.com/view/3542884_Screenshot/)

---

### Post by Mazza558 on 2009-05-06
I use a panel for window management, functions which gnome-do can't fulfill (notification area), and sometimes it's the only way to run an app which hasn't "appeared" on gnome-do's database of apps, as well as apps which I can't remember the name of, or even to be reminded of apps I had forgotten about.

---

### Post by NightwishFan on 2009-05-07
Almost anything that requires a plug-in... It seems unintuitive.

Edit: Please note I do like the program, and do use it.

---

### Post by Dougie187 on 2009-05-07
> **NightwishFan said:**
> Almost anything that requires a plug-in... It seems unintuitive.

I agree, things like the music player managers don't seem to work as I would expect.

I do love gnome-do though, I replaced my Alt+F2 with my gnome-do action. So instead of getting a run dialogue I get gnome-do. :)

---

### Post by nothingspecial on 2009-05-07
> **Mazza558 said:**
> I use a panel for window management, functions which gnome-do can't fulfill (notification area), and sometimes it's the only way to run an app which hasn't "appeared" on gnome-do's database of apps, as well as apps which I can't remember the name of, or even to be reminded of apps I had forgotten about.

You can hide your panel fully using gconf-editor, if you like, then use Alt + F1  to bring up your menu. Your notifications will still appear. 

As for running apps, there`s always the terminal + screen.

---

### Post by zeusalmighty on 2009-05-10
I'm sure someone's already asked this, but, is there a way to move all notification area (systray) icons to Docky? That would be really heplful.

---

### Post by Mazza558 on 2009-05-11
> **zeusalmighty said:**
> I'm sure someone's already asked this, but, is there a way to move all notification area (systray) icons to Docky? That would be really heplful.

There's none yet. Even if you could, you have to have at least **one** panel in GNOME (the last panel refuses to be deleted for obvious reasons)

---

### Post by zeusalmighty on 2009-05-11
> **Mazza558 said:**
> There's none yet. Even if you could, you have to have at least **one** panel in GNOME (the last panel refuses to be deleted for obvious reasons)

I was given to understand that there IS a way to delete the last panel, though it's a bit tricky. Right / wrong?

---

### Post by Goombie on 2009-05-11
I've tried to delete that last panel various times, but without success. I just settled for deleting all the applets and mostly hiding it on my desktop. :)

---

### Post by NixNoobSince1999 on 2009-05-23
Made me register to answer this question! bah.

To disable the panel, open up gconf-editor and go to /desktop/gnome/session
edit the required_components_list key and remove "panel" from the list
restart session.

If you need your panel back, just put the entry back in the same spot (or, temporarily, run gnome-panel from terminal or Do)

Note: by removing the panel, Alt+F2 won't bring up Run and Alt+F1 won't bring up a menu.


BTW, this is a very useful tip if you ever find yourself building a gnome-based internet kiosk.

---

### Post by nothingspecial on 2009-05-23
You could always just move gnome-panel out of /usr/bin.

I say move because you might want it back again.

---

