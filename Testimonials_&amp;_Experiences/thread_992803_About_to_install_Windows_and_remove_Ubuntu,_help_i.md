---
title: "About to install Windows and remove Ubuntu, help is needed"
date: 2008-11-25
forum: Testimonials &amp; Experiences
---

### Post by VitaminBB on 2008-11-25
Ive about had it ...

So I had things going along swimmingly (or so I thought) but the constant tweaking to get things even stable is baffling to me and today I have been smacked around so much that im on the verge of saying "screw this" and installing windows xp.

Let me run down the list of things driving me back to Windows, if you can help thats awesome, if not I have a copy of tinyxp here I can install and not have to be driven mad by linux and its constant annoyances.

The problems right now are listed below, Ill start with the most urgent ...




**_Problem number 1:_**

**[COLOR="Blue"]My wireless connection has disappeared.[/COLOR]**

The network applet is running just fine and as long as the rj-45 is plugged in im connected but when I click on the applet to chose a wireless connection theres nothing there, only a wired connection.

I can see the wireless tab under "edit connections", all my router information including SSID and WEP key is listed there, nothing has been changed but it wont login to the router and the network applet doesnt even show the option to select wireless networks.

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/1222.jpg[/IMG]

Yes, my wifi card is switched on.

This seems to have something to do with a keyring issue which seems to be associatd with the fact that I set my laptop to log in automatically (see bug [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247)), at that time I also recieved this message "Enter Password for Default Keyring to Unlock" which I guessed was my login password, luckily I was right, later I restarted my laptop and I didnt get the keyring message and the wireless connection still didnt display under the network applet.  

I used searhorse and deleted the keyring, like this, 

[B]alt F2 seahorse
edit --> preferences
select "login keyring"
delete keyring[/B]

Now when I login it still doesnt ask me for the password and the wirelss connection still wont show in the network applet.

At the end of my rope with this one, thought about smashing my laptop but figured just going back to windows might be smarter.
[I][U]
Oh but there more![/U][/I]




**_Problem number 2:_**

[COLOR="Blue"]**Emerald is a P.O.S.**[/COLOR]

So I played around with some themes and after much frustration with how stupid the theme system seems to be I realized that Emerald had never worked properly for me, through the great Ubuntu forums I learned that Emerald is a bitch and sometimes just decides it doesnt want to load, so I read a lot and figured out how to force Emerald to load and play nice everytime I login, this worked but now, specifically right after I logged in when the wireless network bullsnot started, now maybe 1 or 2 minutes into my login Emerald decides to die on me, no clue why and Alt+F2 wont work, how convienient! so as im typing this im just waiting for Emerald to die on me and the titlebars to disappear, then I wont be able to navigate! cant wait!




**_Problem number 3:_**
[B][COLOR="Blue"]
My right-click sometimes decides it wants to do other tasks
[/COLOR][/B]
This is an issue I noticed from day one but attributed to my lack of an expensive mouse.  It seems occasionally and entirely randomly from what I can see, my mouse decides that when I do a right click what I really am trying to do is download a page OR what I really wanted to do was open a new window or what I really wanted to do was launch something else ...

After trying several mice I realize that this issue is with Ubuntu and I cant figure it out, for the most part its fine but probably 5 times a day it decides to do something completely different when I right-click, I tried to search the net for a solution to this but I would get confusing results since "right-click mouse problems" gave me a crapload of links that did nothing for me.  

Any ideas on this one are appreciated as always ...




**_Problem number 4:_**

[COLOR="Blue"]**Why is it the shutdown/dropdown menu in the right corner sometimes shows a restart and shutdown option but sometimes shows the options shown in the image below?**[/COLOR]

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/1221.jpg[/IMG]

I dont get it, at times when I click this drop down box I get several options but other times I see only what you see right there, why doesnt it work the same all the time? heck if I know! Im starting to think the answer is "Pssst, cause its Ubuntu and it cant make its mind up, plus it secretly hates you and is trying to drive you insane".




**_Problem number 5:_**

**[COLOR="Blue"]I cant uninstall evolution-data-server without uninstalling ubuntu-desktop.[/COLOR]**

This was the largest annoyance up until I realized that ignoring it was the best route, thinking there were answers to Ubuntu problems seems to be the first problem.

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/pic2.jpg[/IMG]

I still dont have an answer to this, never will and im mostly ok with it, though since im airing grievances it needs to be here.  I dont know why I cant uninstall a part of evolution without ruining the rest of my installation and neither does anyone else, like I said, thinking there was an answer was probably the first mistake.




**_Problem number 6:_**

**[COLOR="Blue"]Remapped "windows" key wont work no matter what I try[/COLOR]**

So I mapped out the super key to open my email client and after setting the key and resetting and checking and rechecking I only seem to be able to set the key but it never works, I press the button afer setting it to many different options and nothing opens, ever and my heart sinks and my inner child dies a little more, thanks Ubuntu!




**_Problem number 7:_**

**[COLOR="Blue"]Compiz demoted itself.[/COLOR]**

So after an update Compiz decided it wanted to reset itself to basic options, not a deal breaking annoyance but enough of a hassle that I included it in this list.

[CENTER]
:confused::(:confused::(:confused:[/CENTER]

Some of these are old issues, two of them including the wireless network option disappearing from the network panel and Emerald being a bitch seemed to happen today after I did an update.

P.S. *Emerald just died on me right as I was making an image to add to this post, great!*

---

### Post by Wickd on 2008-11-25
What distro are you using?

---

### Post by roshanjose on 2008-11-25
r u using ubuntu 8.10 intrepid ibex

---

### Post by VitaminBB on 2008-11-25
> **roshanjose said:**
> r u using ubuntu 8.10 intrepid ibex

Yup, latest version Ubuntu 8.10 ...

---

### Post by Sub101 on 2008-11-25
For the network not appearing try "Connect to Hidden Network". I know your network is not hidden but it seems to be a bug a few people are having.

And as for the superkey: Just go to System ==> Preferences ==> Keyboard Shortcuts. Works fine for me like that as it launches a terminal.

---

### Post by peter_brewer on 2008-11-25
Regarding your first problem has the wireless ever worked and connected?

Not sure about emerald stuff as never used it.

Mouse wise are you moving the mouse when you click, that sometimes brings up other options.

I don't use Gnome so not sure about the logoff shoutdown thing, I'm curious as to whether you get different options if you click on the symbol looking like a power button in the top right hand corner to when you click on the text next to it.

The removing of ubuntu-desktop won't trash your machine.  Its a package which depends on every package needed to make the default ubuntu install, it is handy in that if you choose to install it you ensure that all the base packages are installed, you can however remove it quite safely.

The other questions I am not sure of, I use kde as part of kubuntu so don't have any of these issues.  If you continue to have this many issues may I suggest you try something like kubuntu or alternatively a different linux distribution.

---

### Post by mikewhatever on 2008-11-25
[HOWTO INSTALL XP]("http://theeldergeek.com/xp_pro_install_-_graphic.htm"). Good luck.

---

### Post by VitaminBB on 2008-11-25
> **peter_brewer said:**
> Regarding your first problem has the wireless ever worked and connected?

Yes, always worked ...

> Mouse wise are you moving the mouse when you click, that sometimes brings up other options.

Negative, I thought about that too but it doesnt seem to matter, I can hold it perfectly still and click it and have it screw up.

> I don't use Gnome so not sure about the logoff shoutdown thing, I'm curious as to whether you get different options if you click on the symbol looking like a power button in the top right hand corner to when you click on the text next to it.

Nope, click on the symbol or click on the username, same options, either no restart or what u saw in the first post.

> The removing of ubuntu-desktop won't trash your machine.  Its a package which depends on every package needed to make the default ubuntu install, it is handy in that if you choose to install it you ensure that all the base packages are installed, you can however remove it quite safely.

Good to know, thanks for that, learned something new ...

> The other questions I am not sure of, I use kde as part of kubuntu so don't have any of these issues.  If you continue to have this many issues may I suggest you try something like kubuntu or alternatively a different linux distribution.

Thats an idea but ive dabbled in KDE and it seems less friendly then Gnome, might just be my perception *shrug* ...

---

### Post by VitaminBB on 2008-11-25
> **Sub101 said:**
> For the network not appearing try "Connect to Hidden Network". I know your network is not hidden but it seems to be a bug a few people are having.

I dont even see an option to connect to a hidden network anymore, I posted an image of what im talking about above, youll see what I mean.

> And as for the superkey: Just go to System ==> Preferences ==> Keyboard Shortcuts. Works fine for me like that as it launches a terminal.

Thats what I did, apparently it understands that I pressed the super key but no matter what I set the super key as it never works, I press it and nothing happens *shrug* ...

---

### Post by nothingspecial on 2008-11-25
For your wireless which I suppose is the main annoyance try wicd -

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I find it works much better than network-manager.

Be warned though, installing wicd removes network-manager so if wicd doesn`t work for some reason, getting n-m back will be tricky if you don`t have a wired connection.

---

### Post by CatKiller on 2008-11-25
> **VitaminBB said:**
> So I mapped out the super key to open my email client and after setting the key and resetting and checking and rechecking I only seem to be able to set the key but it never works, I press the button afer setting it to many different options and nothing opens, ever and my heart sinks and my inner child dies a little more, thanks Ubuntu!

I'm not sure that this would work. As I understand it, the Super key is treated as a modifier, like Alt or Shift, rather than as a key on its own. So Win+m, say, might work as a shortcut when just Win doesn't. There may well be a way to make the Windows key behave differently in the keyboard settings. Unless you're using a different key as Super, in which case replace the references to the Windows key with the key that you're using.

---

### Post by Sub101 on 2008-11-25
Out of interest? In order to set the keyboard shortcut you need to ensure you have the correct email client as the default program.

---

### Post by davidbilla on 2008-11-25
System->Preferences->Keyboard Shortcuts : Just the Super key for 'Minimize all windows and show desktop'. Works fine in Hardy.

And... I believe Left and Right Super Keys are treated as different. I'll try to look into the other things. But if a fresh install is all that you have in mind, be it that of Intrepid again!

Or... you can just replace certain system files with those in your live cd, if you know what you're doing. For example, if X11 has problems, just replace the contents of your /etc/X11/ with that of /etc/X11/ from your live cd. No need to install afresh, I believe.

---

### Post by VitaminBB on 2008-11-25
> **CatKiller said:**
> I'm not sure that this would work. As I understand it, the Super key is treated as a modifier, like Alt or Shift, rather than as a key on its own. So Win+m, say, might work as a shortcut when just Win doesn't. There may well be a way to make the Windows key behave differently in the keyboard settings. Unless you're using a different key as Super, in which case replace the references to the Windows key with the key that you're using.

That makes lots of sense, ill bet thats why it never works ...

Now I have to figure a way to change its behaviour ...

Thanks!

---

### Post by Sub101 on 2008-11-25
> **CatKiller said:**
> I'm not sure that this would work. As I understand it, the Super key is treated as a modifier, like Alt or Shift, rather than as a key on its own. So Win+m, say, might work as a shortcut when just Win doesn't. There may well be a way to make the Windows key behave differently in the keyboard settings. Unless you're using a different key as Super, in which case replace the references to the Windows key with the key that you're using.

Not true for me. I press it and it works. I do not use it as a modifier. Just one press.

---

### Post by Kellemora on 2008-11-25
Hi VitaminBB

Not much on your list, would you like me to add about 100 more!

Ubuntu seemed great to me too, until I converted my entire office over to it!

There are just so many things we were used to that JUST WORKED in the DOZE that even the best guru's for Ubuntu can't seem to figure out!

Our first and formost Major problem is the LAN works then don't work, works then don't work, and if you don't do things a certain way, all your permissions get messed up.

We cannot BackUp to a remote hard drive using any automation available in Ubuntu, we can be hand no problem, but get stupid errors on simple files we use every single day.  They are flagged as an invalid and not backed up.

No controls for the center mouse button, the one under the wheel!

No way to change the toner cartridge in a software driven laser printer.

We have one computer that is not recognized on the LAN, yet it is set up IDENTICAL to the other 7 computers (except for IP numbers of course).

What works perfectly one day, does not work the same way the next day!

There is absolutely no way to specify what size to format a floppy disk, and so far the ONLY format we can get to work on ANY floppy drive is to use the FAT file system, EXT2 does not work nor is recognized by Ubuntu.

Not Ubuntu's fault that Manufacturers do not support their equipment on Linux!
But, some of the most popular hardware ever sold is NOT SUPPORTED.
Virtually no Front Office equipment is supported in any way shape or fashion.

We had to revert back to XP on two machines in order to handle normal everyday business affairs such as ACCOUNTING...........
And we gave all the Linux based software a good trial, even several purchased versions.  None of them cut the mustard for even a tiny one man operation, much less one where many entities need to be handled.

If I spent as many hours and wasted whole weekends and burned the midnight oil trying to keep Ubuntu up and running as I did going to skewl, I would have my doctorate in killing time and spinning my wheels.

I'm an olde diehard so am still running Ubuntu.  But working until midnight everynight and almost every weekend since moving over to Ubuntu is getting very olde very fast.........

I know XP is going to be discontinued some day, and Vista is NOT an alternative!  I'll go back to using paper bags for totaling up orders, and paper booklets for keeping track of accounts LONG before I would even consider Vista!  Or anything Mickey$oft again for that matter!

The one and only time our office ran Perfectly and without a single problem was when we were running WANG equipment and Software!  Expensive, but it WORKED!  And lo how many years ago was that, sheee......  One would think the times have progressed instead of regressed.....

But if I were you, I would do like I did, just BITE THE BULLET and Hang in there!

You also might consider Hardy version 8.04, since it's stable and an LTS version.

8.10 is just another experimental version released to find all the bugs in it!
And not much support with it either, and I hear they have dropped support for many things in it, rather than making it backwards compatible.

I'm not planning on replacing one piece of hardware in my office UNTIL a Manufacturer decides to support it.  These third party drivers are iffy at best and usually don't address the features of the item they were written for.  
Even the ones marked as COMPLETE by the third party provider don't provide some of the basic yet necessary features required to use the device.

Some Manufacturer somewhere, someday, will wise up to the fact Mickey$oft is on it's downhill slide and look to supporting Linux.  I'm hoping it will be a company that makes quality products as well.  I would like to see Epson or Canon or Konica or Musetek or Microtec take the market share and put HP down the tubes where they belong!  NOTHING manufactured with the HP label on it has worked properly and if it worked at all was harder to use than pulling hens teeth, and then it broke down completely.  HP does not even fully support their hardware in their own computer brands.  I know, I'm sitting on several HP items that did not work on their own computers they were geared to work on from day one. 

Just hang in their my friend, it WILL get better!

TTUL
Gary

---

### Post by VitaminBB on 2008-11-25
You have my sympathy Gary, im just one guy using Ubuntu as a desktop and ya im hanging in there, I solved a couple of these things yesterday thanks to some input here.

Your advice on downgrading to 8.04 might be what I should do really, ill have to see if I can fix some other issues.

---

### Post by starcannon on 2008-11-25
If you decide to downgrade to 8.04 (which is a good option), be sure to take the time to put /home on its own partition. This will make version switching much easier in the future, and allows for clean installs of new or older versions a simple task; also allowing you to not be bothered with many of the "upgrade install" issues.

As for going back to winXP, I wouldn't discourage you from doing what ever it is you need to do; however, it is good to keep in mind that one spends a lot of time dealing with windows annoyances as well. I guess at the end of the day, no matter where your at, there you are; computers require maintenance; though I will say that once you have a properly configured Ubuntu system, if you resist the urge to mess with it, you will have a lot less maintenance to do than on a windows system. Avoid non productive tweaker toys like compiz and emerald, yeah they look cute, but if your just wanting to get your work done, then why be bothered with all the tweaking they constantly seem to require?

GL and use what works for you.

---

### Post by VitaminBB on 2008-11-25
Hey StarCannon, ya I have the home on its own partition, you set that up for me :) *L*

Im still trying to make it work, the wireless connection problem is fixed and emerald is sort of playing along now, though it did crash on me just 15 mins ago.

Im chipping away at the rest so whatever advice ppl have is appreciated ...

---

### Post by bapoumba on 2008-11-25
Thread title edited and moved to Ubuntu Testimonials & Experiences.

I'll never understand such titles..

---

### Post by VitaminBB on 2008-11-25
> **bapoumba said:**
> Thread title edited and moved to Ubuntu Testimonials & Experiences.

I'll never understand such titles..


Wait a second, this is more then a testimonial!

I want help in fixing the problems I have!

---

### Post by bapoumba on 2008-11-25
> **VitaminBB said:**
> Wait a second, this is more then a testimonial!

I want help in fixing the problems I have!

Looks like an experience :)

---

### Post by VitaminBB on 2008-11-25
> **bapoumba said:**
> Looks like an experience :)

Seriously though, read the first post, im looking for answers here!!!!

Should I repost this where its supposed to be?

I have questions that need answers, im not giving a testimonial here!

Why are u limiting my chance to get input on these questions ?!

---

### Post by mikewhatever on 2008-11-25
> About to install Windows and give Ubuntu the finger, help is needed
To me it looked like you asked for help with removing Ubuntu and installing Windows. Anyway, threatening you might go to Windows unless helped, makes me very unwilling to help.

---

### Post by VitaminBB on 2008-11-26
> **mikewhatever said:**
> To me it looked like you asked for help with removing Ubuntu and installing Windows. Anyway, threatening you might go to Windows unless helped, makes me very unwilling to help.

The only person I was threatening is myself *LOL*

I was trying to convey my frustration and point out the issues I was having ...

---

### Post by Tamlynmac on 2008-11-26
> VitaminBB
Ive about had it ...
 
 So I had things going along swimmingly (or so I thought) but the constant tweaking to get things even stable is baffling to me and today I have been smacked around so much that im on the verge of saying "screw this" and installing windows xp.

I must agree with "bapoumba" & "mikewhatever". Both your title and opening paragraph indicate that you were ready to install XP, if you didn't receive assistance. This type of threatening post tends to generates negative responses and is unnecessary. I suggest you simply repost your issues separately in the appropriate forum sections and title them accordingly.

I in no way wish to interfere with the admins, just observing and making a recommendation to the OP.

---

### Post by VitaminBB on 2008-11-26
I was overbearing maybe but I cant type a scream properly ...

---

### Post by peakshysteria on 2008-11-26
Take a backup of your files and do a cleans install of Intrepid Ibex. This will for sure fix your problems (since it looks to me like you'r saying your system worked before you started tweaking things). Clean install is aprox 30 min. anyway. So no matter how you look at it it will also be the fastest route. And it might be the better alternative than mapping out your different problems and solving them one by one.

---

### Post by stalkingwolf on 2008-11-26
> Anyway, threatening you might go to Windows unless helped, makes me very unwilling to help.

Having been there I read it as a cry of desperation not a threat.  A statement of a last resort.

knowing from personal experience how even the simplest questions, posted in the appropriate place can go unanswered makes ME all the more willing to help the OP.

> Clean install is aprox 30 min. anyway. 
times the number of machines in the office.

My suggestion would be to work on one machine until the issues are solved,
making notes along the way.  When the first is fully operational as you want it, use your notes to set up the rest.  It will be much faster in the successive machines.
Next, once all your machines are working to your satisfaction. Leave them alone.  " If it works, Dont fix it."  This is a lesson it took me some time to learn.

are you using the beta or full release of 8.10?

---

### Post by VitaminBB on 2008-11-26
> **stalkingwolf said:**
> Having been there I read it as a cry of desperation not a threat.  A statement of a last resort.

knowing from personal experience how even the simplest questions, posted in the appropriate place can go unanswered makes ME all the more willing to help the OP.


times the number of machines in the office.

My suggestion would be to work on one machine until the issues are solved,
making notes along the way.  When the first is fully operational as you want it, use your notes to set up the rest.  It will be much faster in the successive machines.
Next, once all your machines are working to your satisfaction. Leave them alone.  " If it works, Dont fix it."  This is a lesson it took me some time to learn.

are you using the beta or full release of 8.10?

Cheers eh ...

Im using the full release 8.10 ...

So far ive only figured out the network manager problem and right now im scouring the web trying to fix compiz and emerald, I just posted on the compiz forum so im hoping for some good input there ...

As for the rest I doubt ill ever figure it out ...

A fresh install isent a bad idea but im not thrilled about the idea and I feel like these problems should have easy solutions.  Im also new to linux overall so im looking to hack, even just a little to get things to work, a fresh install is great but ill run into other problems again, might as well learn common fixes now.

---

### Post by peakshysteria on 2008-11-26
My point was that, if in doubt, you probably are better of with a clean install. If I understand you right you have done several changes to your system not being entirely sure everything under the hood is as perfect as the different forum threads, script snippets, google, blogs and friends have told you and/or promised.

My advice came because I've been there and I am there right now. The easiest and fastest way is to start over again. Then map out the immediate problems and start searching the forums and other helpful different ends of the web. This is also learning in my eyes. At least this is how I have come so far as I am now (still feeling like a n00b though). But at least by your first post I think a clean install will present you with fewer problems than right now. In addition it also might present you for the things you did wrong to your last install so you don't make them once more etc...

And yes it's indeed frustrating sometimes. Sometimes I just want to give up and thrash the whole machine and buy a new one. So far I've yet remained sane enough to calm myself after going through the + seven dirty words a few times.

Remember also 8.0.4.1 is a LTS release and seemingly (in my experience) very stable. So that's also an option. But still I recommend to do a clean install of Intrepid Ibex. All is smooth at my end. So once again (after some hellish, but easier than ever, ATI trouble) I am impressed. Ubuntu rules all three machines in the household without problems. My seven year old daughter enjoys Compiz (among other things). My four year old son enjoys the different games. My better half enjoys the speed, the flawlessness and compatibility. Myself I just enjoy the simplicity and ability to tweak things and run the programs I need for my daily computer-fix.

Good luck man

:popcorn:

---

### Post by VitaminBB on 2008-11-26
> **peakshysteria said:**
> My point was that, if in doubt, you probably are better of with a clean install. If I understand you right you have done several changes to your system not being entirely sure everything under the hood is as perfect as the different forum threads, script snippets, google, blogs and friends have told you and/or promised.

My advice came because I've been there and I am there right now. The easiest and fastest way is to start over again. Then map out the immediate problems and start searching the forums and other helpful different ends of the web. This is also learning in my eyes. At least this is how I have come so far as I am now (still feeling like a n00b though). But at least by your first post I think a clean install will present you with fewer problems than right now. In addition it also might present you for the things you did wrong to your last install so you don't make them once more etc...

And yes it's indeed frustrating sometimes. Sometimes I just want to give up and thrash the whole machine and buy a new one. So far I've yet remained sane enough to calm myself after going through the + seven dirty words a few times.

Remember also 8.0.4.1 is a LTS release and seemingly (in my experience) very stable. So that's also an option. But still I recommend to do a clean install of Intrepid Ibex. All is smooth at my end. So once again (after some hellish, but easier than ever, ATI trouble) I am impressed. Ubuntu rules all three machines in the household without problems. My seven year old daughter enjoys Compiz (among other things). My four year old son enjoys the different games. My better half enjoys the speed, the flawlessness and compatibility. Myself I just enjoy the simplicity and ability to tweak things and run the programs I need for my daily computer-fix.

Good luck man

:popcorn:

Ok, lets say im looking at a clean install ...

Theres lots of sites that outline how to do an install but what can I expect from keeping my /home directory?

Let me be more specific ...

My home directory is on its own partition (starcannon helped me with that) so when I reinstall what will I be looking at?

Will I need to reinstall all the applications and games but the settings will be saved?

Will I have to reinstall email on my client?

What precautions should I take?

Will I start up and everything will look like nothing changed?

Im hesitant also because I dont want to make things worse *L* and im noob enough to know that not knowing what im doing in an install is a real impediment ...

---

### Post by peakshysteria on 2008-11-27
The forums are full of posts witch explain how to save your /home directory. I'm sorry to say I've no experience in doing it that way. But as I've understood it it's possible and not even a hard task to perform.

A quick look gave me: [http://ubuntuforums.org/showthread.php?t=404033](http://ubuntuforums.org/showthread.php?t=404033)

I haven't read the whole thread but it should give you a hint on what's to expect (even though the thread is somewhat old).

Best of luck

---

### Post by VitaminBB on 2008-11-27
> **peakshysteria said:**
> The forums are full of posts witch explain how to save your /home directory. I'm sorry to say I've no experience in doing it that way. But as I've understood it it's possible and not even a hard task to perform.

A quick look gave me: [http://ubuntuforums.org/showthread.php?t=404033](http://ubuntuforums.org/showthread.php?t=404033)

I haven't read the whole thread but it should give you a hint on what's to expect (even though the thread is somewhat old).

Best of luck

Thanks, like I said I know how to do a clean install and I already have my /home on a seperate partition ...

I dont think im explaining myself very well lately ...

I was really just looking to get a sense of what I can expect from a reinstall using the pre-existing home directory ...

Will I have to reinstall programs?

I know the /home directory stores settings but im such a clueless noob that I dont even know if I will need to reinstall programs...

Im wondering what other precautions anyone recommends before doing a reinstall too ...

Thanks for the link ...

---

### Post by waspbr on 2008-11-27
if you are going to do a fresh install and already have a home directory, then you should follow more or less this proceadure.

[LIST]
[*]Pop a live CD when booting, @ desktop click on the install button
[*]Select manual install
[*]Delete the partition of your previous system directory, create a new partition with the new empty space,size it as you wish(I'd recommend min 20 - max 50 GB),choose ext3 as a filesystem (though I hear ext4 may be out and worth a try).
[*]Don't forget set the mount point of your new system partition as  /
[*]After that click on edit your home partition, set the mount point of your home partition as /home ,but do not format it, make sure that the format flag is off.
[*]double check if the format flag (tick) is on for your system partition AND OFF FOR YOUR /HOME PARTITION, (I can't stress that enough)
[*]review your partitions and proceed with the install, choose the same user name you had before in order to access your old account set in your /home part.
[*]wait for the install to complete  and reboot
[*]you should be done, once you login you should have the same desktop as you had before in your old system,  some programs are going to be gone eg skype, awn... you need to re-install them, most of them are available at synaptic, getdeb.net or the maker's website
[*]get a cold beer and enjoy your new desktop
[/LIST]

If I forgot something or wrote anything outrageously wrong (unlikely) everyone please feel free to correct me

good luck

---

### Post by SunnyRabbiera on 2008-11-27
> **VitaminBB said:**
> Cheers eh ...

Im using the full release 8.10 ...

So far ive only figured out the network manager problem and right now im scouring the web trying to fix compiz and emerald, I just posted on the compiz forum so im hoping for some good input there ...

As for the rest I doubt ill ever figure it out ...

A fresh install isent a bad idea but im not thrilled about the idea and I feel like these problems should have easy solutions.  Im also new to linux overall so im looking to hack, even just a little to get things to work, a fresh install is great but ill run into other problems again, might as well learn common fixes now.

But re installing XP is not much better of an idea, a fresh install of windows can be HARDER and yes I said harder then a fresh install of Ubuntu.
I think installing XP is a pain, not only does it take a while but it doesnt support much more then ubuntu does truth be told when its pure XP without the recovery disk that has all the hardware crap.
I have had many fresh installs of XP's go sour on me.

---

### Post by waspbr on 2008-11-27
If I need to install windows what I usually do is to pop a live CD in, use gparted to make the ntfs partition, reboot and pop the windows cd, set it to install on the new ntfs partition. this usually saves time since the windows partition manager is slow.

but I agree with the comment above, it is not a big surprise for a windows installation to freeze or crash.

---

### Post by Liviu-Theodor on 2008-11-27
If I understand correctly, you have Ubuntu, and what to install Windows afterwards, but keeping your documents. If you consider keeping your installation of Ubuntu, maybe you find something useful on [How to install Windows after Ubuntu]("http://ubuntuforums.org/showthread.php?t=993805").

---

### Post by CatKiller on 2008-11-27
> **VitaminBB said:**
> Will I have to reinstall programs?

Yes.

Although it is possible to generate a list of all the packages you've got installed now, which you can then use to install them all again in one command. I can't remember exactly how to do it, but there are instructions on this forum somewhere.

<EDIT>[This post]("http://ubuntuforums.org/showpost.php?p=1521615&postcount=1") tells you how</EDIT>

The other thing to bear in mind is that if you have multiple users of your computer it's much easier if you add them back in the same order you added them before. Although permissions get displayed as user names, they are actually stored as user numbers. Adding the users back in the same order means that the new users will get the same numbers as the old users, which means they'll get the same permissions over their old files as they had before. It can save quite a bit of permissions-juggling.

---

