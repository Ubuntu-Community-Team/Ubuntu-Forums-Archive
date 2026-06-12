---
title: "Include Wine by default?"
date: 2013-07-15
forum: Ubuntu, Linux and OS Chat
---

### Post by King Dude on 2013-07-15
I feel that enough people use Wine to where it's appropriate to include it by default in the Ubuntu OS. It may add some bloat for users who will never use Wine, but it's only about 60MB and would simplify things enough for new users just switching over from Windows. Canonical can also streamline the Ubuntu version so that it blends in seamlessly.

It's just a thought, but I'm curious on what everyone else's thoughts and arguments are.

---

### Post by Werne on 2013-07-15
> **King Dude said:**
> it's only about 60MB
Hah, that's cute. Only the downloaded packages, once extracted, take up 60MB, once the default wineprefix is created (~/.wine) it takes up 370MB in my home directory plus the 60MB you already mentioned (on Ubuntu 12.04).

Ubuntu is over-bloated as is (as far as I've seen, the newer it gets, the more bloated it is), and I don't need another 400MB of it. Not to mention Wine is a pain in the rear to remove completely, no matter how much of it I remove I still find small fragments of it occasionally.

---

### Post by The Spectre on 2013-07-15
I personally would not want Wine Pre-installed in Ubuntu.

Too many programs do not work in Wine correctly or at all, especially newer versions and would probably cause even more frustrations to a new user.

When I first switched over to Ubuntu I played around with Wine and I did like what it was able to do but I did not like the idea of running Windows only programs in Ubuntu plus it ads the potential of a Windows Virus infection. 
Granted if it did happen it should be isolated only to the Wine environment.

So I made a choice to find the Linux/Ubuntu alternatives and learn how to use them.

The program that I missed the most was Photoshop Elements but the more that I used Gimp and learned how to use it and got comfortable with it then I had no more need for Photoshop Elements.

The only other program that I miss that doesn't appear to have a Linux/Ubuntu alternative is vReveal.
[http://www.vreveal.com/](http://www.vreveal.com/)
And if I need to use it I just boot up Windows in VirtualBox and run vReveal that way.

This site is pretty handy for finding Linux Alternative programs.
[http://alternativeto.net/?platform=linux](http://alternativeto.net/?platform=linux)

---

### Post by Copper Bezel on 2013-07-15
Yeah, that's my feeling, too. It's a neat utility when it's really necessary, but it's not at all consistent enough to be a part of the default experience, and including it wouldn't be much a show of good faith for Linux software in general. Much better to offer the native applications than to offer the framework for buggy implementation of Windows apps. Much better to offer no Windows compatibility by default than something that gets users halfway there.

Or, the simpler explanation: Getting Wine to work takes far more geekery and knowledge of Linux than finding out about it and installing it does, so it doesn't make sense to offer it to new users and, again, get them halfway there.

---

### Post by dejavue on 2013-07-15
If I was new to Linux / Ubuntu and got a program pre-installed with my distro, I would want that program to be functioning properly. As this is not the case for all things WINE, it should not be included. 
Why even bother? Installation takes a couple seconds with PlayOnLinux.

What would be nice (especially for newer users) is a preinstalled list of useful tools to install at everyone's own risk --> that could include WINE among others. Could also give installing instructions...

---

### Post by grahammechanical on 2013-07-15
A larger ISO image would affect those who have a slow download data rate and a small download allowance from the ISP. There once was a time when Gimp was included in the ISO image. Wine would not be included for the same reasons Gimp was dropped. A determination to limit the size of the ISO image.

---

### Post by mastablasta on 2013-07-15
and then the size increased to 900 something MB :-P

anyway play on linux is easy to use, but it doesn't seem to integrate the programme propperly. bets thing to use is opensource alternative though sometimes there are programmes that don't have an alternative.

---

### Post by Copper Bezel on 2013-07-15
Psst. *Programmes *are things on the radio. *Programs *&#8203;are things on computers. = )

---

### Post by 3rdalbum on 2013-07-15
If it is preinstalled, people will think "Oh, I can run all my programs in it" and then be resentful when most of them don't work.

We don't want to send the message that Ubuntu is just an inferior Windows. We want to portray confidence in our platform to be a good platform on its own terms.

---

### Post by monkeybrain2012 on 2013-07-15
Even if it works perfectly I wouldn't want it preinstalled. Linux distros in addition to making the OS should be promoting free software which runs natively in Linux. Wine should only be a last resort. New users coming from Windows are more comfortable with programs that they are used to which are not necessarily better.  I have seen many threads where new users inquire about how to run utorrent in Wine while there are many excellent torrent clients native in Linux which they don't even bother to look into. What is the point of using Linux if you still use the same Windows programs?If Wine runs perfectly many Linux programs will not be even given a chance by users who switched from Windows and don't want to venture out their comfort zone.

 WIne should not be preinstalled if it doesn't work well, if it works too well then it is a disincentive for new users to explore native Linux programs, thereby undermining the full Linux experience. 
Either way it shouldn't come preinstalled by the distro.Users who need it as a last resort can always install it themselves easily.

---

### Post by Cheesemill on 2013-07-15
Definitely not.

If you are using Linux then you should try and only use native Linux programs. On the rare occaasion I do have to use MS Word then I fire up a VM as this way I know that there will be none of the issues that can arise running programs under Wine.

Also with more and more games being released for Linux I can only see the popularity of Wine decreasing in the future.

---

### Post by Cheesemill on 2013-07-15
Definitely not.

If you are using Linux then you should try and only use native Linux programs. On the rare occaasion I do have to use MS Word then I fire up a VM as this way I know that there will be none of the issues that can arise running programs under Wine.

Also with more and more games being released for Linux I can only see the popularity of Wine decreasing in the future.

---

### Post by monkeybrain2012 on 2013-07-15
> **Cheesemill said:**
> Definitely not.

If you are using Linux then you should try and only use native Linux programs. On the rare occaasion I do have to use MS Word then I fire up a VM as this way I know that there will be none of the issues that can arise running programs under Wine.
.

Actually, if something runs in Wine then it is usually better to run it is wine than VM because it is a lot faster and offers a more consistent experience. For example, I have installed Winbugs in Wine and made it work in R. I want to compare it with jags. I don't know how it is possible to call it in my native installation of R  if I install winbugs in VM, --and I probably wouldn't even bother anyway if I can only install it in VM, as jags is just as good, I play with winbugs mostly out of curiosity. Then I have pdf-xchange viewer in wine because once in a while I may need to fill a form with scripts and none of the native Linux pdf apps seem able to do it(unless I pay $100 for pdf studio) and I just need to install cups-pdf and it prints to my home, it works pretty seamlessly. It will take a lot longer just to get VM to start and boot Windows.

So WIne has its place as long as there are Windows software that one wants to use, but as I said, it should ideally only be used as a last resort.

---

### Post by mips on 2013-07-15
No!

---

### Post by Warren Hill on 2013-07-15
Why would we want to encourage people to change the OS to Ubuntu, or any Linux, then use Windows software?

Wine has it's place but only where suitable native Linux software does not exist.  No we should not have Wine installed by default.

---

### Post by snowpine on 2013-07-15
That would be like selling Coke with a coupon for Pepsi inside...

---

### Post by Warren Hill on 2013-07-15
> **snowpine said:**
> That would be like selling Coke with a coupon for Pepsi inside...

+1 well said

---

### Post by Copper Bezel on 2013-07-15
> **monkeybrain2012 said:**
>  Then I have pdf-xchange viewer in wine because once in a while I may need to fill a form with scripts and none of the native Linux pdf apps seem able to do it(unless I pay $100 for pdf studio) and I just need to install cups-pdf and it prints to my home, it works pretty seamlessly.
This. I would not need Wine in any form if not for PDFX-Change. I actually prefer it to PDF Studio, since it at least supports opening files by drag-and-drop. I prefer that anyway, but I just don't know what to do with the little non-Gnome file browsers that come up when I hit Open in KDE and Wine apps. (The hell is my recent files? Argleblah.)

---

### Post by 1clue on 2013-07-15
Please don't.

I've never been happy with wine, on the few times I needed some sort of Windows app.  A VM works much better, and frankly with modern hardware it's almost the same speed as it would be without virtualization, unless it's some sort of game.

And before you say it, putting a virtualization engine on by default makes no sense either, what if the *Buntu is being installed inside a VM?

---

### Post by mastablasta on 2013-07-16
> **Copper Bezel said:**
> Psst. *Programmes *are things on the radio. *Programs *&#8203;are things on computers. = )

well... we learn something new every day.

we don't have many double letters in my langauge. :(

---

### Post by Z80A on 2013-07-16
Well, if Wine performance/functionality had been up to the expectations of the average user, this could be a good selling point; migrate to Ubuntu - you can still use your favorite Windows software, if you cannot find an equally good native Linux software. Compatibility on data and, to the extend needed, software is important to new users leaving Windows behind. A remark like "*...If you are using Linux then you should try and only use native Linux programs...*" may scare off new users - this is not religion... ;)

Wine should maybe not be included on the "CD" (mostly not a relevant medium anymore), but during the installation users could be asked if they want to have Wine compatibility installed - just like MP3 support...

---

### Post by PaulW2U on 2013-07-16
> **Z80A said:**
> Wine should maybe not be included on the "CD" (mostly not a relevant medium anymore), but during the installation users could be asked if they want to have Wine compatibility installed - just like MP3 support...

Up until this point I think everyone was in agreement by saying that Wine should not be included in the default installation. Your suggestion would still give new users a frustrating experience.

I haven't used wine for quit a while now but two of the programs that I would like to work properly under Wine don't and their authors have no intention of getting them to work properly either. Why should they? They write Windows software.

The authors of Wine can't get every item of Windows software working properly, there's simply too much of it. A definite **no** from me.

---

### Post by Z80A on 2013-07-16
I agree with you 100% on doing everything to avoid any frustration to new users and I did start my posting this way:

> **Z80A said:**
> Well, if Wine performance/functionality had been up  to the expectations of the average user...

I have had mixed results with Wine. I try to go with native Linux software (no MS Office, etc.), but some games and educational software for kids has only been partially successful.

However, my [PortableApps]("http://portableapps.com") (all Windows) on my USB stick all seem to work and integrate well - quite useful going back and forth between OS'es...

---

### Post by monkeybrain2012 on 2013-07-16
> **Z80A said:**
> Well, if Wine performance/functionality had been up to the expectations of the average user, this could be a good selling point; migrate to Ubuntu - you can still use your favorite Windows software, if you cannot find an equally good native Linux software. ...

If you want to use Windows software why not just stay with Windows? As snowpine puts it, it is like putting a pepsi coupon in coke. Wine should not be a selling point, only a last resort.

---

### Post by Z80A on 2013-07-16
No, the Pepsi/Coke analogy does not work, and it is not a black and white thing. For many reasons existing Windows users may want to move on to Ubuntu (openness, "karma", whatever), but uncertainty stops them. Many alternative applications exist in the Linux ecosystem, often free/open source, but to some users, lacking the ability to run a specific Windows applications, may prevent them from migrating. Could be a small thing like a genealogy software or other specialized software with which they feel comfortable.

If there is a workaround on this (Wine), why not let Windows users joins us? I fail to see Wine as being something evil and threatening to Linux; it is a a "last resort" but highly relevant. Likewise, it's not like we categorically reject people using MP3, because it is not an open format - we have a sort of a "workaround" for this.

Anyway, I hope Wine will improve and that it may be easily accessible and help new users on Ubuntu.

---

### Post by mastablasta on 2013-07-16
ofcourse. and that is why wine is in the repositories.

---

### Post by snowpine on 2013-07-16
> **mastablasta said:**
> ofcourse. and that is why wine is in the repositories.

+1, Linux is all about choice. :)

---

### Post by Bucky Ball on 2013-07-16
Wine by default??? EEEEEK! What a horrible idea. I haven't used it, ever, and would not want all that dross on a clean install.

No idea how you would deduce that there are enough people using it to warrant it being included by default. If someone wants to use Windows apps that bad why the heck would they install Linux??? Why not stick with Windows or dual-boot?

---

### Post by mr john on 2013-07-16
I think it should be an option at installation time, with a very strong disclaimer that not all windows applications work with it.

---

### Post by 1clue on 2013-07-16
There are lots of options for getting software to work.  I think most of them are ignored by almost everyone.  I only have one Linux installation that has anything windows-related on it, and that's KVM running virtual machines.  Everything else, I want nothing windows-related on it.

Crossover Office is a valid alternative if you don't want to run a VM.  Tell them what you want to work, pay them money and they'll make it work for you.  It's not a matter of impossibility, it's a matter of how much licensed software they can include in their product.

Wine is exactly where it should be.  It's in the repositories, and if you want it you can install it for free.

---

### Post by Copper Bezel on 2013-07-16
Crossover Office was an immense disappointment. They handle all the settings to make Office install and run properly, but not the font smoothing. Office under Wine can be made to look a damned sight better, though the hours of status bars and terminal commands and dialogue windows kvetching at me were not exactly worth the trouble, particularly when it didn't work the second time. (Would not purchase again.)

[COLOR=#000000][quote=Bucky Ball]If someone wants to use Windows apps that bad why the heck would they install Linux??? Why not stick with Windows or dual-boot?[/quote]
[/COLOR]Use case: Alice wants to concatenate a handful of PDFs and mark them up with printable comments. Alice likes simple, lightweight tools that do one thing well, and she likes working from a file browser and using drag and drop to keep her files organized. Alice finds that the best tools for her workflow are PDFX-Change and PDF Shuffler, but she needs them available on the same desktop.

Use case: Bob is a student whose instructors often require him to use .docx formats for project submissions. However, he's in the humanities, and finicky as hell. He finds that researching under Windows is like practicing interpretive dance in the Wal-Mart automotive section; plus, it's really irritating to keep track of all those browser windows without multiple workspaces. After composing a document in LibreOffice, he has to load the file into MS Office, correct the formatting glitches (sometimes requiring pasting the text into a new document to remove hidden, screwed-up markup) and re-save the file. To do *that, *he has to reboot his computer into Windows. He's feeling safe and warm back on his Linux desktop when he realizes that he's misattributed one of his sources, and the project is due in five minutes. 

Are not we all Alice? Are not we all Bob? ... No? Then let's just accept that some things work for some folks and others work for others. = )

---

### Post by 1clue on 2013-07-16
Use case:  Alice and Bob both recognize that dual boot is the non-solution it is, and install KVM.  Their Windows VM starts when they boot the Linux box, they have it available at any time without sacrificing their access to Ubuntu.

Later Bob hears about Xubuntu and Alice hears about Kubuntu.  They want to try it, but don't want to mess up their main workstation.  No problem, they each create a new VM with virt-manager, fire it up and install it in the background while working on their next paper.

---

### Post by monkeybrain2012 on 2013-07-16
> **1clue said:**
> Use case:  Alice and Bob both recognize that dual boot is the non-solution it is, and install KVM.  Their Windows VM starts when they boot the Linux box, they have it available at any time without sacrificing their access to Ubuntu.
.

You are missing the point. The place of WIne is not just to run windows software, it is to be able run windows software IN LINUX WITHOUT HAVING TO GO THROUGH WINDOWS, so that such software can be made to work in Linux as a part of an overall work flow and even integrate with other Linux software . E.g I use Winbugs sometimes in R (it is not necessary, there is native linux solution  called jags, but I would like to compare the outputs) , sure you can run it in a VM but then I would need to install a copy of R in VM as well. Why would I want to do that?   Second example, lmms-vst needs wine to run even though it is a part of lmms which you install with sudo apt-get. Then it is certainly a lot more convenient to run pdf-xchange in WINE in Copper Bezel's scenarios than to have to access VB through a shared folder.

Why would I want a vm to be running in the background at all time to drain my resources when all I need is performing some one off tasks now and then? Not all of us have 16G of ram running on quard core. Also setting up a Windows VM requires WIndows, that means paying MS for a license unless you get a pirated copy.It makes no sense to pay for Windows and  spend the time to maintain it (running Windows updates, installing and updating AVS' etc) just so that I can use a few small Windows freeware occasionally.

It seems that those who think that VM renders Wine pointless are heavy Windows users who use VM to replace dual booting. But I think Wine's main use is for people who only use a few pieces of Windows software as a last resort and otherwise have no need for anything Windows, let alone a full blown Windows OS on their machines.

So Wine definitely has its place, even though I don't think it should be installed by default.

---

### Post by 1clue on 2013-07-16
@monkeybrain2012,

No I'm not missing the point.  Copper Bezel was suggesting dual boot.  Dual boot is useless IMO if for no other reason than that you can't access both operating systems at the same time.  There are few if any situations where this is a happy solution.  You inevitably run one or the other most of the time, and try to find another solution to prevent rebooting to switch operating systems.  In my opinion, dual boot is what people use when they haven't fully thought the problem through.  Dual boot is the sole purpose for my previous post.

Your situation is probably a small minority of what people try to use Wine for.  Most people I see discussing it on the forum, including the OP, are trying to get a full app working, or several apps, or want it available as a generic solution for all of their Linux learning curve pains.  The way you explain it is the only way that makes sense, and if that were all anyone tried to use it for it would be fine for me.

Personally, I have one or more VMs running constantly anyway.  I'm messing with FreeNAS (freebsd) and have another Linux install which handles some services I don't want on my workstation.  I write software for a living, and that software needs to be tested on the operating systems my clients use, which means that I need Windows.  There is no Wine or Crossover or anything else that can satisfy the need, I need a fully licensed Windows.  There's nothing I use in Windows except for what I use in testing.

Whether I'm running Linux or Windows, it's not too big a deal to map a network share so I can share data between the VMs and my host via a common file system.  I don't notice that a VM takes that much in the way of system resources unless you're using it.  If that idea bugs you, then you can always use VirtualBox or keep your unused VMs powered down.

FWIW, I don't see the point of mixing software platforms.  The cases where wine works well are few, and generally do not coincide with software I am interested in.

IMO, most people who have been using Linux for more than a year or two don't use Windows software, or if they do they have a separate installation.

I guess it comes down to why people run Linux.  If you use it because you feel it's the best, most comfortable solution for you, then you're probably not opposed to keeping any Windows software safely corralled in a VM.  If you use it because it costs less than Windows, or you hate Microsoft, then I suppose you might feel better with a reverse-engineered version of Windows rather than using the real deal.

It all comes down to the fact that one size cannot fit all.  My solution to Windows needs is limited to testing software I write, in which case a technet subscription solves my total use case, and the VM shares drives so I can access them.  Your solution involves using a freeware Windows app that works fine in wine.

Peace.

---

### Post by Copper Bezel on 2013-07-16
> [COLOR=#000000]No I'm not missing the point. Copper Bezel was suggesting dual boot. [/COLOR]
[COLOR=#000000]He was not. The first example referred to using both applications on the same desktop in ways that wouldn't jive with dual booting; the second was a nightmare scenario caused by dependence on dual-booting. = )

> Dual boot is useless IMO if for no other reason than that you can't access both operating systems at the same time. 
Sure. That's what Wine is for. And Wine apps interact directly with the filesystem and other applications on the desktop, which is a step beyond the "access" you get with a VM (shared clipboards aside.) [/COLOR]VMs also really do eat up an awful lot of resources on a typical to low end machine.[COLOR=#000000]

[/COLOR]> [COLOR=#000000]FWIW, I don't see the point of mixing software platforms. The cases where wine works well are few, and generally do not coincide with software I am interested in.[/COLOR]

Right, and it's just useful in those cases where it does coincide. I fully agree that having a broad suite of Windows apps running under Wine for everyday tasks would be a mess.

> [COLOR=#000000]I guess it comes down to why people run Linux. If you use it because you feel it's the best, most comfortable solution for you, then you're probably not opposed to keeping any Windows software safely corralled in a VM. If you use it because it costs less than Windows, or you hate Microsoft, then I suppose you might feel better with a reverse-engineered version of Windows rather than using the real deal.[/COLOR]
Personally, I'd pay Microsoft for the compatibility layer. I'd just rather not be running Windows. I don't think it's worth maintaining a full install for, whether in a VM or on hardware.

> [COLOR=#000000]It all comes down to the fact that one size cannot fit all.[/COLOR]
Quite.

---

### Post by 1clue on 2013-07-16
> **Copper Bezel said:**
> [COLOR=#000000]He was not. The first example referred to using both applications on the same desktop in ways that wouldn't jive with dual booting; the second was a nightmare scenario caused by dependence on dual-booting. = )


So THAT's the point I was missing!  :)

>  
Sure. That's what Wine is for. And Wine apps interact directly with the filesystem and other applications on the desktop, which is a step beyond the "access" you get with a VM (shared clipboards aside.) VMs also really do eat up an awful lot of resources on a typical to low end machine.


That may be and I wouldn't really know.  My current low-end machine has dual core and 8g, and it feels very claustrophobic.  My main machine is a quad-core i7 which will soon have 24g, and that's fairly comfortable.  My job requires that I have non-low-end hardware.

> 
Right, and it's just useful in those cases where it does coincide. I fully agree that having a broad suite of Windows apps running under Wine for everyday tasks would be a mess.


We agree!

> 
Personally, I'd pay Microsoft for the compatibility layer. I'd just rather not be running Windows. I don't think it's worth maintaining a full install for, whether in a VM or on hardware.


That's exactly what Crossover Office does.  Genuine, legally licensed Windows libraries inside a Wine framework.

---

### Post by monkeybrain2012 on 2013-07-16
A dual core with 8g is not 'low end' for me. I do most stuffs on a dual core 4g. Running a VM on the background at all time is out of the question for me.

---

### Post by 1clue on 2013-07-16
We're wandering away from the whole 'wine' discussion, but have you looked at the prices for new equipment?  It's never been cheaper.  I was amazed when I went shopping for a laptop for my wife.  Just stay away from atom if you want virtualization.

---

### Post by Copper Bezel on 2013-07-16
I have a quad-core and 4 GB RAM on my primary machine, and a sad dual-core Celeron and 4 GB on my secondary. I don't really know what I'd do with more, though, other than virtualization.

[QUOTE=1clue][COLOR=#000000]That's exactly what Crossover Office does. Genuine, legally licensed Windows libraries inside a Wine framework.[/COLOR][/QUOTE]
Oh, I didn't realize. Cool. And I'd confused it with PlayonLinux, as well. I'll have to get me a bit of that, then.

---

### Post by llanitedave on 2013-07-17
My wife uses Wine regularly to run Photoshop Elements, which she uses as a companion to GIMP for her art projects.  I used to use Wine occasionally to run old Windows astronomy programs.  I don't any more -- everything I need can now be found in a Linux app.

I still have it on hand just in case.  But I haven't used it in months.  Default?  I don't really think it's all that necessary.  Even my wife had no trouble installing it when she needed it, and it's only for that one single purpose.

---

### Post by Bucky Ball on 2013-07-19
> **gshankar001 said:**
> How come Wine install themselves?

? Please explain ...

---

