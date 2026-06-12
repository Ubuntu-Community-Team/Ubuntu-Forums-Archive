---
title: "Windows Apps on Linux May Not Be Such a Great Idea"
date: 2006-02-06
forum: The Cafe
---

### Post by grus777 on 2006-02-06
Windows Apps on Linux May Not Be Such a Great Idea  	 

Shutdown
Written by [COLOR="SeaGreen"]Steven J. Vaughan-Nichols[/COLOR]   
Friday, 15 February 2002
[http://www.linux-mag.com/2002-02/shutdown_01.html](http://www.linux-mag.com/2002-02/shutdown_01.html)

[FONT="Arial"]As I write this, many otherwise sane Linux people I know are going gaga over the idea of running Win- dows applications on Linux with Lindows. "It'll make Linux the operating system for the desktop once they can get Office XP running on it," gushes one of my friends.

Oh, please! It won't do anything of the sort. First, while MP3.com millionaire Michael Robertson certainly has the bucks to pursue the dream of a cheap operating system that can run both Linux and Windows programs, it's vaporware now. I'm told that there are plans for a beta release by the end of 2001 and a shipping product in the first quarter of 2002.

Right, a company founded in September will have a shipping operating system by March 2002. I don't think so. Can they put a DOS/Windows emulator on Linux by then? Sure, the company is working with the Wine Windows 16/32-bit emulator, which dates back to 1993. However, even before Wine, DOS/Windows on Unix had already been done, over and over and over again.

We've had Microsoft operating system emulators and virtual machines for Unix since before Linux was around. I wrote my first review of DOS on Unix systems for Computer Shopper in 1990 using Interactive Systems VP/ix and Locus Merge.

Today I'm running NeTraverse's Win4Lin 3.0 (a Merge descendent) on Caldera OpenLinux Workstation 2.3, and I'm writing the first draft of this column in Microsoft Word for Windows 2.0c on it. If I really wanted to, I could get Office 97 running on it.

And you know what? It works well. Not only can I run Office, but I can also run some of my other favorite Windows applications, like Quicken and Photoshop. And if you don't care for Win4Lin or Wine, you can also just run multiple operating systems on one PC at once with VMware.

So you see, there's no need for anything like a Lindows. What it's trying to accomplish has already been done several times.

My point is that simply being able to run Windows applications on a Linux platform isn't going to make a significant impact on the Linux desktop world -- even if it's Office XP. It has never done so before, so why should it now?

Oh, I see how it can be useful. Sometimes you really do want a Windows application. Indeed, for some jobs like cross-platform development or technical support, being able to switch from Windows to Linux and back again on a single machine is a pretty useful option. But that's not where the market is. It never has been and it likely never will be.

The whole idea of emulation and VMs (Virtual Machines) has two fundamental flaws. The first is that try as they might, nobody can keep up with Microsoft's changes to their operating system and APIs. The slap on the wrist meted out by the Department of Justice and a slight opening of Microsoft's source code isn't going to change this. Neither a VM nor an emulator can run Windows and its applications as well as Microsoft's native system running on a standalone machine. The vast majority of people aren't going to come over to Linux when they know that only some Windows applications run on a Linux box. They'll stick with Windows.

The other flaw is that by wasting all this time (I'm talking years!) and energy playing catch up with Microsoft on its own playing field, there's less time and energy for native open source Linux applications. Every minute that a developer wastes trying to copycat Microsoft's operating system and APIs is a minute that could have been spent on some significant Linux application development.

As much as I like the emulators, they only hurt Linux's own software development. Even if we assume that due to a burst of programming genius Lindows can actually run all XP applications by next spring -- it won't happen, but let's assume -- then Linux application development will come to an end.

If you can run Office XP, then what need is there for StarOffice? We've seen it before. As Microsoft Office gained market share by hook or by crook in Windows, competitors like Corel WordPerfect and Lotus SmartSuite became mere shadows of their former selves. The same thing is likely to happen to Linux applications.

I don't know about you, but I don't want Linux to become a secondary platform for Windows applications. It may be Linux under the desktop, but it would only be Windows to users' eyes.[/FONT]

© 1999-2005 Infostrada Communications, LLC ()

---

### Post by briancurtin on 2006-02-06
since when was running windows applications in linux a great idea in the first place?

also, do you realize that this article is 3 years old?

---

### Post by endersshadow on 2006-02-06
It's an article against Lindows...back when Linspire was called Lindows...heh...this is almost 4 years old now...

---

### Post by commodore on 2006-02-06
It's still not a great idea.

---

### Post by ardchoille on 2006-02-06
I agree, running Windows apps on Linux isn't very smart. All applications launched inside Wine, Cedega, or Cross-Over Office are technically just as vulnerable to viruses/worms/trojans/spyware/adware as if those apps were running in Windows:  [http://blogs.zdnet.com/Ou/index.php?p=146](http://blogs.zdnet.com/Ou/index.php?p=146)

---

### Post by jc87 on 2006-02-06
[QUOTE=ardchoille]I agree, running Windows apps on Linux isn't very smart. All applications launched inside Wine, Cedega, or Cross-Over Office are technically just as vulnerable to viruses/worms/trojans/spyware/adware as if those apps were running in Windows:  [http://blogs.zdnet.com/Ou/index.php?p=146](http://blogs.zdnet.com/Ou/index.php?p=146)[/QUOTE]


Someone correct me if im wrong , but i think that Wine and others emulators run in a "sand box" , so the biggest problem may be the emulator crash.

By the way , i personally think that having windows apps available is good because not all the FOSS in Unix systems covers all the necessary areas , we can talk about games , some professional software , etc...  

Off course we don't need to emulate all the win software , but let us be honest , if i need a specific program for my work/living , and i cant find a FOSS substitute , but i really want to use Gnu/Linux , what others alternatives do i have besides Wine/Cedega/Cross office ?

---

### Post by poofyhairguy on 2006-02-06
WINE is not an emulator.

---

### Post by xequence on 2006-02-06
> WINE is not an emulator.

Cant beat recursive acronyms.

It is a compatability layer o.O

---

### Post by GreenfrogCT on 2006-05-12
[QUOTE=commodore]It's still not a great idea.[/QUOTE]

Remember an operating system known as OS/2 Warp?  One of the bright ideas that IBM had was what they called "Warp for Windows" which allowed a Windows 3.x layer to run on top of the OS/2 kernel, thus enabling Windows applications to run "natively".

This, imho, probably had as much to do with the demise of OS/2 as a viable x86 alternative to Microsoft as anything else.  When users could run the same versions of Word and Excel on their Warp boxes there was little reason for developers to come up with alternatives.  When it became obvious that Windows was no more stable (and probably less stable) running on the OS/2 kernel compared to the MS-DOS kernel - and Microsoft still had all of the most wanted applications - there was little reason for most people (particularly businesses) to bother thinking about OS/2 vs. Windows 95 - and OS/2 slowly faded into the sunset.

Indeed, one of the reasons I still have to run Windows XP at work (where I am right now) is that **I HAVE TO**](*,) because there are Windows apps that I absolutely need to do my job.  Being able to run those apps on the Linux kernel *might* be a good thing in the short term . . . but in the long run if everybody continues to use Windows apps with their proprietary formats as a standard it will do nothing to promote the use of GNU distributions and open source software.

The wider adoption of GNU on the desktop will require the continued development of high quality open-source alternatives to proprietary applications, the insistance of the user community on the use of open formats (like XML, FLAC and Vorbis, etc.) over proprietary ones, and the continued improvement in the user experience (especially for non-technical users).  

As long as we have to instruct people like my administrative assistant that she needs to "open a terminal session and type 'sudo modprobe lp'" in orter to get her printer to work again, there will be limits to the acceptance of Linux on the desktop. 

Running Windows applications on your Ubuntu box won't help that process, it will only prolong the acceptance of proprietary software and APIs.

:mrgreen:  Ribbitt

---

### Post by BoyOfDestiny on 2006-05-12
[QUOTE=GreenfrogCT]Remember an operating system known as OS/2 Warp?  One of the bright ideas that IBM had was what they called "Warp for Windows" which allowed a Windows 3.x layer to run on top of the OS/2 kernel, thus enabling Windows applications to run "natively".

This, imho, probably had as much to do with the demise of OS/2 as a viable x86 alternative to Microsoft as anything else.  When users could run the same versions of Word and Excel on their Warp boxes there was little reason for developers to come up with alternatives.  When it became obvious that Windows was no more stable (and probably less stable) running on the OS/2 kernel compared to the MS-DOS kernel - and Microsoft still had all of the most wanted applications - there was little reason for most people (particularly businesses) to bother thinking about OS/2 vs. Windows 95 - and OS/2 slowly faded into the sunset.

Indeed, one of the reasons I still have to run Windows XP at work (where I am right now) is that **I HAVE TO**](*,) because there are Windows apps that I absolutely need to do my job.  Being able to run those apps on the Linux kernel *might* be a good thing in the short term . . . but in the long run if everybody continues to use Windows apps with their proprietary formats as a standard it will do nothing to promote the use of GNU distributions and open source software.

The wider adoption of GNU on the desktop will require the continued development of high quality open-source alternatives to proprietary applications, the insistance of the user community on the use of open formats (like XML, FLAC and Vorbis, etc.) over proprietary ones, and the continued improvement in the user experience (especially for non-technical users).  

As long as we have to instruct people like my administrative assistant that she needs to "open a terminal session and type 'sudo modprobe lp'" in orter to get her printer to work again, there will be limits to the acceptance of Linux on the desktop. 

Running Windows applications on your Ubuntu box won't help that process, it will only prolong the acceptance of proprietary software and APIs.

:mrgreen:  Ribbitt[/QUOTE]

The wine page deals with "wine myths".
[http://www.winehq.com/site/myths](http://www.winehq.com/site/myths)

A lot of people don't switch to Linux because it doesn't run "blahblah" app. If that's what it takes to switch. 
Some apps don't have clones, some are no longer supported (i.e. something closed source and now in the public domain, like castle of the winds, which does work even though it's win16 ;) )

It's just something to help with users' transitions. 

I'm 100% for open alternatives, I don't even have wine installed on any of my machines currently (I had just tried it for fun.) Eventually, it would be amusing if Linux could run windows apps better than windows. Anyway, if you don't like it don't use it. 

Open formats rock for many reasons. I'm hoping ODF takes off, so I can avoid getting MS attachments in emails, considering their newer xml formats (of course incompatible to force upgrades) contain patents... Just google office 2007 file formats... 

As for closed soure drivers, I think these are the most damaging. Luckily my hardware is supported 100% with open drivers.

---

### Post by Kimm on 2006-05-12
Lindows is not an OS that would be able to run windows applications (not to any greater extrent then any other Linux). Its just a name, that is supose to say "Linux for Windows users" or something like that.

New name = Linspire

---

### Post by YokoZar on 2006-05-13
[QUOTE=GreenfrogCT]Running Windows applications on your Ubuntu box won't help that process, it will only prolong the acceptance of proprietary software and APIs.[/QUOTE]If an application works in Wine, then that means it works in Wine's implementation of the Windows API.

Since Wine is open source, by definition this means it's no longer proprietary.  Wine is the very mechanism by which the Windows API is being made open.

---

### Post by kelsey23 on 2006-05-13
I'd like to point out that first of all, Linspire/Lindows dropped the idea of running Windows applications in a GNU/Linux enviroment a few years ago, to focus on making Linux easier for new users and Windows-to-Linux converters. Second, the article says that virtual machines can't keep up with new technology. Funny, I wonder what they call a virtual machine because last times I checked a virtual machine was something that used virtualisation to pretend to be another computer...

---

### Post by GreenfrogCT on 2006-05-13
[QUOTE=YokoZar]If an application works in Wine, then that means it works in Wine's implementation of the Windows API.

Since Wine is open source, by definition this means it's no longer proprietary.  Wine is the very mechanism by which the Windows API is being made open.[/QUOTE]

Not to get too far off track here, but when I spoke of proprietary vs. open source I wasn't talking about WINE - I was talking about the applications themselves.  

My feeling is that in order for GNu/Linux to succeed on the desktop it needs a strong base of native applications.   Running Windows applications does not encourage the development of native alternatives.  Adopting proprietary file formats and reverse-engineered APIs helps proliferate those formats as "standard".  It would be more advisable, IMHO, to encourage the use of open APIs and open formats.

Just one little frog's opinion.

:mrgreen:  Ribbitt

---

### Post by YokoZar on 2006-05-13
[QUOTE=GreenfrogCT]Not to get too far off track here, but when I spoke of proprietary vs. open source I wasn't talking about WINE - I was talking about the applications themselves.  

My feeling is that in order for GNu/Linux to succeed on the desktop it needs a strong base of native applications.   Running Windows applications does not encourage the development of native alternatives.  Adopting proprietary file formats and reverse-engineered APIs helps proliferate those formats as "standard".  It would be more advisable, IMHO, to encourage the use of open APIs and open formats.[/QUOTE]Sure, incompatibility *does* creates extra incentive to develop native applications.  It also, however, creates a lot more incentive to never migrate in the first place.  Forcing the standard open by creating a compatibility layer, however, puts the power in the user's hand to choose the best platform available.

Wine, simply put, lowers the switching cost to Linux by making Linux more useful.  At worst, Wine is something that doesn't work very well and isn't used - still better for the user than if Wine didn't exist in the first place!


I've heard it a lot, but I still don't buy the argument against Wine and Windows application compatibility.  Essentially, it is an argument in favor of making Linux less compatible - by that logic, couldn't we "help" Linux by breaking compatiblity in other areas as well?

The suggestion is of course absurd.  Think of incompatibility as a wall - it functions both to keep new users out, and to trap existing users in.  When most of the users are stuck in Windows territory desperately trying to get out, the best thing for Linux is to knock that wall down and allow the users the freedom to move between platforms.  Putting up our own wall by creating incompatibility, Microsoft-style, is a decision to lock users in - and, frankly, we don't have enough of them in the first place.

---

### Post by GreenfrogCT on 2006-05-14
[QUOTE=YokoZar]Sure, incompatibility *does* creates extra incentive to develop native applications.  It also, however, creates a lot more incentive to never migrate in the first place.  Forcing the standard open by creating a compatibility layer, however, puts the power in the user's hand to choose the best platform available.

Wine, simply put, lowers the switching cost to Linux by making Linux more useful.  At worst, Wine is something that doesn't work very well and isn't used - still better for the user than if Wine didn't exist in the first place!


I've heard it a lot, but I still don't buy the argument against Wine and Windows application compatibility.  Essentially, it is an argument in favor of making Linux less compatible - by that logic, couldn't we "help" Linux by breaking compatiblity in other areas as well?

The suggestion is of course absurd.  Think of incompatibility as a wall - it functions both to keep new users out, and to trap existing users in.  When most of the users are stuck in Windows territory desperately trying to get out, the best thing for Linux is to knock that wall down and allow the users the freedom to move between platforms.  Putting up our own wall by creating incompatibility, Microsoft-style, is a decision to lock users in - and, frankly, we don't have enough of them in the first place.[/QUOTE]

YokoZar -

Don't get me wrong, I'm not madly "anti-Wine"  (sounds like what someone might have said back during prohibition ;) )   If Wine or other compatibility layers can eventually make it possible for specific application portability (unique apps that there is no GNu equivelent for) that's not my concern.  I just think it is far more important to make things like Ooo mainstream rather than concentrating on running MS Office 2003 under Linux.

I have Wine on this machine and have played with it some, but at this point it's too funky to be of much use.

Interesting article on NewsForge about this subject:  [ HERE ]("http://business.newsforge.com/business/06/04/27/155209.shtml?tid=18&tid=2") 

Have a happy!

:mrgreen:  Ribbitt

---

