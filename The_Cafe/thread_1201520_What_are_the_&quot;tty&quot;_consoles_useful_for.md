---
title: "What are the &quot;tty&quot; consoles useful for"
date: 2009-07-01
forum: The Cafe
---

### Post by jward3010 on 2009-07-01
What I'm referring to of course are the 6 consoles that can be accessed by pressing "Ctrl + Alt + F1, F2, F3,...". I have a couple of questions in relation to this.

1. First of all what are they still used for when you can have multiple terminals open in your X session (GNOME Desktop).

2. How do they interact with each other i.e. if one console has a problem can you use another console to kill the app, and how do you do it. 

3. The above could be useful for unstable X sessions and GUI's, like killing "gdm" or "gnome-panel" but as I've successfully killed "stuff" (using killall) I find I can't start them again in the the same tty console (I get "can't find display"). Is there anyway you can direct a command from, say tty3 to run on tty7 so you can get your desktop started again.

---

### Post by tarps87 on 2009-07-01
1) They have many uses one example is on servers where there is no graphical environment, you can also stop the graphical environment form running on boot if you only require command line tool and then boot the graphical environment when you need it

2) You can, either by killall as you have stated below or using ps -A to list all the processes followed by kill *processId*

3) In the case of Ubuntu where the root account is disabled it is possible you will see this message if you try to start it with super user permissions.
If this is not the case have you tried startx?

---

### Post by Mornedhel on 2009-07-01
> **jward3010 said:**
> 1. First of all what are they still used for when you can have multiple terminals open in your X session (GNOME Desktop).

They're not really used anymore on desktops, but it's nice to have them if you need the equivalent of multiple workspaces/terminal emulators if for some reason you borked your X server, for instance.

> **jward3010 said:**
> 2. How do they interact with each other i.e. if one console has a problem can you use another console to kill the app, and how do you do it.

It's exactly the same as having multiple terminal emulators (gnome-terminal instances) running. Try it : open a tty session, log in, return to the graphical session, open a gnome-terminal, type who. You should have something like this :

```

username tty1         2009-07-01 14:44
username tty7         2009-07-01 10:42 (:0)
username pts/0        2009-07-01 10:44 (:0.0)
username pts/1        2009-07-01 14:48 (:0.0)
```

pts/* are your terminal emulators, tty7 is your graphical session, tty* are your console sessions. You can use console sessions separately as you would use gnome-terminal instances separately and you can kill processes from a console to another.

> **jward3010 said:**
> 3. The above could be useful for unstable X sessions and GUI's, like killing "gdm" or "gnome-panel" but as I've successfully killed "stuff" (using killall) I find I can't start them again in the the same tty console (I get "can't find display"). Is there anyway you can direct a command from, say tty3 to run on tty7 so you can get your desktop started again.

That's more than one question. I am not that familiar with the subtleties of console sessions, and I'm afraid I can't answer that, sorry.

---

### Post by jward3010 on 2009-07-01
Hey, thanks both for your quick replies. It makes sense now. Mornedhel, you mentioned terminal emulators (pts*) - what are they?

---

### Post by jward3010 on 2009-07-01
I love coming on this forum and adding a whole pile of new useful commands to my repetoire:

"ps -A" and then "kill"
"who" for tty consoles

Thanks, I'll have fun with them when I get back from lunch - how sad am I!

---

### Post by Mornedhel on 2009-07-01
They're what gnome-terminal and xterm and others use to emulate a console. It's what you've been using from the start. Basically, it's a file (in /dev/pts*) that your terminal does input/output from to mimic the functionality of a real console.

If you liked who, try w.

---

### Post by tarps87 on 2009-07-01
> **Mornedhel said:**
> ...If you liked who, try w.

What about the one for the forgetful, whoami :)

oh and no really a command

apt-get moo

aptitude moo
aptitude -v moo (just keep adding v's)

---

### Post by jward3010 on 2009-07-01
> **Mornedhel said:**
> They're what gnome-terminal and xterm and others use to emulate a console. It's what you've been using from the start. Basically, it's a file (in /dev/pts*) that your terminal does input/output from to mimic the functionality of a real console.

If you liked who, try w.

So the tty screens are the real consoles and pts's are a virtual connection to them for gnome-terminal etc. It's interesting thinking of an OS as a something that treats everything as a file - My hard disk is a big file that you pump stuff into.

---

### Post by jward3010 on 2009-07-01
> **tarps87 said:**
> What about the one for the forgetful, whoami :)

oh and no really a command

apt-get moo

aptitude moo
aptitude -v moo (just keep adding v's)

My favourite is "apt-get moo". I hadn't even mooed today and needed the reminder.

---

### Post by lykwydchykyn on 2009-07-01
> **jward3010 said:**
> 
3. The above could be useful for unstable X sessions and GUI's, like killing "gdm" or "gnome-panel" but as I've successfully killed "stuff" (using killall) I find I can't start them again in the the same tty console (I get "can't find display"). Is there anyway you can direct a command from, say tty3 to run on tty7 so you can get your desktop started again.

You can restart X on tty7 using the gdm init script, like so:
```

sudo /etc/init.d/gdm restart

```

If you have a running session, you can launch applications on it by setting the DISPLAY environment variable, like so:
```

export DISPLAY=:0
xterm

```
That would launch an xterm in your GUI session on tty7 from any other tty. You have to be the same user (or have authority to launch apps in the other user's session -- that's another ball of wax).

Of course if you have multiple X sessions running (e.g., one on tty7, one on tty9), you would set DISPLAY to :0, :1, :2 etc respectively.

---

### Post by scorp123 on 2009-07-01
> **jward3010 said:**
>  1. First of all what are they still used for when you can have multiple terminals open in your X session (GNOME Desktop).  Try that on a server where no GUI is installed ... ;)

> **jward3010 said:**
>  2. How do they interact with each other i.e. if one console has a problem can you use another console to kill the app, and how do you do it.  I think that one has been answered? Commands you may wish to experiment with:
```

who
w
ps -efH
kill *PIDofProgram*
pkill *nameOfProgram*
pkill -u *nameOfUser*
killall *nameOfProgram*
...
```

> **jward3010 said:**
>  3. The above could be useful for unstable X sessions and GUI's Bingo.

> **jward3010 said:**
>  I find I can't start them again  You have to use the proper start scripts. Most of them are underneath this location: **/etc/init.d**

... And they need "root" priviledges to run.

So the proper way to get GDM started again would be something like:
```
sudo /etc/init.d/gdm restart
```

Also, for some historical background info, you might be interested to read this posting where someone asked a similar question like you did:

[http://ubuntuforums.org/showpost.php?p=7182310&postcount=89](http://ubuntuforums.org/showpost.php?p=7182310&postcount=89)

---

### Post by bodhi.zazen on 2009-07-01
Well, you can do some very cool things with these toys.

I am surprised no one has added **[size=2]screen[/size]** to the cool command list :guitar:

How about ssh -X ?

OK, not impressed yet, how about ssh -X startx

and starting a new desktop, on a remote machine, on Ctrl-Alt-F8 ?

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

Put those two sets of information together :twisted:

---

### Post by tarps87 on 2009-07-02
> **bodhi.zazen said:**
> ...OK, not impressed yet, how about ssh -X startx

and starting a new desktop, on a remote machine, on Ctrl-Alt-F8 ?
...

I never thought of that, I was using vnc but this would be good for using my desktop from my laptop, thanks

---

### Post by jward3010 on 2009-07-02
> **lykwydchykyn said:**
> You can restart X on tty7 using the gdm init script, like so:
```

sudo /etc/init.d/gdm restart

```

If you have a running session, you can launch applications on it by setting the DISPLAY environment variable, like so:
```

export DISPLAY=:0
xterm

```
That would launch an xterm in your GUI session on tty7 from any other tty. You have to be the same user (or have authority to launch apps in the other user's session -- that's another ball of wax).

Of course if you have multiple X sessions running (e.g., one on tty7, one on tty9), you would set DISPLAY to :0, :1, :2 etc respectively.

So just to be clear - DISPLAY:0 starts at tty7, :1 at tty8 etc.

This is great, thanks for all the info, this is what learning linux is all about and the depth that this system can go.

---

### Post by Hetor on 2009-07-02
I use a tty to run irssi (an IRC client) and MOC (a console-based music player) on Screen (terminal multiplexer). This is very useful during online gaming, since you can't minimize games, and a custom X server eats many resourses.

---

### Post by jward3010 on 2009-07-02
Thanks for the people who mentioned "sudo /etc/init.d/gdm restart" and I assume that can run from any tty console (including it's own as I've had to before). I assume the "restart" goes for all commands in /etc/init.d?

I'm going to try absolutely everyone of these out when I get my Ubuntu laptop up and running again. I'm testing Karmic and hitting a whole pile of login problems so this stuff is especially useful in using the good old console to good effect.

---

### Post by lykwydchykyn on 2009-07-02
> **jward3010 said:**
> So just to be clear - DISPLAY:0 starts at tty7, :1 at tty8 etc.

This is great, thanks for all the info, this is what learning linux is all about and the depth that this system can go.

Well, it's not quite that simple.  By default, each new X session will get assigned the next DISPLAY value in the sequence, but you can manually override that and assign any DISPLAY value you want to.  You also have things like Xephyr (running an X session within another X session) which can use display numbers.

On top of that, Ubuntu uses tty8 to display log messages at bootup, so tty8 can't be used for X sessions.  Your second X session would start at tty9.

---

### Post by lykwydchykyn on 2009-07-02
> **jward3010 said:**
> Thanks for the people who mentioned "sudo /etc/init.d/gdm restart" and I assume that can run from any tty console (including it's own as I've had to before). I assume the "restart" goes for all commands in /etc/init.d?


*Mostly*.  The scripts in /etc/init.d/ are called "init scripts" and (AFAIK) they only have to accept "start" and "stop", but it's a common convention to also have "restart" which simply invokes "stop" then "start" (sometimes with a delay in between).

Some init scripts accept other arguments such as "setup", "status", "reload", etc.  If you run it with no arguments, it usually outputs a "usage" string that tells you all the possible arguments.

---

### Post by jward3010 on 2009-07-03
I'm messing around as we speak and find myself reaching for the "Ctrl" and "Alt" keys all the time now - so efficient, multiple things running all at once, never leaving the keyboard. Here's one thing I need to do though:

How do I copy and paste from the GUI into a tty console. Ctrl-Alt-Ins ain't working as it would in a gnome-terminal.

---

### Post by Mornedhel on 2009-07-03
Sorry, I think X handles copy-pasting. As a workaround, you could paste text in a file and read it from the tty, or redirect output in a file and copy it from the graphical session.

I'm curious though, what's wrong with gnome-terminal ?

---

### Post by bodhi.zazen on 2009-07-03
You can not paste from X to a console.

But you can copy-paste in a console with gpm.

[http://www.cyberciti.biz/tips/howto-linux-configure-the-mouse-at-a-text-based-terminal-for-copy-and-paste-operation.html](http://www.cyberciti.biz/tips/howto-linux-configure-the-mouse-at-a-text-based-terminal-for-copy-and-paste-operation.html)

---

### Post by jward3010 on 2009-07-03
> **Mornedhel said:**
> I'm curious though, what's wrong with gnome-terminal ?
Are you asking generally, as in "why are you interested in using tty consoles over gnome-terminal?" The answer is pure curiosity, I'm finding a very efficient way of jumping between terminal windows to do stuff without leaving the keyboard, and in some cases it's negating the need for me to start gdm (i.e. login to Gnome) which means I'm using Linux quicker than usual if I want to do something simple.

Apart from that I find gnome-terminal great and often I'm more in need of it than the tty consoles as I'll be copying and pasting from Firefox which of course relies exclusively on tty7.

It's a pity that you can't copy and paste from X to consoles, can copy buffers not be used universally?

---

### Post by Mornedhel on 2009-07-03
> **jward3010 said:**
> Are you asking generally, as in "why are you interested in using tty consoles over gnome-terminal?"

Yeah, that was what I meant.

> **jward3010 said:**
> The answer is pure curiosity, I'm finding a very efficient way of jumping between terminal windows to do stuff without leaving the keyboard, and in some cases it's negating the need for me to start gdm (i.e. login to Gnome) which means I'm using Linux quicker than usual if I want to do something simple.

I get what you mean, but wouldn't it be just easier for you to use the multi-tabs functionality in gnome-terminal, which kind of replicates what you're doing with multiple consoles open ?

---

### Post by jward3010 on 2009-07-11
> **bodhi.zazen said:**
> Well, you can do some very cool things with these toys.

I am surprised no one has added **[size=2]screen[/size]** to the cool command list :guitar:

How about ssh -X ?

OK, not impressed yet, how about ssh -X startx

and starting a new desktop, on a remote machine, on Ctrl-Alt-F8 ?

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 


[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

Put those two sets of information together :twisted:

That's really impressive as I do a lot of remote work, haven't done much at all in relation to ssh though, so I'll have to scrub up on that. "Screen" is generally handy even to see what type or CPU you're working under.
> **Hetor said:**
> I use a tty to run irssi (an IRC client) and MOC (a console-based music player) on Screen (terminal multiplexer). This is very useful during online gaming, since you can't minimize games, and a custom X server eats many resourses.
People would generally thing that a command line based music player is from 10 years ago but it serves a useful function and probably uses a tenth of the memory of Rhythmbox. I can see this as useful in a situation where music needed to be played from a machine for, say a shop or even during a party, but you didn't want the player to be seen or manipulated.

Thanks to everybody for all the help and info in this, it's been a great mine of learning for me and ultimately boosts my confidence with this system.

---

### Post by jward3010 on 2009-07-11
> **Mornedhel said:**
> I get what you mean, but wouldn't it be just easier for you to use the multi-tabs functionality in gnome-terminal, which kind of replicates what you're doing with multiple consoles open ?

You've just made me figure out I was doing something wrong for ages. I was about to get into a big rant about gnome-terminal having a serious bug in relation to the tab switching key shortcut occasionally switches your current tab to another tab position - but I've realised I've been using the wrong shortcut so thanks for making me look it up!

To be honest, I'm not a big fan of the Ubuntu Desktop, it's not that zippy even with Compiz basic switched on (i.e. Normal mode - not much fanciness), with even a 7800GTX, Athlon64 3700, 1GB RAM helping it out, GNOME is chunky and fat and not much fits on the screen, so although I don't hate it, what I can do command wise with the consoles before I'm forced to logon to the desktop is great, as they load so quick, perform efficiently etc. So basically I get to the graphical login screen as thats where Ubuntu begins and the first thing I do is hit Ctrl - Alt - FX, login there and start doing apt-get update or upgrade, moving, copying, creating files and other messing. 

It's a handy way also with getting to grips with the massively powerful Linux command line and also getting use to the fact that if "gdm" dies one day that I can get be proficient enough at using a basic console to get everyday things done. I spend my lifetime on the gnome-terminal anyway within a graphical environment.

Apart from that there's little difference between tty consoles and gnome-terminal's except of course from the fact that gnome-terminal is bloated like crazy for a terminal.

---

### Post by Mornedhel on 2009-07-11
> **jward3010 said:**
> People would generally thing that a command line based music player is from 10 years ago but it serves a useful function and probably uses a tenth of the memory of Rhythmbox. I can see this as useful in a situation where music needed to be played from a machine for, say a shop or even during a party, but you didn't want the player to be seen or manipulated.

I myself use the Music Player Daemon (mpd) and EMMS, which is a music player for Emacs that can serve as a client for mpd. I use Emacs without X support by the way, so I'm way ahead of you when it comes to doing everything from the terminal :)

> **jward3010 said:**
> To be honest, I'm not a big fan of the Ubuntu Desktop, it's not that zippy even with Compiz basic switched on (i.e. Normal mode - not much fanciness), with even a 7800GTX, Athlon64 3700, 1GB RAM helping it out, GNOME is chunky and fat and not much fits on the screen, so although I don't hate it, what I can do command wise with the consoles before I'm forced to logon to the desktop is great, as they load so quick, perform efficiently etc. So basically I get to the graphical login screen as thats where Ubuntu begins and the first thing I do is hit Ctrl - Alt - FX, login there and start doing apt-get update or upgrade, moving, copying, creating files and other messing.

Maybe you should use a different window manager. There are several other paradigms than Metacity out there. You can get more from your screen real estate with minimalist window managers and/or tiling window managers.

> **jward3010 said:**
> Apart from that there's little difference between tty consoles and gnome-terminal's except of course from the fact that gnome-terminal is bloated like crazy for a terminal.

Unfortunately, the fact that I do all of my work (programming, writing papers, etc.) and more (EMMS, IRC, mail, etc.) from within Emacs means that I can't really live without a nice antialiased console font anymore. That being said, you don't really see the difference with a console anymore when your workspace is a fullscreen Emacs and you never switch away from it.

Also, I never really tried to make my consoles pretty (256 colors, etc.).

---

### Post by jward3010 on 2009-07-12
> **Mornedhel said:**
> I myself use the Music Player Daemon (mpd) and EMMS, which is a music player for Emacs that can serve as a client for mpd. I use Emacs without X support by the way, so I'm way ahead of you when it comes to doing everything from the terminal :)

I've heard a lot about Emacs before, sounds incredibly powerful but needs a little getting use to by the looks of things.

> **Mornedhel said:**
> Maybe you should use a different window manager. There are several other paradigms than Metacity out there. You can get more from your screen real estate with minimalist window managers and/or tiling window managers.

I have tried emerald at least and even other desktops like XFCE, fluxbox etc. but one way or another they take from functionality that I'm used to. Have you got a few suggestions, I don't mind tinkering but ultimately I'd like Ubuntu to either adopt a different desktop manager or refine their own version of Gnome to be lighter and less space consuming, it loves being fat and readable as if it's users are partially blind, and this is really annoying on 1280 X 800 desktops.

---

### Post by Mornedhel on 2009-07-12
> **jward3010 said:**
> I've heard a lot about Emacs before, sounds incredibly powerful but needs a little getting use to by the looks of things.

You're right on both counts. The main hurdle is the weird keybindings. C-x C-c to exit is disconcerting at first when you're used to C-q, which in turn is quoted-insert (insert literal control characters) in Emacs. However, once you've gotten used to those, you will find many have been re-used in bash (hence the "emacs editing mode" which is the default to edit the current line), for instance C-a (beginning-of-line), C-e (end-of-line), C-k (kill-line), C-r (isearch-backward) etc.

> **jward3010 said:**
> I have tried emerald at least and even other desktops like XFCE, fluxbox etc. but one way or another they take from functionality that I'm used to. Have you got a few suggestions, I don't mind tinkering

I didn't try every single window manager out there (not even more than a few actually), but I could probably recommend some. Depends on the functionality you require. What are the features that are absolutely essential to you (in terms of functionality, and in terms of tolerated degree of bloatiness) ?

> **jward3010 said:**
> but ultimately I'd like Ubuntu to either adopt a different desktop manager or refine their own version of Gnome to be lighter and less space consuming, it loves being fat and readable as if it's users are partially blind, and this is really annoying on 1280 X 800 desktops.

Ubuntu uses almost vanilla Gnome, so I don't think there's much of a chance of switching to a different WM unless upstream Gnome also changes. Given that Gnome's goal when picking a WM was simplicity and stability, which Metacity achieves admirably (never seen it crash, never seen an unnecessary option, never seen many necessary ones), they're not likely to recommend a sudden change either. Gnome 3 (not too far away) will apparently partly change this, since they're adding in Clutter (OpenGL "interactive canvas" library) to what will basically be Metacity 3. I'm curious as to what new features this will bring exactly (native compositing ?), but I'll probably be staying with Sawfish.

As a side note, I'm using 1280x800 as well, and I don't have any particular qualms with wasted space. Could you point to a particular area where the graphics seem too fat to you ?

---

### Post by scorp123 on 2009-07-12
> **Mornedhel said:**
> As a side note, I'm using 1280x800 as well, and I don't have any particular qualms with wasted space. Same here. The only thing that springs to my mind is the possibility that per default the fonts might be too big? IMHO they look uglier than they'd need to this way. So I prefer to keep my fonts small (e.g. size 9 or even 8 instead of the default 10 ...) and font rendering is set to "best shapes". Maybe this helps?

---

### Post by jward3010 on 2009-07-12
> **Mornedhel said:**
> You're right on both counts. The main hurdle is the weird keybindings. C-x C-c to exit is disconcerting at first when you're used to C-q, which in turn is quoted-insert (insert literal control characters) in Emacs. However, once you've gotten used to those, you will find many have been re-used in bash (hence the "emacs editing mode" which is the default to edit the current line), for instance C-a (beginning-of-line), C-e (end-of-line), C-k (kill-line), C-r (isearch-backward) etc.

Is vi and vim similar, I hear it has very clever keybindings for removing, selecting, cutting text and other stuff but once again it's a case of getting use to it. With everybody weaned on Word, notepad, gedit etc. nowadays, it's a strange experience to see how the likes of these ingenious text editors work.

> **Mornedhel said:**
> I didn't try every single window manager out there (not even more than a few actually), but I could probably recommend some. Depends on the functionality you require. What are the features that are absolutely essential to you (in terms of functionality, and in terms of tolerated degree of bloatiness) ?

What I'm interested in keeping is everything that GNOME currently does even with metacity (right click menu is good in Nautilus and on desktop, left-hand side drives and common folders is really handy, App, Places and System menu's are fine, maybe some refinement needed)  but just scale it down in terms of fat buttons, lots of row spacing where those buttons are, even the top and bottom panels chew up space when Firefox is maxmised and add to that the size of buttons within Firefox. Web browser page space, nautilus space etc. really reduces when these things are left at there default. I usually drop font DPI to 80 and switch to "Use small icons" and "Icons beside text options". All I know is that as soon as I started using GNOME I wanted XP's explorer back to some degree because fonts got bigger, panels liked a few pixels above and below for breathing space and buttons wanted to be large and well fed. To some degree it's hard to describe but you just know you're scrolling too much or you can't see as much as usual.

> **Mornedhel said:**
> Ubuntu uses almost vanilla Gnome, so I don't think there's much of a chance of switching to a different WM unless upstream Gnome also changes. Given that Gnome's goal when picking a WM was simplicity and stability, which Metacity achieves admirably (never seen it crash, never seen an unnecessary option, never seen many necessary ones), they're not likely to recommend a sudden change either. Gnome 3 (not too far away) will apparently partly change this, since they're adding in Clutter (OpenGL "interactive canvas" library) to what will basically be Metacity 3. I'm curious as to what new features this will bring exactly (native compositing ?), but I'll probably be staying with Sawfish.

Thats what I was thinking, Gnome will have to change and they wont at this point in time, hence why the particular distribution has to do the refinements but Ubuntu doesn't look set to with the current Gnome desktop.

Gnome3 is a possible step backwards as it seems to assume decent hardware acceleration and thats not a great idea for all laptops out there. Also I don't think the whole search for everything functionality will necessarily be everyone's cup of tea. To be honest it could be life changing for the way desktops are provided to us and maybe it will cause rethinks in the way OS providers do their desktops but GNOME have never done anything too radical so I doubt it will be.

> **Mornedhel said:**
> As a side note, I'm using 1280x800 as well, and I don't have any particular qualms with wasted space. Could you point to a particular area where the graphics seem too fat to you ?

Like I said above, in terms of fattness eating up general vertical space. I'll provide a picture of a default Ubuntu Gnome desktop without the refinements I usually do. It may not do justice, but have it anyway. Note especially the vertical height of nautilus's top button panel. 

Later on I'll post a similar shot but with my refinements, my battery is dying as we speak, which reduce the size and make it slightly easier to look at, for example a large image in Firefox without having to make it fullscreen

---

### Post by Mornedhel on 2009-07-12
> **jward3010 said:**
> Is vi and vim similar, I hear it has very clever keybindings for removing, selecting, cutting text and other stuff but once again it's a case of getting use to it. With everybody weaned on Word, notepad, gedit etc. nowadays, it's a strange experience to see how the likes of these ingenious text editors work.

vi and others (vim, gvim) have even weirder keybindings, which are arguably more ergonomical (at least that's what vi users say). I don't know, :wq! to quite without saving just seems weird to me. Bear in mind that vi also is a modal editor, that is, it has a mode for edition and a mode for commands, and you have to switch between each mode. It's even harder to get used to than Emacs. Also, it only does text edition (or it's meant to), whereas Emacs has a lot more features. Some say bloat.

> **jward3010 said:**
> What I'm interested in keeping is everything that GNOME currently does even with metacity (right click menu is good in Nautilus and on desktop, left-hand side drives and common folders is really handy, App, Places and System menu's are fine, maybe some refinement needed)

Those are Nautilus functionalities. You don't have to give that up if you change window managers ; you can obviously keep Nautilus as your file browser, but you can also keep it as your desktop manager.

> **jward3010 said:**
> but just scale it down in terms of fat buttons, lots of row spacing where those buttons are, even the top and bottom panels chew up space when Firefox is maxmised and add to that the size of buttons within Firefox. Web browser page space, nautilus space etc. really reduces when these things are left at there default.

From that, and the screenshot you posted, it seems like you're using a theme that has heavier spacing than necessary. I'll post my own screenshot later. Looks like each row of buttons, including title bars, use a few more pixels in your setup than in mine.

> **jward3010 said:**
> I usually drop font DPI to 80 and switch to "Use small icons" and "Icons beside text options". All I know is that as soon as I started using GNOME I wanted XP's explorer back to some degree because fonts got bigger, panels liked a few pixels above and below for breathing space and buttons wanted to be large and well fed. To some degree it's hard to describe but you just know you're scrolling too much or you can't see as much as usual.

It's possible to change a few options here and there (font size, etc.). I'll give you that, Nautilus displays few icons at a time when compared to Explorer.

> **jward3010 said:**
> Gnome3 is a possible step backwards as it seems to assume decent hardware acceleration and thats not a great idea for all laptops out there.

They probably assume that by the time it comes out, lower end laptops will be able to do compositing without problems.

> **jward3010 said:**
> Also I don't think the whole search for everything functionality will necessarily be everyone's cup of tea. To be honest it could be life changing for the way desktops are provided to us and maybe it will cause rethinks in the way OS providers do their desktops but GNOME have never done anything too radical so I doubt it will be.

Actually, I don't like search for everything and the metadata filesystem paradigm, either. Maybe us heavy console users aren't too compatible with this trend...

> **jward3010 said:**
> Like I said above, in terms of fattness eating up general vertical space. I'll provide a picture of a default Ubuntu Gnome desktop without the refinements I usually do. It may not do justice, but have it anyway. Note especially the vertical height of nautilus's top button panel. 

Later on I'll post a similar shot but with my refinements, my battery is dying as we speak, which reduce the size and make it slightly easier to look at, for example a large image in Firefox without having to make it fullscreen

[Include screenshot here.]

Here is a screenshot of my setup. (Yes, you have my username now. I have yours, too.) Notice (compare both images side by side) that my Nautilus top button bar uses less pixels than yours. Same for most controls. I'd definitely say it's the theme.

Controls are from Mist, icons from the Tango set, decorations are handled by the Sawfish "Mono" theme. I use only one panel, old-style, as recently (probably because I switched to Sawfish) I have had some nostalgia of my first Linux installations. It's completely cluttered with various things -- I really wish there was some way to configure the notification area to use only smaller icons, on two rows if possible. Having a small space for the window list doesn't bother me, since I typically have one to three windows open on the same workspace.

---

### Post by scorp123 on 2009-07-12
> **Mornedhel said:**
>   :wq! to quite without saving  Au contraire: your "w" up there will make sure that whatever you were writing will get saved! To quit without saving you'd hit  **:q!**

> **Mornedhel said:**
>  just seems weird to me. Bear in mind that vi also is a modal editor, that is, it has a mode for edition and a mode for commands, and you have to switch between each mode. It's even harder to get used to than Emacs.  You have to bear in mind from which age "vi" originates from.

The "weird" keyboard commands are easily explained with the fact that computer keyboards looked like *this* when "vi" was first created (picture is from Wikipedia):

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/KB_Terminal_ADM3A.svg/450px-KB_Terminal_ADM3A.svg.png[/IMG]

... so there was no separate cursor key block, there was no separate numerical block .... *This* was the *entire* keyboard, and whatever you wanted had to be achieved by some keyboard sequence on this thing.

Computer screens back then were running in a 40 x 25 text mode. So screen real estate was already highly limited in any direction. That's why "vi" comes without any menus of sorts because they would have been a waste of screen estate. Instead the thing with the mode changes was created .... and it stuck, up to this day.

Modern and friendly variants such as "gvim" come with menus and everything though, but it's still absolutely cool that modern "gvim" will happily accept the same (obscure) commands like the original "vi" 40 years ago.

That's what I was taught about "vi": "Learn it once -- use it forever." Because the commands will always be the very same, no matter on what OS you're working on - if the thing has a "vi", you will know how to use it.


> **Mornedhel said:**
>  Also, it only does text edition (or it's meant to)  I'd highly recommend to get rid of the default "vim-tiny" that Ubuntu ships with and go for this package:  "vim-full"  ... it's soooooo much better. ```
 sudo apt-get install vim-full
``` There is also this package "vim-scripts" which adds nice extras.

In fact there are plenty of vim*-something* packages in the repos. Whatever you try will definitely be better than that ugly "vim-tiny" thingie Ubuntu unfortunately ships with.

---

### Post by Mornedhel on 2009-07-12
> **scorp123 said:**
> Au contraire: your "w" up there will make sure that whatever you were writing will get saved! To quit without saving you'd hit  **:q!**

Yeah, I thought I had an extra character in there. Didn't really bother to double-check though. My bad.

> **scorp123 said:**
> You have to bear in mind from which age "vi" originates from.

The "weird" keyboard commands are easily explained with the fact that computer keyboards looked like *this* when "vi" was first created (picture is from Wikipedia):

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/KB_Terminal_ADM3A.svg/450px-KB_Terminal_ADM3A.svg.png[/IMG]

... so there was no separate cursor key block, there was no separate numerical block .... *This* was the *entire* keyboard, and whatever you wanted had to be achieved by some keyboard sequence on this thing.

No, actually, I'm not saying these are bad commands (... I think we're going into an emacs vs vi war here, but never mind). It's just that by default, when you type letters in Emacs, the letters actually appear in your buffer. In {g,}vi{m,}, the whole modal thing means that depending on your mode, the same keystrokes may do completely different things. Anyway, I do believe that vim uses the cursor keys now, doesn't it ? (Emacs also has vintage cursor movement commands, but no one uses them anymore.) 

> **scorp123 said:**
> Modern and friendly variants such as "gvim" come with menus and everything though, but it's still absolutely cool that modern "gvim" will happily accept the same (obscure) commands like the original "vi" 40 years ago.

Who wants to use menus anyway ? :)

> **scorp123 said:**
> I'd highly recommend to get rid of the default "vim-tiny" that Ubuntu ships with and go for this package:  "vim-full"  ... it's soooooo much better. ```
 sudo apt-get install vim-full
``` There is also this package "vim-scripts" which adds nice extras.

In fact there are plenty of vim*-something* packages in the repos. Whatever you try will definitely be better than that ugly "vim-tiny" thingie Ubuntu unfortunately ships with.

Um, actually, I got rid of vim-* altogether... Sorry :)

I know that vim has plugins nowadays, but it's still nowhere near the extensibility of Emacs. I mean, I hacked together a bit of elisp to have my Emacs media player talk to libnotify and display song titles every time a new song begins, and applied the changes *on the fly* without restarting Emacs. (It did take several tries until the code compiled.) On the other hand, vim users seem to use it as just an editor, possibly with a few added features.

---

### Post by scorp123 on 2009-07-13
> **Mornedhel said:**
>  Who wants to use menus anyway ? :) Exactly :KS

> **Mornedhel said:**
>  I mean, I hacked together a bit of elisp to have my Emacs media player talk to libnotify and display song titles every time a new song begins, and applied the changes *on the fly* without restarting Emacs.  Nice ... One day I'll have to try ***that OS*** too ....  :lolflag:

---

### Post by Mornedhel on 2009-07-13
> **scorp123 said:**
> Nice ... One day I'll have to try ***that OS*** too ....  :lolflag:

The joke goes like this : "Emacs is a powerful OS that only lacks a decent text editor."

Another one : "I'm using Linux. A library that emacs uses to communicate with Intel hardware." (stolen from #emacs on freenode).

---

### Post by scorp123 on 2009-07-13
> **Mornedhel said:**
> The joke goes like this : "Emacs is a powerful OS that only lacks a decent text editor."

Another one : "I'm using Linux. A library that emacs uses to communicate with Intel hardware." (stolen from #emacs on freenode). Hah! Brilliant :KS

---

### Post by jward3010 on 2009-07-13
**":q"** I know it well, for exiting man pages.

> **Mornedhel said:**
> From that, and the screenshot you posted, it seems like you're using a theme that has heavier spacing than necessary. I'll post my own screenshot later. Looks like each row of buttons, including title bars, use a few more pixels in your setup than in mine.

It's called Dust Sand, the one in your screenshot is something I used to use but has now been removed from Jaunty and I assume we wont see it again in Karmic either. The fancy ones are taking hold, just take a look at "Themes" in Jaunty. I don't particularly mind them but there just all fat, even in your particular shot look at the space (height) given to the "location" bar (if you like) in Nautilus. It's huge in my opinion and thats a different theme from mine even, mine being even more generous. This is where I'd love to provide an "explorer" comparison, forgive me.

> **Mornedhel said:**
> It's possible to change a few options here and there (font size, etc.). I'll give you that, Nautilus displays few icons at a time when compared to Explorer.

I often prefer the used created Gtk2 (I think it's called) themes that you'll occasionally see on gnome-look.org. They usually get the idea, I'll try and post a link later.

> **Mornedhel said:**
> They probably assume that by the time it comes out, lower end laptops will be able to do compositing without problems.

Or possibly they'll give it as a choice when installing or in "Visual Effects" or something. With Ubuntu designed to run on laptops 4 and 5 years old (and it does pretty well often) it's definitely something they can't give as immediate default even for another couple of years. And there's always the issue, even in the late future with graphics drivers compatibilities, instabilities etc. Can't wait for the revolution and the world to eventually be run open source!

> **Mornedhel said:**
> Actually, I don't like search for everything and the metadata filesystem paradigm, either. Maybe us heavy console users aren't too compatible with this trend...

It quite possibly creates a laziness with knowing where everything is, it will be a case of: "Where's the XXXX folder?" - "Oh, I don't know - just type it in and it'll come up" - not good. Basically the day Google goes down is a day that we're f*cked! We rely heavily on searching, maybe it's ok, maybe not.

> **Mornedhel said:**
> Here is a screenshot of my setup. (Yes, you have my username now. I have yours, too.) Notice (compare both images side by side) that my Nautilus top button bar uses less pixels than yours. Same for most controls. I'd definitely say it's the theme.

Yeah, you have a few pixels less here and there but I don't think it's much and you haven't seen the other themes yet - they're even worse, the likes of New Wave - now don't get me wrong they're great at 1600 X 1200 but in my opinion thats about it.

> **Mornedhel said:**
> Controls are from Mist, icons from the Tango set, decorations are handled by the Sawfish "Mono" theme. I use only one panel, old-style, as recently (probably because I switched to Sawfish) I have had some nostalgia of my first Linux installations. It's completely cluttered with various things -- I really wish there was some way to configure the notification area to use only smaller icons, on two rows if possible. Having a small space for the window list doesn't bother me, since I typically have one to three windows open on the same workspace.

I know exactly the feeling, on some machines I have the single bottom panel KDE style and it's a difference alright but being able to edit the panel easily to create two row's of icons would be icing on the cake, the ultimate in customisable desktops. How do you do the two rows for the taskbar?

---

### Post by Mornedhel on 2009-07-13
> **jward3010 said:**
> It's called Dust Sand, the one in your screenshot is something I used to use but has now been removed from Jaunty and I assume we wont see it again in Karmic either. The fancy ones are taking hold, just take a look at "Themes" in Jaunty. I don't particularly mind them but there just all fat, even in your particular shot look at the space (height) given to the "location" bar (if you like) in Nautilus. It's huge in my opinion and thats a different theme from mine even, mine being even more generous. This is where I'd love to provide an "explorer" comparison, forgive me.

I used to use Dust as well, albeit the darker one. It was quite pretty, but it didn't play well with Sawfish window decorations, so I dumped it. As I said before, my current controls theme is Mist, and I did get it from the Jaunty theme packages -- not sure if it was installed by default or if I had to install the package from the repositories, definitely not from gnome-look. You do have a point though : it's been a while since I checked gnome-look out, they might have some interesting minimalist themes now. If I find something good I'll be sure to let you know.

> **jward3010 said:**
> I often prefer the used created Gtk2 (I think it's called) themes that you'll occasionally see on gnome-look.org. They usually get the idea, I'll try and post a link later.

I'd appreciate that.

> **jward3010 said:**
> Or possibly they'll give it as a choice when installing or in "Visual Effects" or something. With Ubuntu designed to run on laptops 4 and 5 years old (and it does pretty well often) it's definitely something they can't give as immediate default even for another couple of years. And there's always the issue, even in the late future with graphics drivers compatibilities, instabilities etc. Can't wait for the revolution and the world to eventually be run open source!

Actually, Metacity with compositing capabilities probably won't be as heavy as Compiz is. I remember trying an Enlightenment 17 based Ubuntu derivative last year. One of the first things I noticed was that the window manager did compositing by default (Enlightenment is known for its eye-candy). I wasn't too keen on it until I noticed that I hadn't installed the drivers for my NVidia yet. (In the end I gave up on Enlightenment 17 because it was still in alpha and it segfaulted from time to time.)

> **jward3010 said:**
> It quite possibly creates a laziness with knowing where everything is, it will be a case of: "Where's the XXXX folder?" - "Oh, I don't know - just type it in and it'll come up" - not good. Basically the day Google goes down is a day that we're f*cked! We rely heavily on searching, maybe it's ok, maybe not.

The standard use case for metadata-heavy desktops is that when you're opening a document you might want to open it by tags, and once you've opened it you might want to open other similar documents, or documents belonging to the same workflow. I use directories for that. To find a document relative to my thesis, I go to the ~/thesis directory. To find a document relative to my thesis main LaTeX file, I look around in the ~/thesis directory and its subdirectories. I don't really get the point of the metadata shells, but they sure sound cool.

> **jward3010 said:**
> I know exactly the feeling, on some machines I have the single bottom panel KDE style and it's a difference alright but being able to edit the panel easily to create two row's of icons would be icing on the cake, the ultimate in customisable desktops. How do you do the two rows for the taskbar?

I will try and Google (heh) something up for the two rows of notification icons. The two rows for the taskbar is completely out of luck : some themes use that, some don't. I was really relieved when it turned out Mist did.

Will post again here to share results, be back later tonight.

---

### Post by jward3010 on 2009-07-13
> **Mornedhel said:**
> Actually, Metacity with compositing capabilities probably won't be as heavy as Compiz is. I remember trying an Enlightenment 17 based Ubuntu derivative last year. One of the first things I noticed was that the window manager did compositing by default (Enlightenment is known for its eye-candy). I wasn't too keen on it until I noticed that I hadn't installed the drivers for my NVidia yet. (In the end I gave up on Enlightenment 17 because it was still in alpha and it segfaulted from time to time.)

Was it by any chance CrunchBang Linux, I installed that and was able to enable some kind of fancy compositing even though I was using an 
Silicon Images S3 card that wouldn't work for Compiz.

NO, I take it back, just checked out Enlightenment and it ain't Crunch. That uses Openbox. Quite zippy and nice, in fact I like it quite a bit in terms of space saving, should try it again soon - [www.crunchbanglinux.org](www.crunchbanglinux.org)

---

### Post by Mornedhel on 2009-07-13
> **jward3010 said:**
> NO, I take it back, just checked out Enlightenment and it ain't Crunch. That uses Openbox. Quite zippy and nice, in fact I like it quite a bit in terms of space saving, should try it again soon - [www.crunchbanglinux.org](www.crunchbanglinux.org)

Yeah, Enlightenment is quite a different thing... The actual distribution was OpenGEU. It's an Ubuntu derivative that focuses on being, uh, pretty. Since E17 is still not desktop-ready, that's about all it can do. If that (and the waaay overboard themes) was fixed it would probably be a very decent distribution. As it is I won't try it again for the moment.

I heard a lot about CrunchBang and Openbox, but my current machine is decent and I have no need for a fast distribution.

Right now on gnome-look I have found about a dozen hundred themes that claim to be minimalist, but not in the sense I meant -- rather they use little decoration, which can be nice, but is not what I was looking for. I've had more luck using "compact", which yielded a few engines that actually look like they're designed to save space, although most leave too much space between rows. Something like this : [http://www.gnome-look.org/content/show.php/Clearlooks+Compact?content=69357](http://www.gnome-look.org/content/show.php/Clearlooks+Compact?content=69357) Unfortunately for me, the controls are rounded and I am going for the full squarish look.

Edition: Well, about the multiple rows for the notification area, it seems that it's been recently solved in XFCE 4.6, but it's been a [bug](http://bugzilla.gnome.org/show_bug.cgi?id=102183) in Gnome for over six years now... I'm creating a Bugzilla account now to add my voice to the comments, care to join me ?

---

### Post by jward3010 on 2009-07-15
> **Mornedhel said:**
> Yeah, Enlightenment is quite a different thing... The actual distribution was OpenGEU. It's an Ubuntu derivative that focuses on being, uh, pretty. Since E17 is still not desktop-ready, that's about all it can do. If that (and the waaay overboard themes) was fixed it would probably be a very decent distribution. As it is I won't try it again for the moment.

I saw Enlightment sometime in the past and whether it's a "fancy" desktop is up for debate, I'd regard ordinary Gnome as fancy in comparison. It looks just gimmicky and kind of silly space age, but it looks compact yet still legible so thats something.

> **Mornedhel said:**
> I heard a lot about CrunchBang and Openbox, but my current machine is decent and I have no need for a fast distribution.

I've tried out Crunchbang and it's good, light, quick, using aptitude for updates and app installs, compact yet legible and the right click menu is nicely designed and highly configurable so recommended. Also it's got some other compositing engine (other than compiz) which is nice and light, especially if you want a highly important and completely useful fade-in and out right-click menu. Rather dark though and I don't mind a bright distbution.

> **Mornedhel said:**
> Edition: Well, about the multiple rows for the notification area, it seems that it's been recently solved in XFCE 4.6, but it's been a [bug](http://bugzilla.gnome.org/show_bug.cgi?id=102183) in Gnome for over six years now... I'm creating a Bugzilla account now to add my voice to the comments, care to join me ?
I shall join you, later on tonight or tomorrow. Would launchpad not accept our abuse or are they exclusively using Bugzilla. Never knew Gnome we're within Bugzilla.

---

### Post by Mornedhel on 2009-07-15
> **jward3010 said:**
> I saw Enlightment sometime in the past and whether it's a "fancy" desktop is up for debate, I'd regard ordinary Gnome as fancy in comparison. It looks just gimmicky and kind of silly space age, but it looks compact yet still legible so thats something.

I guess it depends on the theme, and of course if you were looking at E16 screenshots it certainly didn't look fancy. Enlightenment 17 on OpenGEU right now looks like this by default : [http://opengeu.intilinux.com/Screens_files/ls-s2.png](http://opengeu.intilinux.com/Screens_files/ls-s2.png)

> **jward3010 said:**
> I've tried out Crunchbang and it's good, light, quick, using aptitude for updates and app installs, compact yet legible and the right click menu is nicely designed and highly configurable so recommended. Also it's got some other compositing engine (other than compiz) which is nice and light, especially if you want a highly important and completely useful fade-in and out right-click menu. Rather dark though and I don't mind a bright distbution.

Mmkay, will try Openbox someday, right now Sawfish is configurable enough for me.

> **jward3010 said:**
> I shall join you, later on tonight or tomorrow. Would launchpad not accept our abuse or are they exclusively using Bugzilla. Never knew Gnome we're within Bugzilla.

Launchpad uses their own bug tracker. Actually I started looking there and found [this bug report](https://bugs.launchpad.net/gnome-panel/+bug/34156), which as you can see has been related upstream to a Gnome bug, which is the one I mentioned on my previous post. So it's marked Triaged as far as Ubuntu is concerned and they're counting (rightly) on upstream Gnome to fix it. Gnome in turn has it marked as a bug of normal severity and it's been unfixed for six years, I guess no one cares enough.

---

