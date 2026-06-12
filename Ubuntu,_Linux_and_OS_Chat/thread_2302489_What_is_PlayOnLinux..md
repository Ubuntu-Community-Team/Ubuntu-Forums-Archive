---
title: "What is PlayOnLinux."
date: 2015-11-10
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2015-11-10
i have an old emachines T3092 desktop with an (amd athlon XP3000+) 2.1ghz single core processer / 2.0gb ddr memory and i believe it was born around 2004.
installed lubuntu 14.04 and it runs ok however the internet is slow and i mean slow. also it wouldn't support youtube something to do with SSE instruction whatever. installed PlayOnLinux and running internet and youtube through it all works normal for what this is. exactly what is PlayOnLinux. are there any security risks in runnig internet in PlayOnLinux mode.

thanks
the poorguy

---

### Post by Bucky Ball on 2015-11-10
> **poorguy said:**
> exactly what is PlayOnLinux.

You didn't think to look at [their website]("https://www.playonlinux.com/en/")? "What is Playonlinux?" is answered first question, top of the page there. :)

No idea about security risks involved with running internet and Playonlinux.

---

### Post by poorguy on 2015-11-10
> **Bucky Ball said:**
> You didn't think to look at [their website]("https://www.playonlinux.com/en/")? "What is Playonlinux?" is answered first question, top of the page there. :)

No idea about security risks involved with running internet and Playonlinux.

OK you got me there. i didn't think. 

anyway always get better answers and advice here.
i will check out PlayOnLinux website.

thanks
the poorguy

---

### Post by monkeybrain20122 on 2015-11-11
It basically allows you to install and run your Windows application with a specific version of wine. This would be useful if your application only works in some versions of wine but not others. With POL you can install many versions of wine and specify the version for each application. I never find any use of it though since I only have one wine application and it works pretty for all versions of wine.

---

### Post by poorguy on 2015-11-11
my only interest was to use POL for normal web surfing which when I ran POL for some reason it ran normal. I don't understand why but I have since put it on the shelf. when I ran system manager and got on the web it always was showing cpu at 100%. it may just be to old as its processor is SSE and is not supported anymore. have to read up on exactly what SSE is but I know it is way old and no longer supported.

---

### Post by monkeybrain20122 on 2015-11-11
> **poorguy said:**
> my only interest was to use POL for normal web surfing which when I ran POL for some reason it ran normal. I don't understand why but I have since put it on the shelf. when I ran system manager and got on the web it always was showing cpu at 100%. it may just be to old as its processor is SSE and is not supported anymore. have to read up on exactly what SSE is but I know it is way old and no longer supported.

Well POL is basically wine. What does it have to do with web surfing??

---

### Post by poorguy on 2015-11-12
> **monkeybrain20122 said:**
> Well POL is basically wine. What does it have to do with web surfing??


I was able to load Mozilla though POL and use it for web surfing which ran quicker through POL.
the default Mozilla browser in lubuntu ran really slow.
when using mozllia through POL it ran faster.
I am confused also by that.
the Mozilla browser in POL may have been an older version which maybe required less resources. I don't know.
this amd Athlon xp 3000+ seems to be SSE and that is really old technology and not supported by a lot of things that processors with SSE2 or SSE3 or SSE4 supports. SSE has something to do with instruction sets of data or something as such I am uncertain as this is beyond any of my knowledge.
 just an old desktop that I installed lubuntu on to see how it would run and it did not do very well at all. I believe that it is just way to old. I have read that people have ran Linux on old Pentium 3 processors and I myself have installed and ran Linux on Pentium 4 processors and it worked very well. can't understand why this pc is so slow on the internet. it had widows xp running on it and worked well when it was given to me. it doesn't seem to like Linux though. something for me to play with that's all.

---

### Post by poorguy on 2015-11-12
in my one year as a Linux user I have had very good results with installing Linux distros on old windows xp computers that ran great with Linux.

I have also installed Linux distros on old windows xp computers that just didn't like Linux and wouldn't run no matter what I tried to do to get them to run. my own experience is that certain hardware just will not run with Linux distros.
I resurrect old windows xp computers and donate them through a project at my church so I deal with lots of old hardware and find that most is supported very well in Linux and also the rare occasion of some old hardware is not and I think that is the case with this desktop. I do enjoy the challenge of this and it helps a lot of people out that can't afford a computer.

---

### Post by Mike_Walsh on 2015-11-12
Yup; you've only got SSE's. (Short for [COLOR=#ff0000]**S**[/COLOR]treaming [COLOR=#ff0000]**S**[/COLOR]IMD [COLOR=#ff0000]**E**[/COLOR]xtensions.)

[http://www.cpu-world.com/CPUs/K7/AMD-Athlon%20XP%203000%2B%20-%20AXDA3000DKV4D.html](http://www.cpu-world.com/CPUs/K7/AMD-Athlon%20XP%203000%2B%20-%20AXDA3000DKV4D.html)

Anything requiring video playback requires at the very least SSE2's; SSE3's and upward, better still.

> [COLOR=#000000] have to read up on exactly what SSE is but I know it is way old and no longer supported.

[/COLOR]Not so much a case of no longer supported (it's an integral part of every modern processor out there); it would be truer to say that it's no longer the most current instruction set available. And this stuff is at 'firmware' level (installed at the time of manufacture by Intel or AMD); it's not something that a user can update or upgrade.

[https://en.wikipedia.org/wiki/Streaming_SIMD_Extensions](https://en.wikipedia.org/wiki/Streaming_SIMD_Extensions)
[https://en.wikipedia.org/https://en.wikipedia.org/wiki/Streaming_SIMD_Extensionswiki/SSE2](https://en.wikipedia.org/https://en.wikipedia.org/wiki/Streaming_SIMD_Extensionswiki/SSE2)
[https://en.wikipedia.org/wiki/SSE3](https://en.wikipedia.org/wiki/SSE3)
[https://en.wikipedia.org/wiki/SSE4](https://en.wikipedia.org/wiki/SSE4)

All a bit technical, I'm afraid; but basically , these are extra instruction sets (over & above the basic MMX ones.....which are intrinsic to all modern, x86 processors), built-in to your CPU, which tell it what it is able to do with a given byte of information, in any given situation, according to what program code it is fed. That's very simplistic.....but it gives you some idea of what it's all about.

You're on the money when you state that your old laptop with Lubuntu 'didn't do very well at all'. Really, anything still running these days, if it doesn't have SSE2's, absolute minimum, won't be able to run the majority of modern, x86-architecture software (i386; i486, i586, etc.)

In a nutshell, the higher the instruction set, the more complex the instructions your processor will be capable of carrying out. Each successive instruction set is in addition to the ones before it, i.e, my own Athlon 64 X2 3800+ dual-core has SSE3's. This means it has MMX+SSE+SSE2+SSE3.

Hope that helps to lighten the murk a little bit. :)


Regards,

Mike. ;)

---

### Post by poorguy on 2015-11-12
hey mike thanks for the links and input.
kinda figured it had something to do with the SSE.
it is a great little desktop for its day (2003 / 2004) and i think i will just make it a windows xp desktop and load all of my old software and 2002 flight simulator on it just for the fun of it. and of course keep it off the internet.

as old as i am i am still learning.
life is great.
the poorguy

---

### Post by Mike_Walsh on 2015-11-12
Glad I could help. Ah, you're never too old to learn; it just takes a bit longer when you get the wrong side of 50! (As I know to my cost...)

Yes, the whole business of SSE's, SSE2's, etc **is** confusing. You're in good company there. I have a slightly older Dell than yours, but it's Intel-based; Pentium 4 generation. Those had SSE2's from the word go. At that time, Intel had just snatched the advantage back from AMD; less than a year later, AMD rubbed their nose in it (again!) with the introduction of the Athlon 64 series of CPU's, with SSE3 support; the first ever CPU's on the general market that would natively run 32- AND 64-bit software, without the user having to intervene. Which is what mine is.

Might I make a suggestion? Give 'Puppy' Linux a try. It's rejuvenated many an XP-era 'puter; it's MY main OS (in fact, I run four of 'em!) You might be pleasantly surprised at just how well it **does** run.

Unfortunately, you're kinda stuck with that Athlon XP. The Socket 462 (Socket A) boards would support the Semprons & Durons, as well as the K7 Athlons and Athlon XPs.....but none of them have any more than SSE (1). And that **is** going to be a 'brick wall' as far as modern browsers are concerned...


Regards,

Mike. ;)

---

### Post by kurt18947 on 2015-11-12
I had one of those and saw the same symptoms - 1 CPU core pegged at 100% and flash playback was atrocious.  PATA port died on that board so I bought my current desktop MoBo. Would HTML5 or other non-flash video perform as poorly as flash on non-SSE2+ processors?

---

### Post by poorguy on 2015-11-12
i was actually thinking about a super lite linux distro that i had read about on here. i will give puppy linux a try and see how it runs.
this pc has two 40gb hard drives so i can still do the windows xp as i have tons of cool software for it that can be used ofline and also the old 2002 flight simulator. i can install puppy linux on the other hard drive. yeah i will give that a try and see what happens. it is just cool for what it was in it time. it will give me something to do for the fun of it and perhaps it will be useful again.

thanks again

---

### Post by poorguy on 2015-11-12
hey mike

one question even with the puppy linux i will still have the problem with streaming of videos correct.

---

### Post by monkeybrain20122 on 2015-11-12
You are running Windows version of Firefox with POL. I don't know how it could be "faster", but for your problem with old hardware and videos, I would suggest avoiding flash and HTML5 altogether if possible. Get the mpv addon [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)
For this you need mpv and youtube-dl installed in your system.

For mpv
[https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

For youtube-dl
[https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)

This works on many sites besides youtube. Youtube-dl needs to be kept up to date. With mpv it is a bit tricky, the latest release is 12.0 but it has removed some "hacks" for dash videos (format used in Youtube) because the latest ffmpeg now supports this format. But the problem is this latest version of ffmpeg is not released so no distro provides it unless you compile it yourself and then compile mpv with it. With older ffmpeg mpv12+youtube-dl works everywhere except Youtube, well it works but it takes forever to buffer. So you need mpv which is not too old but not the newest, 11.0 would work (from Mc3man's ppa) So you need to install it from ppa and then pin it in synaptic so it won't get upgraded.
I just compile mpv myself.

---

### Post by monkeybrain20122 on 2015-11-12
> **poorguy said:**
> hey mike

one question even with the puppy linux i will still have the problem with streaming of videos correct.

Yes same problems. same advise re mpv. But puppy uses a stripped version of Firefox by default (palemoon) some addons may not work. Of course you won't be able to use Ubuntu's ppas so ypu may have to 1) install Firefox 2) get mpv somewhere, repo version maybe too old. 3) Get youtube-dl and update it manually (it may be in puppy's repo but100% guaranteed broken if it is a very old version like in Ubuntu's repo.

---

### Post by poorguy on 2015-11-12
hey monkeybrain20122

ok well sounds like i going to have some research to do but i am willing to do that. learning quite a bit about things here. confused but interesting however that is what makes it fun. i am starting to understand what it was like in the earlier days of pc OS and such. i cut my teeth on windows xp so most things worked pretty much out of the box when i started. anyway thanks for the input and help. i will figure all of this out and i may learn some more seem to be using brain cells that have been dormant for awhile.

thanks for everyones [I]patience.
life is good.
the poorguy
[/I]

---

### Post by Mike_Walsh on 2015-11-12
> **poorguy said:**
> hey mike

one question even with the puppy linux i will still have the problem with streaming of videos correct.

Hi, poorguy.

Actually, there is a way round it that might work. A number of us on the Puppy Forums have developed a way to stream videos'n'stuff directly to VLC via a proxy (streaming is native to VLC anyway). Mind you, I don't know whether it'd work for you. BTW, I agree with you; for its time, your PC was a pretty nifty piece of hardware. I've been reading up about it; a few period reviews of the time.

It's a ten-minute job to install Puppy; what've you got to lose? If it won't do what you want, just nuke it. No harm, no foul.


Regards,

Mike. :)

---

### Post by poorguy on 2015-11-12
hey mike,

installed tarpup 6.0 CE
very different / difinate learning curve here.
fast as hell. youtube works as i beleive html5 might be the case as i haven't installed adobe plash anything and don't plan on it.
did the auto firewall and i choose admin instead of spot.
it works but i have to set up things again when i reboot don't know where my 1st reboot folder is but i will find it.
runs really great just takes some getting use to as it is really different.
the old emachine is got new life again and it is cool because i like old out dated stuff.


thanks  for your help and no complaints at all.
life is good.
the poorguy

---

### Post by Mike_Walsh on 2015-11-13
Hah! You sound as though you're like me; I, too, like keeping older equipment going. I'm not fussed about having the most modern, up-to-date stuff on the market. Don't have no real need for it.....and I'd only be wasting my money.

I take it you're referring to your 'save-folder'? This is usually created at first shut down on your actual install.....and is where Puppy saves all your system config stuff. You get the option for it at the end of the Live session, but there's no point creating it at that stage (since Puppy is running 'Live' at that point, and in RAM, you'd just lose everything; Puppy doesn't use 'persistence' like the 'buntus); just shut down, and then re-boot into your newly-created Pup. **Then** create your 'save-folder' at the end of your first **real** session.

Rox ( the file manager in Tahrpup...and in fact, **most** Pups) **does** take some getting used to.....but when you've gotten the hang of it, it is **so** ridiculously easy to use it's untrue.

Anyway; rather than go into detail here, I'll give you a link to the Puppy Forums:-

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

We can all of us help you a **lot **better over there, than I can by myself on here.

BTW; your 'save-folder' should be mounted at /mnt/home (which is the partition, on HDD or USB, where you've installed Puppy).

Hope to see you over there!


Regards,

Mike. ;)

---

### Post by poorguy on 2015-11-13
hey mike,

yeah it took me a few installs to get it right but they say the third is the charm and it is as i finally got it installed right. i had to install it on the hard drive as this won't boot a usb drive but it all fits on this super large 20gb hdd with room to spare. runs well on this old desktop.
i am really liking tahrpup for my PC needs it is all i need. yep you will see me over on the pup forum as i am sure the ubuntu forum folks need a rest from me. HAHA! 
the old stuff works good and its all i need and there is tons of goodies still available.

thanks.
the poorguy

---

### Post by poorguy on 2015-11-13
> **kurt18947 said:**
> I had one of those and saw the same symptoms - 1 CPU core pegged at 100% and flash playback was atrocious.  PATA port died on that board so I bought my current desktop MoBo. Would HTML5 or other non-flash video perform as poorly as flash on non-SSE2+ processors?

that i beleive you will have to try. i have not installed any adobe flash plugin on my SSE system and youtube works but it is slow due to the processor that it has. i was surprised that youtube even worked as it never would when i had lubuntu installed.

the poorguy

---

### Post by Mike_Walsh on 2015-11-13
Ah, that's great! Glad to hear you've got it sorted.....and that it's doing what you want from it.

I said Puppy might do the trick, didn't I? Just as a general note (lest anybody accuse me of 'poaching' :lol: ), the idea here was to help out somebody whose hardware even struggles with the most lightweight of the 'buntu 'flavours.....and by extension, that likely goes for many of the 'buntu-based 'spins'.

The 'Pups' (although many of them have access to the Ubuntu repositories), aren't even remotely built on any Ubuntu code-base. Rather, they are built using the T2 and 'Woof-CE' build systems, and, as such, are pretty much unique among Linux distros, being built from the ground up. The build systems are able to take binary packages from just about all of the available Linux distros, and turn them into the uniquely lean, minimalist 'Puppy' code-base.....and by this, it can be seen that Puppy is, very definitely, a 'one-off'. Yet, it undeniably works.

T2 was the first build-system, developed by Puppy's originator, Barry Kauler. When Barry gave up full-time development about 2 1/2 yrs ago to concentrate on his 'Quirky' series (the most recent of which is Quirky 'Werewolf', based on 15.10), the community took the T2 system, and further developed & refined it into the 'Woof-CE' build-system.

T2 and Woof-CE are fully automated; upon being presented with the desired binary packages, you run it.....and a fully functional Puppy ISO file comes out at the other end. This is, of course, a simplified version of events.....but in essence, that is what happens. So, in theory, anybody can build their very own, personalised Puppy.....which accounts, partly, for why there are over 400 different 'spins' & 'remasters' of this amazing little distro.

Puppy to the rescue again! :D


Regards,

Mike. ;)

---

