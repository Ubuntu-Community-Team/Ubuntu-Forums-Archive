---
title: "We can only take so much before we head for home."
date: 2010-04-07
forum: Testimonials &amp; Experiences
---

### Post by Nightstrike2009 on 2010-04-07
I hate to say this because I actually like Linux and Ubuntu in particular but i headed away from MS because of bug ridden OS and actually found the solution (Ubuntu) to be worse than the problem (Windows).

This attitude of "oh is broken a bit but so what its free stinks", I came to Ubuntu for a stable os and i found that: 

1) The .deb installer packages couldn't touch the simplicity of windows .exe files.

2) What was ofen fixed in one distro was broken in the next, then fixed in the next, then broke again in the one after that.
Ubuntu 9.04 my CD/DVD burner wouldn't work, than in 9.10 it did but the internet didn't (a bit of a bugger for an OS that relies on the internet for software and updates).

I admire Linux's morals and its goals but Ubuntu is never going to surpass Windows with bickering about pointless features, when essential ones don't work, at least in my opinion anyhow.

I am not aiming this at the Linux community (as I will probably carry on with another OS and admire its morals) but releasing bug ridden OS's is the reason many turn to Ubuntu they don't expect the same treatment with a different look.

I wanted too leave Windows for good but these faults have turned me in the opposite direction (Back to Windows) and I am far from alone many newcomers have given up due to daft and avoidable errors.

Id like to say I left windows for a better more stable OS, maybe I'll still find it one day.

I myself have tried to help newcomers and convert people to Ubuntu but nearly all have returned to Windows because of daft errors. If more focus was placed on reliablity and stabiltity rather than moving window buttons around when no one had a problem before (and other such stupidity, like no internet connection on 9.10 for 3g modem users because of a bug WTF)

I thought we were trying to prove we were better than the competition not trying to make ourselves and newcomers look stupid. 

I'd like to thank the Ubuntu community for making me feel welcome, and I will continue to help out if I can. I found you all to be a great crowd and always willing to help. 

Thanks for the memories, I hope the upcoming 10.04LTS will prove me wrong by being as stable and reliable as the others should have been (I can handle the daft window gadgets has i know how to return them to how they were) :-(

---

### Post by uRock on 2010-04-07
I am so glad that Linux doesn't do .exe style files. That is part of what makes it more secure. I have never had a .deb that wouldn't install.

Good luck in whatever you end up using.

I have installed many programs in Windows that wouldn't work as advertised.

Cheers,
Ronnie

---

### Post by marshmallow1304 on 2010-04-07
Did you report the bugs?  That's the only way they'll have a chance to be fixed.

---

### Post by Nightstrike2009 on 2010-04-07
Yeah once I had navigated another nightmare of a website (In the compiz bug case I gave up as I had to file a bug on yet another website altogether) its probably easy for veterans but its a pain just to find the right section for newcomers.

I am typing this from my (New) OS right now Xubuntu 9.10 I have got around the 3g modem bug as I had to before and find Xubuntu to be more in keeping with what I wanted.

Weird how we all use Ubuntu forums (Xfce, Kubuntu) guess we are the same OS with a different window manager, in Xubuntu's it make a big difference though, maybe I had right OS just wrong window manager before.

PS: The Compiz bug was fixed in 9.10 (After affecting 9.04). I dont expect it to re-appear again.

The 3g Modem bug is inexcusable unless you have a workaround or a dual boot machine, which was also reported before 9.10's release, but crippled many newcomers internet connections anyhow. 

I have also had dependency errors where one .deb relied on another and neither would install first, again with no connection to auto-install was stuffed again.

The window gadget argument currently ongoing is stupid in my opinion too it wasn't broken so why fix it. Why don't they put the Window gadgets at bottom-left or bottom-right or maybe even in the middle in 10.10? Joke :-)

---

### Post by doas777 on 2010-04-07
gl & hf

cheers,
Franklin

---

### Post by uRock on 2010-04-07
> **Nightstrike2009 said:**
> Yeah once I had navigated another nightmare of a website (In the compiz bug case I gave up as I had to file a bug on yet another website altogether) its probably easy for veterans but its a pain just to find the right section for newcomers.

I am typing this from my (New) OS right now Xubuntu 9.10 I have got around the 3g modem bug as I had to before and find Xubuntu to be more in keeping with what I wanted.

Weird how we all use Ubuntu forums (Xfce, Kubuntu) guess we are the same OS with a different window manager, in Xubuntu's it make a big difference though, maybe I had right OS just wrong window manager before.

PS: The Compiz bug was fixed in 9.10 (After affecting 9.04), I didn't expect it to re-appear again,(The 3g Modem bug is inexcusable unless you have a workaround or a dual boot machine, which was also reported before 9.10's release, but crippled many newcomers internet connections). I have also had dependency errors where one deb relied on another and neither would install first, again with no connection to auto-install was stuffed again.

I am testing Lubuntu and plan to put it on my desktop machine as the primary OS in the next week or so.

---

### Post by kaldor on 2010-04-07
Maybe you'd prefer a Mac? Similar to Linux, more stable than Windows.

---

### Post by julianb on 2010-04-07
I couldn't get Lubuntu Lucid to remember my WEP key, so I use Ubuntu Lucid instead. Other than that, Lubuntu is great!

---

### Post by 2hot6ft2 on 2010-04-07
The deb installer works fine for most everything but if you find something that's not for the version of ubuntu you're running then it's like trying to install something for win 98 on win7 good luck with that. That's why there are repos.
> **Nightstrike2009 said:**
> no internet connection on 9.10 for 3g modem users because of a bug WTF
I don't know if it will help any but I saw this post a while back that was interesting.
> **fheinsen said:**
> I have the same mobile broadband modem and use it regularly without any problems. 

The Verizon UMW190 is a so called "global ready" 3G modem, meaning that it connects to both CDMA and GSM networks.  Alas, Ubuntu 9.10's Network Manager currently identifies this modem as GSM only, so until this gets fixed, connecting over a CDMA network (such as Verizon's network in the US) requires that you use an additional application.

Install gnome-ppp -- this is the application you will use to connect, and do the following:

**Step 1.** Plug the modem in on a freshly restarted computer.
**Step 2.** Launch gnome-ppp as superuser (e.g., press Alt-F2 and type "gksu gnome-ppp"), and configure the following settings:
 
[LIST]
[*]Modem Tab
[LIST]
[*]Device: /dev/ttyACM0
[*]Type: USB Modem
[*]Speed: 460800
[*]Phone Line: Tone
[*]Volume: Off
[/LIST]
 
[/LIST]
 
[LIST]
[*]Options Tab
[LIST]
[*]Minimize: checked
[*]Dock in Notification Area: checked
[/LIST]
 
[/LIST]
 Click Close.  Fill in the fields in the main Gnome PPP window:
 
[LIST]
[*]Username: _1234567890@vzw3g.com_
[*]Password: vzw
[*]Phone Number: #777
[/LIST]
 **Step 3.** Click Connect.  That should be it.


To disconnect, click on the gnome-ppp dock notification icon.

(Hat tip: [http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/](http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/))
If nothing else it may help you or the next person to read it figure that problem out. But I guess it doesn't matter since ubuntu's so buggy for you. You know the old saying "You can't please all the people, all the time."
I wish you the best.

---

### Post by J_Stanton on 2010-04-07
"We can only take so much before we head for home." exactly why i left windows 3 years ago. ubuntu works perfectly for me and everyone i know. have fun with windows.

---

### Post by Nightstrike2009 on 2010-04-08
I have recently found this and I agree [http://www.sucka.net/2010/03/xubuntu-10-04-lucid-lynx-screenshots-tour/]("http://www.sucka.net/2010/03/xubuntu-10-04-lucid-lynx-screenshots-tour/")

> **By Nightstrike 2009**:I am typing this from my (New) OS right now Xubuntu 9.10 I have got around the 3g modem bug as I had to before and find Xubuntu to be more in keeping with what I wanted.

I already have a workaround for the modem bug 2hot6ft2, I posted it elsewhere on this forum [http://ubuntuforums.org/showthread.php?t=1398434&highlight=nightstrike2009]("http://ubuntuforums.org/showthread.php?t=1398434&highlight=nightstrike2009") (Post No10) but thanks for trying to help me out anyhow, I had to use wvdial and extract the DNS address and add it in the connection wizards fields.

(In Xubuntu you leave out the username and password fields if you don't want to be nagged over them) 

I believe Ubuntu has lost its way and could learn a lot from Xubuntu, I dont want a Mac and never will i prefer performance rather than overpricing and proprietry hardware chips so I can't use PC parts.

I want an Xubuntu only machine eventually, because even though I believe the 3g modem bug was an avoidable farce, I respect Linux's goals and enjoy being part of its community, software should be open-source that how open-minded people prefer it.

PS: I don't seek to flame or annoy these are my personal opinions and nothing more I respect all other Linux users we are all on the same team seeking similar goals we need to stick together not fall apart, nobody has a community like ours (like 2hot6ft2 has proven by offering assistance before). Despite Ubuntu's faults I have the deepest respect for its goals and morals, i just think it should be more reliable and stable than it is and hope 10.04 LTS will achieve just that, something we can all be proud off. :-)

PPS: I think this thread was started while I was having an off day, I am quite happy with Xubuntu and glad I am still part of the Ubuntu forums community. I may have been heading back to software home (Windows) but I guess home is where the heart is (Xubuntu) :-)

---

### Post by DrMelon on 2010-04-08
Too many people expect Ubuntu to be something it is not. This is Linux, not Windows. Things are done differently on a very fundamental level. Learn about it before using it, is all I can say.

---

### Post by Nightstrike2009 on 2010-04-08
I have DrMelon i am not just some noob having a rant, I have been using linux since Red Hat 3, and Ubuntu since 7.04. I am just annoyed that I manage to convert people (that also want to use Linux and learn it) over only to have them leave because of daft & avoidable flaws.

Your point is valid many "dip there toes in" expecting it to be windows, which it isn't and then leave. I am not one of those people I was an "Amiga Survivor" long before I bought a PC, and hated the fact I had to buy one just to have a home computer. We maxed out our Amigas with PC hardware modifications Like accelerator cards, ram, and PC hardisks until many of us had to admit defeat (Though a few still fight on to this day).

Thats why I am always drawn to Linux, I don't mind being different and never did, I actually enjoy it. :-)

---

### Post by PhilMize on 2010-04-08
The best way to get used to linux and be able to use it fully is to troll these forums. 

If you have a laptop, and certain parts are not working on it. There's probably a thread for it. If not just make one. I'm sure there's many others like yourself hoping for answers. If you guys met up in a thread and collaborated, that thread will get more attention. 

There's some vastly knowledgeable people here that are constantly lending a hand to others. That's how I got started using linux. I had a Lenovo Y510 laptop that I wanted to run linux on. Couldn't get a bunch of stuff to work, found a thread for it on here and like 5-6 pages later in a thread everything worked peachy on my Lenovo. And I made it all work. Myself. There's no moment in my computer using history that I'm more found and proud of. 

Since then, ( oct 2008 ) It's been down hill for me. I only use Windows for gaming and work. Even at work I use Ubuntu to access and control all the Window's & Mac machines I support. 

It's like the more you flex a muscle the better it is. Same goes for Linux. The more you use it, the better it gets.

You can't go into any OS and expect it to be flawless. I bet if you were solely a Mac user and went to use a Windows machine you'd be like wtf, and there would be some post on a Windows forum ranting about how unreliable it is. :)

---

### Post by pbpersson on 2010-04-08
Well.....okay....personal rant here......

I was just reading a thread on here last night and was going to comment but did not because I wanted to let the thoughts settle in my mind so I could say something coherent.

The thread was about the XServer changing - it is all becoming automatic so it does not need an xorg.conf file as I recall the thread.

In older versions when XServer would not start you could easily issue a command line directive to cause the system to create a new xorg.conf file.

This all changed so it no longer worked - all these people had these machines that would not work and they were all talking about scrapping Ubuntu and going to another distro.

Here is my beef - we have an OS which is COMMUNITY created and COMMUNITY supported - by community I mean from Linus Torvalds through the XORG people through the Gnome people down through the Ubuntu developers.  Yet **time and time again** I see things changed in a distro - no one knows how it was changed, who changed it, why, where the documentation is, or how to fix it!  I see poor users here on this forum randomly typing things into the command line hoping to trip across the right combination of commands to fix it and eventually after months they get the issue worked out.
[SIZE="5"][B]
WHAT THE HECK?????[/B][/SIZE]

Okay....end of rant.....now back to our regularly scheduled thread.  ;)

---

### Post by MarcusW on 2010-04-08
Care to elaborate a bit about the deb-files? Click install and it installs? :S (have you tried using the ubuntu software center instead btw? Even simpler)

pbperson, now instead of creating a new xorg.conf you *delete* the existing xorg.conf thus using the standard settings. I really don't see the problem. Can you give an example of these changes where none knows why, who etc?

---

### Post by Nightstrike2009 on 2010-04-08
It happened with two of the files in "Avant Window Navigator" from the repos and a few others. Users that don't have the internet have to download .deb packages just to use them (often from a windows machine) have enough to deal with clicking on multiple packages just to find some of the packages are broken and can't continue. (terminal download via apt-get can get around it but that isn't the point)

---

### Post by MarcusW on 2010-04-08
> **Nightstrike2009 said:**
> It happened with two of the files in "Avant Window Navigator" from the repos and a few others. Users that don't have the internet have to download .deb packages just to use them (often from a windows machine) have enough to deal with clicking on multiple packages just to find some of the packages are broken and can't continue. (terminal download via apt-get can get around it but that isn't the point)

I don't quite understand, the packages were broken? In what way is that the "deb-file system"s fault? (a tip: when installing many deb-files at the same time use "sudo dpkg -i ./*" instead of clicking, much faster and easier)

---

### Post by pbpersson on 2010-04-08
> **MarcusW said:**
> Care to elaborate a bit about the deb-files? Click install and it installs? :S (have you tried using the ubuntu software center instead btw? Even simpler)

pbperson, now instead of creating a new xorg.conf you *delete* the existing xorg.conf thus using the standard settings. I really don't see the problem. Can you give an example of these changes where none knows why, who etc?

[Here is the thread]("http://ubuntuforums.org/showthread.php?t=1306844&highlight=phigh") to which I was referring, it only took about five months to get the final answer on this for both Nvidia and ATI drivers.  If there was a an easy answer, these people REALLY needed it.

---

### Post by Nightstrike2009 on 2010-04-08
Argh don't get me started on Nvidia / Ati drivers that is a nighmare my first experience is always crashing my ubuntu graphics server serveral times, requiring a clean install before finding that i had right files and it was just hit n miss weather they worked or not. Then posing my findings here to hopefully spare others the pain. There is usually a very simple answer that gets far too complicated for some new users (Mainly due to endless pages of terminal commands and data dumps)

Thankfully 10.04 has Open-source ATI & Nvidia drivers capable of 3d effects, not upto the proprietary ones standard for gaming but more than usable otherwise, this is something that deserves praise as we have all suffered with that.

With Avant window navigator the debs on 9.04 that were faulty were:

avant-window-navigator_0.3.2-0ubuntu2_i386
awn-applets-c-core_0.3.2.1-0ubuntu3_i386
awn-applets-python-core_0.3.2.1-0ubuntu3_all
awn-manager_0.3.2-0ubuntu2_all

(All the above depended on each other and could not be installed outside of apt-get terminal commands)

I didn't keep a record for 9.10 although it too suffered on manually installation from .debs has i ended up using gnome-do with "Docky" instead.

PS: I now have an ATI card so I expect loads of fun trying to get that to work with a proprietry driver in 10.04 too, without crashing xorg server once again.

> **By MarcusW:** Care to elaborate a bit about the deb-files? Click install and it installs? :S (have you tried using the ubuntu software center instead btw? Even simpler)

PPS: I like to know what files do what thats why i use the .deb double-click way its slower but I learn more, I can wipe my own backside, I don't need apt-get to do it for me, but again thats just my way and my opinion. which is no less valid than yours, BTW "Ubuntu Karmic Koala (testing)" Isn't 9.10 finished now, why are you still "testing" surely you should be (Testing) 10.04 by now or using 9.10 final. LMAO

We are all free to use Linux anyway we wish, thats the beauty of it. :-)

---

### Post by J_Stanton on 2010-04-08
> **Nightstrike2009 said:**
> Argh don't get me started on Nvidia / Ati drivers that is a nighmare my first experience is always crashing my ubuntu graphics server serveral times, requiring a clean install before finding that i had right files and it was just hit n miss weather they worked or not./>

it sounds to me that your computer is not linux compatible. if it was, you would not be having these problems. consider buying/building one that is, and these problems go away. i built one to run linux and it has been the best experience i can imagine. people buy windows machines, they buy mac machines, why not buy a linux machine instead of trying to fit a square peg into a round hole?

---

### Post by MarcusW on 2010-04-09
> **Nightstrike2009 said:**
> Argh don't get me started on Nvidia / Ati drivers that is a nighmare my first experience is always crashing my ubuntu graphics server serveral times, requiring a clean install before finding that i had right files and it was just hit n miss weather they worked or not. Then posing my findings here to hopefully spare others the pain. There is usually a very simple answer that gets far too complicated for some new users (Mainly due to endless pages of terminal commands and data dumps)

Thankfully 10.04 has Open-source ATI & Nvidia drivers capable of 3d effects, not upto the proprietary ones standard for gaming but more than usable otherwise, this is something that deserves praise as we have all suffered with that.

With Avant window navigator the debs on 9.04 that were faulty were:

avant-window-navigator_0.3.2-0ubuntu2_i386
awn-applets-c-core_0.3.2.1-0ubuntu3_i386
awn-applets-python-core_0.3.2.1-0ubuntu3_all
awn-manager_0.3.2-0ubuntu2_all

(All the above depended on each other and could not be installed outside of apt-get terminal commands)

I didn't keep a record for 9.10 although it too suffered on manually installation from .debs has i ended up using gnome-do with "Docky" instead.

PS: I now have an ATI card so I expect loads of fun trying to get that to work with a proprietry driver in 10.04 too, without crashing xorg server once again.



PPS: I like to know what files do what thats why i use the .deb double-click way its slower but I learn more, I can wipe my own backside, I don't need apt-get to do it for me, but again thats just my way and my opinion. which is no less valid than yours, BTW "Ubuntu Karmic Koala (testing)" Isn't 9.10 finished now, why are you still "testing" surely you should be (Testing) 10.04 by now or using 9.10 final. LMAO

We are all free to use Linux anyway we wish, thats the beauty of it. :-)

You can still learn what they do, just have a look in synaptic or with "aptitude show". Downloading debs from http is more complicated, less safe, and it won't get updates automatically. (like security updates) Considering that the installs failed when you didn't use APT, it does sound like you "need it to wipe your backside". ;) No offense intended ofc. :)

When you have packages depending on eachother, just put them in the same folder and type "sudo dpkg -i ./*" a couple of times and it will work. :) Had to do that once because debian didn't feel networkmanager was necessary at a base install...

I'm using Debian now, so changing to 10.04 or 9.10 final wouldn't be more true. ^^

---

### Post by Nightstrike2009 on 2010-04-09
I guess I deserved that MarcusW, you obviously know what your doing LOL. I've came across elitists that knew less than me telling me how to suck eggs, and jumped to the wrong conclusion.

I have great respect for debian and would use it myself, only for some reason the Debian iso's dont seem to boot on my machine. I prefer deb based packages to rpm's any day.

---

### Post by Nightstrike2009 on 2010-04-09
> By J_Stanton: It sounds to me that your computer is not linux compatible. if it was, you would not be having these problems. consider buying/building one that is, and these problems go away. i built one to run linux and it has been the best experience i can imagine. people buy windows machines, they buy mac machines, why not buy a linux machine instead of trying to fit a square peg into a round hole? 

Its little more than a year old and all programs including NVIDIA/ATI drivers work with this machine. Its internal hardware is compatible with linux as it was designed to be that way, it isn't a shop build but a custom built model.

I had no problems with Ubuntu 9.04, the faults lie with 9.10 bug has many other ubuntu users have reported the same issues. Linux is always hit and miss hardware wise (Some machines are lucky others are not) but as we have done the answer is to by a PC to run linux rather than windows.

PS: Kinda think this thread is derelict now, has I learned of Xubuntu and now use 10.04 Beta 1 of Xubuntu and love it. (So still a form of Ubuntu user I guess) LOL

---

### Post by WinterRain on 2010-04-09
Great to hear you've found something that works. I wish you the best of luck.

---

### Post by Tamlynmac on 2010-04-09
> WinterRain
Great to hear you've found something that works. I wish you the best of luck. 	

Well said. 8-)

It's been my experience, that debating with someone who already has a mindset is generally non-productive. It's best to just wish them well and hope they enjoy their OS of choice. Which IMHO is what Linux/FOSS is all about - Choice.

When put in perspective, we shouldn't even be using this section for debating purposes based on it's guidelines.

I also agree with your statement wishing the OP the best of luck.

---

### Post by Nightstrike2009 on 2010-04-11
(Nightstrike pulls foot out of mouth)

After using Xubuntu which I was (and still am impressed with) i tried to get some handy packages working, the dependancy list was far higher than ubuntu and Compiz was nigh on impossible to enable even with what i assumed to be correct packages.

So rather embarrasingly I am drawn back to Ubuntu 10.04 Beta (But this time v2) has I think it should be easier to install "xubuntu-desktop" package into that and choose between each in ubuntu's session manager.

PS: I did say i think i was having a bad day, Ubuntu's a bit like a magnet to me I keep giving up because experiencing stupid bugs (I mean essential bugs like no modem connection, not a package that doesn't work that I can easily source an alternative for), then end up drawn back to a later Ubuntu version.
E.g. If "brasero" doesn't work with your cd/dvd burner use "Gnomeburner" instead it worked for me.

PPS: I also forgot that XX.04 releases are often more stable than XX.10 ones too (In my own opinion)

---

### Post by Glucklich on 2010-04-11
I like Xubuntu more than the original Ubuntu as well. In fact, I've used it for a looong time. But... Lubuntu Beta 1 rocked so ******* much! I'm a bit surprised why the Beta 2 isn't out yet... I thought keeping up with the main releases was an important factor for being approved by Canonical. Still, I believe it will be one of the best *buntu's EVER!

---

