---
title: "GUI Fan Club – for a Terminal-free Ubuntu experience ! (Only if you want it…)"
date: 2008-08-23
forum: Tutorials
---

### Post by 2CV67 on 2008-08-23
[I][EDIT 7 Feb 2012:  I notice that some of the detail content below is getting a bit out-of-date now.
Since I have dropped out of mainstream Unity & Gnome to play with Lubuntu, I am not in a position to keep track of GUI Tips & Needs for the popular desktops.
So I guess this thread may become somewhat frozen, unless anybody else wants to take over...][/I]

OK & firstly, I really do fully understand that Terminal is a wonderfully powerful, flexible & efficient interface for young, fit, regular, proficient users, really I do!
I am not trying to eliminate it.
I am not trying to suggest that anybody who likes it should consider stopping.
I know I could get lynched for even thinking that sort of thing here! ;)

None the less, many casual users, much of the time, find Terminal daunting, obscure, demanding, dangerous and generally a step back to the dark ages of DOS after years of lazy Mac or Windows mouse clicking.

My personal view is that the undoubted efficiency, in the rare case when I happen to know exactly the right short command & type it right first time (& I do that voluntarily sometimes for stuff I need regularly) is completely offset by the 99% of cases when I have to search for the right complicated command, cross check that it really will do what I want in my particular circumstance, then either type it meticulously & cross-check my input, or look up a list & copy/paste it.
By that time I could usually have clicked my way to where I want to get with a good GUI.
Put it down to age, if you like.
I also happen to have a deep-rooted conviction that any user interface which requires substantial, error-free keyboard input is fundamentally a bad interface, especially for the general public.
A keyboard is quite suitable for writing, because reading is error-tolerant. Computer OSs are not.
As one illustration, I never, ever, try to input a website address directly as &#8220;[http://etcetcetc.org/nanana&#8221;](http://etcetcetc.org/nanana&#8221;) but I always Google something like &#8220;etcetc&#8221; & click on the best offering.
I also have a big bank of well-sorted bookmarks, so most of the time I can get to a regular site in 2 clicks anyway.
So, basically, I prefer GUI methods wherever possible.

Let me repeat, I am not trying to persuade anybody to hate Terminal.

What I WOULD like to do, is to help anybody who, like me, prefers the GUI way of doing things, to be able to find the many existing tools, tips & methods  as easily as possible.
Reading all the available Ubunu/Linux guides doesn&#8217;t seem to do this (or maybe I have not found the right guide yet - there is always one more stone to unturn&#8230;).
As a later step, it might be feasible to push for development of suitable GUI tools for some tasks which enough users ask for.

A probable side effect would be that less newbies would give up on Linux, so the Linux community would grow quicker, so it would have more clout, so manufacturers would take more account of it, and so on&#8230;
We need this.

Although I have had these general feelings for a very long time, what prompts me to publish this post now is some serendipitous  experiences I just had on this forum.  :)
1. Looking for a simple way to act as root when I need to, somebody mentioned I could: > Go into Synaptic and install the package nautilus-gksu. Log out, and log back in again. Now whenever you right-click a file or folder, you will have the option to "Open as Administrator". Man, this is heaven !

2. Wanting to get my boot process as I like it (Default to XP for the family, 3-second screen for selecting Ubuntu for me, limit displayed kernels to current & previous without having to wipe some out manually after every update, show scripts, etc) I had been having to revise boot/grub/menu.lst file with root permission & with potentially disastrous consequences at the slip of a fingertip. I did get all that to work, but not first time, and the several times when booting failed completely were heart-stoppers!
Then I discovered I could go into Synaptic and install the package startupmanager. Now I can make all the above adjustments in GUI, simply, instantly and, above all, safely. I don&#8217;t need to remember anything about becoming root, locating menu.lst, splash, quiet, #,##,### etc etc. I just click the options I want from those on offer, and change them as often as I want.
Heaven again!

So how to proceed?

I invite any GUI enthusiasts to contribute to this thread, with all the available GUI tools, tips & methods they have found useful.
Also with any tasks they particularly would like to find GUI methods for.
Beyond that, we would have to see how to get the accumulated information tidied up & kept obviously available somewhere, but we are not there yet!

To start the ball rolling, here are a few suggestions:
I am NOT an expert, so some of what I say below may be rubbish. Use at your own risk.
Constructive correction is welcome!

If you need trouble-shooting or help on any particular item, it would probably be better not to use this thread, thanks.

_1. GUI Tool: Synaptic Package Manager  (I really suppose everybody knows this one!)_
How to see all (well most) available packages you can add to Ubuntu, and install them in a couple of clicks, with all dependencies & conflicts looked after automatically.
Uninstall & reinstall just as easily.
Wonderful!
Find it at: System > Administration > Synaptic Package Manager.

_2. GUI Tip: Rapid scrolling in Synaptic Package Manager_
It is a long, delicate & frustrating business in Synaptic, to try to scroll to a particular package you know the name of, because there are 25000 packages in the list.
The wheel is too slow & the scroll bar too fast...
Instead: click on any item in the list, then start typing the name of your package
As soon as you enter, say "s", it takes you to the top of the "s" items.
If you then enter "c" you get to the top of the "sc" items.
If you then enter "r" you get to the "scr" items.
Etc.
2 or 3 letters are usually enough to get within easy wheel-scrolling distance.

_3. GUI Tool: nautilus-gksu_
Allows you to open & modify files with root priviledges by a simple right-click on the file.
Find it in Synaptic.

_4. GUI Tool: startupmanager_ ***[EDIT Feb 2012 - Startup Manager no longer developed - Try Grub Customizer]***
Get your boot process exactly how you want it.
Select which OS is default.
Adjust timeout on selection screen.
Decide if you want scripts or not.
Keep as many or as few kernels as you want.
Change it as often as you want.
Find it in Synaptic.

_5. GUI Tip: Bookmarks in file sytem_
Instant access to any folder you regularly use, without having to drill down to it &#8211; even in another OS zone.
Find it at:
To set bookmark &#8211; navigate to folder using File browser, then Bookmarks > Add Bookmark.
To use bookmarks &#8211; Places > Bookmarks

_6. GUI Tip: middle click copy/paste_
If Control+C > Control+V is too much for you, try this (once you've tried it, you won't go back) :
Select what you want to copy.
Move cursor to where you want to paste.
Middle click &#8211; that's all!
Don't tell anybody, but it even works in Terminal, where you previously had to remember to use Control+Shift+V or something like that.
There are some limitations. Google for more details.
You can even do this in Windows, using DragKing v1.3 (see post #27).

_7. GUI Tool: Ping_
Helps in checking networks.
Find it at: System > Administration > Network Tools > Ping
[U]
8. GUI Tool: Firefox Add-on: Scrapbook[/U]
Bookmarks save the address, but using them brings you to the latest updated page, or maybe nothing if the page has moved on.
Scrapbook allows you to save the page exactly as it is now, then look at it whenever you like as a Firefox page.
Find it in Synaptic.

_9. GUI Tool: Firefox Add-on: ScreenGrab!_
Make screenshots of any rectangular portion of any page in Firefox.
Save as .png image.
Note, you choose Screengrab! first, then make your rectangular selection afterwards &#8211; somewhat counter-intuitive!
Find it at: Firefox > Tools > Add-ons > Get Add-ons > &#8220;Screengrab!&#8221; > Enter > Add to Firefox

_10. GUI Tool: sbackup_
Easily backs up what I suppose are a good selection of important files to your Ext HD (or whatever).
Numerous options. 
Can restore individual documents or whole directories, but could be tedious from incremental backups...
I just do a weekly full backup with sbackup & use Grsync for frequent backups of  /home but experts may disagree!
Find it in Synaptic.

_11.GUI Tool: Grsync_
Easily backs up whatever you want to your ExtHD.
Maintains a single synchronised copy of files so it's easy to find any documents in their latest state.
Personally, I use this for my /home directory & sbackup for the wierd stuff, but experts may suggest better strategies! 
Find it in Synaptic.

_12.GUI Tip: Put ikons on the panel (top of screen) for instant access to whatever you want._
Like Terminal (!), Screenshot, Grsync, Synaptic, OOo Word Processor, Tomboy notes.....
Find it, for example: Applications > Accessories > Calculator > Right click on ikon > Add this launcher to panel.
Or: right click on panel > Add to panel > then follow options



..................................

Missing GUI items - What would I like to find GUI tools/methods/tips for?

_a. MD5 checksum generation & checking._ SOLVED see item 22
Like the simple md5.exe I have added in XP.

_b. More obvious rapid scrolling in Synaptic Package Manager (& others)._
Without needing to know/remember to click on some odd folder first.

_c. Real-time Wi-Fi signal strength indicator/meter_
Why do I have to optimise my aerial position in XP (with signal strength gauge) instead of in Ubuntu?

_d. Setting-up & fault-finding in Networking & Wi-Fi_
I suppose that is a big one &#8211; I am not holding my breath!

Oh & finally, PLEASE do not use this thread to try to convince me that I should learn to love Terminal because it is great & fast & efficient & smart & powerful &&#8230;
I know all that, as I said at the beginning.
By all means, start your own thread on that subject if you want to! ;)

Thanks!

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

Edit: following items pulled up to first post from subsequent posts.
Thanks to those contributors!

_**13.GUI Tip: Put icon on the panel for instant navigation as root**_, so you can modify files with root permissions (post#3 & 4 Thanks meindian523)
Right click on panel.
Add to Panel > Custom Application Launcher > Add
Name "root" or whatever you want
Command "gksudo nautilus"
"OK"
Should provide a new icon on panel.
Click icon.
Insert your own password (not root password).
Should open navigation window "root &#8211; file browser"

_**14. GUI Tool: gnome-do**_ (post#5 Thanks ByteJuggler)
Looks like you can do anything in a couple of clicks!
Not tried it yet.
See [http://do.davebsd.com/]("http://do.davebsd.com/") and watch some of the screencasts! 
Find it in Synaptic.

_**15. GUI Tool: gnome-schedule**_ - for for configuring a users' cron (automatic jobs) (post#15 Thanks Killerkiwi)
Find it in Synaptic.

_**16. GUI Tool: rapache**_ - for configuring apache (post#15 Thanks Killerkiwi)
Find it at: [https://edge.launchpad.net/rapache](https://edge.launchpad.net/rapache)

_**17. GUI Tool: nautilus-actions**_ - add context menu items to nautilus (post#15 Thanks Killerkiwi)
Find it in Synaptic.

_**18. GUI Tool: quicksynergy**_ - set up a synergy keyboard / mouse connection (post#15 Thanks Killerkiwi)
Find it in Synaptic.

_**19. GUI Tool: system-config-samba**_ - creating, modifying, and deleting samba shares and users. (post#19 Thanks mgmiller)
Find it in Synaptic.

**_20. GUI Tool: pysdm_** - create mount points for drives (post#19 Thanks mgmiller)
Find it in Synaptic.

_**21. GUI Tool: fusion-icon**_ - easily switch between metacity, compiz and beryl (if it's installed) and also quickly get to the settings dialogs for everything (post#19 Thanks mgmiller)
Find it in Synaptic.
Run it from Applications > System tools > Compiz Fusion Icon
It will put an icon in the top panel, right click it see choices.

**_22. GUI Tool: Make md5_** - generate md5 checksums by right-click on file (post#24 Thanks itssaurav2004)
Find it at: [http://g-scripts.sourceforge.net/cat-fileproc.php](http://g-scripts.sourceforge.net/cat-fileproc.php) > Make_md5
See post#26 for details

**_23. GUI Tips: setting up your sound so you never need to use a terminal_**  (post#33 Thanks Markbuntu)
Find it at: [http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")

**_24. GUI Tool: Remastersys_** &#8211; easily make a live CD/DVD of your own complete Ubuntu set-up (Thanks newbee70)
You can then install it on any other PC &/or keep it as a backup with all your data & settings.
Find information: [http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)
That is a GUI tutorial which includes how to add the Software Source to Synaptic.

**_25. GUI Tips: listing and removing orphaned packages_** (post #35 thanks mgmiller)
Best see that post for details.

**_26. GUI Tools: Disk-Manager & PySDM & MountManager_** - file system configuration, mounting, shares, etc without fstab intervention (posts #36 & #37 Thanks KillerKiwi)
Find them in Synaptic
Run them from System > Administartion > XXXX
Warning: Probably not for total noobies?
See links in posts #36 & #37 for more info.

***_e. GUI Need: Something to rename (label) USB drives & other partitions_***  - more simply that using GParted.
Windows Explorer does it by:  Right Click > Rename > XXXX
That is a good benchmark!
***[EDIT Feb 2012: Accessories > Disk Utility > Click on Drive > Unmount Volume > Edit File System Label]***

**_27. GUI Tools: Ubuntu Tweak_** - for tweaking system settings and adding items quickly. (post#40 thanks Twitch6000)
 [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

**_28. GUI Tools: Control Center_** - quick GUI access to just about everything. (post#40 thanks Twitch6000)
Find it in: System > Control Center
Sorry, I don't remember if it's there initially or if you need to put it there...

**_29. GUI Tips: GIMP - Screenshots, Missing Toolbox menu & How to minimize GIMP Toolbox window._** (post#41)

**_30. GUI Tools: Shutter (aka Gscrot)_** - very flexible screenshot tool with great edit facility (post #43 thanks jolx).
Not for noobies due to installation via PPA & no help yet.

**_31. GUI Tips: GUI Launcher Icons - change, find, make your own..._** (post #44)

***_f.  GUI Need: Control over frequency & timing of disk checks at start-up._*** (post #55)

***_g. GUI Need: For Setting System-Wide or Printer-Wide Default Papersize._*** ((post #56)

---

### Post by puurokauha on 2008-08-23
I was wondering how to copy text in liferea, and that nautilus-gksu is really useful.
Thanks!

---

### Post by meindian523 on 2008-08-23
Correspondingly,you could input gksudo nautilus and everything would be well with the world.Please move to Recurring Discussions.

---

### Post by 2CV67 on 2008-09-08
> **meindian523 said:**
> Correspondingly,you could input gksudo nautilus and everything would be well with the world.

Yes, if you can remember it's gksudo nautilus and not sudogknautilus or any of the other millions of combinations possible, and then type it right first time, which I can't...
Of course you can also keep a list of that stuff ready for copy-pasting (I do...) but that is not the way I want my Ubuntu.
I am not suggesting you do anything different, just allow me (& anybody else) to try to do what we want.

Profiting from meindian523's contribution, for anybody who would like to be able to navigate as root in one click, then you could try adding a root-file-browser icon as follows (you don't have to!).

_13.GUI Tip: Put icon on the panel for instant navigation as root,so you can modify files with root permissions_
Right click on panel.
Select "Add to Panel" "Custom Application Launcher" "Add"
Name "root" or whatever you want
Command "gksudo nautilus"
"OK"
Should provide a new icon on panel.
Click icon.
Insert your own password (not root password).
Should open navigation window "root – file browser"

Other ideas (for improving the GUI experience, I mean)?

---

### Post by ByteJuggler on 2008-09-08
As somewhat of a compromise between a "blind" command prompt and the confines of a pre-canned GUI with buttons etc, I suggest you try "gnome-do".  It's like GUI versoin of "command-line completion" on steroids.  Very very useful/fast especially once you're used to it.  A bit like your google analogy - type a few letters or a shortcut acronym for something and Gnome-do will suggest the most appropriate completion/action, but there's a lot more to it than just that.  See [**_here_**]("http://do.davebsd.com/") and watch some of the screencasts!

---

### Post by Flimm on 2008-09-08
I've always thought that requiring Ubuntu users to use the terminal for certain tasks was against the Ubuntu philosophy, which says:
> Every computer user should be able to use their software in the language of their choice.
Every computer user should be given every opportunity to use software, even if they work under a disability.
How can you expect someone who only speaks Arabic to use the terminal? They'll have to learn a new keyboard layout just to use it!
BTW, does this thread really belong in Absolute Beginner Talk?

---

### Post by Liviu-Theodor on 2008-09-08
> **Flimm said:**
> I've always thought that requiring Ubuntu users to use the terminal for certain tasks was against the Ubuntu philosophy, which says:

How can you expect someone who only speaks Arabic to use the terminal? They'll have to learn a new keyboard layout just to use it!
BTW, does this thread really belong in Absolute Beginner Talk?

I don't know about another languages, but I installed ubuntu (at least once) in my language (romanian) and the name of the folders (viewed in the CLI) (and many applications and some help pages) were translated from english, and quite correct too. And anybody can contribute to translations into his/her own language, or even other's, on launchpad, so he or she can help. But alas, the translations were not complete, but for sure were much better than those found on Microsoft Windows and Office (and even there, the translations are not complete).

And the name of commands, for sure, were the same as in english, but I think this is the way to be.

And this kind of questions, indeed, only an absolute beginner can ask. And ubuntu does not **require** use of terminal, but it is used on posts as it is very difficult to understand so many languages as are spoken on Earth, and english is usually common known, and ubuntu is developped in english mainly, and english is the language most used over the internet. How so many people could understand each other if we were speaking only in our languages (one chinese, one french, one hindi, one swahili, and so on)? And of course, one can use GUI for the same commands in the CLI, if so desires.

---

### Post by 2CV67 on 2008-09-08
> **Flimm said:**
> 
BTW, does this thread really belong in Absolute Beginner Talk?

Thanks for your comments.

I put it in Absolute Beginner Talk mainly because it is absolute beginners who most often have difficulty with Terminal & who are most likely to give up in the face of those difficulties.
I hoped (& still hope) it might become a repository of enough good GUI ideas to be really useful for such Absolute Beginners.

---

### Post by 2CV67 on 2008-09-08
> **ByteJuggler said:**
> ...I suggest you try "gnome-do".  It's like GUI versoin of "command-line completion" on steroids.  Very very useful/fast especially once you're used to it...but there's a lot more to it than just that.  See [**_here_**]("http://do.davebsd.com/") and watch some of the screencasts!

Thanks for that information!

I had never heard of gnome-do, but it looks amusing & is most certainly GUI (so has its place in this thread)!

Not sure that it is the way I want to go, but I will give it a try anyway.

---

### Post by 3rdalbum on 2008-09-08
> **2CV67 said:**
> 
1. Looking for a simple way to act as root when I need to, somebody mentioned I could:

[INDENT][I]Quote:
Go into Synaptic and install the package nautilus-gksu. Log out, and log back in again. Now whenever you right-click a file or folder, you will have the option to "Open as Administrator".[/I][/INDENT]

Man, this is heaven !

I'm not sure if you're thanking me for giving you the GUI-ised version of the instruction rather than the terminal-ised (sudo apt-get install nautilus-gksu) version; but if so, then you're welcome.

Your point about opening files and folders as root is absolutely correct - I cannot see a non-terminal way of doing this unless you install the nautilus-gksu package. And the point raised later on about "How does somebody with an Arabic keyboard type English-based commands, and isn't this against the Ubuntu philosophy" was an excellent one.

Ubuntu has been making strides toward removing the need for terminal use on compatible hardware, and there's always room for improvement. But I've been to the Microsoft Knowledgebase, and I *know* that a huge number of things that Windows users want to do require dropping to the MS-DOS prompt and typing in very long commands that are more cryptic than GNU/Linux commands and seem to be directly calling functions in Windows APIs.

Also, be aware that when faced with the choice between Windows 95 and Mac OS, most people still bought Windows 95 even though it definitely required use of the terminal and the Mac OS didn't even have a terminal. Once you use the terminal on GNU/Linux enough, you remember the commands that you use, just like how salespeople can remember model numbers.

---

### Post by jerome1232 on 2008-09-08
Personally I don't see much difference between remembering commands, and remembering where to find everything in a million gui's.

I guess most people are just use to the gui and don't want to learn to use the command line.

---

### Post by Rocket2DMn on 2008-09-08
Moved to Tutorials & Tips.

---

### Post by mgmiller on 2008-09-08
What I did was combine tracker with deskbar and added the google-suggest and wikipedia-suggest addons from here:  [http://www.k-d-w.org/node/39](http://www.k-d-w.org/node/39)

Now the all powerful alt/F3 can do almost anything very quickly, much like gnome-do.  High lite a word or phrase and when you hit alt/F3 it pops up with the selection already loaded and your choices are below.  You can also have it do system commands if you like or if you input someones name from your address book, will send an e-mail.

Just right click the deskbar icon and select preferences and you can see the choices of actions.  Click to enable.  You can even change the order the actions are displayed.

One function that was lost in the transition to Firefox 3 was the ability of deskbar to hook into your bookmarks and browsing history.  This feature will be back in Intrepid and I really miss it, although, once FF is open, the address bar does many of the same functions.

To enable deskbar, right click your panel and select "add to panel" and select "deskbar".

This is a feature that is installed by default, but not enabled.  I think it should be enabled by default also.

---

### Post by 2CV67 on 2008-09-08
> **3rdalbum said:**
> I'm not sure if you're thanking me for giving you the GUI-ised version of the instruction rather than the terminal-ised (sudo apt-get install nautilus-gksu) version; but if so, then you're welcome
Yessir! Sorry I did not attribute it to you in this thread.
I did officially thank you for that post though. :)
Thanks again!

> Also, be aware that when faced with the choice between Windows 95 and Mac OS, most people still bought Windows 95 even though it definitely required use of the terminal and the Mac OS didn't even have a terminal. Once you use the terminal on GNU/Linux enough, you remember the commands that you use, just like how salespeople can remember model numbers.

I started with punched cards so the original Mac with about 7" screen & a mouse was an absolute revelation as an interface.
Later I changed from Mac to Windows (95) because it was cheaper, even though it was less good.
In 13 years I hardly ever (never?) needed to use terminal.
Now I have decided to avoid Vista and shift progressively from XP to Ubuntu, again because it is cheaper, whether it is better or not as good.
Philosophically, I like & support Ubuntu.
Practically, it is still not, BY MILES, fit to be used by anybody else in my family, for lots of reasons including terminal.

Personally, maybe due to age, but I don't think so, I admit that I can remember for a short time, the commands I use frequently & recently, but that is not enough.
I don't intend to become an Ubuntu Geek  - I just want to be a computer user.
There is no place there for learning hundreds of commands which need to be memorized & typed without error.

If somebody would like to start a philosphical thread on this subject, I would be delighted to join in.
Please post a link here!

But I would like this thread to stick to its original purpose of providing a repository of helpful tips & tricks for people who want or need to have thier Ubuntu as a GUI experience.

Thanks!

---

### Post by KillerKiwi on 2008-09-09
[gnome-schedule]("apt:gnome-schedule") - for scheduling things ;)

rapache - for configuring apache [https://edge.launchpad.net/rapache]("https://edge.launchpad.net/rapache")

[nautilus-actions]("apt:nautilus-actions") - add context menu items to nautilus

[quicksynergy]("apt:quicksynergy") - set up a synergy keyboard / mouse connection

---

### Post by 2CV67 on 2008-09-09
Thanks for those suggestions, KillerKiwi.

Small problem (at least for me) I can't see your links.
When I click, I get:
> Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program.

Do I have to make an adjustment, or can you clean that up for dummy users? ;)

---

### Post by KillerKiwi on 2008-09-09
There apt install links, they should work on ubuntu with firefox....

try 


```
sudo apt-get install gnome-schedule
```

```
sudo apt-get install nautilus-actions 
```

```
sudo apt-get install quicksynergy 
```

---

### Post by 2CV67 on 2008-09-09
:oops: :oops: :oops:

Sorry! - I was in XP & half asleep at the time....

---

### Post by mgmiller on 2008-09-09
To make setting up samba a nice gui experience:
```
sudo apt-get install system-config-samba
```Run it from System > Administration > Samba

Instead of manually editing /boot/grub/menu.lst, use:
```
sudo apt-get install startupmanager
```Run it from System > Adminstration > StartUp-Manager

To create mount points for drives:
```
sudo apt-get install pysdm
```Run it from System > Administration > Storage Device Manager

To easily switch between metacity, compiz and beryl (if it's installed) and also quicly get to the settings dialogs for everything:
```
sudo apt-get install fusion-icon
```Run it from Applications > System tools > Compiz Fusion Icon
It will put an icon in the top panel, right click it see choices.

---

### Post by Jeztastic on 2008-09-19
This is all so true. The number of times I have struggled with the command line or editing .conf files, only to find that I could have just point and clicked in a few steps to sort it out. 

I believe that there should be a Canonical policy that any official documentation or advice/support given in ubuntu should be provided side by side gui and command line, for the user to choose. 

If possible, the user should be given the choice which they would prefer, and if there is doubt, the gui method should be given by default. Otherwise, Linux operating systems will just never take off.

---

### Post by 2CV67 on 2008-09-20
I am surprised nobody had any suggestions for the "missing" GUI items I listed, nor asked for any new ones:
> Missing GUI items - What would I like to find GUI tools/methods/tips for?

a. MD5 checksum generation & checking.
Like the simple md5.exe I have added in XP.

b. More obvious rapid scrolling in Synaptic Package Manager (& others).
Without needing to know/remember to click on some odd folder first.

c. Real-time Wi-Fi signal strength indicator/meter
Why do I have to optimise my aerial position in XP (with signal strength gauge) instead of in Ubuntu?

d. Setting-up & fault-finding in Networking & Wi-Fi
I suppose that is a big one – I am not holding my breath!

Nobody?

---

### Post by Bios Element on 2008-09-20
> **Jeztastic said:**
> This is all so true. The number of times I have struggled with the command line or editing .conf files, only to find that I could have just point and clicked in a few steps to sort it out. 

I believe that there should be a Canonical policy that any official documentation or advice/support given in ubuntu should be provided side by side gui and command line, for the user to choose. 

If possible, the user should be given the choice which they would prefer, and if there is doubt, the gui method should be given by default. Otherwise, Linux operating systems will just never take off.

No doubt you could get that if you wanted to burn some money on paid support. The Vast majority of us on the forums help you because we enjoy it. Not because we want to spend hours typing up detailed "Now click the second yellow button to the right. Then select the dropdown labeled "123"" Complete with Screenshots. If you can read, you can understand the CLI. If your a normal human being, You can learn. Thus, you can learn CLI. Nothing is perfect. No OS is going to be ready outta the box for every single person on the world.

Some people need things others wouldn't. Some need more help, Some need none. I generally think Ubuntu currently has about the best blend possible.

---

### Post by Jeztastic on 2008-09-20
> **Bios Element said:**
> No doubt you could get that if you wanted to burn some money on paid support. The Vast majority of us on the forums help you because we enjoy it. Not because we want to spend hours typing up detailed "Now click the second yellow button to the right. Then select the dropdown labeled "123"" Complete with Screenshots. If you can read, you can understand the CLI. If your a normal human being, You can learn. Thus, you can learn CLI. Nothing is perfect. No OS is going to be ready outta the box for every single person on the world.

Some people need things others wouldn't. Some need more help, Some need none. I generally think Ubuntu currently has about the best blend possible.

I appreciate the support I receive here, I really do. And I appreciate why, sometimes, CLI is a convenient and effective way of giving support. For example 'Post the output of lspci'. Or 'apt-get install xyz'. However, for complicated driver setups, system config etc, editing .conf files no way. For example, a common reply for a request about driver setup might involve detailed instructions on adding sources, downloading, extracting, making, installing, running files from inside directories, enabling and disabling lines inside conf files... I would utterly contest that this is easier for anyone than instructions like 'download this package from synaptic, then download that application to configure it'. I have struggled to set up my PCs in this way numerous times, often buggered it up, re-installed, or given up. Then later found a nice little application which does it all through the gui, which would have made it oh so simple.

---

### Post by itssaurav2004 on 2008-09-20
for MD5 sum look at
[http://yabblog.com/2008/09/18/top-10-nautilus-scripts/](http://yabblog.com/2008/09/18/top-10-nautilus-scripts/)

---

### Post by 2CV67 on 2008-09-20
Thanks very much itssaurav2004!

Maybe I'm an even bigger dummy than I thought, but I had never heard of nautilus scripts.

I checked your link & Googled a bit more to find the following which offer very comprehensive lists of nautilus scripts:

> [http://www.ubuntu-unleashed.com/2007/09/125-nautilus-scripts-to-simplify.html](http://www.ubuntu-unleashed.com/2007/09/125-nautilus-scripts-to-simplify.html)
> [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php)

Are these the best/easiest/safest sites for dummies?

I am sure I am going to get a lot of mileage out of this new (for me) idea!

Hope it helps others too!

Thanks again!

---

### Post by 2CV67 on 2008-09-20
Thanks again itssaurav2004!

I installed just "Make md5" without the other "Top 10" to see if/how it works.

It was easy & it works OK. :)

For info: this is what I did (please correct if necessary!).

1. Go to [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php)
2. > File Processing > Make md5 (opens text file)
3. Select all & copy.
4. Ubuntu > Places > Home > View > Show hidden files > .gnome2 > nautilus-scripts
5. Right-click > Create document > Empty file > Open new file > Paste (copies text file).
6. Rename new file > Make md5

To use: Right click on Target file > scripts > Make md5 > Voila!

---

### Post by 2CV67 on 2008-09-25
One for dual-booters:

If you got addicted to middle-click copy/pasting (post #1 - item 6.) then frustrated because Windows wont...

Add DragKing v1.3 which allows Windows to catch up with Linux on this point!

From:> [http://www.donationcoder.com/Software/Skrommel/index.html#DragKing](http://www.donationcoder.com/Software/Skrommel/index.html#DragKing)

Enjoy! :)

---

### Post by egalvan on 2008-09-25
> **Bios Element said:**
> Vast majority on the forums help you because we enjoy it. Not because we want to spend hours typing up detailed "**Now click the second yellow button to the right.** Then select the dropdown labeled "123"" Complete with Screenshots. If you can read, you can understand the CLI. If your a normal human being, You can learn. Thus, you can learn CLI. Nothing is perfect. No OS is going to be ready outta the box for every single person on the world.

Some people need things others wouldn't. Some need more help, Some need none. I generally think Ubuntu currently has about the best blend possible.

Not to mention the fact that when "Kicking Klingon" 9.04 or "Lying Llama" 9.10 comes out, it will change to the "third red button"

:lolflag:

Seriously, the CLI changes MUCH less than the GUI.

---

### Post by 2CV67 on 2008-09-26
Yes I know that is true but, as I said in post #1:
> Oh & finally, PLEASE do not use this thread to try to convince me that I should learn to love Terminal because it is great & fast & efficient & smart & powerful &…
I know all that, as I said at the beginning.
By all means, start your own thread on that subject if you want to! 

& in post #14:
> If somebody would like to start a philosphical thread on this subject, I would be delighted to join in.
Please post a link here!

But I would like this thread to stick to its original purpose of providing a repository of helpful tips & tricks for people who want or need to have their Ubuntu as a GUI experience.

So I will not be responding to any further similar posts.

Thanks!

---

### Post by egalvan on 2008-09-26
> **2CV67 said:**
> PLEASE do not use this thread to try to convince me that I should learn to love Terminal because it is great & fast & efficient & smart & powerful &…
Thanks!

Well, I for one am not trying to convince you...

if you don't want to use the terminal, don't use it...
(but you don't have to 'love it' to 'use it')

the CLI has its place, and the GUI has its place

Thing is, many times the CLI is the easiest way to GIVE help.
Although I've noticed an increase in 'Synaptic' advice versus 'aptitude'.

It's All About Linux!
It's All About Choice!

---

### Post by jdorenbush on 2008-12-02
Great thread! Thanks for tips.

---

### Post by mgmiller on 2008-12-03
Here is an update to my post #13 where I lamented the loss deskbar's ability to read the new ff3 database for bookmarks and recent searches. 

Although this function was not added in Intrepid as I had hoped, someone has created an extension for deskbar that works well.

Get it here:
[http://github.com/lutzky/deskbar_ff3/tree/master](http://github.com/lutzky/deskbar_ff3/tree/master)

Click the download link near the top of the page to get it.  It includes instructions for installation.

In the deskbar preferences it's called "Firefox 3 Places"  I have moved it to the top of my list in deskbar so it displays first.

I can now go back to the alt F3 key combo to do almost anything.  ):P

---

### Post by markbuntu on 2008-12-21
GUI tools for sound control

gnome-alsamixer 

It is alot easier to use that alsamixer and often shows more options than the panel volume control. Applcations/Sound and Video

padevchooser

This puts a little icon on your panel so you can access various pulseaudio guis like the pavumeters and papreferences and pamanager and

pavucontrol

The PulseAudio Volume Control. I can't believe this is left out of the default desktop. It is critical for using pulseaudio and really handy if you have more than one sound device. Applications/Sound and Video

asoundconf-gtk 

This is for selecting the default sound card for alsa which if you are using Hardy or Intrepid you should set to pulseaudio. System/Preferences/Default Sound Card

gstreamer comes with System/Preferences/Multimedia System Selector to set you gstreamer defaults

soundconverter or soundkonverter (kde) for converting you sound files from one format to another.

Ubuntu Studio GUIs

qjackcontrol

The jack control panel

Ubuntu Studio Controls

for setting audio system priorities

patchage

for connecting all your studio audio and midi apps and devices.

For a full rundown on setting up your sound so you never need to use a terminal go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by 2CV67 on 2009-01-28
I recently discovered Remastersys.

This is really neat as it lets you make a live CD/DVD of your own complete Ubuntu set-up, with all your data & settings, so you can install it on any PC & have everything just like home.
Or keep it as a backup, especially during an upgrade…

There is an excellent tutorial: [http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)
which shows you how to get it & how to use it.

---

### Post by mgmiller on 2009-02-02
I just discovered some interesting ways of listing and removing orphaned packages.  

First one I found was:
```
sudo apt-get install gtkorphan
```After install, it's here:  System&#8212;>Administration&#8212;>Remove Orphaned Packages

But then I discovered you can set up Synaptic to do this for you:

How to define a custom filter in Synaptic for orphaned packages, instead of installing GTKOrphan. 
1) Run Synaptic
2) Click Settings > Filters
3) Click New
4) Click "Deselect All"
5) Check the box next to &#8220;Orphaned&#8221;
6) Give the new filter a name, and click OK.

To use it:
Run synaptic and click on the "Custom Filters" button on the bottom left.
Select "Orphaned" in the list above the buttons.
All the orphaned files appear on the right side.

---

### Post by KillerKiwi on 2009-02-02
A new one i've started using [disk-manager]("apt:disk-manager")
[http://flomertens.free.fr/disk-manager/]("http://flomertens.free.fr/disk-manager/")

---

### Post by 2CV67 on 2009-02-04
> **KillerKiwi said:**
> A new one i've started using [disk-manager]("apt:disk-manager")
[http://flomertens.free.fr/disk-manager/]("http://flomertens.free.fr/disk-manager/")

Thanks for that suggestion.

Other similar GUI tools for file system configuration without manually fiddling in fstab include [PySDM]("http://pysdm.sourceforge.net/") & [MountManager]("http://www.opendesktop.org/content/show.php/MountManager?content=78270").

Both in Synapt.

Comparison at: [http://www.linux.com/feature/153412](http://www.linux.com/feature/153412)

Pity none of these seem to enable changing Labels on existing drives, as far as I can see.

---

### Post by mgmiller on 2009-02-04
> Pity none of these seem to enable changing Labels on existing drives, as far as I can see.If you have gparted installed, that can change drive labels.  
If you don't have it, install it:
```
sudo apt-get install gparted
```

1) Run gparted... System > Administration > Partition Editor
2) Select the drive you want to change the label for by clicking on the drop down list in the upper right corner of the window.
3) Unmount the drive by right clicking and selecting "unmount" or from the drop down menu at the top... Partition > Unmount
4) either right click and select "Label" or...  Partition > Label
5) type the new name in the field provided and click OK
6) remount the drive by either right clicking and select "Mount On"  or...  Partition > Mount On.  (Note, the area to mount the drive should be where it was last mounted.) 


This won't work on the drive your OS is running from, because you can't unmount it.  You would have to run gparted from the Live CD to do that.

---

### Post by 2CV67 on 2009-02-04
Thanks, mgmiller for that suggestion & the concise instructions.

In my today's edit #e at the bottom of the original post I said I would like to find something simpler & safer that GParted.

More background in this thread:
[http://ubuntuforums.org/showthread.php?t=1055136](http://ubuntuforums.org/showthread.php?t=1055136)

I found GParted worked but was slow & potentially dangerous for such an elementary task.

Actually, for anybody dual-booting with Windows, then Windows Explorer is by far the best way of renaming any drive Windows can see...

Maybe we can keep any discussion on this topic in the other thread & just put any solution(s) here?

So far, GParted is the only solution I have seen for anybody not dual-booting.

Thanks again!

---

### Post by Twitch6000 on 2009-02-05
This is a great Tutorial :D.

Here are thee more great GUI tools

Ubuntu Tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

A great tool for tweaking system settings and adding items quickly.

It is also good for adding extra repos.(warning though the repo tool is a bit buggy)

All in all a quick and useful tweak tool that saves loads of time.

Ubuntu Control Center [http://ubuntuforums.org/showthread.php?t=207894](http://ubuntuforums.org/showthread.php?t=207894)

Well I think you can guess what this is ;).

A area that has everything just one click away :D.

Mint Menu [http://packages.linuxmint.com/#6main](http://packages.linuxmint.com/#6main)

A easier to use Menu. I find it probably the best to use.

---

### Post by 2CV67 on 2009-02-12
**_GIMP - Screenshots, Missing Toolbox menu & How to minimize GIMP Toolbox window._**

GIMP drives me crazy as a counter-intuitive interface, in spite of it's undoubted technical capabilities.

Today I wanted to try it for screenshots (with mouse pointers - but that's another story) - total mystery!

I found tutorials which told me to go: Toolbox > File menu >...
but my Toolbox has no menus!

OK, don't panic - you need to use the other (main?) GIMP window, the one which is initially empty except for some menus. 

Go: **Edit > File > Create > Screenshot**


Then, if you try to take a screenshot of the whole screen, you get GIMP Toolbox window thrown in...
I spent a long time looking in every possible menu item, especially Preferences, without finding how to minimize the Toolbox window.
Can you believe that?

Finally, as usual, Google found the answer, thanks to Michael Soibelman on Google Groups forum:
> [B]Edit ->Preferences -> Window Management -> Hint for the toolbox -> change
to 'Normal window' -> click OK

You must restart Gimp for the 'minimize' button to appear in the toolbox.[/B] 

That works OK, but "Hint for the toolbox"???

---

### Post by ByteJuggler on 2009-02-12
What's wrong with pressing PrtSc when you need a screenshot? :P  (Or for that matter, Applications->Accesories->Take screenshot?)

---

### Post by 2CV67 on 2009-02-13
> **ByteJuggler said:**
> What's wrong with pressing PrtSc when you need a screenshot? :P  (Or for that matter, Applications->Accesories->Take screenshot?)

I agree that simply pressing the screenprint button (or Alt/scrn for current window only) is the easiest & best method for most purposes.
Especially if you don't do it very often.
Or if your mouse is frozen!

If you want a bit more control, you can use Applications > Accessories > Take Screenshot.
This gives you the choice of:
- including the pointer or not
- including the window border or not
- setting a time delay or not (useful for setting/pointing etc)

In fact, all of the above methods fail to display the pointer correctly in the 'current window' configuration, which can be a big nuisance if you are using screenshots to explain something.
Another disadvantage of the 'Take Screenshot'method is that it closes after every shot, so you need to go through the Applications > Accessories > Take Screenshot routine every shot...

To avoid going through that routine every shot, you can, of course add a launcher for 'Take Screenshot' to the panel, so then you can launch in one click.
If you have that, you will probably use it most times & forget about the Screenprint button...

None of the above will get you a shot of a limited area, so if you want to, for instance, publish a shot of part of a screen on a forum, you need to re-open your saved screenshot in, say, Gimp & crop it to the size you want then re-save it.

That led me to the idea that, if I wanted to include pointers &/or crop areas, then maybe it would be easier to just do the whole thing in Gimp, which has a native screenshot facility.

Maybe there is something wrong with me (no comments please) but I find nearly everything in Gimp counter-intuitive.
Firstly, although I knew it was there, I couldn't find the screenshot control.
Tutorials said it was in the Toolbox window menu bar, but my Toolbox had no menu bar.
Eventually I found it in the 'other' Gimp window menu bar, under File > Create > Screenshot.
There, I found options for 'Entire screen' or 'Single window' and for Including the mouse pointer, but only for the Entire screen option, so no advantage over above methods.
Toolbox window is on desktop & so figures in any screenshot.
To fix that, as I said in my last post:
Edit > Preferences > Window Management > Hint for the toolbox > change to 'Normal window' > click OK
You must restart Gimp for the 'minimize' button to appear in the toolbox.
Then you can minimize Toolbox window (but not close it...).

One big advantage of Gimp is the facility to 'Select a region to grab'.
This allows you to do just that - select any rectangular region so you save just that bit & don't need any subsequent cropping.
So, if you want to end up with a small section of screen, it is easier to start in Gimp.
But then you can't have the pointer in that small section....

Other disadvantages are
- your desktop gets cluttered with Gimp windows, each with one screenshot
- for every new shot, you need to find one of those windows, then do File > Create > Screenshot again.

I don't think Gimp is the way to go, at least not for me.

I also tried KSnapshot but that seems to have no option for including the pointer.

Then I tried **_Gscrot (aka Shutter)_**.

What follows is copied from my post [here.]("http://ubuntuforums.org/showthread.php?t=1067795")
> After a few minutes trial, I am already convinced this is just what I was looking for & seems to be a particularly well-thought-out tool.

You get to select with/without pointer & that works.

You can choose delays, surrounds etc & that works.

You can save one or several combinations of criteria into "Profiles" to re-select in one click.

You can capture the whole screen or any window or any rectangle you want, with or without pointer.

The Shutter/Gscrot window gets out of the way when it should but does not keep closing & needing re-opening.

The option for capturing any rectangle is particularly well thought out as it presents you with a screen to do your selecting on, but then waits until you press "Enter" before taking the shot, unlike Screengrab, for instance, which takes the shot as soon as you have created a rectangle - like it or not.

Without talking about the various save options.

Obviously a good application!

On the downside, I had never heard of PPAs and would probably not have dared to go ahead with this installation without recommendation on this thread.
The written instructions on [the PPA page]("https://launchpad.net/~shutter/+archive/ppa") are short but ambiguous & confusing for a noobie.
The next link "[Follow these instructions]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")" adds to the confusion & goes over my head, being apparently aimed at developers.
Most reassuring was the [Utube video]("http://www.youtube.com/watch?v=UUZOQsNo_ws") which made it look feasible or at least worth a try.

I followed the video, selecting only the "deb....intrepid main" line (not the "deb-src..." line??).
I never got warned or asked about OpenPGP keys, so did nothing there (why??).

I did not find any kind of Help or Tutorial....
[This was the best description]("http://maketecheasier.com/gscrot-a-powerful-screen-capture-tool-for-linux/2008/11/14") I found.

Going through the installation, the references are "Shutter" but in Synapt it is still Gsrcot for now.

Additional plus points I found since are
- It keeps your recent shots all tabbed in one window (hint to Gimp!)
- You can save, rename, copy, upload, etc very easily.
- There is a GREAT editing facility, where you can easily add text, comments, symbols etc etc!

So I think Shutter/Gscrot is the best screenshot tool I have found so far, for any kind of advanced usage (pressing the screenshot button is still best for most routine jobs!).
I am using it in preference to all the others now.

I probably can't recommend it for everybody, due to the PPA installation hassles & lack of help function at the moment, but worth a try if you are not put off by that.

---

### Post by 2CV67 on 2009-02-24
**GUI Launcher Icons - change, find, make your own...**

If you are seriously GUI like me, you probably have a lot of icons, particularly little icons around 5mm x 5mm on the top panel.

If you want to improve the iconfusion situation, then:
- It's easy to change icons.
- There are a huge number of icons already in your Ubuntu to choose from without needing to look outside.
- It's quite easy to make your own.

[Further details here.]("http://ubuntuforums.org/showthread.php?t=1070608")

---

### Post by markbuntu on 2009-02-24
I put a lot of stuff in drawers in my panels. I have a side panel full of drawers. If only I could put names on them......

---

### Post by mgmiller on 2009-02-25
> If only I could put names on them......

You can change the icon for the drawer, just right click it and select properties.  So maybe you could make an icon that had the name you wanted in it.

---

### Post by markbuntu on 2009-02-26
> **mgmiller said:**
> You can change the icon for the drawer, just right click it and select properties.  So maybe you could make an icon that had the name you wanted in it.

Yaarg....sometimes I wonder where my brain wanders off too....

---

### Post by sofasurfer on 2009-03-02
2CV67.
This is a great thread. I have come a long way with the CLI and I find that for many tasks it is plenty useful and adequete. I intend to learn a lot more with it. But some days you just can't remember that old command or you don't have time to do days of research to find a method of completing a task. I'd like to just click on a GUI that can perform a few differant chores all from the comfort of a window with lots of buttons and bells.

Those GUI's exist for a purpose. Theres lots of reasons to expect people to use them. Thanks.

---

### Post by gg234 on 2009-04-07
Mount ISO files using 

Furius ISO Mount

An ISO, IMG, BIN, MDF and NRG Image management utility for the Gnome Desktop Environment.Check more details  

[http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html](http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html)

AcetoneISO

AcetoneISO is CD/DVD image manipulator for Linux.Using this tool it is very easy to Mount and Unmount ISO,MDF,NRG Images 

[http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)

---

### Post by jerrrys on 2009-07-26
> **sofasurfer said:**
> 2CV67.
This is a great thread. I have come a long way with the CLI and I find that for many tasks it is plenty useful and adequete. I intend to learn a lot more with it. But some days you just can't remember that old command or you don't have time to do days of research to find a method of completing a task. I'd like to just click on a GUI that can perform a few differant chores all from the comfort of a window with lots of buttons and bells.

Those GUI's exist for a purpose. Theres lots of reasons to expect people to use them. Thanks.

Maybe some new ideas will come along...

---

### Post by dcstar on 2009-11-16
**galternatives** - graphical setup tool for the alternatives system

This allows users a decent interface to view/change the various default applications in the system.

Also this will allow you set up to use the graphical interface (Gnome KDE, whatever you have) for any of those software installs that prompt you:

**sudo dpkg-reconfigure debconf**


BTW, great thread, something that all command line snobs should read to rid themselves of the seemingly "superiority complex" that some exhibit by always telling novice users to use the command line instead of a perfectly good (and usually far more appropriate) GUI alternative.

PS: I have been using the command line (in various forms) since 1976, and do know when it is appropriate and when it does more damage than good.

---

### Post by Windwalker52 on 2010-06-10
I am going to try to include a screenshot of my current desktop which has my idea of eyecandy on it. I am glad I found this forum and thank you. Is it legal and ethical and safe to upload file attachments?
 I started with a proprietary GUI that got consumed by DOS and 3.1 and then went heavily into DOS/3.1 before XP and finally migrated into Ubuntu 10.04 after trying Debian which has a lot of the flaws mentioned here.
 Dockbars are good handy little tools and coming from XP I am used to icons.
 I just wanted to say hello and thanks and offer my two cents. If I can get it to work with typing then just at the screenshot which is another good tool to have on hand.
                                                                                                Windwalker

---

### Post by Windwalker52 on 2010-06-10
one more try

---

### Post by edempco on 2010-06-16
The first page of this thread is great - 1 thru X numbers of GUI items. Can there be a summary screen or link that gives all of the GUI suggestions on one page without having to read 6 pages of stuff?

I believe in GUI. It's more accurate. It can become a standard way of addressing installation difficulties for software. It is an easy way to add and remove software; doesn't leave connecting junk in the operating system (as much as using Terminal). It levels the "using" field for many users of this operating system. Could this be why there are two ways to add and remove programs? Synaptic and the software center (found as various names under Applications - this needs a standard name) are great ways to access and install software. To facilitate this idea, we need a GUI recap page every once in a while, in this thread, to help others that come here - maybe it should be a web page by itself with screen shots.

Additionally, there has got to be a way to get the word out and to discourage most people (maybe not all) that are offering help in forums from using Terminal commands. Some of these people seem to be using Terminal as a way of attempting to show their prowess in this operating system. Some Linux distributions only have Terminal (that's a pity). Ubuntu, on the other hand, was made to be a GUI. Should people who post is this thread refrain from using Terminal commands and instead, tell how to get the "whatever" by GUI methods? Since, Terminal can be so dangerous (as others have commented), should we attempt to encourage (in a stronger way) others to stay away from using it as much as possible? For instance (in a recent posting above), _doesn't removing and reinstalling dpkg_ (using Synaptic) do the same thing as "**sudo dpkg-reconfigure debconf"** in terminal**? ... it's certainly would be easier ****(not completely sure about this)**[B]; especially if you can't put your fingers on the right keys or have an hand/eye coordination problem.

My main comment/question is ... how do we go from the great thing that was started here, to informing countless others of the benefit of GUI?
[/B]

---

### Post by 2CV67 on 2010-12-18
> **edempco said:**
> The first page of this thread is great - 1 thru X numbers of GUI items. Can there be a summary screen or link that gives all of the GUI suggestions on one page without having to read 6 pages of stuff?

I do edit the original post, to include all the suggestions I can actually understand...

**New GUI need:**
Control over the frequency of the automatic disk checks on start-up.

As far as I can see, the only way to handle this at the moment is using tune2fs in terminal.
[http://ubuntuforums.org/showthread.php?p=10252490#post10252490](http://ubuntuforums.org/showthread.php?p=10252490#post10252490)

It would be great to have a clear GUI to allow setting disk checks for whenever is most convenient.
And maybe on shut-down, instead of start-up?

---

### Post by 2CV67 on 2012-02-07
**New GUI need:**

To Set the System-Wide Default Papersize.

The current method is to navigate to /etc/papersize & rewrite the contents with Admin priviledges & save.
Not that difficult when you know, but hard to find, or find again after a lapse.
The default setting probably depends on something you choose when initially installing Ubuntu, maybe Language?
Doesn't seem to be the more logical "Location", since I always end up with "Letter" here in France where A4 is the only option you will ever need.

Can't think how much time I have wasted trying to reset defaults in OpenOffice & LibreOffice, where I might have expected to be able to do it, only to find my good work over-ruled by some invisible hand.
The invisible hand is /etc/papersize.

To me, the logical place to find a GUI selection of Default Papersize would be in Printer Properties, becoming a Printer-wide, rather than system-wide default.

---

### Post by 2CV67 on 2012-02-07
I notice that some of the detail content in this thread is getting a bit out-of-date now.
Since I have dropped out of mainstream Unity & Gnome to play with Lubuntu, I am no longer in a position to keep track of GUI Tips & Needs for the popular desktops.
So I guess this thread may become somewhat frozen,unless anybody else wants to take over...

Thanks, everybody, for your contributions so far!

---

### Post by mgmiller on 2012-02-07
[QUOTE=2CV67;11670499]**New GUI need:**

To Set the System-Wide Default Papersize.

In both 10.04 with gnome 2.x and in 11.10 with unity, the default paper size is set the same way.  In printer properties, printer options, General, page size.  Whatever is set there will appear in /etc/papersize.

In 10.04/gnome 2.x Click through System > Administration > Printing to bring up the printer driver window.  Right click the printer and select properties, printer options, General, page size

In 11.10/Unity, either hit the super key and type printing and click on the icon or in the upper right corner of the top panel, click the power icon and the first choice is system settings.  Then click the printing icon.  In both cases you will get the same window as 10.04 gave you and it's set the same way.

I often have to change the paper size the first time I use open/libre office also, but it works fine in every other printing application, browsers, etc.  Open/Libre Office wants to default to A4 regardless of the default setting in the printer driver properties, but I need US letter.  I make that change once, and I'm done.

---

### Post by 2CV67 on 2012-02-07
Thanks, mgmiller, for that advice.

I checked & it doesn't seem to work that way for me.

To avoid a long discussion in this thread & because the situation seems more complicated than I thought, I have started a new thread here on this subject:
[http://ubuntuforums.org/showthread.php?p=11671423#post11671423](http://ubuntuforums.org/showthread.php?p=11671423#post11671423)

---

### Post by mastablasta on 2013-03-08
i just saw this (take here form another thread & your sig). a good compendium. might be good to put it in a different form (with pics and all) and perhaps to the ubutnu wiki. i am also GUI fan. so i use Kubuntu which has this done better out of the box. Gnome has plenty of GUI but mostly they are sort of 3rd party. as the Gnome philosophy is not to overwhelm the user with various settings and options. i think this is a good aproach (it was well doen especially in GNome2).

KDE doesn't have that philosophy so it has many things implemented by defalut in it's GUI. various settings, customisations etc.

---

