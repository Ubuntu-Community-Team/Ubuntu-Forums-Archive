---
title: "Why Ubuntu currently can not compete with OSX/Windows"
date: 2009-03-22
forum: Testimonials &amp; Experiences
---

### Post by stormfrog on 2009-03-22
Linux is a superior OS, thats more of a fact than an opinion. Its diversity, open ended interface and simplicity is just simply stunning. Ubuntu tries its best as a flavour to become user friendly and while I think Ubuntu is the linux flavour that has taken this most serious it still has a very, very long way to go.

All linux systems aer great as server OS:es. As a Desktop/Office user OS:es they are not at all impressive, neither is Ubuntu.

Out of the box Ubuntu works fine. All "normal" and intended uses of Ubuntu is great. But thats not really what is important, what is important is how Ubuntu performs when something goes awry, when a system is subject of failing harware, when a system has bad memory modules causing corrupt data to be written to the disk, when system wakes from hibernation and some vital system services are down... these are just a very few examples of common errors that can occur on any system.

How does Ubuntu handle errors like this and how is the user informed of system errors/solutions? I am not impressed by this part of Ubuntu and I think this is an area that need serious work. While you can solve much of these errors to begin with by user testing before release the Ubuntu community simply does not have the same resources to do this as OSX/Windows OS. There is an abundance of different hardware systems with an odd collection of jumbled hardware. There is so much that testing Ubuntu with all these different setups is just to much work.

What else can be done... well, I am in no way a developer of such things. But I think an interesting option would to investigate if it is possible to create a system manager that is built into the core of Ubuntu. A system manager that track the condition of the systems hardware/data that can give the user a through and easy to grasp report of what has gone awry with a system if something breaks down - and also present the user with a list of what actions must be made to correct this error.

Something user friendly that could work as an alternative to current console command based repair / rescue operations.

An example of something that is occuring on my system that constantly is driving me nuts is that after every sleep/hibernation some system services are broken. It usually is the network being down. The solution is really simple. All I need to do is fire up a console prompt and restart network services by typing /etc/init.d/networking restart. Voila! But as simple as it might seem to me that is NOT user friendly. Imagine a windows user faced with a problem that can only be solved by using the windows command prompt... even if that is a possible solution most windows users would not be able to do that. Neither would a common OSX user. And they would then call up tech support/friend/relative to solve the problem. Still, an impressive number of errors on both the Win/OSX platform can be solved by the user.

Restarting the network services on XP is done by simply right clicking network taskbar icon and press repair - this usually solves any temporary networks hiccups. Such a function is completely absent in Ubuntu. Its just one example. In my experience there are many more.

A OS must not only be built to function well, it must also be built to be able to fail and break down - and do so in a way that the user easily can identify and possibly repair the damage.

My two cents :)

---

### Post by jbysmith on 2009-03-22
Well, I do agree that for the people who are still learning, Gnome could use a better control panel style system.  KDE has an edge there, especially some distros which took it a bit further, say openSUSE's YaST or Mandriva's DrakConf.

Just keep in mind though that different does not mean better/worse.  Just different ways of doing things.  In Linux, the window manager you're using is just a "wrapper" around the Linux/GNU stuff.  In Windows, it's completely backwards, there's a few console apps to manage the system stuff, but it's more of an afterthought than anything else.

In your example, restarting the network.  You can manage the same thing in a Windows console via netsh; they just have a shortcut so people don't need to know it.  Services are the same way.. "net restart ______" vs "/etc/init.d/_____ restart".. same but different.  Windows just has a cute little wrapper for it.  (Does Gnome's Network Manager applet let you down/restart an interface?  I don't use it myself.)

That aside, you still have a services manager.  Still got an event viewer, which is actually a **lot** more useful than what Windows gives you. There's various front-ends for other system management tasks too.  Everything about the system can be controlled via the terminal.. there just isn't always a GUI frontend available yet for everything.  Windows is kinda backwards here, not everything is available at a console level, which can really limit extending/automating things, one of the *many* reasons why I think Windows will never be able to compete with Linux.  

Plus, to be honest Linux in general is a lot easier to deal with when things go wrong.  Between fixing an unbootable Windows and an unbootable Linux system, I'll take the Linux system every time thank you.  More often than not the Linux system can be fixed pretty quickly.  Windows on the other hand is a crapshoot; if the registry gets destroyed for example, well I hope you got that install CD handy.

---

### Post by cardinals_fan on 2009-03-22
> **jbysmith said:**
> 
Just keep in mind though that different does not mean better/worse.  Just different ways of doing things.  In Linux, the window manager you're using is just a "wrapper" around the Linux/GNU stuff.  In Windows, it's completely backwards, there's a few console apps to manage the system stuff, but it's more of an afterthought than anything else.

Not really.  It's just that the command line is still very popular for everyday use on Linux, so shells like BASH and Zsh receive more maintenance.  There are also more CLI apps available.  Windows is also build on top of a command line.

---

### Post by jbysmith on 2009-03-22
> **cardinals_fan said:**
> Windows is also build on top of a command line.

That's not really true either.  Applies to the older Windows in the 95 generation, but after NT there is no DOS anymore.  You *can* boot to a safe mode command prompt, but that's still cmd.exe running on the Windows kernel.. technically cmd.exe is still a Windows program.  Gnome and Linux on the other hand are completely separate entities, actually a lot like the Win95 generation.

---

### Post by monkeyKata on 2009-03-22
> **stormfrog said:**
> 
All linux systems aer great as server OS:es. As a Desktop/Office user OS:es they are not at all impressive, neither is Ubuntu.  

I won't comment on Ubuntu/Linux's error handling, but as someone who's been using Ubuntu since the summer I'll say that I'm very impressed.  I think Ubuntu (and in that Gnome, Compiz, different bundled software...) is very impressive.   Even if I'm only using my computer for non-intensive, 'average' tasks like browsing through a dozen tabs in Firefox, watching movies, listening to music, and writing/reading documents, it's impressive to me that I have been doing all of this for 8 months without acquiring a virus.  I cannot remember when my computer last crashed.  Then there are lots of little things that impress me (the fact that the hard drive doesn't grind for a couple of minutes after closing open programs, booting down in under 10 seconds, having a second or third of fourth desktop to spread windows about, moderately wobbly windows and animations that add life and character to the desktop, being able to easily change the entire look).  

I think that Ubuntu and Linux must impress people on all sorts of levels.


> **stormfrog said:**
> 
Restarting the network services on XP is done by simply right clicking network taskbar icon and press repair - this usually solves any temporary networks hiccups. Such a function is completely absent in Ubuntu. Its just one example. In my experience there are many more.  

While the network manager may not have a reset (though maybe it does I don't know) could right-clicking on the wifi/network icon and unchecking then rechecking "Enable Wireless" and/or "Enable Networking" have the desired effect?

---

### Post by SunnyRabbiera on 2009-03-22
But the thing is that as time passes more GUI apps are added to the linux side.
To me linux has more progress with GUI apps and interfaces in the last 4 years then what Windows could develop in 10.
When I first used Linux it was more CLI oriented, this was 2004, but between now and then many GUI apps have come about.
Look at the time between Windows 95 and XP, really Windows really didnt become fully "user friendly" in the modern sense until XP.
95 had far less decent GUI tools when it came out then Linux does now, and between then and XP little improvement in general user interface and ease of use was made.
But even XP pre SP1 to me is less user friendly then Linux is today, without all its fancy pre installed nonsense XP is far less user friendly then Linux could ever hope to be.
Try a fresh non OEM install of XP SP1 sometime, or even SP2.
With XP coming pre installed on most systems it only gives the illusion its easy to use, but really its not.

---

### Post by Aflack on 2009-03-22
i have always thought similar. Ubuntu runs flawlessly... with the bundled software. But when it comes to installing 3rd party stuff from sites it becomes difficult. for me at least. And bugs tend to pop up.

---

### Post by lisati on 2009-03-22
> **jbysmith said:**
> That's not really true either.  Applies to the older Windows in the 95 generation, but after NT there is no DOS anymore.  You *can* boot to a safe mode command prompt, but that's still cmd.exe running on the Windows kernel.. technically cmd.exe is still a Windows program.  Gnome and Linux on the other hand are completely separate entities, actually a lot like the Win95 generation.

This makes sense and helps explain something I'd noticed. <off topic> a few years back I threw together a couple of small programs to help clean the rubbish off my system. The 16-bit DOS version was smart enough to recognize when Win98SE was runnning, and fire up the 32-bit Windows version as required, but it isn't smart enough to recognize XP's presence. Updating it is low on my list of priorities.</off topic>

---

### Post by issih on 2009-03-22
The problem you are having can also probably be sorted by setting the wireless kernel module to be unloaded on suspend.

This thread will show you how.

[http://ubuntuforums.org/showthread.php?t=385226](http://ubuntuforums.org/showthread.php?t=385226)

Things are often a bit less gui centric it is true, but not as much as people tend to think, there are lots of gui front ends for many tasks, you just don't always get told that they are there.

cases in point:

grsync and ndisgtk, things that are very regularly asked about round here, and for which the advice nearly always focusses on the command line version of the tools.

I'm willing to bet there is a gui services manager in the repositories if you go hunting..

Hope that helps

---

### Post by cardinals_fan on 2009-03-22
> **jbysmith said:**
> That's not really true either.  Applies to the older Windows in the 95 generation, but after NT there is no DOS anymore.  You *can* boot to a safe mode command prompt, but that's still cmd.exe running on the Windows kernel.. technically cmd.exe is still a Windows program.  Gnome and Linux on the other hand are completely separate entities, actually a lot like the Win95 generation.
My first computer was an old desktop with Win95.  I never realized my XP setups were different.  Thanks for the info.

---

### Post by dodle on 2009-03-22
> **stormfrog said:**
> Restarting the network services on XP is done by simply right clicking network taskbar icon and press repair - this usually solves any temporary networks hiccups. Such a function is completely absent in Ubuntu. Its just one example. In my experience there are many more.

In my opinion, this is fairly new to Windows.  I believe that in earlier systems the command line had to be used to repair network interfaces.  

A front-end for Ubuntu would be very simple to write for someone who knew the correct shell commands.

---

### Post by jbysmith on 2009-03-22
> **dodle said:**
> A front-end for Ubuntu would be very simple to write for someone who knew the correct shell commands.

I'm on the road myself, so I can't check.  (My little tablet is cute but not very Linux friendly yet.)  No idea if the network manager has that functionality yet or not.. but if it's not though I definitely agree, the Gnome guys should add it.  Interface up, down and restart networking, all one command each.  Should be a no-brainer to add I would think.  

> **cardinals_fan said:**
> My first computer was an old desktop with Win95.  I never realized my XP setups were different.  Thanks for the info.

No problem.  Since you came in after DOS probably wouldn't have even noticed it.  A lot of old timers threw a fit when DOS was finally dropped though if I remember right.  (Windows is just a fad, it'll never catch on.)  I for one don't miss it.  My personal un-favorite was having to make an interactive config/autoexec because some games ran ok with an extended memory manager, some didn't.  Some games wouldn't run with the mouse, Gravis Ultrasound and MSCDEX extensions because not enough low memory free.  Networking was painful at times.  Wheee fun.

---

### Post by wolfen69 on 2009-03-22
linux is not windows. i like it the way it is. if i want something that works like windows, i'll just use windows. 

if you are not techie enough to use ubuntu, then get something that will hold your hand. i don't care about competing with other companies, as my life will not change one way or the other.

---

### Post by betrunkenaffe on 2009-03-22
fyi, regarding the problem, I will confirm that unchecking "Enable Networking" and checking it again will fix the problem. Unchecking "Enable Wireless" is a waste of time.

---

### Post by Tamlynmac on 2009-03-23
Another, "Not Ready for Prime Time" post, comparing Ubuntu to Windows . Seems Ubuntu may be having a bigger impact than many might admit. Between this and the elitist factor, I'm starting to believe Ubuntu is being closely monitored by many that fear it's potential.

As I've stated in numerous posts, any documentation generated in an effort to either bash or demean Ubuntu, may have unexpected results. The more time individuals invest in this effort, the more people they make aware of Ubuntu. Some of  the newly informed individuals may investigate and decide to find out for themselves what the controversy is all about. A number of friends (who knew I use Ubuntu) didn't seriously start questioning me about the OS until after reading a rant comparing Ubuntu to Windows, written by a Windows user.

IMHO we should smile every time someone makes an effort to compare Ubuntu to Windows. Especially, when they endeavor to point out that it's not "Ready for Prime Time". Ubuntu may represent a greater threat than many of us realize. We should ask ourselves, how many would waste time on this effort, if they didn't perceive Ubuntu as a serious threat?

We should all take a moment to thank those that invest their time in this endeavor, for they are unknowingly spreading the word. By notifying disgruntled Windows users of an alternative. Of course, we already know there are no disgruntled Windows users.;)

---

### Post by MYGRA1N on 2009-03-23
> **Tamlynmac said:**
> Another, "Not Ready for Prime Time" post, comparing Ubuntu to Windows . Seems Ubuntu may be having a bigger impact than many might admit. Between this and the elitist factor, I'm starting to believe Ubuntu is being closely monitored by many that fear it's potential.

As I've stated in numerous posts, any documentation generated in an effort to either bash or demean Ubuntu, may have unexpected results. The more time individuals invest in this effort, the more people they make aware of Ubuntu. Some of  the newly informed individuals may investigate and decide to find out for themselves what the controversy is all about. A number of friends (who knew I use Ubuntu) didn't seriously start questioning me about the OS until after reading a rant comparing Ubuntu to Windows, written by a Windows user.

IMHO we should smile every time someone makes an effort to compare Ubuntu to Windows. Especially, when they endeavor to point out that it's not "Ready for Prime Time". Ubuntu may represent a greater threat than many of us realize. We should ask ourselves, how many would waste time on this effort, if they didn't perceive Ubuntu as a serious threat?

We should all take a moment to thank those that invest their time in this endeavor, for they are unknowingly spreading the word. By notifying disgruntled Windows users of an alternative. Of course, we already know there are no disgruntled Windows users.;)

Of course some fear its potential. Especially m$. Who is gonna pay for a £110.00 operating system which you can only activate three times before having to ring to beg for a reset or new serial, when theres a perfectly free alternative that does 75% of things better and quicker. I have the feeling that Karmic may well begin to be the turning point for Linux. Maybe.

---

### Post by Riffer on 2009-03-23
> **stormfrog said:**
> 
Restarting the network services on XP is done by simply right clicking network taskbar icon and press repair - this usually solves any temporary networks hiccups. Such a function is completely absent in Ubuntu. Its just one example. In my experience there are many more.

)

Ummm in Gnome try right clicking on the network manager, unticking "enable networking" to stop network services and reticking to restart networking.  Works for me.  The icon is found in the right hand top corner.

---

### Post by 3rdalbum on 2009-03-23
I often get mistaken for a "computer guru" :-)   And I'm often called upon to fix somebody's Windows problems.

Since I know next-to-nothing about using Windows, I immediately go and look up the problem/error message at the Microsoft Knowledgebase website. And the workaround to the problem is always something like this:

```
RUNDLL32.EXE SHELL32.DLL,Control_RunDLL HotPlug.dll
```

Yes, that's a Windows command that you put into the MS-DOS prompt. There is no GUI equivilant to this command. A similar problem occurs on Ubuntu - this is the Ubuntu command-line fix:

```
nm-applet
```

Which one is less frightening? :-)

---

### Post by moster on 2009-03-23
> **3rdalbum said:**
> I often get mistaken for a "computer guru" :-)   And I'm often called upon to fix somebody's Windows problems.

Since I know next-to-nothing about using Windows, I immediately go and look up the problem/error message at the Microsoft Knowledgebase website. And the workaround to the problem is always something like this:

```
RUNDLL32.EXE SHELL32.DLL,Control_RunDLL HotPlug.dll
```

Yes, that's a Windows command that you put into the MS-DOS prompt. There is no GUI equivilant to this command. A similar problem occurs on Ubuntu - this is the Ubuntu command-line fix:

```
nm-applet
```

Which one is less frightening? :-)

That what you said is used to create shortcut or for some masochist trying to use CLI on windows. Usually clicking on icon in tray is easiest way for most people ;)  (in windows, of course)

---

### Post by 3rdalbum on 2009-03-23
Actually, that command makes the "Safely Remove Hardware" applet appear on the Windows XP taskbar, in the event that it did not appear normally. I'll confess that I looked up "rundll32.exe" in Google to find a suitably scary-looking command, as the darn things are usually too long for me to remember!

The point is, contrary to what the original poster said, some problems on Windows require a command-line to fix. But it's usually MUCH easier to decipher the Ubuntu ones than the Windows ones.

---

### Post by brokenLockpick on 2009-03-23
> **SunnyRabbiera said:**
> *snip*

Try a fresh non OEM install of XP SP1 sometime, or even SP2.
With XP coming pre installed on most systems it only gives the illusion its easy to use, but really its not.

This can be equally true of Vista. I've come to dread reinstalls at work as usually whether XP or Vista none of the network interfaces work "out of the box." Thus the irritating  process of taking a usb drive to another computer to get a networking driver and watching Windows fail to find half the drivers and having to go get them manually.

As for the person who mentioned the difficulty of downloading and installing programs found online. Personally I like that I can usually find a program to do what I need in the repositories, even when using windows I never had good luck with programs from here and there online, they contained/were generally some form of crapware.

---

### Post by TWO on 2009-03-23
> **Tamlynmac said:**
> 

1)I'm starting to believe Ubuntu is being closely monitored by many that fear it's potential.

2)A number of friends (who knew I use Ubuntu) didn't seriously start questioning me about the OS until after reading a rant comparing Ubuntu to Windows, written by a Windows user.

3)We should ask ourselves, how many would waste time on this effort, if they didn't perceive Ubuntu as a serious threat?


1)Fear it's potential? *Fear? :confused:*How many more ***year of the linux desktop* **are going go by before you realise that there is no fear on anyone's part. It's an operating system, not an atomic bomb.

2)  So based on *one *rant by *one *self-righteous blogger on the entire internet, your friends chose to switch to Ubuntu, rather than doing so based upon their own grievances? 

3) Only those that aren't prepared to see Linux-based OSes for what they are: OSes for tech savvy people. It can be said until one is blue with asphyxiation: If the command line/configuring .conf files isn't your thing, then Linux is not for you. You don't use OS X expecting it to be Windows and vice versa.

Wolfen69 said it best:
> **wolfen69 said:**
>  linux is not windows. i like it the way it is. if i want something that works like windows, i'll just use windows. 

if you are not techie enough to use ubuntu, then get something that will hold your hand. i don't care about competing with other companies, as my life will not change one way or the other.

It's just trolling, plain and simple...

---

### Post by Bölvaður on 2009-03-23
> **TWO said:**
> 1)Fear it's potential? *Fear? :confused:*How many more ***year of the linux desktop* **are going go by before you realise that there is no fear on anyone's part. It's an operating system, not an atomic bomb.

You didn't see Steve Ballmer's presentation? It is a ppt file that can be found on the internet.
He was having one of those presentation to impress investors (their stock were falling very rapidly) where Linux was shown as a bigger threat than Mac OSX (bigger market share).

and to be a little sarcastic...
Ballmer has never said anything bad about Linux or open source software... ever.


2009 was not celebrated as year of Linux for the first time in what... 10 years? 
Why? Because we have already got on a good place when the most wanted hardware makers are making drivers for us... sure there are small printer companies and such but hey we got hp and also ati and nvidia doing quite good jobs.
We stop caring the moment things are good. We only complain when things are bad. Most have stopped caring.

---

### Post by elliotn on 2009-03-23
For me, linux was dificult n not user friendly but as I go around to learn it slow by slow I manage to learn few staff. Taking into consideration that I dont have full internet access.

I use my SE w890i fone as modem I couldnt believe it that when I pluged it up it worked out of the box. I was surprised as I didnt have to enter commands in the network manager like in Xp, nor need the SE PC Suite. Which is imposible in Windows.

---

### Post by stalkingwolf on 2009-03-23
> How does Ubuntu handle errors like this and how is the user informed of system errors/solutions? I am not impressed by this part of Ubuntu and I think this is an area that need serious work. While you can solve much of these errors to begin with by user testing before release the Ubuntu community simply does not have the same resources to do this as OSX/Windows OS. There is an abundance of different hardware systems with an odd collection of jumbled hardware. There is so much that testing Ubuntu with all these different setups is just to much work.

What else can be done... well, I am in no way a developer of such things. But I think an interesting option would to investigate if it is possible to create a system manager that is built into the core of Ubuntu. A system manager that track the condition of the systems hardware/data that can give the user a through and easy to grasp report of what has gone awry with a system if something breaks down - and also present the user with a list of what actions must be made to correct this error.

If you have your machine set for the verbose boot up. you can see at each step what is happening.

Mine tells me if there is a problem or suspected problem.  I willingly 
sacrifice a bit of boot time to know whats up.  this has saved me from loosing info on a drive that was about to go belly up several times

I dont know how much easier than ESC>RECOVERY MODE>FIX BROKEN PACKAGES
it can be , or that you want it.

True Linux is not for everyone.  But i think if a six year old can figure it out most can.

but then that is just my experience, to date i have set up systems for 4 six yr olds and a 5 yr old.  they have a blast.  they can even log on by themselves.

---

### Post by MYGRA1N on 2009-03-23
> **Bölvaður said:**
> You didn't see Steve Ballmer's presentation? It is a ppt file that can be found on the internet.
He was having one of those presentation to impress investors (their stock were falling very rapidly) where Linux was shown as a bigger threat than Mac OSX (bigger market share).

and to be a little sarcastic...
Ballmer has never said anything bad about Linux or open source software... ever.


2009 was not celebrated as year of Linux for the first time in what... 10 years? 
Why? Because we have already got on a good place when the most wanted hardware makers are making drivers for us... sure there are small printer companies and such but hey we got hp and also ati and nvidia doing quite good jobs.
We stop caring the moment things are good. We only complain when things are bad. Most have stopped caring.

Ummmmm Ballmer has said negative things. He said that linux was a cancer.... :(

---

### Post by MartyBuntu on 2009-03-23
> **MYGRA1N said:**
> Ummmmm Bulmer has said negative things. He said that linux was a cancer.... :(

Do you have a link for this?

---

### Post by MYGRA1N on 2009-03-23
> **MartyBuntu said:**
> Do you have a link for this?

[http://www.theregister.co.uk/2001/06/02/ballmer_linux_is_a_cancer/](http://www.theregister.co.uk/2001/06/02/ballmer_linux_is_a_cancer/)

---

### Post by 3rdalbum on 2009-03-25
I just installed Windows Vista from scratch on a new computer. Absolutely nothing was automatically detected - I had to install all drivers from scratch, including the Ethernet driver; which would have been very difficult if I'd lost the CD with it on!

By contrast, the Ubuntu live CD immediately started working with everything, except the Nvidia graphics card (much better resolution than Vista with no drivers, but no 3D acceleration). Yes, this computer has wireless. The Nvidia driver was a couple of clicks away.

---

### Post by mdsmedia on 2009-03-25
> **issih said:**
> The problem you are having can also probably be sorted by setting the wireless kernel module to be unloaded on suspend.

This thread will show you how.

[http://ubuntuforums.org/showthread.php?t=385226](http://ubuntuforums.org/showthread.php?t=385226)

Things are often a bit less gui centric it is true, but not as much as people tend to think, there are lots of gui front ends for many tasks, you just don't always get told that they are there.

cases in point:

grsync and ndisgtk, things that are very regularly asked about round here, and for which the advice nearly always focusses on the command line version of the tools.

I'm willing to bet there is a gui services manager in the repositories if you go hunting..

Hope that helps
I have to agree on this. I started using rsync, because it was available. I later learned of grsync and I love it, but rsync would have been fine from CLI.

I learned about rsync, and it's a brilliant backup utility. I used grsync only because I learned about it later.

---

### Post by stchman on 2009-03-25
> **MYGRA1N said:**
> Ummmmm Ballmer has said negative things. He said that linux was a cancer.... :(

After reading that article.  His concern sounds like that WHEN he uses GPL protected software to make Windows apps that he must make the source code available for all that ask.

If it was not for Linux or OSX, M$ would not have any good ideas to steal.

M$ after they steal the source code, use it to do what they need to do patent it.  Then they have the stones to say that Linux stole their intellectual property.

Smells like bull$hit to me.

---

### Post by cardinals_fan on 2009-03-25
The comparison to cancer was actually quite valid, except that cancer is horrible and often kills people, while open source software only threatens the pocketbooks of traditional software distributors.

---

### Post by quazi on 2009-03-25
> **wolfen69 said:**
> linux is not windows. i like it the way it is. if i want something that works like windows, i'll just use windows. 

if you are not techie enough to use ubuntu, then get something that will hold your hand. i don't care about competing with other companies, as my life will not change one way or the other.

That's very elitist of you.  Because you're able to solve most problems that crop up, you don't think that there should even be the option for a GUI which helps deal with this issues?  

The OP isn't saying Linux should work like Windows, but that it shouldn't be worse at doing something just to avoid being too similar to windows.  You might not care about competing with OSX/Windows, but the well-being of Linux is not solely determined by your usage.  

The more people who use Linux, the better.  Period.

---

### Post by TWO on 2009-03-27
> **quazi said:**
> That's very elitist of you.  Because you're able to solve most problems that crop up, you don't think that there should even be the option for a GUI which helps deal with this issues?  


You answered your own question there: yes. If someone is able to resolve those problems, why would they want additional bloat to perform the same function? 

> 
The OP isn't saying Linux should work like Windows, but that it shouldn't be worse at doing something just to avoid being too similar to windows.  You might not care about competing with OSX/Windows, but the well-being of Linux is not solely determined by your usage.  

The more people who use Linux, the better.  Period.By whose judgement are the methods used to fulfil tasks on a Linux-based distro as opposed to on Windows/ OSX worse? 

And by the same assertion, the well-being of Linux is not determined by *your *usage, so what does any of it matter? 

You are at liberty to use your skill to shape Linux in the way that you see fit, or to make use of KDE as opposed to GNOME, or Enlightenment, and/or vice versa. What you are failing to address about the very nature of Linux-based distributions is that there is not single standard way for things to be done. Windows/ OSX have one, uniform method of doing everything and that is cool, but with Linux, you have a multitude of methods at your disposal.

You can't base your judgement of *the Linux experience *on your single experience with say, Ubuntu and the GNOME desktop environment, when there are many other methods at your disposal. GNOME does not work like KDE, which does not work like the next desktop environment. And I guess the same can be said across different distributions. 

Your complaint simply does not apply to the entirety of Linux.

---

### Post by GSF1200S on 2009-04-03
The reason Linux cannot compete with Windows or Mac OSX is vendor lock out. Part of it im sure Microsoft pays for to ensure Linux cannot grow, and others are due to corporations worried about money instead of the support.

Take for example my current desktop. My motherboard has a myriad of software included to overclock, control audio, change bios loading screens, configure profiles, etc. I cant use any of it on Linux- only Windows.

Windows is just an operating system, as is Linux. Sometimes I digress and wonder if Im robbing myself of fun/capability, especially when im fortunate enough to enjoy some truly amazing hardware, by using only Linux. As it stands now, im fighting with myself over it. There are two schools of thought:
1) Its just an operating system- being stubborn and staying solely linux is robbing me of the whole experience available. "Loyalty persevered beyond logic creates the fool"
2) On the other hand, Windows is not just a product. If Microsoft tried to create the best product, and while falling second to Linux in terms of power and stability, still did their best to create their product, I would have no problem using it. But they dont- they only make it good enough to sell, and they do everything to pack the same **** in ever prettier packages. A turd is still a turd, and a turd peddled by a ruthless greedy company whoes only concerned with their bottom line is not a turd I need in my life. Linux is made by the people for the people, with a totally noble disposition. It is more powerful, more modular, more eloquent, and totally keeps your privacy in mind. 

Can Ubuntu or Linux compete? Not really- Microsoft has defined computing around its operating system, and until/if ever people become willing to change their perspective on the expierience, Linux will continue to bleed and suffer from its ideological plight. I really REALLY want to mess with the software included in my mobo, but Im very zealous in all avenues of my life to follow whats morally right. Im starting to lose the faith with Linux, even though I know the OS is superior and the ideological stance is superior- Linux is holding me from other software that would enable me to do more.

Arghh.. This is why people bounce back and forth, and this is why many people go back. Many of you think we will eventually win, but I dont think we will. I think people are generally ignorant (thanks to sociological influence) and I think Linux will end up being another November 5th or Guy Fawkes memorium. New concepts of computing will eliminate the desktop, much as the telephone eliminated the telegraph, and Linux will be only a memory. I really hope im wrong, and ten years from now Linux has 90% market share, but I doubt it...

---

### Post by druellan on 2009-04-03
I agree with GSF1200S. Two things that stop me thinking on Linux as a replacement of Windows/OSX on my workstation.

  * Lack of commercial software: there are few professional quality software for Linux (usually one of a kind). Community support is not enough if you're going to expend money and time becoming an expert using a complex application that has a volatile set of developers.

  * Occasional regressions: sometimes updates can break a previously working feature. This happens on other OSs, but is still pretty frequent on Linux desktop distros. Pay support helps, but is still a problem.

---

### Post by solwic on 2009-04-04
> **quazi said:**
> That's very elitist of you.  Because you're able to solve most problems that crop up, you don't think that there should even be the option for a GUI which helps deal with this issues?  

The OP isn't saying Linux should work like Windows, but that it shouldn't be worse at doing something just to avoid being too similar to windows.  You might not care about competing with OSX/Windows, but the well-being of Linux is not solely determined by your usage.  

The more people who use Linux, the better.  Period.

You had me until that last line.  I wholly and completely disagree.  If Linux takes over market share of the desktop PC world (the more the merrier, you said), the viruses and other various badware will just be targeted at Linux.  No OS is invulnerable.

Period.

Besides, if Ubuntu/Linux ever did make it to the big time, all the software vendors would just target it like they have Windows and Mac, and pretty soon you've got a world of Linux that's polluted to the very core with third-rate, third party software that's more often than not pre-packaged with the latest versions of whatever toolbar/tracking app/adware that has floated to the top of the toilet bowl.

In short, whichever OS collects the most users and exposure will be targeted by every lowlife scumbag itching to make a buck or steal your data.  

:biggrin:

---

### Post by brokenLockpick on 2009-04-04
> **jrock612 said:**
> ...In short, whichever OS collects the most users and exposure will be targeted by every lowlife scumbag itching to make a buck or steal your data.  

:biggrin:

I could not have put it better.

---

### Post by Mr Henderson on 2009-04-04
> **monkeyKata said:**
>  could right-clicking on the wifi/network icon and unchecking then rechecking "Enable Wireless" and/or "Enable Networking" have the desired effect?

When I do that the system hangs and needs a reboot.

Inevitably these threads are written mainly by people who have no problem getting Ubuntu to connect to the internet. If everyone who's given up on Linux because of internet connection problems was posting here, we might get a rather different picture.... 

(Writing on a Windows machine.)

---

### Post by albinootje on 2009-04-04
> **druellan said:**
> 
  * Lack of commercial software: there are few professional quality software for Linux (usually one of a kind). Community support is not enough if you're going to expend money and time becoming an expert using a complex application that has a volatile set of developers.

And what are you and me and everyone else who is interested in Linux gonna do about this ?

A few days ago I've let some friend install Ubuntu on her laptop, and the people there asked about Linux on a Mac.
I said that it is more difficult, and as an example I told them that Flash plugin for Linux on the Mac doesn't exist.
Later at home I looked up some details (It's years ago that I have used Linux on a Mac), and I found out that there has been a petition to ask Adobe to make the Flash plugin available for Linux on the Mac. There were more than 4000 people who signed that petition, and the result ? Still no Flash plugin for Linux on the Mac.

And this is only about a rather simple plugin for a web browser

What can you do .. ?

---

