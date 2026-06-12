---
title: "Breezy Colony 3 Review"
date: 2005-08-23
forum: The Cafe
---

### Post by poofyhairguy on 2005-08-23
Breezy Colony 3 Review

Well, yesterday I looked at OSNEWS and saw a Hoary review and thought to myself "thats a little old to be reviewed." Many of the comments complained about a lack of a good Breezy preview, so I thought I would make one. This is my review of the Breezy Colony 3 release. Please remember that this is just my opinion, I don't know a lot about the under the hood changes, so this is mostly a superficial review (the kind I would want to read).

I have to say that overall...I hate to say this but...Breezy has kinda disappointed me. Just because its not as big of a jump on the surface between Warty and Hoary (in my opinion). There are hints at a lot of under the hood stuff, and I can only review the stuff you can actually see (most reviewers are like this).  I guess it would only be fair to give the good and the bad, so I'll do it that way. 

The good first:

The first thing I noticed about Breezy is that fonts are a little different. I would say better, but someone might debate that. 

Secondly, Breezy now has a "Boot Manager Settings" tool which allows you to pick what OS you want by default to boot, how long you want for grub to show and those sorts of things. Its less powerful than the grub manager on the forum but its still neat.

Thirdly, Breezy has a "disks manager" tool that allows you to see all of you disks. It will tell you how full a disk is, what format its in (ext3 ,ntfs) and what its properties are (read, read write, etc). Unfortunately this tool kinda disappointed me. From what the tool shows you, you think that you can use it to mount ntfs disks (as opposed to using the ubuntu guide's way) but when I tried I failed. Also, this tool doesn't do the big thing I wanted it to do- allow the user to turn on DMA through a GUI tool. You still have to touch the command line to do that in Breezy.

Fourthly as of the Colony 3 Breezy is still pretty stable so its workable. The xserver problems that I have read about in the forum did not affect me.

Fifthly, There is a new "services settings" tool. This tool allows you to pick what services start when your computer starts. Its pretty neat. I never knew that my computer booted with fetchmail, but I'm glad I can make it not. This tool is my new favorite part of Breezy.

Sixth, (this one I didn't notice at first, don't know why) is a "about me" tool that allows you to do something neat: easily change you password with a GUI. Very nice. The name made me think it was a different thing than it was, but its cool that can be done with a GUI too.

Finally, there is a "multimedia systems selector" too. This thing allows you to chose the input and output source for audio and video. No more killall esd! A very nice improvement. I think this tool hints at the important under the hood changes in Breezy. In a superficial review like this one, thing like this get downplayed.

The bad:

First bad thing for me was the installation. I have broadband, and because of that it seems that the damn installer wants to download updates if it can detect that you have a fat pipe. The problem is that the day I installed it the Ubuntu server was down (I know because I wanted to upgrade to Breezy) and so it got to a certain point and just hanged. I'm an impatient man, so I rebooted. I was happy to find out that I was booted into the login screen, but when I logged in and tried to do something with apt-get it told me the thing was locked up. I knew that I had put mirrors in my sources.list, so I didn't know what was wrong. I restarted my xserver only to find that Breezy was still trying to install itself underneath, and it was hung up and the same point. I wasn't able to get into synaptic until the next day, when the main Ubuntu server was back online. If the server can't take a Colony release, the day of the official release is gonna suck if the installer still insists on downloading updates. I recommend anyone installing Breezy unplug their broadband till the installation is over.

Secondly, besides the fonts I don't see any visual improvements in Breezy. No wobbly windows or nothing. Despite all the noise about Cairo, corners still look pixelated and there is not more visual bling than in Hoary. Metacity still does the draw black crap all over my screen thing, and even worse now when my computer gets pegged (aka my CPU is maxed out) whatever Window is maximized is replaced by complete blackness when you try to minimize it. I hope that is fixed before the final release, or the beginner forum will be filled with "how do I disable this black feature" posts.

Thirdly, I didn't get what I really wanted for Christmas. The savior for all Metacity woes (xcompmgr) is still really unstable. It still produces garbage when Xine is playing full screen yet gstreamer can't use w32codecs yet so there is no way around it. Xcompmgr still crashes when I leave it on over night. The lack of an improvement in the area almost made me cry.

Fourthly, Openoffice just won't work. It would rather crash than open the writer. I hope that is fixed. And I can't get the new "gnome-app-install" tool to work at all. Not from the menu, not with gksudo. 

Fifthly I can't figure out how to edit the menus without smeg. So I just installed smeg....but wasn't there supposed to be something else? Also there is no GUI way to edit your xorg.conf yet that I can find.

Finally, Breezy took away my "run dialog." I loved that thing because I could start a program or kill the gnome-panel without opening a terminal. It will be missed.

Basically, as you can tell I'm disappointed. And before you jump on me and say "its the development release!" let me say that I know...I was reviewing the Colony 3. Many of the bugs might be fixed...I'll file a few bug reports myself. The problem is that the feature freeze has come and gone, and what I really wanted is not here. Sigh.

I will say that Breezy is more stable than I thought, so I would say if you have been holding back jump in and help bug test. Personally, the Colony 3 has shown me one thing- I better learn to love KDE. :) I hear the 3.5 version is bringing improvements in the kcompmgr, sounds tasty. One day Metacity will fall, and I will dance a jig on its grave when it does.

Have a nice day.

EDIT: *Slaps forehead* I try to write a superficial review but I forgot a fun new eye candy. When tasks want to be clicked on in the taskbar, they kinda glow. Its better than a hard blink, and I would faint if they ever give you a way to control the color that glows (yellow would kick ass there). Also the default nautilus is better....much needed I say.

EDIT 2: I thought about it, and I remembered that if I read this review, I would want screenshots, so here they are:

1. Bootmanager tool

[http://img295.imageshack.us/img295/9199/bootmanager1op.png](http://img295.imageshack.us/img295/9199/bootmanager1op.png)

2-4. Disk tool

[http://img161.imageshack.us/img161/1458/disktool10wo.png](http://img161.imageshack.us/img161/1458/disktool10wo.png)

[http://img297.imageshack.us/img297/1772/disktool16os.png](http://img297.imageshack.us/img297/1772/disktool16os.png)

[http://img297.imageshack.us/img297/6353/disktool23sx.png](http://img297.imageshack.us/img297/6353/disktool23sx.png)

5. multimedia systems selector

[http://img117.imageshack.us/img117/7546/mulitmediatool0py.png](http://img117.imageshack.us/img117/7546/mulitmediatool0py.png)

6. Service tool

[http://img161.imageshack.us/img161/1094/servicestool0iv.png](http://img161.imageshack.us/img161/1094/servicestool0iv.png)

7. Password tool:

[http://img84.imageshack.us/img84/556/password8za.png](http://img84.imageshack.us/img84/556/password8za.png)

All those people that complained about Ubuntu's lack of GUI will like this release I think....

EDIT 3: One really nice thing is that Evince is the default document handler. It does a really good job, especially with PDFs.

---

### Post by poofyhairguy on 2005-08-23
Note: I just did a big edit. In my first version I forgot to mention some new  GUI tools. These tools are the best part of Breezy (its obvious that development work went into these) so its not fair if I leave them out. In fact, after playing with them more, I must admit I like Breezy a bit more as well. If I can find someway to add back the run dialoge, I'd be a happy man.

---

### Post by drizek on 2005-08-23
[QUOTE=poofyhairguy]Note: I just did a big edit. In my first version I forgot to mention some new  GUI tools. These tools are the best part of Breezy (its obvious that development work went into these) so its not fair if I leave them out. In fact, after playing with them more, I must admit I like Breezy a bit more as well. If I can find someway to add back the run dialoge, I'd be a happy man.[/QUOTE]
 Hint: Press Alt+F2 and see what happens.

---

### Post by poofyhairguy on 2005-08-23
Me begging for run dialog back:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=14047](http://bugzilla.ubuntu.com/show_bug.cgi?id=14047)

---

### Post by poofyhairguy on 2005-08-23
[QUOTE=drizek]Hint: Press Alt+F2 and see what happens.[/QUOTE]

I keep pressing it...what should I expect to happen? It does nothing in Firefox, and nothing in a clean desktop. Let me upgrade out of Colony 3 and try again.

---

### Post by drizek on 2005-08-23
[QUOTE=poofyhairguy]I keep pressing it...what should I expect to happen? It does nothing in Firefox, and nothing in a clean desktop. Let me upgrade out of Colony 3 and try again.[/QUOTE]
 for me, it brings up the run dialog. it works in breezy, but not in hoary.

---

### Post by Knome_fan on 2005-08-23
1. Nice review
2. You should do an upgrade. Some of the issues have been fixed (at least for me)
OpenOffice2 and the complete blackness were caused by a cairo upgrade if I understood it correctly. As there are now new version build against this cairo releas, the problems should be solved. 
3. About smeg. Strange that it wasn't there. At least for me it was installed by default and according to BreezyGoals it should be.
4. If I understand it correctly, cairo doesn't have much to do with the bling you expected, but at least on my ibook the fonts and the general rendering has improved dramatically with cairo. Also, we should wait till the first themes come out that actually make use of cairo, from what I read about it I think they will be very nice.
5. Personally, from what I can say playing around with it now for a few days, I think breezy is a very nice improvement, but certainly not mindshattering, at least from what one sees on the outside (of course there's amazing stuff going on on the inside, changing to the new gcc and to modularized X for example). And unfortunately, some things I was really looking forward to, like network-manager and gnome-power-manager don't seem to make it in.

Edit:
Just tried it. Alt+F2 brings up the run dialogue here too.

---

### Post by jobezone on 2005-08-23
Poofyhairguy, the dozen of active ubuntu developers can only do so much (is this number correct?), and the graphical new tools for editing grub and managing disks are a good step in the right direction. I liked your review, I was looking for one which clearly explained the new changes.

 P.S.-Is there a wifi applet thingy? I know wifi works (a friend of mine managed to configure his just by installing the driver, and configuring it in the Network configuration dialog), just wanted to know if one of the various applets for detecting wifi networks is pre-installed.

---

### Post by poofyhairguy on 2005-08-23
[QUOTE=drizek]for me, it brings up the run dialog. it works in breezy, but not in hoary.[/QUOTE]

It seems that you might be correct, look at the attacked image. It just doesn't work for me for some reason....hmm....I'll chalk that as a bug (so it can/will probably be fixed) and thank you for showing me that its not gone forever.

---

### Post by poofyhairguy on 2005-08-23
[QUOTE=jobezone]Poofyhairguy, the dozen of active ubuntu developers can only do so much (is this number correct?)[/QUOTE]

Actually....its seems most of my problems are not problems that are the devlopers fault. It seems that many problems are do to the fact that for some reason Breezy's universe and multiverse maybe did not sync with Sids completely...or that packages in the universe don't work (bittornado....one of my favorite programs....does not work!).

For example, Zsnes is still at 1.36, but 1.4 has been in Sid for a long time. Interesting.

---

### Post by a-nubi-s on 2005-08-23
> Originally Posted by **poofyhairguy**
I better learn to love KDE.  [[IMG]http://x2.putfile.com/8/23413193923.png[/IMG]](http://www.putfile.com)   isn't *that* bad and Kubuntu really *is* one of the better laid-out ones. I think you might find what you want in KDE *if* you give it the same chance you've given Gnome and keep an open mind about it.

---

### Post by poofyhairguy on 2005-08-23
[QUOTE=jobezone]P.S.-Is there a wifi applet thingy? I know wifi works (a friend of mine managed to configure his just by installing the driver, and configuring it in the Network configuration dialog), just wanted to know if one of the various applets for detecting wifi networks is pre-installed.[/QUOTE]

I don't have wireless on this comp, so I can't if the network tool has changed. The network monitor applet seems the same.

---

### Post by poofyhairguy on 2005-08-23
[QUOTE=a-nubi-s][[IMG]http://x2.putfile.com/8/23413193923.png[/IMG]](http://www.putfile.com)   isn't *that* bad and Kubuntu really *is* one of the better laid-out ones. I think you might find what you want in KDE *if* you give it the same chance you've given Gnome and keep an open mind about it.[/QUOTE]

Its cool I have the option honestly. The best thing about Ubuntu is its great package selection. And the overall packages are 1000+ more according to synaptic.

I have been spreading a lot of kubuntu lately. I think people deserve to know about it too. I don't really dislike KDE, its just that I like GTK programs more usually. I can change though.

---

### Post by poofyhairguy on 2005-08-23
Added Screenshots

---

### Post by Corlian on 2005-08-23
I'm sure there's a more appropriate place to discuss the details, but since I'm reading them here --

I'm relieved that services program is in there.  As a new Linux user, I feel a little helpless as far as reducing boot times, plus Linux users are always talking about how streamlined things are, but I've had no way of checking it for myself.  I suppose someone will say I'm too stuck in a GUI mentality, but I'm happy to free up resources just to use them up again with interface options that please me.

---

### Post by poofyhairguy on 2005-08-23
[QUOTE=Corlian]I'm sure there's a more appropriate place to discuss the details, but since I'm reading them here --

I'm relieved that services program is in there.  As a new Linux user, I feel a little helpless as far as reducing boot times, plus Linux users are always talking about how streamlined things are, but I've had no way of checking it for myself.  I suppose someone will say I'm too stuck in a GUI mentality, but I'm happy to free up resources just to use them up again with interface options that please me.[/QUOTE]

Its my favorite new thing.

---

### Post by poofyhairguy on 2005-09-05
I just wanted to give an update:

A lot of work has been done in short time! Many problems I went on about have been fixed- the only major bugs I now have is programs randomly dying (no warning) and the fact that Metacity now has a "move an ugly black box to the taskbar" when you minimize "effect".

If fact, I got what I wanted for Christmas. After playing with Breezy a bunch, I figured out a few things.

First of all....Totem has come a long way! A LONG way! It went from being the thing I replace as soon as I install Ubuntu to being my favorite media player of all time. IT has GREAT Xinerama support...and....(this almost made me cry when I found it out)- IT NOW WORKS FULL SCREEN WITH XCOMPMGR!!!!!! Its the only Xine that does that...

Because of this, I did what I wanted to do for a while- made it so that xcompmgr starts when my computer logs in. I turned off drop shadows (they are too buggy) and if I could give up the fading effect I bet the whole deal would be stable!!! No more window redraw problem for me! As it is, I keep the fading effect and even though it still crashes (seeing as how xcompmr hasn't been worked on since 2004), Breezy is a lot better at handling crashes. The new Openoffice.org2 + Firefox with the session saver extension makes the xserver crashes tolerable (for me....many would disagree).

So I am no longer disappointed. Breezy is much better. People with Nvidia cards can finally have a modern desktop, and new users that need GUIs will love the new ones. The add/remove program thing is especially easy to use (so easy I personally will never use it).

Life is good. Santa Claus is real. Makes me want to cry!

---

### Post by TravisNewman on 2005-09-05
two things--

The multimedia system selector has been around since warty (at least hoary). I haven't had to do a killall esd in ages.

Second, I'm really pretty impressed with the superficial things in Breezy. Usplash is awesome, but the run application being gone is a little upsetting. I just added an applet to the panel to bring it up. And alt-f2 does work well for me, but I miss the old way too. I like how gksudo darkens the rest of the screen. The improvements to the update manager and add/remove programs are great. The under-the-hood stuff (on the laptop front at least) is much better too. Better suspend/hibernate (though that's borked for me at the moment)/function key support. Breezy finally has a built in audio-cd creator (serpentine). Mounted disks show up on the desktop again. They brought back the old spatial (that was a big sticking point with some), though they did change the default to "always use browser windows" checked.

It's great on this end, and relatively few bugs.

---

### Post by TravisNewman on 2005-09-05
[QUOTE=Corlian]I'm sure there's a more appropriate place to discuss the details, but since I'm reading them here --

I'm relieved that services program is in there.  As a new Linux user, I feel a little helpless as far as reducing boot times, plus Linux users are always talking about how streamlined things are, but I've had no way of checking it for myself.  I suppose someone will say I'm too stuck in a GUI mentality, but I'm happy to free up resources just to use them up again with interface options that please me.[/QUOTE]
 my one disappointment here is that it doesn't show everything that starts.

---

### Post by poofyhairguy on 2005-09-05
[QUOTE=panickedthumb] They brought back the old spatial (that was a big sticking point with some), though they did change the default to "always use browser windows" checked.
[/QUOTE]

And we will watch the "Nautilus sucks" complaints go away. 

I have had it explained to me 1000 times, and I still can't get why anyone likes spatial mode!

---

### Post by Kvark on 2005-09-05
[QUOTE=poofyhairguy]Fifthly, There is a new "services settings" tool. This tool allows you to pick what services start when your computer starts. Its pretty neat. I never knew that my computer booted with fetchmail, but I'm glad I can make it not. This tool is my new favorite part of Breezy.[/QUOTE]
Great, as a normal user I feel very powerless about whats started and ran in the background. I guess it's good to have to learn more before being able to mess with system critical services. But it's great to see an easy way to control non system critical things like fetchmail you mention, the clock synching, etc.

---

### Post by TravisNewman on 2005-09-05
[QUOTE=poofyhairguy]And we will watch the "Nautilus sucks" complaints go away. 

I have had it explained to me 1000 times, and I still can't get why anyone likes spatial mode![/QUOTE]
 I adore spatial :)

---

### Post by poofyhairguy on 2005-09-05
[QUOTE=panickedthumb]I adore spatial :)[/QUOTE]

I know. Some people do.

The biggest benefit of spatial from what I have heard is "if you know nothing about computers its more natural." Yet even people leik yourself that are geeks love it too.

I get so frustrated with it personally....I miss me tree view quickely.

---

### Post by Weav on 2005-09-05
Oh i'm probably going to be disappointed, I was looking forward to new themes icons, and hughe GUI advancements and some sweet new eyecandy. Oh well i guess i will continue to wait maybe KDE will do something revolutionary...

---

### Post by poofyhairguy on 2005-09-06
[QUOTE=Weav]Oh i'm probably going to be disappointed, I was looking forward to new themes icons, and hughe GUI advancements and some sweet new eyecandy. Oh well i guess i will continue to wait maybe KDE will do something revolutionary...[/QUOTE]

Sounds like what you want is KDE 4:

[http://www.canllaith.org/svn-features/kde4.html](http://www.canllaith.org/svn-features/kde4.html)

It seems many of the Breezy improvements are under the hood (better sound support and things like that).

---

### Post by Wolki on 2005-09-06
[QUOTE=poofyhairguy]I know. Some people do.

The biggest benefit of spatial from what I have heard is "if you know nothing about computers its more natural." Yet even people leik yourself that are geeks love it too.

I get so frustrated with it personally....I miss me tree view quickely.[/QUOTE]

A brief introduction why the idea of spatial is good and important is here:

[http://juicability.blogspot.com/2005/09/top-8-reasons-hci-is-in-its-stone-age.html](http://juicability.blogspot.com/2005/09/top-8-reasons-hci-is-in-its-stone-age.html)

Point 6. Note that unfortunately the way in which Gnome implements spatial is - in my opinion - not the optimal solution and would need a lot of work. It's still probably the best one we currently have.

Another thing I like about it is that it is so simple. When I use a file manager, I want to do stuff with files - open them, move them somewhere, drop them into an application, whatever. With spatial mode, there's nothing distracting me from my files. No tree requires additional attention, there's not a lot of buttons, no sidebars or anything. Just me and the things i need to interact with. It feels natural, and that translates to comfort and speed.

It would be really helpful to have advanced control of windows, though.

---

### Post by poofyhairguy on 2005-09-06
[QUOTE=Wolki] When I use a file manager, I want to do stuff with files - open them, move them somewhere, drop them into an application, whatever. .[/QUOTE]

I think all file managers suck at this. Thats why I can't wait for a polished beagle.

---

### Post by Wolki on 2005-09-06
[QUOTE=poofyhairguy]I think all file managers suck at this. Thats why I can't wait for a polished beagle.[/QUOTE]

I'm not so sure about this. Sure, Beagle has it's purpose and one it's more polished it will be really useful. But searching has limits and problems. It means that you have to think about how to ask your query, so that it will find the file you want (ie not make it so specific it won't find it anymore) and not too much more (so you won't spend a lot of time serching your search results for a certain result). You'll have problems with typos and memory errors. It will make you switch between keyboard and mouse, something that is often necessary but takes time and complicates the process.

And, last not least, often it's simply not needed. If I want to read these great forums, I'll open Firefox and use a bookmark, or type ubu and choose [www.ubuntuforums.org](www.ubuntuforums.org) from the list firefox offers me, or just type the adress. I usually don't open google first, search for ubuntuforums, read the results and click the link I think will lead me here. Why add that step?

It's similar with file access. I may know that a file is at "Mouse into the lower left corner, click, mouse up to the middle of the screen, target on icon, click, move up and right, target on icon, click, move to the middle of the screen, choose file." Sounds complicated, but it's really easy since there's little thinking involved and even reading has been greatly reduced. Mentally automating a task and building "muscle memory" are great things, and computers should be designed for that.

---

### Post by mrtaber on 2005-09-06
I really appreciate all the good work they've done on Breezy.  However, the one thing I miss, that I catch myself trying to use multiple times a day, is right-clicking into a terminal.  

I vaguely remember that in Gnome, one can create a .Template folder somewhere, and add blank documents to it, that will show up in the context menu.  I might be able to do this with a terminal document, too, I guess.

Otherwise, things are looking pretty fine.  (A blue-based theme would be a nice touch, for those who don't care for brown).

Mark :)

---

### Post by escuchamezz on 2005-09-06
[QUOTE=poofyhairguy]And we will watch the "Nautilus sucks" complaints go away. 
[/QUOTE]

thank god for that, Nautilus seriously suckers

---

### Post by Wolki on 2005-09-06
> **mrtaber]I really appreciate all the good work they've done on Breezy.  However, the one thing I miss, that I catch myself trying to use multiple times a day, is right-clicking into a terminal.  [/quote]

Hehe... How many folders did you accidentally create? I didn't count, but it's approximately 5 each day since i switched to breezy. ^^ said:**
> Otherwise, things are looking pretty fine.  (A blue-based theme would be a nice touch, for those who don't care for brown).

Isn't a blue one installed by default, too? Anyway, blue themes are really boring and ugly. Human is a nice theme that grows on you, but i've seen lots of others with good colors in many shades. There's so many beautiful colors and non-colors in the world, why should computers all use the same one?

[edit] quote fixed

---

### Post by poofyhairguy on 2005-09-06
[QUOTE=Wolki]I'm not so sure about this. Sure, Beagle has it's purpose and one it's more polished it will be really useful. But searching has limits and problems. It means that you have to think about how to ask your query, so that it will find the file you want (ie not make it so specific it won't find it anymore) and not too much more (so you won't spend a lot of time serching your search results for a certain result). You'll have problems with typos and memory errors. It will make you switch between keyboard and mouse, something that is often necessary but takes time and complicates the process.
[/QUOTE]

For some. Personally my home drive is like my home-a mess. It would be nice to have a way around that problem.

---

### Post by Wolki on 2005-09-06
[QUOTE=poofyhairguy]For some. Personally my home drive is like my home-a mess. It would be nice to have a way around that problem.[/QUOTE]

I wish there was something that cleaned my room (and my home dir) automatically... Thank god there are things that help you take care of your home dir, that's why I have that one far more cleaned up ^^;;;

One thing i do is have clutter folders and sorted stuff... my home is usually quite cleaned up. Now the downloads folder (and everything new data goes, like stuff i ripped) can get pretty messy, but occasionally i just go through it and delete/move most of the stuff in there. If you do it regularly it's quite easy and rather quickly done. And a little clutter is good, as long as I still have a basic idea where everything is.

I'm planning to try setting the home directory as desktop soon. I basically have my stuff sorted in each, so combining them should make the structure only more clean. And having everything that ends up in home on the desktop will encourage me to take care of it and putting it in a sensible place.

Hm... some years ago, i never did anything with my desktop, except putting soemthing there rarely when i didn't know where to put it. Now I use it as the main entrance to my file system... must be that conveniently placed "show desktop" button in Gnome :)

---

### Post by mrtaber on 2005-09-07
Hey Wolki, thanks for the info.  :)  I'm a happier camper. 

And actually, *I* like brown...for some reason, though, many people find that it doesn't look "professional."  

Thanks again,
Mark :)

---

### Post by poofyhairguy on 2005-09-08
My lecture about Breezy and xcompmgr:

[http://slashdot.org/comments.pl?sid=161495&threshold=0&commentsort=0&tid=131&tid=99&mode=thread&pid=13505790#13506790](http://slashdot.org/comments.pl?sid=161495&threshold=0&commentsort=0&tid=131&tid=99&mode=thread&pid=13505790#13506790)

---

