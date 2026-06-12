---
title: "my neighbor's computer part 2"
date: 2006-02-18
forum: The Cafe
---

### Post by fuscia on 2006-02-18
i tried to run *services.msc*, on xp, and i got a denial message. i'm signed in as owner. i don't know xp and they have no idea what they're doing. i'm trying to get more speed into this thing. (400mhz, 256ram) thanks.

---

### Post by prizrak on 2006-02-18
[QUOTE=fuscia]i tried to run *services.msc*, on xp, and i got a denial message. i'm signed in as owner. i don't know xp and they have no idea what they're doing. i'm trying to get more speed into this thing. (400mhz, 256ram) thanks.[/QUOTE]
XP won't be running fast on that EVER. Services control is in the Administrative tools tho

---

### Post by rfruth on 2006-02-18
More speed out of a 400 Mhz box with 256 Meg of RAM, throw it as far as you can (ok recycle) then get a real computer ...

---

### Post by fuscia on 2006-02-18
[QUOTE=prizrak]XP won't be running fast on that EVER. Services control is in the Administrative tools tho[/QUOTE]


sorry, i meant 'less slowly'. 

i'm getting the same error going through admin. tools as well.

edit: got in through msconfig

---

### Post by mstlyevil on 2006-02-18
[QUOTE=fuscia]i tried to run *services.msc*, on xp, and i got a denial message. i'm signed in as owner. i don't know xp and they have no idea what they're doing. i'm trying to get more speed into this thing. (400mhz, 256ram) thanks.[/QUOTE]

Very odd. Since you are signed is as owner it should work. Check to see what permissions are on the account by going to the control panel and click on user accounts. Then select that account and see what type of account it says it is. If it says user then the account does not have admin priviledges. You could go into safe mode by typing F8 during the boot up process and just use the Administrator account. It is it's own seperate account and will actually be called administrator. Services.msc will definately work there unless the pc has been completely hijaced by malware. In that case the only way to fix it will be a fresh install. (I would just do a fresh install anyway after backing up all the data.)

---

### Post by bjweeks on 2006-02-18
[QUOTE=fuscia]sorry, i meant 'less slowly'. 

i'm getting the same error going through admin. tools as well.

edit: got in through msconfig[/QUOTE]

Don't edit services in msconfig.

---

### Post by WildTangent on 2006-02-18
[QUOTE=mstlyevil]You could go into safe mode by typing F8 during the boot up process and just use the Administrator account. It is it's own seperate account and will actually be called administrator.[/QUOTE]
You don't need to be in safe mode to do that. Log out of all accounts (IE: not switching users), and then hit ctrl+alt+del at the welcome screen twice, this gives you the old-school login prompt, type in "Administrator" with no pass, and login.

/me fixes way too many Windows computers...

-Wild

---

### Post by mstlyevil on 2006-02-18
[QUOTE=WildTangent]You don't need to be in safe mode to do that. Log out of all accounts (IE: not switching users), and then hit ctrl+alt+del at the welcome screen twice, this gives you the old-school login prompt, type in "Administrator" with no pass, and login.

/me fixes way too many Windows computers...

-Wild[/QUOTE]

Kewl, I learned something new.

---

### Post by fuscia on 2006-02-19
so here's the latest...

i finally got into services via *msconfig*. using this page as a guide [http://www.theeldergeek.com/services_guide.htm](http://www.theeldergeek.com/services_guide.htm) i unchecked everything declared 'unnecessary'. when it said it was possibly necessary, i only unchecked it if i knew what it was and if i were sure it wasn't necessary. i clicked 'apply', it asked me if i wanted to restart, i clicked 'yes'. it went down to reboot and came back on to the ibm screen and never rebooted. eventually, there was a message saying that windows couldn't be loaded as there had been some interruption of some kind. it then said to pick one of the options, or hit enter. there were no options listed, so i hit 'enter'. again, nothing happened, so i turned off the power and tried again and again and got the same thing each time. i tried starting it up while hitting F1, but nothing happened. i tried starting it up while hitting F8, but again, nothing happened. i tried booting an ubuntu livecd, but nothing happened (i checked the boot order the last time i took a look at this thing, and i'm sure it was set up to boot off a cd). they said it has been taking longer to reboot each time.

the first thing they had asked me about tonight was how to keep their computer on all the time. they had it set for hibernate. i selected 'always on' in all the places that option was offered. 

so, any ideas what's going on with this thing? i can't imagine that anything i did could have caused this, but i want to eliminate that notion. most importantly, i'd like to know if there is anything i can do to rescue this thing. they're all cool and had anticipated this thing throwing a shoe for some time now. they have another computer that someone gave them that's a little old, but could be pretty usable.

---

### Post by mstlyevil on 2006-02-19
[QUOTE=fuscia]so here's the latest...

i finally got into services via *msconfig*. using this page as a guide [http://www.theeldergeek.com/services_guide.htm](http://www.theeldergeek.com/services_guide.htm) i unchecked everything declared 'unnecessary'. when it said it was possibly necessary, i only unchecked it if i knew what it was and if i were sure it wasn't necessary. i clicked 'apply', it asked me if i wanted to restart, i clicked 'yes'. it went down to reboot and came back on to the ibm screen and never rebooted. eventually, there was a message saying that windows couldn't be loaded as there had been some interruption of some kind. it then said to pick one of the options, or hit enter. there were no options listed, so i hit 'enter'. again, nothing happened, so i turned off the power and tried again and again and got the same thing each time. i tried starting it up while hitting F1, but nothing happened. i tried starting it up while hitting F8, but again, nothing happened. i tried booting an ubuntu livecd, but nothing happened (i checked the boot order the last time i took a look at this thing, and i'm sure it was set up to boot off a cd). they said it has been taking longer to reboot each time.

the first thing they had asked me about tonight was how to keep their computer on all the time. they had it set for hibernate. i selected 'always on' in all the places that option was offered. 

so, any ideas what's going on with this thing? i can't imagine that anything i did could have caused this, but i want to eliminate that notion. most importantly, i'd like to know if there is anything i can do to rescue this thing. they're all cool and had anticipated this thing throwing a shoe for some time now. they have another computer that someone gave them that's a little old, but could be pretty usable.[/QUOTE]

Do they have a windows install CD? If they do it might be time just to do a clean install. It actually is a good idea to reinstall Windows at least once a year. You could also suggest they try Ubuntu for a few weeks and see if they like it.

---

### Post by TechSonic on 2006-02-19
[QUOTE=mstlyevil]Kewl, I learned something new.[/QUOTE]


Same here, although it would of been nice to know that 3 years ago.


[QUOTE=mstlyevil]It actually is a good idea to reinstall Windows at least once a year.[/QUOTE]

QFT

---

### Post by fuscia on 2006-02-19
[QUOTE=mstlyevil]Do they have a windows install CD? If they do it might be time just to do a clean install. It actually is a good idea to reinstall Windows at least once a year. You could also suggest they try Ubuntu for a few weeks and see if they like it.[/QUOTE]

but i couldn't even get the ubuntu livecd to boot. i don't think an installation of any kind is possible in it's current state.

---

### Post by mstlyevil on 2006-02-19
[QUOTE=fuscia]but i couldn't even get the ubuntu livecd to boot. i don't think an installation of any kind is possible in it's current state.[/QUOTE]

It could be bad RAM or a fried Motherboard then. I would actually have to be there to really tell what is wrong.

---

### Post by bascha on 2006-02-19
Are you able to get in the BIOS??

---

### Post by fuscia on 2006-02-19
[QUOTE=bascha]Are you able to get in the BIOS??[/QUOTE]

not at all. all i get is a bunch of beeping when i hit F1. 

[quote=mstly]
It could be bad RAM or a fried Motherboard then. I would actually have to be there to really tell what is wrong.[/quote]

the fried motherboard thought had occured to me. apparently, the ram is newish.

---

### Post by mstlyevil on 2006-02-19
[QUOTE=fuscia]not at all. all i get is a bunch of beeping when i hit F1. 



the fried motherboard thought had occured to me. apparently, the ram is newish.[/QUOTE]

Are they willing to spend a few hundred dollars to upgrade the pc? They could buy a motherboard, CPU and new RAM for the computer to put new life in that old computer.

---

### Post by bascha on 2006-02-19
You could always try to re-seat the ram or if you have another stick, give that a try.

---

### Post by mstlyevil on 2006-02-19
[QUOTE=bascha]You could always try to re-seat the ram or if you have another stick, give that a try.[/QUOTE]

Good suggestion. Also it is not unheard of to buy bad RAM especially if it is generic.

---

### Post by fuscia on 2006-02-19
[QUOTE=mstlyevil]Are they willing to spend a few hundred dollars to upgrade the pc? They could buy a motherboard, CPU and new RAM for the computer to put new life in that old computer.[/QUOTE]

i'm going to set up the computer they just got from her dad, tomorrow. hopefully that one will be in better shape. if not, they're talking a trip to best buy. mrs. fuscia suggested they get a laptop, which would be good for them.

---

### Post by fuscia on 2006-02-19
[QUOTE=bascha]You could always try to re-seat the ram or if you have another stick, give that a try.[/QUOTE]

i've got a 64mb stick that might be compatible. i'll give it a shot, but that may not be enough to do anything. they have two 128mb chips in there now.

---

### Post by bascha on 2006-02-19
Just recently I had 1 of my 512MB sticks of Corsair Value select go bad on me.  Was still able to get to the desktop but was having constant crashes and very unusual behavior, even for windows.  Memtest indicated a memory error problem and changing the stick solved everything.

I too recently was working on a 400mHz IBM with 256MB RAM for a friend but it was running Win98 and only had networking issues.  Was seriously considering installing ubuntu on it

good luck

---

### Post by fuscia on 2006-02-19
[QUOTE=bascha]Just recently I had 1 of my 512MB sticks of Corsair Value select go bad on me.  Was still able to get to the desktop but was having constant crashes and very unusual behavior, even for windows.  Memtest indicated a memory error problem and changing the stick solved everything.

I too recently was working on a 400mHz IBM with 256MB RAM for a friend but it was running Win98 and only had networking issues.  Was seriously considering installing ubuntu on it

good luck[/QUOTE]

i suspect they secretly want it to be dead so they can get something new. i'll give the memory a few twists and tugs and see how the other machine is (maybe i can swithc its memory out before i pronounce the poor bastard dead).

thanks, everyone, for participating. i knew i would get a lot of help on this one. i appreciate it, quite a bit.

---

### Post by disabled_20220313 on 2006-02-19
[QUOTE=fuscia]i suspect they secretly want it to be dead so they can get something new. i'll give the memory a few twists and tugs and see how the other machine is (maybe i can swithc its memory out before i pronounce the poor bastard dead).
[/QUOTE]

If you think that then usually trying to fix the computer isn't the problem. 

Try to fix the user. Just sit down and talk to them. I've done this with quite a few of my friends and their families. They try to run the newest games, most up to date version of Windows OS, or Office, on their aging machine and end up having loads of trouble.

Explaining the limitations of their computers, and giving them alternatives to the most up to date stuff will mean they have little trouble. I usually set up a Win98SE machine (with all the needed anti-virus etc), with a little CD wallet of applications. 

Once they understand that each new version of software requires a faster and faster processor then they usually understand that they can't just use it easily without a faster computer.

At this point they ask about new computers usually. Again give the best advice you can. Most of the families I dealt with only needed a low-powered computer, as they had consoles a plenty to play games on.

---

### Post by Netisan on 2006-02-19
A paradox:
The better computer one owns - the less demands one has. It's from my observations.

---

### Post by Alpha_toxic on 2006-02-19
Suggestion:
If it beeps, there is still hope. Try finding out the exact model of the motherboard, then google for the manual. It should say what exactly the beeps mean. Sth like "beeeeeep-bep-beeeep"="bad memory" and etc.
Good luck :)

---

### Post by fuscia on 2006-02-19
[QUOTE=Alpha_toxic]Suggestion:
If it beeps, there is still hope. Try finding out the exact model of the motherboard, then google for the manual. It should say what exactly the beeps mean. Sth like "beeeeeep-bep-beeeep"="bad memory" and etc.
Good luck :)[/QUOTE]

the beep, quite clearly, is a 'stop hitting the F1 key, dickface' type of beep, which i found out is also the 'stop hitting the F8 key, dickface' beep.

---

### Post by majikstreet on 2006-02-19
maybe you could download SLAX popcorn, change some modules, add some.. like remove XFCE and make it boot into fluxbox which is in popcorn, add some stuff like abiword, and other useful stuff... show them it, let them play around, then you could maybe install it to their hard drive :D

---

### Post by fuscia on 2006-02-19
[QUOTE=majikstreet]maybe you could download SLAX popcorn, change some modules, add some.. like remove XFCE and make it boot into fluxbox which is in popcorn, add some stuff like abiword, and other useful stuff... show them it, let them play around, then you could maybe install it to their hard drive :D[/QUOTE]

is slax an irish distro? (see pic below) this could be the coolest thing since we built the pyramids.

[img]http://storetn.cafepress.com/6/17844506_F_store.jpg[/img]

---

### Post by majikstreet on 2006-02-19
mm... I don't think it's Irish.. The guy could be norwiegan or something but I dunno! lol

---

### Post by DigitalDuality on 2006-02-19
400Mhz, 256M of Ram.. it should work.  After spending almost a year at the job i'm at which is full of cheapscapes and crooks who refuse to buy employee's new machines.. tweaking them to run faster on P2s and P3s is a daily chore for me.  This should help out a great deal:

**Speed up XP**

**Increase Virtual memory/Paging File**

Also ensure your paging file is at least double your RAM.  In windows do the following:

Start
Control Panel
Administrative Tools
Computer Management

Right Click Computer Management Icon at the top
Properties
Advanced Tab 
Performance Settings button 
Virtual Memory Change button 
Change the Initial Size of the paging file (make sure Max size is more than initial).  

Hit Ok. Ok. Ok.  Restart.

This will increase your virtual memory on the machine, which can speed things up a bit at times.

**Get rid of un-necessary effects**
1.  Right click on your desktop, change XP theme to use Windows Classic
2. Go to the Appearance tab; Effects Button
3. Make sure these are unchecked:
Use the following transistion effect for menus and tooltips
Use the following method to smooth edges of screen fonts
show shaddows under menus
Show window contents while dragging

This will change alot of the same settings as above, and more:
   1. Open Control Panel from the Start menu and choose System
   2. Choose the Advanced tab.
   3. Select the Settings button under the Performance section.
   4. Check the Adjust for best performance box and click Apply to apply the settings.
   5. Alternatively, you can choose the Custom, open, you can then selectively enable or disable each specific effects.


**Start Menu and Taskbar**

      Context click (usually known as Right click) on the Windows XP Start button and choose Properties from the contextual menu.
   1. Choose Classic Start Menu
   2. Click the Customise button
   3. Select the Show Small Icons in Start Menu option
   4. Unselect any other items that you don't use often.

**Folder Options**

   1. Open My Computer
   2. Open the C: Drive or any other drive
   3. Choose Folder Options from the Tools menu
   4. Select Use Windows classic folders
   5. Select the View tab.
   6. Unselect the Automatically search for network folders and Printers option.
   7. Click Apply
   8. Click the Apply to All Folders button
   9. Click OK.

**Disable Messenger Service**
Start-
Settings
Control Panel
Administrative Tools
Services 
and disable MESSENGER service

**Disable as many start up items as possible**
Start 
Run 
Type msconfig 
Startup Tab 
 Uncheck all familiar items you know you do not need.  If you are unsure, probably best to look it up (Google) to see what it is.  Stuff like MS Office, OpenOffice quick starter, AIM, HP printing services, iTunes, Real, all should be unchecked.

**Defrag**
Start
Control Panel
Administrative Tools
Computer Management
Defrag option is in the left column.

And of course.. run scans for spyware and remove them.  I recommend using Lavasoft's Ad Aware and Spybot Search and Destroy. (both have very different definition files)

---

### Post by bascha on 2006-02-19
[QUOTE=fuscia]is slax an irish distro? (see pic below) this could be the coolest thing since we built the pyramids.

[img]http://storetn.cafepress.com/6/17844506_F_store.jpg[/img][/QUOTE]

Distrowatch has its origin listed as Czech

Great live cd but have never installed to hard drive.

---

### Post by Tinuz on 2006-02-19
Well, maybe a little late, but okay. 
I've always found that people(mostly windows users) are simply afraid to learn new things. I once knew someone who had a state-of-the-art computer(back then atleast) but didn't dare to use it because he might crash something. I once thought to wreck it for him personally and have him fix it himself, but okay. 
Anyways, simply pushing people to use new things works often. People get over their initial fear, they find that most things aren't really that difficult and that computers actually behave quite predictably when you get to know them. Also, people get a sense of satisfaction out of it, they just learned something new, something which other people can't do. 
It usually works for me, you just have to find an excuse to get people to try new stuff.

---

### Post by Mr_J_ on 2006-02-19
Sorry it's so late...

The BIOS warning beeps are indicators of errors that in the old days you searched for in a large heavy book that allowed you to translate beeps into warnings like morse code.

Of course there is the common "don't touch me!" warning beep one can get ocasionally...

The most common ones are RAM and HardDrive jumper configurations.
Some times... With PS/2 you can mix them up, but earlier non PS/2 you just can't switch them wrongly.
Of course, and this is from annoying experience, some Motherboard NEED a floppy drive. Busted if you have it, but it has to be there. Good or not. Took me a few hours of staring into air to figure it out... Sounds about the same time as yours should be.

Just crack it open; if you did so before; and make sure you got everything right and stuck tight.

---

### Post by fuscia on 2006-02-19
they turned it on today and it booted up. even though i turned off half the services on it, it is apparently running as it always has. i set everything to 'always on', so i think i will suggest they just use it as is until it dies, or they can't take it anymore.

[quote=tinuz]Anyways, simply pushing people to use new things works often.[/quote]

i prefer to help them do what they want to do. if they want to stick with this mess, that's fine with me. i know they'd be better off running a stripped down linux, but i don't want to be that intrusive. they do so little with the thing.

---

### Post by mstlyevil on 2006-02-19
[QUOTE=fuscia]they turned it on today and it booted up. even though i turned off half the services on it, it is apparently running as it always has. i set everything to 'always on', so i think i will suggest they just use it as is until it dies, or they can't take it anymore.[/QUOTE]

Computers sometimes just have a mind of their own. ( I think it could have been a heat issue causing the problem.)

---

### Post by fuscia on 2006-02-20
[QUOTE=mstlyevil]Computers sometimes just have a mind of their own. ( I think it could have been a heat issue causing the problem.)[/QUOTE]

my fan died about a year and a half ago. i had no clue and things started getting all kinds of weird. i was getting all kinds of complicated advice about this, that and the other thing when, finally, someone asked "hey moron, is your fan still working?" (what fan? :confused: )

---

