---
title: "Request: Blackbox 0.7"
date: 2005-05-29
forum: Ubuntu Backports
---

### Post by jonrkc on 2005-05-29
The latest Blackbox (window-manager) release on backports is 0.65.  This release is no longer supported and the Blackbox project suggests everybody should upgrade to 0.7 which supports newer window-manager standards.  I tried to install it from tar.gz but ran into a whole bunch of unmet dependencies--libraries newer than what Hoary includes, as well as the "iconv" program which itself has more dependencies, etc.

I am not smart enough to put together a package myself.  I belong to Club Mandriva from being a former Mandriva user (and I might maintain my membership!).  But I was surprised to see the latest package they offer is 0.65, also.  Strange, because it seemed better under Mandriva than the 0.65 I got via backports and tried out. Fonts were antialiased if you wanted, but I couldn't find that option on the unofficial Ubuntu version.

---

### Post by ow50 on 2005-05-31
Building it now. I won't test it, so you'll have to see yourself if it works.

---

### Post by jdong on 2005-05-31
preparing to upload....

---

### Post by jdong on 2005-05-31
ok, test.

---

### Post by jonrkc on 2005-05-31
[QUOTE=jdong]ok, test.[/QUOTE]
 Will do.  Thanks for your effort!  :)

---

### Post by jonrkc on 2005-05-31
I added the backports mirror (after removing the ubuntu.org one you said to remove that resulted in "Forbidden" message) but though I tried four or five times, I keep getting this, and the mirror keeps getting deleted by Synaptic from the source.list file:

```

root@ubuntu:~# Traceback (most recent call last):
  File "/usr/share/update-manager/python/dialog_add.py", line 88, in on_button_custom_clicked
    self.sourceslist.list.append(aptsources.SourceEntry(line))
  File "/usr/share/update-manager/python/aptsources.py", line 125, in __init__
    self.parse(line)
  File "/usr/share/update-manager/python/aptsources.py", line 87, in parse
    self.uri = string.strip(pieces[1])
IndexError: list index out of range

```

Can you suggest how I can fix this?  Thanks.

---

### Post by ow50 on 2005-05-31
You must have made a typo somewhere.

Try these instructions:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Make sure you add the staging repositories:
```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted
```

And remember that it takes a couple hours (about?) for the packages to show up at a mirror.

---

### Post by jonrkc on 2005-05-31
[QUOTE=ow50]You must have made a typo somewhere.

Try these instructions:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Make sure you add the staging repositories:
```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted
```

And remember that it takes a couple hours (about?) for the packages to show up at a mirror.[/QUOTE]
 Thanks.  But I still can't get the repositories added.  Here is an exact copy of what I put in the sources.list file.  It got deleted by apt-get as soon as I ran "update."

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted

deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
 
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

```

What am I doing wrong?

---

### Post by jonrkc on 2005-05-31
OK, I got it to work, though I'm not sure how.  I went through the steps in the instructions for adding repositories again, including this time the GPG-related one, which didn't seem to work, but perhaps did the trick anyway.  

Now the backports mirror is accepted, that's the main thing.  

Thanks for the tips!

---

### Post by jonrkc on 2005-05-31
Initial testing shows very nice appearance; it seems all the themes have been changed (something I wish didn't happen--Firefox does this, too).  The fonts look better now.  Key bindings don't work.  I suspect a new version of bbconf is needed, which I can probably obtain somewhere.  Likewise, bbpager could not connect with the window manager.  

A peculiarity of Blackbox is that some slit apps have to be loaded before Blackbox itself in order to work.  That means the GDM mechanism won't be able to handle Blackbox right, unless the user knows how and where to modify the GDM configuration files.  I believe messing with Gnome files is one of the unwisest things I can do--they seem very, very TOUCHY.  

So I improvised a temporary .xinitrc file and went back to the good old way (which I far prefer) of starting the X session with "startx" in a console.  That worked.

I'll work on the things I mentioned above and see how they go.  Should I post about that here, or would it be off-topic?

---

### Post by dlpfmVfH on 2005-05-31
bbkeys is at version 8.6 and for blackbox 0.7 bbkeys needs to be at version 9...
can you backport bbkeys please??

---

### Post by jonrkc on 2005-05-31
[QUOTE=aboe]bbkeys is at version 8.6 and for blackbox 0.7 bbkeys needs to be at version 9...
can you backport bbkeys please??[/QUOTE]
That's probably why bbconf (which includes a revised and easier version of bbkeys, by the way) doesn't work.  It hasn't caught up with blackbox 0.7 yet, is my guess.

It makes it really hard to switch between windows without key bindings to do it.  The mouse is useless if a window's totally obscured, unless you "shade" one or more windows to make the desired one visible...

I generally use IceWM anyway, but do enjoy the beautiful clean look of Blackbox a lot and use it when I'm in a beautiful clean mood.  :)

Maybe I'll just go back to version 0.65 and wait for things to settle down.  I do greatly appreciate jdong's quick action on version 0.7.  It will be useful someday, I hope soon.

---

### Post by jdong on 2005-05-31
ok, autobuilding and uploading....

---

### Post by dlpfmVfH on 2005-05-31
[QUOTE=jdong]ok, autobuilding and uploading....[/QUOTE]
 jdong youre the greatest!

---

### Post by jonrkc on 2005-05-31
Without wanting to sound biased, I have found in several forums that I've got especially friendly and useful help from users in the Netherlands and from South America.  I'm old enough (65! and counting, rapidly) to remember when it was exciting to receive a letter from abroad after a wait of ten days or more.  The first time I wrote on the Internet to somebody in Australia and about one minute later had their reply, it seemed unbelievable (1997).  Can anybody truly imagine what life without the Internet would be today?  I try, and I cannot.

OK, I'll get back on topic next time.  Thanks to all.

BTW, Blackbox 0.65 (I just now downloaded it and installed) works fine (again), but bbconf and bbpager refuse so far to work with it, while they worked normally a few days ago.  Another puzzle.

---

### Post by jdong on 2005-05-31
What bb* packages need work now?

---

### Post by dlpfmVfH on 2005-05-31
bbkeys works with blackbox 0.7

Have been playing with blackbox and the configuration...themes work, menu works, just needs to copy default menu to ~/.blackbox/menu, and gedit away...

docker works...

haven't tried the bbtools...

---

### Post by jonrkc on 2005-05-31
[QUOTE=aboe]bbkeys works with blackbox 0.7

Have been playing with blackbox and the configuration...themes work, menu works, just needs to copy default menu to ~/.blackbox/menu, and gedit away...

docker works...

haven't tried the bbtools...[/QUOTE]
 I installed blackbox 0.7 again and still can't get bbconf to make key bindings that work.  So I installed bbkeys and it complains that all the key bindings are invalid.  Then I tried bbpager and it says it cannot connect with the window manager.  At first it need a "Blackbox Styles" file that it couldn't find.  So I manually created one of those, assuming (with no documentation) that it would just contain the name of the style in use.  That enabled bbpager to load and appear on the screen, in the slot, in the form of a tiny little square about 3x3 pixels.  Click on the square once and it's gone for good.

So I'm not having much luck with blackbox 0.7 at this point.

---

### Post by dlpfmVfH on 2005-06-01
I installed bbkeys, and used the example bbkeys.rc from the wiki website...there's lots of information there,
You can also install blackbox-themes, and edit the blackboxrc and menu to list those and they work...

hope it helps you with blackbox 0.7

---

### Post by jonrkc on 2005-06-01
[QUOTE=aboe]I installed bbkeys, and used the example bbkeys.rc from the wiki website...there's lots of information there,
You can also install blackbox-themes, and edit the blackboxrc and menu to list those and they work...

hope it helps you with blackbox 0.7[/QUOTE]
 Which wiki is that?  I searched the Ubuntu wiki for "blackbox" and "bbkeys" and found nothing useful, and I couldn't find a wiki related to bbkeys anywhere....

I know the version of bbconf I have produces the old-style key bindings, yet it seems to be the latest, and bbkeys still refers to configuring bindings using bbconf...which I'd much rather do than to manually edit a file, if possible.  

At this point I'm rather confused!  It used to be so easy....  :(

---

### Post by dlpfmVfH on 2005-06-01
[http://blackboxwm.sourceforge.net/](http://blackboxwm.sourceforge.net/)

all information and example files came from there...
just read through it.. and for me it all worked out... did the manual edit and copy and paste from the example files...

just tried bbconf, with the new bbkeys from backport...but editting manually for me is easier.

---

### Post by jonrkc on 2005-06-01
[QUOTE=aboe][http://blackboxwm.sourceforge.net/](http://blackboxwm.sourceforge.net/)

all information and example files came from there...
just read through it.. and for me it all worked out... did the manual edit and copy and paste from the example files...

just tried bbconf, with the new bbkeys from backport...but editting manually for me is easier.[/QUOTE]
 I'm glad it works for you...I've spent hours with this and that version of everything and finally got to where bbkeys works but manual editing is the only option--bbconf produces the old-style bindings which are not used anymore in blackbox.  I think bbconf is not being developed anymore, but I haven't been able to confirm it after following dozens of search leads.  

Oh, well, I'll see if I can edit the .bbkeysrc file manually to my satisfaction, but there are terms in it I don't understand, so it won't be easy for me.

And bbpager (as noted before) doesn't work...so I'm beginning to feel I might as well forget about blackbox.  I did like using it before, when everything worked for me.

Thanks for your replies.

---

### Post by jonrkc on 2005-06-02
Update, next day--just to let you know this quest wasn't a total failure...  I still couldn't get blackbox functioning properly, but on about the sixth attempt to install fluxbox, I have just got it working, it seems, perfectly.  Yesterday it didn't display anything useful in the menus.  I uninstalled it and re-installed it and tried to find another debian package (couldn't, except ones marked incompatible with Ubuntu!), tried to compile it (couldn't get a libstd version it wanted)...  Then tried one more time with the Ubuntu packages and it works with full menus, transparency, configuration via menu, etc., etc.  Who knows why these things go the way they do.  I didn't download anything different from yesterday; I installed via apt-get like yesterday.  But today it works.

Fluxbox of course is so much like blackbox that I won't really miss blackbox except for the nice feeling it gives of being very very minimal.  :)

And fluxbox has the added advantage of tabbed windows, which I really like.  

So I'm pretty happy with my semi-minimal wm now.  I'll probably still use icewm most of the time if only out of a feeling of loyalty (and because it always does just what I want it to do).  But it's nice to have fluxbox again!

Thanks once more to jdong for acting so swiftly and generously on my blackbox request, even if I wasn't able to get the package to work on my system.  I hope it will work for lots of other users, for blackbox is a fine piece of software.

---

### Post by dlpfmVfH on 2005-06-03
jdong, I can't install the fluxbox package when blackbox is installed, Because attempt to overwrite  `/usr/share/man/man1/bsetroot.1.gz', thats also in fluxbox...

and the bbappconf, needs blackbox < 0.70 to work....

can you take a look at this?

---

### Post by jdong on 2005-06-03
[QUOTE=aboe]jdong, I can't install the fluxbox package when blackbox is installed, Because attempt to overwrite  `/usr/share/man/man1/bsetroot.1.gz', thats also in fluxbox...

and the bbappconf, needs blackbox < 0.70 to work....

can you take a look at this?[/QUOTE]

Hmm, I'll backport bbappconf, and tell devs about the fluxbox-blackbox conflict, which is still in Breezy.

---

### Post by jonrkc on 2005-06-03
[QUOTE=aboe]jdong, I can't install the fluxbox package when blackbox is installed, Because attempt to overwrite  `/usr/share/man/man1/bsetroot.1.gz', thats also in fluxbox...

and the bbappconf, needs blackbox < 0.70 to work....

can you take a look at this?[/QUOTE]
 I wouldn't hesitate to delete bsetroot.1.gz in order to install fluxbox, as it's only the man page for the fluxbox utility to set backgrounds.  It would apparently get put back in by the fluxbox installation anyhow....

If blackbox 0.70 is going to be in breezy, a lot of users are going to be unhappy that bbconf doesn't work with blackbox anymore.  That wouldn't be the fault of Ubuntu in any way--but bbconf is very popular among blackbox users, and I guess it just hasn't kept up with blackbox.  I'm surprised there isn't a mention of this on the blackbox page at sourceforge.

---

### Post by jonrkc on 2005-06-08
Well...I did delete bsetroot etc. in an attempt to install Blackbox as well as fluxbox--I got the same error message when I tried to install Blackbox. Deleting it didn't do any good.  Then I removed Fluxbox and was able to install Blackbox.  Next, I tried to install Fluxbox again--and got the same error message, even though the file didn't exist anymore.  

The good news is that I finally got both Blackbox and Fluxbox installed.  

The bad news is that I don't remember how I did it.  I do know that I messed so many things up in the process of fumbling around that it took me a couple of hours to get back to normal, or halfway normal, operation.  

I like how Blackbox loads instantly.  Why does Fluxbox take as long as KDE, or longer?!  

I do NOT like the themes (styles) furnished with Blackbox 0.7.  I think there's a way to convert old themes to use with it and it would certainly be worthwhile, because the old themes are very nice (and Fluxbox can use them).  That will be a project for sometime soon, but not tonight.

---

### Post by jdong on 2005-06-08
BTW, you could've used **dpkg --force-overwrite --install /var/cache/apt/archives/blackbox*.deb** ;)

---

### Post by allforcarrie on 2005-06-08
you can call it blackbuntu....... :-P

---

### Post by jonrkc on 2005-06-08
[QUOTE=jdong]BTW, you could've used **dpkg --force-overwrite --install /var/cache/apt/archives/blackbox*.deb** ;)[/QUOTE]
Ah...  I didn't know about that.  I'll add that command to my ever-growing list of lifesavers that I keep in JPilot memos (so I can refer to them even if the system's totally useless, by using my handheld).  

I know, I know...  If I'd thoroughly read the manual pages for apt and dpkg, etc.  I have skimmed them but there's so much to read and as it is I spend most of my time at the computer and a LOT of it reading manual pages.  I don't think one person could ever master it all.

---

### Post by jonrkc on 2005-06-09
Aboe, if you're still reading this thread--or anybody who's tried the new Blackbox 0.7--on your setup, are the titlebars and the window-bar at the bottom of the screen way fatter than on previous versions of Blackbox?  One of the things I liked about Blackbox was the thin decorations, and now with a 20-inch monitor I still prefer the thin decor just for its looks.  I imported a bunch of 0.65 styles into Blackbox and they are fat now where they were thin and elegant before. Then I converted them with bstyleconvert thinking maybe they needed that, but they remained the same.  Very disappointing!

I had Blackbox crash once this morning but considering I've been having other rather major trouble with Gnome and some apps rely on Gnome even though they're not "Gnome" apps--I won't blame it on Blackbox till I have my system more stable. 

The same lightning-fast operation is in Blackbox that I enjoyed before, and that's a plus.

I do think there's going to be a lot of people crying because bbconf doesn't work with it anymore, though.  The Blackbox wiki still makes reference to bbconf.  That will mislead some people.

---

