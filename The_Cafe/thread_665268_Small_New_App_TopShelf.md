---
title: "Small New App: TopShelf"
date: 2008-01-12
forum: The Cafe
---

### Post by kripkenstein on 2008-01-12
I wrote a small app to make my daily GNOME use more efficient, I'm posting it here in hopes someone else might find it useful.

The idea is something like a 'recent files list' (which GNOME already has), but **editable** and **user-managed**. The issue is, there are always some *really* important files that I work on every day (say, a school paper, a short story, etc.), and these files get bumped off the recent files list very fast due to other more temporary files, even those that I just want to open once.

So I wrote an app which I call TopShelf, which basically is meant to be a panel applet that acts as your 'top shelf' - you can add files to it, remove files from it, and doubleclick them to open. Not much more - a very small app. So, you would drag&drop important files that you are constantly working on to the applet, and you can then access them quickly through TopShelf, instead of finding them in their actual directory somewhere on the drive, or looking for them (and often not finding them ;) ) in the recent files list. I've seen some people use their desktop as a 'top shelf' - this I consider clunky, because (1) the actual files are on the desktop, and I want the shelf to only **link** to the files, and (2) the desktop isn't really the right place IMHO at least, a panel applet seems better.

The project page is [here]("https://launchpad.net/topshelf"). The current release is 0.2, which you can get [here]("https://launchpad.net/topshelf/trunk/0.2/"). Installation is a simple "sudo make install". After installing the .deb, do 'add to panel' (rightclick on an empty space on a panel), and TopShelf should be in the 'Accessories' area.

Comments, bugs etc. are welcome :)

Edit: Added screenshots, after M7S's good suggestion:

---

### Post by M7S on 2008-01-12
Screenshots?

---

### Post by kripkenstein on 2008-01-12
> **M7S said:**
> Screenshots?

Yeah, I should have thought of that myself... ok, added to original post :)

---

### Post by SunnyRabbiera on 2008-01-12
interesting...
I hope you can make a port of this for kde users though, or someone else does as this is an interesting looking app.

---

### Post by Praadur on 2008-01-12
This looks to be a veritable corker of a deskbar applet, I have to say.  I do have a question though and perhaps a feature request.

First of all, the question: How does it deal with file deletion?  For example, if I were to delete a file from a directory that's contained within its list, will that file still be within its list even though it's deleted the next time I open it?

Next, the feature request (and this actually ties into the question): Would it be easily possible to 'watch' a directory?  For example, I could tell it to watch directory A and it would automatically add and remove files from the list as they enter and leave that directory.  This would be very handy for my anime-watching habits and would mean that I wouldn't need a Nautilus window open a great deal of the time.

Anyway, I will note that I'm more than aware that such a request might be beyond the scope of the applet or that it might bloat it out too much, in which case feel free to tell me to bugger off!  I've been a developer in the past, so I know how it is when people come out with fantastical feature requests, like... I just have.

---

### Post by kripkenstein on 2008-01-12
> **SunnyRabbiera said:**
> interesting...
I hope you can make a port of this for kde users though, or someone else does as this is an interesting looking app.
Thanks. Well, I don't know Qt, but it probably wouldn't be hard to make something similar for KDE. In fact, if someone wants to collaborate on this, I'd be happy to include a KDE port in my project.

> **Praadur said:**
> This looks to be a veritable corker of a deskbar applet, I have to say.  I do have a question though and perhaps a feature request.

First of all, the question: How does it deal with file deletion?  For example, if I were to delete a file from a directory that's contained within its list, will that file still be within its list even though it's deleted the next time I open it?

Not sure I understand you, but if I did, then the idea is that the TopShelf app only contains links to documents, but not the actual documents. So you would delete files and so forth using your usual file manager. If you deleted the file, TopShelf wouldn't know about it. But perhaps I should make it automatically clean out deleted files? I need to think if that's the best behavior, though. 
> 
Next, the feature request (and this actually ties into the question): Would it be easily possible to 'watch' a directory?  For example, I could tell it to watch directory A and it would automatically add and remove files from the list as they enter and leave that directory.  This would be very handy for my anime-watching habits and would mean that I wouldn't need a Nautilus window open a great deal of the time.

Well, really the main usefulness of TopShelf would be when the files are **scattered** around your hard drive. If they are already in a particular directory, then as you say, you can just keep an open nautilus window for that directory. Or even just a bookmark in nautilus for that directory is almost as useful (single-click access).

However, that's just me, perhaps most people would like your feature. It doesn't sound hard to implement, so if there is interest I'm open to doing so :)
> 
Anyway, I will note that I'm more than aware that such a request might be beyond the scope of the applet or that it might bloat it out too much, in which case feel free to tell me to bugger off!  I've been a developer in the past, so I know how it is when people come out with fantastical feature requests, like... I just have.
Thanks for the suggestion, while it isn't exactly what I have in mind so far, as I said, I'm open to changing my mind. Really I just wrote it for my personal use, but if simple changes can make it helpful for other people, then that's good.

---

### Post by mrgnash on 2008-01-12
This is a great idea :) And this is what is so great about opensource.

---

### Post by Praadur on 2008-01-12
> **kripkenstein said:**
> Not sure I understand you, but if I did, then the idea is that the TopShelf app only contains links to documents, but not the actual documents. So you would delete files and so forth using your usual file manager. If you deleted the file, TopShelf wouldn't know about it. But perhaps I should make it automatically clean out deleted files? I need to think if that's the best behavior, though.

You understood me perfectly!

I was actually worried this might be the case because I tend to have a weird schema when it comes to handling files, I tend to go by filenames as much as the contents.  So for example, I might have 'todo.text-20080112', as this would mark the day I created this todo and it helps me keep a timeline of the things I wanted to do more easily.  If I happened to delete one of these files though, anything that works by links alone would keep it around regardless.  (I'll also note that this ties into the notion of a directory-watching feature.)

What you could do is add an option for it in an options dialog, but again this might be too much work for just one option, there might be a better way.

One thing I'd like to stress though is that I've been in the spot where I'm a developer and I've shared a project for others to enjoy, and I've found myself swamped with suggestions that really go beyond what I'd planned.  So if all of this sounds like ti would pollute the original idea then simply don't implement these ideas, that's perfectly alright!  I merely suggest ideas on the merit that someone might think 'Hey, that's a good idea!' and run with them, they're just passing thoughts really.

One other thing I have to apologise for though is that my ideas might not be particularly easy to understand at first, I tend to think of things in a particularly fractured way, and I'm not that good at explaining them!  Through circumlocutory effort though, I often get the idea out... I hope I did this time, too.

---

### Post by kripkenstein on 2008-01-12
> **mrgnash said:**
> This is a great idea :) And this is what is so great about opensource.

Thanks. Actually, writing this app really showed me how open-source is useful, for example, I had no idea how to get small icons appropriate for the files' mime-types. So I just downloaded and read the source code to the GTK+ recent files dialog and understood the idea from there. You can't do that in a closed-source environment...

> **Praadur said:**
> 
I was actually worried this might be the case because I tend to have a weird schema when it comes to handling files, I tend to go by filenames as much as the contents.  So for example, I might have 'todo.text-20080112', as this would mark the day I created this todo and it helps me keep a timeline of the things I wanted to do more easily.  If I happened to delete one of these files though, anything that works by links alone would keep it around regardless.  (I'll also note that this ties into the notion of a directory-watching feature.)

What you could do is add an option for it in an options dialog, but again this might be too much work for just one option, there might be a better way.

Ok, thanks, I'll keep this idea in mind. My near-future plans are to fix some bugs, but later on I'll start adding new features, including perhaps this one, depending on other people's reactions and so forth.

---

### Post by koleoptero on 2008-01-12
Oh my god, and I was always thinking how I needed something like this, cause I have some ebooks that I read daily and sometimes get lost from the recent documents list. Thank you so much! Keep up the good work!:KS

---

### Post by FuturePilot on 2008-01-12
This is really cool :)

---

### Post by trash on 2008-01-12
Great idea! I am just wondering how it handles files on an external drive or mem stick? I have several files that I update almost daily on my stick, I wouldn't care if it didn't see the files if the stick wasn't pluged in but would it once pluged in again?

thanks:)

---

### Post by kripkenstein on 2008-01-12
> **trash said:**
> Great idea! I am just wondering how it handles files on an external drive or mem stick? I have several files that I update almost daily on my stick, I wouldn't care if it didn't see the files if the stick wasn't pluged in but would it once pluged in again?

thanks:)
Well, as currently written, TopShelf shows the files that you added to its list no matter where they are. If its on a usb drive that isn't plugged, and you try to doubleclick a file, you'll get an error (from the application that tries to open it, that TopShelf calls). If the usb stick is plugged in, then it'll open without problem, so what you say should work.

Actually it might be a nice feature to have it display a warning on files that aren't available, so you'll know you need to plug in the drive before you double click. I think I'll add that to my TODO list.

---

### Post by trash on 2008-01-12
I love it!
The icon needs a transparent background but aside from that I love that too:)

---

### Post by urukrama on 2008-01-12
This looks very handy. Thank you kripkenstein.

Once you handle the dependencies, please don't make it dependent on gnome-panel, though, so that us Gnome non-users don't need to install an extra panel :-)

---

### Post by kripkenstein on 2008-01-13
> **urukrama said:**
> This looks very handy. Thank you kripkenstein.

Once you handle the dependencies, please don't make it dependent on gnome-panel, though, so that us Gnome non-users don't need to install an extra panel :-)

Hmm, TopShelf is currently a gnome panel applet, so it would naturally depend on gnome-panel... :) But perhaps it doesn't need to be... I guess it could have the ability to run 'standalone' as an always-on-top window, without any connection to a panel. Is that what you would like?

Btw, what desktop are you using?

---

### Post by init1 on 2008-01-13
This looks like a cool app, any chance you could make a RPM for it?

---

### Post by brennydoogles on 2008-01-13
You may want to look at the source code for the Stacks plugin for Avant Window Manager. It is very similar to what you are describing, and could maybe give you ideas on how to do some of the things that people are asking for. Hope this helps!

---

### Post by zero-9376 on 2008-01-13
also there is an existing panel applet called a drawer which as far as i can tell does basically the same stuff as your application except it only shows the filename etc as a tooltip which is rather useless for files but good for application launchers which and other applets which it can also handle.
the drawer also just throws an error if a file isn't available. a simple workaround to this might be to have an option to remove the item from the shelf/draw or ignore (for cases where its on an external drive for example)
maybe your applet could replace the draw or you could integrate your features into the existing application

---

### Post by trash on 2008-01-13
> **zero-9376 said:**
> also there is an existing panel applet called a drawer which as far as i can tell does basically the same stuff as your application except it only shows the filename etc as a tooltip which is rather useless for files but good for application launchers which and other applets which it can also handle.
the drawer also just throws an error if a file isn't available. a simple workaround to this might be to have an option to remove the item from the shelf/draw or ignore (for cases where its on an external drive for example)
maybe your applet could replace the draw or you could integrate your features into the existing application

Fading unavailable files would look nice and be better than a popup message IMO:)

---

### Post by kripkenstein on 2008-01-13
> **init1 said:**
> This looks like a cool app, any chance you could make a RPM for it?
I'm sorry, I have no idea how to make RPMs... however, you can install it from source, this is **very** easy. Grab the .tar.gz from the releases directory [here]("http://codebrowse.launchpad.net/~kripkenstein/topshelf/main/files"), then just run make install (as superuser). That should work, unless your distro manages directories much differently than Debian/Ubuntu.

If someone knows how to make RPMs 'correctly', I'd be grateful for the help.

> **brennydoogles said:**
> You may want to look at the source code for the Stacks plugin for Avant Window Manager. It is very similar to what you are describing, and could maybe give you ideas on how to do some of the things that people are asking for. Hope this helps!
Thanks, I'll look at that.

> **zero-9376 said:**
> also there is an existing panel applet called a drawer which as far as i can tell does basically the same stuff as your application except it only shows the filename etc as a tooltip which is rather useless for files but good for application launchers which and other applets which it can also handle.

Well, the drawer applet does something completely different then TopShelf. The drawer is basically an extension of a panel - you can add things to a drawer exactly as you add them to a panel; no difference. So you **can** add files to a drawer manually - as launchers - just as you can to a panel, but this is not very convenient IMO at least. It isn't what it is meant for. For example, you can't sort the launchers in a drawer by filename or other criteria, which TopShelf can in fact do.

> **trash said:**
> Fading unavailable files would look nice and be better than a popup message IMO:)
I already implemented this meanwhile :)  Unavailable files now appear with their filename in red. Note that this change is only in the development version (which you can see if you get the source code using Bazaar), not the 0.1 release and the 0.1 .debs.

---

### Post by urukrama on 2008-01-13
> **kripkenstein said:**
> Hmm, TopShelf is currently a gnome panel applet, so it would naturally depend on gnome-panel... :) But perhaps it doesn't need to be... I guess it could have the ability to run 'standalone' as an always-on-top window, without any connection to a panel. Is that what you would like?

Btw, what desktop are you using?

I am using Openbox and Xfce. TopShelf looks like something that would be very useful to me. I would run it as a stand-alone app that I could launch with a menu entry in Openbox, or on the xfce-panel.

If this is unfeasible or is not at all the direction you want to go with this app, that is fine with me.

---

### Post by kripkenstein on 2008-01-13
> **urukrama said:**
> I am using Openbox and Xfce. TopShelf looks like something that would be very useful to me. I would run it as a stand-alone app that I could launch with a menu entry in Openbox, or on the xfce-panel.

If this is unfeasible or is not at all the direction you want to go with this app, that is fine with me.
I think this is feasible, in fact, I already run it in a standalone window for debugging purposes. So I believe it should be possible to arrange this, I added it to my TODO list. (However, making it run in the Xfce panel would mean a lot more work, so I think I won't try to do that, but perhaps sometime later).

---

### Post by urukrama on 2008-01-13
To run it on the xfce panel should be doable with [this]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin"). I don't think you need to do much there.

But my main interest is the option to run it as a stand-alone app. Thank you for considering it. :-)

---

### Post by diskotek on 2008-01-13
looks really nice, thank you. i'll try it.

---

### Post by kripkenstein on 2008-01-13
> **urukrama said:**
> To run it on the xfce panel should be doable with [this]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin"). I don't think you need to do much there.

But my main interest is the option to run it as a stand-alone app. Thank you for considering it. :-)
Interesting, that link shows how to run any GNOME applet in an Xfce panel. Nice :) I added a mention of this to the README so Xfce users will know about it (if they don't already).

Meanwhile I finished coding the standalone version, wasn't hard. It'll be functional in 0.2.

---

### Post by urukrama on 2008-01-13
Wonderful!

---

### Post by init1 on 2008-01-13
> **kripkenstein said:**
> I'm sorry, I have no idea how to make RPMs... however, you can install it from source, this is **very** easy. Grab the .tar.gz from the releases directory [here]("http://codebrowse.launchpad.net/~kripkenstein/topshelf/main/files"), then just run make install (as superuser). That should work, unless your distro manages directories much differently than Debian/Ubuntu.

If someone knows how to make RPMs 'correctly', I'd be grateful for the help.

Thanks, it works great :D . Currently, I'm using Blag (Fedora based) and although the make file didn't work (/usr/lib/gnome-panel/ does not exist)  I was able to figure out how to install it. I'll try to make an RPM for it.
Edit:
I hadn't realized how difficult making an RPM was. I may or may not complete one. I suppose installing it from source isn't very hard though.

---

### Post by kripkenstein on 2008-01-14
> **init1 said:**
> Thanks, it works great :D . Currently, I'm using Blag (Fedora based) and although the make file didn't work (/usr/lib/gnome-panel/ does not exist)  I was able to figure out how to install it. I'll try to make an RPM for it.
Edit:
I hadn't realized how difficult making an RPM was. I may or may not complete one. I suppose installing it from source isn't very hard though.
Can you tell me what you needed to change for it to install (so I can add it to the documentation)?

---

### Post by init1 on 2008-01-14
> **kripkenstein said:**
> Can you tell me what you needed to change for it to install (so I can add it to the documentation)?
The only thing that was needed was to add the directory /usr/lib/gnome-panel/ and then the make script worked.

---

### Post by kripkenstein on 2008-01-15
> **init1 said:**
> The only thing that was needed was to add the directory /usr/lib/gnome-panel/ and then the make script worked.
Ok, thanks.

---

### Post by brunovecchi on 2008-01-15
Your application is in my panel now! And it's staying there! 
Really nice work, great idea. It works as I wished the shelf applet worked, back then I was disappointed at it.
I am willing to translate your application if you want! I'm a native spanish and would love to contribute in any way (I'm no developer, so making cool little apps like yours is out of the question). I clicked the "help translate" button but it said that I sould talk to you.

I'd also add tooltips to the wishlist, that is: when you hover over the buttons of the panel, a short description would pop up.

Congratulations, and thank you!

EDIT: It would also be great if it supported right-clicking on the file, to open it with a different program than the default one. :D

---

### Post by kripkenstein on 2008-01-15
> **brunovecchi said:**
> Your application is in my panel now! And it's staying there! 
Really nice work, great idea. It works as I wished the shelf applet worked, back then I was disappointed at it.
I am willing to translate your application if you want! I'm a native spanish and would love to contribute in any way (I'm no developer, so making cool little apps like yours is out of the question). I clicked the "help translate" button but it said that I sould talk to you.

I'd also add tooltips to the wishlist, that is: when you hover over the buttons of the panel, a short description would pop up.

Congratulations, and thank you!

EDIT: It would also be great if it supported right-clicking on the file, to open it with a different program than the default one. :D

Thanks for the positive response:)

Tooltips have already been added, in the development code (it'll be in 0.2).

I like your suggestion about rightclicking to allow opening with other programs. I'll look into this; if it isn't too complex, I'll do it.

---

### Post by brunovecchi on 2008-01-15
> **kripkenstein said:**
> 
Tooltips have already been added, in the development code (it'll be in 0.2).
.

Great! looking forward to the upgrade :)

Can I add one more? (sorry, it's just that I _actually_ find TS very useful!). It would be nice if it accepted keyboard input to remove files from the Shelf using the Delete button. I wouldn't know if it's too hard to implement or not, just mindless suggesting!

---

### Post by kripkenstein on 2008-01-15
> **brunovecchi said:**
> Great! looking forward to the upgrade :)

Can I add one more? (sorry, it's just that I _actually_ find TS very useful!). It would be nice if it accepted keyboard input to remove files from the Shelf using the Delete button. I wouldn't know if it's too hard to implement or not, just mindless suggesting!

Thanks for the suggestion. Actually I was meaning to let users close the window with "escape", so it isn't too hard to add deleting as well :)

---

### Post by stueyboy on 2008-01-16
great little ap thanks. I'll keep this thread in my subscribed list and look forward to future updates.

---

### Post by kripkenstein on 2008-01-16
Version 0.2 of TopShelf is hereby released. Changes:
```

	Ability to run standalone, i.e., not in a GNOME panel
	Show directories with nice mimetype
	Icons without transparency issues and other aesthetic matters
	Show missing files with red filenames (good for pluggable USB drives etc.)
	"Open containing folder" action
	Help docbook and tooltips for assistance
	No longer a popup window (can be resized normally)
	Keyboard actions: escape to close window, delete to remove a file
	"Are you sure?" on removal
	Rightclick menu for file actions

```

At this stage TopShelf is feature complete, as I see it. Hopefully bug-free as well, but I'm sure I missed some stuff...

You can download the source package [here]("https://launchpad.net/topshelf/trunk/0.2"). Installation is a simple "sudo make install". I think .deb packages will be built, but I'm not in charge of them, so no promises about that.

---

### Post by koleoptero on 2008-01-16
The resizeable window is much better than the previous one. Thanks a lot once more :D

---

### Post by urukrama on 2008-01-20
I install the latest version of topshelf (0.2.1), but haven't been able to run it yet.

The command 'topshelf' didn't work as I was told "bash: topshelf: command not found"

I tried running /usr/lib/gnome-panel/topshelf.py but that gave me the following error message:

> Traceback (most recent call last):
  File "/usr/lib/gnome-panel/topshelf.py", line 36, in ?
    import gnomeapplet
ImportError: No module named gnomeapplet


This was without the gnome-panel installed. I tried it also with the panel installed, but that gave the same error. An apt-cache search for gnomeapplet gave me nothing.

I am using Ubuntu Dapper.

Am I doing something wrong?

---

### Post by kripkenstein on 2008-01-20
> **urukrama said:**
> I install the latest version of topshelf (0.2.1), but haven't been able to run it yet.

The command 'topshelf' didn't work as I was told "bash: topshelf: command not found"

I tried running /usr/lib/gnome-panel/topshelf.py but that gave me the following error message:



This was without the gnome-panel installed. I tried it also with the panel installed, but that gave the same error. An apt-cache search for gnomeapplet gave me nothing.

I am using Ubuntu Dapper.

Am I doing something wrong?

TopShelf is a panel applet. To run it, add it to a panel. That is, rightclick on a panel, select add to panel, and select TopShelf (should be in the 'accessories'). You can add it to a GNOME panel or an XFce panel (instructions for the latter are in the README file).

You can also run TopShelf standalone, without a panel, but as of 2.1 this isn't recommended. If you want to, just run "python DIR/topshelf.py" where DIR is the path to topshelf.py (you can get it from the source code and put it whereever you want, this isn't automated at this point. Or do 'locate topshelf.py' to find where the installer placed it).

---

### Post by urukrama on 2008-01-20
I suppose TopShelf depends on some gnome material that is not available in Dapper. Running "python DIR/topshelf.py" gives the same error as above. And if I try to add it to my gnome-panel, I get and error message saying *"The panel encountered a problem while loading "OAFIID:Gnome_Panel_TopShelf" Do you want to delete the applet from your configuration?".*

Too bad... I'll guess I'll have to wait until I upgrade.

---

### Post by kripkenstein on 2008-01-20
> **urukrama said:**
> I suppose TopShelf depends on some gnome material that is not available in Dapper. Running "python DIR/topshelf.py" gives the same error as above. And if I try to add it to my gnome-panel, I get and error message saying *"The panel encountered a problem while loading "OAFIID:Gnome_Panel_TopShelf" Do you want to delete the applet from your configuration?".*

Too bad... I'll guess I'll have to wait until I upgrade.

I'm sorry, I made a mistake. There is in fact a simple solution here, you need to install the package
```

python-gnome2-desktop

```

---

### Post by Techwiz on 2008-01-20
I was wondering if there is any way I could change the icon? It doesn't fit with my theme.

---

### Post by kripkenstein on 2008-01-20
> **Techwiz said:**
> I was wondering if there is any way I could change the icon? It doesn't fit with my theme.

Sure. The relevant icons are at /usr/share/pixmaps, and they are
```

	topshelf-24.png 
	topshelf-48.png 
	topshelf-64.png 

```
Just overwrite them. 24 is the panel icon itself, 64 is used for the about dialog, and 48 is for the 'add to panel' dialog.

Edit: Btw, if anyone has some artistic ability and can draw up some nice icons for TopShelf, that would be great. I'm not an artist and I admit the current icons are not so good :) Any help is welcome.

---

### Post by urukrama on 2008-01-21
> **kripkenstein said:**
> I'm sorry, I made a mistake. There is in fact a simple solution here, you need to install the package
```

python-gnome2-desktop

```

I installed that and all its dependencies, but it still doesn't work. I can't add it to my gnome-panel (though it shows up in the Add to panel window), and when I try to run *python /usr/lib/gnome-panel/topshelf.py* I get the following error:

```
Traceback (most recent call last):
  File "/usr/lib/gnome-panel/topshelf.py", line 779, in ?
    factory(applet, None, standalone_window=main_window)
  File "/usr/lib/gnome-panel/topshelf.py", line 765, in factory
    ts = TopShelf(applet, standalone_window)
  File "/usr/lib/gnome-panel/topshelf.py", line 219, in __init__
    self.panel_image.set_tooltip_text("TopShelf")
AttributeError: 'gtk.Image' object has no attribute 'set_tooltip_text'

```

---

### Post by meborc on 2008-01-21
this little app is excellent :D i would love to see it integrated into the default installation... i have only used it for few days, but i have already used it more than most of the panel apps

i have only one thing that bothers me - when adding new items to the TS list, i always get moved to the filesystem folder... i would like it to be my home folder... also i am not able to add more then 1 file at the time

this little app rocks... :guitar:

---

### Post by kripkenstein on 2008-01-21
> **urukrama said:**
> I installed that and all its dependencies, but it still doesn't work. I can't add it to my gnome-panel (though it shows up in the Add to panel window), and when I try to run *python /usr/lib/gnome-panel/topshelf.py* I get the following error:

```
Traceback (most recent call last):
  File "/usr/lib/gnome-panel/topshelf.py", line 779, in ?
    factory(applet, None, standalone_window=main_window)
  File "/usr/lib/gnome-panel/topshelf.py", line 765, in factory
    ts = TopShelf(applet, standalone_window)
  File "/usr/lib/gnome-panel/topshelf.py", line 219, in __init__
    self.panel_image.set_tooltip_text("TopShelf")
AttributeError: 'gtk.Image' object has no attribute 'set_tooltip_text'

```
Tooltips are new in PyGtk 2.12... and I see that only Gutsy and Hardy have it. So I guess that is the issue.

I just committed a new version, revision #43. This will only apply tooltips if they are available. If you want, you can try to see if this works (hopefully it will). To test it, get the latest source using Bazaar ([instructions]("https://code.launchpad.net/~kripkenstein/topshelf/main")), if you haven't already, and "sudo make install".

---

### Post by kripkenstein on 2008-01-21
> **meborc said:**
> 
i have only one thing that bothers me - when adding new items to the TS list, i always get moved to the filesystem folder... i would like it to be my home folder... also i am not able to add more then 1 file at the time

Thanks for the suggestions. I'll add it to my TODO list.

---

### Post by koleoptero on 2008-01-21
I actually did some gimp work, and although these icons suck, I thought I'd post them here and if you like them better than the original, then use them.

> **meborc said:**
> i have only one thing that bothers me - when adding new items to the TS list, i always get moved to the filesystem folder... i would like it to be my home folder... also i am not able to add more then 1 file at the time

+1 to these. Multiple add, and startup from home or last directory would be nice.

---

### Post by kripkenstein on 2008-01-21
> **koleoptero said:**
> I actually did some gimp work, and although these icons suck, I thought I'd post them here and if you like them better than the original, then use them.

Thanks for the icons. I'm afraid however that there is a problem with using transparency, I should have mentioned this before. For some reason I can't figure out - might be a bug in python-gtk - transparency in the panel icon won't work (even though the icon has transparency and appears with transparency elsewhere than the panel). That is the reason for the current square icons - they don't rely on transparency.

As for the icons themselves, I like the idea of shelves. I am slightly worried however that at 24x24 this will not be understandable (but I might be wrong). Perhaps just a single shelf with only a few books on it?

---

### Post by koleoptero on 2008-01-21
> **kripkenstein said:**
> Thanks for the icons. I'm afraid however that there is a problem with using transparency, I should have mentioned this before. For some reason I can't figure out - might be a bug in python-gtk - transparency in the panel icon won't work (even though the icon has transparency and appears with transparency elsewhere than the panel). That is the reason for the current square icons - they don't rely on transparency.

As for the icons themselves, I like the idea of shelves. I am slightly worried however that at 24x24 this will not be understandable (but I might be wrong). Perhaps just a single shelf with only a few books on it?

The transparency seems to be working fine with my panel... :confused: But I can flatten them. The 24px icon is understandable as far as I'm concerned, but it could've been better of course, cause it's actually a resized version of the 64px icon with TS letters. I'll give them another shot. These were more a concept that actually usable icons (although I somewhat like the 64px one in the about dialog after all LOL).

---

### Post by kripkenstein on 2008-01-21
> **koleoptero said:**
> The transparency seems to be working fine with my panel... :confused:

Weird. Let's make sure: change the panel background color (in the panel preferences) to something very different like dark gray or black. Does transparency work in that case?

---

### Post by koleoptero on 2008-01-21
> **kripkenstein said:**
> Weird. Let's make sure: change the panel background color (in the panel preferences) to something very different like dark gray or black. Does transparency work in that case?

Ah no it doesn't. Should have checked before posting. Sorry :lolflag: I use a very white theme so it looks like it's working I suppose.

---

### Post by kripkenstein on 2008-01-21
> **koleoptero said:**
> Ah no it doesn't. Should have checked before posting. Sorry :lolflag: I use a very white theme so it looks like it's working I suppose.
Yep, exactly why I didn't notice it until someone filed a bug :)

---

### Post by kripkenstein on 2008-01-22
Ok, due to popular demand, I committed some updates (Rev #45) to let multiple files be selected and operated on, as well as remembering the directory in the 'add' dialog.

These should mostly work, but I'm not 100% sure about selecting and opening multiple files.

---

### Post by meborc on 2008-01-23
> **kripkenstein said:**
> Ok, due to popular demand, I committed some updates (Rev #45) to let multiple files be selected and operated on, as well as remembering the directory in the 'add' dialog.

These should mostly work, but I'm not 100% sure about selecting and opening multiple files.

sweet :)

---

### Post by kripkenstein on 2008-01-26
I'm close to releasing 0.3. If anyone feels like testing the latest trunk for bugs, now would be a good time :)

---

### Post by koleoptero on 2008-01-26
Had another go with help from a friend on the icons. Dumped the whole shelves idea, cause they only looked good on bright themes. Hope you like them better.

---

### Post by kripkenstein on 2008-01-27
> **koleoptero said:**
> Had another go with help from a friend on the icons. Dumped the whole shelves idea, cause they only looked good on bright themes. Hope you like them better.
Thanks, I tried these out. However, the colors look funny on my desktop somehow. I wasn't sure why until I read about the [Tango guidelines]("http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines") - it looks like this is something the icon should follow in order to have a good chance at being portable between themes.

I think I really like your original idea of a bookshelf. So my goal now is to get a Tango-compatible iconset for a bookshelf somehow. Meanwhile I've gotten transparency to work (finally...), so nice icons are possible in theory. I attach my first (not so good) idea at a simple abstract 'shelf with a book'. No Tango colors yet.

---

### Post by kripkenstein on 2008-01-27
0.3 is hereby [released]("https://launchpad.net/topshelf/trunk/0.3"). I did my best with the icons, but I hope to improve them at some point.

Changes:

	* F5 to refresh list
	* Multifile actions: in main view, and in add dialog
	* Remember last directory in add dialog, and default to home directory if none
	* New icons, somewhat Tango-ized. These should now look ok with more themes
	* Transparency and scaling of icons

---

### Post by hawkbane47 on 2008-11-24
Is there any way to set a hotkey for topshelf so that it can pop out?

---

### Post by kripkenstein on 2008-11-24
> **hawkbane47 said:**
> Is there any way to set a hotkey for topshelf so that it can pop out?

That's a good idea. I'm not sure how to implement it myself, I guess it would need to rely on some functionality in GTK or GNOME for hotkeys?

---

### Post by Grant A. on 2008-11-24
This feature exists in Windows, chances are, it's patented :(

---

