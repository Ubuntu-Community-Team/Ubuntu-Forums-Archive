---
title: "Really Old Computer. What To Do?"
date: 2011-07-08
forum: The Cafe
---

### Post by Khakilang on 2011-07-08
Recently I was given an old IBM Personal Computer 300GL that come with Intel Pentium 2 processor, not sure about the speed, 64MB RAM, 10GB hard disk I guess never really check, S3 built in display card and Window 95. Thought I might squeeze some juice out of it.

Now the question is what Distros should I use? Of course Tiny Core comes to my mind but I am suck at CLI. Maybe it is time to learn. Other I have thought of is Puppy Linux. But before that. What other Distro is user friendly and able to coup with the low spec? I had no problem with Pentium 3 or 4 but this is beyond my expertise. So what Distro is equivalent to Window 95? Appreciate to whoever that help!
:confused::confused::confused:

---

### Post by country0129 on 2011-07-08
DSL, Puppy - both are working on my old Compaq along with MEPIS.  I like all of 'em.  Couldn't make Ubuntu work on it as hard as I tried.

---

### Post by country0129 on 2011-07-08
:guitar:Sorry...DSL = D.amned S.mall L.inux

---

### Post by jerenept on 2011-07-08
> **Khakilang said:**
> Recently I was given an old IBM Personal Computer 300GL that come with Intel Pentium 2 processor, not sure about the speed, 64MB RAM, 10GB hard disk I guess never really check, S3 built in display card and Window 95. Thought I might squeeze some juice out of it.

Now the question is what Distros should I use? Of course Tiny Core comes to my mind but I am suck at CLI. Maybe it is time to learn. Other I have thought of is Puppy Linux. But before that. What other Distro is user friendly and able to coup with the low spec? I had no problem with Pentium 3 or 4 but this is beyond my expertise. So what Distro is equivalent to Window 95? Appreciate to whoever that help!
:confused::confused::confused:

[Haiku]("http://haiku-os.org/") is actually really good on low-spec computers.

---

### Post by vehemoth on 2011-07-08
You could try peppermint os, never used it but it seams to fit well [http://peppermintos.com/](http://peppermintos.com/)

---

### Post by Primefalcon on 2011-07-08
I'd Lubuntu or barring that, Puppy Linux

---

### Post by frankbooth on 2011-07-08
Some people have proposed very heavy OS' for this type of computer :P.

_64 MB RAM_, you won't be able to run either Lubuntu nor Peppermint on that system, that's for sure.

As some have suggested, maybe Damn Small Linux or Puppy. Or just go with a minimal install of Ubuntu (maybe even that is too heavy, dunno) and don't use GUI applications.

---

### Post by Lampi on 2011-07-08
@Khakilang: debian still ship the 486 arch kernel in their repositories. I had no problems using those packages on a pentium II box and install a small web-/chatserver. Sure thing you boot this one to the prompt only, there is no X involved.

Runs like a charm, does not consume much energy, but it takes it's time to boot up :-)

---

### Post by lucazade on 2011-07-08
> **frankbooth said:**
> Some people have proposed very heavy OS' for this type of computer :P.

_64 MB RAM_, you won't be able to run either Lubuntu nor Peppermint on that system, that's for sure.

As some have suggested, maybe Damn Small Linux or Puppy. Or just go with a minimal install of Ubuntu (maybe even that is too heavy, dunno) and don't use GUI applications.

Agree, X server (needed for any GUI application) will eat more than half of that 64mb, so you wont to be able to run anything on it.
Ubuntu minimal installation, cli browser like lynx and other tiny apps for terminal.

---

### Post by Random_Dude on 2011-07-08
K.Mandla's blog has some cool posts about how to revive old computers.
[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)

Cheers :cool:

---

### Post by snowpine on 2011-07-08
Not to be negative but I would recycle it. The hardware specs are borderline even for the most "lightweight" distros and there is nothing it can do that can't be done more efficiently on modern hardware. If you want to learn more about terminal applications and commands, you can do so in a terminal window (or virtual machine) on your regular computer. :)

---

### Post by mips on 2011-07-08
TinyCore.

Installing to disk takes jumping through a few hoops but once it's installed you have a GUI.

---

### Post by BrokenKingpin on 2011-07-08
++TinyCore... I am pretty sure it does have a GUI, just a very basic one.

---

### Post by mips on 2011-07-08
> **BrokenKingpin said:**
> ++TinyCore... **I am pretty sure it does have a GUI, just a very basic one**.

It's a pretty nice one I reckon, played around with it two weeks ago.

---

### Post by IWantFroyo on 2011-07-08
Macpup.

I would suggest Arch, but you said you don't like CLI.

---

### Post by Dustin2128 on 2011-07-08
With patience and time, gentoo with icewm could work wonders on that hardware. Not for the faint of heart, though. If it's got appropriate sockets/slots though, you could upgrade it to a still-useful pentium 3 ~1GHz with around 384Mb RAM. I've got a pair of machines with those specs, xubuntu hardy flies on one of them, debian stable on the other.

---

### Post by Old_Grey_Wolf on 2011-07-08
Will it boot from a CD or USB? Some of the really old computers wouldn't boot from anything but a floppy; therefore, it is rather difficult to install any distro. I had a 486DX2 with 64MB of RAM and a 2GB HDD. I finally found a floppy that I could boot from in order to install an OS; however, the computer was so slow that it was useless for my needs.

It was fun trying it although I ended up disposing of the computer. :)

---

### Post by Famicube64 on 2011-07-08
Forget Linux on that thing. If you still have the 95 disc, reinstall it and then download and install KernelEX. It'll let you run pretty much anything that will run on XP. This means you can have a modern antivirus and web browser. Not that you really need the antivirus.

---

### Post by Old_Grey_Wolf on 2011-07-08
> **Famicube64 said:**
> Forget Linux on that thing. If you still have the 95 disc, reinstall it and then download and install KernelEX. It'll let you run pretty much anything that will run on XP. This means you can have a modern antivirus and web browser. Not that you really need the antivirus.

I thought that KernelEX only worked for Windows 98 and Windows ME. The OP has Windows 95.

---

### Post by Famicube64 on 2011-07-08
I saw an update on the site that it "Now works better with Windows 95" so I suppose it does now.

Edit: Nevermind, it looks like it used to support 95 but dropped it due to limitations. Sorry about that.

---

### Post by Sammi on 2011-07-08
I've tried DSL and Puppy, but they just weren't small or easy enough.

Then I tried TinyCoreLinux, and it was an eye opener. I didn't know you could make such a small distro so elagant and smooth. Nice GUI and lots of functionality in less than 10 MB. And there is an ocean of extra apps to install from the repository. It's madness I tell you!

I didn't set out to sound like such an ad, but hey, TinyCore really deserves more recognition.

---

### Post by zer010 on 2011-07-08
With those low of specs, about the most useful thing you could do is a headless server of some sort. Print server, file server or use it as a firewall/honeypot box.  ^_^d

---

### Post by Dustin2128 on 2011-07-08
Actually, not being good with the command line might be a good reason in itself to install gentoo. I learned more in the 6 hair-tearing hours of gentoo install and setup on an old pentium 4 than I ever did in my first year and a half of ubuntu.

---

### Post by Bandit on 2011-07-08
DSL or Puppy IMHO, Other option would be to install Ubuntu Server and recompile the kernel leaving out as much stuff as you can without gimping your system. Then install Xorg and somthing like openbox or windowmaker.

My first fully dedicated linux box was a K6-2 500 with 96MB of RAM, it ran good. Played MP3s with XMMS and surfed the net just fine over 56k external modem.

---

### Post by Bandit on 2011-07-08
> **Dustin2128 said:**
> Actually, not being good with the command line might be a good reason in itself to install gentoo. I learned more in the 6 hair-tearing hours of gentoo install and setup on an old pentium 4 than I ever did in my first year and a half of ubuntu.

So true. CLI is a good thing to learn. I have been studying for my Linux+ certification over the past few days and there is tons of CLI stuff I completely forgot that I am relearning. Its actually very fun.:)

---

### Post by Khakilang on 2011-07-09
It certainly a challenge to have such an old computer to run any Distro. But I believe it is time for me to take that challenge. I have been spoilt with all the GUIs eye candy for too long. I think I might as well get my hand dirty on this. Thank you guys for all your input.

---

### Post by Dustin2128 on 2011-07-09
So, gentoo? Always glad to help, of course.

---

### Post by Khakilang on 2011-07-09
Currently I have Tiny Core and Puppy store some where. Gentoo, why not!

---

### Post by Dustin2128 on 2011-07-09
> **Khakilang said:**
> Currently I have Tiny Core and Puppy store some where. Gentoo, why not!
Don't do it unless you're really wanting to learn a lot to get the system setup- but it serves as one of the best crash courses in command line linux I've ever used. But really, first time around you have to do it by the handbook: [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml) . Tip- don't use genkernel. It's the easy way out but you don't get as much of a speed boost.

I'd set aside a good few hours for a gentoo install. If you don't have that kind of time, tiny core might work out. Anyway, if you have to have a GUI on the machine afterwards, I'd recommend icewm, lxde or straight openbox.

---

### Post by cbanakis on 2011-07-09
I think the fastest distro for a pentium2 box, would be the one where you distribute it off the edge of a cliff.
You will never top that speed.

Next in line would maybe be Puppy.

I only used for about an hour before dumping it, but it seemed to be quite snappy.

---

### Post by Bandit on 2011-07-09
Talking about slow PCs, my daughter isnt using her Netbook anymore as she is using my wifes laptop. Its got the slightly slower 32bit Atom in it with 1GB of RAM. I am thinking about install Xubuntu on it since its got XP on it. Just dual boot them incase. Its a nice IBM netbook.:twisted:

---

### Post by Khakilang on 2011-07-09
> **Dustin2128 said:**
> Don't do it unless you're really wanting to learn a lot to get the system setup- but it serves as one of the best crash courses in command line linux I've ever used. But really, first time around you have to do it by the handbook: [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml) . Tip- don't use genkernel. It's the easy way out but you don't get as much of a speed boost.

I'd set aside a good few hours for a gentoo install. If you don't have that kind of time, tiny core might work out. Anyway, if you have to have a GUI on the machine afterwards, I'd recommend icewm, lxde or straight openbox.

I keep that in mind and already bookmark it for future reference. Thanks!

---

### Post by wolfen69 on 2011-07-09
Recycle it. Computers that old are next to useless. Really, what would you expect to do with it? You can't even run a youtube video on it. Basic word app? Maybe?

---

### Post by Dustin2128 on 2011-07-09
> **cbanakis said:**
> I think the fastest distro for a pentium2 box, would be the one where you distribute it off the edge of a cliff.
You will never top that speed.

*tsk tsk* so wasteful... you can do a lot with such hardware.

---

### Post by wolfen69 on 2011-07-09
> **Dustin2128 said:**
> *tsk tsk* so wasteful... **you can do a lot with such hardware**.

A lot? What do you consider *a lot*? I see it as a waste of time. I don't want it in the landfill, just recycled. What's wrong with that?

---

### Post by Dustin2128 on 2011-07-09
> **wolfen69 said:**
> A lot? What do you consider *a lot*? I see it as a waste of time. I don't want it in the landfill, just recycled. What's wrong with that?
It all depends on how smart you are with resources- with simply the command line, those specs would handle most distros fairly well. From there, you've got the server end- mail server, web server, irc server etc. As far as end user goes, using command line programs, you can listen to music, browse the web, check and send email, code, chat with friends via irc and more. Need to relax? Just fire up doom! :p Or nethack.

---

### Post by wolfen69 on 2011-07-09
> **Dustin2128 said:**
> It all depends on how smart you are with resources- with simply the command line, those specs would handle most distros fairly well. From there, you've got the server end- mail server, web server, irc server etc. As far as end user goes, using command line programs, you can listen to music, browse the web, check and send email, code, chat with friends via irc and more. Need to relax? Just fire up doom! :p Or nethack.

Don't make it out to be a multimedia powerhouse. ;) It is what it is. And for even most semi-modern uses, it won't do much.

I accept donated computers from schools and businesses, (and have gotten many) but there's no way I would take 50 of those computers. They are just too limited in the real world. Things have moved on since Win 3.1

If you can find a use for it, go for it. But the stuff *I* do, requires a bit more, um, oomph? Horsepower? What's the maximum ram that pc can even take? My general rule is, if it can't even play a youtube video, it's not worth the hassle. But I've had 100's of computers go through my hands, so maybe I'm jaded (spoiled) a bit.

---

### Post by Dustin2128 on 2011-07-09
Multimedia, but those media are text and music :D. I could think of a million uses for such a computer- yes, you are spoiled. I'm thinking that it can be upgraded to a usable amount though- somewhere in the 256-512Mb range. As far as a semi-modern GUI desktop goes though- yeah, anything below a pentium 3 won't cut it for me. Even then, only with a respectable clock. But hey, that was back when the same generation of processors fit the same connectors as other members of its generation, so that can be upgraded on the cheap.

And you couldn't even think of a use for 50 pentium IIs? Beowulf cluster!

---

### Post by wolfen69 on 2011-07-09
> **Dustin2128 said:**
> But hey, that was back when the same generation of processors fit the same connectors as other members of its generation, so that can be upgraded on the cheap.

As a whole though, I like computing much better now compared to when you could "swap parts" easier. I see what you're saying, but I sell computers to make money, and P2's just don't fit for some reason. 

Like I said, go for it if it works, but for the most part, most people will pass. Even early to mid P4's are getting tuff to work with if you want a fully functional, modern computer.

---

### Post by Dustin2128 on 2011-07-09
> **wolfen69 said:**
> As a whole though, I like computing much better now compared to when you could "swap parts" easier. I see what you're saying, but I sell computers to make money, and P2's just don't fit for some reason. 

Like I said, go for it if it works, but for the most part, most people will pass. Even early to mid P4's are getting tuff to work with if you want a fully functional, modern computer.
I use a pentium D personally, but what I was complaining about is how, for instance, intel currently has 3 different sockets being sold concurrently for the same generation of CPUs. I've personally not had much of a problem setting up even an intensive GUI environment on even a pentium 3- as long as the video card isn't something ancient. GeForce 3 Ti/4 Ti is sufficient. Pentium 4 is comfortable to me as long as the clock is >2.5GHz, hyperthreading just makes it all the sweeter.

---

### Post by wolfen69 on 2011-07-09
> **Dustin2128 said:**
> GeForce 3 Ti/4 Ti is sufficient.

We must be doing different things. I had a geforce 3 ti in 03/04, and it didn't last long even then. I'm not even a big gamer, but nvidia has made great strides in future cards. I don't know, maybe I notice fractions of a second difference in new technologies, (speedwise) and other people don't care. But to say a geforce 3 is sufficient these days is stretching it, big time. Plus, having a decent video card eliminates one more bottleneck.

---

### Post by Dustin2128 on 2011-07-09
We can't seem to agree on anything... I use a 9600 GT myself, but I've got a machine with a Ti4200 in the house. It runs minecraft acceptably well, and runs ioquake3 based games amazingly well. Aside from that, it handles my basic xfce GUI just fine, but it can scale to KDE- it's just less responsive. A GeForce 3 is not sufficient for most people, but to run a basic GUI, even some compositing, it's just fine. Especially considering that it's more powerful than integrated intel video. For a person building a machine, I would not dream of recommending a GeForce 3, I'm just saying that's good enough for **me **in most cases, to setup a decent, responsive, low resource pentium 3 system. I think you underestimate the capabilities of old hardware.

---

### Post by GarlicBread on 2011-07-09
> **Khakilang said:**
> Recently I was given an old IBM Personal Computer 300GL that come with Intel Pentium 2 processor, not sure about the speed, 64MB RAM, 10GB hard disk I guess never really check, S3 built in display card and Window 95. Thought I might squeeze some juice out of it.

Now the question is what Distros should I use? Of course Tiny Core comes to my mind but I am suck at CLI. Maybe it is time to learn. Other I have thought of is Puppy Linux. But before that. What other Distro is user friendly and able to coup with the low spec? I had no problem with Pentium 3 or 4 but this is beyond my expertise. So what Distro is equivalent to Window 95? Appreciate to whoever that help!
:confused::confused::confused:

Lubuntu might work, but don't take my word on that - worth a shot though.

---

### Post by Dustin2128 on 2011-07-09
> **GarlicBread said:**
> Lubuntu might work, but don't take my word on that - worth a shot though.
Lubuntu's not going to run with less than 100Mb RAM- he's settled on gentoo, puppy, or tiny core.

---

### Post by Khakilang on 2011-07-09
After going through again on the spec. It is actually Pentium 2 running at 400Mhz and only 2GB hard disk. So I upgrade to 128MB RAM and 20GB hard disk. So I figure if it can use Window 95 swiftly. I am sure there is something Linux can do. Let see what happen in a few days.

---

### Post by Erik1984 on 2011-07-09
FreeDOS?

---

### Post by Dustin2128 on 2011-07-09
> **Khakilang said:**
> After going through again on the spec. It is actually Pentium 2 running at 400Mhz and only 2GB hard disk. So I upgrade to 128MB RAM and 20GB hard disk. So I figure if it can use Window 95 swiftly. I am sure there is something Linux can do. Let see what happen in a few days.
400MHz is not bad- high for a pentium 2. 128MB RAM opens up more options- you can probably run a gui that doesn't suck- openbox is sounding better with more than 100MB RAM. It may even be possible to use it as a web browsing machine with adblock plus and noscript- don't expect a speed demon though. See if you can find out what interface the pentium 2 uses though, if it's slot 1 you can upgrade it to a cheap (5$ if that) 1GHz pentium 3 which really ups the use you can get out of the machine.

---

### Post by Khakilang on 2011-07-19
Ok. Here are the result. I try Puppy Linux but come out with an error. Maybe the ISO may have been corrupted. Try Damn small Linux and It seem to works fine but I haven't given it a good run yet and lastly Gentoo which I think I may need more time to master all its command but nevertheless it would be a good way to learn Linux. Conclusion, there is some life in that old junk but of course for simple light work so I won't chuck it away just because it is old and outdated. Thank for all your input!.

---

### Post by Dustin2128 on 2011-07-19
My pentium II box has a slightly higher clock at 450MHz, but with just 384Mb RAM, it handled openbox, midori web browser, freedoom and loads else just fine. I'm compiling gentoo as we speak, so I'll test that for you tomorrow probably :). Oh, best of all, those old CPUs are cooled exclusively by heat sink. With a good spinning hard drive or a solid state, the thing is *silent*. I could think of endless uses for it, some even including using the Floppy drive!

---

### Post by Khakilang on 2011-07-19
> **Dustin2128 said:**
> My pentium II box has a slightly higher clock at 450MHz, but with just 384Mb RAM, it handled openbox, midori web browser, freedoom and loads else just fine. I'm compiling gentoo as we speak, so I'll test that for you tomorrow probably :). Oh, best of all, those old CPUs are cooled exclusively by heat sink. With a good spinning hard drive or a solid state, the thing is *silent*. I could think of endless uses for it, some even including using the Floppy drive!

Your computer sound cool and a higher spec than mine. But mine has a clicking sound coming from the hard disk but it doesn't show any problem or error and everything seem to run fine. More test is needed to actually proof its life span.:D

---

### Post by Dustin2128 on 2011-07-19
Hm, a clicking hard drive is usually a sign of imminent death. I'd look into a replacement if I were you- that machine would be great as a home file server with a 160GB PATA. Really though, the hard drive is usually the point of failure in old machines- with a good one, those things usually last forever.

---

