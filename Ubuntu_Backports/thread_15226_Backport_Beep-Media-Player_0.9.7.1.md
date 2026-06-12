---
title: "Backport: Beep-Media-Player 0.9.7.1"
date: 2005-02-13
forum: Ubuntu Backports
---

### Post by rufius on 2005-02-13
**Synopsis**
Backported beep-media-player 0.9.7.1 package per user request.

**Backporting Process**
The source archive directly came from Hoary. I was able to meet all dependencies with current dev libraries available in Warty.

**Packaging Status:**
i386 -- Staging at revision 20
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
Said program worked without error on packager's machine.

---

### Post by Nano on 2005-02-13
[QUOTE=rufius]**Synopsis**
Backported beep-media-player 0.9.7.1 package per user request.

**Backporting Process**
The source archive directly came from Hoary. I was able to meet all dependencies with current dev libraries available in Warty.

**Packaging Status:**
i386 -- Staging at revision 20
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
Said program worked without error on packager's machine.[/QUOTE]

Using it right now and it works perfectly.
However, I think it would be great to include some plugins for it also, like the notification icon.

---

### Post by rufius on 2005-02-13
[QUOTE=Nano]Using it right now and it works perfectly.
However, I think it would be great to include some plugins for it also, like the notification icon.[/QUOTE]
 I'll look into finding some of the plugins.

---

### Post by Nano on 2005-02-14
[QUOTE=rufius]I'll look into finding some of the plugins.[/QUOTE]

Wow! This is what I call a fast response!

Great, dude!

---

### Post by kassetra on 2005-02-22
I noticed that this upgrade requires me to upgrade glib as well... have the new glibs been tested?  Are they fairly stable?

---

### Post by jdong on 2005-02-23
The ubp2 revision has been confirmed working and stable by a few. ubp1 had a menu-changing issue.

---

### Post by rufius on 2005-02-23
jdong is correct, the newest version of the glib2.0 backport is stable and has run without flaw on my system and others have reported success in using it.

---

### Post by kassetra on 2005-02-23
[QUOTE=rufius]jdong is correct, the newest version of the glib2.0 backport is stable and has run without flaw on my system and others have reported success in using it.[/QUOTE]

That's super wonderful and all I needed to know.  :)
Man I love you guys!

You ever need any graphics-ish anything, you let me know!  :)

quick note here: I chose to upgrade beep-media-player and beep-media-player-dev at the same time, and I got a bunch of overwrite errors, which caused b-m-p-dev not to be upgraded, so I had to go back and upgrade it after the initial upgrade was over.

---

### Post by rufius on 2005-02-23
Odd, I hadn't gotten those when I upgraded my bmp-dev stuff. I'll be sure to keep that in mind for ubp2 version of bmp.

---

### Post by kassetra on 2005-03-02
[QUOTE=rufius]jdong is correct, the newest version of the glib2.0 backport is stable and has run without flaw on my system and others have reported success in using it.[/QUOTE]

Hmmm, I've noticed a small flaw actually... It probably doesn't happen on other people's computers because they don't customize their menus... 

I have (had) a heavily customized applications menu - with my own sections and launchers... now, however, the launchers that I added do not appear.  When I check in the menu system, such as applications:/// et al., they are still there and still correct, but do not show up in my menus.

For example, I created a "favorites" section in my applications menu to add all of my favorite launchers, the section for "Favorites" still shows in the menu, but the launchers that should be in that sub menu do not appear any longer.

I can live, obviously, but I would like my customized applications menu back some time... and yeah, I can recreate it if I have to.

---

### Post by dcstar on 2005-03-03
[QUOTE=kassetra]Hmmm, I've noticed a small flaw actually... It probably doesn't happen on other people's computers because they don't customize their menus... 

I have (had) a heavily customized applications menu - with my own sections and launchers... now, however, the launchers that I added do not appear.  When I check in the menu system, such as applications:/// et al., they are still there and still correct, but do not show up in my menus.

For example, I created a "favorites" section in my applications menu to add all of my favorite launchers, the section for "Favorites" still shows in the menu, but the launchers that should be in that sub menu do not appear any longer.

I can live, obviously, but I would like my customized applications menu back some time... and yeah, I can recreate it if I have to.[/QUOTE]
I reported the same issue with the ligblib ubp2 files a couple of days ago, but I am still awaiting a response:

[http://ubuntuforums.org/showthread.php?t=15468](http://ubuntuforums.org/showthread.php?t=15468)

---

### Post by rufius on 2005-03-03
[QUOTE=dcstar]I reported the same issue with the ligblib ubp2 files a couple of days ago, but I am still awaiting a response:

[http://ubuntuforums.org/showthread.php?t=15468](http://ubuntuforums.org/showthread.php?t=15468)[/QUOTE]

I'd suggest you roll back your glib2.0 version to the one from the stable Warty tree. I believe its 2.4.7. Then re-upgrade and see if the problem persists. If it doesn't I'll have to look deeper into it.

---

### Post by kassetra on 2005-03-03
[QUOTE=rufius]I'd suggest you roll back your glib2.0 version to the one from the stable Warty tree. I believe its 2.4.7. Then re-upgrade and see if the problem persists. If it doesn't I'll have to look deeper into it.[/QUOTE]

eep!  This apply to me as well?

---

### Post by dcstar on 2005-03-03
[QUOTE=rufius]I'd suggest you roll back your glib2.0 version to the one from the stable Warty tree. I believe its 2.4.7. Then re-upgrade and see if the problem persists. If it doesn't I'll have to look deeper into it.[/QUOTE]
I done the roll-back and re-upgrade about 3 times now with no change, unfortunately if I try to roll glib back at this very time, I also have to roll-back the recent backport of Firefox!

---

### Post by kassetra on 2005-03-04
[QUOTE=kassetra]eep!  This apply to me as well?[/QUOTE]

all fixed, thanks rufius.  

dcstar - are you rolling back from synaptic?  I did it from the command line and it worked great...

---

### Post by dcstar on 2005-03-04
[QUOTE=kassetra]all fixed, thanks rufius.  

dcstar - are you rolling back from synaptic?  I did it from the command line and it worked great...[/QUOTE]
Yes, I did (try to) use Synaptic - and I have a heap of items that will be removed if I downgrade.

What was you command line solution?

---

### Post by kassetra on 2005-03-04
[QUOTE=dcstar]Yes, I did (try to) use Synaptic - and I have a heap of items that will be removed if I downgrade.

What was you command line solution?[/QUOTE]

What I did:
1. Download all of the .deb files from the warty version (if you're using a standard pc, go [here]("http://www.linuxpeach.com/temp.zip") and open the zip file, then put the directory on your desktop or in your home directory... those are all the files I just used.)
2. Change to that new directory from a terminal (cd /Desktop/temp or wherever) and then install them from the terminal with: sudo dpkg -i *.deb
3. Reboot your computer (the whole thing, just to be sure) -- some things will *not* work when you first reboot because of the downgrade, but you'll fix that asap in the next step:
4. Open synaptic and upgrade libglib... (say yes to what it wants to remove and what it wants to upgrade, most likely the only thing it will want to remove is the -dbg package)

As soon as I did that last upgrade, everything was fixed.  :)

---

### Post by dcstar on 2005-03-04
[QUOTE=kassetra]What I did:
1. Download all of the .deb files from the warty version (if you're using a standard pc, go [here]("http://www.linuxpeach.com/temp.zip") and open the zip file, then put the directory on your desktop or in your home directory... those are all the files I just used.)
2. Change to that new directory from a terminal (cd /Desktop/temp or wherever) and then install them from the terminal with: sudo dpkg -i *.deb
3. Reboot your computer (the whole thing, just to be sure) -- some things will *not* work when you first reboot because of the downgrade, but you'll fix that asap in the next step:
4. Open synaptic and upgrade libglib... (say yes to what it wants to remove and what it wants to upgrade, most likely the only thing it will want to remove is the -dbg package)

As soon as I did that last upgrade, everything was fixed.  :)[/QUOTE]
Unfortunately it was all going well until step 4 - my system had full menus again but Synaptic complained that Firefox was a broken package, and when I "fixed" it by upgrading all the libglib components, I was back to square one (after a reboot) - no customised menus!

I will do steps 2 and 4 again, and live with a "broken" (but working) Firefox and my menus.

Thanks for the help anyway, it's appreciated.

---

### Post by rufius on 2005-03-04
[QUOTE=dcstar]Unfortunately it was all going well until step 4 - my system had full menus again but Synaptic complained that Firefox was a broken package, and when I "fixed" it by upgrading all the libglib components, I was back to square one (after a reboot) - no customised menus!

I will do steps 2 and 4 again, and live with a "broken" (but working) Firefox and my menus.

Thanks for the help anyway, it's appreciated.[/QUOTE]
 Thats odd dcstar, because I was the one that helped kassetra roll back her glib and it went flawless, needless to say because I've had to do it several times lol. It may just take some playing around with though I've done the process at least 5 times on this box because of one screw-up or another.

---

### Post by dcstar on 2005-03-05
[QUOTE=rufius]Thats odd dcstar, because I was the one that helped kassetra roll back her glib and it went flawless, needless to say because I've had to do it several times lol. It may just take some playing around with though I've done the process at least 5 times on this box because of one screw-up or another.[/QUOTE]
The rollback worked fine, it was the subsequent step which re-upgraded it again which caused the (same) problem.

The latest port of Firefox and it's libglib dependency also just got too annoying for me, so I've stepped back to the previous Firefox version so I once again can regain control of my packages.

---

