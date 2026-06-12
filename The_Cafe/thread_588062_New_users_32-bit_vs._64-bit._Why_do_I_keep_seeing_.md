---
title: "New users: 32-bit vs. 64-bit. Why do I keep seeing so many 64-bit users?"
date: 2007-10-23
forum: The Cafe
---

### Post by bmartin on 2007-10-23
I was looking for good reasons for running a 64-bit operating system, but I really couldn't find anything. The most compelling article I found is [this one]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/69585-should-you-choose-32-bit-64-bit-linux.html").

I see a lot of users are installing 64-bit Ubuntu, which is fine with me. They're causing themselves a lot of unnecessary pain. Unless you have more than 4GB of memory, I can't think of a big advantage.

When it comes to FOSS, any open-source program can be compiled to run on a 64-bit machine; you simply need the GNU GCC tools for that architecture. Proprietary software is another story. There's a significant amount of 32-bit code that won't run with a 64-bit kernel.

People are increasingly turning to laptops instead of desktops for their computing needs, and it seems that everyone's trying to connect to a wireless router. A 64-bit kernel means that you need a 64-bit driver. These drivers are often very hard to track down, if they exist at all.

When I ran Gentoo, I used to cross-compile frequently, creating custom software packages for my non-Gentoo distributions so that I could customize them. Using architecture-specific optimizations yields minuscule performance gains (around 2%). As a side, it's my contention that Gentoo is lighter and faster than other distributions, but it's USE flags that make it that way (and not CFLAGS, if you speak GCC). I have my CFLAGS set on Ubuntu, just in case I decide to compile something (e.g., I run Battle for Wesnoth v1.3.8, compiled from source with the -O2 optimization flag; no other flag seems worthwhile).

New users have a lot of headaches. I feel that this fact is compounded by the 32-bit vs. 64-bit issue; many new users choose a 64-bit OS when a 32-bit one would suit them just fine. I'd like to see Ubuntu reach out to potential users, explaining to them before they grab the 64-bit version that there aren't that many tangible benefits of the 64-bit version, while the hurdles can be quite burdensome.

---

### Post by Phil Airtime on 2007-10-23
.

---

### Post by markp1989 on 2007-10-23
i tried 32bit and 64bit feisty, and the 64bit was significantly faster

 i also tried 64bit and 32bit gusty., the 32bit was alot more responsive

---

### Post by Nunu on 2007-10-23
> **markp1989 said:**
> i tried 32bit and 64bit gusty, and the 64bit was significantly faster

 i also tried 64bit and 32bit gusty., the 32bit was alot more responsive

Depends on your CPU, its a bit of a waist to run a 32 bit OS on a 64 bit chip. and if you have a 32 bit chip there shouldn't be a 64 bit OS running it... or is there a way to force ubuntu 64 on a 32 bit CPU??? and dose it offer better performance. Logically i can't see it even being possible

---

### Post by Shin_Gouki2501 on 2007-10-23
> **markp1989 said:**
> i tried 32bit and 64bit gusty, and the 64bit was significantly faster

 i also tried 64bit and 32bit gusty., the 32bit was alot more responsive
*read the  post*
*readitagain*
wait that sounds strange did u misstype?!

So what ? the 64 bit GUTSY was faster and the 32 bit GUTSY was more responsive.. i see.. not what are u trying to say?!

---

### Post by glupee on 2007-10-23
I use 64-bit for the same reason i use linux.
The more people use it the faster it will become mainstream. While not all applications are native 64-bit, all new processors being made are, so IMHO it's only reasonable to support its development. 

It's not perfect right now, but it does work. With a little research you could find a way to do everything you need to do and it's not much harder than in 32-bit.
Also, i paid for my machine so i'm going to use it to its full potential, or as close as i can get to it.

---

### Post by markp1989 on 2007-10-23
> **Shin_Gouki2501 said:**
> *read the  post*
*readitagain*
wait that sounds strange did u misstype?!

So what ? the 64 bit GUTSY was faster and the 32 bit GUTSY was more responsive.. i see.. not what are u trying to say?!

sorry thansk for noticing, the top line was meant to say feisty

---

### Post by rsambuca on 2007-10-23
> **bmartin said:**
> I was looking for good reasons for running a 64-bit operating system, but I really couldn't find anything. The most compelling article I found is [this one]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/69585-should-you-choose-32-bit-64-bit-linux.html").

I see a lot of users are installing 64-bit Ubuntu, which is fine with me. They're causing themselves a lot of unnecessary pain. Unless you have more than 4GB of memory, I can't think of a big advantage.

When it comes to FOSS, any open-source program can be compiled to run on a 64-bit machine; you simply need the GNU GCC tools for that architecture. Proprietary software is another story. There's a significant amount of 32-bit code that won't run with a 64-bit kernel.

People are increasingly turning to laptops instead of desktops for their computing needs, and it seems that everyone's trying to connect to a wireless router. A 64-bit kernel means that you need a 64-bit driver. These drivers are often very hard to track down, if they exist at all.

When I ran Gentoo, I used to cross-compile frequently, creating custom software packages for my non-Gentoo distributions so that I could customize them. Using architecture-specific optimizations yields minuscule performance gains (around 2%). As a side, it's my contention that Gentoo is lighter and faster than other distributions, but it's USE flags that make it that way (and not CFLAGS, if you speak GCC). I have my CFLAGS set on Ubuntu, just in case I decide to compile something (e.g., I run Battle for Wesnoth v1.3.8, compiled from source with the -O2 optimization flag; no other flag seems worthwhile).

New users have a lot of headaches. I feel that this fact is compounded by the 32-bit vs. 64-bit issue; many new users choose a 64-bit OS when a 32-bit one would suit them just fine. I'd like to see Ubuntu reach out to potential users, explaining to them before they grab the 64-bit version that there aren't that many tangible benefits of the 64-bit version, while the hurdles can be quite burdensome.
Did you look at the date on that link?  It is over a year old!!!  Given how quickly the development of linux moves, that article is too outdated to base any conclusions on.  You talk of "unnecessary pain", and "hurdles can be quite burdensome".  These things, thanks to the extensive work by the developers, are a thing of the past.  As far as advantages, which you seem to think are nonexistent - 30% performance gains in many tasks such as video transcoding/editing, audio ripping, etc.  Try backing up half your CD collection in 32bit, and half in 64 bit, and you will see for yourself the difference.

Flash works, java works, basically there is little reason NOT to use 64bit these days.

---

### Post by Paul820 on 2007-10-23
> They're causing themselves a lot of unnecessary pain.:confused:

Why does it cause unnecessary pain? Do you mean software or what? When i had 32 bit feisty and switch to 64 bit there was no difference at all with software available. And my hardware worked fine on both, no difference. I am running gutsy 64 and nothing is wrong with this either. I have a 64bit processor so i am going to use the 64bit OS.

The reason i used 32bit feisty was because people were spreading FUD about it not working properly and flash was hard to install etc. :---) A little search for the flash fix was easy enough with the script provided by kilz and everything else was was as easy as clic....click.

---

### Post by conehead77 on 2007-10-23
I use 64bit because i can. I dont use many proprietary software and i dont use wireless though.

---

### Post by OffHand on 2007-10-23
> **rsambuca said:**
> 
Flash works, java works, basically there is little reason NOT to use 64bit these days.

Codecs?

---

### Post by DigitalDuality on 2007-10-23
d

---

### Post by Anessen on 2007-10-23
What codec issues are there with 64bit? Also, is there a Flash plugin for 64bit Firefox?

---

### Post by glupee on 2007-10-23
> **Anessen said:**
> What codec issues are there with 64bit? Also, is there a Flash plugin for 64bit Firefox?
I have no codec issues at all... anyone else?
and yes there is 64bit flash for firefox. It comes included in gutsy.

---

### Post by tribaal on 2007-10-23
Codecs and flash plugins are installed the same way than on 32bits since Gutsy: Ubuntu just pops up a "would you like to install this package" dialog... How hard is that?

The only thing that is not yet fully supported and that can be a pain at some times is the lack of java *firefox plugin*. The java JRE and JDK work just fine, but there is currently not Sun java plugin for 64bit systems.

Wireless worked out of the box for every single laptop I installed gutsy 64bits on (about 10).

Most of what people say about 64bit is either just repeating what they have heard but didn't try for themselves, or outdated.

Hope this clarifies... :)

- trib'

---

### Post by rsambuca on 2007-10-23
> **OffHand said:**
> Codecs?

Codecs work.

---

### Post by distroman on 2007-10-23
I guess FUD is a two way street you just I to find out for yourself.
I do feel 64 bit is well supported but the only reason for most to run 64 bit would be to somehow support/push development.

---

### Post by rsambuca on 2007-10-23
> **DigitalDuality said:**
> meh, 64 bit will never take off completely.

Too many applications don't have 64bit versions, not to mention drivers.   Windows 64 bit and Linux 64 bit are plagued with a lot of the same problems.  Breaking the 32bit paradigm will prove to be quite difficult.

People said this about 32 bit when it came out, and they were wrong.  64bit will be the norm within a few years.

---

### Post by Paul820 on 2007-10-23
No codec issues here. I have flash and can play .rm files, avi, quicktime, encrypted DVD's etc...

---

### Post by speedwell68 on 2007-10-23
I have an Acer Aspire with an AMD Turion 64 chip.  When I first migrated from M$ Windoze to Linux I used 32bit Ubuntu on my old Toshiba Satellite and when I got my Acer I stuck with 32bit Feisty.  The automatic upgrade of Gutsy screwed right up so I decided to go for 64 bit and a clean install.  Gotta say I am impressed, it has worked out of the box, a much smoother install than with Feisty on the same machine.  I have even got Compiz Fusion to work with my ATI card, something I could never do on feisty.  I don't see the point in investing in 64 bit hardware and still running a 32 bit OS.

---

### Post by bmartin on 2007-10-23
> **rsambuca said:**
> People said this about 32 bit when it came out, and they were wrong.  64bit will be the norm within a few years.
I disagree with many of the other claims people have been making about 64-bit advantages, but this one is very valid; sooner or later, computers, will start appearing with more the 4GB of RAM; the memory addressing alone will require 64-bit space.

I found another (old) link [here]("http://www.phoronix.com/scan.php?page=article&item=616&num=2"),  with two similar processors. The only significant difference was the 64-bit processor's ability to compile the Linux kernel, which is probably worthwhile if you do that sort of thing frequently. On other metrics, including transcoding, the speeds were very close, with the LAME encoding favoring the 32-bit processor. Unless some magical voodoo optimization has occurred within the last year, there's no way a 30% boost would be seen with 64-bit processors... and I haven't heard of any such performance gains.

---

### Post by Dribbel on 2007-10-23
> **markp1989 said:**
> i tried 32bit and 64bit feisty, and the 64bit was significantly faster

 i also tried 64bit and 32bit gusty., the 32bit was alot more responsive

So I better run Gutsy 32bit instead of 64bit with my AMD X2
'Cause I've had a lot of problems installing software and tried a lot, but it never seems to work in 64bit.

Flash doesn't even work (Kubuntu Gutsy Firefox)

Btw how do I get beans :lolz:

---

### Post by OffHand on 2007-10-23
> **Paul820 said:**
> No codec issues here. I have flash and can play .rm files, avi, quicktime, encrypted DVD's etc...

This is what used to give people major headaches. I am happy to hear that all works now without using fakeroot and what have you. I would try it but I just finished doing a clean install and setting everything up again and I really don't feel like going through that again at this point. Probably I'll leave it like it is untill the next release. But like I said... great that everything works OTB now.

---

### Post by bmartin on 2007-10-23
> **Dribbel said:**
> So you say it's a better idea to run 32bit 7.10 with an AMD64 cpu?
'Cause I've had a lot of problems installing software and tried a lot, but it never seems to work in 64bit.
There aren't any drawbacks to installing 32-bit 7.10 (Gutsy) on a 64-bit processor. 64-bit processors work just as well as 32-bit processors when running 32-bit operating systems and software.

Opinions on this thread vary greatly. I've posted a couple links to web pages that say there are no significant gains when using a 64-bit processor with a 64-bit OS. I'd personally go with 32-bit Gutsy; take my opinion with a grain of salt. There are a lot of claims floating around to the effect of "64-bit problems are a thing of the past"; I don't feel like sacrificing one of my existing computers to test the theory.

If you're an adept Linux user and want to try each one, make a separate partition for your home directory, then install one of them. Next time, when you install the other one, **don't format the /home partition** and you can keep all of your user data intact.

Poke around on Google and various Linux forums. 64-bit Linux seems to take more work and it has caused many people lots of headaches. If you want something simple and functional, opt for a 32-bit OS.

---

### Post by bruce89 on 2007-10-23
> **bmartin said:**
> Poke around on Google and various Linux forums. 64-bit Linux seems to take more work and it has caused many people lots of headaches. If you want something simple and functional, opt for a 32-bit OS.

Depends what you're trying to do. My AMD64 installation is fine., and I can't think of anything I can't do (apart from X-Plane).

---

### Post by hellmet on 2007-10-23
I can do everything on 64bit that I was able to do on 32bit.. I mean EVERYTHING..

---

### Post by qazwsx on 2007-10-23
64 bit runs  perfectly on mine box. Absolutely right solution. Gutsy even makes 64 bit very easy.
There are huge performance differences  on some apps. Lame is a very lame example. Just look at oggenc. It is a really wonderful app on 64 bit. 
Linux supports multiple architectures and I am a Linux user!

---

### Post by misfitpierce on 2007-10-23
64 is most responsive and fast. I would recommend 100% and ten fold. Only OS I dont use it on is Linux Mint b/c its 32 bit only. But hey cant win em all :)

---

### Post by helliewm on 2007-10-23
I have had no codec issues at all. 64 bit works brilliantly including flash, java etc. I have 4 gig of ram in my Desktop so it was the way to go but I have also installed on both my laptops too without any problems whatsoever.

Helen

---

### Post by cogitordi on 2007-10-23
> **bmartin said:**
> I was looking for good reasons for running a 64-bit operating system, but I really couldn't find anything...

Or you didn't really think about it. RAM is fast and getting faster. It's also getting CHEAPER. People are using very powerful computers for video editing and rendering. New computers will all support a large amount of RAM. The top Apple box right now can use >>16GB<< of RAM. 

This is where the technology is going. And Linux is already on that train. If you do some research about animated movies and CGI, you'll discover that many computer farms are running Linux and are loaded with RAM.

The fact that Windows isn't useful as a 64-bit platform is evidence that Windows is not even a player in these leagues. 

> New users have a lot of headaches. I feel that this fact is compounded by the 32-bit vs. 64-bit issue; many new users choose a 64-bit OS when a 32-bit one would suit them just fine.

Ah, so that's your only concern. I think Shuttleworth & Co. understand their business rather well. Ubuntu is the Number 1 distribution.

---

### Post by samb0057 on 2007-10-23
I use 32-bit only because of proprietary things such as the flash plugin.

---

### Post by rsambuca on 2007-10-23
> **bmartin said:**
> There aren't any drawbacks to installing 32-bit 7.10 (Gutsy) on a 64-bit processor. 64-bit processors work just as well as 32-bit processors when running 32-bit operating systems and software.

Opinions on this thread vary greatly. I've posted a couple links to web pages that say there are no significant gains when using a 64-bit processor with a 64-bit OS. I'd personally go with 32-bit Gutsy; take my opinion with a grain of salt. There are a lot of claims floating around to the effect of "64-bit problems are a thing of the past"; I don't feel like sacrificing one of my existing computers to test the theory.

If you're an adept Linux user and want to try each one, make a separate partition for your home directory, then install one of them. Next time, when you install the other one, **don't format the /home partition** and you can keep all of your user data intact.

Poke around on Google and various Linux forums. 64-bit Linux seems to take more work and it has caused many people lots of headaches. If you want something simple and functional, opt for a 32-bit OS.Odds are you will run into issues whether you are running 32bit or 64bit.  It is hardly a "sacrifice" to run 64bit Ubuntu.  This is, like many other posts, just pure FUD.

---

### Post by qazwsx on 2007-10-23
OMG. Just compiled mplayer and x264 while using 32 bit distro . I get  3 times less fps under 32 bit than I get while using 64 bit :shock:

Massive diffrence on  multitasking as well .

---

### Post by songshu on 2007-10-23
> **qazwsx said:**
> OMG. Just compiled mplayer and x264 while using 32 bit distro . I get  3 times less fps under 32 bit than I get under 64 bit :shock:

you serious?

---

### Post by songshu on 2007-10-23
> **qazwsx said:**
> 

Massive diffrence on  multitasking as well .

now you tell me that is pure and only due to the 32 / 64 bit?

---

### Post by |2A|N on 2007-10-23
> **bmartin said:**
> I was looking for good reasons for running a 64-bit operating system, but I really couldn't find anything. The most compelling article I found is [this one]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/69585-should-you-choose-32-bit-64-bit-linux.html").

I see a lot of users are installing 64-bit Ubuntu, which is fine with me. They're causing themselves a lot of unnecessary pain. Unless you have more than 4GB of memory, I can't think of a big advantage.

When it comes to FOSS, any open-source program can be compiled to run on a 64-bit machine; you simply need the GNU GCC tools for that architecture. Proprietary software is another story. There's a significant amount of 32-bit code that won't run with a 64-bit kernel.

People are increasingly turning to laptops instead of desktops for their computing needs, and it seems that everyone's trying to connect to a wireless router. A 64-bit kernel means that you need a 64-bit driver. These drivers are often very hard to track down, if they exist at all.

When I ran Gentoo, I used to cross-compile frequently, creating custom software packages for my non-Gentoo distributions so that I could customize them. Using architecture-specific optimizations yields minuscule performance gains (around 2%). As a side, it's my contention that Gentoo is lighter and faster than other distributions, but it's USE flags that make it that way (and not CFLAGS, if you speak GCC). I have my CFLAGS set on Ubuntu, just in case I decide to compile something (e.g., I run Battle for Wesnoth v1.3.8, compiled from source with the -O2 optimization flag; no other flag seems worthwhile).

New users have a lot of headaches. I feel that this fact is compounded by the 32-bit vs. 64-bit issue; many new users choose a 64-bit OS when a 32-bit one would suit them just fine. I'd like to see Ubuntu reach out to potential users, explaining to them before they grab the 64-bit version that there aren't that many tangible benefits of the 64-bit version, while the hurdles can be quite burdensome.

I agree and as a fairly new user to the Linux world I quickly uninstalled x64 and went back to Gutsy x86. The only reason why I tried x64 was because I have 4GB ram and wanted to use it all beingIi paid for it but I couldnt get flash working correctly under x64 despite all the tuts available so am back to x86 again. I see you live in Va Beach As well small world :lolflag:

---

### Post by FredB on 2007-10-23
> **|2A|N said:**
> I agree and as a fairly new user to the Linux world I quickly uninstalled x64 and went back to Gutsy x86. The only reason why I tried x64 was because I have 4GB ram and wanted to use it all beingIi paid for it but I couldnt get flash working correctly under x64 despite all the tuts available so am back to x86 again. I see you live in Va Beach As well small world :lolflag:

For flash : sudo aptitude install flashplugin-nonfree

Too complicated ?

64 bits IS USABLE ! No more bad excuses now !

---

### Post by FredB on 2007-10-23
> **samb0057 said:**
> I use 32-bit only because of proprietary things such as the flash plugin.

So why ubuntu coders made meta package flashplugin-nonfree available ?

For nothing ?

---

### Post by |2A|N on 2007-10-23
> **FredB said:**
> For flash : sudo aptitude install flashplugin-nonfree

Too complicated ?

64 bits IS USABLE ! No more bad excuses now !

Wasn't complicated and I hated not being able to use x64 Gutsy but when I tried that I got an error about something missing so it wouldn't install. I should have came here for help but i was to impatient and went back to Gutsy x86. Maybe i will try again and if the same problem will come back here and post for help :)

---

### Post by matthewdhandley on 2007-10-23
When I started using Ubuntu back in March my friend told me to use 32-bit Edgy because there were lots of problems with the 64-bit edition. So for Edgy and Feisty I've been using 32-bit. When Gutsy was released I decided to do a clean install and try 64-bit. It was like I was suddenly using a new computer. Everything runs noticeably faster, and I haven't had a single problem. Not even with flash.

---

### Post by qazwsx on 2007-10-23
> **songshu said:**
> you serious?
totally. I am quite amazed. Dual Core CPU usage ~180% appoximately same on 64 bit.

---

### Post by ssam on 2007-10-23
some people work with big data sets and high precision numbers.

last week i heard someone complaining about not having 128bit CPUs. (he does simulations of particle accelerators)

---

### Post by songshu on 2007-10-23
> **qazwsx said:**
> totally. I am quite amazed. Dual Core CPU usage ~180% appoximately same on 64 bit.

then what about all those benchmarks that show only a marginal difference?

i'm sure your computer runs faster then before and will not call you a liar, but i do suspect that there is some other reason to it then the 64 bit architecture

---

### Post by songshu on 2007-10-23
i have kept my architecture strictly 32bit so far, but good to hear that the mayor drawbacks ar becomming less. think i might consider to go 64 bit in a year or two

---

### Post by forrestcupp on 2007-10-23
So did they finally get Windows Media Codecs working in 64 bit?  I've seen people talking about rm, avi, flash, java, etc., but no one has mentioned Windows Media.  Does it work now?

---

### Post by nirkir on 2007-10-23
I consider myself a newbie in the Linux area. I'm using 64 bit Gutsy and I get everything I want to work. No problem with codecs, flash and anything else. The system works fast.

I believe that expanding the install base for 64 installations will benefit everyone in the long run. Just like installing Linux is the only way to create an alternative for Windows. Just like installing Firefox creates an alternative for IE.

If you got 64 bit enabled CPU - go ahead and use a 64 bit system.

---

### Post by rsambuca on 2007-10-23
> **forrestcupp said:**
> So did they finally get Windows Media Codecs working in 64 bit?  I've seen people talking about rm, avi, flash, java, etc., but no one has mentioned Windows Media.  Does it work now?

Yes.

---

### Post by d_in_Conduct on 2007-10-23
I'm running gutsy-32 for my production system and experimenting with gutsy-64-based Ubuntu Studio on a spare partition.  

The only problems so far have been due to gutsy, not 64-bit.  They simply broke rt2500 wireless in gutsy.  I was able to compile the legacy rt2570usb driver from serialmonkey in 32-bit and get it working there.  It seems that the kernel sources are laid out differently in 64-bit because I haven't come even close to compiling that driver there.  Maybe I don't have all the sources.  

Fortunately, 32-bit gutsy is still plenty fast for what I do and, I suspect, what most people do.  So it's not a tough decision to make.  If you have to time to test out 64-bit, do it and see if it does everything you need.  If not, most people aren't giving up much power by sticking to 32-bit for another cycle.

Just an opinion with anecdotal evidence for a narrow segment of users, like most posts.

---

### Post by Billy_McBong on 2007-10-23
[COLOR="Blue"]i use 64-bit gutsy and everything works perfectly fine
most of the problems you here about are no longer an issue(flash, codecs, ext)

if you have a 64-bit processor i suggest you use it to its full potential[/COLOR]

---

### Post by igknighted on 2007-10-23
OMG, no one show this thread to Kilz... people might die.

But I think we should push the 64bit version as much as possible.  The simple fact is it is better and faster at lots of tasks that many users do.  A/V encoding for example.  I for one rip CDs all the time and do not feel that I am in the minority here.  And honestly, flash is so easy and with OSS Java on the way with a 64bit plugin, there isn't much reason NOT to.

---

### Post by songshu on 2007-10-23
> **igknighted said:**
> OMG, no one show this thread to Kilz... people might die.

But I think we should push the 64bit version as much as possible.  The simple fact is it is better and faster at lots of tasks that many users do.  A/V encoding for example.  I for one rip CDs all the time and do not feel that I am in the minority here.  And honestly, flash is so easy and with OSS Java on the way with a 64bit plugin, there isn't much reason NOT to.

before we all start saying Amen and Halleluja, there is no reason WE should push anything, first of all lets not forget that a lot of general optomisations have been made for this release so do not compare feisty 32 bit with gutsy 64 bit wich i think many are doing here.

did any body used 32 bit AND 64 bit on the exact same machine? if so, please show some benchmarks

---

### Post by dmacdonald111 on 2007-10-23
My machine is 64 bit, but only has 512Mb ram (on this one). Obviously I will be upgrading the ram in the very near future, but as I have used the 64bit version before and it worked well, I will definitely be giving it a go.

---

### Post by hellmet on 2007-10-23
Windows x64 XP sucks really.. I even received 64bit drivers for XP, but they don't install. Some s/w don't install too. Ubuntu 64 is so much better. Everything works..

---

### Post by forrestcupp on 2007-10-24
Well, if Flash, Java, Windows Media codecs, and all of the other codecs and drivers work well with 64-bit, I only have one more question.

Does every single obscure app and game that you run have to be compiled for 64-bit, or only just the system level stuff?

---

### Post by bmartin on 2007-10-24
> **cogitordi said:**
> Ah, so that's your only concern. I think Shuttleworth & Co. understand their business rather well. Ubuntu is the Number 1 distribution.
Yeah, you're right. It's the number one distribution... except on distrowatch.com, where it's about 500 HPD behind PCLinuxOS. Wireless support for Ubuntu seems to be getting worse. Load up the PCLinuxOS Live CD. Do you notice anything? I'm not a huge fan of KDE (or GNOME; I think they both stink; I refuse to use either one), but I'm more impressed with how they run things there.

I've considered switching. I've got a lot of time invested in this distro. I do some development work, mostly high-level stuff in regards to wireless functionality. A lot of people thought Fedora would be on top forever. People move on when their OS doesn't do what they want it to. That's why people move between OS's. There's always hesitation to move, but if your hardware doesn't work on the new OS, how can you switch? Legacy support is just as important as support for newer devices. A lot of people will shun an OS simply because of its lack of driver support. An example of an OS with excellent driver support is XP; most things don't work out of the box, but there ARE drivers and they DO work. I have a year-old laptop here and the ACPI and the ENE card reader don't work in Ubuntu. It won't even boot in PCLinuxOS or Fedora because no processor is detected. What's the point in installing another OS if the ACPI isn't going to be fixed? I just run Windows on that machine.

> **cogitordi said:**
> Or you didn't really think about it. RAM is fast and getting faster. It's also getting CHEAPER. People are using very powerful computers for video editing and rendering. New computers will all support a large amount of RAM. The top Apple box right now can use >>16GB<< of RAM. 
I'll upgrade (meaning install a 64-bit OS on a computer instead of what I've been doing) when I need to. Lots of new Ubuntu users have immense need for video editing and rendering. And you know how the requirements for Compiz-Fusion are, right? A 64-bit address space is necessary for the required 8GB of RAM, since no vendor supplies enough onboard RAM to handle everything at once.

I guess I was vague when I said **users** and **vague**. Not more than 5% of people need 64-bit capabilities and I haven't found anything other than anecdotal evidence to suggest that 64-bit offers any improvement in anything, even LAME, which trials have shown actually runs slower in 64-bit.

> **cogitordi said:**
> The fact that Windows isn't useful as a 64-bit platform is evidence that Windows is not even a player in these leagues.
Funny you bring that up. Who cares about Windows? Let's worry about Linux. Let's worry about Ubuntu, because if things don't change, it won't be "the top distribution" anymore.

People are installing Gutsy and their installations aren't working like the Live CD did. Some of them can't boot their computers. People are "upgrading" and their devices stop working. Wireless is a nightmare, so I'm writing [this]("http://sourceforge.net/projects/wifix") (it's actually ready for alpha testing; I'd release a beta, but I don't have enough feedback yet).

Most people don't have the patience I do when it comes to computers. Most people just complain that Linux doesn't work for them and that it's too much trouble. At the rate Ubuntu is moving, it'll die before it hits the #1 spot on distrowatch.com again (except for the last 7 days, since there was a release, but the hype will die).

In other news, an fglrx driver w/ AIGLX support has been released, but **not for 64-bit Linux**. I tested it out w/ Compiz-Fusion and Beryl (I keep it around because it's more intuitive and exciting than Compiz-Fusion), and it works quite well on my 32-bit Linux kernel running on my 64-bit hardware. Maybe we'll see 64-bit support for it next time around... but you know how ATI is with their promises.

---

### Post by cogitordi on 2007-10-25
> **bmartin said:**
> Yeah, you're right. It's the number one distribution... except on distrowatch.com, where it's about 500 HPD behind PCLinuxOS.

Ubuntu+Kubuntu+Xubuntu+Ubuntu Studio. Ubuntu bundling deals for commercial hardware. It's going well. Ubuntu was number 1 on Distrowatch for a long time. Both the #1 and #2 distros are far beyond the others. Healthy competition. 

> **bmartin said:**
>  Wireless support for Ubuntu seems to be getting worse. Load up the PCLinuxOS Live CD. Do you notice anything? I'm not a huge fan of KDE (or GNOME; I think they both stink; I refuse to use either one), but I'm more impressed with how they run things there.

My wireless has been nice since Edgy Eft. I'll try PCLinux when I have a chance. Gnome hurts my eyes less than KDE. I like how Xfce looks but I've had problems with its functionality. I do like Compiz.

> **bmartin said:**
> 
I guess I was vague when I said **users** and **vague**. Not more than 5% of people need 64-bit capabilities and I haven't found anything other than anecdotal evidence to suggest that 64-bit offers any improvement in anything

Video editing requirements are not anecdotal evidence, nor are Hollywood CGI farms, nor are high-volume servers, nor is Apple's MacPro. How much computer most people need in their homes is... not very much. Franky, "most people" do NOT need Linux. They just don't want to pay Microsoft anymore and suffer the constant virus fears. Their first experience with Linux is going to be an eye-opener, 32-bit or 64-bit. 

And as many others pointed out, stuff is working in 64-bit that did not work before. Hell, even WINE works in 64-bit now.

> **bmartin said:**
> 
Funny you bring that up. Who cares about Windows? Let's worry about Linux. Let's worry about Ubuntu, because if things don't change, it won't be "the top distribution" anymore.

Oh, we all care. However, I mentioned Windows because Linux 64 is capable of heavy assignments in 2007 that Windows is not capable of doing, in markets where "Windows" is just a sarcasm. Linux 64 has a growing place in the world and interest in it is growing. 

> **bmartin said:**
> 
Most people just complain that Linux doesn't work for them and that it's too much trouble.

Well, "most people" are probably right. 

> **bmartin said:**
> 
running on my 64-bit hardware. Maybe we'll see 64-bit support for it next time around... but you know how ATI is with their promises.

You're trying to make a point about 64-bit Linux here, but really you're making a point about closed-source development.

---

### Post by bmartin on 2007-10-25
> **cogitordi said:**
> (incoherent babble from a 16-yr-old)
Oh, lordy lordy! You've opened up my eyes! Ubuntu is the best distribution! Other than it and PCLinuxOS, they're all terrible!

The point about the ATI driver is 64-bit support, not necessary via Linux, but for Linux. A lot of NDIS drivers also aren't readily available in their 32-bit versions.

The existence of non-anecdotal evidence doesn't mean that people saying "It works faster for me" isn't anecdotal.

There's no point to me reading or responding to this thread anymore. I'm not sold on the idea of a use for 64-bit, unless you're doing... uh, what was it that 64-bit does really well? Oh yeah, really precise floating-point computation. Grid computing. Right. I'll wait for the >4GB RAM requirement.

---

### Post by cogitordi on 2007-10-25
> **bmartin said:**
> There's no point to me reading or responding to this thread anymore.

Thanks for sparing us more embarrassing examples of your diaperish personality.

> **bmartin said:**
> 
I do some development work, mostly high-level stuff in regards to wireless functionality. 

I hope you're good at code, in any case.

---

### Post by southernman on 2007-10-25
I've not used the 64 bit yet. Machine specs don't allow.

However, the parts for my new rig will be in tomorrow from NewEgg.

> 
MB GIGABYTE GA-M61P-S3 GF6100 AM2
CPU AMD|A64 X2 4200+ AM2 2x512K R
HD 250G|ST 7K 16M SATA2 ST3250410AS
PSU TT | W0070RUC 430W RTL
MEM 1Gx2|G.SK F2-6400CL5D-2GBNQ R

Currently downloading U&Xubuntu 64bit now.

If I had a ferrari in the garage, I wouldn't drive a pinto to work. ;)

---

### Post by Divan Santana on 2007-10-27
My experience...

64 seems quicker so far, always used 32 bit previously.

So far Skype doesn't work and haven't a clue where to get 64 bit skype or how to install 32bit skype. Anyone?

Luckily freenx nxclient nxserver etc supports 64bit arch :)

Hope my quake3 works!
Anyone have any ideas on skype on 64 bit??

---

### Post by MariusSilverwolf on 2007-10-27
I use 64-bit Gutsy (and Feisty before it) because I shelled out a fair chunk of change for my AMD 64 Newcastle 3400+ and the 2 GB of RAM supporting it, and I wanted to at least reduce the processing load when working on my system.

It's a matter of heat.

In 32-bit, I'm spending longer (no matter how small) using only a portion of the processor to accomplish any CPU-Intensive task, be it ripping, encoding, running a CPU/GPU intensive screensaver, or compiling new programs.  The longer the CPU performs these tasks, the more heat it generates.

In 64-bit, that processing time has been reduced, sometimes significantly, (ripping/encoding and compiling, specifically) so the CPU is spending less time generating greater heat.

I'm extending the life of my chip and keeping my entire system running cooler.

Not a bad trick for changing the structure of my OS.

---

### Post by the.dark.lord on 2007-10-27
> **MariusSilverwolf said:**
> I use 64-bit Gutsy (and Feisty before it) because I shelled out a fair chunk of change for my AMD 64 Newcastle 3400+ and the 2 GB of RAM supporting it, and I wanted to at least reduce the processing load when working on my system.

It's a matter of heat.

In 32-bit, I'm spending longer (no matter how small) using only a portion of the processor to accomplish any CPU-Intensive task, be it ripping, encoding, running a CPU/GPU intensive screensaver, or compiling new programs.  The longer the CPU performs these tasks, the more heat it generates.

In 64-bit, that processing time has been reduced, sometimes significantly, (ripping/encoding and compiling, specifically) so the CPU is spending less time generating greater heat.

I'm extending the life of my chip and keeping my entire system running cooler.

Not a bad trick for changing the structure of my OS.

I too had the heat problem with the closed structure of my iMac with 32-bit -it actually got so hot, that you could fry stuff on it.

---

### Post by rsambuca on 2007-10-27
> **Divan Santana said:**
> My experience...

64 seems quicker so far, always used 32 bit previously.

[COLOR="Red"]So far Skype doesn't work and haven't a clue where to get 64 bit skype or how to install 32bit skype. Anyone?[/COLOR]

Luckily freenx nxclient nxserver etc supports 64bit arch :)

Hope my quake3 works!
Anyone have any ideas on skype on 64 bit??

[Instructions are here]("http://ubuntuforums.org/showthread.php?t=432295&highlight=skype").  It seems to work fine for me.

---

### Post by Vadi on 2007-10-27
I recommend new people to Ubuntu to get the 32bit, simply because for the usual tasks on the internet flash & java are a must, and to get it to work on 64bit, they need to install the 32 bit version of firefox to run the 32 bit plugins. Saves me & them trouble in the future to just go with 32 at the moment (because in 32, installing java & flash is a piece of cake).

---

### Post by conehead77 on 2007-10-27
> **Vadi said:**
> I recommend new people to Ubuntu to get the 32bit, simply because for the usual tasks on the internet flash & java are a must, and to get it to work on 64bit, they need to install the 32 bit version of firefox to run the 32 bit plugins. Saves me & them trouble in the future to just go with 32 at the moment (because in 32, installing java & flash is a piece of cake).

I installed 64bit Firefox, Flash installed with 1 click. Just like 32bit.
Dunno about Java, didnt need it yet.

---

### Post by rsambuca on 2007-10-27
> **Vadi said:**
> I recommend new people to Ubuntu to get the 32bit, simply because for the usual tasks on the internet flash & java are a must, and to get it to work on 64bit, they need to install the 32 bit version of firefox to run the 32 bit plugins. Saves me & them trouble in the future to just go with 32 at the moment (because in 32, installing java & flash is a piece of cake).

This is completely outdated and incorrect.  Flash works perfectly with Ubuntu 64bit Gutsy.  Just install through Synaptic.

---

### Post by OffHand on 2007-10-27
I went back to 32bit because I could not get a few games to work with Cedega on 64bit.

---

### Post by Vadi on 2007-10-27
Is it outdated as of... a week ago?

Because this first started with Java. Java was installed with the firefox options, but it just gave a white screen instead.

I didn't know about the synaptic option (who would?!) so we went the same way to get java working as on fiesty - firefox32 & java32.

---

### Post by Depressed Man on 2007-10-27
Hmm one of the things I read about Leopard that I like is the ability to run 64 bit and 32 bit programs in the same environment. (well I think it's natively 64 bit but it can also run 32 bit programs in the same environment).

At least I don't think they were using virtualization and what not?

Would be cool to see that here too to remove the 32bit vs 64 bit problem.

---

### Post by FUbuf on 2007-10-27
I'm going 64 bit version a go. If I don't get it working properly in something like two weeks I'll switch to 32 bit Vista.

```

Antec P182 ATX + 400W Fortron
Asus P5K
Intel Core 2 Quad Q6600 2,4 GHz 8 Mt S775
Kingston 2048 DDR2 800 MHz CL5 2x1024 
Seagate Barracuda 7200.10 500GB SATA 16MB
Geforce 8500GT PCI-E 256 Mt Silent

```

I hope everything will be fine, I'll be happy person using Ubuntu and using full 64 bit potential.

---

### Post by dptxp on 2007-10-27
This debate will continue for one more year.
The winner is going to be 64 bit.

Some new programs are now made in 64 bit only, there is
one from Creative, I do not remember which one.

AMD and INTEL no longer make 32 bit CPU for PC.

---

### Post by Depressed Man on 2007-10-27
Intel and AMD no longer making 32 bit processors doesn't really matter though. Considering 64 bit processors can run 32 bit operating systems and applications. I personally don't think it'll be one year though. Eventally we will get there though

---

### Post by Vadi on 2007-10-27
> **rsambuca said:**
> [Instructions are here]("http://ubuntuforums.org/showthread.php?t=432295&highlight=skype").  It seems to work fine for me.

> **Depressed Man said:**
> Hmm one of the things I read about Leopard that I like is the ability to run 64 bit and 32 bit programs in the same environment. (well I think it's natively 64 bit but it can also run 32 bit programs in the same environment).

At least I don't think they were using virtualization and what not?

Would be cool to see that here too to remove the 32bit vs 64 bit problem.

Well... I don't get what you mean. Normal java32 runs fine in ubuntu64, isn't that the same thing as leopard except already in?

---

### Post by cogitordi on 2007-10-27
> **Vadi said:**
> Is it outdated as of... a week ago?

It appears to be outdated as of Feisty Fawn. I installed flashplugin-nonfree using Synaptic and I didn't even have to restart Firefox to watch a video making fun of Ann Coulter. I'm using Ubuntu Gutsy Gibbon for AMD64 on a Biostar iDeq box. 

> **Vadi said:**
> 
Because this first started with Java. Java was installed with the firefox options, but it just gave a white screen instead.

I've never had trouble with Java at all. Firefox doesn't install Java so I don't understand what you mean.

> **Vadi said:**
> 
I didn't know about the synaptic option (who would?!) so we went the same way to get java working as on fiesty - firefox32 & java32.

Well, if anyone else doesn't know, it's documented here:
[https://help.ubuntu.com/community/MultimediaApplications#head-8da6bb74fc999112e0c2ec15e70c1cb4a1187107](https://help.ubuntu.com/community/MultimediaApplications#head-8da6bb74fc999112e0c2ec15e70c1cb4a1187107)

The package has been "backported" to Dapper Drake and Edgy Eft and was first present in Feisty Fawn, if I have my release numbers/animal names straight.

---

### Post by p_quarles on 2007-10-27
Just switched up to 64 bits last night, and my experience confirms that it's extremely easy. I had to hunt down one .deb for a game I like, and it looks like I'll have to compile kgtk-wrapper myself. Other than that, nothing is particularly different on the applications/codecs side of things. I haven't done anything resource-intensive yet, though, so we'll see if I really get a boost.

As for the question of how far off the widespread adoption is: it really looks like Linux is ready now. Proprietary binaries are the problem right now, and that affects some Linux users, but just about all Win users.

---

### Post by Vadi on 2007-10-27
Heh, I won't argue since I don't have the 64bit system, but I do know that the user couldn't get it working on 64bit firefox, and we solved it somewhat easily via the 32bit way. It works, and that's all it ever needs to do.

---

### Post by rsambuca on 2007-10-27
> **Vadi said:**
> Heh, I won't argue since I don't have the 64bit system, but I do know that the user couldn't get it working on 64bit firefox, and we solved it somewhat easily via the 32bit way. It works, and that's all it ever needs to do.

If you don't use it and you are obviously not keeping up with the advancements, then please STOP "recommend(ing) new people to Ubuntu to get the 32bit...".

---

### Post by p_quarles on 2007-10-27
> **rsambuca said:**
> If you don't use it and you are obviously not keeping up with the advancements, then please STOP "recommend(ing) new people to Ubuntu to get the 32bit...".
+1

---

### Post by professor fate on 2007-10-27
The Vostro 1400 I've been dealing with was beaten down by the 32bit regarding sound.  I simply could not get it to work. (Three installs and one kernel update).  So, out of grins and giggles I tossed the 64bit on this evening.  Guess what?  I have SOUND.  I don't know why.  It just is.

---

### Post by cogitordi on 2007-10-28
> **rsambuca said:**
> If you don't use it and you are obviously not keeping up with the advancements, then please STOP "recommend(ing) new people to Ubuntu to get the 32bit...".

Summarizes the whole thread.

---

### Post by kiepmad on 2007-10-28
We should have sticked with 16bit! It would have prevented  this discussion. :P


I see now reason not to use 64bit, I mean, everything in the computing world is work in progress. And I won't hinder progress!

---

### Post by sayuki288 on 2007-10-28
i use 8-bit ubuntu

---

### Post by Depressed Man on 2007-10-28
> **Vadi said:**
> Well... I don't get what you mean. Normal java32 runs fine in ubuntu64, isn't that the same thing as leopard except already in?

Yes that's what I'm talking about. But does it work that way for all applications? E.g., can you run say a 32 bit Firefox in a 64 bit Ubuntu?  If so then I guess we had it all along lol..and in that case I need to switch my systems to 64 bit OS then.

---

### Post by MariusSilverwolf on 2007-10-28
> **Depressed Man said:**
> Yes that's what I'm talking about. But does it work that way for all applications? E.g., can you run say a 32 bit Firefox in a 64 bit Ubuntu?  If so then I guess we had it all along lol..and in that case I need to switch my systems to 64 bit OS then.

Does this link help? [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by Depressed Man on 2007-10-28
Yes it does, but what I meant was, can I click on say any 32 .deb and have it install and work fine in a 64 bit system? (in case a 64 bit version isn't avaliable)

Since I think that's what Leopard allows you to do (install any 32 bit program if a 64 bit isn't avaliable). If not then I guess it was just marketing.

---

### Post by MariusSilverwolf on 2007-10-28
> **Depressed Man said:**
> Yes it does, but what I meant was, can I click on say any 32 .deb and have it install and work fine in a 64 bit system? (in case a 64 bit version isn't avaliable)

Since I think that's what Leopard allows you to do (install any 32 bit program if a 64 bit isn't avaliable). If not then I guess it was just marketing.

Running a quick search, I can find one piece of info that addresses your concerns:  [http://www.debian-administration.org/articles/534](http://www.debian-administration.org/articles/534)


Yes, no, maybe?

---

### Post by Vadi on 2007-10-28
Oh, dear.

What latest advancements? 64bit 7.10, which gave a white screen on Java? Did you even read that I said that this was the case for **7.10**, not **7.04** only?

I'm really glad that there are improvements being made, but for the cases that I saw, *using* the latest version, that was not the case.

---

### Post by thx11381974 on 2007-10-28
32 bit is the past 64 will be necessary for applications of the future.The need to address more than 4gb isn't fanciful it's real. I just tried last night to burn a 6.7gb video file to dvd+rdl  kb3 wouldn't take it. Some light searching on the net seems to show it's cause kb3 is based on 32bit code witch can't deal with files over 4gb.

Some of the post I've read here seem to be inferring that running over 4gb's of ram is something no one would be doing anyhow, but most modern motherboards can take more than 4bg of ram.  My motherboard can take 8gigs, as soon as it becomes afordable to add another 4, I will.

---

### Post by Depressed Man on 2007-10-28
> **MariusSilverwolf said:**
> Running a quick search, I can find one piece of info that addresses your concerns:  [http://www.debian-administration.org/articles/534](http://www.debian-administration.org/articles/534)


Yes, no, maybe?

Interesting. I'll have to look more into this. So it seems there isn't a con to running a 64 bit OS, since you could always fall back to 32 bit apps if you had to.

---

### Post by saulgoode on 2007-10-28
> **thx11381974 said:**
> Some of the post I've read here seem to be inferring that running over 4gb's of ram is something no one would be doing anyhow, but most modern motherboards can take more than 4bg of ram.  My motherboard can take 8gigs, as soon as it becomes afordable to add another 4, I will.

32-bit Linux supports >4G RAM if your kernel is compiled with HIGHMEM support. The restriction is that any single process is limited to 4G.

---

### Post by Mike'sHardLinux on 2007-10-28
> **thx11381974 said:**
> 32 bit is the past 64 will be necessary for applications of the future.The need to address more than 4gb isn't fanciful it's real. I just tried last night to burn a 6.7gb video file to dvd+rdl  kb3 wouldn't take it. Some light searching on the net seems to show it's cause kb3 is based on 32bit code witch can't deal with files over 4gb.

Some of the post I've read here seem to be inferring that running over 4gb's of ram is something no one would be doing anyhow, but most modern motherboards can take more than 4bg of ram.  My motherboard can take 8gigs, as soon as it becomes afordable to add another 4, I will.

I am pretty sure 64-bit vs 32-bit OS has nothing to do with how large a file a program can deal with. That is probably some other issue you are having. 64 bit can address more RAM than 32 bit. I am pretty sure a 32 bit OS does not have a 4GB FILE limit.

I have to admit, I am one of those who last tried 64-bit when there were all sorts of hoops you had to go through to make some things work like java and non-free codecs, and as far as I remember, many programs also would not work with 64 bit. And that wasn't very long ago - less than a year.

I have been running 7.10 for a week or two and it is not nearly as responsive as Feisty was for me. Sometimes, the whole system seems to pause for a second for no apparent reason. Looks like an opportunity to try 64 bit.

---

### Post by Ehtetur on 2007-10-28
Now that adobe flash 9.0 works on x64, I think you're gonna see even more users flooding onto the x64 platform...

One the other hand, businesses like my company who are on 32bit, will probably remain there for a long time since all their codes, programs, and programmers are on the 32bit platform.

---

### Post by Divan Santana on 2007-10-28
My take on all this:

I've been using 32 bit forever! Finally switched to 64 bit. Nothing wrong. Everything works and bit quicker, maybe its my imagination but boot seems quicker too :)

Otherwise everything seems to run quicker and no problems so far.

Even my old Quake 3 install works.
Skype doesn't but I am reading the work-around :)

Enjoy!

---

### Post by thx11381974 on 2007-10-28
> **Mike'sHardLinux said:**
> I am pretty sure 64-bit vs 32-bit OS has nothing to do with how large a file a program can deal with. That is probably some other issue you are having. 64 bit can address more RAM than 32 bit. I am pretty sure a 32 bit OS does not have a 4GB FILE limit.

I have to admit, I am one of those who last tried 64-bit when there were all sorts of hoops you had to go through to make some things work like java and non-free codecs, and as far as I remember, many programs also would not work with 64 bit. And that wasn't very long ago - less than a year.

I have been running 7.10 for a week or two and it is not nearly as responsive as Feisty was for me. Sometimes, the whole system seems to pause for a second for no apparent reason. Looks like an opportunity to try 64 bit.

I wish I had a link to point to, but if I understood it right even though k3b is running in my case on a 64bit OS it was written for a 32bit so it won't allow you burn any single file over 4gigs. I remember reading only 64bit versions of vista would be allowed to play blue ray I wonder if it's a similar issue? I had thought it was just their insane security crap

I'm liking 64bit Kubuntu, but as far as Linux goes I can only compare it to 32bit Suse 10.0 & 10.2 witch was on a much older pc. In any case I don't think you'll be disappointed.

---

### Post by rsambuca on 2007-10-28
> **thx11381974 said:**
> I wish I had a link to point to, but if I understood it right even though k3b is running in my case on a 64bit OS it was written for a 32bit so it won't allow you burn any single file over 4gigs. I remember reading only 64bit versions of vista would be allowed to play blue ray I wonder if it's a similar issue? I had thought it was just their insane security crap

I'm liking 64bit Kubuntu, but as far as Linux goes I can only compare it to 32bit Suse 10.0 & 10.2 witch was on a much older pc. In any case I don't think you'll be disappointed.

Let's cut out the hysterics and FUD!  You do NOT require 64bit Vista to allow play blu-ray playback.

---

### Post by saulgoode on 2007-10-28
> **thx11381974 said:**
> I wish I had a link to point to, but if I understood it right even though k3b is running in my case on a 64bit OS it was written for a 32bit so it won't allow you burn any single file over 4gigs.

The 4gig per file is a limitation of the ISO9660 file system specification. It has nothing to do with K3B being a 32-bit program. You should have no problem creating >4gig DVDs as long as no single file is greater than 4gig.

---

### Post by thx11381974 on 2007-10-28
> **rsambuca said:**
> Let's cut out the hysterics and FUD!  You do NOT require 64bit Vista to allow play blu-ray playback.

No FUD here I meant Microsoft is requiring 64bit not that you need Microsoft to play blue ray.

---

### Post by MariusSilverwolf on 2007-10-29
> **thx11381974 said:**
> No FUD here I meant Microsoft is requiring 64bit not that you need Microsoft to play blue ray.

ZDNet testers have played many a Blue-Ray disk on test machines that run the 32-bit version of Vista.  There's no 64-bit requirement from MS to play Blue-Ray.

---

### Post by daflame on 2007-11-18
As for an avid Ubuntu/Linux user (I have used most of the main flavors at some point); I have to say that I am VERY impressed with the advances in 64bit support in Linux in general.  When I installed my laptop with feisty I was impressed to go 32bit for compatibility and I ran it that way for a short while, but I found intensive apps to heat up my CPU quite fast.  Then I decided to reinstall and go 64bit.  I was impressed that apps that used to heat up my CPU ran cooler than before and faster than ever.  I would compile apps in 32bit and it was no faster than my desktop (which is 32bit).  Now I compile apps with a 20% speed improvement and my laptop has a slower core than the desktop.

---

### Post by Ux64 on 2007-11-18
I got new comp, and I though whatta **** I won't use 32 bit OS anymore. I took the change, installed 64 bit version. And I'm quite happy with it. Actually I don't notice any difference compared to 32 bit version.

But for future, this is great. I don't need to think about moving from 32 bit system to 64 bit system.

And I'm going to use this comp for 3-5 years. So in that time I'm quite sure that 64 bit systems will grow even more popular. And I can add memory up to 8 gigabytes on this motherboard.

---

