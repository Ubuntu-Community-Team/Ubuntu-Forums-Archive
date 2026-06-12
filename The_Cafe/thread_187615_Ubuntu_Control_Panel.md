---
title: "Ubuntu Control Panel"
date: 2006-06-03
forum: The Cafe
---

### Post by curuxz on 2006-06-03
I know this idea has been said before but I really cant see any progress on it, if someone knows of any please post a link. With the web based Ubuntu Centre now being non-ubuntu specifc I think it would be a great time to make a stand.

So unless any one can show evidence of an active project doing the same, Im proposing starting a new peice of software the Ubuntu Control Panel, name and details to be desided later etc...

Basic idea, combine/wrap the functions of the 50 or so programs/utilities that admin Ubuntu linux and make one easy to use application that will help migrating users and pro's alike.

Anyone willing to help out/comment/suggest things to include?

---

### Post by rowanparker on 2006-06-03
I second this, it's a very good idea.

---

### Post by sudomania4 on 2006-06-03
> 50 or so programs/utilities that admin Ubuntu linux
which programs? like the "change desktop background" "system volume control" "keyboard" "mouse", and basically everything else under the "system" menu at the top gnome-panel?

---

### Post by Stone123 on 2006-06-03
all i read in your post is "make it your self project". I think it would be good thing if you start it i ll help out (if buy that you mean server-vise controll panel )

---

### Post by curuxz on 2006-06-03
[QUOTE=sudomania4]which programs? like the "change desktop background" "system volume control" "keyboard" "mouse", and basically everything else under the "system" menu at the top gnome-panel?[/QUOTE]

Amoung other things yes, im also talking about putting GUI on lilo/grub configs, Xorg.conf etc

One of the big stregths of Windows and distros like SUSE (with YAST) is their config programs are intergrated and easy to use. Linux has always had strength in the right tool for the right job approach and im not looking to get rid of that but I think we need a program that saves us time and im willing to spearhead its development for those that want it. IF its wanted and hopefully with help from others since it will be a big and slow project for just me.

---

### Post by sudomania4 on 2006-06-03
OK, like the windows control panel, where they have akmost EVERYTHING you can edit in one place...

---

### Post by curuxz on 2006-06-03
exactly.....but better :)

---

### Post by papangul on 2006-06-03
There is a view that it is more productive to access the control panel items directly from 'System' menu rather than clicking on the 'control panel' item in a menu and then waiting for it to start up. 

My idea is to have a tab like thing on the panel like the tabs of virtual desktops; when it is clicked, the control panel opens up instantly like a virtual desktop. But to achieve that, the control panel has to be loaded in memory during gnome startup, so the startup time will increase and more memory will be blocked. But I don't think these are issues with contemporary hardware. Or a option might be provided so that people with less powerful machines can disable the feature.

---

### Post by curuxz on 2006-06-03
Well my idea was to keep the current way of being able to go directly to specific items from the start menu but do it the same way the KDE control centre works, ie instead of having items in the system menu that link to diffrent applications they link to the diffrent pages of the Control panel, and just like KDE control centre you can chose to load the whole program and do multiple admin tasks, that way it remains quick and acessable while being usable as a replacement for windows control panel for those used to doing things that way around.

Saying that, loading the whole thing to the tray could be an option for those that want an instant click pop-up version like your suggesting, tho I will need help doing stuff like that.

---

### Post by Carrots171 on 2006-06-03
I don't like the "classic view" of the Windows control panel. There are so many little icons everywhere that it's hard to find what you want to click on. I like the system menu in Ubuntu better.

However, I think that it would be great if something like [mission control]("http://shots.osdir.com/slideshows/467/35.gif") was implemented

---

### Post by curuxz on 2006-06-03
[QUOTE=Carrots171]I don't like the "classic view" of the Windows control panel. There are so many little icons everywhere that it's hard to find what you want to click on. I like the system menu in Ubuntu better.

However, I think that it would be great if something like [mission control]("http://shots.osdir.com/slideshows/467/35.gif") was implemented[/QUOTE]

Now you see thats exactly what im thinking off, mission control style make it easy and the users will follow.

Please please, if you can program or help out in anyway PM me lets get this going most of the work is already done all we need to do is design a cool interface, which I can take care off in under a week, and then hack the scripts to respond to the interface all the admin tools exist its just a case of bringing them all together peice by peice.

---

### Post by MetalMusicAddict on 2006-06-03
In case you guys didnt know, press Alt+F2 then enter **gnome-control-center**.

---

### Post by curuxz on 2006-06-03
yes im aware of that same with KDE having one, but it not good enough by any standard, Its features need to be incorperated but the list of stuff it CANT do is endless. We need to put and end to this process of having to ask newbies to post xorg config files or type so and so command. Ubuntu just works but its admin is just not there we wont something that is as easy to use as the whole of the distro :)

---

### Post by BanskuZ on 2006-06-03
Good idea.

---

### Post by Zyphrexi on 2006-06-03
hmm I was considering something like that as well, but I despise gnome-control-panel and windows control center. I found KDE intuitive, and think something along those lines would be better. Everytime I go to System, I feel overwhelmed by the amount of listings in one place. But I have anxiety disorders among other fun disorders, so I may be a minority.

Usually I just end up putting commonly used items on my taskbar, but it can get crowded.

---

### Post by curuxz on 2006-06-03
[QUOTE=Zyphrexi]hmm I was considering something like that as well, but I despise gnome-control-panel and windows control center. I found KDE intuitive, and think something along those lines would be better. Everytime I go to System, I feel overwhelmed by the amount of listings in one place. But I have anxiety disorders among other fun disorders, so I may be a minority.

Usually I just end up putting commonly used items on my taskbar, but it can get crowded.[/QUOTE]

Well what if you took the KDE control centre, Gnome control centre, windows control panel and YAST and mixed em up taking all the good features, then extended it to cover things like Xconfiguration, Grub management, maybe even things like Apache and MySQL support down the line since they killed Webmin in Dapper im lacking a good admin console for all my server side stuff as well as my desktop admin tasks.

Thats the dream, it cant be that hard so I have asked one of the mods to make a third party room for it and as soon as we have that we can get to work on a road map, prioritise the features and see who wants to do what and how.

---

### Post by curuxz on 2006-06-09
While there has been many places asking for this feature I have still not had that many pm's about it nor has the admin's setup a third party forum for it despite others getting theirs. I understand your busy but when your doing it for other people who asked after me it seems a little fustrating,

Im officaly recending my request for a room on this forum and im publicaly stating why, its not much to pm back saying yes or no esp when you are helping others...

Over the weekend I'll give the project its own site and if their is intrest so be it, if not then hey at least I tried.

regards.
A disapointed curuxz

---

