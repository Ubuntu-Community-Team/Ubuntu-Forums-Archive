---
title: "Tabby window manager a la Chrome"
date: 2009-12-17
forum: The Cafe
---

### Post by beloved88 on 2009-12-17
Who loves Chrome tabs!?
I DOOOOOO!!!!!
It's the one reason why i use Chrome over Firefox, because it's uses space on my itty bitty netbook screen so effectively.

Now, what if there was a window manager that took all the multiple instances of programs and put them in a nice tabby window!?  

Well, for one my window-picker-applet would stop crowding out all my launchers while doing research papers! :D

If you like this idea, support it at [brainstorm.ubuntu.com/idea/23000/]("http://brainstorm.ubuntu.com/idea/23000/")

I have no idea how i got lucky enough to have idea # 23k but it makes me super happy

If you have any input, +/-, leave it here

@Moderators: if you want to move this somewhere else, i don't care, i don't really know the best place on the forum to promote my crazy ideas like this.

---

### Post by earthpigg on 2009-12-17
LXDE's panel has a 'combine multiple application windows into a single button' option.

so if i have 5 terminal windows open, the panel still only shows me 1 window 'tab' down there... is that what you seek?

incidentally, i run lxde on my netbook and <3 it.

---

### Post by beloved88 on 2009-12-17
very interesting.  What libraries does it use?  Does it use GTK+?  Would i be able to install the netbook-launcher package on top of that?
kinda, but basically what i am seeking is something exactly like Chrome's tabs-in-the-title-bar

---

### Post by beloved88 on 2009-12-17
> **earthpigg said:**
> so if i have 5 terminal windows open Terminal's can have tabs too!  you probably already knew that already though, but i just found that out today while doing research to make sure i wasn't proposing a duplicate idea

---

### Post by hellion0 on 2009-12-17
This would be a pretty good idea. Not everyone's using super-huge resolutions, especially those using netbooks and older laptops. This'd save a lot of space. Alternately, integrating the window close/hide/maximize(/shade/stick/menu) buttons into the panel (and doing away with the titlebar entirely) wouldn't be such a bad idea either, I think.

Either way, I'm hoping one of the big WMs (Metacity, Kwin, Xfwm) integrates this at least as an option in the near future.

---

### Post by lzfy on 2009-12-17
Something like this?
[[img]http://omploader.org/tMzBpZA[/img]](http://omploader.org/vMzBpZA)

---

### Post by earthpigg on 2009-12-17
> **beloved88 said:**
> very interesting.  What libraries does it use?  Does it use GTK+?  Would i be able to install the netbook-launcher package on top of that?
kinda, but basically what i am seeking is something exactly like Chrome's tabs-in-the-title-bar

it's gtk+.

ive never played with ubuntu's netbook implementation of gnome alongside lxlauncher. i suppose it would work, though. i don't see why not.

it does, however, have this:
[IMG]http://wiki.lxde.org/en/images/5/5c/LXlauncher.png[/IMG]
the package is called 'lxlauncher'. to have it start at boot, add "@lxlauncher" to /etc/xdg/lxsession/LXDE.

result:
application groups at the top, tabbed windows wherein multiple instances of the same app share a single window selector at the bottom.

---

### Post by wersdaluv on 2009-12-17
> **lzfy said:**
> Something like this?
[[img]http://omploader.org/tMzBpZA[/img]](http://omploader.org/vMzBpZA)
Wow how'd you get that?

It feels confusing though. Tabs on top and bottom. lol

---

### Post by AllRadioisDead on 2009-12-17
> **lzfy said:**
> Something like this?
[[IMG]http://omploader.org/tMzBpZA[/IMG]]("http://omploader.org/vMzBpZA")
I believe that's what OP was looking for.

---

### Post by beloved88 on 2009-12-17
> **lzfy said:**
> Something like this?
 Yes, something like that.  But i prefer gnome and GTK+ apps.  Although did that have different programs in the same window?  I wouldn't like that, i would just want it to group all the instances of just one program in each window automatically.  What package is that you're showing me? is that KDE's default window manager?

---

### Post by beloved88 on 2009-12-17
> **earthpigg said:**
> it's gtk+.

ive never played with ubuntu's netbook implementation of gnome alongside lxlauncher. i suppose it would work, though. i don't see why not.

I'll have to play with that on a VM for a while and look into that, thanks
> 
result:
application groups at the top, tabbed windows wherein multiple instances of the same app share a single window selector at the bottom.
ehh, i don't like to have a second bar along the bottom.  Everything for me is across the top, even though it's a little crowded with all my launchers, window-picker and indicators, personal preference.[IMG]http://lh3.ggpht.com/_41UF2Kxmhr0/SynqfuE7QwI/AAAAAAAAAIM/p6RRIFyymXM/s640/Screenshot.png[/IMG]

---

### Post by beloved88 on 2009-12-17
basically, the exact thing I am looking for is exactly as Chrome.  I'm not saying Canonical techs need to build a special package designed just for me, but linux is all about having it your way, even moreso that burgerking, i would like to see what i want possible through configuration, as well as what ever everybody else wants too

---

### Post by beloved88 on 2009-12-17
oh, i was meaning to ask someone, just because i am curious, how is Windows' implementation of tabs.  Does Explorer (file, not internet) allow for tabs like Nautilus does? any other programs than IE?  OSS has always seemed to lead the way with the whole tabby idea.  Random trivia, anyone know what the first program to impliment tabs was?

---

### Post by Hetor on 2009-12-17
> **lzfy said:**
> Something like this?
[[img]http://omploader.org/tMzBpZA[/img]](http://omploader.org/vMzBpZA)

I love it. I would run KDE 4.4 when it comes out, but my PC specs won't let me :(

---

### Post by TheNessus on 2009-12-17
> **beloved88 said:**
> Yes, something like that.  But i prefer gnome and GTK+ apps.  Although did that have different programs in the same window?  I wouldn't like that, i would just want it to group all the instances of just one program in each window automatically.  What package is that you're showing me? is that KDE's default window manager?

eeeh...Nautilus can have tabs. just right click "open a new tab"...

---

### Post by lzfy on 2009-12-17
> **beloved88 said:**
> Yes, something like that.  But i prefer gnome and GTK+ apps.  Although did that have different programs in the same window?  I wouldn't like that, i would just want it to group all the instances of just one program in each window automatically.  What package is that you're showing me? is that KDE's default window manager?

KDE 4.4 allows you to group windows by dragging them into each other. So if you want all instances of Dolphin in one window, you can. It doesn't do this by default though, you have to drag and drop with middle mouse click. I hope I was clear with my bad English :P

---

### Post by beloved88 on 2009-12-17
> **TheNessus said:**
> eeeh...Nautilus can have tabs. just right click "open a new tab"...
yeah, i know, but
1) that's not the program that clutters my window-picker, it's things like Oo.o and tomboy notes and document viewer
2) it's tabs show up below the menu, a la firefox.  It takes away from the space inside the window.  Chrome's tabs are consolidated in the title bar, taking a somewhat unfunctional space and turning it into something much more functional.  Sorry if i sound like a Google fan boy, but chrome really has a nearly perfect balance between form and function.  No space is wasted, functionality is juiced to it's max.  I dare say it's elegant, and i wish everything else was thus as elegant.

---

### Post by beloved88 on 2009-12-17
> **lzfy said:**
> KDE 4.4 allows you to group windows by dragging them into each other. So if you want all instances of Dolphin in one window, you can. It doesn't do this by default though, you have to drag and drop with middle mouse click. I hope I was clear with my bad English :P
that's kinda what i figured, but it's a step in the right direction.  It's too bad i despise KDE for some reason.  I didn't like it 6 years ago when i first was introduced to Linux, and i didn't like it when i tried it out again recently.  Gnome and xfce just work with my brain, and i'm gonna try out lxde soon.

---

### Post by Tibuda on 2009-12-17
I think Fluxbox and Compiz can group windows in tabs. I can't confirm, as I don't use those window managers.

---

### Post by Xbehave on 2009-12-17
> **Hetor said:**
> I love it. I would run KDE 4.4 when it comes out, but my PC specs won't let me :(
What specs you got? I'm running kde4.4 on turion@2GHZ (bogomips:1595.67) and a crappy internal card using radeon drivers.

You can run, gtk apps with an alternative window manager (that's what happens if you have desktop effects on)
Compiz a.k.a desktop effects already offers this ([http://wiki.compiz.org/Plugins/Group](http://wiki.compiz.org/Plugins/Group))
Kwin will offer this in 4.4
Fluxbox offers this

edit: oops missed danielrmt's post, i suppose I'm just confirming what he said

---

### Post by urukrama on 2009-12-17
Try Fluxbox or Pekwm. Both WMs can tab windows and allow you to set rules to automatically tab certain applications (Pekwm does; I think Fluxbox does too), so that you get the effect you wanted: all your terminals are tabbed together, all your text editors, etc.

Some older window managers also have this function.

---

### Post by beloved88 on 2009-12-17
I'll have to play with these once i get a spare second.  If the tabs do show up neatly in the title bar, I'll simply change the idea I'm promoting to use * window manager is default in NBR instead of Maximus.  If not, I'll still promote my original idea.  Can somebody provides some screenshots Pekwm and fluxbox's tabbed windows?

Oh, also, since the idea I am proposing on brainstorm is specifically for NBR, it would need to run on GTK+ libraries and be lightweight, low ram/cpu reqs.  How do these match up?

---

### Post by MaxIBoy on 2009-12-17
Compiz can group and tab windows. It would be kinda cool to integrate this with the window decorator.

---

### Post by Mr. Picklesworth on 2009-12-17
Fluxbox does tabs properly (similar to how KDE 4.4 does them). Personally, there being no integration with the decorator with Compiz's tabs horrifies me. Just feels hopelessly wrong!

Come to think of it, I wonder if any of Chromium's tabbing functionality is implemented by [the ChromiumOS window manager]("http://www.chromium.org/chromium-os/chromiumos-design-docs/software-architecture#TOC-Chromium-and-the-window-manager")? (whose name I sadly forget)

Edit: Ah, [there it is]("http://src.chromium.org/cgi-bin/gitweb.cgi?p=chromiumos.git;a=tree;f=src/platform/window_manager;h=232bed4a46731e29368b76dedc86804d66fa29c7;hb=HEAD") if someone feels like a lot of (probably pointless) tinkering.


Another edit:

Okay, I did it! Umm... it actually runs, and it has pretty effects. It maximizes almost everything, and you can switch between windows in a few different ways (keyboard shortcuts!). It definitely doesn't do any window decorations at all, so, no tabs.

The thread here has some relevant information: [http://ubuntuforums.org/showthread.php?t=1331975](http://ubuntuforums.org/showthread.php?t=1331975)

F8 gives a little keyboard overlay that explains the various shortcuts available, Alt+number switches between windows, F12 gives you a zoomed out view of all the windows.

---

### Post by beloved88 on 2009-12-17
> **MaxIBoy said:**
> Compiz can group and tab windows. It would be kinda cool to integrate this with the window decorator.

compiz doesn't play well with netbook launcher (scrolling up and down on the launcher changes workspaces, rather than scrolling through menu option, renders the launcher useless for menus with a large number of entries. i've seen absolutely no tabs in metacity except what programs have themselves. Haven't tried fluxbox yet though...

---

### Post by K.Mandla on 2009-12-17
> **urukrama said:**
> Try Fluxbox or Pekwm. Both WMs can tab windows and allow you to set rules to automatically tab certain applications (Pekwm does; I think Fluxbox does too), so that you get the effect you wanted: all your terminals are tabbed together, all your text editors, etc.

Some older window managers also have this function.
+1.

[http://urukrama.wordpress.com/2008/07/21/a-tabbed-desktop/](http://urukrama.wordpress.com/2008/07/21/a-tabbed-desktop/)

(Yes, I do have a bulletproof memory. ;) )

---

### Post by beloved88 on 2009-12-22
pekwm doesn't seem to play nice with gnome-panel, netbook-launcher, and chrome, but the basic tabs functionability is what i'm looking for, idk, if only metacity could do that too...

---

### Post by hessiess on 2009-12-22
Stumpwm, and most tiling WM's can group windows.

---

### Post by spupy on 2009-12-22
> **beloved88 said:**
> Who loves Chrome tabs!?
I DOOOOOO!!!!!
It's the one reason why i use Chrome over Firefox, because it's uses space on my itty bitty netbook screen so effectively.

Firefox takes a lot less space if you know how to customize it.
Search for vimperator, userChrome.css, [total toolbar]("http://totaltoolbar.mozdev.org/").

---

### Post by Warpnow on 2009-12-22
[http://awesome.naquadah.org/images/screen.png](http://awesome.naquadah.org/images/screen.png)

I had a setup with Awesome for a while where each app was spawned in a new tab at the top with the title of the application. It worked decently well. Don't have a screenshot of it, though.

---

### Post by hessiess on 2009-12-22
> 
It's the one reason why i use Chrome over Firefox, because it's uses space on my itty bitty netbook screen so effectively.

My firefox doesn't use any screen space for the UI, its extremely constomisable;)

---

### Post by madnessjack on 2009-12-22
> **hessiess said:**
> My firefox doesn't use any screen space for the UI, its extremely constomisable;)
Me neither :P
[http://jack.kingbrick.co.uk/blog/my-firefox.png](http://jack.kingbrick.co.uk/blog/my-firefox.png) (that's with a bookmarks bar)

---

