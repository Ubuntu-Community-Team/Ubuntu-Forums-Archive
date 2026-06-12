---
title: "Concerned criticism : firefox"
date: 2007-06-22
forum: The Cafe
---

### Post by vexorian on 2007-06-22
I got to say, I love firefox! and all its features, specially the addons. But I also hate firefox, for one big reason:

It is way too independent! Yes, it is true, it fails to integrate at all with its host OS, I know for a fact it doesn't look correctly in Mac OS/X , I've seen its flaws in windows, it won't render any gtk theme correctly, not to mention it won't use the Linux icon themes and it absolutely hates KDE! (it will fail rendering the selected menus correctly!)

As a matter of fact, the only Desktop that doesn't really have huge issues with integration but just some minor things that don't really matter is Windows! friging windows! , why is firefox promoting such Operating System?

Seriously, shouldn't the Linux community ask firefox to correctly integrate to gtk AND qt (it is made to be flexible, you know...) besides of coming with the ability to use the system's icons instead of relying on themes for that?, is it so hard for it?

As a matter of fact, I would have moved to epiphany a long ago if it wasn't for the fact epiphany doesn't have a NoScript equivalent, I swear, if it did I would be using it already.

Edit: I am including an screenshot just in case, firefox with no installed themes, and epiphany, epiphany shows how it "should" look, notice the size of the menu bar and the icons that match the gorilla icon theme I installed.

edit II: forgot to mention the tabs, look how different.

---

### Post by juxtaposed on 2007-06-22
For me it's always worked fine. Yea, not as much in KDE, but still. My big problem is the fact that it takes alot of RAM.

---

### Post by vexorian on 2007-06-22
I don't care about the RAM FUD, but really use a custom gtk theme and notice, firefox is the only app that renders a huge menu app, all the other gtk apps are rendering the menu bar correctly.

or how about changing the icon theme, icon themes contain icons for toolbars specially reload, home, back and forward, but firefox won't use them... You have to hope someone made a firefox theme that's compatible.

---

### Post by SoulinEther on 2007-06-22
Epiphany + javascript / java disabled, enabled only when you're visiting sites you trust?

Like juxtaposed (or justaposé, the sexier sounding french version) said, my beef is with its ram consumption.

---

### Post by vexorian on 2007-06-22
If you are asking what I want yes that's it.

If there is a way to do that then teach me...

But noscript is so practical, if javascript was blocked you can enable with 2 clicks. I only have 3 sites on whitelist because of that...

---

### Post by SoulinEther on 2007-06-22
sudo apt-get install epiphany-browser

Run it with epiphany

Edit > Preferences > Privacy.

Simple. :)

---

### Post by juxtaposed on 2007-06-22
> I don't care about the RAM FUD

Explain?

You're saying I am spreading fear, uncertainty, and doubt about firefoxs ram usage?

---

### Post by kamaboko on 2007-06-22
I use FF on XP, Vista, and Ubuntu (Edgy).  Once in a while in Ubuntu FF over takes my CPU and cycles it out to 100%.  I have to close FF and re-open it.  I also occasionally run into a few websites using Ubuntu and FF whereby FF either won't download the media or play it.  Other than that it has been fine.

---

### Post by CheShA on 2007-06-22
> **kamaboko said:**
> I use FF on XP, Vista, and Ubuntu (Edgy).  Once in a while in Ubuntu FF over takes my CPU and cycles it out to 100%.  I have to close FF and re-open it.  

Are you using any extensions?  I've had these kinds of problems myself and it has always been an extension that caused the problem, not FF itsself.  If so, try disabling them one at a time to see which one is causing the problem.

---

### Post by crimesaucer on 2007-06-22
> **vexorian said:**
> I got to say, I love firefox! and all its features, specially the addons. But I also hate firefox, for one big reason:

It is way too independent! Yes, it is true, it fails to integrate at all with its host OS, I know for a fact it doesn't look correctly in Mac OS/X , I've seen its flaws in windows, it won't render any gtk theme correctly, not to mention it won't use the Linux icon themes and it absolutely hates KDE! (it will fail rendering the selected menus correctly!)

As a matter of fact, the only Desktop that doesn't really have huge issues with integration but just some minor things that don't really matter is Windows! friging windows! , why is firefox promoting such Operating System?

Seriously, shouldn't the Linux community ask firefox to correctly integrate to gtk AND qt (it is made to be flexible, you know...) besides of coming with the ability to use the system's icons instead of relying on themes for that?, is it so hard for it?

As a matter of fact, I would have moved to epiphany a long ago if it wasn't for the fact epiphany doesn't have a NoScript equivalent, I swear, if it did I would be using it already.

I don't agree... Firefox will use your gtk-2.0 in the default classic theme...it only doesn't use the gtk-2.0 theme when using an installed Firefox theme.

This is my Firefox using my gtk-2.0 theme for XFCE:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-30-11.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-30-12.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-30-12.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-31-5.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-31-6.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-31-6.png)

...Not only does Firefox 2.0.0.4 use my gtk-2.0 theme, Thunderbird 2 uses it as well...and I even have the UbuntuStudio Folders in my Firefox 2.0.0.4 drop down menus.

To change the icons in Firefox 2.0.0.4 it is really easy, just replace the Toolbar.png in your /usr/lib/firefox/chrome/classic/skin/classic/browser directory, and to change the folders just change the folder-item.png in your /usr/lib/firefox/chrome/classic/skin/classic/global/icons directory.

I use a little userChrome.css to make my tab-bar look better, but you could just keep the default look.

---

### Post by Ultra Magnus on 2007-06-22
FF does seem to have some memory leeks - but its a solid browser and a good all rounder

---

### Post by crimesaucer on 2007-06-22
I have no problems with my memory.

---

### Post by CheShA on 2007-06-22
> **juxtaposed said:**
> Explain?

You're saying I am spreading fear, uncertainty, and doubt about firefoxs ram usage?

I wouldn't go as far as to call it FUD, but I personally think FFs RAM 'issue' tends to get blown out of proportion.     I can run a single FF session for weeks at a time without it bloating too badly. It usually settles at around 100Mb  and stays there, which I don't really see as being an issue for what is probably the most important application on my PC. Plus, its not like its a memory leak or anything, it's all being used!  It might seem quite hefty when there's only one or two tabs open, but IIRC, FF also scales better than most other [popular] browsers so when you get up to 15 or 20 tabs, it can even work out more efficient than e.g. Opera or IE.

---

### Post by juxtaposed on 2007-06-22
> but I personally think FFs RAM 'issue' tends to get blown out of proportion.

All I know is that I can have alot more open tabs in opera and it is still faster then firefox.

That said, I do use firefox (iceweasel actually), but I don't know why.

---

### Post by crimesaucer on 2007-06-22
> **CheShA said:**
> " but I personally think FFs RAM 'issue' tends to get blown out of proportion."

I agree...just like the Fasterfox issues, and people's incorrect settings in about:config

EDIT:

I've tried Opera and Epiphany...and if you have Firefox correctly tweaked in about:config, it is about as fast as Opera, easier to use, more enjoyable to use, better looking, with better extensions offered compared to the userscripts and widgets in Opera, and it keeps getting better...not to mention most web pages look better in Firefox rather than Opera.

And the next Firefox is going to use your gtk-2.0 widgets more properly in the wep pages.

---

### Post by nalmeth on 2007-06-22
crimesaucer,

how did you get those icons and buttons at the very top alongside the menu items?

Delicious, weather, Gmail, etc, that is very cool.
It bugs me when there is a whole bar of space not being used.

---

### Post by CheShA on 2007-06-22
[COLOR=Silver]Different extensions  sometimes add different buttons. e.g for delicious, check [here]("http://del.icio.us/help/firefox/extension")

[COLOR=Black]Sorry just realised what you were on about - that is pretty neat[/COLOR] :D
[/COLOR]

---

### Post by CheShA on 2007-06-22
Youneed to add a new tool bar - right click on your toolbar, lcikc customize then add a new toolbar. Add you buttons and move it to where you want. Sweet!

---

### Post by crimesaucer on 2007-06-22
> **nalmeth said:**
> crimesaucer,

how did you get those icons and buttons at the very top alongside the menu items?

Delicious, weather, Gmail, etc, that is very cool.
It bugs me when there is a whole bar of space not being used.

I have used a lot of different toolbar configurations so as to only use 2 toolbars and a tab-bar...When I use extensions like Stumbleupon or Forecast Fox Enhanced I add them into the Toolbar-Menubar and into my Navigation bar. 


For this screenshot I just clicked: View-->--Toolbars-->--Customize 

...and then put the url address bar down to the lower toolbar, and then put all of the icons up to the upper Navigation toolbar or also called, the toolbar-menubar...

---

### Post by SoulinEther on 2007-06-22
Well, for me, Firefox in Ubuntu has a problem loading pages with either large pictures or repeating backgrounds, especially when those backgrounds are PNG to utilize its alpha layer - ie, making shadows.

Completely slows down my computer... but epiphany does that too. It's not Firefox, it's gecko, I guess.

Otherwise both are great.

---

### Post by nalmeth on 2007-06-22
Thanks CheShA and crimesaucer!

BTW: Maybe its just me, but I think firefox looks BETTER in GNU/Linux than in Windows, and even with my rather sluggish laptop, it runs acceptably. I need the features man

---

### Post by nalmeth on 2007-06-22
I love having the 'add tab' and add 'window' buttons, but what I've learned today kicks even more ***

---

### Post by nalmeth on 2007-06-22
??? OK... trying again with screenshot

---

### Post by airtonix on 2007-06-22
converslly by choosing to not use firefox or epiphany dues to these (infrequent) memory leaks....you can look forward to using internet explorer....or konqourer...

where your patience will be tested (frequently in IE's case) by crashing your browser window....and all the other browser windows....plus the desktop....

seya...sorry forgot what YOU WERE DOING? sorry to break your concentration. but you have to wait another 5 secs for the system to become usable again...

i choose epiphany or opera anyday...for this outlines probably the one of the strongest points for not creating "swiss-army-desktop-slash-office-applications-in-one-blob".

blah. end rant

---

### Post by qamelian on 2007-06-22
> **Ultra Magnus said:**
> FF does seem to have some memory leeks - but its a solid browser and a good all rounder

No memory leaks according to the last round of leak tests that I saw reported. However, unless you tweak a few settings, Firefox will do a few things that chew up far more memory than some users would like.

---

### Post by crimesaucer on 2007-06-22
> **SoulinEther said:**
> Well, for me, Firefox in Ubuntu has a problem loading pages with either large pictures or repeating backgrounds, especially when those backgrounds are PNG to utilize its alpha layer - ie, making shadows.

Completely slows down my computer... but epiphany does that too. It's not Firefox, it's gecko, I guess.

Otherwise both are great.

My Firefox uses a gtk-2.0 gradient box fill with no pix_map images, so it stays really fast, faster then an installed theme. The only image I use is a 1 pixel wide image for the tab-bar using userChrome.css and it doesn't slow anything down at all. My icons and folders are placed into the default classic folder using the same name as the icons and folder-item that I replaced, so it stays the exact same as the default theme...


@ nalmeth- try to install either your stumble upon toolbar or an extension like Forecastfox Enhanced to your upper menubar...then try and add icons to it.

---

### Post by SoulinEther on 2007-06-22
> **crimesaucer said:**
> My Firefox uses a gtk-2.0 gradient box fill with no pix_map images, so it stays really fast, faster then an installed theme. The only image I use is a 1 pixel wide image for the tab-bar using userChrome.css and it doesn't slow anything down at all. My icons and folders are placed into the default classic folder using the same name as the icons and folder-item that I replaced, so it stays the exact same as the default theme...


@ nalmeth- try to install either your stumble upon toolbar or an extension like Forecastfox Enhanced to your upper menubar...then try and add icons to it.
You must have misunderstood me - I meant when it renders a page with a background that repeats.

---

### Post by CheShA on 2007-06-22
> **qamelian said:**
> No memory leaks according to the last round of leak tests that I saw reported. However, unless you tweak a few settings, Firefox will do a few things that chew up far more memory than some users would like.

Yup. not memory leaks -  "it's a feature not a bug"!!!

---

### Post by crimesaucer on 2007-06-22
> **SoulinEther said:**
> You must have misunderstood me - I meant when it renders a page with a background that repeats.

I did...I thought you were saying a back ground image for a themes toolbars like some themes use with pixmaps images for buttons and toolbars...

Sorry.

---

### Post by SoulinEther on 2007-06-22
> **crimesaucer said:**
> I did...I thought you were saying a back ground image for a themes toolbars like some themes use with pixmaps images for buttons and toolbars...

Sorry.
I forgive you. :)

What a waste of a post.

---

### Post by zero244 on 2007-06-22
I like Firefox a lot and its pretty much all I use.
I do think it will occasionally malfunction if your running Beryl or Compiz.
With my machine on the fairly rare occasion Firfox malfunctions it usually brings my whole system down. A complete solid Freeze that requires a reset.

---

### Post by crimesaucer on 2007-06-22
> **SoulinEther said:**
> Well, for me, Firefox in Ubuntu has a problem loading pages with either large pictures or repeating backgrounds, especially when those backgrounds are PNG to utilize its alpha layer - ie, making shadows.

Completely slows down my computer... but epiphany does that too. It's not Firefox, it's gecko, I guess.

Otherwise both are great.

After re-reading your comment, I think you might want to check these about:config tweaks out that might help in page loading times...

This is an older page but it explains some good things: [http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)

This is the newer page of configuration: [http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)

This is a good reference to look any setting up: [http://kb.mozillazine.org/Category:Preferences](http://kb.mozillazine.org/Category:Preferences)

and : [http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Mail.db+timestamp+leeway](http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Mail.db+timestamp+leeway)

and another: [http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)

---

### Post by vexorian on 2007-06-22
added screenshot to first post so people understand what I am trying to say, It should work combined out of the box, and not require people to manually change themes (and most of the times they have to look for the icons themselves or even make their own firefox themes... ) It is bad for ubuntu's consistance if you ask, the theme manager changes all the preinstalled apps but firefox,...

---

### Post by macogw on 2007-06-23
I don't like integration anyway.  Evolution?  Yuck, won't let me use a calendar without setting it to muck about with my email.  I don't want multiple programs mucking about with each other.

I just have to do the occasional "killall -9 firefox-bin" which I*shouldn't* have to do, but the darned mem leaks still haven't been squashed.

---

### Post by vexorian on 2007-06-23
That's just senseless, this is not about one program integrating with another, it is about a program integrating with the whole desktop

---

### Post by macogw on 2007-06-23
Okay, howabout, "I have no idea what you're talking about since when I change my GNOME theme Firefox changes with it.  It doesn't keep old window borders, and it pics up the new colors I set in my GTK settings just fine, so I don't see anything wrong"?

Also, the only time I've ever installed an icon theme, nothing changed in ANY of my apps, not just firefox.  The GNOME Menu and Nautilus are the only things that changed.  Every other app looks perfectly normal (the way it did originally).  Perhaps every other program has this problem too?

---

### Post by jrusso2 on 2007-06-23
> **CheShA said:**
> I wouldn't go as far as to call it FUD, but I personally think FFs RAM 'issue' tends to get blown out of proportion.     I can run a single FF session for weeks at a time without it bloating too badly. It usually settles at around 100Mb  and stays there, which I don't really see as being an issue for what is probably the most important application on my PC. Plus, its not like its a memory leak or anything, it's all being used!  It might seem quite hefty when there's only one or two tabs open, but IIRC, FF also scales better than most other [popular] browsers so when you get up to 15 or 20 tabs, it can even work out more efficient than e.g. Opera or IE.

Mine uses around 100mb of ram too but I think thats too much.  Other browsers don't use that much.

---

### Post by vexorian on 2007-06-23
You Can set firefox to go down to 35MB if you want, it is all about the CaChe option

> lso, the only time I've ever installed an icon theme, nothing changed in ANY of my apps, not just firefox. The GNOME Menu and Nautilus are the only things that changed. Every other app looks perfectly normal (the way it did originally). Perhaps every other program has this problem too

All apps inCluded with ubuntu are Compatible with the theme Changes, even OpenOffiCe, so no, you are wrong. And please take a look at the sCreenshot firefox just disagrees with the gtk theme.

---

### Post by macogw on 2007-06-23
> **vexorian said:**
> You Can set firefox to go down to 35MB if you want, it is all about the CaChe option



All apps inCluded with ubuntu are Compatible with the theme Changes, even OpenOffiCe, so no, you are wrong. And please take a look at the sCreenshot firefox just disagrees with the gtk theme.
My current icon theme is all grey-scale icons.  OpenOffice's icons are still in color; therefore, it's not working there.

I set the cache to 1MB and Firefox is using 76MB right now.  Often it's over 120MB, and I always keep cache set to 1MB (I think it wouldn't allow me to put 0MB).

---

### Post by BoyOfDestiny on 2007-06-23
> **vexorian said:**
> That's just senseless, this is not about one program integrating with another, it is about a program integrating with the whole desktop

If I understand what you want, I think firefox3 will offer it. I'm waiting for the beta to hit gutsy, but from one poster he (or she) mentioned that things like the command buttons and drop down button etc, will match the theme, which I know firefox 2 doesn't do (as I have a dark theme and custom colors...) Firefox itself does match it...

Here is a little screen cap of the submission here, you'll see the command buttons in the page vs the about box, also notice the background of firefox's about ignore my theme.

---

### Post by vexorian on 2007-06-23
> **BoyOfDestiny said:**
> If I understand what you want, I think firefox3 will offer it. I'm waiting for the beta to hit gutsy, but from one poster he (or she) mentioned that things like the command buttons and drop down button etc, will match the theme, which I know firefox 2 doesn't do (as I have a dark theme and custom colors...) Firefox itself does match it...

Here is a little screen cap of the submission here, you'll see the command buttons in the page vs the about box, also notice the background of firefox's about ignore my theme.
Guess I  Can only hope.

The whole memory issue is kind of lame, sinCe even with the default CaChe value i have not seen firefox go use more than 75MB and that's when I have plenty of tabs open, on average it is 45MB , I am not sure what Could be what Causes some of the Crazyngly huge values some people report.

Regarding openoffiCe, at least it follows the gtk theme...

---

### Post by BoyOfDestiny on 2007-06-23
> **vexorian said:**
> Guess I  Can only hope.

The whole memory issue is kind of lame, sinCe even with the default CaChe value i have not seen firefox go use more than 75MB and that's when I have plenty of tabs open, on average it is 45MB , I am not sure what Could be what Causes some of the Crazyngly huge values some people report.

I have no clue about the RAM stuff. I have a gig myself here, so as long as I'm not using the swap, I'm happy if it means fast browsing. Maybe if there are memory leaks or something, they are going to be, or are fixed in the next release.

One thing I'm hoping for from firefox 3 is a real page zoom, and one bug I think is fixed, since I use custom colors for pages (to make it easier to read for me) is that sites with menus, are transparent, a minor annoyance, since I run into it rarely, but I'll be glad to have that bug gone.

---

### Post by kamaboko on 2007-06-23
> **CheShA said:**
> Are you using any extensions?  I've had these kinds of problems myself and it has always been an extension that caused the problem, not FF itsself.  If so, try disabling them one at a time to see which one is causing the problem.

No, I'm not using any extensions.

---

### Post by vexorian on 2007-06-23
> **BoyOfDestiny said:**
> I have no clue about the RAM stuff. I have a gig myself here, so as long as I'm not using the swap, I'm happy if it means fast browsing. Maybe if there are memory leaks or something, they are going to be, or are fixed in the next release.

One thing I'm hoping for from firefox 3 is a real page zoom, and one bug I think is fixed, since I use custom colors for pages (to make it easier to read for me) is that sites with menus, are transparent, a minor annoyance, since I run into it rarely, but I'll be glad to have that bug gone.
zoom is probably not needed now that Compiz-fusion allows it in suCh a beautiful way...

---

### Post by BoyOfDestiny on 2007-06-23
> **vexorian said:**
> zoom is probably not needed now that Compiz-fusion allows it in suCh a beautiful way...

Very true, I've been using it (well beryl still, is it much improved in compiz fusion?) for youtube and such. 
Not everyone uses compositing though, the more flexibility we get the better I think. 
I like to use ctrl++ shortcut to boost the font sizes a bit, but some sites have fixed width columns... So it's big enough for me to read comfortably, but like a few words a column since the column stayed the same size, or one can just disable CSS etc... 

Not an issue on sites with fluid layouts, but it seems like "news" type sites love fixed width... I don't think I'm alone in being annoyed by it...

---

### Post by @trophy on 2007-06-23
> **juxtaposed said:**
> My big problem is the fact that it takes alot of RAM.

AMEN!!!!  Firefox is firmly in the clutches of feeping creaturism, and even though I still use it for everything, I'm getting mighty tired of "All your RAM are belong to me".  Sometimes I have Photoshop and Firefox open at the same time at work... then I click a button, go to lunch, come back, and see if it's done thinking yet... :-(

PS:  I don't have the screenshot here at home, but the other day at work FF was eating 210 of my 256 MB of RAM.  That's re-friggin-diculous!!!

---

### Post by blah blah blah on 2007-06-23
[https://addons.mozilla.org/en-US/firefox/search?q=gnome&status=4&show=50](https://addons.mozilla.org/en-US/firefox/search?q=gnome&status=4&show=50)

---

### Post by init1 on 2007-06-23
I don't have an issue with the RAM, CPU, or the rendering, but I don't like that it doesn't change fonts when I change the fonts in KDE.

---

### Post by Erunno on 2007-06-24
Firefox is an alien on the Open Desktop as the Mozilla Foundation doesn't make any effort to integrate it (and Thunderbird) with GNOME and KDE. There's no support for keyring/wallet, no awareness of global proxy settings, no theming support under GTK/Qt, no integration with standard RSS aggregators, no font awareness, no KDE file chooser dialog, etc. And these are just the issues which concern me, I bet there are tons of others if you ask other people with different usage patterns.

And worse: Firefox is slow. On my 2 GHz/ 1 GB RAM desktop computer I can actually *see* the delay when switching tabs. And it's not a case of feature overload either as Opera never had this kind of performance issues and is has way more features build-in out of the box. It simply comes down to sloppy programming in my oppinion.

There was a thread some months ago when someone dug up a page from the Mozilla Wiki which explained that the Linux port of Firefox 3 has the lowest priority (even Windows 20000 prioritized higher). I don't like the Mozilla Foundation. They are firmly rooted in the Windows world right now and only do a minimal effort to promote the Free Desktop.

---

### Post by crimesaucer on 2007-06-24
> **BoyOfDestiny said:**
> If I understand what you want, I think firefox3 will offer it. I'm waiting for the beta to hit gutsy, but from one poster he (or she) mentioned that things like the command buttons and drop down button etc, will match the theme, which I know firefox 2 doesn't do (as I have a dark theme and custom colors...) Firefox itself does match it...

Here is a little screen cap of the submission here, you'll see the command buttons in the page vs the about box, also notice the background of firefox's about ignore my theme.

Firefox 3 will have better gtk widgets in the page, instead of the box with shadows...

...as for everyone saying that Firefox 2.0.0.4 doesn't work with gtk-2.0...well, your just wrong.

Default Firefox uses your gtk-2.0 theme...but the moment you use a Firefox theme, it doesn't use it at all... not even the Human theme...in fact, out of all the themes that I tested for gtk-2.0 support, only the Tango theme worked with the gtkrc, and only in the menu bar, and nowhere else.

But the Default Firefox theme, the one it comes installed with, will change to any color or gradient color of your gtk-2.0 theme. I don't know if it can use a pix_map image because I've never tried it.



***This is Proof of Default Firefox using the gtk-2.0, all of these are changed in the gtkrc***:



....This was maybe my 5th or 6th theme attempt, pretty much just a default Xfce theme that came installed with xubuntu, just with different colors....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-8-11.png[/IMG]



.... Same theme with a gradient in the gtkrc....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-10-10.png[/IMG]


.... Same theme with no dividing lines and the same gradient written into the gtkrc....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-11-6.png[/IMG]


.... Same theme without the lines, but with a different way to draw the gradient in the gtkrc....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-12-7.png[/IMG]


....The newest way I made the same theme look. I just add a simple Firefox fix on the tab bar so the theme would look better and the xubuntu apps now are perfect....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-14-8.png[/IMG]


....another way to make it look...

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-15-12.png[/IMG]


The icons above were the Toolbar.png from Cylence:Obsidian, all it took to use them, or any other correct size/order .png, is to unpack a .jar file from one of your installed themes, then in Root, copy and paste the Toolbar.png that you want to use, into your /usr/lib/firefox/chrome/classic/skin/classic/browser directory. Just make sure it's the correct number, size, and order as the default .png...


... And as for icons, I agree with vexorian that it would be nice to have ubuntu icons that also worked in the Firefox toolbar, just like Epiphany does. 

But as for Epiphany, I only played around with it for a week, and I never liked their tab-bar and url/search box...and how it just missed all of the features that I like in Firefox.

As for RAM...I still don't see the problem...

and Opera may be stable (if you luck upon a web page written for it)...but all of the themes are really ugly and don't even use any gtk/qt and you can't even change the colors from those corny system colors that they give you...plus...it just is a hassle with userscripts and java/flash.


...and this is my latest Default Firefox 2 using gtk-2.0:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-1-10.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-5-10.png[/IMG]


Gradient drop down menus, gradient buttons, gradient menubar, gradient toolbar, gradient colored button rollovers, gradient color buttons when clicked, compact menubars and compact toolbars and compact icons...blue url box, blue search box, no dividing lines...all of this is from a Linux /gtk-2.0/gtkrc and the way it is written for the gtk widgets.

All of that applies to Firefox 2 and the default theme...so does the way it draws the colors of your tabs, and the default 3D tab-bar to blend with your main colors.

---

### Post by praxis22 on 2007-06-24
I was about to add another thread saying, "Damn firefox is fast on KDE" but I found this instead :)

I Switched from Gnome to KDE, and now firefox is a banshee, it's looks pretty drab, as indeed does much of KDE, but it absolutely flies. It's spookily fast when loading up my last tab set (33 tabs), and this is while my broadband speed is less than stellar on account of my crap ISP (BT, came with the flat, cant change it) :( 

Firefox is fairly heavily tweaked, and I have 27, (count them) extensions installed, but it's the kind of fast that has you wondering if you've stumbled into a parallel world, or somebody has installed a small nuclear reactor under the desk, etc. Firefox does a use a fair chunk of memory, granted, but that's why I bought a lot of it, (1Gb) 

Without wishing to invoke Godwin's law, I think people who bleat on about memory footprint need to "get a grip" and go buy more of it, or just tweak more.

Actually come to think of it, it could be that I recompiled the kernel... But Damn! It's fast.

---

### Post by Erunno on 2007-06-24
> **praxis22 said:**
> Without wishing to invoke Godwin's law, I think people who bleat on about memory footprint need to "get a grip" and go buy more of it, or just tweak more.

1. Since when users should be forced to tweak their browser to get an acceptable performance?

2. Other browsers like Opera prove already that it's possible to get acceptable performance without delving too deeply into application internals.

3. "Actually come to think of it, it could be that I recompiled the kernel... But Damn! It's fast." :roll:

---

### Post by clevin on 2007-06-24
firefox 3.0's recent nightly build already offering native widgets under GTK2

[IMG]http://img374.imageshack.us/img374/1268/screenshotev7.png[/IMG]

---

### Post by crimesaucer on 2007-06-24
> **clevin said:**
> firefox 3.0's recent nightly build already offering native widgets under GTK2

[IMG]http://img374.imageshack.us/img374/1268/screenshotev7.png[/IMG]

Look at that web page...that looks nice, in fact, the whole theme looks really good.

I want those scroll bars!

---

### Post by clevin on 2007-06-24
> **crimesaucer said:**
> Look at that web page...that looks nice, in fact, the whole theme looks really good.

I want those scroll bars!

i got it from gnome-look.org , the gtk2+ theme is titled "nimbus"

---

### Post by vexorian on 2007-06-25
well It does look like it is improving for 3.0 , but someone should really request a QT version, in KDE firefox really doesn't integrate well, the selected menu item was a big issue for me since I used dark color for the selected item background and anywhere else it used white font for the selected text, besides firefox.

Then there is the font on menu bar and many things that would improve for firefox in KDE. I know some(most maybe) KDE guys would prefer Konqueror but for some people firefox has a couple of useful features over Konqueror...

crimesaucer: bingo, all gradients and colors are supported, but pixmaps don't.  The gtk theme I am making based on a macOSX-like theme is full of pixmaps...

---

### Post by tk03759 on 2007-07-15
For anyone who says it integrates well with themes... I don't have any add ons or themes installed on firefox, but here's a pic of it's integration, versus that of nautilus (which demonstrates how any other application on my computer runs).

The biggest issue is the menu bar font color, which becomes unreadable. It also doesn't use the tool bar icons either though...
[URL="http://i9.tinypic.com/6fqoxup.png"]
http://i9.tinypic.com/6fqoxup.png[/URL]

---

### Post by kamaboko on 2007-07-15
As of late FF has been sucking wind.  It frequently crashes and goes on a CPU cycle fandango. It'll suck up all remaining CPU cycles and max it out to 100%.   I don't have anything added to it; stock, vanilla FF.

---

### Post by starcraft.man on 2007-07-15
> **kamaboko said:**
> As of late FF has been sucking wind.  It frequently crashes and goes on a CPU cycle fandango. It'll suck up all remaining CPU cycles and max it out to 100%.   I don't have anything added to it; stock, vanilla FF.

I dunno what your doing, I've never had any such difficulty... especially not maxing the cpu of my p4 just by browsing...

> **clevin said:**
> i got it from gnome-look.org , the gtk2+ theme is titled "nimbus"

That theme looks awesome... thanks for pointing it out. Oh and the nightly build looks good too, I'm gonna hold off till it's ready though I like surprises.

---

### Post by crimesaucer on 2007-07-15
> **tk03759 said:**
> For anyone who says it integrates well with themes... I don't have any add ons or themes installed on firefox, but here's a pic of it's integration, versus that of nautilus (which demonstrates how any other application on my computer runs).

The biggest issue is the menu bar font color, which becomes unreadable. It also doesn't use the tool bar icons either though...
[URL="http://i9.tinypic.com/6fqoxup.png"]
http://i9.tinypic.com/6fqoxup.png[/URL]


Firefox looks like it is using your theme. The only thing that looks wrong is the menubar font, which will mean your menus are probably screwed up also. 


All the other colors look correct (like the nautilus colors). And it seems to be using your menubar which looks like a glossy Vista image.


Icons won't be used unless you do it yourself by creating a Toolbar.png


In a regular /gtk-2.0/gtkrc, the fg[NORMAL] will change the color of the Firefox menubar fonts. It looks like your other app is using it correctly with the white text in the nautilus menubar, but maybe it's Firefox using a pixmap image for your theme's menubar that might have made things weird, just like vexorian had said in his post about Firefox and gtk-2.0 themes using pixmap images. 


Can you post your theme's gtkrc?


You could also try a bit of userChrome.css to fix that. Just go to the Mozilla Forum's "Themes" section and ask for help there: [http://forums.mozillazine.org/viewforum.php?f=18](http://forums.mozillazine.org/viewforum.php?f=18)



As for the memory leak, I watch my mem stats on my Conky for Swiftweasel/Swiftfox/Firefox and I only see them increase from 18% to maybe 23%...and I leave it on for days sometimes...and if I restart it, then it's back to the low normal....I also only have 512MB ram, and when I monitor my total memory usage with this command:

```
free -m
```

...then I still have free and cached mem...and my Swap file is only using 1%...it takes me running a few different GIMP projects (like 3 or more on different workspaces), a media player, and a few other open apps to bounce me into my swap file.





Now, for browser quickness, I recommend Swiftweasel: [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)

It is optimized for your processor. 



And...I find that when I fill up my 76.5MB Cache, what I do is press "shift+ctrl+delete" and just erase my Cache. Make sure your "about : config" setting of "browser.cache.disk.parent_directory" is pointed to your profile's Cache folder, in: /home/folder/.mozilla/firefox/yourprofile.default/Cache

or /.mozilla/swiftweasel/yourprofile.default/Cache


as for Firefox using a gtk-2.0 theme, this is my latest one: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-46-9.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-46-9.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-46-8.png[/IMG]

---

### Post by Old Pink on 2007-07-15
As I've said [here](http://www.mbhoy.com/05-07-2007/gran-paradiso-alpha-6) even the current build of Alpha Firefox 3 is stable and much more effective in memory management. :D

---

### Post by prizrak on 2007-07-15
FF's RAM usage issue comes from being a completely standalone and self contained application. It doesn't integrate well into the OS and takes up alot of the resources it really shouldn't be. If I'm running Gnome I don't want to load another framework on top of that, I got GTK running already.

Mozilla has promised to release the engine as a standalone for years and never have.

---

### Post by Old Pink on 2007-07-15
> **prizrak said:**
> FF's RAM usage issue comes from being a completely standalone and self contained application. It doesn't integrate well into the OS and takes up alot of the resources it really shouldn't be. If I'm running Gnome I don't want to load another framework on top of that, I got GTK running already.

Mozilla has promised to release the engine as a standalone for years and never have.Pull it out of the firefox source yourself? ;)

---

### Post by starcraft.man on 2007-07-15
> **clevin said:**
> firefox 3.0's recent nightly build already offering native widgets under GTK2

[IMG]http://img374.imageshack.us/img374/1268/screenshotev7.png[/IMG]

Can anyone point me to the right place for this theme? I went to [Nimbus on gnomelook]("http://www.gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755") (as clevin said) but it seems the only thing that's similar is the scroll bar (windows certainly look completely different)... I really would like it (one clevin got). Also oddly enough the Feisty links for Nimbus on that page are dead... dunno why.

---

### Post by prizrak on 2007-07-16
> **Old Pink said:**
> Pull it out of the firefox source yourself? ;)

Doesn't seem to be possible, not sure why. Epiphany has to have Firefox installed and so does Yelp to use it's engine. I'm sure the devs would have done it if they could.

---

