---
title: "Upgrade to new 13.10 really makes me sad"
date: 2013-12-26
forum: Ubuntu, Linux and OS Chat
---

### Post by gaxi on 2013-12-26
After working with Ubuntu for many years now on several computers, I really could recommend it as a great replacement for the "common", most sold operating systems.

My newly installed 13.10 lets my hair get gray, I cannot recommend this system to my colleagues any more, because it really changed it's behavior - but not get better. It is not easy to change over from ie Windows.

- Nautilus:
. Status bar has disappeard. How can I _easily_ find out, how much space is left on my disk or on my SD-card?
. Simply starting to type in a directory now starts a "long"-lasting search in all subfolders. I am used to start typing the first three characters and immediately push Enter to change the directory or open a file. Now I have to wait a second the search has started/finished. 
. I cannot find, how to set a bookmark on a local directory. This only seems to be possible on connected/mounted external shares like ssh or smb-connections.
. In the past I could click to a directory and "Open with...." a program like VLC. This possibility totally has disappeared.
. Backspace in Nautilus does not go up one directory any more. I have to hack config-files to reenable this most common shortcut in all systems. (gtk_accel_path "<Actions>/ShellActions/Up" "BackSpace")

- Restart:
. When I select "Restart" from the menu appearing from the upper right gear and press Enter to restart, the computer shuts down, because Shutdown is selected by default, instead of Restart.

- Removing that music-search-stuff
Horribly complicated to remove all that ad-stuff. My dash was so slow and unusable with all that enabled. I understand that there is a need to earn money, but this really was a pain.

It does not seem, anyone really has tested this system. And it seems, some managers without any idea how to work on a computer have decided, how the system should behave. 
Why did this all change after all? 

GaXi ;(

---

### Post by coffeecat on 2013-12-26
The Ubuntu+1 forum is for the development version (currently 14.04) and this thread sounds more like a discussion thread than a request for help. Therefore...

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by craig10x on 2013-12-26
To remove the amazon ad stuff, all you had to do was go to privacy section of system settings and hit the off button for online searches, then all you get in the search is the stuff on your system...takes 5 seconds to do...what is complicated about that? 

I didn't like it either because i don't like the clutter so i turned mine off...but if not for that, i would have left it on since canonical gets some revenue from it to help development...so instead i send them an occasional donation...

Certainly, Unity isn't difficult to use...it is just a dock, really...lots of windows users convert to mac and that uses a dock and you don't find them complaining that it is difficult to use...

---

### Post by deadflowr on 2013-12-26
> [COLOR=#000000]Horribly complicated to remove all that ad-stuff. My dash was so slow and unusable with all that enabled. I understand that there is a need to earn money, but this really was a pain.[/COLOR]

Open dash one time, type privacy click enter find online results in search tab turn off.
Not that complicated.

---

### Post by monkeybrain20122 on 2013-12-26
Well, everything you dislike about the new nautilus is the result of upstream changes by gnome, which has nothing to do with Canonical.
There is a recent thread on this [http://ubuntuforums.org/showthread.php?t=2191936](http://ubuntuforums.org/showthread.php?t=2191936)

You can restore some old behaviour of Nautilus with a ppa
[https://launchpad.net/~mc3man/+archive/sacy-tests](https://launchpad.net/~mc3man/+archive/sacy-tests)

Or you may try to replace it with nemo
[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

---

### Post by rrnbtter on 2013-12-26
Greetings,
This thread was moved from the ubuntu +1 area as not a dev topic but acutally 13.10 is part of the development stream as not LTS. I would save my complaints until the 14.04LTS is released. That being said Nautilus has been default in every Ubuntu version that I have ever used and it hasn't been a problem. Microsoft was and remains the champion of crappy utilities. Back in the old days DR Dos had single pass disk copy long before MS DOS picked it up in version 6 and it only begins there. Nautilus isn't Ubuntu, it is a utility which defaults in Ubuntu. It is actually part of the 80% of the Ubuntu install that is NOT Ubuntu. Regarding the Shut Down defaulting to Restart, I agree that the Windows users will be perplexed at the need to make a choice.  In addition I find it interesting that these complaint threads often claim to represent  the need of every Windows user that will ever try Linux. My guess is that most will take it the way they find it and think it's normal.  

PS. Please don't take my first sentence as a challenge as to the moving of this thread. I was only making the point that 13.10 went final as an incomplete set of objectives. It will not become 14.04LTS even with updates.

---

### Post by grahammechanical on 2013-12-26
Both the Gnome developers with Gnome 3 desktop environment and Gnome 3 shell and the UBuntu developers with the Unity user interface have been on this path for about two years. I cannot understand how some people are surprised at the changes being made. Ubuntu 13.10 is not that much different in looks from Ubuntu 12.04. And, as has, already been pointed out a lot of the differences are do to changes being put through by upstream developers. But people criticise Ubuntu because it no longer looks similar to an old Microsoft OS.

And this is a completely uninformed false accusation that is an insult to all those who develop Linux and often do it in their own time and without pay.

> [COLOR=#000000]It does not seem, anyone really has tested this system. And it seems, some managers without any idea how to work on a computer have decided, how the system should behave. [/COLOR]
[COLOR=#000000]Why did this all change after all? [/COLOR]

Some people just do not deserve Linux. A link to Usability Testing of Ubuntu.

[http://design.canonical.com/2012/03/about-usability-testing-recruiting/](http://design.canonical.com/2012/03/about-usability-testing-recruiting/)

---

### Post by Jonor on 2013-12-26
It may technically be a U-turn but after the third attempt at installing a stable 13.10 i reverted to 12.04 
which as a relative newcomer i had never tried and was surprisingly impressed with it.
Your colleagues may like the idea of being able to stick with it for several more years rather than just a few months.

---

### Post by ventrical on 2013-12-26
I still have several installs of Saucy on most of my machines and also have installed it on other machines for other end_users. Saucy runs fine on my SandyBridge and non-SandyBridge systems. Some older nVidia cards are obsoleted but the money I would pay to have MS VLKs now go on upgrading to newer  (even used) hardware at a fraction of the cost. Saucy/ Raring etc .. (and Trusty) has made my computer not only economically feasable but also profitable in several different ways. One of those ways is that my PC's actually best themselves  (run at a higherperformance level) than they would if using other commercial types.

As for nautilus problems  .. there is always PC_Filemanager in the SC. It puts the olde Ubuntu back into the new Ubuntu. Why would I complain over that?

  As for durability and testing, we at U+ 1 and q&a_tracker work as dilligently as we possibly can, for free and to the best of our abilites. Ubuntu (of any cycle) is not just an experience .. it is an endeavour.  In U+1 I have freedom to test and experiement all different sorts of software without anyone breathing down my neck.  How can anyone be sad knowing this?  Not only do we have the freedom to endeavour, we have also the freedom to discover, share and learn new technologies and contribute our own personal ideas, thoughts and frameworks.

  As I always say .. when I see messages such as these .. go over to that other commercial OS and run 35 tabs on the default browser uninterrupted. don't tell me. Show me.

  ---

  I too lamented the falling away of Unity 2D but now, with the Uniy8 webapp emulator I can see a greater version of itself (unity2d that is) just upon the horizon  and even on legacy machines with older cards.

Regards..

---

### Post by gaxi on 2013-12-27
Thank you, I could not find this information on the web. 
So, to disable Amazon and music search, go to System Settings/Security and Privacy/Search and set "Include online search results" to off.

---

### Post by gaxi on 2013-12-27
I am sorry, I did not want to insult someone, I now am aware of the upstream-problematics of Nautilus. 
I tried Nemo already but it was unstable unfortunately. 

I really appreciate Ubuntu and Linux, but stepping from 12.04 to 13.10 did not bring an advantage. Some things changed, no problem.  
For me, essential things are missing or were unconfigured. I suppose all of you are using backspace to move up one directory. 
This is what distributions are for, I thought. pre-configuring common features and being consistent in some extent.

So many thanks to all who are able to contribute and work on making things greater and better!

Sorry again, GaXi

---

### Post by Morbius1 on 2013-12-27
Your sadness comes from the shock of going from 12.04 to 14.04 without getting smaller sadness increments along the way. I have these non-LTS 9-month releases installed in a VBox guest so the shock isn't so great.

By doing this my decision to go with Xubuntu was easier.

---

### Post by mc4man on 2013-12-27
> **gaxi said:**
> Thank you, I could not find this information on the web. 
So, to disable Amazon and music search, go to System Settings/Security and Privacy/Search and set "Include online search results" to off.

That will disable all online searches (if that's what you want..

Otherwise you can do many on an individual basis, takes a min or so
Open Dash > Applications
Expand the "Filter results", enable "Dash plugins"

In the Dash plugins results - 
Starting with the 1st one,  left click on
From there you can disable or enable that scope
Using the > you can go thru all listed & disable the ones you don't want

(you can also blacklist scopes in gsettings but the above usually suffices

---

### Post by craig10x on 2013-12-27
Right...as mc4man mentioned...you can turn off those things selectively if you prefer (doing what he outlined) or if you prefer to just shut off all online searches in the dash search then just go to privacy settings and turn off the "include online search results"...then there is no searching online at all...only the stuff on your system (apps, files, etc...) ;)

---

### Post by monkeybrain20122 on 2013-12-27
> **Morbius1 said:**
> Your sadness comes from the shock of going from 12.04 to 14.04 without getting smaller sadness increments along the way. I have these non-LTS 9-month releases installed in a VBox guest so the shock isn't so great.

By doing this my decision to go with Xubuntu was easier.

Now this I can't undrestand because even when Nautilus has lost some of its functionalities it is still much better than thunar, which never has those features that are lost in Nautilus to begin with, and even less than what it has now.

---

### Post by pqwoerituytrueiwoq on 2013-12-27
> **gaxi said:**
> 
- Nautilus:
. Status bar has disappeard. How can I _easily_ find out, how much space is left on my disk or on my SD-card?
. Simply starting to type in a directory now starts a "long"-lasting search in all subfolders. I am used to start typing the first three characters and immediately push Enter to change the directory or open a file. Now I have to wait a second the search has started/finished. 
. I cannot find, how to set a bookmark on a local directory. This only seems to be possible on connected/mounted external shares like ssh or smb-connections.
. In the past I could click to a directory and "Open with...." a program like VLC. This possibility totally has disappeared.
. Backspace in Nautilus does not go up one directory any more. I have to hack config-files to reenable this most common shortcut in all systems. (gtk_accel_path "<Actions>/ShellActions/Up" "BackSpace")


try using nemo
[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

---

### Post by Toz on 2013-12-27
> **monkeybrain20122 said:**
> Now this I can't undrestand because even when Nautilus has lost some of its functionalities it is still much better than thunar, which never has those features that are lost in Nautilus to begin with, and even less than what it has now.
Thunar's purpose was never to be an all-inclusive, functionally-saturated file manager. From [http://docs.xfce.org/xfce/thunar/start]("http://docs.xfce.org/xfce/thunar/start"):
> Thunar is a new modern file manager for the Xfce Desktop Environment. Thunar has been designed from the ground up to be fast and easy-to-use. Its user interface is clean and intuitive, and does not include any confusing or useless options by default. Thunar is fast and responsive with a good start up time and folder load time. 

That being said, from your initial post:
> - Nautilus:
. Status bar has disappeard. How can I _easily_ find out, how much space is left on my disk or on my SD-card?
Thunar has a status bar that displays space used and Free space.
> . Simply starting to type in a directory now starts a "long"-lasting search in all subfolders. I am used to start typing the first three characters and immediately push Enter to change the directory or open a file. Now I have to wait a second the search has started/finished.
Works in thunar.
> . I cannot find, how to set a bookmark on a local directory. This only seems to be possible on connected/mounted external shares like ssh or smb-connections.
Thunar supports bookmarks.
> . In the past I could click to a directory and "Open with...." a program like VLC. This possibility totally has disappeared.
Functionality can be added using [Custom Actions]("http://docs.xfce.org/xfce/thunar/custom-actions").
> . Backspace in Nautilus does not go up one directory any more. I have to hack config-files to reenable this most common shortcut in all systems. (gtk_accel_path "<Actions>/ShellActions/Up" "BackSpace")
Works in thunar.

"Better" is a subjective term.

---

### Post by monkeybrain20122 on 2013-12-27
> **Toz said:**
> 

Thunar has a status bar that displays space used and Free space. 

Well I never really noticed that you can use the status bar to display used and free space, I always right click and choose "Properties", that still works.



> Thunar supports bookmarks.
As does Nautilus, but the option is now in the "File" menu which is on the top panel. It can be easily missed and it would disappear if you remove the global menu. I think that is bad design.

> 
 In the past I could click to a directory and "Open with...." a program like VLC. This possibility totally has disappeared.                      

Still works, right click > Properties > Open With
(**Edited:** Oh I see he is talking about clicking a directory, not a file. The function is restored in mc4man's ppa linked to in my first post)

---

### Post by mc4man on 2013-12-27
> **gaxi said:**
> After working with Ubuntu for many years now on several computers, I really could recommend it as a great replacement for the "common", most sold operating systems.

My newly installed 13.10 lets my hair get gray, I cannot recommend this system to my colleagues any more, because it really changed it's behavior - but not get better. It is not easy to change over from ie Windows.

- Nautilus:
. Status bar has disappeard. How can I _easily_ find out, how much space is left on my disk or on my SD-card?
. Simply starting to type in a directory now starts a "long"-lasting search in all subfolders. I am used to start typing the first three characters and immediately push Enter to change the directory or open a file. Now I have to wait a second the search has started/finished. 
. I cannot find, how to set a bookmark on a local directory. This only seems to be possible on connected/mounted external shares like ssh or smb-connections.
. In the past I could click to a directory and "Open with...." a program like VLC. This possibility totally has disappeared.
. Backspace in Nautilus does not go up one directory any more. I have to hack config-files to reenable this most common shortcut in all systems. (gtk_accel_path "<Actions>/ShellActions/Up" "BackSpace")
(

You can simply r. click on any mounted volume in the sidebar > properties
 - for your current volume open "Computer" & right click on the breadcrumb > properties

Personally I like nautilus's seach over the read-ahead of past, there is a possibility it, (interactive/readahead search),  will be enabled in 14.04's nautilus as an option

You can bookmark any directory by opening that directory > cog menu > Bookmark this location or ctrl+d on keyboard

[open with on dir. has been gone for a while]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254"), not enough complaints, am going to again propose it's returned in 14.04, otherwise will be in a ppa

Backspace to go up is not too good if one uses nautilus's search or even the 'new' readahead. If enabled,  when backspace is used on a search term nautilus will go up a dir instead of backspacing on the search term
The current kb is alt+up
(an up button is easily added to nautilus though needs to be done in source

---

### Post by Tar_Ni on 2013-12-29
Have to agree, I made a clean install after formating of Ubuntu 13.10 and it was horribly buggy. Seriously I wouldn't recommend it to anyone. 12.04 is a much safer bet and works pretty well. I hope the new LTS will be free of these horrible bugs.

---

### Post by craig10x on 2013-12-30
> **Tar_Ni said:**
> Have to agree, I made a clean install after formating of Ubuntu 13.10 and it was horribly buggy. Seriously I wouldn't recommend it to anyone. 12.04 is a much safer bet and works pretty well. I hope the new LTS will be free of these horrible bugs.


Sorry to hear that...on my hardware, 13.10 was super smooth and stable...i am in 14.04 development now and even though it's still Alpha it's running darn good as well (with a few glitches that no doubt will get fixed along the way)...

---

### Post by Tar_Ni on 2013-12-30
I liked the look of it though.

First thing I do, I tried to change the wallpaper and it crashed right there. After that all was buggy and slow, error messages to report bugs kept appearing. It was unbearable really. Never had such problem with Ubuntu 12.04.

Aparently I was not alone in this situation for exemple:

[http://ubuntuforums.org/showthread.php?t=2185912](http://ubuntuforums.org/showthread.php?t=2185912)

[http://www.securitronlinux.com/bejiitaswrath/ubuntu-13-10-an-unstable-and-hopelessly-useless-mess-what-the-hell-is-going-on/](http://www.securitronlinux.com/bejiitaswrath/ubuntu-13-10-an-unstable-and-hopelessly-useless-mess-what-the-hell-is-going-on/)

---

### Post by linuxyogi on 2014-01-14
I was using Xubuntu 12.04. Problem was I getting frequent crashes. 3 things usually crashed on a regular basis. First (I dont remember the name) was the service which is responsible for displaying thumbnails in thunar and the 2nd was thunar itself and finally the Ubuntu Software Center.

I am using Mint 16 Mate which is based on 13.10 and its super stable.

I will try the next LTS of Xubuntu after its release in virtualbox and if I find it stable I will install it.

---

