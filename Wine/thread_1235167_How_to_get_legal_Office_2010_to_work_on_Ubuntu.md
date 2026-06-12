---
title: "How to get legal Office 2010 to work on Ubuntu"
date: 2009-08-08
forum: Wine
---

### Post by Vignesh S on 2009-08-08
Alright, this time, I did it the legal way, and I got Office 2010 from Microsoft via the invitation only technical preview signup thing. Now, I want to know how to get it to work Ubuntu.

Where did I get this from? From the technical preview signup from here ([https://microsoft.crgevents.com/Office2010TheMovie/Content/Home.aspx](https://microsoft.crgevents.com/Office2010TheMovie/Content/Home.aspx), though now its over)

---

### Post by doorknob60 on 2009-08-08
Try it in Wine. If it doesn't work, it probably won't for a while since most people can't test it to try to make it work since it's not out yet.

---

### Post by philcamlin on 2009-08-08
> **doorknob60 said:**
> Try it in Wine. If it doesn't work, it probably won't for a while since most people can't test it to try to make it work since it's not out yet.
or cross over

---

### Post by Vignesh S on 2009-08-12
Which version of Wine would be the best for Office 2010? I know that I need an MSXML of 6 or above.

---

### Post by Vignesh S on 2009-10-08
Well, apparently, Crossover has better support for Office 2007 now. I'll download the trial and see if I can get it to work...

(NOTE: MSXML 6.0 or above needs to installed in the same bottle that you intend to install Office 2010 into, or it won't work)

---

### Post by beastrace91 on 2009-10-08
Yea give it a go on Crossover, I use Onenote 2007 on it and it works quiet well :)

~Jeff

---

### Post by blazemore on 2009-11-17
I tried to install it, but I get ERROR_LANGUAGE_NOT_SUPPORTED does anyone know how to fix this?

---

### Post by Vignesh S on 2009-11-23
Now that I've finally got some free time, I should finally be able to test Office 2010 beta under Crossover/Wine (I'm banking on Crossover working, because that's way more stable ;-) I'm gonna give installing 2010 beta in a Office 2007 "bottle" a crack

---

### Post by lucianct on 2009-11-23
I am using crossover 8 with a winxp bottle. I just downloaded the beta version of office 2010.
All I get is "Microsoft Office Professional Plus 2010 encountered an error during setup."
When I try to install 2007 I also get ERROR_LANGUAGE_NOT_SUPPORTED.

---

### Post by Vignesh S on 2009-11-24
> **lucianct said:**
> I am using crossover 8 with a winxp bottle. I just downloaded the beta version of office 2010.
All I get is "Microsoft Office Professional Plus 2010 encountered an error during setup."
When I try to install 2007 I also get ERROR_LANGUAGE_NOT_SUPPORTED.

Strange :???: Office 2007 in Crossover (with winxp bottle) works fine on 64-bit Ubuntu 9.10 for me, and it also worked fine on 32-bit Ubuntu 9.10 on my old lappy (before it broke :-(). Maybe its a problem with the cd/installer?

I'll give Office 2010 a crack on Crossover tonight...

---

### Post by lucianct on 2009-11-24
office 2007 worked with crossover 7.10 in intrepid and jaunty x86. on karmic amd64 it doesn't work, i don't know why... i tried with both wine and crossover.
if you can make 2010 work please post your results :)

---

### Post by Vignesh S on 2009-11-25
Despite using Crossover 8, it doesn't work :-( Here's what I did:
Just use the Office 2007 installation method (but choosing the Office 2010 .exe file)
It will go along its merry way till it reachers the part about installing 2010, where it says it needs MSXML 6.10.1129.0 (at least) to install.

I went and installed that into the SAME (not different) bottle via the "install unsupported software" option. 

After doing that, the installation came up, and it was actually doing well, until around 2/3 of the way, when the setup said that it experiened an error during setup. 

So Crossover isn't going to work, I'm going to have to try this in every single Wine version up to now after the "stable" release 1.01 (hardly doubt Wine has ever been stable, but they do a pretty damn good job of it considering it is quite hard to get MS stuff to work in Ubuntu or anything that isn't MS in the first place!)

Anyone by any chance got Office 2010 beta to work in Wine?

I'll post some screenshots of what happened later on ;-)

---

### Post by JCoster on 2009-11-26
I'm giving it a go on Wine- get the same MSXML6 error.

Have a look at this:
[http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)

Could be a start.

UPDATE: Using this, I get a new error:
"Setup cannot continue because a required file is either corrupted or not available. Run Setup again from the original source disc or download location."
And the specific error was:
"Error: Xml Signature verification failed for setup metadata Type: 45::InvalidMetadataFile."

It's early progress.

Anyway, to get this far, here's what I did:
```
wget http://www.kegel.com/wine/winetricks
sh winetricks msxml6
```

---

### Post by JCoster on 2009-11-29
More progress:
Alt-f2: winecfg
On the libraries tab, add a new override for library 'msxml6'.
This gets me to the part where it asks me to enter my product key, but it does not appear to realise when I have entered it.

---

### Post by nwarrenfl on 2009-11-29
Others already tried to run it but it doesn't install: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336)

However nobody showed the Wine debug output to be able to find the cause, it would be nice to know so developers could fix it for the release!

Could you try to run the installation or the program in terminal and paste the Wine output?

---

### Post by Vignesh S on 2009-11-29
I tried the suggestions above (as well as running the .exe under Windows Vista) using version 1.0.1 of Wine, but it failed. Here's the output from the terminal in a .odt file (strange, I thought a gedit file would upload, but it didnt. Oh well, no harm done ;-))

Quite a bit, but I'm not quite sure how to put this all into a bug report for the wine devs. I'll try this again under Wine 1.1.31 (my internet's been throttled, so I can only download stuff off netspace' servers, and that's the version in the repos :-() When my internet comes back on Friday, I'll start this whole thing from version 1.1.16 (apparently the 1st version to let Office 2007 install) so we'll see how this goes...

---

### Post by NuevaVictima on 2009-12-07
I tried Wine and Crossover. To be sure if the whole thing is working I installed the 2010beta on a Windows 7 Sony I have. It gives me the sense that while is asking for the key, is executing a script or something else, just to know if the key is acceptable. This is the moment that Wine or Crossover is getting to nowhere.

---

### Post by blazemore on 2009-12-26
I think when it comes out in retail, Crossover etc will work to get it functional, if they aren't already. They'll probably use it as an excuse for a new release number.
The good thing about Crossover is they put (all?) their code upstream so vanilla Wine benefits as well.

---

### Post by besweeet on 2009-12-29
Any luck with this? I'm [unfortunately] on a uMBP with W7, Ubuntu 9.10, and Snow Leopard. Since it's a Mac, I try to use SL as much as possible. W7 is still my OS of choice. 

Would love to get Office 2010 working in CrossOver or [Dar]Wine.

---

### Post by NuevaVictima on 2009-12-31
I use MSOffice 2010 in my Ubuntu KK 9.10 through virtual box and it's working fine. Only sometimes is pausing a sec for breathing....
*the only notable difference with MSOffice 2007 is the speed. It's really fast. Faster than OO3.2.

---

### Post by dBuster on 2010-01-02
I have gotten past that msmxl or what ever that error is, and have gotten it to look like it has installed and then near the end it pops up and tells me setup has failed...

Anyone have any luck?

Using Crossover 8 and trying to get the beta installed.  Just downloaded the installation right from MS...

---

### Post by Vignesh S on 2010-01-02
Nope, I certainly haven't had any luck with this at all. I think Wine/Crossover (or whoever does it first) have to find where the problem lies (which is around 2/3 of the installation) and fix it up for good. But then again, even if that's fixed, there could be other probs. Oh well, all part and parcel of getting Office working in Linux...

Anyone out there had any luck at all in installing Office 2010 Beta 2 successfully?

---

### Post by besweeet on 2010-01-10
> **NuevaVictima said:**
> I use MSOffice 2010 in my Ubuntu KK 9.10 through virtual box and it's working fine. Only sometimes is pausing a sec for breathing....
*the only notable difference with MSOffice 2007 is the speed. It's really fast. Faster than OO3.2.

...

How'd you get it working?

---

### Post by Vignesh S on 2010-01-10
> **besweeet said:**
> ...

How'd you get it working?

I presume that he used Windows *inside of* VirtualBox, the host being Ubuntu 9.10. 

And judging by things over at [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336") in regards to getting Office 2010 working, things aren't getting any better. I'll try the installer out with the most recent version of Wine and see if that gets anywhere.

---

### Post by besweeet on 2010-01-16
Any luck? :popcorn:

---

### Post by Vignesh S on 2010-01-16
Nope :-( I tried it with Wine 1.1.36, and it didn't want to work. Same problem as usual: didn't want to go past around 2/3 of the installation. But good news is at hand: Crossover is committed to getting Office 2010 to work. And who knows? It might even work in the next release of it :-D

Until then, we are stuck with trying to get it to work with Wine, which isn't always guaranteed ;-)

---

### Post by gemygk on 2010-02-01
Could anyone tell how to install msxml 6.10.1129.0 in the bottle??

Thanks in advance..:P

---

### Post by Vignesh S on 2010-02-02
You have to download it first (a google search should come up with [this]("http://www.microsoft.com/downloads/details.aspx?FamilyID=D21C292C-368B-4CE1-9DAB-3E9827B70604&displaylang=en")). After downloading the XP file, you just right click it and click on "Open with "Wine Windows Program Loader"". 

It will go through the setup without much problems. 

And it looks like Crossover is working on it, judging by their latest entry in their blog.

---

### Post by blazemore on 2010-02-02
Better way:
```
wget http://www.kegel.com/wine/winetricks; sh winetricks msxml6
```

---

### Post by Vignesh S on 2010-02-03
Oooh, I just realised that since Crossover provides all of its changes back to Wine, Office 2010 will also work in Wine too (once Crossover gets around to getting it to work :))

---

### Post by besweeet on 2010-03-18
CrossOver 9.0 is out. I've seen quite a few programs that are now working where they wouldn't work before (like iTunes 9). Maybe someone could try it out? Microsoft made some weird auto-downloader/installer thing instead of a regular EXE installer (probably can be found on a torrent though).

---

### Post by beadrifle on 2010-04-30
Bump.

Has crossover support for Microsoft office 2010 arrived as yet?

---

### Post by besweeet on 2010-04-30
> **beadrifle said:**
> Bump.

Has crossover support for Microsoft office 2010 arrived as yet?

Nope. They're still working on it.

---

### Post by binamenator on 2010-05-09
I tried open it with Open office (right click. Open as open office) but it takes forever and dosn't work :(. And with Wine Beta it says I need to download MSXML I6.10.1129.0 But when I tried to look it up on the internet it only offers it for Windows XP or 7 or any other Windows program.
I'm so confused. Help! :confused:

---

### Post by Ibidem on 2010-05-11
See post #29

---

### Post by dino99 on 2010-05-12
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=31](http://appdb.winehq.org/objectManager.php?sClass=application&iId=31)

---

### Post by binamenator on 2010-05-12
> **Ibidem said:**
> See post #29
Sorry.. I didn't see that. thanks for the help, but it still doesn't work...
It says Microsoft Professional Plus encountered an error during setup.

---

### Post by abdusamed on 2010-11-15
Maybe another reason it probably is't working is because .netframework 3.5 doesn't exist on wine right now which is a huge set back. Almost all then new application work with it!

If anyone knows how to get it working.. it would be interesting...

---

### Post by ktneely on 2011-01-14
Evernote 4 has a silver medal on the [Codeweavers page]("http://www.codeweavers.com/compatibility/browse/name/?app_id=8179").  I think it uses .Net framework 3.5.

---

### Post by Worp8d on 2011-04-30
> **dBuster said:**
> I have gotten past that msmxl or what ever that error is, and have gotten it to look like it has installed and then near the end it pops up and tells me setup has failed...


I'm using Wine and I get the same error (presumably, there's no way to tell what's going on with good old MS)

---

### Post by Worp8d on 2011-04-30
[http://www.junauza.com/2010/04/how-to-install-microsoft-office-on.html](http://www.junauza.com/2010/04/how-to-install-microsoft-office-on.html)

A start perhaps?  If there's someone who knows more about the workings Office...

---

### Post by samMD on 2011-05-18
Supposedly Play on Linux now has an option to install Office 2010 now.. There is a script on there website that allows you to do that..

here is a link to the script [http://www.playonlinux.com/repository/?script=801]("http://www.playonlinux.com/repository/?script=801")

Im trying to click "install this program" but nothing is happening maybe I should pop in the office 2010 CD first? 

Ill attempt again later this week

---

### Post by StrayEddy on 2011-05-18
Simple,
 
Use LibreOffice ;)

---

### Post by maxmiaggi on 2011-05-23
Hello everyone..

I am a newbie to the world of linux. I tried installing office 2010 using PlayOnLinux.. The following error pops up in the midst of the installation (check the attachment)..

any idea what is it all about? how to tackle it??

thanks

---

### Post by eltonw on 2011-05-23
> **maxmiaggi said:**
> Hello everyone..

I am a newbie to the world of linux. I tried installing office 2010 using PlayOnLinux.. The following error pops up in the midst of the installation (check the attachment)..

any idea what is it all about? how to tackle it??

thanks
It means you have to configure WINE to run Office 2010.
IMVHO, I don't understand:roll: why people are beating themselves over their heads with this when you have the **_[COLOR="Red"]free[/COLOR]_** OPEN OFFICE /LIBRE OFFICE suites ....which are *_native_* linux appliations

The current version of Ubuntu (11.04 AKA "Natty Narwahl" comes with LibreOffice 3.0 installed.
[COLOR="Red"]**REF:**[/COLOR] 
[ww.openoffice.org/]("ww.openoffice.org/")
[www.libreoffice.org/download/]("www.libreoffice.org/download/"):lol:

---

### Post by Jagoly on 2011-05-27
Exactly. The only real use for ms office os for testing out (very complicated) layouts before giving a document to another ms office user. In this case case, just install it in windows. Which I'm sure that 99% of people that have office 2010 (legally) have.

In my case, I have office 2007 working perfectly in wine. Probably better for this purpose, as most ms office users have this version.

---

### Post by dBuster on 2011-05-27
Does anyone know if you can get the latest versions of Open Office/Libre Office to emulate the Microsoft office 10??  

I mean the setup, layout, etc...  

If so then there definitely, IMO, no reason for using the microsoft software...  

Would be another reason if I could configure the two to emulate the one for me to migrate my in-laws from their microsoft grasp...  They are sticking with an old and I mean 5 or 6 year old, if not older, because my mother in law, bless her heart, says that all new computers now are coming with windows 7 and she needs them to have windows 10 as that is what she is using at work.  I tried to explain the difference but it was futile.  

So

If I can get open office/libre office to emulate version 10 of the microsoft software I might be able to convert another household...

---

### Post by Jagoly on 2011-05-27
> **dBuster said:**
> Does anyone know if you can get the latest versions of Open Office/Libre Office to emulate the Microsoft office 10??  

I mean the setup, layout, etc...  

If so then there definitely, IMO, no reason for using the microsoft software...  

Would be another reason if I could configure the two to emulate the one for me to migrate my in-laws from their microsoft grasp...  They are sticking with an old and I mean 5 or 6 year old, if not older, because my mother in law, bless her heart, says that all new computers now are coming with windows 7 and she needs them to have windows 10 as that is what she is using at work.  I tried to explain the difference but it was futile.  

So

If I can get open office/libre office to emulate version 10 of the microsoft software I might be able to convert another household...

My head hurts...

---

### Post by collisionystm on 2011-05-27
Office 2010 installed fine for me on on Play on Linux with Natty.

Only 2 things

Cant activate over the internet

I get a 'not enough memory' error when trying to open a local spreadsheet

---

### Post by Jagoly on 2011-05-28
I couldn't get it to to activate either. I had to resort to using a crack. I didn't really feel bad. It was a legal copy after all.

but I cant get the service packs to install. Which is annoying cause I can't open normal open document files.

---

### Post by NormanFLinux on 2011-05-28
Try Crossover. Its a proprietary version of WINE. It should better support Office and other Microsoft applications.

You set up a "Bottle" - which is like a virtual Windows OS and add your applications to it. They live there after installation.

---

### Post by rhoffmann on 2011-11-02
I use VMWare viewer for Linux.  It's a bit clunky as it is a true virtual machine tool and not like WINE, but once setup I have a WinXP desktop running.  I loaded XP Pro, SP3, and current hotfixes for security.  Then I installed purchased copies of Office 2010, Visio 2010, and Project 2010.  Once all three were activated I disabled the virtual machines internet connection through VMWare.  I share my home folder through VMWare (looks like a shared drive in WinXP) and can access any file I need.  When I can I convert these docs back to older versions (like .doc for 97/2000/XP) as those tend to be more LibreOffice compatible.  Works for me as I only need Office 2010 for a contract job I'm on.  Everything else I do using LibreOffice or other FREE tools on Linux.  I just joined the Ubuntu and Linux crowd a few months ago and I am lovin it...

---

### Post by Andre-D on 2011-11-03
for what it's worth:
I used Outlook 2007 - until I switched to Outlook 2010 (web-app) - running in browser.
I don't care much for the rest of the office, OpenOffice/LibreOffice does a good job, and most of my business contacts have it, or even prefer it.

---

### Post by BillyBoa on 2011-11-05
If Ubuntu cannot work with MS Office 2010, this is a major drawback. Most of us need to work with Office. If you work without sharing files with other MS Office users it's ok, but when you are sharing files, and specially Powerpoint presentations, it's a mess.
So the sooner Ubuntu finds a solution, the better for all of us.

---

### Post by FlyingIsFun1217 on 2011-11-10
> **BillyBoa said:**
> If Ubuntu cannot work with MS Office 2010, this is a major drawback. Most of us need to work with Office. If you work without sharing files with other MS Office users it's ok, but when you are sharing files, and specially Powerpoint presentations, it's a mess.
So the sooner Ubuntu finds a solution, the better for all of us.

Office 07 runs well enough in wine, and you can install a compatibility program that allows it to open 2010 files.

FlyingIsFun1217

---

### Post by Andre-D on 2011-11-11
I assume all of your checked out Crossover:  [http://www.codeweavers.com/compatibility/browse/name/?app_id=7437](http://www.codeweavers.com/compatibility/browse/name/?app_id=7437)

And gave your votes for individual office application (click on them and look around) or pledged ?

That's mostly likely the method it will start working - by putting money into WINE - Microsofts always seeks to mess-up for Linux community, and this time, while they're sh**ing their p*nce when seeing success of Android(/basically Linux)  - they are not very likely to ever compile their greatest lock-in mechanism for Linux.
Let's face it - the office lock-in is what keeps many users paying microsoft for the daily bloat.

---

### Post by mb36 on 2011-11-20
There is a very recent report (7 Nov, 2011) at the Wine website ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336)) of Microsoft Office Professional Plus 2010 working with ubuntu 11.10 using Wine 1.3.32. It has been given silver status and there are installation instructions.

However I didn't get it to work all the way, myself, but there seems to be hope.

---

### Post by fenrir12 on 2011-11-30
Running Word 2010 with Ubuntu 11.10, 64 bit, through wine. Ran into a snag when winetricks .net framework 3.0 failed, but installed mono 2.8 and runs fine. I'm getting some weird behavior with opening files, but so far, so good!

---

### Post by bluexrider on 2011-11-30
> **connectnow said:**
> 3 months later NO SOLUTION.

No magic answer. Office IS a Microsoft Product. 
I prefer to use VM ware and run XP install Office there.

---

### Post by fenrir12 on 2011-11-30
I am encountering problems opening .docx files saved in Libreoffice through my install. Word prompts me to check the file permissions for the document or drive. Any suggestions on how to resolve this? I have run winecfg and auto-dectected the drives, is there further steps I need to take? I never had issues under Word 2007.....

---

### Post by cherry316316 on 2011-12-29
use "playonlinux" 
its free and it has full support for upto office 2007.

---

### Post by LoveToSail on 2012-08-15
So what is the best way to get Office 10 working?
 
I tried loading with PlayOnLinux and Wine and got the same error message about 2/3 way through Setup.
 
Help!

---

### Post by erguille on 2012-10-26
Update to last version of play on linux, or the last version of wine and it should work. To do so run:

```
wget -q \"http://deb.playonlinux.com/public.gpg\" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_precise.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-add-repository -y ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install -y libjpeg62:i386 wine1.5 playonlinux
```

crossover is easier and more automated, and it's only 30 bucks

the other thing that could be going wrong is the version of your office 2010, if it doesn't install with crossover 11 that means you should get the original trial version from MSDN and then upgrade it with your KMS key if you have one, I'm making an autoinstaller for wine 15 but I it's not ready yet, I hope this helps Cheers

---

