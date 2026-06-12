---
title: "A point from Microsoft's forums about Ubuntu"
date: 2009-05-05
forum: The Cafe
---

### Post by aimpau on 2009-05-05
[http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/](http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/)


A post by jgalley:

[I]"You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard.  What OS do you want to be running?  From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks.


If I have to rebuild my worstation and development environment even once then the actual cost of Ubuntu is more that the cost of Vista.  In fact, for every extra time my Ubuntu system crashes hard and fails to boot I could have purchased a new Vista system from Dell, thrown my old system in the trash and still come out ahead.


Linux is the best, if what you like to do is rebuild and reinstall operating systems or endlessly search the internet for cryptic instuctions on how to edit /etc files to make some piece of hardware or software sort of work."

[/I]Can someone please elaborate on what he means when "if the power fails...etc etc"? Also, I am really perplexed by his allegations ubuntu crashing etc etc, the costs etc etc....I mean Ubuntu supports RAID right? And the last hard lock up I experienced in ubuntu was in Gutsy and they fixed that already...

---

### Post by Idefix82 on 2009-05-05
> **aimpau said:**
> [http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/](http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/)
Can someone please elaborate on what he means when "if the power fails...etc etc"? Also, I am really perplexed by his allegations ubuntu crashing etc etc, the costs etc etc....I mean Ubuntu supports RAID right? And the last hard lock up I experienced in ubuntu was in Gutsy and they fixed that already...

Warren Buffet once said, among many other wise things, "Never ask your barber whether you need a haircut."

You were browsing a Windows forum, so you can expect to find some unjustified rant about Linux and some calculations of costs which have a certain bias to them. I wouldn't be at all surprised if this jgalley was employed by Microsoft.

---

### Post by loell on 2009-05-05
only he, knows. ;)

---

### Post by loell on 2009-05-05
> **Idefix82 said:**
> 
You were browsing a Windows forum, so you can expect to find some unjustified rant about Linux and some calculations of costs which have a certain bias to them. I wouldn't be at all surprised if this jgalley was employed by Microsoft.

and vice versa, to some far lesser exent would have been the same. :D

---

### Post by Idefix82 on 2009-05-05
> **loell said:**
> and vice versa, to some far lesser exent would have been the same. :D

Yes, but let the people on the Windows forums worry about that :)

---

### Post by apoth on 2009-05-05
Imagine if it crashed when doing a Windows update and the lost time meant losing out on the cost of a Windows licence, when he'd already forked out for one. Screwed twice over!

---

### Post by aimpau on 2009-05-05
Yes, I know its a windows forum, what i meant was, is that is there some truth is what he was saying? would it really cost a lot to repair ubuntu every single time? my xubuntu HD has almost all software known to xfce and gnome except kde and it has "crashed" on me yet. I tried running avidemux, xine, gimp. blender, jack, seq24 while watching TV on the pc as well and it never hang so im really wondering why he claims that.

---

### Post by infinitejones on 2009-05-05
I think he's talking about a theoretical situation where you're waiting for the OS (let's say Windows) to do some kind of automatic update and there's a power failure while the software is updating. 

I haven't used Windows regularly for a long time but looking at friend's machines while they update, it does this thing where it downloads all the patches, security fixes, service packs or whatever, installs some of them, then tells you to restart - but then sits there for about five minutes before actually restarting because it's installing the rest. I assume if the power fails during that, the OS could possibly "crash hard", by which he means you can't restart the OS at all because critical files haven't been updated fully. 

It sounds to me like he's never actually installed or upgraded a live Ubuntu system (or any modern *nix system), and also he has a very high opinion of himself and the value of his time. I don't see how he reaches the conclusion that having to reinstall Ubuntu costs him $400. 

Even if you're upgrading the kernel or the X server or something else critical and it crashes, chances are you can get to a terminal somehow, and fix it from there. I've never ***not*** been able to rescue a failed install or upgrade, because you just get yourself a terminal and do a quick sudo apt-get install -f or something, and carry on from there.

And absolute worst case, even re-installing Jaunty from scratch currently takes me about 15 minutes, from a USB stick. You could probably keep working using the LiveUSB while it was installing, and as long as you're sensible and create a separate home partition, plus what the OP mentioned about RAID etc, you don't lose any data. 

He seems to be saying that this process would be $400 worth of his time and trouble, but that's rubbish, unless he genuinely charges himself out at $1600 an hour. And if he did that, you'd think he'd have better things to do than post stuff like this...

Don't forget, on Vista (and maybe even XP) there's no easy way of getting to a fully fucntional terminal without loading the whole OS first. It's all or nothing. Therefore a crash of the sort he's talking about is, indeed, a royal pain in the behind. He's forgetting that a crash of the sort he's talking about, caused by the circumstances that he's talking about, pretty much can never happen on a modern *nix system.

---

### Post by aysiu on 2009-05-05
I don't even think it's factually true, regardless of whether it's worth $400 or not.

As infinitejones said, the worst I've had to deal with (and this was many releases ago) was a crashed X server. You end up at a command prompt and can ```
sudo /etc/init.d/gdm restart
``` or whatever else you need to do, and a reinstall is all of about 20 minutes for me.

In Windows, if you end up with a missing system file, you end up at the blue screen of death, and no one command is going to fix that (good luck getting to a command prompt). And if you decide to reinstall Windows, that's hours of your time. And it's not hours you can walk away from. That's hours of waiting, rebooting, clicking "Yes," rebooting, waiting...

In my experience, maintaining Windows is for those who don't value their time, despite Linux's reputation.

---

### Post by cfree220 on 2009-05-05
ROFLCOPTER

I switched to Linux after having to reinstall Vista Ultimate for the 5th time. What, you have a virus? What, you screwed over your mbr? Sure, new Linux users have a tendency to nuke they're systems once or twice doing something dumb. I had to reinstall Ubuntu twice when I first started, and that was not because the problem was irreparable (as was the case in 3 of the Vista installs), but because I lacked the knowhow.

btw, did anyone know that none of the tools in Window's bootrec.exe can recover the mbr from a GRUB overwrite?

---

### Post by pwnst*r on 2009-05-05
> **Idefix82 said:**
> Warren Buffet once said, among many other wise things, "Never ask your barber whether you need a haircut."

You were browsing a Windows forum, so you can expect to find some unjustified rant about Linux and some calculations of costs which have a certain bias to them. I wouldn't be at all surprised if this jgalley was employed by Microsoft.

you mean like the tripe found around here?  it goes both ways.

---

### Post by itsStephen on 2009-05-05
I can sort of relate to the paragraph about the updates.

The update manager popped up so I downloaded the updates and the computer froze so I didn't have any other option than to just turn it off. Now the mouse and keyboard don't respond so tomorrow I'm going to have to reinstall Ubuntu.

---

### Post by disturbed1 on 2009-05-05
> **aimpau said:**
> Can someone please elaborate on what he means when "if the power fails...etc etc"? Also, I am really perplexed by his allegations ubuntu crashing etc etc, the costs etc etc....I mean Ubuntu supports RAID right? And the last hard lock up I experienced in ubuntu was in Gutsy and they fixed that already...

He's talking about support costs. 

Let's say the upgrade is in a dpkg-reconfigure state, and only writes half of the configuration files before the power cuts. ( Even with a battery backup on a RAID card strange things happen ) your upgrade has the chance of actually corrupting files, and upon next boot, the system may not start. This would require a support call. 

That's his take of things. Which would be valid **IF** there is no such thing as the internet, google, message boards .................. Which all invalidate his claim.

Microsoft offers free phone support for a limited time, where as **phone** support for Ubuntu is not free.

This guy probably has used Windows all his life, and is already used to fixing things in Windows. Remember the first time you had to drill through the registry to fix corruption? How about rebuilding winsock for the first time, that was fun :)

---

### Post by Mistrblank on 2009-05-05
What an idiot. 

"You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard. What OS do you want to be running? From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks."

Yeah.  I go to the BACKUP I took of my root partition and restore it using one of ANY LiveCD of the dozens of copies I've made of the various releases over time.  I can even use one of the Gentoo, Fedora or OpenSUSE cds I've got. 

With Windows, I STILL don't know how to properly restore an XP build as there is no alternate environment to boot.  Automatic backups ALWAYS break with the built in backup utility from the XP Pro disk.  I have yet to try a Vista backup and restore, and I suspect it works, but the reality is it's no different than Ubuntu if you have a backup.  Most of the time, when I backup a Windows partition, I just take a disk image using a LINUX based LiveCD and dd on the command line.  

The moral, MAKE A BACKUP!

---

### Post by suitedaces on 2009-05-05
> **Mistrblank said:**
> What an idiot. 

"You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard. What OS do you want to be running? From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks."

Yeah.  I go to the BACKUP I took of my root partition and restore it using one of ANY LiveCD of the dozens of copies I've made of the various releases over time.  I can even use one of the Gentoo, Fedora or OpenSUSE cds I've got. 

With Windows, I STILL don't know how to properly restore an XP build as there is no alternate environment to boot.  Automatic backups ALWAYS break with the built in backup utility from the XP Pro disk.  I have yet to try a Vista backup and restore, and I suspect it works, but the reality is it's NO DIFFERENT THAN UBUNTU.  Most of the time, when I backup a Windows partition, I just take a disk image using a LINUX based LiveCD and dd on the command line.  

The moral, MAKE A BACKUP!

I think you're trying to tell us something...

---

### Post by Dr. C on 2009-05-05
Like a 1 year old thread on a Microsoft forum on what happens if you cut the power to an Ubuntu computer in the middle of an upgrade to the OS? Really you may have to reinstall. Now try that with Windows and get the same result you may have to reinstall.

---

### Post by aimpau on 2009-05-05
Ok, no i feel embarrased. I forgot to research "ext4", it says there that ext4 filesystem actually holds all data first in the memory before actually writing them on the disk thus IF ever there would be power outtages during an upgrade, no file is corrupted since it was still in RAM and the writing process hasn't begun yet...:) That's how I understand it and pls correct me if im wrong.

BTW, how cheap it is to have a decent RAID setup these days?

---

### Post by wispygalaxy on 2009-05-05
Last year, SP1 for Vista ruined my friend's laptop.  The desktop loaded *so* slowly, and it took at least 10 minutes.  Also, the whole screen would turn white when the desktop was clicked on.  This caused everything to freeze, so the laptop had to reboot!  Grrrr.  :(

---

### Post by mamamia88 on 2009-05-05
it's not rocket science if your computer crashes while in the middle of updating it's bound to screw something up that goes for both windows and ubuntu

---

### Post by tarps87 on 2009-05-05
> **aimpau said:**
> 
[/I]Can someone please elaborate on what he means when "if the power fails...etc etc"? Also, I am really perplexed by his allegations ubuntu crashing etc etc, the costs etc etc....I mean Ubuntu supports RAID right? And the last hard lock up I experienced in ubuntu was in Gutsy and they fixed that already...

Theoretically this could happen if the updater was in the process of updating the kernel or a configuration setting when there was a power cut, even there there are ways to recover without a reinstall and there is always the live cd and google or these forums. During a kernel upgrade it is likely to have little effect is GNU/Linux systems due to there being an back up of the previous kernel and the boot menu is updated after the new kernel is installed. There are ways to rebuild config files, in several cases deleting the file and rebooting will cause whatever needs that file to recreate it.
I believe the cost that he is referring to is time rather than money, it is likely that he has very little GNU/Linux experience and therefore only know the window solutions.

---

### Post by Arathorn on 2009-05-05
> **cfree220 said:**
> btw, did anyone know that none of the tools in Window's bootrec.exe can recover the mbr from a GRUB overwrite?
I don't know what bootrec.exe is, but the fixmbr command (accessible from the Windows install disc) works fine.

---

### Post by cfree220 on 2009-05-05
I can tell you from my time with Vista (most of which was fixing broken things), that the system recovery tools are very good BUT they are not reliable. It is usually very easy to use system restore to revert settings in the registry, but sometimes these system restore points vanish for no apparent reason. Recovering using a full PC backup is a great tool, but I have had times where, for no apparent reason, either the recovery environment just would not see the restore image (even though the device was listed), or it just returned some other error.

---

### Post by cfree220 on 2009-05-05
Unfortunately fixmbr did not work for me. Neither did fixboot. I think the other option is to export the current boot record after which you can write a new one. If my memory serves me correctly, this returned an error saying that it could not export a non-standard (non-windows) boot loader.

---

### Post by geoken on 2009-05-05
I think his point is that the recovery tools in Windows are easier than Ubuntu. I've successfuly used restore points to fix my system while having similar problems in Ubuntu caused me to do a re-install (after spending some time on google and running a few commands in vain).

---

### Post by Wiebelhaus on 2009-05-05
Don't sweat it , the more this thing grows the more haters will be having fits , getting drunk off the haterade and becoming increasingly agitated and angry , let em'! no worries.

---

### Post by cfree220 on 2009-05-05
Yeah, Vista tools and recovery are a lot easier. Then again, Ubuntu doesn't break nearly as often. btw, if anyone knows of any good tutorials on creating disk images in Ubuntu, I would appreciate it greatly. I did some light googling, but it was late and I did not find anything. Probably do some more later this week. Want a backup in case something goes wrong when I deploy a new partitioning scheme during the 9.04 installation.

---

### Post by miegiel on 2009-05-05
It's pure [_FUD_]("http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt"), but since I don't consider shooting fish in a barrel immoral, let's [s]lock and[/s] load and fire.

> [A post by jgalley:]("http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/")

"You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard.  What OS do you want to be running?  From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks.

If I have to rebuild my worstation and development environment even once then the actual cost of Ubuntu is more that the cost of Vista.  In fact, for every extra time my Ubuntu system crashes hard and fails to boot I could have purchased a new Vista system from Dell, thrown my old system in the trash and still come out ahead.

Maybe he makes $1000.- an hour and it takes him half an hour more to get "his linux" running than it would take him to order a new machine with vista on it delivered to his office. Or maybe he makes $10.- an hour and fixing "his linux" takes 50 hours more.

Is he arguing vista is for the ignorant and/or those who get paid insane wages? No, of course not!

He's implying a [_TCO_]("http://en.wikipedia.org/wiki/Total_cost_of_ownership") argument. But as in almost every TCO argument I come across, costs are left out. "Imaginairy Cost of Ownership" I'd call it.

But let's leave neverland and go to the real world. In the real world he's not allowed to do anything on his PC but work. He doesn't update his OS, he doesn't install software or hardware. When his machine breaks he doesn't fix it but grabs the phone to call the helpdesk, the helpdesk sends an admin to fix it and if the admin can't fit it in minutes his machine gets replaced by one that does work.

In the real world the cost of the vista license is almost irrelevant and so is the fact that linux is free (as in free beer, since he's discussing costs). The real cost is the time it costs admins to get broken machines running again, the frequency that machines break and the cost of building an environment in which people can do their job.

> Linux is the best, if what you like to do is rebuild and reinstall operating systems or endlessly search the internet for cryptic instuctions on how to edit /etc files to make some piece of hardware or software sort of work."

Here he's implying linux is ***only*** a hobby OS for nerds, 'nuff said, pure FUD.

---

### Post by Firestem4 on 2009-05-05
I can tell from personal experience that windows is no friend of crashing during an update, and it happens quite frequently.

Ive hard reset my Linux machines during major updating (i believe even one was a Kernel update) and the beauty of linux is that when I had to hard reset, the system came up working 100%, and only needed to be patched.

I built out a new Windows machine for work. After 2 1/2 hours of going through the Installation (Windows XP mind you....,), and another 2 hours of updating it with the latest updates. When I shutdown to install the patches, it froze, crashed itself. And refused to boot up. It effectively hung itself...As you can guess..I was doing a repeat show for another 4 1/2 hours =*(

At least it wasn't money lost for me or my company (necessarily), because nobody needed that computer at the time.

---

### Post by Thanh-BKK on 2009-05-05
Hi.

I have been running Ubuntu as my sole OS for just over a year and still consider myself a bloody nOOb, i still panic when i grab a kernel update (like today!) and the reboot stalls with a bunch of text on the screen, no movement at all... and thoughts spin in my head "how old is my data backup, kernel, reinstall OS, customization, three weeks aaaargh" but then, oh magic, it moves, more text runs, the brown-ish screen comes, flickers as the Nvidia-driver is loaded an WHAM there's my desktop and the icons and all is there and perfectly intact (and the next reboot takes it's usual 30 seconds again). 

However if i am in the mentioned situation (power failure during an update) i'd rather run Linux. Because i know that even a screwed-up system can likely boot, at least into an older kernel or CLI-mode. And if not - there's always the live CD which is powerful, too.

I have not (yet) experienced the situation with Ubuntu (and, seriously, hope i never will.. touch wood, the battery in my UPS is new!) but i HAVE been there with Windows, XP that is. The computer was in the process of shutting down ("Installing update 18 of 22, do not power down your computer, it will shut down by itself when completed") and ZAP there went the power. It was back a second later. The computer would not boot - some cryptic message about some file being damaged and to try the Recovery Console. No such thing on that computer, and where is an XP CD when one is needed..? Next morning - Recovery Console didn't recover and i ended up re-installing XP, of course losing all data in "My Documents" in the process as the previous install wasn't even detected during the re-install!

Now, a question i would like to ask that same guy: "If you are working on your computer and not thinking of something bad, suddenly your PSU goes up in smoke and takes the mainboard along with it. Which OS would you prefer to be running, Windows or Linux..?"

I'd opt for Linux. Been there, done that a gazillion times (i fix computers), a mainboard swap. And in 95% of the cases after the swap Windows will NOT BOOT AT ALL, even if the new board is close to the old one (same manufacturer, same chipset manufacturer etc). BSOD's all the way, and usually Windows-re-install as well. One single time i had XP magically accept a rather brute swap - Gigabyte for Asus, NOTHING identical but that one just booted fine, rummaged a while to install new drivers and soldiered on, even stranger as the graphics card had to be swapped too (Nvidia for AMD). And in the remaining cases i am able to get into Safe Mode and get rid of old drivers and install new ones to make it work.

Ubuntu? No issue. Swap, boot, runs. 

And i am seeing WAY more failed mainboards than power cuts during updates. 

Best regards....

Thanh

---

### Post by sydbat on 2009-05-05
> **sx66gns said:**
> Don't sweat it , the more this thing grows the more haters will be having fits , getting drunk off the haterade and becoming increasingly agitated and angry , let em'! no worries.Mmmmm...Haterade...minty fresh...

---

### Post by thewolfman on 2009-05-05
Interesting read from all of you, so I have a question:

"Why doesn't Ubuntu have a restore/recovery mode like Windows"

You know like F8 and so, I am not new to Linux but get a little scared when trying something out because I don't really know how to undo what I just did if my PC won't boot and furthermore; why is it necessary to continuly update Ubuntu's kernel, why not just have one major update per year instead of every couple of weeks!.

What makes people afraid of Linux is Linux itself due to its vast complexity, if it were made even more user friendly with built-in failsafes that even mere mortals can understand, then just maybe more people would switch to Linux. People have been schooled in the MS school of life and want it kept simple!.

PS: my Ubuntu (Jaunty 9.04) hasn't let me down yet and I do "BACK-UP".

Have a good one chaps.

---

### Post by Maheriano on 2009-05-05
His post is true..........for Gentoo 4 years ago. That's exactly the kind of trouble I had when trying to setup a sound card and dual head video card with all the /etc/fstab editing and recompiling of the kernel. It frustrated me back to Windows.
So I think he just hasn't updated his mindset, nor tried Ubuntu recently to know the difference. When I came back and gave it another try.....well.......3 of my 4 computers now are single booting Ubuntu and if I can get a 7 inch touchscreen friendly version for my car with GPS then I would have all 4.

---

### Post by darlek5000 on 2009-05-05
> **aimpau said:**
> [http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/](http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/)
 
i dont think its easy to crash ubuntu is it?

---

### Post by monsterstack on 2009-05-05
I always thought that Linux distros lacked fix-up tactics because everything you could possibly do it is un-doable. But then again, chmod'ing your entire disk to some random user is one of those things you really wouldn't want to even try and fix. Still, if you use a persistent /home partition, what's the problem with the occasional nuke or clean install if you're feeling bored one day?

---

### Post by LightB on 2009-05-05
Admit it, you all work for Linux! Linus Torvalds has you all bought!

---

### Post by miegiel on 2009-05-05
> **thewolfman said:**
> ... Why doesn't Ubuntu have a restore/recovery mode like Windows? ...

It does. here's part of my bootmenu as an example :
```
...
Ubuntu 8.04.2, kernel 2.6.24-24-generic
Ubuntu 8.04.2, kernel 2.6.24-24-generic **(recovery mode)**
Ubuntu 8.04.1, kernel 2.6.24-23-generic
Ubuntu 8.04.1, kernel 2.6.24-23-generic **(recovery mode)**
...
```
You need to press a key to see the boot menu if it's not there. But since I always see my boot menu (not default I believe), I have no idea what the key is :)
There are fail-safes in linux, but they're just a bit different. You don't get warnings like "... bla ... may cause you system to -fill in sometheing scarry-!". But whenever you are changing system files, you get prompted for your password. When ever you need to fill in your password you should always think twice about what it is that you're doing.

> **LightB said:**
> Admit it, you all work for Linux! Linus Torvalds has you all bought!
I wish :D I'll bring him coffee for only $5.- an hour at a snap of his fingers.

---

### Post by calrogman on 2009-05-05
I would simply reboot into recovery mode, wait as the journal is restored, then attempt to fix all broken packages.

Good luck with your failed Vista > 7 upgrade.

---

### Post by thewolfman on 2009-05-05
> **miegiel said:**
> It does. here's part of my bootmenu as an example :
```
...
Ubuntu 8.04.2, kernel 2.6.24-24-generic
Ubuntu 8.04.2, kernel 2.6.24-24-generic **(recovery mode)**
Ubuntu 8.04.1, kernel 2.6.24-23-generic
Ubuntu 8.04.1, kernel 2.6.24-23-generic **(recovery mode)**
...
```
You need to press a key to see the boot menu if it's not there. But since I always see my boot menu (not default I believe), I have no idea what the key is :)
There are fail-safes in linux, but they're just a bit different. You don't get warnings like "... bla ... may cause you system to -fill in sometheing scarry-!". But whenever you are changing system files, you get prompted for your password. When ever you need to fill in your password you should always think twice about what it is that you're doing.


I wish :D I'll bring him coffey for only $5.- an hour at a snap of his fingers.

I know about the recovery mode function which is accessed by the esc key if not shown in the boot menu but a lot of people new to Linux would not, so my point was that there should be a "Full Recovery" function and not just the "Failsafe" of being asked for your password!. In its current form, Ubuntu recovery mode does not offer an undo/restore function which is really what I am ranting on about!.

---

### Post by days_of_ruin on 2009-05-05
I once was installing a bunch of updates on a laptop that froze up
while it was actually doing the installing part. Guess what happened after
I did a hard shutdown and started it back up again? It booted up like nothing happened.:)

---

### Post by rajeev1204 on 2009-05-05
The last paragraph from that post is true isnt it.

Iam not saying windows doesnt have problems, but frankly, i havent had as many frustrating days or nights with windows as i have had with ubuntu.

I mean why the hell should i try to edit some /etc or some other file to get my display to work? Its been 2 years and still they cant solve the X problems.Then they go ahead and disable ctl alt backspace to fix the most annoying problem linux has. LOL.nice.


I also say this,windows XP is a good stable operating system.I love it and i have never seen a BSOD on it.Saw it on win 95 and 98 butnever on XP.


Thanks.Ill cool down by tomorrow. :)

---

### Post by Mistrblank on 2009-05-05
I also have to laugh at the "Sort of work" comment considering I had to jump through IMMENSE hurdles to get my nforce2 board to work with Vista.  I had to go get alternative drivers, edit config files.  The AGP ATI 2600xt required some hacking (Omega drivers) to get working in XP.  

Both work mostly by default on Ibex (haven't tried Jaunty on that box yet) save for proprietary driver activation.

---

### Post by Keithhed on 2009-05-05
I've managed to break all the versions of windows multiple times, and even had trouble with Ubuntu, but I don't sweat it.  If I can't repair whatever damage that has taken place I simply reinstall the OS.  Simple as that, data backed up on spare HDD.  I could crash this right now and be running in no time with no loss (except time)

---

### Post by mousestalker on 2009-05-05
I hate interjecting facts into a thread like this, but as it happens we lost power this past Sunday while I was updating Jaunty. Eleven hours later when the power clicked back on, I had to unplug a usb printer and then plug it back in. My system worked fine after that.

I've had to the same with both XP and ME. The results were not nearly as pretty.

I suppose if you had a lightning strike on the power line and your hard drive got totally fried then recovery would be awful. But that would be true of any OS as the problem then would be data recovery.

---

### Post by billgoldberg on 2009-05-05
> **aimpau said:**
> [http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/](http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/)


A post by jgalley:

[I]"You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard.  What OS do you want to be running?  From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks.


If I have to rebuild my worstation and development environment even once then the actual cost of Ubuntu is more that the cost of Vista.  In fact, for every extra time my Ubuntu system crashes hard and fails to boot I could have purchased a new Vista system from Dell, thrown my old system in the trash and still come out ahead.


Linux is the best, if what you like to do is rebuild and reinstall operating systems or endlessly search the internet for cryptic instuctions on how to edit /etc files to make some piece of hardware or software sort of work."

[/I]Can someone please elaborate on what he means when "if the power fails...etc etc"? Also, I am really perplexed by his allegations ubuntu crashing etc etc, the costs etc etc....I mean Ubuntu supports RAID right? And the last hard lock up I experienced in ubuntu was in Gutsy and they fixed that already...

His post doesn't make any sense.

He claims he will lose a lot of money if his system goes down.

That can be true.

But why he says this:

> You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard.  What OS do you want to be running?  From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks.

I don't know.

Anyone who needs his computer to make money surely has one of those boxes (I forgot the name)that will prevent power loss even when the whole city goes out.

Even my mother has one of those for her work computer.

Also he should be doing automatic backups and ghost his system frequently.

If Ubuntu or Windows crashes and leaves your system unstable, you use the ghosted image and your backups.

Reinstalling the ghosted Ubuntu shouldn't take more than 30 minutes. 

Note that he also says "automatic updates". Nobody that uses a production machine does automatic updates. Ubuntu updates aren't automatic, nor are Windows. They can be, but he shouldn't do that.

Also, if you use Ubuntu on a production machine you should get support by Canonical.

---

### Post by Luggy on 2009-05-05
> **aimpau said:**
> [http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/](http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/)


A post by jgalley:

[I]"You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard.  What OS do you want to be running?  From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks.


If I have to rebuild my worstation and development environment even once then the actual cost of Ubuntu is more that the cost of Vista.  In fact, for every extra time my Ubuntu system crashes hard and fails to boot I could have purchased a new Vista system from Dell, thrown my old system in the trash and still come out ahead.


Linux is the best, if what you like to do is rebuild and reinstall operating systems or endlessly search the internet for cryptic instuctions on how to edit /etc files to make some piece of hardware or software sort of work."

[/I]Can someone please elaborate on what he means when "if the power fails...etc etc"? Also, I am really perplexed by his allegations ubuntu crashing etc etc, the costs etc etc....I mean Ubuntu supports RAID right? And the last hard lock up I experienced in ubuntu was in Gutsy and they fixed that already...

I think what jgalley was talking about was that the cost of lost time is worth more then the cost of the operating system.

I believe the intent of the comment was that if you have to spend a day fixing up your machine after it breaks it self or you break it or something doesn't work quite right and you need to tweak it, then you would have been better off spending the money to get something that works instead of something that is free and kinda sorta works.


I don't agree with jgalley because he makes the assumption that Windows is bug free and that time isn't needed to be spent setting up or fixing stuff on a Windows machine.

---

### Post by Tipped OuT on 2009-05-05
Why can't we all (Microsoft, Linux, and Apple) just get along for the sake of the children like me. :)

---

### Post by DenysT on 2009-05-05
If the power fails have no fear, battery backup works! Oh well, it may cost him $400 to fix but he could have bought a good UPS for less. Wal-Mart sells them for Pete's sake.

---

### Post by pwnst*r on 2009-05-05
> **DenysT said:**
> If the power fails have no fear, battery backup works! Oh well, it may cost him $400 to fix but he could have bought a good UPS for less. Wal-Mart sells them for Pete's sake.

Pete has nothing to do with it and WalMart sucks :)

---

### Post by JohnFH on 2009-05-05
> **Keithhed said:**
> I could crash this right now and be running in no time with no loss (except time)

If you were running again in no time then you wouldn't have lost any time either.

The Pedant Chief.

---

### Post by pwnst*r on 2009-05-05
> **JohnFH said:**
> If you were running again in no time then you wouldn't have lost any time either.

The Pedant Chief.

also, there's big difference between business and home down time.

---

### Post by DenysT on 2009-05-05
> **pwnst*r said:**
> Pete has nothing to do with it and WalMart sucks :)

OK, but UPSes are available at a lot of places. And for Bill's sake you should use them. Keeps Windows honest.

---

### Post by Idefix82 on 2009-05-05
> **Tipped OuT said:**
> Why can't we all (Microsoft, Linux, and Apple) just get along for the sake of the children like me. :)

In simple terms, because people who buy Windows give money to a company that then uses this money to eliminate competitors, like for example other OSs. For some reason, people who use other OSs don't like that.

---

### Post by zakany on 2009-05-05
Windows warns you to not power down while it's updating, so I assume that losing power during this critical time would FUBAR my Vista machine no different than it would my Ubuntu iron.

From an unbiased POV, I don't understand what the poster's point was.

---

### Post by xArv3nx on 2009-05-05
> **zakany said:**
> Windows warns you to not power down while it's updating, so I assume that losing power during this critical time would FUBAR my Vista machine no different than it would my Ubuntu iron.

From an unbiased POV, I don't understand what the poster's point was.
no, i don't think so.. if you did a hard reboot, it would probably restart then continue installing updates, or it has this feature where it rolls back updates (when the updates don't successfully install). either way, you should be good.

i don't think ubuntu has this yet. i think the overall point is the whole ubuntu system is.. fragile. too many risks for no real gain.

---

### Post by Mehall on 2009-05-05
Not read the thread but...

there's a reason we all use Journaled filesystems in Linux. ;)

---

### Post by forrestcupp on 2009-05-05
> **Luggy said:**
> I think what jgalley was talking about was that the cost of lost time is worth more then the cost of the operating system.

Exactly.  We're talking corporate here, not a home user.  If you've ever dealt with work orders before, you should know that it all adds up.  Even if it only takes 30 minutes to install Ubuntu, that's 30 minutes you're paying at least one IT guy to do it, 30 minutes you're paying the guy who usually uses that computer to do nothing, and 30 minutes of work time that you lost that is going to be much more valuable than anyone's pay for that half hour.

And those of you who are arguing that it only takes 30 minutes have a pitiful argument.  We all know that it only takes 30 minutes to get a standard installation complete.  But anyone who claims that it only takes 30 minutes to install from scratch *and* have it all set up and ready for your specialized business and needs is just plain wrong.

So now we're talking about hours.  And most corporations are running a network.  So then you have to multiply all of that by however many computers were affected.

Personally, I think $400 is on the low end of an estimate.  But it's a whole different argument as to whether Windows would actually be any better.  Probably not.

---

### Post by pwnst*r on 2009-05-05
> **forrestcupp said:**
> Exactly.  We're talking corporate here, not a home user.  If you've ever dealt with work orders before, you should know that it all adds up.  Even if it only takes 30 minutes to install Ubuntu, that's 30 minutes you're paying at least one IT guy to do it, 30 minutes you're paying the guy who usually uses that computer to do nothing, and 30 minutes of work time that you lost that is going to be much more valuable than anyone's pay for that half hour.

And those of you who are arguing that it only takes 30 minutes have a pitiful argument.  We all know that it only takes 30 minutes to get a standard installation complete.  But anyone who claims that it only takes 30 minutes to install from scratch *and* have it all set up and ready for your specialized business and needs is just plain wrong.

So now we're talking about hours.  And most corporations are running a network.  So then you have to multiply all of that by however many computers were affected.

Personally, I think $400 is on the low end of an estimate.  But it's a whole different argument as to whether Windows would actually be any better.  Probably not.


^^^exactly.

---

### Post by Keithhed on 2009-05-05
You know you're a geek when:

   You argue about a hypothetical situation endlessly and split hairs about peoples responses!

---

### Post by LowSky on 2009-05-05
Any business who doesn't use proper server designed system on redundant power supplies and battery backups is just asking for a disaster and a huge costs to get anything back up. Windows, OS/S, or Linux, any proper IT manager is going to have back ups off all the configuration files saved somewhere else. Not to mention they are going to create a separate partitions for the OS and for the DATA/config files.

---

### Post by miegiel on 2009-05-05
> **forrestcupp said:**
> ...
If you've ever dealt with work orders before, you should know that it all adds up.  Even if it only takes 30 minutes to install Ubuntu, that's 30 minutes you're paying at least one IT guy to do it, 30 minutes you're paying the guy who usually uses that computer to do nothing, and 30 minutes of work time that you lost that is going to be much more valuable than anyone's pay for that half hour.

And those of you who are arguing that it only takes 30 minutes have a pitiful argument.  We all know that it only takes 30 minutes to get a standard installation complete.  But anyone who claims that it only takes 30 minutes to install from scratch *and* have it all set up and ready for your specialized business and needs is just plain wrong.
...

If that IT guy is any good, he knows in 5min if he can finish it in a few more minutes. If he can't he's got 5min left to plug in a spare PC (he's got at least 3 spare PCs waiting for an "emergency" :D). Ok, to be fair you need to add the response time to that. And not always is there an IT guy who can drop what he's doing and run to the rescue.

Now (in most businesses) you can't jump behind the bosses PC because he's in a meeting and not using his PC anyway. But there's always a PC around doing nothing. Just because your PC goes on strike doesn't mean you can't do your job.

---

### Post by Sealbhach on 2009-05-05
> **Tipped OuT said:**
> Why can't we all (Microsoft, Linux, and Apple) just get along for the sake of the children like me. :)

Patents. That's one reason of many.


.

---

### Post by pwnst*r on 2009-05-05
> **miegiel said:**
> If that IT guy is any good, he knows in 5min if he can finish it in a few more minutes. If he can't he's got 5min left to plug in a spare PC (he's got at least 3 spare PCs waiting for an "emergency" :D). Ok, to be fair you need to add the response time to that. And not always is there an IT guy who can drop what he's doing and run to the rescue.

Now (in most businesses) you can't jump behind the bosses PC because he's in a meeting and not using his PC anyway. But there's always a PC around doing nothing. Just because your PC goes on strike doesn't mean you can't do your job.

lol, you don't know what you're talking about.

---

### Post by miegiel on 2009-05-05
> **pwnst*r said:**
> lol, you don't know what you're talking about.

Maybe I do, maybe I don't.

I know there are IT departments that don't have their **** together. I also know there are IT guys that can waste time fixing a machine, while they should ask themselves: "What's the fastest way to get this employee working again?" I know there are employees that will spend ages looking over the IT guys shoulder, instead of doing something useful. And I know that some employees are so connected to their PC and their desk that they can't work anywhere else.

All this doesn't mean you can't fix it in minutes by replacing a PC with one that does work.

---

### Post by Mehall on 2009-05-05
I agree. In a company of 1000 people, owning 20 spare computers or something so you can switch them out is useful. I mean, everything on the comuters is standard, and all documents should be on the file server anyway, so it's a valid tactic, and allows the IT dept to actually fix a machine, rather than applying a quick fix to get it workign temporarily again.

---

### Post by oack on 2009-05-05
If one had to reinstall window after a hard-crash then better hope the recovery disks burned with no faults, I have heard of loads of people that have been stuck up the river because of bad recovery media.

---

### Post by Cybie257 on 2009-05-05
> **aimpau said:**
> Ok, no i feel embarrased. I forgot to research "ext4", it says there that ext4 filesystem actually holds all data first in the memory before actually writing them on the disk thus IF ever there would be power outtages during an upgrade, no file is corrupted since it was still in RAM and the writing process hasn't begun yet...:) That's how I understand it and pls correct me if im wrong.

BTW, how cheap it is to have a decent RAID setup these days?

Probably already answered,but, in Linux... Using mdadm, the raid will ONLY cost you what you spend on the hard drives. And setting it up? A piece of cake. Oh, and if you want multiple instances on Linux on your computer, no problem, you can setup that exact raid across all your installs and access the raid. 

Or, if you got some older drives laying around, might not cost you anything. Heck, have an 80gig, 100gig, and say 60 gig laying around? You can build a (approx) 120 gig raid 5 within 5-10 mins, plus the time it takes to install the hardware. :)

-Cybie

---

### Post by yaiyuy8W on 2009-05-05
Well Ubuntu has epic failed me 3x. When it goes into suspend/hibernate BOOM FAIL! Nothing! I'd suspect this is worse as it's getting power the sad thing is it hasn't been fixed since 8.04.

---

### Post by Cybie257 on 2009-05-05
> **thewolfman said:**
> Interesting read from all of you, so I have a question:

"Why doesn't Ubuntu have a restore/recovery mode like Windows"

You know like F8 and so, I am not new to Linux but get a little scared when trying something out because I don't really know how to undo what I just did if my PC won't boot and furthermore; why is it necessary to continuly update Ubuntu's kernel, why not just have one major update per year instead of every couple of weeks!.

What makes people afraid of Linux is Linux itself due to its vast complexity, if it were made even more user friendly with built-in failsafes that even mere mortals can understand, then just maybe more people would switch to Linux. People have been schooled in the MS school of life and want it kept simple!.

PS: my Ubuntu (Jaunty 9.04) hasn't let me down yet and I do "BACK-UP".

Have a good one chaps.

You have the choice as a user to update any components. Limiting those who wish to have the latest would be wrong by only releasing once a year. 

I have built an off-site server that I only administer remotely, although have 24/7 access if needed to the building. I turned off the updates. If the system is working where it's at for what you use it for, updates are not necessary. Just because updates exist, doesn't mean that you are forced to install them. 

Linux isn't any more complex that Windows. In fact, as I learn more, I come to realize how much easier it is than windows. I come from the old MS-Dos days and when I first begun to use Linux when RedHat was the big-gun, I thought to myself, "What is all this crazy mess". Well, Windows is just as crazy when you get down to the nitty gritty. The difference is, well, Difference. Linux is different and NOT the same as Windows, so therefore, you have to learn something new. If a person started with Windows, it's likely they've learned things along the way. Then, when they feel they have learned most of what's going on, then switch to something else, it's like whoa!... 

Compare it to learning English. Most of the world says it's really the toughest language to learn because of all the different ways we use words and emphasis. Because I grew up 'slowly' learning the language, I can only say learning a different language is to tough because of the way they use words and phrases. And languages like Japanese? Wow, what are all those little squiglies. 

I wonder if the thoughts on Linux complexity would be completely reversed had Windows been something new and everyone already used Linux/Unix???

-Cybie

---

### Post by wsonar on 2009-05-05
Hmmm someone that got frustrated with there lack of knowledge decided to vent about it among a group that would cup his balls for him


seems typical

---

### Post by pwnst*r on 2009-05-05
> **miegiel said:**
> Maybe I do, maybe I don't.

I know there are IT departments that don't have their **** together. I also know there are IT guys that can waste time fixing a machine, while they should ask themselves: "What's the fastest way to get this employee working again?" I know there are employees that will spend ages looking over the IT guys shoulder, instead of doing something useful. And I know that some employees are so connected to their PC and their desk that they can't work anywhere else.

All this doesn't mean you can't fix it in minutes by replacing a PC with one that does work.

hey, that'd be great if nobody needed special apps and/or builds.

that's not the real world in a large company.

---

### Post by Cybie257 on 2009-05-05
> **Idefix82 said:**
> In simple terms, because people who buy Windows give money to a company that then uses this money to eliminate competitors, like for example other OSs. For some reason, people who use other OSs don't like that.

Which is why Linux is only getting bigger. You can't buy a company that isn't really a company. :) It's the whole world and MS is putting every effort, even losing money, to try to crush any competition. But, how can they crush an OS that costs $0.00 with their overpriced OS? 

-Cybie :popcorn:

---

### Post by wsonar on 2009-05-05
I have to say in the real world the fastest IT solution no matter what OS is Reimage

---

### Post by MaxIBoy on 2009-05-05
[I]"You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard.  What OS do you want to be running?  From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks.


If I have to rebuild my worstation and development environment even once then the actual cost of Ubuntu is more that the cost of Vista.  In fact, for every extra time my Ubuntu system crashes hard and fails to boot I could have purchased a new Vista system from Dell, thrown my old system in the trash and still come out ahead.


Linux is the best, if what you like to do is rebuild and reinstall operating systems or endlessly search the internet for cryptic instuctions on how to edit /etc files to make some piece of hardware or software sort of work."[/I]


Yeah, and I suppose [forty bucks for a UPS](http://www.newegg.com/Product/Product.aspx?Item=N82E16842117001) is highway robbery, right?

---

### Post by FuturePilot on 2009-05-05
All I can say is from my own experiences I have had the system go down while installing updates. It wasn't an upgrade but it was still while installing something. This is why we have the recovery mode option. Booted that, selected "Fix broken packages" rebooted after that was done and I was back up and running. So myself not being a frequent Windows user, how exactly does Windows act in this situation?

> **aimpau said:**
> Ok, no i feel embarrased. I forgot to research "ext4", it says there that ext4 filesystem actually holds all data first in the memory before actually writing them on the disk thus IF ever there would be power outtages during an upgrade, no file is corrupted since it was still in RAM and the writing process hasn't begun yet...:) That's how I understand it and pls correct me if im wrong.

BTW, how cheap it is to have a decent RAID setup these days?

Yes, delayed allocation. Correct that no file is corrupted, however you're actually left with no file at all since it never hit the disk.

---

### Post by MaxIBoy on 2009-05-06
> **thewolfman said:**
> I know about the recovery mode function which is accessed by the esc key if not shown in the boot menu but a lot of people new to Linux would not, so my point was that there should be a "Full Recovery" function and not just the "Failsafe" of being asked for your password!. In its current form, Ubuntu recovery mode does not offer an undo/restore function which is really what I am ranting on about!.LaRoza (remember him?) wrote a program for this a while back:
[https://launchpad.net/sysres](https://launchpad.net/sysres)

---

### Post by aimpau on 2009-05-06
> **FuturePilot said:**
> All I can say is from my own experiences I have had the system go down while installing updates. It wasn't an upgrade but it was still while installing something. This is why we have the recovery mode option. Booted that, selected "Fix broken packages" rebooted after that was done and I was back up and running. So myself not being a frequent Windows user, how exactly does Windows act in this situation?



Yes, delayed allocation. Correct that no file is corrupted, however you're actually left with no file at all since it never hit the disk.

Yep, but I'm talking about update files. If they never hit your HD, then you're just back with your old system.

Talking about extensibility, I watched a clip at Youtube on what will happen to a pc if you "sudo rm **censored**" your PC...Guess what, the mouse was still working. :)

---

### Post by FuturePilot on 2009-05-06
> **aimpau said:**
> Yep, but I'm talking about update files. If they never hit your HD, then you're just back with your old system.


Not quite, it's a bit different than that because the file gets truncated before it's written to disk. Basically with Ext4 the way it works is Truncate > Update > Write to disk. The issue is that with Ext4's delayed allocation there's a long delay between Update and Write to disk. If the system were to go down when there's a file in the buffer, you're going to end up with a 0 byte file since it was truncated first and never actually got written to the disk.

If you want to learn some stuff about Ext4, read through some of the comments on [this bug report]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/317781"). The behavior of Ext4 was discussed very thoroughly. Quite interesting really.

---

### Post by thewolfman on 2009-05-06
> **Cybie257 said:**
> You have the choice as a user to update any components. Limiting those who wish to have the latest would be wrong by only releasing once a year. 

I have built an off-site server that I only administer remotely, although have 24/7 access if needed to the building. I turned off the updates. If the system is working where it's at for what you use it for, updates are not necessary. Just because updates exist, doesn't mean that you are forced to install them. 

Linux isn't any more complex that Windows. In fact, as I learn more, I come to realize how much easier it is than windows. I come from the old MS-Dos days and when I first begun to use Linux when RedHat was the big-gun, I thought to myself, "What is all this crazy mess". Well, Windows is just as crazy when you get down to the nitty gritty. The difference is, well, Difference. Linux is different and NOT the same as Windows, so therefore, you have to learn something new. If a person started with Windows, it's likely they've learned things along the way. Then, when they feel they have learned most of what's going on, then switch to something else, it's like whoa!... 

Compare it to learning English. Most of the world says it's really the toughest language to learn because of all the different ways we use words and emphasis. Because I grew up 'slowly' learning the language, I can only say learning a different language is to tough because of the way they use words and phrases. And languages like Japanese? Wow, what are all those little squiglies. 

I wonder if the thoughts on Linux complexity would be completely reversed had Windows been something new and everyone already used Linux/Unix???

-Cybie

You make some very valid points in your post but I wasn't refering to general up-dates but just ranting about up-dates to the kernel itself.

If for example I set-up Avira anti virus which I also have to install Dazuko and then along comes Mr Kernel up-date and he is going to wipe out all my hard work; or am I missing something?.

The main gripe I have is that for people who don't have a good working knowledge of the command line can come seriously unstuck in no time at all. So that is why I am going on about a full restore mode for Ubuntu.

---

### Post by rajeev1204 on 2009-05-06
> **aimpau said:**
> [http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/](http://social.msdn.microsoft.com/forums/en-US/hottechnology/thread/b998ea87-1857-4bd1-ba38-a202c4ce6b97/)


A post by jgalley:

[I]"You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard.  What OS do you want to be running?  From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks.



.


This thread should be closed.Waste of forum space.

---

### Post by slakkie on 2009-05-06
I lolled, Windows can never replace a Unix box (it can, for games). But other then that it is a [Legacy OS](http://www.euronet.nl/users/wesleys/legacyOS.png)

---

### Post by dmn_clown on 2009-05-06
> **forrestcupp said:**
> And those of you who are arguing that it only takes 30 minutes have a pitiful argument.  We all know that it only takes 30 minutes to get a standard installation complete.  But anyone who claims that it only takes 30 minutes to install from scratch *and* have it all set up and ready for your specialized business and needs is just plain wrong.

Guess you've never rolled your own installation disk that had everything pre-configured for your hardware including your own custom builds, configuration files, etcetera.  It is more than possible.

---

### Post by Chame_Wizard on 2009-05-06
It's a good thing Live-CD's are very very powerful.:guitar:

---

### Post by Cresho on 2009-05-06
that is totally stupid.  What forum is this?  forums for idiots?  If I am updating and my system shuts down during an upgrade, my data is safe because its in the home and not root directory.  I can still boot in terminal and restore my partition from a backed up tar file.

who is the idiot who wrote that forum post?  Some idiot!  that's who!

---

### Post by Wiebelhaus on 2009-05-06
> **thewolfman said:**
> Interesting read from all of you, so I have a question:

"Why doesn't Ubuntu have a restore/recovery mode like Windows"

You know like F8 and so, I am not new to Linux but get a little scared when trying something out because I don't really know how to undo what I just did if my PC won't boot and furthermore; why is it necessary to continuly update Ubuntu's kernel, why not just have one major update per year instead of every couple of weeks!.

What makes people afraid of Linux is Linux itself due to its vast complexity, if it were made even more user friendly with built-in failsafes that even mere mortals can understand, then just maybe more people would switch to Linux. People have been schooled in the MS school of life and want it kept simple!.

PS: my Ubuntu (Jaunty 9.04) hasn't let me down yet and I do "BACK-UP".

Have a good one chaps.






System Recovery? Ha! Laughable , I have 7,000+ Service orders and I've disabled every restore partition Why? Because it hardly ever works as intended! Why are most people doing it anyway? Viral infection , What is also restored with the recovery point? A Virus. Absolutely Worthless , I'd rather use half of that 12% disk space to contribute to a lager swap file for increased performance which is How I set up Windows Machines and the other half for storage which is what it was intended for anyway , do you disagree? Doesn't matter it's been working for years and 1,000's of PC's literally.


The only Time I've seen System Recovery work and continue to be viable is when Windows updates pushes through a botched driver and blows the whole installation to smithereens but still any other issues remain.

See in Ubuntu if you have a separate /Home Partition , you could reinstall Ubuntu in twelve Minutes and retain all your settings and data and still reap the benefits of a new installation. How long does System restore normally take? Close to an hour. Ha! Laughable man!

---

### Post by CrazyArcher on 2009-05-06
I don't understand why people should bother discussing whether that idiot is factually right or not, let alone discuss his rave in a more global perspective.

---

### Post by Xbehave on 2009-05-06
reasons he is wrong:
1) journalling filesystem and atomic operations of apt, mean your filesystem will be fine, the same cannot be said for FAT in a crash
2) to boot up and continue the update you only need kernel (which updates always leave one stable version around), bash+dpkg and their libraries (i've never seen any of these updated after a release)
3) I'm fairly sure updates use an atomic method, download, write update files to disk, rename new files over old files, mark update as complete. So the only stage that can cause problem is the rename and you have to be damn unlucky for the power to go out while that is happening.

Windows requires a lot more stuff to successful run updates and if your power goes out while half way through updating one of those files, your totally screwed because you cant chroot into a windows box!

---

### Post by ChadMMc on 2009-05-06
I actually did lose power (actually accidentally knocked the power cord loose) during my ubuntu upgrade from 8.10 to 9.04 and it was not that great a problem at all. (I have my home directory on a separate partition and I save the markings via the synaptic, so no real losses at all...was back up in very little time.  (also I use sbackup and my /var directory is in it's own partition.)

I NEVER had it so easy when doing a windows install.

---

### Post by SuperGeeky on 2009-05-06
Whether this person is an "Idiot" or not I hope isn't the question anymore as long as this thread seems to have gone over a simple inquiry. I do, however, agree with what SX66GNS had to say.  I have repaired, reconfigured, and built from scratch hundreds of computers with every flavor of Windows from 3.1 through Windows 7, and the first thing I do is to turn off the system restore options.  System recovery in the Windows operating system can take almost an hour to perform sometimes, and usually doesn't solve your problems.  I can literally install the operating system, drivers, and applications all over again in the same or less time so the option for system recovery seems to be unneccessary, not to mention it is utilizing precious resources which could be redirected and devoted to doing things which actually matter, like running your games or applications. If you don't want to have to mine your data after a catastophic failure, back up your important documents, pictures, etc.. it is just common sense, regardless of your recovery option.  I am new to Linux, but loving every minute of it! Do I think they need to implement an F8 recovery option or the like? No way, what's the point. From the stability I have witnessed from my installations of both desktop and server editions of 8.10 and 9.04, I don't believe I will even _think_ of a recovery option anytime soon.

---

### Post by forrestcupp on 2009-05-06
> **miegiel said:**
> Maybe I do, maybe I don't.

I know there are IT departments that don't have their **** together. I also know there are IT guys that can waste time fixing a machine, while they should ask themselves: "What's the fastest way to get this employee working again?" I know there are employees that will spend ages looking over the IT guys shoulder, instead of doing something useful. And I know that some employees are so connected to their PC and their desk that they can't work anywhere else.

All this doesn't mean you can't fix it in minutes by replacing a PC with one that does work.

Well, you're right that things *should* be like that.  But it rarely is like that in the real world.

Also, swapping computers out only works if all files for work in progress are saved to the network drive.  More and more, people are using laptops so they can work from home and dock to the docking station at the office.  So more and more, some files are getting saved to the local drive.  Also, those 3 extra computers would have to have all of the software installed that every department uses, or they would have to take the time to install the specific software that the affected department uses.

Hey, I think the guy's arguments are total bunk and he doesn't have a clue what he's talking about.  But I also realistically know that if something did happen that actually would call for a network reinstall, it would take a lot of time and work.  And time is money.

---

### Post by Thanh-BKK on 2009-05-15
Hello.

Guess what? I had the exact situation today!! I managed to convince my boss to give Linux a try, as we had a couple of computers that were screwed up anyway.... so i put Jaunty on them, a test run so to speak. One a couple of days ago, the other today. Installed from the Jaunty Beta-CD and updated.

And about half way through the installation of the 345 MB of updates we had one of those half-second power cuts that are soooo common here in Bangkok. 

It was enough to send that Compaq Deskpro into Nirvana - Ubuntu flat refused to boot. Or wait, it does something? "Ubuntu is running in low graphics mode". This cycled a few times, appeared to hang - and suddenly i got another graphical Window with the option to "repair broken packages". Selected that and it started rummaging around, running text through the screen for some 25 minutes (yes, the other one took well over an hour to complete the initial update - those ARE slow computers!) and then - it shut down itself!

So i turned it on - and it booted into a beautiful, fully updated Jaunty :)

Now if someone would tell me how to make a CD from the currently installed system so i can put it 1:1 on another machine i'd be happy as Larry - as we have 22 more of those identical machines and i just can't wait to have them ALL run Ubuntu :) My boss said "if something breaks on the Windows ones, just put your Linux on". Windows breaks easy.... with a little help if need be.....

Kind regards.....

Thanh

---

### Post by Paqman on 2009-05-15
> **Thanh-BKK said:**
> 
Now if someone would tell me how to make a CD from the currently installed system so i can put it 1:1 on another machine i'd be happy as Larry - as we have 22 more of those identical machines and i just can't wait to have them ALL run Ubuntu :) My boss said "if something breaks on the Windows ones, just put your Linux on". Windows breaks easy.... with a little help if need be.....

Kind regards.....

Thanh

[Clonezilla]("http://clonezilla.org/") is your friend. You can make an image of your installed system and clone it to as many machines as you want simultaneously.

---

### Post by Regenweald on 2009-05-15
> **thewolfman said:**
> Interesting read from all of you, so I have a question:

"Why doesn't Ubuntu have a restore/recovery mode like Windows"

.

When i messed my xorg.conf first time i attempted manual install of the nvidia 180.xx series and tried 'sudo shutdown now' I was give some recovery options. Also the first time i had ext4 problems( think it had something to do with utorrent) the system went straight to an fsck recovery environment at boot.
So recovery has never been a big problem for me, but i see the point being made about DEDICATED recovery tools. 

Although, it has to be said that with the GNU/Linux community, ANY live cd is a fully functional recovery suite :) I guess that's why recovery tools are not such a big deal. If windows crashes and right after BIOS you go to blue screen, a Puppy, Knoppix, Ubuntu etc live cd becomes an invaluable data recovery tool before a full windows re-install.

---

### Post by Regenweald on 2009-05-15
> **Thanh-BKK said:**
> [snip] Windows breaks easy.... with a little help if need be.....

Kind regards.....

Thanh

LOL you made my day man..... pure mischief.... :)

---

### Post by tkoco on 2009-05-16
Quite a message thread. I use both Ubuntu and MS Windows. Both will crash if the hardware goes bad. Neither OS likes a loss of power. Each OS has it's own quirks. Given a choice, I prefer Ubuntu over MS Windows - not because of costs - rather, Ubuntu just plain works out of the box and has basic functionality/programs "ready to use". Not so with MS Windows. This is a pragmatic point of view - no religious wars, please.

---

### Post by marco123 on 2009-05-16
All this over some guy that hasn't got a clue what he's talking about.:lol:

It takes me  25 minutes to install Ubuntu, another 25 to install any updates.

To install all the extra programs I need: 

> sudo apt-get install audacious conky devede dvdrip lm-sensors sensors-applet ubuntu-restricted-extras

Compare THAT to finding and downloading the newest version of everything, including 50MB of security software, then clicking next 48 times.

Oh well, at least Ubuntu can't get hacked easily like Windows and OS X. [http://news.softpedia.com/news/Mac-OS-X-Hacked-Vista-SP1-Hacked-Ubuntu-Linux-Survives-Unscathed-82079.shtml](http://news.softpedia.com/news/Mac-OS-X-Hacked-Vista-SP1-Hacked-Ubuntu-Linux-Survives-Unscathed-82079.shtml)

Edit: At least he is right about a power cut bringing Linux down.  I had a power cut after 45days uptime in October 2007; the first and only time Ubuntu has shut down without me telling it to.  I just booted it back up.

---

### Post by miegiel on 2009-05-16
> **marco123 said:**
> ...

Edit: At least he is right about a power cut bringing Linux down.  I had a power cut after 45days uptime in October 2007; the first and only time Ubuntu has shut down without me telling it to.  I just booted it back up.

I think you're missing his point. The point he's making (as I see it) is that ***_Vista_***'s superior updating and the NTFS journaling file system will prevent loss of power to destroy Vista beyond easy repair even while Vista is updating the OS. While if the same happened while updating Ubuntu you would be up ****'s creek.

Of course he's just echoing Vista's selling points (over windows XP mainly).

Regardless, his knowledge makes him blind of his ignorance, and he's pretty damn ignorant :twisted:

---

### Post by blastus on 2009-05-16
> You are doing an automatic upgrade of your OS and in the middle of the application of the patches the power fails and your system crashes hard. What OS do you want to be running? From my experience if it is Linux then you are about to see firsthand why Ubuntu is free and Vista costs 400 bucks.

If I have to rebuild my worstation and development environment even once then the actual cost of Ubuntu is more that the cost of Vista. In fact, for every extra time my Ubuntu system crashes hard and fails to boot I could have purchased a new Vista system from Dell, thrown my old system in the trash and still come out ahead.

All I can say is this guy must be extremely inept if it costs him $400 to rebuild his computer. So even if he made $50/hour he is saying it would take him 8 hours to rebuild it. Sorry man but that just screams incompetence--if I owned a repair shop I would fire you.

> Linux is the best, if what you like to do is rebuild and reinstall operating systems or endlessly search the internet for cryptic instuctions on how to edit /etc files to make some piece of hardware or software sort of work.

This is a load of BOVINE SPONGIFORM. The same criticism can also be easily leveled against Windows.

I setup a Ubuntu machine for someone about a year ago. I did not have to configure anything on that machine to get it to work except install an NVIDIA driver. I didn't even have to download the driver, I just had to click with a mouse button when automatically prompted that drivers were available. In Windows you would have to go and find the driver on the Internet, download it, and then install it. In Ubuntu you only have to activate it when prompted.

This person has never used a computer before and found Ubuntu to be really easy to use. He UPDATES the OS by clicking (with an actual mouse button) on the software updater that Ubuntu automatically presents when updates are available. He has never had a problem with the computer yet and this has been what a year now.

He recently got a digital camera and hooked it up to the computer and transferred images from the camera WITHOUT ANY HELP FROM ANYONE. This is from someone who has never used a computer before.

---

### Post by Kareeser on 2009-05-16
He mentiones all the downtime you get reinstalling an Ubuntu system... but if you pull the power cord halfway through a service pack upgrade, you're going to easily spend double that time reinstalling everything else...

---

### Post by marco123 on 2009-05-16
> **miegiel said:**
> I think you're missing his point. The point he's making (as I see it) is that ***_Vista_***'s superior updating and the NTFS journaling file system will prevent loss of power to destroy Vista beyond easy repair even while Vista is updating the OS. While if the same happened while updating Ubuntu you would be up ****'s creek.

Of course he's just echoing Vista's selling points (over windows XP mainly).

Regardless, his knowledge makes him blind of his ignorance, and he's pretty damn ignorant :twisted:

Agreed, that could have dire effects on either OS.  I think I'd just boot into an earlier Kernel though if it happened in Linux.

I think the fact that he thinks that file system journaling is Windows/NTFS only sums it up though.:lol:  (Which is the OS that can only read 2 file systems, both it's own?) [http://en.wikipedia.org/wiki/File_system#File_systems_under_Microsoft_Windows](http://en.wikipedia.org/wiki/File_system#File_systems_under_Microsoft_Windows)

From Wikipedia:
> The File Allocation Table (FAT) filing system, supported by all versions of Microsoft Windows, was an evolution of that used in Microsoft's earlier operating system (MS-DOS which in turn was based on 86-DOS). FAT ultimately traces its roots back to the short-lived M-DOS project and Standalone disk BASIC before it. Over the years various features have been added to it, inspired by similar features found on file systems used by operating systems such as Unix.

I love the fact that they sued Tom-Tom for using FAT.

---

