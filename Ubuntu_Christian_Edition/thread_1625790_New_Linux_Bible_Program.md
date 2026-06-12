---
title: "New Linux Bible Program"
date: 2010-11-19
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2010-11-19
Ok, I came across another Bible program for Linux.  Runs native in Linux.  You can see how to install it here:  [http://www.bibleanalyzer.com/forum/viewtopic.php?f=7&t=196#p698](http://www.bibleanalyzer.com/forum/viewtopic.php?f=7&t=196#p698)

I didn't feel like re-writing up the how to that I put there (but now I did).  Since you are probably already registered for these forums, you can feel free to post problems here and I will get back with you.  Enjoy.

[CENTER][SIZE="4"]How to Install Bible Analyzer[/SIZE][/CENTER]
[COLOR="Red"]Lucid and Maverick are the only ones currently supported.[/COLOR]
Ok, the quick how to for installing Bible Analyzer:
1.  In the Terminal **Applications -> Accessories -> Terminal** Copy and paste this:
```

sudo add-apt-repository ppa:shane2peru/bibleanalyzer-stable

```
2.  Again in the terminal:
```
sudo apt-get update
```
3.  And finally in the terminal:
```
sudo apt-get install bibleanalyzer
```

That simple.  There are GUI instructions in the link above if you have terminalphobia. :)  They are longer.

Shane

---

### Post by jonathonblake on 2010-11-21
> **shane2peru said:**
> Ok, I came across another Bible program for Linux.  Runs native in Linux. 


Two points:
* The resources are self installing executables that require WINE;
* It seems strange to me that with such a strong pro-1611-kjv position, they do not offer the entire 1611 KJV;


jonathon

---

### Post by shane2peru on 2010-11-22
> **jonathonblake said:**
> Two points:
* The resources are self installing executables that require WINE;
* It seems strange to me that with such a strong pro-1611-kjv position, they do not offer the entire 1611 KJV;


jonathon

We still need to make provision for installing the resources, although it is very easy to do manually without wine.  Simple right click on the resources and select extract here.  A $App folder or something similar will appear, inside that folder you can copy the folder inside several folders and get the resource and put it in your home directory inside .bibleanalyzer/modules/ 

As for the second question/comment, the 1611 is offered in form of the 1769, of which the changes are merely spelling changes, from the 1611 to the 1769.  We aren't here to debate beliefs or opinions so simply stated, we reject the Apocrypha as being a part of the Scriptures and we are aware of the fact that it was included in the 1611, however they didn't believe it to be Part of the Scriptures, but included it for it's historical content.  That is our position, and why it is not included in Bible Analyzer.  Perhaps the Bible Analyzer author would have more to comment on that, but that is sufficient for here.

Shane

---

### Post by MoreRam on 2010-11-22
I have posted on BibleAnalyzer in this forum before, but not for some time.

BibleAnalyzer is the program I use in Ubuntu. I very much prefer it over all others. It is easy to install and does not require Wine. 

The author of BibleAnalyzer appears to be a Fundamentalist. He also appears to believe that the KJV is actually inspired rather than just highly anointed. These positions do not affect my use of Bibleanalyzer in any way whatsoever. It is still just a very excellent program.

I am the opposite of a Fundamentalist in theological belief, and I hold, like Martin Luther's catechism, that it is simply not possible for a translation to be inspired -- which is contrary to the biblical principles of establishing canon. However, I find this software extremely useful and of the best quality. 

In English, I prefer the KJV, and I am most satisfied with the BibleAnalyzer edition of this translation. It is excellent and extremely easy to use.

I highly recommend this software to all Linux users (and even Windows users).

---

### Post by ubuntu27 on 2010-11-22
I love this Bible program.

But I have a beef with their modules. Even though Bible Analyzer itself is available for Linux, the modules come with exe format.

I was not able to extract the exe files in Linux. 
This left me with two choices:

1) Use a Windows machine, download the exe modules, and extract. Later copy the extracted files to Linux.

2) Use Wine to load Linux Analyzer and the modules


Option #1 is very cumbersome, it takes time. It also dishonor Linux users by requiring Windows OS.

Option #2: Not everyone wants to use Wine. And why build a native Linux program which will not work?


Perhaps it will be a great idea if the modules are repackaged and added to the PPA. What do you think Brother Shane? ;-)

EDIT:

> **shane2peru said:**
> We still need to make provision for installing the resources, although it is very easy to do manually without wine.  Simple right click on the resources and select extract here.  A $App folder or something similar will appear, inside that folder you can copy the folder inside several folders and get the resource and put it in your home directory inside .bibleanalyzer/modules/ 

Shane

I have tried extracting the exes with multiple methods such as right clicking and extract, open with cabextract, 7-zip for Linux, gzip, p7zip, etc. None were successful. :(

---

### Post by shane2peru on 2010-11-22
> **ubuntu27 said:**
> I love this Bible program.

But I have a beef with their modules. Even though Bible Analyzer itself is available for Linux, the modules come with exe format.

I was not able to extract the exe files in Linux. 
This left me with two choices:

1) Use a Windows machine, download the exe modules, and extract. Later copy the extracted files to Linux.

2) Use Wine to load Linux Analyzer and the modules


Option #1 is very cumbersome, it takes time. It also dishonor Linux users by requiring Windows OS.

Option #2: Not everyone wants to use Wine. And why build a native Linux program which will not work?


Perhaps it will be a great idea if the modules are repackaged and added to the PPA. What do you think Brother Shane? ;-)

EDIT:



I have tried extracting the exes with multiple methods such as right clicking and extract, open with cabextract, 7-zip for Linux, gzip, p7zip, etc. None were successful. :(

You are right, and we will get this fixed as soon as we can.  I had forgot about this issue, and it is a very legitimate complaint/problem.  We will get to work on this to fix this, and make it 100% Linux friendly.  The program itself is written in Python or (wxPython?) I'm not a programmer, but know that it runs native in Linux, and that is where my enthusiasm kicks in.  I apologize to those trying to get modules installed.  We will get this fixed.

Shane

---

### Post by ubuntu27 on 2010-11-22
Shane, you are working with Bible Analyzer team now? Thank you for accepting our inputs.

I will look forward to the new Linux friendly modules.


Oh, could you tell the Bible Analyzer developers to please include other Linux package so that non-Ubuntu Users could install them as well? Of course we could use Alien, but it is not full-proof.
Perhaps [Linstaller]("http://listaller.nlinux.org/"), and [Zero Install]("http://zero-install.sourceforge.net/") might be useful.

---

### Post by shane2peru on 2010-11-22
> **ubuntu27 said:**
> Shane, you are working with Bible Analyzer team now? Thank you for accepting our inputs.

I will look forward to the new Linux friendly modules.


Oh, could you tell the Bible Analyzer developers to please include other Linux package so that non-Ubuntu Users could install them as well? Of course we could use Alien, but it is not full-proof.
Perhaps [Linstaller]("http://listaller.nlinux.org/"), and [Zero Install]("http://zero-install.sourceforge.net/") might be useful.

Well the ppa specified in the first post is my ppa.  Here is the problem.  The developer is not really a Linux user/enthusiast, but is a python developer, and did actually make the original debs.  Having tried his app, I liked the way it looks, runs in Linux in some regards better than any Bible app that we currently have in Linux.  So being a Linux enthusiast, I set out to help get it out to Linux users in an easier format.  That being said, I'm not a dev, and have limited time, but am helping in any way that I can.  Converting it to rpm, is out of my class, I'm a 100% Ubuntu/debian user.  I have dabbled with rpm (Fedora, OpenSuse, Mandriva, etc.) but I just have too much on my plate to learn another packaging methods.  No opposition to it, just no time.  I will let you know when we have the modules setup for Linux.  Should be soon.

Shane

PS - Thanks for the links, I did look at them, and they do look interesting.

---

### Post by shane2peru on 2010-11-23
Ok, thanks to the developer we now have bz2 modules available to download.  He was quick in getting them up.  They are on the web page.  For any bought modules, you will have to contact him, and he will be able to get you the module in bz2 file.  It at least eliminates the need for wine.  Modules should be placed in your USER directory inside the hidden folder (View -> Show Hidden or ctrl + h in nautilus) find the .bibleanalyzer folder  then Modules, and there are ones for Bible, Commentary, Devotion, Dictionary and Text.  Select the appropriate folder and you can put the module there. I noticed on one of my modules I had to add the .bib extension on the one because it didn't show up without it. 

Shane

---

### Post by ubuntu27 on 2010-11-23
Hello Shane. Say thank you to the developer and webmaster for me.

By the way, in the non-English Bible Bundle module, the Reina-Valera Gómez (RVG) Bible is from the draft of 2004 instead of the final version. :)


Thank you for all your hard work.
God bless thee.

---

### Post by MoreRam on 2010-11-23
OK, I just now went to the BibleAnalyzer module page [http://www.bibleanalyzer.com/modules.html](http://www.bibleanalyzer.com/modules.html)
and downloaded some free modules for experiment. Installing them was not easy, but it was not difficult either.

First I downloaded the free books bundle, which had a Linux .bz2 link. Then I went to my download folder and found the file. I right clicked and then clicked on extract here. This created a new folder with all the books which I opened. I went to my home folder and pressed ctrl h. This revealed all hidden folders, and I opened BibleAnalyzer, and then the modules folder. I moved the books to the Text folder. I then restarted BA, and in the upper left window clicked the books tab and then hit F3. The newly transferred books displayed.

I noted the KJ2000 had a Linux link. I downloaded it and extracted it. I dragged it into the Bible folder of the BibleAnalyzer folder of the home folder. However, it did not display on restarting BA. This file had no suffix but the same icon as the book files. So I tried it in the text folder but it did not display.

So I downloaded the free post AV Bibles, which had a Linux link, and extracted them. I put them in the Bible folder of BA in the home folder, and on restarting BA, they displayed.

My impression is, the .bz2 files on the BA Modules page work. I don't know what that KJ2000 file was about. However, only the free modules indicate a Linux link. Who knows if the modules for purchase have a Linux link. It would be interesting to test one of those, and there are some good resources there. But why pay $3 or $4 if one does not know if there is a Linux .bz2 file? All the free modules have a .bz2 file.

But at any rate, this is all fun I think.

---

### Post by shane2peru on 2010-11-23
> **ubuntu27 said:**
> Hello Shane. Say thank you to the developer and webmaster for me.

By the way, in the non-English Bible Bundle module, the Reina-Valera Gómez (RVG) Bible is from the draft of 2004 instead of the final version. :)


Thank you for all your hard work.
God bless thee.

Thank you for the kind comments!  I don't know if you noticed but the RVG 2010 module is available on the web page there as well.  

> **MoreRam said:**
> OK, I just now went to the BibleAnalyzer module page [http://www.bibleanalyzer.com/modules.html](http://www.bibleanalyzer.com/modules.html)
and downloaded some free modules for experiment. Installing them was not easy, but it was not difficult either.

First I downloaded the free books bundle, which had a Linux .bz2 link. Then I went to my download folder and found the file. I right clicked and then clicked on extract here. This created a new folder with all the books which I opened. I went to my home folder and pressed ctrl h. This revealed all hidden folders, and I opened BibleAnalyzer, and then the modules folder. I moved the books to the Text folder. I then restarted BA, and in the upper left window clicked the books tab and then hit F3. The newly transferred books displayed.

I noted the KJ2000 had a Linux link. I downloaded it and extracted it. I dragged it into the Bible folder of the BibleAnalyzer folder of the home folder. However, it did not display on restarting BA. This file had no suffix but the same icon as the book files. So I tried it in the text folder but it did not display.

So I downloaded the free post AV Bibles, which had a Linux link, and extracted them. I put them in the Bible folder of BA in the home folder, and on restarting BA, they displayed.

My impression is, the .bz2 files on the BA Modules page work. I don't know what that KJ2000 file was about. However, only the free modules indicate a Linux link. Who knows if the modules for purchase have a Linux link. It would be interesting to test one of those, and there are some good resources there. But why pay $3 or $4 if one does not know if there is a Linux .bz2 file? All the free modules have a .bz2 file.

But at any rate, this is all fun I think.

Ok, for the KJ2000  you need to right click on the file and select **Rename**  at the end of the name put: [COLOR="Blue"].bib[/COLOR]  and it should work after that.  As for the paid modules, for the time being you will have to email the developer and he will get them to you in a bz2 format.  He is working on fixing the store, the way the store is setup it is a little more complex though.  Lord willing we will make this a little more simple.  

Also version 4 will be coming soon to Linux, with many improvements.  

Shane

---

### Post by ubuntu27 on 2010-11-23
> **shane2peru said:**
> Thank you for the kind comments!  I don't know if you noticed but the RVG 2010 module is available on the web page there as well.  
 

Shane

Sorry my post wasn't clear.
Yes, there is a RVG 2010 package available, but only for Windows (exe), there is no .bz2 package.

---

### Post by MoreRam on 2010-11-23
> **shane2peru said:**
> 
Ok, for the KJ2000  you need to right click on the file and select **Rename**  at the end of the name put: [COLOR="Blue"].bib[/COLOR]  and it should work after that.  As for the paid modules, for the time being you will have to email the developer and he will get them to you in a bz2 format.  He is working on fixing the store, the way the store is setup it is a little more complex though.  Lord willing we will make this a little more simple.

Well, I renamed KJ2000 as you indicated and it all worked perfectly. Thank you. Looking at this Bible should be interesting.

I am interested in some of the paid modules, but I would prefer to wait until the developer has them ready. I hope he will post an announcement in the BA forum when they are ready, and then, I can give them a try.

I pray for BA in Linux from time to time, and I will continue to do so, and I am expecting this program to take off........ :)

---

### Post by shane2peru on 2010-11-23
> **ubuntu27 said:**
> Sorry my post wasn't clear.
Yes, there is a RVG 2010 package available, but only for Windows (exe), there is no .bz2 package.

Oh, you are right, I will check let him know about that!  Thanks!

> **MoreRam said:**
> Well, I renamed KJ2000 as you indicated and it all worked perfectly. Thank you. Looking at this Bible should be interesting.

I am interested in some of the paid modules, but I would prefer to wait until the developer has them ready. I hope he will post an announcement in the BA forum when they are ready, and then, I can give them a try.

I pray for BA in Linux from time to time, and I will continue to do so, and I am expecting this program to take off........ :)

No problem.  Version 4 has many improvements.  Hopefully the store thing will be setup/fixed soon. 

Shane

---

### Post by MoreRam on 2010-11-24
Shane,
Note that the modules page of the BA website states that downloading another set of Hebrew and Greek fonts is necessary for the display of words in some modules. Actually, I have not had any problem with displaying Greek or Hebrew in Ubuntu using other Bible programs. How necessary, do you believe, is this download for additional fonts? Does this font download work with Linux?

Thanks for the response.

---

### Post by shane2peru on 2010-11-24
> **MoreRam said:**
> Shane,
Note that the modules page of the BA website states that downloading another set of Hebrew and Greek fonts is necessary for the display of words in some modules. Actually, I have not had any problem with displaying Greek or Hebrew in Ubuntu using other Bible programs. How necessary, do you believe, is this download for additional fonts? Does this font download work with Linux?

Thanks for the response.

That is a good question, I have added a bunch of fonts to my system anyway, so on a default install, I'm not sure.  If your fonts don't display like the attached screenshot for the Greek text, then you probably need the fonts.  Greek and Hebrew fonts are probably going to be the problematic fonts.  **If anyone needs them, please post here and we will get you setup**.  The fonts that are on the Bible Analyzer would work, however the installer will not work for you.  

Shane

PS - Also I edited the first post to include quick easy installation instructions.

---

### Post by MoreRam on 2010-11-24
Shane,

What I meant was -- does the font installation offered at the BA website work with Linux, or only Windows? In the page you attached, the Greek fonts did display on my computer -- so maybe, that indicates I would not have a problem anyway. 

I am also going to post a link now to the developer's YouTube video demonstrating the software. This video demonstrates just how sophisticated this software is, although most people would not be interested in going to this depth of study. Still, the software is good just for reviewing Bible passages, looking at a commentary, or looking at a book. 

[http://www.youtube.com/watch?v=Y-AwB3_NYFw]("http://www.youtube.com/watch?v=Y-AwB3_NYFw")

Note that the developer seems to have a fine Texas accent.

---

### Post by shane2peru on 2010-11-27
> **MoreRam said:**
> Shane,

What I meant was -- does the font installation offered at the BA website work with Linux, or only Windows? In the page you attached, the Greek fonts did display on my computer -- so maybe, that indicates I would not have a problem anyway. 

I am also going to post a link now to the developer's YouTube video demonstrating the software. This video demonstrates just how sophisticated this software is, although most people would not be interested in going to this depth of study. Still, the software is good just for reviewing Bible passages, looking at a commentary, or looking at a book. 

[http://www.youtube.com/watch?v=Y-AwB3_NYFw]("http://www.youtube.com/watch?v=Y-AwB3_NYFw")

Note that the developer seems to have a fine Texas accent.

No what is currently offered would only work in Windows.  Thanks for the link!  I didn't know those were out there.

Shane

---

### Post by trulan on 2010-11-28
Thank you for an excellent piece of software!  I haven't had a lot of time to use it yet, but if my first impressions are accurate this is going to very quickly become my preferred Bible study program.

One (small) suggestion I would make:  It would be nice if the menu entry followed linux/freedesktop.org standards.  
[http://www.freedesktop.org/wiki/Specifications/menu-spec](http://www.freedesktop.org/wiki/Specifications/menu-spec)
Basically, rather than creating a separate group in the applications menu, Bible Analyzer would be under the 'education' group (or maybe under 'office', though Xiphos Bible Guide is under 'education' so that would seem to be the logical place to put Bible Analyzer as well.  Everything else would be accessed from within the program.

This is easy enough to change using Gnome/Ubuntu, so it's not a big deal, just a suggestion.  Thanks again for a wonderful program!

---

### Post by MoreRam on 2010-11-28
> **shane2peru said:**
> Thanks for the link!  I didn't know those were out there.

Shane

There are also three video links on this Facebook page --

[http://www.facebook.com/BibleAnalyzer?v=wall]("http://www.facebook.com/BibleAnalyzer?v=wall")

One of the videos covers the new features of version 4.

---

### Post by RevJack on 2010-11-28
I just installed BibleAnalyzer in LinuxMint 10 with no problems! Very nice Bible application!

---

### Post by Subito Piano on 2011-01-22
Hmm...can't extract the .deb - wrong architecture.  Any how-to's for AMD64?

---

### Post by Brad55 on 2011-01-22
I know you people are working to get this running but have you ever heard of Xiphos Bible Guide [Xiphos]("http://xiphos.org/") I use this one all the time.

---

### Post by marl30 on 2011-01-22
> **Subito Piano said:**
> Hmm...can't extract the .deb - wrong architecture.  Any how-to's for AMD64?

I just installed it on 64 bit and did not get any errors. It's working quite nice as well.

---

### Post by Subito Piano on 2011-01-23
The downloaded deb wouldn't install, as mentioned...after your response i went to terminal, added the ppa, and BibleAnazlyzer "apt-get installed" just fine--but it won't work from the menu.

back in terminal I typed:
[I][INDENT]python -u /usr/share/bibleanalyzer/analyzer3.py
[/INDENT][/I]
received response:
[I][INDENT]Traceback (most recent call last):
  File "/usr/share/bibleanalyzer/analyzer3.py", line 6, in <module>
    import wx, re, wx.html, sys, os, cStringIO
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so: symbol _ZN21wxMemoryFSHandlerBase19AddFileWithMimeTypeERK8wxStringPKvmS2_, version WXU_2.8 not defined in file libwx_baseu-2.8.so.0 with link time reference
[/INDENT][/I]
I can handle some commandline -- but i have no  idea what it's trying to tell me. :(

---

### Post by jonathonblake on 2011-01-23
> **Brad55 said:**
> I have you ever heard of Xiphos Bible Guide 

BibleAnalyzer offers some functionality that Xiphos currently does not have. Functionality that would be trivial to add to Xiphos.

This is not an endorsement of BibleAnalyzer. (The licence prohibits the use of the software!)

jonathon

---

### Post by My_World on 2011-02-13
> **jonathonblake said:**
> 
This is not an endorsement of BibleAnalyzer. (The licence prohibits the use of the software!)

jonathon
Could you explain this a bit more please?

Is there an ETA of when version 4.0 will be available for Linux?

If we would want to add additional modules, like extra Bibles that are not currently available, how should we go about it?

---

### Post by jonathonblake on 2011-02-14
> **My_World said:**
> Could you explain this a bit more please?

The license requires that you use either the complete 1611 or 1769 KJV.

However, the software does not have the capability to display, or otherwise utilise either of those editions, and the developer point blank refuses to change the software to enable those versions to be used.

jonathon

---

### Post by My_World on 2011-02-14
What a strange condition if he cannot enable one to meet that condition...

Thank you for the reply.

I'm on the hunt for an e-sword alternative, but will open another thread if I find nothing, this looked like a very viable option indeed.

---

### Post by jonathonblake on 2011-02-14
> **My_World said:**
> What a strange condition if he cannot enable one to meet that condition

Crafting licenses for software, and related things is extremely difficult.  You have to pay attention to the details, and the consequences of those details.

In this case, there are two possible solutions:
* Add the code so that the program displays the complete 1611/1769 KJV.  For various reasons, the developer is theologically opposed to doing this;
* Change the license so that the legal meaning is what the developer intended. This change is going to require a solicitor, preferably one that has also studied Canon Law;

jonathon

---

### Post by Subito Piano on 2011-02-14
> **My_World said:**
> What a strange condition if he cannot enable one to meet that condition...

Thank you for the reply.

I'm on the hunt for an e-sword alternative, but will open another thread if I find nothing, this looked like a very viable option indeed.

I did not see you mention other programs, so idk what you have tried.  Here are some...honestly, most of the programs are about the same as e-sword as far as features go and everyone has their *preferences* - except i think the first one below is *substantively* better than even e-sword.

Windows, use with Wine:
[LIST]
[*][TheWord]("http://www.theword.com") -- imo much more scholarly & more features than e-sword (almost too many for me)
[*][BPBible]("http://www.bpbible.com") -- a nice program, not as advanced as TheWord, roughly equivalent to e-sword.
[/LIST]
Cross-platform:
[LIST]
[*][Sword projects]("http://www.crosswire.org/sword/software/index.jsp") under various names (BibleTime, Xiphos, etc.) - again, imo, these are fairly similar to e-sword, sans maps.
[/LIST]
Also, there's a nice [list on Wikipedia]("http://en.wikipedia.org/wiki/Biblical_software").
 
Hope this helps!

---

### Post by My_World on 2011-02-14
I do not want to derail this thread...

I rely very heavily on a lot of modules, like various commentries (not a problem on most), different translations of the Bible (a problem on some) and various maps and timelines (again, a problem on Sword project based versions), also a lot of reading of dictionaries and books (problem on most).

e-Sword is filling all the gaps, but with them moving their modules to be downloaded from within the application this is going to become a problem for most Linux users in the near future so it is time to look for something new that can also do what one wants.

I'll start a thread on The Word momentarily, first want to test it on my Arch system before drawing conclusions.

---

### Post by MoreRam on 2011-02-14
> **jonathonblake said:**
> The license requires that you use either the complete 1611 or 1769 KJV.

However, the software does not have the capability to display, or otherwise utilise either of those editions, and the developer point blank refuses to change the software to enable those versions to be used.

jonathon

This quoted statement struck me as a highly bazaar representation of the BibleAnalyzer license. Therefore, I opened the software and read the license. I do not see anything like what you are representing.

I do see these two statements quoted below regarding the 1611 and 1769 KJVs. 
---This software is intended to promote and distribute the Holy Bible as found in the Authorized King James Bible of 1611. Use of this software in any way to attempt to question, undermine, or subvert the integrity of the Holy Bible as found in the Authorized Version is strictly prohibited.
---Bible Analyzer must not be used to criticize, undermine, subvert, or in any way question the accuracy and integrity of biblical Christianity or the Authorized King James Version of 1611 or 1769.

However, these conditions do not reflect in any way the representations you have made. Perhaps, you should clarify what you are talking about, or otherwise, make a retraction.

---

### Post by jonathonblake on 2011-02-15
> **MoreRam said:**
>  I do not see anything like what you are representing.

The only authorised editions of both the 1611 and 1769 KJV _required_ the 76 Book Anglican Canon to be included.

As such, the failure of the program to display that content has the result of casting doubt on the legitimacy of those translations, and furthermore criticises and undermines the accuracy and integrity of both Christianity, and those editions of the KJV.

jonathon

---

### Post by MoreRam on 2011-02-15
> **jonathonblake said:**
> The license requires that you use either the complete 1611 or 1769 KJV.

However, the software does not have the capability to display, or otherwise utilise either of those editions, and the developer point blank refuses to change the software to enable those versions to be used.

jonathon

No, the license does not say that -- I quoted above what it actually says in regard to these versions, that the software cannot be used to subvert their accuracy or integrity.

> **jonathonblake said:**
> The only authorised editions of both the 1611 and 1769 KJV _required_ the 76 Book Anglican Canon to be included.

As such, the failure of the program to display that content has the result of casting doubt on the legitimacy of those translations, and furthermore criticises and undermines the accuracy and integrity of both Christianity, and those editions of the KJV.

jonathon

You are using a specialized definition of "authorized editions," but there is no indication the author of the license intended this definition, rather than the common one, of being a descriptive phrase created by a printer for reference to the KJV in general, and having nothing to do with an official endorsement by the monarchy and church. However, even if some special definition you are trying to reference was intended, rather than merely being imposed on the language, the license does not make the requirement you stipulate.

In short, it appears there are no license complications in this software of the nature you indicate.

However, license interpretation can be clarified at the BibleAnalyzer forum, and I am quite certain the issue raised will be dismissed by the creator of the software and its license.

---

### Post by jonathonblake on 2011-02-15
> **MoreRam said:**
> You are using a specialized definition of "authorized editions,"

That is the meaning as defined by both the Royal Patent that the KJV is distributed under, and under Anglican Canon Law.

The license is a legal document, and as such, is to be understood in terms of the legal meaning of the words and phrases.

> but there is no indication the author of the license intended this definition

If the license does not reflect the intentions of the author, then the license needs to be rewritten by the author, so that it does what they want it to do.

>  having nothing to do with an official endorsement by the monarchy and church.

What counts is what it legally means. The term "Authorised Version" is from both Anglican Canon Law, and the Royal Patent that it was issued under. Arguably, its status as "Authorised Version" is also derived from the fact that it's creation was ordered by King James.

That is the reason why Archbishop George Abbot declared a penalty of imprisonment of one year for distributing the Bible without including all of the books found within the Anglican Canon in 1615.

> the license does not make the requirement you stipulate.

In as much as the program does not permit the entire work to be used, it ipso facto disputes the validity and accuracy of that omitted work, and hence using it for any purpose serves to cast doubt upon the legitimacy, accuracy, and validity of that material, which is a violation of the license, as written. 

jonathon

---

### Post by MoreRam on 2011-02-16
Jonathan,

Your legal analysis is totally convoluted, fictional, and meaningless. The meaning of language is always interpreted by law as that intended by the author. In this instance, the meaning you are trying to force on the language is obviously not applicable. The intended bibles are the ones set out in the software. There are not legal cases that note for licenses the definitions must be the one you have set out (which is actually absurd), or that not setting out an entire bible in software degrades the parts of a bible actually in use. You are manufacturing a way to try to represent that using the software is illegal. Legally, it would be held as totally absurd to assert the creator of the software then put it under a license to make its use illegal. The license will be interpreted in a manner consistent with the design of the software. 

So, Jonathan, I think the problem is, that you just do not want people using this software. However, there is no problem whatsoever with the license of this software.

---

### Post by jonathonblake on 2011-02-16
> **MoreRam said:**
> 
The meaning of language is always interpreted by law as that intended by the author.

The language of the contract is examined in terms of the legal meaning. Then, and only then, if there are ambiguous terms, is the author's intent examined. Furthermore, just because the author intended a specific consequence, that does not mean that the court will see that specific consequence as being found in the license.

> 
The meaning of language is always interpreted by law as that intended by the author.

The language of the contract is examined in terms of the legal meaning. Then, and only then, if there are ambiguous terms, is the author's intent examined. Furthermore, just because the author intended a specific consequence, that does not mean that the court will see that specific consequence as being found in the license.

>  In this instance, the meaning you are trying to force on the language is obviously not applicable.

The flaw there is that meaning that I am using is the one that has historical precedence. That both the 1611 and 1769 KJV were authorised for use in worship, and specifically to be used for the readings from the lectionary. How does one do a reading from the lectionary, when the Bible does not contain the passage that is to be read?

>  or that not setting out an entire bible in software degrades the parts of a bible actually in use.

By omitting books, it is implicitly questioning and subverting the accuracy and integrity of the Authorised Version of the 1611 KJV and 1769 KJV. The books that are omitted, are books that are still used in the Anglican Liturgy, Orthodox Christian Liturgy, Catholic liturgy, and even the RCL.

>  Legally, it would be held as totally absurd to assert the creator of the software then put it under a license to make its use illegal. 

You realise that this wouldn't be the first time that something has been distributed with the sole aim of suing the people that acquire and use the item being distributed.

> The license will be interpreted in a manner consistent with the design of the software. 

In which case the absence of the Anagignoskomena would be viewed by the court as a software bug that needs to be fixed.

> However, there is no problem whatsoever with the license of this software.

I just pointed out the first major issue with the license, there are at least six other points in the license that mitigate against using it.

Start with what the word "criticise" means.

jonathon

---

### Post by MoreRam on 2011-02-16
Jonathan,

Your legal analysis, (and in particular on how legal definitions are determined), and your assertion of this software being illegal due to the license is totally, completely, outright **bogus.** 

So, what do you hold will happen to those using the software? Will they be arrested for its illegal use? Will the creator of the software and license be arrested because he uses the program?

Or do you hold there will be a statutory penalty to be paid, not to the owner of the program as he will have to pay also, but to some entity somewhere?

Or do you hold that the owner of the software and license will sue for money damages for anyone using the software, (including having to sue himself, in which case he will be both the plaintiff and defendant)?

Jonathan, by all appearances, you are merely manufacturing a method to make people afraid to use the software. However, your argument has no basis in fact or law. However, I see no reason to continue posting on the issue you have raised. Let me reiterate simply and once again, the position you have taken is absurd.

---

### Post by jonathonblake on 2011-02-16
> **MoreRam said:**
> your assertion of this software being illegal due to the license is totally, completely, outright bogus

For starters,  I have never asserted that the software was illegal.

What I did assert, was that one could not use the software, without being in violation of the EULA that it is distributed under.

> So, what do you hold will happen to those using the software? 

That would be up to the civil court to decide.  

> Will they be arrested for its illegal use?

This is civil law, not criminal law. Civil law violations need not be, and usually are not illegal actions.

> However, I see no reason to continue posting on the issue you have raised.

Considering that your responses have repeatedly demonstrated a profound ignorance of contract law, civil law, and legal terms of art, I can understand you not wanting to repeatedly demonstrate that you don't even want to understand them.

jonathon

---

### Post by MoreRam on 2011-02-17
> **jonathonblake said:**
> 
Considering that your responses have repeatedly demonstrated a profound ignorance of contract law, civil law, and legal terms of art, I can understand you not wanting to repeatedly demonstrate that you don't even want to understand them.


Correction -- your position demonstrates a profound ignorance of the law, including even a definition for "illegal."

---

### Post by MoreRam on 2011-02-17
For anyone interested, you can verify that definitions legally are determined by author intent, just by picking up your Automobile or Homeowners Insurance Policy. At the beginning there will be a section entitled &#8220;Definitions,&#8221; and the most basic terms will be defined, such as &#8220;auto&#8221; or &#8220;residence.&#8221; Most contracts have a definitions section, (and even statutes often have definition sections). These sections are necessary as by law language is defined and interpreted according to author intent. However, when definitions are not set out, they are determined by context but still according to author intent.

---

### Post by jonathonblake on 2011-02-17
> **MoreRam said:**
> For anyone interested, you can verify that definitions legally are determined by author intent, just by picking up your Automobile or Homeowners Insurance Policy.

a) Contracts provide definitions of key terms, to clarify the precise meaning of those terms. Usually, but not always, these definitions restrict the scope of the term being defined.

b) The BibleAnalyzer License does not provide definitions for _any_ terms. As such, the usual and normal legal meaning is to be applied.  

>  These sections are necessary as by law language is defined and interpreted according to author intent.

Author intent has meaning in two instances:
* The definitions that are provided in the license;
* Where the author provides their interpretation and understanding of the license, in a separate document, or set of documents. This document [COLOR="DarkRed"]does not[/COLOR] take precedence over the legal meaning of the license. 

The Creative Commons Foundation has a goal of "*develops, supports, and stewards legal and technical infrastructure that maximises digital creativity, sharing, and innovation*." To that end, they have created several licenses. To help adoption of those licenses, they have been ported to more closely conform with the legal requirements of the specific country.

The aim of CCF is that all licenses of the same type, are compatible with each other.  Content that is licensed under CC-BY-SA 3.0 or CC-BY-SA 3.0 (ZA) or CC-BY-SA 3.0 (NZ) can be freely intermixed, because it is all the same license.

The intent of the CC-BY-SA 2.0 and CC-BY-SA 2.0 (UK) is that they are compatible with each other.

_Clause 3 e i_ and _Clause 3 e ii_ in the CC-BY-NC 2.0  and CC-BY 2.0 clearly show the difference in intent of these two licenses.   

_Clause 2.5_ in the CC-BY-NC 2.0 (UK) and CC-BY 2.0 (UK) are identical. This clause is functionally equivalent to _Clause 3 e i_ and _Clause 3 e ii_ in the CC-BY-NC 2.0.

Were a user to intermix CC-BY 2.0 and CC-BY 2.0 (UK) content, the copyright holder could go to court, saying that the content was being used in violation of the license it was distributed under, and thus is a copyright infringement. The CCFs intent that those two licenses be compatible, takes a back seat to the specific wording of the licenses.  

Talking about CC Licenses, _GateHouse Media, Inc. v. That’s Great News, LLC, No. 10-50164 N.D.III_ is interesting, precisely because it gets into the issue of whether the CC license is a license, or a contract.

>  However, when definitions are not set out, they are determined by context but still according to author intent.

One of the reasons why crafting licenses and contracts is so difficult, is that when definitions are omitted, the usual and normal legal meaning takes precedence over the author's intended meaning.

jonathon

---

### Post by MoreRam on 2011-02-17
Jonathan,

Your analysis on the definition of &#8220;authorized version&#8221; to apply to this license is **sheer baloney.**

Your concept of legal definition in general is **sheer baloney. **

Definitions only become difficult when they cannot be determined as set out in the contract or as indicated by context. Then, the court must set a definition, which will be determined by the circumstances and only to apply to specific circumstances. No court will hold that an author of a software license has set out a definition making the use of the software a violation of the law, when a ready alternative is available, as it is in the case of Bible Analyzer. It is obvious the author did not intend the definition you are trying to force on the license.

Further, even if your definition were accepted, your presumption that the non-inclusion of certain books degrades the specified bible overall would never be upheld by a court. It is just a position you have manufactured for the sake of asserting that using BibleAnalyzer software violates its license.

Your position is completely and totally absurd.

---

### Post by jonathonblake on 2011-02-17
> **MoreRam said:**
> Your analysis on the definition of “authorized version” to apply to this license is sheer baloney.

Your analysis has failed to even allude to canon law, case law, common law, statute law, contract law, or mercantile law. Nor has it provided anything other than an emotionally based whining about what the author of the license would possibly like it to mean.

> Definitions only become difficult when they cannot be determined as set out in the contract or as indicated by context.

In the context of the license, _Authorised Version of the 1611 KJV_ could only refer to the version that was requested by King James, and used by the Anglican Church for reading during a Church service, and furthermore, has to be a Bible that contains the content that the lectionary reading calls for. Something that is not possible with the Bibles that are distributed with BibleAnalzyer.

Furthermore, that is not the only place in the license where word have meanings that are, shall we say, ambiguous. Within the context of the license, several words have meanings that could fall either way. That the only way to know if one's usage was in violation of the license, would be after the fact.  

>  No court will hold that an author of a software license has set out a definition making the use of the software a violation of the law,

When a court finds a phrase or clause in a contract or license that violates the law, that specific clause or phrase is struck from the contract, or license. If the license does not contain language that covers that potential situation, then the license or contract is held to be null and void.

Courts have found definitions in contracts and licenses to be violations of the law, and nullified the definition, accordingly. In those instances where the license or contract failed to have a clause that allowed nullification of part of the license or contract, the entire license or contract has been nullified.

The BibleAnalyzer License does not have any clauses about nullification of part of the license. Hence, if any of it is nullified by a court, the entire license will be nullified. If the license is nullified, then users do not have the legal right to use the software.

Also note that I have not made any claims about the legality, or otherwise of the software. What I have repeatedly stated, is that usage of the software is a violation of the license.

> It is obvious the author did not intend the definition you are trying to force on the license.

Between the ambiguity of the license, and the even more ambiguous non-clarifications by the author, the only thing that is obvious, is that the license is landmine for potential users.

> your presumption that the non-inclusion of certain books degrades the specified bible overall would never be upheld by a court. 

The probability is that a court would uphold the statement that omission of content questions the accuracy and legitimacy of the work as a whole, especially since 2/3s of Christianity considers the 66 Book Protestant Canon to be defective, precisely because it (the 66 Book Christian Canon) discredits and questions the Bible as a whole, by omitting the Anagignoskomena.

> It is just a position you have manufactured 

Writing licenses is extremely difficult. Covering edge cases so that they fall where the license holder wants them, is even more difficult.   

If I thought you were seriously interested in discussing all of the flaws of the license, I'd lay out all of the problems with it here.



jonathon

---

### Post by shane2peru on 2011-03-09
I interrupt this on-going pointless argument to bring you the news that I have upgraded the ppa to 4.1 version of Bible Analyzer.  New and improved.  Enjoy.

Shane

---

### Post by ubuntu27 on 2011-08-31
Hello Mr. Shane.
Will the PPA be updated to Bible Analyzer version 4.3.1?
Both the PPA and the official deb are of version 4.1

Also, what is the difference between the official deb and the PPA? :)


Thank you.

---

### Post by shane2peru on 2011-09-01
> **ubuntu27 said:**
> Hello Mr. Shane.
Will the PPA be updated to Bible Analyzer version 4.3.1?
Both the PPA and the official deb are of version 4.1

Also, what is the difference between the official deb and the PPA? :)


Thank you.

Well, I'm thinking that the PPA is a lot of work, and very little interest.  So I'm reconsidering.  Every update, I have to re-learn the process to properly build the file, then upload.  So I think it would be best to go ahead and the get official deb.  The deb and the ppa should be identical, however I'm not keeping up lately.  Thanks for asking though.

Shane

---

### Post by antomoreng on 2011-09-01
> **shane2peru said:**
> Ok, I came across another Bible program for Linux.  Runs native in Linux.  You can see how to install it here:  [http://www.bibleanalyzer.com/forum/viewtopic.php?f=7&t=196#p698](http://www.bibleanalyzer.com/forum/viewtopic.php?f=7&t=196#p698)

I didn't feel like re-writing up the how to that I put there (but now I did).  Since you are probably already registered for these forums, you can feel free to post problems here and I will get back with you.  Enjoy.

[CENTER][SIZE=4]How to Install Bible Analyzer[/SIZE][/CENTER]
[COLOR=Red]Lucid and Maverick are the only ones currently supported.[/COLOR]
Ok, the quick how to for installing Bible Analyzer:
1.  In the Terminal **Applications -> Accessories -> Terminal** Copy and paste this:
```

sudo add-apt-repository ppa:shane2peru/bibleanalyzer-stable

```2.  Again in the terminal:
```
sudo apt-get update
```3.  And finally in the terminal:
```
sudo apt-get install bibleanalyzer
```That simple.  There are GUI instructions in the link above if you have terminalphobia. :)  They are longer.

Shane

thanks bro.  i have to try...God Bless U...:guitar:

---

### Post by antomoreng on 2011-09-01
Help me for Language Indonesia KJV Bahasa Indonesia...

---

### Post by bedpotato on 2012-03-06
Hello! I would be inetrested in getting this so I pasted the commands listed into a terminal, and lots of writing appeared as though it was working, but at the end after the final command it said "unable to get Bible package Bible Analyzer." :(

Has it worked for anyone else recently? Did I do something wrong?

---

### Post by stlsaint on 2012-03-18
Wanted to know what was the latest updated status on Bible Analyzer? Are modules native now? Issues worked out, etc.

---

