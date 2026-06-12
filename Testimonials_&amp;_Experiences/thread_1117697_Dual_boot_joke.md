---
title: "Dual boot joke"
date: 2009-04-06
forum: Testimonials &amp; Experiences
---

### Post by alz5280 on 2009-04-06
After following directions and installing Ubuntu 8.10 I lost access to my windows XP. After all the genius community support I have to say Its not worth the trouble. Your Ubuntu by design is so windows unfriendly I will not recommend a dual boot to anyone and even running the disc to try it out can mess up windows. I need windows work programs and didn't appreciate the work installing everything from scratch. In any given endeavor you would think that measures would be taken to assure that the system would truly work with the existing norm. My advice; Develop a disk that really allows booting both systems with no BS and don't promote Ubuntu anywhere near windows until you do. How many people weren't able to re-install everything like I did?

---

### Post by Spunkbubble on 2009-04-06
EDIT: I should really read people's posts more carefully. Sorry!

---

### Post by alz5280 on 2009-04-06
> **Spunkbubble said:**
> If you're not prepared to put up with, or even, *gasp*, *enjoy* a little bit of trial and error, then don't bother with linux at all. This isn't a commerical OS, no one is profiting, no one is being paid to sit here and be your personal guide. No one is being paid to make an installer which does even the most painstakingly simple things at the click of a button, which it already does mostly. And most importantly, no one is being paid to listen to your flaming.

People will help if you have a real problem and you post about it accuractely and politely. You have to appreciate that they are donating their own time to help you, even though they don't have to... so show a bit of gratitude, or at the very least, don't act like an arsehole.

I see it went over your head

---

### Post by Spunkbubble on 2009-04-06
EDIT: I should really read people's posts more carefully. Sorry!

---

### Post by estyles on 2009-04-06
I don't get the joke referenced in the subject line?  What's the punchline?

Is it that installing Ubuntu in a dual-boot configuration on a Windows PC is really easy, whereas installing Windows onto an Ubuntu PC will overwrite the master boot record, rendering Ubuntu inoperable?  People actually pay money for an OS that will totally bork your system after you install it?  Forget that!

My advice to MS: Develop a disk that really allows booting both systems with no BS and don't promote Windows anywhere near Ubuntu until you do. How many people weren't able to re-install everything like I did?

---

### Post by mickey57 on 2009-04-06
alz5280,
....Maybe read up on where [COLOR="Red"]you[/COLOR] f'ed up:guitar:
.....Get ya some grub too:lolflag:

---

### Post by Kareeser on 2009-04-06
alz5280... Windows is far more unfriendly to Ubuntu than Ubuntu is to Windows. Like others have said, it doesn't play fair with any other operating system.

Note that with Macs, Apple had to design its own utility to make Windows play nice, just like GRUB is there to make Windows play nice.

---

### Post by Sef on 2009-04-06
Moved to Testimonials and Experiences.

---

### Post by Pasdar on 2009-04-06
MS is too big and powerful to even need to care about anyone wanting to keep their option of logging into another OS.

---

### Post by Dan_Dranath999 on 2009-04-06
> **alz5280 said:**
> After following directions and installing Ubuntu 8.10 I lost access to my windows XP. After all the genius community support I have to say Its not worth the trouble.

Have you asked for help? You have only 2 posts in this forums (in 2 days!), and neither one of them has provided enough info for the rest of us to be of some assistance.

---

### Post by Methuselah on 2009-04-06
His post doesn't make any sense to me.
I don't even know what his problem was.

---

### Post by musky on 2009-04-06
Awhile ago, tried out [[COLOR="Blue"]*wubi*[/COLOR]]("http://wubi-installer.org/faq.php") & worked really good. At the time, hadn't sorted out a solid wifi connection sooo..  only spent a ltd amount of time with ubuntu.

Read recently that rt73 is plug & play so gave wubi another shot & works great with my e-machines w3609 vista box.

Haven't found anything better or easier out there than wubi to try out linux from win.

I'd say dual booting (or any number of things..) win with any distro can be problematic & requires some understanding before going there. Often, a boot prob with win after a dual boot setup can be corrected.

No such thing as no risk & I think I speak for many when I say, no pain, no gain. Lost count of how many disasters have come my way.. just trying to run win & get up to speed with linux.

Once starting with linux, yes there is a learning curve but you will not regret it.

---

### Post by wolfen69 on 2009-04-06
i've set up at least 12 dual boots no problem. i guess i'm one of those genius's you refer to. have a nice day.

---

### Post by jbysmith on 2009-04-06
You mean your previous post?

*Help after loading Ubuntu disk and trying it out and removing it now when trying to boot windows I get disk read error. After trying to boot from windows xp install disk computer starts inspecting setup then goes blank. Wont even allow a repair boot. what will fix my windows boot up? DESPERATE*

If you're just trying the LiveCD, it makes **zero** changes to your hard drives, unless you run the installer or do something silly to your Windows partition, say deleting NTLDR or the like via Nautilus.

The XP installation disc, even the original RTM pre-service-pack builds will see a Linux partition, it'll just flag it as an unknown OS.  It won't just go blank and lock up.  Assuming nothing is wrong with the hardware itself, it sounds like you might have damaged your partitions.. hitting the reset button while the partition editor is busy for example is a great way to bork your system in a hurry.

And as Wolfen69 points out, *many* people do this all the time with zero problems, but they took the time to understand the procedure before jumping in blindly.

Either way, unless you're using Wubi or just toying around with the LiveCD, making major changes your boot loader or partitions without backups is just a bad bad bad idea unless you're willing to possibly lose data.  It *usually* doesn't happen but it can; I've had one of those "half second power failures" on a system without a battery while it was doing a partition re-size.. big splattage.  If you go through a major system update like installing a second operating system without understanding the procedure or possible ramifications, you're risking a complete data wipeout.  You can get the exact same corruption by setting up an XP and Vista dual boot; no Linux required for data borkage.

You might want to look into some sort of data recovery disk to see what's up with your partitions.. probably has a nice error somewhere.  Once you fix that, you should be able to get the XP installer going, get into a recovery console and run FixMBR to restore the original XP boot loader, assuming you didn't reformat already.

They also really need to add another sub-forum for the  "I didn't read the instructions so Ubuntu sucks" threads.

---

### Post by wolfen69 on 2009-04-06
well said, jbysmith. people need to do a little research and preparation before taking a chance with a much needed work partition. i NEVER assume anything will work out perfectly. "plan for the worst, hope for the best". 

if one was really smart (like me)  ;)  they would make an image of their computer hard drive before trying something new. but that makes too much sense for some people.

and really, why is it that if i go to install xp after i have ubuntu, i can not get into ubuntu? until the day comes when windows will get this dual booting thing right, i will not recommend windows to anyone. (btw, i don't use windows. end sarcasm)

---

### Post by stchman on 2009-04-06
WOW, another troll that made an account to whine and moan.

---

### Post by iaswni on 2009-04-06
> **alz5280 said:**
> After following directions and installing Ubuntu 8.10 I lost access to my windows XP. After all the genius community support I have to say Its not worth the trouble. Your Ubuntu by design is so windows unfriendly I will not recommend a dual boot to anyone and even running the disc to try it out can mess up windows. I need windows work programs and didn't appreciate the work installing everything from scratch. In any given endeavor you would think that measures would be taken to assure that the system would truly work with the existing norm. My advice; Develop a disk that really allows booting both systems with no BS and don't promote Ubuntu anywhere near windows until you do. How many people weren't able to re-install everything like I did?

HE IS PROBABLY BILL GATES SABOTAGING OUR FREEDOM! LET THE DOGS AFTER HIM!
:lolflag:
....what a smuck..

---

### Post by Tamlynmac on 2009-04-06
I so agree, when it comes to dual booting - Windows is a joke.

That's why we don't dual boot, but rather elected to run Ubuntu only. It's amazing how quickly one can forget about Windows and learn to use the new OS. Guess it may be a matter of necessity, as some may require specific Windows programs that won't run in Ubuntu for work or business. But with just a little creativity, we've overcome that and are 100% Ubuntu here at home.

Guess one might say, to each their own. What works for some, may not work for others. Isn't freedom of choice a wonderful thing? Without FOSS there would be substantially fewer choices.  :-k

---

### Post by jbysmith on 2009-04-06
> **iaswni said:**
> HE IS PROBABLY BILL GATES SABOTAGING OUR FREEDOM! LET THE DOGS AFTER HIM!

Lol I wouldn't put it past Steve Ballmer to do something like that to help his anti-Linux crusade.  Hire a bunch of stooges to flood various Linux forums and spread how bad Linux is, and why I should have stuck with Windows and all that other good FUD nonsense.  

It's almost as if he brought Tomás de Torquemada back from the dead and hired a gaggle of PR people to help him, but instead of burning you at the stake they burn you at the checkout line when you buy their stuff, and then they burn you again with the "upgrades".  

Confessor Ballmer - "Confess!"

Me - "NO! I want to know why Windows 6.1 is being called Windows 7 with a big price tag!"

Confessor Ballmer - "Renounce choice!"  (Hits me on the head with a Vista Ultimate box repeatedly)

Me - "No!"

Confessor Ballmer - "Henchmen.. bring me.. the spyware."

Me - "Nooooooo" (mumbles incoherently)

*Yes, I have too much time on my hands on my days off.*

---

### Post by jdunn on 2009-04-06
I have installed Ubuntu as dual boot with XP and Vista a number of times.  It even nicely resizes the MS Windows partition to the size I specify (Vista has its own built-in partion resizing tool but it sucks).  I never had any problems.  There are friendly tutorials out there with screenshots that walk you through dual boot installations.  Did you use one of these?  Was your MS Windows install up-to-date before you attempted the dual boot install?

---

### Post by polkadotteapot on 2009-04-06
Sod the cd unless you need to try it first. If using windows use the Wubi program, or unetbootin if you're installing a different distro to ubuntu.
If there's anything you don't understand look it up in your favourite search engine first.

I dual boot with xp no problem, had a few issues with ubuntu initially, I'm no expert, but asked and got very good help on here to sort those out. It can be a little frustrating but it's worth it.

Someone was sneering - not everyone is aware you have to back up your whole os, files yes, but when using a cd or installer wizard for something like this you do kind of expect it not to **** up as any issues should be sorted out by the lovely community.

---

### Post by zero244 on 2009-04-06
Every computer is setup differently. You do need to do a little for thought to install Ubuntu along side Windows.
I like to keep the Windows partition first of second and Ubuntu towards the end of the hard drive.
Windows and Windows software seems to handle better if Windows is installed on drive C or D.
When you install Ubuntu is best to use the Manual partition process.
Ive installed several versions of Linux including Ubuntu and its never bothered my Windows partitions.
Windows on the other hand destroys any reference to any OS but Windows.

You might check around there is a grub restore ISO that can fix boot problems.
Ive used it to repair boot problems with other Linux distro's who sometimes don't play well with Ubuntu.
I'm typing this using a version of Puppy Linux which is a pretty good OS
I'm running Xfce and compiz.
Good luck

---

### Post by longtom on 2009-04-07
Hmmm...look at my post count.....and I am an absolute beginner who wanted to make this work.

I had my trials and tribulations and will probably have some more to come.  But if you want to make it work you can - without being a super wizzard (which I am not by any account - ask anybody arround here who had to help me....;))

But one of the things with which I never, ever had a problem whatsoever, was installing Ubuntu for a dualboot with a Windows installation present.
Got myself a 3 page guide somewhere on the i-net (consisting mostly of screenshots) and was good to go every time I did it.

Now I am having CrunchBang and Fedora as well to check it out - in a quadrouble boot....and I am still a beginner - with a bit more confidence than a month or 2 ago.

Conclusion:

If you want to make it work, you will.  If you have a post count <10 and starting ranting here, you never tried...

Enjoy your trip!

---

### Post by caravel on 2009-04-07
> **alz5280 said:**
> After following directions and installing Ubuntu 8.10 I lost access to my windows XP.
I'm sorry to hear that, but it's very likely that you've made a mistake such as instructing the installer to use the entire disk.  I've been installing Linux distributions on and off in dual boot since about 2003 and I've managed to mess up a lot, and still do, but never have I wiped out Windows in the process.  I'm a casual user, not a pro by anyone's standard, yet I can manage to install it without doing any serious damage.

> **alz5280 said:**
> After all the genius community support I have to say Its not worth the trouble.
You didn't ask for support and what you mean is that it's not worth *your* trouble.

> **alz5280 said:**
> Your Ubuntu by design is so windows unfriendly I will not recommend a dual boot to anyone and even running the disc to try it out can mess up windows.
It's an OS it does not have to be "windows friendly".  Windows by design is unfriendly to all non windows OSes.  It's also false that running the livecd can "mess up windows".

> **alz5280 said:**
> I need windows work programs and didn't appreciate the work installing everything from scratch.
If your PC is important for work, and if you need windows programs.  Then what were you thinking of installing another OS on it?

> **alz5280 said:**
> In any given endeavor you would think that measures would be taken to assure that the system would truly work with the existing norm.
Never assume.

> **alz5280 said:**
> My advice; Develop a disk that really allows booting both systems with no BS and don't promote Ubuntu anywhere near windows until you do. How many people weren't able to re-install everything like I did?
My advice: Get your facts straight and read up before you try installing any Linux distribution again.

---

### Post by lisati on 2009-04-07
Ay ay ay! (repeat ad nauseum)

> **wolfen69 said:**
> i've set up at least 12 dual boots no problem. i guess i'm one of those genius's you refer to. have a nice day.
All three of my current crop of three machines with Ubuntu on them on are dual-boot. It's kinda flattering to be thought of as a genius. Please excuse me for a moment while I take steps to make sure my head doesn't explode with self-importance - it could get messy




(A few moments later)


> **jdunn said:**
> I have installed Ubuntu as dual boot with XP and Vista a number of times.  It even nicely resizes the MS Windows partition to the size I specify (Vista has its own built-in partion resizing tool but it sucks).  I never had any problems.  There are friendly tutorials out there with screenshots that walk you through dual boot installations.  Did you use one of these?  Was your MS Windows install up-to-date before you attempted the dual boot install?

Again, I agree it can be done! And my most recent dual boot with Vista went smoother using Ubuntu's partition manager than through trying to use Vista's contribution.

---

### Post by Bearly Able on 2009-04-07
> **alz5280 said:**
> After following directions and installing Ubuntu 8.10 I lost access to my windows XP.

So did I, and after posting in the [forums]("http://ubuntuforums.org/showthread.php?t=1060203"), I got expert assistance to sort out my problem.  For some reason, GRUB wouldn't boot Windows, so I had to edit my Windows boot loader to start GRUB.  Simple when you know how - and how grateful I am to the folk who do know how and are willing to help.

---

### Post by Tamlynmac on 2009-04-07
> caravel
 	Quote:
 	 	 		 			 				 					Originally Posted by **alz5280** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7022992#post7022992") 				
 				*In any given endeavor you would think that measures would be taken to assure that the system would truly work with the existing norm.*
 			 		 	 	 
Never assume.

Perhaps the wisest advice I've ever read on this forum. :-k

Assumption is the route followed by many a fool. When assuming anything we place ourselves in a position of compromise, between that which we believe and that which is.

Good call carvel. My only suggestion is in the future you capitalize and bold the words. ;)

---

### Post by MartyBuntu on 2009-04-07
> **alz5280 said:**
> After following directions and installing Ubuntu 8.10 I lost access to my windows XP.


From my point of view, I would consider that a smashing success.
Job well done!

---

### Post by charles woodward on 2009-04-09
I've had dual boot with vista for 12 months now (previous machine was Ubuntu only).  Only problem I've found is what to use vista for.  In fact as I haven't used it I'm about to delete it.  

By the way I will still keep a dual boot - one for the official ubuntu release - one for the development version so I can test things out.

---

### Post by digital_sc4rz on 2009-04-09
I had ubuntu setup dualbooting with vista x64 using grub -- Never had no issues when i was setting this up - Now i've decided to just have ubuntu installed on my machines since i want to get away from m$ and when i wanna just play around with windows in vmware :)

---

### Post by mousestalker on 2009-04-09
This boot is walking down the street when he spots a bar. Feeling thisty and hungry he enters and is surprised to finding another boot working the bar. The first boot steps up to the bar and asks the other boot: "Do you serve sole food?" to which the bartender boot replies














"Only if you are well heeled".
:P

That should satisfy the complaint about not having a punch line in the thread.

---

### Post by digital_sc4rz on 2009-04-09
Lmao !!! =d>
> **mousestalker said:**
> this boot is walking down the street when he spots a bar. Feeling thisty and hungry he enters and is surprised to finding another boot working the bar. The first boot steps up to the bar and asks the other boot: "do you serve sole food?" to which the bartender boot replies














"only if you are well heeled".
:p

that should satisfy the complaint about not having a punch line in the thread.

---

### Post by calrogman on 2009-04-11
I'll just go right ahead and quote my /boot/grub/menu.lst file.

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1


Note that this line, as well as another line to boot the Vista recovery partition on my laptop, were added automagically on install, the only change I made to the menu.lst file was changing the menu entry for Vista to say "Windows Vista" instead of some stuff involving longhorn.

---

