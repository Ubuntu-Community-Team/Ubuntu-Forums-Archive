---
title: "A couple of things about Karmic (good and bad)..."
date: 2009-11-02
forum: Testimonials &amp; Experiences
---

### Post by monkeyKata on 2009-11-02
So how are y'all liking Karmic?

A few things I dig:
- Apps seem to load a bit quicker
- Intel graphics are the smoothest yet (with the 2.9 driver).  Animations look better than before, no delay on maximizing windows (wobbly windows enabled)
- New wallpapers look great, professional.  Good balance.
- Appearance app is showing me icons/previews for everything again (it did so before, but at some point it stopped and just put a question mark next to each theme).
- Login screen looks professional, as does the simplistic glowing Ubuntu logo (this made me think of the apple logo on the back of mac laptops.  Maybe the developers are trying to polish everything up)

A few things I don't dig so much:
- Can no longer seem to theme the GDM/login screen.
- Bug with the volume control muting from 0 through about 15% volume.
- Changing wallpaper no longer fades. (Funny, when the fade was introduced whenever that was one or two versions back, I disliked it.  Now with it taken out [or maybe just disabled], I miss it.)
- Software Center.  I guess it's got potential, though I just don't like the look and feel of it.  I use Synaptic mostly, but I'd like the old Add/Remove back.  Is this possible now?
- When launching Rhythmbox, it goes to the notification area and doesn't actually open, or pop up.  You have to (or at least I do on my machine) click again on the icon in the notification area.  To me this is annoying, and I couldn't find a setting to change this in the preferences.

So yeah...  what do you all think?  And I'm not highlighting what I dislike to complain, but instead in hopes of seeing if anyone else feels as I do or has found a way to fix/change/revert some of these settings.

---

### Post by 3rdalbum on 2009-11-03
GDM has been rewritten, so old themes won't work on the new GDM.

I'm not sure about the fading wallpaper - it sometimes does it for me, and sometimes doesn't do it. It's gotta be a bug.

Try looking in gconf-editor for the Rhythmbox setting. It doesn't do that behaviour here on my computer.

---

### Post by monkeyKata on 2009-11-03
Thanks for the tip.  I checked configuration editor and couldn't find a setting for it.  And I read that about the GDM, how it's actually a newer version not yet able to be themed.

---

### Post by dominiquec on 2009-11-03
It seems pretty minor but inability to change GDM login themes is a sore point for me.  Might have been all right if Karmic had a login screen as nice as Jaunty's (that was tops in my book.)

---

### Post by UnrealMiniMe on 2009-11-03
> **monkeyKata said:**
> 
- Software Center.  I guess it's got potential, though I just don't like the look and feel of it.  I use Synaptic mostly, but I'd like the old Add/Remove back.  Is this possible now?


I agree with you on the look and feel of the Ubuntu Software Center.  Until we can sort apps by popularity and browse the full app list without choosing a category, I'll continue using the trusty old Add/Remove Applications.

If you want to use it, just install the gnome-app-install package via Synaptic or the command line.  It popped up at the top of my System->Administration menu. :)

---

### Post by airencracken on 2009-11-04
I agree about the GDM themes. I don't like having my user name listed, I prefer typing it in. I dislike the loss of customizability. It's too much like Apple. Hopefully the new version of GDM will support themes soon. The login sound isn't customizable either, had to rename the file to stop the login drums. Again, not being customizable is *bad thing*. Hopefully it's all just growing pains for the new version of gnome though.

---

### Post by Yanno on 2009-11-04
The ext4 file system is much quicker than before.The broadcom updating failure really troubled me and I still have problems about USB mounting.I don't know why the auto mounting doesn't work,I have to use this below each time I login
              sudo start udev

---

### Post by GodLikeCreature on 2009-11-04
> **monkeyKata said:**
> So how are y'all liking Karmic?

A few things I dig:
- Apps seem to load a bit quicker
- Intel graphics are the smoothest yet (with the 2.9 driver).  Animations look better than before, no delay on maximizing windows (wobbly windows enabled)
- New wallpapers look great, professional.  Good balance.
- Appearance app is showing me icons/previews for everything again (it did so before, but at some point it stopped and just put a question mark next to each theme).
- Login screen looks professional, as does the simplistic glowing Ubuntu logo (this made me think of the apple logo on the back of mac laptops.  Maybe the developers are trying to polish everything up)

A few things I don't dig so much:
- Can no longer seem to theme the GDM/login screen.
- Bug with the volume control muting from 0 through about 15% volume.
- Changing wallpaper no longer fades. (Funny, when the fade was introduced whenever that was one or two versions back, I disliked it.  Now with it taken out [or maybe just disabled], I miss it.)
- Software Center.  I guess it's got potential, though I just don't like the look and feel of it.  I use Synaptic mostly, but I'd like the old Add/Remove back.  Is this possible now?
- When launching Rhythmbox, it goes to the notification area and doesn't actually open, or pop up.  You have to (or at least I do on my machine) click again on the icon in the notification area.  To me this is annoying, and I couldn't find a setting to change this in the preferences.

So yeah...  what do you all think?  And I'm not highlighting what I dislike to complain, but instead in hopes of seeing if anyone else feels as I do or has found a way to fix/change/revert some of these settings.

Strange...  I consistently get the fading on the wallpaper change, but it is a lot faster now, which I like.  But doing it anyways?

As for the Rythmbox thing, in my case this depends on how I close the app.  If I close it by right-clicking the icon on the notification area, with the application not showing, it will open as such next time.  However, if I close the application while it is showing, using Ctrl-Q, it will open normally on next open...  Is this something you have tried?

---

### Post by solwic on 2009-11-04
> **dominiquec said:**
> It seems pretty minor but inability to change GDM login themes is a sore point for me.  Might have been all right if Karmic had a login screen as nice as Jaunty's (that was tops in my book.)

+1.  The changes in Karmic to the login system weren't an improvement, IMHO.

---

### Post by Flyers2391 on 2009-11-04
> **monkeyKata said:**
> So how are y'all liking Karmic?
- When launching Rhythmbox, it goes to the notification area and doesn't actually open, or pop up.  You have to (or at least I do on my machine) click again on the icon in the notification area.  To me this is annoying, and I couldn't find a setting to change this in the preferences.

I've had a this happen with Rythmbox before, but that is when I right click > quit when it is already minimized the the notification area.  If I close it when the full interface is viewable it comes back in that view.  I figured it was a feature to open as it closed?

Separately, I found this thread because of the login screen comments ... I, too, dislike how my name is listed in the new login screen.

---

### Post by Vostrocity on 2009-11-04
I was kinda busy the last week, so I just updated to Karmic now. Just a few things off the bat:
-Everything seems a little bit choppier, maybe it will smoothen out
-The wallpaper fade works inconsistently as other people noticed
-Don't like the new GDM (nevermind I actually like it better)
-Like the new upper right notifications (except for the [async positioning]("https://bugs.launchpad.net/notify-osd/+bug/434789"))
-Two-finger scroll is broken (fixed it but now I can't have sidescroll and two-finger simultaneously)
-Switching workspaces with scrolling on desktop is broken (fixed in Compiz)
-The new Humanity icons are just as ugly (using Simple icon set)
-Boot was slower, maybe because it's the first time (faster second time)

---

### Post by Zoot7 on 2009-11-04
I find it a lot snappier than Jaunty. :)

---

### Post by monkeyKata on 2009-11-05
Whoa I hadn't checked back on this thread... I didn't expect all the replies.

Yes, I've since noticed the bit about closing Rhythmbox.  If I go into the menu and hit quit instead it will then pop open the next time launched.  Before just x-ing out at the top right corner of the window closed *and* quit the program, now it just closes the window and leaves it running in the notification area.  I was going to say I dislike this... though just now playing with it I see it allows you to keep music playing after closing the window, which I guess could be space-saving and useful if you're just letting the music go and not paying attention to it, browsing through tracks and all.

About the GDM and theming.  I don't mind having my name already there.  Do some of y'all who do mind not like having your name/username visible by default?  Just curious.  I could see that.  Hopefully theming capabilities will return soon.  I think it ought to be customizable, with whatever streamlined look they're going for only there by default.  Being able to change everything up is why I like linux so much.

UnrealMiniMe, thanks for the tip about Add/Remove.  I'll look for the package.

Oh, and the lower volumes being muted thing can be fixed, as I got Kushkah's solution working from this post:

[http://ubuntuforums.org/showthread.php?t=1309427](http://ubuntuforums.org/showthread.php?t=1309427)

---

### Post by Donalb on 2009-11-05
I skipped Jaunty, cause of the Intel graphics regression problems and Karmic Intel Graphics are now awesome. I now have all the bells & whistles from the same onboard graphics card.

But I really miss the GDM for login. I've got (don't know why) the UGLY login screen

[IMG]http://i33.tinypic.com/21ce80l.jpg[/IMG]

And the only fix I've found, I don't understand how to follow!

[http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/)

---

### Post by solwic on 2009-11-05
> **Zoot7 said:**
> I find it a lot snappier than Jaunty. :)

Boot time was slower on Karmic than Jaunty on my machine, but once it was up and running, it did seem to be a little snappier.

---

### Post by D351 on 2009-11-07
> **airencracken said:**
> I agree about the GDM themes. I don't like having my user name listed, I prefer typing it in. I dislike the loss of customizability. It's too much like Apple. Hopefully the new version of GDM will support themes soon. The login sound isn't customizable either, had to rename the file to stop the login drums. Again, not being customizable is *bad thing*. Hopefully it's all just growing pains for the new version of gnome though.

Seriously, customization was a huge selling point for previous versions. As far as my user experience goes, not being able to customize the login screen is the only major change... that and the idicator-applet-session which (once I figured out how to change the icons) I really like.

---

### Post by solwic on 2009-11-07
> **D351 said:**
> Seriously, customization was a huge selling point for previous versions. As far as my user experience goes, not being able to customize the login screen is the only major change... that and the idicator-applet-session which (once I figured out how to change the icons) I really like.

You can't customize the login screen anymore?  I didn't realize that had changed.

That's kinda lame, if you ask me.  One more reason to skip Karmic, I guess.

---

### Post by noelvh on 2009-11-07
So far for me the only issue I have is with FireFox. I feel FF is a bit slower and the scroll dose not work all the time for me. I some time have to kill FF and start over. I did try the 3.6 beta but I did not like the way it opens tabs next to the current tab an not on the end of the tab line.

As for the log on screen I never use it so I don't care what it looks like, or if I can change it. I have also never change it in the past even when I did use it. This issue can not be what keep one from using KK.

I will report the boot time in longer then it was in JJ, but I did build KK on a new to me hard drive, and my laptop dose not care for it as it dose not have the crash protection the BIOS is looking for. But that is not KK's fault nor do I care. Once it is up, it runs faster than JJ. My system is older it a IBM T43 with an ATI x300 video card, 2gb of ram.

I did try and upgrade from JJ, and that sucked, so I did a clean install after deleting all my .files from my home drive. Works like a top. I have also installe this on a number of other machines with out issue. I can not talk for others and there issues but I am sure issues will get worked out, in a few months. 

Noel

---

### Post by solwic on 2009-11-07
> **noelvh said:**
> So far for me the only issue I have is with FireFox. I feel FF is a bit slower and the scroll dose not work all the time for me. I some time have to kill FF and start over. I did try the 3.6 beta but I did not like the way it opens tabs next to the current tab an not on the end of the tab line.

As for the log on screen I never use it so I don't care what it looks like, or if I can change it. I have also never change it in the past even when I did use it. This issue can not be what keep one from using KK.

I will report the boot time in longer then it was in JJ, but I did build KK on a new to me hard drive, and my laptop dose not care for it as it dose not have the crash protection the BIOS is looking for. But that is not KK's fault nor do I care. Once it is up, it runs faster than JJ. My system is older it a IBM T43 with an ATI x300 video card, 2gb of ram.

I did try and upgrade from JJ, and that sucked, so I did a clean install after deleting all my .files from my home drive. Works like a top. I have also installe this on a number of other machines with out issue. I can not talk for others and there issues but I am sure issues will get worked out, in a few months. 

Noel

There's a fix to that Firefox problem:  Opera.  Unless you play Facebook apps...then you're kind of stuck with Firefox, at least for that....

:biggrin:

---

### Post by raj7095 on 2009-11-07
Few of the things have been oversimplified.

---

### Post by noelvh on 2009-11-07
I gave Opera a shot but i love the FF add ons and can not live with out them. I am dealing with the issues as they are not so bad. But thanks for the reply, and the suggestion. If not for the FF add ons I would have made the switch.

Noel

---

