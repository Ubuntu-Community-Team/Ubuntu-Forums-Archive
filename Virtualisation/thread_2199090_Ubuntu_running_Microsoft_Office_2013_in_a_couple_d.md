---
title: "Ubuntu running Microsoft Office 2013 in a couple different ways (no wine involved)"
date: 2014-01-12
forum: Virtualisation
---

### Post by Resilldoux on 2014-01-12
Hi there,

So, I thought of sharing my way to run Office 2013 on your Linux box. I uploaded a couple of videos demonstrating a few different ways on how to do this.


[LIST]
[*]As a RemoteApp (brief): [http://www.youtube.com/watch?v=C-DrfMReaYg](http://www.youtube.com/watch?v=C-DrfMReaYg)
[*]As a RemoteApp (more elaborative): [http://www.youtube.com/watch?v=wWu2le159K4](http://www.youtube.com/watch?v=wWu2le159K4)
[*]With VirtualBox Seamless-mode: [http://www.youtube.com/watch?v=9MsJXST1QJk](http://www.youtube.com/watch?v=9MsJXST1QJk)
[*]With VMware Player Unity: [http://www.youtube.com/watch?v=O2CqfsQl5r0](http://www.youtube.com/watch?v=O2CqfsQl5r0)
[/LIST]

Cheers.

---

### Post by Bucky Ball on 2014-01-12
As the links in your post seem to be about running Windows as a guest in a Ubuntu host using Virtualbox or something like it, your thread has been moved to ***Virtualisation***. 

Please be aware that the ***Cafe*** is for non-technical, non-support threads.

---

### Post by monkeybrain20122 on 2014-01-12
I don't agree with using MSO unless it is absolutely necessary (and often it is not). But if you have to, I think Wine is a better solution than virtualization if it works. This goes with all Windows apps. If  something works in wine ('works' means it actually works, not with features missing or broken) it would be preferable to VM because it requires much less overhead in terms of system resources and it doesn't require Windows.

---

### Post by Resilldoux on 2014-01-13
Of course, I agree. Though, using the RemoteApp solution, you could RDP into a whole other system. If you're connecting to a terminal server, it only stresses the server, not your own box.

---

### Post by hasanalikhattak on 2014-02-12
i came across this text
> **On January 03, Alexandre Julliard announced a new development version of the Wine app, which brings a few new features and a lot of bug fixes.**

[FONT=Verdana]As usual, the number of new features and bug fixes in the development version of Wine (Wine Is Not an Emulator) is quite large, even if we don&#8217;t take the important changes into account.[/FONT]

[FONT=Verdana]The current Wine feature a couple of new things, such as AVI compressor implementation and threaded local storage support in dynamically loaded libraries. Also, the beginnings of a Task Scheduler implementation have been put in place, and the IPX protocol support has been extended.[/FONT]

[FONT=Verdana]Wine 1.7.10 also brings bug fixes for the following Windows games and tools: Dungeon Keeper Gold, Garmin MapSource 6.x, AIM Pro, Jumpstart Mystery Club, The Bat!, Skype, MotorM4X, Blood Bowl Legendary Edition, Google Music Manager, Corel Photo Downloader, Visual C++ 2010, Freemake Video Converter, Anno 1602, Microsoft Office 2013, Volvo The Game, and Torch Browser.[/FONT]

[COLOR=#0000FF][FONT=Verdana]**Highlights of Wine 1.7.10:**[/FONT][/COLOR]

[FONT=Verdana]&#8226;	The Jumpstart Mystery Club download manager now works correctly;[/FONT]
[FONT=Verdana]&#8226;	ActiveX Control Pad installer no longer hangs sometimes on exit;[/FONT]
[FONT=Verdana]&#8226;	Jasc Animation Shop 3.05 no longer crashes on startup;[/FONT]
[FONT=Verdana]&#8226;	Microsoft Office 2013 full offline installer no longer crashes on startup;[/FONT]
[FONT=Verdana]&#8226;	GoldCoin 0.7.1.7 no longer shows assertion on startup (needs ntdll.NtQuerySemaphore implementation);[/FONT]
[FONT=Verdana]&#8226;	Visual Studio 2010 installer no longer fails to install in 64-bit Windows XP WINEPREFIX (claims "Windows XP x64 Service Pack 2 is required");[/FONT]
[FONT=Verdana]&#8226;	Multiple applications no longer refuses to load or crash on startup (Nitro PDF Reader 3, Mozilla Firefox);[/FONT]
[FONT=Verdana]&#8226;	Mobile Master no longer crashes on startup.
[/FONT] [http://news.softpedia.com/news/Microsoft-Office-2013-Installation-Works-with-Wine-1-7-10-413664.shtml](http://news.softpedia.com/news/Microsoft-Office-2013-Installation-Works-with-Wine-1-7-10-413664.shtml)

i wonder if someone has tried it yet :)

---

### Post by Resilldoux on 2014-02-12
Yes, that's really great, but it also was about time. I haven't tried it yet since I'm using LibreOffice just fine. I might look into this though, just to see how it works.

---

