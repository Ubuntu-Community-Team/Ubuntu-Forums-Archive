---
title: "Firefox 3 release megathread"
date: 2008-03-10
forum: The Cafe
---

### Post by selda on 2008-03-10
Fourth beta of Firefox 3 is out - [https://www.mozilla.com/en-US/firefox/all-beta.html](https://www.mozilla.com/en-US/firefox/all-beta.html)

---

### Post by vishzilla on 2008-03-10
Awesome, downloading it right away!!!

---

### Post by Polygon on 2008-03-11
*waits for firefox-3.0 package in ubuntu to be updated*

---

### Post by sunexplodes on 2008-03-11
You guys aught to be using the Swiftfox repo. It uses nightlies (so now, the 3.0 Beta 5 pre-releases), and can be configured using apt or by downloading deb files.

---

### Post by mrgnash on 2008-03-11
Hopefully Hardy updates soon, because the .tar.gz version appears to have a problem grabbing the Gnome icon theme.

---

### Post by SomeGuyDude on 2008-03-11
> **sunexplodes said:**
> You guys aught to be using the Swiftfox repo. It uses nightlies (so now, the 3.0 Beta 5 pre-releases), and can be configured using apt or by downloading deb files.

Problem: plugins don't keep up with nightlies. Thus, my upgrading is dependent upon the speed of plugin updates.

---

### Post by sunexplodes on 2008-03-11
Which plugins? I have no problem at all with Flash or MPlayer (although I'm using Arch).

And as for extensions, 99% work just fine with "extensions.checkCompatibility" set to "false" in about:config.

---

### Post by SomeGuyDude on 2008-03-11
Extensions, my bad.

Hm. I'll give that a shot with the compatibility thing, actually. Good tip! I'd imagine the few I use aren't going to break anything.

STATUS REPORT: all is good. Nice!!

---

### Post by mrgnash on 2008-03-11
Ok I'm seeing the same problem with 3.0.5bpre; is anyone else experiencing the same thing -- i.e. instead of using the icons from the gnome icon theme, it just displays little boxes with red 'x' symbols?

---

### Post by RJ Hythloday on 2008-03-11
> **sunexplodes said:**
> Which plugins? I have no problem at all with Flash or MPlayer (although I'm using Arch).
 
And as for extensions, 99% work just fine with "extensions.checkCompatibility" set to "false" in about:config.
That's pretty cool, I've been thinking about giving 3 a try.

---

### Post by Erunno on 2008-03-11
Just tested it on Mac OS X and there's still no keychain integration. Bummer, I was hoping that Firefox 3 would be a better citizen on non-Windows platforms.

How's the situation on Linux respectively GNOME?

---

### Post by 23meg on 2008-03-11
> **Erunno said:**
> Just tested it on Mac OS X and there's still no keychain integration. Bummer, I was hoping that Firefox 3 would be a better citizen on non-Windows platforms.

How's the situation on Linux respectively GNOME?

[http://blog.mozilla.com/dolske/2007/05/28/followup-password-manager-changes-coming-in-ff3-alpha-5/](http://blog.mozilla.com/dolske/2007/05/28/followup-password-manager-changes-coming-in-ff3-alpha-5/)

---

### Post by Erunno on 2008-03-11
> **23meg said:**
> [http://blog.mozilla.com/dolske/2007/05/28/followup-password-manager-changes-coming-in-ff3-alpha-5/](http://blog.mozilla.com/dolske/2007/05/28/followup-password-manager-changes-coming-in-ff3-alpha-5/)

Yes, this blog entry is full of shoulds and coulds but so far nothing usable has materialized on the user-visible side. Does this mean that integration with the base system will be offloaded to 3rd party plug-in developers? Judging by the fact that this is already the fourth beta release I doubt that we'll see anything official from the Mozilla developers for the final release. It would probably slander to assume that this has anything to do with Mozilla's main target platform (i.e. Windows) being the only supported OS which has no such facilities.

---

### Post by mrgnash on 2008-03-11
[img]http://img360.imageshack.us/img360/2555/screenshotbd4.png[/img]

Seriously. Is nobody else experiencing this problem?

EDIT: I discovered that it seems to be a problem with loading svg icon themes:

```
(firefox-bin:8455): Gtk-WARNING **: Error loading theme icon 'gtk-undo-ltr' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so: wrong ELF class: ELFCLASS64

```

Hence, the error would appear when I was using either the default Hardy 'Human' icon theme, or 'Ultimate Gnome' -- both of which contain SVG icons. When I switched to a non-svg theme, the problem did not arise.

---

### Post by TheCarNinja on 2008-03-11
> **sunexplodes said:**
> Which plugins? I have no problem at all with Flash or MPlayer (although I'm using Arch).

And as for extensions, 99% work just fine with "extensions.checkCompatibility" set to "false" in about:config.

This option doesn't exist in my about:config. Am I missing something? :(

---

### Post by 23meg on 2008-03-11
> **Erunno said:**
> Yes, this blog entry is full of shoulds and coulds but so far nothing usable has materialized on the user-visible side. Does this mean that integration with the base system will be offloaded to 3rd party plug-in developers? 

It's "offloaded" to anyone who's ready to put in the (apparently little) work. It may already be done in trunk, actually; it's been a while since the beta deadline.

---

### Post by enaut on 2008-03-11
> **TheCarNinja said:**
> This option doesn't exist in my about:config. Am I missing something? :(

just create it by right clicking...

---

### Post by Kakihara on 2008-03-11
I am getting
```
Error: in guard: symbol required but got: Error: fatal: looped fatal error
```
when running ./firefox

and
```
./firefox-bin: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory
```
when running ./firefox-bin

libjemalloc.so is present in the same directory.
Ubuntu 7.10
anybody experienced this? any suggestion?

---

### Post by TheCarNinja on 2008-03-11
> **enaut said:**
> just create it by right clicking...

Didn't know you could do that, thank you.

---

### Post by mech7 on 2008-03-11
Umm how can i install it? I allready have b3 from the repository ?

---

### Post by SomeGuyDude on 2008-03-11
As a note, the latest Swiftfox is CRAZY good on RAM usage.

---

### Post by kuja on 2008-03-11
> **mrgnash said:**
> 

Seriously. Is nobody else experiencing this problem?

EDIT: I discovered that it seems to be a problem with loading svg icon themes:

```
(firefox-bin:8455): Gtk-WARNING **: Error loading theme icon 'gtk-undo-ltr' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so: wrong ELF class: ELFCLASS64

```

Hence, the error would appear when I was using either the default Hardy 'Human' icon theme, or 'Ultimate Gnome' -- both of which contain SVG icons. When I switched to a non-svg theme, the problem did not arise.

Looks like the error you get when a 32-bit program tries to load a 64-bit lib ... or maybe the other way around, I forget.

---

### Post by Mazza558 on 2008-03-11
> **mech7 said:**
> Umm how can i install it? I allready have b3 from the repository ?

I'd like to know too. I downloaded that file and are using beta 4 now, but only in a folder in /home - this means that every time I start it, it comes up with a tab welcoming me to beta 4... :(

---

### Post by sunexplodes on 2008-03-11
Dudes, listen. Follow the instructions here: [http://getswiftfox.com/](http://getswiftfox.com/)

Swiftfox is a bleeding-edge build of Firefox3, optimized for Linux systems. They have a repository so you can install it with Apt. There's really no good reason to use vanilla Firefox.

---

### Post by Mazza558 on 2008-03-11
> **sunexplodes said:**
> Dudes, listen. Follow the instructions here: [http://getswiftfox.com/](http://getswiftfox.com/)

Swiftfox is a bleeding-edge build of Firefox3, optimized for Linux systems. They have a repository so you can install it with Apt. There's really no good reason to use vanilla Firefox.

I thought it was discontinued?

---

### Post by sunexplodes on 2008-03-11
The discontinued work on the 2.0 branch and moved to 3.0.

---

### Post by Mazza558 on 2008-03-11
> **sunexplodes said:**
> The discontinued work on the 2.0 branch and moved to 3.0.

Ah, I see. I installed my version (deb) and when opening it, it just opens FF beta 4 instead.

---

### Post by Iehova on 2008-03-11
> **mrgnash said:**
> 
Seriously. Is nobody else experiencing this problem?

EDIT: I discovered that it seems to be a problem with loading svg icon themes:

```
(firefox-bin:8455): Gtk-WARNING **: Error loading theme icon 'gtk-undo-ltr' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so: wrong ELF class: ELFCLASS64

```

Hence, the error would appear when I was using either the default Hardy 'Human' icon theme, or 'Ultimate Gnome' -- both of which contain SVG icons. When I switched to a non-svg theme, the problem did not arise.

I get it on beta 4 using the Kamel icon theme with firefox installed to my home directory, but not with the human icons. I don't get the problem with beta 3 which is installed via synaptic (and thus presumably in /usr/bin/ or somewhere).

---

### Post by qazwsx on 2008-03-11
> **sunexplodes said:**
> Dudes, listen. Follow the instructions here: [http://getswiftfox.com/](http://getswiftfox.com/)

Swiftfox is a bleeding-edge build of Firefox3, optimized for Linux systems. They have a repository so you can install it with Apt. There's really no good reason to use vanilla Firefox.
It is  proprietary. Very good reason not to use it!!!
Also amd64 build is actually 32 bit. Looks like crab on 64 bit.

---

### Post by Xanatos Craven on 2008-03-11
> Also amd64 build is actually 32 bit. Looks like crab on 64 bit.
Are you using a theme engine that didn't come with Ubuntu? 32-bit programs look like crap here too (using murrine engine).

I hope this is backported to Gutsy. I remember for months Gutsy's Firefox 3 was still alpha while Hardy had a beta.

---

### Post by Sunflower1970 on 2008-03-11
Just installed Firefox 3 beta 4....Is anyone else having trouble with using their mouse button to make the browser go back a screen? It was working perfectly in beta 3 but now it won't work in beta 4...

---

### Post by Mazza558 on 2008-03-11
> **Sunflower1970 said:**
> Just installed Firefox 3 beta 4....Is anyone else having trouble with using their mouse button to make the browser go back a screen? It was working perfectly in beta 3 but now it won't work in beta 4...

You mean mouse gestures? If so, hardly any extensions are officially compatible with b4 yet (as it was only released today).

---

### Post by Sunflower1970 on 2008-03-11
> **Mazza558 said:**
> You mean mouse gestures? If so, hardly any extensions are officially compatible with b4 yet (as it was only released today).

No, not mouse gestures. It's where I hit the side button on my mouse and the screen goes back one, or I hit my other mouse side button and the screen goes forward one. All the time I've been using Minefield nightly builds I've had no problems whatsoever. Today, though after deciding to just use the beta 4 my two side mouse buttons don't work. This is the guide I used to originally get them to work: 

[http://ubuntuforums.org/showthread.php?t=178574&highlight=mouse+buttons+imwheel](http://ubuntuforums.org/showthread.php?t=178574&highlight=mouse+buttons+imwheel).

---

### Post by qazwsx on 2008-03-11
> **Xanatos Craven said:**
> Are you using a theme engine that didn't come with Ubuntu? 32-bit programs look like crap here too (using murrine engine).

I hope this is backported to Gutsy. I remember for months Gutsy's Firefox 3 was still alpha while Hardy had a beta.
Nope qtk-qt-engine. Finally decided to build it for my system to actually see it. Outcome didn't look so good at all with domino as qt theme :(.

Oh well Konqueror will be  my #1 browser.

---

### Post by adamup on 2008-03-11
> **Sunflower1970 said:**
> No, not mouse gestures. It's where I hit the side button on my mouse and the screen goes back one, or I hit my other mouse side button and the screen goes forward one. All the time I've been using Minefield nightly builds I've had no problems whatsoever. Today, though after deciding to just use the beta 4 my two side mouse buttons don't work. This is the guide I used to originally get them to work: 

[http://ubuntuforums.org/showthread.php?t=178574&highlight=mouse+buttons+imwheel](http://ubuntuforums.org/showthread.php?t=178574&highlight=mouse+buttons+imwheel).

Yeah, I had that problem as well. This link helped me solve it:

[https://bugzilla.mozilla.org/show_bug.cgi?id=420294](https://bugzilla.mozilla.org/show_bug.cgi?id=420294)

Firefox 3 apparently maps back/forward to mouse buttons 8 & 9 rather than 6 & 7 as in Firefox 2. You just need to modify your xorg.conf to reflect that change. Here's a snippet of mine to take a look at...

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"9"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping"	"1 2 3 6 7 8 9"
	Option		"Emulate3Buttons"	"no"
EndSection

Hope that helps :)

---

### Post by selda on 2008-03-11
What's up with text rendering in Firefox? Text in Epiphany looks much smoother.

---

### Post by Mad_Gouki on 2008-03-11
I found a fix in beta 4 that works for me (synaptics touchpad w/ scroll box between mouse buttons)
go to about:config and set
mousewheel.horizscroll.withnokey.action
to 2
2 is the forward backward functionality
1 is horizontal scroll
0 is disabled possibly
you might also need to change
mousewheel.horizscroll.withnokey.numlines
to -1
1 will reverse the normal scrolling, so if you want the forward key to go back and the back key to go forward, change it to that.
-1 is normal forward/back functionality, or it should be

---

### Post by Sunflower1970 on 2008-03-11
> **adamup said:**
> Yeah, I had that problem as well. This link helped me solve it:

[https://bugzilla.mozilla.org/show_bug.cgi?id=420294](https://bugzilla.mozilla.org/show_bug.cgi?id=420294)

Firefox 3 apparently maps back/forward to mouse buttons 8 & 9 rather than 6 & 7 as in Firefox 2. You just need to modify your xorg.conf to reflect that change. Here's a snippet of mine to take a look at...



Hope that helps :)

I'm afraid that's not working :( ...Do you have imwheel installed? Maybe that's my problem...

---

### Post by OrangeCrate on 2008-03-11
> **selda said:**
> What's up with text rendering in Firefox? Text in Epiphany looks much smoother.

It's a beta, give it time...

---

### Post by Sunflower1970 on 2008-03-11
> **Mad_Gouki said:**
> I found a fix in beta 4 that works for me (synaptics touchpad w/ scroll box between mouse buttons)
go to about:config and set
mousewheel.horizscroll.withnokey.action
to 2
2 is the forward backward functionality
1 is horizontal scroll
0 is disabled possibly
you might also need to change
mousewheel.horizscroll.withnokey.numlines
to -1
1 will reverse the normal scrolling, so if you want the forward key to go back and the back key to go forward, change it to that.
-1 is normal forward/back functionality, or it should be

That sort of works..but it's not working quite right. I can use one of my side buttons to go back and forth, but not one for forward or one for backwards.

---

### Post by Mad_Gouki on 2008-03-11
make sure the sysnumlines 1 is set to false
mousewheel.horizscroll.withnokey.action = 2
mousewheel.horizscroll.withnokey.numlines = -1
mousewheel.horizscroll.withnokey.sysnumlines = false
see if those 3 settings work.  this is on a synaptics touchpad tho, so your mileage may vary, but those are the only changes i made and now the forward/back buttons work.
you may still need to configure your buttons in xorg.conf.
also, the settings might be different for a mouse than they are for a touchpad, so mess around with it till you get something that works and let us know ;)

---

### Post by selda on 2008-03-11
> **OrangeCrate said:**
> It's a beta, give it time...
I don't think is beta issue. because text in Firefox 2 looks the same as in 3

---

### Post by Sunflower1970 on 2008-03-11
I think that works as long as I use no other version of FF. The moment I switch over to FF 2 the settings will work in it, but when I switch back to FF 3 Beta those settings go away...

Ah, well. I can live with it for the moment. :)

---

### Post by Sunflower1970 on 2008-03-11
I figured it out. (yay!) I'm using xbindkeys & xvkbd to be able to map the side buttons. Now I have back & forth not only in Firefox 3 & 2, I also have it in Nautilus. Which I didn't have before.

---

### Post by ZaphodNE on 2008-03-11
Please, someone, tell me how to get rid of FF 3.....what junk!!   Please, how do I get back to FF 2....PLEASE!!!

---

### Post by FrozenFox on 2008-03-11
> **ZaphodNE said:**
> Please, someone, tell me how to get rid of FF 3.....what junk!!   Please, how do I get back to FF 2....PLEASE!!!

I'm on Hardy, so forgive me if my instructions are not as simple as they could be in Gutsy, which your info suggests you are using..

Just open synaptic and uninstall firefox (firefox-3.0 on gutsy), find a gutsy .deb for firefox 2.0.0.12 (i found it on the gutsy repo page a ways back, its not  hard to find), and install that.

In most peoples' case, I think the desired file would be [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb)
If not (ie you're not something OTHER THAN i386 32 bit) you can look here
[http://security.ubuntu.com/ubuntu/pool/main/f/firefox/](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/)   and make sure you're getting the right one. 

That said, calm down. Why is it 'junk'? FF2 won't be updated forever (at that, much longer at all) so you might as well just update and fix your problems when you are back in a more level-headed state (if they are fixable. else, perhaps wait for the post-beta versions) or use a different browser (for security's sake). You also need to understand that it's still in beta.

---

### Post by Xbehave on 2008-03-11
swiftfox, is just Firefox compiled with -O3, i dont know much about compiler flags but from whats put on the gentoo wiki, compiling with -O3 is a bad idea as it is much more likely to introduce instability! thats why i just unpack the nightly FF build (means i can beta test, as any other build process may fix/make bugs).

FF3 rocks, the mouse changes suck, but then again i suppose they have a point, as they did with scrolling over icons to switch them.

FF3 is a good branch, i think that with mozilla the time is taken to make great .0s but competition forces .5s which are unstable and couse trouble (2.0 is a '.5')

---

### Post by kindofabuzz on 2008-03-11
mine work.  here's the mouse section of my xorg.conf:
```

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "Buttons" "7"
	Option "ZAxisMapping" "4 5"
EndSection

```

---

### Post by mister_k81 on 2008-03-12
> **Mazza558 said:**
> Ah, I see. I installed my version (deb) and when opening it, it just opens FF beta 4 instead.

I have the same problem. But instead of beta 4, it opens up FF 2.0.0.12 when I try to start up the latest beta build of swiftfox.

---

### Post by FrozenFox on 2008-03-12
You can't have swiftfox and firefox or whatnot -open- at the same time. Close one, wait a second, then open the other and it will open the right one. At least, that's how it worked for me. This way I can have both ff 2.0.0.12 and the latest firefox at the same time. 

However, this new beta solved all of my previous ff3 problems, so I don't see a need to go back to ff2 anytime soon. The only issues I had are now solved: **extention compatibility** (worked around by about:config in the location bar, adding extensions.checkCompatibility as binary to false), **hating the location bar** (solved by [https://addons.mozilla.org/en-US/firefox/addon/6227](https://addons.mozilla.org/en-US/firefox/addon/6227) installing this addon which restores similar to ff2 location bar functionality), and **adding a close button to all tabs** (solved [http://kb.mozillazine.org/Browser.tabs.closeButtons](http://kb.mozillazine.org/Browser.tabs.closeButtons) changing the browser.tabs.closeButtons entry in about:config again to 1 fixed this).

I did not have to reconfigure my mouse between firefox 2 and 3. I use imwheel and the right xorg.conf settings to translate the side buttons into key combinations that are fwd/back in all standard browsers. Both of my mice (microsoft intellimouse explorer 3.0a and logitech mx400) work fine with no changes.

---

### Post by mister_k81 on 2008-03-12
> **FrozenFox said:**
> You can't have swiftfox and firefox or whatnot -open- at the same time. Close one, wait a second, then open the other and it will open the right one. At least, that's how it worked for me. This way I can have both ff 2.0.0.12 and the latest firefox at the same time. 


Thanks! I got it working now.

---

### Post by mgkimsal on 2008-03-13
> **Kakihara said:**
> I am getting
```
Error: in guard: symbol required but got: Error: fatal: looped fatal error
```
when running ./firefox

and
```
./firefox-bin: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory
```
when running ./firefox-bin

libjemalloc.so is present in the same directory.
Ubuntu 7.10
anybody experienced this? any suggestion?

I've got the same problem on Mandriva 2008 - it's nothing specific to Ubuntu.  Also using 2.6.22.18 kernel.

Really annoying, because all the other betas have worked just fine.  


Michael Kimsal
[http://michaelkimsal.com/blog](http://michaelkimsal.com/blog)

---

### Post by mrpeenut24 on 2008-03-13
> **mgkimsal said:**
> I've got the same problem on Mandriva 2008 - it's nothing specific to Ubuntu.  Also using 2.6.22.18 kernel.

Really annoying, because all the other betas have worked just fine.  


Michael Kimsal
[http://michaelkimsal.com/blog](http://michaelkimsal.com/blog)

I've got the same problem on Ubuntu...  And google is turning nothing up.  When I try to run it in the local desktop directory, it says it, as well as if I put it in /usr/lib/firefox...  Have you found anything about it yet?


EDIT:
Actually, mine's not exactly the same.  Mine says: ```
Error: in (function call): procedure or syntax required but got: Error: fatal: looped fatal error
```.
Yet I *do* get the same error in firefox-bin.

---

### Post by ChrisNiemy on 2008-03-14
Hi,

those who got used to swiftfox you can switch to Swiftweasel. (not joking ;-)) It's not closed source and about performance even better than swiftfox. Downloads here: [http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)
Also includes .tar.gz for 64bit. :-) beta4 already there. .deb will come soon, I guess.

[url]http://swiftweasel.tuxfamily.org[/urll]

There's also a repository for different ubuntu versions:
[http://swiftweasel.tuxfamily.org/wiki/index.php5?title=Apt](http://swiftweasel.tuxfamily.org/wiki/index.php5?title=Apt)
For gutsy it's ```
deb http://download.tuxfamily.org/swiftweasel gutsy multiverse
```
There seems to be no APT-Key (so far), so you will get an unauthenticated warning in synaptic. Please note, the repository does not include firefox3 builds you have to download them manually.

---

### Post by Kakihara on 2008-03-18
> **mrpeenut24 said:**
> I've got the same problem on Ubuntu...  And google is turning nothing up.  When I try to run it in the local desktop directory, it says it, as well as if I put it in /usr/lib/firefox...  Have you found anything about it yet?


EDIT:
Actually, mine's not exactly the same.  Mine says: ```
Error: in (function call): procedure or syntax required but got: Error: fatal: looped fatal error
```.
Yet I *do* get the same error in firefox-bin.

Removing uim (japanese/chinese/... input) made the firefox 3b4 run. Upgrade to newer version of uim should also help, but it's not yet in gutsy repos...

---

### Post by mrpeenut24 on 2008-03-18
I had scim installed, but I believe I had removed it at that point.  It doesn't matter much (for me) now, as I've recently upgraded to Hardy, which has FF 3.0b4 in the repositories.

*For those wondering, Hardy works pretty well for me.  No problems as of yet.  I've also got Envy's nVidia driver enabled.

---

### Post by golem3 on 2008-03-18
Swiftweasel was a great tip. Thanks a bunch.application. According to Wikipedia, it's completely compatible with all FF extensions and themes, and it has AdBlock built in already.

---

### Post by Nycthbris on 2008-03-21
Has anybody else had problems with Swiftfox incorrectly rendering Gmail? After a Swiftfox update a few weeks ago the drop down menus on the left pane (Chat, Labels, etc.) do not show their content. For example the Chat menu will indicate it is expanded but there will be no names or anything listed under it. In FF2 or any other browser this never happens. I suspect it may have something to do with the scripting Gmail uses? I have the NoScript extension but google.com is allowed so this shouldn't be a factor.

Anybody else have this problem?

---

### Post by IHATEDLINK on 2008-05-30
The Mozilla folks are trying to make Firefox 3 the most downloaded software on a day, and **YOU** can help them! :D
Just go to the [Download Day 2008]("http://www.spreadfirefox.com/en-US/worldrecord")(which is the project's home page) and click the PLEDGE button. Total Pledges: 368,409 and counting... ( Friday the 30th May at 6:50 pm)

This was taking from the site:

[B]Set a Guinness World Record
Enjoy a Better Web

Sounds like a good deal, right? All you have to do is get Firefox 3 during Download Day to help set the record for most software downloads in 24 hours - it’s that easy. We're not asking you to swallow a sword or to balance 30 spoons on your face, although that would be kind of awesome.

By the way, the official date for the launch of Firefox 3 will be posted here soon - so check back! Join our community and this effort by pledging today.[/B]

Got questions? Check out the [FAQ]("http://www.spreadfirefox.com/en-US/worldrecord/faq") or reply to this thread.
[IMG]http://www.spreadfirefox.com/files/images/affiliates_banners/dday_badge_fox.png[/IMG]

---

### Post by cookieofdoom on 2008-05-30
381,209 people already. I wonder if servers will be able to keep up, lol.

---

### Post by nick09 on 2008-05-30
I'm gonna do that!:lolflag:

---

### Post by Sam Lars on 2008-05-30
Nice FAQ they have... is it a joke/they're working on it?
I still haven't found yet what the record is they have to break... or is it a new one?

Edit: I guess they're establishing a new record.
[http://www.informationweek.com/news/internet/browsers/showArticle.jhtml?articleID=208401028](http://www.informationweek.com/news/internet/browsers/showArticle.jhtml?articleID=208401028)

---

### Post by DrSRQ on 2008-05-31
> **cookieofdoom said:**
> 381,209 people already. I wonder if servers will be able to keep up, lol.

There will be multiple region specific servers for download...It's gonna be big. 


Support from India.

---

### Post by visionaire on 2008-05-31
sorry, i use opera :)

---

### Post by joshdudeha on 2008-05-31
Does it count if you download it via synaptic?

---

### Post by andrek on 2008-05-31
Poland's on second place, yay!

---

### Post by spidernik84 on 2008-06-01
As for the missing libraries errors, like:
```
 error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory
```

I solved copying all lib* files from the zip into usr/lib, issuing this command via terminal:

```
sudo cp firefox/lib*.so /usr/lib/

```

This has been tested on Firefox 3.0 rc1 on Ubuntu 7.10.

Hope this helps.

---

### Post by Joeb454 on 2008-06-01
I'd imagine this has been fixed now - Firefox RC1 is out, and beta 5 was included in Hardy by default

---

### Post by spidernik84 on 2008-06-01
> **Joeb454 said:**
> I'd imagine this has been fixed now - Firefox RC1 is out, and beta 5 was included in Hardy by default

Yeah, i just omitted some details: i had these errors testing FF 3.0rc1 on Ubuntu 7.10 aswell.
Gotta update the prev message :)

---

### Post by IHATEDLINK on 2008-06-01
> **joshdudeha said:**
> Does it count if you download it via synaptic?

NO, it has to be a FULL DOWNLOAD (NOT AN UPDATE!) and it has to be downloaded over Firefox's home page

---

### Post by Sam Lars on 2008-06-01
Technically if you download it from the repos (synaptic, apt-get, however), it's a full package (that's capable of updating an older installed package).
But, yes, it has to be from the Firefox site.  I'm sure they'll specify when we find out when it is.

---

### Post by Sam Lars on 2008-06-01
> **visionaire said:**
> sorry, i use opera :)

Download it anyway just to help?  You can just delete it... :)

---

### Post by BradwJensen on 2008-06-06
I wish they would make/host tested deb files for us to download..  And make their update service work on Linux machines.  It wouldn't be a bad thing if they just tested the code before letting it out for download / updates.

Downloading one of the packages they have now on Firefox's website; which won't install like doing it from synaptic is plain weird, even if it is just for a world record..

Am I the only one who feels this way?
I will download one of those files anyways, but still..

---

### Post by Sam Lars on 2008-06-06
Last time I checked I think the update worked on Linux, it's just that Ubuntu has disabled it in their version.  You have to update it via the repositories like any other program.
I agree that they should really host a deb, though.  A lot of other projects do that, and a project of their scale definitely should.  I guess they figure that most major OS's will provide it somehow.

---

### Post by ahawesome on 2008-06-09
Update on the number of pledges:

As of June 9, 2008 at about 4:30 PM EDT

[SIZE="7"]970,530[/SIZE]

people have pledged to download Firefox 3 on Download Day. The current total is at the Download Day website.

---

### Post by id1337x on 2008-06-09
Ya I already pledged to do this! I just worry about the date...

---

### Post by ahawesome on 2008-06-10
It looks like they could hit one million pledges today! Actually, it's gone from 970,000 to almost 1,000,000 in about 19 hours. That's about 30,000 people who are going to get Firefox.

---

### Post by bvanaerde on 2008-06-10
Is it normal that I just downloaded Firefox 3.0 through the repositories?
edit: oh nevermind, it's RC1 :)

---

### Post by irate vermin on 2008-06-10
I just upgraded firefox via the repos and it says its the final V3. today isnt the dl day right?

---

### Post by ahawesome on 2008-06-10
YES!!!!!!!! **_One million_** pledges (and a screenshot to prove it)! This happened at about 12:32 PM EDT on June 10. Download day is going to be huge.

---

### Post by ahawesome on 2008-06-10
> **irate vermin said:**
> I just upgraded firefox via the repos and it says its the final V3. today isnt the dl day right?

By the way, the same thing is going on here. It isn't download day yet. It still says Firefox 2 on the website. Can anyone explain this?

---

### Post by bvanaerde on 2008-06-10
In Synaptic it's saying RC1. So I suppose we've got Release Candidate 1 instead of the final version...

---

### Post by magnus0 on 2008-06-10
I don't like Firefox. I've hot 512M memory and it's such a memory hog. I use Epiphany instead, it's smaller and faster.

---

### Post by Nano Geek on 2008-06-10
> **magnus0 said:**
> I don't like Firefox. I've hot 512M memory and it's such a memory hog. I use Epiphany instead, it's smaller and faster.They've cleaned up a lot of the memory leeks and it runs much faster now. 

You might want to download it and give it a try. :)

Oh, and I've already pledged and I'm planning on downloading. (USA! USA! USA! :) )

---

### Post by andrewabc on 2008-06-11
Firefox 3 final has not been released. What you have is RC1.

RC3 will be released today on mozilla website.
[http://wiki.mozilla.org/Releases/Firefox_3.0rc3](http://wiki.mozilla.org/Releases/Firefox_3.0rc3)

---

### Post by elmer_42 on 2008-06-11
I just want to say that the United States of America is the only country in red. USA FTW!

---

### Post by ahawesome on 2008-06-11
> **andrewabc said:**
> RC3 will be released today on mozilla website

It still says RC2 [here]("http://www.mozilla.com/en-US/firefox/all-rc.html"). Where did you hear this?

---

### Post by andrewabc on 2008-06-11
> **ahawesome said:**
> It still says RC2 [here]("http://www.mozilla.com/en-US/firefox/all-rc.html"). Where did you hear this?

Did you go to my link?

Anyways, the link you provided now shows RC3.

---

### Post by bufsabre666 on 2008-06-12
[http://developer.mozilla.org/devnews/index.php/2008/06/11/coming-tuesday-june-17th-firefox-3/](http://developer.mozilla.org/devnews/index.php/2008/06/11/coming-tuesday-june-17th-firefox-3/)

we officially have a release date =)

---

### Post by ahawesome on 2008-06-12
Okay, I found the link to the download site. Also, I just got an e-mail. Mozilla is planning to release Firefox 3 on June 17 (this coming Tuesday). I guess this is when download day will be if everything goes well.

---

### Post by Wobedraggled on 2008-06-12
Wooohooo

---

### Post by reyfer on 2008-06-12
Oh man, they launch on my birthday!!!!

---

### Post by rudihawk on 2008-06-12
Yay! Now when is FF4 coming out?

*duck*

---

### Post by Swarms on 2008-06-12
Please all the upgrades that will be run, direct them throught their servers so it get added the record attempt. :)

---

### Post by Quillz on 2008-06-12
I think there was an RC3 release today, but it might have only been for Mac OS X users. Anyway, looking forward to the final release. Been using Firefox 3 full-time since Beta 5, and it's proven remarkably stable for me.

---

### Post by SunnyRabbiera on 2008-06-12
I will probably download it from mozilla to help the effort to get firefox its world record and all but I wont actually use it until my favorite add ons are available for it.

---

### Post by Robux the great on 2008-06-12
Firefox 3 has been great for me


I got a load of updates the other day. I assume that it was an upgrade
to release candidate.

I like Firefox 3. Beta 5 has been very stable for me.

Regards

Rob

---

### Post by iidestined on 2008-06-12
i saw the rc3 was released today. Anybody know how to install it?

---

### Post by SunnyRabbiera on 2008-06-12
> **iidestined said:**
> i saw the rc3 was released today. Anybody know how to install it?

eh right now there is no real easy way to get it, you are better off waiting.

---

### Post by bjschuma on 2008-06-12
> **reyfer said:**
> Oh man, they launch on my birthday!!!!

Mine too!

---

### Post by bruce89 on 2008-06-12
3.0 final is already in hardy-proposed by the way. I'm actually using XULRunner 1.9 final just now in fact.

---

### Post by xMoDx on 2008-06-13
so this mean loading FF in ubuntu hardy will be much faster than current? since FF2 loads faster......

---

### Post by kernelhaxor on 2008-06-13
thats awesome! can't wait!

---

### Post by renzokuken on 2008-06-13
> **reyfer said:**
> Oh man, they launch on my birthday!!!!

hey thats my birthday too....... i already got a dishwasher early for my brithday, now Firefox 3 !!!! how can it get any better...hehe

---

### Post by Maratonda on 2008-06-13
Sorry, I don't understand: why does the English site say that they release it on the 17th of June and here [ITALIAN] [http://www.spreadfirefox.com/it/worldrecord](http://www.spreadfirefox.com/it/worldrecord) they say (in Italian) that they will ANNOUNCE the RELEASE DATE on the 17th, which is different from releasing it. 
Any Italian around?
> La data ufficiale del rilascio di Firefox 3 verrà **annunciata** il 17 Giugno, 2008. Unitevi alla nostra comunità aderendo oggi stesso a questo tentativo di record.
In French it is the same as in English
> La date officielle du **lancement** de Firefox 3 est le 17 juin 2008.
I don't know much Spanish, but looks ok too...
> La fecha oficial de la publicación de Firefox 3 es el 17 de junio de 2008

---

### Post by the yawner on 2008-06-13
I haven't enabled my hardy proposed on my repo, but I got a Firefox 3 update which remove any traces naming it RC or anything. xulrunner's updated to 1.9. Is this it?

---

### Post by Polygon on 2008-06-13
the way rc releases work, is that if there are no further problems with it, literally the RC becomes final. So they dont put RC in the about box because if its all fine and good they just take that package and release it as final

---

### Post by akahige on 2008-06-13
> **iidestined said:**
> i saw the rc3 was released today. Anybody know how to install it?

The changes in RC3 are for Macs only. There's no difference between RC2 and RC3 for any other platform.

---

### Post by mahela007 on 2008-06-14
If you use firefox then you know that its a fantastic browser. I would just like to spread the word about download day. I dont intend this as an advertisement. I only want to tell everyone that firefox 3 will be available for download from june 17th onwards

---

### Post by ahawesome on 2008-06-14
I just got an e-mail confirming that Download Day will be [SIZE="5"]**June 17th**[/SIZE]. Be ready!

---

### Post by Mgiacchetti on 2008-06-14
[[IMG]http://www.spreadfirefox.com/files/images/affiliates_banners/468x60_ddayb_en.png[/IMG]]("http://www.spreadfirefox.com/node&id=0&t=272")
Release?
Tuesday, June 17, 2008

---

### Post by keiichidono on 2008-06-14
I am going to download it on download day but i won't be installing it. I'll wait for the repo's to update it for me. ;)

---

### Post by klange on 2008-06-14
hardy-proposed has RC3. Which looks like the final - it has no RC branding on it, and in fact the version in the repos doesn't even say it's an RC.

Of course, come download day I'll be getting it on my notebook and desktop just for the download to count, but I'll also be getting it on my family's two Windows machines and my laptop at work (which doesn't even run Firefox yet :( )

---

### Post by nilarimogard on 2008-06-14
[http://icehot.wordpress.com/2008/06/14/don%E2%80%99t-forget-to-be-part-of-firefox%E2%80%99s-download-day/]("http://icehot.wordpress.com/2008/06/14/don%E2%80%99t-forget-to-be-part-of-firefox%E2%80%99s-download-day/")

---

### Post by Robux the great on 2008-06-14
I am looking forward to the final release

Regards

Rob

---

### Post by Kalleo on 2008-06-14
I've already pledged and can't wait. Using the Release Candidates kinda spoils it though.

---

### Post by p_quarles on 2008-06-14
"Firefox download day" threads merged.

---

### Post by Ptero-4 on 2008-06-14
Supporting from Panamá.

---

### Post by GOROSSI on 2008-06-14
I Might even download the (im going to say a dirty world) :shock: mac  version to add to the count

---

### Post by aysiu on 2008-06-14
I don't think the record will mean anything (seeing as how any given Firefox user could download Firefox multiple times to bump up the number), but the publicity from it should be good for Firefox.

---

### Post by zmjjmz on 2008-06-14
I'm going to get my dad's IT department (made up of one woman) to install and download FF on all the computers that day.

---

### Post by Joeb454 on 2008-06-14
> **aysiu said:**
> I don't think the record will mean anything (seeing as how any given Firefox user could download Firefox multiple times to bump up the number), but the publicity from it should be good for Firefox.

They may do it by IP, and count 1 IP as 1 download, though I can totally see what you mean :confused:

---

### Post by sharks on 2008-06-14
Firefox 3 releases on june 17

[http://www.spreadfirefox.com/en-US/worldrecord/firefox3](http://www.spreadfirefox.com/en-US/worldrecord/firefox3)

[http://www.mozillazine.org/talkback.html?article=23871](http://www.mozillazine.org/talkback.html?article=23871)

---

### Post by kool_kat_os on 2008-06-14
i have the release candidate

---

### Post by mthei on 2008-06-14
I'll wait for it to enter the Fedora repos (still Beta 3, by the way - an RC was supposed to given this week, but it looks like they're waiting for the official release on Tuesday), but I installed Firefox on my parents' horribly out of date XP computer (so called "professional programmer" installed what was supposed to be a legitimate version of XP, although it will not update. I'm debating giving them Ubuntu or Mint or whatever), so I'll no doubt be downloading it for them anyway on Tuesday. I was surprised at how FF3 looks on Windows, though at least by default it blocks a lot of bad cookies, which I thought was something I'd have to myself.

---

### Post by Dark_Fire on 2008-06-15
Hey hey!

Just wanted to remind you all of the firefox download day! Also join the event on facebook! Let all your friends know! Lets make this one HUGE record!

Firefox is trying to see if they can set a record for the most sofware downloads in a single day! Will your name be in the book?

[Check it out!]("http://www.facebook.com/event.php?eid=16999458883")

---

### Post by robertchahine on 2008-06-15
i will attempt the event right now ;)

---

### Post by zmjjmz on 2008-06-15
This is the 4th thread on this?
I mean, it's good and all, but seriously.

---

### Post by id1337x on 2008-06-15
Ya I've seen this type of thread a lot, but you don't have to worry because there is only one more day before the download day comes along and then these topics will be gone. (Not that there a bad thing)

---

### Post by eeried on 2008-06-16
What's wrong with helping libre software like Firefox 3 set a record, I ask you.

Just because we Ubuntu users are spoilt doesn't mean we shouldn't make a gesture.

Mozilla was the software that introduced me to libre sofwtare and I never looked back. I want to say "thank you".

If you think that's silly then I'm afraid there's something wrong with you Linux user (I have neen a Linux user for about four years, no dual boot with M$).

In fact it would have decent of the forum admin to put up an annoucement for the D-Day. The Ubuntu communinty is quite large and international and we could add our weight.

Can we actually trust M$ users only to promote libre software?

Please note you don't have to install FF3, you're just invited to download it from Download central (you'll find web sites showing the D-Day logo, and click on it, surest thing to do).

Sorry to sound like spam -- I'm a SpreadFirefox affiliate, so I'm doing my duty, hey!

---

### Post by Dark_Fire on 2008-06-16
oops, This post went thru twice...

---

### Post by Dark_Fire on 2008-06-16
> **eeried said:**
> What's wrong with helping libre software like Firefox 3 set a record, I ask you.

Just because we Ubuntu users are spoilt doesn't mean we shouldn't make a gesture.

Mozilla was the software that introduced me to libre sofwtare and I never looked back. I want to say "thank you".

If you think that's silly then I'm afraid there's something wrong with you Linux user (I have neen a Linux user for about four years, no dual boot with M$).

In fact it would have decent of the forum admin to put up an annoucement for the D-Day. The Ubuntu communinty is quite large and international and we could add our weight.

Can we actually trust M$ users only to promote libre software?

Please note you don't have to install FF3, you're just invited to download it from Download central (you'll find web sites showing the D-Day logo, and click on it, surest thing to do).

Sorry to sound like spam -- I'm a SpreadFirefox affiliate, so I'm doing my duty, hey!

I must agree with you here. Firefox has done us nothing but good! Its been giving us allot of opportunity! Imagine where we would have been without it?

Most browsers strive to Firefox. So Opera, IE7, and any other might not have had tab browsing, extended security features, spell check, you name it. Firefox can also get through almost any proxy servers. At school we are restricted to internet access. Firefox gets through it as if I am the network admin...

Come on guys, we have ALLOT to be thankful for. Lets show Firefox how thankful we are! Just one download. YOU DONT EVIN NEED TO INSTALL IT! Just download it...

Lets make our mark in history!

---

### Post by ma_nkooo on 2008-06-16
I'm not going download it, because they posted wrong map of INDIA in their spreadfirefox website.

---

### Post by Kingsley on 2008-06-16
> **zmjjmz said:**
> This is the 4th thread on this?
I mean, it's good and all, but seriously.
Hey! The more threads floating around, the less likely I'll forget to download Firefox.

Thanks for the reminder. :guitar:

---

### Post by Dark_Fire on 2008-06-16
> **Kingsley said:**
> Hey! The more threads floating around, the less likely I'll forget to download Firefox.

Thanks for the reminder. :guitar:
Hehe, its a pleasure man!

You can always "Thanks" me for it... :P

I just think Firefox rox and that if only 18% of the market uses it that means that 82% have never had a "Firefox experience!" and that's just sad to say the least...

---

### Post by eeried on 2008-06-16
Comme on ma_nkooo, be a sport! 

What you can do instead of sulking is join SpreadFirefox and complain. 

Hey all, don't forget to pledge [http://www.spreadfirefox.com/en-US/worldrecord/](http://www.spreadfirefox.com/en-US/worldrecord/) -- though of course the pledge is less important than the actual donwload from the right place (fell free to read the Faq on the same page)

---

### Post by zgornel on 2008-06-16
All your Firefox 3 are belong to us !

---

### Post by Colonel Kilkenny on 2008-06-16
> **Dark_Fire said:**
> 
Most browsers strive to Firefox. So Opera, IE7, and any other might not have had tab browsing, extended security features, spell check, you name it.

Sorry for offtopic, I have to.
Internet Explorer got tabbed interface with shell called NetCaptor in 1997. Opera introduced MDI interface in 1994.
Firefox (or Mozilla) got it year 2001.

I'm not even going to start about other features...

[http://meyerweb.com/eric/browsers/timeline.html](http://meyerweb.com/eric/browsers/timeline.html)

And yes, it would be nice if the would be only one thread about one thing.

---

### Post by Fedz on 2008-06-16
I've been using the RC of FF3 for a few weeks but, tow the party line I've pledged and will download it anyway despite having it ;-)

Is it coincidence that they've decided to officially release FF3 on my birthday :lolflag:

---

### Post by nick09 on 2008-06-16
> **Fedz said:**
> I've been using the RC of FF3 for a few weeks but, tow the party line I've pledged and will download it anyway despite having it ;-)

Is it coincidence that they've decided to officially release FF3 on my birthday :lolflag:

Consider it a present.:lolflag:

---

### Post by mgol on 2008-06-16
Does anyone know at what hour is Fx3 intended to appear? :)
We now have June 17, so this is the day!

EDIT: Ahh, I guess we have to wait at least till US 0:00, which is Polish 6:00 am. This makes it more clear...

---

### Post by Raccoon1400 on 2008-06-16
[http://www.spreadfirefox.com/en-US/worldrecord/](http://www.spreadfirefox.com/en-US/worldrecord/)

Finally firefox 3 is ready to come out. Download it tomorrow to attempt to set a world record.

---

### Post by cardinals_fan on 2008-06-16
*yawns*

---

### Post by ahawesome on 2008-06-16
1,409,851 Pledges - Monday June 16th at 7:54 PM EDT

Let's just hope all these people are actually going to download FF3. I wonder if they will have some kind of 'download counter' so we know how big this is...

---

### Post by Redrazor39 on 2008-06-16
idk about you guys, but I'm thinking of going Bittorrent with this one. An HTTP download from all those people in such a short time would probably jam up something.

Firefox 3- June 17, 2008. USE BITTORRENT!!!

---

### Post by Lostincyberspace on 2008-06-16
> **Redrazor39 said:**
> idk about you guys, but I'm thinking of going Bittorrent with this one. An HTTP download from all those people in such a short time would probably jam up something.

Firefox 3- June 17, 2008. USE BITTORRENT!!!
NO then it doesn't count. Which is the whole reason for this.

---

### Post by tdrusk on 2008-06-16
I have a few computers to update tomorrow.

---

### Post by Vitamin-Carrot on 2008-06-16
But its the 17th today

---

### Post by Raccoon1400 on 2008-06-16
> **Vitamin-Carrot said:**
> But its the 17th today

Where you are. In Canada it is still the 16th.

---

### Post by nick09 on 2008-06-16
> **Raccoon1400 said:**
> Where you are. In Canada it is still the 16th.

Yeah in New York its the 16th.

---

### Post by the_darkside_986 on 2008-06-16
I'll be sure to do this for the Windows Vista machine at work. Manual download and installation of software in Ubuntu is something to avoid.

EDIT: oh wait, there's already a topic about this below.

---

### Post by quanumphaze on 2008-06-16
It's been June 17th for 11 hours now in Australia and the site still shows FF 2

What hour does it come out?

---

### Post by Depressed Man on 2008-06-16
> **Joeb454 said:**
> They may do it by IP, and count 1 IP as 1 download, though I can totally see what you mean :confused:

If that's the case I might as well download it on my desktop then take a USB flash drive and copy the .exe (installing it on Windows, on Ubuntu I'll just wait for it to hit the repos) over to my laptop. 

Was just going download it on both machines. But oh well :P

---

### Post by Raccoon1400 on 2008-06-16
> **the_darkside_986 said:**
> 
EDIT: oh wait, there's already a topic about this below.

Oops.

---

### Post by xebian on 2008-06-16
> **Raccoon1400 said:**
> [http://www.spreadfirefox.com/en-US/worldrecord/](http://www.spreadfirefox.com/en-US/worldrecord/)

Finally firefox 3 is ready to come out. Download it tomorrow to attempt to set a world record.

If they have 64-bit I will.

 Opera 9.5 has 64-bit version released just a couple of days ago.

---

### Post by sports fan Matt on 2008-06-16
Im in the minority I think..I may not even bother since im exploring and liking Opera...

---

### Post by xebian on 2008-06-16
But where is the 64-bit version?  If they have one then I'll download.

I think they are acting like arrogant Adobe (Flash) ignoring the 64-bit users out there.

Opera 9.5 was just released a few days ago and the 64-bit version is very nice.

---

### Post by cardinals_fan on 2008-06-16
> **sox fan Matt said:**
> Im in the minority I think..I may not even bother since im exploring and liking Opera...
+1

I don't care anymore...

---

### Post by Daedal Dementia on 2008-06-16
i prefer opera over FF. i only use FF to mess with opera or if opera decides to be gay when playing flash.

---

### Post by andrewabc on 2008-06-16
According to mozilla wiki it wont be out until 10:00 AM PST.

---

### Post by sports fan Matt on 2008-06-17
Im still trying to find a few things like a weather theme (forecast fox in ff) and a mail notifier

---

### Post by bvanaerde on 2008-06-17
> **ahawesome said:**
> 1,409,851 Pledges - Monday June 16th at 7:54 PM EDT
Looks a bit disappointing to me, as they were aiming at 5 milion, if I recall correctly.

But of course there'll be a lot more actual downloaders, as not everybody will do the plegde-thingie :)

---

### Post by bikeboy on 2008-06-17
Dare I mention that final builds can now be downloaded - please find a mirror rather than hammering the main ftp server, it will make Mozilla unhappy if we all go there (hence I'm not mentioning the address here).

Note: Downloading now will not count towards the download day for those who care about that.

Linux x86_64 tar.bz is coming, not ready yet.

Update: [http://www.mozilla.org/mirrors.html](http://www.mozilla.org/mirrors.html) <--- not all mirrors will be up to date yet but that should help.

---

### Post by bvanaerde on 2008-06-17
hmm... I think they want us to wait :)

---

### Post by bomanizer on 2008-06-17
> **andrewabc said:**
> According to mozilla wiki it wont be out until 10:00 AM PST.

That will be 20:00 over here :) (GMT +2)

---

### Post by eeried on 2008-06-17
nick09 Happy Birthday with Firefox 3!

mgol: Download Day starts at 5pm UTC so you should be able to work out what time it is in Poland (cheers to Poles in Poland the leading European pledgers so far, and France rather close behind now!)

---

### Post by GavinZac on 2008-06-17
> **ma_nkooo said:**
> I'm not going download it, because they posted wrong map of INDIA in their spreadfirefox website.

What's wrong about it?

---

### Post by quanumphaze on 2008-06-17
Do they count only if I do a full download?

If for example it fails or I have to stop it for some reason will it still count?

---

### Post by -gabe-noob- on 2008-06-17
Plegeded

---

### Post by billgoldberg on 2008-06-17
Am I the only one that can't seem to get to one of mozilla's firefox' website?

None of them load.

---

### Post by geoken on 2008-06-17
I'll be doing at least 8 downloads today, 4 at work and 4 at home. If while walking through my workplace I notice any unattended computers that number will get bumped up while I hijack that machine to download FF.

I also haven't pledged, so those pledge numbers can be taken with a grain of salt.

---

### Post by eragon100 on 2008-06-17
I pledged, I am going to download it twice :)

---

### Post by billgoldberg on 2008-06-17
The main page still want me to download firefox 2.

It's already 14.35h, they can't wait much longer or they won't get any from Europe. As I think most people will download on the job.

---

### Post by bufsabre666 on 2008-06-17
> **billgoldberg said:**
> The main page still want me to download firefox 2.

It's already 14.35h, they can't wait much longer or they won't get any from Europe. As I think most people will download on the job.

10am pacific standard time, just wait 4.5 hours left

---

### Post by quanumphaze on 2008-06-17
I guess it will have to be tomorrow for me. It's 10:42p and I have an exam tomorrow.

I only have a 2 hour window of opportunity tomorrow before I pack up.

---

### Post by billgoldberg on 2008-06-17
> **bufsabre666 said:**
> 10am pacific standard time, just wait 4.5 hours left

They bringing it out on June 17, at 19.00h for Europe?

It seems they care more about there American user base, well I won't be downloading it then.

I'll just wait for it to hit the Ubuntu repo's.

---

### Post by Occasionally Correct on 2008-06-17
> **billgoldberg said:**
> They bringing it out on June 17, at 19.00h for Europe?

It seems they care more about there American user base, well I won't be downloading it then
That's just a little on the silly side. If they wanted to cater to Americans, they could have released it by now so we'd have the entire day to download it. As it stands, Europeans aren't the only ones waiting four~ more hours.

:p

---

### Post by bufsabre666 on 2008-06-17
> **billgoldberg said:**
> They bringing it out on June 17, at 19.00h for Europe?

It seems they care more about there American user base, well I won't be downloading it then.

I'll just wait for it to hit the Ubuntu repo's.

i dont know if you noticed, but an overwelming majority of pledgers are american, and by overwelming, i mean they more than doubled poland who was in second, besides mozilla servers are in mountain view california

---

### Post by FuturePilot on 2008-06-17
So I take it it's not available yet? Because I can't find a download anywhere. :confused:

---

### Post by GStubbs43 on 2008-06-17
Download Day starts on June 17th at 10 a.m. PDT.  Check this out for local times: 

[http://www.timeanddate.com/worldclock/fixedtime.html?month=6&day=17&year=2008&hour=10&min=0&sec=0&p1=224&sort=1](http://www.timeanddate.com/worldclock/fixedtime.html?month=6&day=17&year=2008&hour=10&min=0&sec=0&p1=224&sort=1)


Countdown:

[http://www.timeanddate.com/counters/customcounter.html?month=6&day=17&year=2008&hour=10&min=00&sec=00&p0=224](http://www.timeanddate.com/counters/customcounter.html?month=6&day=17&year=2008&hour=10&min=00&sec=00&p0=224)

---

### Post by FuturePilot on 2008-06-17
Oh. There's 3 hours left. I see :)

---

### Post by rune0077 on 2008-06-17
What's all this obsession with world records? I'd assume a product is good because of it's quality not because it got mentioned in a book somewhere. Just to show my defiance, I hereby pledge to wait until Download Day is over, before downloading it (yes, I'm just annoying that way).

---

### Post by legolas_w on 2008-06-17
Hi
Thank you for reading my post
I heard that FireFox 3 is going to be out in a few hours. I am wondering whether a deb package will be available for Ubuntu in the same day or not.
I saw in the news that FF folk want to register a record for the biggest amount of download in 24 hours.

The other question is, does FF 3 remove my current FF configuration or it will use them (I have FF 2)? 


Thanks

---

### Post by Exsecrabilus on 2008-06-17
If it reaches the repos today, I guess you could say it might be available on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Nepherte on 2008-06-17
I highly doubt it. If you want to contribute to the number of downloads, you can of course download the linux binaries and use those.

Relating the compatibility issue, Firefox 3 uses the same .mozilla folder as Firefox 2. Just backup your .mozilla directory in case you want to use Firefox 2 later on and remove the .mozilla directory. Firefox 3 will create a new entry the first time you start it:
```
mv ~/.mozilla ~/.mozilla_backup
rm -r ~/.mozilla
```

---

### Post by K.Mandla on 2008-06-17
Similar threads merged.

---

### Post by FuturePilot on 2008-06-17
> **legolas_w said:**
> Hi
Thank you for reading my post
I heard that FireFox 3 is going to be out in a few hours. I am wondering whether a deb package will be available for Ubuntu in the same day or not.
I saw in the news that FF folk want to register a record for the biggest amount of download in 24 hours.

The other question is, does FF 3 remove my current FF configuration or it will use them (I have FF 2)? 


Thanks

That's the plan. They've been doing extensive testing with the packages in Proposed so if everything goes well we may see an update on the same day.

---

### Post by Mr. Picklesworth on 2008-06-17
It will happen, but I bet it won't happen in 24 hours because Firefox 3 + extensive Ubuntu-specific patches must be tested for regressions. Mid-release, even the slightest regression is a bad thing.

---

### Post by MaximB on 2008-06-17
Why do we really need a .deb ?
It works great just from it's folder , similar to Blender.
Blender versions come out more often then Ubuntu packages.
I rather just unzip and use it.

---

### Post by Negadrive on 2008-06-17
> **bufsabre666 said:**
> an overwelming majority of pledgers are american, and by overwelming, i mean they more than doubled poland who was in second, besides mozilla servers are in mountain view california
I'm not sure about this: billgoldberg said «Europe», not «Poland». If you check the whole Europe, the sum is roughly 2X larger than the whole North America and even if you include South America, you still don't get any overwelming majority. But you are right about where Mozilla is, and also I agree with Occasionally Correct.

---

### Post by jrusso2 on 2008-06-17
Some way to try to set a record I can't even find the download link.  All I can find is the Release Candidate.

---

### Post by andrewabc on 2008-06-17
> **jrusso2 said:**
> Some way to try to set a record I can't even find the download link.  All I can find is the Release Candidate.

IT WILL BE RELEASED 10AM PST.

/waiting for 100 other users to complain about the same thing without reading the thread.

---

### Post by reyfer on 2008-06-17
> **andrewabc said:**
> IT WILL BE RELEASED 10AM PST.

/waiting for 100 other users to complain about the same thing without reading the thread.

And you're surprised? The vast majority of people don't read threads, they read the title and the last post.

On topic...waiting patiently for the GO!!!!

---

### Post by elmer_42 on 2008-06-17
I just went to the website to download it and was like, "Where is it?" Then I decided to check here. Now I have to wait 2 whole hours. I'm going to get the Linux binary from their site, but do you know when the repos will have it?

---

### Post by smartboyathome on 2008-06-17
I am waiting also, but am glad it is released on a time easily remembered for me because I live in PDT. :p

---

### Post by CH1C0 on 2008-06-17
i hope its good with java because i cant even play yahoo games with this firefox even though java is installed and enabled. anyway, because of that, opera has become my friend.

---

### Post by geoken on 2008-06-17
Wouldn't a .deb hosted by ubuntu fail to effect the total download count (which would negate the desire to have the .deb released today)?

---

### Post by dr.koljan on 2008-06-17
[http://packages.ubuntu.com/intrepid/firefox-3.0](http://packages.ubuntu.com/intrepid/firefox-3.0)

Look at the version. Could it be Firefox 3 has been already released for Ubuntu testers? :)

---

### Post by shearn89 on 2008-06-17
its possible - given that its the default browser for ubuntu, its likely that mozilla have some sort of agreement, and have allowed the ubuntu team to start work on the ubuntu-specific patches ahead of release date! only an hour and 5 to go though... Plus, i get to download twice for both windoze and linux... woot!

---

### Post by hjs1118 on 2008-06-17
Is there any differences between firefox3s which I updated from Ubuntu repositories and plan to download from 'firefox3' download page? Is it rc2 or rc3?

---

### Post by castrojo on 2008-06-17
Good reading material on the subject:

[http://snurl.com/2jcpf](http://snurl.com/2jcpf)

---

### Post by Depressed Man on 2008-06-17
> **geoken said:**
> Wouldn't a .deb hosted by ubuntu fail to effect the total download count (which would negate the desire to have the .deb released today)?

Probably. I think they're only counting downloads from the Mozilla site. While if we did get a deb, it would come from Ubuntu's servers.

---

### Post by Exsecrabilus on 2008-06-17
> **shearn89 said:**
> only an hour and 5 to go though...
There's a specific time for the release? O.o

---

### Post by bobbocanfly on 2008-06-17
Definately:

[QUOTE="17:36 BST"]<asac> pitti: ok i am off now for 1h ... if you are around, please push xulrunner-1.9 and firefox-3.0 at 19:00 our time (or slightly in advance). thanks
<asac> (to -updates)[/QUOTE]

(for those who dont know asac is the leader of the mozilla team)

---

### Post by melrom on 2008-06-17
I keep refreshing the mozilla page, and it goes down like every other refresh. lol.

---

### Post by Exsecrabilus on 2008-06-17
> **bobbocanfly said:**
> Definately:



(for those who dont know asac is the leader of the mozilla team)
So about an hour more then? WOOT!

---

### Post by cookieofdoom on 2008-06-17
> **melrom said:**
> I keep refreshing the mozilla page, and it goes down like every other refresh. lol.

You're breaking the site! Stop it! AHHH!!!
lol

---

### Post by melrom on 2008-06-17
> **cookieofdoom said:**
> You're breaking the site! Stop it! AHHH!!!
lol

it broke of its own volition at 1 PM EST exactly. lol.

---

### Post by Kosimo on 2008-06-17
Firefox website is down!!!!!!    

I hope they are prepared to support a 10000000 millions downloads in less than 24 hours...

---

### Post by Sinkingships7 on 2008-06-17
I'm having no luck connecting to their site as well. I hope the fix it soon...

---

### Post by Gourgi on 2008-06-17
website down ??
:(

---

### Post by cookieofdoom on 2008-06-17
Did I mention I knew this was coming? lol

---

### Post by FuturePilot on 2008-06-17
It's probably down because there was a huge massive download rush :lolflag:

---

### Post by Sim777 on 2008-06-17
This reminds of famous event called "Night of the refreshing monkeys"

---

### Post by Kosimo on 2008-06-17
> **FuturePilot said:**
> It's probably down because there was a huge massive download rush :lolflag:

If this is the problem I have to say: Bad for Mozilla!! They should have been prepared!

---

### Post by beniwtv on 2008-06-17
rofl... I was also expecting the website to be down sooner or later....

I just hope they fix it somehow... so that we can actually download. :lolflag:

---

### Post by FuturePilot on 2008-06-17
Or maybe they're just updating the site.

---

### Post by Sunflower1970 on 2008-06-17
Bummer...Was hoping to at least get to the homepage... :(

---

### Post by Sinkingships7 on 2008-06-17
I finally connected to it. I guess Firefox 3 isn't quite ready yet. I read somewhere that there's a set time, and that there's about 45 minutes left (2:00 P.M. EST?)

---

### Post by zgornel on 2008-06-17
Well, don't go on the main page, everyone goes there. Here would be more appropiate : [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/) . Happy downloadin' !

---

### Post by Sim777 on 2008-06-17
> **zgornel said:**
> Well, don't go on the main page, everyone goes there. Here would be more appropiate : [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/) . Happy downloadin' !
> 
We're not quite ready yet!

We're just as excited as you are for our upcoming release, but we're still putting the finishing touches on Firefox 3: preparing the new mozilla.com website, getting our severs ready for downloads, and doing our final pre-launch checks. You can follow our progress if you'd like! 

not quite...

---

### Post by beniwtv on 2008-06-17
OMG! The link to firefox 2 just disappeared for me :/. I think we are near guys! :popcorn:

EDIT: It just came back...

---

### Post by frmneo999 on 2008-06-17
> **zgornel said:**
> Well, don't go on the main page, everyone goes there. Here would be more appropiate : [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/) . Happy downloadin' !

Its hash check matched RC3 :(

---

### Post by bufsabre666 on 2008-06-17
10am pdt is 1pm edt, so where is my red panda? i mean firefox

---

### Post by BreakDecks on 2008-06-17
I just got an e-mail from spreadfirefox:

> 
Are you ready to make history? Are you ready to set a World Record? Today is Download Day. To become part of the official Guinness World Record you must [download Firefox 3]("http://www.mozilla.com/en-US/firefox/?p=downloadday") by 17:00 UTC on June 18, 2008, or roughly 24 hours from now.


---

### Post by sports fan Matt on 2008-06-17
20 mins to go for the ff fanboys

---

### Post by rudihawk on 2008-06-17
Everything mozilla related is going haywire. Links time out, FF extensions wont download. Pages just stop. Its driving me nuts! I cant wait!

---

### Post by Mazza558 on 2008-06-17
Well, that's the end of that record...

If they don't get their servers up within about an hour from now, a lot of people will just give up -> bad record.

---

### Post by Eisenwinter on 2008-06-17
The Mozilla website is accessible, but a Firefox 3 download link is nowhere to be seen.

---

### Post by Delever on 2008-06-17
Another case of overbuilt hype?

---

### Post by YAOMTC on 2008-06-17
Dang it... I should have known this would happen.

---

### Post by Mr. Picklesworth on 2008-06-17
I expected that well ahead of time. People have a nasty habit of finding the files before the displayed site links to them (eg: before it is ready), then post said links on forums, which effectively breaks the purpose of download mirrors and the like by putting all the load on the central server...
It would be nice if people didn't do that ;)

---

### Post by rulsky on 2008-06-17
Well as far as I know the record they were trying to break is the most downloads in 24 hours. my guessing is that it starts from the moment the servers are up to start the massive party.

Don't worry Mozilla, I can just sit here and wait as long as you want.......:popcorn:

---

### Post by Wobedraggled on 2008-06-17
I wouldn't doubt them getting hit by a ddos from some rabid FF haters.

---

### Post by Sunflower1970 on 2008-06-17
> **zgornel said:**
> Well, don't go on the main page, everyone goes there. Here would be more appropiate : [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/) . Happy downloadin' !

Ahhh. Thanks for that. D/L the Windows version for work, and the Linux files to install later on on my laptop. :)

---

### Post by Exsecrabilus on 2008-06-17
[http://www.mozilla.com/en-US/](http://www.mozilla.com/en-US/)

Only the main page is available, though. IDK why.....

---

### Post by rudihawk on 2008-06-17
Thats for FF2...

---

### Post by bomanizer on 2008-06-17
...waitasec..

---

### Post by Delever on 2008-06-17
What out? :P

---

### Post by reyfer on 2008-06-17
It says 3 is out, but the download link still says version 2.0.0.14 for linux

---

### Post by schnauzer93 on 2008-06-17
Thar she blows! 

...but the link still points to FF2...

---

### Post by Exsecrabilus on 2008-06-17
> **Delever said:**
> What out? :P
LOLZ. I'm so happy. Kinda weird it doesn't have the download for v3.0 up.....

---

### Post by magnus0 on 2008-06-17
It's like 1 hour and 25 minutes past 10 and still not ready.

---

### Post by crakkajakka15 on 2008-06-17
i wonder why the download for 3 isnt up also?

---

### Post by Delever on 2008-06-17
Oh yeah, I just got delayed :D

EDIT: Hey! Come on, give me version 3!...

---

### Post by Exsecrabilus on 2008-06-17
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/)

Maybe that works.....?

---

### Post by bomanizer on 2008-06-17
It's getting there.. a moment ago I got nothing on that link.

---

### Post by cardinals_fan on 2008-06-17
Their site's totally screwed up...

---

### Post by Exsecrabilus on 2008-06-17
WHAT! The main page is back to the original boring Firefox 2 ad. :(

---

### Post by kernelhaxor on 2008-06-17
I think the server got hosed by the amount of traffic .. Even the main home page doesn't show up for me, I got a blank page once, when refreshed, it says 'Repair in progress'

---

### Post by billgoldberg on 2008-06-17
> **magnus0 said:**
> It's like 1 hour and 25 minutes past 10 and still not ready.

It's already available here:

[http://www.mozilla-europe.org/en/firefox/](http://www.mozilla-europe.org/en/firefox/)

But I won't be downloading it.

---

### Post by Delever on 2008-06-17
> **Exsecrabilus said:**
> [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/)

Maybe that works.....?

I want to do it the "tru" way.

---

### Post by Exsecrabilus on 2008-06-17
The site's back to its previous state. :(

---

### Post by Exsecrabilus on 2008-06-17
> **Delever said:**
> I want to do it the "tru" way.
LOLZ winnah quote.

---

### Post by kernelhaxor on 2008-06-17
They really shud hav taken into account ppl living in other parts of the world .. its already 18th in so many places . a lotta ppl r pissed tht they still haven't been able to download ..

---

### Post by Kosimo on 2008-06-17
guys guys guys!   

Have a look what mozilla says about the server's saturation

[http://blog.mozilla.com/blog/2008/06/17/firefox-3-coming-soon/](http://blog.mozilla.com/blog/2008/06/17/firefox-3-coming-soon/)


Don't download Firefox yet, as it won't count for the record 'till they can fix all servers

---

### Post by Le-Froid on 2008-06-17
Its released on the home page! :)

edit: ...or, their site is messed up :S

---

### Post by Delever on 2008-06-17
> **kernelhaxor said:**
> They really shud hav taken into account ppl living in other parts of the world .. its already 18th in so many places . a lotta ppl r pissed tht they still haven't been able to download ..

Well, it's 24 hours anyway, so we (ppl living in other parts of the world) have all night for page and other refreshes, plus long morning to catch up.

---

### Post by robertchahine on 2008-06-17
> **billgoldberg said:**
> It's already available here:

[http://www.mozilla-europe.org/en/firefox/](http://www.mozilla-europe.org/en/firefox/)

But I won't be downloading it.
yep the link works great

---

### Post by mrgnash on 2008-06-17
From the Mozilla blog:

> The outpouring of interest and enthusiasm around Firefox 3 has been overwhelming (literally!).  Our servers are currently feeling the burn and should be back to normal shortly.  Download day will officially commence once the site goes live.  The 24 hours period will be clocked from that moment.  Thanks for your continued support.

---

### Post by -grubby on 2008-06-17
Well, if Mozilla wanted to make a record for the most downloads, they should have at least had their servers ready for this. I see this as a failure on their part

---

### Post by Delever on 2008-06-17
> **cardinals_fan said:**
> Their site's totally screwed up...

Balloons and all, and you ain't happy? :D

---

### Post by andrek on 2008-06-17
Go there - [http://www.spreadfirefox.com/en/worldrecord](http://www.spreadfirefox.com/en/worldrecord) - there's a new world map showing the download count by country, also there's a download link !

---

### Post by cardinals_fan on 2008-06-17
> **Exsecrabilus said:**
> WHAT! The main page is back to the original boring Firefox 2 ad. :(
The UFO art is psychedelic...

---

### Post by Sinkingships7 on 2008-06-17
> **cardinals_fan said:**
> Their site's totally screwed up...

That's not messed up: it's their new download site!

---

### Post by Sunflower1970 on 2008-06-17
> **Kosimo said:**
> guys guys guys!   

Have a look what mozilla says about the server's saturation

[http://blog.mozilla.com/blog/2008/06/17/firefox-3-coming-soon/](http://blog.mozilla.com/blog/2008/06/17/firefox-3-coming-soon/)


Don't download Firefox yet, as it won't count for the record 'till they can fix all servers

Gahh!...

oh well.... I'll just download a copy from home then later today...

---

### Post by Le-Froid on 2008-06-17
Main site seemed to fix bug, downloading it from their *real* site right now

---

### Post by Exsecrabilus on 2008-06-17
[http://www.mozilla.com/](http://www.mozilla.com/)

When you do that, it takes you to the Firefox 3 RC 3 download center, with Firefox 2 downloads listed. So screwed up.....

Think about how much votes they could have gotten if they started at the same time as the other countries' sites.

---

### Post by bomanizer on 2008-06-17
[http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0&os=linux&lang=en-US]("http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0&os=linux&lang=en-US")

That's it, I'm off to bed :D

---

### Post by Mazza558 on 2008-06-17
[http://www.mozilla.com/en-US/]("http://www.mozilla.com/en-US/")

This works and shows the new firefox 3, but download link doesn't work.

---

### Post by Sinkingships7 on 2008-06-17
That blog has been fixed. It doesn't say that anymore. It says that when the site launches, they're ready.

Their site launched.

I'm downloading as we speak.

EDIT: The Mozilla front page is up and running, as is the Firefox (all) page.

EDIT2: My download just finished.

---

### Post by Redrazor39 on 2008-06-17
wth is going on!

Man, I wish they could count downloads via bittorrent. I would totally do that.

---

### Post by Exsecrabilus on 2008-06-17
How does the record counting actually work?

If you just download it, does Mozilla record it?
Or does it get recorded when you run the installer?

---

### Post by Jay_Bee on 2008-06-17
I got the download to start on Windows, but the dl speed is 3.3kb/sec... They should have prepared better.

---

### Post by Le-Froid on 2008-06-17
downloaded what they said was 3.0, but was RC 3

---

### Post by cardinals_fan on 2008-06-17
> **Delever said:**
> Balloons and all, and you ain't happy? :D

> **Sinkingships7 said:**
> That's not messed up: it's their new download site!
*sigh*

If you looked before (the server just went down again) their FF3 download box actually downloads version 2.  And the balloons are CRAZY!

---

### Post by Exsecrabilus on 2008-06-17
This blows.

---

### Post by Mazza558 on 2008-06-17
> **Exsecrabilus said:**
> How does the record counting actually work?

If you just download it, does Mozilla record it?
Or does it get recorded when you run the installer?

Just when you download it.

---

### Post by Exsecrabilus on 2008-06-17
Don't Do Anything, The 24-hour Count Hasn't Started Yet.

What You Download Now Won't Count For The Record.

Wait A Few Moments And Keep Reading The Mozilla Blog.

---

### Post by Mazza558 on 2008-06-17
> **Exsecrabilus said:**
> Don't Do Anything, The 24-hour Count Hasn't Started Yet.

What You Download Now Won't Count For The Record.

Wait A Few Moments And Keep Reading The Mozilla Blog.

It should have started nearly 2 hours ago now - any downloads since that time should have counted.

EDIT: Just looked at the mozilla blog. I see what you mean.

---

### Post by Sinkingships7 on 2008-06-17
> **cardinals_fan said:**
> *sigh*

If you looked before (the server just went down again) their FF3 download box actually downloads version 2.  And the balloons are CRAZY!

It did. Then I refreshed and FF3 was up. Go check again. Just keep refreshing if you get page load errors.

---

### Post by Sunflower1970 on 2008-06-17
> **Sinkingships7 said:**
> That blog has been fixed. It doesn't say that anymore. It says that when the site launches, they're ready.

Their site launched.

I'm downloading as we speak.

EDIT: The Mozilla front page is up and running, as is the Firefox (all) page.

EDIT2: My download just finished.

...It's hard to keep up with all the changes...

---

### Post by Eclipse. on 2008-06-17
Heres the horribley simple way for anyone who cant access the site:

Linux - [http://releases.mozilla.org/pub/mozi...ox-3.0.tar.bz2]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-GB/firefox-3.0.tar.bz2")

Windows - [http://releases.mozilla.org/pub/mozi...etup%203.0.exe]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/win32/en-GB/Firefox%20Setup%203.0.exe")

OSX - [http://releases.mozilla.org/pub/mozi...efox%203.0.dmg]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/mac/en-GB/Firefox%203.0.dmg")

Source - [http://releases.mozilla.org/pub/mozi...source.tar.bz2]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/source/firefox-3.0-source.tar.bz2")

---

### Post by MemoryDump on 2008-06-17
just go here:
[http://download.mozilla.org/?product=firefox-3.0&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-3.0&os=linux&lang=en-US)
(for the English/US)

---

### Post by dodghz on 2008-06-17
All seems well here in the UK. We've got spaceships on the download page (no balloons). Seemed to download 3.0 from the Japanese mirror.

---

### Post by Exsecrabilus on 2008-06-17
Don't Do Anything, The 24-hour Count Hasn't Started Yet.

What You Download Now Won't Count For The Record.

Wait A Few Moments And Keep Reading The Mozilla Blog.

---

### Post by Delever on 2008-06-17
Spaceships in UK. Just what i feared.

---

### Post by Christmas on 2008-06-17
I was determined to download it but the servers are down. After so much fuss around how we should all download it to break the record, they didn't even prepare themselves for the event like we did.

The heck with it, go Opera and Konqueror, I'm not downloading anything.

---

### Post by Sinkingships7 on 2008-06-17
Some screenshots of what I just witnessed:

---

### Post by Mazza558 on 2008-06-17
Server works fine for me now - as fast as normal, though download's a bit slow.

---

### Post by Exsecrabilus on 2008-06-17
> **Christmas said:**
> I was determined to download it but the servers are down. After so much fuss around how we should all download it to break the record, they didn't even prepare themselves for the event like we did.

The heck with it, go Opera and Konqueror, I'm not downloading anything.
Yeah, that's the attitude that landed man on Neptune!

---

### Post by AOZ on 2008-06-17
> **FuturePilot said:**
> Or maybe they're just updating the site.

They picked a pretty good time to do it...

---

### Post by BreakDecks on 2008-06-17
> **Exsecrabilus said:**
> Don't Do Anything, The 24-hour Count Hasn't Started Yet.

What You Download Now Won't Count For The Record.

Wait A Few Moments And Keep Reading The Mozilla Blog.

> **Mazza558 said:**
> Just looked at the mozilla blog. I see what you mean.

What?  I just downloaded it and installed it and it is showing up as the official (Win32) version of Firefox 3.

I can tell it isn't RC3 because I was having a login error on this site with RC3, forcing me to go back to FF2.  That login error is now gone.

---

### Post by Mazza558 on 2008-06-17
Well, looks like download day started just a few minutes ago instead, as the blog says it wouldn'y start until the new website's up.

---

### Post by smartboyathome on 2008-06-17
> **Exsecrabilus said:**
> Don't Do Anything, The 24-hour Count Hasn't Started Yet.

What You Download Now Won't Count For The Record.

Wait A Few Moments And Keep Reading The Mozilla Blog.

I think it has, as spreadfirefox.com is down. :(

---

### Post by GavinZac on 2008-06-17
Linux download worked for me, downloading on Windows now.

---

### Post by Redrazor39 on 2008-06-17
I have an idea: let's all download firefox 3 twice.. or three times, or 5 times! That way, mozilla gets many more downloads, and we can just delete the file later.

Let's do it! I know I will!

---

### Post by Redrazor39 on 2008-06-17
btw you can download firefox 3 now

---

### Post by irshadcharm on 2008-06-17
how do you install?

---

### Post by Mateo on 2008-06-17
Firefox came preinstalled for me, no need to install.  Besides, I primarily use Epiphany anyways.  Are there even any major differences between this and the "alpha" version included in Hardy?

---

### Post by Exsecrabilus on 2008-06-17
> **BreakDecks said:**
> What?  I just downloaded it and installed it and it is showing up as the official (Win32) version of Firefox 3.

I can tell it isn't RC3 because I was having a login error on this site with RC3, forcing me to go back to FF2.  That login error is now gone.
I never said it was going to be the RC 3 if you downloaded it.

I just said it wouldn't count for the world record.

But I guess it started, since the site's back up now! :D

---

### Post by cardinals_fan on 2008-06-17
> **Exsecrabilus said:**
> Yeah, that's the attitude that landed man on Neptune!
Uh, did I miss something?

---

### Post by Exsecrabilus on 2008-06-17
> **irshadcharm said:**
> how do you install?
I think you just open it up and click the file called *firefox* and choose *Run in Terminal* or *Run*.

---

### Post by Sinkingships7 on 2008-06-17
> **irshadcharm said:**
> how do you install?

You don't. It's a binary, so just double click the file that says "firefox" and select Run.

---

### Post by Exsecrabilus on 2008-06-17
> **cardinals_fan said:**
> Uh, did I miss something?
You missed the launch of Firefox 3.

---

### Post by irshadcharm on 2008-06-17
ive done that but no response from the terminal...the terminal vanishes

---

### Post by cardinals_fan on 2008-06-17
> **Redrazor39 said:**
> I have an idea: let's all download firefox 3 twice.. or three times, or 5 times! That way, mozilla gets many more downloads, and we can just delete the file later.

Let's do it! I know I will!
Artificially boosting their scores?  Maybe not.

---

### Post by Sinkingships7 on 2008-06-17
> **irshadcharm said:**
> ive done that but no response from the terminal...the terminal vanishes

just 'Run',not 'Run in Terminal'.

---

### Post by dodghz on 2008-06-17
You might need to look at the attributes of your download & make sure it's executable. Thereafter, it might install ok.

i.e.
right click the downloaded file
go to Permissions
tick box next to make file executable
close the window
double click the downloaded file

---

### Post by izelpii on 2008-06-17
I received the same error using FF3.

./firefox-bin
error while loading shared libraries: libjemalloc.so

and ended up in this forum.

I noticed that I was not running ./firefox, but ./firefox-bin
(like the original post)

turns out, that when I uncompressed FF, the executable 'firefox' was not copied to my directory, (create dir, move bz2, uncompress, move everything ..)

Just running 'firefox' instead of 'firefox-bin' solved the issue.

Maybe some people with this problem can solve it this way too.

---

### Post by melrom on 2008-06-17
Comin' at you from shinyyy new FF3 on a CentOS box!

Can't wait to put it on my personal comptuer when I get home!

---

### Post by cardinals_fan on 2008-06-17
> **Exsecrabilus said:**
> You missed the launch of Firefox 3.
What does that have to do with Neptune?

---

### Post by jpf76 on 2008-06-17
I really like the new address bar...or 'smart bar' as I think they are calling it.  Woot!

---

### Post by Exsecrabilus on 2008-06-17
> **cardinals_fan said:**
> What does that have to do with Neptune?
*Launch*? Robots? Rocket? Space? Moon? Planets? Neptune? Don't you see?

---

### Post by klange on 2008-06-17
Strange things happening on a Windows machine I'm trying to download on - I get the FF2 page, but it clearly says version: 3.0. This is strange because I get the FF3 page quite clearly on the machine I spent all afternoon waiting on.

Can't wait to download on my laptop just to download it.

---

### Post by irshadcharm on 2008-06-17
> **Sinkingships7 said:**
> just 'Run',not 'Run in Terminal'.

ive done that...no response...im a noob...so please tell the detailed steps...

---

### Post by NJC on 2008-06-17
> **sharks said:**
> 
[http://www.spreadfirefox.com/en-US/worldrecord/firefox3](http://www.spreadfirefox.com/en-US/worldrecord/firefox3) 

Hmm, connection timed out - and it's only lunch time here!

---

### Post by Sunflower1970 on 2008-06-17
It's working here...I see spaceships instead of balloons that were there before...

---

### Post by aysiu on 2008-06-17
If you're going to use the .tar.gz from the Mozilla website instead of updating through the Ubuntu repositories, you should refer to this link:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by Exsecrabilus on 2008-06-17
> **irshadcharm said:**
> im a noob...so please tell the detailed steps...
Right-click on the .tar.gz file, and click _Extract Here_.
Open up the folder (that just appeared) and look for a file called *firefox* (nothing more.)
Double-click it, and when a confirmation window pops up asking you whether to _Run in Terminal_, _Display_, _Cancel_ or _Run_, select **Run**.

---

### Post by melrom on 2008-06-17
> **jpf76 said:**
> I really like the new address bar...or 'smart bar' as I think they are calling it.  Woot!

I heard they're calling it the "awesome bar". ;)

---

### Post by Sunflower1970 on 2008-06-17
> **jpf76 said:**
> I really like the new address bar...or 'smart bar' as I think they are calling it.  Woot!

It has taken me a long time to figure out the best way for meto use the awesome bar (I think it's called) I've been using FF3 since the alpha stage, and at first I really disliked it. But now, I find it much more handy than I thought I would :)

---

### Post by Sim777 on 2008-06-17
> **Exsecrabilus said:**
> Right-click on the .tar.gz file, and click _Extract Here_.
Open up the folder (that just appeared) and look for a file called *firefox* (nothing more.)
Double-click it, and when a confirmation window pops up asking you whether to _Run in Terminal_, _Display_, _Cancel_ or _Run_, select **Run**.

Nothing happens. What's the command in terminal to do same?

---

### Post by cardinals_fan on 2008-06-17
> **Sim777 said:**
> Nothing happens. What's the command in terminal to do same?
./firefox

---

### Post by Exsecrabilus on 2008-06-17
When's this going to be in the updates????? :(

---

### Post by Exsecrabilus on 2008-06-17
Omg The Updates Are Here!!!!! Omg Omg Omg Omg Omg.

---

### Post by reyfer on 2008-06-17
Sorry, but I downloaded this, and every time I run it, I get my usual firefox 2 running, so....is there a way to actually install this? Should I move the extracted file to /etc/firefox or /etc/firefox 3.0 ? I run it by clicking on it, and it starts my usual firefox 2

---

### Post by oldsoundguy on 2008-06-17
Got it on two Windows machines .. only issue was with Skype, which took a visit to the Skype site and downloading their Beta release.

Works GREAT!! and VERY VERY FAST .. much faster than the previous version.  Like the new "look", too!

Curious about the Linux boxes and just when it is going to land in the repositories (learned the hard way not to install "off the web",  tarballs not withstanding.)

And of course, those that go via update manager will not be counted in the attempt for the record.

---

### Post by reyfer on 2008-06-17
Also I cannot get it via update manager because it says I already have the latest version running, but still I have firefox 2 running...help, please?

---

### Post by FuturePilot on 2008-06-17
> **melrom said:**
> I heard they're calling it the "awesome bar". ;)

That's because it's so awesome :lolflag:

Download is incredibly slow.

---

### Post by Sim777 on 2008-06-17
> **cardinals_fan said:**
> ./firefox

Thanks. 

>  /firefox$ ./firefox
./firefox-bin: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory


 

I'm trying to redownload it but their site is back to 2.0 version.

---

### Post by DAE_JA_VOO on 2008-06-17
Well, i upgraded through Synaptic, restarted and i'm still sitting with FF2. What's going on?

---

### Post by Sim777 on 2008-06-17
> **DAE_JA_VOO said:**
> Well, i upgraded through Synaptic, restarted and i'm still sitting with FF2. What's going on?

I looked in synapt and they had only 2.0 versions....

---

### Post by Jay_Bee on 2008-06-17
According to spreadfirefox page:
Total Downloads 1,707,620

Note: it says downloads not pledges (and last time I checked the number was 550,000) :)

---

### Post by DAE_JA_VOO on 2008-06-17
> **Sim777 said:**
> I looked in synapt and they had only 2.0 versions....

Hmmm, my bad then.

Also, i go to the FF site and i only see version 2.0.0.14.  Where can i DL 3?

---

### Post by ahawesome on 2008-06-17
_WOW!!!! Spreadfirefox.com just came up on this computer!!!_ :KS

[SIZE="6"]1,718,070[/SIZE] downloads worldwide. 441,156 in the US.


Seriously amazed that this works...

---

### Post by bobbocanfly on 2008-06-17
To all those trying to get it from Synaptic/Apt/Whatever: This isnt in the repos! You have to grab it from the Firefox website for it to count towards the record.

---

### Post by ahawesome on 2008-06-17
2,983,210 downloads at 4:49 PM EDT June 17th.

---

### Post by Sunflower1970 on 2008-06-17
> **ahawesome said:**
> 2,983,210 downloads at 4:49 PM EDT June 17th...

They must be having some trouble...I'm showing zero downloads....

That interactive map is pretty cool though...

---

### Post by Delever on 2008-06-17
> **Sunflower1970 said:**
> ..

They must be having some trouble...I'm showing zero downloads....

That interactive map is pretty cool though...

Well, probably no one was interested...

---

### Post by klange on 2008-06-17
Got it on two Windows machines at work and just finished downloading the tarbell on my laptop. Gonna get it on my family's machines at home as soon as I get back, and gotta count a download from server. Hope they're not filtering by IPs as that would give a lower number, and kill them in universities / business.

Freaking interactive map still doesn't work with SwfDec. >_>

---

### Post by nick09 on 2008-06-17
> **WindowsSucks said:**
> Got it on two Windows machines at work and just finished downloading the tarbell on my laptop. Gonna get it on my family's machines at home as soon as I get back, and gotta count a download from server. Hope they're not filtering by IPs as that would give a lower number, and kill them in universities / business.

Freaking interactive map still doesn't work with SwfDec. >_>

Yes they are doing by IP so people can't download more than once.

---

### Post by BackwardsDown on 2008-06-17
> What is Mozilla doing to make sure the record attempt is valid?

    Mozilla will only count downloads that are fully and completely transmitted, not partial or complete updates. We will also discard duplicate downloads with the help of a cookie system. We will be logging our downloads using Apache and these logs will be made available for audit to Guinness World Records™, as well as two judges - Corey Shields and Paul Vixie.

Multiple pc's on 1 IP will count as more downloads as far as I can tell, they count the cookies.

---

### Post by wipeout140 on 2008-06-17
Downloaded on XP and Hardy. But versions work great

---

### Post by reyfer on 2008-06-17
> **wipeout140 said:**
> Downloaded on XP and Hardy. But versions work great

How did you make it work in Hardy? I'm using the one from the repos because the one downloaded today does not run, using Kubuntu Hardy

---

### Post by zgornel on 2008-06-17
I did my share. :D

---

### Post by klange on 2008-06-17
Just went and installed the Windows version in Wine to test out some claims that it's just RC3. It's not, it loads the 3.0/firstrun page, not the RC3 one. Some crazy people out there.

---

### Post by hellion0 on 2008-06-17
Downloaded on four machines (Two Macs, a Windows laptop and a Linux laptop).

---

### Post by Gaming4JC on 2008-06-17
Anyone know how to compile the tar.bz2 on Ubuntu or have a deb I can get? :confused:

---

### Post by hellion0 on 2008-06-17
> **Gaming4JC said:**
> Anyone know how to compile the tar.bz2 on Ubuntu or have a deb I can get? :confused:Assuming you've already extracted it, you shouldn't even need to install it. Just run the "firefox-bin" file in the directory, I think.

Then wait for the final to hit the repos.

---

### Post by Exsecrabilus on 2008-06-17
> **hellion0 said:**
> Assuming you've already extracted it, you shouldn't even need to install it. Just run the "firefox-bin" file in the directory, I think.

Then wait for the final to hit the repos.
It already did.

---

### Post by The Devil Is A Squirrel on 2008-06-17
All I'm saying: [http://lubosz.de/Firefox3PerformanceBug/](http://lubosz.de/Firefox3PerformanceBug/)

Note: Under WinXP it's better but it's also an issue! (not for FF2 or Opera)

---

### Post by Gaming4JC on 2008-06-17
I don't see it? Can you post the link from packages.ubuntu.com, I only see a beta? (the offficial repos) :)

---

### Post by The Devil Is A Squirrel on 2008-06-17
All I'm saying: [http://lubosz.de/Firefox3PerformanceBug/](http://lubosz.de/Firefox3PerformanceBug/)

Note: Under WinXP it's better but it's also an issue! (not for FF2 or Opera)

---

### Post by Can+~ on 2008-06-17
firefox has **1,700,852 ** downloads.

(Consider the time of this post)

Let's see how much it grows.

---

### Post by TBOL3 on 2008-06-17
Well, I downloaded it, but I'm not going to use it, because I like the one in the repos.  However, our connection comes through a switch, which we connect our entire house to.  Do any of you know if it will count as a different download and help if I download it from a different computer?

---

### Post by Gaming4JC on 2008-06-17
LOL nice saying. I noticed this bug too, but it's not to much of a problem I guess. :-/
Hopefully they will fix it soon enough.

---

### Post by klange on 2008-06-17
> **The Devil Is A Squirrel said:**
> All I'm saying: [http://lubosz.de/Firefox3PerformanceBug/](http://lubosz.de/Firefox3PerformanceBug/)

Note: Under WinXP it's better but it's also an issue! (not for FF2 or Opera)
... What's supposed to be a major issue on that page?
Scrolling is a *bit* slower than normal, but honestly, that's to be expected from a page filled with lots of semi-transparent items. If it's the semitransparent tiling images, it's a Cairo thing.

---

### Post by Gaming4JC on 2008-06-17
Well the bug causes pages to get a lot slower when your makeing stuff in the GIMP and surfing the web. Also try other sites with a lot of graphics, it causes the same. Here's another example that lags my computer a good bit with FF3:
[http://z8.invisionfree.com/RRR_Racing_Forum](http://z8.invisionfree.com/RRR_Racing_Forum)

The Logo changer and background seem to greatly affect the scrolling. :-/

---

### Post by ahawesome on 2008-06-17
> **Sunflower1970 said:**
> They must be having some trouble...I'm showing zero downloads....

The number of downloads reached 2 million at one point. It's back down to about 1.7 million.

---

### Post by klange on 2008-06-17
> **ahawesome said:**
> The number of downloads reached 2 million at one point. It's back down to about 1.7 million.
Live number is available [here](http://downloadcounter.sj.mozilla.com/). Currently at 1.9 million.

---

### Post by ahawesome on 2008-06-17
Yeah, I've been keeping track of it. Hey, didn't they say you'd get a certificate for participating? I downloaded it to a Windows 2000 VM and just got a normal download page.

---

### Post by The Devil Is A Squirrel on 2008-06-17
> **WindowsSucks said:**
> ... What's supposed to be a major issue on that page?
Scrolling is a *bit* slower than normal, but honestly, that's to be expected from a page filled with lots of semi-transparent items. If it's the semitransparent tiling images, it's a Cairo thing.

Really? So try it with FF2, Opera, even IE. Not any problem there.

Try this page [www.xwiki.org](www.xwiki.org) (or sub pages). Even Gmail is slower. This IS a huge bug!

---

### Post by Gaming4JC on 2008-06-17
Aha! FireFox 3 just came on my software updates. So yah it hit the repositories... :D

---

### Post by aysiu on 2008-06-17
This page will help you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by andrewabc on 2008-06-17
> **Can+~ said:**
> firefox has **1,700,852 ** downloads.

(Consider the time of this post)

Let's see how much it grows.

Where'd you get that info from? Nothing showing at mozdev which is where they were posting server stats.

EDIT: nevermind, the tally is at
[http://www.spreadfirefox.com/en-US/worldrecord/](http://www.spreadfirefox.com/en-US/worldrecord/)

They have it broken down as to how many downloads from each country.

---

### Post by ahawesome on 2008-06-17
Back up to 2 million

---

### Post by Can+~ on 2008-06-17
> **Gaming4JC said:**
> Aha! FireFox 3 just came on my software updates. So yah it hit the repositories... :D

Are you on hardy? I've been updating in gutsy and nothing :(.

**2,012,488 downloads**

---

### Post by ahawesome on 2008-06-17
> **ahawesome said:**
> Hey, didn't they say you'd get a certificate for participating?

If you want a certificate, go [here]("http://www.spreadfirefox.com/en-US/worldrecord/certificate_form"). It was on the world record page. 2,042,333 downloads and still counting...

---

### Post by diaa on 2008-06-17
It's in the Repos :popcorn:

---

### Post by steveneddy on 2008-06-17
I DLed it anyway, but won't install it. I will wait for it to come down in the repos.

---

### Post by K.Mandla on 2008-06-17
Merged a LOT of similar threads together. And renamed the thread.

---

### Post by Kronie on 2008-06-17
[http://downloadcounter.sj.mozilla.com/](http://downloadcounter.sj.mozilla.com/)
2mil 117thousand and counting.. average 150 dls/second :P 5265 dls/minute

---

### Post by Kronie on 2008-06-17
guys how do i install the tar.gz file i downloaded from tehir site? 0_o

---

### Post by K.Mandla on 2008-06-17
And merged another one.

---

### Post by mrgnash on 2008-06-17
> **Kronie said:**
> guys how do i install the tar.gz file i downloaded from tehir site? 0_o

Just extract it, and run the executable.

---

### Post by Joeb454 on 2008-06-17
> **Kronie said:**
> guys how do i install the tar.gz file i downloaded from tehir site? 0_o

Wait for it to appear in the repo's, it's just easier :)

---

### Post by ladr0n on 2008-06-17
> **Kronie said:**
> guys how do i install the tar.gz file i downloaded from tehir site? 0_o

Just download the tarball to help their numbers.  If you update your system through synaptic, you'll get Firefox 3 (assuming you're on Hardy).

---

### Post by SomeGuyDude on 2008-06-17
Welp, no FF3 in Synaptic for me yet. Can't wait, though.

Actually, I can't wait for the Swiftfox variant, since I haven't used Firefox proper in a while.

---

### Post by diaa on 2008-06-17
> **Kronie said:**
> guys how do i install the tar.gz file i downloaded from tehir site? 0_o
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by Gaming4JC on 2008-06-17
> **K.Mandla said:**
> Merged a LOT of similar threads together. And renamed the thread.

Oh so that is what happened? I was on page 24 and it jumped to 34, lol. :)

Anyhow I am definitely seeing that scrolling bug in FF3 :(

---

### Post by z0mbie on 2008-06-17
> **SomeGuyDude said:**
> Welp, no FF3 in Synaptic for me yet. Can't wait, though.

Actually, I can't wait for the Swiftfox variant, since I haven't used Firefox proper in a while.

at this to your repo:

```
deb http://ppa.launchpad.net/fta/ubuntu hardy main
```


It's got the latest RC3 candidate which is also Firefox 3 Final, since no changes were made.

---

### Post by Kronie on 2008-06-17
> [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
..yea, ill just wait for it to hit the repos.. 

o yea, and also, i just checked the ysnaptic and i found theese:
firefox-3.0(installed(N.I))(last time i had firefox update was 3-4 days ago)
firefox-3.0 dev(N.I)
firefox-3.0 dom inspector(N.I)
firefox-3.0 gnome support(N.I)
firefox-3.0 venkman(N.I)

and i also got 
firefox-3.1(N.I)
and the dev, dom inspector etc for that version 0_o
so does that mean that i have firefox 3 final? 0_o cuz i remember after the last update(~3 days ago) i went to 'aout firefox' and it told me that i had firefox 3.0 (no RC, no beta)

---

### Post by klange on 2008-06-17
Firefox 3 final was *technically* out a few days ago - this was just the official release date. If you've been on the RC track and got an update a few days ago, it should be the final, right?

---

### Post by Kronie on 2008-06-17
i read on some forums that it was RC5 version... but again, i dont have any signs of RC or beta in about window or firefox header..

---

### Post by andrewabc on 2008-06-17
> **Kronie said:**
> i read on some forums that it was RC5 version... but again, i dont have any signs of RC or beta in about window or firefox header..

I'm pretty sure todays release is the exact same file as RC3. No difference whatsoever (other than file is renamed).

---

### Post by steveneddy on 2008-06-17
> **Polygon said:**
> *waits for firefox-3.0 package in ubuntu to be updated*

Me too, but I DLed it anyway, just so it counts.

I unpacked it and just ran it from the folder and it is very snappy.

I like it.

---

### Post by isaacj87 on 2008-06-17
Okay, I'll admit, I'm a little late to this thread...Could a kind Ubuntu Forums Member explain something to me...

I receive an update today and I looked at the description...Bug report indicated it was the release of RC2, but I could of sworn earlier today I saw RC3 available for download and now Mozilla is saying the "final" is now available. So, are we (linux distros) not getting the "final" release? Am I going to see another update to Firefox coming in the next week or so?

Sorry, I'm sure all these questions have been asked...

Thanks!

---

### Post by chudder on 2008-06-17
I have a question about FF3, I'm still running Feisty and it seems it's not in the repositories, could have guessed as much, but how would I get it to install optimally without messing up dependencies and all that?  Basically I would like to get it from a repository if I can and have it replace FF2.  Thanx!

---

### Post by aysiu on 2008-06-17
> **chudder said:**
> I have a question about FF3, I'm still running Feisty and it seems it's not in the repositories, could have guessed as much, but how would I get it to install optimally without messing up dependencies and all that?  Basically I would like to get it from a repository if I can and have it replace FF2.  Thanx!
This should help you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by riven0 on 2008-06-17
> **z0mbie said:**
> at this to your repo:

```
deb http://ppa.launchpad.net/fta/ubuntu hardy main
```


It's got the latest RC3 candidate which is also Firefox 3 Final, since no changes were made.


:( I did that, but it still listing the Firefox version as 3b5. *Sigh*, I'll just have to run it from the tar.gz until the repository is updated. Update soon, Canonical! :cry:

---

### Post by rab4567 on 2008-06-17
Just passed the 3 millon mark.

---

### Post by vishzilla on 2008-06-17
3 million. I wonder how many will permanently use Firefox 3 from that 3 million. Firefox does have a history of people who download and don't use.

---

### Post by andrewabc on 2008-06-18
Firefox 3 was mentioned on the colbert report!
It was during an interview with a guy who was talking about the internet.
Colbert asked what the safest browser is, and the guest responded with Firefox 3 since it was released today.

---

### Post by rab4567 on 2008-06-18
I think many people will retain it on their computers there is vast a difference from ff3 in April and now.   It actually is much more usebly than ff2, now if they only could fix the flashy thingy.

---

### Post by reyfer on 2008-06-18
> **rab4567 said:**
> I think many people will retain it on their computers there is vast a difference from ff3 in April and now.   It actually is much more usebly than ff2, now if they only could fix the flashy thingy.

What flashy thingy?

---

### Post by rab4567 on 2008-06-18
Adobe flash thingy.

---

### Post by gaspard.leon on 2008-06-18
Wow the download counter has really sped up: [http://downloadcounter.sj.mozilla.com/](http://downloadcounter.sj.mozilla.com/)

It was down to about 3500 per minute, now it's up past 11000+

must be those people in the USA getting home from work ;)

well I downloaded on my work machine, about to leave work and download at home... (I'm in New Zealand, and it's 5pm on the 18th)

---

### Post by jetpeach on 2008-06-18
in case anyone was wondering ( i think someone asked earlier in this thread and it was unanswered) i dug around to find out if the version in the ubuntu _regular_ repos is the final. it seems it is, because this final version is after RC1. RC3 is identical to the final, and RC2->RC3 only have a small difference for macs only. So the version in the repos must be the final... I wish there had been an easier way to see this though (why is "Help-about mozilla firefox" so worthless? no build number anywhere, just an older gecko number?)

---

### Post by j0shdt on 2008-06-18
Hey guyz! Hot news! I've just updated my ubuntu system, and one of those updates is FIREFOX. May be it comes from FF3 repository here:

deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main

I checked in synaptic, and it's NOT Release Candidate nor beta. It's 3.0. It kept all of my settings in ubuntu default beta 5.

What're you all waiting for? Install the repo and get it while it's still HOT:popcorn:!

---

### Post by hyperboloid on 2008-06-18
1. Go to: System -> Administration -> Update Manager

2. Click on "Check"

3. Install the updates. Enjoy Firefox 3.0  :)

---

### Post by SupaSonic on 2008-06-18
I can't get to getfirefox.com or mozilla.com atm. Too much for their servers?

---

### Post by moreinfo on 2008-06-18
Hi,

I started reading this post and then decided to take the jump to Firefox 3, well, that was 2 hours ago, now Im using my last window in Swiftfox, because i can't open anything but Opera.

Anywa, I'm still using 6.06 and I still like it, thing is I downloaded Firefox 3 and it says that I have to use GTK 2.0 what ever that is, but it also says I have GTK 2.08, I just need GTK 2.10 then it'll work, anyway reading down this post It recommended Swiftfox, so I decided to download that, I did and it said to move the download file to my home folder, so I copy and pasted from my desktop to my home folder then installed it.

It then collapsed! the firefox hangs when it opens and the swiftfox still says it requires GTK 2.10.

Can someone please explain step by step by step ;) ...sorry... what to do next and how to do it :D please... 
Thanks in advance

---

### Post by reyfer on 2008-06-18
> **rab4567 said:**
> Adobe flash thingy.

I installed flash, and all is perfect, so I don't understand the "flashy thingy" people talk about. No problems with flash for me so far.

---

### Post by ubuntu27 on 2008-06-18
All right people! Keep downloading Firefox3 from every single computer you got.

Visit your neighbors, and download it for them :D

Here is the link:

[http://www.spreadfirefox.com/worldrecord  ]("http://www.spreadfirefox.com/worldrecord")

---

### Post by K.Mandla on 2008-06-18
Merged more similar threads.

---

### Post by Mazza558 on 2008-06-18
Hah, 4,700,000 downloads as of now, with just under 7,000 downloads a minute.

---

### Post by gaspard.leon on 2008-06-18
just passed that magic five million mark!

baby!

0.08% of the worlds population has 1 copy... or more likely a much smaller group has many copies LOL

---

### Post by The_Dark_Lord on 2008-06-18
@gaspard.leon, im also from New Zealand

5,214,369 downloads as of now 8:37pm jun 18 New zealand

---

### Post by Zeratul7 on 2008-06-18
[http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) only has packages for hardy but what about gutsy? There is only ff3 b2 for gutsy in there. Where can I get an update for gutsy?

---

### Post by -Outcast- on 2008-06-18
People I download FF3 on Vista and Ubuntu 8.04. 

It knocks the pants of FF2 on Vista. 

On Ubuntu it looks like it got a raw deal.... 

It looks sooo plain and it takes up so much space. Even with small icons enabled it still has 1/8 of an inch more space on the Vista version. That might not seem like much but on a laptop its a lot. Then consider without disabling the taskbars you lose even more space on the ubuntu version. 

Secondly the GUI is old on Ubuntu!! There are no nice icons, and everything looks really clunky.

Very dissapointed with the ubuntu version, very happy with the Vista version. 

Bollox

---

### Post by meganox on 2008-06-18
So it I want to help with the world record I have to download the tarball as well as install from repos?

Pffffft no thanks.

---

### Post by quanumphaze on 2008-06-18
Nearly 6M, what was their original target again?

---

### Post by rab4567 on 2008-06-18
Oh man this is great! FF3 final version really works on youtube.

---

### Post by rab4567 on 2008-06-18
Hey outcast you know there are plugins for changing the look of FF.

---

### Post by Joeb454 on 2008-06-18
> **-Outcast- said:**
> People I download FF3 on Vista and Ubuntu 8.04. 

It knocks the pants of FF2 on Vista. 

On Ubuntu it looks like it got a raw deal.... 

It looks sooo plain and it takes up so much space. Even with small icons enabled it still has 1/8 of an inch more space on the Vista version. That might not seem like much but on a laptop its a lot. Then consider without disabling the taskbars you lose even more space on the ubuntu version. 

Secondly the GUI is old on Ubuntu!! There are no nice icons, and everything looks really clunky.

Very dissapointed with the ubuntu version, very happy with the Vista version. 

Bollox

Mozilla stated they didn't think the visuals were overly important to make it stand out on Linux (probably because it's included by default in quite a few distro's). So it didn't get a theme like Windows or Mac did, though you can always change that :)

Also the space issue you may find is due to the fact that you have a panel at the top and bottom of your screen, instead of just 1 :)

---

### Post by sharks on 2008-06-18
[http://news.softpedia.com/news/First-Look-at-Firefox-3-0-for-Linux-88211.shtml](http://news.softpedia.com/news/First-Look-at-Firefox-3-0-for-Linux-88211.shtml)

---

### Post by klange on 2008-06-18
6.3 at 8:14AM EDT. And since they updated the end time to match the start time (now 3:16PM EDT), and at the current rate, they should hit another 2 million by the end mark.

---

### Post by Jay_Bee on 2008-06-18
If anyone wants the Keyhole on linux, check out this theme:
[https://addons.mozilla.org/en-US/firefox/addon/6839](https://addons.mozilla.org/en-US/firefox/addon/6839)

---

### Post by K.Mandla on 2008-06-18
Merged similar threads.

---

### Post by jpf76 on 2008-06-18
> **melrom said:**
> I heard they're calling it the "awesome bar". ;)

awesome bar is even better! \\:D/

---

### Post by Sportingfan on 2008-06-18
I installed Firefox 3 this morning. 
First opinion: it seems nice and smooth but the home button is not in the navigation bar (and i don't need a bookmark bar or whatever, but this was easily fixed).

After using it for several hours, i got so frustrated that i moved back to firefox 2. 
Firefox 3 is said to be lightweight but it isn't at all.(at least not at this moment) It was eating more memory then my fat uncle eats hamburgers! 
Firefox constantly turned into it's gray-hanging mode. Therefore i got back to the previous version.

Another thing i don't like about it, is how it handles secure pages. When entering one, firefox 3 gave me the idea that i was using Microbugging internet explorer. I had to confirm that i would like to enter that page, several times.

I hope the developers can do something about this because i liked all other versions of their browser.

---

### Post by kneewax on 2008-06-18
OK - I am so confused....


IS FF3.0 out on the distros yet?  A few folk say yes, but I have seen no update here.  I did about: after this morning's package update but am told there that I am running FF1.9 even tho I know it is the RC of FF3.0

When I try to add a theme (poor show that on FF's part) I get a warning saying that I cannot install because it is for a later version....

Can anyone tell me why????  Is there a simple 'howto' to do a manual install from the tarball?  I think something is screwed up...

---

### Post by nick09 on 2008-06-18
> **kneewax said:**
> OK - I am so confused....


IS FF3.0 out on the distros yet?  A few folk say yes, but I have seen no update here.  I did about: after this morning's package update but am told there that I am running FF1.9 even tho I know it is the RC of FF3.0

When I try to add a theme (poor show that on FF's part) I get a warning saying that I cannot install because it is for a later version....

Can anyone tell me why????  Is there a simple 'howto' to do a manual install from the tarball?  I think something is screwed up...

Try:
```
sudo apt-get update
```

Then try checking the update manager.

---

### Post by Sportingfan on 2008-06-18
Kneewax, see [this page]("http://news.softpedia.com/news/Install-Firefox-3-Beta-3-on-Ubuntu-7-10-78875.shtml")

---

### Post by -Outcast- on 2008-06-18
Yea I know about the themes and that, also I disable the lower bar in Ubuntu anyways. I would have just thought they would make it look at bit better. After all Ubuntu is prasied for bringing the GUI back to Linux, hence the general public like it so much. 

I will have to download the vista theme for FF3 and see if it reduces the amount of space it takes up. :popcorn:

Seriously though, there is a big difference between vista and ubuntu FF3 Gui:-\"

---

### Post by graabein on 2008-06-18
I just installed Firefox 3 on Windows XP at work today. The default icons for reload, stop and home buttons are awful so I quickly installed the [Kempelton 3.0 theme]("https://addons.mozilla.org/en-US/firefox/addon/5394") along with the [del.icio.us official add-on]("https://addons.mozilla.org/en-US/firefox/addon/3615").

---

### Post by Exsecrabilus on 2008-06-18
> **graabein said:**
> I just installed Firefox 3 on Windows XP at work today. The default icons for reload, stop and home buttons are awful so I quickly installed the [Kempelton 3.0 theme]("https://addons.mozilla.org/en-US/firefox/addon/5394") along with the [del.icio.us official add-on]("https://addons.mozilla.org/en-US/firefox/addon/3615").
If you don't like the large back button, you could always go *View -> Toolbars -> Customize* and check *Use Small Icons*.
This will reduce all other icons by like 5% but will make the large back button the same size as the front button.

---

### Post by Dbugger on 2008-06-18
This thread is kinda long to check it all out.... could someone tell me how could I install FF3 in Gutsy?

---

### Post by Exsecrabilus on 2008-06-18
You could try downloading the [Firefox 3 .deb packages](http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=hardy-updates&section=all) for Hardy, though some unmet dependencies might break your whole system.

Or you could just download the [.tar.bz2 file](http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0&os=linux&lang=en-US), extract it, and click the file called *firefox* and choose *Run*.

---

### Post by Dr Small on 2008-06-18
Yeah. The SSL part is what bugs me. I really don't care if it is a self-signed certificate or not. My server's is a self-signed one, but I want the SSL encryption for transfering data across the network.

My biggest problem with Firefox 3 was it severely lagged when opening it. So I immediately switched back to RC2.

---

### Post by Dbugger on 2008-06-18
> **Exsecrabilus said:**
> You could try downloading the [Firefox 3 .deb packages](http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=hardy-updates&section=all) for Hardy, though some unmet dependencies might break your whole system.

Or you could just download the [.tar.bz2 file](http://www.mozilla.com/en-US/products/download.html?product=firefox-3.0&os=linux&lang=en-US), extract it, and click the file called *firefox* and choose *Run*.

I was hoping for a "cleaner" installation help.

---

### Post by Exsecrabilus on 2008-06-18
> **Dbugger said:**
> I was hoping for a "cleaner" installation help.
Uhh, try upgrading.

One click in Update Manager!

XD

---

### Post by mpince on 2008-06-18
71100949

What time did the download officially go live yesterday?

---

### Post by nick09 on 2008-06-18
> **mpince said:**
> 71100949

What time did the download officially go live yesterday?

well it ends:
11:16 a.m. PDT (18:16 UTC) on June 18th

so I'm guessing 11:15 AM the 17th.

---

### Post by GStubbs43 on 2008-06-18
> **mpince said:**
> 71100949

What time did the download officially go live yesterday?

11:16 a.m. PDT (18:16 UTC)

That's 11:16 a.m. in Mountain View, 2:16 p.m. in Toronto, 3:16 p.m. in Rio de Janeiro, 8:16 p.m. in Paris, Madrid, Berlin, Rome and Warsaw, 10:16 p.m. in Moscow, and June 19, 2008 at 2:16 a.m. in Beijing and 3:16 a.m. in Tokyo.

(from [http://www.spreadfirefox.com/en-US/worldrecord/](http://www.spreadfirefox.com/en-US/worldrecord/))

---

### Post by FuturePilot on 2008-06-18
> **kneewax said:**
> OK - I am so confused....


IS FF3.0 out on the distros yet?  A few folk say yes, but I have seen no update here.  I did about: after this morning's package update but am told there that I am running FF1.9 even tho I know it is the RC of FF3.0


I haven't seen the update either. Mine still says (Build 2008060309) in the title bar. :confused:

---

### Post by ahawesome on 2008-06-18
[Here's a post from the Mozilla Blog.]("http://blog.mozilla.com/blog/2008/06/17/kicking-off-firefox-3-download-day-with-a-boom/") Personally, I find some of the stats pretty amazing. Especially the following:

> We are currently serving almost 9,000 downloads a minute

I had been wondering what that number was. Also, 7,389,769 downloads with just over two hours to go.

---

### Post by mordi05 on 2008-06-18
I downloaded the tar.bz2 package, extracted it and ran the firefox file. So firefox 3 loaded as it should.

However whenever I close it and try to reopen firefox from my panel, its firefox 2 again. Is there another way to really install it?

I mostly use the package manager to install things, sorry.

---

### Post by Delever on 2008-06-18
> **mordi05 said:**
> I downloaded the tar.bz2 package, extracted it and ran the firefox file. So firefox 3 loaded as it should.

However whenever I close it and try to reopen firefox from my panel, its firefox 2 again. Is there another way to really install it?

I mostly use the package manager to install things, sorry.

There was update in repositories. Try to update.

---

### Post by mgol on 2008-06-18
> **Delever said:**
> There was update in repositories. Try to update.

This is RC2, I have had it since June 10. Nevertheless, I'm not convinced if there are any differences between RC2 and final version.

---

### Post by mordi05 on 2008-06-18
But there must be something I am missing about the downloadable install right?

Anyone else been able to permanently install the final release?

---

### Post by russlar on 2008-06-18
> **mordi05 said:**
> But there must be something I am missing about the downloadable install right?

Anyone else been able to permanently install the final release?

On gutsy, I dl'ed the tarball to a directory on my desktop. from there, I used tar -xvfj *filename*. That creates a directory called firefox. I then moved that directory to /opt. At this point, it's perma-installed,

---

### Post by aysiu on 2008-06-18
> **russlar said:**
> On gutsy, I dl'ed the tarball to a directory on my desktop. from there, I used tar -xvfj *filename*. That creates a directory called firefox. I then moved that directory to /opt. At this point, it's perma-installed,
You're missing a couple of steps, as the command ```
firefox
``` won't launch the Mozilla version of Firefox, and the Mozilla version also won't be linked to your plugins.

More details here:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by mordi05 on 2008-06-18
I see now.
Thank you for clearing that up.

---

### Post by ahawesome on 2008-06-18
Download Day has just finished. And now, the total number of downloads worldwide...

**[SIZE="7"][COLOR="Red"]8,249,092!!![/COLOR][/SIZE]**

Now the record people will review it and Firefox may have set a world record!

---

### Post by klange on 2008-06-18
And it's over.
8.3 million downloads for the record!
And still going strong over 10,000/min. Amazing.

@ahawesome: That number is a few minutes old ;)

---

### Post by ahawesome on 2008-06-18
Whoa. I didn't see that they still have the counter going. How long is it going to keep going?

---

### Post by ice60 on 2008-06-18
edit, i want to put this in another firefox thread, maybe it will end up here??

---

### Post by ahawesome on 2008-06-18
They took off the counter on the record site. It just says zero downloads.

---

### Post by graabein on 2008-06-19
> **Exsecrabilus said:**
> If you don't like the large back button, you could always go *View -> Toolbars -> Customize* and check *Use Small Icons*.
This will reduce all other icons by like 5% but will make the large back button the same size as the front button.

Thanks for the tip but I'm actually fine with the large back button. It's the reload, stop and home buttons that look ugly on classic Windows XP. Problem solved with Kempelton 3.0 theme.

> **ahawesome said:**
> They took off the counter on the record site. It just says zero downloads.

That's not very accurate ;)

---

### Post by moore.bryan on 2008-06-19
just wondering if anyone else has found difficulty with some addons and ubuntu's firefox 3.0rc3; both firegestures and firetray install, but do not work. any ideas where i can start to debug?

---

### Post by GavinZac on 2008-06-19
> **moore.bryan said:**
> just wondering if anyone else has found difficulty with some addons and ubuntu's firefox 3.0rc3; both firegestures and firetray install, but do not work. any ideas where i can start to debug?

Firebug. 99% of firefox addons are just javascript controlling xml/xul so any errors show up in Firebug.

---

### Post by samwyse on 2008-06-19
I find it silly that you need an extension for switching tabs with the mouse wheel on the tab bar. Any extension that puts "back" on the top of the image context menu? The normal behaviour is just user unfriendly.

---

### Post by moore.bryan on 2008-06-19
i've solved the firetray issue... the official addons page was installing 0.1.9beta, when simply installing 0.1.9 works. strange.

@GavinZac:
how will firebug help me evaluate what's going wrong with firegestures?

---

### Post by GavinZac on 2008-06-19
> **moore.bryan said:**
> @GavinZac:
how will firebug help me evaluate what's going wrong with firegestures?

Assuming its an error in the javascript code, it will show some errors in its Javascript Error Console, and allow you to place 'stops' where there error is. 75% of the time the error involves some value being undefined.

---

### Post by -Outcast- on 2008-06-19
Anyone know how to remove the File-Edit-View toolbar, I want to make more space without going smaller? 

Erm, if you could send me a message it would be good, this thread is getting very long, don't know if I can find my way back:confused:

---

### Post by GavinZac on 2008-06-19
> **-Outcast- said:**
> Anyone know how to remove the File-Edit-View toolbar, I want to make more space without going smaller? 

Erm, if you could send me a message it would be good, this thread is getting very long, don't know if I can find my way back:confused:

An extension called "Tiny Menu". I use it in conjunction with messing around with the toolbars to give me this setup:

---

### Post by moore.bryan on 2008-06-19
> **GavinZac said:**
> Assuming its an error in the javascript code, it will show some errors in its Javascript Error Console, and allow you to place 'stops' where there error is. 75% of the time the error involves some value being undefined.
no dice; no errors. i do have another question, though: do you happen to know the order of dirs firefox 3.0 installed from the repos looks in when it starts; i seem to have an endless supply of firefox, firefox-3.0, mozilla, mozilla-trunk, etc. dirs.

thanks, in-advance.

---

### Post by -Outcast- on 2008-06-19
Thank you  for the tiny menu, but I was looking for an option to actually turn it on and off. Will have a look anyways

---

### Post by -Outcast- on 2008-06-19
Nope, tiny menu wasn't what I wanted, top toolbar space is still there

---

### Post by GStubbs43 on 2008-06-19
> **-Outcast- said:**
> Nope, tiny menu wasn't what I wanted, top toolbar space is still there


You can use tiny menu, then move all of the navigation toolbar stuff up to the top toolbar, and hide the location toolbar.

---

### Post by -Outcast- on 2008-06-19
thanks will try again
:KS

---

### Post by BreakDecks on 2008-06-19
[http://tomoshibi.mozilla.jp/](http://tomoshibi.mozilla.jp/)

---

### Post by Kronie on 2008-06-21
yay! foxy 3 had hit the repos couple hours ago! ^_^

---

### Post by Kronie on 2008-06-21
@-Outcast-
check this out, [IMG]http://ipicture.ru/uploads/080619/ruw4tyVlBe.png[/IMG]

---

### Post by sports fan Matt on 2008-06-22
I just downloaded 3.0 on my dad's laptop (dialup) and it seems faster then FF 2..I'm even using the grapple graphite theme..But I will probably use Opera 9.5 on my machine when i return home

---

### Post by moore.bryan on 2008-06-24
this is a *little* off-topics, but has anyone else noticed running the latest stable safari (3.1.2) through wine is even faster at rendering than ff3 and even konqueror-kde4? i get the difference between gecko and webkit, but why would safari be faster than konq4 being they use basically the same rendering engine?

---

### Post by Chame_Wizard on 2008-06-24
maybe this week i can finally use my JMW5 :(

---

### Post by kuja on 2008-06-24
> **moore.bryan said:**
> this is a *little* off-topics, but has anyone else noticed running the latest stable safari (3.1.2) through wine is even faster at rendering than ff3 and even konqueror-kde4? i get the difference between gecko and webkit, but why would safari be faster than konq4 being they use basically the same rendering engine?

Well, webkit forked khtml years ago, They've had plenty of time to make tons of changes to it ... many of which never make their way back to khtml.

---

### Post by moore.bryan on 2008-06-24
> **kuja said:**
> Well, webkit forked khtml years ago, They've had plenty of time to make tons of changes to it ... many of which never make their way back to khtml.
i realized there was a fork, but didn't know to what extent. strange a lot of the positive changes won't make their way back...

---

### Post by hanzomon4 on 2008-06-24
No matter... won't kde4 start using webkit?

---

### Post by moore.bryan on 2008-06-25
> **hanzomon4 said:**
> No matter... won't kde4 start using webkit?
that's what i thought, but konqueror-kde4 isn't nearly as quick rendering as safari through wine. it is also quite buggy for me, crashing every ten minutes or so.

---

