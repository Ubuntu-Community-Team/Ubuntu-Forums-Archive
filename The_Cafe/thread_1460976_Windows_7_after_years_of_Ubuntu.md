---
title: "Windows 7 after years of Ubuntu"
date: 2010-04-23
forum: The Cafe
---

### Post by 3Miro on 2010-04-23
Ubuntu and Windows 7

Couple of years ago I migrated from Windows XP to *Ubuntu and only yesterday, when I tried Windows 7, did I realize how spoiled I have become. Basically I wanted a new video card (64-bit OpenCL capable) and after a decade or so of NVIDIA, I decided to try to switch to an ATI. The main reason was the price, good experience with AMD CPUs and the reviews of the new Catalysis driver. Unfortunately I had overestimated the ATI – Linux compatibility. After hours of reading about settings, tweaks and unofficial repos, I got the thing behaving for regular apps, compiz and native 3D apps. However, as unfortunate as it was,  ATI and wine did not agree. Games like Civilization IV and Oblivion play well on an older NVIDIA 8600GT + wine, but fail with the newer ATI Radeon 4850. I tried both Karmic and Lucid beta 2, different versions of wine, native .dll files, installs and reinstalls as well as game settings, and at the end the games would either crash, or be choppy, or give fragments, or mostly, all of the above. So I decided to put my hands deeper into my pockets and go back to  NVIDIA ... and right after I ordered the new card, maybe because of all the money that I spend, the devil got in me, and it wasn't the good BSD devil, but the greedy, corporate, Microsoft one. Thus I decided to give Windows 7 a try.

So here we go....

I got a trial version of Windows 7, put in the disk, reboot, select to boot from the drive …... and wait ….. and wait …... and wait …. and finally a setup screen appeared. It was in bad resolution, due to the lack of a good default driver (I wonder what was taking it so long) and there was no familiar “Try Windows 7 w/o changes to your system”, but anyway. I went through the wizard Next, Next, OK, I agree, and so on until I got to the partitioning stage. I had cleaned one of the ext4 partitions from all important data and wanted to use it for windows, while keeping Ubuntu on another partition. I knew that I will have to reformat and reinstall grub, however, I did not expect that Windows 7 would refuse to install on an extended partition. WTF, Ubuntu never had trouble with that.

I guess I should have given up there, but I was stubborn. I moved everything to a secondary storage drive, so I can give Windows the entire HDD. I was thinking that I will still be able to access all my files from Windows … then I realized that Windows doesn't read ext4 partitions (or at least not without special software). I am so used to Ubuntu reading everything that I forgot that I have to think about compatibility of file systems. I decided to go ahead any way, but only because I also have an Ubuntu laptop, which I can use in conjunction with a Live CD and a jump drive to get to anything if I needed it urgently. 

I booted from the Windows 7 disk again and after waiting again, I told it to wipe the entire primary drive. It was happy to do so. Then the installation began, and went on and on and on. For this time I could have installed 2 copied of Ubuntu (if not three). Finally after an hour or so, couple of reboots (which still baffles me, why do you need to reboot in the middle of the install) and after I was almost out of patience (I swear this thing is purposely spinning empty for-loops), I got into Windows 7 for the first time.

It looks nice, fading effects in aero are pretty, but after compiz it takes way more than that to impress me. “I wonder if they will make the cube in aero”, but then I remembered that I am now restricted to one desktop only. Even theoretically, it would be impossible for aero to outshine compiz. And as for the many desktops, I don't know how many times I scrolled the mouse on the background in a futile attempt to go to the next workspace.

After the first look, I realized that I am not done yet, since I still need to install drivers. I got the motherboard CD, stick it in and an installer popped up. First it said that it would require administrative privileges, I prepared to type in the password, but it was enough to just say “continue”. OK, no password, but still it is an advancement from XP, where one would have to install extra software like Zone Alarm to get the simple feature of prohibiting someone from installing whatever they want. I also remember Windows 98, where you could click cancel on the password login screen and you would still get in.

It also asked to install a trial version of Norton, to which I said: “Sure why not.” If I am going to form an opinion of Windows 7, I should probably try the full experience. Then installation began and I once again tried to go to another workspace to do something else in the mean time. How naive of me! The installer went on and suddenly, without any warning or whatsoever, the entire system rebooted. This wasn't a crash or a bug, this was the standard behavior of the installer. How dare it take so much control from me! What if I wanted to reboot later? Who's in charge here!?

On the second boot I installed the ATI driver, it took some time to find the right driver on the Internet (had to go to AMD/ATI's site, not XFX), and there was no nice window with a check box: use the proprietary driver. In any case, it was the ATI driver that drove me to Windows in the first place (which is totally ATI's fault) so I shouldn't complain much. I ran the installer, but this time I was also ready for the reboot: I went into the other room, so I could pretend that the process was simply being automated as opposed to me not being in charge.

On the third boot, a Norton window popped up asking for activation and my e-mail address. Well I don't want to activate now (if I ever decide to activate), there is no cancel button, there is no activate later and when I tried to x out of the windows, it refused to do so. I couldn't go to another workspace and all I could do was to minimize it and now I have a minimized Norton activation window constantly polluting my taskbar.

In any case, I decided to finally install Oblivion. Since it is somewhat old, it actually works very well under wine, with only a minimal amount of tweaking, which of course wasn't necessary under windows. I did not feel much of a difference there, however, if you have a newer game, then I am sure Windows would be a huge advantage. Also, there are no problem with the ATI driver under Windows.

After the initial install of the game, I decided to install some of my favorite mods (in my opinion mods for Oblivion are a must have) and that is when the real hell broke loose. I had all the mods on a flash drive, I open the drive and one of the mods was compressed to a .rar file. Right-click and it turned out there was no program to read .rar files. OK, lets install one. Ops, no repository. I went to Google, typed rar + windows 7 and a nice web page popped up with a version of 7zip for windows. I clicked “download” and then cold shivers ran down my spine. What if this software wasn't safe, what if it was spyware or a malware of some sort. When I was using XP, I used to download random thing all the time and I was always somewhat anxious, but since I had the community repository I never had to worry about this. Windows can be kept safe, as long as you don't download and install random apps, but without a repository you have to do just that. With Windows you constantly have to expose your system to security risks.

Going on, the program did not appear to do anything bad, or at least not on the surface and it did extract the rar file just fine. Then came the second problem, I had forgotten how to install one of the mods, so I had to open the .pdf file with the instructions. No .pdf viewer of course, but at least this time Windows automatically took me to Adobe's web page. I guess the Windows' version of repository consists only of a list of URL's for large corporations. The Adobe Reader took forever to install and right after that, I got a “reboot now or later” popup. I was simultaneously happy that finally someone cared to ask and outraged about why the !#%! do I need to reboot after installing a .pdf reader. This was the 5 – 6th reboot and I had completely lost count. Furthermore, right after I got back into windows, it asked to download updates for the reader that I had just installed from the Internet. Why couldn't this thing just install the latest version? I made it wait of course and proceeded to open the .pdf file, which in itself took over 10 seconds …. I miss evince.

For the purpose of the mod, I also had to edit some files and luckily Notepad was sufficient. In Windows 7, it even has tabs like gedit. However, there was another problem. I couldn't see how to tell Windows to show the file extensions much less edit them. Under Linux, I would back up SomeConfigFile.whatever to  SomeConfigFile.whatever_mybackup, and the penguin couldn't care less, however, this totally messed Windows. Why does a system have to depend on filenames so much. The solution that I found was Start Menu &#8594; cmd to get to the DOS shell. Well it is “dir” and not “ls” and you have to type all four letters of “copy” as opposed to “cp”, but it has tab completion and gets the job done.

I thought I installed everything on the first try, but I failed and I realized that, only after I had deleted the extracted version of the .pdf file. No problem, I will just open the rar archive and open the pdf from there. Then I realized that Windows lacks application integration, you have to explicitly extract the file first, before you can open it with another program.

After some tweaking with the mods, I got things working. Once in Tamriel, I could finally relax a little. The game did look better than ever before, but it was mainly due to the better graphics card. The process of installing Windows 7 and dealing with all the little and major wrong things is hardly worth the trouble. I have been through a lot of pain with wine in the past, but every step of the way, I was surrounded by a helpful and friendly community, as opposed to a bunch of greedy corporations. Besides, I don't think Microsoft deserves any credit for the beautiful games that other people have made for Windows operating systems. At the end, Windows 7 is definitely not worth the trouble (well maybe if I were deep into this really new game and Windows was the only option …. and I was drunk).

For now I have decided to stay with Windows 7 on until my new NVIDIA card comes from newegg. It will rain over the weekend, so I guess I will be staying inside chasing after Deadra Lords from the infernal planes of Oblivion. I thought about using it for some simple work, but then I realized that I have no office apps, only IE browser, no mail client, no text/code editors … what was it taking so long to install. This thing wasn't just running empty for-loops, it was running empty while-loops.

However, the experience has given me an opportunity to reflect. There are a lot of people out there that are in genuine OS pain and many of them don't even realize it. If they only knew what it is like to be “free as in freedom” Bill Gates would starve (well not really). Yet unfortunately due to the “free as in cheap” aspect of GNU/Linux, we don't have the resources to mount a decent PR campaign. As good as YouTube channels like NixiePixel are, they can only get you so far.

This morning, while having breakfast, I decided to let Adobe install its update. It did so and then it had to reboot again. This is not Microsoft, this is Adobe, but this is also the entire corporate environment. I might not wait till next week, I might just open the computer case, install the old NVIDIA card, put a *Ubuntu Live CD into the drive and END THE NIGHTMARE.

---

### Post by Idaho Dan on 2010-04-23
I couldn't stop chuckling! That was good.
Makes me appreciate Ubuntu even more.

---

### Post by Objekt on 2010-04-23
> **3Miro said:**
> At the end, Windows 7 is definitely not worth the trouble (well maybe if I were deep into this really new game and Windows was the only option …. and I was drunk).

That is sig material right there!

I installed the Windows 7 RC last October, and have reached more or less the same conclusions.  In the final analysis, I wasn't all that excited about paying big bucks for more of the same.  Windows XP is perfectly adequate for the non-serious tasks (read: games) for which I now use it.

---

### Post by 3Miro on 2010-04-23
I am glad you guys enjoyed the rather long post. If something else comes up in the next couple of days, I will post update.

---

### Post by sixthwheel on 2010-04-23
I usually don't have the patience to read long posts, but yours got me from the first line and kept me glued to the screen.:)

Good post.

---

### Post by wilee-nilee on 2010-04-23
Started on open source, got W7 for 25$ student price. With a usb install about 20 min works fine, never really use it though, except to understand it so I can fix my friends computers.

Where did you get a install that includes the AV stuff the standard installation that I have did not have those waiting to be installed, is this a torrent?

---

### Post by Palanthas on 2010-04-23
> **sixthwheel said:**
> I usually don't have the patience to read long posts, but yours got me from the first line and kept me glued to the screen.:)

Good post.

Ditto.

> **wilee-nilee said:**
> ...never really use it though, except to understand it so I can fix my friends computers.?

Again, ditto. I do use windows for gaming but I also help fix friend's/co-workers's computers. So having winXP, Vista, and Win7 available for me to "play" with is very helpful. (I also have win98 SE that I install from time-to-time just for the fun of it)

---

### Post by 3Miro on 2010-04-23
> **wilee-nilee said:**
> Started on open source, got W7 for 25$ student price. With a usb install about 20 min works fine, never really use it though, except to understand it so I can fix my friends computers.

Where did you get a install that includes the AV stuff the standard installation that I have did not have those waiting to be installed, is this a torrent?

The AV trial came on a CD with my Motherboard. I had to install standard Motherboard drivers as well, they should be better than the generic MS ones.

Windows naturally doesn't come with AV at all, however, there are free AV programs (free as in legally free of charge). I just don't know how good they are.

---

### Post by wilee-nilee on 2010-04-23
> **3Miro said:**
> The AV trial came on a CD with my Motherboard. I had to install standard Motherboard drivers as well, they should be better than the generic MS ones.

Windows naturally doesn't come with AV at all, however, there are free AV programs (free as in legally free of charge). I just don't know how good they are.

Of course we all have different opinions, but if you want live running protection avast is pretty good and runs with a pretty small footprint, and there is a free version.
[http://www.avast.com/index](http://www.avast.com/index)

These other two are free and are also very good cleaners, and can bet set to no autostart with ccleaner or msconfig,
superantispyware is the only one that auto installs as a auto start though. A friend who is a tech says these last two are some of the best.

[http://www.superantispyware.com/](http://www.superantispyware.com/)
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)

---

### Post by iponeverything on 2010-04-24
@3Miro you have far more patience than me. 

Nag windows that you can't close and software that can be almost impossible to un-installed -- two things that I really miss.

---

### Post by bikodog on 2010-04-24
> However, as unfortunate as it was, ATI and wine did not agree. Games like Civilization IV and Oblivion play well on an older NVIDIA 8600GT + wine, but fail with the newer ATI Radeon 4850. I tried both Karmic and Lucid beta 2, different versions of wine, native .dll files, installs and reinstalls as well as game settings, and at the end the games would either crash, or be choppy, or give fragments, or mostly, all of the above.

I'm have ATI Radeon HD 4300/4500 Series using Catalyst drivers on Ubuntu 9.04 64 bit and Civ4 runs great in wine. had to tweak with winetricks and run in a virtual desktop, but other than that it is flawless.

As a side note, my daughter has similar specs but running Karmic and has some buggy graphics on Civ4.

---

### Post by 3Miro on 2010-04-24
> **bikodog said:**
> I'm have ATI Radeon HD 4300/4500 Series using Catalyst drivers on Ubuntu 9.04 64 bit and Civ4 runs great in wine. had to tweak with winetricks and run in a virtual desktop, but other than that it is flawless.

As a side note, my daughter has similar specs but running Karmic and has some buggy graphics on Civ4.

To be honest, I did not do much with Civilization, my main effort was with Oblivion since it has more demanding graphics.

---

### Post by elarrarte on 2010-04-25
Oh men ... is ubuntuforums dedicated to do this kind of threads?????
I thought that it was for talking about ubuntu and trying to make it be a better OS.

So ... we have a user that knows nothing about Windows, and use a program called obligon or something like that ... under wine ofcourse =D ... install a lot of useless programs under windows and say bad things of it ... let s say it s a good point of view :confused:

So ... i really like ubuntu and linux in general ... but i think things like that dont allow us to grow up like community ... 

If u have to expose these things in a conference ... like ve seen ... u ll be very frustrated ... a windows user would say ... 

- obligon under wine? this is windows code ... don t u have a native obligon for linux? :)
- can u play fullscreen HD youtube videos under the crap of X server and ur "proyect of driver for ur ATI/NVIDIA" ... consuming less than 30% of CPU ?
- software integration ... did u read something about OLE object? ... i think not ... can u paste an object from DIA to openoffice directly and edit it in openoffice? ... NO ... i imagine !
- is ur wireless card working fine? and what about hibernation?
- problems with upstart, flymouth, ureadahead, new kernel?
- do u work with ur computer? did u try to make a complex engineer diagram like i do in VISIO with DIA??????????? 

Ohhhhh ... but the guy has flying windows with compiz and boot his OS in 10 secs ... that s great !!!! ... opensource software like DIA, firefox, thunderbird, pidgin, vlc, gvim, virtualbox, eclipse .... work better on windows than on linux ... try them for a bit please!

I think there are good opensource software out there ... but linux for desktops is not mature enough today ... there are a lot of things that must be arranged ...

Look at this ... the GVIM editor ... my favourite ... try to print something in linux ... u ll be redirected to a windows saying "lpr -P ..." ?????? ... in windows u ll be redirected to the classic printer window selection ... that s the software integration we all want my friend !

Please see my post called "My little contribution" under these same Forum ...

Bye ...

---

### Post by John Bean on 2010-04-25
Your ... keyboard ... seems ... to ... have ... a ... sticky ... period .................

;-)

---

### Post by Palanthas on 2010-04-25
> **John Bean said:**
> Your ... keyboard ... seems ... to ... have ... a ... sticky ... period .................

;-)

Was thinking the same ;)

I don't care which OS one uses (Windows, Linux, Mac, etc...) but personally I prefer Ubuntu even though I am writing this post in windows 7 while my ubuntu machine is idling beside me. :p Typically my windows machine gets used more often but that's because I do gaming and it likes my facebook apps better then the ubuntu machine. (just reinstalled karmic after making a mess of installing lucid lynx thus win7 running better at the moment)

---

### Post by elarrarte on 2010-04-25
I 'm sorry about my little english ... i apologize ... i dont want to argue, i just want to see linux to grow up, nothing else ... i have linux in all of my servers ... i m not a gammer ... i do some multi-platform developing and network administrator task in my work ... i have a lot of OS in my work: windows, linux, mac and unix

newer versions of windows are growing up in stability and security
newer versions of mac osx are growing up in stability and easy of use
unix --- i must admit is a rock-solid OS for our administrative tasks
linux --- runs good in our proxy & mail servers ... but on workstations: 

newer versions of ubuntu:
- new theme --- ok that s great!
- better compiz effects --- who cares?
- boot in 10secs --- who cares?
- pulseaudio sucks
- video drivers for linux suck ... until ubuntu 8.04 youtube was ok ... stability?
- installing the lastest updates of a software is a nightmare (compile, read howtos?)
- printing complex engineer diagrams with ... cups? =D
- ubuntu "managing users & groups" dosent work anymore ... create a user without permissions and the user can still using cdroms, usbs ... security??????

so ... if u just play some games with wine because u have no native games, use pidgin and see ur facebook in firefox ... linux is ok ... but try it for work and let me know ur experience ... even the original GVIM program runs much nicer in windows than on linux ... i hate saying that ... but that s the truth !

Bye

---

### Post by chayzer on 2010-04-25
I can't remember the last time I had to "compile an update"

Boot in 10 seconds is amazing. I travel a lot and I like having a full battery and not waiting minutes for my windows to boot.

As far as sharing printers over my home network, CUPS is far simpler to use than say.. trying to share a printer from Windows 7 to an XP machine.

VDPAU

What's the point of arguing this stuff anyways. If I really had any use for Windows I wouldn't have just given away a copy of Windows 7 that came with my new computer. I actually find Windows to be basically worthless.

---

### Post by chayzer on 2010-04-25
Although a decent CAD program would let me finally reclaim that other partition that lingers like a bad taste in my mouth.

---

### Post by 3Miro on 2010-04-25
> **elarrarte said:**
> Oh men ... is ubuntuforums dedicated to do this kind of threads?????
I thought that it was for talking about ubuntu and trying to make it be a better OS.


This part of the forum is for people to share their personal experience with Ubuntu. While my post talked a lot about Windows 7, my main goal was to compare and contrast the two.


> 

So ... we have a user that knows nothing about Windows, and use a program called obligon or something like that ... under wine ofcourse =D ... install a lot of useless programs under windows and say bad things of it ... let s say it s a good point of view :confused:

The program is called Oblivion and it is a 3D video game. I only installed that game (from a DVD that I got at Walt-Mart), Adobe Reader and a 7zip archive program. Do you know of a way to install a 7zip or rar program without downloading it from some web-page. I was contrasting that to the trusted repository system of Ubuntu.

> 

So ... i really like ubuntu and linux in general ... but i think things like that dont allow us to grow up like community ... 

If u have to expose these things in a conference ... like ve seen ... u ll be very frustrated ... a windows user would say ... 
I don't understand what you are trying to say. What is prohibiting the community from growing? My criticism of Windows 7? What do you means by a conference, I have given many conference talks on my Ubuntu laptop, however, those were about Math and not operating systems. I am frustrated with Windows and I have sometimes been frustrated with Linux. Can you please clarify this.

> 

- obligon under wine? this is windows code ... don t u have a native obligon for linux? :)
3D games very rarely come out natively for Linux, however, Oblivion works perfectly under wine (so long as you have a good video card and a good driver).

> 
- can u play fullscreen HD youtube videos under the crap of X server and ur "proyect of driver for ur ATI/NVIDIA" ... consuming less than 30% of CPU ?

In Ubuntu, open Movie Player (totem) and select YouTube from the play list menu. Search for your favorite video and see if you like how light it is. I don't think that the X-server is the crap, the problem is with the Linux version of flash that is released by Adobe. I don't think the fact that people make good programs for an OS makes that OS good in itself.

Also, while flash does take a lot of CPU under Linux, you should also compare how much RAM it is using.

> 
- software integration ... did u read something about OLE object? ... i think not ... can u paste an object from DIA to openoffice directly and edit it in openoffice? ... NO ... i imagine !
Again you are listing specific software. I am sure you need this for work, but it is not fair to praise Microsoft or bash Ubuntu based upon what other people have done for one or the other. I understand that some people are simply forced to use Windows by such circumstances and I totally feel your pain.

> 
- is ur wireless card working fine? and what about hibernation?I have a cheap Lenovo laptop and my wife has a nice System 76 Pangolin. I have had no problems with wireless cars, hibernation or whatsoever. Look up System 76, they have very nice machines that come with Ubuntu preinstalled and working out of the box.  Great support too.

(I just saw that you are from Argentina and I don't think System 76 ships outside USA. There are web pages that list laptop models and how well they work with Linux, you should check them out next time you are buying a machine.)

> 

- problems with upstart, flymouth, ureadahead, new kernel?

I don't know what those are, except for the kernel. I often compile my own kernels to optimize them for my machines, but this is not because I have to, it is just because I like to do it.

> 

- do u work with ur computer? did u try to make a complex engineer diagram like i do in VISIO with DIA??????????? 
I play games a lot, but I mainly work on my machines. I don't draw many diagrams, but I do use MATLAB and C++ to develop new algorithms in computational Mathematics (that is why I got the new video card, I want to do 64-bit numerical computations). There is a reason why 90% of the top 500 supercomputers in the world use Linux (the other 10% use othe variants of Unix). Windows is simply incapable of handling the power. Well, XP was, I haven't tested Windows 7 and I wouldn't be able to do it anyway (I only have a 32-bit version of it and it is totally unfair to match it to a 64-bit system).

> 
Ohhhhh ... but the guy has flying windows with compiz and boot his OS in 10 secs ... that s great !!!! ... opensource software like DIA, firefox, thunderbird, pidgin, vlc, gvim, virtualbox, eclipse .... work better on windows than on linux ... try them for a bit please!

Windows 7 came out with claims for all of those revolutionary changes that it is introducing. Aero effects were a big thing in their adds. While Aero looks nice, the truth is, that they are years behind Compiz.

I don't care much about the 10 second boot in Ubuntu, but that is mainly because unlike Windows, I only have to reboot if I happen to update the kernel.

FireFox is an outdated browser, both Konqueror and Midori are ahead of it and Google Chrome works great under both systems. I don't use Thunderbird, simply because I like the simplicity of Claw Mail. I prefer Totem, Dragoon and MPlayer to VCL, but that is just my preference.

I do use Virtualbox, mostly for my printing needs. I would much rather run Linux as my main OS and use an old copy of XP for the occasional printing task, than the other way around. 

> 

I think there are good opensource software out there ... but linux for desktops is not mature enough today ... there are a lot of things that must be arranged ...

I am sorry to hear that you have had some bad experience, however, while you are not alone in this, I do think you are in a minority.

I have been using Ubuntu exclusively for years. I don't think I can ask any more of than what it offers today. There are things that need to be improved, but people are working on them faster than one can imagine possible. There is a new version every 6 months, this easily beats Windows and Mac 4 - 6 versions to one. 


> 

Look at this ... the GVIM editor ... my favourite ... try to print something in linux ... u ll be redirected to a windows saying "lpr -P ..." ?????? ... in windows u ll be redirected to the classic printer window selection ... that s the software integration we all want my friend !

Please see my post called "My little contribution" under these same Forum ...

Bye ...I did read the posts in your thread. 

My biggest point would be about the registry. This is one of the worst concepts of the Windows world. The entire system is 100% dependent on a single database, which inevitably gets cluttered the more software you add and remove. Windows always slows down over time and you have to engage in all kinds of maintenance activities, like clean the registry, defragment, scan for spyware and so on. A crash in the registry can simply destroy the entire system.

On the other hand, simple text files are so much better, and yes perhaps XML would be even better.

"lpr -P" is a bug, please report that in either Ubuntu or GVIM bugzilla pages. They do care about those things and will try to fix the issue.

You seems to be unhappy with the many choices of Linux, well I prefer too many choices to too little. I don't want to be restricted to doing things only one way or another. As for writing apps, one rarely writes apps for an environment, much less a kernel version. One simply uses the tools in the open source GTK or the proprietary QT. It is true that Gnome and XFCE are based upon GTK and KDE is based upon QT, so mixing those might cause some slow down, but I am yet to see in Ubuntu a GTK app that fails under KDE and QT app that fails under Gnome/XFCE. The choice is not a choice of functionality, but rather a personal preference and comfort.

---

### Post by arizwan on 2010-04-27
> **3Miro said:**
> This part of the forum is for people to share their personal experience with Ubuntu. While my post talked a lot about Windows 7, my main goal was to compare and contrast the two.




The program is called Oblivion and it is a 3D video game. I only installed that game (from a DVD that I got at Walt-Mart), Adobe Reader and a 7zip archive program. Do you know of a way to install a 7zip or rar program without downloading it from some web-page. I was contrasting that to the trusted repository system of Ubuntu.



I don't understand what you are trying to say. What is prohibiting the community from growing? My criticism of Windows 7? What do you means by a conference, I have given many conference talks on my Ubuntu laptop, however, those were about Math and not operating systems. I am frustrated with Windows and I have sometimes been frustrated with Linux. Can you please clarify this.



3D games very rarely come out natively for Linux, however, Oblivion works perfectly under wine (so long as you have a good video card and a good driver).

> 
- can u play fullscreen HD youtube videos under the crap of X server and ur "proyect of driver for ur ATI/NVIDIA" ... consuming less than 30% of CPU ?
[/CODE]
In Ubuntu, open Movie Player (totem) and select YouTube from the play list menu. Search for your favorite video and see if you like how light it is. I don't think that the X-server is the crap, the problem is with the Linux version of flash that is released by Adobe. I don't think the fact that people make good programs for an OS makes that OS good in itself.

Also, while flash does take a lot of CPU under Linux, you should also compare how much RAM it is using.

```

- software integration ... did u read something about OLE object? ... i think not ... can u paste an object from DIA to openoffice directly and edit it in openoffice? ... NO ... i imagine !

```Again you are listing specific software. I am sure you need this for work, but it is not fair to praise Microsoft or bash Ubuntu based upon what other people have done for one or the other. I understand that some people are simply forced to use Windows by such circumstances and I totally feel your pain.



I have a cheap Lenovo laptop and my wife has a nice System 76 Pangolin. I have had no problems with wireless cars, hibernation or whatsoever. Look up System 76, they have very nice machines that come with Ubuntu preinstalled and working out of the box.  Great support too.

(I just saw that you are from Argentina and I don't think System 76 ships outside USA. There are web pages that list laptop models and how well they work with Linux, you should check them out next time you are buying a machine.)



I don't know what those are, except for the kernel. I often compile my own kernels to optimize them for my machines, but this is not because I have to, it is just because I like to do it.



I play games a lot, but I mainly work on my machines. I don't draw many diagrams, but I do use MATLAB and C++ to develop new algorithms in computational Mathematics (that is why I got the new video card, I want to do 64-bit numerical computations). There is a reason why 90% of the top 500 supercomputers in the world use Linux (the other 10% use othe variants of Unix). Windows is simply incapable of handling the power. Well, XP was, I haven't tested Windows 7 and I wouldn't be able to do it anyway (I only have a 32-bit version of it and it is totally unfair to match it to a 64-bit system).



Windows 7 came out with claims for all of those revolutionary changes that it is introducing. Aero effects were a big thing in their adds. While Aero looks nice, the truth is, that they are years behind Compiz.

I don't care much about the 10 second boot in Ubuntu, but that is mainly because unlike Windows, I only have to reboot if I happen to update the kernel.

FireFox is an outdated browser, both Konqueror and Midori are ahead of it and Google Chrome works great under both systems. I don't use Thunderbird, simply because I like the simplicity of Claw Mail. I prefer Totem, Dragoon and MPlayer to VCL, but that is just my preference.

I do use Virtualbox, mostly for my printing needs. I would much rather run Linux as my main OS and use an old copy of XP for the occasional printing task, than the other way around. 



I am sorry to hear that you have had some bad experience, however, while you are not alone in this, I do think you are in a minority.

I have been using Ubuntu exclusively for years. I don't think I can ask any more of than what it offers today. There are things that need to be improved, but people are working on them faster than one can imagine possible. There is a new version every 6 months, this easily beats Windows and Mac 4 - 6 versions to one. 




I did read the posts in your thread. 

My biggest point would be about the registry. This is one of the worst concepts of the Windows world. The entire system is 100% dependent on a single database, which inevitably gets cluttered the more software you add and remove. Windows always slows down over time and you have to engage in all kinds of maintenance activities, like clean the registry, defragment, scan for spyware and so on. A crash in the registry can simply destroy the entire system.

On the other hand, simple text files are so much better, and yes perhaps XML would be even better.

"lpr -P" is a bug, please report that in either Ubuntu or GVIM bugzilla pages. They do care about those things and will try to fix the issue.

You seems to be unhappy with the many choices of Linux, well I prefer too many choices to too little. I don't want to be restricted to doing things only one way or another. As for writing apps, one rarely writes apps for an environment, much less a kernel version. One simply uses the tools in the open source GTK or the proprietary QT. It is true that Gnome and XFCE are based upon GTK and KDE is based upon QT, so mixing those might cause some slow down, but I am yet to see in Ubuntu a GTK app that fails under KDE and QT app that fails under Gnome/XFCE. The choice is not a choice of functionality, but rather a personal preference and comfort.another long post that I actually enjoyed reading :)

---

### Post by mastablasta on 2010-04-28
>  
On the second boot I installed the ATI driver, it took some time to find the right driver on the Internet (had to go to AMD/ATI's site, not XFX), and there was no nice window with a check box: use the proprietary driver.

 
This is not true - the drivers are (have to be) provided with the card. And even if you needed the latest ones they are very easy to find. You would have to do the same in Linux (donwload and install).
 
>  
Windows naturally doesn't come with AV at all, however, there are free AV programs (free as in legally free of charge). I just don't know how good they are.

 
They are of medium quality. If you take care of the sites you go to they can help otherwise they just waste system resources. They also can't really be used as cleaning programmes. In conjunction with a medium quality free firewall they make a good team.

---

### Post by Dayofswords on 2010-04-28
i want to throw in that 7zip is amazing, legitimate, safe, open source archive maker/extractor

its primary format 7z doesnt hold permissions here in Linux, so its not used so much here, but its still good ratio.

7zip is even in the repo(its command line, but things can use it)

> I also remember Windows 98, where you could click cancel on the password login screen and you would still get in.

I remember this too. :)

> And as for the many desktops, I don't know how many times I scrolled the mouse on the background in a futile attempt to go to the next workspace
what do you have set up to do this?

---

### Post by GodLikeCreature on 2010-04-28
I very much agree with most of your review, very good one!

I think lots of people miss the point when comparing Win7 and Ubuntu or any other major Linux distro.  There is so much that is good about Linux that can only be appreciated after a decent amount of use...

---

### Post by Linuxforall on 2010-04-28
Excellent review, this is a keeper for me.

---

### Post by 3Miro on 2010-04-28
> **mastablasta said:**
> This is not true - the drivers are (have to be) provided with the card. And even if you needed the latest ones they are very easy to find. You would have to do the same in Linux (donwload and install).


The card was manufactured and packaged some time ago. 4850 is far from a new line. You are right that it cam with a disk, but at this point it is always a better idea to go and look on-line. Ubuntu on the other hand, always comes with pretty new driver right from the repos (maybe one version late, depending on the release cycles of both Ubuntu and the manufacturer).

On the other hand, installing the latest-latest Linux driver right from NVIDIA or ATI can be a bit tricky.

---

### Post by Linuxforall on 2010-04-28
Latest nvidia via run file is not tricky at all, in fact I do it on regular basis, remove older one by sudo nvidia-uninstall after stopping gdm and then install latest one after reboot.

---

### Post by 3Miro on 2010-04-28
> **Dayofswords said:**
> i want to throw in that 7zip is amazing, legitimate, safe, open source archive maker/extractor

its primary format 7z doesnt hold permissions here in Linux, so its not used so much here, but its still good ratio.

7zip is even in the repo(its command line, but things can use it)


I could have researched the software to see if it is legitimate (and OSS by that), but it would have taken me more time. With the repos I don't have to do a lot of reading for a small utility.

I guess I can try it under Linux now. Yes, I am back to using an operating system.

> 
what do you have set up to do this?


Under compiz: got to compiz-config-settings-manager (install it from synaptic if you have to) -> Viewport Switcher -> Desktop-based viewport switching, then associate Move Left and Move Right with buttons 4 and 5 (test to see which one you want to be left and right).

Under xfce (xfwm): Settings -> Windows Manager Tweaks -> Workspaces, use the mouse wheel ....

As far as I know, metacity does not support this.

---

### Post by uRock on 2010-04-28
> **3Miro said:**
> I have a cheap Lenovo laptop
Lol, I love my Lenovo. I received it as a X-mas gift and thought it would be junk, because I had never heard of Lenovo at the time. It has turned out to be the best system I have ever owned. I have seen a lot of people having issues with Lenovo's laptops not behaving well with Ubuntu, hopefully that will change in Lucid.

---

### Post by 3Miro on 2010-04-28
> **uRock said:**
> Lol, I love my Lenovo. I received it as a X-mas gift and thought it would be junk, because I had never heard of Lenovo at the time. It has turned out to be the best system I have ever owned. I have seen a lot of people having issues with Lenovo's laptops not behaving well with Ubuntu, hopefully that will change in Lucid.

Don't get me wrong, the Lenovo laptop is very solid, it is just that the specs are not going to impress anyone and I got it mainly because of the price. It has been working great for me, except one of the keys on the keyboard is broken and I don't know if it is Ubuntu or the hardware, but I cannot burn CDs and DVDs. For that money, it is worth to get an external keyboard and use only the ASUS burner on my desktop.

No problems with suspend, wireless and/or dual monitor under Gnome and XFCE.

---

### Post by lin73 on 2010-04-28
I'd like to point out first that I'm not an IT expert, and don't have any advanced knowledge in programming (etc...) to judge about really technical sides of either OS (Ubuntu or windows 7). But as someone who has tried both, I don't think Windows 7 is a hassle as described in the first post. I downloaded the trial RC of windows 7 some few months ago (late 2009 I think), and it detected all hardware seamlessly, didn't have software compatibility issues, and looked pretty nice; And in fact, it never crashed. Many of the problems that were mentioned here are related to unfamiliarity with windows: Restarts during installation (is it really a huge deal given that it's a 1 time process?), showing files' extensions (it's a fairly simple deal), and finding proper (and free) compression software (plenty available). All in all, it's a pretty good OS; It doesn't need to be bad for another OS to be good.

I tried Ubuntu 9.1 in that same period, and it worked fairly well too. Previous versions had problems with detecting wireless network cards (had to go through the ndiswrapper, pppoeconf etc), and video card drivers. The problem is that it once crashed after either a kernel update (or another change I made to some configuration files that I don't really remember); Being unable to fix it, and since I didn't like the gnome environment and the brownish theme all that much (Yes I know it's all customizable, but I couldn't make it look much better), I installed another linux distribution with the KDE environment, and have been using it almost exclusively for some 6 months. Windows remains useful though for CAD applications (mainly Autocad), and other software that don't seem to run very smoothly with wine.
Looking forward to try the 10.04.

Regards

---

### Post by blur xc on 2010-04-28
I recently did a clean install of Win 7 and my experience was really quite pleasant compared to yours.  I need windows for work, can't help that, but I stuck my disk in, and it didn't take more than 20mins to get up to a running desktop again.  Now reinstalling all my software wasn't nearly as easy as a few sudo aptitude installs, but it got done.  My only outstanding issue is my gigabit lan card isn't running at gigabit speeds, but either way- it's been pretty good.  I had a few drivers missing which I got off the dell website, and whatever ones I missed, Win 7 found them and downloaded them for me.  I thought that was pretty impressive...

I wonder if some of the headaches are from starter or home editions, because the professional and ultimate editions I use at work never rebood during the middle of the day like my home pc w/ vista (and the old pc w/ xp) used to do.  At work, they both install and configure updates when I shut down at the end of the day.

BM


BM

---

### Post by blwizard on 2010-04-29
I'd say this review is a bit biased but it's nice. I agree with most of your points made. Having been using Linux for ages, I hate the constant reboot prompt in Windows so much, Why in the name of abyss would installing a pdf reader require system reboot? I also can't get used to the way how Windows manages software installation either. Where is the software repository? Where are all the useful programming tools? So I mainly use Windows for games, which I don't really have much time for. Once in a while when I use windows for some simple work, I always wonder why couldn't Windows get some virtual desktops to avoid the desktop getting too crowded.

It seems to me that after people get used to working on Linux, it's hard to switch back to Windows, and vice versa. However, I don't seriously hate Windows, it has it uses and I use it whenever is appropriate.

---

### Post by Rodney9 on 2010-04-29
> **Objekt said:**
> That is sig material right there!

> I installed the Windows 7 RC last October, and have reached more or less the same conclusions.  In the final analysis, I wasn't all that excited about paying big bucks for more of the same.  Windows XP is perfectly adequate for the non-serious tasks (read: games) for which I now use it.

I did and thought the same exactly.

---

### Post by 3Miro on 2010-04-29
> **lin73 said:**
> I'd like to point out first that I'm not an IT expert, and don't have any advanced knowledge in programming (etc...) to judge about really technical sides of either OS (Ubuntu or windows 7). But as someone who has tried both, I don't think Windows 7 is a hassle as described in the first post. I downloaded the trial RC of windows 7 some few months ago (late 2009 I think), and it detected all hardware seamlessly, didn't have software compatibility issues, and looked pretty nice; And in fact, it never crashed. 


Windows never crashed for me either and this is a big step up from XP or Vista, but after Linux, I raze the bar higher than that. Also, compatibility issues are rare (maybe not for Vista, but for XP and 7) mostly because both hardware and software is primarily done for windows (see my point for Microsoft taking credit for other people's good software).

> 
Many of the problems that were mentioned here are related to unfamiliarity with windows: Restarts during installation (is it really a huge deal given that it's a 1 time process?), showing files' extensions (it's a fairly simple deal), and finding proper (and free) compression software (plenty available). All in all, it's a pretty good OS; It doesn't need to be bad for another OS to be good.


I am used to playing with different Linux distros and I often install and reinstall (I have one main distro and one test partition for others). Unlike Linux, most people never install their own Windows. Most people that have trouble with Ubuntu and end up giving it up, are usually having precisely installation issues.

Finding the settings for file extensions is a non-issue, the point is that the system if very heavily dependent on file names. My mom (who is still using XP on an old PC) often has to rename files that I send her, before she can open them. I don't know how Linux does it, but it has no such issues.

I found free compression software on the first try, but I would normally have to do extra research to make sure I am not installing the latest version of spy_on_my_computer_virus_now. It is a big contrast to the repos.

> 

I tried Ubuntu 9.1 in that same period, and it worked fairly well too. Previous versions had problems with detecting wireless network cards (had to go through the ndiswrapper, pppoeconf etc), and video card drivers. The problem is that it once crashed after either a kernel update (or another change I made to some configuration files that I don't really remember); Being unable to fix it, and since I didn't like the gnome environment and the brownish theme all that much (Yes I know it's all customizable, but I couldn't make it look much better), I installed another linux distribution with the KDE environment, and have been using it almost exclusively for some 6 months. Windows remains useful though for CAD applications (mainly Autocad), and other software that don't seem to run very smoothly with wine.
Looking forward to try the 10.04.

Regards

A kernel update issue can be resolved with holding the Shift key while booting and using an older version of the kernel. You can also set up an older version to be the default. I had some trouble with a 9.10 update at one point. Most issues with Ubuntu come from video and wireless drivers as well as flash. Ironically, those are precisely the proprietary parts of the system.

I am not much of a fan of Gnome and KDE doesn't work very well on Kubuntu (I hope they manage to fix this for 10.04). Mandriva and Sabayon are much better when it comes to KDE. I myself use mainly XFCE, which looks like Gnome, but is much faster.

I know that many people are still stuck with windows for some application or another, I am happy to be free myself.

Thanks for the good points.

---

### Post by uRock on 2010-04-29
I thought Windows7 was pretty awesome. Installed in less than an hour with no problems what so ever. The interface is sharp and they made administering it even easier with the new menu layouts. 

I still prefer Ubuntu over W7 any day.

---

### Post by fedexnman on 2010-04-29
i bought w7,  the installer is horrible, so much waiting, the microsoft devs should try installing ubuntu or try updating a mac . 1st impression its a more polished vista thats more like xp.  2nd impression why the heck did i pay for this ?? i also thought about installing snow leopard on my pc just for something to do and have itunes. i love the free factor of ubuntu !

---

### Post by Endolith on 2010-04-30
I've been running Ubuntu for a few years, and have been growing increasingly frustrated with it.

At work, I've been running Windows 7 for a few months, and it's really great in comparison.  

Canonical's attempts at hiding their underlying problems by painting over them with a new theme every 6 months aren't working on me.  I think with my next computer I'm going to switch back to Microsoft.  :)  I'll gladly pay for an OS and lose a little bit of "freedom" if it runs stably and I can have my free time back and fewer headaches.

---

### Post by uRock on 2010-04-30
Every Ubuntu I have used has been rock solid as far as stability goes.

---

### Post by lavinog on 2010-04-30
> **3Miro said:**
>  Ubuntu on the other hand, always comes with pretty new driver right from the repos (maybe one version late, depending on the release cycles of both Ubuntu and the manufacturer).

On the other hand, installing the latest-latest Linux driver right from NVIDIA or ATI can be a bit tricky.

The ATI binary driver that shipped with the last 3 releases were pre-releases and had their share of bugs.  Usually the driver released the next month addressed the bugs.  ATI releases a new driver each month.  Sometimes some versions have worse regressions than the previous, so sometimes newer is not always better though.

The ATI installer is pretty straight forward though: download the installer from AMD's website, run the installer with sudo bash installerfile, once complete, reboot (I think restarting X is all that is needed, but with dontzap enabled it seems easier to just reboot)

---

### Post by 3Miro on 2010-04-30
> **Endolith said:**
> 
Canonical's attempts at hiding their underlying problems by painting over them with a new theme every 6 months aren't working on me.  I think with my next computer I'm going to switch back to Microsoft.  :)  I'll gladly pay for an OS and lose a little bit of "freedom" if it runs stably and I can have my free time back and fewer headaches.

Can you be more specific on the underlying problems that you are mentioning?

---

### Post by randolf_ambrose on 2010-04-30
> **sixthwheel said:**
> I usually don't have the patience to read long posts, but yours got me from the first line and kept me glued to the screen.:)

Good post.

same here!!!

good post!!!:lolflag:

---

### Post by bigseb on 2010-04-30
Not only did I read the entire first post (a rarity with something so long) but also every reply that followed. Made me wonder... why does the rest of the world not know what we do?

---

### Post by Frak on 2010-05-02
There's so much BS in this story, well, I don't even want to sift through it.

For one, ATi drivers don't reboot Windows 7. The driver model in 7 allows drivers to hotswap instantly, without reboot. It's rare to see any driver actually reboot the system, and when they do, it's usually because they were made for Vista.

Secondly, worrying about installing random crap is an issue regardless of your OS. Recently, we had a Trojan passed through gnome-look that compromised many, many, many Ubuntu systems. Linux is not immune to them either, and is a direct result of the user becoming complacent. Windows does not make you administrator by default and uses UAC to make you more aware of what is trying to execute on your system. If you allow a program to do administrative tasks, it is only your fault, and nobody else's. You were warned.

Thirdly, Windows does not have a "try Windows 7 option" because it would be trivial. People know Windows will work with their system, and due to the lack of competence of many users, a live mode could damage the installing system.

Lastly, not the last point, but the last point I'll go over, Aero was designed to be visually pleasing but not be obtrusive nor harm the system in available resources. Compiz, on the other hand, just goes out to do everything. Compiz is very resource inefficient, consuming upwards of a couple hundreds megabytes of RAM while running. Aero (DWM) usually runs within ten megabytes (according to me and nearly a hundred of my closest friends). Aero tries to look nice without being in the way.

Also, the part on file integration sounds like clever rhetoric. Don't take a problem from a 3rd party application and blame it on Microsoft. WinRAR can open PDFs just fine from an archive. As for the repository, that would be incredibly difficult to manage. There millions of applications available for Windows, and categorizing and testing them all would be unfeasible. Why do that when the internet exists?

---

### Post by QwUo173Hy on 2010-05-03
That was a very interesting post 3Miro, thank you for sharing that. I bought a laptop for my mother with windows 7 on it for my mother. The first thing she did was fire up IE and my god, there was so much rubbish in the menus and bookmarks etc.

I put Lucid alpha 3 on as an option and she's still using it now and I've done very little in the line of explaining things. 

Don't get me wrong, there are some usability problems with Gnome, but I get fewer phone calls from the owners of machines I put Ubuntu on than from those running Win.

And as for the comment a poster made about the gnome-theme trojan .. that hardly catches us up to the level of vulnerability and susceptibility that Windows experiences does it? Really, talk straight.

---

### Post by mastablasta on 2010-05-03
> **3Miro said:**
>  
I found free compression software on the first try, but I would normally have to do extra research to make sure I am not installing the latest version of spy_on_my_computer_virus_now. It is a big contrast to the repos.

 
 
Then again repos don't have all the latest software with newest features. So if you encounter a bug upon a system upgrade you are on your own. In fact upgrading Linux can be quite painfull process (if you use it for other things that just browsing, games, wordprocessing and such). On the contrary Windows (unless you did a Vista) is an easy and painless process. I have a computer at home who was slowly upgraded from Win95 to Win98 to XP in the end. I am sure Win7 upgrade would also do well on it.
 
Also you mention running old kernels. Do you also run Windows unpatched? This is like leaving the doors open to cybercriminals.
 
It's not that Windows are much better system but they do have better support. It's much longer and free. And they have reasonably good backwards compatibility (either through their own system or 3rd party software). If you need to spend even 7 hours on getting something to work in linux it's already more expencive than buying windows home and have it working instantly.
 
I have been using windows for a long time and i have to say i really didn't have any software related issues. The one i did have runed out to be a hardware malfunctioning. And when i replaced the faulty part it all worked well. 
 
BTW good GPU card you have there :-P i used the default drivers, see how they worked and if games i played worked well i left it there. maybe later when i had time i downloaded the stuff and updated. But upon first install it's not really necessary to do driver upgrade unless you really need it.

---

### Post by uRock on 2010-05-03
> **mastablasta said:**
> Then again repos don't have all the latest software with newest features. So if you encounter a bug upon a system upgrade you are on your own. In fact upgrading Linux can be quite painfull process (if you use it for other things that just browsing, games, wordprocessing and such). On the contrary Windows (unless you did a Vista) is an easy and painless process. I have a computer at home who was slowly upgraded from Win95 to Win98 to XP in the end. I am sure Win7 upgrade would also do well on it.
I was reading about Windows 7 and they were having a lot of problems with upgrades.

---

### Post by MarcusW on 2010-05-03
> **Frak said:**
> There's so much BS in this story, well, I don't even want to sift through it.

For one, ATi drivers don't reboot Windows 7. The driver model in 7 allows drivers to hotswap instantly, without reboot. It's rare to see any driver actually reboot the system, and when they do, it's usually because they were made for Vista.

Secondly, worrying about installing random crap is an issue regardless of your OS. Recently, we had a Trojan passed through gnome-look that compromised many, many, many Ubuntu systems. Linux is not immune to them either, and is a direct result of the user becoming complacent. Windows does not make you administrator by default and uses UAC to make you more aware of what is trying to execute on your system. If you allow a program to do administrative tasks, it is only your fault, and nobody else's. You were warned.

Thirdly, Windows does not have a "try Windows 7 option" because it would be trivial. People know Windows will work with their system, and due to the lack of competence of many users, a live mode could damage the installing system.

Lastly, not the last point, but the last point I'll go over, Aero was designed to be visually pleasing but not be obtrusive nor harm the system in available resources. Compiz, on the other hand, just goes out to do everything. Compiz is very resource inefficient, consuming upwards of a couple hundreds megabytes of RAM while running. Aero (DWM) usually runs within ten megabytes (according to me and nearly a hundred of my closest friends). Aero tries to look nice without being in the way.

Also, the part on file integration sounds like clever rhetoric. Don't take a problem from a 3rd party application and blame it on Microsoft. WinRAR can open PDFs just fine from an archive. As for the repository, that would be incredibly difficult to manage. There millions of applications available for Windows, and categorizing and testing them all would be unfeasible. Why do that when the internet exists?

Pretty much the biggest + Ubuntu has in security over windows is because of the repo, secure downloads from a trusted source. I do believe you realize a software repo DOES NOT contain every <expletive deleted> program ever compiled for that operating system. I don't see why a repo with the same software as in Ubuntu would be harder than in Ubuntu.

Even if it would be hard to implement, that doesn't mean it isn't a downside of using windows.

---

### Post by VastOne on 2010-05-03
> **sixthwheel said:**
> I usually don't have the patience to read long posts, but yours got me from the first line and kept me glued to the screen.:)

Good post.

Ditto.  And though we all have been there and done that, it still was a joy to read...I guess I am sadistic or a masochist after all.

---

### Post by 3Miro on 2010-05-03
> **Frak said:**
> There's so much BS in this story, well, I don't even want to sift through it.

For one, ATi drivers don't reboot Windows 7. The driver model in 7 allows drivers to hotswap instantly, without reboot. It's rare to see any driver actually reboot the system, and when they do, it's usually because they were made for Vista.


The motherboard drivers requires a reboot. The latest ATI driver from AMD required a reboot. Installing Adobe Reader, of all things, required a reboot (and then again when it was updated). I downloaded this from Adobe's web-page for Windows 7.

> 
Secondly, worrying about installing random crap is an issue regardless of your OS. Recently, we had a Trojan passed through gnome-look that compromised many, many, many Ubuntu systems. Linux is not immune to them either, and is a direct result of the user becoming complacent. Windows does not make you administrator by default and uses UAC to make you more aware of what is trying to execute on your system. If you allow a program to do administrative tasks, it is only your fault, and nobody else's. You were warned.



Installing random stuff is always an issue. If you give any random program administrative privileges then no defense can help you. On the other hand, in the case of Ubuntu, you have the trusted repositories. May not be 100% perfect, but it is something. There are no repositories for Windows. I don't want every Windows program in a database. I just want basic utilities, archive program, documents readers (.pdf, .doc ... ), couple of medial players (not one WMP fit all mentality) and a few others.

> Thirdly, Windows does not have a "try Windows 7 option" because it would be trivial. People know Windows will work with their system, and due to the lack of competence of many users, a live mode could damage the installing system.

A few years ago a friend of mine had a computer that he had declared total loss. He gave it to me for free. Windows 2000 and Windows XP would both fail to install on it. Mandrake 8 worked flawlessly. Computers are made for Windows and that is why there are only a few problems (Vista also comes to mind). If you want a nice Linux machine, go to System 76.

How can a live mode damage the system? The only way I can think of is if you mess with files on the hard-drive, but you can do that once the system is installed anyway.

> 
Lastly, not the last point, but the last point I'll go over, Aero was designed to be visually pleasing but not be obtrusive nor harm the system in available resources. Compiz, on the other hand, just goes out to do everything. Compiz is very resource inefficient, consuming upwards of a couple hundreds megabytes of RAM while running. Aero (DWM) usually runs within ten megabytes (according to me and nearly a hundred of my closest friends). Aero tries to look nice without being in the way.


Compiz lets you pick and chose between all the different effects, on the basic level it is fast and it starts to drain resources only after you turn too much stuff on. Furthermore, compiz is a hack on top of Gnome, if you want a good comparison between desktop effects, try Aero vs Kwin.

Later I did run a test with the memory usage of Windows 7. From a fresh boot: Skype + Google Chrome playing/loading a YouTube video + WMP with a small mp3 took almost a gig of RAM. I wanted to compare that to Linux, but at the time I only had my laptop with XFCE and I decided that it is in no way a fair match. I should try Ubuntu just for fun.

> 

Also, the part on file integration sounds like clever rhetoric. Don't take a problem from a 3rd party application and blame it on Microsoft. WinRAR can open PDFs just fine from an archive. As for the repository, that would be incredibly difficult to manage. There millions of applications available for Windows, and categorizing and testing them all would be unfeasible. Why do that when the internet exists?

And while it is not fair to blame Microsoft for other people's crappy software, it is surprising how often Windows takes credit precisely for the good apps that others have made. You have to have it both ways or no way, and if we were to separate Windows from the apps for Windows, I wonder what would be left. Windows comes with IE, WMP and Minesweeper.

---

### Post by uRock on 2010-05-03
> **Frak said:**
> There's so much BS in this story, well, I don't even want to sift through it.

For one, ATi drivers don't reboot Windows 7. The driver model in 7 allows drivers to hotswap instantly, without reboot. It's rare to see any driver actually reboot the system, and when they do, it's usually because they were made for Vista.

Secondly, worrying about installing random crap is an issue regardless of your OS. Recently, we had a Trojan passed through gnome-look that compromised many, many, many Ubuntu systems. Linux is not immune to them either, and is a direct result of the user becoming complacent. Windows does not make you administrator by default and uses UAC to make you more aware of what is trying to execute on your system. If you allow a program to do administrative tasks, it is only your fault, and nobody else's. You were warned.

Thirdly, Windows does not have a "try Windows 7 option" because it would be trivial. People know Windows will work with their system, and due to the lack of competence of many users, a live mode could damage the installing system.

Lastly, not the last point, but the last point I'll go over, Aero was designed to be visually pleasing but not be obtrusive nor harm the system in available resources. Compiz, on the other hand, just goes out to do everything. Compiz is very resource inefficient, consuming upwards of a couple hundreds megabytes of RAM while running. Aero (DWM) usually runs within ten megabytes (according to me and nearly a hundred of my closest friends). Aero tries to look nice without being in the way.

Also, the part on file integration sounds like clever rhetoric. Don't take a problem from a 3rd party application and blame it on Microsoft. WinRAR can open PDFs just fine from an archive. As for the repository, that would be incredibly difficult to manage. There millions of applications available for Windows, and categorizing and testing them all would be unfeasible. Why do that when the internet exists?

Every time I've had to change nVidia drivers I have had to restart. Other than that I agree with everything else you have pointed out. 

I would like to add that if Microsoft had to maintain even the most popular of programs in a repo, they would then add to the price for their costs to maintain such a repo. Just as if and when ubuntu starts adding paid material to Ubuntu Software Center it will most likely be taking a cut of the money charged.

---

### Post by 3Miro on 2010-05-03
> **uRock said:**
> 
I would like to add that if Microsoft had to maintain even the most popular of programs in a repo, they would then add to the price for their costs to maintain such a repo. Just as if and when ubuntu starts adding paid material to Ubuntu Software Center it will most likely be taking a cut of the money charged.

Ubuntu will always provide hundreds of apps that are free as in freedom and free and in cheap. Otherwise, this will stop being a Linux distribution and I will be one of the first to run away from it.

In the case of Windows, I am not asking for a repo with commercial software. If I pay money for something, then I know that there is a company behind it. While they may spy on me to send me spam or something, they will not put something in their software that steals my credit-card. What I am talking about, is a repo for Windows with free (as in cheap) software that has been screened for viruses (as in identity theft) and usability (however, Microsoft might as well decide to charge for those anyway). There are already hundreds of free programs for Windows, it is just an extra effort to sort the good ones from the viruses.

---

### Post by Ms_Angel_D on 2010-05-03
Moved to the cafe, sine T&E is for reviews concerning the Ubuntu family.

---

### Post by Ugluk on 2010-05-06
You must be kidding.

> **3Miro said:**
> Ubuntu and Windows 7
...Windows 7 would refuse to install on an extended partition. Lies.
> OK, no password, but still it is an advancement from **XP**, where one would have to install extra software like Zone Alarm to get the simple feature of prohibiting someone from installing whatever they want.Lies.
> Oblivion. Since it is somewhat old, it actually works very well under wineLies.
> However, there was another problem. I couldn't see how to tell Windows to show the file extensions much less edit them. Result #2 for 'show file extensions'. Very difficult. > you have to explicitly extract the file first, before you can open it with another program.Lies.
<joke>> ...chasing after Deadra Lords from the infernal planes of Oblivion.Only 2 Daedra Lords make appearance in Oblivion and they are friendly.</joke>

Have you ever saw Windows 7? If yes, how could you make so many inaccuracies? Why are you trolling? People like you make a laughing stock out of Linux, honestly.

---

### Post by rottentree on 2010-05-06
It's hard to decide which OS I like more or like less.
1)The one which doesn't work as I want it to or 2)the one which doesn't work as it should.

I think I like 2) more but I use 1) more :|

---

### Post by beastrace91 on 2010-05-06
> **Ugluk said:**
> You must be kidding.

Lies.
Lies.
Lies.
 Result #2 for 'show file extensions'. Very difficult. Lies.
<joke>Only 2 Daedra Lords make appearance in Oblivion and they are friendly.</joke>

Have you ever saw Windows 7? If yes, how could you make so many inaccuracies? Why are you trolling? People like you make a laughing stock out of Linux, honestly.

I smell a troll... Windows 7 does refuse to install to extended partitions - and yes Elder Scrolls 4 does work well under Wine with nvidia

~Jeff

---

### Post by gasparov on 2010-05-06
It wasn't a nightmare for me, I like windows 7. Finally a Microsoft operating system that can be used.
I hope that this version doesn't have "that" directory (the one with thousand sub directories full of dlls ) that becomes huge after some month of usage.

It runs games much better that Vista, and games are the only reason why windows is still around ( and some others like CAD software).So its good

---

### Post by user1397 on 2010-05-06
I definitely agree with the OP, nearly every aspect of installing and maintaining an Ubuntu system is easier than for a Windows 7 system.

I have Win 7 on my desktop at home (got the $30 student pricing), and it is not as easy or painless to use as Ubuntu, but I have made some of the headaches go away, at least security wise, by having a password-protected admin account, and only using a limited account all the time (this way it is very much like sudo when doing administrative tasks), and by installing NoScript on firefox and being cautious when surfing the web.  This way I don't need to run any antivirus/antiadware/antispyware software.

---

### Post by kpkeerthi on 2010-05-06
> **sixthwheel said:**
> i usually don't have the patience to read long posts, but yours got me from the first line and kept me glued to the screen.:)

good post.

+1

---

### Post by dedis on 2010-05-06
I loled :lolflag:

---

### Post by Tristam Green on 2010-05-06
I like how the one guy who actually rebuffs the erroneous or fallacious claims gets automatically labeled a troll.

Stay classy, Café.

---

### Post by Ugluk on 2010-05-06
Is /dev/sda6 extended enough partition for you? I used it to test W7 for couple of months.
And by the fates I'm owner of Radeon videocard and TES:Oblivion too. It doesn't work as should in current development Wine version.

---

### Post by Rick B. on 2010-05-06
[SIZE="3"]To: 3Miro

The TRUE story goes that Bill Gates never really liked Windows that well. Guess what? He had Linux on his desktop. He said the only reason MS continued updating and selling Windows was because it was a good  money maker. After 13 years with WIN, I recently switched to Linux for good. NO regrets![/SIZE]

---

### Post by Ric_NYC on 2010-05-06
I have friends that use Windows... I always see them fighting with virus and spyware... I think they love installing toolbars on Internet Explorer. :)

---

### Post by profslughorn on 2010-05-06
rest of the world just don't care. take my instance:

- took me 1 week of reading this message board to get my wireless card up to full(er) signal on Gateway's version of the Acer AOD250. the answer was in backports.

- took me 3 days to get get 2 finger scrolling to work by finding a couple lines of text i had to add.

- since i did the 2 finger scrolling, the track pad goes haywire on log in. the only way to stop it was to put the computer to sleep and wake it. this persisted for 3 months until i updated to Lucid.

- ever tried getting XBMC to work with the Broadcom HD card? i had it working until i updated but i'm giving up now.


...however, i find this stuff kinda fun :p

rest of the world can't be bothered to take their car for an oil change every 3k-5k miles, what makes us think they'll be willing sit in front of a computer scouring forums for a solution?

Win 7 is about as idiot proof as anything right now when it comes to installing an OS. it has its faults but then so does everything else.

> **bigseb said:**
> Not only did I read the entire first post (a rarity with something so long) but also every reply that followed. Made me wonder... why does the rest of the world not know what we do?

---

### Post by blueturtl on 2010-05-06
> **3Miro said:**
> Ubuntu and Windows 7...

I might be in the same situation as you in some time as StarCraft 2 is about to get released. It's probably the only thing that I would really install Windows for...

During all these years I've been on Linux my memory has started playing tricks on me. Every now and then when fixing something in Linux I just think to myself: "Wouldn't it be easier to just get the support and comfort by using Windows. No more hacking to fix bugs, no more fighting to find drivers/support. Just download, double click, reboot and enjoy your computer."

But I know this is only fantasy. It was never like that for me on Windows. Never. Something always broke. Somehow against all odds, something would not work even though it was supposed to. I'd be fixing the drivers and the applications trying to find a solution through Google. Fixing one thing would break another one. Ubuntu and Linux are not perfect, but damn it - at least I can have them the way I want.

It's good to get a recap of how things are "on the other side of the aisle". Thank you for posting.

---

### Post by deanhopkins on 2010-05-06
Lol, that was a funny read, thanks. Really well written too!

---

### Post by &#32 Greg on 2010-05-06
> **profslughorn said:**
> rest of the world just don't care. take my instance:

- took me 1 week of reading this message board to get my wireless card up to full(er) signal on Gateway's version of the Acer AOD250. the answer was in backports.

- took me 3 days to get get 2 finger scrolling to work by finding a couple lines of text i had to add.

- since i did the 2 finger scrolling, the track pad goes haywire on log in. the only way to stop it was to put the computer to sleep and wake it. this persisted for 3 months until i updated to Lucid.

- ever tried getting XBMC to work with the Broadcom HD card? i had it working until i updated but i'm giving up now.


...however, i find this stuff kinda fun :p

rest of the world can't be bothered to take their car for an oil change every 3k-5k miles, what makes us think they'll be willing sit in front of a computer scouring forums for a solution?

Win 7 is about as idiot proof as anything right now when it comes to installing an OS. it has its faults but then so does everything else.

Unless of course you are coming from the other direction. Going from experience with Linux to Windows which you know nothing about can be difficult. You look for the software installer, and it isn't there. You try to open files like .pdfs, and they don't work. Try to switch workspaces and it doesn't happen. It's all perspective.

---

### Post by 3Miro on 2010-05-06
The thread was initially in the testimonial experience sub-forum. It was a good contrast to the many thread dedicated to bashing Ubuntu and Linux for being too different from Windoes. I decided to share my experience coming from the other way and it did spark a discussions, so it got moved.

BTW I don't consider myself a Windows noob. I had never used W7 before, but I was an XP user for many years. At the end, Windows 7 worked much better than XP and it worked exactly as it was meant to work. My problems was with the way it was designed to work.

Most of the Linux problems that people have, come from incompatible hardware and/or bad installs. Very few people ever need to install Windows and all hardware is designed and supported with Windows in mind. If you research the hardware properly and have the install done by someone with experience, there are little to no problems. My wife and I have two laptops (Lenovo and System 76) as well as a build-by-me desktop. The only issue I ever had was with one 64-bit printer driver (resolved with the use of Virtual Box) and the ATI issue (which was very specific related to wine). 

Suspend/hibernate, wireless and wired, audio, video etc it all works fine for me on all machines.

---

### Post by vacc73 on 2010-05-06
[FONT="Arial Black"][SIZE="3"]I have win7 on a separate hard drive on my computer. If I want to use it I have physically do the disconnect and the reconnect. I prefer it that way. I did this to help in the inevitable friendly arguments that ensue when ever some one asks me about linux. I figure that if I have experience with it, it will add weight to my argument, and it does more often than not. That said, win7 is still essentially what vista was intended to be if only MS hadn't got in it's own way. However it boots too slow and  you still spend TOO MUCH TIME using utilities to keep the system operating at a speed that is not as fast, I have found ,as linux. You still have to INVEST in anti virus software, and unless you are a gamer that wants to be on the bleeding edge, all win7 seems to have is the shiny (AERO) stuff. Open source will catch that one I'm sure but compiz has much that Aero doesn't. Unless there is software you need that won't run on linux, even with wine,.... Windows 7 after years of Ubuntu,... Naaaah! I wouldn't pay retail for it.(mine was a gift!):guitar:[/SIZE][/FONT]

---

### Post by uRock on 2010-05-06
What is with the big bolds?

---

### Post by uRock on 2010-05-06
> **vacc73 said:**
> [FONT=Arial Black][SIZE=3]I wouldn't pay retail for it.(mine was a gift!):guitar:[/SIZE][/FONT]
I got it for free also. Good old MSDNAA.

---

### Post by cammin on 2010-05-06
> **uRock said:**
> What is with the big bolds?

His 'font size' key is broken.

---

### Post by James78 on 2010-05-06
I got a genuine copy for free, so I figured why not have a dual boot, Win 7 for when I need it, Linux for everything else, because lets just face it, Linux = more features... Windows doesn't even have iso mounting built into the OS, you know how easy that would be to do...?

But anyways, when it comes to games, the best solution is to just bite the bullet and play it on Windows.. I dare you to get Crysis working perfectly on Linux...

For games there's Windows.. For everything else there's Masterca... Err Linux.

---

### Post by MasterNetra on 2010-05-06
Well to the OP.

1. Norton has always been garbage, it was a mistake to use it. For AV you want Avast or Antivira, free wise Avast. Firewall, comodo, and you can throw in threatfire for added protection, it barely touches the resources so no bigge.

2. It was unfortuante it took it so long for you. Installation on my Latitude D30 (with 1GM of ram, and theorically 80GB of space) took me around 45 min. Ubuntu is faster no question about it though. 

3. 7zip is perfectly fine I use it all the time, and there is a less featured version of 7zip in ubuntu's rep, just search for .7z. 

While Ubuntu and many linux distro in general are overall superior to windows. Windows 7 is by far the most behaved and better secured system of the windows brand...that said however, they still have a ways to go to reach the level of secuirty that GNU/Linux provides. Of course Linux also no doubt has more developers working on its parts then Windows does I do believe.

---

### Post by Lensman on 2010-05-07
I have used Linux for a number of years now, but I can never resist the temptation of a new OS, so I tried Vista - mistake. Back to Linux. Win Se7en came out, so I had to have that too. I clean installed it three times and during all three times, the OS would drop the NIC after around 45 minutes, requiring a re-boot. Now, I gave Se7en three good tries and for me, it was unstable and difficult to use. As a result, Ubuntu 10.04 is in my PC and Win Se7en is in my bottom drawer.

Yesterday, I bought a new Brother laser printer and set it up. All I had to do was plug in the USB. Ubuntu correctly detected the printer model and configured the appropriate driver, no muss, no fuss. Wasn't that supposed to be a major selling point of Windows? ;)

---

### Post by Johnsie on 2010-05-07
I always take a review/comparison of Windows on a Linux forum with a pinch of salt.

This isn't really relevant but I have the best of both worlds:

[http://www.youtube.com/watch?v=4GwQ_btT6PE]("http://www.youtube.com/watch?v=4GwQ_btT6PE")

[IMG]http://steeky.com/john/images/ss2.png[/IMG]

---

### Post by fjf on 2010-05-07
I have 7 on a media htpc I use only for watching movies.  I LOOOVE when the damned OS pops up a window in the middle of a movie saying "new update installed, plase reboot now or remind me in 10 minutes". It is a true pain in the rear.

---

### Post by Johnsie on 2010-05-07
You can turn that off. It only happens if you've enabled 'automatic updates' in Windows ;-)

---

### Post by murderslastcrow on 2010-05-07
Hey Johnsie- seamless mode FTW! Unless you're a gamer or Premiere video-renderer, you don't really need to dual-boot if you've got sufficient RAM. Of course, some people figure "why make me use up all mah rAMzeZ??"

Still, dual-booting is cool. It actually provides some limited benefits you wouldn't get otherwise. Of course, it's nice to have everything you want working on Linux (with or without Wine) as it is, which I've been lucky enough to have.

I'd sooner buy a Mac than go back to Windows if I couldn't use Linux for a given period of time. Just because I know the security benefits, and any market share I take away from Microsoft is gonna' help Linux in the long run. If you can make it work on Windows and OS X, there's little reason you can't easily port it to Linux.

I think things will be split pretty evenly and critical applications (including games) will be available across all systems in about 10 years, at least on hardware bought from today forward.

---

### Post by Johnsie on 2010-05-07
If you're on a decent computer then running seamless mode doesn't really affect performance in any noticeable way. I'm running on a Phenom X3 with 3GB in work and I'm not noticing any performance issues at all. I need to try something a little more heavy duty like playing a 3d game to see if there are any rendering issues, but for what I use it for it's the perfect solution. Visual Studio, IE and MSN all work great. I wouldn't try doing this on a Pentium 4 though and I wouldn't even bother with the OSE of VirtualBox, the closed source version is much better.

---

### Post by Meep3D on 2010-05-07
On the subject of reboots, if a 3rd party piece of software or a 3rd party driver wants to reboot the system **[COLOR="DarkRed"]then it is the fault of that 3rd party software[/COLOR]**.  It is not the fault of Windows.  Windows will happily let you reinstall or change video (and other) drivers without a reboot, even if the video driver crashes Windows will just restart it - can Linux do any of these things?

> If you know others and know yourself, you will not be imperiled in a hundred battles; if you do not know others but know yourself, you win one and lose one; if you do not know others and do not know yourself, you will be imperiled in every single battle. - *Sun Tzu*

Here's a free piece of advice:  **Take Windows Seriously**.

Windows is used in around 90% of all desktop PC's and it's usage has not changed significantly in over a decade and the only impact that has been made on it has been by OSX.  Although many people seem to delude themselves into thinking there is a large Linux movement happening, there isn't.  Any non-biased look at the stats will show a Linux usage increase of around 50% over the last five years with average usage hovering around 1% for over a decade.

**If you do not understand why people use Windows you have failed.**

Sure, declare everyone that uses Windows an idiot, declare Linux fantastic and perfect, but if you do not understand why things are the way they are and are only concerned with pumping out propaganda and select 'facts' engineered to make your side look better then you are doing everyone a disservice.  No amount of argument or discussion will change any basic truths - arguing that rain is better than sun is possible, even easy, with there being no ability to ever come to a consensus (I mean sunlight gives you cancer) but no amount of clever words will change the basic facts that people like the sun.

If I was in a market where I had 1% and my competitor had 90% I'd take this problem seriously and investigate the root cause.  If I declared my competitor as crap and myself as the winner, despite utterly no gains in marketshare I'd be called an idiot, and rightfully so.

---

### Post by Meep3D on 2010-05-07
> **fjf said:**
> I have 7 on a media htpc I use only for watching movies.  I LOOOVE when the damned OS pops up a window in the middle of a movie saying "new update installed, plase reboot now or remind me in 10 minutes". It is a true pain in the rear.

If updates were optional (and they were) for you to update when you are ready then 90% of Windows users would never update.  What this does is basically forces people to do the updates who would under normal circumstances never do them.  If you don't like it turn it off, it's actually easy, as opposed to '[linux easy]("http://piestar.net/2010/04/14/easy-has-a-meaning-you-know/")'.

Microsoft gets bashed when machines don't ever get patched and form large botnets, now they get bashed for enforcing patching by default.  Make your damn mind up.

---

### Post by Half-Left on 2010-05-07
> **Meep3D said:**
> On the subject of reboots, if a 3rd party piece of software or a 3rd party driver wants to reboot the system **[COLOR="DarkRed"]then it is the fault of that 3rd party software[/COLOR]**.  It is not the fault of Windows.  Windows will happily let you reinstall or change video (and other) drivers without a reboot, even if the video driver crashes Windows will just restart it - can Linux do any of these things?



Here's a free piece of advice:  **Take Windows Seriously**.

Windows is used in around 90% of all desktop PC's and it's usage has not changed significantly in over a decade and the only impact that has been made on it has been by OSX.  Although many people seem to delude themselves into thinking there is a large Linux movement happening, there isn't.  Any non-biased look at the stats will show a Linux usage increase of around 50% over the last five years with average usage hovering around 1% for over a decade.

**If you do not understand why people use Windows you have failed.**

Sure, declare everyone that uses Windows an idiot, declare Linux fantastic and perfect, but if you do not understand why things are the way they are and are only concerned with pumping out propaganda and select 'facts' engineered to make your side look better then you are doing everyone a disservice.  No amount of argument or discussion will change any basic truths - arguing that rain is better than sun is possible, even easy, with there being no ability to ever come to a consensus (I mean sunlight gives you cancer) but no amount of clever words will change the basic facts that people like the sun.

If I was in a market where I had 1% and my competitor had 90% I'd take this problem seriously and investigate the root cause.  If I declared my competitor as crap and myself as the winner, despite utterly no gains in marketshare I'd be called an idiot, and rightfully so.

I don't know where you're getting this info but Windows software has always been low level. Windows own patches and updates require a reboot. OS X is actually worse for reboots, since Apple's own software requests a reboots just for updating iTunes or Quicktime.

1% share is an estimate and most people agree, there are more Linux users out there than this 1%. Windows has been sold to OEM for a long time and it's not got 89%(was 95%+ at once point) share based on being the best OS either, since the US government split Microsoft up over it's anti-competitive behaviour.

There is nothing to underestimate about Windows, it's Linux that is not to be underestimated. Microsoft is trying to do what it can to not let Linux get any traction in the desktop market. Netbook share has proven that Linux can be up there with Windows in a similar market.

---

### Post by Meep3D on 2010-05-07
> **Half-Left said:**
> I don't know where you're getting this info but Windows software has always been low level. Windows own patches and updates require a reboot. OS X is actually worse for reboots, since Apple's own software requests a reboots just for updating iTunes or Quicktime.
Five seconds on Google, that's all it took: [http://en.wikipedia.org/wiki/Windows_Display_Driver_Model](http://en.wikipedia.org/wiki/Windows_Display_Driver_Model) - namely the quote "WDDM also allows the graphic hardware to be reset or unplugged without a proper reboot. In practice, a driver update should not necessitate a reboot."

Even more amusingly Ubuntu always asks for a reboot after doing updates, despite the fact that everyone states it doesn't need to.
> 1% share is an estimate and most people agree, there are more Linux users out there than this 1%.
It's impossible to know the exact figure but this does not give you license to simply make stuff up.  Looking at trends is where I got the 50% over 5 years number, as even without any form of accuracy on actual usage, trends will give a good indication of the rate of adoption.  If you want to dispute me put up some numbers.
> Windows has been sold to OEM for a long time and it's not got 89%(was 95%+ at once point) share based on being the best OS either, since the US government split Microsoft up over it's anti-competitive behaviour.
Microsoft was split up?  Plus this is a decade old show-pony people love to trot out despite being entirely irrelevant to the discussion.  If Ubuntu had 90% of the market it would also be declared anticompetitive for all the reasons Windows is, price dumping, bundling etc.
> There is nothing to underestimate about Windows, it's Linux that is not to be underestimated. Microsoft is trying to do what it can to not let Linux get any traction in the desktop market. Netbook share has proven that Linux can be up there with Windows in a similar market.
Windows 7 beat Linux' marketshare *before it was even out of beta*.  All your talk of OEM's, anti competitiveness and bribery are irrelevant faced with the fact that despite being harder (apparently) to download, install and use it beat over a decade of Linux gains despite not being available on new hardware legally, let alone seriously marketed, especially compared to the relentless propaganda that is spewed *everywhere* by Linux advocates.  How did it manage this?

---

### Post by MarcusW on 2010-05-07
> **Meep3D said:**
> 
Even more amusingly Ubuntu always asks for a reboot after doing updates, despite the fact that everyone states it doesn't need to.


Lies. It only asks for a reboot when it's required, like a kernel update. 

Could you elaborate a bit on the "linux easy"? Is it being able to install software through the software center? Is it adding virtual desktops by simply right-clicking on the "workspaces" icon? Is it controlling your processor speed by adding an icon to the gnome-panel? (I could continue like this for a loong time)

Linux is hard for a windows power user. Windows is hard for a power linux user. Please try being a little less biased.

---

### Post by Bölvaður on 2010-05-07
I want to thank the OP for a good post.
I know exactly what you went through, I would have reacted exactly the same as you except in few instances... like I wouldnt scroll on the background to go to another workspace but rather ctrl+alt+&#8592;&#8594;

---

### Post by Meep3D on 2010-05-07
> **MarcusW said:**
> Lies. It only asks for a reboot when it's required, like a kernel update.
I neither know nor care why it wanted to reboot, only the fact that it did (and does) regularly require it is important.  Again crappy 3rd party Windows software asking for a reboot is not Microsoft's fault and if you tell it 'no' and carry on it'll be fine 99% of the time.

This whole 'reboot required' argument also proves my point exactly, nobody ever shuts up about how Windows requires a reboot, yet only very recently did Linux gain the ability to change the display resolution in X without restarting X itself (and losing all your running programs).  Yet not a peep out of anybody about this, and it was downplayed as 'not an issue' when it was not fixed despite being much more annoying than a monthly patch reboot.
> Could you elaborate a bit on the "linux easy"? Is it being able to install software through the software center? Is it adding virtual desktops by simply right-clicking on the "workspaces" icon? Is it controlling your processor speed by adding an icon to the gnome-panel? (I could continue like this for a loong time)
[http://en.wikipedia.org/wiki/Straw_man](http://en.wikipedia.org/wiki/Straw_man)

Pointing out things that work does nothing to combat the things that don't work.  Like NTFS-3G, which if a drive is marked as dirty requires you to access it with the CLI.  Or if you want to update your software to some that isn't in the repo's or if they are out of date, or when no build exists for your distro, or when your hardware doesn't work and requires CLI voodoo, or one of the many little occasions something goes wrong.
> Linux is hard for a windows power user. Windows is hard for a power linux user. Please try being a little less biased.
You are calling *me* biased.  My whole freaking point was that people act like Windows is utter crap and Linux is magical brilliance (see the first post in this thread) when in reality if you want a true picture of the situation you need to understand the true strengths and weaknesses of everyone involved.

I would never say that Linux was wrong or inferior to someone that actually uses it, only that for myself it isn't as good.  Yet the very fact that I don't use it is treated like a failing with me, rather than a failing with Linux.

As I said if you prefer the rain to the sunshine no amount of debunking me and 'proving me wrong' will make me prefer the rain as you do.  You either take the criticisms of people that don't use it seriously or you stop promoting it to them.

---

### Post by Johnsie on 2010-05-07
With regard to reboots. Both Ubuntu and Windows patches often require reboots... I've been using Ubuntu 10.04 for a week now and have already been asked by the OS to reboot my computers several times.

Generally when a major update is made to the kernel or other core system files then both operating systems will require a reboot. It's not some advantage that Ubuntu has over Windows.

At the end of the day, if you're burying your head in the sand and limiting yourself to just one operating system then you are missing out on some great software. Windows has some great apps and so does Ubuntu. Don't shoot yourself in the foot just because of your paranoia or blind 'loyalty' to one particular OS ;-)

Be sensible and enjoy the best of both worlds if you can :-) 


[IMG]http://steeky.com/john/images/ss2.png[/IMG]

---

### Post by RiceMonster on 2010-05-07
> **MarcusW said:**
> Lies. It only asks for a reboot when it's required, like a kernel update. 

On a lot of distros, driver and service updates ask for reboots too. I admitadly can't speak specifically for Ubuntu, however, because I habven't used it in a while.

> **Half-Left said:**
> There is nothing to underestimate about Windows, it's Linux that is not to be underestimated. Microsoft is trying to do what it can to not let Linux get any traction in the desktop market. Netbook share has proven that Linux can be up there with Windows in a similar market.

In terms of desktops, I HIGHLY doubt Microsoft even cares about Linux. They're more concerned about OSX, which actually poses some level of threat. People just like to think of Microsoft as "the man keeping them down" so they have something to blaim, rather than looking at actual problems with Linux.

---

### Post by Meep3D on 2010-05-07
> **Johnsie said:**
> With regard to reboots. Both Ubuntu and Windows patches often require reboots... I've been using Ubuntu 10.04 for a week now and have already been asked by the OS to reboot my computers several times.

Generally when a major update is made to the kernel or other core system files then both operating systems will require a reboot. It's not some advantage that Ubuntu has over Windows.

At the end of the day, if you're burying your head in the sand and limiting yourself to just one operating system then you are missing out on some great software. Windows has some great apps and so does Ubuntu. Don't shoot yourself in the foot just because of your paranoia or blind 'loyalty' to one particular OS ;-)

Be sensible and enjoy the best of both worlds if you can :-) 

Exactly.  Use whatever is best and understand that it is a tool and nothing more.

I develop web apps for LAMP, but create them on a Mac and test them internally on a Windows box before deployment to CentOS.  It just annoys me the 'we don't care about your needs, requirements or preferences, Linux is better Windows sucks, BSOD lol attitude'.  It's counterproductive and provides an unrealistic impression of the capabilities of Linux which often leads to disappointment.

---

### Post by Half-Left on 2010-05-07
> **Meep3D said:**
> Five seconds on Google, that's all it took: [http://en.wikipedia.org/wiki/Windows_Display_Driver_Model](http://en.wikipedia.org/wiki/Windows_Display_Driver_Model) - namely the quote "WDDM also allows the graphic hardware to be reset or unplugged without a proper reboot. In practice, a driver update should not necessitate a reboot."

Even more amusingly Ubuntu always asks for a reboot after doing updates, despite the fact that everyone states it doesn't need to.

It's impossible to know the exact figure but this does not give you license to simply make stuff up.  Looking at trends is where I got the 50% over 5 years number, as even without any form of accuracy on actual usage, trends will give a good indication of the rate of adoption.  If you want to dispute me put up some numbers.

Microsoft was split up?  Plus this is a decade old show-pony people love to trot out despite being entirely irrelevant to the discussion.  If Ubuntu had 90% of the market it would also be declared anticompetitive for all the reasons Windows is, price dumping, bundling etc.

Windows 7 beat Linux' marketshare *before it was even out of beta*.  All your talk of OEM's, anti competitiveness and bribery are irrelevant faced with the fact that despite being harder (apparently) to download, install and use it beat over a decade of Linux gains despite not being available on new hardware legally, let alone seriously marketed, especially compared to the relentless propaganda that is spewed *everywhere* by Linux advocates.  How did it manage this?

I see you have fallen into the same BS people say about any monopoly. If Ubuntu/Linux had a 90% share it wouldn't be classed as anti-competitive, you're just lead to believe that unless they actually did something anti-competitive to gain market share. As you know, Ubuntu/Linux doesn't have any lock-in software to gain share, unlike Microsoft have. You can uninstall all software and install any piece of software of your choice.

Microsoft 'was' split up by the Clinton government for their anti-competitive behaviour and why you have the defaults application Windows 2000 Sp3 and all Windows versions after it.   

So what? Linux never has needed a reboot for driver updates, the fact that Ubuntu does it is irrelevant because other distros just require a re-login. As for reboots, only a kernel update requires one, no security updates do, unlike Windows.

Windows is fighting Windows in the desktop market, nobody else yet. Apple doesn't sell computers in this OEM market either, so it's just Windows. Until Linux gets traction with OEMs, Microsoft will remain a monopoly. I should tell you that Windows primary market share is with the OEM, not with selling Windows off the shelf's and Microsoft have that locked in until whatever Linux company can get some real OEM support.

---

### Post by 98cwitr on 2010-05-07
while ( user == frustrated ) {
                   continue;
                   frustration++;
      }

Found the code for that while loop...well back to Hell, glad you're enjoying your torment.

---

### Post by Meep3D on 2010-05-07
> **Half-Left said:**
> I see you have fallen into the same BS people say about any monopoly. If Ubuntu/Linux had a 90% share it wouldn't be classed as anti-competitive, you're just lead to believe that unless they actually did something anti-competitive to gain market share. As you know, Ubuntu/Linux doesn't have any lock-in software to gain share, unlike Microsoft have. You can uninstall all software and install any piece of software of your choice.
Using your monopoly marketshare in one market (operating systems) and using that to gain marketshare in another market is what is not allowed.  Ubuntu One, the Ubuntu Music Store and Software Centre all fall foul of this.
> Microsoft 'was' split up by the Clinton government for their anti-competitive behaviour and why you have the defaults application Windows 2000 Sp3 and all Windows versions after it.
What on earth are you talking about?  This is not what is meant by 'split up'
> So what? Linux never has needed a reboot for driver updates, the fact that Ubuntu does it is irrelevant because other distros just require a re-login. As for reboots, only a kernel update requires one, no security updates do, unlike Windows.
Again with the no idea what you are talking about.  Do some research on the words 'Monolithic Kernel' and the implications thereof then come back.  Seriously.
> Windows is fighting Windows in the desktop market, nobody else yet. Apple doesn't sell computers in this OEM market either, so it's just Windows. Until Linux gets traction with OEMs, Microsoft will remain a monopoly. I should tell you that Windows primary market share is with the OEM, not with selling Windows off the shelf's and Microsoft have that locked in until whatever Linux company can get some real OEM support.
Why don't you start an OEM selling Linux based PC's?  It's a free market after all and that is the whole point of a free market.  You obviously see a gap, and could no doubt cut costs significantly by not paying Windows licenses, so why don't you do it?  Why does nobody else do it?  Are you worried that Bill Gates will come round and break your legs?

---

### Post by RiceMonster on 2010-05-07
> **Half-Left said:**
> So what? Linux never has needed a reboot for driver updates, the fact that Ubuntu does it is irrelevant because other distros just require a re-login. As for reboots, only a kernel update requires one, no security updates do, unlike Windows.

Ok, let's say my nVidia driver is updated. Explain to me how I can load in the new kernel module by logging in and out. Or, let's say networkmanager gets updated. How do I restart the daemon by logging in and out?

---

### Post by Half-Left on 2010-05-07
I'm not going to argue with you Meep3D because that last post was so wrong it's not even funny.

Go find out more about what happened in the 90's with Microsoft. Part of Microsoft was split up for being anti-competitive and Bill Gates was grilled about it all and the whole IE/Windows Media Player mess.

Ubuntu itself might require extra reboots but other distros do not and never have done. If you install the NVIDIA proprietary drive in OpenSUSE, you just need to logout and in again for it to be activated. The fact that Ubuntu does it is their system and doesn't reflect other Linux distros.

---

### Post by Half-Left on 2010-05-07
> **RiceMonster said:**
> Ok, let's say my nVidia driver is updated. Explain to me how I can load in the new kernel module by logging in and out. Or, let's say networkmanager gets updated. How do I restart the daemon by logging in and out?

XOrg does it and has done for years now. Try a manual install and you'll see it doesn't require a reboot because the module is unloaded and reloaded like kernel modules can be.

All you need to do it let XOrg restart and it reloads the NVIDIA kernel module. Also note that in the extra settings when updating the software, such services get restarted.

---

### Post by RiceMonster on 2010-05-07
> **Half-Left said:**
> XOrg does it and has done for years now. Try a manual install and you'll see it doesn't require a reboot because the module is unloaded and reloaded like kernel modules can be.

All you need to do it let XOrg restart and it reloads the NVIDIA kernel module.

Well of course, I can manually load in the new kernel module or restart a daemon, but are inexperienced users going to know how to do that? No. So what's the update manager going to tell them to do? That's right, reboot.

---

### Post by blueturtl on 2010-05-07
Guys, mind the poor OP's thread. It is a user review posting. Just as valid as any user review ever is. Why turn it into a battle field?

> Ok, let's say my nVidia driver is updated. Explain to me how I can load in the new kernel module by logging in and out. Or, let's say networkmanager gets updated. How do I restart the daemon by logging in and out?

Why pick the guy apart for poor phrasing? Is this the famous Ubuntu spirit?

He made point about design modularity. Compiling or installing new modules does not infact require rebooting (in Linux). What you need to do is unload the old modules first, and then load the newly installed modules in place. Since this happens automatically on reboot, new users are being guided to do it that way. It's not necessary though.

In the olden times, what you would do after installing the new nVidia driver would be to hit Ctrl+Alt+Backspace effectively logging out and restarting X. X would then load with the new display driver. This has the benefit of keeping any background daemons and services running.

---

### Post by RiceMonster on 2010-05-07
> **blueturtl said:**
> Guys, mind the poor guy's thread. It is a user review posting. Just as valid as any user review ever is. Why turn it into a battle field?



Why pick the guy apart for poor phrasing? Is this the famous Ubuntu spirit?

The guy made point about design modularity. Compiling or installing new modules does not infact require rebooting (in Linux). What you need to do is unload the old modules first, and then load the newly installed modules in place. Since this happens automatically on reboot, new users are being guided to do it that way. It's not necessary though.

In the olden times, what you would do after installing the new nVidia driver would be to hit Ctrl+Alt+Backspace effectively logging out and restarting X. X would then load with the new display driver. This has the benefit of keeping any background daemons and services running.

See above. I know you don't *have* to reboot, but "user friendly" distros are obviously going to ask for a reboot because new users don't know how to unload and load a kernel module.

---

### Post by Half-Left on 2010-05-07
> **blueturtl said:**
> The guy made point about design modularity. Compiling or installing new modules does not infact require rebooting (in Linux). What you need to do is unload the old modules first, and then load the newly installed modules in place. Since this happens automatically on reboot, new users are being guided to do it that way. It's not necessary though.

In the olden times, what you would do after installing the new nVidia driver would be to hit Ctrl+Alt+Backspace effectively logging out and restarting X. X would then load with the new display driver. This has the benefit of keeping any background daemons and services running.

Correct.

---

### Post by Half-Left on 2010-05-07
> **RiceMonster said:**
> See above. I know you don't *have* to reboot, but "user friendly" distros are obviously going to ask for a reboot because new users don't know how to unload and load a kernel module.

As I've said. Never did I ever have to reboot to install the NVIDIA driver. In OpenSUSE all you do is just add the NVIDIA repos and install the driver and then logout, login and the driver is working, full 3D. Ubuntu does it their way, for whatever reason but the simple fact is, you don't need to reboot.

---

### Post by uRock on 2010-05-07
> **Half-Left said:**
> As I've said. Never did I ever have to reboot to install the NVIDIA driver. In OpenSUSE all you do is just add the NVIDIA repos and install the driver and then logout, login and the driver is working, full 3D. Ubuntu does it their way, for whatever reason but the simple fact is, you don't need to reboot.
Windows 7 has made me reboot with every nVidia driver change, but unlike Lucid every time I reboot the driver doesn't revert to Nouveou in Windows.

---

### Post by Half-Left on 2010-05-07
> **uRock said:**
> Windows 7 has made me reboot with every nVidia driver change, but unlike Lucid every time I reboot the driver doesn't revert to Nouveou in Windows.

Yes. In fact if you do the driver install the proper way in Windows, you have to reboot twice.

Once you have uninstalled the NVIDIA drive in Windows, then reboot and let it detect your card, you have to reboot again, since Windows installs it's own set of drivers. Uninstalling old drivers first is recommended in Windows.

In Linux it's just a case of reloading the model and then Xorg starts. It maybe that Ubuntu uses the Nouveau driver differently or some conflict there but that's just a guess.

---

### Post by Calmor on 2010-05-07
I know the thread has deviated some from the original post, but I also tried out Windows 7 after a long period of Ubuntu use.  I do use Windows XP at work, and on a VirtualBox for some things that absolutely require Windows (Quicken, mainly), but I'd gone a year or two on Linux for my personal computing needs.

Like many Linux enthusiasts, I went through the standard cycle - thinking this is the best thing ever, talking about it as if it was the best thing ever, convincing a few people to try it, recognizing it does have its own issues and limitations, stop preaching and start being realistic in discussions with others, and finally just using it and being happy to discuss if people ask about computers or what I'm running.

When it was all said and done, I came to the realization that while Linux is a great fit for me, it's not for everyone.  My girlfriend runs it, but we keep a Windows PC at the house to run Office 2007, since it doesn't work well under Wine, and she needs to collaborate with people at her school that run Office 2007.  (OOo's compatibility is nowhere near good enough for complex documents with multiple tables, etc.)  My girlfriend's mom rather prefers its stability and security, but can't often run it because her husband uses a music service that doesn't have a Linux client, and also does his taxes and finances (no TurboTax for Linux).  She has a Zune too.  None of those things can I control.

As an experiment, I was able to pick up a free, legal copy of Windows 7 and all the fixins other than the core Office 2007, which I got on the student discount on The Ultimate Steal.  So, cost not being an issue, I tried it out for a semester, and avoided Linux use where possible.  (My TV/Print/Web/File server is a Mythbuntu machine, so that wasn't entirely feasible)

(note that this is my list, everyone has their own opinion)

The Pros:

[LIST]
[*]Installed over top of the Vista partition without killing my Linux partition (did have to re-do Grub, though)
[*]OneNote has no replacement in the Linux world for school notetaking.  I've tried a lot of them.  There's just nothing close.
[*]Not having to boot a VM to do my bills (again, no replacements for Quicken that I've seen, with online account updating) or Windows development when required.
[*]System was surprisingly stable and less of a resource hog than Vista, for sure.
[*]Say what you will of Aero, but the new gestures (snap to half-screen, snap to maximize/unmaximize) are actually useful for me.  Compiz generally just adds eye candy, not functionality in my experience.  I understand the latest KDE has this same Aero-style functionality.
[*]Office is about as compatible with Office (and the rest of the world) as it gets, though there are some incompatibilities with older versions.
[*]The start menu search function.  I thought it was a gimmick until I started using it.  I don't think I ever looked through my start menu after that.  I might give Gnome Do a try as a result.
[/LIST]

The Cons:

[LIST]
[*]Freedom.  I'll run non-open versions of software when there is an advantage (I use VirtualBox with USB support since I require that functionality.)  However, I try to stick with FOSS whenever possible.  Even in Windows, I ran open-source where available.
[*]Multiple desktops.  I know there are add-on programs, but I missed being able to switch natively.  Some people find this a hindrance, I tend to organize tasks based on desktop.
[*]Ability to modify anything and everything to match my requirements/demands.
[*]ls.  Windows Powershell actually recognizes ls, but the normal command line only recognizes dir.  I like to work in the command line for some tasks (from my MS-DOS 4.11 days)
[*]Everything requires a download.  I'd been spoiled in my Linux installs since they come with everything.  PDF viewer?  Office software?  Mail client?  Image editor?  Photo organizer?  Text editor that doesn't suck?  Sorry, go find your own.
[*]64-bit hang-ups.  Windows 7 64-bit had some things that were just plain not supported, that were oddly supported in Linux x64.  Like my Microchip ICD2 (programmer module).  Even though drivers are actively developed by the company, I couldn't get it to work.  I was able later to get the device to work in Linux x64.
[*]Printing!  Since I'm including the whole user experience with software in some of the pros or cons, I have to add this one in.  The Windows drivers for my particular HP printer refuse to allow network printing, even if it were installed on another Windows machine.  Linux drivers have no such restriction.  I had to print by printing to PDF (another add-on, by the way), SCP the PDF to the Linux server, then running an lp command at the SSH terminal.
[/LIST]

All in all, though I found Windows 7 robust, relatively secure, and perfectly usable for most people and situations.  I still prefer Linux, personally.  I don't think 7 is the worst thing out there, and both systems, realistically, have their flaws.  As a wise man once said here, they're both tools - use which one works best for you.

---

### Post by Half-Left on 2010-05-07
Sorry for being slightly off topic.

Personally, I don't see the big deal with Windows 7, it offered me nothing over any other version(DX versions you could say but it's build-in to Windows anyway). I just use it for games I cannot play in Linux, nothing more.

I didn't buy Windows 7 because I have friends who got me the OEM version, otherwise I just won't bother using Windows at all.

---

### Post by Calmor on 2010-05-07
> Sorry for being slightly off topic.

Not my thread, but I felt compelled to give my own personal experience.  The discussions about drivers were interesting, and I'd forgot to mention how much I HATED rebooting my machine 1000 times.  Every update meant I had to reboot my machine, usually twice.  Nothing was more irritating than when Windows would subtly add the "install updates and shut down" option to your laptop, and not noticing, you try to shut it down, only to have it take forever.  My battery only lasts 20 minutes these days, so it effectively kept me from going anywhere.  Then the next reboot, it installs more and has to reboot again?  Why?

> Personally, I don't see the big deal with Windows 7, it offered me nothing over any other version(DX versions you could say but it's build-in to Windows anyway). I just use it for games I cannot play in Linux, nothing more.

Whether it's games or Quicken, software is part of the whole reason we use computers (not just the OS and its features).  Linux is for most of those on this forum (that's why we're here, right?), but not for everyone.  I agree with not seeing the big deal about Windows 7.  There were some nice things, like I mentioned the Aero improvements to the UI, but nothing earth-shattering.  While a lot of the back-end code may have changed, to the user it's just a prettier XP with a couple of nice tweaks.  My point was that it is perfectly usable, and for those who subscribe to the MS way of life and how things should be done, it's worth moving to *with your next computer purchase* since it's way too expensive outright.

> I didn't buy Windows 7 because I have friends who got me the OEM version, otherwise I just won't bother using Windows at all.

I'm "lucky" enough to be in a school partnered with Microsoft's Developers Network, so I get a copy gratis, but I surely pay for it in tuition.  I figured I should at least give it a go.  I have a virtualized Server 2003 machine as well for web development and server maintenance self-education for MS systems.  I still prefer the Linux server method better, but it's more marketable to know both sides of the house, at least to some degree.

---

### Post by m4tic on 2010-05-07
> **Tristam Green said:**
> I like how the one guy who actually rebuffs the erroneous or fallacious claims gets automatically labeled a troll.

Stay classy, Café.

My Ubuntu 9.10 did not have a .rar unpacker, did i make a post of it? Nope, this thread's only points are the program restart annoyances, and even those are not created by the OS but the program's recommendations. Ubuntu works well most of you know it but this vs thing is really old now, most Windows users don't know linux  and its obvious where this topic usually starts from. The ubuntu forums start boring me where when someone points anything positive about Windows gets labled, it feels like this is a cult, is it?

---

### Post by sydbat on 2010-05-07
> **m4tic said:**
> **it feels like this is a cult, is it?**Yes. And now that you know, we have to reprogram you...):P

---

### Post by 3Miro on 2010-05-07
A lot of posts and a lot of comments. I will try to address as many as possible in a single post, hopefully it will not be confusing.

On the entire reboot issue: my problem doesn't come just from rebooting. I can live with that, as long as it is done in a way that is convenient for me. Even when I boot from a Linux live CD and then check my mail while the system is installing, I will be prompted politely to reboot at my convenience. In Windows, I got the Motherboard driver CD, from a brand new MB, with a big shiny "Windows 7 Certified" logo and that rebooted the machine without even giving me the old annoying XP message: "System will reboot in 10 minutes, please save all your work." Furthermore, while I can live with kernel updates and drivers requiring a reboot, why does Adobe Reader need one?

Consider the argument: "Windows is great because I can play games and do my taxes. Furthermore, this guy, who complains about Adobe rebooting is a troll, because you cannot blame MS for Adobe's bad code." It should be clear to everyone, how inconsistent this is. You cannot include facts that are convenient and ignore facts that don't suit you. If MS is to take credit for Windows apps, then it is only fair to also take the blame.

Not too long ago, I read an article where an MS representative said how people "Choose Windows 90% of the time." I really disagree with the use of the term "choice". One makes a choice, only when he/she is aware of all the options (and the consequences). Of the vast army of MS users, the overwhelming majority has never even heard of Linux (at most the more expensive Mac). Most of those people, also have low level of computer skills, they just one someone experienced to install and set up the system for them, so they can use it for usually simple asks. The Windows users that are aware of Linux and would come to this forum are far more often powerusers. It is only natural to expect that a poweruser will have a hard time adjusting to a new and different system; to the average "windows Joe" one OS will look just like another and at the end, all that he needs to know is where to click to check mail and use eBay. I have personally installed Linux on several computers of people with somewhat low tech-skills and once I have the system properly set up for them, they love it. I was a Windows 95-XP user for years and I never had security issues or trouble finding proper software, but I was also a poweruser; most people don't have the advantage of my education, so having a trusted repository is a great thing.

When I studies computer science, most of my teachers were Linux fans, but I was making deliberate efforts to learn as much about Windows as I can. I did this, simply because I did not want to limit myself to only one system. Now, having my career in computational science, I have no need for Windows. While 90% of the home PC computers are Windows based, the realm of supercomputers and servers is ruled by Tux (with only a few other *nix systems making a competition). When it comes to professional level of Speed, Security and Stability, MS is just out of the game.

To make a fair comparison of Windows vs Linux, we should consider those in a "raw" form, without 3rd party apps. In the OSS world, any distro is allowed to adopt any software that they want. Windows comes with IE and WMP. You can add MS Office to the mix if you like, even though it is sold as a separate product, but please don't bash Open Office for not being fully compatible with MSO. MS Office comes for Windows and Mac and complicated graphics, math formulas and Power Point cannot be shared between those two. Even Microsoft is incapable of making software compatible with their own software. To take a more technical view, at the level of the OS, right from the start, 32-bit Windows 7 easily hogs 600MB of RAM (which is a big improvement over Vista). I use mostly 64-bit XUbuntu that does net, char and mail with under 500MB. Then comes the app and HDD cache, Linux doesn't waste RAM, Windows is more than happy to do so.

I don't think anyone can make an objective argument of Windows being better than Linux in any conceivable way. The best argument that one can make, is that due to the many Windows apps, Windows is an useful OS. While this is a valid reason to use Windows, it is also a very unfortunate one. When a technical product establishes a near full monopoly, not due to their engineers, but entirely due to their PR and legal departments, that is when we need antitrust laws to kick in. Ironically, it is Unix that was held back by such laws for many years and without antitrust we would have never seen pre-Unix Mac or MS-DOS (we might have had MS-Unix though).

---

### Post by lashram on 2010-05-07
**I have Windows 7 on my Lenovo laptop it actually came with the full install disk of Windows 7 professional and windows XP pre-installed. I have Ubuntu 10.04 installed on a custom laptop that i built a few months ago. I am using Ubuntu as my main and only operating system on this machine. I let my kids use the Lenovo for there schoolwork,movies etc. Now what made me switch from Windows is Microsoft Security Essentials invalidated all of my windows machines licenses as invalid now I was able to reinstall and all is well now but I will never install MSE again and I probably will not use Windows on my personal laptop anymore because of this experience. Microsoft is so concerned about piracy that they often hurt innocent consumers who overpaid for their product in the first place me being one of those consumers. But I have found through my years of experimenting and using Ubuntu that i can do everything that i did on my Windows system with Linux. Ubuntu has come a long way and i feel it is progressing nicely. I also like the freedom to customize my system the way I want it and being able to choose what programs to use and also being able to help improve those programs if I am able to. My custom laptop came with an Nvidia chipset and Nvidia graphics I have not had any issues with it under Lucid up to this point and with WineI am still able to play my games and enjoy the same experience that I had playing them with Windows. I am not bashing Microsoft but mainly praising and showing appreciation for Ubuntu and the open source community versus being tied on a leash with a short chain by certain $$$ hungry propriatory corporate entities. :guitar:  Rock on Mates !!**

---

### Post by sXeChris on 2010-05-07
Ha, you gotta love Ubuntu. Great story, BTW.

---

### Post by uRock on 2010-05-07
> **lashram said:**
> I have Windows 7 on my Lenovo laptop it actually came with the full install disk of Windows 7 professional and windows XP pre-installed. I have Ubuntu 10.04 installed on a custom laptop that i built a few months ago. I am using Ubuntu as my main and only operating system on this machine. I let my kids use the Lenovo for there schoolwork,movies etc. 

Now what made me switch from Windows is Microsoft Security Essentials invalidated all of my windows machines licenses as invalid now I was able to reinstall and all is well now but I will never install MSE again and I probably will not use Windows on my personal laptop anymore because of this experience. 

Microsoft is so concerned about piracy that they often hurt innocent consumers who overpaid for their product in the first place me being one of those consumers. But I have found through my years of experimenting and using Ubuntu that i can do everything that i did on my Windows system with Linux. Ubuntu has come a long way and i feel it is progressing nicely. 

I also like the freedom to customize my system the way I want it and being able to choose what programs to use and also being able to help improve those programs if I am able to. My custom laptop came with an Nvidia chipset and Nvidia graphics I have not had any issues with it under Lucid up to this point and with Wine I am still able to play my games and enjoy the same experience that I had playing them with Windows. 

I am not bashing Microsoft but mainly praising and showing appreciation for Ubuntu and the open source community versus being tied on a leash with a short chain by certain $$$ hungry propriatory corporate entities**. :guitar:  Rock on Mates !!**
Isn't that much easier to read. No disrespect meant.

I agree with what your point of view.

---

### Post by Calmor on 2010-05-07
3Miro - I generally agree with you, except for a few minor points:

> To make a fair comparison of Windows vs Linux, we should consider those in a "raw" form, without 3rd party apps.

I agree that in a strict Windows vs. Linux comparison, they need to be considered in a raw form, and in most (but not all) cases, Linux wins hands down (for me).  

However, for a "real world" comparison, the true measure of any computer is what you can do with it.  If I can't do my taxes or play a game I desire to play on Linux, then a Linux PC isn't for me.  It's not Linux's fault so to speak, but by nature of its low adoption rate, third-party vendors don't see any reason to port software over.  I won't argue your points about monopoly and reasons for the adoption rate - I agree with you.  But, if you're a third party vendor like Intuit, Quicken's maker, what financial motivation do you have to port your product?  Even going to Mac should be questioned for profitability reasons.

Therefore, when I compare the two, I have to look at the apps as well.  The downside is that everything that's popular or good and also open source is generally ported to Windows as well, so there's no "killer app" for Linux (again, for me).  I prefer its stability, its "modifyability," and the challenge and experience I get from using it.

> but please don't bash Open Office for not being fully compatible with MSO. MS Office comes for Windows and Mac and complicated graphics, math formulas and Power Point cannot be shared between those two. Even Microsoft is incapable of making software compatible with their own software.

I only bash OOo for not being fully compatible with MSO because in Sun's installers for Java on Windows platforms, it boldly advertises OpenOffice as a free office product that is compatible with Microsoft Office.  I can't blame them for not being 100% compatible to a closed standard that's been reverse engineered.  I blame them for not promoting that there can be (and are) significant challenges when sharing files with MSO users.  In the latest release of OOo, if I format a table's dimensions directly in the dialog window in Writer, save it as a Word doc, and open it again in OOo (never touching MSO), the table is shifted so far right, I can't see it exists.  That's its own output that it can't read.  How could Word read it?  Their website also promotes that it can sometimes open corrupted files that MSO can't.  True - and I've seen it myself, it's saved me a few times.  They would have more fans (and adopters) if - they advertised more... and - they advertised that there is no guarantee of 100% compatibility due to MSO's closed standard.

I personally bash all office products for not being compatible.  MSO 2003 w/ 2007 compatibility pack doesn't render things the same way 2007 does.  That's sad, but another topic all together.  

I like some of what Office 2007 is doing, and some of OOo's functionality.  I well prefer the OOo formula writer over MS Office's.

Some day I'll just learn LaTeX and be done with all this compatibility stuff.

---

### Post by uRock on 2010-05-07
I blame MSO for not being compatible with OpenOffice. For the money people pay for MSO, they should be able to open the open source formats as well as the paid ones.

---

### Post by RiceMonster on 2010-05-07
> **uRock said:**
> I blame MSO for not being compatible with OpenOffice. For the money people pay for MSO, they should be able to open the open source formats as well as the paid ones.

Office 2007 and 2010 can open odf formats.

---

### Post by Calmor on 2010-05-07
> **RiceMonster said:**
> Office 2007 and 2010 can open odf formats.

With Sun's plugin, Office 2007 can, but not natively to the best of my knowledge.

I tend to agree though.  ODF is a standard.  MSO should support it.  (So is OOXML, but only because we can bribe the standards committee.)

---

### Post by djsroknrol on 2010-05-07
Thanks for all the reminders "why" I went to Linux in the first place =D>=D>

---

### Post by lashram on 2010-05-07
> **uRock said:**
> Isn't that much easier to read. No disrespect meant.
 
I agree with what your point of view.
 
 
Oh sorry about the bold print actually I cant see that well so for me the bold print looks better. Thanks I did not take it as being disrepectful at all.;)

---

### Post by Johnsie on 2010-05-07
I get this quite regularly. I also had to log off and on again just to change my display driver. Sometimes I've actually had to manually modify xorg.conf just to get a display to work  properly. 

[IMG]http://steeky.com/john/images/reboot.png[/IMG]

---

### Post by hatebreed on 2010-05-07
I'll admit that Ubuntu is very nice, the best linux i've tried to date. As a matter of fact its the only one that would detect all my hardware automatically. Linux has come along ways since I started trying it back in 98. The installers had improved drastically and the hardware detection is very good these days. I still use windows for games but I foresee a day when we can choose between a linux version and a windows one. Now we need to get this silverlite figured out so I can use my netflix without any hitches. Keep up the good work Ubuntu, you guys rock!!!

---

### Post by hatebreed on 2010-05-07
I agree the display drivers are pretty quirky. I had a hell of a time getting the new nvidia driver to work right. I had to manually add display modes to be able to adjust resolution. That is unacceptable these days, Nvidia what gives.

---

### Post by Ugluk on 2010-05-08
> to a closed standard that's been reverse engineered
The Word, Excel, PowerPoint and OneNote binary formats has been documented (since their Office 97 versions) for several years already. So any incompatibilities come from incompetence of implementors.

---

### Post by del_diablo on 2010-05-08
> **hatebreed said:**
> Nvidia what gives.

SUPPORT XRANDR ALREADY! That is what gives :P

---

### Post by 3Miro on 2010-05-08
> **Ugluk said:**
> The Word, Excel, PowerPoint and OneNote binary formats has been documented (since their Office 97 versions) for several years already. So any incompatibilities come from incompetence of implementors.

Check out my comment on the MS Office incompatibilities between the OSX and Windows versions. If MS can't/won't create a piece of MS compatible software, how is it fair to go after Open Office. In general MS is notorious about failing to document key aspects of their system (check out how the wine people are doing their job).

---

### Post by 3Miro on 2010-05-08
> **hatebreed said:**
> I agree the display drivers are pretty quirky. I had a hell of a time getting the new nvidia driver to work right. I had to manually add display modes to be able to adjust resolution. That is unacceptable these days, Nvidia what gives.

Yes this happens sometimes. However, it is interesting to note that display drivers are one of the very few proprietary aspects of Ubuntu and as such are totally outside of the control of the community.

---

### Post by 3Miro on 2010-05-08
> **Johnsie said:**
> I get this quite regularly. I also had to log off and on again just to change my display driver. Sometimes I've actually had to manually modify xorg.conf just to get a display to work  properly. 


I have seen systems where you can hot-swap CPU and RAM without the need to reboot or even turn the system off, however, for the PC hardware this is not possible. Ubuntu is a more "rebooty" distro then most, but having to reboot every now and then is hardly an issue. For the first few weeks of a new release, many glitches are polished and naturally one will see many updates. Ultimately, Ubuntu reboots for kernel and driver updates. And Linux never reboots without asking for permission.

On Windows, even simple software constantly asks you to reboot. And then it comes to kernel and drivers, the ones that really need a reboot, Windows doesn't even care to ask.

---

### Post by MarcusW on 2010-05-08
> **Meep3D said:**
> I neither know nor care why it wanted to reboot, only the fact that it did (and does) regularly require it is important.  Again crappy 3rd party Windows software asking for a reboot is not Microsoft's fault and if you tell it 'no' and carry on it'll be fine 99% of the time.

This whole 'reboot required' argument also proves my point exactly, nobody ever shuts up about how Windows requires a reboot, yet only very recently did Linux gain the ability to change the display resolution in X without restarting X itself (and losing all your running programs).  Yet not a peep out of anybody about this, and it was downplayed as 'not an issue' when it was not fixed despite being much more annoying than a monthly patch reboot.

[http://en.wikipedia.org/wiki/Straw_man](http://en.wikipedia.org/wiki/Straw_man)

Pointing out things that work does nothing to combat the things that don't work.  Like NTFS-3G, which if a drive is marked as dirty requires you to access it with the CLI.  Or if you want to update your software to some that isn't in the repo's or if they are out of date, or when no build exists for your distro, or when your hardware doesn't work and requires CLI voodoo, or one of the many little occasions something goes wrong.

You are calling *me* biased.  My whole freaking point was that people act like Windows is utter crap and Linux is magical brilliance (see the first post in this thread) when in reality if you want a true picture of the situation you need to understand the true strengths and weaknesses of everyone involved.

I would never say that Linux was wrong or inferior to someone that actually uses it, only that for myself it isn't as good.  Yet the very fact that I don't use it is treated like a failing with me, rather than a failing with Linux.

As I said if you prefer the rain to the sunshine no amount of debunking me and 'proving me wrong' will make me prefer the rain as you do.  You either take the criticisms of people that don't use it seriously or you stop promoting it to them.

Sorry for the late response.

CLI != hard. I'm not saying everything that's easy in windows is easy in Linux. Some things are really hard. Just like some things that are easy in Linux are hard in Windows.

I like using the terminal, and I can solve problems easily with it. I've been using Linux for about a year and a half. I had been using windows much longer when I used it, and things like regedit and the more advanced administration tools still was a bit too complicated for me to really use.

EDIT:
FYI my debian desktop has been running for 31 days now, updating every day and it hasn't asked me to reboot.

---

### Post by sdowney717 on 2010-05-08
A major gripe for me are uninstall programs that require the original install CD to uninstall. Norton security essentials I think had done that. Only way to get rid of it on the Dell was to reformat the drive. And it had come with the Dell package software from Dell. 
minor gripes is Windows constantly having to reboot and malware worries, having to run and update the programs. Best one was Avast.

---

### Post by Calmor on 2010-05-08
> **3Miro said:**
> Check out my comment on the MS Office incompatibilities between the OSX and Windows versions. If MS can't/won't create a piece of MS compatible software, how is it fair to go after Open Office. In general MS is notorious about failing to document key aspects of their system (check out how the wine people are doing their job).

I agree completely and have never understood why MS can't make their products compatible with each other.  It drives me insane.

However, if you're a student working for a grade, or a consultant or freelancer writing a document for a client, and both must be in Word format, do you use OOo or find an MSO installation somewhere?  I personally would choose the latter (and use .doc not .docx), if only because I find MSO about 98% compatible with other MSO versions, whereas OOo is (and I'm estimating) about 80% compatible.  If my grade or job is on the line, I'm not taking that chance.

---

### Post by blueturtl on 2010-05-08
> **Ugluk said:**
> The Word, Excel, PowerPoint and OneNote binary formats has been documented (since their Office 97 versions) for several years already. So any incompatibilities come from incompetence of implementors.

I would love to get a reference for this as I was under the impression that the Office formats (prior to .docx) were closed and therefore required reverse-engineering to get working.

If what you say is true, then problems with the formats can't be attributed to Microsoft alone.

---

### Post by Ugluk on 2010-05-08
[http://msdn.microsoft.com/en-us/library/cc313118(v=office.12).aspx](http://msdn.microsoft.com/en-us/library/cc313118(v=office.12).aspx)

---

### Post by sydbat on 2010-05-08
> **Ugluk said:**
> [http://msdn.microsoft.com/en-us/library/cc313118(v=office.12).aspx](http://msdn.microsoft.com/en-us/library/cc313118(v=office.12).aspx)All that link talks about is ODF and Open XML. Nice misdirection.

---

### Post by blueturtl on 2010-05-08
> **sydbat said:**
> All that link talks about is ODF and Open XML. Nice misdirection.

First sentence on the page:

> The Microsoft Office file formats documentation provides detailed technical specifications for Microsoft Office file formats, **including the binary file formats** as well as the standards-based file formats, ODF and Open XML (ECMA 376 and IS 29500). 

Now I am curious.

---

### Post by Calmor on 2010-05-11
> **blueturtl said:**
> Now I am curious.

It does appear that the documentation is there... interesting!

---

### Post by sbergman on 2010-05-11
> ..... I swear this thing is purposely spinning empty for-loops

That line really cracked me up.

---

### Post by 3Miro on 2010-05-14
> **Calmor said:**
> It does appear that the documentation is there... interesting!

From what I have read about wine, the problem with MS is not that they have no documentation, but rather that they have very poor documentation. Basically they will be usually missing key things and/or have incorrect information. MS often doesn't follow its own specification, otherwise it makes no sense that they are unable to make MS Office files compatible between Mac and Windows.

Due to bad documentation, WineHQ people had to reverse engineer the API (not the code). That was the main reason why it took so long to come up with a usable wine version (and why they have so many regressions so often). If you have the exact API specification, making wine is just code crunching, still hard and time consuming, but straight forward.

---

### Post by KingYaba on 2010-05-14
With Compiz Ubuntu is more usable than Windows 7. The only reason I have Windows 7 on my hard drive is because of, well, games. :) But Compiz and Gnome-Do are so nice to have. Instead of clicking around, I simply invoke Gnome-DO and open what I need. Apps, images, documents, you name it. Win 7 also removed a trojan the other day. Glad I don't do my banking on there!

---

### Post by MooPi on 2010-05-16
I use Windows 7 for gaming and nothing else. PERIOD. Linux has something that Microsoft will probably never give me,(freedom to control my system completely). There isn't an Itunes that tries to control my music files in how they are recorded and played. There isn't a Quicken the locks my personal finance info into a proprietary format that must always be updated to the newest version. Same goes for Office software that doesn't play well with others. Now on to security. AV software that robs my system of resources and the constant small nagging fear that at any moment a new and exotic virus hack or malicious code will be deployed on my system. The entire ecosystem of the Windows world seems viral and combative to me and doesn't have that warm fuzzy feeling I get by booting to Linux. Yes I said warm and fuzzy about Linux.:P

---

### Post by RiceMonster on 2010-05-16
> **MooPi said:**
> There isn't an Itunes that tries to control my music files in how they are recorded and played. There isn't a Quicken the locks my personal finance info into a proprietary format that must always be updated to the newest version.

I'm confused, is someone forcing you to install those or something? There's other options on Windows, you know.

---

### Post by steveneddy on 2010-05-16
I have 7 in a VM, but only for the few times when i actually need it, which isn't very often.

Can't wait to get home next week and install 10.04.

The Live CD looks great.

---

### Post by jerenept on 2010-05-16
Anyone posting on this thread should scroll up to the top and READ CAREFULLY!!!!

---

### Post by jerenept on 2010-05-16
COME ON CAN'T WE ALL JUST GET ALONG PLEASE!
[http://en.wikipedia.org/wiki/Ubuntu_(philosophy)]("http://en.wikipedia.org/wiki/Ubuntu_(philosophy)")
The main thing is personal choice, not flaming whoever does not agree with you.
Uh, I think GNUCash and OpenOffice are available for windows too...

---

### Post by JayKay3000 on 2010-05-16
Great, funny thread!

Luckily i've had few problems with windows so I can't really complain and I need to keep in the know for support purposes. I skipped the Vista era though. 

I have to admit I was a 'noob' recently and set the old family XP machines page file to 2gb, to defragment the drive windows needs 15% free but there is no error check that takes into account the page file size. So an indicated 18% free hard drive space was lower than 15% if you included the 2gb into the total size. The defragmenter simply says 'error in file so n so' (some system file). Changing the page file back to a small size it worked fine. I did every check before I clicked that was the prob. D'oh! But it's not every day I work with 25GB hard drive partitions!

I really enjoy using Ubuntu/Kubuntu but I also really enjoy using windows 7. I've not tried using an ATI card and simply use NVIDIA because all of my pc cards have ever been of that brand.

I use openoffice so cross compatibility has never been a problem when working. I submitted my 17k word dissertation in .odf format for uni + the uni machines have openoffice installed so no probs there. 

Gimp and 7-zip both work on win an Linux and Java applications are often cross platform.

Spotify even runs under wine which is great!

The only thing that holds me to ms is Windows Messenger because I use it to make video calls to family & the wireless was an issue. But since 10.2 that seems to work fine on my laptop. Bonus! I do wish that movie dvds worked out of the box because that must be a little off-putting for non geeks and I always forget how to do it. It's easy to do though 'once you know'.

I've also yet to try Format Factory under wine, although even in Windows 7 it flashes and sort of crashes the aero sometimes.

The other problem is that I just love using Windows 7 even with all those potential viruses but i've been using Panda Cloud av for a while on Win 7 and Xp which seems to function great.

But whenever I download some new app i'm always anxious. I tend to look for stuff with reviews (especially if it's freeware) so that I know people have used it without problems.

The integrated installation environment within Ubuntu/Kubuntu is fantastic, even installing stuff through the terminal is a whiz after a little practice. It's also 'nice' to see what is going on.

---

### Post by screaminj3sus on 2010-05-16
Sounds like you just got really unlucky, I mean ubuntu does definitely install faster than widnows but win7 didnt take nearly that long for me, and when i first booted (I have a 4870) I was greeted with a proper res aero desktop with no driver installation needed, internet and sound worked too, of course I updated my ati drivers being a pc gamer. I quite like windows 7 its a big improvement. I also like ubuntu as well, they both have their strengths and weaknesses. If I wasnt a gamer Id probably switch to ubuntu just so I wouldnt have to pay for windows anymore.

And by the sound of the disc having norton and such on it it was not a "clean" windows disc which probably accounts why the install took a long time and such.

---

### Post by Ranko Kohime on 2010-05-16
> **Idaho Dan said:**
> I couldn't stop chuckling! That was good.
Makes me appreciate Ubuntu even more.
I couldn't stop guffawing.  Having a Mac as my desktop, though, I'm appreciative of nearly everything that is not related to Windows, though.  :)

---

### Post by 3Miro on 2010-05-19
> **screaminj3sus said:**
> Sounds like you just got really unlucky, I mean ubuntu does definitely install faster than widnows but win7 didnt take nearly that long for me, and when i first booted (I have a 4870) I was greeted with a proper res aero desktop with no driver installation needed, internet and sound worked too, of course I updated my ati drivers being a pc gamer. I quite like windows 7 its a big improvement. I also like ubuntu as well, they both have their strengths and weaknesses. If I wasnt a gamer Id probably switch to ubuntu just so I wouldnt have to pay for windows anymore.

And by the sound of the disc having norton and such on it it was not a "clean" windows disc which probably accounts why the install took a long time and such.

I think the default free ATI driver for Linux also supports compiz, you need the proprietary one for heavier work. Default NVIDIA driver, however, supports nothing.

Norton did not come with the Windows 7 CD, it came with the Driver CD for the motherboard. The Windows CD was "clean".

---

### Post by recluce on 2010-05-21
I realize that I am late to that discussion, but the OP and some other guys discussed rather hotly (YOU LIE! NO - YOU LIE!) about whether Windows 7 (or any other Windows NT family OS) would install to an extend partition or not.

The answer is a clear as mud "maybe". Without some extremely involved tinkering, Windows needs a SYSTEM partition that is primary. Note that the system partition is not the same as the WINDOWS partition. If you have any (non-hidden, active) primary partition that is FAT or NTFS, than Windows will happily use that as a system partition and an extended partition as the Windows partition. 

My setup for example:

/dev/sda1 (hidden diagnostics)
/dev/sda2 (small FAT32 partition, Windows SYSTEM drive, C:\)
/dev/sda3 (the logical partition "pointer")
/dev/sda4 (GRUB - dedicated GRUB boot, reiserfs)
/dev/sda5 (Windows XP, NTFS, D:\)
/dev/sda6 (Windows Data, NTFS, E:\)
/dev/sda7 (Windows 7, NTFS, F:\)
/dev/sda8 (Ubuntu Jaunty, reiserfs)
/dev/sda9 (Linux Swap)
/dev/sda10 (/home, EXT3)
/dev/sda11 (Ubuntu Lucid, EXT4)

This setup boots all four operating systems without a hitch, even though Windows XP is a three-stage boot (GRUB -> Win7 Bootmanager -> NTLDR)

Other than that, I can only (more or less) confirm the OPs assessment. Windows 7 is much better than Windows XP (as long as your old hardware and software is still supported), but I would not pay money for it (got it legally for free trough MS TechNet).

When compared to Ubuntu, I rather prefer Ubuntu over any Windows system. Less hassle, fewer reboots, more freedom, less headaches, more support of everything out of the box. Much cleaner 64bit implementation. That being said, I still need Windows for testing/support purposes - and of course for some new games. Older games are just as happy (or happier) under WINE or Virtual Box.

---

### Post by 3Miro on 2010-05-21
@recluce: Thanks for the enlightened post. Now I understand what was happening. I just erased a Linux ext4 extended partition and told Windows "Install there", however, I definitely did not give it a primary system partition (nor did I have one available, I had to clean both my Linux installs anyway).

I have actually been triple-booting for most of my computer life. When Windows 2000 came out, it was the most stable and secure windows yet, but many games were Windows 98 only. At that time I was also learning Mandrake 5 or 6. So I had Windows 2000, Windows 98 and Linux. 

Later I had the setting of Windows XP for games, 32-bit Ubuntu for regular use and 64-bit Ubuntu for work, now with the advancements of wine and 64-bit Linux I only dual boot Xubuntu 10.04 for everything and Some-Other-Distro to play with.

---

### Post by JedMeister on 2010-06-09
I'm a bit late to the party but here goes anyway...

@3Miro- Great post! I didn't wade through the pages of flame wars but your original post and the first page were worth the effort/ I can say that I feel your pain with Win7. 

IMO all-in-all it's not a bad OS (at least as far as Windows goes). I'm only a relatively new Ubuntu/Linux convert (I played with 6.06, then 7.04 but had too many headaches). I have been using it as my primary OS now for almost a year (9.04, 9.10 and now 10.04 although my laptop still running 9.10). I have had very little interest in Win7 as Ubuntu and XP (dual boot) continues to serve me fine but I recently got a new laptop at work and had no choice. 

During that time I must admit that I've been pleasantly surprised with Win7 (from a user standpoint) but only recently have I installed it on a PC at home (for some new games). I too found the install slow and painful with the harsh reality that in MS world installing the OS is only a small part of the process of a clean install. Even if you use a lot of non-standard apps in Ubuntu it's relatively easy to devise a script to install everything you want (or better still set up one system and use remastersys). I know there are tools for including updates and apps in Windows install mediums but as software so often gets out of date, even with that setup, you'll still spend a lot of time updating everything, and much of its not automated.

Another interesting thing that my son pointed out is that many of the (good) 'new' features in Win7 seem to have been 'robbed' from Linux or Mac!?

---

### Post by Ubom on 2010-06-09
I just installed both Ubuntu and Windows 7 on my new PC (using USB for both). I will entirely admit Ubuntu installed faster and more completely than Windows but Windows installer took around 25 mins to get to the desktop (about 10mins on Ubuntu).
Same result with both Windows 7 and Ubuntu, all drivers seem to be working but requiring updates, Windows 7 updater pops up telling me it wants to install around 20 updates including ATI driver, monitor settings, sound driver etc. even though everything appears to be working fine anyway so I selected them all and installed, message pops up saying the system needs to be restarted, postponed 4 hours but restarted anyway, no visible change to the system - I guess they were probably just more stable or something.
Ubuntu updater runs, around 100 updates here, takes a lot longer than Windows to installed, yet again restart required but not imposed on me, this time no postpone window either so thats a plus.
Overall:
Boot time is around 35 seconds on Windows and 20 seconds on Ubuntu but Windows loads Antivirus, MSN, steam, spotify and tweetdeck in that time so not sure how that works out.
Graphics performance far greater than in Ubuntu (ATI HD4850).
Sound, only basic output working in Ubuntu but everything working in Windows.
Speed, Windows 7 feels faster than Ubuntu, loading google chrome is as fast as I click the mouse where there is a 1 -2 second delay in Ubuntu. Sound also seems to be delayed while watching videos in Ubuntu, not much (less than half a second maybe) but annoying when watching movies. 
Software, for Windows I had a lot more software to install, such as chrome, Microsoft secutiry essentials, spotify, Windows live essentials, Office, CS4, iTunes, handbrake, Peazip taking around an hour after installing the OS compared to Ubuntu which just required installing Docky, New theme, chrome,  gimp, handbrake, restricted extras taking only around 20 minutes. Unlikely to be related to Ubuntu and more adobe but flash has horrible performance in Ubuntu compared to Windows.
Finally: I can watch around 5 1080p blu ray rips on Windows at the same time with no dropped frame rates anywhere but in Ubuntu even watching one 720p movie results in stuttering.
Overall I think that even though I have a soft spot for Ubuntu, Windows 7 is the better OS for my needs at the moment and since I already spent around £600 on CS4 (only £30 for Windows and £11 for office) I thought I might as well have it installed. I vary from week to week but recently I have been almost exclusively running Windows. Hopefully 10.10 will fix the sound and performance issues so that I can Ubuntu my primary OS.

---

### Post by kamaboko on 2010-06-09
There are just as many frustrating posts here installing Ubuntu from either scratch or an upgrade.

---

### Post by luceerose on 2010-06-10
> **Palanthas said:**
> I also have win98 SE that I install from time-to-time just for the fun of it

Installing windows for FUN ?!?
I'd rather do this --- ](*,)

---

### Post by proggy on 2010-06-10
> **3Miro said:**
> I am glad you guys enjoyed the rather long post. If something else comes up in the next couple of days, I will post update.
I did enjoy it,i even had time to do a couple of windows 7 installs while reading it.:lolflag:

---

### Post by 3Miro on 2010-06-13
I figurer one more point. Some people were calling me troll for saying that Windows 7 requires reboot upon installing graphics drivers. The technology for swapping drivers "on the fly" exists in Windows 7 Ultimate, but not regular home edition. Most people use Home Premium since Ultimate is considerably more expensive.

---

### Post by 3Miro on 2010-06-13
> **kamaboko said:**
> There are just as many frustrating posts here installing Ubuntu from either scratch or an upgrade.

The purpose of this forum is for people to ask for help. The overwhelming majority of us have no trouble with Ubuntu or whatsoever and we often come here in order to help others.

---

### Post by kamaboko on 2010-06-13
> **3Miro said:**
> The purpose of this forum is for people to ask for help. The overwhelming majority of us have no trouble with Ubuntu or whatsoever and we often come here in order to help others.

If there were no problems, there would be no need for help.  I would also argue against the suggestion that the overwhelming majority of people don't have problems with Ubuntu, or Linux for that fact.  There are simply too many posts on this BB to demonstrate otherwise.  General Help alone has over 8000 pages of help requests.

---

### Post by smellyman on 2010-06-13
> **kamaboko said:**
> If there were no problems, there would be no need for help.  I would also argue against the suggestion that the overwhelming majority of people don't have problems with Ubuntu, or Linux for that fact.  There are simply too many posts on this BB to demonstrate otherwise.  General Help alone has over 8000 pages of help requests.

ranging from the benign to severe.

8000 "problems" / 12000000 users = pretty good ratio

---

### Post by 3Miro on 2010-06-14
> **kamaboko said:**
> If there were no problems, there would be no need for help.  I would also argue against the suggestion that the overwhelming majority of people don't have problems with Ubuntu, or Linux for that fact.  There are simply too many posts on this BB to demonstrate otherwise.  General Help alone has over 8000 pages of help requests.

Do you believe that given the enormous variety of hardware and users it is possible to make a system that is completely without "problems"? Besides your point about the 8000 pages is not valid. The forum doesn't delete old pages and most of those 8000 pages concern old versions of Ubuntu. With Google, I often come upon threads from 2005 - 2006 with bugs/issues that have been resolved long time ago. Then you get thousands of threads of the type: "Should I use 64-bit vs 32-bit?", "How do I set up different Wallpapers under Gnome/KDE/XFCE?", "How do I change the buttons?", "I am using media player X, but I don't like it. Does anyone know of a better one?" ... Those are valid questions, but they do not constitute a "problem". 

The overwhelming majority of "problems" that people have come form either hardware incompatibility or wrong set up. With every release there are overall fewer and fewer HW issues (with only printers remaining as the one really weak area). Considering how most people get Windows pre-installed for them and then they try to set up Linux entirely on their own, problems are only natural. I wonder how many problems people would have if the average user had to set up Windows on their own.

---

### Post by julio_cortez on 2010-06-14
@ OP: This is one of the most entertaining posts I've ever read.. keep it up!!

By the way, I've been running Kubuntu for 4 days in a row and had no trouble..
Switched to Win 7 (I had to move some files from/to my portable music player which uses SonicStage) and it crashed after half an hour.. What the heck?

Seriously, I'm starting thinking you're right.. Though, in my case, I'm more prone to think it's some driver/BIOS issue (already happened with my HD5770 where I had to ask Sapphire for a stable BIOS to make it work) than a W7 one..

---

### Post by t.rei on 2010-06-14
Usually the uptime of my computer only gets cut off, when a kernel upgrade occurs, and I am running this thing every single day for multiple hours. Wich would be sad, if it weren't my 'job'. So yeah, I'm very comfortable with ubuntu. I do have a win7 install. I never boot it tho. Just keep it lingering there if a game should come along, that does not play well with wine. :P

Just yesterday I had a 'customer' complaining about something not working in ubuntu... he went on a rage and started installing win7... at the evening (7 hours later) he called me again, saying he's sorry for the hate and that he's back on ubuntu, because 'nothing worked properly'... the usual end-user-bugreport... and that he figured if 9.10 works flawlessly and 10.4 doesn't why not use 9.10 ... 

Yes, installing windows is - mostly - a pain in the bum. Well not windows itself, that installs rather smoothly, but all the additional software needed, all the configuring of said additional software and all the updates. 

Actually, from a company point of view, giving this to us 'for free', having this be free software is INSANE. But without it, without every single raindrop of content, help, discussion, contribution and thoughts - even rage - this would never ever have been possible to get. And not possible to improve at such huge paces.

THANKS to EVERYONE!

---

### Post by rmvasuki on 2010-06-14
Awesome post. 80% of what I experienced trying to install windows on my cousin's desktop!

---

### Post by Johnsie on 2010-06-14
Shame you can't run most professional quality applications natively in Ubuntu and are left with the lower quality 'linux equivalent' lol.

---

### Post by kamaboko on 2010-06-14
> **smellyman said:**
> ranging from the benign to severe.

8000 "problems" / 12000000 users = pretty good ratio

Uhh....those are pages, not threads.  Each page contains numbers of threads.  And...there are 14 more categories in the main support area which I didn't include.  Furthermore, how did you come up with 12 million users?

---

### Post by kamaboko on 2010-06-14
> **3Miro said:**
> Do you believe that given the enormous variety of hardware and users it is possible to make a system that is completely without "problems"?

Good point.  Remember that when you think about Windows.

---

### Post by 3Miro on 2010-06-14
> **kamaboko said:**
> Uhh....those are pages, not threads.  Each page contains numbers of threads.  And...there are 14 more categories in the main support area which I didn't include.  Furthermore, how did you come up with 12 million users?

Most of those 8000 pages are 4 - 5 years old and concern issues from old versions of Ubuntu that have been fixed already. Then there are many non-support questions especially in the non-general area. The number of pagers in the non-general area is also much smaller (something of the order of 2000 per category of which most are also old).

If you want a comparison, go around the windows forums and see what is going on. This is on top of the MS call centers which is the main source of support for Windows. Besides most of the manufacturers/vendors provide additional support of their own. Try to count those "problems" and then divide it by the approximate number of Windows users.

---

### Post by 3Miro on 2010-06-14
> **kamaboko said:**
> Good point.  Remember that when you think about Windows.

I believe you have missed my point on the first post. Windows worked exactly like it was supposed to work, there were no crashes or "issues". My problems is with the way MS thinks a system should work, which is a huge contrast compared to the FOSS philosophy.

---

### Post by smellyman on 2010-06-14
> **kamaboko said:**
> Uhh....those are pages, not threads. Each page contains numbers of threads. And...there are 14 more categories in the main support area which I didn't include. Furthermore, how did you come up with 12 million users?
 
ohh silly me.
 
sincere apologies

---

