---
title: "Online Bible Program"
date: 2006-12-13
forum: Ubuntu Christian Edition
---

### Post by Baasha on 2006-12-13
Has anyone out there been able to get the Online Bible program
[www.online-bible.com](www.online-bible.com)
working with Wine or any other means on a Linux system?  This is the best free bible program I have ever used, but alas, they only produce Windows and Mac versions.

Bob

---

### Post by doobit on 2006-12-13
> **Baasha said:**
> Has anyone out there been able to get the Online Bible program
[www.online-bible.com](www.online-bible.com)
working with Wine or any other means on a Linux system?  This is the best free bible program I have ever used, but alas, they only produce Windows and Mac versions.

Bob

Actually the Gnome Sword in Ubuntu CE is very good. If you want a strictly online Bible search tool, then [www.biblegateway.com](www.biblegateway.com) is great!

---

### Post by Darrious on 2006-12-13
Have you also tried the site [http://bible.crosswalk.com/](http://bible.crosswalk.com/)

---

### Post by Baasha on 2006-12-16
Thanks for the suggestions, but I have looked at these other programs and they don't meet my needs.  As I said, Online Bible is, IMHO, by far the best bible research tool available for those of us who can't afford Bibleworks.  It's only flaw is that they don't produce a Linux distro.  I know that some people have been able to make older versions of OLB work with Wine, but later versions won't run.  I am pretty sure it is a reasonably simple fix, but I haven't found anyone who has managed it.  I was hoping there would be someone on this forum who was familiar with it.

Bob

---

### Post by silvagroup on 2006-12-16
You can go here [http://forums.churchforge.net/viewtopic.php?t=162](http://forums.churchforge.net/viewtopic.php?t=162) and see how to use E-sword on Linux. I think it's one of the best free Bible programs there is. I have Logos and I use E-sword over half the time, it's fast and not as cumbersome as Logos.
For online you may want to try [http://blueletterbible.org/index.html](http://blueletterbible.org/index.html).
God bless and Merry Christmas to all.

---

### Post by Billy McCann on 2007-03-14
> **Baasha said:**
> Thanks for the suggestions, but I have looked at these other programs and they don't meet my needs.  As I said, Online Bible is, IMHO, by far the best bible research tool available for those of us who can't afford Bibleworks.  It's only flaw is that they don't produce a Linux distro.  I know that some people have been able to make older versions of OLB work with Wine, but later versions won't run.  I am pretty sure it is a reasonably simple fix, but I haven't found anyone who has managed it.  I was hoping there would be someone on this forum who was familiar with it.
I totally agree regarding the Online Bible.  According to folks on their forum, Online Bible 2.0 and up just won't work with Wine.  i asked them where I could find older versions of OLB.  I'll post here if they respond.  

By the way, I can't install GnomeSword.  When I try, I get the error message " Depends: libsword5c2a (>=1.5.8-7) but it is not installable".  Performing a package search returns that this package isn't available with Edgy.  Maybe I should just switch to CE, which I just today realized even existed.  

maybe...

---

### Post by silvagroup on 2007-03-14
Looked at the website and it looks very similar to some of the Sword Projects Bible programs.
I will download it and try it in wine and try figure it out for wine. :lolflag: 
That may take a while so mean while have you tried an emulator such as Virtual Box (free) or my personal favorite that I use for running Libronix's Logos, Adobe Acrobat Pro, Turbo Tax and several other Windows only programs, win4linpro, not free, but well worth the cost for those of us who need to run Windows only programs.

---

### Post by Billy McCann on 2007-03-15
Hi silvagroup.

I've used E-Sword before.  I far prefer Online Bible.  You can toggle Strongs numbers and parsings with the push of a key.  Bring up an alternate version(s) within the same window (as many as you'd like) with the push of a key as well.  Basic definitions of both Greek and Hebrew parts of speech are built in; you only need to hover over the pop-up window, and another pop-up window will display ad infinum.  There are many Greek texts to choose from and you can search the parsed LXX and GNT by parsing codes including the use of wildcards within the parsing codes.  Sometimes I'm looking only for Paul's use of masculine, dative adjectives.     

In my opinion, no other free software compares.  

If only I could find version 1.3, I'd be satisfied.  But perhaps you can get it running with Wine.  This is the only Windows program that I use with any regularity, so running XP in a virtual machine just to run this one program doesn't seem worth all the trouble of setting up the virtual desktop.  

I hope you can get it running using Wine.

Blessings on your efforts.  

Billy

---

### Post by ronald_stall on 2007-03-15
If you're already running Wine, I would suggest the program Esword which is the in the process of being integrated into Ubuntu CE. You can see Eswords features at [www.e-sword.com](www.e-sword.com) and for more information on this Ubuntu project follow this link.

[http://ubuntuforums.org/showthread.php?t=372359&highlight=esword](http://ubuntuforums.org/showthread.php?t=372359&highlight=esword)

---

### Post by silvagroup on 2007-03-19
> Esword which is the in the process of being integrated into Ubuntu CE what wonderful news!!!!
I know Billy likes Online Bible and having never used it I checked out the website and  they do the same thing, but in different ways, and sometimes it's just a matter of what you have grown accustomed to that makes the difference. Like I said I use Gramcord, and Libronix Logos on an emulator and those are not cheap. But I begin my research with E-sword and do all my searches in E-sword (fast) and IT WORKS WITH WINE !!!! :KS :KS 

@Billy McCann and Baasha: 

It maybe a few weeks before I can really try getting Online Bible running in wine. My Windows partition is messed up, gee what's new. So I need to re-install Windows and it will be a couple of weeks before I can get to that. Have an ill parent I need to go be with (please pray for his health, his hearts right with The Lord). I did try to install Online Bible in wine and as you said it installs but won't run. I think from what I have seen so far that it's due to Onlines use of IE. What I was going to do, you can try if you have windows, is to intstall it into windows check to see what dll's it loads make sure they are installed in your wine installation, you may need to copy them from windows. You may need to add some to the wine config libraries as native (experiment) and maybe copy your Windows Online directory over to your wine drive_c Online directory. That's for starters. :lolflag: 
Will get back to you in after a couple of weeks with whatever progress.

---

### Post by iMav on 2007-03-19
From the online Bible website:

*"Current version runs OK under Linux using latest WINE emulator. You must use the native riched20.dll and riched32.dll for the Online Bible program to work properly. "*

Sounds like it shouldn't be a problem at all!

---

### Post by silvagroup on 2007-03-19
Yeah, I tried that with no success. E-sword needs riched20 also.

---

### Post by Billy McCann on 2007-03-19
> **iMav said:**
> From the online Bible website:

*"Current version runs OK under Linux using latest WINE emulator. You must use the native riched20.dll and riched32.dll for the Online Bible program to work properly. "*

Sounds like it shouldn't be a problem at all!
The WINE emulator comes with riched20.dll and riched32.dll, unless my eyes were deceiving me.  :)   Keep in mind that those comments were regarding a previous version (< 2.0). 

 I'll do what silvagroup suggested and run OLB in Windows to see which .dll's it loads (once I found out how to do just that).

@silvagroup

Thanks for your efforts.  Hope your ill parent begins toward better health.  

Confused regarding your comment about OLB using IE.  I'll look into that.  Thanks again.


Billy

---

### Post by silvagroup on 2007-03-19
Thank you Billy. 

I think what iMAv was eluding  to is that they should be included in your winecfg (maybe).  Sometimes you have to use native from Windows. However I have tried several things with within wine no success. Something very curious I have noticed is that if I have my e-mail (Kmail in my case) open when I try to run OLB, OLB some how is trying to use the ports my e-mail is using to access the web, I get a status message saying "Attempying to access URL", don't really like that. But it would seem it needs a internet access, not sure why, in windows that's areally  scary proposition! Also my CPU usage goes to 100% and will stay there until I kill the process.
Those are my findings so far.

---

### Post by Billy McCann on 2007-03-21
Hi silvagroup.  

Thanks for your continued efforts.  The behaviour of OLB that you're reporting is very, very strange.    Perhaps it's time to put it aside and work with E-Sword more.  I'll look into the link that you gave in one of your earlier posts on how to get E-Sword working in Linux.  

Thanks, again.

---

### Post by silvagroup on 2007-03-21
It is very strange and I will try to figure it out once I get back from taking care of my father.
However it could end up being one of those programs which just will not run in wine.
I think once you get used to e-sword you may end up liking it. Also try ISA (scripture4all.org) it an interlinear which I like and runs in wine also. :) 
God bless.

---

### Post by Billy McCann on 2007-03-27
Thanks for the links to the E-Sword thread, silvagroup.

---

### Post by silvagroup on 2007-04-16
Well folks have had no success.
 And frankly with OLB looking at my email ports to try to connect to the web with wine, I would be very hesitant to use it anyway, especially on Windows. Even more so if it were on my home or work system. That just seems like an open invitation to trouble.

---

### Post by shane2peru on 2007-04-17
E-Sword vs Online Bible.  They both have their strenghts.  I personally like and use e-Sword, it has more of a graphical interface with point and click.  Although I do have to admit, once you learn the keyboard shortcuts that OLB is a very fast program.  I have often wanted to try and get it running in Linux via wine, and have yet to have success.  I think it is a very worthwhile project, if someone more proficient in wine is willing to help, I too would be willing to chip in and see what we can figure out.  I would like to use it as well.  I will play around with it some more in my spare time too and see what I can do.  I have a CD for version 1.4 I think, and will see if I can get that working.  If I can, I will have to check if they don't care if I make it available for download.  Version 2 though introduced a new way of handling material, and is not backwards compatible from my understanding, so you will need the old modules as well.  :(  

Shane

---

### Post by eddy-14 on 2007-12-12
the major reason i'd prefer to use the online bible on ubuntu than e-sword is because of its content. I don't know about other editions, but the french edition is very rich in modern translations, commentaries, dictionnaries, and other tools. for what I know, e-sword (or any free bible software) allows only content that is free from rights (which is logical, you need to pay what is under rights).
another solution would be to be able to import online bible material inside e-sword, but if I understood correctly, the Microsoft database programm (I can't remember its name) is needed for that...

---

### Post by dmacbanay on 2007-12-23
Because of hardware failures I recently had to re-install kubuntu 7.10.  After installing it I installed wine .9.50 and Online Bible.  To my amazement it actually started to run but then locked up and I could not get it to run again.  So if it could only be figured out what is causing it to fail it may not be that big of a job to make it work.  Version 1.32 did work with wine.  Unfortunately I only have the update install file for it and not the full install.  I wish I would have thought ahead and gotten the full install file for it when available.

Someone mentioned they got ISA to work.  I can't get either version 1 or 2 to work.

---

### Post by silvagroup on 2007-12-23
Yes I had ISA working within Wine on Fiesty.
 For some reason I can't get it to work on Gutsy.
Could be Wine version not sure at this point, but ISA will not work in Gutsy.

---

### Post by dmacbanay on 2007-12-24
I got Online Bible to startup.  It displays but still has severe lockup problems when you go to do much of anything.  I deleted the program directory and the directories it puts in the 'my documents' folders.  There is one for all users and one for the current user.  Then I ran the install program.  Then I opened a terminal shell and executed 'wine Olb.exe' and as soon as it started I switched to the terminal shell and hit ctrl-c.  I have a fairly fast computer and found it needs to be done about as soon as I can switch over to the terminal shell.  If done at the proper time it doesn't exit the program but instead exits whatever routine olb is stuck on.   After that first time olb will start normally.   I have riched20 & riched32 configured to load native.

As for ISA, I got it to work also.  I compiled wine myself after installing the following dependencies: 

flex
bison
tk8.4-dev
freeglut3-dev
libfreetype6-dev
gnome-devel

I did have fontforge installed but removed it.  It was after that that I think things started to work for me.

I've been having problems with wine where when exiting some programs it still leaves open processes hanging that I am not able to kill without re-booting.  If any of these processes keep running then many wine programs will not run until they are killed.  So I just started to have all the wine programs start from a terminal shell.  That way if things don't close out properly I can hit ctrl-c in the terminal and stop the processes.  I went into the menu editor and enabled the option to start in a terminal for each of the programs.

---

### Post by Frogfoot on 2008-09-19
Has anyone found the solution to run Online Bible version 2.20.03 on the latest Wine version?

---

### Post by silvagroup on 2008-09-19
Frogfoot I gave up due to time contarinst and just ran it form my emulator which works evrytime with windows based programs.

I run Libronix, Gramcord, Abobe Acrobat and several other Windows only programs from it.

Wine is still very limited in what it can do. It's major limitation is that it can't run the Windows Explorer which many of the windows based programs are very dependent on.

The emulator I use is one you have to pay for but for what it does it's extremely inexpensive at less than $30 US dollars and well worth the times saving for me also.

There is also vmware server which works very well. I have recently experimented with kvm but it too can be very time consuming in seting up. Once they get it totally ironed out and user friendly it will be a great tool and will probably be the one I will use excusively, becasue it's open source, but it has away to go.

Sorry maybe soem one else has had some succes with OLB with wine and will ring in.
Don't forgetto also check the wine hq database to see if their is anything there on OLB.

---

### Post by rwaldo on 2008-11-15
I have not been able to get OLB to work in Wine but I did get it working on my Ubuntu 8.10 desktop. I used the VirtualBox program from Sun (free for personal use). It also allows me to Active Sync my PDA and even install the OLB on the PDA. It runs at about the same speed as a stand-alone Windows install. Check out my review at my website: [http://chiefshepherd.net/2008/11/14/converted-to-linux](http://chiefshepherd.net/2008/11/14/converted-to-linux)

---

### Post by shadman1957 on 2009-02-21
I'm new to Ubuntu and new to linux. But I did attempt to get OLB up and running via Wine. No luck. Using MS Process Explorer, identified all DLLs and updated all allowable Wine DLLs. OLB comes up but any real actions caused OLB to hang. So, if anyone has any ideas to try ... but I'm guessing there will still be issues with it.  I know I can go with a VM but I was hoping to avoid that.

thx,

---

### Post by mrmom7837 on 2010-04-01
I have been looking for a while now and the best, easy-to-use online bible program is e-sword live.  It is free and no install just have to be online.  Give it a shot.  Beats trying to install everything in Wine.
[http://live.e-sword.net/](http://live.e-sword.net/)

---

### Post by TuckLive on 2010-04-04
[www.BibleForge.com]("http://www.BibleForge.com") is a new and upcoming web-based bible study tool.  It's currently in Alpha with the developer working to add new features.  I've installed it on my 10.04 virtual machine and it was easy.

When searching you can use the following to get specific returns:

anyword AS RED -- Will show when Jesus spoke about it
anyword AS NOUN 

You can contact the developer at [email]info@bibleforge.com[/email] for suggestions, bugs, or comments.  If you would like to install this on your personal site or pc send me a pm.

---

### Post by tom4jean on 2010-04-18
> **TuckLive said:**
> [www.BibleForge.com]("http://www.BibleForge.com") is a new and upcoming web-based bible study tool.  It's currently in Alpha with the developer working to add new features.  I've installed it on my 10.04 virtual machine and it was easy.



This webpage just has a plain search box that opens simple bible searches in the webpage if you enter a word. 
no install option or anything else?
Where is the program to install?

---

### Post by TuckLive on 2010-04-18
> **tom4jean said:**
> This webpage just has a plain search box that opens simple bible searches in the webpage if you enter a word. 
no install option or anything else?
Where is the program to install?

Here are the instructions to download:

[http://wiki.github.com/bibleforge/BibleForge/installation-instructions](http://wiki.github.com/bibleforge/BibleForge/installation-instructions)

Currently if you install BibleForge right now all you will get is what you saw on the webpage.  The developer is working on some new features and design.  A simple install script will be coming shortly also.

---

