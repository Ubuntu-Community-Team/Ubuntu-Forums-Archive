---
title: "Gnome vs XX  (With a difference!)"
date: 2011-03-28
forum: The Cafe
---

### Post by StephanG on 2011-03-28
I got tired of all the back and forth bickering over which desktop is better.  So I thought that I would try to put another slant on it.  Instead of saying that this or that desktop is 'better' (whatever that means).  I'm hoping that this discussion will get people talking about what they need from a Desktop environment, and perhaps, we can address those needs.

I'm going to say right of the bat that I use KDE, and that I currently find several obstacles to using Gnome.  I'm not going to try and bash Gnome, and I ask that others refrain from bashing as well.  The idea is help people migrate to new desktop environments, not discourage them from doing so.

That said, as a KDE user, there are probably several features in Gnome that I'm not aware of.  If at all possible, please help me to understand how to do those same things in Gnome so that I can set it up to my liking.

Lastly, I want to ask people to keep this discussion about the things that are preventing them from using GNOME.  The reason for this is simply, that I thought it would be awesome if we could start a thread like this for each desktop.  Then after most grievances have been aired, we could start a poll to show which of the named features that the most users want to see in that DE.

So, lets get the show on the road.  These are the first (minor) things that come to mind, when asked why I don't choose Gnome: 

1. Ctrl + Alt + Esc  - I know that a lot of people feel that Linux software shouldn't crash.  But the fact is, it does.  And in Kubuntu, I can just press those three magic buttons and easily, and suprisingly efficiently kill whatever is crashing.  Whether is a game running in W.I.N.E, or accidentally opening a binary file with a word editor, not being able to kill apps is a PitA. Especially if it doesn't show up in the processes section of the system monitor.  Is there an alternative shorcut key used in Ubuntu?  

((BTW, I'm not saying this because of buggy KDE apps that crash on me.  I'm saying this because I've had problems with frozen Gnome apps, in Gnome.))

2. Alt + Click-and-Drag – I incorrectly installed Unity, so I'm not sure how accurate this is. But, there where no panels, just one icon on the desktop.  No problem, I could just click on the one desktop icon (a shortcut to my CD-ROM Drive) and browse to /usr/bin/ start a terminal and log out.  Except there was a decorationless window hovering over the icon.

Like I said, I'm aware of the fact that I acted without thinking, and should have read up on how to install unity in Kubuntu natty, rather than just typing in “sudo apt-get install unity”.  And I'm also not aware if this functionality was broken by my stupidity, but it seems really basic to be able to click anywhere on a window with Alt and drag it around.

3. Desktop Indexing – I know a lot of people don't like this, but I find that KDE's desktop indexing works flawlessly (admittedly after a VERY bumpy start).  And as a student I find it inestimably valuable in searching through all my class notes for a specific concept.  So, if someone could suggest an alternative for Gnome, I would be grateful.

4. Alternative to Krunner -  I'm haven't researched this yet, but Krunner just feels like its light years ahead of whatever it is that pops up on Ubuntu when I press Alt + F2.  It lets me run program, do math calculations, open files, search through my indexed desktop.  Is there something comparable for Gnome I could use?

5. Widgets – I'm not asking for a drop-in replacement of plasmoids, but it would be great to have a simple clock, and maybe CPU and RAM monitors in a corner somewhere.  I know this is possible in Gnome, as I've seen many people do it.  So, if someone could point me in the right direction, it would be appreciated.  (I do know about screenlets.  I'm just wondering if there's an option that doesn't have such an inactive development history.)

6. Keep above/below – A feature, that while not used regularly, seems really basic.  And I have found that its a major annoyance in that handful of cases when you need to keep the window your actively using from covering another, smaller window.

7. Turn Numlock on, on startup.  - I'm one of those idiots that bought a keyboard without an LED light to indicate whether the numlock is on, or off.  On KDE, I can set it to turn on automatically, then I know that its always on, unless I turned it off.  I can't quite seem to find that setting in Ubuntu, so if someone could point me in the right direction, it would be appreciated.  

Then there are several things that I do know how to do in Ubuntu, but still find a bother.  I'm not saying that these things are barriers, just that it would be easier for me to switch to Ubuntu if I didn't have to set them up every time I install a new Ubuntu.

7.1 I already mentioned this somewhere else, but it would be great if Transmission could continue downloads from the system tray after I close it.  I think its kind of self explanatory that things in your taskbar are things that you switch between (i.e. use regularly), and programs like Torrent clients, that you don't want to see until they've finished their jobs, have no place on either my desktop or my taskbar.

7.2 Guake – Now, this is personal preference, so if anyone wants to keep it the way it is, please let me know.  Its just that as far as I'm concerned, the reason I download, and installed a drop down terminal, is because I want to have a terminal within easy reach at all times.  If I'm only going to be using a terminal for one day, I wouldn't have installed it in the first place.  So, having to add it to the start-up application list seems kinda redundant. Shouldn't it do that auto-magically?

Speaking of which, when there's a power outage (Here in SA, our power supply isn't a constant in our lives.  Though it is getting much better) and everything I'm working on is closed.  Shouldn't those apps start up again when I log in again?

And that's all I can think of on the spur of writing this.  So, if anyone can help me overcome some of these barriers, I would be grateful.

And to users of other desktops, what things are preventing you from using Gnome?

P.S.  I tried to make this thread in the Recurring Discussions forum, but apparently I don't have the authority to do that.

---

### Post by 3Miro on 2011-03-28
I am not a Gnome user myself (I stick to XFCE), but this is the best I can do about Gnome.

1. You can use Gnome System Monitor to kill any process. You should also install CCSM (Compiz-Config-settings-manager which will give you a lot more options about managing windows and such).

2. Alt + Drag is a feature in Compiz (Unity is a Dock+Menu for Compiz). Install CCSM. I don't know what is the correct way to install Unity under Kubuntu.

3. Services that I don't need (like desktop indexing) is one of the main reasons for me to run XFCE. I think Gnome 3 (shell and unity) come with some indexing, but I am not sure.

4. I believe the Gnome alternative to Krunner is Gnome-Do.

5. You need Gnome-panel applets. Right-click on the panel and select "add". You can install more applets from the Software Center.

6. Check CCSM, there are literally hundreds of option, I am sure this is somewhere inside. Compiz can be somewhat confusing, the default settings in Ubuntu are rather basic, to get the full functionality, you need CCSM.

7. Try System -> Prefs/Admin -> Keyboard settings.

7.1 Transmission has an option to minimize to the tray (just like ktorrent), you can also use transmission-daemon which becomes a background process completely independent from the graphical environment (you can control it from a web-browser).

7.2 I don't even know what Guake is and auto-magically adjusting my settings is a feature that many of us would not enjoy.

For the power point, there may be a place to adjust the "save-session" options. I don't know.

---

### Post by Sean Moran on 2011-03-28
I'm very happy with the GNOME desktop that came with Karmic.  I've got a nice panel at the top which is always there to tell me the time and date and weather in Rayong, and the processor usage, and all my most-used apps are there, plus the menus on the rare occasions that I need to access them.  I've got a good handle on the wifi sitation at a glance, and can adjust the volume or laptop brightness in a click.

There are three desktops depicted right in the middle of the top panel, so I can be running some maintenance across partitions with Nautilus, and listening to music, and ranting away on a forum, all in separate windows. (If only I could get a desktop with a beer fridge I'd never have to leave the chair).

On the bottom panel there is Wanda the fish and the window list and  garbage bin, but that one hides because I hardly eve need it - I keep my windows nicely placed around the desktops so I can usually always see each titlebar.  Sort of a four-corner cascade system.

The windows are nice for me and my many years stuck with windows95.  I know where to click when I have to, and I don't have to think about that when my mind is 100% occupied on the task at hand.

I wish I could tell you how much I don't like GNOME, but I'd be lying if I did.

---o0o---

PS: I forgot to mention the wonderful little Keyboard Indicator icon up there by my brightness and volume and network indicators.  I have Thai and two different Canadian keyboards installed, and can switch between them so easily, mainly for the simple motive that I can write cafè pseudo-properly when the need arises.  It's these little things that matter when you don't want to be distracted by the incidentals.

---

### Post by Copper Bezel on 2011-03-28
Alt + Drag should be on by default whether you're running Compiz or Metacity. 

The answer to 3 is Tracker. For 4, there are several alternatives made for Gnome's Run Dialog, like Synapse and, yes, Gnome-Do; personally, I opt for something even more basic, XFRun4, but will KRunner not work under Gnome? The answer to 5, such as it is, is Screenlets, such as they are (and they are *not *a drop-in replacement for anything,) and the answer to 6 is to right-click the titlebar. 

Seven might require an xdotool script on startup. For 1, I just use a Compiz binding to xkill.

---

### Post by StephanG on 2011-03-28
Thanks 3Miro, that was very illuminating.

I've looked into it, and can now cross 2, 3 (Will wait for 11.04), 4, and 5 off the list.

1 - But the reason I mention 1, was because the system monitor can be a pain to use if the program I want to close is a run-away CPU user.  Then you have to wait for the sysmonitor to open, scrolling to the process is a pain, unless you've set it to show in order of CPU usage.  And then close it.

The reason I mentioned it, is just that it seemed like it would be really simple to rectify.  The point isn't bash gnome, but to make up a list of simple changes that users of other environments would like to see.

6 - I'll have a look for this one, but couldn't find it last time.  And even if I could, I think it still think its pretty basic and should be easily accessible.

7 - Can't find it.

7.1 - I know it has the option, I'm just putting the idea "out there" to maybe enable it by default.

7.2 - Guake is the gnome version of Yakuake.

Sean Moran - The idea isn't to say how much I hate gnome.  I'm simply trying to create a thread where people can accumulate simple ideas, that would make it that little bit better for them.

If I wanted to talk about hating Gnome, I would have mention the Folderview widget, and other KDE features that would be very difficult to implement.

---

### Post by Sean Moran on 2011-03-28
> **StephanG said:**
> 
Sean Moran - The idea isn't to say how much I hate gnome.  I'm simply trying to create a thread where people can accumulate simple ideas, that would make it that little bit better for them.

That's basically where I was coming from, without meaning to play devil's advocate, but you'd had no responses at the time, and those are the positives of GNOME that I like the most.

---

### Post by StephanG on 2011-03-28
Oh, sorry Sean.

I've just received an SMS using fighting words, so when I read your post I wasn't thinking clearly. And the word 'hate' kinda' made me fear the coming of a flame war.

Thanks though, useful information. i'll definitely look into that indicator app. I still feel that adding a turn numlock on on startup checkbox would be both simple and well within Gnome's philosophy. Though, that said, I just realized that this thread is rather pointless. I completely forgot that Gnome3 & unity/gnome-shell are going to replace gnome 2 anyway. Guess we'll just have to see what the future holds...

---

### Post by 3Miro on 2011-03-28
CCSM should have options to kill an application and/or keep it always on top. CCSM, however, has so many options that finding the one you need can be somewhat hard.

---

### Post by Sean Moran on 2011-03-28
> **StephanG said:**
> Oh, sorry Sean.

I've just received an SMS using fighting words, so when I read your post I wasn't thinking clearly. And the word 'hate' kinda' made me fear the coming of a flame war.

Thanks though, useful information. i'll definitely look into that indicator app. I still feel that adding a turn numlock on on startup checkbox would be both simple and well within Gnome's philosophy. Though, that said, I just realized that this thread is rather pointless. I completely forgot that Gnome3 & unity/gnome-shell are going to replace gnome 2 anyway. Guess we'll just have to see what the future holds...
Stephan, this is actually a thread with some great potential, although the short-term comes back to the micro- scale, of configuration of what is available, but on the macro- scale, you're addressing the issues regarding the improvements and modifications for GNOME4 and other alternatives.  

I took the base-user style by starting out with the simple thngs I like about GNIOME as a long term- Win95 user in the past, (and because some of the points you listed went straight over my head), but here is a place where we might learn what most people like in a desktop, and how to span that chasm to include some of the old-fashioned diehards like me into the mix of the future.  

Brilliant thread, mate.  Let's hope it goes recurring.
:popcorn:

---

### Post by koleoptero on 2011-03-28
> **StephanG said:**
> 1. Ctrl + Alt + Esc  - I know that a lot of people feel that Linux software shouldn't crash.  But the fact is, it does.  And in Kubuntu, I can just press those three magic buttons and easily, and suprisingly efficiently kill whatever is crashing.  Whether is a game running in W.I.N.E, or accidentally opening a binary file with a word editor, not being able to kill apps is a PitA. Especially if it doesn't show up in the processes section of the system monitor.  Is there an alternative shorcut key used in Ubuntu?

((BTW, I'm not saying this because of buggy KDE apps that crash on me.  I'm saying this because I've had problems with frozen Gnome apps, in Gnome.))
Install compizconfig-settings-manager (ccsm), go to commands, edit one of them and set it to run xkill, set the shortcut you'd like on the next tab, you're done.

> **StephanG said:**
> 2. Alt + Click-and-Drag – I incorrectly installed Unity, so I'm not sure how accurate this is. But, there where no panels, just one icon on the desktop.  No problem, I could just click on the one desktop icon (a shortcut to my CD-ROM Drive) and browse to /usr/bin/ start a terminal and log out.  Except there was a decorationless window hovering over the icon.

Like I said, I'm aware of the fact that I acted without thinking, and should have read up on how to install unity in Kubuntu natty, rather than just typing in “sudo apt-get install unity”.  And I'm also not aware if this functionality was broken by my stupidity, but it seems really basic to be able to click anywhere on a window with Alt and drag it around.
Your installation was faulty and the window manager was dead, that's why you didn't have alt+click drag or resize. It's set as such by default.
> **StephanG said:**
> 3. Desktop Indexing – I know a lot of people don't like this, but I find that KDE's desktop indexing works flawlessly (admittedly after a VERY bumpy start).  And as a student I find it inestimably valuable in searching through all my class notes for a specific concept.  So, if someone could suggest an alternative for Gnome, I would be grateful.
Install tracker and you're done with this. It isn't installed by default because it uses massive amounts of ram many people don't have.
> **StephanG said:**
> 4. Alternative to Krunner -  I'm haven't researched this yet, but Krunner just feels like its light years ahead of whatever it is that pops up on Ubuntu when I press Alt + F2.  It lets me run program, do math calculations, open files, search through my indexed desktop.  Is there something comparable for Gnome I could use?
I use synapse, google it. You can also use gnome-do, kupfer (iirc), or even simple gmrun. You can set their shortcut from ccsm as described above for xkill if it isn't available from their preferences.
> **StephanG said:**
> 5. Widgets – I'm not asking for a drop-in replacement of plasmoids, but it would be great to have a simple clock, and maybe CPU and RAM monitors in a corner somewhere.  I know this is possible in Gnome, as I've seen many people do it.  So, if someone could point me in the right direction, it would be appreciated.  (I do know about screenlets.  I'm just wondering if there's an option that doesn't have such an inactive development history.)
Conky? Google conky hardcore. And screenlets development isn't dead, just slow, but they work don't they? Why fix something that isn't broken? And if the default set isn't enough for you go to gnome-look.org and find more.
> **StephanG said:**
> 6. Keep above/below – A feature, that while not used regularly, seems really basic.  And I have found that its a major annoyance in that handful of cases when you need to keep the window your actively using from covering another, smaller window.
Right click on a window's decoration and you'll see it in the menu, as always on top.
> **StephanG said:**
> 7. Turn Numlock on, on startup.  - I'm one of those idiots that bought a keyboard without an LED light to indicate whether the numlock is on, or off.  On KDE, I can set it to turn on automatically, then I know that its always on, unless I turned it off.  I can't quite seem to find that setting in Ubuntu, so if someone could point me in the right direction, it would be appreciated.
I haven't had need for this (I have a laptop) so I can't help you with it.
> **StephanG said:**
> Then there are several things that I do know how to do in Ubuntu, but still find a bother.  I'm not saying that these things are barriers, just that it would be easier for me to switch to Ubuntu if I didn't have to set them up every time I install a new Ubuntu.

7.1 I already mentioned this somewhere else, but it would be great if Transmission could continue downloads from the system tray after I close it.  I think its kind of self explanatory that things in your taskbar are things that you switch between (i.e. use regularly), and programs like Torrent clients, that you don't want to see until they've finished their jobs, have no place on either my desktop or my taskbar.
Transmission does this, I think by default, and you can change it in its preferences if it doesn't.
> **StephanG said:**
> 7.2 Guake – Now, this is personal preference, so if anyone wants to keep it the way it is, please let me know.  Its just that as far as I'm concerned, the reason I download, and installed a drop down terminal, is because I want to have a terminal within easy reach at all times.  If I'm only going to be using a terminal for one day, I wouldn't have installed it in the first place.  So, having to add it to the start-up application list seems kinda redundant. Shouldn't it do that auto-magically?
Tilda?
> **StephanG said:**
> Speaking of which, when there's a power outage (Here in SA, our power supply isn't a constant in our lives.  Though it is getting much better) and everything I'm working on is closed.  Shouldn't those apps start up again when I log in again?
Go to system->preferences -> startup applications, and there's an option somewhere about saving the session. That should be enabled by default I agree.
> **StephanG said:**
> And that's all I can think of on the spur of writing this.  So, if anyone can help me overcome some of these barriers, I would be grateful.

And to users of other desktops, what things are preventing you from using Gnome?

P.S.  I tried to make this thread in the Recurring Discussions forum, but apparently I don't have the authority to do that.
All these things are changes you'll have to do only once, and not every day, so they shouldn't be an impediment to you using gnome. They're just settings you can change. There's no reason to be installing ubuntu THAT often so that default settings should bother you. Unless it doesn't work properly in which case this whole point is moot.

And if you prefer kde there's no reason for you not to use it instead of gnome so just do that.

Hope this helps! :)

---

