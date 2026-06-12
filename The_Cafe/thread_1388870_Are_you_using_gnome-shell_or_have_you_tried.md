---
title: "Are you using gnome-shell or have you tried ?"
date: 2010-01-23
forum: The Cafe
---

### Post by MooPi on 2010-01-23
I've been using gnome-shell for two days now and find it very useful and light on the resources. I've read complaints and don't know why beyond the lack of good documentation. Took a day to sift through page after page of gnome shell reviews and gnome live info to get enough knowledge of how it works and tips and tricks.
[IMG]http://ubuntuforums.org/%3Ca%20href=http://s559.photobucket.com/albums/ss36/MooPii/?action=view&current=2010-01-23-164200_1680x1050_scrot.png%20target=_blank%3E[IMG]http://i559.photobucket.com/albums/ss36/MooPii/th_2010-01-23-164200_1680x1050_scrot.png[/IMG][[IMG]http://i559.photobucket.com/albums/ss36/MooPii/th_2010-01-23-164200_1680x1050_scrot.png[/IMG]]("http://s559.photobucket.com/albums/ss36/MooPii/?action=view&current=2010-01-23-164200_1680x1050_scrot.png")

---

### Post by ankspo71 on 2010-01-23
I tried it in Karmic, but now that I am using Lucid testing, I am unable to use it because it isn't ready to be installed according to synaptic.

My opinion of it. I like the looks of it, and I can get used to it very quickly. But when I tried it and put it in my start up applications, I had no way to access any system menus or my gnome panels. For that reason, I think it needs some more features, like a button to minimise it to access the panels and menus, or a 'complete' menu set-up so I can access system menus. Until that happens, I find to be less productive than the regular gnome desktop. It ran fine though, and looked good too. It has good potential also...


Lol, now that I just checked, synaptic says it can be installed now. I'll give it another try and see if any features have been added.

Edited: Thanks to Moopi's help, I can find the control center now.

---

### Post by MooPi on 2010-01-23
The system menu is hidden in the upper right hand corner and activated by mouse click. Actually it is a drop down of Gnome Control Center.

---

### Post by ankspo71 on 2010-01-23
Hi,
So that's where it was hiding!!!... I'm embarrassed now.](*,)lol.
Okay this will make it MUCH more productive now.
I'm using it as we speak. So far so good. 
And yes, I just found the control center. :P 
thanks for the showing me where it was.

---

### Post by d3v1150m471c on 2010-01-23
I don't see anything in the top corner of my screen except my desktop background lol... what is this again?

---

### Post by ankspo71 on 2010-01-23
Hi,
Is gnome shell running? If not Press Alt + F2  then type the command ```
gnome-shell --replace
``` or you can use the same command in the terminal.

When it starts, you can access the control center by clicking on your name in the upper right corner.  A drop down menu will appear after you click on your name

I have to be in a full desktop view, not "activities" view (the multi-desktop view), for the drop down menu to work for me though.

---

### Post by d3v1150m471c on 2010-01-23
cool thanks. :)

---

### Post by Mornedhel on 2010-01-23
Tried it on Karmic.

Waiting for the devs to add a way to *remove* workspaces when you've added one too much. Also 24h time.

I am not comfortable with the order the windows are presented in when you alt-tab. Overall, not very keyboard friendly.

Meh.

---

### Post by scottuss on 2010-01-23
This thread inspired me, so tonight, I installed Gnome Shell onto my Karmic netbook (EEE 701)

Wow! It runs so smoothly (more so than the standard desktop, would you believe?)

Plus, the workflow of having different work spaces for different activities is very logical, and works really well on this small screen.

---

### Post by k64 on 2010-01-23
Enjoy:

---

### Post by k64 on 2010-01-23
> **Mornedhel said:**
> Tried it on Karmic.

Waiting for the devs to add a way to *remove* workspaces when you've added one too much. Also 24h time.

I am not comfortable with the order the windows are presented in when you alt-tab. Overall, not very keyboard friendly.

Meh.

If you want to remove a workspace, hover over it and click on the (-) icon. Presto! It has been removed.

---

### Post by MooPi on 2010-01-24
Looks like more and more folks are trying Gnome-shell. I personally think it is an improvement and for the betterment of Gnome desktop. Shell on brothers ! :P

---

### Post by k64 on 2010-01-24
> **MooPi said:**
> Looks like more and more folks are trying Gnome-shell. I personally think it is an improvement and for the betterment of Gnome desktop. Shell on brothers ! :P

Agreed. It is GNOME enhanced with Clutter to its benefit.

Personally, when I install GNOME, I always install GNOME Shell and set "gnome-shell --replace" as a startup application. This makes it your default window management app.

Even though GNOME Shell uses Metacity as a window manager, there is one clear difference: In GNOME Shell, Metacity is enhanced with Clutter. In GNOME Panel, it isn't.

For others' record: [Please try it out for yourself]('apt:/gnome-shell')

---

### Post by rliegh on 2010-01-24
I'm trying right now, and I'm not sure what I think. I think it's a great way to handle virtual desktops, but there's little things that bug me (having no way to delete recent documents, the fact that virtualbox doesn't like it) -it looks promising, though; and I can easily see myself being used to it by the time it becomes mainstream.

---

### Post by ElSlunko on 2010-01-24
I did try it and I thought it was okay but it didn't work with one of my key apps so I didn't test it much. I have the latest version installed via ppa and it just crashes so I haven't tested in quite a while.

---

### Post by Nevon on 2010-01-24
If I go ahead and install it, does it mess with my current gnome desktop at all? I would like to try it, but I'm not sure I'm willing to risk my current workspace.

---

### Post by k64 on 2010-01-24
> **Nevon said:**
> If I go ahead and install it, does it mess with my current gnome desktop at all? I would like to try it, but I'm not sure I'm willing to risk my current workspace.

First of all [GNOME Shell]('apt:/gnome-shell'), when run, automatically migrates all your apps. No, GNOME Shell does not kill the apps. It simply enables compositing on the XServer (xserver-xephyr), runs Mutter, and gets rid of the second panel. Not too mention, it also enables such effects as RGBA and transparency. It does NOT kill your apps in the process.

---

### Post by MooPi on 2010-01-24
> **rliegh said:**
> I'm trying right now, and I'm not sure what I think. I think it's a great way to handle virtual desktops, but there's little things that bug me (having no way to delete recent documents, the fact that virtualbox doesn't like it) -it looks promising, though; and I can easily see myself being used to it by the time it becomes mainstream.
I found a solution to eliminate recent documents. Not a big fan of this feature to begin with as I know what I've been doing and don't need a reminder.Solution : Create text file if not already present, ```
.gtkrc-2.0
```Add this line of code: ```
gtk-recent-file-max-age=0
```Upon restart recent documents will be disabled.

---

### Post by Starlight on 2010-01-24
Gnome-shell should be nice when it's finished, but right now it doesn't seem to have an easy way to switch between applications. And the top panel and menus don't follow the GTK theme and colors, so they look rather out of place on my desktop...

---

### Post by markinf on 2010-01-24
I really hope that gnome-shell get's better, because I've tried and I really disliked. I want my panels back!!!

---

### Post by ElSlunko on 2010-01-24
I really wish they had gone with a shelf design instead of the overlay.

---

### Post by l-x-l on 2010-01-24
I tried it a while back. But it was unstable & not fully functional. Hopefully much of that has changed.

---

### Post by rapidog on 2010-01-24
I tried Gnome Shell about 3-4 months ago form the Ubuntu repositories. :( Like pulling teeth.

---

### Post by ankspo71 on 2010-01-24
Hi,
Does anybody know of a way to get the panel of gnome-shell to appear on the bottom of gnome-shell, instead of on the top? 
Thanks.

---

### Post by ibuclaw on 2010-01-24
> **ankspo71 said:**
> Hi,
Does anybody know of a way to get the panel of gnome-shell to appear on the bottom of gnome-shell, instead of on the top? 
Thanks.

The answer is, we are not sure.

But, the panel is a plugin, plugins can be loaded/unloaded freely in Gnome-Shell (at least, that is what the Devs have implied though my ignorance of looking it up). And since they are all in JS, that should give you a better head start than what you were certain of before you asked.

Regards
Iain

---

### Post by k64 on 2010-01-24
> **ankspo71 said:**
> Hi,
Does anybody know of a way to get the panel of gnome-shell to appear on the bottom of gnome-shell, instead of on the top? 
Thanks.

I suggest diving into /usr/share/gnome-shell/js/ui and seeing if there's a setting for panel position.

---

### Post by ankspo71 on 2010-01-24
Thanks tinivole and k64

I'm reading through the js code in /usr/share/gnome-shell/js/ui now.

---

### Post by k64 on 2010-01-24
> **ankspo71 said:**
> Thanks tinivole and k64

I'm reading through the js code in /usr/share/gnome-shell/js/ui now.

What you would do is edit the panel.js file to add the following line at the end:

```
Panel.Position = "Bottom"
```

---

### Post by rliegh on 2010-01-25
> **MooPi said:**
> I found a solution to eliminate recent documents. Not a big fan of this feature to begin with as I know what I've been doing and don't need a reminder.Solution : Create text file if not already present, ```
.gtkrc-2.0
```Add this line of code: ```
gtk-recent-file-max-age=0
```Upon restart recent documents will be disabled.

Sounds exactly like what I'm looking for --Thanks very much! :guitar:

---

### Post by Roasted on 2010-01-25
> **markinf said:**
> I really hope that gnome-shell get's better, because I've tried and I really disliked. I want my panels back!!!

In the few short weeks I've used Gnome Shell I've seen quite a few improvements that really helped out usability of Gnome Shell.

Is it there yet? Not quite.
Will it be? It's Gnome. I'm sure they'll pull something out of the hat. :P

---

### Post by Roasted on 2010-01-25
> **rapidog said:**
> I tried Gnome Shell about 3-4 months ago form the Ubuntu repositories. :( Like pulling teeth.

The version from the repos is old and sucks.

Run this:

sudo add-apt-repository ppa:ricotz/testing

To add the latest PPA for it. Then

sudo apt-get install gnome-shell

It'll pull down the PPA, which is updated frequently whereas the repo version is not.

I would base your judgment on the PPA. Not the repo version.

---

### Post by icyzer on 2010-02-20
> **Roasted said:**
> The version from the repos is old and sucks.

Run this:

sudo add-apt-repository ppa:ricotz/testing

To add the latest PPA for it. Then

sudo apt-get install gnome-shell

It'll pull down the PPA, which is updated frequently whereas the repo version is not.

I would base your judgment on the PPA. Not the repo version.

After I had the repo version installed I liked it allot to be honest. But the PPA version is worse. I really hope they are not going to keep it as it is now. It's just counter productive :(

---

### Post by Roasted on 2010-02-20
> **icyzer said:**
> After I had the repo version installed I liked it allot to be honest. But the PPA version is worse. I really hope they are not going to keep it as it is now. It's just counter productive :(

I really have -no- idea what you're talking about. I can't think of a single thing from the repo version that's better than the PPA version. But hey, to each his own...

---

### Post by ubudog on 2010-02-20
I have not tried and am probably not going to try it.

---

### Post by regeya on 2010-02-20
I've tried it, and I guess I'll be the contrarian and say I love it so far!  I have to admit, though, that some habits are hard to unlearn; I've had a taskbar ever since Windows 95 came out, and about the only time I've not had one is in OS X. :D  Seriously, even when I used Window Maker almost exclusively several years ago, I kept the window list pinned.  I suppose there'll be a way to write a plugin for the thing in GNOME Shell if there isn't one already, but aside from that, this is looking pretty sweet!

---

### Post by icyzer on 2010-02-20
> **Roasted said:**
> I really have -no- idea what you're talking about. I can't think of a single thing from the repo version that's better than the PPA version. But hey, to each his own...
In the repo version there is still the 'big' + icon to add a workspace and a 'big' - icon on the workspace to remove it. Whilest in the PPA version there are these miniscule little - and +buttons. Just one little difference that really annoys me. Though the PPA version has the X buttons on applications to close them from the shell window, that's cool.

And what's up with the 'Available' 'busy' and 'invisible' status in the usermenu? 

How can you see which version of Gnome-shell you got installed and which are in the repo's/PPA?

Has anyone seen any themes around by the way? There is a theme-folder in the gnome-shell folder, that would suggest it's possible to make theme's. And I've seen wallpapers on the back of the gnome-shell activities windows on youtube, but nowhere how it's done. Apart from editing the .css file I guess.

This version of Gnome-shell looks good too, wonder which version it is?
[http://mairin.wordpress.com/2010/02/10/gnome-shell-usability-test-plan/](http://mairin.wordpress.com/2010/02/10/gnome-shell-usability-test-plan/)

---

### Post by techno-mole on 2010-02-20
i havent seen any themes, i have however been thinking about how to add themes to gnome shell, most people that use it may well want to customize it.

ive played around with the css, and the image files, its not too much trouble to adjust the images, colours, sizes etc and the css is easy enough, i havent quite figured out what it all does as yet.

i think it would be easy enough to have theme folders, and either a main theme folder in the usr/share/gnome-shell/theme or rename it to usr/share/gnome-shell/themes and then place each theme into that folder, or have a system when users can drag and drop theme files (like you can with the appearances as they are in gnome, least that how i do it)

but then what do i know, im not a developer.

PS - open synaptic and type gnome shell in the search bar at the top, you should see the entry for gnome shell about halfway down, it should tell you what version it is, the version im running is - 2.28.1~git20100220-0ubuntu1~9.10~ricotz

---

### Post by icyzer on 2010-02-20
> **techno-mole said:**
> i havent seen any themes, i have however been thinking about how to add themes to gnome shell, most people that use it may well want to customize it.

ive played around with the css, and the image files, its not too much trouble to adjust the images, colours, sizes etc and the css is easy enough, i havent quite figured out what it all does as yet.

i think it would be easy enough to have theme folders, and either a main theme folder in the usr/share/gnome-shell/theme or rename it to usr/share/gnome-shell/themes and then place each theme into that folder, or have a system when users can drag and drop theme files (like you can with the appearances as they are in gnome, least that how i do it)

but then what do i know, im not a developer.

PS - open synaptic and type gnome shell in the search bar at the top, you should see the entry for gnome shell about halfway down, it should tell you what version it is, the version im running is - 2.28.1~git20100220-0ubuntu1~9.10~ricotz
Oke I got the latest then... Still think the smaller + and - icons really suck :(

Other than that I really LOVE gnome-shell, but only when combined with Docky for windows switching.

---

### Post by juancarlospaco on 2010-02-20
[**Click here to see my Gnome-Shell with Murrine enabled RGBA.**]("http://img64.imageshack.us/img64/7773/tempx.jpg")
*...also im using Gnome-Journal*

---

### Post by Roasted on 2010-02-20
> **icyzer said:**
> In the repo version there is still the 'big' + icon to add a workspace and a 'big' - icon on the workspace to remove it. Whilest in the PPA version there are these miniscule little - and +buttons. Just one little difference that really annoys me. Though the PPA version has the X buttons on applications to close them from the shell window, that's cool.

And what's up with the 'Available' 'busy' and 'invisible' status in the usermenu? 

How can you see which version of Gnome-shell you got installed and which are in the repo's/PPA?

Has anyone seen any themes around by the way? There is a theme-folder in the gnome-shell folder, that would suggest it's possible to make theme's. And I've seen wallpapers on the back of the gnome-shell activities windows on youtube, but nowhere how it's done. Apart from editing the .css file I guess.

This version of Gnome-shell looks good too, wonder which version it is?
[http://mairin.wordpress.com/2010/02/10/gnome-shell-usability-test-plan/](http://mairin.wordpress.com/2010/02/10/gnome-shell-usability-test-plan/)

Ah yes, you got me there. I do miss the large + icon very much. However, this is something that has been addressed to the devs and I'm sure they will change it. Just keep in mind, this software is in what.. alpha? pre alpha? 

There will be more to come I'm sure. For right now stabilizing it seems to be the main focus (despite the fact its relatively stable considering its status). Once that's finalized, I'm sure people will customize the ever loving **** out of it. :)

---

### Post by PhoHammer on 2010-02-20
I just installed gnome shell and I love it. It reminds me more of Mac OS X 10.6's UI for some reason (maybe the fact that the top-left corner does that thing, which is how I have my bottom-left set up in Mac OS, exposes or something?). 

Great work, Gnomies. Keep it up!

---

### Post by icyzer on 2010-02-21
> **Roasted said:**
> Ah yes, you got me there. I do miss the large + icon very much. However, this is something that has been addressed to the devs and I'm sure they will change it. Just keep in mind, this software is in what.. alpha? pre alpha? 

There will be more to come I'm sure. For right now stabilizing it seems to be the main focus (despite the fact its relatively stable considering its status). Once that's finalized, I'm sure people will customize the ever loving **** out of it. :)
yea it sure is stable for an alpha :)

Are you using it with an dock or something? Because I can imagine that the critics who use it without such enhancement hate it :)

Too bad I've got no experience what so ever with .css and .js :)

---

### Post by macaz1 on 2010-02-21
> **k64 said:**
> Enjoy:

Miley Cyrus, :?

---

### Post by Viva on 2010-02-21
Can you install it in Karmic without disrupting GNOME too much? Is it possible to uninstall it without losing any settings?

---

### Post by icyzer on 2010-02-21
> **Viva said:**
> Can you install it in Karmic without disrupting GNOME too much? Is it possible to uninstall it without losing any settings?Yes, just do this:

sudo aptitude install gnome-shell (either from the repo's or the add the PPA first)
and then gnome-shell --replace. When you don't like it just log out or quit the terminal.
When you do like it, add gnome-shell to the startup list.

Beware though, disable all eye-candy and stuff like nitrogen before you do. Otherwise it won't work properly :)

---

### Post by dragos240 on 2010-02-21
I've heard so much about this. Emerging it right now.

---

### Post by Viva on 2010-02-21
> **icyzer said:**
> Yes, just do this:

sudo aptitude install gnome-shell (either from the repo's or the add the PPA first)
and then gnome-shell --replace. When you don't like it just log out or quit the terminal.
When you do like it, add gnome-shell to the startup list.

Beware though, disable all eye-candy and stuff like nitrogen before you do. Otherwise it won't work properly :)

Thanks. I installed it. It looks good, but is there anyway I can configure it? I can't see any settings manager to change the theme and behaviour.

---

### Post by icyzer on 2010-02-21
> **Viva said:**
> Thanks. I installed it. It looks good, but is there anyway I can configure it? I can't see any settings manager to change the theme and behaviour.
It's still alpha and there is no 'easy' way of customizing it with a settings manager. You can however edit the .css and .js files to customize it :)



I had to remove gnome-shell, I really loved it but it got my GPU up to 97 degrees Celcius, idle. To bad...

Hope the next build works better...

---

### Post by gnomeuser on 2010-02-21
I tried the g-s several times including forcing myself to use it for long periods of time. However I still don't agree with the technical decisions nor to I find it an improvement over the gnome2 shell in any significant way to warrant the project. 

I wouldn't describe my feelings as murderous like the poll suggests, the gnome-shell is implemented by long term members of the Linux community who have before this given us very useful technology. I would though perhaps suggest we lock them up for an evaluation period to see if they regretably were driven insane by one or more factors. I think not so much about the horrid impact of the g-s itself but before we know what drove these otherwise wellbalanced and talented developers to design and implement it we risk it happening to someone else.

---

### Post by Post Monkeh on 2010-02-21
> **k64 said:**
> Enjoy:

hmm, kenny strawn eh?

---

### Post by PhoHammer on 2010-02-23
> **Roasted said:**
> The version from the repos is old and sucks.

Run this:

sudo add-apt-repository ppa:ricotz/testing

To add the latest PPA for it. Then

sudo apt-get install gnome-shell

It'll pull down the PPA, which is updated frequently whereas the repo version is not.

I would base your judgment on the PPA. Not the repo version.

The repo version flaked out on me (my pointer started disappearing if I hovered on the panel) so I just installed this PPA version. Much better! I'm loving this shell of the Gnome!

---

### Post by swoll1980 on 2010-02-23
Where's the option for no haven't got around to it? "No with no plans to" is the only option for people that haven't tried it yet. That's a little harsh don't you think?

---

### Post by PhoHammer on 2010-02-26
Just got the update from that ricotz/testing PPA, and it's coming
 along nicely! Cool new additions, like ripple effect when you hit
 the top left corner to reveal your spaces. It also includes a 
stylish, large icon in the panel area that tells the name of the 
active application. And!! there's a nice change to the notification
 popup, which now comes up at the bottom.

Gnome shell is now even more reminiscent of many of Mac OS X 10.6's
 UI goodies, but also original in its own way.

Here's a screenie of the new update:

---

### Post by BrokenKingpin on 2010-02-26
It was horribly slow on my system for some reason, to the point I could barely use it.

---

### Post by PC_load_letter on 2010-02-26
Tried it from the Rico Tzschichholz's PPA. I'm running Karmic 64bit. When I type **gnome-shell --replace**, the icons on my desktop disappear, along with the menu bar, but I don't see anything else. No overlay, no GS menu bar, nothing!

I can probably post about the problem, and find a solution, but too I'm too busy & lazy to do it. Maybe I'll wait till it's released.

---

### Post by Woolio1 on 2010-02-26
Well, this redefines the desktop. We're used to taskbars and menubars and all sorts of things. If you look at Windows 7, theirs takes up a good inch of your screen! Here, however, we have this tiny strip across the top. Click the strip, it takes you outside of the workspace to the launcher.

Excellent thinking, implemented well. And this, my friends, is the future. Not some silly icon-launching-nomultitasking tool.

I hate Apple's ideas, I hate Microsoft's implementations... In the Open Source World, I find perfection.

---

### Post by Roasted on 2010-02-26
> **Woolio1 said:**
> Well, this redefines the desktop. We're used to taskbars and menubars and all sorts of things. If you look at Windows 7, theirs takes up a good inch of your screen! Here, however, we have this tiny strip across the top. Click the strip, it takes you outside of the workspace to the launcher.

Excellent thinking, implemented well. And this, my friends, is the future. Not some silly icon-launching-nomultitasking tool.

I hate Apple's ideas, I hate Microsoft's implementations... In the Open Source World, I find perfection.

I agree. And while I do think Gnome Shell needs some work, I actively use it on my work laptop, which has proven to be relatively stable despite its alpha (or pre alpha?) state it's currently in.

It's very remarkable. I still want to see a few features added before I'll use it *exclusively* (such as a logical task/application switcher on screen) but it's progressed quite a bit so far. I'm anxious to see what they bring to the table tomorrow, next week/month/etc.

---

### Post by samjh on 2010-02-26
I've tried it, and don't like how it is *at the moment*.

Like KDE 4, it holds a lot of promise.  But like KDE 4, it will need time to mature.

Some negative points I've experienced:
[list][*]There is no way to quickly find and select opened (or minimised) windows on a desktop.  Alt-tab is tedious, and using the application menu is slow and convoluted.  The great thing about the traditional task-bar interface is that you can immediately see and select any window with one glance and a click, rather than numerous Alt-tabs or click-wait-search-click.
[*]Why shrink the entire desktop just to open an application or access the main menu?  It's a waste of resources, disorienting to users, and a completely unnecessary change of paradigm.
[*]The top bar is useless.  It displays only the date, the name of the active application, and the preferences menu.  It could be used for other useful things, like a list of opened tasks.[/list]

That list is just a small set of the most obvious issues.  There are many others, like disappearing mouse cursors, and other bugs, but I accept that they will be fixed in time.

---

### Post by gjoellee on 2010-02-26
It is a new idea, but it will never be functional as it is now. The concept just does not work!

---

### Post by gsmanners on 2010-02-26
What's the point in making a poll like that? How about just "yes" or "no"?

My answer is "no" because when people complain, you're invariably told that this is alpha-quality software, and you really shouldn't expect it to work. Never mind the fact that if you wait until it's beta, you'll be told that you should have complained earlier and helped steer their feature decisions.

This is probably why so many larger, more complicated projects are a bad idea. If you invite criticism and then fend off complaints merely because the project isn't finished, then people are going to get discouraged and not help you make your project better.

---

### Post by Woolio1 on 2010-02-26
> **gsmanners said:**
> What's the point in making a poll like that? How about just "yes" or "no"?

My answer is "no" because when people complain, you're invariably told that this is alpha-quality software, and you really shouldn't expect it to work. Never mind the fact that if you wait until it's beta, you'll be told that you should have complained earlier and helped steer their feature decisions.

This is probably why so many larger, more complicated projects are a bad idea. If you invite criticism and then fend off complaints merely because the project isn't finished, then people are going to get discouraged and not help you make your project better.

O RLY?

Sorry, just couldn't resist. :P

---

### Post by Jekshadow on 2010-02-26
Still a few memory leaks. I left my computer on for a week and its memory usage had grown to about 1.2GB. Other than that, it has been great.

I prefer KDE's look, but GNOME has always been more stable and reliable for me.

---

### Post by n0dix on 2010-02-27
just no. I don't want to try.

---

### Post by oedipuss on 2010-02-27
> **samjh said:**
> I've tried it, and don't like how it is *at the moment*.

Like KDE 4, it holds a lot of promise.  But like KDE 4, it will need time to mature.

Some negative points I've experienced:
[list][*]There is no way to quickly find and select opened (or minimised) windows on a desktop.  Alt-tab is tedious, and using the application menu is slow and convoluted.  The great thing about the traditional task-bar interface is that you can immediately see and select any window with one glance and a click, rather than numerous Alt-tabs or click-wait-search-click.
[*]Why shrink the entire desktop just to open an application or access the main menu?  It's a waste of resources, disorienting to users, and a completely unnecessary change of paradigm.
[*]The top bar is useless.  It displays only the date, the name of the active application, and the preferences menu.  It could be used for other useful things, like a list of opened tasks.[/list]

That list is just a small set of the most obvious issues.  There are many others, like disappearing mouse cursors, and other bugs, but I accept that they will be fixed in time.

I find it works best with the addition of a dock, like docky+gnome do or awn. For a new user setting that up could be tricky though, unless it comes with a reasonable default dock.  

Perhaps the intention was to encourage each app in its own workspace, so shrinking the current workspace kind of disconnects the app launcher with the single workspace paradigm, or forces you to acknowledge multiple desktops. I dunno really... 

The top bar *is* rather useless isn't it? I hope there's at least the option of changing its size, later on, and move that calendar to a corner.. I hate how it's in the middle. 

I've been using the ricotz/testing ppa too, checking it periodically, and sometime recently animations became very slow =/ Moving windows is fine, even between desktops, but zooming in and out happens at 3 frames or so :(

Also, what's with the application categories being gone, in recent builds from ricotz/testing ? Now it shows all the apps in one big icon view mess... I guess there must be a way to change that but I haven't used it that much to actually care.

---

### Post by 23meg on 2010-02-27
> **gsmanners said:**
>  If you invite criticism and then fend off complaints merely because the project isn't finished, then people are going to get discouraged and not help you make your project better.

One point to note is that the people who invite criticism and those who fend off complaints "because it's alpha" are almost invariably different people.

---

### Post by Foxmike on 2010-03-01
Just for your information guys, a more efficient way to make gnome-shell start with the session is to set the windowmanager key in gconf to it like this (in a terminal):
```
gconftool-2 -t string -s /desktop/gnome/session/required_components/windowmanager gnome-shell
```

This will start gnome-shell in place of compiz (or whatever window manager your have chosen), instead of loading it over it.  That means reduced loading time, do to loading of compiz, then, gnome-shell.

If anyone is using this method, then reverting it is easy:
```
gconftool-2 -t string -s /desktop/gnome/session/required_components/windowmanager gnome-wm
```

For your information, I'm using Gnome-Shell exclusively since a month, and I have no plan to switch back to anything else soon.  Just having a way to dynamically manage my workspaces is a must!  I realize that I'm usually using only one workspace, but when needed adding a second (or a third) one is so easy.

---

### Post by fanum on 2010-03-09
> **gjoellee said:**
> It is a new idea, but it will never be functional as it is now. The concept just does not work!

I have been using it for the last month, on my main machine (with several hiccups along the way), but have throughly enjoyed it. It took about a week to get used to (good, full week) but since then, i have found the application menu not only functional, but a better implementation of virtual desktops, then in the previous gnome. As far as features that are not there yet, there are many of them. And they are slowly emerging into the shell with every update. Other than there being no categories in the application menu (which really does not bother me that much, as the search function, is so functional) I really dont see any down sides. And the categories (from what i have read) will be available through an old gnome style menu available through the desktop, without needing to even enter the activities menu. 

I encourage everyone to keep in mind, there is a reason that gnome shell being the standard UI has been put off several times so far. It is a revolutionary idea, and very new code, that is trying to envision not only what we are trying to use our computers for now, but what the trends are when it comes to new technologies, and where they may be goin over the next several years. Seeing into the future is difficult, but i think they are doing a great job. 

Since it is so early in development, we also have the chance to help shape its future. If there is something that you think they are missing, or something that has been overlooked, join us on IRC and share your ideas irc.gnome.org/gnome-shell

---

### Post by Madspyman on 2010-03-09
Gnome-shell is a more original idea than Lucid Lynx is shaping up to be. I can't wait till all the bugs are worked out.

---

