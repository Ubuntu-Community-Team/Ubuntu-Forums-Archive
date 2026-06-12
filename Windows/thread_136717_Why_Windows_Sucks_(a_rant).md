---
title: "Why Windows Sucks (a rant)"
date: 2006-02-26
forum: Windows
---

### Post by Kerberos on 2006-02-26
It&#146;s a universally held opinion by most PC users on the planet that 'Windows Sucks'.  Most couldn't back this assertion up with concrete evidence though and most anti-Windows comments are actually blatantly wrong or refer to problems long fixed.  

Windows, from a usability point of view, has also come a long way.  When you get over the rabid Microsoft hating fervor gripping most people you&#146;ll come to realize that (although I don&#146;t know why they got a 8 year old to design the theme) its actually a very well thought out GUI and if looked at from a objective usability based point of view, you can see the time and effort that has gone in to trying to make it as easy to use as possible.  Its certainly miles ahead of the Open Source competition.

But Windows does suck, and the reason is the software.  For the uninitiated Windows software installs via an executable file (setup.exe usually) that places the main program files in the directory program files and then places a shortcut, or a folder of shortcuts in documents and settings->all users->start menu.  The installing software has complete access to all areas of the hard drive &#150; there are absolutely no limitations on what it can access and where it can put things.  The software also generally saves settings in the Windows Registry (a centralized point of failure) via Windows APIs.

Of course sometimes programs do what they want.  If some software wants to install itself in the root of c: (an incredibly bad place to put it) - its allowed.  The fact of the matter though is that programs can install themselves anywhere they want, add as many icons as they want to any place they want - and even delete anything that they want.

The problem with this is that programs think they are much more important than they actually are.  Quicktime, which isn't even the worst, and which 99% of people only have to use very occasionally watch a QuickTime file, installs a system tray stub (for settings and fast launch) a Quick-launch icon and an icon in your start menu.  Not only that it also runs an updater in the background that'll alert you when new versions of the software come out.  Its bundled with iTunes also (you don&#146;t get a choice in the matter you've got to download both) which also gives it a quick-launch icon.  I now have 3 icons taking up room on my start bar, some more on the desktop, a constantly running process (quick-launch and auto-update) and a mp3 player when all I needed was the ability to play QuickTime files.

If just one program does this it is not so bad but even things which don&#146;t even need an icon do it.  Acrobat for example puts shortcuts everywhere, features a quick-launch and auto-updater (which I will go into in a minute) yet the only time Acrobat files are actually used is either integrated into the browser (so no launch button is required) or if you open a PDF (double clicking on it opens it in acrobat).  Yet icons are everywhere.

The auto-update mentioned in the previous paragraph is a classic example of the bloatware PC's face.  Yahoo! Toolbar for Internet Explorer now automatically adds itself to the 'Critical Updates for Download' box beside the 'Security Update for Acrobat'.  You can't remove it either, you have to remove the Acrobat update (which removes Yahoo) then re-add the Acrobat Update.  The fact I have to go out of my way to separate junkware from valid security downloads is disgusting.

Yahoo Messenger also now has a nice feature whereby the 'Load this program automatically on startup' button is grayed out unless you log in with a valid Yahoo account.  So if someone installs Yahoo Messenger on your computer you can't actually stop it starting whenever you log in to Windows unless you sign up with yahoo, sign in, and then disable it.  This wasn't a feature in earlier versions either.  Skype goes one step further and simply doesn't give you the option of not starting automatically - If it *does* give you the option I couldn't find it!

Unfortunately every single bit of irrelevant software nowadays has its own autoupdater, quicklaunch, system tray and start menu icons if it actually needs it or not.  Now add RealPlayer (which is one of the worst for it), AIM, MSN, Skype, the usual collection of toolbars foisted on you, the half dozen more pointless icons added by your scanner, printer, OEM and mouse and you've got a slow booting computer with irrelevant icons repeated all over the place (and no room to view running programs) all popping up alerts, news, updates and generally getting in your way.  You have to manually delete several dozen or so icons and then try to figure out where the 'stop annoying me all the time' button is buried on each one.  It is generally buried fairly well too.

To add the icing on the cake the uninstall process is also handled by the software - Windows has pretty much nothing to do with it.  If the installer wants to leave icons everywhere, it does.  If it wants to remove key system files or leave software running in the background and not tell you about it, it can.  It can even just not work entirely leaving you no decent way of getting rid of it.  Installing things in Windows is generally a permanent move.

Most people don't even realise that it&#146;s not meant to be like this - they just think that it&#146;s the way it is and just learn to live with it.  I have no idea why software installers are given 100% free reign over your PC, but they are.  It&#146;s as big a problem as spyware and it&#146;s the main, large IT companies that are responsible.  Sun has even recently declared a public partnership with Google - probably to try and install Google Toolbar whenever you install OpenOffice or Java as MSN&#146;s toolbar (foisted on you by MSN Messenger) and Yahoo's toolbar (Critical Update by Acrobat Reader) may not empower your browser quite enough on their own.  It is misbehaving software (and installers) that are responsible for 99% of the unstable, unbootable and otherwise slow to the point of unusable Windows computers.

Windows without any untrustworthy 3rd party software is as stable as it realistically needs to be 'Windows crashes a lot' is no longer a valid insult - in fact it&#146;s a lie.  The last time I saw a BSOD (Blue Screen of Death) was when I took a modem out without shutting down the PC first (you cannot really blame Windows for that).  You will generally only see a BSOD in the event of hardware failure (not Windows fault), because of a bad device driver, (not Windows fault) or because a 3rd party piece of software has screwed the OS (partially Windows fault).

If the software install was not such a treacherous process, if programs didn't have complete reign over your PC and you could actually uninstall software without worrying about your PC actually starting next time you turn it on Windows might have a chance of being a decent OS.  Until then it sucks.

---

### Post by aysiu on 2006-02-26
Neither Windows nor Ubuntu has full control over third-party software development.

It's sad, but it's true.

I don't really have that much of a problem with Windows or Ubuntu because I just don't install that much software in either. My needs are very basic--the internet, email, some light word processing, an FTP client. I'm probably the minority that way (at least in this community).

---

### Post by K.Mandla on 2006-02-26
Nice work. It's always good to see a well thought-out opinion, written cleanly and completely.

Me, I'm just sitting around with a stack of prepressed Ubuntu CDs, waiting for the next big virus alert, so I can sit outside Wal-Mart and hand them out to all those folks running inside to buy antivirus software. 

Or all those poor Windows 98 users who have been abandoned, running in to give another $100+ to Micosoft.

It's all in the timing. :)

---

### Post by bjweeks on 2006-02-26
> Its bundled with iTunes also (you don&#8217;t get a choice in the matter you've got to download both)

Um no.

> Skype goes one step further and simply doesn't give you the option of not starting automatically - If it *does* give you the option I couldn't find it!

Yea, it does.

This rant is pointless, try if you run an installer with sudo you get the same effect. I don't have any of that shit installed on my computer and I can watch any video I want and can messange my buddys. So this again comes down to windows sucking cause the user doesn't know what there doing.

---

### Post by xequence on 2006-02-26
If someone wrote why ubuntu sucks, people would be all "TROLL, FUD-ER, NEWB, GO TO HELL".

> It&#8217;s a universally held opinion by most PC users on the planet that 'Windows Sucks'.

No, just zealots of another OS.

And all your rant is is one thing: Saying windows sucks because of what some programs can do to it.

---

### Post by DigitalDuality on 2006-02-26
Hey.. with Trusted Computing..3rd party software will be more secure and stable!!

---

### Post by Kerberos on 2006-02-26
[QUOTE=bjweeks]Um no.
Yea, it does.[/QUOTE]
[http://www.apple.com/uk/quicktime/download/win.html](http://www.apple.com/uk/quicktime/download/win.html)

QuickTime 7 with iTunes 6
for Windows 2000/XP

Um yes.  Unless there's a link they have hidden somewhere I can't find.  And you have to 'go pro' (pay) to watch QT files full screen.

---

### Post by bjweeks on 2006-02-26
[QUOTE=Kerberos][http://www.apple.com/uk/quicktime/download/win.html](http://www.apple.com/uk/quicktime/download/win.html)

QuickTime 7 with iTunes 6
for Windows 2000/XP

Um yes.  Unless there's a link they have hidden somewhere I can't find.  And you have to 'go pro' (pay) to watch QT files full screen.[/QUOTE]

[http://www.apple.com/uk/quicktime/download/standalone.html](http://www.apple.com/uk/quicktime/download/standalone.html) and it is linked on that page you just showed me! If you want to watch Qt movies fullscreen use VLC.

---

### Post by Kerberos on 2006-02-26
[QUOTE=xequence]If someone wrote why ubuntu sucks, people would be all "TROLL, FUD-ER, NEWB, GO TO HELL".[/quote]
I actually got banned for it, but nm :)

> 
No, just zealots of another OS.

And all your rant is is one thing: Saying windows sucks because of what some programs can do to it.
Damn straight!  I shouldn't have to go around cleaning up after installers simply because they can do whatever they please.  Installation should be handled by the OS **especially** in Windows case as its essentially a single user OS.  I dont want my desktop branded by Yahoo, Google etc and constantly have to put up with irritating software simply because they are trying to 'build the brand'.

---

### Post by bjweeks on 2006-02-26
[QUOTE=Kerberos]I actually got banned for it, but nm :)


Damn straight!  I shouldn't have to go around cleaning up after installers simply because they can do whatever they please.  Installation should be handled by the OS **especially** in Windows case as its essentially a single user OS.  I dont want my desktop branded by Yahoo, Google etc and constantly have to put up with irritating software simply because they are trying to 'build the brand'.[/QUOTE]

Then don't it's not windows problem that you install shit.

---

### Post by Kerberos on 2006-02-26
[QUOTE=bjweeks][http://www.apple.com/uk/quicktime/download/standalone.html](http://www.apple.com/uk/quicktime/download/standalone.html) and it is linked on that page you just showed me! If you want to watch Qt movies fullscreen use VLC.[/QUOTE]
Fortunatley I never get QT files.  And your right, its just not the most prominant of buttons (I missed it despite reading the page twice).  They try to foist crap on you though - thats why the link is text based, hidden in a corner and indistinguishable from surrounding text - all other links at least have an underline to indicate them as such.

---

### Post by bjweeks on 2006-02-26
[QUOTE=Kerberos]Fortunatley I never get QT files.  And your right, its just not the most prominant of buttons (I missed it despite reading the page twice).  They try to foist crap on you though - thats why the link is text based, hidden in a corner and indistinguishable from surrounding text - all other links at least have an underline to indicate them as such.[/QUOTE]

Ya, apple wants you to install there apps so?

---

### Post by KiwiNZ on 2006-02-26
Enough of the "Windows suck" threads already.Sheesh:rolleyes:

But I will put this to the backyard at least

---

### Post by Alpha_toxic on 2006-02-26
Yep, you're right... I just love programs that run from exe's without installers (µTorrent for example).
On other hand things like auto-starters running in background etc. are not so bad, some people actually need them. But leaving them ON by default - brrrrrr.

P.S. about Skype: There should be an option to make stop it loading at win startup (mine doesn't), I just can't seem to find it... Ah, here it is. Just log-out (without stopping Skype) and log-in again. It's at the log-in dialog (a really weird place eto put it) .

---

### Post by Kerberos on 2006-02-26
[QUOTE=KiwiNZ]Enough of the "Windows suck" threads already.Sheesh:rolleyes:

But I will put this to the backyard at least[/QUOTE]
I would say its more 'tongue in cheek' sucks rather than a pointless 'Windows BSOD lolzorz' post.  I tend to be the one pointing out flaws in Linux  I just posted this so people would see that I'm not just a trolling Windows fanboy.

P.S. rogue installers are the reason Windows is so unstable and crash prone, rather than the OS itself.  I reckon the post was fairly well written.  oh well...

---

### Post by mstlyevil on 2006-02-26
One thing most Windows users do not know is there is a way to turn off all those system tray icons, updaters and background programs. It is called msconfig. All you have to do after installing all that crap is go to Start-->Run and type in msconfig. Then you go to the startup tab. You just uncheck all those programs but your firewall and antivirus then reboot. Upon reboot you get a dialog box that you just put a check in the checkmark and close and then all those programs will no longer be running. If you use Quicktime it has a way of adding a new entry everytime you use it so you have to repeat this everytime you use Quicktime. I refuse to use Quicktime for this very reason since Apple does not respect my wish to not have it's processes running in the background.

I guess what I am trying to say is if you know how you still have the ability for all that junk not to run without searching for how to turn it off in the program.

---

### Post by fuscia on 2006-02-26
[quote=kerberos]It’s a universally held opinion by most PC users on the planet that 'Windows Sucks'.[/quote]

i have no clue where you got this idea. most pc users have never heard of anything but windows and, if they can get what they want done on their pcs, they think it's great. my guess is that most pc users are end users and don't share our fascination for these lovely little creatures (i guess i'm a rare end user). the last thing they want to think about is how to install something. because of this, software companies can take advantage of the end user's "i don't care. just make it work" mentality and take over the user's pc. for most users, the annoyances of instrusive software are still less than those of tv commercials.

---

### Post by prizrak on 2006-03-03
I do agree with  this rant. I think the only problem here is the registry and the lax way in which Windows handles it's stuff. It is definetly a non issue on Linux because software installs into predictable folders and puts is easy to manually clean out if needed. In Windows alot of stuff is hidden and there is the added problem of DLL hell where your programs just rewrite the libraries with their own version that may very well be incompatible with others. In Linux that issue doesn't exist because the libraries don't normally come with the software. The ones that do go into their own directories, something Windows software vendors are FINALLY starting to do, however that defeats the point of the DLL model creating the slowdowns and instabilities.

---

### Post by jmullagh on 2006-03-03
Funny thing as I read through many posts... this Anti-Microsoft culture. First, I have been into computers since 1986 and 'surfing' the net meant the use of Veronica and Archie! Hate to say it but Microsoft did change that. Sure, there were others but Microsoft, at the time, was a very small company fighting for its life against what was then the bad boy of computers...IBM. They did it with the introduction of MS DOS 5.0 and then later layered Windows 3.1 on top of DOS 5.5 creating a GUI environment which made it easy to use than DOS and all of a sudden... IBM was history in the software arena...  

The thing I find funny is this.... why does everybody compare Linux to Windows?
Instead, you should compare Linux to what it is you are trying to accomplish. Case in point... if you wish to talk about stability of an operating system, then you should be discussing Linux vs Unix. Unix...to this day... is the absolute most reliable operating system known. If you wish to embark upon graphics, then compare Linux to Mac. It is well known that Mac is the superior graphics OS... but you don't have to take my word on it, simply go into any graphic artists studio and...hmmmm... there it is...Mac. I believe that these two areas are the most important for most users today....

Windows can ONLY be compared in one area and one area only... popularity! PERIOD.... 

So, can we stop doing a great dis-service to Linux and the Linux community by comparing it to Windows and instead, build the best operating system ever.... by comparing it to the best! The popularity will follow!

---

### Post by Mr_J_ on 2006-03-04
True that most of your reasoning makes sense up to a point, but not after it...
Windows can't suck without lips.
The users usually suck the most of it due to lack of knowledge of what they are using.

The fact the installers were given such large reigns is bad and it is very valid point.
It has been my wish that the "Add & Remove Programs" would be given a more synaptic kind of control.
Reading the instalation files from the cds or pre-packaged bundles of software in whatever form, and installing them with windows having the control.

The largest reason windows sucks is that the users are trying to do things without the propper knowledge of what they are doing. Also... Lazy system administrators that give the end-user administrative privilieges.

This is the case with almost all computers built in stores or otherwise.
The scheme is poorly done and it's the assumption the user being handed the computer has enough knowledge to control a computer... Or just plain lazyness of the installing I.T. professional.

Getting a computer is like having an "autistic genius". The little dude isn't very friendly unless you know what you are doing.

---

### Post by aysiu on 2006-03-04
[QUOTE=jmullagh]
The thing I find funny is this.... why does everybody compare Linux to Windows?[/QUOTE] I think people compare the two because most Linux migrants (failed or successful) are ex-Windows users or current Windows users dual-booting.

Even though Linux may not be a substitute for Windows, it is an alternative to Windows, and by virtue of being an alternative, it's often compared to Windows.

Why is that funny? I think it makes perfect sense.

I used to use Windows full-time.
Now I use Linux full-time.
Why, then, would I not compare the two?

---

### Post by prizrak on 2006-03-04
> Funny thing as I read through many posts... this Anti-Microsoft culture. First, I have been into computers since 1986 and 'surfing' the net meant the use of Veronica and Archie! Hate to say it but Microsoft did change that. Sure, there were others but Microsoft, at the time, was a very small company fighting for its life against what was then the bad boy of computers...IBM. They did it with the introduction of MS DOS 5.0 and then later layered Windows 3.1 on top of DOS 5.5 creating a GUI environment which made it easy to use than DOS and all of a sudden... IBM was history in the software arena...]
And of course Apple never existed? 
> If you wish to embark upon graphics, then compare Linux to Mac. It is well known that Mac is the superior graphics OS...
I suggest you google for Irix, that is the superior graphics OS. Also ALOT of graphics shops use Linux. Pixar is the most known of these. 
> Windows can ONLY be compared in one area and one area only... popularity! PERIOD....

Windows is a desktop OS ergo it can be compared to other desktop OS's. OS X, OS/2 Warp, various Linux flavors.

---

### Post by jmullagh on 2006-03-04
Well... the point is, I for one am NOT going to put down the Linux operating system by comparing it to an inferior operating system. If you wish to continue this dis-service .... what can I tell you!

BTW: What is a Mac? ohhhh ...yeah... its an Apple..... how about that!

As far as Pixar is concerned, I suggest you find out for yourself who its founder is....

One last note...Windows is NOT an operating system in the true sense of the word. It is still layered upon DOS and as such, for those of us that have been around a while know better....


Now I know why some compare Linux to Windows......

---

### Post by prizrak on 2006-03-05
[QUOTE=jmullagh]Well... the point is, I for one am NOT going to put down the Linux operating system by comparing it to an inferior operating system. If you wish to continue this dis-service .... what can I tell you!

BTW: What is a Mac? ohhhh ...yeah... its an Apple..... how about that!

As far as Pixar is concerned, I suggest you find out for yourself who its founder is....

One last note...Windows is NOT an operating system in the true sense of the word. It is still layered upon DOS and as such, for those of us that have been around a while know better....


Now I know why some compare Linux to Windows......[/QUOTE]
It matters very little who founded Pixar the point is their renderfarms run Linux not OS X. Windows is an OS. The NT family (NT, 2K, XP) has not a thing to do with DOS. DOS was also an OS btw..... 
Windows is an inferior OS? Can you please list the hard facts based on modern reality to prove your point? There is a number of things Windows does better than Linux and vice versa. Between the big three there is really not one that is clearly superior, and like I said products are compared in their respective markets which is why comparing Windows, OS X and some Linux flavors is completely fair.

---

### Post by napnip on 2006-03-05
[QUOTE=prizrak] The NT family (NT, 2K, XP) has not a thing to do with DOS. [/QUOTE]

That is correct.  NT/2K/XP/Vista do not have DOS in them at all.  They emulate DOS, but do not actually have DOS in them, which is why they are so much more stable than the 9x family.

In fact, DOS is one of the reasons why 9x was so unstable at times.  DOS was not a multitasking OS by nature.  When doing only one thing at a time, DOS was/is rock solid.  But introducing pseudo-multitasking to it crippled its stability, in addition to the fact that a 32-bit GUI was put on top of a 16-bit OS.

At this point one might be inclined to curse Microsoft for doing something like that.  Granted, it didn't make for a very stable product, but the fact that it ** did ** run, and at times run relatively well (98SE) gives reason to pause and consider that Microsoft accomplished a software engineering miracle.  Instead of cursing Microsoft, one should actually praise its engineers and programmers for being able to get such a concoction to actually work!

As for the NT-family, I've got very little to complain about as far as stability goes.  NT was leaps-and-bounds better than 9x, and 2K was leaps-and-bounds better than NT.  In my experience, XP and 2K are about equal in terms of stability.  If you want an NT-based OS to be stable, start with good quality hardware, and couple that with good quality official drivers.

---

### Post by Kerberos on 2006-03-06
Wow.  I thought this was where threads went to die!
[QUOTE=jmullagh]Well... the point is, I for one am NOT going to put down the Linux operating system by comparing it to an inferior operating system. If you wish to continue this dis-service .... what can I tell you!

BTW: What is a Mac? ohhhh ...yeah... its an Apple..... how about that!

As far as Pixar is concerned, I suggest you find out for yourself who its founder is....

One last note...Windows is NOT an operating system in the true sense of the word. It is still layered upon DOS and as such, for those of us that have been around a while know better....

Now I know why some compare Linux to Windows......[/QUOTE]
Stop reading and believing all the anti-Windows FUD posts on Slashdot* and develop some of your own opinions for a change.  If you want to say it sucks, like I did, back it up with an argument based on points, not just some vague allusions to it being 'inferior'.  Why not throw in a 'chair throwing' joke and maybe a 'Windows is based on DOS lolzorz**' comment to keep it fresh & further back up your succinct points?

** I dont really read SD anymore as it's just BSOD jokes and chair throwing jokes by bitter Linux zealots, which lose their humour and freshness on the 1,356 use.  Its over a **decade** since Win95 was released - jokes mocking it just aren't funny anymore.*

*** Its funny how much criticism Windows gets for being based on DOS (which is simply just a CLI) while Linux is based on, or at least entirely centred around, a CLI.*

---

### Post by xequence on 2006-03-08
> One last note...Windows is NOT an operating system in the true sense of the word. It is still layered upon DOS and as such, for those of us that have been around a while know better....

Obviously you are a little behind the times.

Windows hasnt been based on DOS in what... 5 years?

---

### Post by jayres on 2006-04-08
I agree with the annoyance caused by installation programs doing what they want. But in my opinion that is not why windows sucks. It's because the company has an agenda to guide users and programmers to their way (and consequently continuing their monopoly). When you look in help provided by the Linux community you get help from people who are trying to help you figure out what your problem is and how to fix it so that you can continue with what you are working on. When you go to help in windows you have to wade thru the bull of whatever their next big thing that they are pushing. Your need for help is used as a method to 'educate' you about what they want you to be doing. This is propaganda not help and it sucks.
There are other ways that this monopolistic venue plays out that are not in the interest of users. But instead, I want to thank every member of the open software community for the help in recovering from  windows problems.
Thank You

---

### Post by kh4nh on 2006-04-08
95% of computers on the planet are running Windows. Sadly the 5% left are running Linux or Mac

Instead of speding time on saying why Windows sucks, why not do something to make those numbers switched around. I am tired of hearing complaints about the Windows from some of the Mac and Linux users. If you are happy with your Linux (or Mac), good for you. Just let the other OS be.

---

### Post by prizrak on 2006-04-08
[QUOTE=kh4nh]95% of computers on the planet are running Windows. Sadly the 5% left are running Linux or Mac

Instead of speding time on saying why Windows sucks, why not do something to make those numbers switched around. I am tired of hearing complaints about the Windows from some of the Mac and Linux users. If you are happy with your Linux (or Mac), good for you. Just let the other OS be.[/QUOTE]
Since when do 95% of computers on the planet run Windows? 95% of DESKTOPS are estimated to run Windows, not computers. Windows share on the server side of things is less that 50% (49) and there are plenty of hardware that Windows would not run on at all, i.e. SPARCs, SGI stations, Beowulf, big iron, the list goes on.

---

### Post by macgig on 2006-07-10
always does my heart good to see some good ole micro$oft bashing. :)

windows xp stinks. the xp box at work freezes/crashes all the time. brand new dell pc. LOL

w00t. 

I see only ONE problem with pc's... Windows. enuf said. ;)

---

### Post by aysiu on 2006-07-10
My XP at work rarely freezes or crashes.
I think Windows XP is a decent OS. I just prefer Ubuntu.

---

### Post by someusernoob on 2006-07-11
I actually never had any probs with XP too. Never had a virus or spyware. Had a BSOD once, but that was because i bought a new grapchics card, and whatever i did, it wouldnt install properly without Windows being reinstalled. I didnt install lots of junk software either. Kept it clean with clean apps, most of them even beta's, but it wouldnt crash.

The thing that made me actually go away from Windows is this genuine and license stuff. Bought a preinstalled computer, but the motherboard broke down and had to buy another one, and the license said that i had to buy a new license. The price is acceptible, but its really a turn down when youre not expecting it. Then there was this genuine stuff that really made me tired. I really had some troubles with it, even when i owned a licensed copy of XP.

It even got worse (and im not trying to bash or anything here) when i installed the Vista beta. Besides it slowed down my computer (which would mean i have to buy a new one to use Vista as fast as i used XP) i had to find out that the security issues were still there. And without any nasty spyware applications i got slammed around the ears with popups. You first have to click a couple of popups away even before the installation of an application starts. Since "click-click-click" is the most common way to get spyware installed, i dont think Windows giving some "click-click-click" popups first will help making it safer for people. And im getting pretty tired of it.

That is when Linux became a real alternative for me. Have tried it in the past, but i always had to go back to Windows for some applications. And as far as i've seen now, i dont have to anymore. Ubuntu is complete for me (yes, for ME). And im happy with it.

Windows doesnt suck, Linux doesnt suck.
Windows was great for me in the past, Linux is great for me now, and possibly it will be in the future.

---

### Post by viraptor on 2006-07-11
Ok. My list of "teh suck / fail" in windows:
1. shares / windows networking:
 - 2 min. for system to notice a named computer in network, when it's got static wins ip given... it's not impressive at all...
 - Why? Just why? People on cross cables / mini-lans can use ips and some decent protocol (webdav? ftp? scp?). People on large lans have smb blocked at routers. People on internet don't use it at all. Companies map shares statically / on login to hd letters. I have 2 networks with at least 2 XP boxes at a time fighting for local browser status... with each other... both have static wins given and it is local master... they know about it - I've got captures of net trafic and it's just nonsense... So why is ms network still a standard with no real alternative?

2. Hardware change (think motherboard, not disk...) == reinstall typically. Just great :)

3. Services... to get a VPN you have to enable Telephone... any questions? I know that pptp can have something in common with ppp, but isn't every vpn depending on ppp silly? (based on W2k - don't know about xp / whatever) Other than that - windows services are great - think about init monitoring daemon status and doing certain action if it's down for some unknown reason... In Windows it's really done at system level.

4. IE... Update running from browser... Isn't that just funny?

5. XP install or XP update... in normal language - install overwriting your last system first time, or install w98 every next time. It's great, that you can choose. (no - local shops don't offer the great box with both and there is no volume licence for 1 computer :) )

That said - I'm still running w2k as a secondary - just to play games (nfs only, fortunately q3 works on linux :) ) and develop .net (yes, yes - I use Mono too, but not always). I'm more eager to see [Singularity]("http://research.microsoft.com/os/singularity/") (think VM based system with high process abstraction / isolation, system gc  heap and stuff) than Vista.
For personal use - prefering ubuntu.

---

### Post by TeeAhr1 on 2006-07-13
> **someusernoob said:**
> It even got worse (and im not trying to bash or anything here) when i installed the Vista beta. Besides it slowed down my computer (which would mean i have to buy a new one to use Vista as fast as i used XP)...*snip*
Agreed.  The look of awe on my roommate's face when I installed Dapper, and it actually ran *faster* on the same hardware than Breezy did... :D

---

### Post by simukas on 2006-08-19
i say that acctually windows rocks. you just say that everyone needs to buy buy buy buy. But hey don't you cn get everything for free exect the windows. And you could play more free games do more free stuff than in linux. So why are you complaining.

---

### Post by bjweeks on 2006-08-19
> **simukas said:**
> i say that acctually windows rocks. you just say that everyone needs to buy buy buy buy. But hey don't you cn get everything for free exect the windows. And you could play more free games do more free stuff than in linux. So why are you complaining.

Way to dig up a really old thread.

---

### Post by EdThaSlayer on 2006-10-30
Its your fault for installing the software...but...you are right about the installing icons and shortcuts everywhere! In linux they dont so not a lot changes!When you install a application, in GNOME it is placed in a nice menu called Applications which has many interesting submenus!

---

### Post by Reshin on 2006-10-30
> **EdThaSlayer said:**
> Its your fault for installing the software...but...you are right about the installing icons and shortcuts everywhere! In linux they dont so not a lot changes!When you install a application, in GNOME it is placed in a nice menu called Applications which has many interesting submenus!

Only IF it comes with a menu entry by default

---

### Post by prizrak on 2006-10-30
> **Reshin said:**
> Only IF it comes with a menu entry by default

Yes that is an issue and a pretty big one unless you know what you are doing.

---

