---
title: "Negative experiences... (not going back to windows, but....)"
date: 2010-06-07
forum: Testimonials &amp; Experiences
---

### Post by Istrebitel on 2010-06-07
Greetings!

I am not one of those who say "ah this wont work i'm back to my windoze". I took open source philosophy seriously and right now i'll try to use windows as little as possible, while migrating. But this is just preamble because i've read the top post here.

When i came to Linux i was choosing a distro. And Ubuntu was the most popular. I chose most popular because i thought it would be suitable for a novice.

My background is a very experienced windows user with some linux experience too (red hat technican something, i even passed their tests and got two diplomas, on administrating and installing linux redhat). I started to read books on linux to understand how it works, and installed Kubuntu.

I've read "Linux is NOT Windows" and such articles, that explain why vi is superior to notepad, why Linux cant mimick windows and success etc. I understand. Still, what i've seen is some serious problem that, to my view, will not allow people to call Ubuntu so easy, "Linux for people", etc, because they will get frustrated. I am not affraid of command prompt and see why Linux approach to it rocks, the problem is not there (mostly)

To the point. What i didnt like:

1) Starting our system, we have interface problems. For example, the console is not in utilities (while the utilities icon looks like a console!). We are not offered a single "getting started" guide (would be very nice to introduce newbie to things he would like to change most likely). The system messages dont stick correctly and overlap each other, their fonts getting out of bonds. But this is minor nuisance.

2) For some reason kubuntu comes with ntfs-3g precompiled without internal FUSE support. What this means is there is no way to mount an ntfs drive without entering a password! Even after tweaking alot of stuff (Recompiling ntfs-3g manually, tweaking configs of different programs) it is still IMPOSSIBLE to make those ntfs drives mount via built-in gui without password prompt (although i made them mount all right via console). But dolphin and "remote drives" still would ask for a password. This is really not what a user would expect, if i plug the device in, in the current age, i expect it to work it out on itself how to connect to my pc and mount itself and be ready for action.

3) Networking. Oh hell! There is a nice tidy gui, but guys, NO WAY TO SAVE YOUR PREFERENCE? Really, you have ZERO control over your network with ubuntu! Because the network manager will overwrite it. It will think for you, and it can only think of one: DHCP! And that i have ports forwarded for exact address and i need my main pc to be that exact address, it doesnt care. That i want to use another interface probably (wifi, not built in eth0) it doesnt care. Why on earth there is no "use this settings" option, i dont know. REsult - hour of searches, frustration, need to revert to manual editing of interfaces file... Seriously, at this age of technology, i would expect such easy stuff to be done via gui, with profiles stored and on the fly change, with option to choose one as a default... I can edit text files, but regular users should not. Nor should they be tortured with a program that takes control of their pc's network for them.

4) No built in "Paint"??? Really, out of three (or four) graphics software coming with ubuntu NO SINGLE ONE can edit! We have whole open office, but we dont have preinstalled gimp? For what reason?

5) No built in codecs for most media. Okay, i know, legal stuff. But 99% of your users wont say "okay i need to make sacrifice to ubuntu, i wont watch dvds or listen to mp3 on my pc anymore, for the freedom!" So why should people look for guides (which are not easy to find, and which are outdated, meaning you have to google to find them, then google again to make them work). Why not include serious list of codecs from the guide on this very forum to some option in "getting started guide"? Really, user buys a pc to work and relax, both of which include listening to music. Latter includes watching dvd's as well. It does not matter is Linux a Windows or is it not, it should just do it to stay competitive. It can do it in some other matter, but people dont get a computer to work for it (they already worked for it, to pay for it), they get it for it to work for them.
I can understand how to install those, but regular users should not, they should get one "codec pack" which they are guided to (ofc with alot of legal notices like consult your lawyer etc).

6) Built-in web browser konqueror is just nonsence. IT cannot view pages properly. You ofter get disorted text and you cannot select text properly, it will slide off.

7) No option to "run as administrator" on right click! Seriously, how should a novice user get a clue on editting config files? You cannot elevate when you already ran software, and before you did, you could not chose that. This option should be in.

8) No built in ibus?????? Why a system that says its "for people" and meaining "for different races of people" with brown guys hugging asians hugging white guys on the advertisments, has NO BUILT IN SUPPORT FOR IBUS? No seriously, not only that, but, why do alot of software included EXPECT it to be there? Dolphin, kate, they spit errors on you every time you launch them! Because they dont have ibus. A fellow on vlc forums even told me "ibus is dead on your system" because he didnt knew it never actually was alive. Most novice users wont know what ibus is anyway, but they still will get errors! And what are errors? Inconvinience that makes them hate ubuntu

9) Incorrect storing of sessions. If it doesnt work - why make it? Or is it one of those "0.1" features we should be grateful it ever exists? For instance, if you've ran something with root permissions you will get an error "kdesudo was ran without parameters" when you logout and log back.

10) Numerous problems with audio. Creative is a very popular company, and it even delivers Linux drivers, yet there is no clue how to install them, and there is no clue how to enable 3d surround in ubuntu with built in alsa ones. If you cannot use your system to the full extent, once again, there is little can be done

11) Even more, the ideology of linux (fine tuning, made easy) is very hard  with Ubuntu! You have for some reason a reworked sudo model (wtf really, why break something that works?), you have numerous software that, instead of modifying config files, makes its own work, thus confusing advanced users even more! (why for god's sake the network manager wont store its settings in the interfaces file! It could comment the currently unused ones and that would be PERFECT! users would be able to tune it via file editing or via gui, whatever they like). You have software that changes config files's names with every release making it another time waster to guess what to tweak for it to work. And so on. 

Overall Kubuntu (Linux) experience feels like a road of sacrifices on the road to some "heaven"? Just like a religion, which it truly is in minds of many.

So far experience with Kubuntu is
- You get a free OS
- no payment
- relative ease of fine tuning 
- friendly support forums
- great amount of eyecandy with kde, even more to download in a blink
- great ease of installing new software
- fast working, fast booting

But! It starts demanding sacrefices:
- You get peices of gui software made so badly that it is unusable (dreaded networking manager taking control of your network, for example). You have to revert to command prompt for those
- Something a windows user can do just plugging you have to each time open console for, and type, spending your time for something trivial
- You get hardware not willing to work (even that officially supported or deemed working)
- You cannot watch your favourite dvd's or mp3's unless you've spent another time on hard labor
- As a result, you spend more time in command prompt than you do actually USING the system

And the list seems to go on, unfortunately. Ubuntu is interesting in terms of learning, exploring, constructing and tweaking, but it is NOT very interesting for actually what it tells it will be usefull, unless you can accept the need to input your password deaded amount of times, having no ability to play music (or use your 5.1 system as well), if you forget your ability to set up your network card or agree to manually choose the connection settings on every boot, and so on. 

I was told that "you have to learn linux, when you switch from windows ure a novice, so get that, and start learning, when you learn linux you will understand the philosophy and will have a working system made for yourself which you are statisfied with" but so far it is not a problem of learning a system, it is a problem of learning the conflicts between different packages or absence of them, or short-sightedness of them. 


So the only reasons i would say i'd choose Kubuntu over Windows any day would be:

1. Eyecandy and desktop functionality. Those are superior to any Win (even 7) and multiple desktops are very usefull.
2. Being free vs serious amount of $$$ M$ demands from you. Unfortunately i have coprorative Win 7 for free even for home use so i cannot make this choice.
3. Being less hassle with malware, but this will quickly emerge when it will become popular so not a major advantage
4. Being very easy to install software, definete serious plus over Windows way (involving searching, watching ads, more ads, more clicking, even more ads, then you download a trojan, it cant be cured you have to delete it, another round, watching ads...)
5. Being (partially) easy to tweak via console, with no need to dig through gui's.
6. Being faster, both in reaction and in boot times.

But thats not enough for regular user, and sometimes i myself want to be a regular user. I want to USE my PC not WORK for my PC. Until Ubuntu becomes the OS that can be USED by, not WORKED for, it wont be winning market shares from microsoft... (and fixing bug 1)

---

### Post by quinntar on 2010-06-07
Hmm waow this is an amazing and long description of your user experience... 
I've got a simple question have you ever tried just ubuntu without kde but with Gnome instead?
As for me whenever I tried KDE 4 desktop I found it spectacular but not as easy to use as gnome and not really efficient for me...

Along with gnome you've gdm with a debugging console that you can choose at start and so on, no problem with fuse, I noticed it in the last version 10.04 I mean, My ntfs-drives just mount without password anymore... I had to enter it once I think but that's all...

I think you should try it, if you cannot get along with the gnome menu you can even download mint linux menu to make it look like KDE menu interface...

Have a try...


Quinntar

ps: for dvds --> just install libdvdcss ... (I've been wodering why it was not installed directly : everything is explained there [https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html) --> actually dvd playback seems to be protected...

mp3s read well with any vlc or other reader on ubuntu as far as I know... maybe totem needs a codec but I do not use totem...

---

### Post by derekeverett on 2010-06-07
I sympathize with your frustration. I have come to the conclusion that to be content I simply can't and won't choose "just one" OS. I need to dual boot. Best of both worlds.

I don't think it should be an all or nothing game. Between Windows, OS X and any given Linux distro there just isn't "one" that makes me completely happy. I need choice, so I need more than one.

Really... even between Linux distro's there isn't "one" that has it all. I think Ubuntu and it derivatives are a good choice though because of the community if nothing else. It's probably easier to learn things and get questions answered with Ubuntu than any other distro at this point in time.

---

### Post by wilee-nilee on 2010-06-07
Wow, good luck getting anybody to read that whole thing, it is the Ubuntu forums. All the complaints have been posted 100's if not 1000's of times your opinions are not new to the forums. Use what works for you and have a good time doing it. ;)

---

### Post by derekeverett on 2010-06-07
> **wilee-nilee said:**
> Wow, good luck getting anybody to read that whole thing, it is the Ubuntu forums. All the complaints have been posted 100's if not 1000's of times your opinions are not new to the forums. Use what works for you and have a good time doing it. ;)

I agree that the complaining certainly isn't new. But if there is one thing I have learned about Linux it's that sometimes you just have to vent!!

---

### Post by wilee-nilee on 2010-06-07
> **derekeverett said:**
> I agree that the complaining certainly isn't new. But if there is one thing I have learned about Linux it's that sometimes you just have to vent!!

That is why I try to just either not reply or at least be civil on a good day. I have had to vent, but never about my computer or OS, they are inanimate objects, and there is always another distro to try. I'm just a armchair user, I don't need to project a distros intentions and get upset. I guess if I new more about coding or wanted to even edit files I could get irritated but I'm not that interested.

---

### Post by randcoop on 2010-06-07
I read your whole post and found it interesting.  I think, though, that it has a fundamentally flawed premise: Linux is not trying to compete with Windows.  Microsoft has a monopoly.  Manufacturers of computer equipment produce their products in accordance with that monopoly control.  That means they don't produce drivers that will function with Linux operating systems.  That means that anyone who uses Linux will have to accept less than perfect drivers.

Linux is for people who might have different expectations for their computers than the ones you suggest.  They might not care about effortless ease of use.  They might instead be willing to work harder in order to combat the Microsoft monopoly.  Or they might find working with computers interesting and enjoy the challenges presented by a tiny minority system.

In a monopoly system, it is impossible to compete.  Linux is not trying to compete with Windows.

---

### Post by gwaar on 2010-06-07
I agree with the first reply; KDE always gave me more problems. I started off with kubuntu and dealt with the problems for a while, as they were mostly little things (I completely agree with you on Kubuntu's network manager - even getting passworded wireless internet to work was a pain that took me forever to deal with), but had to switch after kubuntu started using KDE4 - it was too much for my computer and me. I used xubuntu for a while; I still like xfce, but still had little problems. 

But, switching to straight Ubuntu, everything has been much easier. A few things on your list might still linger, but on the whole everything is much easier. It's difficult to not conflate Kubuntu and Xubuntu, etc. with Ubuntu itself, as they're all built on the same base - but I feel like Ubuntu is the one that is, and is meant to be, the easiest, and most successful of the bunch. 

Some people like KDE more, some people like Xfce, but they're not going to be the ones that are picked to showcase what Linux has become. Ubuntu, while it still has several drawbacks (straight-up inability to play HD flash movies unless your computer is at levels way above where it should need to be, being my peeve) is becoming something that can at least be comparable to other OSes. My 0.02.

---

### Post by John Bean on 2010-06-07
> **Istrebitel said:**
> When i came to Linux i was choosing a distro. And Ubuntu was the most popular. I chose most popular because i thought it would be suitable for a novice.

Ok...

> 2) For some reason kubuntu comes with ntfs-3g precompiled without internal FUSE support. What this means is there is no way to mount an ntfs drive without entering a password!

Kubunti is not Ubuntu. Had you installed Ubuntu as you said earlier you'd have found this to be not the case.

> 3) Networking. Oh hell! There is a nice tidy gui, but guys, NO WAY TO SAVE YOUR PREFERENCE? Really, you have ZERO control over your network with ubuntu! Because the network manager will overwrite it. It will think for you, and it can only think of one: DHCP!

You wrote "Ubuntu" but you have Kubuntu. I can't speak for Kubuntu's Network Manager since I don't use it but Ubuntu allows GUI configuration of most networks whether DHCP or not, and of course it saves the settings. Just like Windows really, no need to resort for manual configuration except in very unusual situations for desktop machines.

I'm not starting a debate but I felt the need to correct some of your points concerning **Ubuntu **which are simply not true.

---

### Post by za.zen on 2010-06-07
.

---

### Post by ralanyo on 2010-06-07
I have been using Ubuntu for over 4 years and I have to admit; in the beginning it was a little hard to adjust. But as the distro updates have been coming in, I have found that it is getting easier and easier to use. Things like connecting printers, flash, java were all an issue in the beginning. Now most of those things have be resolved. Overall Ubuntu is not perfect, but certainly on its way to being one of the most powerful linux disto's on the planet. 

Once you get used to it you will find that there is no more spyware or viruses. Good luck.

---

### Post by coffee412 on 2010-06-07
Im sorry to hear that you are having so many problems with Kubuntu. However, From my personal and professional experience I find Ubuntu very satisifying. 

I have installed and maintained Ubuntu on alot of my customers computers and have had very little problems with it. The only time that I have had real problems with it is with either Adobes Flash  or an older ATI video card like the onboard mobility chipset. Most comments from my customers are that 1- Linux menus are alot better layed out than windows(vista, 7). 2 - Their HP all in one printer now works correctly (with installed HP driver). No more virus problems and breakin worries.

Linux has come along ways since the old days. You have to remember that computer and parts manufactuers do not really support linux. They are all comfortable in the windows camp. However, In IT rooms around the world linux has displaced windows to a large extent and I can only see the trend continuing. Most recently, Google dropping windows comes to mind. 

My advice to you is to boot to a live preview of Ubuntu and see if all your hardware is recognized. If it does then install it and then investigate the "Software Center" for more applications that suit your needs. You can also post and ask what software people recommend.

I have been working with linux since the days of kernel 2.0.36 and have always appreciated linux for what it is - An alternative to windows in a free world. :P

coffee
- Newsposter - the Linux binary posting script 
[http://parkit.dyndns.org](http://parkit.dyndns.org)

---

### Post by blur xc on 2010-06-07
> **randcoop said:**
> I read your whole post and found it interesting.  I think, though, that it has a fundamentally flawed premise: Linux is not trying to compete with Windows.  Microsoft has a monopoly.  Manufacturers of computer equipment produce their products in accordance with that monopoly control.  That means they don't produce drivers that will function with Linux operating systems.  That means that anyone who uses Linux will have to accept less than perfect drivers.

Linux is for people who might have different expectations for their computers than the ones you suggest.  They might not care about effortless ease of use.  They might instead be willing to work harder in order to combat the Microsoft monopoly.  Or they might find working with computers interesting and enjoy the challenges presented by a tiny minority system.

In a monopoly system, it is impossible to compete.  Linux is not trying to compete with Windows.


Maybe Linux isn't but it's apparent that Ubutnu is- [https://launchpad.net/ubuntu/+bug/1](https://launchpad.net/ubuntu/+bug/1)

to the op- As for my NTFS partition, I have edited my fstab to automount on boot.  See /etc/fstab

Have you installed the ubuntu-restricted-extras package?  It takes care of most codecs...

I've had pretty decent luck playing dvd's on my computer, but don't do it that often...I have a big tv for that.

BM

---

### Post by steveneddy on 2010-06-07
> **Istrebitel said:**
> 

My background is a very experienced windows user ......

I find this phrase in posts that more often than not portray new users of Linux in general and Ubuntu in particular as "advanced" computer users but incapable of fully understanding Linux as an operating system doesn't operate like a Windows machine.

Reading about how Linux is not Windows and understanding Linux is not Windows is something that these users have a hard time comprehending. For some reason Windows is the defacto standard by which all computing should be judged, which in reality is not the case.

The only advice that I could offer to the OP is to use Ubuntu and not Kubuntu and to migrate slowly from Windows until you understand how computers work and when you really don't feel that you need a GUI to get something done on a real computer.

As for certain packages not being installed by default, that is a philosophical and democratic issue that can be rectified by simply installing the packages you need/want through apt or Synaptic. This is where getting to know your new OS by using it as much as possible and learning what does and doesn't work will help you be a better Linux user and Ubuntu advocate.

---

### Post by aysiu on 2010-06-07
I think half your problems would be solved by using Linux Mint.

---

### Post by NUboon2Age on 2010-06-07
> **Istrebitel said:**
> Greetings!
...
1) ... We are not offered a single "getting started" guide (would be very nice to introduce newbie to things he would like to change most likely). ...

That is an EXCELLENT POINT.  I saw a [very cool getting started guide]("http://ubuntu-manual.org/") that is being lovingly created by the community.  It needs to popup after install and be right there on the desktop and/or even as an option on the Try/Install menu.

In addition these web pages have more of that kind of info that should be made available:
[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

---

### Post by bondo101 on 2010-06-07
Wow someone's not happy. Ah yes does one remember the days of windows 3.1 or the great 95 a" edition . perhaps the blue screen of death? long boot up times , crossed files ,crashes and more lockup's? Mabey the person chose the wrong version for his own needs mabey he should try Debian or Suse. If he's that heavy into windows then those distros shoud be a breese for him.
I to get frustraited but SOOOO What ! It is just a computer if ya don't like what it's putting out , then turn it off and read more info to solve your problems. Try to get more info on the distros before using them  to fit your needs. its a learning process for me every day its a new challenge, beats watching stupid videos on you tube.:confused:

---

### Post by WinterRain on 2010-06-07
Kubuntu and KDE are less than good, to put it mildly. I suggest trying regular ubuntu.

---

### Post by mastablasta on 2010-06-08
> **Istrebitel said:**
>  
2)  This is really not what a user would expect, if i plug the device in, in the current age, i expect it to work it out on itself how to connect to my pc and mount itself and be ready for action.
 
Interesting feature. Does make sense. For example let's say you have internet cafe or work computer. Someone comes and collects the data off without you even knowing. if he needs to add password he can't do that.
 
> 
4) No built in "Paint"??? Really, out of three (or four) graphics software coming with ubuntu NO SINGLE ONE can edit! We have whole open office, but we dont have preinstalled gimp? For what reason? 
Reason is discussed in the Mark's blog. However i think it is to get space for other things.
 
> 5) No built in codecs for most media. 
These are so easy to install. Windows also comes without them. I had to download k_lite kodecs pack to play the media.
 
 
> 7) No option to "run as administrator" on right click! Seriously, how should a novice user get a clue on editting config files? You cannot elevate when you already ran software, and before you did, you could not chose that. This option should be in.
 you mean super user? 
SUDO
 
 
 
You also mentioned there is no user guide. As i know there are at least two good ones.
 
One is available here for Ubuntu 10.04 (project 80% done): [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
The other one is for Ubuntu 8.04 (but still valid and an excelent staring point): [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by Istrebitel on 2010-06-08
Didnt ever think people will actually read and comment. Thank you everybody. I will answer as well:

**2 quinntar**
I think i will try gnome interface, maybe it will fix that ntfs problem all right. I dont have mp3 or dvd problems after i've spent 4 hours figuring out. My point was i shouldnt have to! If the system is to be used by USER, he should be able to install everything with a click of a button (or series of clicks of a button, if law demands that those packages are not included in ubuntu distro). Instead i had to spend times studying how codecs work on linux, how payers work on linux, try 6 players, then find a post, try the post suggestions, google why it doesnt work, get to know what should i change in the command line suggested by the post for it to work, retry, regoogle, retry, and finally get it done. I refer to the pinned post in multimedia forum of this site.

**2 derekeverett**
Yes, so far i thinkg will stick to 99% open source software on windows 7 i suppose, i still have the linux dualboot, but before i get the audio surround (5.1) working, i wont be able even to work on it, because i work listening to music, and i got used to hearing music around me, not through two front little speakers... 
And i cant mosty game on linux too because i have Razer NAGA  mouse and it is not fully supported on linux (mainly, i cannot remap the keys, so i cannot use it to its full potential in World of Warcraft for example).
If the sound card problems woud be solved (i'm even gonna look for an alternative card, i can afford spending time on finding it and money on it if it will work with surround on linux) i could at least work on linux all right. And then probaby leave win7 just for games (this is my problem, i understand why Razer does not spend time developing drivers for linux, if linux if 5% against 90% of microsoft on the market)

And its not about venting. I truly hope that some of my thoughts will help probably improve ubuntu to make it more appealing to new users.

**2 wilee-nilee**
Well, i understand that, but still, i had to say, and i said. Somebody did read, you see :)

**2 randcoop**
I dont quite think you are right. If you meant "compete" as "earn money" then you are right. But if you meant "compete" as "make a better product" then you are wrong 100%.

Again we must settle the basics. Linux as linux, the kernel, of course does not compete with windows, the operation system and applicaton suite in one. Kernel today is close to useless to a user. Today, user needs a PC to preform different tasks:
- working with documents (graphic, text, tables, media)
- surfing the internet
- enternaintment (playing music, video)
- gaming

Therefore, comes the need of "distributives" as we see them today. People need not only linux kernel, but the operation system and application suite to do what they need.

If ubuntu or other "user-friendly" distros, as THEY CALL THEMSELVES, would not try to "compete" as "try to be better", they should never exist in the first place! Firefox tries to compete. Thunderbird tries to compete. Open Office tries to compete. They do, they admit it, and i can prove with citations from their own websites or readme's. They want to prove to the user, why use them, why using them is better than using proprietary analogues, and they succes only when they actually offer what they say they will. 

Firefox has destroyed IE monopoly on the internet ONLY because it was competing, and it was BETTER. It was EASIER to use, it didnt require digging the consoles or bearing the sacrefices.

I understand that its harder to compete with an OS because of driver and hardware problem, but it should be aimed at, otherwise there is no point making a "user-friendly" distro! And non-user-friendly distro, distro for "pros", does not need all that stuff included in Ubuntu.

Last word, Ubuntu is a most popular distro you might now. Why's that? Google it, mostly because it TRIED to compete. It has windows-like interface (easing the migration) and it tries to offer the boons that are unavailable to windows users (or less available). 

**2 gwaar**
I chose kubuntu because of an eyecandy. I am addicted to eyecandy (but couldnt get enough in windows, it starts to slow to a crawl!). Could you advise me some comparing articles or articles about how to make gnome look nicer? Am i wrong that KDE offers much more easilly tweaked and obtained eyecandy than gnome?

**2 John Bean**
I am sorry for me it is hard to distinguish. Because i dont quite understand how a pure matter of interface (as a friend "linux pro (he's a Gentoo lover)" explained to me, everything is in fact a skin to an "X server" which actually runs all the windowing work. KDE or Gnome just offer a wrapper around it.) can introduce such array of problems. 
Also i thought that ideology is preserved, and ubuntu (i use that word as "ubuntu family" mostly) is the same. If it is not, i beg you pardon, i would indeed want to try ubuntu if you say it is more stable and easier to use and it does differ that much from kubuntu.
Once again, i used "ubuntu" as "ubuntu family of gnu/linux operation systems" and if i was wrong assuming that non-interface specific problems are same for every ubuntu-family os, i am sorry, please correct me.

**2 ralanyo**
Thank you. I understand that it was much harder in the past. I knew about linux for about five years and i only wanted to try it just now when i learned about how much progress it had made. I understand progress is serious. I am just speaking that it is not yet enough to suit a regular user.

**2 coffee412**
The comments about "ubuntu is better than kubuntu" start to stack. I guess i will try it all right. I dont think your customers used Creative Titanium X-FI  and succeeded with 5.1 surround working?.... I understand why most hardware developers dont worry making linux drivers if linux users are such a minority, but we are not talking about some bizzare devices like i've met (custom usb connected chips to emulate voltage meters and control various mechanisms) we are talking about a sound card that is said to SUPPORT ALSA! and yet it wont work and people have no clue how to make it work....
And this was not the only point of my negative experience with kubuntu anyway...

**2 blur xc**
Unfortunately if i automount, it makes boot time last ~15 seconds more because this external hard drive is "warming up" when first queried, and when this happens during boot, kubuntu starts complaining that the drive is not responding and should it enter manual setup mode, this adds some extra seconds... overalll the 4 second boot time can last up to 20 because of that, so it is not a solution....
About codecs i already answered earlier (same question was asked)

**2 steveneddy**
I dont think i am in position to say what i am capable of and what not, but i THINK i am. I am certified Red Hat specialist if you ask, i have attended to certified courses and passed Red Hat certified exams, [http://www.redhat.com/certification/rhct/](http://www.redhat.com/certification/rhct/) and [http://www.redhat.com/certification/rhce/](http://www.redhat.com/certification/rhce/). I could provide scans of the diplomas if you dont belive me. I have also read "Linux is not Windows" article which i stated in my post. 

I also think i understand how computers work... Up to the point i not only know the purpose of each interconnected part of the PC, but can distinguish parts of the motherboard or graphics card/audio card/etc, in case of faults isolate the problem in the software or the hardware and fix it (if it doesnt involve smoldering or somehow changing the integrity of the boards themselves). I had experience constructing my PC from scratch (meaning buying every component and connecting everything myself) and even have been employed in that (dunnow how the profession called, the one who constructs and tests pc's) for two months (earning money on summer vacation).
 
And i understand that switching OSes makes you a newbie and you should learn the new OS and adopt.

My point was, if Ubuntu is to be called "user-friendy linux" or "linux for people", it should not be a windows (linux is not windows), but it should offer what windows does, or any user-oriented OS offers, otherwise it would not be truly comfortably usabe by a simple user. This should not be "same hotkeys, same interface, same folder structure". But this should be "same or better functionality". Firefox way, i'd call it.

**2 aysiu**
could you be more specific please about Ubuntu mint?

**2 NUboon2Age**
my point exatly. Faqs and manuals already exist, what's left is to tie them to the points where user will need them! because, honestly, not always you can make up a query in google that will give you the best guide as a result. For example with my password ntfs problem, i only got a suitable guide at 3 or 4 attempt... 

**2 bondo101**
I remember, i worked in dos when 3.1 wasnt even universally available (although since im Russian probably it was just late coming to our country...)
I made my point about where Ubuntu is better than Windows. I support that 100 percent. And i had billions of problems with windows. I agree with you. 
I didnt speak of them because i knew M$ wouldnt care. Moreover i didnt use legal M$ software before lately (and dont blame me please, you should first know that the 1000 euro salary here in Russia is considered HUGE, while european person gets 2000 euro just for cleaning toilets or being unemployed at all) so i didnt have the right to speak (well peope still do pirate here in russia and THEN complain but i think they should not, because if you pirated something, you have to rights to ask for technical support or fixes from the company whose terms of service you violated). And then i only started using legal M$ software because company that employs me is M$ partner who has permission to use its stuff (corporate license). 
I started to talk about problems with ubuntu not to swear at someone or dunno, speak out. I did it because probably, maybe, i will make a valid point that will somehow help improve Ubuntu.
I probably would try different distros, but as i said, i am attracted to eyecandy, and thats why i took kubuntu in the first place...

**2 WinterRain**
i see... definetly stacking up... okay okay you convinced me!

**2 mastablasta**
on the password protection - 100% agree with you. But it should be easilly turnable off. Instead to PARTIALLY turn it off you have to dig, dig, dig more, learn to compile packages and set options, and you still didnt solve the whole problem.

could you link me the blog? if the reason is space - hmm, why not make an entry in the quick start guide that should pop when user enters the system, with a list of suggestd packages that couldnt be included in the distro but are offered as best for their field?

I would argue on easiness to instal codecs. you dont have a "pack". You have to find a complex number of them. and the only good guide on them in the net is wrong ( you have to manually find that one package is changed name and others should not be installed at all). So it is more complex, from user point of view. I suppose a dummy package listing those codecs prerequisites, showing itself in the quick start guide, would be very nice way for it to work out for users.

And thank you i know SUDO. But not SUDO. First of all, KDESUDO or SUDO depending on circumstances. But how are you supposed to know about sudo at all?
1)and why do i have to do:
- navigate through menus to my program icon
- remember how exatly the program is called (i can never know it because i could use abbreviation or just remember the icon or its placement!)
- navigate through menus to terminal
- open terminal
- write kdesudo name of my program
when i could
- navigate through menus to my program icon
- right click the program, choose run as adminstrator
There is no point for command line usage here, it slows things down
2) how does a newcomer to the system supposed to know about sudo or kdesudo? When he has no rights to do something, he is told "file is read only" or "you have no rights" or "only root can do that". But he cannot login as root (account disabled, if you enable system might get ruined). He has to google. Providing a gui option for that or at least mentining "use sudo to run program as superuser" would save time and make system easier to use, wouldnt it?
3) how does a user who knows linux supposed to know that he should NOT use sudo for graphical applications (kdesudo instead)? 

Thank you for the link to the guide. This guide doesnt apply to kubuntu, does it? Because frequently guides  in the net i found offer gui ways for doing something, when in kde there is no analog (for example, the IBUS problem, ubuntu is said to have gui to tweak it while in kde it does not exist at all...)

**Thanks everybody.**

I must once again impress the fact that i am not trying to insult people who had put thousands of hours of work into making this project possible. Nor i am trying to be smarter than them. I am just trying, from the point of user, to tell what is extremely annoying or what is missing in order for Ubuntu to really be Linux for people, user friendly operation system. Thats all.

PS: also forgive my poor choice of words, probably, english is not my native language nor did i attend anywhere to learn it (i am a self learner through untranslated games, mostly...)

---

### Post by mastablasta on 2010-06-08
> **Istrebitel said:**
>  
**2 aysiu**
could you be more specific please about Ubuntu mint?

Linux Mint is a distribution of Linux that is based on Ubuntu (which is based on Debian). It includes codecs as well as some bug fixes and inovations.
[http://www.linuxmint.com/](http://www.linuxmint.com/)
 
Looks nice but to me Ubuntu desktop seemed more intuitive, so in the end i installed Ubuntu. 
 
 
**>  **
2 mastablasta
on the password protection - 100% agree with you. But it should be easilly turnable off. Instead to PARTIALLY turn it off you have to dig, dig, dig more, learn to compile packages and set options, and you still didnt solve the whole problem.
****
Virueses could then easilly turn it of, no?
 
> could you link me the blog? if the reason is space - hmm, why not make an entry in the quick start guide that should pop when user enters the system, with a list of suggestd packages that couldnt be included in the distro but are offered as best for their field?
 
Sorry, but form Wiki:
[GIMP]("http://ubuntuforums.org/wiki/GIMP") was removed from the Lucid installation CD due to its professional-grade complexity and its file size. [F-Spot]("http://ubuntuforums.org/wiki/F-Spot") provides normal user level graphics editing capabilities and GIMP remains available for download in the repositories
 
Also more here:
[http://www.omgubuntu.co.uk/2009/11/gimp-to-be-removed-lucid.html](http://www.omgubuntu.co.uk/2009/11/gimp-to-be-removed-lucid.html)
 
Also wiki says GIMP wasn't in KDE editions. :-O
 
> I would argue on easiness to instal codecs. you dont have a "pack". You have to find a complex number of them. and the only good guide on them in the net is wrong ( you have to manually find that one package is changed name and others should not be installed at all). So it is more complex, from user point of view. I suppose a dummy package listing those codecs prerequisites, showing itself in the quick start guide, would be very nice way for it to work out for users.
 
I think they are hiding in restricted extras package in the software repository. Also they can all be installd with single command line for those that don't like the GUI. Yes they should be more easy to find.
 
> And thank you i know SUDO. But not SUDO. First of all, KDESUDO or SUDO depending on circumstances. But how are you supposed to know about sudo at all?
 
Everyone should at least read the beginners guide or user manual (like with every product yet most people feel confident enough not to need one - like me and my car radio).
 
well actually to run programmes you shouldn't have top type SUDO everytime. Only when you are installing or accessing system files. since i know little about the OS i don't really like to mess arround with these. And for installing programmes there is a pop up for entering the passoword. at leats i htink i have the concept here.
 
Like other have pointed out Kubuntu is not really best starting point to meet with Ubuntu. Also it has some issues as i can read. I tried it (9.10) as i was hoping to get a closer to Windows experience. My brother (uses linux at work) helped me a bit with it that is until he too got a bit lost. I also didn't like menu navigation so i went with standard Ubuntu (Gnome). Like someone mentioned try Mint (at least live CD) see if you like it. The have some great inovations that are missing in Ubuntu (for example user reviews of software, backup programme...). i just didn't like the menus. But if upcomming LDXE version is good i will likelly install it on the old notebook.

---

### Post by Istrebitel on 2010-06-08
2 mastablasta
(about mint)
Thank you, could you probably provide a link to a good comparison article? Because my experience with googling for A vs B is that those arcticles are mostly either stolen other article or just technical comparison "A has theese, B has theese" or "A has 20-000packages, B has 25000 packages". They dont get to the point "If you like a and dont need b, you choose A. If you like c and dont need d, you choose B"

(about viruses)
no, they wouldnt. Provided the option itsef can only be changed with root acces. If there is no exploit to elevate to root, viruses wouldnt be able to turn it off. If there is such exploit, then it wouldnt matter as whole system is compromised! :)

(about gimp)
Those that come with kubuntu - i tried every one of them - I dont call them "editors" because they cannot EDIT. I couldnt find pencil, line, box, copy, paste tools.... I belive they can just toy with colors a bit, like remove red eyes or change saturation... Thats not true editing, as i see it.

"Also they can all be installd with single command line for those that don't like the GUI."
you mean command line from here? [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
it doesnt work anymore, have to fix some issues first before using it

(about sudo)
Well i knew about sudo, because i attended to RH courses and exams. But i didnt knew about not using it with graphic apps. Didnt see it in manuals i've read too. Common sense told me "use sudo if you need it to access system files". How could've i known to use kdesudo instead?
And still i think "run as root" is an option to be always included in right click over an application. Otherwise there is no point adding gui icons to applications that need to be ran with sudo at all?
Whats the point of making a gui icon for something that is useless if you run it clicking on the icon, and can only be used if you run it from console?

---

### Post by mastablasta on 2010-06-08
Unfortunatelly the reviews are indeed mostly centered on what you wrote. So i found out the best way is to just try the live CD. after all until you do you don't even know if the computer will work well with it. CD's are cheap. of course if you don't have broadband it could be a bit difficult but even so, you can always get it shipped.
 
Still Mint has a page with Mint review links: [http://www.linuxmint.com/reviews.php](http://www.linuxmint.com/reviews.php)
 
 
Yes i too noticed that F-Spot (the default one in Ubuntu) is rather limited. I mean if they had something like Irfanview or ACDSee then we could talk... But F-spot just doesn't do it. GIMP in my opinion is too complex, but F-Spot is too simple and (at least in 9.10) it's lacking some important functions - such as easy picture resizing.
 
 
XVID Movies and Flash
 
No. Single command line as this one:
 
```
sudo apt-get install ubuntu-restricted-extras
```
 
from here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 
Maybe it should be replaced by kubuntu-restricted-extras in Kubuntu (read the info on the site to learn more)

---

### Post by Istrebitel on 2010-06-08
For some reason LiveCDs boot for minutes on my pc... sometimes tenths of minutes... about 20 probably. And it gives me nothing - annoyances mosty dont show up during "test run" - for example, dreaded network manager can only be annoying after you install system, configure it, restart and see it had forgotten what you chose and sits on DHCP again. Well it proves it will work on my system but i suppose if kubuntu and ubuntu did, so will mint, based on them?

Why does the post i shown still exist then, if all those big list of codecs can now be installed with one command? Or is it just kept for the sake of completeness? Does this line install all codecs mentioned in that post?

---

### Post by aysiu on 2010-06-08
Linux Mint is a Linux distribution based off Ubuntu. It mainly uses Ubuntu's repositories and installer, but it has a few tweaks and some different default software packages installed. > **Istrebitel said:**
> 
1) Starting our system, we have interface problems. For example, the console is not in utilities (while the utilities icon looks like a console!). In Linux Mint, the terminal is in the menus. It's in the menus in Ubuntu as well, but I believe in Mint's menu, it's more readily apparent. > We are not offered a single "getting started" guide (would be very nice to introduce newbie to things he would like to change most likely). The system messages dont stick correctly and overlap each other, their fonts getting out of bonds. But this is minor nuisance. Linux Mint presents you with a getting started guide right when you boot up. I hate this actually, since it is essentially an unavoidable pop-up. It'd be nice if it were more unobtrusive. I like how in Ubuntu (not sure if this is true for Kubuntu or not) there is a tutorial slideshow during installation. You have to wait around then anyway, so you might as well learn something.

> 
4) No built in "Paint"??? Really, out of three (or four) graphics software coming with ubuntu NO SINGLE ONE can edit! We have whole open office, but we dont have preinstalled gimp? For what reason? Linux Mint comes with GIMP by default.

> 5) No built in codecs for most media. Okay, i know, legal stuff. But 99% of your users wont say "okay i need to make sacrifice to ubuntu, i wont watch dvds or listen to mp3 on my pc anymore, for the freedom!" So why should people look for guides (which are not easy to find, and which are outdated, meaning you have to google to find them, then google again to make them work). Why not include serious list of codecs from the guide on this very forum to some option in "getting started guide"? You seem a bit confused. Legal issues are only part of the story. The exclusion of proprietary codecs by default in Ubuntu comes primarily from philosophy, not legality. More details here:
[http://www.ubuntu.com/project/about-ubuntu/our-philosophy](http://www.ubuntu.com/project/about-ubuntu/our-philosophy)

But Ubuntu works out a nice compromise, because it also provides tools for you to easily install proprietary codecs if you want them.

As I said before, though, Linux Mint seems right up your alley. It comes with all the popular proprietary codecs by default. Not only that, but it has a local repository for proprietary hardware drivers, so if you won't need an internet connection in order to get your internet connection set up. 

> Really, user buys a pc to work and relax, both of which include listening to music. Latter includes watching dvd's as well. If you **buy** a Ubuntu preinstalled Dell computer, it will come with legally licensed proprietary codecs preinstalled.

> 6) Built-in web browser konqueror is just nonsence. IT cannot view pages properly. You ofter get disorted text and you cannot select text properly, it will slide off. Once again, Linux Mint comes with Firefox, as does Ubuntu.

> 7) No option to "run as administrator" on right click! Seriously, how should a novice user get a clue on editting config files? You cannot elevate when you already ran software, and before you did, you could not chose that. This option should be in. This is unfortunate. The developers seem to have approached this with the idea that those who don't know how to edit root-owned files shouldn't be editing them. The truth is that the vast majority of new Linux users are installing and configuring Linux for themselves, and sometimes that configuring involves changing system files.

If you're interested, there are some easy workarounds, though. For one thing, you can install a software package called *nautilus-gksu* that will allow you to right-click to edit as administrator (this works for Gnome's Nautilus file manager, but there is an equivalent package for Dolphin or Konqueror in Kubuntu--I just don't remember what it is.

So, yeah, about half your problems would be solved by just using Linux Mint. The bottom line, though, is that for most new Linux users, the chances of a seamless experience will be a crapshoot, since the primary means to getting Linux is searching for a disk image, downloading the disk image, verifying the download, burning the download to disc (or to USB), making sure one's computer boots from CD or USB, repartitioning the hard drive, installing Linux, and then troubleshooting hardware or software setup problems.

The only chance consumer Linux has is with a well-thought-out and well-marketed preinstalled product. So far, the preinstalled options have been obscure (not available in most countries), not well-thought-out, and barely marketed (in some cases, marketed against, since Dell's own Ubuntu pages "recommend" Windows 7).

---

### Post by mastablasta on 2010-06-09
> **Istrebitel said:**
>  
Why does the post i shown still exist then, if all those big list of codecs can now be installed with one command? Or is it just kept for the sake of completeness? Does this line install all codecs mentioned in that post?
 
The post is instructions for older version of the system (8.04LTS and 8.10) which some people might still use. Just as some people are still using Win98 or even 95.
 
Also 8.04 was Long Term Support release, released in April 2008. Since it is an LTS release it means it is still supported (until April 2011 i believe).

---

### Post by Istrebitel on 2010-06-09
2 mastablasta
Thanks!
May i then suggest that this post should contain a hint that newer ubuntu users should use command you specified? Because i tried it and it works magic!

And if you dont know it exists, you google, find this post, find a header called:
UBUNTU FAMILY 8.10 AND HIGHER USERS ONLY

and you think thats what you should do.

2 aysiu
I decided to try Ubuntu first but it seems indeed that most of my problems were because of Kubuntu. Damn eyecandy addiction...

I must say that in Ubuntu
1) is not a problem
2) is almost not a problem (i can mount ntfs partitions without password prompt, but i have to manually do it each boot and i cant do it from file manager, or havent found how yet)
3) i have yet to restart to see if they will persist, my networking settings, but ubuntu netwroking manager seems to have an option to actually configure this auto eth0 connection, if it does always uses auto eth0 its atleast a partial solution to my problem, if not permanent (i.e. if i ever get wifi card it will still use eth0 on each reboot)
4) is solved
5) was not a problem if a new user would somehow be told of this "restricted" package. Because he is only told about "getting mp3 codecs" or am i wrong on it?
6) with firefox it is solved
7) is still a problem, and yet i wont agree that those who dont know how to sudo should not be able to do it. Its not the matter of knowing, its the matter of not wasting excessive time opening windows and typing when you can just click
8) didnt check if ibus works. gotta do it when i have time
9) i think it still is a problem, but i will find out
10) i found out that in the hardware guide of overclockers forum, x-fi is listed especially as a card that has problems... guess probably thats bad luck for me? Can anyone advise a good tux-friendly PCI-E sound card with 5.1 support? 
11) i cannot agree that removing root solves the problem. you can still sudo rm -(dont remember the keys) to destroy your pc. it is easier to switch to root and so some work, then switch back, and having root enabled does not remove sudo as an option to elevate permissions for once...
other inconsistensies are even piling up (now i learned there is only run level 2 in ubuntu instead of typical 3/5) but this is not a major inconvinience. 
Overall, i suppose i wrote this part just because i was too frustrated with network manager/ntfs mounting problems

Definetly the list of benefits of Ubuntu (not kubuntu) vs Windows grows in my eyes.

PS: I recently found this:

[http://www.youtube.com/user/nixiepixel?blend=2&ob=4#p/c/C57C60F699A5C44D/12/VFqj2hS_0iQ](http://www.youtube.com/user/nixiepixel?blend=2&ob=4#p/c/C57C60F699A5C44D/12/VFqj2hS_0iQ)

and now i think i'll fall in love with Ubuntu...

I think if this would be included in Ubuntu tutorial, like a link on how to setup compiz - watch this video, Ubuntu popularity will exponentially grow ^_^

PSS: Although i suppose that its all an act, and she's just using "geek" image to up her popularity... meaning its a kind of fake... still, having a cute girl (sexually dressed and made up, with brains and deep understanding of computers and linux) lecture you through the process definetly makes you feel good towards anything :)

---

