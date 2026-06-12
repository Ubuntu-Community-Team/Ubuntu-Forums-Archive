---
title: "Tool: Gestikk Mouse Gesture Recognition"
date: 2008-01-21
forum: The Cafe
---

### Post by fred.reichbier on 2008-01-21
Hi,

please read [this post](http://ubuntuforums.org/showpost.php?p=4657761&postcount=23) instead of this, old one ;)

-------
i wrote a simple application for mouse gesture recognition called Gestikk. Today I 'released' version 0.4, and I'd likte to introduce it to you :-)

With Gestikk you'll be able to define as many gestures as you want and connect them to a keypress simulator or an application launcher. I wanted to have a simple, friendly interface for it, I hope that task was successfull ;-) There's still no Gesture On-Screen-Painting feature, but I'm working at it.

Gestikk is written in Python 2.5 with wxPython 2.8. A port to pygtk is planned. If you want to simulate key presses, you additionally need [xdotool](http://www.semicomplete.com/projects/xdotool/), an open source tool of Jordan Sissel (not in the repos, but easy to compile).
Installation is quite easy (I hope):
Just install packages *python2.5*, *python2.5-wxgtk2.8* and xdotool.

Project Page is [here](https://launchpad.net/gestikk), the home page is located [there](http://projects.reichbier.de/gestikk/) :)
Please feel free to add bug reports, blueprints or translations.

Please excuse my bad english,

Fred

---

### Post by hype on 2008-01-22
Exellent, i've had some issues when testing, but seems to work ok now.
I had some gesture to open nautilus, tho its not "really" 100% working: i sometime have to re-do the gesture to have it start Nautilus.

It could be nice to be able to redraw the gesture for an existing one.
For now, if i want to re-do the gesture, i have to delete the prvious one and do another gesture.

Promising stuff anyway. :D

---

### Post by KingArthur10 on 2008-01-29
Any chance on getting a compiled deb?  Looks interesting, but I'm having problems making it.

---

### Post by Luffield on 2008-01-29
Very interesting! I hope I'll have time to try it this weekend.
A deb package would be nice, I agree :)

---

### Post by fred.reichbier on 2008-01-31
Hi,

first thanks for your post and feedback.
Yesterday I uploaded the .debs on the [official webpage](http://projects.reichbier.de/gestikk/), compiled for Ubuntu Gutsy. Have fun :)

hype: Conditions are featured in Gestikk 0.5. That means that you can have multiple actions for one gesture, but different conditions (e.g. 'firefox window opened' or 'nautilus is active window') :)

---

### Post by KingArthur10 on 2008-02-01
THANKS!  The compiled DEBs worked perfectly.  I'm having problems with being able to get it to register keypresses as options, though.  Kinda annoying.  I'll check out your site later to see if you have any guidance in editing the config files.

Thanks again, and I hope to use it more in the future.

---

### Post by Luffield on 2008-02-08
I'm having similar problems to KingArthur10. I'm able to launch a program using a command, but keystroke don't seem to work.
Still, it looks promising and I'm looking forward to try the next version.

---

### Post by frup on 2008-02-08
Hey it would be nice if you had the dates each version was released on your site, would be a great way to help casual observers track your progress.

I wish you the best of luck, it looks cool and well done for spotting an area where things needed improvement. I hope to see it in System > Preferences > Mouse or similar one day :)

---

### Post by fred.reichbier on 2008-02-08
Hello,

first thanks for testing and feedback :)
Did you install the xdotool package, too? At the moment it is necessary for simulating keypresses (I want to replace it with a pure-python solution in gestikk 0.5).
Could you try to type 'xdotool' on the command-line?

frup: you can see the date of each release on its page: [click](http://projects.reichbier.de/gestikk/news/gestikk-03/) ;) But I'll create a simple list site, thank you.
Greetings,

Fred

---

### Post by Luffield on 2008-02-08
I think I installed xdotool, IIRC the deb was in the tar.gz file I downloaded from your site.
Here's the output I get::
```
xxxx@luffield:~$ xdotool
usage: xdotool <cmd> <args>
Available commands:
  getwindowfocus
  search
  help
  -h
  click
  key
  keydown
  keyup
  mousedown
  mousemove
  mousemove_relative
  mouseup
  type
  windowfocus
  windowmap
  windowmove
  windowraise
  windowsize
  windowunmap

```

---

### Post by fred.reichbier on 2008-02-09
Hm, xdotool is installed properly. Maybe you have set wrong keys which xdotool doesn't understand.
I give you a few examples ;)
CTRL+T
CTRL+ALT+Escape
CTRL+SHIFT+N
You can test these keystrokes by typing *xdotool key <stroke>* in a terminal. The *xev* tool will help you to find the keynames, for example:
```
KeyPress event, serial 30, synthetic NO, window 0x3600001,
    root 0x8a, subw 0x0, time 4257492194, (206,46), root:(211,94),
    state 0x0, keycode 22 (keysym 0xff08, **BackSpace**), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XmbLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False
```

And if that all doesn't help anything, try to start gestikk in a terminal with the -d option: *gestikk -d* and paste the output :)

Thanks for using,

Fred

---

### Post by Luffield on 2008-02-10
Thanks Fred, xev helped.
I was trying to assign gestures to basic navigation actions in Nautilus, like alt-left for back and alt-up for up. Using xev I realized that I was supposed to use "Alt_L+Up" or "Alt_R+Up" and not just "Alt+Up".
It works pretty well now.

---

### Post by KingArthur10 on 2008-02-12
Thanks for the help.  That works better.  Gotta figure out how to make it work well with small, quick flicks now.

---

### Post by kportertx on 2008-02-27
K so I've made a simple gesture and set it to open the calculator, but its not loading the program, not even giving an error or anything.  Do I need to set the absolute path the the calculator, normally I can just type kcalc and pull it up.  Is there something I have to do to get it to start capturing mouse input?  Its set for when I press ctrl key.

Also is there somewhere I can go for documentation?

Thanks,
Kporter

---

### Post by kportertx on 2008-02-28
Hmm so I got it working... Decided to download the developmental branch from the projects bzr...  Think I may have found a bug in it if anyone would like to confirm,

lines 220 in start_config.py gives me an error and and I to comment everything pertaining to the about button.

Haven't done much gui dev in python so don't really know a better workaround att.  But I may look more into that later :).

BTW this is line 220 in start_config.py on main branch located [https://code.launchpad.net/gestikk](https://code.launchpad.net/gestikk)

Thanks,
Kporter

---

### Post by kportertx on 2008-02-28
O yea the main branch also draws the lines when you are trying to do a gesture, this feature is great.  Does anyone know of a non resource hog for kde and "magic corners" <-- like apple magic corners.  I found Brightside but its for gnome only :*(

---

### Post by fred.reichbier on 2008-02-28
Hello,

thanks for your bugreport here and on launchpad, I'll look after this ;)
The development branch has some 'breaking' changes, first is the paint-on-screen feature, which is not configurable at the moment, and the second is a simple condition script language. Using this, you'll be able to define multiple actions for one gesture, but with different conditions, e.g. if Nautilus is active, a '<----' will do a Alt+Left, if not, it will start the calculator.

And if Gestikk doesn't work, try to start in the console with `gestikk -d` and look for weird output ;)

Greetings,

Fred

---

### Post by lnlds on 2008-02-28
I install gestikk and xdotools, My xdotools is working fine but when I create the action I keep getting 
"Small error, that hasn't much to say (1)"
And my mouse gestures dont do anything. Am i missing an important step?

---

### Post by fred.reichbier on 2008-02-29
Hi,

no, that error shouldn't harm the gestures.
Try this:
 - start gestikk in a terminal with *gestikk -d*
 - use the 'View gesture' feature to see the gesture it recognized
 - look for errors in the terminal
 - change your tolerance value to ~ 20

Greetings,

Fred

---

### Post by lnlds on 2008-03-01
I have some gestures working but when i try to define new ones i get this error

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 14095, in <lambda>
    lambda event: event.callable(*event.args, **event.kw) )
  File "/usr/lib/python2.5/gestikk/start_config.py", line 171, in check_mouse_position
    self.check_gestures()
  File "/usr/lib/python2.5/gestikk/start_config.py", line 128, in check_gestures
    action = dlg.value
AttributeError: 'ActionDialog' object has no attribute 'value'

---

### Post by fred.reichbier on 2008-03-01
Hello,

you're right, that's a little bug in gestikk. You have to select either 'Keypress' or 'Command' in the list on the left, then type the keypress or command in the text entry box on the right, and then press 'Create'.
If you press 'Create' before you have selected an action, this error is thrown.

Greetings,

Fred

---

### Post by lnlds on 2008-03-01
thank you! everything works perfectly now except i can't figure out what the arrow keys are called. RIGHT and LEFT don't seem to work

edit: I used all caps and only the first letter should be uppercase hahah wooo everything works flawlessly now =)

---

### Post by fred.reichbier on 2008-04-05
The gestikk team proudly presents: 
**gestikk "Aaargh!" 0.5**

gestikk 0.5 is completely ported to PyGTK. That means that you won't have to install wxPython anymore.

It has some hot features now:
[list]
[*] On-Screen and on-the-fly gesture painting
[*] powerful condition parsing => define one gesture, but multiple actions
[*] gesture notifications (ballontip / on-screen-display)
[*] a better gesture recognition algorithm
[*] a new logo (thanks to Samsemilia) :)
[/list]

You can also watch a short [demo video](http://gestikk.reichbier.de/downloads/demo-0.5.ogg) of the new version!

Download gestikk 0.5 on the [new official webpage](http://gestikk.reichbier.de) as Ubuntu package or tarball.

Any questions, bugs, blueprints? Post them here or on the [Launchpad project page](https://launchpad.net/gestikk)!

Greetings,

Fred

---

### Post by Luffield on 2008-04-05
Wow, cool!
I'm on Hardy already. Will the deb work? I should I just test it myself?
Heck, I think I won't be able to resist the temptation and test it before you answer :D

---

### Post by fred.reichbier on 2008-04-05
Hello :D

Yes, the package should work under Hardy, too. Could you post whether it worked or not, so I can change the information on the homepage? :)

---

### Post by Luffield on 2008-04-05
Aaargh! :D
OK, I have similar problems to the ones I had when I tested the last version: it works great when I try to start an application, but it doesn't work when I try to do a command like Alt-Left in Nautilus for example. The gestures were recognized, though: I saw it on the notification -- nice touch, I like this feature!
I didn't have time to read the documentation, so the fact that the gestures didn't do anything could well be my mistake.
Another thing: when I had the OSD on, drawing a gesture made the whole screen go black. I have compiz on and I'm using an nVidia card with propietry drivers.
I gotta go now and I don't know if I'll have time to test this version before Monday, but I'm looking forward to try it again, I'm impressed with the progress you've made in this version.

---

### Post by fred.reichbier on 2008-04-05
Aaargh.

You have Compiz on, that should be the problem. Damn, I haven't heard about this problem before - sorry, you may have to turn it off; I will do some research about that -.-

@simulating issues: Use alt**+**Left, not alt-left could help :)

Thank you,

Fred

---

### Post by fred.reichbier on 2008-04-06
Hello,

I released a bug fix release, which should fix the compiz issues: [gestikk 0.5.1](http://gestikk.reichbier.de/uncategorized/gestikk-051).

Please report all bugs.

Greetings,

Fred

---

### Post by Luffield on 2008-04-07
Hi Fred,
The file gestikk-0.5.1-debs.tar.gz seems to be corrupt. Archive Manager is unable to open it, giving this error message:

> gzip: stdin: invalid compressed data--format violated
tar: Child returned status 1
tar: Error exit delayed from previous errors

It's also about half the size of the version 0.5, which seems odd.

---

### Post by fred.reichbier on 2008-04-07
Hello,

Sorry; the deb packages package should be OK now ;)

Greetings, Fred

---

### Post by Luffield on 2008-04-07
Thanks, I'll test it now.
I think that if I find bugs I'll report them on Launchpad, probably that's the right place to do it.

---

### Post by Chokkan on 2008-04-07
Great! I love gestures in Firefox and often find myself using them when I'm using Thunar. This is going to be very useful :)

 I'll have a proper play with this tomorrow and file my bugs too.

Keep up the good work!!

---

### Post by Luffield on 2008-04-07
OK, I'm posting here because I tested version 0.5.1 and I don't think I found any serious bugs. That's good.

Not all is well, though.
I'll start with what seems to be a little bug: when I used the OSD with compiz I got a flash of black screen every now and then, but it was very brief, way under a second. Also the color of the the mouse trail sometimes changed mid-way. Nothing too big, and a huge improvement over yesterday's version :)

A more frustrating thing I found was that Gestikk doesn't seem to work well with Nautilus when I use the default option of right mouse button for gestures (which is what I'm used to from Firefox). Gestures do get recognized, I see them on the notification area, but they usually don't do anything (and they are supposed to do very simple things like ALT+Up or ALT+Left) -- but sometimes they do work, in maybe 10% of the cases. I suspect that it has to do with the fact that Nautilus opens a context menu on the event of right mouse button down, instead of up with is the case with Firefox (and most programs, I think) so it doesn't conflict with the gestures. Strangely, when I configured a gesture for closing a window with ALT-F4, it worked like a charm, always, in any window including Nautilus. I don't think there's much you can do about it, Fred, I guess I'll just have to adjust to using the middle button for Gestikk and the right button for Firefox.

Which leads me to a feature request: when I used the right mouse button for gestures, they conflicted with the Firefox gestures (the gesture I used to close a tab in Firefox was the same gestures I used to close a window on Gestikk, so I closed Firefox accidently a few times). Would it be possible to disable Gestikk when Firefox is the active window?

But all in all, I'm very happy with this version and I will add Gestikk to my session and try to get used to the middle button thing. I think it will work out well.

Great job, Fred!

---

### Post by fred.reichbier on 2008-04-07
Hello,

thanks for your test and your report.
> **Luffield said:**
> A more frustrating thing I found was that Gestikk doesn't seem to work well with Nautilus when I use the default option of right mouse button for gestures (which is what I'm used to from Firefox). Gestures do get recognized, I see them on the notification area, but they usually don't do anything (and they are supposed to do very simple things like ALT+Up or ALT+Left) -- but sometimes they do work, in maybe 10% of the cases. I suspect that it has to do with the fact that Nautilus opens a context menu on the event of right mouse button down, instead of up with is the case with Firefox (and most programs, I think) so it doesn't conflict with the gestures. Strangely, when I configured a gesture for closing a window with ALT-F4, it worked like a charm, always, in any window including Nautilus. I don't think there's much you can do about it, Fred, I guess I'll just have to adjust to using the middle button for Gestikk and the right button for Firefox.
Hm, strange. Maybe it works better if you use CTRL or ALT as gesture switch (just for a test)? I think it's because the pop-up menu. If you do a gesture too slow, as the popup menu is the active window when the action is executed, it doesn't seem to work. But that's only a suggestion.

> Which leads me to a feature request: when I used the right mouse button for gestures, they conflicted with the Firefox gestures (the gesture I used to close a tab in Firefox was the same gestures I used to close a window on Gestikk, so I closed Firefox accidently a few times). Would it be possible to disable Gestikk when Firefox is the active window?
I want to add a 'Global condition' in gestikk 0.6. You could set it on *not activeApplication("firefox")* then :)
> 
But all in all, I'm very happy with this version and I will add Gestikk to my session and try to get used to the middle button thing. I think it will work out well.
Great job, Fred!
Thank you!

Sorry for the count of bugs... I noticed not one of them in my testings before :D

Greetings,

Fred

---

### Post by OrbitEleven on 2008-06-17
I'm having the same problem with context menus canceling out the functionality of Gestikk.  StrokeIt for Windows manages to capture all right clicks and releases them only after the timeout.  Is this possible in Gestikk?  I think WayV is able to do this too.

Otherwise, a promising project!

---

### Post by fred.reichbier on 2008-06-18
Hello!

Today we release gestikk 0.6. Let's do it quickly, the changelog: :D
> - fixed open bugs of gestikk 0.5.1
    - provide a better keypress simulation. We have integrated debug messages 
      and are going to introduce a new keystroke notation style, we call it Gnome-style.
      Before: Ctrl+Shift+W
      Now: <Control><Shift>W
    - a new keystroke assistant, introduced in the hope it simplifies the keystroke building.
    - a new 'Global Condition'. No gesture will be executed unless this condition is True.
    - more window managers supported by using netwm features. All netwm-compilant window managers
      should be working, tested are: Metacity (Gnome), KWin (KDE3/KDE4), xfwm4 (Xfce), Fluxbox, 
      Matchbox, Awesome, WindowMaker, IceWm, Openbox; because of this feature:
    - No dependency on Gnome anymore.
    and, finally
    - a new slogan :-)

We have included all Launchpad translations. Thanks to all contributors!


You do not really have to update if you are happy with gestikk 0.5.1; if you're not, try it ;)

OrbitEleven: We are currently doing some research for this. Thanks for the tip with WayV :)

Enough talky-talky, the download link:

[http://gestikk.reichbier.de/download](http://gestikk.reichbier.de/download)

Thanks again to BigChiller for the packages :)

Any suggestions, bugs, feature requests? :P

Greetings,

Fred

---

### Post by OrbitEleven on 2008-06-18
Can't wait to try it!

Thinking more about it, it seems that some good would come from a merger between the WayV and Gestikk projects.  WayV seems to run at a level that captures gestures well, but is a bear to configure.  Gestikk is much easier to work with, but doesn't quite work (for me) because context menus keep popping up.

If there's anything a PHP/CFML/Java programmer can do, let me know!

---

### Post by Luffield on 2008-06-18
I updated before I noticed the "no need to update if you're happy with 0.5.1" sentence. Well, I'm also happy with version 0.6 :)

---

### Post by Melodic_BM on 2008-06-19
Hello out there, I'm Co-developer (acutally I've got more ideas for features than I can code but fred.reichbier does good coding :P).
Now the thing is that we've written a manual for gestikk (I don't think anybody needs it) and it would be nice if someone could translate this from german to english. I'm afraid of doing this myself because my english is quiet a lil bit ugly ;)

So is there any german and english speaker? Now I could ask this in a german forum but I hope for native speakers here :)

Cheers

---

### Post by fred.reichbier on 2008-06-20
Hello!

First, thanks for your comments! :)

OrbitEleven: Finally, I got it because of your tips. Basicially, I have mapped the popup menu to the Button Release Event, not to the Button Press Event. If the Button Release point is far away from the Button Press point, gestikk should suggest that the user painted a gesture. 
It would be nice if you could try out an [example I wrote](http://paste.pocoo.org/show/74330/) (requires python-xlib). Just run it and press the right click, with or without moving ;) You can kill the script with CTRL+C. 
Please test the X-Server after that (click around, raise Windows, etc.). It worked for me, and it should work for anybody, but I am not completely sure :D

I hope to integrate that in gestikk 0.6 today evening, I'm going to provide a patch for that.

Cheers,

Fred

---

### Post by fred.reichbier on 2008-06-20
Hello again, sorry for the double posting.

the changes are committed in the gestikk-0.6, and I made a patch against gestikk 0.6 for you ;) In order to use it, you have to have python-xlib installed and the XTest X-Server extension enabled (enabled in the common Ubuntu X-Server, afaik). Note that this patch is **really experimental**, and I cannot guarantee that it works - you do that **on your own risk!** If your X-Server freezes or does not react, a X-Server restart (CTRL+ALT+BackSpace) worked for me.
Some words to the patch: If you installed gestikk per package, do the following in a terminal:
```
cd /usr/lib/python2.5/site-packages
wget -q http://gestikk.reichbier.de/downloads/patches/popups_gestikk-0.6-EXPERIMENTAL.patch -O - | patch -p1
```
You should see that output:
> patching file gestikk/start_main.py
patching file gestikk/tools.py
If not, you have made something wrong :D

Now you can run gestikk using `gestikk`. I don't know why, but the status icon won't appear immediately. The solution: Just click and drag around with the right mouse button until the icon appears. Now you can use gestikk like you used it before.

If you notice any bugs, please file them and attach the output of `gestikk -d`.

Cheers,

Fred

---

### Post by crystaldart on 2009-08-24
hai pals,

Just installed Gestikk using the debian file **gestikk_0.6-0ubuntu1_all**.

But I can't see it in the applications menu. Please tell me how to open it.

Thanks

---

