---
title: "Smooth upgrade from Edgy"
date: 2007-02-15
forum: The Cafe
---

### Post by boulderjams on 2007-02-15
Even though, I use my laptop as a primary computer & for my web developement work, I thought I could lend a hand in testing out Feisty Fawn. So I implemented the command 'update-manager -c -d'. I am running a Dell Inspiron 6000, 1.73mhz Pentium M, 512MB Ram notebook. The upgrade was smooth. I use a quick comcast cable connection and the download took about an hour and a half. The actual installation and upgrades took about an hour. No problems, all settings saved and a very happy ubuntu user. The only error that I even ran into was upgrading vmware-player and modules. (I don't use vmware often enough to care). Cannot wait for the final release. 

ps. Oh yeah, I must say, I like the idea of the control center, but it seems more time consuming to get to what I need. That extra step, I guess.

---

### Post by VanHammersly on 2007-02-15
Wow.  Sharp looking desktop.  I was considering the upgrade too.  I am pretty happy with edgy, but always get curious about the latest and greatest every six months.  Have you noticed any substantial changes between edgy and feisty?

---

### Post by FuturePilot on 2007-02-15
What theme is that? Looks nice.

---

### Post by calvmari on 2007-02-15
That screenshot convinced me to upgrade :)

---

### Post by beercz on 2007-02-15
Thanks for this boulderjams.  I am thinking about upgrading to fiesty very soon.

How long did it take?
Did it go smoothly?
Were there any serious problems to overcome?
Does it work well?

Just curious.

---

### Post by muguwmp67 on 2007-02-15
Can anyone tell me what dock feisty is using?  If thats the default, it sure looks a lot more polished than using gnome panels.

---

### Post by Yoooder on 2007-02-15
Edgy is my first taste of Ubuntu, could you either tell me how to upgrade or point me in the direction of a tutorial?

Thanks much!

*** I found the answer to this, if anyone else is wondering, the update-manager shows a button at the top that says "a new version is available" and offers you to upgrade to 7.04 (which is Feisty)

---

### Post by Old Pink on 2007-02-15
Guys, remember feisty is still in development, and will not be stable until April 07. 

Until then, use it on testing machines only!!

---

### Post by qpieus on 2007-02-15
sharp looking desktop. I've skipped edgy, but I may just have to try out feisty.

---

### Post by Bragador on 2007-02-15
> **qpieus said:**
> sharp looking desktop. I've skipped edgy, but I may just have to try out feisty.

I too wanted to skip edgy but I installed it a couple of days ago. It's a nice little upgrade. Don't stay on 6.06. You deserve better! Unless you want to punish yourself and make yourself suffer...

Is this what it takes to make you happy!?! Is this !?!

Now go upgrade!

---

### Post by Nikron on 2007-02-15
Well this post made me update to Fiesty since it gave me the command to.  It went smoothly.  However, I had to downgrade the version of my Nvidia driver, and my mouse configuration using evdev no longer worked.  Fiesty looks good, the control panel is decent but...  To much like copying off of Windows.  I kinda wish they had been a little more creative...  Oh well, it's cool though, thanks for the inspiration

---

### Post by Artemis3 on 2007-02-15
I suppose the gdesklets starter bar is not default, is it?

---

### Post by boulderjams on 2007-02-16
To answer all those questions....

First off, Feisty is still in development. It will be released fairly soon.

VanHammersly:  I havn't noticed to much difference just yet. I know the dev is in a freeze right now. But, I have noticed that it boots about 3-5 seconds quicker for me.

FuturePilot:  I am using beryl+rounded-tish theme+the aqua gtk theme & a modified top-panel background. that's it.

beercz:  Let's say it took about 3 1/2 hours, give a take a few. The upgrade was smooth. There where no serious problems to overcome. The only snag I ran into was everytime I try to add/remove or update with apt, it would try to remove vmware-kernel-modules and halt with an error. All I did was remove vmware-player and sudo rm /var/lib/dpkg/info/vmware-kernel-modules*. Other than that it runs smooth as can be. (Just a reminder, it is still in development, I do expect bugs at some point. Don't upgrade unless you are wanting to deal with bugs).

muguwmp67:  That dock is gdesklets-starterbar. I added the icons myself. Standard is gnome-panels.

Yoooder:  The command is sudo update-manager -c -d. 

Old Pink:  I couldn't agree more. Testing. And as I stated in my post, I am willing to test "Feisty Fawn" and report the bugs.

---

### Post by Sunflower1970 on 2007-02-16
I know it's all in testing mode, but this thread made me curious, so I d/l'd Ubuntu and Kubutu...although too chicken to actually install them on any of my computers, I've been just playing around with the CD's. The live CD's seem to boot up faster than 6.10 (both of them). Some things freeze on me in Ubuntu, such as opening up any of the networking tools, or OO.o...but that could be from only having 256 MB RAM in it....(or maybe the CD is bad...?)

This time around, I think I like the look of Kubuntu better than Ubuntu....I might just get brave enough to install Kubuntu and see what happens.

---

### Post by jocheem67 on 2007-02-17
I installed the herd 3 alpha  on my workin' machine in triple-boot with eddgy and xp.
Grub has the tendency to install itself on the wrong disk, which is manually configurable, but I using the edgy one , just a lazy workaround. There is a bug in mounting/fstabbing :)  my disks...they are just in my /media directory and nowhere on my desktop. Can use them though through /media...
The old ati/fglrx problem is there, so I stuck with mesa...

It's all a bit annoying, but the system is so much more responsive compared to edgy, that I use feisty all the time. Software is no problem, all my apps are there, restricted stuff works nicely. Hardware is no prob.

I say , go for a edgy/feisty dual-boot, and just be a bit of a tester and enjoy the reponsiveness!

---

### Post by Polygon on 2007-02-17
hopefully the upgrade here will go a lot better then the one from dapper -> edgy. I did not appreciate 1 kb/s download speeds (not really anyones fault) and getting errors and x not starting when i booted up into my new edgy system =/

---

### Post by CheeseEatingBulldog on 2007-02-17
I started with ubuntu on the testing release of Breezy and also upgraded to Dapper before time and never had a problem, but am hesitant to do it with Feisty as I really don't feel like fixing my X and beryl stuff that might break.

Although....nice new shiny release....tempting.

---

### Post by boulderjams on 2007-02-17
> **CheeseEatingBulldog said:**
> I started with ubuntu on the testing release of Breezy and also upgraded to Dapper before time and never had a problem, but am hesitant to do it with Feisty as I really don't feel like fixing my X and beryl stuff that might break.

Although....nice new shiny release....tempting.
CheeseEatingBulldog:  Actually, I have Beryl & a modified X.conf and after the upgrade it worked out of the box. No problems at all. It was nice.

---

### Post by xfile087 on 2007-02-18
> **boulderjams said:**
> CheeseEatingBulldog:  Actually, I have Beryl & a modified X.conf and after the upgrade it worked out of the box. No problems at all. It was nice.

Same goes for my upgrade - works great so far.

Except i've just noticed Beryl's setting manager won't work. :|

---

### Post by boulderjams on 2007-02-18
I don't use the beryl's setting manager (the systray icon?). I just have gnome-sessions load 'beryl --replace' & 'emerald --replace' which loads fairly quick.

---

### Post by HellRat on 2007-02-21
I downloaded the Feisty herd4 CD. Can I upgrade from edgy with it or do I have to dl everything with apt-get. If its possible to upgrade from the disc, how do I do that? It doesnt seem to happen anything when I try any of the icons on the disc. LiveCD works fine though.

---

### Post by bigjack on 2007-03-29
Ubuntu 6.10 Edgy Eft installed and worked perfectly on IBM Thinkpad T40--found the wireless card and connected to my home wireless network with no problem.

But in trying to upgrade to Feisty Fawn 7.04 Beta (used "update-manager -d" in terminal) it went smoothly until the stage for checking for outdated software--total freeze. I had to turn off the computer, then reboot. All looked OK but could not get the wireless to see our home network--said the signal was 0%.

Decided to install Feisty Fawn 7.04 Beta from CD. When it got to the stage for setting up the network, it could not see our network. Note that Edgy 6.10 Edgy Eft sees network and sets up wireless with no problem.

I just reinstalled Edgy Eft 6.1 and will keep using it until the problem with Feisty Fawn and wireless is corrected.

---

### Post by rockin_goliath on 2007-03-29
That looks like the dock used in gDesklets, which can be found in Automatix.

---

