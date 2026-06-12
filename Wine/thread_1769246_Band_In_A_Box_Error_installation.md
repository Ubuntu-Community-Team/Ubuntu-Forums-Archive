---
title: "Band In A Box: Error installation"
date: 2011-05-27
forum: Wine
---

### Post by rubebop on 2011-05-27
Hello Ubuntu Forums's Community!

I have a problem who is killing me: I don't succes installing Band In A Box.
I have tried versions 2009 and 2010 on Ubunutu Natty 11.04 32bits, with Wine 1.22 and 1.3 beta.
And nothing!

First there is the following message that appears while installing:

"restorePGPluginpresets.exe" error

An then,

"Virtual Sound Canavas VST
Error installing iKernel.exe: (0x1400)"

After that there is the icon in my Desktop, but when I click it the program doesn't launch!
What should I do? I have spent lots of hours looking for solutions and explanations, but nothing...

Thank you so much for your attention!

---

### Post by bobwyajnr on 2011-05-28
Hi

You will need to refer to your version of BIAB on the [Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1094"). Posting comments under the AppDB entries can often elicit responses from other users. You can also try contacting Richard Griffiths the maintainer of this application. He has undertaken (in an **unpaid** capacity) to monitor and keep up-to-date with the best way to install and run the BIAB application - be it the use of Windows libraries, patches, different Wine versions, etc.)

Sadly debugging application errors (when running via Wine) requires a good familiarity with the command line! The [Wine FAQ]("http://wiki.winehq.org/FAQ") and [Wine User Guide]("http://www.winehq.org/documentation") are well set out and worth wading through! :P


Wine is great software but sadly it can often take a lot of work and patience to get a particular application running! :popcorn:

Bob

---

### Post by rubebop on 2011-05-28
Bob, thank you for your answer!

I must say that I've already registered in this website, and I also added 2 test data, but Richard Griffiths erased my report, saying that for him the installation and program were ok! 
I added my second test data yesterday, and I'm expecting wether he's gonna erase it or try to understand my problem!

The worst thing is that I've being looking  in internet if there are other reports like mines, but I don't find anything... :(

---

### Post by bobwyajnr on 2011-05-28
> **rubebop said:**
> Bob, thank you for your answer!

I must say that I've already registered in this website, and I also added 2 test data, but Richard Griffiths erased my report, saying that for him the installation and program were ok! 
I added my second test data yesterday, and I'm expecting wether he's gonna erase it or try to understand my problem!


When testing an application I will generally file a bug report or ask on the Wine forums - about problems I cannot bypass. Only then would I submit an application report to AppDB.

The ideal entry on AppDB: details what doesn't work, what work-arounds are needed and gives a realistic overall assessment (Garbage->Platinum). Nobody wants to read another 'Garbage - doesn't run' type entry - that doesn't help other users. Richard- type entries don't help either (they are not nearly detailed enough)... ](*,)](*,)

It's best to start with a clean slate. I would recommend using Wine **1.3.21**. You'll be asked to submit a WineHQ bug report against the latest version of Wine.

Fire up a Gnome terminal...
I would recommend setting up a Wineprefix for your application:
```
mkdir ~/.biab/
```
Set Wine to use this (only in this terminal tab/session):
```
export WINEPREFIX=~/.biab/
```
Launch Band In a Box installer (CD):
```
cd media/<BIAB CD mount folder>
wine Autorun.exe &> ~/log.txt
```
**OR**
Launch Band In a Box installer (executable in folder on Desktop):
```
cd ~/Desktop/<BIAB folder>
wine Setup.exe &> ~/log.txt
```
(Please just use one of these examples and replace the executables names with the actual ones!)

You will get a log.txt file (in your home folder). Check this is filled with sensible stuff (usually lots of **fixme:**!! tags...) If it's more a few dozen lines I would post it on [PasteBin]("http://pastebin.com/") and just give a link here.

Could you contact Richard and check whether he striped out **PulseAudio** from his system?

Post back with the problems you get with this step or a Pastebin link... :popcorn:

Bob

---

### Post by rubebop on 2011-05-30
Bob, thanks, again, really!

I did what you told me:

[http://pastebin.com/Yt9CwSJE](http://pastebin.com/Yt9CwSJE)

Sorry but I pasted the whole text file, because I didn't know what was important :S

I'll ask him about that and I'll let you know what is going on :)

---

### Post by bobwyajnr on 2011-06-01
> **rubebop said:**
> Bob, thanks, again, really!

I did what you told me:

[http://pastebin.com/Yt9CwSJE](http://pastebin.com/Yt9CwSJE)

Sorry but I pasted the whole text file, because I didn't know what was important :S

I'll ask him about that and I'll let you know what is going on :)

Ok, I had a quick look at that output. It would also help to know how you are launching the application. TBH the actual launching command-line is also important! Is the installer on a CD? 

The errors about **msvcp60.dll** could be helped typing the following:
```
winetricks vcrun6
```
The **winetricks** script will download and install the Microsoft Visual C++ 6.0 libraries. (NB **winetricks** will display a simple GUI interface if you run it without any parameters. It will cache any download libraries, locally on your harddisk, for 'optional' use in other WINEPREFIXs...)

I guess it might help to clean the WINEPREFIX (before retrying the install):
```
rm -Rf /home/rubebop/.biab
```
Remake the **/home/rubebop/.biab** folder. Then install the Visual C++ libraries using Winetricks. Just follow my guide again... ;)

Basically I can get you 'so far' - so you won't look like a complete idiot if you submit a bug on WineHQ! I'll probably get stuck at some point... I do a bit of C/C++ programming but I'm not a Wine Developer! :popcorn:

Bob

PS Remember you can always type
```
man <commandname>
```
if you want to know what a particular CLI program/BASH command actually does!

---

### Post by rubebop on 2011-06-02
Bob, really, I feel sorry for you, hope I don't bother you too much with this stuff!
I did again what you told me, this is the new log.txt:
[http://pastebin.com/jRfFRzm2](http://pastebin.com/jRfFRzm2)
Is there any improvement?

Once again,  they deleted my wine bug report haha I won't try until you tell me :) 
Dear god how silly I feel! 

Take care

---

### Post by bobwyajnr on 2011-06-02
> **rubebop said:**
> 
Once again,  they deleted my wine bug report haha I won't try until you tell me :) 
Dear god how silly I feel! 

Take care

Let's be clear here! There's nothing simple about Wine bugs! We are talking about an incomplete implementation of the API of a radically different OS here!

What do you mean that they are deleting your bug report? Did you post to WineHQ Bugzilla or the AppDB page?

I would highly recommend posting what you've done (and giving your pastebin link) on the [WineHQ forums]("http://forum.winehq.org/"). Nobody will delete your post there and a few developers trawl the forum from time to time... :popcorn:

RE your latest attempts. Can you make sure that:
```
env | grep WINEPREFIX
```
shows
```
WINEPREFIX=/home/rubebop/.biab
```

... before you run the winetricks command ...

Then (in the same terminal tab) type:
```
winecfg
```
making sure that the *libraries* tab has an override specified for **msvcp60** (native). 

It's very easy to start overriding Windows library files for the default WINEPREFIX (~/.wine) if you're not careful! The command:
```
export WINEPREFIX=/home/rubebop/.biab
```
only has scope for the *current tab* in your terminal window and will be *lost* when you *exit that terminal/tab*...

Bob

---

### Post by rubebop on 2011-06-02
Hi there!

I tried to install an other time paying attention on these libraries. I added what you told me before the last attempt of installing. But still nothing, do you want me to show the log.text?

An other thing I forgot to tell you, is that I have the .exe in my HDD (I haven't the cd)

When I told they erased my report I was more precisely speaking about AppDB.
But I understood what you said me.

I  also filled a WineHQ Bugzilla report, which is:
[http://bugs.winehq.org/show_bug.cgi?id=27328](http://bugs.winehq.org/show_bug.cgi?id=27328)

But then my question is: [EMAIL="arethusa26@gmail.com"] Andrew Nguyen[/EMAIL] wrote 
*** This bug has been marked as a duplicate of [bug 27068]("http://bugs.winehq.org/show_bug.cgi?id=27068") ***
Ok, but is the problem solved?

Thanks,

Rubén

---

### Post by bobwyajnr on 2011-06-03
> **rubebop said:**
> 
Ok, but is the problem solved?

Thanks,

Rubén


Hi Rubén

I guess what is happening is that the MS Visual C++ runtime library is making an external call to another Windows library. I am puzzled about why the error would not change when you over-rided the builtin (Wine implemented version) of the runtime library. Ah well I'm still learning...

You have to understand the idea behind Wine. It is never going to completely replicate (exactly) the Windows API. Currently it doesn't even fully-implement all of the built-in Windows API. I believe the limited time of the (unfunded) Wine development team is focused towards bugs and API features that get the most hits. An example of this is the ongoing mouse warping issue affecting a lot of OpenGL/DirectX games...

I will say it again. PM Richard Griffiths or that Wolfgang Polzleitner and ask him/them to detail (or least sketch out) how he/they got the program working. Even the Wine Developers will not/cannot work with software they do not own! (A test suite of Windows game demos are available for download in the **winetrick**s app for example...) Your best bet is always going to be someone who has the software and has gotten it working in Wine! :popcorn:

All the best,
Bob

---

