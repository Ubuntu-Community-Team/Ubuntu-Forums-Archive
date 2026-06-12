---
title: "Ubuntu 13.04 is slower than Windows 8?"
date: 2013-08-21
forum: Ubuntu, Linux and OS Chat
---

### Post by steve30 on 2013-08-21
Today I decided to try out Ubuntu 13.04 on my ASUS A55A PC. Honestly, I have been trying to get linux on my PC for a while because I have heard linux is suppose to be "way" faster than Windows. Finally I got around the UEFI firmware but have experienced a much slower, less snappy PC. Here are some specs:

Specs:
Memory 5.7 GiB
Proccessor Intel® Core™ i5-3210M CPU @ 2.50GHz × 4 
Graphics Intel® Ivybridge Mobile 
OS type 64-bit
Disk: 9.4 GB

Note: My OS drive has 69,5 GB left on it, after installing Ubuntu. My Data drive has 277.5 GB left on it. I was thinking of trying to boot off the Data drive to see If I would get any speed improvments.


Installation: Did the typical "Install alongside Windows 8"


Anyways, is it common for Ubuntu to be slower than Windows? I have always heard the opposite. Was it due to me installing Ubuntu "alongside Windows 8" and only having 9.4 GB of Disk Space? It is not terribly slow but enough to be noticiable. On the good side, I really like the workspace switcher. 

I would like to stick with Ubuntu but cannot seem to completely be satifsfied knowing the Windows 8 is more snappy and just quicker!

In conclusion, is the  lack of speed in Ubuntu 13.04 due to my ignorance in only giving it 9.4 GB of disk space or rather that Windows 8 is superior to Ubuntu in terms of speed?

---

### Post by startas on 2013-08-21
Welcome to the real world :) windows always was and is the fastest os in the world, no matter what you heard in linux forums. Maybe some hairy linux fans would start to shout, that ubuntu is slow and it is not linux and blah blah blah, try archlinux blah blah blah, but thats is a lie too. It's not just an accident, that windows rules the world, it costs a few hundred bucks, but thats what you get - the fastest os with the best drivers and everything else, including top quality software and millions of games, which of course costs money too, but thats not a problem compared to what you get. Especially with intel graphics, linux intel graphics is getting better, but there still is a big hole between linux and windows versions of intel graphics drivers.

---

### Post by QIII on 2013-08-21
Just curious...

Anyone have any objective data to demonstrate that Windows 8 is the faster of the two?  Or (for the Linux fanboyz out there) that Linux is faster?

There are so many variables in terms of what people subjectively perceive as "fast".  You'd have to define what "fast" is, I suppose.  Then you'd have to define metrics.  Experiment.  Compare.  What are the benchmarks?  What are you testing?  Boot times might be good to compare, except that "fast boot" isn't really "fast boot", but a form of sleep.

Then, of course, you'd have to consider whether being faster in certain areas is more important that being faster in other areas.  

Hard to say.

I can say something about the relative speed and stability of Windows versus Linux with regard to heavy computation envirionments:  there is a reason why 95%+ of the world's top 500 supercomputers run Linux.  Then you have to ask if that even matters since we're probably talking about PCs here.

Anyway, the question is vague.  In what ways is Ubuntu slower than Windows 8?  For that matter, what objective measures indicate that Win 8 is faster than Win 7 as often cited?

---

### Post by startas on 2013-08-21
Well, lets begin our journey around the world with a simple lecture :
1) The reason why linux is used so much in super pcs is not the speed, but its structure, the fact that linux is just a kernel, and you can add just what you want, whereas windows is made as perfect desktop os or a great server, but there is no version for super computers. Super computers have enough speed from their hundreds of cpus :D
2) any cpu tests shows at least about 5 % more speed on windows.
3) graphically, linux kind of lacks great de, and that makes the most of linux slowness, because visually everything is slower than in windows, and this is the real dealbreaker, not pure cpu tests or something else.

---

### Post by QIII on 2013-08-21
I understand the concept of the supercomputer...  sort of a professional necessity. ;)

I'd love to see your sources, by the way.  Particularly with regard to the 5% performance hit.

Not being argumentative.  I'm neither a Windows fanboy nor a Linux fanboy.  I use both (and UNIX/BSDs).

---

### Post by sbnwl on 2013-08-21
Hi Steve30

What you heard about linux is (in terms of) the computational power, not the graphic response. Regarding the boot speed, you may not have provided enough swap space which is configured as a separate partition during the installation.
Try installing ubuntu alone on any other machine (be it older/slower than your current machine) and see if you get some speed.

---

### Post by adrian89 on 2013-08-21
What I've seen ubuntu has issues with managing the graphic cards resources.
The desktop environment(unity) uses a lot of memory from the graphic cards,thus,having a low specced graphic cards, makes it look like it is slower the windows.
For lesser cards are lighter desktop environments like,xfce,lxde.(I've seen the difference).
In the future this will change since ubuntu is developing they're own display manager(Mir) which,from what I've heard is much better then the acual one(Xorg).
So to make a short version(in my opinion), ubuntu's desktop environment(at this moment) is like windows vista desktop environment(in terms of video memory use).

---

### Post by TenPlus1 on 2013-08-21
I have had Windows 7 and 8 installed natively on my Acer Aspire Revo as well as Ubuntu 13.04, Xubuntu and Lubuntu and tested each one seperately and found that the best for my needs was Lubuntu 13.04 running propriatary nvidia drivers and tweaking the swappiness and fstab for SSD performance which gave me a very fast, very stable and very easy to use operating system that does anything I ask of it with no problems...

Try all, use what's best for you...

---

### Post by xzhamppa on 2013-08-21
Most of the linux fanboys are speaking early days of linux and windows back when windows was bluescreen of death OS, but since then they have improved a lot. Huge step was from windows vista -> windows 7. I think linux comes little behind from terms of speed, but it still is more stable OS and way much more customizable than windows. That customization comes with price and that is the speed, if you take lubuntu for example it is lightweight OS and very snappy. Windows has it's own starter package, but there the difference is huge i would take lubuntu any day over windows 7 starter. When the speed crow's in terms of cpu and better graphics card's the speed isn't that noticeable any more to human eye and the differences begin to even out.

---

### Post by startas on 2013-08-21
> **adrian89 said:**
> What I've seen ubuntu has issues with managing the graphic cards resources.
The desktop environment(unity) uses a lot of memory from the graphic cards,thus,having a low specced graphic cards, makes it look like it is slower the windows.
For lesser cards are lighter desktop environments like,xfce,lxde.(I've seen the difference).
In the future this will change since ubuntu is developing they're own display manager(Mir) which,from what I've heard is much better then the acual one(Xorg).
So to make a short version(in my opinion), ubuntu's desktop environment(at this moment) is like windows vista desktop environment(in terms of video memory use).

Well that is the whole linux problem, bad optimizations for graphics. xfce and company are very bad des because of lack of simple things like vsync and many others, it's horror. Speed gain from using xfce instead of unity is zero, its maybe little bit faster than gnome or kde (two big bloatware and slow desktops), but the reason for this is not funny - xfce is still staying in 80's with the technologies, and a little bit more modern des are full of bugs and are going through big changes, so we have to wait a few more years to see what is what in linux. Windows always was ahead in this, especially with windows 7/8, graphics performance for desktop is perfect, everything flies, so that where windows speed comes from, user can see everything much faster in windows. And the usage of computer resources is a good thing, thats the whole purpose, you know, like food - you eat it, you dont keep it for years till it starts to smell, its just that linux lacks high level optimizations of resources usage.

---

### Post by startas on 2013-08-21
> **xzhamppa said:**
> Most of the linux fanboys are speaking early days of linux and windows back when windows was bluescreen of death OS, but since then they have improved a lot. Huge step was from windows vista -> windows 7. I think linux comes little behind from terms of speed, but it still is more stable OS and way much more customizable than windows. That customization comes with price and that is the speed, if you take lubuntu for example it is lightweight OS and very snappy. Windows has it's own starter package, but there the difference is huge i would take lubuntu any day over windows 7 starter. When the speed crow's in terms of cpu and better graphics card's the speed isn't that noticeable any more to human eye and the differences begin to even out.

You wanna talk about linux kernel panics ? :D Blue screen is not a bad thing, it says that there was a serious error on your pc, plus a havent seen any bsod in like 10 years, babe, if you wanna talk about which os is more stable :) customization is just for noobs, it is never good, as it never fits well with standard user interface, and its just for small things, not for fixing the whole user interface. And the speed in windows over linux is very noticeable, but thats maybe depends on peoples reaction time :)

---

### Post by QIII on 2013-08-21
OK, now we're getting somewhere.  Something specific we can use to get back to the OP's post.

steve30 -- are you talking about graphical response?

---

### Post by mastablasta on 2013-08-21
> **QIII said:**
> I'd love to see your sources, by the way. Particularly with regard to the 5% performance hit.
i found this to be an interesting read: 

> Windows 8 has been banned from HWBot, one of the world&#8217;s top benchmarking and overclocking communities.
[http://www.extremetech.com/computing/164209-windows-8-banned-by-worlds-top-benchmarking-and-overclocking-site](http://www.extremetech.com/computing/164209-windows-8-banned-by-worlds-top-benchmarking-and-overclocking-site)
only their rankings are windows only i believe.

to the OP - you installed the auto install alongside widnows and you gave it only 9.4 GB? if you have 5 GB RAM then it will probably create at least 4 GB size /swap parititon. this would limit the disk space from the OS. how much disk is actually available in OS?

i don' know how fast windows 8 is. i do know i have win7 starter with Kubuntu dual boot. And kubuntu is so much faster it is not even funny. Default effects on and programs such as firefox start almost instanly on that netbook. while it takes them considerably longer in widnows 7. windows switching is also noticably faste rin Kubuntu. memory usage is a bit lower in Kubuntu but Kubutnu is 64 bit OS (starter is 32 bit). i tried the 32 bit version before that and speed was the same but RAM usage was lower.

and as explained there are various desktops in linux. some are faster and use a lot less system resources as they do not use 3D effects (for example icewm looks like win98).


but this shouldn't be a problem in your case. the GPu should be abel to easilly handle Unity interface and work quite fast at that.

though it is still possible it will be slower than in windows (as shown here: [http://www.phoronix.com/scan.php?page=article&item=intel_ivbmesa92_win7&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_ivbmesa92_win7&num=1)) due to drivers being worse.

i think nvidia has good support for linux. or so they say. with propper drivers for all hardware linux is probably still faster.

for exmaple here test show their linux proprietary drivers to be on par with win8 [http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)

---

### Post by mastablasta on 2013-08-21
> **startas said:**
>  And the usage of computer resources is a good thing, thats the whole purpose, you know, like food - you eat it, you dont keep it for years till it starts to smell, its just that linux lacks high level optimizations of resources usage.

not when you have a computer oprating on a battery. though with propper management --- windows can do it because they work with hardware manufacturers - they give them specs what will be in the next OS and expect drivers for it in time. widnows demands - they deliver. linux demands - they say "we'll see" or "in your dreams" or make your own if you want to mess with my hardware. Ubuntu has a problem deciding which browser will be used half a year in avdance. anyway it seems that where proprietary or other drivers are done well then system is on par with windows in desktop performance (or at least percepiton of it).

---

### Post by coldraven on 2013-08-21
I first switched to Linux from XP pro.
XP took about three minutes to boot up, Ubuntu took 30 seconds.
When I say boot up time I mean the time before the cursor stops being an hourglass and the system is usable, not just being able to see the desktop.
I found that if you tried to run a program before the OS had finished loading it would invariably crash.
As for Win 7 or 8 I have no intention of buying them. I do not trust Microsoft and I believe that they are an underhand, devious and morally bankrupt company.

Microsoft released Vista knowing that it would not run on the machines that advertised it should.
Vista was using **your own resources** to check if you were a criminal by copying copyright material.
In other words, they valued their friends in Hollywood above **you**, the customer.
**You the customer** paid for all of Vista's DRM features*. 
Will I ever trust Microsoft again? **Definitely not! **

If you think that Microsoft have now changed their spots, dream on!
If you think that the NSA cannot get direct access to your Skype conversations you really are deluded.
Skype is now hooked into Outlook so there goes your email privacy too!
[http://www.theregister.co.uk/2013/08/20/microsoft_skypes_up_its_outlook/](http://www.theregister.co.uk/2013/08/20/microsoft_skypes_up_its_outlook/)

*Read Peter Gutmann's analysis of Vista
[http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html)
or
[http://en.wikipedia.org/wiki/Criticism_of_Windows_Vista](http://en.wikipedia.org/wiki/Criticism_of_Windows_Vista)

---

### Post by startas on 2013-08-21
So you see what money does ? Even with all this spying, antiviruses and other things, windows still running faster than linux :D BTW, if you dont like win8, you can just install win7, it works a little bit better and it is without all that tablets/phones stuff.
Comparing boot times of win xp / ubuntu is not very fair, because win xp is known to boot slower on slower hardware, plus it has some boot issues, which you must manually tweak to remove. Windows xp loads tons of stuff during boot, whereas ubuntu loads not so much, you can compare win xp to ubuntu 13.10 - it has broken boot process, everything loads, but you still have black screen for a minute... Anyway, win xp on fast hardware loads just in a few seconds.
And you really shouldnt talk about spying in windows in ubuntu forums, if you know what i mean ;)
And linux has much bigger chance to crash than even windows xp, because linux base is changing too fast, it never gets to a really stable base, it gets updated too fast, and old releases gets unsupported. Its just a shame, every new linux distro release brings back tons of same old errors... And btw, even windows xp is now very stable, because it was getting fixes for many years, that "linux lts releases" is getting pooped on :D
And i dont think, that you should expect privacy on the internet, even google tells you that - [http://www.dailymail.co.uk/sciencetech/article-2392773/Gmail-email-users-NOT-expect-privacy-Google-claims-stunning-admission.html](http://www.dailymail.co.uk/sciencetech/article-2392773/Gmail-email-users-NOT-expect-privacy-Google-claims-stunning-admission.html)

---

### Post by Cheesemill on 2013-08-21
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request.

---

### Post by mastablasta on 2013-08-21
> **startas said:**
> And linux has much bigger chance to crash than even windows xp, because linux base is changing too fast, it never gets to a really stable base, it gets updated too fast, and old releases gets unsupported. Its just a shame, every new linux distro release brings back tons of same old errors... And btw, even windows xp is now very stable, because it was getting fixes for many years, that "linux lts releases" is getting pooped on 

when you talk abotu base are you talking about linux kernel ? that one is stable. debian stable is also stable as a desktop. doesn't really crash much. similar goes for Red hat or SUSE Enterprise Linux. 
majority of the internet is powered by same base. it doesn't crash too often there.
the problem is probably not the base but desktops and their fragmentation.
XP is also stable. but for the first couple of years it was a nightmare. win7 is vista made more stable and win8 is a bit improved win7.
the development in linux is fast. and hardware manufacturers don't want to keep up. they prefer older stuff. less investment i guess... i can see they still sell mobile phones with android 2.x. not many have latest one installed.
---
another thing is that the modular nature of linux can reduce system resoruces usage. alowing to use new software on a much older hardware.
i can run debian 6 or 7 on the following mashcine:
1,2Ghz AMD cpu 
with 256MB system ram of which only 224 is available to the OS
20 GB HDD

i can browse web with it, write texts, watch movies, watch youtube... i consider it a "netbook"
computer boots in about 30-45 secs. battery life was abouT 3 hours .

the computer came with winxp preinstalled. it used 10 minutes just to boot. though we could watch movies on it there was often a lot of stuttering. websurfing was very slow. youtube videos were mostly a slide show. writing a text in word was typing, watching cursor blinking, waiting and then suddenly the text would appear...  battery lasted about 1.5 hour.
 i used latest windows drivers for video and all hardware. it didn't help. fresh reinstall did not help.

now since windows7 and windows 8 are much faster than linux and apparetnly use less resources surely they wouldn't have any problem s running on this mashicne would they? i mean it's not fair to compare this debian install with 12 year old xp is it? ;-)

---

### Post by startas on 2013-08-21
That is a nice piece of wood :D

---

### Post by carl4926 on 2013-08-21
It's very subjective and depends what you measure

Do clean install of each > completely updated
See how long windows takes LOL

---

### Post by steve30 on 2013-08-21
I have experienced simillar results when installing Ubuntu 12.04 on another machine and felt the UI snappiness go away. Reinstalled Windows 8 and snappiness was back. Maybe I am measuring it incorrectly. Also as to linux being more reliable it seems like Windows 8 might be a tad more reliable...Second or Third time I shut my laptop screen after closing all programs I tried to log in and startup firefox and boom firefox is not responding...Obviously that's all anecdotal, but I decided to install chromium anyways! Would I be wasting my time taking a video to show the change in speed?

---

### Post by steve30 on 2013-08-21
I am talking about graphical response. How fast firefox opens, boot up times (Windows 8 clearly wins here because it doesn't shutdown all the way but merely sort of hibernates), Log-in times, etc. Many may claim I am just seeing and it is just anecdotal evidence however I have "seen" this on 2 computers. Hopefully I am doing something wrong!
[B]
Reliability[/B]

If Ubuntu is more reliable I am willing to sacrafice some speed. I have noticed "hellish" not responding with Eclipse IDE in Windows and was wondering if it will be worse on Linux? Firefox stopped responding one time in all of Window 8's use probably around 8 months where linux it stopped responding yesterday after 2 hours of use. I haven't tried running Eclipse in Linux.

---

### Post by steve30 on 2013-08-21
> **mastablasta said:**
> i found this to be an interesting read: 

[http://www.extremetech.com/computing/164209-windows-8-banned-by-worlds-top-benchmarking-and-overclocking-site](http://www.extremetech.com/computing/164209-windows-8-banned-by-worlds-top-benchmarking-and-overclocking-site)
only their rankings are windows only i believe.

to the OP - you installed the auto install alongside widnows and you gave it only 9.4 GB? if you have 5 GB RAM then it will probably create at least 4 GB size /swap parititon. this would limit the disk space from the OS. how much disk is actually available in OS?

i don' know how fast windows 8 is. i do know i have win7 starter with Kubuntu dual boot. And kubuntu is so much faster it is not even funny. Default effects on and programs such as firefox start almost instanly on that netbook. while it takes them considerably longer in widnows 7. windows switching is also noticably faste rin Kubuntu. memory usage is a bit lower in Kubuntu but Kubutnu is 64 bit OS (starter is 32 bit). i tried the 32 bit version before that and speed was the same but RAM usage was lower.

and as explained there are various desktops in linux. some are faster and use a lot less system resources as they do not use 3D effects (for example icewm looks like win98).


but this shouldn't be a problem in your case. the GPu should be abel to easilly handle Unity interface and work quite fast at that.

though it is still possible it will be slower than in windows (as shown here: [http://www.phoronix.com/scan.php?page=article&item=intel_ivbmesa92_win7&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_ivbmesa92_win7&num=1)) due to drivers being worse.

i think nvidia has good support for linux. or so they say. with propper drivers for all hardware linux is probably still faster.

for exmaple here test show their linux proprietary drivers to be on par with win8 [http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)

I chose the deafault "Install alongside Windows 8." 119 GB is actaully left in the OS drive; I forgot to subtract 62GB from the size of the Disk. How do I check how much diskspace is in the OS? I thought the OS Drive is how much disk space I have.

---

### Post by Mark Phelps on 2013-08-21
The original issue (about which is "faster") is very hard to measure -- unless we can all agree on what we're measuring.

When someone claims Linux boots in a few seconds but Windows takes a minute or more -- that is booting, not using the OS after it is up and running. On my multi-core CPU desktop, observing the time it takes to boot, the order (fastest to slowest) is the following:
1) Win8 -- under 15 seconds from OS selection to working desktop (because fast startup is turned on)
2) Win7 -- around 30 seconds
-- big gap in  timeframe --
3) Ubuntu 12.10 -  couple of minutes or more
4) Linux Mint 15 -- three minutes or more
So clearly, using this measure of "speed", Windows is "faster". 

However, the total boot time is dependent on how much stuff you load when starting up the OS.  Win8 (in my case) loads fewer services than does Win7, Mint appears to load more stuff than does Ubuntu.  And yeah, I know that loading can be tweaked to eliminate startup processes to reduce it's time -- but I'm not going to spend hours and hours doing this just to save a few seconds a day.

A second "measure" is how responsive the OS is during actual use.  How long does it take to launch an app, have it open a window on the desktop, and be able to use it. Once again, Windows wins out -- but the reason here is largely due to display drivers.  In Win8 and Win7, I can use hardware-accelerated AMD drivers; in Linux, I have to use the default Radeon  drivers.  So, this is really comparing "apples to oranges", and the slower feel of the Linux distros is not the fault of the underlying OS.

A third measuring approach would be using benchmarks to see how long it takes an app to perform a task -- like converting a large video file from one format to another, or recalculating all the cells in a very large, complex spreadsheet.  While this sounds like it would be comparing "apples to apples", it really is not because the same app run in different OSs actually uses very different code.  So, to some degree (maybe, to a large degree), you're measuring the run-time efficiency of the underlying application code, not of the OS, per se. I have done this informally (with the video conversion) and found much the same results -- Win8 is the fastest, with the other three roughly the same, and only a little slower.

All this said, if you run all of these using a very high speed processer (i7) and 8GB of memory, you could possibly get very different results.

---

### Post by kurt18947 on 2013-08-21
I suspect comparing computer speeds is sorta like polls commissioned by special interest groups.  You can get any result you want, just structure the questions/test correctly.  The art is in not being too obvious about it;).  Dual booting Win 7 /Ubuntu 12.04 or newer Ubuntu wins the perception test.  My daily usage doesn't stress either O.S. on the same machine so I use what I prefer.

---

### Post by carl4926 on 2013-08-21
> [COLOR=#000000]3) Ubuntu 12.10 - couple of minutes or more[/COLOR]
[COLOR=#000000]4) Linux Mint 15 -- three minutes or more[/COLOR]
Woooh
What the...
You must be kidding!
Ubuntu 12.04 < 1 min
Mint 14 < 45 sec
openSUSE 12.3 < 45 sec
Win 7 < 45 sec
Win 8 1 min dead

---

### Post by MadmanRB on 2013-08-21
> **startas said:**
> Welcome to the real world :) windows always was and is the fastest os in the world, no matter what you heard in linux forums. Maybe some hairy linux fans would start to shout, that ubuntu is slow and it is not linux and blah blah blah, try archlinux blah blah blah, but thats is a lie too. It's not just an accident, that windows rules the world, it costs a few hundred bucks, but thats what you get - the fastest os with the best drivers and everything else, including top quality software and millions of games, which of course costs money too, but thats not a problem compared to what you get. Especially with intel graphics, linux intel graphics is getting better, but there still is a big hole between linux and windows versions of intel graphics drivers.

Nice Mr Microsoft employee, but looks like you never tried distros like peppermint or Elementary.
Elementary especially its lightning :D

---

### Post by erasmusp on 2013-08-21
[I]> Woooh
> What the...
> You must be kidding!
> Ubuntu 12.04 < 1 min
> Mint 14 < 45 sec
> openSUSE 12.3 < 45 sec
> Win 7 < 45 sec
> Win 8 1 min dead [/I]

Now this is my experience as well. I cannot say about Win8 and openSUSE but I agree with the balance of your findings. Although booting times are not that important as you only do it the very first time, but the overhaul snappiness of the OS is what you are using continuously and should therefore be more important. However how much time is being spent typing or browsing where the speed would then not be obvious at all. Where there would be important differences could be the playback of a video file perhaps (lagging) or copying data but I must say here I have not noticed whether a Windows or Linux machine would handle this any different on the equipment I've used. Therefore I will stick with my preference on my personal PCs and laptops, Linux, and use Windows only on the equipment I have no choice of OS, at work.

---

### Post by monkeybrain20122 on 2013-08-21
> **Mark Phelps said:**
> 
2) Win7 -- around 30 seconds
-- big gap in  timeframe --
3) Ubuntu 12.10 -  couple of minutes or more
4) Linux Mint 15 -- three minutes or more
So clearly, using this measure of "speed", Windows is "faster". 
.
Hmmm..That would depend on your hardware. 

For me Ubuntu 13.04 around 20-25 sec (the variations across different releases is small, but 13.04 feels fastest)

Fedora 19 around 20-25 sec

Debian unstable around 15-20 sec.

All of them definitely faster than Windows of any version except 8, which I don't know cos I never use it. But Win8 doesn't really turn off, it kinds of went into suspension (fast boot) so it is sort of cheating.

---

### Post by montag dp on 2013-08-21
I guess it depends on what you are doing.  I can believe that Windows is faster for graphics-intensive things like video games.  But for everything else, in my experience Windows has been much slower.  Web browsing, opening programs, running programs that aren't extremely graphics intensive (basically everything I do), booting and shutting down (Windows 7 without SSD) is slower in Windows.  Oh, and I hate how even after booting and logging in I have to wait 2 minutes for everything to get going and be ready to do anything.

---

### Post by monkeybrain20122 on 2013-08-21
> **montag dp said:**
> I guess it depends on what you are doing.  I can believe that Windows is faster for graphics-intensive things like video games.  But for everything else, in my experience Windows has been much slower.  Web browsing, opening programs, running programs that aren't extremely graphics intensive (basically everything I do), booting and shutting down (Windows 7 without SSD) is slower in Windows.  Oh, and I hate how even after booting and logging in I have to wait 2 minutes for everything to get going and be ready to do anything.

That is an interesting point. Just staying in Ubuntu I find that nouveau is faster and smooth than the Nvidia blob for most things except intensive graphic uses.

---

### Post by oldfred on 2013-08-21
Windows 8 adds fast boot which really is just hibernation to make it seem like it boots faster. In most cases you do not need to do a full check to see if system has changed so always hibernating usually works. But you really cannot use the fast boot feature if dual booting even if dual booting another Windows.

With games being released for Linux, the proprietary video drivers for Linux are improving. Before they were always behind the Windows versions.

nVidia on FreeBSD, Windows & Linux
[http://www.phoronix.com/scan.php?page=article&item=freebsd_win8_ubuntu&num=1](http://www.phoronix.com/scan.php?page=article&item=freebsd_win8_ubuntu&num=1)

I think phoronix has also done comparisons of Windows with Intel but could not quickly find it.

---

### Post by mastablasta on 2013-08-22
> **oldfred said:**
> I think phoronix has also done comparisons of Windows with Intel but could not quickly find it.



they did. but intel linux drivers are still worse than windows. but not so much that one would experince such slowness as the OP only in desktop.

regarding boto times. - Ubuntu 10.04 - 15-20sec. i wonder how much is 12.04 with Mate.

also i am running xubuntu in vbox (on WinXP computer with 2GB ram). i assigned it 32MB for graphics, 512MB RAM, 8 GB disk (total). i have a single core cpu so i can't asign specific core to it. is running fine for some safe webbrowsing. i am also running apache webserver on it. i use it mostly to test new sites in various browsers. i doubt i can make windows 8 or 7 run in such a virtual environment. the ram is way too low to run it, also the GPU ram and also not enough disk. CPU is probably also an issue. 

i've since upgrade the computer to 4GB ram so i can assign more eassilly 1GB to vbox. i was thinkign of adding a lighter wm or LXDE to it to make it run even faster.

---

### Post by steve30 on 2013-08-22
I have fell in love with Kubuntu! It will be my main OS. Nice User Interface. Seems more snappy than Ubuntu (it shouldn't) but then again I did give it more space when installing :p

I will continue to dual boot (unfortunately) for Windows programs (I don't want to deal with WINE if I can just use Windows.

---

### Post by monkeybrain20122 on 2013-08-22
Actually my boot time is very fast, what takes longer is logging in (from the login screen to the fully usable desktop), that bring the total up to about 20-25 seconds, it is still very fast, but for booting alone  it is 15 sec max.  The same is true for all DEs I have tried (KDE, gnome-shell, Unity) and gnome-shell seems fastest in terms of initial login.

---

### Post by buzzingrobot on 2013-08-22
We really need more info from the OP specifying what, exactly, is slow? 

Meanwhile, 9.6gb for an Ubuntu install is a pretty tight squeeze.

Subjective impressions of speed and responsiveness are what matter to most of us.  But, comparisons are valid and accurate only when based on reliable benchmarking, performed in a controlled environment on controlled hardware.  Broad claims that X is always faster than Y, or vice versa, are worthless.

I find most people equate speed with the GUI.  If it's responsive and fast, most people never even notice or think about how long disk writes take, etc., unless they are running an app that has high resource demands. E.g., processing a 150-meg file in PhotoShop.

After its Vista debacle, Microsoft began an internal effort to remove or optimize much of the bloated code that its developers had added to Windows since the days of NT.  Windows 7 saw some of that, and Windows 8 has apparently seen a great deal. Win8 really is faster than previous releases. The only way to know if it's faster than Ubuntu on *your* hardware is to benchmark it.

---

### Post by startas on 2013-08-22
Well yeah, if we arent talking about very unoptimized and slow like hell programs like "ubuntu software center", then comparing linux to windows is mostly about gui. While victory in more or less pure cpu/ram performance tests for windows isnt much of a factor, the biggest part of windows speed is its perfectly optimized and just flying gui - in windows 7/8 everything about gui's speed and quality is just perfect, and that where linux is having a lot of difficulties - many mini des with many problems + worse drivers. But hey, linux just recently began to move forward with its graphics, and windows already has reached its perfection (lets hope microsoft will not kill windows with their mobile-mania). So, maybe when wayland and mir will be released and will get tons of fixes and improvements, and graphics drivers will get improved during these ~5 longs years, maybe linux will catch up with windows. Yep, thats another problem of all linux stuff - open source... one sleepy man tries to "develop" something during his free time, not much of a progress and quality you can hope from this kind of development, it will take many years for anything, versus the army of ms or fruits.

And about real world testing linux vs windows - there is nothing, all you can do is just browse through both os and try to see a difference, but results relies on your reaction time, so results will be different, so this test is just for yourself, not much of use for other people.

---

### Post by monkeybrain20122 on 2013-08-22
> **startas said:**
> , the biggest part of windows speed is its perfectly optimized and just flying gui - in windows 7/8 everything about gui's speed and quality is just perfect, and that where linux is having a lot of difficulties - many mini des with many problems + worse drivers. ..
.

Maybe on your hardware, it is not a general fact. I have Ubuntu and other Linux installed/tested on different computers and the gui speed and quality are terrific. On the same work pc Ubuntu 12.04 is a lot faster and smoother than WIndows 7 and my work colleagues all say wow, and that was booting off an external hard drive.Only issue I have encountered is running KDE with the proprietary Nvidia driver, which does seem a bit sluggish (no problem with nouveau though). But anything else (LXDE, XFce, Unity, Gnome shell) is fast.

Also you need to take into account that OEM do all the testings and optimizations on Windows machines.

---

### Post by MetalAZ on 2013-08-22
I had been running Windows 8 since the first day I could buy it online (upgrading from Windows 7).  But like 7, I've always had problems with very high memory usage, not to mention swap usage, and so-so performance. I finally had enough of Windows and last month I switched back to Linux.  I installed Linux Mint 15 on my desktop (which I bought a year ago) and Ubuntu on my laptop (bought two years ago).  Both Mint and Windows 8 takes about 15-20 seconds to get to the login screen but Mint is much, much, much more responsive for me.  Like night and day.  Not to mention the low memory usage.  I've hardly booted into Windows 8 since installing Linux -- it's just there for games now. Ubuntu on my laptop seems to run the same as Mint does for me on my desktop.

Edit: I was a little off on my timings. I used a stopwatch this time.  Windows 8 from boot menu to login screen was 33.96 seconds and Linux Mint 15 was 31.38 seconds (HP Pavilion p7-1210 w/ 8GB RAM).  Ubuntu 13.04 on my laptop took 8 seconds (HP Pavilion dv7-4263cl w/ an SSD).

---

### Post by buzzingrobot on 2013-08-22
It makes no sense to call anything about Windows or Linux "perfect".  That kind of hyperbole conveys no information.

Software Center is not speedy.  That's why I use one of several alternatives that do exactly the same thing, only faster.

On the other hand, running Windows Updates is also very slow, and no alternatives exist.  I can't decide which program I want to use to pull updates. Nor can I choose which server I want to pull from. 

I've had to recently, and repeatedly, install and re-install Windows 7/8 on some very capable high-end hardware on which I've also run Linux. Nothing about Windows struck me as extraordinarily better, or worse, or faster, or slower, than a polished Linux like Ubuntu.  Ignoring Win8's schizoid GUI, I could use Win7 without any angst.

But...the quality of the font rendering on both was attrocious: Smearing, distortion, pixelation, artifacting.Text in IE10 at msn.com looks like ink ran down the page.   Even on $3000 monitors and $1000 graphics cards in a photo studio the results are awful.  Most of my computing time is spent reading and writing, so text quality is a very high priority.  Windows cannot compete in that category.

---

### Post by startas on 2013-08-22
Well, linux is not very polished, especially ubuntu now, with so many unstable components, like compiz, unity, kernel, soon mir will be added to this list - the whole core. And windows gui is perfect, because even with very old intel graphics, like gma x3100, everything just flies, you press some button, and you instantly get a result (not like in linux, press and wait for gui to load...), or like first gen intel hd graphics, that can even run games like "call of duty mw3" really well, whereas it is enough just to open ubuntu's dash, to make pc lag like hell :D Tried many pcs with windows/linux, but never got a positive experience with linux, and always got super stable and super fast windows. And, well, you can always configure millions of things on windows too, if you have some brains left from using linux :D About updates - i would suggest to end your dial-up internet contract and come to the 21 century :D

---

### Post by monkeybrain20122 on 2013-08-22
> **startas said:**
> Well, linux is not very polished, especially ubuntu now, with so many unstable components, like compiz, unity, kernel, soon mir will be added to this list - the whole core. And windows gui is perfect, because even with very old intel graphics, like gma x3100, everything just flies, you press some button, and you instantly get a result (not like in linux, press and wait for gui to load...), or like first gen intel hd graphics, that can even run games like "call of duty mw3" really well, whereas it is enough just to open ubuntu's dash, to make pc lag like hell :D Tried many pcs with windows/linux, but never got a positive experience with linux, and always got super stable and super fast windows. And, well, you can always configure millions of things on windows too, if you have some brains left from using linux :D About updates - i would suggest to end your dial-up internet contract and come to the 21 century :D

Why do you insist that Windows is better in some cosmic sense based only on your own experience while many others here have experienced the opposite?? If Windows is so superior why don't you just stick with it instead of wasting your time trolling here? :)

---

### Post by startas on 2013-08-22
Well, i am now on windows 7, and suprise surprise, i can write from there to ubuntu forums too :D Meh, you are bigger troll, you have 39 beans :D

---

### Post by Cheesemill on 2013-08-22
And with that, this thread has run it's course.

Some people find Linux faster, some people find Windows faster.

Thread closed.

---

