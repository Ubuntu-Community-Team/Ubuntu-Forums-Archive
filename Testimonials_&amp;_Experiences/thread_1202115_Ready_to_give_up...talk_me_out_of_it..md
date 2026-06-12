---
title: "Ready to give up...talk me out of it."
date: 2009-07-01
forum: Testimonials &amp; Experiences
---

### Post by juelze on 2009-07-01
So, I've used Windows all of my life, but I was always interested in trying Linux.  One day, after having to reinstall Windows XP due to some problems, I figure "What the heck, I should try Linux!"  I download Wubi and am pretty intrigued with Ubuntu.  I figure I'll put off Linux for now and go back to Windows XP, but I'll order the free CD to toy with.  

I get Ubuntu 8.10 in the mail and after having further issues with XP, I decide to do a full install of Ubuntu.  Everything runs great and I'm happy with it.  Jaunty is released soon after and I go to do an upgrade via the upgrade manager.  Everything goes smooth and it runs really well.  The next day I go to boot up and there are some updates that I install and next thing you know I can't get into Ubuntu anymore.  Frustrated, I go back to XP but really miss how fast and rock solid (security wise) Ubuntu is.  So, I post on the forums here and someone said to give Jaunty another go but stay away from the FGLRX drivers as they cause issues (I have an ATI 9800 Pro).  So, I give Jaunty another try and it runs like a dream.  I can even run Compiz now!!!

Fast forward a month and I go to do some update and now it seems some remnants of the FGLRX drivers are back on my PC via the Update Manager.  ARGH!  I post in this thread:

[http://ubuntuforums.org/showthread.php?t=1201250](http://ubuntuforums.org/showthread.php?t=1201250)

And I follow the instructions, but things are still not working for me.  So, now I'm at a turning point.  Part of me things I should just reinstall Jaunty and give it another go.  However, part of me thinks that it's pretty lame that I have to avoid an update just to have my PC run the way I want it, so I should go back to XP.  However, part of me hates dealing with the ongoing maintenance of XP (virus scans, spyware updates, etc. etc.)

So, what to do?  Part of me just says to heck with both operating systems...I'll just get a Mac!  But I really don't like that idea.  

I know there is a lot of learning with Linux, and I'm okay with that.  But it was running fine without a lot of maintenance and just doing an update as hampered the performance I was enjoying.  So frustrating!!!!  Sorry for my rant, but I REALLY want to continue to use Ubuntu but it can be so frustrating at times.

Cheers,
Juelze

---

### Post by overdrank on 2009-07-01
Sorry to hear of your troubles, Have you considered trying Hardy 8.04? :)

---

### Post by Geoff918 on 2009-07-01
Well, there are other distros, too. I really, really like Jaunty. I really didn't like Ibex (8.10) and used openSUSE instead. I really fell in love with SUSE until I tried the new Ubuntu and made the switch back. Certain things in SUSE were bothering me, but I did like the RPM support, etc.  What sort of upgrades are you doing? Are you doing them from the terminal?

---

### Post by nhasian on 2009-07-01
hello juelze,

sorry to hear about your troubles.  the good news though, is that you know what package is giving you problems.  Once you have your Ubuntu up and running, go to System->Administration->Synaptic Package Manager and find the FGLRX drivers that are giving you trouble.  Highlight the package and go to *Package* in the menu and select *Lock Version*.  Now it will not be upgraded and you wont have to worry about an upgrade messing your system up.

---

### Post by hansdown on 2009-07-01
Hi juelze.

Don't let re-installs put you off.I've done quite a few, due to my
care-free approach to learning new things.It's sometimes easier than
figuring how to fix an os that is brand new to you.Plus it gives me more
experience with installing.

As overdrank said, 8.04 is rock solid to learn on.Updates are pretty
safe.

---

### Post by Chemical Imbalance on 2009-07-01
Welcome to the joys & frustrations of linux!

You can try distro-hopping: [http://distrowatch.com/](http://distrowatch.com/)

Or go back to Intrepid or Hardy until Karmic.

Or dig in and find the solution to your problem.

Everything has its advantages and disadvantages. 

Ask yourself, "Is Linux worth it"?  Maybe make a mental list of the pros and cons for windows and linux and see what wins.

Good luck.

---

### Post by Tamlynmac on 2009-07-02
I have a philosophy that might work for you.

Before returning to Windows or buying a Mac - try 8.04 (Hardy). If it fails, all you've done is spent a little time making the attempt. Download the file, burn a disk and give it a try.

Many people still use 8.04 and are extremely satisfied with that version of Ubuntu.

Nothing ventured - nothing gained.

Good Luck with what ever decision you make.

---

### Post by xeticus on 2009-07-02
> **nhasian said:**
> hello juelze,

sorry to hear about your troubles.  the good news though, is that you know what package is giving you problems.  Once you have your Ubuntu up and running, go to System->Administration->Synaptic Package Manager and find the FGLRX drivers that are giving you trouble.  Highlight the package and go to *Package* in the menu and select *Lock Version*.  Now it will not be upgraded and you wont have to worry about an upgrade messing your system up.I was just browsing the thread and saw this. I don't have the OP's problem but it's really nice to know you can lock a package to keep you from having problems. Thank you!

---

### Post by steveneddy on 2009-07-02
I started usinfg Ubuntu at version 5.something.

Yes it can be frustrating.

I recommend using Hardy as it is more stable than the newer versions (it the Long Term Supported version) until the next LTS comes out in April.

Good luck. Choose what works best for you.

---

### Post by caravel on 2009-07-02
If you can do without compiz and don't play games - then avoid the ATI proprietary fglrx driver.  Just do a clean install and do not enable the "restricted driver" for ATI from "hardware drivers" - it's that which actually downloads installs and configures the fglrx kernel module.  Avoid that and you'll be ok.  Updates often break it and your card won't run with the latest fglrx driver that comes with Ubuntu 9.04 anyway.

If you have the Ubuntu 8.10 on disc just install that, then immediately do a dist upgrade from update manager or the terminal before doing anything else.  If all goes well you should not be bothered to install the restricted driver as it won't be available.

---

### Post by betrunkenaffe on 2009-07-02
As another word of wisdom, avoid blind updates, take a quick look through the programs that will be updated and if there's any in there that you think "I wonder", don't do it and check it up first. I have a wine update waiting to be done (for a few months now) because if I leave 1.1.20 then Guild Wars (main reason I have wine) won't work.

Think of it this way, you have your entire machine updating through update manager, not just the OS. These issues wouldn't arise in Windows because it doesn't do anything but itself and every other app has to fend for itself.

If you are getting annoyed, dual boot, saves you the reinstall of Linux later the next time Windows pisses you off :P

As suggested, check out other distros as well, some good ones out there.

---

### Post by automaton26 on 2009-07-02
> Lock Package
> avoid blind updates

These are both good suggestions if you don't want update hassles.

The update manager in (Kubuntu?) 9.04 also has some better description text, which can help.

---

### Post by Simian Man on 2009-07-02
I know it doesn't help your current situation, but next time you buy a computer, go with Nvidia over Ati.

---

### Post by juelze on 2009-07-02
Whoa.  Thanks for all the great responses!!!  I haven't tried Hardy, but I'm thinking I'll just reinstall Jaunty now that I know I can lock the driver version down as someone mentioned.  I also appreciate the advice about going through the updates instead of blindly installing them all.

I'm also thinking about getting a Nvidia card, but since I have a 9800 Pro (ATI) and no PCI express, it's hard to find a card for a decent price that works with AGP.

Also, I read that Linux is more secure then Windows.  However, I read someone stating that "no one breaks into the porta-potty at the construction site, but someone will try to break into the bank up the street, does that make the porta-potty more secure?"  So is Linux really more secure in Windows?  Or is it simply not in the hackers best interest to spend time on Linux?

Anyway, again, thanks to everyone for reinvigorating my interest in Linux.  I'll be doing a reinstall tonight!

---

### Post by armandh on 2009-07-02
> **Simian Man said:**
> I know it doesn't help your current situation, but next time you buy a computer, go with Nvidia over Ati.

+1 for now

but levels of support from the manufacturer change over time

my DDS32 printer works great in xp with the last driver available [2K beta] and I have it printing 2 sided with Ubuntu, but not other features. since support ended about the time of Studebaker production, there is no hope for Vista which is a total cluster **** when it comes to unsupported orphan equipment drivers.

very secure, most of the major server farms are linux
cute but invalid arguement ..... best return for effort is why hackers prefer windows. 
[which wont ast 20 minutes with out an AV slowing it down.]

open source is peer review security. found an fixed early.
.

---

### Post by 3rdalbum on 2009-07-02
> **juelze said:**
> Also, I read that Linux is more secure then Windows.  However, I read someone stating that "no one breaks into the porta-potty at the construction site, but someone will try to break into the bank up the street, does that make the porta-potty more secure?"  So is Linux really more secure in Windows?  Or is it simply not in the hackers best interest to spend time on Linux?

Linux *is* the bank. Linux-based systems send, receive and transmit most of the world's credit card details. They also store and retrieve most industrial and government secrets.

What it really comes down to is that Windows was originally written with the assumption that each PC it runs on would have just one user and no Internet access. Linux was written with the assumption that each Linux machine would have multiple users and be permanently network-connected. Eventually, Windows had security features bolted-on, but nothing was designed from the get-go to be secure. There is a culture of "writing for security" around Linux-based development that simply doesn't exist with Windows.

---

### Post by caravel on 2009-07-02
> **juelze said:**
> I'm also thinking about getting a Nvidia card, but since I have a 9800 Pro (ATI) and no PCI express, it's hard to find a card for a decent price that works with AGP.
As I said it depends on what you want to do.  If you're not gaming and compiz is not that important then don't even consider changing the card - stick the open source Radeon/ATI driver.

If you do want an Nvidia card you should still be able to get hold of a budget Nvidia 7300GT AGP for about £30

---

### Post by HappyFeet on 2009-07-02
> **hansdown said:**
> Hi juelze.
Don't let re-installs put you off.I've done quite a few, due to my
care-free approach to learning new things.It's sometimes easier than
figuring how to fix an os that is brand new to you.Plus it gives me more
experience with installing.


I must have reinstalled 50 times. I didn't give up, and now I'm the happiest computer user in the world. 

Consider how long it took you to learn windows, then compare the 2. See?

If you don't want to learn something new, or use a different distro, then by all means use windows. Bill will take you back with open arms.

---

### Post by eldragon on 2009-07-02
keep a separate home partition, backup your /etc folder (shouldnt be big), reinstall... if you remember it took you ages to setup samba (or anything else), restore the needed config files... your system will be as you remembered it in no time (if there is a package missing, just install, all your settings will be magically back if you backed up your home).

---

### Post by Jestersage on 2009-07-02
Funny thing is that in the past, I dislike Ubuntu due to the reliance of CLI. Now I ended up pulling out the GUI and do most of the stuff through CLI, including reinstallation of the kernel.

Another way to ease the transition of Ubuntu is to spend a little bit of money to buy a basic system, especially if your city have a FreeGeek. I manage to purchase $30 worth of equipment ($50 if you include case and hard drive) that make a really good secondary desktop. (and that's because I have a top-of-the-line case. Sometimes you can buy a "scrap case" as scrap for $2 worth.)

---

### Post by s3a on 2009-07-02
Wasn't fglrx the issue all along since the fglrx update stopped supporting your card? Just use the open source driver. Open source drivers always support your device.

Take my webcam for instance, through upgrades, it still works while in the Windows world, after XP, it is no longer supported and I cannot use it anymore! On the other hand, I am really anticipating the video conference feature of empathy for the MSN protocol.

---

### Post by evermooingcow on 2009-07-02
The way I got into Linux was home servers. Try applying Linux where it clearly does better than Windows - servers - and you might appreciate it enough to want to learn more. Good motivation to learn the CLI too.

---

### Post by betrunkenaffe on 2009-07-02
Just as another point on that little example. Are you likening your computer with Windows to a porta potty and your computer with Linux as a bank?

Wait, I think you've really already made the point with that comparison.

Nothing is 100% secure, just like your home, a thief can break your windows, cut through your wall or drive a car through it. One way or another, you can always get in. That doesn't mean you need to leave every window open and valuables nicely packaged so anyone can just walk through the open door and take it.

Linux by default is more secure, it minimizes the inherent security holes of the system so the major source of security risk is you. Windows has all the windows and doors open and tries to bar them up so no one can get in. While it works for a while, a smart person can still get through the patchwork security and it's still susceptible to the same vulnerability, you. Worst thing about that system is that it also makes it alot harder to get out when you want to.

Use what works for you, all computers have a price to pay, Windows it's money and security, Linux is time and effort. Once I paid that time and effort when I first started, I really don't have to pay anymore but Windows is still stuck with massive security flaws even after you've paid off the credit card.

---

### Post by Shadowking on 2009-07-03
> **juelze said:**
> So, I've used Windows all of my life, but I was always interested in trying Linux.  One day, after having to reinstall Windows XP due to some problems, I figure "What the heck, I should try Linux!"  I download Wubi and am pretty intrigued with Ubuntu.  I figure I'll put off Linux for now and go back to Windows XP, but I'll order the free CD to toy with.  

I get Ubuntu 8.10 in the mail and after having further issues with XP, I decide to do a full install of Ubuntu.  Everything runs great and I'm happy with it.  Jaunty is released soon after and I go to do an upgrade via the upgrade manager.  Everything goes smooth and it runs really well.  The next day I go to boot up and there are some updates that I install and next thing you know I can't get into Ubuntu anymore.  Frustrated, I go back to XP but really miss how fast and rock solid (security wise) Ubuntu is.  So, I post on the forums here and someone said to give Jaunty another go but stay away from the FGLRX drivers as they cause issues (I have an ATI 9800 Pro).  So, I give Jaunty another try and it runs like a dream.  I can even run Compiz now!!!

Fast forward a month and I go to do some update and now it seems some remnants of the FGLRX drivers are back on my PC via the Update Manager.  ARGH!  I post in this thread:

[http://ubuntuforums.org/showthread.php?t=1201250](http://ubuntuforums.org/showthread.php?t=1201250)

And I follow the instructions, but things are still not working for me.  So, now I'm at a turning point.  Part of me things I should just reinstall Jaunty and give it another go.  However, part of me thinks that it's pretty lame that I have to avoid an update just to have my PC run the way I want it, so I should go back to XP.  However, part of me hates dealing with the ongoing maintenance of XP (virus scans, spyware updates, etc. etc.)

So, what to do?  Part of me just says to heck with both operating systems...I'll just get a Mac!  But I really don't like that idea.  

I know there is a lot of learning with Linux, and I'm okay with that.  But it was running fine without a lot of maintenance and just doing an update as hampered the performance I was enjoying.  So frustrating!!!!  Sorry for my rant, but I REALLY want to continue to use Ubuntu but it can be so frustrating at times.

Cheers,
Juelze
Ubuntu is free and very young! There are bugs that have been solved YEARS ago by Apple and Microsoft. That's why you have to pay for them; and that's why you have to do some of the work in order to get ubuntu running properly. It's frustrating, but heck....for something that's free, isn't it pretty damn good?

---

### Post by juelze on 2009-07-03
> **s3a said:**
> Wasn't fglrx the issue all along since the fglrx update stopped supporting your card? Just use the open source driver. Open source drivers always support your device.

Take my webcam for instance, through upgrades, it still works while in the Windows world, after XP, it is no longer supported and I cannot use it anymore! On the other hand, I am really anticipating the video conference feature of empathy for the MSN protocol.

How do I go about preventing FGLRX from install?  I know I can lock the packages in Synaptic (thanks for the tip!), but how do I lock the open source driver to prevent FGLRX from installing?

---

### Post by HappyFeet on 2009-07-03
This is not a support forum. Start a thread in the appropriate forum, and people will be more than happy to help you.

---

### Post by Tamlynmac on 2009-07-03
I always have a couple of simple questions that immediately come to mind when reading threads that have titles similar to this.

1. **Why** would anyone post on a forum asking others to convince them to continue using a specific software product? It's seems logical to me that if it works - I use it, if not - I don't. Asking others to convince me is (IMHO) foolish. I trust my own common sense to make a logical decision based on functionality, need and expectation. Asking this question on a forum sponsored by that software and expecting negativity, just doesn't make any sense to me. Or is that the purpose of making the statement "Ready to give up...talk me out of it". I really don't understand.

2. **Why,** when asking others to justify something, does it result in arguing? Seems if someone was seriously asking others to "talk them out of it" they would either accept the responses or give up. It's been my experience when reading threads with this in the title, that it's an open invitation to bash and arguing over the + & -'s of the software. So why not just say that????

I'm often confused as to the motivation of others that seem to intentionally use terminology that is oblique. Of course, it is possible that I misinterpret their intentions.

[juelze]("http://ubuntuforums.org/member.php?u=809993"):
Ever notice at a construction site that has crane, the porta-potty is hung from the crane when the construction site is vacant (especially during bridge work). Ever wonder why they would go out of their way to protect it? After all it's just a porta-potty. That is until you need it - then it's often a place of great assuagement ([http://www.merriam-webster.com/dictionary/assuagement](http://www.merriam-webster.com/dictionary/assuagement)). ;)
Construction site vandalism is often targeted at said enclosures and thus many sites go out of their way to protect them (for multiple reasons).

[> ]("http://ubuntuforums.org/member.php?u=335139")[HappyFeet]("http://ubuntuforums.org/member.php?u=335139")
This is not a support forum. Start a thread in the appropriate forum, and people will be more than happy to help you. 	

+1
Again, you point out the obvious.

---

### Post by juelze on 2009-07-04
> **Tamlynmac said:**
> I always have a couple of simple questions that immediately come to mind when reading threads that have titles similar to this.

1. **Why** would anyone post on a forum asking others to convince them to continue using a specific software product? It's seems logical to me that if it works - I use it, if not - I don't. Asking others to convince me is (IMHO) foolish. I trust my own common sense to make a logical decision based on functionality, need and expectation. Asking this question on a forum sponsored by that software and expecting negativity, just doesn't make any sense to me. Or is that the purpose of making the statement "Ready to give up...talk me out of it". I really don't understand.

2. **Why,** when asking others to justify something, does it result in arguing? Seems if someone was seriously asking others to "talk them out of it" they would either accept the responses or give up. It's been my experience when reading threads with this in the title, that it's an open invitation to bash and arguing over the + & -'s of the software. So why not just say that????

I'm often confused as to the motivation of others that seem to intentionally use terminology that is oblique. Of course, it is possible that I misinterpret their intentions.

[juelze]("http://ubuntuforums.org/member.php?u=809993"):
Ever notice at a construction site that has crane, the porta-potty is hung from the crane when the construction site is vacant (especially during bridge work). Ever wonder why they would go out of their way to protect it? After all it's just a porta-potty. That is until you need it - then it's often a place of great assuagement ([http://www.merriam-webster.com/dictionary/assuagement](http://www.merriam-webster.com/dictionary/assuagement)). ;)
Construction site vandalism is often targeted at said enclosures and thus many sites go out of their way to protect them (for multiple reasons).

[URL="http://ubuntuforums.org/member.php?u=335139"]

+1
Again, you point out the obvious.

Whoa, easy there fella.  I guess my post was out of frustration because I had Ubuntu working fine, and I loved it.  Then, some update gimped my OS.  So, I guess I was looking for a little reassurance as well as some other people to share their struggles and successes.  My "bash" with the analogy about Linux and the porta-potty wasn't mean to be a negative about Linux.  I always heard that Linux was far more secure then Windows.  The analogy I posted I read on another site and thought to myself "Gee, I thought Linux was really secure, but maybe the lack of viruses and other negative software aspects is because it's such a small percentage of PC users."  So, that analogy wasn't my comment, just quoting something I read and hoping someone would disprove it.

Anyway, sorry to have ruffled your feathers.

Cheers,
Juelze

---

### Post by Tamlynmac on 2009-07-04
> juelze
Anyway, sorry to have ruffled your feathers.

You did not ruffle my feathers. As I indicated in my response:
> I'm often confused as to the motivation of others that seem to intentionally use terminology that is oblique. Of course, it is possible that I misinterpret their intentions.
I often don't understand why individuals title threads similar to yours, when their intent is either to seek help (which should be done as HappyFeet suggested), or they only wish to become argumentative.

It's been my experience that when someone posts a similar title on the forum, they often are attempting to circumvent the "Help Section" process or immediately start bashing and complaining about the OS. As HappyFeet suggested, if you post a thread in the appropriate help section the odds are you will receive assistance. Assuming someone can provide said assistance.

As for the porta-potty, I assumed (bad idea) you had quoted it based on the concept you found it enlightening or shared the belief.

As I said you did not ruffle my feathers, just hoped your thread wasn't going to emulate the threads I've read previously with a similar title.

Good Luck

---

### Post by evermooingcow on 2009-07-04
> **juelze said:**
> Whoa, easy there fella.  I guess my post was out of frustration because I had Ubuntu working fine, and I loved it.  Then, some update gimped my OS.  So, I guess I was looking for a little reassurance as well as some other people to share their struggles and successes.  My "bash" with the analogy about Linux and the porta-potty wasn't mean to be a negative about Linux.  I always heard that Linux was far more secure then Windows.  The analogy I posted I read on another site and thought to myself "Gee, I thought Linux was really secure, but maybe the lack of viruses and other negative software aspects is because it's such a small percentage of PC users."  So, that analogy wasn't my comment, just quoting something I read and hoping someone would disprove it.

Anyway, sorry to have ruffled your feathers.

Cheers,
Juelze
As many have similarly brought up people seem to forget that Linux is only vastly outnumbered in the Desktop market.
Linux is very competitive in the server world where unlike personal computers, security is often a real issue. Linux is not an obscure target - at least not where it matters.

---

### Post by aago1254 on 2009-07-05
Okay  let me start with something here . i do understand the issue you are having. but let me tell ya i had alot of issues with 8.10  tell you what happened to me.. 
 
 
i was using linux mint 5 (ubuntu 8.04 )was working great i started using linux mint 6(ubntu 8.10) i was like whats the problem with 6 why is it always not working freezing having problems.  so i said heck with mint i think im good enough to use ubuntu now.  so i install 8.04 and wow it was back to how good mint 5 was running.. so i said umm i should go to 8.10  so i go to 8.10 and i start having a unstable machine again im like what is going on here so i BACK up my system and wipe it AGAIN and put 8.04 back on it.   and i said well this is a waiting game.  so i wait and wait and wait and now i use 9.04 and wow it runs better than 8.04  and i am able to use ext4 and it just runs great all my java works all my stuff works the way it should.   
 
I dont know may be it was the stuff i was trying to install on ubuntu 8.10 it could have been the novice in me who knows.  but lets say if i am willing to wipe a perfectly good running home server from windows to ubuntu server.. i guess im here to stay with ubuntu for a long time.. 
 
the boat with windows has left but im here to stay with ubuntu.. 
 
im not saying microsoft is bad or windows is bad im not like that i grew up with dos and windows 98-vista   and NO VISTA didnt make want to leave it was hard to leave vista if they had ubuntu 9.04 back in the time of xps main glory i would have left sooner i hated xp and always will hate xp.  but windows 2k and 98 se and vista are really good os's for there time but xp always seems problematic .. 
 
anyway in a few years my wife will take windows off her comptuer and we will be a full linux household...  :guitar: just think ubuntu will runs better than windows.. im waiting for 9.10  its going to be good. 
 
apple snow leopard is out sept 2009 
windows seven  oct 22 2009 
and ubuntu 9.10 oct 2009 
 
so we will see who is going to see some changes happen in the computer world
 
also not a time to buy a mac snow leopard is going to be 64bit and that is no 32 bit atleast this is what apple says.  that is going to cause problems with programs and companies are going to have to build 64 bit software and hardware issues might happen and im just waiting for a stupid commercails to start happining any who have a good day

---

### Post by juelze on 2009-07-22
So, after using Windows for years, I finally switched to Ubuntu for the past few months having been intrigued by it.  Well, my first install went fine (8.10) but after FGLRX got installed, my 9800 Pro suffered in some web applications.  I tried Jaunty when it came out, stayed away from FGLRX and things seemed to be better.  However, I didn't get the graphical performance I want.  "Get Nvidia!" said the Ubuntu locals as they offer more Linux support.  So, I drop $40 on eBay and get myself a Nvidia 6600GT.  

My 6600GT arrives in the mail and I back up my stuff, install the card and completely reinstall Ubuntu (9.04).  I go into System>Admin>hardware drivers and install the Nvidia 180 drivers.  As I restart I'm eagerly awaiting the REAL Linux experience where everything is free and runs great.  Turns out that this was just the start of my Linux nightmare.  After the restart I get a black screen.  I reboot, go into GRUB, do the autofix graphics problems and I'm in....640x400 hell.  Great.  I read the forums, post some questions in the forums and all I get is crickets chirping.  I get a few responses but most of them do not offer any real clue as to why it's happening.  Basically, throw some junk against the wall and hope it sticks.  Ugh.  Not wanting to give up on Linux I try 8.04 today.  Guess what?  Same garbage.  

Here I was hoping that I would get some outpouring of support on these forums, but in all honesty, I had to beg for the little help I got.  It really wants me to say "screw you Windows" and "Screw you Linux" and get a Mac and ditch all this garbage.  Sorry to be ranting here, but I have a basic PC and was hoping that Linux would give me a stable OS that was rock solid and would be good enough for web surfing, but in reality, it just isn't that.  Thank god I got my netbook that runs XP.  Ya, it might be prone to viruses and other junk, but at least it works, whereas Linux takes hours of fiddling around with no help except for running through page after page after page of sudo this and that and no real luck.

Again, sorry for ranting, but for a beginner entering the Ubuntu world I haven't had a really good experience.  I pity the poor PC newbie who ventures into the Linux world, because if it doesn't work out of the box, they'll be reinstalling Windows in a heart beat.  If Linux is ever to gain traction with the majority of computer users then these issues need to be ironed out.

Thanks for reading my rant...or ignoring it.  Right now I need to figure out what I want to do.  I hate spending more money on a basic PC just to be used for web surfing, and I really wish I could get Ubuntu working.  But the lack of support and the plethora of problems is making me regret ever trying this.  :-(

---

### Post by HappyFeet on 2009-07-22
If you are willing to plop down ~1500 for a mac, why not just get a computer with linux preinstalled? They are guaranteed to work well. (and save **a lot** of money)

Not every computer in the world will run every OS perfectly. Don't judge linux based on 1 computer. I know many people that use and love linux, and would never use anything else. But yeah, first impressions do make a difference. It's not that linux sucks, it just sucked on that computer.

Anyway, if you feel the need to get a mac, go right ahead and do it, as it's your money. Good luck and peace be with you.

---

### Post by aysiu on 2009-07-22
Macs have problems, too. They are computers, not magic.

But HappyFeet is right--if you're going to give Linux a proper chance, buy it preinstalled before you go Mac.

---

### Post by Arup on 2009-07-22
ATI is an issue with Linux, point is Mac is not a saint and in recent times some glaring security issues have popped up regarding Mac but if it works for you, well and good.

---

### Post by LADmaticCA on 2009-07-22
I'm sorry you had problems with video. My first experience with Ubuntu was very much the same (blank screen after Nvidia driver install), but I was determined to find a solution because I really liked the layout of the Gnome desktop, and I could see the performance increase of my machine. Turns out the solution was very simple but it did take a long time to find. Since then I've fallen in love with this OS and the freedom it brings, and I'm really glad I toughed it out. Your monitor's not using DVI is it? Cause that was my problem. Anyway, I wish you luck in whatever you decide to do.

---

### Post by Dullstar on 2009-07-22
Ubuntu + Windows = headache, in my opinion.

Why?  See "Windows"

This is what I want, personally.

Mac OS X & Ubuntu = Guaranteed awesome computer

---

### Post by DeepEllum on 2009-07-22
Take it from someone who went from windows to mac... to only go back to windows to end up with Linux. Apple has the MOST RESTRICTIVE software I have ever seen. Having a Mac is like hooking Megan Fox, but she wants to have sex in a phone booth with three condoms on, blindfolded and your hands tied behind your back. Sooooo restrictive and controlling. I never felt like I owned my Mac, more like I was borrowing it from the Apple store. I let some other chump "own" it.

I'll soon be parting with my even more controlling and restrictive iphone as well.

---

### Post by Dullstar on 2009-07-22
Well, honestly there was a time when the Macs weren't as good, though I believe that has changed now.  So far the only complaint I've seen about modern Macs is about the dock...  and it was an irrelevant complaint, because he was comparing it to the taskbar in Windows 7, but said it as if the Mac dock didn't do such and such thing, but about five minutes of using it will show that it DOES have those features.

Anyways, while I disagree with what you say about the Macs, I really agree with what you said about the iPhone.  I don't know what the software for the iPhone is like, but I've heard that you have to use AT&T.  That seems restrictive enough, in my opinion.

---

### Post by raymondh on 2009-07-22
Sorry to hear you encountered problems.  I am a mac user and will continue to be one.  I also am a linux/Ubuntu enthusiast.

In the end, go with the OS that makes you happy and productive. They are after all, merely tools. 

Peace.

---

### Post by juelze on 2009-07-22
> **LADmaticCA said:**
> I'm sorry you had problems with video. My first experience with Ubuntu was very much the same (blank screen after Nvidia driver install), but I was determined to find a solution because I really liked the layout of the Gnome desktop, and I could see the performance increase of my machine. Turns out the solution was very simple but it did take a long time to find. Since then I've fallen in love with this OS and the freedom it brings, and I'm really glad I toughed it out. Your monitor's not using DVI is it? Cause that was my problem. Anyway, I wish you luck in whatever you decide to do.

Yes, the 6600GT has two DVI ports, no VGA to test.  I'd really like Ubuntu to work, but it seems I'm not really getting the support I hoped.  Ugh.  I'm guessing I'll be going to Windows 7 or back to XP if I can't get this to work the way I hoped.  As far as preinstalled Linux...isn't that just on Dell laptops?  I'd be looking for a desktop in reality since I just bought a 19" widescreen monitor for my desktop.

---

### Post by Dullstar on 2009-07-23
Don't give up yet.  Maybe he/she just needed to know something about the DVI ports.  We're doing our best.

---

### Post by Tamlynmac on 2009-07-23
This appears to be a continuation of this thread:
[http://ubuntuforums.org/showthread.php?t=1202115]("http://ubuntuforums.org/showthread.php?t=1202115&page=4")

Perhaps, they should be combined as a reoccurring discussion.

---

### Post by Dullstar on 2009-07-23
I don't know, the poor application of the English language makes it hard to read.  I can't tell if they're saying Ubuntu is good or bad.

---

### Post by LADmaticCA on 2009-07-23
> **juelze said:**
> Yes, the 6600GT has two DVI ports, no VGA to test.  I'd really like Ubuntu to work, but it seems I'm not really getting the support I hoped.  Ugh.  I'm guessing I'll be going to Windows 7 or back to XP if I can't get this to work the way I hoped.  As far as preinstalled Linux...isn't that just on Dell laptops?  I'd be looking for a desktop in reality since I just bought a 19" widescreen monitor for my desktop.

I sent you a pm.

---

### Post by HappyFeet on 2009-07-23
> **LADmaticCA said:**
> My first experience with Ubuntu was very much the same (blank screen after Nvidia driver install), but I was determined to find a solution

It takes a dedicated person to do this. I am the same way, but I really don't expect the average user to feel this way. Some of us get it, some of us don't.

---

### Post by Dullstar on 2009-07-23
Dedication is fueled by the crashing of Windows in the world of Linux! :popcorn:

---

### Post by juelze on 2009-07-23
> **Dullstar said:**
> Don't give up yet.  Maybe he/she just needed to know something about the DVI ports.  We're doing our best.

LADmatic sent me a PM.  Apparently I need to add a line in my xconf.org file to tell the OS that I'm using DVI.  I REALLY hope this works ::crosses fingers::.

---

### Post by wandalalakers on 2009-07-23
I use EnvyNG on both my kubuntu 8.04 desktops with Nvidia cards.  I'm using a generic video card with an Nvidia 7300 chipset and have it connected via dvi to a Dell lcd.

If the xorg doesn't work try this:
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

A) How do I Install EnvyNG?

1) If you installed Envy or EnvyNG 1.1.0 (or lower), make sure you remove them by typing:
sudo apt-get remove envy
sudo apt-get remove envyng
sudo rm -R /usr/share/envy

2) EnvyNG is available in Ubuntu's "universe" repository, therefore all you have to do is enable this repository. If you don't know how to do it, see Point E.

3) Install EnvyNG: Open Terminal or Konsole and type:
sudo apt-get install envyng-qt

OR if you want to install only the textual interface just type:
sudo apt-get install envyng-core

4) Launch EnvyNG's GUI (inside a Desktop Environment such as GNOME,KDE, etc.) by selecting it in the "Applications/System Tools" menu OR if you need to use EnvyNG's textual interface you will have to type:
sudo envyng -t

---

### Post by solwic on 2009-07-23
I was going to buy a Mac at one point, but for the hardware specs I want, it'd be over $2,000...and that's just obscene.  So I'll live with the few bugs Linux has, and be happy with the extra cash in my pocket.

---

### Post by apple+ on 2009-07-23
I had no problems at all when I switched from Win.xp to xubuntu 9.04.I also had a "ubuntu fanatic" install it for me so,I don't know what's up with your comp.My is very low in specs and works fine.

---

### Post by juelze on 2009-07-23
> **pcdoctor said:**
> I use EnvyNG on both my kubuntu 8.04 desktops with Nvidia cards.  I'm using a generic video card with an Nvidia 7300 chipset and have it connected via dvi to a Dell lcd.

If the xorg doesn't work try this:
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

A) How do I Install EnvyNG?

1) If you installed Envy or EnvyNG 1.1.0 (or lower), make sure you remove them by typing:
sudo apt-get remove envy
sudo apt-get remove envyng
sudo rm -R /usr/share/envy

2) EnvyNG is available in Ubuntu's "universe" repository, therefore all you have to do is enable this repository. If you don't know how to do it, see Point E.

3) Install EnvyNG: Open Terminal or Konsole and type:
sudo apt-get install envyng-qt

OR if you want to install only the textual interface just type:
sudo apt-get install envyng-core

4) Launch EnvyNG's GUI (inside a Desktop Environment such as GNOME,KDE, etc.) by selecting it in the "Applications/System Tools" menu OR if you need to use EnvyNG's textual interface you will have to type:
sudo envyng -t


I'll try this again, but Envy worked worth squat when I tried it.  In fact, I could never get it to frakkin' launch!!!  Ugh.  I also tried adding a line of code in my xconf.org file and alas, it did not help.  I'm thinking I'm just going to put my 9800 Pro back in, clean install Jaunty and put this @*#&@#($& Nvidia card back on ebay and kiss it goodbye.  Nvidia, despite what people say, has crap for supporting Linux because this card is nothing but a frakkin' nightmare!

---

### Post by juelze on 2009-07-23
Holy @)*(&#$.  Looks like EnvyNG is running.  Must be because I'm running 8.04 because it did not work in Jaunty.  Oh well, I hope this works!

---

### Post by juelze on 2009-07-23
Well, EnvyNG gave me a black screen as well.  Enough messing around.  The 6600 GT is going back onto eBay and I have my 9800 pro back in my PC.  At least that worked out of the box.  So much for crap ATI drivers, right?  :confused:

---

### Post by juelze on 2009-07-23
Ugh.  Still not having good luck even after putting my 9800 Pro back into my PC.  Tomorrow, I'm going back to XP.  I'll miss Linux, but until it gets better at supporting more hardware, it's more of a PITA then XP.  Thanks for all those who have helped.  Maybe I'll see you around for Karmic.

---

### Post by Dullstar on 2009-07-24
We'll welcome you back with open arms.
At least, I will.

Don't know about the rest of the community, but I think they'll be ready to welcome you back.


If you get a Mac, I'll be seeing you eventually too!  Heh heh, I've wanted to replace my computer for a while, it's just isn't very good.  I had no choice but to go to Linux.  And I've liked it enough that when I do get a Mac, I'm going to, once again, set up a dual boot.

By the way, I'm just wondering...  this won't sway my opinions, but I wonder, is it unusual for Mac users to set up a dual boot to Linux as opposed to Windows?

---

### Post by kg4cna on 2009-07-24
Sorry you had problems with your Nvidia card. Did you check to see if it was supported before buying it?

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

I'm not sure exactly which one you have...but it appear to work fine with versions 6.60 through 8.04.

If the ATI card is working...just hang with it for awhile. I have an older
model Nvidia card and it's worked in every distro I've tried.

Don't give up...but I understand you need a machine that works for you. You know best :)

All the best to you,
Allen

---

### Post by wandalalakers on 2009-07-24
Julze,
I'm going to send you a PM.

6600GT info
[http://www.ubuntuhcl.org/browse/product+nvidia-geforce-6600gt?id=249](http://www.ubuntuhcl.org/browse/product+nvidia-geforce-6600gt?id=249)

---

### Post by juelze on 2009-07-24
Well, I didn't know about that hardware site until now.  However, it shows that my card SHOULD work with 8.04 which I did try and it did not work (Black screen) again.  Same thing when I used EnvyNG.  I think I'm going to try LinuxMint tonight and see how it behaves.  It's an on and off love affair with Linux.  Part of me REALLY doesn't want to go back to Windows, but part of me just wants his PC to work without anymore monkeying around.  Are any other distros a bit better in terms of Linux?

---

### Post by HappyFeet on 2009-07-24
"Better" is a relative term, as *I* think ubuntu is the best out there. Remember that not every OS will work perfectly on every computer, and that includes windows. But other good distros include Mandriva One, Fedora, Opensuse. I think [Mandriva One]("http://www.mandriva.com/en/download/free") has the Nvidia drivers (and flash) installed by default, and may be the easiest to get going. PM me if you have any questions. If you like gnome, just make sure you download the right one.

---

### Post by L815 on 2009-07-24
> **Chemical Imbalance said:**
> Welcome to the joys & frustrations of linux!

You can try distro-hopping: [http://distrowatch.com/](http://distrowatch.com/)

Or go back to Intrepid or Hardy until Karmic.

Or dig in and find the solution to your problem.

Everything has its advantages and disadvantages. 

Ask yourself, "Is Linux worth it"?  Maybe make a mental list of the pros and cons for windows and linux and see what wins.

Good luck.


I'd say avoid distro hopping. It becomes addictive :(

---

### Post by juelze on 2009-07-24
> **Dullstar said:**
> We'll welcome you back with open arms.
At least, I will.

Don't know about the rest of the community, but I think they'll be ready to welcome you back.


If you get a Mac, I'll be seeing you eventually too!  Heh heh, I've wanted to replace my computer for a while, it's just isn't very good.  I had no choice but to go to Linux.  And I've liked it enough that when I do get a Mac, I'm going to, once again, set up a dual boot.

By the way, I'm just wondering...  this won't sway my opinions, but I wonder, is it unusual for Mac users to set up a dual boot to Linux as opposed to Windows?

Thanks man.  I'm actually taking a break from my PC tonight to watch Watchmen.  I'm going to try Mint and see what else I can do to figure it out.  Guess I'm just angry that I was hoping that I could finally get rid of Windows, but instead it seems like in order for things to work the way I want them, I have no choice but to use Windows.  Oh well, I got Mint ready to try so maybe this weekened I'll get around to it.

---

### Post by juelze on 2009-07-24
> **L815 said:**
> I'd say avoid distro hopping. It becomes addictive :(

Haha, I could understand that.  My have to give Mandriva  a try if Mint doesn't work and maybe OpenSUSE.

---

### Post by cooper77z on 2009-07-24
juelze wrote, " Sorry for my rant, but I REALLY want to continue to use Ubuntu but it can be so frustrating at times."

I encountered the same problems, my solution was to install server 8.04.2, partially because I want to learn how to serve web pages, and partially because I knew it would be rock solid.

The OS is rock solid, and I am still developing my server. It's supported untill 2013. I think Jaunty is great, but Jaunty is nowhere near as stable as hardy server, in my noob opinion. Still, Jaunty needs to be used and improved. You can improve Jaunty by using it and reporting problems, like you are doing.

---

### Post by Dullstar on 2009-07-25
juelze, this *might* not be until a couple of years, depending on when I find the computer to do it on, but I will do a test of 4 *buntu systems.

These will be Ubuntu and Kubuntu, 8.04 and 9.04 in both cases.

Let me know if you want me to give you the results once I get around to it.  Be aware, it could be a while!  I won't actually come to need the CD's for too much until I get a Mac.  Sure, Mac OS X is great, and I can see myself using it as a main OS more than Windows or Ubuntu, but I know I'll miss Ubuntu, so that is my solution!

---

### Post by cooper77z on 2009-07-25
huh, why would you abandon ubuntu, you can do anything with it. ???

sure macs are great, final cut pro is great, but it's not anything better, just more user friendly...

it makes no sense to give up on ubuntu, it's like giving up on yourself.

I am looking forward to the cool stuff I can create in linux, with programs, paradigms and stuff. :)

---

### Post by Dullstar on 2009-07-26
[COLOR="Red"]cooper77z wrote, "huh, why would you abandon ubuntu, you can do anything with it. ???"

"it makes no sense to give up on ubuntu, it's like giving up on yourself."[/COLOR]

Actually, no.  Two words:  Dual boot.

---

### Post by juelze on 2009-07-27
Well, I'm sticking with Linux for the time being.  Got rid of Ubuntu and installed Linux Mint, and let me tell you, I love it.  Just the overall looks is 5 times better then Ubuntu and everything seemed to work great out of the box.  I'm not running with my Nvidia card now, but I don't need to, my 9800 pro works great in Mint.  I love it!!!  Ubuntu gets a 7 out of 10 and Linux Mint a 9 out of 10!

---

### Post by HappyFeet on 2009-07-28
It's great to see you have found something you like, and that it is still in the ubuntu family. Have fun.

Btw, if you don't game or need dual monitors, there is no real need for the nvidia drivers. I myself have only been using the nvidia drivers since ubuntu 8.10

---

### Post by wandalalakers on 2009-07-28
> **juelze said:**
> Well, I'm sticking with Linux for the time being.  Got rid of Ubuntu and installed Linux Mint, and let me tell you, I love it.  Just the overall looks is 5 times better then Ubuntu and everything seemed to work great out of the box.  I'm not running with my Nvidia card now, but I don't need to, my 9800 pro works great in Mint.  I love it!!!  Ubuntu gets a 7 out of 10 and Linux Mint a 9 out of 10!

Ahem.  ;)
Glad it's working for you but I'm dying to know if your Nvidia card would work.
Here is some more stuff for you.
[http://linuxmint-art.org/](http://linuxmint-art.org/)

---

### Post by rannable on 2009-07-28
Ok, ill give you $5 not to go to Windows :D

---

### Post by ngsupb on 2009-07-28
it seems to me he is depreseed an need to talk to someone.

p.S. stay away from distro-hopping. I thought I found Ubuntu. It is awesome. but I tried Arch yesterday...I am going to take a look what is Mint about later...

---

### Post by wandalalakers on 2009-07-28
Juelze,
I wasn't sure if you backed up your system as an ISO.  I use Remastersys to backup my ubuntu system to dvd.  I highly recommend Remastersys.
You create a backup of your ubuntu system as is or you can give your family and friends a copy of your ubuntu system without your home directory.
Every time there is a 8.04.x release I create a new backup ISO.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

[http://klikit.pbworks.com/Remastersys](http://klikit.pbworks.com/Remastersys)

Where can I get remastersys?
The Remastersys repository needs to be added to your /etc/apt/sources.list
Paste the following into the sources.list:

For Gutsy and Earlier - up to version 2.0.11-1
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/

For Hardy and Newer - version 2.0.12-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/

Then simply either reload in Synaptic, Adept or you can "sudo apt-get update" and install remastersys.

---

