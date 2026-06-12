---
title: "Why is there always problems installing flash on Ubuntu???"
date: 2009-12-12
forum: The Cafe
---

### Post by marchost on 2009-12-12
I will never understand why, release after release, flash is still not working properly in Ubuntu... It's a major issue they should work on before adding eyes candy or faster boot time (9.04) which in the end, we dont really care about. 

I mean, I can get flash working BUT it 1) doesnt work all the time (issue with youtube & many others) and 2)it's very slow (when it works). Same problem with the free (gnuflash) or adobe version.

---

### Post by Uncle Spellbinder on 2009-12-12
In my personal experience, I've not had any issues with Flash since Hardy. Only issue that popped up for me was on Karmic 64-bit. Went back to 32-bit and all was well.

---

### Post by Raffles10 on 2009-12-12
64bit flash in Linux is really very simple if you don't rely on obtaining everything from the repo's.

Download 64-bit Plugin for Linux (TAR.GZ, 3.6 MB)

[http://labs.adobe.com/downloads/flashplayer10_64bit.html]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")

Extract to ~/.mozilla/plugins

If the plugins directory doesn't exist, create it. This also works for 32bit but obviously you'll need to download the 32bit plugin. ;)

---

### Post by LuisGMarine on 2009-12-12
[http://ubuntuforums.org/showthread.php?t=1352617]("http://ubuntuforums.org/showthread.php?t=1352617")

That's if you are using 64-bit Ubuntu.  I even made a video tutorial! Enjoy, essentially you could use the same concept for Ubuntu 32-bit, just make sure you download the 32-bit of Flash.  That is if you are not into the whole .deb thing and like doing things the hard-way, but at the same time learning something about your system.

---

### Post by wojox on 2009-12-12
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by webbdawg on 2009-12-12
Wojpx, I think the point of the thread is that Flash is so prevlant everywhere there is no reason the developers should not have a bullet proof version working.

Can you imagine the net with out flash player. If FF can do it for windows then why is it so tough for linux??

---

### Post by monraaf on 2009-12-13
The Adobe flash player is closed source, go complain to Adobe about their crappy software.

---

### Post by ankspo71 on 2009-12-13
Hi,
I know the flash problems in linux too well. When I was using my intel celeron 2ghz which is a single core processor,  flash caused firefox to max out my cpu up to 100%. Since then I have upgraded my processor to a Pentium 4 3.0ghz (which is almost like having a dual core processor because of 'hyperthreading'), and I have not had a major problem with flash since. 

I know that not everybody can do that (obviously), but I have a few tips that might help.

Find a firefox addon that blocks flash videos and games (examples would be flashblock and stopautoplay), that way you can control how many flash videos/games run at the same time. I recommend only running one flash object running at a time.

Reduce the number of tabs in your browser while watching videos or playing games.

Close all other applications you don't need  while watching videos or playing games.

Disable any services or startup applications you know you don't need (Be careful!)

Disable desktop 3d effects.

Upgrade to firefox-3.5 (if you are using the 3.0 version)

Finally, you might have to end up watching your videos offline in a media player, which means you would have to download them, or copy them them from your firefox's cache(?) folder. A firefox addon that works great for this is called 'video download helper'.

I hope this will help.
James.

---

### Post by jrusso2 on 2009-12-13
> **monraaf said:**
> The Adobe flash player is closed source, go complain to Adobe about their crappy software.

Always worked fine for me.  Be glad Adobe even makes a Linux port or we would be stuck with nothing.

Its really not worth their effort for 1% of the desktop.

---

### Post by marchost on 2009-12-14
Hi all, thanks for your replies... I forgot to say that im using AMD64 version.

I really tried all solutions :
1)gnuflash
2)from adobe
3)from software center

Since I reinstalled it from software center, it seems better but i'm still having issues. Sometimes, for no apparent reasons, when I have tabs open in FF where flash banners are displayed, CPU usage ( 1 core of a T7200) can go up to 100% and FF becomes unresponsive.

The point of the thread was not really to get a solution (I think I tried every solution out there) but to point out (and discuss) that Ubuntu should concentrate on such important issues before implementing new "cool" features that in the end, dont improve productivity... Indeed, it's adobe fault as well but i'm sure with all bright people working at Ubuntu, they could find a simple solution.

---

### Post by LinuxFanBoi on 2009-12-14
The thing that drives me nuts is how flash doesn't allow a lot of "interactive" flash apps don't work.  It could be bad programming, But I have to put some of the blame on adobe for not making it one code set for both platforms.

If there is something about flash that I don't know, and thus I am mistaken in my opinion, please explain.

---

### Post by perce on 2009-12-14
I've never had serious problems with flash.

---

### Post by cariboo on 2009-12-14
I had some problems with the flash version installed from the repositories, yesterday on my Karmic powered media center pc. remove that version and installing the lastest 64-bit from adobe solved the problem. I went from 90-100% cpu usage down to about 15%. When installing flash from Adobe you have to uninstall the repository version as well as nspluginwrapper on 64-bit versions.

I always install libflashplayer.so to /usr/lib/mozilla/plugins, so that it is available system wide.

---

### Post by Keyper7 on 2009-12-14
> **marchost said:**
> Hi all, thanks for your replies... I forgot to say that im using AMD64 version.

Of Ubuntu or of the plugin?

By default, the 64-bit version of Ubuntu installs the 32-bit plugin with a special wrapper to make it work. That's because the 64-bit version given by Adobe is still an alpha and is not fully reliable on, for example, security. As far as performance goes, however, it is much better than the 32-bit version.

Using it, I can smoothly watch HD videos in YouTube in full screen.

> **marchost said:**
> The point of the thread was not really to get a solution (I think I tried every solution out there) but to point out (and discuss) that Ubuntu should concentrate on such important issues before implementing new "cool" features that in the end, dont improve productivity... Indeed, it's adobe fault as well but i'm sure with all bright people working at Ubuntu, they could find a simple solution.

Canonical should concentrate on what they **can** do. Even for a million dollars, they won't find a magical programmer who can read binary and change how the closed-source plugin works.

It's not Adobe's fault "as well". This is **entirely** Adobe's fault.

---

### Post by LowSky on 2009-12-14
> **ankspo71 said:**
> Hi,
I know the flash problems in linux too well. When I was using my intel celeron 2ghz which is a single core processor,  flash caused firefox to max out my cpu up to 100%. Since then I have upgraded my processor to a Pentium 4 3.0ghz (which is almost like having a dual core processor because of 'hyperthreading'), and I have not had a major problem with flash since. 


Pentium 4 with HT is nothing a vitualized dual-core. Its a gimmick that brings maybe 5-30% boost to your processor, but in turn wastes more energy. The reason that P4 seems faster is the 1 extra Ghz and the Level 2 Cache, that were lacking on the Celeron. My Intel Atom based netbook has HT tech and the thing is slow no matter how many cores it pretends to have.
To the OP:
If you use 32bit you should not have any flash problems, if you do something is really borked on your PC. I wont lie Flash is a memory hog,it burns through system cache and in many cases Java is running at the same time causing you even more grief. Stay away from HD videos if your monitor and graphics chip are not built for them.
If you have used 64bit for years like I have, you know the pain of flash and the godsend it was to have even the Alpha edition for 64bit.

---

### Post by crimesaucer on 2009-12-14
> **perce said:**
> I've never had serious problems with flash.

Me neither.


When I used xubuntu from version 6.06 to version 7.04 the flashplugin worked fine. It was on an "i386" install and my processor was an Intel Celeron M. On that same laptop I installed Arch "i686" for another year and had absolutely NO flash problems. installation was easy on both distros, all I had to do was follow the Ubuntun wiki page for the first year, and the Arch wiki page for the second.


A third year later I got a new notebook with an AMD Turion 64 x2 processor so I now needed flash to work for Arch "x86_64".


At that point it was done with the nsplugginwrapper and lib32's, which wasn't too difficult to install..... again, just follow instructions on the wiki page. 


Then Adobe finally came out with an official flashplugin for 64-bit Linux. Since then flash has been pretty very solid. I'm currently using the official 64-bit "flashplugin 10.0.42.34-1" and have no complaints.

---

### Post by NoaHall on 2009-12-14
I don't have problems. I can install it properly. So there isn't "always a problem".

---

### Post by wojox on 2009-12-14
> **webbdawg said:**
> Wojpx, I think the point of the thread is that Flash is so prevlant everywhere there is no reason the developers should not have a bullet proof version working.

Can you imagine the net with out flash player. If FF can do it for windows then why is it so tough for linux??

First of all it's not Ubuntu, it's Linux in general. Could you point me to a distro where it works flawlessly? 

A net without Flash? That would be great. Then I wouldn't need FlashBlock enabled. Flash is over rated and over used. There are plenty of other scripting languages out there that do a way better job when used properly.

Microsoft and Adobe are in bed together. Nothing I can do...

It seems to run pretty decent from my end.

---

### Post by nothingspecial on 2009-12-14
I have had no problem with flash ever.

Mind you I`ve never used windows so I can`t compare. Does it do anything else on there except play moving pictures of some sort?

---

### Post by blur xc on 2009-12-14
How much of it has to do w/ your video card?  I have a good nvidia card w/ the proprietary drivers and flash works great- cpu usage can be a bit high, but I've got a lot of that as well.

Is there a 32bit version from the Adobe site that's better than the one from the repos?  What about netbooks, I've recently dual booted an Asus Eee PC and flash works, but online games play in SUPER slow motion.  Youtube works though.  I haven't done anyting to try and optomize that system yet.

Thanks,
BM

---

### Post by blur xc on 2009-12-14
> **nothingspecial said:**
> I have had no problem with flash ever.

Mind you I`ve never used windows so I can`t compare. Does it do anything else on there except play moving pictures of some sort?

try [www.teagames.com](www.teagames.com)

I bring that up a lot, but it's the only real online flash game site I visit regularly.  My wife plays flash games on Facebook- Farkle, that fish tank/aquarium game, Bedjeweled Blitz...etc...

BM

---

### Post by V for Vincent on 2009-12-14
Haven't had any issues with it since I started using the adobe plugin. Which, IIRC, is just a matter of enabling universe and entering apt-get install flashplugin-nonfree.

---

### Post by ankspo71 on 2009-12-14
> **LowSky said:**
> Pentium 4 with HT is nothing a vitualized dual-core. Its a gimmick that brings maybe 5-30% boost to your processor, but in turn wastes more energy. The reason that P4 seems faster is the 1 extra Ghz and the Level 2 Cache, that were lacking on the Celeron. My Intel Atom based netbook has HT tech and the thing is slow no matter how many cores it pretends to have.


This is all true, and might I also add that my new new processor is rated 3.0ghz at 800Mhz, instead of the older celeron's 2.0 400Mhz specs :D. Virtualized cores or not, my system needed all the help it could get at the time and the available flash player(s) were the most irritating of all problems of all time for me. I can also see each virtualized core handling those simple multi-tasks I couldn't do before and I feel the enabled hyperthreading is a big help in this department. As long as I can easily run the 'full' default Ubuntu install now (instead of a minimal gnome install using the mini cd) and play flash I am happy for now. I am far from a computer expert, so seeing your experience with the P4 makes me feel even more[COLOR=Red] luckier [/COLOR]than I originally thought about coming this far in building this system. But this isn't a topic that actually concerns processors... I chose to include my experience [COLOR=Red]to show how **poor** adobe's linux flash player performed on my low end system[/COLOR], not to recommend anyone getting a Pentium 4. I hope my post didn't show otherwise. I'm sorry to hear your experience with the Pentium 4 hasn't been as good. A good friend of mine also said he didn't like P4's that much either, and he is now a AMD 64bit user and won't settle for less. I'm okay with that because I can't settle for less than what I have either.;)

---

### Post by sandyd on 2009-12-14
> **marchost said:**
> I will never understand why, release after release, flash is still not working properly in Ubuntu... It's a major issue they should work on before adding eyes candy or faster boot time (9.04) which in the end, we dont really care about. 

I mean, I can get flash working BUT it 1) doesnt work all the time (issue with youtube & many others) and 2)it's very slow (when it works). Same problem with the free (gnuflash) or adobe version.
i got three worlds for ya
adobe propriety software

-----------------------
side-note
at least were getting somewhere.
the latest update sped things up a lot.

---

### Post by sandyd on 2009-12-14
> **lowsky said:**
> pentium 4 with ht is nothing a vitualized dual-core. Its a gimmick that brings maybe 5-30% boost to your processor, but in turn wastes more energy. The reason that p4 seems faster is the 1 extra ghz and the level 2 cache, that were lacking on the celeron. My intel atom based netbook has ht tech and the thing is slow no matter how many cores it pretends to have.
To the op:
If you use 32bit you should not have any flash problems, if you do something is really borked on your pc. I wont lie flash is a memory hog,it burns through system cache and in many cases java is running at the same time causing you even more grief. Stay away from hd videos if your monitor and graphics chip are not built for them.
If you have used 64bit for years like i have, you know the pain of flash and the godsend it was to have even the alpha edition for 64bit.
+1

---

### Post by sandyd on 2009-12-14
> **blur xc said:**
> How much of it has to do w/ your video card?  I have a good nvidia card w/ the proprietary drivers and flash works great- cpu usage can be a bit high, but I've got a lot of that as well.

Is there a 32bit version from the Adobe site that's better than the one from the repos?  What about netbooks, I've recently dual booted an Asus Eee PC and flash works, but online games play in SUPER slow motion.  Youtube works though.  I haven't done anyting to try and optomize that system yet.

Thanks,
BM
I think it doesn't have to do with the video card, but has more to do with the **Video Drivers.** Video on Linux is generally slower (in fact, much much slower) than on windows. The FPS is way higher on windows.
If you have a high-end system, say for example an alienware desktop, the video will work fine - because even though the fps/quality is lower in linux, it is still high enough to display the video without a hitch.

that saying, my laptop (ati 3650HD 1GB RAM) can play almost every linux game that i see in the repo. (went to my local library and downloaded the entire repo's game section onto my portable Hard Drive). We dont notice this in games and such programs, because the developers have already anticipated this. They KNOW that we aren't gunna have the highest FPS and quality on linux, so they tune down the quality in the application itself.

When i played the games on my overpowered desktop/workstation (used to actually be a server)( 2x Nvidia 9800 SLI) there wasn't any real difference in the video quality or anything. developers were DEFINATELY not excepting me to run games on this computer.....

---

### Post by murderslastcrow on 2009-12-14
Some integrated video cards just don't play nice with Flash, since Flash isn't exactly the best port at the moment. However, there is only one computer I've installed Karmic on that has had any problems with Flash playback, and it's only on games, not on YouTube.

I would suggest upgrading to Karmic if you haven't already. And perhaps accepting that Adobe's Linux port of flash isn't really a shining example of the excellence of the Linux desktop, but it's not horrid either. Hopefully with Adobe collaborating with Google on Chrome OS, we'll get a much better port of Flash by that time.

---

### Post by squilookle on 2009-12-14
I haven't had problems with flash on linux for a while now, other than cpu usage being a little high. 

I usually install from adobe now rather than trying to get it from the repos. 

I'm using crunchbang cat the minute and didn't have to install flash at all on my current install as it came with. 

Which is an idea... if you have difficulties getting this stuff working,you might be better off with mint, as that comes with flash installed too.

---

### Post by blur xc on 2009-12-14
> **cariboo907 said:**
> I had some problems with the flash version installed from the repositories, yesterday on my Karmic powered media center pc. remove that version and installing the lastest 64-bit from adobe solved the problem. I went from 90-100% cpu usage down to about 15%. When installing flash from Adobe you have to uninstall the repository version as well as nspluginwrapper on 64-bit versions.

I always install libflashplayer.so to /usr/lib/mozilla/plugins, so that it is available system wide.

For a 32 bit system, if I want to try the version from the Adobe website, what (if any) packages do I need to uninstall first?  I downloaded the tar.gz and I'm ready to install, just want to make sure what I need to uninstall first.

Thanks,
BM

---

### Post by Warpnow on 2009-12-14
You know what I hate about playgrounds? How some, its not very sunny. I mean, they should get on top of that. Why build a new slide if its going to be nasty outside and ruin everyone's fun?

Ubuntu can't do anything about ADOBE flash. However, adobe flash has never given me a problem, ever, so...not sure what you mean. Just do sudo apt-get install flashplugin-nonfree

---

### Post by Megrimn on 2009-12-15
here's one for the 64-bit users, since we're discussing this stuff.  

I have to copy the libflash.so file to the plugins directory every time I restart firefox in order for it to work at all, in which it works perfectly until the restart.  It's as if running firefox once breaks it or something... any ideas?  I already uninstalled any other versions of flash and the nspluginwrapper, and this has me quite confunded.

---

