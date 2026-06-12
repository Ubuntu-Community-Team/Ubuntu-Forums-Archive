---
title: "Terminals and GUIs"
date: 2016-02-18
forum: The Cafe
---

### Post by user1397 on 2016-02-18
So I've been discussing this topic with a friend of mine.  To give a bit of background, I have been using linux mainly ubuntu as my main OS on and off for the past 10 years, and am quite familiar with windows as well.  This friend of mine actually introduced me to linux (ubuntu breezy badger!) 10 years ago, but he has far more windows knowledge than I do and maybe a bit less linux knowledge than I do (debatable).  My friend is also a gifted programmer, whereas I have only dabbled in programming.  Also, he is not a linux basher or a windows lover or anything like that, he is quite OS neutral, and loves and hates things about every major OS, quite like myself.

Anyways, he says that every time he has tried using linux (usually ubuntu), he hates the fact that either
a) he finds a really annoying bug during the install process or when using the newly installed system normally, and/or
b) he has to use the terminal to do/fix something. 
 I told him he must have terrible luck with his hardware or something because I usually never have any problems with ubuntu, or at least just a minimal amount of bugs (no more than I would in Windows or OS X).

He's of the opinion that in a modern, general purpose, user friendly OS (such as windows, OS X, ubuntu, etc), you shouldn't need to use the command line or edit config files manually at all if you're an end user.  He says it's fine to have config files but there should be standardized, user friendly GUI wrappers around these config files and system settings.

Now, I've explained to him that I've actually run ubuntu for months or years on end and rarely needed the terminal for anything; I only use the terminal as a preference sometimes, and that many people say the same thing.  Either way, when it comes down to it though, I agree with him in general.  I feel like any serious user friendly OS should have nice standardized GUI wrappers around all system settings config files for example.  I'm not saying *instead* of plain text config files; I mean have the GUI wrapper as the main method of doing things, but leave the config files where they are in case you want to do things the manual way.

Now I realize there are already a lot of GUI tools for system settings and configuration, and just about every DE has some sort of control panel looking app.  But at the same time, if you (as an end user) run into some kind of issue and you can't find an obvious GUI tool to fix it, you are basically forced to google the issue or post a thread here, and in either case you will most likely be told "copy and paste this into the terminal" without you actually knowing what you're doing.  Does this happen in other OS's such as windows? Yes, but not on the scale that it does with linux.  Most online troubleshooting guides for windows guide you through a GUI solution to a problem.  Most linux guides give you terminal commands.  No arguing that.

A good example would be network troubleshooting.  In windows for example, if you can't connect to the internet, you can right click and click "troubleshoot problems" and a simple dialog box appears that in the background performs basic troubleshooting steps to try to resolve the problem, such as disabling/re-enabling the internet connection, and performing commands like "ipconfig /release" and "ipconfig /renew".  As far as I know, linux doesn't have anything nice and simple like this for a regular ol' end user.  You're stuck with googling for help and probably getting shown how to run a command in the terminal that might fix your problem.

So what is the actual gripe with linux power users and GUIs?  Too often I've heard things like "GUIs are slow and bloated" or "they are way buggier than editing plain text files" or similar things, but it really just doesn't seem convincing.  A common thing I hear linux people say is "once you get familiar with the linux way of doing things, the terminal makes more sense."  That sounds pretty vague to me. Has it just become some form of an elitist statement?  I guess the most extreme example of this would be a distro like Arch, where they glorify the terminal and manually editing config files for all users.  Obviously that's a bit different because their target isn't your average joe regular user like ubuntu's is, but still.

Thoughts please!

**I'd like to reiterate, that I am talking about terminal usage for the average end user, not power users or technically-minded folk.

***If you would like to see what my friend (the one I'm talking about at the top of this post) said on this subject, he posted [this]("http://ubuntuforums.org/showthread.php?t=2314057&page=3&p=13443187#post13443187") in this thread.

---

### Post by QIII on 2016-02-18
Neither is better.  Doing what you need to do in a manner with which you are comfortable is better.  In my opinion, the purist terminal elitists fail: they trade pragmatism for a false sense of superiority. 

The console is simply "universal".  That is -- without knowing which one of dozens of GUIs you may be using, I can tell you how to do something via the command line.  Therein lies its utility.

But nearly anything you want to do can be done via a GUI, be it the components of the DE/WM you are using or by using installed apps.

That said, I use the terminal very extensively -- and that out of long experience since the 70s and Unix, not out of some misguided belief that I am somehow a "real" user.

The machine is *your* tool to do with what *you* want to do however *you* want to do it to get the results that *you* want.

By the way, when you say "I feel like any serious user friendly OS should have nice standardized GUI wrappers around all system settings config files", *who is it that gets to decide what the standardized GUI is?*   That is a problem.

---

### Post by user1397 on 2016-02-18
> **QIII said:**
> Neither is better.  Doing what you need to do in a manner with which you are comfortable is better.  In my opinion, the purist terminal elitists fail: they trade pragmatism for a false sense of superiority. 

The console is simply "universal".  That is -- without knowing which one of dozens of GUIs you may be using, I can tell you how to do something via the command line.  Therein lies its utility.

But nearly anything you want to do can be done via a GUI, be it the components of the DE/WM you are using or by using installed apps.

That said, I use the terminal very extensively -- and that out of long experience since the 70s and Unix, not out of some misguided belief that I am somehow a "real" user.

The machine is *your* tool to do with what *you* want to do however *you* want to do it to get the results that *you* want.

I agree with you for the most part.  I agree about the machine being your tool and using the best tool for the job.  And you are right, the console is universal.  I guess I was talking more about how things should be by default, or for most users.  In that case I think having extensive, standard GUI tools should be the norm, but of course the option to use the terminal should always remain.

---

### Post by QIII on 2016-02-18
See the last line I just added.  ;)

---

### Post by user1397 on 2016-02-18
> **QIII said:**
> [COLOR=#000000]By the way, when you say "I feel like any serious user friendly OS should have nice standardized GUI wrappers around all system settings config files", [/COLOR]*who is it that gets to decide what the standardized GUI is? That is a problem.*
Ahah, why that is a whole separate issue :)

But yea in an ecosystem as fragmented as linux, standardization is hard.  Although you could say there are certain tools that have become standard, and there are certain standards or guidelines in place.  But yea, you definitely bring up a great point.

Also I'd like to say I am not like professing that this should definitely be done, I'm just talking in hypotheticals here and asking for opinions. :)

---

### Post by mastablasta on 2016-02-18
> **ubuntuman001 said:**
> 
So what is the actual gripe with linux power users and GUI tools?  Too often I've heard things like "GUI tools are slow and bloated" or "they are way buggier than editing plain text files" or similar things, but it really just doesn't seem convincing.  Windows for example, has great GUI tools to edit almost any settings you can think of, and OS X has quite a few though not nearly as many as Windows.  


Please check the philosophy behind gnome desktop and you will see that they are trying not to overwhelm the common user with various settings and options in GUI. KDE is the opposite of that and they try to create a GUI for everything. and they encourage this. perhaps your friend could help them in this process?! it's not that no one wants them, but more the case that no one made them. everyone is invited to make them.

> 
A quick example I thought of would be if you were trying to edit any grub settings like the timeout (I could see how a regular user would want to do this, because the normal timeout is 10 seconds and maybe they think that takes too long).  Without googling it, it would be nearly impossible for a regular user to figure out how to edit grub settings.  And I think there maybe is a GUI wrapper to edit grub settings nowadays, but it is definitely not installed by default and usually isn't mentioned in grub editing guides.

So in this example, the user has no choice but to google information and then type in some strange commands to edit something in his system.  The ideal would be to have a "edit bootloader" settings in a main settings GUI app, and from there being able to edit the basic things like timeout.

a regular user would not want to do this. a user that bought a system with ubuntu preloaded has no need for this. in fact they do not need to know about grub at all.

and speaking of boot loader example - this is how same operation is done in windows 10 : [https://msdn.microsoft.com/en-us/library/windows/hardware/ff543423(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/ff543423(v=vs.85).aspx)
oh is that a command line I see?

and going back to gnome there is an application available called Grub Customizer. might not be preloaded but that is understandable as regular user does not need to know about grub.

> 
Another common thing I hear linux people say is "once you get familiar with the linux way of doing things, the terminal makes more sense."  That sounds pretty vague to me, like a not-convincing-at-all argument.  It seems like maybe linux (and I guess any unix-like) users have been sucked into this mindset that terminal and config files is for the best, but why exactly is that?   Has it just become some form of an elitist statement, kind of like how vim users think their way of doing things is better just because? (had to throw that one in there :))


because some operations can be done faster. same goes for windows. there are some huge operations that are just simply done faster via terminal. if we talk about home PC there are maybe only some cases when CLI is faster, but if you have administration of thousands of PCs believe me that plenty is still done in terminal even in windows. ever heard of windows batch files?

config files - I don't know if you used any in Linux. they often include documentation. and they work in same way weather desktop is installed or there is only text terminal interface.

why so much is available in CLI - Linux was created from Unix which was mostly in server. it then moved to desktop. windows was created on desktop first and then moved to server area. in linux same edition, same install can be used as server or as desktop. windows has some limitations.

---

### Post by vasa1 on 2016-02-18
> **QIII said:**
> ...
By the way, when you say "I feel like any serious user friendly OS should have nice standardized GUI wrappers around all system settings config files", *who is it that gets to decide what the standardized GUI is?*   That is a problem.
KDE v/s GNOME v/s XFCE v/s Enlightenment v/s ...

---

### Post by user1397 on 2016-02-18
> **mastablasta said:**
> Please check the philosophy behind gnome desktop and you will see that they are trying not to overwhelm the common user with various settings and options in GUI. KDE is the opposite of that and they try to create a GUI for everything. and they encourage this. perhaps your friend could help them in this process?! it's not that no one wants them, but more the case that no one made them. everyone is invited to make them. I agree with you on that, gnome seems to be taking away more and more GUI options every year, while KDE seems to add more and more, so in this regard I do consider KDE to be implementing this better than anyone else in the linux world at the moment.  And I will suggest to my friend that perhaps he can try to help make/improve these things with open source projects, he might be into the idea.



> a regular user would not want to do this. a user that bought a system with ubuntu preloaded has no need for this. in fact they do not need to know about grub at all.

and speaking of boot loader example - this is how same operation is done in windows 10 : [https://msdn.microsoft.com/en-us/library/windows/hardware/ff543423(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/ff543423(v=vs.85).aspx)
oh is that a command line I see?

and going back to gnome there is an application available called Grub Customizer. might not be preloaded but that is understandable as regular user does not need to know about grub.You're right, the grub example was bad.  I could see how there is a small chance a non-power user would maybe think the bootloader menu takes too long and would wanna maybe see if there is a way to change that, but a regular user wouldn't even know where to begin searching for that...he/she probably wouldn't know the terms "bootloader" much less "grub" or anything related to it.  And yea I mentioned how I thought there was a GUI tool for that in my original post.

Can't that be done in a GUI way in windows though? I thought if you go to advanced system settings, under the advanced tab there is a "Startup and Recovery" section with a settings button.  Maybe this is for a different setting and not a timeout though, not sure.




> because some operations can be done faster. same goes for windows. there are some huge operations that are just simply done faster via terminal. if we talk about home PC there are maybe only some cases when CLI is faster, but if you have administration of thousands of PCs believe me that plenty is still done in terminal even in windows. ever heard of windows batch files?

config files - I don't know if you used any in Linux. they often include documentation. and they work in same way weather desktop is installed or there is only text terminal interface.

why so much is available in CLI - Linux was created from Unix which was mostly in server. it then moved to desktop. windows was created on desktop first and then moved to server area. in linux same edition, same install can be used as server or as desktop. windows has some limitations.I agree, it can be faster.  I meant my original argument in the case of regular users and basic system settings changes and maintenance.  And yes, I have used config files before...I don't know why you ask that. Whether they have documentation or not isn't related to the discussion on whether there should be a GUI wrapper for them or not.

---

### Post by buzzingrobot on 2016-02-18
Using the command line is not -- at least, should not be -- necessary to using a Linux distribution that targets mainstream non-technical users. It's not on Windows or OS X or iOS and Android, so it shouldn't be needed on Linux.

Many Linux sites offer "guidance" that's strictly command line because, I'd argue, many simply plagiarize it from other sites, it's easier to create than it is to build a lengthy howto with screen grabs of GUI tools, and they want to encourage their readers to simply (unthinkingly) copy-and-paste instructions.

The command line is as much of interface as any GUI.  It exists because operating systems and other software existed before hardware was capable of displaying a GUI. Think mid-20th century.

The commands we enter on a command line are interpreted and acted on by software.  Since software is rather literal, what we type must conform to a specific vocabulary, a specific syntax, etc.  That accounts for the precision the command line demands.  It's unforgiving handing of user errors is more tradition and inertia. 

However, there's nothing you can do at the command line that can't also be done in a GUI, as long as the developers include that capability.  The command line is considered more capable only because GUI's are limited to the capabilities the designers and developers chose to include. (Actually, so are command line tools.)

Both are equally rigid.  GUI tools simply prepackage things.

Of course, the opposite is also true. Imagine doing what you do with Photoshop or Gimp at the command line.

There's always been some degree of chest thumping in some circles trying to position "real" Linux users as folks who live on the command line. Pfft.:p

---

### Post by mastablasta on 2016-02-18
> **ubuntuman001 said:**
> 
Can't that be done in a GUI way in windows though? I thought if you go to advanced system settings, under the advanced tab there is a "Startup and Recovery" section with a settings button.  Maybe this is for a different setting and not a timeout though, not sure.


quite possibly it can. if not by default then by some 3rd party tools. but that 3rd party made them and often these tools are closed source and sold. for example TweakUI might have it. there are also graphic registry cleaners. point is in Linux there are GUI tools as long as someone made them. if no one makes them or feels the need for them then they are not available. for example why would you need a GUI for fail2ban config if it is used primarily on headless servers where for various reasons you do not want to have or need a desktop GUI?

Even servers have plenty (web) GUI's available so one can administer them and change config files via GUI (Zentyal, OpenMediaVault, Nethserver, ClearOS...). so again many tools exist, many are not installed by default. if it doesn't exist then it's not that no one wants it, it's because either no one feels the need for it or no one made it yet. it doesn't have to do with elitist or anything like that. I use Linux and I am crazy about GUI. I even helped with bugs and suggestion for one app gui improvement (yes only one, no time these days...).

> 
I agree, it can be faster.  I meant my original argument in the case of regular users and basic system settings changes and maintenance.  And yes, I have used config files before...I don't know why you ask that. Whether they have documentation or not isn't related to the discussion on whether there should be a GUI wrapper for them or not.

I don't know what basic operation requires CLI and is not available via GUI. last thing I ran from CLI on desktop was phoronix test suite and it was just because it was faster copying a command.
note that I use KDE but:
File management is covered, troubleshooting is covered, bug reporting is covered, drivers install is covered, networking covered, PPA's & software install is covered by GUI, systems settings have a GUI, backups have GUI, system upgrade has GUI, system install has GUI, logs overview has GUI... so I wonder what basic system function requires a CLI?

CLI only programs do need CLI obviously. but it's the same thing in windows. and just like in windows you can run them from GUI.

---

### Post by coldraven on 2016-02-18
Some years ago a friend used to scour the internet for GUI utilities to do various tasks. Then he would try out each one and tell me which performed best.
The problem was that downloading random shareware, freeware or cracked* programs inevitably resulted in our computers being virus, trojan and spyware ridden. In the end I was spending more time trying to clean my computer than actually using it productively. I switched to Linux and now I don't have that problem. 

As for using the terminal it's really about money.
I can lift the bonnet of my car and check the oil level or I can pay someone to do it for me. How much money does your friend have?

*Again it's money related, not all of us can afford expensive proprietary software.

---

### Post by montag dp on 2016-02-18
I think if you shun one or the other, you are missing out. The terminal, for example, is very powerful and can also accomplish basic tasks (e.g., certain file management and manipulation operations) much more quickly than with a GUI, especially when one considers scripting possibilities. In many other cases, a GUI is more convenient and/or useful. They both have their uses.

I think that terminal-only elitists (which I've heard exist but have never actually met one) are foolish, just as I think people who are unwilling to learn to use the terminal should step out of their comfort zone. Oh, and actually, I have run across GUI-only elitists on this forum before, which is just as foolish a position to take, IMO.

One other thing. I think the reason why help is often given as terminal commands in Linux forums is because the terminal is ubiquitous and most of the commands cross DE and distro lines. So there's no reason to ask which DE or distro one is using and then guide them through the specific menu options to find the setting they are looking for. Plus, many system related tasks that the average user doesn't need to mess with unless something breaks simply don't have a GUI, just like in Windows and OSX.

---

### Post by kurt18947 on 2016-02-18
> The console is simply "universal".  That is -- without knowing which one  of dozens of GUIs you may be using, I can tell you how to do something  via the command line.  Therein lies its utility.

Exactly. Most hardware manufacturers use some sort of CLI installer because they only have to write one. I think the patched rtl-8192cu driver found on github is a good model for installing via the command line for non-technical users. Have the appropriate part of the web page visible and open a terminal. Copy and paste, one line at a time. No need to understand syntax, no problem with letter case or typos. Brother and Samsung have printer & scanner drivers that are installed via the command line. A user only needs to type or copy/paste one line to launch the script and manufacturers need not create multiple GUI based installers. 

I'm sure if manufacturers thought they'd be selling machines to 10s of millions or 100s of millions of desktop linux users they'd be glad to devote the necessary resources to creating multiple graphical installers. I'm fairly certain they don't see the desktop linux market that big yet but developing a universal installer script is pretty simple.

---

### Post by grahammechanical on 2016-02-18
My first install of Ubuntu was 7.04. It seemed that to change settings I had the choice of 2 or 3 different utilities. And the terminology was very specialised. All that has changed. Do I thank Gnome or Ubuntu devs? I does not matter. I am thankful. 

To speak of one universal set of GUI utilities is to miss an important point about Linux distributions. They are not controlled by one mega, over-riding corporation. I do not want Linux to be controlled by RedHat or by Canonical or by some other foundation/commercial enterprise. I do not want Linux to have only one Desktop Environment with a universal set of utilities.

Linux exists because of the principles of Free & Open Source Software. There are advantages and disadvantages that come from FOSS. Is it an advantage or a disadvantage that Linux is not like an Apple or a Microsoft OS? I do not care. I do not see any point in disputing the details of the differences.

Regards.

---

### Post by buzzingrobot on 2016-02-18
> **montag dp said:**
> I think if you shun one or the other, you are missing out.

True.  GUI's simply don't have enough space to handle all the options and combinations of options possible on the command line, not to mention the piping, backgrounding, etc., available in a Unix/Linux shell.

In ancient times, when I started with Linux, little or no configuration or management could be done via a GUI. No package managers, no dependency resolvers, we had to walk six miles through the snow to install a driver, that sort of thing. No Gnome, no KDE, just a handful of ancient-even-then window managers with Byzantine configuration file syntaxes.

No wonder Linux was a niche product, in a very small niche.

These days, though, any major, competently supported, distribution can be used and managed successfully without opening a terminal window. (That's important because most people fear the command line and won't consider a system that they think requires using it.) Modern Linux is not as foolproof as OS X in that regard, but we're getting close. (Apple's tight control of its systems and OS X software distribution prevents much of the breakage that the freewheeling approach of Linux can cause.)

---

### Post by yoshii on 2016-02-18
I agree with Ubuntuman001 that there really should be GUI front ends for just about everything in Linux.  That would be a lot more user friendly.  
I think gradually it's heading that way.  

I am not very familiar with console commands, but I know a few.  Usually I end up using the console for stuff like "sudo mv" or "sudo gedit".  
The whole sudo thing is a bit ridiculous coming at things from the perspective of a former Puppy Linux user.  In Puppy Linux there is only one major user and they are root by default.  Puppy still works OK with the internet even as root.  It's easier to config and some versions are based upon Ubuntu.  I really wish I could just use that approach instead of the sudo nonsense.  It's not that much of a hassle, but it's a little bit old fashioned and not necessarily needed.  I'm the only person who uses my computer so i don't really need a multi-user environment.  

As for firewalling, I wish the options for firewall GUI were more user-friendly.  I can barely comprehend the recommended programs and techniques.

---

### Post by montag dp on 2016-02-18
Sudo isn't nonsense.  It's not secure to run as root all the time.

---

### Post by QIII on 2016-02-18
Even when I use distros that have a root as a user with a password by default, I never - ever - log in as root.

---

### Post by mikodo on 2016-02-19
An opinion on your title question coming from a "cli challenged" old man who, started with computers in the second half of his 6th decade of life might surprise you that that I think the cli is superior.  To not repeat what others have already said and I agree with, I'll try to offer a reason that maybe hasn't been put forth yet. 

Unix and Unix-like OS's have been traditionally front-runners in this technology. Therein lies the appeal for the developers. &#8220;To bravely go where no man has gone before&#8221;. They are going to code it, and use it. People are going to try it and file bug reports and the code becomes mature, useable  and sustainable. Then a &#8220;new itch&#8221; is in need of scratching and other devs rally behind the next good idea, and the same thing happens with that. I think that is what inherently keeps Unixes "on the bubble" and "pushing the envelope". The devs have "free reign" to run with what "catches their fancy". They are not encumbered with having to produce the shinny gui to appease the "Lords of the Manor" so, people will buy their products because it looks good and "appears" easy to use.  Now, the benefits of Unixes being developed and often more readily available for these newer technologies by cli are pushed to the users, too. These "mere-end users" have access to really cool stuff that, the end-users in those proprietary gui OS's have no exposure to.        

To recap. Libraries and apps become mature, useable and reusable. Some of the best stuff still used today in Unixes remain only in cli. Much of that great stuff that came from Bell labs, IBM, MIT from "back in the day", remains in cli and accessible and is still used and is available only on cli. Granted, newer stuff is used today from those beginnings  but, it is built in conjunction with it.  That is because the impetus and emphasis for Unixes is, to keep "pushing the envelope" with this code and it is being done on the cli.  End-users are able to read guides, ask for "hand-holding" in places like here and enjoy witnessing a "magical world" that, those other end users can't even imagine.

---

### Post by Habitual on 2016-02-19
A terminal emulator is a tool, and a GUI one at that.
Command-line knowledge is great to have experience with.
GUIs sometimes do not have all available options.

When I need to add zones to DNS, I'm using Webmin.

A GUI for everything does seem to be a recent trend in computing and new users seem to have a reliance on them.
I wish they understood that it's just lipstick on the pig.

Some things scare me to death, or at least cause me pause...
I'm pretty sure that no one is compiling kernels with a GUI.

Wise users understand harmony can be achieved using both GUI and c-line.
Neither is "better".

That is my opinion.

---

### Post by user1397 on 2016-02-20
Hmmm I think a bunch of you missed the point.  Maybe not everyone read my entire original post?  Or maybe I didn't word it the best way?  Not entirely sure.  I've been using linux for 10 years, I'm no "expert" but I've picked up a few things along the way.  Yes, I know the command line is extremely fast and useful in many ways, and neither one is better per say (the title I put on the thread was sort-of tongue in cheek in a sense, probably a bad idea on my part). 

I wasn't discussing whether we should eliminate the terminal or if we should have only one distro where everything is standardized.  I was talking about in general terms, for a regular user, and sometimes even for a power user, the GUI tools available in linux are usually lacking as far as complimenting the terminal based tools.  

There is nothing inherently wrong with using a GUI for anything, it is just a preference.  At the same time though, for 99% of users, a terminal shouldn't *need* to be used.  And no, just because it's "linux" or "unix-like" isn't an excuse for that.  There is no inherent excuse for someone to need the command line to perform some sort of fix on their system.

I get that it is easier to just post a command rather than step by step instructions, but often times there just aren't GUI tools for a certain task or the one that exists is horrible or not friendly. 

I wasn't trying to say anything like "linux sucks, windows or os x are better" or anything idiotic like that, I was just bringing up a hypothetical and wanted some constructive arguments.

---

### Post by montag dp on 2016-02-20
Why do you say the terminal shouldn't ever need to be used? I've seen several people say this, but never with any real explanation. In many cases, it's the best tool for the job, so that's your "excuse." And, has been stated already, even in Windows and OSX it's necessary to use the CLI sometimes to fix issues.

Personally, I don't need developers wasting their time making GUIs for every obscure system function under the sun when it could be better spent fixing important bugs or bringing new software technologies to the desktop. It also increases clutter and reduces maintainability, which is bad especially for open source projects because there's always uncertainty about whether there will be enough developers around at any given point in the future.

---

### Post by matt_symes on 2016-02-20
I've just written another script in powershell.

It's very powerful and the best thing Microsoft has done for years.

---

### Post by Hedzer on 2016-02-20
So, **I'm the guy ubuntuman001 had the debate with** - and it's not completely about GUI vs Terminal.  Let me clarify, a CLI is absolutely a necessity for automation and administration.  All of my work with cloud computing setups and servers has been through a SSH'd terminal, no complaints there. 


The debate is about context. Ubuntu has several flavors, this includes several desktop flavors - one of which is considered primary.  If this flavor is meant for the same crowd as Windows and Mac OS, then it stands that it should have a comparable offering. This offering should include some level of similar functionality paired with a consistent look and behavior.  Now, I hear a lot of rambling about Linux and how do we standardize across all distros? We don't. At this point it's silly to look at Ubuntu and abstract back to linux in general. Don't build for all of Linux then, build for Ubuntu Desktop; there's no way to build for all targets unless you build for the lowest common denominator (which is CLI).


I realized I was about to ramble on for a long time, so I broke the points down into a more pithy bullet point format:


**On command line vs GUI:**
* There is no contest, they are for different purposes. 
* Terminal/CLI is for administration and automation.
* GUI is for the average user that thinks opening up a terminal is "hacking" (thanks TV shows...)


**What about consistency and standardization?**
* I keep hearing about how that's impossible to standardize GUIs across Linux. Okay, but this is Ubuntu, more specifically this can be done with the flavor of Ubuntu that is actually recognized as "Ubuntu Desktop" by the public. We can build GUI tools specifically for the look, feel, and behavior of one flavor. 
* I have a separate gripe about config files, mainly the same lack of standardization.


**But Windows and Mac also have issues with standardization, and you sometimes have to use CLI with them too:**
* And? Because they have a problem it's okay for Ubuntu to have it? in any case it's an advantage and an opportunity to gain market share if Ubuntu can fix something that other OS's can't see might be broken.  The limitation of a product for financial gain is that whether a task is done will always depend on whether it makes sense monetarily to fix.  This is an OS for people, by people, not for profit. We can build a better OS. 


**My Stance On Current OSs**
* I'm not a big fan of Windows, because with it, we have become the product. (Also, its current market domination was gained by entrenchment, which is lame)
* I'm not a big fan of Mac OS, because with it, and every other apple product we step further into a walled garden controlled by a single entity.
* Finally, I'm not a big fan of most desktop Linux distros, because they feel cobbled together and incomplete.
* I have yet to see an operating system that truly inspires, and I've probably felt this way since 2005. I realize this kind of makes me terrible. I accept it. 


**My Past With Linux, More Importantly, Ubuntu**
* I was a pretty die-hard fan. I gave out Ubuntu CDs, had copies of different distros for people to try out (mainly Ubuntu, Open SUSE, Fedora, Slax, Puppy), and even did some installs that breathed new life into computers that were getting dusty. I had a desktop quad booting windows 2000, XP, Open SUSE, and Ubuntu.
* What changed? I realized that with every install, one way or another I ended up at the terminal within minutes or hours of it being finished. A piece of hardware that didn't work, some failure with installing a required piece of software, other small errors here and there. If you want to see someone's eyes glaze over, open up the terminal. At this point I stopped evangelizing, I felt it wasn't ready. I told myself that the day I could install a distro and basically not need to use the terminal, then it would be ready for the average user.

**Then Why Don't I Improve It?**
* Once upon a time, the community had some toxicity to it. I recall being called a noob for not knowing how to restart my window manager; I didn't realize that was knowledge I was supposed to be born with. Back then, why support a toxic community?
* Now, the community doesn't seem toxic, but there's still denial that there's a problem. The fact that command line vs GUI became heated shows a general lack of understanding and acceptance of underlying issues that prevent Desktop Ubuntu from being a true champion in the market.  Should I help an effort that can't recognize it needs help? As much of a cocky little **** as I was in my youth coding, I recognize now I'm simply okay, maybe even good, but not some kind of God or genie. I can't make change on that scale alone, moreso with the existing divisive mentality about GUIs.

**Why Care So Much About Market Share?**
* I seem obsessed with it right? Well, that's because there's a lot at stake.  Market share is power.
* Having market share increases hardware and software support, which increases adoption, which brings about entrenchment. Entrenchment in the right hands is great for users, and in the wrong hands turns users into a product or siphons money out of their pockets needlessly.
* Market share means relative immunity to vendor lock out, which could happen through a combination of legal and hardware related shenanigans. This could leave Linux on the desktop crushed; only used by hobbyists or on virtual machines.  It could mean death to ignore low adoption in a market. 



I still feel Linux, specifically Ubuntu has insane potential in the desktop market. Linux is already the winner in server and mobile markets. Ubuntu, in my opinion, has the ability to dominate the desktop market if we want to take it there.


Please feel free to respond, even angrily if you'd like (understandable) publicly or through private messages.  I'll do my best to respond.  Also, if you have suggestions, questions, or other comments I'm open to them.  


There seem to be some pretty smart people on here, and maybe I'm all wrong about my opinions. If you think it's the case, let me know with a good supporting argument.


I also have some ideas about how some issues could be fixed, or how additional market share could be gained, but that's off topic.

---

### Post by mikodo on 2016-02-20
> **ubuntuman001 said:**
> Hmmm I think a bunch of you missed the point.
I wasn't discussing whether we should eliminate the terminal or if we should have only one distro where everything is standardized.  I was talking about in general terms, for a regular user, and sometimes even for a power user, the GUI tools available in linux are usually lacking as far as complimenting the terminal based tools. I think we get that. 

> There is nothing inherently wrong with using a GUI for anything, it is just a preference.  At the same time though, for 99% of users, a terminal shouldn't *need* to be used.  And no, just because it's "linux" or "unix-like" isn't an excuse for that.  There is no inherent excuse for someone to need the command line to perform some sort of fix on their system. Alright, that's your position. A bunch of us gave ours. 

What more do you want? For us to agree with you? Give arguments in how you are correct in your opinion?

---

### Post by uRock on 2016-02-20
Hedzer,

Hello and welcome to the forums!

I think I've been very lucky with recent installs, as I haven't had to open a terminal to do anything that can't be done through a GUI. I usually just jump in the terminal, because the tutorials I followed in the past wrote their instructions that way.

In the past I used to create screenshots and post them to help users fix things in ubuntu. I have even created a few YouTube vids. 

I know that not everything can be done in the GUI and I think it'd be great to see a simple interface for things such as editing grub, restarting services, and configuring hardwares that can't currently be done in the GUI. 

Depending on which project you want to take on, you may be able to start a thread here on UF to get it started. There'll always be push back from users who prefer to do things in the terminal, but there is the likely chance that there'll be people ready to jump in and get it rolling.

It'd be great to see more tools created and incorporated into the System Settings GUI, which to me is the equivalent to Control Panel in Windows.

---

### Post by yoshii on 2016-02-20
I am under the impression that it's not so hard for devs to create a "FRONT END" which is just barely graphical and just helps the user to choose the correct command line and actually uses the command line in the background.  On Windows, you can find some front ends for FLAC.exe or LAME.exe which are both command line programs.  The front ends just help you to implement the commands you need by having choices in plain english instead of "paramaterese".  I really don't see a problem with that approach.  

Of course Linux devs can do that too.  And it doesn't have to be overwhelmingly complex for them.  They don't need to create a GUI for every Linux distro, just maybe a few like Ubuntu (and by default it's flavors) and maybe Debian.  

A few Linux graphical interfaced programs have special settings fields where you can enter in console commands or parameters so it's not really such an abstract concept even if they aren't always as simple as front ends.

---

### Post by Hedzer on 2016-02-21
uRock, 
  I'd like to say thanks for actually taking time to read my giant response.  Your attitude is pragmatic and positive, which I greatly appreciate.  I talked to my friend (ubuntuman001) and mentioned the idea of maybe building some basic config tools.

You're right, there are tasks that have a depth to them that would make the GUI harder to use than opening up a terminal. I like to think that, even if those tasks had GUI to manage them, the average person would still likely call an IT guy to come fix the issue for them.  However, there are still plenty of things I'd like to see done with a GUI that the average person might be okay with doing.  In the end, a user decides to stay with an operating system based on its usability, which is a broad and inclusive term for everything from performance and behavior to what software you're looking to run and is it available for your OS.

I'm starting to wonder if maybe the GUI discussion is just a smaller part of a larger issue - one that maybe I can help solve if I open a thread for it here in Ubuntu Forums. We'll see, I'll have to first gauge how much time I can put towards a big cause.  In any case, thank you for the suggestion uRock, it's much appreciated.

---

### Post by kurja on 2016-02-22
> **mastablasta said:**
> 

I don't know what basic operation requires CLI and is not available via GUI. last thing I ran from CLI on desktop was phoronix test suite and it was just because it was faster copying a command.
note that I use KDE but:
File management is covered, troubleshooting is covered, bug reporting is covered, drivers install is covered, networking covered, PPA's & software install is covered by GUI, systems settings have a GUI, backups have GUI, system upgrade has GUI, system install has GUI, logs overview has GUI... so I wonder what basic system function requires a CLI?

CLI only programs do need CLI obviously. but it's the same thing in windows. and just like in windows you can run them from GUI.

One example of a "basic operation" requiring CLI I've encountered is configuring the buttons on a wacom stylus & tablet and doing that through the terminal really isn't trivial. You're on KDE, afaik you have a GUI for that too but there isn't one for vanilla Ubuntu. 

I think that for an "end user" using the CLI is not really an option, what they end up doing is either copy pasting commands they find online without really understanding what they're doing (and there be dragons) or conceding that the configuration option they wanted doesn't exist when they can't find it in system settings GUI.

---

### Post by Geoffrey_Arndt on 2016-02-22
For the casual user, additional gui based apps for system mgmt & config are a total plus.    Something like YAST (from Suse) on Ubuntu would be awesome in my view.   Perhaps wrap that level of functionality with the caveat "for experts only".etc.    

However, for non casual use - - nothing even approaches the power, speed and flexibility of the CLI.   I worked in one of the US's largest IT depts, where Linux rules all but the desktop . . . and CLI is the most common thing (besides IDE,s, Version Managers & Browsers) that you see on desktops screens all across IT.   If I, as a Project Manager or Systems Consultant where to suggest increased use of gui in that environment, well, my rep would go down the proverbial toileten with a whoosh.

EDIT:   re increased use of gui config apps in Unity . . . my perception is that Canonical views that as not worth the risk . . . .

---

### Post by user1397 on 2016-02-23
> **kurja said:**
> One example of a "basic operation" requiring CLI I've encountered is configuring the buttons on a wacom stylus & tablet and doing that through the terminal really isn't trivial. You're on KDE, afaik you have a GUI for that too but there isn't one for vanilla Ubuntu. 

I think that for an "end user" using the CLI is not really an option, what they end up doing is either copy pasting commands they find online without really understanding what they're doing (and there be dragons) or conceding that the configuration option they wanted doesn't exist when they can't find it in system settings GUI.Exactly!  I guess I haven't been on unity in a while so I find it hard to think of examples, but you're right about that one.

> **Geoffrey_Arndt said:**
> For the casual user, additional gui based apps for system mgmt & config are a total plus.    Something like YAST (from Suse) on Ubuntu would be awesome in my view.   Perhaps wrap that level of functionality with the caveat "for experts only".etc.    

However, for non casual use - - nothing even approaches the power, speed and flexibility of the CLI.   I worked in one of the US's largest IT depts, where Linux rules all but the desktop . . . and CLI is the most common thing (besides IDE,s, Version Managers & Browsers) that you see on desktops screens all across IT.   If I, as a Project Manager or Systems Consultant where to suggest increased use of gui in that environment, well, my rep would go down the proverbial toileten with a whoosh.

EDIT:   re increased use of gui config apps in Unity . . . my perception is that Canonical views that as not worth the risk . . . .Couldn't agree more.  I've thought about a Yast-like utility for ubuntu unity, it could even be split into regular user options and then power user options.

---

### Post by vasa1 on 2016-02-23
*Someone* should do *something* about it. At times it may be necessary to "[scratch one's own itch]("https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar")".

If I find a particular CLI solution cumbersome, I ask for help. I've been pointed to Zenity. I've been shown how to use functions when aliases won't work. I have keyboard shortcuts. 

I don't worry about "meta" issues such as "Is command line usage ***_really_*** better than GUI?". Life's too short.

---

### Post by user1397 on 2016-02-24
Indeed vasa1, my friend and I are actually talking about perhaps tackling this problem head on.  

I don't worry about meta issues such as that either, as that wasn't the point of this thread.  When I said "is command line usage really better than GUI?" I meant in the context of "is it always better in every case for an end user" or "should we really recommend a terminal command as the default (for certain things) for end users?"

Of course I am not arguing that the command line should be replaced by GUI only, or that the command line is dumb, or something else along those lines...

---

### Post by vasa1 on 2016-02-24
> **ubuntuman001 said:**
> Indeed vasa1, my friend and I are actually talking about perhaps tackling this problem head on.  

I don't worry about meta issues such as that either, as that wasn't the point of this thread.  When I said "is command line usage really better than GUI?" I meant in the context of whether is it always better in every case, or is there a point to it?  Then I put forth some arguments as to why for regular users, GUI tools should be standard, that's about it.  

Of course I am not arguing that the command line should be replaced by GUI only, or that the command line is dumb, or something else along those lines...

Without really knowing, I'd say that zenity or yad or Gtkdialog could be used to provide GUIs for many CLI tasks:
[http://stackoverflow.com/questions/7035/how-to-show-a-message-box-from-a-bash-script-in-linux](http://stackoverflow.com/questions/7035/how-to-show-a-message-box-from-a-bash-script-in-linux)
[http://pclosmag.com/html/Issues/201404/page12.html](http://pclosmag.com/html/Issues/201404/page12.html)
[http://forum.slitaz.org/topic/howto-write-simple-user-input-gui](http://forum.slitaz.org/topic/howto-write-simple-user-input-gui)

Anyway, in a diverse world, I'd rather not try to get opinions on 
[LIST]
[*]whether X is *really better* than Y or 
[*]whether X is *always better* in *every case* than Y or 
[*]whether something *should be* standard 
[/LIST]
If it makes any sense, it's like looking for an objective answer to a subjective question.

As I said, if I need help on some specific task, I ask for it (and mostly get it).

> **uRock said:**
> ...
Depending on which project you want to take on, you may be able to start a thread here on UF to get it started. ...
+1.

---

### Post by mikodo on 2016-02-24
> **Geoffrey_Arndt said:**
> For the casual user, additional gui based apps for system mgmt & config are a total plus.    Something like YAST (from Suse) on Ubuntu would be awesome in my view.   Perhaps wrap that level of functionality with the caveat "for experts only".etc.

> **ubuntuman001 said:**
> Couldn't agree more.  I've thought about a Yast-like utility for ubuntu unity, it could even be split into regular user options and then power user options.I don't know what YAST is but, if it could be fashioned similarly in Ubuntu to allow  for easier management of typical cli tasks, I think it sounds  promising.

> **Geoffrey_Arndt said:**
> EDIT:   re increased use of gui config apps in Unity . . . my perception  is that Canonical views that as not worth the risk . . . . Therein, "lies the rub". There are too many gui apps available that have one developer who, may or may not be supporting it. Or, it doesn't work like it should. 

> **ubuntuman001 said:**
> When I said "is command line usage really better than GUI?" I meant in the context of whether is it always better in every case, ***or is there a point to it?*** 

There is a*** very good point to it***. 

- As I said before, it is reusable. Like using it it for gui's as you are suggesting.
- It is tested and proven. It works. It is released and can be used without need of people making sure the bugs are ironed out of the gui.

One of a few personal examples I could list.

- About 3 years into using a computer, I was still struggling with how to safely backup my important data. I decided on using a gui backup app that is developed by one man that, Ubuntu wanted to support at the time. They hired him with Canonical and allowed him to develop it more "on company time". "He thanked Canonical for that in a blog". The inevitable of course happened to this noob and, I lost some data. I went into the gui app and tried to bring it back from backup. It failed. I contacted the developer on Launchpad. He was in the process of fixing the bug in the app that had caused the problem with the app causing users not being able to bring back their data. "Long story short", he eventually told me he couldn't backport the fix into the gui app to the supported Ubuntu LTS I was using. That data is lost to me. I am using cli apps for backup now as, I know that they work and are not dependent on developers/maintainers.

Now that you have surely read all that, I want you to also read my saying to you, I support you and and your friend developing more "user-friendly tools", for lack of a better reference that, comes to mind right now.

---

### Post by vasa1 on 2016-02-24
> **mikodo said:**
> I don't know what YAST is ...
Yet another setup tool: [https://en.wikipedia.org/wiki/YaST](https://en.wikipedia.org/wiki/YaST)

---

### Post by vasa1 on 2016-02-25
> **Geoffrey_Arndt said:**
> For the casual user, additional gui based apps for system mgmt & config are a total plus.    Something like YAST (from Suse) on Ubuntu would be awesome in my view. ...
Don't **most** distros come with something like that?
Even Lubuntu has an assortment of GUI-based tools.

Anyway, let's see what come of this thread.

---

### Post by user1397 on 2016-02-25
> **mikodo said:**
> There is a*** very good point to it***. Darn, I totally mis-worded (is that even a word? hehe) that sentence as well.  I guess my mind has been all over the place these last couple of days and I'm leaving half thoughts and unfinished sentences...


But yea I agree with you on all accounts.

I also took the liberty of changing the title of the thread so that it isn't so polarizing and prone to misinterpretation (I feel like my original more or less tongue-in-cheek thread title is probably the cause of most of the misinterpretation of my OP, but feel free to disagree on that too if you like :)) and also edited the OP to more accurately portray my original thoughts on the subject.

---

### Post by DuckHook on 2016-02-25
> **Hedzer said:**
> ...let me know with a good supporting argument.Hello Hedzer,

It's so nice and refreshing reading such a thoughtful, carefully reasoned&#8213;and courteous&#8213;rant. In like spirit, here is my reply rant.

**Obscurity:**

There *are* GUI tools for a tremendous number of CLI functions. They're just not installed by default and/or they are (admittedly) difficult to find. For example, arandr is a tidy little GUI for a subset of xrandr functions. So is system-config-lvm as a GUI for a subset of functionalities within the whole lvm suite of CLI apps. dconf-editor and gconf-editor are GUI editors that consolidate management of a whole zoo of scattered config files. GUFW is an excellent GUI for UFW. GRSYNC is pretty good GUI for rsync. Almost everything involving apt can be done with synaptic. And so on. Dozens&#8213;perhaps hundreds&#8213;of GUI apps already exist and do a perfectly adequate job smoothing over the basic functions of their CLI apps. However, this brings us to the next issue:

**Versatility:**

People use GUIs ostensibly because they are "more intuitive". But this phrase is so vague and premise-assuming as to be almost meaningless. When people say "more intuitive" what they really mean is that it's similar to something they already use, and&#8213;above all&#8213;that it is simple. But simple also means constraining. GUIs feel friendly because they constrain the users' choices to a few no-brainer options. You can't offer a ton of options in a "simple" interface, else it ceases to be simple. In fact, the worst GUI apps are those where you must hunt through a dog's breakfast of nested drop-down menus to turn on that one option flag that you simply must have. In such apps, it is *much easier* to invoke the option using a simple CLI command were it not for the CLI phobia that most people have trained themselves into feeling. Which leads into the next point:

**Irrational fear and resentment:**

I know about command line phobia. That's because I speak from personal experience. I'm not a programmer or administrator and had nothing to do with the command line for decades of my working life. I had gotten so used to a completely GUI world (both Windows and Mac) that, like most users, I thought it the natural order of the universe, which&#8213;in hindsight&#8213;was actually a very arrogant attitude. Yes, I'd used the DOS command line, but that's child's play compared to Linux, and I never got deeply into DOS anyway notwithstanding it's Mickey Mouse simplicity. For years, I had the same fear and&#8213;I may as well confess it&#8213;disdain for the command line that many new users bring to Linux today. But this was never due to any inherent awfulness of or evilness in the command line. If I'm honest with myself, my attitude sprang from the fact that the CLI made me feel stupid. And I resented that. So, rather than approaching the CLI with an open mind, I joined the chorus that convinced themselves that the CLI is "unintuitive", "pointless", "unnecessary" and "so yesterday".

It wasn't until, for various reasons which I won't get into (for fear of the mods shutting me down for hijacking the thread) that I forced myself to explore and eventually adopt Linux. This process also opened me to *gradually* exploring and adopting the CLI. I can't emphasize this enough: it was done in baby steps and took a long time. To this day, I can still empathize with new users who are well-nigh allergic to the CLI, because that was how I felt for the longest time.

**Sheer mad unadulterated power:**

So what changed for me? Through slow steps I discovered that not only is the CLI not my enemy, but it is, in fact the very opposite: it is a stupidly-powerful friend. It does things that are next to impossible in the GUI universe, and it does these things not only quickly and productively, but elegantly (expand more on this last point later). Permit me an example:

I use bash all the time because I'm now deeply interested in exploring the CLI. But one of the most irritating aspects of bash usage is calling up the history of prior commands. Since *every* command is recorded, the history file quickly fills with tons of duplicates (for the sake of this example, let's ignore the HISTCONTROL options for now), so the use of <CTRL>+<r> brings up a ridiculous amount of cruft before you finally find that old command after twenty invocations of <CTRL>+<r>. Therefore, my objective was to cull the history file of duplicates. But it's more complicated than merely culling duplicates: most commands also have a historical context. They make far more sense placed in relation to the commands that were used both before and after. Therefore, I did not want to cull duplicates using any *sorting* process because this would destroy the order of the history file and consequently also destroy the usage context.

In the GUI universe, solving this problem is very difficult. It would involve a long and convoluted process of many steps that would take ages to think through, set up, test, and execute. And even were such a procedure developed, it would have involved so much work, learning and unravelling of obscurity, that it would make learning the command line look like a Sunday picnic.

The GUI universe is just not set up to be malleable and versatile. Its strength is that of a carefully confined box of predetermined utility that offers just enough options to get the job done but no more. But the CLI universe is the opposite. Referring back to my example, after very little Googling and some self-education, I cobbled together this:```
awk '!x[$0]++' .bash_history > .bash_history_clean && mv .bash_history .bash_history_old && mv .bash_history_clean .bash_history && chmod g-rw .bash_history && chmod o-r .bash_history
```The important part is this:```
awk '!x[$0]++'
```...the rest of it is simply a rather clumsy way to replace the old bash history file with the lean-and-mean one generated by the *awk* command. For the general public who may happen upon this thread: what this command does is it runs through any text file and eliminates all duplicate lines but the last one. It does not need to sort them first, but keeps everything in their original order. This is done within the space of one measly command totalling 14 measly characters. The supporting code fit all on one line, and I'm sure that the real gurus on this forum could have achieved the same result even more succinctly and elegantly than I did.

The power of the command line is, frankly, mind-boggling. But it is also something more, which brings me to my last point.

[B]Aesthetics:
[/B]
The CLI is analogous to math. Like math, it isn't "natural", it isn't "intuitive", and it involves the learning of symbols, rules, a new language and, most of all, a new way of thinking that is initially intimidating, scary and foreign to our minds. But, once mastered, it opens up a whole new toolbox for solving problems and manipulating our world that is just not feasible in any other practical way.

But this only speaks to its power and its utility. However, to my sensibilities, there is an added dimension that is rarely discussed in relation to the CLI: and this is *elegance*. There is something undeniably elegant (and possibly eloquent) in cracking a nut as tough as my example in the space of 14 characters. The prospect of the dozens of mouse movements, clicks, menu invocations, and god-knows what else that would be needed in the GUI universe to achieve what was done in this one line of code is, frankly, ugly, intimidating, discouraging and depressing.

**Conclusion:**

Just as people can get by in the world without any real knowledge of math and simply leave it to the "experts", likewise, people can get by without any knowledge of the command line and leave that to the "experts" as well. And I'm not expecting everyone to become command line jockeys any more than I expect everyone to become math wizards.

But there's a world of difference between saying: "I'm no CLI jockey so I find GUI tools useful" and "There's no need for the CLI for the ordinary user". I'm not a CLI jockey. I am very much an ordinary user. Maybe an ordinary power-user, but still ordinary, in that I am nowhere close to being a guru. And yet, even my very limited grasp of the command line opens up solutions to me that would have been next to impossible in my GUI-only days. The example that I used isn't even exotic and has clear application to all sorts of everyday lists in which one wants to eliminate duplicates without changing the order of the original list.

I realize that I haven't addressed all of your points. But I've already rambled on long enough that I should stop for now.

---

### Post by montag dp on 2016-02-26
Very good post.  A lot of that is what I was trying to get across, just not nearly as clearly.  The fear and resentment aspect, and maybe we can add just plain disinterest, are the reason why many people never come to understand the power of the terminal.  But computer interfaces are really just following the same trend as much of technology: they have become so user friendly that they do almost everything for you automatically, and very few people care to delve deeper.  I don't really blame them for that, either; after all, a computer is just a tool, and as long as it does its job, there's no compelling reason to delve deeper.  That said, everyone I know who has put in the effort to become good with Linux/Unix command line tools was glad they did.

With that in mind, I do still think it is a worthy effort to improve the user friendliness of Linux by adding more GUI utilities.  The difficulty with that is maintaining them and retaining consistency, and that's very hard to do, especially for small teams that aren't already part of a distro or other major project already.

---

### Post by Geoffrey_Arndt on 2016-03-24
Wow . . . what an awesome post by DuckHook . . . . straight down the fairway . . . . no hook to it at all (e.g., no one needed to "Duck" as the ball whizzed by . . . . sorry, . . . couldn't resist!)

---

