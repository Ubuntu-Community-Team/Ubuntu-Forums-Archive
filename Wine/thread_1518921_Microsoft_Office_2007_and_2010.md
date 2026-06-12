---
title: "Microsoft Office 2007 and 2010"
date: 2010-06-27
forum: Wine
---

### Post by jereece on 2010-06-27
I have been using Ubuntu at home for the past year learning and gaining experience a little at a time.  I went into this understanding there would be a learning curve, but I would push forward an try to make things work.  For the most part, I have done that.  However the one thing I am still disappointed in is Open Office.  I always have frustrating problems when I bring a document, spreadsheet or database home and want to work on it.  OO always seems to mess up the document.  It's clear that in order to make this work for me I must have Microsoft Office.  My question is, has anyone successfully installed Microsoft Office 2007 or 2010 (just released) on Ubuntu?  If so, how do I do it?  I have successfully installed some programs via Wine but those were small programs I downloaded.  Any suggestions is greatly appreciated.

Jim

---

### Post by wpshooter on 2010-06-27
> **jereece said:**
> I have been using Ubuntu at home for the past year learning and gaining experience a little at a time.  I went into this understanding there would be a learning curve, but I would push forward an try to make things work.  For the most part, I have done that.  However the one thing I am still disappointed in is Open Office.  I always have frustrating problems when I bring a document, spreadsheet or database home and want to work on it.  OO always seems to mess up the document.  It's clear that in order to make this work for me I must have Microsoft Office.  My question is, has anyone successfully installed Microsoft Office 2007 or 2010 (just released) on Ubuntu?  If so, how do I do it?  I have successfully installed some programs via Wine but those were small programs I downloaded.  Any suggestions is greatly appreciated.

Jim

Jim:

    I really hate to say this, but I see what you are mentioning here as the ultimate downfall of Ubuntu, i.e. its non-ability to successfully run (or to have the vendors of M/S compatible applications write their applications to run NATIVELY under Ubuntu).  I'll say that if the aforementioned does not happen fairly soon, the people that are investing so much money in Ubuntu will lose interest in it and that will be its demise, what a shame !!!

    But good luck.

---

### Post by jereece on 2010-06-27
I agree.  I am really trying to make Ubuntu work for me at home but I need to bring documents, spreadsheets and Access database home to work on.  Right now, I can't successfully do that in Ubuntu because of OO.  OO has really messed up some of my documents and the functionality is not there that I need.  I am currently dual booting but that's a hassle.  

Jim

---

### Post by Jerry N on 2010-06-27
I haven't tried running Office 2007 and Office 2010 in Ubuntu but I do run Office 97 and I have had a lot better luck getting it to run correctly under Codeweaver's Crossover than I have had with Wine, particularly the recent versions of Wine that get installed with Ubuntu 9.10 and 10.04.  And I find that Word 97, Excel 97, and Powerpoint 97 running under Crossover perform quite a bit better than the corresponding OpenOffice applications.  The Crossover web site would have information on its compatibility with Office 2007.  Office 2020 is probably too new.  OpenOffice does a few things, such as creating PDF files, that Microsoft Office doesn't do.  

Crossover costs a few dollars and uses Wine as its basis.
BTW, I have not tried Access under crossover. 

Jerry

---

### Post by cogier on 2010-06-27
Office 2003 seems to work very well with Wine without modification.

---

### Post by macstar on 2010-06-27
> **jereece said:**
> I have been using Ubuntu at home for the past year learning and gaining experience a little at a time.  I went into this understanding there would be a learning curve, but I would push forward an try to make things work.  For the most part, I have done that.  However the one thing I am still disappointed in is Open Office.  I always have frustrating problems when I bring a document, spreadsheet or database home and want to work on it.  OO always seems to mess up the document.  It's clear that in order to make this work for me I must have Microsoft Office.  My question is, has anyone successfully installed Microsoft Office 2007 or 2010 (just released) on Ubuntu?  If so, how do I do it?  I have successfully installed some programs via Wine but those were small programs I downloaded.  Any suggestions is greatly appreciated.

Jim


office 2007 is very easy to install on ubuntu 10.04. i have done it several times.

you need wine and some other vb files for it.

```

sudo aptitude install wine1.2
sudo aptitude install cabextract
wget http://www.kegel.com/wine/winetricks

```

then:
you can copy paste all these at once!
```

sh winetricks dotnet11
sh winetricks gdiplus
sh winetricks vb3run
sh winetricks vb4run
sh winetricks vb5run
sh winetricks vb6run
sh winetricks msxml3
sh winetricks msxml4
sh winetricks msxml6
sh winetricks riched20
sh winetricks riched30
sh winetricks vcrun6

```

after you are done with that, just run the setup.exe on office 2007 dvd, install the program. you ll find it in applications, wine, programs folder after installation finished.

---

### Post by nacho32 on 2010-06-27
if all fails and you must have MS office I would just run a dual boot, saves the head-ache for them windows programs you must have and it's fun for the whole family:)

---

### Post by Mark Phelps on 2010-06-27
The WineHQ page below shows the results of trying to install MS Office in Wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=31]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=31")

The results for Office 2010 are dated, but it's unlikely that they are any better now.

---

### Post by jereece on 2010-07-03
macstar - When you install Office 2007, does Access and Outlook work?  I use these probably more than Word and Excel.

---

### Post by metalf8801 on 2010-07-03
Office 2007 can be run using Wine or crossover office but there are problems for example I noticed spell check underlining lots of words that were spelled correctly  

there are other versions of Open Office that might work better but I haven't tested them yet 
[LIST]
[*]go-oo claims to have better support then openoffice.org for Microsoft Office binaries [http://www.go-oo.org/](http://www.go-oo.org/)
[/LIST]
**Edit** Sorry Go-oo is the version of Openoffice that comes with Ubuntu
[LIST]
[*]Novell Makes its own version of Openoffice.org but I'm not use if you can use it on Ubuntu [http://www.novell.com/products/desktop/features/ooo.html](http://www.novell.com/products/desktop/features/ooo.html)
[/LIST]
[LIST]
[*]Oracle Open Office [http://www.oracle.com/us/products/applications/open-office/index.html](http://www.oracle.com/us/products/applications/open-office/index.html)
[/LIST]

and
There are other Office suite that run on Linux some are FOSS like Koffice  others are just free as in beer depending on how you are using them like IBM's lotus symphony and some you can try for free with a 30 day trials like SoftMaker Office 

[http://www.koffice.org/](http://www.koffice.org/)

[http://symphony.lotus.com/software/lotus/symphony/home.nsf/home](http://symphony.lotus.com/software/lotus/symphony/home.nsf/home)

[http://www.softmaker.com/english/of_en.htm](http://www.softmaker.com/english/of_en.htm)

those are just a few examples 

If you try any of these alternatives please report your findings 
good luck  
Dan



PS
Does anyone know if the online version of Microsoft Office 2010 can be used when running Linux?

---

### Post by sgage on 2010-07-03
Outlook 2007 works under wine/crossover. I just tried installing Office 2007 using the "recipe" given above, and Access does NOT work. It did not work using the last version of Crossover Office I tried, but that was a while ago. Go to their website and ask there - they will tell you straight.

In Office 2000 under wine/crossover, everything works, including Access. I've never tried Office 2003.

---

### Post by macstar on 2010-07-03
> **jereece said:**
> macstar - When you install Office 2007, does Access and Outlook work?  I use these probably more than Word and Excel.


sorry, about access and outlook i cant tell you anything, as these are the programs i never install. 

i know excel, word and publisher and powerpoint are working.

---

### Post by Mark Phelps on 2010-07-03
In MS Office 2007, neither Access nor Outlook will work with Wine or any of their variants.

I suspect that None of Office 2010 will work, but there are no recent testing results in the Wine repository to confirm that.

---

### Post by holycow131415 on 2010-07-03
get playonlinux.

i installed office 2007 using it, and word,excel, powerpoint, publisher and infopath do work. outlook did start up, but i did not set up an email account with it to test. access is not starting up.

---

### Post by jereece on 2010-07-03
Well that's just great.  I guess I am still forced to keep ties with Windows.  I was hoping to get away totally.

---

### Post by ajwho on 2010-07-03
> **jereece said:**
> Well that's just great.  I guess I am still forced to keep ties with Windows.  I was hoping to get away totally.
Would it be possible to virtualize Windows and then run MS Office from there?

---

### Post by rollin on 2010-07-03
Hi OP! If you want an insane approach and idea that in all honesty probably still won't work you could try copying a windows installation into the wine directories!

I know it is a little crazy but a suggestion all the same! I only mentioned it because unixmen.com did a guide on installing Adobe CS4 in Jaunty which worked for me: 
[http://www.unixmen.com/linux-tutorials/324-install-dreamweaver-cs4-in-ubuntudebian](http://www.unixmen.com/linux-tutorials/324-install-dreamweaver-cs4-in-ubuntudebian)

Totally different software I agree but the concept and some of the instructions might work! It's probably worth pointing out here that I haven't attempted this with Office at all.

Probably more hassle than it's worth but just an alternative idea!

---

### Post by Leppie on 2010-07-03
install VirtualBox PUEL edition and create an XP virtual machine.
this way you can continue using Ubuntu and have access to MS Office at the same time.
you can share folders, access cd-rom, usb devices, and even copy and paste between host and vm.

if you already have windows on your machine and have an installation disc for it, you can easily install it in a virtual machine. no problem with licensing either, as it still is the same machine.

---

### Post by dcstar on 2010-07-03
> **jereece said:**
> I have been using Ubuntu at home for the past year learning and gaining experience a little at a time.  I went into this understanding there would be a learning curve, but I would push forward an try to make things work.  For the most part, I have done that.  However the one thing I am still disappointed in is Open Office.  I always have frustrating problems when I bring a document, spreadsheet or database home and want to work on it.  OO always seems to mess up the document.  **It's clear that in order to make this work for me I must have Microsoft Office**. 
........

No, just do not use the latest MS 2007/2010 format for saving documents, use the other options available - like the older document versions that are actually supported by OO.

It is the same issue when you have to send to people who still only use Office 2003, **you** have to change the format so they can use the documents.

---

### Post by jimmers on 2010-07-04
I agree with DC Star, I always save MS Docs under 97/2000/XP format, and have never had any problems, I also run Windows in VM, and have Office 2007 installed which works really well,  but I never use, with any frequency.

You can but try.

Jim

---

### Post by dcstar on 2010-07-04
> **jimmers said:**
> I agree with DC Star, I always save MS Docs under 97/2000/XP format, and have never had any problems, I also run Windows in VM, and have Office 2007 installed which works really well,  but I never use, with any frequency.

You can but try.

Jim
People have to realise that if Microsoft made their formats easy for others to use then the billions of dollars that they make from regular "upgrades" to Office would disappear.

The 98% of functions that are most used in Office apps have changed little over the last 20 years, yet people have been forced to spend billions for new versions of tools that basically do the same thing as the old versions.

Microsoft make it as hard as they possibly can for anyone to reverse-engineer their proprietary formats, it is a wonder that OO can actually do what it does so well and a credit to the developers that it can.

If people want compatibility, then **stop** using Office in Windows and use OO in Windows - all these problems will then go away no matter what platform you want to use.

---

### Post by jereece on 2010-07-04
Some of you are hearing what I am saying.  My employer uses Microsoft Office.  I do a lot of work at home in Microsoft Access and Outlook plus a little in Word and Excel.  I have tried using Open Office for some time but even for Word documents OO has messed them up.  For example, I recently opened a password protected document that contained a simple table.  OO prompted me for the password to open just fine, however after saving my changes I later discovered that OO unprotected the document without me knowing it.  OO also royally messed up my table.  Not to mention that OO won't run my Access databases.  So, for now I must have Microsoft Office.  We are currently running 2007 and plan to migrate to 2010 next year.  I would like to get away from Windows totally at home but Office is the main thing preventing me from being successful. I guess I'll have to continue dual booting.

---

### Post by dbowlin17 on 2010-07-04
dual boot or try wine? i never have really had much success with wine, but then again my computer is a 2ghz p4 with 1.5 gb of rambus... that might be why.

---

### Post by philinux on 2010-07-04
Moved to Wine forum

---

### Post by Skara Brae on 2010-07-04
> **dcstar said:**
> People have to realise that if Microsoft made their formats easy for others to use then the billions of dollars that they make from regular "upgrades" to Office would disappear.

The 98% of functions that are most used in Office apps have changed little over the last 20 years, yet people have been forced to spend billions for new versions of tools that basically do the same thing as the old versions.

Microsoft make it as hard as they possibly can for anyone to reverse-engineer their proprietary formats, it is a wonder that OO can actually do what it does so well and a credit to the developers that it can.

If people want compatibility, then **stop** using Office in Windows and use OO in Windows - all these problems will then go away no matter what platform you want to use.
Well said, dcstar!!!

-oo-

For example: I have been reading up on the "problems" with Microsoft's version of the OpenDocument format ("Office Open XML", who comes up with that name to begin with?). I tell you: they do that on purpose...

As a "punishment", everyone should dump MS Office and switch to OOo (or at least, *try*...).

The arrogance of Microsoft, because of their monopoly, personally angers me so much that I even refuse to buy mice or keyboards from Microsoft (i.e. with the name on it).

There is nothing wrong with making money... but when a business or shop stops treating me with the respect that I as a potential customer deserve, then I get very, very angry.

---

### Post by Tombgeek on 2010-07-05
> **Skara Brae said:**
> Well said, dcstar!!!

-oo-

For example: I have been reading up on the "problems" with Microsoft's version of the OpenDocument format ("Office Open XML", who comes up with that name to begin with?). I tell you: they do that on purpose...

As a "punishment", everyone should dump MS Office and switch to OOo (or at least, *try*...).

The arrogance of Microsoft, because of their monopoly, personally angers me so much that I even refuse to buy mice or keyboards from Microsoft (i.e. with the name on it).

There is nothing wrong with making money... but when a business or shop stops treating me with the respect that I as a potential customer deserve, then I get very, very angry.


Of course, Microsoft has been doing that for years. They deliberatly place code in their software to prevent them from running under WINE, so that you are forced to move away from Mac OS and Linux to Windows.
Microsoft actually got sued by USA because of their monopoly, and there was evidance that Microsoft deliberatly made it difficult to install third-party web browsers, so that people only use Internet Explorer.
And I think they mentioned that Windows actually crashed when IE was removed.
I can't remember so well, but here is the article if you want to read up more about it.
[http://en.wikipedia.org/wiki/United_States_v._Microsoft](http://en.wikipedia.org/wiki/United_States_v._Microsoft)

Unfortunaly, I am still forced to use Windows for school.

---

### Post by Leppie on 2010-07-05
> **Tombgeek said:**
> And I think they mentioned that Windows actually crashed when IE was removed.
internet explorer is one of the core parts of windows. there basically is no difference between windows explorer and internet explorer (never wondered why a url opens normally when pasted into windows explorer?) as it apparently is the same thing.

---

### Post by skyiscrying on 2010-08-31
Latest Open Office runs real well on Windows Vista and Windows 7. Runs real good on Ubuntu 10.04 too, of course. I have tried MS Office 2007 on Ubuntu 10.04 using Crossover from Codeweavers but the fonts don't look as nice as when using it on Windows. Access will not run on Ubuntu either and I haven't investigated KEXI of late so I don't know how that data base is going along. 
A simple data base can be made by using Calc in Open Office. 

Dual Boot if you want the best of both worlds.

---

### Post by jre6 on 2010-08-31
[LIST]
[*]Install *Wine*
[*]Select Applications>Wine>Configure Wine to bring the Wine Configuration dialog box.
[*]Select *Windows Version* as *Windows Vista* from the *Applications Tab*
[*]Override two dll files rpcrt4.dll and msxml3.dll from Libraries tab. Override them to be Native (Windows)
[*][Download rpcrt4.dll file. Click here and save it on your desktop.]("http://rds.yahoo.com/_ylt=A0oG72O_yXxMJ30AR2JXNyoA;_ylu=X3oDMTEzNjlpbjg5BHNlYwNzcgRwb3MDMwRjb2xvA2FjMgR2dGlkA0g2MTlfMTU2/SIG=12ei9194e/EXP=1283332927/**http%3a//www.dll-files.com/dllindex/dll-files.shtml%3frpcrt4")
[*]Open the c_drive from Wine menu
[*]Delete rpcrt4.dll and  msxml3.dll files from Windows/System32 directory.
[*]Copy the downloaded rpcrt4.dll file into Windows/System32 directory
[*]Download msxml3.msi file from Microsoft download site ([here is the direct link for your convenience]("http://www.microsoft.com/downloads/details.aspx?FamilyID=28494391-052b-42ff-9674-f752bdca9582&DisplayLang=en")).
[*]Install msxml3.msi file from the Terminal window by issuing msiexec /i msxml3.msi
[*]Double click on setup.exe file from your MS  Office 2007 installation CD. If it doesn’t work just type wine setup.exe  from the Terminal window.
[*]Follow the normal installation procedures.
[/LIST]

efore you install Office 2007 don’t forget about winetricks. It might help to resolve many issues. Just go to [this link]("http://www.kegel.com/wine/winetricks"), copy the text (codes) in a file winetrick. From the terminal window type sh winetricks. Check all the msxml stuffs and click install.

---

