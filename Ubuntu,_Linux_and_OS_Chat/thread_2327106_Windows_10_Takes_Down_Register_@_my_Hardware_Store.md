---
title: "Windows 10 Takes Down Register @ my Hardware Store"
date: 2016-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-06-07
I've read about older Windows systems being force-upgraded, but have  never seen it. Today, at the local hardware store, I saw the fabled  beast.

One of their main registers at the back desk proudly (had  been Windows 7) announced it had been updated to Windows 10, then went  black. It took down the printer with it, apparently. The business is  mildly panicked about their other registers. Gotta' love MS.

They claim nobody okay's the upgrade. Might have been one of those dialog windows without a back button. Who knows.

---

### Post by poorguy on 2016-06-07
It can be rolled back to whatever OS it was running before the Windows 10 upgrade. After the rollback is finished change the update settings to check for updates but let me choose which updates to install. 

Also look for KB 3035583 and remove it and when it shows up again hide it. 
Download and install and configure the GWX Control Panel to monitor for Windows 10 updates.

Here's the link.

[http://ultimateoutsider.com/downloads/](http://ultimateoutsider.com/downloads/)

---

### Post by neu5eeCh on 2016-06-07
Yeah, thanks, but I'm a builder (a customer there), not the owner of the hardware store; and that's all besides the point. I know it can be rolled back. They probably called in their own IT support tech... who knows? I'm sure all will be fine until MS magically upgrades the next register... unless the tech is knowledgeable.

---

### Post by mastablasta on 2016-06-08
there are 3rd party software to help you remove the autoupgrade.

first they said you can reserve then download and upgrade at your convenience. then they start nagging. finally the opened a Window and if you clicked the X to close it was a confirmation rather than just close. and latest one is that it shows a notice that it will do the upgrade with timer. after 15 mins are up and if you don't click no in the mean time it proceeds to the upgrade. the porblme is if oyu have desktop always on or maybe working on something you might not see the notice. like register might have some Windows always up fornt or something.

Windows 10 is not that bad itself (aside from tracking and commercials), however it can be quite buggy as i recently experienced on Windows 10 certified system (i really thought things like this - poorly compatible hardware only happened in Linux).

---

### Post by neu5eeCh on 2016-06-08
> **mastablasta said:**
>  Windows 10 is not that bad itself (aside from tracking and commercials), however it can be quite buggy...

I'm glad I'm not the only having that experience. On my one system that I occasionally use for Windows-only software, I've found Windows 10 to be surprisingly buggy. In the past there were always little windows annoyances that could sometimes (usually) be solved by the knowledge base, but Windows 10 reminds me of my first experiences with Linux (way back when) -- and that's saying something. Death by a thousand paper cuts. One example: The audio will mysteriously quit working after about 3 to 4 minutes of play -- absolutely reproducible. I don't use the system often enough to care. Also, font rendition on Windows 10 is, well, just crap. I can go to BEST BUY and Windows 10 makes even the best monitors look like low resolution CRTs (as far as text goes). It's really incredible. It's not just me who's noticed this. Many complaints and a few solutions offered (nothing at the Knowledge Base). I've tried a couple with mixed success, but none produce results in the same ballpark as any of my Linux distros. All in all, I was shocked to find myself yearning for Linux dependability. Software tends to crash frequently and of course there are all the (MS) pop-up windows that ignore my attempts to disable. Yadda, yadda...

As for my local hardware store, they tell me their system doesn't work on Windows 10.

---

### Post by grahammechanical on 2016-06-08
Early on this evening I was reading a newspaper article by a UK member of parliament, a onetime government minister. Her normal routine is to get up. Switch on her computer and after dressing come back to the machine. Today, when she followed that same routine she came back and found on the machine an unfamiliar OS which she did not know how to use. An upgrade to Windows 10 had taken place without her approval.

If this can happen what does it say for the future of user control of the computer?

---

### Post by kansasnoob on 2016-06-08
I didn't believe people when I was told this until I saw it myself. What exactly happened:

(1) I was asked if I wanted to upgrade to Win 10
(2) There were no yes or no buttons, just the typical X in the upper right hand corner. 
(3) I clicked on the X to close that dialog window and investigate what was going on in update settings, but the upgrade began immediately upon clicking X to close that window :o

After seeing that happen before my own eyes I did some googling:

[http://www.computerworld.com/article/3080102/operating-systems/how-windows-10-became-malware.html](http://www.computerworld.com/article/3080102/operating-systems/how-windows-10-became-malware.html)

As it says there Windows is violating their own policy:

> So is the Windows 10 upgrade malware? One place to look for clues is in Microsoft’s document, “How to prevent and remove viruses and other malware.” That document warns, “Never click 'Agree' or 'OK' to close a window that you suspect might be spyware. Instead, click the red 'x' in the corner of the window or press Alt + F4 on your keyboard to close a window." And it defines spyware, in part, this way: “Spyware can install on your computer without your knowledge. These programs can change your computer’s configuration or collect advertising data and personal information.”

So let’s see: The Windows 10 upgrade downloads its bits to your PC without your knowledge. It changes your computer’s configuration. By default, Windows 10 collects advertising data and personal information. And if you try to stop the upgrade by doing what Microsoft tells you to do with every other application — click the X on its dialog box — it installs anyway.

The embarrassing part for me personally is that it wasn't my puter :redface:

It was a friends dual-boot  computer that I was just doing maintenance on so I had to tell them what happened. Luckily they didn't care - stating that they hadn't booted into Windows for months :D

He does want to be sure that his printer works with Win 10 but that shouldn't be a huge problem.

---

### Post by neu5eeCh on 2016-06-08
> **kansasnoob said:**
> I didn't believe people when I was told this until I saw it myself. 

I didn't either. I guess MS is within their rights to do whatever they want. It may be your computer but it's *their* OS. I'm very surprised there isn't more blow back, but probably most people don't care.

---

### Post by Frogs Hair on 2016-06-08
I just killed the GWX process with sysinternals  process explorer at first and that worked for the current session pretty well. I then found the GWX control panel application linked earlier linked on another forum and that put GWX to rest without having to monitor the update manager.

---

### Post by mastablasta on 2016-06-09
> **VTPoet said:**
> I didn't either. I guess MS is within their rights to do whatever they want. It may be your computer but it's *their* OS. I'm very surprised there isn't more blow back, but probably most people don't care.

becuase often people do not read or understand the EULA, they believe it is their computer and their OS. and also often people thing the computer is doing something by itself (like no one contorling it and such)

my experience with 10 and brand new work laptop (supposedly fully compatible):

- docked display would occasionally not work (it turn otu that for some reason the PC resets the screen settings). after that it is almost impossible to switch displays without restarting and such. similar with external display. this is "great" when you visit a client and want to give them a presentation.
- apps and Windows store everywhere even in excell
- commercials and such running in start menu. WTF!?!
- EDGE - ridiculous - no menues, difficult ot navigate, right click is missing a number of important options. how the hell do oyu donwload a PDF opened in edge? x to close tab would sometimes not response
- pictures (or is it photos) app - right click the pic and there is no "save as" option?!?!?
- PC itself acts strange when i unplug the external monitor or undock it. rather than reverting to single monitor it appears it is struggling to display two desktops on same 15" monitor
- went to a meetingthe other day, turned it on only to have it reboot 3 times to install updates (they are not automatic but pushed by IT dept.). why thank you for looking out after me.
- calculator app is kind of lame compared to speedcrunch.
- lack of official themes

the only thing that is still good is the Office suite and that's not part of the OS anyway.

---

### Post by neu5eeCh on 2016-06-09
> **mastablasta said:**
> ...the only thing that is still good is the Office suite and that's not part of the OS anyway.

I was just listening to Tom Ashbrook this morning as I worked. He was discussing the [international pushback against American Tech Companies]("http://onpoint.wbur.org/2016/06/09/global-pushback-on-american-i-t-giants"). A caller dialed in and said that he did business in Canada and that MS only licenses Office for a given language. If he wants Office in French and in English, that's two discrete licenses. That's so "money-grubbingly" astonishing I have a hard time believing it. 

I read about more and more European localities switching to LIbreOffice, and begin to see some of the costs associated with using MS Office. I was just discussing this with a friend today and heard another story of an acquaintance's system being "borked" by an "unwitting?" upgrade. Had to pay for a local computer tech to sort out sudden software incompatibilities.

---

### Post by kansasnoob on 2016-06-27
[A lawsuit over an unwanted Windows 10 upgrade just cost Microsoft $10,000]("http://www.pcworld.com/article/3088755/windows/a-lawsuit-over-an-unwanted-windows-10-upgrade-just-cost-microsoft-10000.html")

Maybe they'll get the message that people don't like to have things forced on them.

---

### Post by coldraven on 2016-06-28
I just bought a second hand laptop which comes with Windows 8. This is the only Microsoft product that I've had  in this house for many years.For several days I was pondering whether to get the free upgrade to 10. After doing minimal research now I remember why I abandoned Windows, it's spyware!!

---

### Post by ventrical on 2016-06-28
Just got  my Windows spam.

"Time's running out. Windows 10 FREE upgrade offer ends July 29"

Does this sound familiar- 'Get the fastest, most secure windows ever.'

 If any of you have installed Windows XP Home or XP Professional you would notice the same banner on your screen during the install. It's beyond the pale.

Regards..

---

### Post by mastablasta on 2016-06-29
> **VTPoet said:**
>  A caller dialed in and said that he did business in Canada and that MS only licenses Office for a given language. If he wants Office in French and in English, that's two discrete licenses. That's so "money-grubbingly" astonishing I have a hard time believing it. 
ok so this explains why i noticed several Office items in installed programs list each with different language. btu i am sure the disocunt was good. and kickback even better.

> 
I read about more and more European localities switching to LIbreOffice, and begin to see some of the costs associated with using MS Office. I was just discussing this with a friend today and heard another story of an acquaintance's system being "borked" by an "unwitting?" upgrade. Had to pay for a local computer tech to sort out sudden software incompatibilities.

some sane ones. 

was just checking some stuff we have and the files are offered in Word 2003 version, odt and pdf. or just odt and pdf. which could signal the move. but even having it enshrined in law doesn't help much. components for e-signatures are in some way connected to MS. so while they work in other browser occasionally they would not and the plugins in other browsers lag behind IE support. still i did my last tax report in Firefox, while in the previous brush with tax authorities i ended up using "enhanced" Chromium (Chromodo). 

Italian army is the latest major mover to OpenOffice.

where i work i could easilly do with Linux & LO. the programs i use on daily basis all have Linux clients or have a way of making them work on Linux or a good alternative. but it is juts easier for them to pay to MS and have them take care of some (most) things. Half the servers are running Linux though, as well as various machines, test devices.... just no desktops arround yet.

---

