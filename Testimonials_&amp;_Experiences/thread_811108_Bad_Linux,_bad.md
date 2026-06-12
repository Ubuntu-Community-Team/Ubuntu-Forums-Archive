---
title: "Bad Linux, bad"
date: 2008-05-28
forum: Testimonials &amp; Experiences
---

### Post by mlemanczyk on 2008-05-28
Hi,

I suspect there may be big discussion on this topic. I may be blamed for it. But still, I need to write this.

My adventure with Linux started with Red Hat 6.0. Since then I installed it like 5 times. Every time something didn't work. My printer, my scanner, my sound card (working with Red Hat 6, didn't work with Red Hat 7 etc.). After it I dropped Linux for few years.

Now I'm back & I'm going away again. Come on...

I started with Ubuntu 7.10. Cool. Looks nice. All hardware was recognized. Great. But some of the software was deprecated. Then my friend told me, that there is Ubuntu 8.04 coming out. This is great. I read in a newspaper, that this is the most expected release this year!

I couldn't wait 3 days until the official release. I follow upgrade path and upgraded my 7.10 installation using automatic updates. It downloaded & installed everything. Again, 3 days before official release date.

This is were problems start. 3 days before release date my Ubuntu 8.04 was crashing evey 5 mins, because of kernel panic. I've found on forums, that many people have the same problem because there are some problems with wireless drivers. Not good...

Ok, final release came out. I downloaded it & installed by formatting my hard drive. Cool. All hardware was recognized. Wireless is working, sound is working, I even installed my printer, shared on Winndows. Great.

I spent like 2 weeks playing with the installation. Then, I went into Synaptics Package Manager and turned on all update options. I installed new kernel etc. All new packages were coming to me right away. Cool.

Seems, like the problems are resolved? Great. I recommended Ubuntu 8.04 to my father & friend. I installed it by myself on my father's computer & tried to configure. No luck. After some tricks with graphic modes I finally got it to install (ATI graphics card). Then I installed & configured MPlayer to play DivX movies. Oh, no! There is no video when playing any movies! I search on Google and found out a setting to be set in X configuration file, for ATI cards. Good. After restarting I got MPlayer to display the video.

Then I started with TV card... I installed one of the apps for TV watching. Oh no, there is no video again! I went to X config & disabled the setting. Video from TV card is on again. But MPlayer is not showing any movies. It's playing, but you can't see anything. I switched the setting again. MPlayer is working, TV is not!

That's the place were Ubuntu adventure finished for my father. He came back to Windows. He can watch movies & TV with the same configuration! Wow...

Then, my friend downloaded & tried to install Ubuntu 8.04 on his laptop. No way. It's crashing at 54%. Too bad. That's were Linux adventure finished for my friend.

Now me. After Googling I finally found out, how to mount Samba shares using fstab. Gfvs was not working properly with F-Spot. Too bad, but I workarounded it with fstab. Unfortunately, it is not working properly & can't be used with multiuser environment, because the mount folder needs to be owned by the mounting user. I found out on forums, that this is a planned future. Huh... Ok, I can live with this. I just created multiple fstab entries for other users. Good. Mounted ok & seems to work.

I started F-Spot & tried to import images (without copying to local folder) from Windows Share. Kernel panic occurred during import. Now, every time I start F-Spot and view already imported images, I'm getting kernel panic! Too bad...

Anyway, I don't need to use F-Spot, right? Then can live with it. I used Ubuntu successfully for some time. Until some time there was an update to the packages, which screw my login screen. I can't see users list anymore. There is a box for it, but it's not displaying anymore. Every time I need to enter user name manually. Not a big deal, right? I can live with it.

So, what's left. I'm watching Flash movies on You Tube. But, god dammed, it's really slow. Some of them are good. But most are taking 100% CPU power & are breaking. It wasn't like that under Windows XP Pro! Huh, I can live with that.



I downloaded & installed KMyMoney. This is really great piece. I can substitute MS Money with it. It's missing some features, but hey! I'm a programmer. I can contribute to the community & help developing it. So I downloaded & installed KDevelop, QT Develop & so on. Everything, what was required. Let's try to debug. I put a breakpoint & started. Didn't stop at the breaking :-/ I tried to solve this problem for a day & gave up. Then an idea came to my mind. Maybe it didn't stop, because I have real KMyMoney installation separately. I uninstalled it, compiled from & started again. No luck. In addition, some it was giving error during startup because of missing resources. Ok... I gave up on this. I won't contribute.

Now, let's watch some funny movies on JoeMonster.org. Some of them worked nice. Then one of them was handled by MPlayer addin for Firefox. It buffered & started playing. Just after that the system crashed with blank screen with some distortions. Not good.

Let's not play too much movies in a row. I was just surfing web pages & ended up with 3 kernel panics! Come on. WTF is Kernel Panic? Poor, poor kernel. It doesn't know what to do & is going into panic, so I can't do anything.

What is the result of todays evening? 4 Ubuntu 8.04 crashes. What is the total balance of Ubuntu installation? Lot of problems and kernel panics!

Come on. Regular (not IT) user will never use a system like this! For a regular user, there is no such thing like "terminal" or "command prompt"! Everything must be GUI, with the less possible user possible user interaction!

Linux will NEVER get into personal computers of regular users, unless:
1) there will be drivers for the hardware
2) Linux performance will be at least that good as Windows
3) there will be no need terminal use

I was watching Linux improvements by at least 10 years. Come on!

1) You're wasting resources on reinventing the wheel in many cases. At least 2 window managers (Gnome, KDE). Couple of different software used for exactly the same thing (e.g. CD burning). No compatibility between these 2 window managers! Etc. There are plenty of examples.

2) NO BACKWARD COMPATIBILITY. This is a MUST. All new lib versions & kernels MUST BE backward compatible. There is NO EXCUSE for this. It's unacceptable, that a driver works with kernel version 2.xx & doesn't work with 2.yy. You're wasting resources. Same with all other software. Why user list on my login screen stopped working after I upgrade some of the packages with your Update Manager?

3) There is NO COMPANY in the market, which can support your NO BACKWARD COMPATIBILITY model. If you want companies to write good drivers for your OS, YOU MUST provide them with backward compatibility. Otherwise no one reasonable will develop drivers for you.

4) You need to provide driver model, which is efficient and backward compatible. Why Apple is successful with Unix? Because they support very little of hardware, but have good drivers. Concentrate on the performance & write good drivers. People can't use BETA software all the time. My impression on Ubuntu 8.04 is, that it's mostly beta & pre-release software.

I'll watch your steps ;-) But for now, I'll disrecommend Linux to all home users. It's not for them. It's for servers, where graphics performance is not important, there is no need for TV cards, cameras etc. I've 2-3 Linux VM running successfully as server versions, without any GUI.

I'm sorry to say that, but Linux is great for admins & server use. But for home users it's unfortunately useless & the situation didn't change at least since 10 years.

---

### Post by dougmorin on 2008-05-28
do i see a tear?

---

### Post by perlluver on 2008-05-28
I have tried just about every Linux distribution there is, I am now running Slackware, I must say in all my journey's Ubuntu was the easiest one that just worked with all of my hardware.  I have installed on about 6 different computers and have yet to have any major problems.  The ones I did have I got pretty quick answers from these forums.  It just takes patience and knowledge.

Sorry to see you go, come back and visit when Intrepid Ibex comes out.

---

### Post by mlemanczyk on 2008-05-28
Yeah, thanks Perlluver. I spent with Ubuntu 8.04 all the time since the first day it came out & a few days with Ubuntu 7.10 before, but including today I was mostly solving problems & finding workarounds.

I can hear many people blaming Windows because of the security or stability, but for me Ubuntu was really way of behind. It stops working for me, crashes with Kernel Panic, not mentioning other software crashing with no reason :-(

I don't want to be offensive with my post or blame all & everything. I hope you'll figure out what is the reason for these problems (especially backward compatibility) and solve it one day :-)

---

### Post by mlemanczyk on 2008-05-28
> **dougmorin said:**
> do i see a tear?

No, not really. I'm a legal Windows XP Pro & MS Money owner. I'd like to contribute some way to Linux, because I believe it has possible potential. So, from time to time with some new releases I'm installing Linux distributions.

After I've installed 8.04 I liked it that much, that I completely removed my Windows installation and moved my data to KMyMoney. Now I'm a little sad, that I need to reinstall everything, because Ubuntu turned out to be very unstable. 4 crashes in a single evening is really too much :-(

Btw. It happened also on my father's computer with LAN (not wireless). When I was downloading big files for a longer time, it was going into kernel panic :-/

Not mentioning, that I didn't get my IPCop/Zerina installation working with Network Manager plugin. I converted p12 file as required, but still it can't connect. It doesn't also accept my Zerina client package and I had to enter everything manually. But with OpenVPN Gui under Windows everything was working in 5mins.

There are really many problems like this :-(

---

### Post by raul_ on 2008-05-28
Nice until the conclusion, too much troll influence imho.

Plus, Linux is not Ubuntu

---

### Post by Ripfox on 2008-05-28
Hmm. I use it for home use on all my computers and it seems quite useful to me. :lolflag:

Oh yea it's on all my work computers too...huh.

---

### Post by jrusso2 on 2008-05-28
I gave up years ago any idea that Linux would become mainstream but it does what I want, and I enjoy using it and thats good enough for me.

---

### Post by jimv on 2008-05-29
Linux IS NOT:

For servers
For the desktop
For new users
For experienced users
For your mom

It's for whoever wants to use it.  End of story.  If it doesn't work for you, well, oh well.  This isn't a business endeavor.  No one is losing any money if you decide to go back to Windows.  Thanks for being part of the community.

---

### Post by kpkeerthi on 2008-05-29
Its very unfortunate that Linux does not work for you the way you want it to. But for million others (including me), Linux is serving well and as the only primary OS. If it did not work you, it does not mean that it will not and is not working for everyone. 

I understand your disappointment but please do remember that linux is more community driven and support for more hardware can be extended only if the manufacturers are willing to open their specs to the community and/or provide native linux drivers themselves. We should blame the manufacturers, not linux. 

In my opinion, Linux is a better OS than the one that has currently monopolised the market. I don't care if Linux is not dominating the desktop market (and if it ever will) as long as I'm able to do what I need to do with Linux.

---

### Post by lisati on 2008-05-29
Sorry to hear of the woes people sometimes experience, but which OS doesn't come with its share of hiccups?

I have 7.04 Feisty as the main OS on my laptop and apart from a few headaches when I manage to mess things up, it serves me well - surfing, occasional email, occasional printing through my home network (thankfully it came with a driver for one of my printers), browsing these forums.....

---

### Post by mlemanczyk on 2008-05-29
I just found the reason for my problems. It's all described in another thread
[http://ubuntuforums.org/showthread.php?t=768200&highlight=caps+lock+blinks&page=3](http://ubuntuforums.org/showthread.php?t=768200&highlight=caps+lock+blinks&page=3)

It's just terrible for me. There are better days, when it doesn't crash, but mostly they are much worse, when it crashes every few mins - like today & yesterday.

I could see some ACPI failures in kern log files. I went & disabled APM & ACPI, but still doesn't work. It seems, that whenever there are multiple wireless requests in a very short time, it freezes for me.

Example
Open 10 different web pages in Firefox. Close & save the session. Now start FF. After it starts loading all the web pages, Hardy freezes with kernel panic.

I didn't go trough all posts in that thread, yet. But I'll look, if there is a workaround to my problems with freezing all over and over again.

---

### Post by Nexano on 2008-05-29
> **mlemanczyk said:**
> Hi,

Linux will NEVER get into personal computers of regular users, unless:
1) there will be drivers for the hardware
2) Linux performance will be at least that good as Windows
3) there will be no need terminal use

I was watching Linux improvements by at least 10 years. Come on!

1) You're wasting resources on reinventing the wheel in many cases. At least 2 window managers (Gnome, KDE). Couple of different software used for exactly the same thing (e.g. CD burning). No compatibility between these 2 window managers! Etc. There are plenty of examples.

2) NO BACKWARD COMPATIBILITY. This is a MUST. All new lib versions & kernels MUST BE backward compatible. There is NO EXCUSE for this. It's unacceptable, that a driver works with kernel version 2.xx & doesn't work with 2.yy. You're wasting resources. Same with all other software. Why user list on my login screen stopped working after I upgrade some of the packages with your Update Manager?

3) There is NO COMPANY in the market, which can support your NO BACKWARD COMPATIBILITY model. If you want companies to write good drivers for your OS, YOU MUST provide them with backward compatibility. Otherwise no one reasonable will develop drivers for you.

4) You need to provide driver model, which is efficient and backward compatible. Why Apple is successful with Unix? Because they support very little of hardware, but have good drivers. Concentrate on the performance & write good drivers. People can't use BETA software all the time. My impression on Ubuntu 8.04 is, that it's mostly beta & pre-release software.

I'll watch your steps ;-) But for now, I'll disrecommend Linux to all home users. It's not for them. It's for servers, where graphics performance is not important, there is no need for TV cards, cameras etc. I've 2-3 Linux VM running successfully as server versions, without any GUI.

I'm sorry to say that, but Linux is great for admins & server use. But for home users it's unfortunately useless & the situation didn't change at least since 10 years.

Drivers for the hardware? thats not linux developers fault, its the companies that make the hardwares fault. Nvidia is one of the companies that supports linux and makes good drivers.

On my end, linux performance > windows by a long shot.

Terminals are barely used as it is in ubuntu. Theres very little you HAVE to use a terminal for.

Backward compatibility? You mean like Microsoft went NT and ditched anything DOS based completely? Yay i have to download emulators or downgrade to win98 to play my old games \o/

Apple is successfull thanks to fanbois and hype. Yes theyve got some strong points, but to be honest, i dont even see what its doing on the market :x OS X is more restrictive then Windows, Mac`s cost way too much. Apple make money on i-pods, i-phones and i-paywhateveryoutellmetoaslongasimcool.

---

### Post by zetetic on 2008-05-29
I have reasons to suspect the OP is a troll.

---

### Post by mlemanczyk on 2008-05-31
Seems that I may stay with Linux. I'm updating the other topic with my testing results about lock ups.

Anyway, I believe my points about backward compatibility are still valid. I've seen it planty of times:
1) CMI driver was working & compiling in 1 kernel version & wasn't compiling in little bit newer
2) CMI driver was working in 1 kernel version & was giving noices only in a little newer one
3) Kylix was installing in one Red Hat version fine & wasn't in a newer one without tricks
4) cross-linux (sic!) compatibility problems. The app may work in one distro and doesn't work in other
5) latest example. I used VMWare 1.x. It turned out that there is full screen problem and keyboard stops working correctly in Ubuntu. There is a workaround for this, but doesn't work everytime. I couldn't even install it without a special patch in 8.04.
6) why I need to recompile a driver, if it was compiled for a different kernel version?

That's what I call backward compatibility. My understanding is that lot of developers' work goes into keeping their Linux apps up to date everytime when other libraries change and making sure it can work in other distros.

This is really bad. You can't break interface contract. Whatever bad you say on MS, they are (were?) keeping their interface contracts. In most cases, if they wanted to add/change some functionality, they created a new interface leaving the old one the same. If they were going to drop any WinAPI functions, there was a notice about it for a really long time in advance.

Unfortunately, that's not what they did with Vista. They broke their contracts in many areas. Many applications (even very simple, like movie players)  stopped working. Drivers architecture changed and they dropped many drivers. In my opinion this is the place of their failure and that's why people doesn't really like Vista. It's crashing, its performance is worse etc. I tried it on my box - no drivers, no performance. I switched back to XP.

I'm not saying that all developers are breaking contracts in Linux. Many of them are not. I just believe that if the others stop doing it, you will be in a very good shape and will go forward at high speed. And this is what I'd concentrate on. If you solve this problem, you'll have much less work ;-)

It just came to my mind. If you look into the thread I gave above, you'll see many people complaining about functionality, which worked in previous release(s) and stopped. This is what I call "no backward compatibility".

---

### Post by jocko on 2008-05-31
> **mlemanczyk said:**
> 1) CMI driver was working & compiling in 1 kernel version & wasn't compiling in little bit newer
2) CMI driver was working in 1 kernel version & was giving noices only in a little newer one
3) Kylix was installing in one Red Hat version fine & wasn't in a newer one without tricks
4) cross-linux (sic!) compatibility problems. The app may work in one distro and doesn't work in other
5) latest example. I used VMWare 1.x. It turned out that there is full screen problem and keyboard stops working correctly in Ubuntu. There is a workaround for this, but doesn't work everytime. I couldn't even install it without a special patch in 8.04.
6) why I need to recompile a driver, if it was compiled for a different kernel version?

That's what I call backward compatibility. My understanding is that lot of developers' work goes into keeping their Linux apps up to date everytime when other libraries change and making sure it can work in other distros.

This is really bad. You can't break interface contract. Whatever bad you say on MS, they are (were?) keeping their interface contracts. In most cases, if they wanted to add/change some functionality, they created a new interface leaving the old one the same. If they were going to drop any WinAPI functions, there was a notice about it for a really long time in advance.

Unfortunately, that's not what they did with Vista. They broke their contracts in many areas. Many applications (even very simple, like movie players)  stopped working. Drivers architecture changed and they dropped many drivers. In my opinion this is the place of their failure and that's why people doesn't really like Vista. It's crashing, its performance is worse etc. I tried it on my box - no drivers, no performance. I switched back to XP.

I'm not saying that all developers are breaking contracts in Linux. Many of them are not. I just believe that if the others stop doing it, you will be in a very good shape and will go forward at high speed. And this is what I'd concentrate on. If you solve this problem, you'll have much less work ;-)

Why you need to recompile a driver that was compiled for a different kernel?
The same reason why a driver compiled for windows XP doesn't work in windows vista (or even why some drivers compiled for the original release of windows XP did not work in service pack 1 and so on).
As the kernel changes, some of the functions the driver needs to access will work differently (some functions gets other names, some gets replaced by other functions and so on), which means the driver has to be compiled against the kernel it is intended to run on.
I'm not sure what your problem is. It is probably impossible to make ONE driver that is compatible with all available versions of the linux kernel (pre 1.0 to the current 2.6.25), not to mention that it's absolutely impossible to make one that will be compatible with all future versions... Unless the linux developers would suddenly realize they had reached the absolute perfect kernel which never again have to be changed.
The same is true for windows, there is not ONE hardware driver that is compatible with windows 3.x, windows 95, 98, Millenium, NT, 2000, XP, Vista, and probably not one that is compatible with all minor revisions (service packs) within the "same" windows version.
It's just that the hardware manufacturers make most of their money selling their products to windows users and OEM's that preinstall windows, so they make sure to release driver install packages that contains precompiled drivers for all currently supported versions of the windows kernel.

---

### Post by jespdj on 2008-05-31
> **mlemanczyk said:**
> Linux will NEVER get into personal computers of regular users, unless:
1) there will be drivers for the hardware
2) Linux performance will be at least that good as Windows
3) there will be no need terminal use

1. That's the fault of hardware manufacturers, not of Ubuntu or Linux developers. Kick manufacturers who don't want to open up their hardware to Linux in the pants by buying hardware from their competitors who do make good Linux drivers (or who open up the specs to their devices so that others can make open source drivers). For example, buy an nVidia graphics card instead of an ATI.

2. This is simply not true; Linux / Ubuntu does not perform worse than Windows.

3. You almost never need to use the terminal if you don't want to; Ubuntu contains a GUI for almost anything that you can configure in the system.

---

### Post by mlemanczyk on 2008-06-02
Jocko,
you are partially right. It's a valid situation, where a driver works on 1.x version, but doesn't on 2.x. That I can understand. But why it doesn't work when minor version change, e.g. from 2.6.x to 2.6.y or I should even say from 2.x to 2.y?

That's exactly what I'm trying to say & you confirmed. Some function got renamed, some got removed, some other works differently. This means, that the contract gets broken. This is true for many other Linux apps.

I believe, that once people realize they can not break the contract, you will go forward much faster.

---

### Post by mlemanczyk on 2008-06-02
> **jespdj said:**
> 1. That's the fault of hardware manufacturers, not of Ubuntu or Linux developers. Kick manufacturers who don't want to open up their hardware to Linux in the pants by buying hardware from their competitors who do make good Linux drivers (or who open up the specs to their devices so that others can make open source drivers). For example, buy an nVidia graphics card instead of an ATI.

I can partially agree with you. It's partially hardware manufacturers fault. But I still think their fault is much less, then Linux community. If I'd be hardware manufacturer, I'd not support OS, where an interface contract may change every 2 months and my drivers need to be reworked/rewritten.

> **jespdj said:**
> 2. This is simply not true; Linux / Ubuntu does not perform worse than Windows.
Unfortunately it's true for me. Graphics performance is really bad on my Intel card in notebook. Flash is breaking up in full screen. Some times is breaking up in windowed mode. Some other display futures are working very slow (e.g. F-spot in full screen). It wasn't like this under Windows :-(

> **jespdj said:**
> 3. You almost never need to use the terminal if you don't want to; Ubuntu contains a GUI for almost anything that you can configure in the system.

Yeah, I wish it was true and I could install VMWare Server and many other apps without compiling (parts of) them first ;-)

---

### Post by powerpleb on 2008-06-02
> But why it doesn't work when minor version change, e.g. from 2.6.x to 2.6.y or I should even say from 2.x to 2.y?

I can partly sympathize with you there. But I suppose it's because Linux develops and evolves a lot more rapidly than Windows, which is both one of it's main strengths and weaknesses.

But if you want an ultra stable Linux OS that doesn't change much maybe try something like Debian Etch (stable) rather than Ubuntu.

> 
I wish it was true and I could install VMWare Server and many other apps without compiling (parts of) them first

Yeah but I thought we were talking about average desktop user stuff. Almost everything you're average computer user will ever use is available through Add/Remove Programs and needs only a check of a box and a click of the Apply Changes button which, actually, is far simpler than installing something in Windows.

---

### Post by Keyper7 on 2008-06-02
> **mlemanczyk said:**
> I can partially agree with you. It's partially hardware manufacturers fault. But I still think their fault is much less, then Linux community. If I'd be hardware manufacturer, I'd not support OS, where an interface contract may change every 2 months and my drivers need to be reworked/rewritten.

If you were a hardware manufacturer, you wouldn't have to worry about reworking or rewriting anything if you did your work correctly. Take nVidia as an example: I used a same driver installer in 7.04, 7.10 and 8.04 and everything worked.

And about your other points, I'm sorry for your problems and I want to help you with them, but first you'll have to stop generalizing your experiences into statements about what the Linux community should do or what Ubuntu must do to be ready for the desktop. You are not the only user in the universe and your hardware is not the only hardware in the universe. Don't be a [well-intentioned Linux troll]("http://ubuntuforums.org/showthread.php?t=58017").

Everything in 8.04 worked for me out of the box, but I won't use this as an argument to say that Ubuntu is ready, because that would be an improper generalization as well.

---

### Post by karellen on 2008-06-02
I've read your post carefully and you obviously have some good points like backward compatibility, system crashes. I've tried Hardy myself and when Nautilus froze for no apparent reason I decided it's time to give other distros a shot. and so I'm having a very good experience with Mandriva. anyway, what I'm trying to say it's that "Linux" is a very heterogeneous world, full of unpredictable things. some distros work like a charm on a particular piece of hardware, some don't. some people say this is a big problem (inconsistency and fragmentation -> an almost complete lack of standardization - > Linux being treated as a step son by the OEM -> poor/lacking drivers) others consider thing a strength of the open source development model (myriad of choices and no uniform platform aka "Linux is not Windows"). the choice between these antagonistic attitudes resides to everyone. if you ask me, I try to hold the middle ground ;)

---

### Post by mlemanczyk on 2008-06-05
OK, I haven't been here for a while. Flashing motherboard's BIOS with FreeDos turned out to be bad idea for me & broke notebook.

But now I'm back on a new one ;-)

What really surprised me is, that I plugged in my hard drive from old notebook into new one with USB case & Ubuntu 8.04 started. It found out all new hardware and now I can work with it. I noticed that in Windows it's not the case, if you change the architecture completely - in most of my cases I had to reinstall it.

But... Here comes ATI problems. It's not working correctly :-/ X1600 or something like this. For most things it works, but not for the others. E.g.:
- MPlayer doesn't like it
- (Advanced) Desktop Effects don't like it
- I had really hard time with uninstalling vendor's drivers & reinstalling Ubuntu ones. After I followed ATI instruction, my X server configuration got broken & I had limited resolution & functionality. So I came back to downloaded ATI drivers.

I'm not saying Ubuntu is bad. What I'm trying to say is, that there are things which are driving new Linux users crazy. I tried Ubuntu on different computers and always have had problems with hardware:
- Sound Blaster Live 24 was recognized as Audigy in 7.10. Microfone didn't work in Skype
- Reinstalling 7.10 on the same box caused sound card to be recognized as a different one, then it was for the first time (nothing changed in the computer). He we come to unpredictability
- I didn't get PixelView TV Pak (Pro?) to work under 7.10. I sold out the TV card finally.
- My GE Skype phone doesn't work with Ubuntu 7.10 & 8.04. For this reason I can't switch to Linux on my server, since it's providing me Skype "for home" functionality
- In clean 7.10 installation I couldn't get BMPx to handle all supported codecs. I installed planty of libs, but still it was missing some :-( Once I switched to 8.04 it started supporting all of them
- After installing KDevelop & QT Develop I couldn't get debugger to work. Still didn't solve the problem, yet

All this is common hardware. Nothing really special, maybe except for the phone.

Let me summarize with the points from "Anatomy of a well-intentioned Linux Troll" web page:
1. Check email/instant message.
Yes, this I can do, except for GTalk. Pidgin in 8.04 just doesn't let me to add new GTalk users. Tough it was working in 7.10 for me. Luckily Polish Gadu-Gadu plugin works like a charm.

2. Surf the internet
Yes, I can, with some limitations. On my previous box Flash movies were terribly slow. In 8.04 there is FF 3.0 Beta installed by default. Latest release (RC)  doesn't support all plugins which I use (e.g. Foxmarks, GreaseMonkey).

3. Organize pictures
F-spot finally started working with Samba shares, after I workarounded it and got them to mount in fstab. It wasn't working correctly with default installation and Gnome support for Samba.

4. Listen to music (I'd also add watch movies here)
Regarding my Bmpx problems, I can now listen to the music.

5. Word process
Yes, OpenOffice works. I used to use it under Windows, too.

6. Play silly games (Solitaire, Tetris)
I don't really do it, but I can ;-)

That's true. I'm a new Linux user. I need to learn how to solve some of the problems & workaround them. But...

I wanted to install Ubuntu for my father, so he can drop Windows. No luck. He used to have ATI problems, similar to mine. His TV card doesn't work very well, too. Either he can watch movies in MPlayer or TV. Not both with the same configuration, because of some incompatibilities. So, point 4 fails for him. And he is not very efficient Windows user, not mentioning Linux. Tough, he can do lot of Windows stuff by himself - he's not complete noob.

I wanted to install Ubuntu for my mother in law on her new laptop. That sound as a great idea to me. No viruses, no hang-ups. But now I'm really scared that I'll get into lot of problems. She is completely unfamiliar with computers & if she can't do all these simple things with no problems, she we'll really complain :-P

I've had lot of problems in ALL areas I touched in Ubuntu by myself. Development, Internet surfing, listening to music, watching movies (I had to drop MPlayer, cauz of ATI incompatibilities), etc. With some patches to the kernel (can't remember the link right now) Ubuntu finally stopped locking up every few mins.

Now, I'm thinking about trying out Mandriva, as Karellen stated. I've seen it already in the market & I've read, that they provide some customized drivers. But they say that the drivers some with paid version. The thing tough is - if I have to pay for Linux and fall into lot of problems with the other software, using Windows emulators (wine, Cedega etc.) why not just paying for Windows and getting rid of the problems? I'm already legal Windows user :-)

But I want to support Linux community. I want to start developing under Linux and make it better.

What interesting to me is, that I think this is the 3rd time when someone calls me a troll, because of the things I'm saying here. I find it to be new trolling itself. Someone is complaining that something doesn't work as designed? Call him a troll. He'll stop complaning. Is he giving some toughts about possible improvement areas? Call him a troll and he'll stop.

I'd really love if someone takes remote control over my box and helps me setting everything up. Maybe I'd be able to start developing and contributing better, than just compalining about all these different problems, which new Linux user/developer is potentially having. They are just driving me crazy some times...

---

### Post by DigitalAngel on 2008-06-05
> **Nexano said:**
> 
On my end, linux performance > windows by a long shot.


I'm with you.  I have a 2 year old "$500 Student Special" from Dell that was starting to show it's first signs of fatigue.  Now, it runs better than it ever has.

---

### Post by jocko on 2008-06-06
> **mlemanczyk said:**
> Jocko,
you are partially right. It's a valid situation, where a driver works on 1.x version, but doesn't on 2.x. That I can understand. But why it doesn't work when minor version change, e.g. from 2.6.x to 2.6.y or I should even say from 2.x to 2.y?

That's exactly what I'm trying to say & you confirmed. Some function got renamed, some got removed, some other works differently. This means, that the contract gets broken. This is true for many other Linux apps.

I believe, that once people realize they can not break the contract, you will go forward much faster.

What "contract" are you talking about? Linux is completely free, so it doesn't come with any "contract". If you don't like it, don't use it and quit complaining about things that can not be changed.
As I said: There is NO WAY to make a driver that works on all kernel versions, hardware drivers ALWAYS have to be compiled on the kernel they are intended to run on. This is true for every operating system, not just linux.
The only way to accomplish what you are asking for would be to completely stop developing linux.

If you are a linux user and decide that you don't want anything on your computer to change, you are completely free to NOT upgrade. If you're happy with one distro, then the choice is _yours_ to NOT install a different distro.

And why don't you accept that a driver that is compiled on linux 2.6.24 doesn't work on linux 2.4, but you accept that it doesn't work on linux 1.0?
That's like saying it's ok that something that is made for windows vista doesn't work in windows 3.11, but at the same time saying it's not ok that it's not working in windows 98.

---

### Post by Methuselah on 2008-06-08
Always having to maintain backwards compatibility ties your hands during the design phase and leads to bloat due to legacy interfaces. Why do you think Microsoft occasionally breaks things? The move from windows 9x to NT/Xp and from NT/Xp to Vista has broken so many drivers and applications from what I've read. 

I'm certain linux developers don't gratuitously break APIs but sometimes that's necessary to improve the system. Even more so than application programs, drivers access some intimate parts of the system that sometimes must be changed. The good news is that many linux drivers are open source so they can be updated to work with the new kernel. The bad news is that this is not an option for closed source drivers created by companies like NVidia. In this case, NVidia has to update the driver code itself. It will do this for hardware it still supports, otherwise you're out of luck whether you run windows or linux (ie if the OS changes in such a way that renders the driver useless).

Open source drivers would obviously fix this problem, making the hardware indefinitely supportable. However, I'm convinced some companies like being able to force you to buy new hardware because of their legacy drivers being incompatible with the OS you're running.

Thumbs up to AMD/ATI and intel for the efforts to create open source drivers! An NVidia card won't be infesting my machine any time soon.

---

### Post by karellen on 2008-06-08
in simple words: it's a vicious circle. oem don't release drivers for Linux because Linux has a very small (insignificant?!) market share so it's not worthy for them - and Linux's market share is so because people can't be convinced to switch if they are not certain that their hardware will be properly supported; I'm glad at least some big names  (Nvidia, Hp) release some drivers for their products

---

### Post by xjgnsdof on 2008-06-08
News flash: hardware isn't made for Linux!

The fact that most pre-built PCs are filled with crappy parts adds insult to that injury.

Linux runs damn near perfectly on my hardware, poorly on yours, and we use the same OS. Your problem with Linux lies in the hardware, not in the software. End of story.

---

### Post by Cifra on 2008-06-08
I don't care about being a Linux evangelist. I've been using Linux for many years now, anfd what people should be happy about is that there is a choice.

---

### Post by fhmanas on 2008-06-08
I don't understand why everybody is on this guy's case, I guess you are all reacting to the title of the post rather than what he was saying.  I agree the title may be a little out there, but he does have valid points.

I have been a long time user of Win as most of us even though you deny it.  And we should all agree that Windows did make it easy for a lot (don't burn me here, it's not 100% but a good margin) by making sure a lot of the drivers, hardware, interface work from the start since they made sure the Hardware Manufacturers fall in line with them or be left behind.

Now, linux does not have this luxury, and I do must give credit where credit is due, the developers has done a grand job in their progress of making the incompatible compatible.

But, as the original points out, linux (of any flavor) is not for the weak hearted and an average user will never go through the forums or google solutions, understand terms like samba, nfs, kernel.  They just want to plug and play.  

If you don't understand how this feels, you probably spend a substantial amount of time fiddling with computers as you won't understand the feeling of being helpless if the printer won't work or mouse won't move.  Let's face it, there are users like these and we should think of a solution for them as well.

---

### Post by Methuselah on 2008-06-08
> 
If you don't understand how this feels, you probably spend a substantial amount of time fiddling with computers as you won't understand the feeling of being helpless if the printer won't work or mouse won't move. Let's face it, there are users like these and we should think of a solution for them as well.


Or they should use windows if it is better for their purpose.
But they'll feel the same helplessness when these things happen under windows (and they sometimes do). 
Their attitude would probably be different though.

---

### Post by Keyper7 on 2008-06-08
> **fhmanas said:**
> I don't understand why everybody is on this guy's case, I guess you are all reacting to the title of the post rather than what he was saying. I agree the title may be a little out there, but he does have valid points.

Erm, most of the posts here were direct replies to what the OP said, most of the times even quoting him. The title is barely mentioned. What the hell are you talking about?

> **fhmanas said:**
> I have been a long time user of Win as most of us even though you deny it. And we should all agree that Windows did make it easy for a lot (don't burn me here, it's not 100% but a good margin) by making sure a lot of the drivers, hardware, interface work from the start since they made sure the Hardware Manufacturers fall in line with them or be left behind.

Ah yes, "support us or you're ******". Also known as monopoly. This is not exactly something I feel I should admire Microsoft for. And I'm not even saying this as a Linux user, not being able to find recent drivers for XP is also very annoying.

> **fhmanas said:**
> But, as the original points out, linux (of any flavor) is not for the weak hearted and an average user will never go through the forums or google solutions, understand terms like samba, nfs, kernel. They just want to plug and play.

And they usually have plug and play with Windows *as long as Windows is preinstalled*. Now ask your average user to install Windows from scratch and to compare the experience to start using a Dell with preinstalled Ubuntu.

> **fhmanas said:**
> If you don't understand how this feels, you probably spend a substantial amount of time fiddling with computers as you won't understand the feeling of being helpless if the printer won't work or mouse won't move. Let's face it, there are users like these and we should think of a solution for them as well.

And since when this is something related to Ubuntu or Linux? I just lost two days of my life trying to figure out why I had an error during the Vista SP1 install and that included installing Vista from scratch (PS: didn't work). I'd be more than happy if I could find anything *nearly* as efficient the Ubuntu Forums to solve this problem, but so far I didn't.

---

### Post by fhmanas on 2008-06-09
> **Keyper7 said:**
> 
Ah yes, "support us or you're ******". Also known as monopoly. This is not exactly something I feel I should admire Microsoft for. And I'm not even saying this as a Linux user, not being able to find recent drivers for XP is also very annoying.

I don't really like how this forced me as a user to choose Windows or not be part of the rest of the world.  But you must admit from the standpoint of Bill Gates, this leveraging is good for his company. He was just looking out for No. 1.  I would have probably done the same, if I was in his shoes.  There was a time Apple almost lost out by being defiant until it too was also forced to play the game when Bill Gates went in.  

I too am on the side of Linux, and it would be good for the community to help ensure it can compete with Windows and others as well, not only in tech but also in marketing the product.  Having a technically superior product does not guarantee success.

---

### Post by 3rdalbum on 2008-06-09
> **fhmanas said:**
> an average user will never go through the forums or google solutions, understand terms like samba, nfs, kernel.

My workmate uses Ubuntu. She probably knows even less about Samba, NFS and the kernel than you do.

Samba is just a name for the file sharing system, so I don't see why that is relevent. If you're setting up a home network, you *must* be able to know something about what you're doing. You can't say that home networking will never take off because nobody wants to know what a "router" or "Ethernet cable" is. Wireless networks are in use by many people, including my workmate, even though they have to learn words like "WPA" and "SSID".

Heck, when you buy a computer, you must learn what the things sitting on your desk are called.

As for looking for solutions on Google, that's true, they don't look. Whenever I get asked to fix someone's Windows computer, and it's a problem I haven't come across, I generally look at the Microsoft knowledgebase first. It always gives me a couple of extremely cryptic commands to put into the MS-DOS prompt that seem to be directly calling DLLs, I check everything's working again, collect my fee and leave.

If you don't want to help yourself, whether on Windows or Linux, you can always hire someone. And many people do.

> They just want to plug and play.

Ubuntu already sets up printers, internet connections, sound, graphics, and virtually *everything* when you boot up the live CD. No operating system shares files with your local network automatically, because that's a very bad thing for security.

Finally, the attitude of "I don't want to learn anything, I just want to plug and play!" is precisely the reason why viruses STILL exist and spread.

---

### Post by 3rdalbum on 2008-06-09
I'd also like to add that drivers distributed as source code will be able to work on (within reason) any kernel version. You install the kernel-headers package and compile the source code, and they will compile against the headers.

It's only when companies don't understand, and try distributing a closed-source binary that's been linked against one kernel version, do you really run into troubles. Some do. In fact, one company recently was so dumb it tried distributing an entire Linux kernel as their "driver"!

ATI and Nvidia drivers tend to work across kernel versions because the drivers are linked against some of their own obfuscated-source wrapper code, and that wrapper code will link against whatever kernel headers you have.

---

### Post by fhmanas on 2008-06-10
> 
Samba is just a name for the file sharing system, so I don't see why that is relevent. If you're setting up a home network, you *must* be able to know something about what you're doing. You can't say that home networking will never take off because nobody wants to know what a "router" or "Ethernet cable" is. Wireless networks are in use by many people, including my workmate, even though they have to learn words like "WPA" and "SSID".


I never said anything about home networking not taking off, I believe it has taken off.  All I was saying, was with Windows, if I wanted to share a folder with another Windows machine, I would just right-click folder, share the folder with or without the password, then I can share it with the rest.  In linux, it is not as simple as that, there are configurations to be made.  My point was a computer-illiterate person using a computer would not know the first thing to do if faced with that situation in linux.  Then, the solution is to go with Windows, but that's the point, linux should move towards making it easier for users to actually use it, and like I said also, I applaud the developers for doing a great job in moving towards that goal, especially with Ubuntu.



> 
Heck, when you buy a computer, you must learn what the things sitting on your desk are called.

Yes they would call it the computer, the "TV", the "thingamagig moving thingy", or they would know the actual terms, computer, monitor, mouse.  These are basic, but if you tell them, in order  to share files, you have configure your samba server, most likely they will look at you and say "huh" and do the Samba.  These are extreme cases but these kinds of people do exists.

> 
As for looking for solutions on Google, that's true, they don't look. Whenever I get asked to fix someone's Windows computer, and it's a problem I haven't come across, I generally look at the Microsoft knowledgebase first. It always gives me a couple of extremely cryptic commands to put into the MS-DOS prompt that seem to be directly calling DLLs, I check everything's working again, collect my fee and leave.

If you don't want to help yourself, whether on Windows or Linux, you can always hire someone. And many people do.

I agree, but you will end up frustrated if they annoy you with the most mundane problem they encounter especially if you are not getting paid.  



> Ubuntu already sets up printers, internet connections, sound, graphics, and virtually *everything* when you boot up the live CD. No operating system shares files with your local network automatically, because that's a very bad thing for security.

Again, I applaud the developers for doing this without the help of the manufacturers.  Damn you, manufacturers.

> Finally, the attitude of "I don't want to learn anything, I just want to plug and play!" is precisely the reason why viruses STILL exist and spread.

As we all know, viruses do abound which just goes to show you that there really are people out there who does not know any better.

---

### Post by chewearn on 2008-06-10
> **3rdalbum said:**
> I'd also like to add that drivers distributed as source code will be able to work on (within reason) any kernel version. You install the kernel-headers package and compile the source code, and they will compile against the headers.

*.edit.*

Indirectly adding to 3rdalbum post.


I read the entire thread and found no one has replied to the OP question about "contract" between manufacturers and kernel development, to maintain a stable API for driver development.

I seemed to recall reading somewhere that an unstable kernel API is intentional.  This is done to stop hardware manufacturer from distributing binary blob drivers, and instead of releasing the source codes (forcing GPL compliance).

Anyone with more knowledge in this; please correct me if I'm wrong.

---

### Post by gman2004 on 2008-06-10
I think all the answers to his questions are at:

[COLOR="Blue"]_[FONT="Verdana"][SIZE="4"]http://ubuntuforums.org/showthread.php?t=58017[/SIZE][/FONT]_[/COLOR]

---

### Post by RESID3NT on 2008-06-10
I can relate with some of your rant, like the media players and add some of my rants.

- X configuration for dual screen solutions always gives me some headaches.
- Sometimes sound starts to fail

other than that, your rants are simply on shaky grounds. Driver support is NOT from Linux/Ubuntu community(ies), but from the hardware vendors.

Tough luck for us :|

---

### Post by mdsmedia on 2008-06-10
> **RESID3NT said:**
> I can relate with some of your rant, like the media players and add some of my rants.

- X configuration for dual screen solutions always gives me some headaches.
- Sometimes sound starts to fail

other than that, your rants are simply on shaky grounds. Driver support is NOT from Linux/Ubuntu community(ies), but from the hardware vendors.

Tough luck for us :|I can only agree with this.

Most of the arguments of the OP are hardware related. Linux does a wonderful job of hardware support. It's not perfect, but to my way of thinking it's FAR better than Windows, out of the box.

Try installing Windows, then installing hardware drivers without the driver CDs provided by the hardware vendors.

MS doesn't provide the drivers for Windows. The hardware vendors do. Linux, on the other hand, supports MOST hardware out of the box, simply because hardware vendors don't provide Linux support.

---

### Post by mivo on 2008-06-10
> **mlemanczyk said:**
> I'm sorry to say that, but Linux is great for admins & server use. But for home users it's unfortunately useless...

Yes, it's so useless that I use it on my three computers for everything, home and professional use, including watching DVDs/videos and playing games in high resolution on a $350 video card. :) Sure, there are issues with some esoteric hardware, as any OS has them, but a blanket statement like the above is just trolling. And for a troll two minutes of my time is all I have to spare. ;)

---

### Post by mlemanczyk on 2008-06-13
At the beginning I'd like to thank you all for the discussion. It started to be really interesting. IMHO there are good points on both sides.

> **Methuselah said:**
> Always having to maintain backwards compatibility ties your hands during the design phase and leads to bloat due to legacy interfaces. Why do you think Microsoft occasionally breaks things? The move from windows 9x to NT/Xp and from NT/Xp to Vista has broken so many drivers and applications from what I've read.

(and rest of the post)

You'are right Methuselah. If you always keep the contract, you're tieying yourself to legacy code. This is definitely not best way.

You're also right about opening the drivers and maintaining closed drivers by vendors.

> **karellen said:**
> in simple words: it's a vicious circle. oem don't release drivers for Linux because Linux has a very small (insignificant?!) market share

(and the rest of the post)

I agree with you, Karellen.

> **fhmanas said:**
> Now, linux does not have this luxury, and I do must give credit where credit is due, the developers has done a grand job in their progress of making the incompatible compatible.

But, as the original points out, linux (of any flavor) is not for the weak hearted and an average user will never go through the forums or google solutions, understand terms like samba, nfs, kernel.  They just want to plug and play. (...) Let's face it, there are users like these and we should think of a solution for them as well.

That's right, Fhmanas. This is exactly my point. I'm really experienced Windows user and software developer. If I'm having so many problems with the software and solving the problems, I may expect average users to have even more.

On the other hand, they may have less, because they may not want to try doing things, which I'm doing.

Linux distros went really long way and changed a lot, since I started playing with it from time to time (starting with Red Hat 6.0). All of you hard working people need to get credits for it. Hats off.

> **fhmanas said:**
> 
I too am on the side of Linux, and it would be good for the community to help ensure it can compete with Windows and others as well, not only in tech but also in marketing the product.  Having a technically superior product does not guarantee success.

I agree.

> **fhmanas said:**
> Again, I applaud the developers for doing this without the help of the manufacturers.  Damn you, manufacturers.

As we all know, viruses do abound which just goes to show you that there really are people out there who does not know any better.

I agree with both parts :)

> **AstalaVista said:**
> I seemed to recall reading somewhere that an unstable kernel API is intentional.  This is done to stop hardware manufacturer from distributing binary blob drivers, and instead of releasing the source codes (forcing GPL compliance).

Anyone with more knowledge in this; please correct me if I'm wrong.

This is really interesting! Is this true? I'm wondering, if that could be the case. Does anyone have any stats, how many vendors published their source codes to get community help in maintaining the drivers? If this was the reason and/or it doesn't work, maybe it's better to stabilize kernel API & get vendors help to write the drivers?

> **mdsmedia said:**
> I can only agree with this.

Most of the arguments of the OP are hardware related. Linux does a wonderful job of hardware support. It's not perfect, but to my way of thinking it's FAR better than Windows, out of the box.

Try installing Windows, then installing hardware drivers without the driver CDs provided by the hardware vendors.

MS doesn't provide the drivers for Windows. The hardware vendors do. Linux, on the other hand, supports MOST hardware out of the box, simply because hardware vendors don't provide Linux support.

That's partially true. MS provides many generic drivers, not very optimized for the software. But that's right, vendors do provide drivers for Linux.


I'll summarize what I'm thinking right now.

1) I'm starting with Linux, but it seems that its kernel is changing much faster, than the one on Windows. My guess is, that hardware vendors don't like to publish their source codes. For this reason it may be (may not?) a good idea to stabilize the API and change it with long time notice in advance - create distribution list with planned API changes for hardware vendors? I think, that in addition kernel API changes should be made between major version mostly, i.e. 1.x vs 2.x vs 3.x.

Let me give you example from my experience. I'm using IPCop over VMware. Of course, people may say that I should not be doing this. But that's beyond the scope of this discussion. That's the route I took. Now, the latest IPCop release is 1.4.18. Unfortunately, it comes with no VMware Tools drivers and I can't find them anywhere. Also, there is no apt-get under it, so I can't install gcc/make and compile the drivers from VMware. I tried to download IPCop sources on Ubuntu 8.04 Jeos, compile & try to add the VMware Tools drivers myself. Unfortunately it didn't compile. IPCop 2.0 didn't, too. Now we come to the next point.

2) API changes in apps & libraries seem to be root reason for all my compatibility problems. My guess is that many of the "Linux" work goes into keeping apps up with the libs and compilers.

E.g. IPCop didn't compile on my box on Ubuntu 8.04 Jeos (seems that I installed all required libs). I couldn't debug with KDevelop. Couldn't compile VMware Tools drivers on different kernels, without specific patches.

Maybe it'd be a good idea to keep app/lib APIs stable, add new ones, mark old ones with deprecated (with timestamp) and remove it after the deprecation date. I've seen some "deprecated" warnings when I was compiling something, so some people are doing something like this.

That way, developers could concentrate more on improving their software, instead of worrying about and keeping up with changed APIs. If they compile vs deprecated functions, they will have long time to adjust the app/lib to new functions.

3) I think I don't exactly get your point about drivers incompatibility between kernel version. From what I know, Linux drivers can be loaded into the kernel as modules. My understanding is, that module API remains mostly the same (how many required changes can there be?). Then, if driver is loaded into kernel as a module (I think it's similar to Windows), why would it need to recompile, if kernel module's API remains the same?

My understanding of a kernel is, that it provides basic (really basic) functions. For accessing files, pipes, allocating memory and so on. Also, some basic functionality for hardware etc. My impression is, that such a basic functionality can't (shouldn't) change very often - only between major releases.

If this is the case, then a compiled driver would work between e.g. all 2.x.y kernel versions, if it's loaded as a module.



I think there are specific benefits of both points.
1) it may be easier to get vendors involved into writing drivers for their software. 
2) it may be easier to track all old functions/structures. All of them will be marked as deprecated with time line
3) there can be tools to remove code marked as deprecated. The code may be surrounded with deprecated marks (like #regions in C#)
4) long enough deprecated timeline will give enough transitional time for developers, while still removing legacy code
5) it may eliminate the need to recompile drivers over and over
6) concentrating on software functions/hardware instead of compatibility issue can speed up Linux in its way

As I already stated, I don't know how changes to kernel/apps/libs in Linux are introduced. It may already work like this. Unfortunately it doesn't seem to for me.

If it's not, then I think that doing something like this will improve the way Linux is going forward and will speed it up.

What do you think?

---

### Post by aysiu on 2008-06-13
> **mlemanczyk said:**
> That's right, Fhmanas. This is exactly my point. I'm really experienced Windows user and software developer. If I'm having so many problems with the software and solving the problems, I may expect average users to have even more.

On the other hand, they may have less, because they may not want to try doing things, which I'm doing. They'll also have less because they'll most likely try Linux only if A) it comes preinstalled and preconfigured on a computer they purchased or B) a Linux geek installs and configures it for them.

No "average user" is going to back up Windows, download Ubuntu, do a checksum on the .iso, burn it as a disk image, set the BIOS to boot from CD, repartition the hard drive, install Ubuntu, troubleshoot potential hardware incompatibilities, install multimedia codecs, and learn a new operating system themselves.

If they do that, they're immediately out of the "average user" category and into the "power user" category.

I bought an Eee PC with Linux preinstalled and *everything* worked out of the box. All the codecs were installed. Screen resolution, Skype video chat, sound, hotkeys, sleep, etc. all worked. Guess why. Because I bought it preinstalled. That's what "average users" do with their Windows computers, and that's what they'll do if they ever get into Linux.

For more details, read [I don’t know about “the desktop,” but Linux appears to be ready for the ultra-mobile PC](http://ubuntucat.wordpress.com/2008/03/15/i-dont-know-about-the-desktop-but-linux-appears-to-be-ready-for-the-ultra-mobile-pc/)

---

### Post by mlemanczyk on 2008-06-13
> **mivo said:**
> Yes, it's so useless that I use it on my three computers for everything, home and professional use, including watching DVDs/videos and playing games in high resolution on a $350 video card. :) Sure, there are issues with some esoteric hardware, as any OS has them, but a blanket statement like the above is just trolling. And for a troll two minutes of my time is all I have to spare. ;)

When I mentioned home users (home use) at the beginning, I meant many (most?) of the users, who don't really know computers and can do very basic operations, only. They don't know what terminal is, what terminal command is, what compilation means etc. Is Linux for them? I don't think so. Just because I express my opinion, I am trolling?

According to Wikipedia:
> 
An Internet troll, or simply troll in Internet slang, is someone who posts controversial and usually irrelevant or off-topic messages in an online community, such as an online discussion forum or chat room, with the intention of baiting other users into an emotional response[1] or to generally disrupt normal on-topic discussion.

(...)

The term troll is highly subjective. Some readers may characterize a post as trolling, while others may regard the same post as a legitimate contribution to the discussion, even if controversial. The term is often used to discredit an opposing position, or its proponent, by argument fallacy ad hominem.

Often, calling someone a troll makes assumptions about a writer's motives. Regardless of the circumstances, controversial posts may attract a particularly strong response from those unfamiliar with the robust dialogue found in some online, rather than physical, communities. Experienced participants in online forums know that the most effective way to discourage a troll is usually to ignore him or her, because responding tends to encourage trolls to continue disruptive posts &#8212; hence the often-seen warning: "Please do not feed the trolls".[9]

Frequently, someone who has been labelled a troll by a group may seek to redeem their reputation by discrediting their opponents, for example by claiming that other members of the group are closed-minded, conspirators, or trolls themselves.

Am I posting "irrelevant or off-topic" posts? I don't think so. I made my own topic on a subject, which I find important.

Have I made the topic & left? I didn't. I'm trying to be constructive and try to give some ideas on the problems I find important for Linux community, based on my experience with it.

Am I trying to discredit people with different opinions? I don't.

Am I going all over the different web pages saying how bad Linux is? No. I'm using Ubuntu and that's the only place I came to. Was there a better place to go & start the discussion? I don't know. I don't know Linux community too good, yet.

Then, am I troll? If so, please delete this topic.


P.S. I agree with you, Aysiu :)

---

### Post by Afkpuz on 2008-06-13
What I love to see is when someone can't get linux to work on their hardware and assumes that all users everywhere are experiencing this.  Not so.  But I hear your frustration OP.  I wish you could see what a flawless installation feels like with ubuntu.  it's a beautiful thing.

---

### Post by mivo on 2008-06-13
> **mlemanczyk said:**
> Just because I express my opinion, I am trolling?

You didn't merely express your opinion, you made rather harsh blanket statements, like Linux being "useless" for home users, and that it has "not progressed in the past ten years" (where have you been?), etc. Those weren't constructive statements, and considering your post count, they were bound to make you look like a troll. I'm not saying that Linux is perfect or that there are no issues, or that expressing criticism is in any way unwanted (I frequently post here defending people who get jumped on when they are frustrated), but I could install Ubuntu on my mother's computer (she's in her sixties), and she'd not have any problem using it -- it's far more than "just a server OS for geeks and admins". I had people look at my computer and not even realize that it wasn't Windows. Sure, it isn't for everyone's hardware, and there are issues in the audio and wireless area, but "useless"? 

Not to mention that these forums here are the best source for help I have ever seen in over twenty years of using computers. If you are an average home user and you have an Ubuntu-related trouble (heck, *any* IT trouble! :)), you'll get hands-on help here. If your Windows messes up, you'll pay through your nose or jump through support hoops. That, too, is part of the Linux experience.

---

### Post by chewearn on 2008-06-13
> **mlemanczyk said:**
> 
..edit..

This is really interesting! Is this true? I'm wondering, if that could be the case. 

..edit..

3) I think I don't exactly get your point about drivers incompatibility between kernel version. From what I know, Linux drivers can be loaded into the kernel as modules. My understanding is, that module API remains mostly the same (how many required changes can there be?). Then, if driver is loaded into kernel as a module (I think it's similar to Windows), why would it need to recompile, if kernel module's API remains the same?

My understanding of a kernel is, that it provides basic (really basic) functions. For accessing files, pipes, allocating memory and so on. Also, some basic functionality for hardware etc. My impression is, that such a basic functionality can't (shouldn't) change very often - only between major releases.

If this is the case, then a compiled driver would work between e.g. all 2.x.y kernel versions, if it's loaded as a module.

..edit..


Ok, I dig some more, here is an interesting read, which should answer some of your questions:
[http://www.linuxdevcenter.com/pub/a/linux/2004/09/02/driver_ease.html](http://www.linuxdevcenter.com/pub/a/linux/2004/09/02/driver_ease.html)

Here is an interview with Linus Torvalds (do a search for "ABI"):
[http://linux-foundation.org/weblogs/openvoices/linus-torvalds-part-i/](http://linux-foundation.org/weblogs/openvoices/linus-torvalds-part-i/)

.

---

### Post by crane on 2008-06-14
One thing to note here. Most people compare Linux(new install) to XP or Vista (Preinstalled, setup, and configured).
If you do a true comparison you will find configuring Windows a little harder.
Take a box that someone gave you and install windows. then try to find out what version of what hardware is installed so you can find and install the drivers. Setting up a windows box from scratch can take hours sometimes.

 Best of luck getting your bugs worked out. I have to run Ubuntu at work now because my new computer (Vista or WimdowsME2 LOL) does not support most of the printers in my office.

---

### Post by Vince4Amy on 2008-06-14
>  I'll watch your steps :wink: But for now, I'll disrecommend Linux to all home users. It's not for them. It's for servers, where graphics performance is not important, there is no need for TV cards, cameras etc. I've 2-3 Linux VM running successfully as server versions, without any GUI.

I'm sorry to say that, but Linux is great for admins & server use. But for home users it's unfortunately useless & the situation didn't change at least since 10 years.To be fair, why don't you try using a different distribution, rather than ditching "Linux" because of Ubuntu. Although some of your problems were with the kernel they probably were due to packages or drivers which you were using.

Also I use both Windows & OpenSUSE and I think they're both great OS's however Windows Vista does take longer to configure than OpenSUSE.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-15
Personally, I think this thread should be LOCKED DOWN by the moderators (where are you?!) as a thread that will lead into a big fight whether Linux is bad or not.

---

### Post by mivo on 2008-06-15
While they are here, they could also fix your name, because it seriously screws up the layout of every thread you post in. :D

---

### Post by fiddledd on 2008-06-15
> **mivo said:**
> While they are here, they could also fix your name, because it seriously screws up the layout of every thread you post in. :D

I'll second that. :)

---

### Post by mlemanczyk on 2008-06-21
I'll answer separately to your posts.

> **mivo said:**
> You didn't merely express your opinion, you made rather harsh blanket statements, like Linux being "useless" for home users, and that it has "not progressed in the past ten years" (where have you been?), etc. Those weren't constructive statements, and considering your post count, they were bound to make you look like a troll. I'm not saying that Linux is perfect or that there are no issues, or that expressing criticism is in any way unwanted (I frequently post here defending people who get jumped on when they are frustrated), but I could install Ubuntu on my mother's computer (she's in her sixties), and she'd not have any problem using it -- it's far more than "just a server OS for geeks and admins". I had people look at my computer and not even realize that it wasn't Windows. Sure, it isn't for everyone's hardware, and there are issues in the audio and wireless area, but "useless"?

Let me explain, how I came to the conclusion, that Linux didn't make progress. Of course, it did. I can see it. It looks much nicer and there are much more easy to use apps (especially for configuration). That's a right direction IMHO.

But... IMHO main Linux problem is not solved over years. What is my understanding of the main problem? It doesn't matter, RedHat 6.0 - Ubuntu 8.04, Linux users need to do over and over the same. They need to Google to find solutions to their problems.

Since I started using Ubuntu Desktop 7-8 like 2 months ago, I had problems and complications in EVERY area I played with. EVERY single one:

[LIST=1]
[*]moving files. Turned out that there is a bug in BSC commander. It didn't copied 20GB from one to another disk, but it recognized it as moved and deleted original file. I spent 2 days on restoring my Zimbra data from backups.

[*]it turned out that there is, let say, deficiency in RSnapshot and it was not running backups for the last 3 months, because a TAB char was missed in config file. A TAB char after folder path to backup. Nothing less, nothing more after it. It didn't recognize, that I want to create the backup in main backup path, given as variable at the beginning.

[*]playing music in BMPx (Ubuntu 7.10) - didn't get it to work with AAC streams. Ubuntu 8.04 installation solved this problem.

[*]it turned out 1h ago, that there is a bug in Gnome-Commander & I lost my source codes on the hard drive. Luckily, most of them are in SVN or in a backup copy. Basically, turn on File Roller plugin. Right click a zip file, choose to unzip to current folder. After unzipping, still the same zip file is selected. Press DEL - it will delete random item from the folder.

[*]GVS (not sure, if that's the right name for Gnome virtual file system) - wasn't working well with Samba Share from WinXP Pro Server & F-Spot. I had to Google & learn how to mount with fstab.

[*]Remote logging to another box. So far it worked only once. In all other cases Gnome login screen disappears and blank screen remains with blinking cursor on it

[*]My Plustek Scanner was either not recognized or just wasn't working, until I Googled, downloaded & installed original Windows firmware

[*]VMware Tools on guest Ubuntu systems always (I believe it was always for me) require some patches and Googling

[*]PDF printing doesn't work right from Acrobat Reader with HP 5740. Sometimes the printing is completely messed up. I found out it's the same, when you print to PDF printer and the solution is to CHECK option for fast printing. This bug was found by my wife and she wouldn't solve it herself.

[*]KDevelop + QTDevelop + Kdebug was unable to debug on clean install. I didn't solve this problem.

[*]MonoDevelop is crashing with no error msgs with very simple (one form, few buttons) test project

[*]MPlayer didn't work with ATI card, so I couldn't use my favorite Linux player

[*]Desktop Effects are not compatible with ATI. Sometimes something gets broken in graphics configuration. It looses settings and requires graphic card driver reinstallation. I experienced this with ATI and with NVidia today.

[*]Many web pages containing TRUE movies doesn't work in Ubuntu (e.g. [www.onet.tv](www.onet.tv)). On Windows these are played with WMP. I managed to workaround some of the problems, so onet.tv can at least open, but most videos are not playing. DRM technology doesn't seem to be handled right and I could neither buy NBA finals online nor watch Euro 2008 online.

[*]I spent a day already trying to share my scanner over network (using SANE), so I can drop Desktop edition and switch to Server. So far it doesn't work.

[*]No voice/video support for GTalk in Pidgin which is installed by default. Needs to be workarounded.
[/LIST]
I tried to show some of the problems from different areas. But there are TONS more, which I had. Usually I was able to sooner or later (usually) work them out.

Last days my friend, after my initial recommendation month ago, installed Ubuntu 8.04. But then he couldn't even install Skype himself, because of AMD64 (he installed 32-bit Ubuntu version). We managed together to find a solution to this problem and get it to install. But now, his camera view is upside down. We didn't solve this problem, yet.

Not mentioning all other hardware problems and 8.04 locking up. Am I the only one, who is/was using ATI card (I changed to NVidia)? Was I the only one using SB Live 24, PixelView TV Pack, Plustek Scanners. Was I the only one trying to do all the things? I can bet, I'm not & I can assume other (not all) people will/do have problems with it.

So far I've tried Ubuntu 8.04 on 4 completely different computers and everywhere were problems with hardware support. I'm experienced computer user, who can Google (but doesn't want to) and try to find the right solution. What'd my father, wife, mother-in-law, friend do?

Finally we came to the conclusion. I installed Ubuntu 7.10 & then 8.04 after a recommendation from my friend, who likes Googling and can solve most of his problems. I was really surprised, with how it looks and has some new features. But I was completely trashed when I started using it and fault into all these different problems, I had similar 10 years ago. I just couldn't believe, that for all these years these problems didn't go away and the community didn't come with a solution.

In addition, Linux stability turned out to be real myth, since it was locking up every few mins. After solving the lockup, I can't remember how many times I already had to use CTRL+ALT+BACKSPACE, because Gnome stops responding to keyboar/mouse. 

So, my "harsh blanket statements" comes from (not much due to all the problems) experience when I was giving a chance to Linux & it was always failing the try.

Now, these are 2 months of using 8.04 Desktop version. I never used it so long in a raw. I'm still fighting and trying to install it the way, I had on XP in a day. I'm slowly getting to a point, where I was with XP, but some times I just thing... my old good XP.

At the time I created this topic I was really angry with the lockups and wanted to go back. But I decided to give it one more chance and try to pass through. Now I'm in trouble with my wife, cause all the long time I'm spending trying to get it to work right ;-)

I believe that I'm not the only one having all the problems. I also believe, that we/you (the community) should come with a real solution, to answer them. For me, this is really huge waste of time, if many people need to go over and over same/similar problems again. This time can be used for something else, instead of solving Linux problem. Maybe contributing. I don't want to say Ubuntu - I believe it's a common problem.

> **mivo said:**
> Not to mention that these forums here are the best source for help I have ever seen in over twenty years of using computers. If you are an average home user and you have an Ubuntu-related trouble (heck, *any* IT trouble! :)), you'll get hands-on help here. If your Windows messes up, you'll pay through your nose or jump through support hoops. That, too, is part of the Linux experience.

Yeah, I'm doing my best and Googling daily, to find a solution for something :-)

---

### Post by starcannon on 2008-06-21
Our family of 4 has been using Ubuntu Linux exclusively for 5+ years.

My wife and I are both returning college students.

I have 10 and 12 year old kids who use it for their school, email, and daily activities as well as games.

If this scenario does not have "ready for prime time" written all over it I don't know what does.

I have also bought my mother a 1420n from Dell that shipped with Ubuntu pre-installed. I put Xubuntu on a jurrassic ware laptop that I then gave to my grandmother (my kids great grandmother). I did a remote install on my Dads computer. And gave another jarrassic ware laptop sporting Fluxbuntu to a family in my community. I installed Ubuntu 7.10 on a clients machine, she is very happy. I installed 7.10 on a next door neighbors aging desktop, he is happy as well.

I would say that Ubuntu is no different install wise than any other OS, installing an Operating System is NOT for the average end-user. Try putting OSX on a PC, it can be done, it is done, but not by the average end user. Read the endless string of windows how to's its not immune either.

If your not a system installer, then pay someone who is to take care of it for you. I drive cars, I pay mechanics to fix them.

GL

---

### Post by mlemanczyk on 2008-06-21
> **starcannon said:**
> Our family of 4 has been using Ubuntu Linux exclusively for 5+ years.

My wife and I are both returning college students.

I have 10 and 12 year old kids who use it for their school, email, and daily activities as well as games.

If this scenario does not have "ready for prime time" written all over it I don't know what does.

I have also bought my mother a 1420n from Dell that shipped with Ubuntu pre-installed. I put Xubuntu on a jurrassic ware laptop that I then gave to my grandmother (my kids great grandmother). I did a remote install on my Dads computer. And gave another jarrassic ware laptop sporting Fluxbuntu to a family in my community. I installed Ubuntu 7.10 on a clients machine, she is very happy. I installed 7.10 on a next door neighbors aging desktop, he is happy as well.

Yeah, there are things, which are finally working for me. But on case by case basis I'm finding, that some others doesn't work as expected. I'd say my laptop is pretty configured. I realized, that some thing just won't work until they get fixed/implemented and decided to live with it. It could be, that it's hardware specific. Some are happy, some are not :-) If my father can't watch movies and TV with the same configuration, he will switch back to Windows. If my friend won't get camera to work with Skype right, he will switch back.

> **starcannon said:**
> I would say that Ubuntu is no different install wise than any other OS, installing an Operating System is NOT for the average end-user. Try putting OSX on a PC, it can be done, it is done, but not by the average end user. Read the endless string of windows how to's its not immune either.

Yes, I agree. But I'm not average user. I started with DOS. Unfortunately, I've never had so many problems with OS, as with Linux.

> **starcannon said:**
> If your not a system installer, then pay someone who is to take care of it for you. I drive cars, I pay mechanics to fix them.

I don't think this is really in the spirit of Linux community. If I have to pay someone to spend a week and configure everything, why don't I just buy Windows and get rid of the problems right away? That's hypothetic, I already own Windows, but I'd like to switch to Linux. I guess I just like some of its features & if I switch back, I'd have to look for these programs (like KMyMoney, BMPx, apt etc.) 8)

---

### Post by chewearn on 2008-06-21
> **mlemanczyk said:**
> Let me explain, how I came to the conclusion, that Linux didn't make progress. Of course, it did. I can see it. It looks much nicer and there are much more easy to use apps (especially for configuration). That's a right direction IMHO.

*edit*


Linux, being a community driven effort, requires participations to drive the direction to a certain point/objective.

I am against and/or neutral about what your proposals in the first thread, briefly summarized as:
1) wasting resources on reinventing the wheel
2) NO BACKWARD COMPATIBILITY
3) provide driver model
4) Concentrate on the performance & write good drivers.
5) don't release BETA software all the time.

Some of the points are unworkable, e.g. you can't stop people who want to go a different direction/reinvent the wheel so to speak.

Some, like backward compatibility and driver model, have been ruled out by the top drivers of the linux community.  Basically, the head honchos say, and we follow.

Of course, nobody is stopping you from taking the entire linux kernel codes and fork a different direction, with you in-charge, and making sure the driver model is not changed.

You see, your complaints are not entirely baseless, and they were recurring problems *for you *that remains unsolved since ten years ago.  Emphasis, *for you*, and perhaps a small number of others.

Nothing is perfect as you want it to be, but to many of us, it's as perfect as it gets, much better *than the other OSes*.

.

---

### Post by starcannon on 2008-06-21
> **mlemanczyk said:**
> Yeah, there are things, which are finally working for me. But on case by case basis I'm finding, that some others doesn't work as expected. I'd say my laptop is pretty configured. I realized, that some thing just won't work until they get fixed/implemented and decided to live with it. It could be, that it's hardware specific. Some are happy, some are not :-) If my father can't watch movies and TV with the same configuration, he will switch back to Windows. If my friend won't get camera to work with Skype right, he will switch back.



Yes, I agree. But I'm not average user. I started with DOS. Unfortunately, I've never had so many problems with OS, as with Linux.



I don't think this is really in the spirit of Linux community. If I have to pay someone to spend a week and configure everything, why don't I just buy Windows and get rid of the problems right away? That's hypothetic, I already own Windows, but I'd like to switch to Linux. I guess I just like some of its features & if I switch back, I'd have to look for these programs (like KMyMoney, BMPx, apt etc.) 8)

Of course everyones mileage may vary, I'd expect that if you've been with MS since DOS then its likely that your very good at making windows work, the way things work in linux is not going to be the same. Think it takes me about 2 hours on an unfamiliar system with an oddball vid card /shrug, doesn't take me a week though, I charge clients $75 first hour, $50 each additional, doubt I'd have any clients left if I hit them for a weeks bill on a single install.

As for "the spirit of the linux community" I wouldn't know, I just know how I deal with things, I do help as much as I can in the forums and try to be a solid community member. But I don't expect that everyone that downloads a LiveCD will have the knowledge, nor the desire to aquire the knowledge to make it go. Free in linux can mean beer, but I generally take it to mean speech, of course everyone is entitled to interprate the word "free" as they see fit, I will say on the "free beer" side of things, I have a sports car in my driveway, I'm currently saving up $6000 for a new high performance motor, but if someone just gave me the motor, I'd still pay a professional to install it for me. 

Anyway, its Linux, use it or not as best suits your needs, and most important, enjoy it, it really is a fun OS after the work day is done.

GL

---

### Post by mlemanczyk on 2008-06-21
> **AstalaVista said:**
> You see, your complaints are not entirely baseless, and they were recurring problems *for you *that remains unsolved since ten years ago.  Emphasis, *for you*, and perhaps a small number of others.

AstaLavista, I'll answer to this part only, since I'm heading to bed already.

I'm sorry to say that, but it always makes me funny, when people on Linux forums answer, that you (complaining person) and probably a very small amount of people are experiencing these problems.

With a Linux market share varying from 0.6-2% it's not very good, if people who give Linux a try hear, that these problems won't get fixed, are not critical (e.g. lockups), since only few people are experiencing them, "that's a planned feature" (e.g. incompatibility) or (regular developer's answer ;-) ) "it works for me" :mrgreen:

P.S. I have an idea, which may help a little with the compatibility problems, but will write it tomorrow. Maybe the community is already doing this, we'll see.

---

### Post by chewearn on 2008-06-21
> **mlemanczyk said:**
> I'm sorry to say that, but it always makes me funny, when people on Linux forums answer, that you (complaining person) and probably a very small amount of people are experiencing these problems.


That's the way of the world, my friend.  We can't solve everything, so we create a pareto, and take care of top 95%.  You can't escape this simple rule, even with Linux.

---

### Post by karellen on 2008-06-21
> **mlemanczyk said:**
> 

At the time I created this topic I was really angry with the lockups and wanted to go back. But I decided to give it one more chance and try to pass through. Now I'm in trouble with my wife, cause all the long time I'm spending trying to get it to work right ;-)

I believe that I'm not the only one having all the problems. I also believe, that we/you (the community) should come with a real solution, to answer them. For me, this is really huge waste of time, if many people need to go over and over same/similar problems again. This time can be used for something else, instead of solving Linux problem. Maybe contributing. I don't want to say Ubuntu - I believe it's a common problem.



Yeah, I'm doing my best and Googling daily, to find a solution for something :-)

the purpose of an OS is to help to use your hardware and to be proficient in what you do with your PC. it's not a purpose per se. if you feel it's a waste of time, switch to something else which requires less fiddling.
just my 0.02$

---

### Post by Keyper7 on 2008-06-21
> **mlemanczyk said:**
> So, my "harsh blanket statements" comes from (not much due to all the problems) experience when I was giving a chance to Linux & it was always failing the try.

You're making assumptions and jumping to conclusions about Linux *as a whole* based on *specific* experiences from *specific* people with *specific* versions of a *specific* distro installed on a *specific* hardware.

That's "harsh blanked statements" in my dictionary. Just like it would be a "fanboy statement" if I said that Linux is obviously ready for everyone because I had a perfect experience with Hardy (and I did have one).

For each bad experience you had, I can mention a good experience I had.

For each hardware that didn't work for you, I can mention a hardware that worked out of the box for me.

For each thing you point that Windows does better for you, I can point a thing that Ubuntu does better for me.

Your problems do exist and your frustration is reasonable. What you're doing wrong is *generalizing*. What you are doing is no different than saying "Well, blond people are usually nice, but what I don't like about them is that they are theives. I was robbed by a blond guy once."

---

### Post by karellen on 2008-06-21
overall, hardware related, Linux is still unpredictable and behind Windows and Mac OS X. and yes, I know that the Linux kernel supports way more hardware configurations out of the box than XP, Vista or Mac OS X. but that's not the point - the point being that it's easier to get the Windows (or Mac OS X, though it's less supported) driver for virtually every new or fairly new piece of hardware/device/gadget. the OEM provide these drivers for the commercial OSs platforms. that's not Linux's fault, everybody knows that, but it remains and indisputable fact. taking all these in consideration, no wonder users experiences with Linux are slippery and often frustrating

---

### Post by aysiu on 2008-06-21
While what you're saying is true, karellen, people still need to phrase their observations correctly. It isn't "Linux sucks, because it's difficult to get my hardware working with Linux." It's "It's difficult to get my hardware working with Linux, because Linux isn't a popular consumer operating system yet."

Frankly, Mac suffers from a lot of the same issues Linux does. My wife and I had quite a time of it getting her parents' Canon printer trying to get it to work with the Mac Mini we got them, and eventually we gave up on it. IEs4Linux works better in Linux than on Intel Macs, so my in-laws ended up giving up on the Mac, because they needed an IE-only website (yes, not even User Agent Switcher did the trick).

They went back to Windows, and we re-gifted the Mac Mini.

Does that mean Mac isn't ready for average users yet or that it's Apple's fault that Canon doesn't work well with CUPS or certain real estate-related websites won't play nice with Safari and Firefox? No. It's ridiculous to think that market forces will work in favor of the minority players in the market.

---

### Post by karellen on 2008-06-22
> **aysiu said:**
> While what you're saying is true, karellen, people still need to phrase their observations correctly. It isn't "Linux sucks, because it's difficult to get my hardware working with Linux." It's "It's difficult to get my hardware working with Linux, because Linux isn't a popular consumer operating system yet."

Frankly, Mac suffers from a lot of the same issues Linux does. My wife and I had quite a time of it getting her parents' Canon printer trying to get it to work with the Mac Mini we got them, and eventually we gave up on it. IEs4Linux works better in Linux than on Intel Macs, so my in-laws ended up giving up on the Mac, because they needed an IE-only website (yes, not even User Agent Switcher did the trick).

They went back to Windows, and we re-gifted the Mac Mini.

Does that mean Mac isn't ready for average users yet or that it's Apple's fault that Canon doesn't work well with CUPS or certain real estate-related websites won't play nice with Safari and Firefox? No. It's ridiculous to think that market forces will work in favor of the minority players in the market.

I agree with you, I've never said "Linux sucks" and I try to be moderate in my judgments - because every OS "sucks" in a way or another, perfection has nothing to do with it. if there is something that I hate, that would be generalizations, simplifications and zealotry. I try be as tech savvy as possible and enjoy everything that has to do with IT.
admittedly, I've never personally used a Mac, but in the near future I think this "deficiency" will be corrected :)

---

### Post by chewearn on 2008-06-22
> **karellen said:**
> admittedly, I've never personally used a Mac, but in the near future I think this "deficiency" will be corrected :)


Come on, man!  After complaining multiple times how expensive Mac are, you are still hoping someday that Apple will overcharge you? :wink:

.

---

### Post by karellen on 2008-06-22
> **AstalaVista said:**
> Come on, man!  After complaining multiple times how expensive Mac are, you are still hoping someday that Apple will overcharge you? :wink:

.

:lolflag: well who knows, maybe I'll get rich ;)...I try to keep an open mind anyway :D

---

### Post by benthegreat on 2008-06-22
I have to say, i agree to some extent with the author. Ubuntu's graphical performance is dire, although this won't cause problems for normal use, noone strains their GPU while watching a video on youtube, to compete with windows at all ubuntu needs to start at least being able to take games (not tux racer), proper games.

This may seem immature at first, but it really is the only reason I keep windows, for games. Sure Ill grow out of it, but by not developing a decent solution, ubuntu is cutting out an entire generation of computer geeks and nerds (im proud to be one), that want an alternative OS.

Also, as secure as linux in general is, I cant help but feel ubuntu gets more "flimsy" each time it's updated. And I know one of the beauties of linux is it's "openness". but without compatibility we're going nowhere.


On the other hand, one of the main overriding reasons i love ubuntu, is because im able to investigate and fix problems myself, because there's no part of the system you cant get at easily, unlike windowz. With each fix comes a feeling of achievement and pride; "i dont need external help, i can fix my own system". I owe a lot to ubuntu, it has taught me, by breaking, how computers actually function, without the heavy veiling M$ does. If it didnt break, well that'd riun my fun!!!

---

### Post by Canis familiaris on 2008-06-22
> **jimv said:**
> Linux IS NOT:

For servers
For the desktop
For new users
For experienced users
For your mom

It's for whoever wants to use it.  End of story.  If it doesn't work for you, well, oh well.  This isn't a business endeavor.  No one is losing any money if you decide to go back to Windows.  Thanks for being part of the community.
Exactly!

---

### Post by mivo on 2008-06-22
> **benthegreat said:**
> I have to say, i agree to some extent with the author. Ubuntu's graphical performance is dire, although this won't cause problems for normal use, noone strains their GPU while watching a video on youtube, to compete with windows at all ubuntu needs to start at least being able to take games (not tux racer), proper games.

Strange. I can play Quake Wars with full details on 1680x1050 without performance issues, and it's a new'ish, graphics-intense, commercial game that's quite heavy on the video system. Perhaps you just don't have a good enough graphics card for high-end games? Which native Linux game is giving you trouble?

---

### Post by quinnten83 on 2008-06-22
I'm just wondering if the original author has posted a bug report on launchpad.
Also I think the problem comes down to expectations; he expected fireworks, and Ubuntu didn't deliver. But then again, we never promised fireworks.
It's a shame he has so many problems with his hardware, but if he is as "techie" as he sounds, he might have really disparaging hardware configurations.

---

### Post by mjp216 on 2008-06-22
i didnt read the whole thing but all i have to say is if Linux had broad support, hefty donations, and some good PR, it isnt the smallest doubt in my mind that it would be the best, most widely used OS ever implemented to the computer world, and it would most certainly destroy the cooperate monopoly that Microsoft, so undeserving, holds in its poorly structured, money hungry hands.

---

### Post by Julian Lewis on 2008-06-23
The tricky bit is the installation. You need to be a bit of a geek to do that, but then once properly installed Ubuntu pisses all over windows and on Macs. On average I find Ubuntu to be at least twice as fast as XP on the same machine. Once I finally managed to get my daughters dual boot lap top up and running, she took to it like a duck to water (7.10 I will take it to 8.04). PS, the windows partition has been bot-net-ised, and is now completely useless, in general windows is unusable its insecure, slow, and restrictive. The major reason for the existence of windows seems to be to keep the flies off the rest of us. The more people use Vista and XP the less we will get bothered. Son forn those who want to go back... bye bye

---

### Post by zmjjmz on 2008-06-23
Wait, let me get this straight. You enabled _all_ the update options?
Well no wonder you were having kernel panics, that's like alpha-testing stage stuff!

---

### Post by TheHorror on 2009-07-05
I agree that the average user won't be able to use Linux.  I guess that I'm probably considered a power user among Windows users since that at least I'm able to install OS's.  I have been frustrated by Kubuntu too.  KDE's plasma desktop makes my comp run slower than it did on Windoze XP.

---

### Post by juancarlospaco on 2009-07-05
All Unix's aren't for cheap hardware.

---

### Post by HappyFeet on 2009-07-06
> **TheHorror said:**
> I agree that the average user won't be able to use Linux.

Agree with who? Why did you dig up a year old thread?

And btw, you're wrong. An average user *can* use linux, they just can't set it up. (just like they can't install windows either)

---

### Post by dmizer on 2009-07-06
As the OP has moved on, I doubt seriously there's much interest in anyone's reply anymore.

Closing this, let the dead rest in peace.

---

