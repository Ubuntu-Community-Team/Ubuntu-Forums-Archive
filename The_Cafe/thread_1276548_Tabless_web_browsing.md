---
title: "Tabless web browsing"
date: 2009-09-27
forum: The Cafe
---

### Post by etnlIcarus on 2009-09-27
I recently realised that I had no need of tabs (afterall, the only reason tabs were introduced, was due to the explorer shell's limitations when it came to managing multiple windows) and that I could interact with my web browser in a much more sophisticated manner, by using separate windows and leveraging all the functionality of my window manager.

Turns out that in practice, it's just as good as it sounded in-theory, except for one little thing: memory usage.

With tabs, only the active tab's pixmaps seem to be retained in memory. With multiple windows and a composited environment, every page I have open is being repainted and is being retained in memory, which is proving problematic, when you're running an Athlon 2800+, with only 512mb of RAM.

My main browser is Firefox 3.5 but I've also tried the latest Midori (RAM usage quickly jumps to triple-digits and is less responsive under load) and Arora (crashes with just a couple of windows open).

I was wondering if anyone else had any experience with this issue, and had any ideas, short of going back to using tabs?

---

### Post by hoppipolla on 2009-09-27
Don't tabs also provide a faster way of switching between lots of pages? I mean... otherwise all the pages would be overlapping and my desktop would be very cluttered! hehe :)

---

### Post by etnlIcarus on 2009-09-27
> **hoppipolla said:**
> Don't tabs also provide a faster way of switching between lots of pages? I mean... otherwise all the pages would be overlapping and my desktop would be very cluttered! hehe :)

With separate windows, I can use:
- the tasklist (basically identical to tabs, except I can scroll-wheel through the list, get thumbnails on mouse-over, and can access all the functionality libwnk offers)
- Compiz' Scale plugin
- Xfdesktop's window list
- I can also lay pages out spatially, so they're not necessarily hidden behind one another.
- Edit: Whoops, I forgot ring-switcher, accessible via alt+tab.

---

### Post by MadCow108 on 2009-09-27
maybe you sould use opera
it provides 2 of those natively (thumbnails by mouseover scrollwheel switching (with thumbnails) and tiling)

---

### Post by etnlIcarus on 2009-09-27
Opera has always been far too buggy for my liking, and it's UI is atrocious (someone forgot to tell Opera that suites and MDIs were retired years ago). And that would still mean going back to tabs, meaning I lose that WM integration.

---

### Post by Colonel Kilkenny on 2009-09-27
> **etnlIcarus said:**
> Opera has always been far too buggy for my liking, and it's UI is atrocious (someone forgot to tell Opera that suites and MDIs were retired years ago). And that would still mean going back to tabs, meaning I lose that WM integration.

Use Opera without tabs?

And Opera's GUI is also much more easily customizable than Firefox UI (to a certain degree). If suites "were retired" years ago, why is Opera still a suite? And why Firefox / Seamonkey / Safari / Chrome / IE / Arora / Midori / etc. users & developers keep on adding these suite features (both native and via extensions) to their own applications? That MDI vs. SDI problem is also just stupid because you can easily use Opera exactly like you would use any SDI application.

I'd also like see/hear some examples of these Opera bugs you mentioned, but perhaps it's not appropriate for this thread.

---

### Post by &#32 Greg on 2009-09-27
> **etnlIcarus said:**
> I recently realised that I had no need of tabs (afterall, the only reason tabs were introduced, was due to the explorer shell's limitations when it came to managing multiple windows) and that I could interact with my web browser in a much more sophisticated manner, by using separate windows and leveraging all the functionality of my window manager.

Turns out that in practice, it's just as good as it sounded in-theory, except for one little thing: memory usage.

With tabs, only the active tab's pixmaps seem to be retained in memory. With multiple windows and a composited environment, every page I have open is being repainted and is being retained in memory, which is proving problematic, when you're running an Athlon 2800+, with only 512mb of RAM.

My main browser is Firefox 3.5 but I've also tried the latest Midori (RAM usage quickly jumps to triple-digits and is less responsive under load) and Arora (crashes with just a couple of windows open).

I was wondering if anyone else had any experience with this issue, and had any ideas, short of going back to using tabs?

Uzbl is designed for having multiple windows opened, you might want to look at that.

---

### Post by Machnikowski on 2009-09-27
I'm willing to lose a bit of resources for tabs. Now that I've experienced browser tabs, I don't think I could ever go back. :)

---

### Post by sertse on 2009-09-27
Though UI designers argue, your liking of tabs actually a fault of your WM. Tabs on a basic level attempt to do the same things your WM does, to manage "the things you have opened". An ideal WM would be designed that you never feel the need to use tabs, which is an inconsistent and overlapping way  on top of things. 

I say this has a tab user, but I accept the theory behind it, and hope towards a "better wm"

On topic: I never noticed it before, but it seems to be case now that you mention it...

(I also think Midori is lighter, I can tell w/ my Aspire One where the fan turns on after a certain threshold - Firefox's CPU jumps will trigger it, Midori doesn't. However, I can't dispute what you feel on your own comp so whatever ;) )

---

### Post by SomeGuyDude on 2009-09-27
Tabs are just too good, especially if you're the kind of person that never has less than four going. It's not uncommon for me to have about a dozen or so, and tabs are just far easier to organize. 

By the way:

1) You can scroll through tabs if your cursor is over them.
2) You can Alt+[number] to insta-switch to a tab, with the caveat that Alt+9 always goes to the last tab.
3) You can close ALL of your tabs at once with Ctrl+Q, as opposed to closing all instances which would require a "killall firefox" or otherwise overly-involved method.
4) Your taskbar is going to be a nightmare after a while if you use one. Tabs are convenient because it separates things.

Just for starters.

---

### Post by etnlIcarus on 2009-09-27
> **MadCow108 said:**
> maybe you sould use opera
it provides 2 of those natively (thumbnails by mouseover scrollwheel switching (with thumbnails) and tiling)

> **Colonel Kilkenny said:**
> Use Opera without tabs?

...

That MDI vs. SDI problem is also just stupid because you can easily use Opera exactly like you would use any SDI application.Well that's kind of defeating the purpose now, isn't it?

> And Opera's GUI is also much more easily customizable than Firefox UI (to a certain degree).I'm unsure whether to ask for an elaboration. I suspect I'll only end up more confused. > If suites "were retired" years ago, why is Opera still a suite? And why Firefox / Seamonkey / Safari / Chrome / IE / Arora / Midori / etc. users & developers keep on adding these suite features (both native and via extensions) to their own applications?There are arguments to be made for software suites - but these aren't them. 

> I'd also like see/hear some examples of these Opera bugs you mentioned, but perhaps it's not appropriate for this thread.Crashes, goofy scrolling, improper caching, rendering glitches (well, arguable), off the top of my head. Opera's browser for PCs has always behaved like more of a software demo, for Opera's embedded products.

[quote=setse]An ideal WM would be designed that you never feel the need to use tabs[/quote]I'd never imagined I'd be saying this but that ideal has more or less been reached with compiz. The, "Place Windows", plugin is about the only thing you need to tweak, to ensure all browser windows open at a predictable place on the screen.

> I also think Midori is lighterI regularly do what I like to call, "the digg test". It's thoroughly un-scientific but testing your browser's mettle is about all digg.com is good for.

1 - open a new session in your browser of choice.
2 - go to the digg homepage.
3 - open every article on the homepage in tabs/windows.
4 - check memory usage/general responsiveness.
5 - close all those tabs/windows, bar the homepage, and check memory/responsiveness again.

Midori will become so slow, as to be utterly unusable, before all the pages can load. It'll easily exceed FF3.5 in memory usage. And after closing all those tabs/windows, it'll still be over 100mb of RAM usage and generally slow. Firefox is far from pleasant after doing this, either and 3.5 is the first version to properly handle memory but it'll remain usable. Arora gets to the 3rd tab/window, locks up and I'm forced to kill it. Opera handles itself pretty well but that still doesn't stop it from being the Frankenstein's Monster of the browser world.

Anyway, that's just my experience, on my PC. Midori and Arora just aren't viable options for me. Don't interpret that as some kind of objective declaration of the quality/attributes of the mentioned browsers.

---

### Post by etnlIcarus on 2009-09-27
> **  Greg said:**
> Uzbl is designed for having multiple windows opened, you might want to look at that.First good idea in thread. Cheers, I'll check it out.

> **SomeGuyDude said:**
> 
1) You can scroll through tabs if your cursor is over them.
2) You can Alt+[number] to insta-switch to a tab, with the caveat that Alt+9 always goes to the last tab.
3) You can close ALL of your tabs at once with Ctrl+Q, as opposed to closing all instances which would require a "killall firefox" or otherwise overly-involved method.
4) Your taskbar is going to be a nightmare after a while if you use one. Tabs are convenient because it separates things.

Just for starters.
1. Not without having to add additional extensions. By default, all the scrollwheel will do is pan through the tabbar, once it 'overflows'.
2. Meh.
3. Whatever happened to just closing the window?
4. Tasklist is no messier than the tabbar. If you're referring to other applications: I make extensive use of workspaces.

---

### Post by Tipped OuT on 2009-09-27
> **someguydude said:**
> tabs are just too good, especially if you're the kind of person that never has less than four going. It's not uncommon for me to have about a dozen or so, and tabs are just far easier to organize. 

By the way:

1) you can scroll through tabs if your cursor is over them.
2) you can alt+[number] to insta-switch to a tab, with the caveat that alt+9 always goes to the last tab.
3) you can close all of your tabs at once with ctrl+q, as opposed to closing all instances which would require a "killall firefox" or otherwise overly-involved method.
4) your taskbar is going to be a nightmare after a while if you use one. Tabs are convenient because it separates things.

Just for starters.

+1

---

### Post by SunnyRabbiera on 2009-09-27
Personally I have grown to really dislike taskbar clutter, so I like using tabs when possible.

---

### Post by SomeGuyDude on 2009-09-27
> **etnlIcarus said:**
> 1. Not without having to add additional extensions. By default, all the scrollwheel will do is pan through the tabbar, once it 'overflows'.
2. Meh.
3. Whatever happened to just closing the window?
4. Tasklist is no messier than the tabbar. If you're referring to other applications: I make extensive use of workspaces.

1) Um. No. I'm doing it right now in Chromium, for example, and obviously I have no anything added.

2) What an eloquent response. I thank you for your carefully thought out input.

3) Do you want to close 12 windows separately? Boy, what an awesome time saver. I don't know why I still use tabs.

4) It adds bulk unless you've got taskbar groups, which would defeat the purpose since you can't change between instances on sight.

Tabs were brought about for a reason: they work better. Imagine if you use a tiling window manager. Having each browser window separate would be a NIGHTMARE.

---

### Post by &#32 Greg on 2009-09-27
> **SomeGuyDude said:**
> 
Tabs were brought about for a reason: they work better. Imagine if you use a tiling window manager. Having each browser window separate would be a NIGHTMARE.

Not true. It works well with Xmonad, for instance- tabbed mode :)

---

### Post by SomeGuyDude on 2009-09-27
> **  Greg said:**
> Not true. It works well with Xmonad, for instance- tabbed mode :)

Tabbed mode explains how it works well if you aren't using tabs? What? :confused:

---

### Post by phrostbyte on 2009-09-27
> **SomeGuyDude said:**
> Tabbed mode explains how it works well if you aren't using tabs? What? :confused:

Some window managers organize opened windows into tabs, thus making tabs in applications kind of redundant.

---

### Post by purgatori on 2009-09-27
Uzbl + Wmii = better than tabs any day :P

---

### Post by doorknob60 on 2009-09-28
Using multiple windows *never* worked well for me back in the IE days, bad memories, I can't imagine going back to that...though it would certainly be better now than it was back then...still, I like tabs :)

---

### Post by ynnhoj on 2009-09-28
i'm rather happy using [surf](http://surf.suckless.org/). (it's probably better clone the latest source rather than downloading the tarball, which might be missing a couple patches that were submitted recently)

if you're a vimperator user but want to get something smaller than firefox while keeping the vim-ness, then [vimpression](https://projects.ring0.de/webkitbrowser/) might be what you're looking for.

PS: when i tried to build these, the version of libwebkit in the (Jaunty) repos didn't seem to cut it. but after adding [this PPA](https://launchpad.net/~webkit-team/+archive/ppa) to my system and updating libwebkit, surf and vimpression built fine.

> **SomeGuyDude said:**
> Tabs were brought about for a reason: they work better. Imagine if you use a tiling window manager. Having each browser window separate would be a NIGHTMARE.
i'm using a tiling window manager-- and i don't think it's a nightmare at all! tabs don't necessarily work better for everybody.

---

### Post by shuttleworthwannabe on 2009-09-28
Why not use epiphany-browser, it opens new windows each time. Uses gecko-rendering engine and is essentially FF only leaner.

S

---

### Post by spupy on 2009-09-28
> **phrostbyte said:**
> Some window managers organize opened windows into tabs, thus making tabs in applications kind of redundant.

In Fluxbox there are tabs. I set the window manager to automatically tab together all firefox windows. I still use tabs, but much less. I open a new firefox window for a new 'tasks'. For example, one window looking at pictures, one window browsing python docs, one window with forums, etc.

There is (was?) a similar tabbing plugin for Compiz.

---

### Post by peakshysteria on 2009-09-28
> **etnlIcarus said:**
> I recently realised that I had no need of tabs (afterall, the only reason tabs were introduced, was due to the explorer shell's limitations when it came to managing multiple windows) and that I could interact with my web browser in a much more sophisticated manner, by using separate windows and leveraging all the functionality of my window manager.

Turns out that in practice, it's just as good as it sounded in-theory, except for one little thing: memory usage.

With tabs, only the active tab's pixmaps seem to be retained in memory. With multiple windows and a composited environment, every page I have open is being repainted and is being retained in memory, which is proving problematic, when you're running an Athlon 2800+, with only 512mb of RAM.

My main browser is Firefox 3.5 but I've also tried the latest Midori (RAM usage quickly jumps to triple-digits and is less responsive under load) and Arora (crashes with just a couple of windows open).

I was wondering if anyone else had any experience with this issue, and had any ideas, short of going back to using tabs?

I cannot see that it is possible to use less resources with more windows than one. Even though, if it is preferable, it is possible off course to set FF to open new windows instead of new tabs.

But I think it would be more effective to use custom builds or to streamline your current install. It is possible to tweak different parts of FF to help you minimize the resources used. Google FF Userchrome.css tweaks and you get tons of links.

Also take a look at some of these links:

[Swiftfox]("http://getswiftfox.com/")

[Firefox Custom Builds]("http://www.ghacks.net/2009/05/09/firefox-custom-builds/")

[The Burning Edge]("http://www.squarefree.com/burningedge/")

_______________________________________

Or you can tweak your current tab setup with TabMix+. Also remember to rightclick and remove unwanted images from different sites. In addition Flashblock helps you to stop unnecessary resources being used for those awful flash commercials. I really cant live without my tabs.

My Firefox Information

Last updated: Mon, 28 Sep 2009 12:36:39 GMT
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3

**Extensions** (enabled: 19, disabled: 1; total: 20)
[list]
[*][Autohide](http://www.krickelkrackel.de/autohide/) 1.3.1 [disabled]
[*][Dictionary Switcher](http://en.design-noir.de/mozilla/dictionary-switcher/) 1.0 
[*][Dictionary Tooltip](http://www.dictionarytip.com) 1.5 
[*][DownloadHelper](http://www.downloadhelper.net) 4.6.2 
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.11.2 
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.10.1 
[*][Greasemonkey](http://www.greasespot.net/) 0.8.20090920.2 
[*][Highlighter](http://hashcolouredtabs.mozdev.org/highlighter/) 0.1.4 
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10.1 
[*][last.fmCode](http://mll2.free.fr/?p=42) 0.7b 
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.6 
[*][Locationbar²](http://en.design-noir.de/mozilla/locationbar2/) 1.0.3 
[*][Nightly Tester Tools](http://www.oxymoronical.com/web/firefox/nightly) 2.0.2 
[*][Norsk Bokmål og Nynorsk ordliste]() 2.0.10.0 
[*][Personas](http://www.getpersonas.com/) 1.2.4 
[*][SmoothWheel (AMO)](http://smoothwheel.mozdev.org/) 0.44.18.20090408.3 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.7.4pre.090516 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 3.1.2009032701 
[*][Tiny Menu](http://trac.arantius.com/wiki/Extensions/TinyMenu) 2.0.1 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.5 
[/list]

**Themes** (6)
[list]
[*]Camifox [selected]
[*]Chromifox Basic 
[*]Daum Firefox&#50857; &#53580;&#47560; 
[*]Default 
[*]Dustfox 
[*]Elementary 
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]Java(TM) Plug-in 1.6.0_16-b01
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]VLC Multimedia Plugin (compatible Totem 2.26.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]

---

### Post by Mr. Picklesworth on 2009-09-28
I find it interesting how many evangelists there are trying desperately to make you see the wrong in your Unix-like ways :P


> **  Greg said:**
> Uzbl is designed for having multiple windows opened, you might want to look at that.

Yep, [Uzbl]("http://www.uzbl.org/") may be the perfect thing for you.

I absolutely agree with your reasoning, too. [This fellow]("http://mystilleef.blogspot.com/2006/10/no-tabs-why.html") has more of it!

That's what I'm hoping for with GNOME Shell, as well: there is an honest attempt to refresh the window manager, and killing the window list (which has facilitated bad window management for a long time!) is one of the first items on the agenda.
We don't necessarily need a tabbed window manager. Just one that exposes windows which are behind each other without breaking context, and where the user can define items he wants to keep together.

---

### Post by sertse on 2009-09-28
> **spupy said:**
> In Fluxbox there are tabs. I set the window manager to automatically tab together all firefox windows.

Do share how? It's sounds useful.

---

### Post by etnlIcarus on 2009-09-28
> **SomeGuyDude said:**
> 1) Um. No. I'm doing it right now in Chromium, for example, and obviously I have no anything added.

2) What an eloquent response. I thank you for your carefully thought out input.

3) Do you want to close 12 windows separately? Boy, what an awesome time saver. I don't know why I still use tabs.

4) It adds bulk unless you've got taskbar groups, which would defeat the purpose since you can't change between instances on sight.

Tabs were brought about for a reason: they work better. Imagine if you use a tiling window manager. Having each browser window separate would be a NIGHTMARE.
1. And that's relevant to me how? I'm asking for a solution to my memory usage problems, without going back to tabs. You're suggesting I keep the tabs *and* the high memory usage.
2. How else am I meant to respond to your trumping a feature I don't give a hoot about? You'd also need to be a card counter just to make practical use of that feature.
3. File>Quit.
4. Learn to read:> Tasklist is no messier than the tabbar. If you're referring to other applications: I make extensive use of workspaces.
> **shuttleworthwannabe said:**
> Why not use epiphany-browser, it opens new windows each time. Uses gecko-rendering engine and is essentially FF only leaner.

S
I haven't used Epiphany for a while. I'm currently trying to figure out how to get the webkit builds back.

[quote=Mr. Picklesworth]I find it interesting how many evangelists there are, trying desperately to make you see the wrong in your Unix-like ways.[/quote]They're doing a good job, too; using Windows terminology like, "taskbar". Clearly, the voice of authority on alternative environments!

Anyway, thanks for the suggestions, folks. As soon as I've got time to think, I'll be looking into a lot of these alternatives.

---

### Post by starcannon on 2009-09-28
@OP;

To answer your question, the only thing I can think of that would be a very immediate, and noticeable fix, would be to upgrade your ram to =>2gb. Running compiz with some fairly generous effects, and a half dozen or more browser windows, yup, I can see how things might slow down. Ram is your key to moving forward, if your motherboard will let you, put in 3gb.

GL and HF

---

### Post by spupy on 2009-09-28
> **sertse said:**
> Do share how? It's sounds useful.
In the _~/.fluxbox/apps_ file, my entry for firefox:
```
[group]
 [app] (class=Shiretoko)
  [Workspace]   {0}
  [Dimensions]  {1170 728}
  [Deco]        {TAB}
  [IconHidden]  {yes}
[end]
```

You just need to add "[group]" before the app. There is more info here: [Grouping apps via the apps file.]("http://fluxbox-wiki.org/index.php?title=Howto_edit_the_apps_file#Grouping_apps_via_the_apps_file")
(It says Shiretoko there since this is the name of firefox in arch. The other settings are not relevant, only the "group" tag.)

---

### Post by etnlIcarus on 2009-09-28
> **starcannon said:**
> @OP;

To answer your question, the only thing I can think of that would be a very immediate, and noticeable fix, would be to upgrade your ram to =>2gb. Running compiz with some fairly generous effects, and a half dozen or more browser windows, yup, I can see how things might slow down. Ram is your key to moving forward, if your motherboard will let you, put in 3gb.

GL and HF

I plan to replace this rig in 6 or so months, anyway, not that I've got a lot in the way of, "generous effects", anyway.

---

